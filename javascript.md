# JavaScript Interview Guide — 4–5 Years of Experience

This guide uses simple English. It covers your 50 questions and adds important topics that interviewers often use to check deeper understanding.

For each answer, learn the idea, explain the example, and discuss the mistake to avoid. You do not need to memorize every sentence. In an interview, give the short answer first, then explain a useful example and a tradeoff.

No question list can guarantee success in every interview. For this experience level, you should also practice debugging, coding, browser behavior, and explaining decisions from your own projects.

## 1. What are the differences between `var`, `let`, and `const`?

**Interview answer:** `var` is function-scoped. `let` and `const` are block-scoped. `let` allows reassignment; `const` does not. I normally use `const`, use `let` when a value must change, and avoid `var` in new code.

| Behavior | `var` | `let` | `const` |
| --- | --- | --- | --- |
| Scope | Function or global | Block | Block |
| Reassign | Yes | Yes | No |
| Redeclare in the same scope | Generally yes | No | No |
| Read before declaration | `undefined` | ReferenceError | ReferenceError |
| Initial value required | No | No | Yes, except declarations in loop headers such as `for...of` |

```js
if (true) {
  var a = 1;
  let b = 2;
}
console.log(a); // 1
// console.log(b); // ReferenceError

const user = { name: "Sam" };
user.name = "Alex"; // Allowed: the object can change.
// user = {}; // TypeError: the binding cannot be reassigned.
```

**Important:** `const` does not make an object immutable. In a classic browser script, top-level `var` can become a property of `window`; top-level `let` and `const` do not. Module variables are scoped to the module.

## 2. What are JavaScript’s primitive and non-primitive data types?

**Interview answer:** JavaScript has seven primitive types: `string`, `number`, `bigint`, `boolean`, `undefined`, `symbol`, and `null`. Objects are non-primitive. Arrays, functions, dates, maps, and sets are all objects.

Primitives are immutable values. Changing a string variable replaces its value; it does not edit the original string. Objects can hold properties and can usually be changed.

```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10

const first = { score: 10 };
const second = first;
second.score = 20;
console.log(first.score); // 20: both refer to the same object.

typeof null; // "object": a historical language quirk.
typeof []; // "object"
typeof (() => {}); // "function"
Array.isArray([]); // true
```

**Important:** JavaScript passes arguments by value. For an object, that value is a reference to the object. It is misleading to say JavaScript passes objects by reference.

## 3. What is the difference between `null` and `undefined`?

**Interview answer:** `undefined` usually means a value has not been supplied or assigned. `null` usually means we intentionally represent an empty value. Both are separate primitive values.

```js
let name;
console.log(name); // undefined
console.log({}.missing); // undefined

const selectedUser = null; // Intentionally no selected user.

null == undefined; // true
null === undefined; // false
```

A function without a returned value also returns `undefined`. Default parameters apply to `undefined`, but not to `null`.

```js
function greet(name = "Guest") { return name; }
greet(undefined); // "Guest"
greet(null); // null
```

**Practical use:** Agree on a clear API contract. For example, `null` can mean “no saved address,” while a missing property can mean “this field was not requested.”

## 4. What is the difference between `==` and `===`?

**Interview answer:** `==` compares after applying type conversion when needed. `===` compares without that conversion. I normally use `===` because the result is easier to predict.

```js
5 == "5"; // true
5 === "5"; // false
false == 0; // true
false === 0; // false
null == undefined; // true
{} === {}; // false: different objects.
NaN === NaN; // false
```

Object equality checks identity, not matching contents. Two objects with the same properties are still different objects.

**Follow-up:** `Object.is(NaN, NaN)` is `true`; `Object.is(0, -0)` is `false`. Strict equality treats `0` and `-0` as equal. An intentional `value == null` checks both `null` and `undefined`, but use it only when the team's style allows it.

## 5. What is type coercion, and how does it affect addition and comparison?

**Interview answer:** Type coercion is automatic conversion from one type to another. It happens in arithmetic, comparisons, conditions, and other operations. I use explicit conversion when handling input to avoid surprising results.

```js
"5" + 2; // "52": string concatenation.
"5" - 2; // 3: numeric conversion.
Number("5") + 2; // 7
"10" < "2"; // true: string comparison.
"10" < 2; // false: numeric comparison.
Boolean("false"); // true: it is a non-empty string.
Number(""); // 0
```

For `+`, operands are converted to primitive values first. If either resulting value is a string, JavaScript concatenates. Otherwise it performs numeric addition; mixing `BigInt` and `Number` throws.

**Mistake to avoid:** Form inputs are usually strings. Validate them before conversion because `Number("")` gives `0`, which may incorrectly accept an empty field.

## 6. What are truthy and falsy values?

**Interview answer:** A falsy value becomes `false` in a Boolean context. A truthy value becomes `true`. The usual falsy values are `false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, and `NaN`.

```js
Boolean([]); // true
Boolean({}); // true
Boolean("0"); // true
Boolean("false"); // true

const count = 0;
count || 10; // 10: replaces every falsy value.
count ?? 10; // 0: replaces only null or undefined.
```

**Practical use:** Use `??` for defaults when `0`, `false`, or an empty string is a valid value. Use explicit checks when the business rule is more specific than “truthy.” An empty array is truthy; check `items.length` to know whether it contains items.

**Browser edge case:** The legacy `document.all` object is also falsy. It is rarely relevant to application code.

## 7. What is hoisting, and how does it affect variables and functions?

**Interview answer:** Hoisting describes how declarations are handled before the code in a scope runs. The code is not physically moved. `var` is initialized to `undefined`; `let` and `const` exist but cannot be read before initialization. Function declarations are usually available before their line runs.

```js
console.log(total); // undefined
var total = 10;

sayHello(); // "Hello"
function sayHello() { console.log("Hello"); }

// console.log(price); // ReferenceError
let price = 20;
```

A function expression follows the rules of the variable holding it. Calling a `var` function expression before assignment gives a TypeError because the variable contains `undefined`.

**Mistake to avoid:** Saying `let` and `const` are “not hoisted.” Their bindings are created early, but remain uninitialized in the temporal dead zone.

## 8. What is the temporal dead zone?

**Interview answer:** The temporal dead zone, or TDZ, is the period from entering a scope until a `let`, `const`, or class binding is initialized. Reading that binding during this period throws a ReferenceError.

```js
const value = 10;
{
  // console.log(value); // ReferenceError: the inner value is in its TDZ.
  const value = 20;
  console.log(value); // 20
}
```

The inner declaration shadows the outer variable throughout the block, including the part before initialization.

**Follow-up:** `typeof unknownName` returns `"undefined"` if the name is undeclared. But `typeof` on a binding in its TDZ throws. Declare variables before use so the execution order is clear.

## 9. What are global scope, function scope, and block scope?

**Interview answer:** Scope controls where a variable can be accessed. Global scope is shared across the relevant global environment. Function scope belongs to a function. Block scope belongs to a block such as an `if`, loop, or `{}` block.

```js
const appName = "Shop";
function show() {
  var message = "Hello"; // Function scope.
  if (true) {
    let count = 1; // Block scope.
    console.log(appName, message, count);
  }
  // count is unavailable here.
}
```

Inner scopes can access outer bindings. Outer scopes cannot access inner bindings. A local variable with the same name shadows an outer variable.

**Practical use:** Keep variables in the smallest useful scope. Modules give files their own scope and help avoid accidental global variables and naming conflicts.

## 10. What is a closure, and what are its practical use cases?

**Interview answer:** A closure is a function together with access to the variables from its surrounding lexical scope. It can keep using those variables after the outer function has returned.

```js
function createCounter() {
  let count = 0;
  return function increment() {
    count += 1;
    return count;
  };
}
const counter = createCounter();
counter(); // 1
counter(); // 2
```

Each call to `createCounter()` creates separate state. Useful cases include private state, memoization, debounce, event handlers, and configuring functions.

**Important:** Closures capture bindings, not a frozen copy of their values. If the captured binding changes, later calls see the change. A closure can also retain large objects in memory; remove unnecessary handlers and references when their work is finished.

## 11. What is lexical scope?

**Interview answer:** Lexical scope means a function's access to variables is based on where the function is defined in the source code, not where it is called.

```js
const name = "Outer";
function printName() { console.log(name); }

function run() {
  const name = "Inner";
  printName();
}
run(); // "Outer"
```

JavaScript looks for a variable in the current scope, then moves through enclosing scopes until it finds the binding or reaches the end.

**Connection to closures:** Lexical scope determines which outer variables a function can access. A closure preserves that access when the function is used later. Ordinary functions have lexical variable scope even though their `this` can depend on how they are called.

## 12. How does the `this` keyword behave in different contexts?

**Interview answer:** For a regular function, `this` usually depends on how the function is called. An arrow function takes `this` from its surrounding scope.

| Call/context | `this` |
| --- | --- |
| `obj.method()` | `obj` |
| Plain regular function call in strict mode | `undefined` |
| Plain regular function call in non-strict mode | Usually `globalThis` |
| `fn.call(obj)` / `fn.apply(obj)` | Explicitly supplied value, with non-strict conversion rules |
| Function created by `fn.bind(obj)` | Bound value for ordinary calls |
| `new Constructor()` | Newly created instance, unless the constructor returns another object |
| Arrow function | Inherited from its surrounding scope |
| Top-level ES module | `undefined` |

```js
const user = {
  name: "Sam",
  greet() { return this.name; },
};
user.greet(); // "Sam"
const greet = user.greet;
// greet(); // Loses the user receiver; throws in strict mode here.
const safeGreet = user.greet.bind(user);
safeGreet(); // "Sam"
```

**Important:** Passing a method as a callback can lose its receiver. In a DOM listener registered with a regular function, `this` is generally the element handling the listener; an arrow does not get that binding.

## 13. What are the differences between regular functions and arrow functions?

**Interview answer:** Regular functions can have a call-dependent `this` and their own `arguments`. Arrows inherit `this` and `arguments` from the surrounding scope. Arrows cannot be called with `new` and have no own `prototype` property for construction.

```js
const user = {
  name: "Sam",
  greet() {
    const readName = () => this.name;
    return readName();
  },
};
user.greet(); // "Sam"

const makeUser = name => ({ name }); // Parentheses return an object.
```

Use arrows for short callbacks and when you want to retain surrounding `this`. Use a regular method when it should operate on the object receiving the call.

**Mistake to avoid:** Defining an object method as an arrow and expecting `this` to refer to that object. Also, `call`, `apply`, and `bind` cannot change an arrow's `this`. Some regular function forms, such as object methods and async functions, are also not constructors.

## 14. What are the differences between `call()`, `apply()`, and `bind()`?

**Interview answer:** `call()` and `apply()` invoke a function immediately with a chosen `this`. `call()` takes separate arguments; `apply()` takes an array or array-like argument list. `bind()` returns a new function for later use.

```js
function greet(greeting, punctuation) {
  return `${greeting}, ${this.name}${punctuation}`;
}
const user = { name: "Sam" };
greet.call(user, "Hello", "!"); // "Hello, Sam!"
greet.apply(user, ["Hello", "!"]); // Same result.
const sayHello = greet.bind(user, "Hello");
sayHello("!"); // "Hello, Sam!"
```

`bind()` can also pre-fill arguments, which is called partial application.

**Practical issue:** Every call to `bind()` creates a different function. Save the bound function if you need to remove an event listener later. Calling `bind()` again will not produce the same callback identity.

## 15. What are higher-order functions and callbacks?

**Interview answer:** A higher-order function accepts another function, returns a function, or does both. A callback is a function passed to another function so it can be called as part of that operation.

```js
function calculate(a, b, operation) {
  return operation(a, b);
}
calculate(2, 3, (a, b) => a + b); // 5

function multiplyBy(factor) {
  return value => value * factor;
}
const double = multiplyBy(2);
double(4); // 8
```

Array methods such as `map()` are higher-order functions. Their callback normally runs synchronously. Timer and event callbacks run later.

**Mistake to avoid:** A callback is not automatically asynchronous. Its timing is decided by the function or API receiving it. Callback-heavy async flows can be harder to compose than promises.

## 16. What is currying, and when is it useful?

**Interview answer:** Currying changes a function that takes several arguments into a chain of functions that each take one argument. It is useful when we want to configure part of an operation and reuse it.

```js
const multiply = a => b => a * b;
multiply(2)(5); // 10
const double = multiply(2);
double(8); // 16

const hasRole = role => user => user.role === role;
const isAdmin = hasRole("admin");
[{ role: "admin" }, { role: "user" }].filter(isAdmin);
```

**Follow-up:** Currying and partial application are related but different. Currying changes the function into a one-argument chain. Partial application fixes some arguments and leaves the remaining arguments for later. Use either when it makes reuse clearer; avoid long function chains that are harder to read than a simple call.

## 17. What is the difference between a function declaration and a function expression?

**Interview answer:** A declaration defines a named function as a statement and is generally callable before its declaration. An expression produces a function value; its availability depends on the variable or place holding that value.

```js
add(1, 2); // 3
function add(a, b) { return a + b; }

const subtract = function (a, b) { return a - b; };
const multiply = (a, b) => a * b;
```

Before the `const` declarations run, accessing `subtract` or `multiply` throws because of the TDZ. A `var` expression would be `undefined` before assignment, so calling it would throw a TypeError.

**Practical use:** Declarations are convenient for named reusable operations. Expressions are useful for callbacks and conditional assignment. A named function expression can also improve debugging and support recursion using its internal name.

## 18. What are pure functions and side effects?

**Interview answer:** A pure function returns the same result for the same inputs and does not change anything outside itself. A side effect changes external state or interacts with the outside world.

```js
function add(a, b) { return a + b; } // Pure.

let total = 0;
function addToTotal(value) { total += value; } // Side effect.

function updateUser(user, name) {
  return { ...user, name }; // Does not mutate the input.
}
```

Side effects include changing an input object, writing to storage, making an API request, and updating the DOM. Depending on time or randomness also makes a function impure because identical inputs may produce different results.

**Practical use:** Keep calculations and transformations pure where possible, and handle side effects at clear boundaries. This makes code easier to test, reuse, and reason about. Applications still need side effects to do useful work.

## 19. What are the differences between shallow copy and deep copy?

**Interview answer:** A shallow copy creates a new outer object but shares nested objects. A deep copy also copies nested data, so changing copied nested objects does not change the original.

```js
const original = { address: { city: "Chennai" } };
const shallow = { ...original };
shallow.address.city = "Pune";
console.log(original.address.city); // "Pune"

const deep = structuredClone(original);
deep.address.city = "Delhi";
console.log(original.address.city); // "Pune"
```

`structuredClone()` supports many built-in data types and circular references, but cannot clone functions and does not preserve arbitrary custom class behavior. Object spread and `Object.assign()` are shallow.

**Mistake to avoid:** Using JSON stringify/parse as a general deep-copy solution. It loses or changes values such as `undefined` and dates, and throws for circular structures and `BigInt`. Often a targeted immutable update is better than copying an entire large object.

## 20. How do spread syntax, rest parameters, and destructuring work?

**Interview answer:** Spread expands values, rest collects remaining values, and destructuring extracts values into variables. They look related but serve different purposes.

```js
const numbers = [1, 2, 3];
const copy = [...numbers]; // Spread.
Math.max(...numbers); // 3

function sum(...values) { // Rest parameter.
  return values.reduce((total, value) => total + value, 0);
}

const [first, ...remaining] = numbers;
const { name: userName, age = 18 } = { name: "Sam" };
const { password, ...safeUser } = { name: "Sam", password: "secret" };
```

Array spread needs an iterable; object spread copies own enumerable properties. Rest parameters must come last and produce a real array. Destructuring defaults apply only to `undefined`, not `null`.

**Important:** Spread does not deep-copy nested data. Removing one field using object rest is convenient but does not replace careful validation of data sent to clients.

## 21. What are the differences between `map()`, `filter()`, `reduce()`, and `forEach()`?

**Interview answer:** `map()` transforms items; `filter()` selects items; `reduce()` combines items into one result; `forEach()` runs an action for each item and returns `undefined`.

```js
const values = [1, 2, 3];
values.map(n => n * 2); // [2, 4, 6]
values.filter(n => n > 1); // [2, 3]
values.reduce((sum, n) => sum + n, 0); // 6
values.forEach(n => console.log(n)); // Return value: undefined.
```

`map()` preserves array length, including holes in sparse arrays. `filter()` can return fewer items. A reducer can return a number, object, array, or other result.

**Mistakes to avoid:** Forgetting `return` in a block-bodied `map()` callback; using `map()` only for side effects; and using `forEach(async ...)` expecting it to wait. These methods do not inherently mutate the source, but their callbacks can.

## 22. What are the differences between `find()`, `findIndex()`, and `filter()`?

**Interview answer:** `find()` returns the first matching value, `findIndex()` returns its index, and `filter()` returns an array of all matching values.

```js
const users = [{ id: 1 }, { id: 2 }, { id: 2 }];
users.find(user => user.id === 2); // First object with id 2.
users.findIndex(user => user.id === 2); // 1
users.filter(user => user.id === 2); // Both matching objects.
```

If there is no match, `find()` returns `undefined`, `findIndex()` returns `-1`, and `filter()` returns `[]`. `find()` and `findIndex()` stop at the first match; `filter()` checks the full array.

**Mistake to avoid:** Testing `if (index)` after `findIndex()`: index `0` is falsy and `-1` is truthy. Use `index !== -1`. Finding an actual `undefined` value also returns `undefined`, so use an index when that distinction matters.

## 23. What are the differences between `slice()` and `splice()`?

**Interview answer:** `slice()` returns a shallow copy of part of an array without changing it. `splice()` changes the original array by removing, inserting, or replacing items.

```js
const values = [10, 20, 30, 40];
values.slice(1, 3); // [20, 30]; end index is excluded.
console.log(values); // [10, 20, 30, 40]

values.splice(1, 2, 99); // Returns removed items: [20, 30].
console.log(values); // [10, 99, 40]
```

`slice(start, end)` uses an end index. `splice(start, deleteCount, ...items)` uses a count of items to delete. Both support negative start positions counted from the end.

**Practical use:** Use `slice()` when you need part of the data and must preserve the input. Use `splice()` for deliberate in-place updates. `toSpliced()` provides a copying alternative to `splice()` in environments that support it.

## 24. How does `sort()` work, and how do you correctly sort numbers?

**Interview answer:** `sort()` mutates an array. Without a comparator, it compares values as strings. For numbers, pass a comparator such as `(a, b) => a - b`.

```js
[10, 2, 1].sort(); // [1, 10, 2]
[10, 2, 1].sort((a, b) => a - b); // [1, 2, 10]
[10, 2, 1].sort((a, b) => b - a); // [10, 2, 1]

const sortedUsers = [...users].sort((a, b) => a.age - b.age);
// users must be an existing array of objects with numeric ages.
```

A negative comparator result puts `a` before `b`; a positive result puts it after; zero means equal for sorting. Modern JavaScript requires stable sorting, so items that compare equal keep their original relative order.

**Mistake to avoid:** Returning only `true` or `false` from the comparator. Use a consistent comparator. `toSorted()` returns a sorted copy; exact sort complexity depends on the engine.

## 25. Which common array methods mutate the original array?

**Interview answer:** Common mutating methods are `push`, `pop`, `shift`, `unshift`, `splice`, `sort`, `reverse`, `fill`, and `copyWithin`. Methods such as `map`, `filter`, `slice`, and `concat` create new arrays.

| Operation | Mutating method | Copying alternative |
| --- | --- | --- |
| Sort | `sort()` | `toSorted()` or `[...arr].sort()` |
| Reverse | `reverse()` | `toReversed()` or `[...arr].reverse()` |
| Insert/remove | `splice()` | `toSpliced()` |
| Replace at index | `arr[i] = value` | `arr.with(i, value)` |

**Important:** A new outer array can still share object elements with the original. `map(user => { user.active = true; return user; })` mutates those objects even though `map()` returns a new array. To avoid that, return `{ ...user, active: true }`.

Check runtime support before using newer copying methods in older browsers.

## 26. What are the differences between `some()` and `every()`?

**Interview answer:** `some()` checks whether at least one item passes a condition. `every()` checks whether all items pass. Both return a Boolean and stop once the answer is known.

```js
[1, 2, 3].some(n => n > 2); // true
[1, 2, 3].every(n => n > 0); // true
[1, 2, 3].every(n => n > 2); // false
[].some(() => true); // false
[].every(() => false); // true
```

**Practical use:** `some()` can check whether a cart contains an unavailable product. `every()` can check whether all form fields are valid.

**Follow-up:** An empty array passes `every()` because there is no item that fails. If a rule also requires at least one item, use `items.length > 0 && items.every(...)`.

## 27. What are the differences between `for...in` and `for...of`?

**Interview answer:** `for...in` visits enumerable string property keys, including inherited ones. `for...of` visits values produced by an iterable, such as an array, string, map, or set.

```js
const values = ["a", "b"];
for (const key in values) console.log(key); // "0", "1"
for (const value of values) console.log(value); // "a", "b"

const user = { name: "Sam", age: 25 };
for (const [key, value] of Object.entries(user)) {
  console.log(key, value);
}
```

Plain objects are not iterable by default. Use `Object.keys()`, `Object.values()`, or `Object.entries()` to iterate their own enumerable string properties.

**Mistake to avoid:** Using `for...in` for array values; it can include extra and inherited properties. If using it for an object and wanting only own properties, check `Object.hasOwn(object, key)`.

## 28. What are the differences between objects, `Map`, and `Set`?

**Interview answer:** Objects store named properties, maps store key-value entries with keys of any type, and sets store unique values.

| Feature | Object | Map | Set |
| --- | --- | --- | --- |
| Main use | Records and structured data | Key-value lookup | Unique values / membership |
| Keys | Strings or symbols | Any value | No separate keys |
| Size | Count appropriate own keys | `.size` | `.size` |
| Directly iterable | No, normally | Yes | Yes |

```js
const key = { id: 1 };
const cache = new Map();
cache.set(key, "result");
cache.get(key); // "result"
cache.get({ id: 1 }); // undefined: different object identity.

const unique = [...new Set([1, 1, 2])]; // [1, 2]
```

Maps and sets preserve insertion order. Their equality treats `NaN` as equal to `NaN`, and object values by identity. Objects have defined property ordering too, but integer-like keys have special ordering. Use `Object.create(null)` when you need an object dictionary without an inherited prototype.

## 29. What are prototypes and prototypal inheritance?

**Interview answer:** An object can have a link to another object called its prototype. When a property is not found on the object itself, JavaScript searches its prototype chain. This allows objects to share methods.

```js
const animal = { speak() { return "sound"; } };
const dog = Object.create(animal);
dog.name = "Buddy";
dog.speak(); // "sound": found on animal.
Object.hasOwn(dog, "speak"); // false
Object.getPrototypeOf(dog) === animal; // true
```

The chain ends at `null`. An own property can shadow an inherited property.

**Follow-up:** A constructor's `.prototype` property is used as the prototype of objects created with `new`. It is different from that function object's own prototype link. Classes use this inheritance mechanism too. Prefer `Object.getPrototypeOf()` and `Object.create()` over the legacy `__proto__` accessor.

## 30. What are the differences between `Object.freeze()` and `Object.seal()`?

**Interview answer:** Both prevent adding or removing own properties. `seal()` still allows changing existing writable data properties. `freeze()` also makes existing data properties non-writable. Both are shallow.

```js
const sealed = Object.seal({ count: 1 });
sealed.count = 2; // Allowed.

const frozen = Object.freeze({ address: { city: "Chennai" } });
frozen.address.city = "Pune"; // Allowed: nested object is not frozen.
// frozen.address = {}; // Fails; throws in strict mode.
```

`Object.preventExtensions()` only prevents new own properties; existing configurable properties may still be deleted. Seal also makes properties non-configurable. Freeze adds non-writability for data properties.

**Important:** These APIs do not provide general deep immutability. Freezing a `Map` does not prevent `map.set()`, and accessors may still have behavior that changes other state.

## 31. How do optional chaining (`?.`) and nullish coalescing (`??`) work?

**Interview answer:** Optional chaining safely stops a property access or call when the checked value is `null` or `undefined`. Nullish coalescing provides a default only for those two values.

```js
const user = { profile: null, score: 0 };
user.profile?.address?.city; // undefined
user.score ?? 100; // 0
user.score || 100; // 100

const onSave = undefined;
onSave?.(); // Does not call anything.
```

**Mistakes to avoid:** Optional chaining does not protect an undeclared root variable. `unknownUser?.name` still throws if `unknownUser` was never declared. Optional call also throws if a present value is not callable.

Keep the chain continuous: `(user.profile?.address).city` can throw because the later access is outside the optional chain. Do not use optional chaining to quietly hide data that should always exist; validate important API contracts.

## 32. What is an execution context, and how does the call stack work?

**Interview answer:** An execution context holds the information JavaScript needs to run code, such as variable bindings, the surrounding scope, and `this`. The call stack tracks active function calls.

```js
function first() { second(); }
function second() { third(); }
function third() { console.log("Done"); }
first();
```

`first` is pushed onto the stack, then `second`, then `third`. When `third` finishes, it is removed. The others finish in reverse order. This is last in, first out.

**Practical effect:** A long synchronous function keeps the stack busy and blocks other JavaScript callbacks on that thread. Unbounded recursion can overflow the stack. Async operations can finish elsewhere, but their JavaScript callbacks must wait until they can run on the thread.

## 33. How does the JavaScript event loop work?

**Interview answer:** The event loop coordinates running JavaScript with queued work from the host, such as browser events, timers, and completed requests. Synchronous code runs first. At microtask checkpoints, queued microtasks run before the next task.

```js
console.log("A");
setTimeout(() => console.log("B"), 0);
Promise.resolve().then(() => console.log("C"));
console.log("D");
// A, D, C, B
```

In a browser, a useful model is: run a task, drain microtasks, then allow rendering when the browser has a rendering opportunity. Rendering is not guaranteed after every task.

**Important:** `setTimeout(fn, 0)` does not mean “run immediately.” It schedules later work, with host timing rules and possible delays. A continuous stream of microtasks can delay timers and rendering. Node.js has additional event-loop phases, so avoid treating every environment as identical.

## 34. What are the differences between microtasks and macrotasks?

**Interview answer:** Promise reactions, `queueMicrotask()`, and async function continuations use microtasks. Timers and many browser events schedule tasks, often called macrotasks. Microtasks are drained at checkpoints before the next task runs.

```js
setTimeout(() => console.log("timer"), 0);
queueMicrotask(() => console.log("microtask"));
Promise.resolve().then(() => console.log("promise"));
console.log("sync");
// sync, microtask, promise, timer
```

Within that example, microtasks execute in the order they were queued. New microtasks queued while processing microtasks are also processed before moving on.

**Practical issue:** Recursively adding microtasks can starve other work. Use task-based yielding or move expensive computation to a worker when appropriate. `requestAnimationFrame()` is a rendering callback mechanism; do not describe it as an ordinary timer task.

## 35. What is a promise, and what are its states?

**Interview answer:** A promise represents the eventual result of an operation. Its states are pending, fulfilled with a value, and rejected with a reason. Once settled, its fulfilled or rejected result cannot change.

```js
const promise = new Promise((resolve, reject) => {
  const success = true;
  if (success) resolve("Done");
  else reject(new Error("Failed"));
});
promise.then(value => console.log(value));
```

The executor passed to `new Promise()` runs synchronously. Registered promise reactions run asynchronously as microtasks.

**Follow-up:** “Resolved” does not always mean “fulfilled.” A promise resolved with another pending promise adopts its eventual state and can remain pending. Creating a promise does not move CPU work to another thread, and promises have no general built-in cancellation mechanism.

## 36. How do promise chaining and error propagation work?

**Interview answer:** Every `.then()` returns a new promise. Returning a value passes it to the next handler. Returning a promise makes the chain wait for it. Throwing an error rejects the next promise, and the rejection moves through the chain until handled.

```js
Promise.resolve(2)
  .then(value => value * 3)
  .then(value => { throw new Error(`Failed at ${value}`); })
  .catch(error => {
    console.log(error.message);
    return 0; // Recovery: next handler receives 0.
  })
  .then(value => console.log(value));
```

**Mistake to avoid:** Starting an async operation inside `.then()` without returning it. The outer chain will not wait for that operation or receive its rejection.

`.finally()` is for cleanup and normally preserves the original result. If it throws or returns a rejecting promise, it changes the chain to a rejection. An error handler that throws continues the rejection instead of recovering.

## 37. How does `async/await` work, and how do you handle errors?

**Interview answer:** An `async` function always returns a promise. `await` pauses that function until a value or promise is ready, while allowing other work on the JavaScript thread. Use `try/catch` around awaited operations and `finally` for cleanup.

```js
async function loadUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    return await response.json();
  } catch (error) {
    console.error("Unable to load user", error);
    throw error; // Let the caller decide how to recover.
  }
}
```

Even an already fulfilled promise resumes the function asynchronously after `await`. Code before the first `await` runs synchronously.

**Important:** Within `try/catch`, `return await operation()` lets the local catch handle the operation's rejection. `return operation()` returns it without locally awaiting the rejection. Handle errors at a useful boundary and avoid logging the same failure at every layer.

## 38. What are the differences between the promise combination methods?

**Interview answer:** Choose the method based on whether you need every result, every outcome, the first settlement, or the first success.

| Method | Result | Failure behavior | Empty input |
| --- | --- | --- | --- |
| `Promise.all()` | All fulfilled values in input order | Rejects when one rejects | Fulfills with `[]` |
| `Promise.allSettled()` | Every outcome in input order | Input rejections become result entries | Fulfills with `[]` |
| `Promise.race()` | First settled outcome | Rejects if first settlement is a rejection | Stays pending |
| `Promise.any()` | First fulfilled value | Rejects with `AggregateError` if all reject | Rejects with `AggregateError` |

```js
const [user, orders] = await Promise.all([loadUser(), loadOrders()]);
const outcomes = await Promise.allSettled([saveProfile(), saveSettings()]);
// The functions above represent your application operations.
```

**Important:** These methods do not cancel the other operations when their returned promise settles. They coordinate operations you pass in; they do not create worker threads. Use `AbortController` or another API-specific mechanism when cancellation is needed.

## 39. What are the differences between sequential and parallel asynchronous execution?

**Interview answer:** Sequential execution waits for one operation before starting the next. Concurrent execution starts independent operations before waiting for their results, which can reduce total waiting time.

```js
// Sequential: needed when orders depend on the loaded user.
const user = await loadUser();
const orders = await loadOrders(user.id);

// Concurrent: use when both requests are independent.
const [products, categories] = await Promise.all([
  loadProducts(),
  loadCategories(),
]);
```

For independent waits of roughly 1 and 2 seconds, sequential execution takes roughly 3 seconds; concurrent execution takes roughly 2 seconds, plus overhead.

**Important:** Concurrent network requests are often called “parallel,” but this does not mean their JavaScript runs on multiple threads. For large batches, limit concurrency to avoid server limits and resource pressure. Use `for...of` with `await` for deliberate sequential processing; `forEach()` does not await async callbacks.

## 40. What are debounce and throttle, and when should you use each?

**Interview answer:** Debounce waits until calls stop for a chosen time before running. Throttle limits how often a function can run during repeated calls. Debounce suits search input; throttle suits scroll or resize work that should update regularly.

```js
// Trailing debounce: run after the last call has been quiet for delay ms.
function debounce(fn, delay) {
  let timer;
  function debounced(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  }
  debounced.cancel = () => clearTimeout(timer);
  return debounced;
}

// Leading throttle: run immediately, then ignore calls during the window.
function throttle(fn, interval) {
  let lastRun = -Infinity;
  return function (...args) {
    const now = performance.now();
    if (now - lastRun >= interval) {
      lastRun = now;
      return fn.apply(this, args);
    }
  };
}
```

**Tradeoff:** This throttle drops the final call if it arrives within the interval. Production versions may need trailing calls, cancellation, or flushing. Debouncing input does not by itself prevent stale network responses; handle request ordering too.

## 41. How do you cancel a `fetch()` request using `AbortController`?

**Interview answer:** Create an `AbortController`, pass its signal to `fetch()`, and call `abort()` when the request is no longer needed. Handle cancellation separately from real request failures.

```js
async function loadData(signal) {
  try {
    const response = await fetch("/api/data", { signal });
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    return await response.json();
  } catch (error) {
    if (signal.aborted) return; // Expected cancellation in this example.
    throw error;
  }
}

const controller = new AbortController();
const pending = loadData(controller.signal);
controller.abort();
await pending;
```

**Important:** An aborted signal stays aborted; create a new controller for a new request. Abort can also stop response body consumption. It does not guarantee the server stops processing or reverses a completed write. Decide whether cancellation should be ignored, returned as a separate outcome, or propagated according to your application's contract.

## 42. How do you handle HTTP errors, network failures, and stale API responses?

**Interview answer:** Check HTTP status explicitly, catch network and parsing errors, and make sure an older response cannot overwrite newer results. Cancellation and a request sequence check are useful together.

```js
let latestRequest = 0;
let controller;

async function search(query) {
  const requestId = ++latestRequest;
  controller?.abort();
  const current = new AbortController();
  controller = current;

  try {
    const response = await fetch(
      `/api/search?q=${encodeURIComponent(query)}`,
      { signal: current.signal },
    );
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    const data = await response.json();
    if (requestId === latestRequest) renderResults(data);
  } catch (error) {
    if (current.signal.aborted || requestId !== latestRequest) return;
    showError(error.message);
  }
}
// renderResults and showError are application UI functions.
```

`fetch()` usually fulfills for HTTP errors such as 404 and 500; it rejects for failures such as network errors and aborts. Invalid response JSON can reject separately. Guard loading/error state updates with the same request check.

**Production discussion:** Use clear loading, empty, success, and error states. Retry appropriate temporary failures with a limit and backoff. Avoid blindly retrying writes because that can create duplicate operations; use server-supported idempotency when needed.

## 43. What are event bubbling, event capturing, and event delegation?

**Interview answer:** Capturing moves through ancestors toward the target. The target receives the event. Bubbling then moves through ancestors away from the target for events that bubble. Delegation handles events on a parent instead of attaching a listener to each child.

```js
const list = document.querySelector("#list");
list.addEventListener("click", event => {
  if (!(event.target instanceof Element)) return;
  const button = event.target.closest("button[data-id]");
  if (!button || !list.contains(button)) return;
  console.log(button.dataset.id);
});

list.addEventListener("click", () => console.log("capture"), {
  capture: true,
});
```

Delegation works for children added later and reduces listener setup. `event.target` is the event's target; `event.currentTarget` is the element whose listener is currently running.

**Follow-up:** Not all events bubble. For delegated focus handling, `focusin` is useful, or use capturing for `focus`. Shadow DOM can retarget events, so event paths can matter in component systems.

## 44. What are the differences between `preventDefault()` and `stopPropagation()`?

**Interview answer:** `preventDefault()` asks the browser not to perform the event's default action. `stopPropagation()` prevents the event from continuing along its propagation path. They solve different problems.

```js
form.addEventListener("submit", event => {
  event.preventDefault(); // Prevent normal form submission/navigation.
  saveForm();
});

button.addEventListener("click", event => {
  event.stopPropagation(); // Ancestor click handlers will not receive it.
});
```

Stopping propagation does not prevent a link from navigating. Preventing navigation does not stop a parent click handler.

**Follow-up:** `stopPropagation()` does not stop other listeners on the same element. `stopImmediatePropagation()` also blocks subsequent listeners there. Default prevention only works for cancelable events, and a passive listener cannot prevent default. Use propagation blocking carefully because it can break delegated handlers and shared UI behavior.

## 45. What causes memory leaks in JavaScript, and how can you prevent them?

**Interview answer:** A memory leak happens when data stays reachable even though the application no longer needs it. Common causes include forgotten listeners, active timers, unbounded caches, subscriptions, and retained DOM nodes.

```js
function watchResize() {
  const onResize = () => console.log(window.innerWidth);
  window.addEventListener("resize", onResize);
  const timer = setInterval(() => console.log("tick"), 1000);

  return function cleanup() {
    window.removeEventListener("resize", onResize);
    clearInterval(timer);
  };
}
const cleanup = watchResize();
// Call cleanup() when the feature is removed.
```

Garbage collection removes unreachable data. It does not know which reachable data your business logic no longer needs. Closures and cycles are not automatically leaks; unreachable cycles can be collected.

**Practical debugging:** Repeat an action, take heap snapshots, compare retained objects, and inspect what holds references. Clean up subscriptions, bound callbacks, observers, and timers; limit cache size. A detached DOM node leaks only if something still retains it.

## 46. How would you implement memoization using a closure?

**Interview answer:** Memoization stores previous results so repeated calls with the same input can reuse them. A closure keeps the cache private. It is most useful for expensive pure functions with repeated inputs.

```js
function memoizeOne(fn) {
  const cache = new Map();
  return function (input) {
    if (cache.has(input)) return cache.get(input);
    const result = fn.call(this, input);
    cache.set(input, result);
    return result;
  };
}

const square = memoizeOne(n => n * n);
square(5); // Computes 25.
square(5); // Reuses 25.
```

**Complexity:** Cache lookup is typically constant time on average; memory grows with distinct inputs. The language does not promise a particular map implementation.

**Limits:** This version supports one argument and assumes the result depends only on that argument, not on `this`. Object inputs are keyed by identity, and changing an object can make the cached result stale. For production, consider size limits, eviction, multiple-argument keys, and removing cached rejected promises. Avoid using JSON serialization as a universal key strategy.

## 47. How would you implement a simplified version of `Array.prototype.map()`?

**Interview answer:** Create an output array, call the callback for each present source index, and store the result at the same index. Preserve holes and the initial length.

```js
function mapArray(array, callback, thisArg) {
  if (!Array.isArray(array)) throw new TypeError("Expected an array");
  if (typeof callback !== "function") {
    throw new TypeError("Expected a callback");
  }

  const length = array.length;
  const result = new Array(length);
  for (let i = 0; i < length; i++) {
    if (i in array) {
      result[i] = callback.call(thisArg, array[i], i, array);
    }
  }
  return result;
}

mapArray([1, 2, 3], n => n * 2); // [2, 4, 6]
mapArray([1, , 3], n => n * 2); // [2, <hole>, 6]
```

**Complexity:** O(n) time excluding callback cost, and O(n) output space.

**Limits:** This is a simplified helper for arrays, not a complete specification-compatible polyfill. Native `map()` also handles array-like receivers and subclass construction rules. Do not modify built-in prototypes just to demonstrate this in an application.

## 48. How would you flatten a nested array without using `flat()`?

**Interview answer:** Visit each item. If it is an array, visit its items recursively; otherwise add it to the result.

```js
function flatten(array) {
  const result = [];
  function visit(items) {
    for (let i = 0; i < items.length; i++) {
      if (!(i in items)) continue; // Skip sparse holes.
      const item = items[i];
      if (Array.isArray(item)) visit(item);
      else result.push(item);
    }
  }
  visit(array);
  return result;
}

flatten([1, [2, [3]], 4]); // [1, 2, 3, 4]
flatten([]); // []
```

**Complexity:** O(n) time for visited entries and O(n) output space, plus O(d) recursion space for depth `d`. This fully flattens finite, acyclic nested arrays.

**Follow-up:** Very deep input can overflow the call stack. An explicit stack avoids recursion. Cyclic arrays need a defined policy, such as detection and rejection. Ask whether the interviewer wants full flattening or a fixed depth.

## 49. How would you solve Two Sum efficiently using a `Map`?

**Interview answer:** While scanning the array, look for the complement `target - current` among values already seen. If found, return the two indices. Otherwise store the current value and index.

```js
function twoSum(numbers, target) {
  const seen = new Map();
  for (let i = 0; i < numbers.length; i++) {
    const needed = target - numbers[i];
    if (seen.has(needed)) return [seen.get(needed), i];
    seen.set(numbers[i], i);
  }
  return []; // Agreed no-result contract.
}

twoSum([2, 7, 11, 15], 9); // [0, 1]
twoSum([3, 3], 6); // [0, 1]
```

**Complexity:** Expected O(n) time with typical map implementations and O(n) extra space, compared with O(n²) for checking every pair.

**Why check before storing?** It prevents using the current item twice and still handles duplicate values. Clarify whether the task requires indices or values, one pair or every pair, and what to return when there is no answer. Assume suitable finite numeric inputs unless told otherwise.

## 50. How would you find the longest substring without repeating characters?

**Interview answer:** Use a sliding window. Store the last index of each character. If the current character already appears inside the window, move the left boundary past its previous position.

```js
function longestUniqueLength(text) {
  const lastSeen = new Map();
  let left = 0;
  let right = 0;
  let best = 0;

  for (const character of text) {
    if (lastSeen.has(character)) {
      left = Math.max(left, lastSeen.get(character) + 1);
    }
    lastSeen.set(character, right);
    best = Math.max(best, right - left + 1);
    right++;
  }
  return best;
}

longestUniqueLength("abcabcbb"); // 3
longestUniqueLength("bbbbb"); // 1
longestUniqueLength("abba"); // 2
longestUniqueLength(""); // 0
```

**Complexity:** O(n) expected time and O(k) space, where `k` is the number of distinct characters seen. `Math.max` prevents the left boundary from moving backward, which is essential for `"abba"`.

**Follow-up:** This version counts Unicode code points using `for...of`, not UTF-16 code units. A visible character can contain multiple code points; user-facing text may require grapheme segmentation. To return the substring, track the best start and work with a code-point array so slicing uses matching indices.

---

# Additional Important Questions

The following topics help move beyond definitions into the reasoning expected from a developer with 4–5 years of experience.

## 51. How do ES modules work, and how are they different from CommonJS?

**Interview answer:** ES modules use `import` and `export`. Imports are live, read-only bindings to exported values. CommonJS uses `require()` and `module.exports`, and loading is generally synchronous. The exact behavior also depends on the runtime.

```js
// counter.js
export let count = 0;
export function increment() { count++; }

// main.js
import { count, increment } from "./counter.js";
increment();
console.log(count); // 1
// count = 10; // Cannot reassign an imported binding.
```

ES modules run in strict mode and have module scope. Static imports help tools analyze dependencies and remove unused code when safe. `import()` loads a module dynamically and returns a promise.

**Follow-up:** Circular dependencies can expose bindings before they are initialized. Prefer clear dependency direction rather than relying on complicated initialization order.

## 52. What happens when you use `new`, and how do classes work?

**Interview answer:** `new` creates an object, links it to the constructor's prototype, runs the constructor with that object as `this`, and normally returns the object. An explicitly returned object can replace it.

```js
class User {
  constructor(name) { this.name = name; }
  greet() { return `Hello ${this.name}`; }
  static createGuest() { return new User("Guest"); }
}
const user = new User("Sam");
user.greet(); // "Hello Sam"
```

Class methods are shared through the prototype. Static methods belong to the class constructor. Class fields are own instance properties. Classes have additional rules beyond constructor-function syntax: their bodies are strict, and they cannot be called without `new`.

**Follow-up:** In a derived constructor, call `super()` before using `this`. Private fields such as `#balance` are language-enforced private state. Prefer composition when inheritance would create tightly connected classes.

## 53. What are property descriptors, getters, and setters?

**Interview answer:** A property descriptor controls whether a property can be written, enumerated, or reconfigured. A property can hold a value, or use getter/setter functions for reading and writing.

```js
const account = { first: "Sam", last: "Lee" };
Object.defineProperty(account, "fullName", {
  get() { return `${this.first} ${this.last}`; },
  enumerable: true,
  configurable: true,
});
account.fullName; // "Sam Lee"
```

Data descriptors use `value` and `writable`; accessor descriptors use `get` and `set`. You cannot combine both forms on the same property. Flags omitted from a new `Object.defineProperty()` definition default to `false`.

**Practical issue:** A getter runs code when the property is read. Avoid expensive or surprising side effects behind ordinary-looking property access. Object spread copies the value produced by an enumerable getter, not its descriptor.

## 54. How do `Object.keys()`, `values()`, and `entries()` differ?

**Interview answer:** They return an object's own enumerable string keys, values, or key-value pairs. They do not include inherited properties or symbol keys.

```js
const user = { name: "Sam", age: 25 };
Object.keys(user); // ["name", "age"]
Object.values(user); // ["Sam", 25]
Object.entries(user); // [["name", "Sam"], ["age", 25]]
Object.fromEntries([["name", "Sam"]]); // { name: "Sam" }
```

Use `Object.hasOwn(obj, key)` to check ownership. The `in` operator checks both own and inherited properties. `Reflect.ownKeys()` includes own string and symbol keys, including non-enumerable ones.

**Mistake to avoid:** Calling `obj.hasOwnProperty(key)` blindly: the object might override that name or have no prototype.

## 55. What are `WeakMap` and `WeakSet`, and when are they useful?

**Interview answer:** Weak collections do not keep supported keys or values alive just because they are stored in the collection. They are useful for metadata tied to an object's lifetime.

```js
const metadata = new WeakMap();
let element = document.createElement("div");
metadata.set(element, { visited: true });
element = null;
// If nothing else retains the element, it can be collected.
```

`WeakMap` stores key-value pairs; `WeakSet` stores membership. Objects are the common weak keys/values; modern JavaScript also permits non-registered symbols. Unlike `Map` and `Set`, weak collections have no general iteration or `.size`, because collection timing must not be exposed through enumeration.

**Important:** Garbage collection is not immediate or predictable. Use explicit cleanup for timers and subscriptions; weak collections are not a general replacement for resource management.

## 56. How do iterables, iterators, and generators work?

**Interview answer:** An iterable provides `Symbol.iterator`, which returns an iterator. An iterator's `next()` returns `{ value, done }`. A generator is a convenient way to produce a sequence while pausing between values.

```js
function* range(start, end) {
  for (let value = start; value <= end; value++) yield value;
}
const iterator = range(1, 3);
iterator.next(); // { value: 1, done: false }
[...range(1, 3)]; // [1, 2, 3]
```

Calling a generator function creates the generator without immediately running its body. `next()` starts or resumes it. Arrays, strings, maps, and sets are iterable; plain objects normally are not.

**Practical use:** Lazy sequences can avoid building large intermediate arrays. Async iterables work with `for await...of` for streams or sequences that produce values asynchronously.

## 57. What are strict mode and accidental global variables?

**Interview answer:** Strict mode makes some mistakes throw errors instead of being silently accepted. For example, assigning to an undeclared variable throws, and a plain regular function call gets `undefined` as `this`.

```js
"use strict";
// total = 10; // ReferenceError if total has no declaration.
function checkThis() { return this; }
checkThis(); // undefined
```

ES modules and class bodies are already strict. Strict mode also rejects certain invalid assignments and syntax that non-strict code may allow.

**Practical use:** Use modules, declare every variable, and use linting to catch mistakes early. A non-strict accidental global can create shared state, naming collisions, and retained data that is difficult to debug.

## 58. Why is `0.1 + 0.2` not exactly `0.3`, and how should you handle numbers?

**Interview answer:** JavaScript `Number` uses binary floating-point representation. Some decimal fractions cannot be represented exactly, so arithmetic can produce small rounding differences.

```js
0.1 + 0.2; // 0.30000000000000004
Number.isNaN(NaN); // true
Number.isNaN("hello"); // false
Number.isFinite(Infinity); // false
Number.isSafeInteger(Number.MAX_SAFE_INTEGER); // true
```

For approximate measurements, compare using a tolerance chosen for the size of the numbers and the problem. `Number.EPSILON` alone is not a universal tolerance. `toFixed()` produces a formatted string; it does not make arithmetic exact.

**Practical use:** For money, use a clear rounding policy and appropriate integer minor units or a decimal library. `BigInt` stores integers beyond the safe integer range, but it cannot be mixed directly with `Number` in arithmetic and does not represent decimal fractions.

## 59. What are sparse arrays, and why do their methods behave differently?

**Interview answer:** A sparse array has missing properties at some indices. A hole is different from an index containing `undefined`.

```js
const sparse = new Array(3);
sparse.length; // 3
0 in sparse; // false

sparse.map(() => 1); // Still has three holes.
Array.from(sparse, () => 1); // [1, 1, 1]
[...sparse]; // [undefined, undefined, undefined]
```

Several methods such as `map()` and `forEach()` skip absent indices. Array iteration with `for...of` produces `undefined` for holes. Methods such as `find()` visit indices even when the entry is absent.

**Mistake to avoid:** `delete arr[0]` leaves a hole and does not reduce length. Use `splice()` when you intend to remove and shift an item. Prefer dense arrays unless there is a specific reason otherwise.

## 60. How would you group, count, and remove duplicates from data?

**Interview answer:** Choose a key that represents equality, then use a map or set to track it. For grouping and counting, make one pass over the data.

```js
function groupBy(items, keyFn) {
  const groups = new Map();
  for (const item of items) {
    const key = keyFn(item);
    if (!groups.has(key)) groups.set(key, []);
    groups.get(key).push(item);
  }
  return groups;
}

function uniqueById(items) {
  const seen = new Set();
  return items.filter(item => {
    if (seen.has(item.id)) return false;
    seen.add(item.id);
    return true;
  });
}
```

Both use expected O(n) time and O(n) extra space in typical implementations. `uniqueById()` keeps the first item for each ID. Clarify first versus last, ordering, and how missing IDs should behave. `new Set(objects)` removes repeated references, not separate objects with matching contents.

## 61. What is a race condition in asynchronous JavaScript?

**Interview answer:** A race condition occurs when correctness depends on the timing of competing operations. JavaScript can have async races even when callbacks run on a single thread.

Example: a search for `"ja"` starts, then a search for `"javascript"` starts. The second request finishes first. If the older response arrives later and updates the screen, the user sees wrong results.

Use sequence numbers, cancellation, explicit queues, or server version checks according to the problem. See question 42 for a request sequence implementation.

**Important:** Preventing stale UI updates does not prevent duplicate server writes. For writes, discuss idempotency keys, transactions, or optimistic concurrency with the backend. Do not assume frontend request ordering alone protects shared server data.

## 62. How do you control concurrency for many async operations?

**Interview answer:** Start only a limited number of operations at once. As each finishes, start another. This balances speed with resource and API limits.

```js
async function mapLimit(items, limit, task) {
  if (!Number.isInteger(limit) || limit < 1) {
    throw new RangeError("limit must be a positive integer");
  }
  const results = new Array(items.length);
  let nextIndex = 0;

  async function worker() {
    while (nextIndex < items.length) {
      const index = nextIndex++;
      results[index] = await task(items[index], index);
    }
  }

  await Promise.all(
    Array.from({ length: Math.min(limit, items.length) }, () => worker()),
  );
  return results;
}
```

This preserves input result order and limits in-flight tasks. The shared index increment happens synchronously before each `await`.

**Limit:** If a task rejects, the returned promise rejects, but other workers keep running and may start more work. Production code may need a stop flag, cancellation, or per-item outcome collection. A concurrency limit is different from a requests-per-second rate limit.

## 63. How would you implement retry and timeout behavior?

**Interview answer:** Retry only failures likely to be temporary, use a bounded attempt count, and increase the delay between attempts. A timeout should cancel the underlying operation when the API supports it.

```js
async function fetchWithTimeout(url, timeoutMs) {
  const controller = new AbortController();
  const timer = setTimeout(() => controller.abort(), timeoutMs);
  try {
    const response = await fetch(url, { signal: controller.signal });
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    return await response.json();
  } finally {
    clearTimeout(timer);
  }
}
```

A timeout implemented only with `Promise.race()` does not cancel a losing request. A timer also cannot interrupt synchronous JavaScript that is blocking the event loop.

**Retry discussion:** Set a maximum number of attempts, use backoff with jitter, respect server retry guidance, and stop after cancellation. Do not retry validation failures or unsafe writes blindly. Decide whether the timeout covers the entire operation or each attempt separately.

## 64. How do you keep the browser responsive during expensive work?

**Interview answer:** Long synchronous work blocks input handling and rendering. Reduce unnecessary work, split large work into smaller chunks, or use a Web Worker for suitable CPU-heavy tasks.

`requestAnimationFrame()` helps coordinate visual updates before a rendering opportunity. It is not a solution for performing a huge calculation without blocking. `setTimeout()` can yield between chunks, but scheduling is not exact.

**Web Worker tradeoff:** Workers run JavaScript on another thread, but cannot directly manipulate the page DOM. Messages usually use structured cloning; transferable buffers can avoid copies for supported data. Communication overhead means a worker may not help for tiny jobs.

**Practical answer:** Measure first. Inspect long tasks and repeated work, choose an approach, and check whether interaction improves afterward.

## 65. What are layout, paint, and common DOM performance mistakes?

**Interview answer:** The browser calculates element sizes and positions during layout, draws pixels during paint, and combines layers during compositing. JavaScript changes can trigger some of this work.

```js
// Read once, then write. Avoid repeating layout reads after each write.
const width = container.offsetWidth;
for (const item of items) item.style.width = `${width}px`;
```

Repeatedly alternating DOM writes and layout reads can force repeated synchronous layout. Batch reads before writes where possible. Reduce unnecessary DOM nodes, use list virtualization for very large lists, and avoid updating unchanged content.

**Follow-up:** `transform` and `opacity` can often animate without repeated layout, but actual behavior depends on the page and browser. Use performance tools to confirm rather than assuming every CSS property has the same cost.

## 66. What are cookies, `localStorage`, `sessionStorage`, and IndexedDB?

**Interview answer:** Cookies can be sent with matching HTTP requests. `localStorage` persists key-value strings; `sessionStorage` is scoped to an origin and tab/page session. IndexedDB stores larger structured data asynchronously.

| Storage | Common use | Important point |
| --- | --- | --- |
| Cookie | Server session information | Can use `HttpOnly`, `Secure`, and `SameSite` attributes |
| `localStorage` | Small saved preferences | Synchronous and readable by same-origin JavaScript |
| `sessionStorage` | Temporary tab state | Synchronous; normally survives reloads in that tab |
| IndexedDB | Offline data and larger records | Async API with transactions |

**Important:** Storage access can fail because of browser policy, quota, or other conditions. Handle errors. Browser persistence is not a guarantee that data lasts forever. A successful XSS attack can read JavaScript-accessible secrets, so do not treat local storage as a secure vault.

## 67. What is CORS, and why does a browser block some requests?

**Interview answer:** CORS is a browser mechanism that lets a server say which other origins may read its responses. An origin is the combination of scheme, hostname, and port.

Some cross-origin requests require an OPTIONS preflight before the browser sends the intended request. The server must return appropriate CORS headers. Credentialed requests require explicit origin permission and appropriate credential settings; a wildcard origin is not allowed for credentialed response access.

**Mistake to avoid:** Using `mode: "no-cors"` as a fix. It usually gives an opaque response whose contents your JavaScript cannot read. Fix the server configuration or use an authorized backend proxy.

CORS controls browser response access; it is not authentication and does not stop non-browser clients. Some cross-origin requests can still be sent even when JavaScript cannot read the response.

## 68. What is XSS, and how can JavaScript code avoid it?

**Interview answer:** Cross-site scripting happens when attacker-controlled content runs as code in a page. Avoid inserting untrusted content as HTML or executable code.

```js
message.textContent = userInput; // Treats the input as text.
// message.innerHTML = userInput; // Dangerous without appropriate handling.
```

Use safe text APIs, context-appropriate escaping, and a trusted sanitizer when rich HTML is required. Avoid `eval()` and the `Function` constructor for untrusted input. Framework escaping helps, but raw HTML escape hatches can bypass it.

**Follow-up:** A Content Security Policy adds protection but does not replace safe coding. Validate URLs before using them as navigation targets. Discuss CSRF separately: it involves unwanted authenticated requests, not necessarily script injection.

## 69. How do you handle errors well in application code?

**Interview answer:** Throw meaningful errors, handle them where a useful decision can be made, preserve details for debugging, and show users a clear message. Do not silently swallow unexpected failures.

```js
async function saveOrder(order) {
  try {
    return await sendOrder(order);
  } catch (cause) {
    throw new Error("Unable to save order", { cause });
  }
}
```

Distinguish expected validation failures, cancellation, network problems, and programming bugs. Use `finally` for cleanup, but avoid returning from it because that can override an earlier return or error.

**Follow-up:** A surrounding synchronous `try/catch` cannot catch an error thrown later by a timer callback. Promise rejections must be awaited or handled. Global error handlers are useful for reporting; they do not replace local recovery.

## 70. How would you test and debug JavaScript code?

**Interview answer:** Start with the expected behavior and reproduce the issue with the smallest useful input. Test normal cases, boundary cases, and failure paths. Use breakpoints and inspect values rather than guessing.

For the coding tasks above, check:

- Two Sum: duplicates, no pair, negative values, and preventing reuse of one index.
- Longest substring: empty input, all duplicates, `"abba"`, and the chosen Unicode definition.
- Map helper: empty arrays, holes, callback arguments, and callback failures.
- Debounce: repeated calls, preserved `this`, latest arguments, and cancellation.
- Async UI: slow older response, HTTP failure, network failure, and cancellation.

Use unit tests for isolated logic, integration tests for boundaries, and a few end-to-end tests for key user flows. Fake timers can make timing tests predictable. Profile performance and memory with browser tools when the issue is about speed or retained data.

## 71. How do you explain time and space complexity?

**Interview answer:** Time complexity describes how work grows as input grows. Space complexity describes how extra memory grows. Explain the operations that cause the growth instead of only giving a label.

- One pass over `n` items: O(n).
- Every pair of items: O(n²).
- Binary search on sorted data: O(log n).
- Divide-and-combine comparison sorting: commonly O(n log n), depending on the algorithm.
- A lookup map with up to `n` entries: O(n) extra space.

**Important:** Callback cost matters. `map()` is not O(n) overall if each callback scans another length-n array. Avoid repeated array spreading inside a reducer when it copies a growing result every time; that can make an apparently simple transformation quadratic.

Big-O describes growth, not exact speed. Constants, data size, engine behavior, and allocation also affect real performance.

## 72. How do you choose mutation versus immutable updates?

**Interview answer:** Mutation changes existing data. An immutable update creates changed data while preserving the old value. I choose based on ownership, state management, performance, and whether other code shares the data.

```js
const updated = {
  ...user,
  address: { ...user.address, city: "Pune" },
};
```

This copies the path being changed while sharing unchanged data. It is often more useful than deep-cloning everything. Immutable updates help systems that detect changes using reference equality and make previous state easier to inspect.

**Tradeoff:** Copying has a cost. Local mutation inside a function can be perfectly reasonable if it does not change shared inputs. Be explicit about who owns the data and which references are shared.

## 73. What output questions should you be able to explain?

Explain the rule before giving the output.

```js
// 1. Shared var binding versus separate let loop bindings.
for (var i = 0; i < 3; i++) setTimeout(() => console.log(i), 0);
// 3, 3, 3
for (let j = 0; j < 3; j++) setTimeout(() => console.log(j), 0);
// 0, 1, 2

// 2. Async function execution order.
async function run() {
  console.log("A");
  await Promise.resolve();
  console.log("B");
}
console.log("C");
run();
console.log("D");
// C, A, D, B for this isolated example.

// 3. Object identity and shared nested state.
const a = { nested: { count: 1 } };
const b = { ...a };
b.nested.count++;
console.log(a.nested.count, a === b); // 2, false

// 4. Missing callback return.
[1, 2].map(value => { value * 2; }); // [undefined, undefined]
```

Run these as separate examples. If you run them together, previously scheduled timers and microtasks also affect the combined output.

## 74. Which additional coding exercises should you practice?

Practice writing and explaining these without copying a solution:

1. Group records by a property and count occurrences using `Map`.
2. Remove duplicate objects by ID while keeping first or last occurrences.
3. Merge sorted arrays and explain time and space costs.
4. Check balanced brackets using a stack.
5. Implement binary search and handle empty input.
6. Implement an event emitter with `on`, `off`, and `emit`.
7. Implement an LRU cache using map ordering or a map plus linked list.
8. Implement a promise-based delay and a bounded retry helper.
9. Implement a small `Promise.all()` helper that preserves result order.
10. Build a search input with debounce, cancellation, and stale-response protection.

For every exercise, state the input contract, explain the approach, write it, test boundaries, and discuss complexity. A correct explanation and working edge cases matter more than a clever one-line answer.

## 75. What should a developer with 4–5 years of experience explain beyond syntax?

**Interview answer:** I should explain why I chose an approach, how it behaves when something fails, how I tested it, and what tradeoffs it has. I should connect language knowledge to real product behavior.

Prepare examples from your actual work for:

- A bug you reproduced and fixed, including the root cause.
- An API integration with loading, cancellation, and failure handling.
- A performance problem you measured and improved.
- A state or component design that reduced complexity.
- A difficult code review decision and the tradeoff you discussed.
- A production issue where you improved tests or monitoring afterward.

Do not invent project results. Explain your role and use measured numbers only when you have them. Depending on the job, also prepare React or another framework, TypeScript, Node.js, accessibility, browser testing, and frontend or backend system design.

---

# How to Study and Answer

## A useful interview answer structure

1. **Give the definition:** one or two clear sentences.
2. **Show a small example:** explain what happens and why.
3. **Give a project use case:** where the idea helps in real code.
4. **Mention a limit:** an edge case, failure mode, or tradeoff.

Example for a closure: “A closure lets a function keep access to outer variables. I can use it to keep a debounce timer private. Each new debounced function gets its own timer. I also cancel that timer during cleanup so old work does not run after the feature is removed.”

## Suggested preparation order

1. Questions 1–20: language basics, scope, functions, and references.
2. Questions 21–31: arrays, objects, and property access.
3. Questions 32–45: async behavior, API requests, events, and cleanup.
4. Questions 46–50: code the solutions and explain edge cases.
5. Questions 51–72: modules, runtime behavior, production concerns, and testing.
6. Questions 73–75: output practice, additional coding, and real project stories.

## Final self-check

- Can I explain each main idea aloud without reading?
- Can I predict an example's output and explain the rule behind it?
- Can I write the five core coding solutions from scratch?
- Can I handle empty inputs, duplicates, errors, and cancellation?
- Can I explain time and space costs accurately?
- Can I describe a real project decision and its tradeoffs?

If an answer is uncertain during an interview, state your assumption, work through a small example, and explain how you would verify it. Clear reasoning is better than confidently repeating an incorrect rule.
