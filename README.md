# JavaScript Interview Questions & Experience Level

<a id="question-index"></a>

## Question Index

Click any question to jump directly to its answer. Each answer has a link back to this index.

### Variables & Scope

- [What are the differences between var, let, and const?](#question-1)
- [What are global, function, and block scope?](#question-2)
- [What is hoisting, and how does it affect variables and functions?](#question-3)
- [What is the temporal dead zone?](#question-4)
- [Can you modify an object or array declared with const?](#question-5)
- [What are JavaScript's primitive and non-primitive data types?](#question-6)
- [What is the difference between null and undefined?](#question-7)
- [Why does typeof null return "object"?](#question-8)
- [What is the difference between ==, ===, and Object.is()?](#question-9)
- [What are truthy and falsy values?](#question-10)
- [What is the difference between implicit and explicit type conversion?](#question-11)
- [How does + behave with numbers and strings?](#question-12)
- [What is NaN, and how do isNaN() and Number.isNaN() differ?](#question-13)
- [What is the difference between || and ???](#question-14)
- [How does optional chaining (?.) work?](#question-15)
- [What is short-circuit evaluation?](#question-16)
- [What is the difference between passing a primitive value and passing an object to a function?](#question-17)
- [Why is 0.1 + 0.2 !== 0.3, and how would you handle decimal calculations?](#question-18)
- [What are Symbol and BigInt, and when would you use them?](#question-19)
- [What is the difference between typeof, instanceof, and Array.isArray()?](#question-20)

### Functions, Scope & Closures

- [What is the difference between a function declaration and a function expression?](#question-21)
- [How do arrow functions differ from regular functions?](#question-22)
- [What is lexical scope?](#question-23)
- [What is a closure?](#question-24)
- [What are practical uses of closures?](#question-25)
- [How can closures accidentally retain unnecessary memory?](#question-26)
- [What is the difference between parameters and arguments?](#question-27)
- [How do default parameters work?](#question-28)
- [What is the difference between rest parameters and spread syntax?](#question-29)
- [What is a callback function?](#question-30)
- [What is a higher-order function?](#question-31)
- [What is a pure function?](#question-32)
- [What are side effects?](#question-33)
- [What is an immediately invoked function expression?](#question-34)
- [What is function currying?](#question-35)
- [What is the difference between currying and partial application?](#question-36)
- [What is recursion, and why is a base case necessary?](#question-37)
- [What is memoization, and when is it useful?](#question-38)
- [How would you implement a function that runs only once?](#question-39)
- [How would you compose multiple functions?](#question-40)
- [What is a stale closure, and where can it cause bugs?](#question-41)
- [How do var and let behave differently inside loops containing callbacks?](#question-42)

### this, Objects & Prototypes

- [How is this determined in a regular function?](#question-43)
- [How does an arrow function obtain its this value?](#question-44)
- [What happens to this when an object method is assigned to a separate variable?](#question-45)
- [What are the differences between call(), apply(), and bind()?](#question-46)
- [Can call(), apply(), or bind() change an arrow function's this?](#question-47)
- [What happens when a function is called with new?](#question-48)
- [What is the difference between a constructor function and a class?](#question-49)
- [What is a prototype?](#question-50)
- [How does the prototype chain work?](#question-51)
- [What is the difference between a constructor's .prototype and an object's internal prototype?](#question-52)
- [What is the difference between an own property and an inherited property?](#question-53)
- [How do Object.hasOwn() and the in operator differ?](#question-54)
- [What is the difference between Object.create() and an object literal?](#question-55)
- [What are property descriptors?](#question-56)
- [What are getters and setters?](#question-57)
- [What is the difference between Object.freeze(), Object.seal(), and Object.preventExtensions()?](#question-58)
- [Does Object.freeze() freeze nested objects?](#question-59)
- [What is the difference between static methods and instance methods?](#question-60)
- [How do extends and super work?](#question-61)
- [What are private class fields?](#question-62)
- [Why can modifying built-in prototypes cause problems?](#question-63)
- [What is prototype pollution?](#question-64)

### Arrays, Strings & Data Transformation

- [What is the difference between map(), forEach(), filter(), and reduce()?](#question-65)
- [What is the difference between find() and filter()?](#question-66)
- [What is the difference between findIndex(), indexOf(), and includes()?](#question-67)
- [What is the difference between some() and every()?](#question-68)
- [What is the difference between slice() and splice()?](#question-69)
- [Which common array methods mutate the original array?](#question-70)
- [Why does numeric sorting need a comparator?](#question-71)
- [What is the difference between sort() and toSorted()?](#question-72)
- [How do flat() and flatMap() differ?](#question-73)
- [What is a sparse array, and how do array methods handle empty slots?](#question-74)
- [What is the difference between for...in and for...of?](#question-75)
- [When would you use a normal loop instead of an array method?](#question-76)
- [How do you remove duplicates while preserving order?](#question-77)
- [How do you group an array of objects by a property?](#question-78)
- [How do you calculate totals using reduce()?](#question-79)
- [What are object and array destructuring?](#question-80)
- [How do destructuring defaults behave with null and undefined?](#question-81)
- [What is the difference between Object.keys(), Object.values(), and Object.entries()?](#question-82)
- [What is the difference between Map and a plain object?](#question-83)
- [What is the difference between Map and Set?](#question-84)
- [What are WeakMap and WeakSet, and when are they useful?](#question-85)
- [What is the difference between a shallow copy and a deep copy?](#question-86)
- [What are the limitations of cloning with JSON.parse(JSON.stringify(value))?](#question-87)
- [What can structuredClone() clone, and what can it not clone?](#question-88)
- [Are JavaScript strings mutable?](#question-89)
- [What is the difference between substring() and slice()?](#question-90)
- [How do replace() and replaceAll() differ?](#question-91)
- [Why can reversing a string with split("") produce incorrect results for some Unicode characters?](#question-92)

### Promises, Async/Await & Event Loop

- [Is JavaScript single-threaded, and how can it handle asynchronous operations?](#question-93)
- [What are the call stack, task queue, and microtask queue?](#question-94)
- [How does the event loop work?](#question-95)
- [What is the difference between synchronous and asynchronous execution?](#question-96)
- [Why does setTimeout(callback, 0) not execute immediately?](#question-97)
- [What is the execution order of synchronous code, Promise callbacks, and timers?](#question-98)
- [What happens when a microtask schedules another microtask?](#question-99)
- [How can long-running JavaScript block the browser UI?](#question-100)
- [What is callback hell, and how can it be avoided?](#question-101)
- [What are the states of a Promise?](#question-102)
- [Does a Promise executor run synchronously or asynchronously?](#question-103)
- [What do .then(), .catch(), and .finally() return?](#question-104)
- [How does returning a value or Promise from .then() affect the chain?](#question-105)
- [How are thrown errors propagated through a Promise chain?](#question-106)
- [What happens if you forget to return a Promise inside .then()?](#question-107)
- [What are the differences between Promise.all(), allSettled(), race(), and any()?](#question-108)
- [Does Promise.all() cancel the remaining operations when one rejects?](#question-109)
- [Does Promise.all() preserve input order in its results?](#question-110)
- [What happens when each Promise combinator receives an empty iterable?](#question-111)
- [What is an AggregateError?](#question-112)
- [What does an async function always return?](#question-113)
- [Does await block the entire JavaScript thread?](#question-114)
- [How do you handle errors with async/await?](#question-115)
- [What is the difference between sequential and concurrent asynchronous operations?](#question-116)
- [Why does forEach(async () => ...) not wait for its callbacks?](#question-117)
- [How would you process asynchronous tasks sequentially?](#question-118)
- [How would you limit the number of concurrent asynchronous tasks?](#question-119)
- [Can a Promise itself be cancelled, and how does AbortController help cancel an operation?](#question-120)

### API Handling & Production Scenarios

- [Does fetch() reject automatically for HTTP errors such as 404 or 500?](#question-121)
- [How do you distinguish network failures, HTTP failures, and response-parsing failures?](#question-122)
- [Why should you check response.ok?](#question-123)
- [Can you read a response body more than once?](#question-124)
- [How do you cancel an API request?](#question-125)
- [How do you prevent an older API response from overwriting newer results?](#question-126)
- [How would you implement request timeouts?](#question-127)
- [What is exponential backoff?](#question-128)
- [Why should retry logic include jitter?](#question-129)
- [Which requests are safe to retry, and how does idempotency affect that decision?](#question-130)
- [How should a client handle 429 Too Many Requests and Retry-After?](#question-131)
- [How would you prevent duplicate API requests?](#question-132)
- [How would you cache API results and expire stale entries?](#question-133)
- [How would you implement debounced search?](#question-134)
- [How would you combine debouncing with cancellation of previous requests?](#question-135)
- [How would you fetch independent resources concurrently?](#question-136)
- [How would you display partial results when some requests fail?](#question-137)
- [How would you prevent multiple simultaneous token-refresh requests?](#question-138)
- [How would you handle pagination and prevent duplicate records?](#question-139)
- [How would you implement optimistic updates and rollback on failure?](#question-140)

### DOM, Events & Browser APIs

- [What is the DOM?](#question-141)
- [What is the difference between querySelector() and querySelectorAll()?](#question-142)
- [What is the difference between a live collection and a static collection?](#question-143)
- [What is the difference between textContent, innerText, and innerHTML?](#question-144)
- [What are event capturing, target, and bubbling phases?](#question-145)
- [What is event delegation, and when is it useful?](#question-146)
- [What is the difference between event.target and event.currentTarget?](#question-147)
- [What is the difference between preventDefault(), stopPropagation(), and stopImmediatePropagation()?](#question-148)
- [Why must you preserve the callback reference when removing an event listener?](#question-149)
- [What do the once, passive, and signal listener options do?](#question-150)
- [How do you handle events on dynamically added elements?](#question-151)
- [What is the difference between debounce and throttle?](#question-152)
- [How does requestAnimationFrame() differ from setTimeout()?](#question-153)
- [What is IntersectionObserver, and how would you use it for infinite scrolling?](#question-154)
- [What is ResizeObserver, and when is it useful?](#question-155)
- [What is the difference between localStorage, sessionStorage, and cookies?](#question-156)
- [Why should browser storage not be treated as secure storage?](#question-157)
- [What is the same-origin policy?](#question-158)
- [What is CORS, and why does using mode: "no-cors" not solve ordinary cross-origin API access?](#question-159)
- [How does postMessage() work, and why should you validate the sender's origin?](#question-160)

### Modules, Errors, Memory & Performance

- [What is the difference between named exports and default exports?](#question-161)
- [What is the difference between static imports and dynamic import()?](#question-162)
- [What are live bindings in ES modules?](#question-163)
- [What can go wrong with circular module dependencies?](#question-164)
- [What is strict mode, and how does it change JavaScript behavior?](#question-165)
- [What is the difference between throw new Error() and throwing a string?](#question-166)
- [What does finally do, and how can a return inside it change the result?](#question-167)
- [When does try...catch fail to catch an asynchronous error?](#question-168)
- [What are iterables and iterators?](#question-169)
- [What are generator functions, and how does yield work?](#question-170)
- [How does garbage collection relate to object reachability?](#question-171)
- [What commonly causes memory leaks in frontend applications?](#question-172)
- [How can timers and event listeners retain memory after a component is removed?](#question-173)
- [How would you prevent a memoization cache from growing indefinitely?](#question-174)
- [What is the difference between a Web Worker and a Service Worker?](#question-175)
- [When would you move work into a Web Worker?](#question-176)
- [How would you split a long-running task to keep the page responsive?](#question-177)
- [What are time complexity and space complexity?](#question-178)
- [How would you identify and fix an unnecessary nested loop?](#question-179)
- [How would you investigate a slow function or memory leak using browser developer tools?](#question-180)


Comprehensive JavaScript interview questions with detailed, experience-based answers from real-world scenarios.


## Variables & Scope

<a id="question-1"></a>

### What are the differences between var, let, and const?

[Back to question index](#question-index)

**Answer:**

In my 5 years of experience, here's how I understand the key differences:

**var** - Old school, function-scoped:
```javascript
function test() {
  var x = 10;
  if (true) {
    var x = 20; // Same variable, overwrites
  }
  console.log(x); // 20
}
```

**let** - Block-scoped, can be reassigned:
```javascript
function test() {
  let x = 10;
  if (true) {
    let x = 20; // Different variable
  }
  console.log(x); // 10
  x = 30; // Can reassign
}
```

**const** - Block-scoped, cannot be reassigned:
```javascript
const x = 10;
x = 20; // Error: Assignment to constant variable
```

**Real-world scenario:** I use `const` by default for everything, `let` only when I need to reassign, and never use `var` in modern code. In a React project, `const` prevents accidental reassignments that cause bugs.

---

<a id="question-2"></a>

### What are global, function, and block scope?

[Back to question index](#question-index)

**Answer:**

**Global scope** - Variables accessible everywhere:
```javascript
const globalVar = "I'm global";

function test() {
  console.log(globalVar); // Can access
}
```

**Function scope** - Variables accessible only within the function (var):
```javascript
function test() {
  var functionScoped = "I'm inside function";
  console.log(functionScoped); // Works
}
console.log(functionScoped); // Error: Not defined
```

**Block scope** - Variables accessible only within blocks { } (let, const):
```javascript
if (true) {
  let blockScoped = "I'm inside block";
  console.log(blockScoped); // Works
}
console.log(blockScoped); // Error: Not defined
```

**Real-world scenario:** In a large project, I accidentally used `var` inside a loop and it leaked outside, causing a bug where variables were getting overwritten. Switching to `let` fixed it because it's block-scoped.

---

<a id="question-3"></a>

### What is hoisting, and how does it affect variables and functions?

[Back to question index](#question-index)

**Answer:**

Hoisting is JavaScript moving declarations to the top of their scope before code execution.

**Function declarations are fully hoisted:**
```javascript
sayHello(); // Works! - "Hello"

function sayHello() {
  console.log("Hello");
}
```

**var declarations are hoisted but undefined:**
```javascript
console.log(myVar); // undefined (not error)
var myVar = 10;
```

**let and const are hoisted but in Temporal Dead Zone:**
```javascript
console.log(myLet); // ReferenceError: Cannot access before initialization
let myLet = 10;
```

**Real-world scenario:** I had a bug where I called a function before defining it, and it worked with function declaration but failed with function expression. This taught me to always define functions before using them or use function declarations when order matters.

---

<a id="question-4"></a>

### What is the temporal dead zone?

[Back to question index](#question-index)

**Answer:**

The Temporal Dead Zone (TDZ) is the time between when a let/const variable is hoisted and when it's actually initialized. You can't access the variable during this period.

```javascript
// TDZ starts here
console.log(myVar); // ReferenceError
let myVar = 10; // TDZ ends here
console.log(myVar); // 10
```

**Real-world scenario:** I was debugging an issue where accessing a let variable at the top of a function threw an error. The variable was declared at the bottom. I moved the declaration to the top to fix it. TDZ exists to catch bugs where you use variables before they're properly initialized.

---

<a id="question-5"></a>

### Can you modify an object or array declared with const?

[Back to question index](#question-index)

**Answer:**

Yes! `const` only prevents reassignment of the variable itself, not modification of the object/array contents.

```javascript
const person = { name: "John" };
person.name = "Jane"; // Allowed
person.age = 25; // Allowed
person = { name: "New" }; // Error: Cannot reassign

const numbers = [1, 2, 3];
numbers.push(4); // Allowed
numbers[0] = 10; // Allowed
numbers = [5, 6]; // Error: Cannot reassign
```

**Real-world scenario:** In a Redux reducer, I use `const` for the state object but modify its properties. This is fine because the reference stays the same. To truly freeze an object, I use `Object.freeze()`.

---

<a id="question-6"></a>

### What are JavaScript's primitive and non-primitive data types?

[Back to question index](#question-index)

**Answer:**

**Primitive types** (stored by value):
- string
- number
- boolean
- null
- undefined
- symbol
- bigint

**Non-primitive types** (stored by reference):
- object
- array
- function
- date
- regex
- map, set, weakmap, weakset

```javascript
let str = "hello"; // Primitive
let obj = { name: "John" }; // Non-primitive
let arr = [1, 2, 3]; // Non-primitive
```

**Real-world scenario:** When copying data, primitives copy the value, but objects copy the reference. I once modified an array thinking I made a copy, but it modified the original because arrays are references. Now I use `structuredClone()` or spread operator for deep copies.

---

<a id="question-7"></a>

### What is the difference between null and undefined?

[Back to question index](#question-index)

**Answer:**

**undefined** - Variable declared but not assigned:
```javascript
let x;
console.log(x); // undefined

function test(a) {
  console.log(a); // undefined if no argument passed
}
```

**null** - Explicitly set to "no value":
```javascript
let x = null;
console.log(x); // null
```

**Key difference:**
```javascript
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object" (bug in JS)
console.log(null === undefined); // false
console.log(null == undefined); // true
```

**Real-world scenario:** In an API response, I use `null` when a field exists but has no value, and `undefined` when the field doesn't exist. This helps distinguish between "empty" and "missing" data in my frontend logic.

---

<a id="question-8"></a>

### Why does typeof null return "object"?

[Back to question index](#question-index)

**Answer:**

This is a historical bug in JavaScript from the first version. The type checking used 32-bit storage, and the lowest 3 bits were used for type tags. `null` was represented as all zeros, which is the same type tag as objects.

```javascript
typeof null; // "object" (bug)
```

**Real-world scenario:** When checking for null, I never use `typeof x === "object"` because it catches both objects and null. Instead, I use:
```javascript
if (x === null) { /* explicitly check null */ }
// or
if (x && typeof x === "object") { /* check for object, not null */ }
```

---

<a id="question-9"></a>

### What is the difference between ==, ===, and Object.is()?

[Back to question index](#question-index)

**Answer:**

**==** - Loose equality (type coercion):
```javascript
5 == "5"; // true (converts string to number)
null == undefined; // true
[] == ""; // true (coercion rules are complex)
```

**===** - Strict equality (no type coercion):
```javascript
5 === "5"; // false
null === undefined; // false
```

**Object.is()** - Strict equality with special cases:
```javascript
Object.is(NaN, NaN); // true (NaN === NaN is false)
Object.is(0, -0); // false (0 === -0 is true)
Object.is(null, null); // true
```

**Real-world scenario:** I always use `===` in my code to avoid unexpected type coercion bugs. Only use `==` when you specifically want coercion (like checking for null/undefined together: `x == null`). `Object.is()` is useful when you need to handle NaN correctly.

---

<a id="question-10"></a>

### What are truthy and falsy values?

[Back to question index](#question-index)

**Answer:**

**Falsy values** (6 values):
- false
- 0, -0
- "" (empty string)
- null
- undefined
- NaN

**Truthy values** (everything else):
- "0", "false" (non-empty strings)
- [] (empty array)
- {} (empty object)
- all numbers except 0

```javascript
if (false) { /* never runs */ }
if (0) { /* never runs */ }
if ("") { /* never runs */ }
if ([]) { /* runs - empty array is truthy! */ }
if ({}) { /* runs - empty object is truthy! */ }
```

**Real-world scenario:** I once had a bug where checking `if (response.data)` returned false when data was an empty array `[]`. I changed it to `if (response.data !== undefined)` to fix it. Empty arrays and objects are truthy, which surprises many developers.

---

<a id="question-11"></a>

### What is the difference between implicit and explicit type conversion?

[Back to question index](#question-index)

**Answer:**

**Implicit conversion** - JavaScript automatically converts types:
```javascript
"5" + 1; // "51" (number to string)
"5" - 1; // 4 (string to number)
"5" * 2; // 10 (string to number)
if ("hello") { /* string to boolean */ }
```

**Explicit conversion** - You manually convert:
```javascript
Number("5"); // 5
String(5); // "5"
Boolean(5); // true
parseInt("5px"); // 5
```

**Real-world scenario:** In form validation, I explicitly convert user input with `Number()` or `parseInt()` to avoid unexpected implicit conversions. Once, a user entered "5abc" and `+input` gave `NaN`, but `parseInt()` gave `5`. I always use explicit conversion for user input.

---

<a id="question-12"></a>

### How does + behave with numbers and strings?

[Back to question index](#question-index)

**Answer:**

The `+` operator is tricky:
- If either operand is a string, it concatenates
- If both are numbers, it adds

```javascript
5 + 5; // 10 (addition)
"5" + 5; // "55" (concatenation)
5 + "5"; // "55" (concatenation)
"5" + "5"; // "55" (concatenation)
5 + 5 + "5"; // "105" (5+5=10, then "10"+"5")
"5" + 5 + 5; // "555" ("5"+5="55", then "55"+5)
```

**Real-world scenario:** I had a bug where `total = price + tax` returned "10010" instead of 110 because one was a string from an API. I fixed it by ensuring both are numbers: `total = Number(price) + Number(tax)`. Now I always convert before math operations.

---

<a id="question-13"></a>

### What is NaN, and how do isNaN() and Number.isNaN() differ?

[Back to question index](#question-index)

**Answer:**

**NaN** (Not a Number) - Result of invalid math operations:
```javascript
Number("hello"); // NaN
0 / 0; // NaN
Math.sqrt(-1); // NaN
```

**isNaN()** - Coerces value before checking:
```javascript
isNaN("hello"); // true (converts to NaN)
isNaN(undefined); // true
isNaN({}); // true
```

**Number.isNaN()** - Checks if value is actually NaN:
```javascript
Number.isNaN("hello"); // false (string, not NaN)
Number.isNaN(NaN); // true
Number.isNaN(Number("hello")); // true
```

**Real-world scenario:** I use `Number.isNaN()` for strict NaN checking and `isNaN()` when I want to know if a value can't be converted to a number. In form validation, `Number.isNaN(Number(input))` is safer to check for invalid numbers.

---

<a id="question-14"></a>

### What is the difference between || and ???

[Back to question index](#question-index)

**Answer:**

**|| (OR)** - Returns first truthy value:
```javascript
0 || "default"; // "default"
"" || "default"; // "default"
null || "default"; // "default"
false || "default"; // "default"
0 || 10; // 10
```

**?? (Nullish Coalescing)** - Returns first non-null/non-undefined value:
```javascript
0 ?? "default"; // 0 (0 is not null/undefined)
"" ?? "default"; // "" (empty string is not null/undefined)
null ?? "default"; // "default"
undefined ?? "default"; // "default"
false ?? "default"; // false (false is not null/undefined)
```

**Real-world scenario:** When setting default values, I use `??` for when I want to accept 0, empty string, or false as valid values. For example, `count ?? 10` allows count to be 0, but `count || 10` would replace 0 with 10.

---

<a id="question-15"></a>

### How does optional chaining (?.) work?

[Back to question index](#question-index)

**Answer:**

Optional chaining safely accesses nested properties without errors:
```javascript
const user = {
  address: {
    city: "NYC"
  }
};

user.address.city; // "NYC"
user.address.zip; // undefined
user.contact.phone; // Error: Cannot read property 'phone' of undefined

user.contact?.phone; // undefined (no error)
user?.address?.city; // "NYC"
```

**Real-world scenario:** In a React app, I had many crashes when API responses had missing fields. I changed `user.profile.avatar` to `user.profile?.avatar` and it eliminated those crashes. Now I use optional chaining for all optional nested properties.

---

<a id="question-16"></a>

### What is short-circuit evaluation?

[Back to question index](#question-index)

**Answer:**

JavaScript stops evaluating logical operators as soon as the result is determined.

**OR (||) short-circuits on truthy:**
```javascript
false || true || false; // Stops at first true
// Only evaluates first two, never reaches third
```

**AND (&&) short-circuits on falsy:**
```javascript
true && false && true; // Stops at first false
// Only evaluates first two, never reaches third
```

**Real-world scenario:** I use this for conditional execution:
```javascript
isLoggedIn && renderDashboard(); // Only runs if true
user && user.profile && updateProfile(user.profile); // Safe nested access
```

This pattern is cleaner than nested if statements and prevents errors from missing properties.

---

<a id="question-17"></a>

### What is the difference between passing a primitive value and passing an object to a function?

[Back to question index](#question-index)

**Answer:**

**Primitives are passed by value:**
```javascript
function modify(x) {
  x = 10;
}
let num = 5;
modify(num);
console.log(num); // 5 (unchanged)
```

**Objects are passed by reference:**
```javascript
function modify(obj) {
  obj.name = "Changed";
}
let person = { name: "Original" };
modify(person);
console.log(person.name); // "Changed"
```

**Real-world scenario:** I once passed an array to a function, modified it inside, and was surprised when the original array changed. Now if I need to keep the original, I pass a copy: `modify([...arr])` or `modify(structuredClone(arr))`.

---

<a id="question-18"></a>

### Why is 0.1 + 0.2 !== 0.3, and how would you handle decimal calculations?

[Back to question index](#question-index)

**Answer:**

JavaScript uses binary floating-point, which can't represent some decimals exactly:
```javascript
0.1 + 0.2; // 0.30000000000000004
0.1 + 0.2 === 0.3; // false
```

**Solutions:**

1. **Round to precision:**
```javascript
const result = Math.round((0.1 + 0.2) * 100) / 100; // 0.3
```

2. **Use toFixed() for display:**
```javascript
const result = (0.1 + 0.2).toFixed(2); // "0.30"
```

3. **Use a library for money (best for production):**
```javascript
// Using decimal.js or similar
import Decimal from 'decimal.js';
new Decimal(0.1).plus(0.2).toNumber(); // 0.3
```

**Real-world scenario:** In an e-commerce app, I had cart totals showing $0.30000000000000004 instead of $0.30. I switched to using a decimal library for all monetary calculations to avoid floating-point errors.

---

<a id="question-19"></a>

### What are Symbol and BigInt, and when would you use them?

[Back to question index](#question-index)

**Answer:**

**Symbol** - Unique, immutable values (often used as object property keys):
```javascript
const id = Symbol('id');
const user = {
  [id]: 123,
  name: "John"
};
user[id]; // 123
user.name; // "John"
```

Use Symbol when you need unique property keys that won't collide.

**BigInt** - For integers larger than Number.MAX_SAFE_INTEGER:
```javascript
const big = 9007199254740991n; // n suffix
Number.MAX_SAFE_INTEGER; // 9007199254740991
Number.MAX_SAFE_INTEGER + 1; // 9007199254740992 (wrong!)
Number.MAX_SAFE_INTEGER + 1n; // 9007199254740992n (correct)
```

Use BigInt for very large numbers (database IDs, timestamps, crypto).

**Real-world scenario:** I used BigInt when working with Twitter Snowflake IDs which are 64-bit integers. Regular JavaScript numbers lose precision for such large values, so BigInt was necessary.

---

<a id="question-20"></a>

### What is the difference between typeof, instanceof, and Array.isArray()?

[Back to question index](#question-index)

**Answer:**

**typeof** - Checks primitive type:
```javascript
typeof "hello"; // "string"
typeof 42; // "number"
typeof {}; // "object"
typeof []; // "object" (array is object)
typeof null; // "object" (bug)
typeof undefined; // "undefined"
```

**instanceof** - Checks if object is instance of constructor:
```javascript
[] instanceof Array; // true
[] instanceof Object; // true
{} instanceof Object; // true
"hello" instanceof String; // false (primitive)
```

**Array.isArray()** - Specifically checks for arrays:
```javascript
Array.isArray([]); // true
Array.isArray({}); // false
Array.isArray("hello"); // false
```

**Real-world scenario:** When validating function parameters, I use:
- `typeof x === "string"` for primitives
- `Array.isArray(x)` for arrays (most reliable)
- `x instanceof MyClass` for custom classes
- Never use `typeof` for arrays (returns "object")

---

## Data Types & Type Coercion

*(Answers covered in Variables & Scope section above)*

---

## Functions, Scope & Closures

<a id="question-21"></a>

### What is the difference between a function declaration and a function expression?

[Back to question index](#question-index)

**Answer:**

**Function declaration:**
```javascript
function sayHello() {
  console.log("Hello");
}
sayHello(); // Works
```

**Function expression:**
```javascript
const sayHello = function() {
  console.log("Hello");
};
sayHello(); // Works
```

**Key differences:**

1. **Hoisting:**
```javascript
sayHello(); // Works (hoisted)
function sayHello() { }

sayBye(); // Error (not hoisted)
const sayBye = function() { };
```

2. **IIFE:**
```javascript
// Function expression can be IIFE
(function() {
  console.log("IIFE");
})();
```

**Real-world scenario:** I use function declarations for named functions that I call directly, and function expressions for callbacks, passing as arguments, or when I need to assign to variables. The hoisting difference has caused bugs when I called a function expression before its assignment.

---

<a id="question-22"></a>

### How do arrow functions differ from regular functions?

[Back to question index](#question-index)

**Answer:**

**1. No `this` binding:**
```javascript
const obj = {
  value: 10,
  regular: function() {
    console.log(this.value); // 10
  },
  arrow: () => {
    console.log(this.value); // undefined (this from outer scope)
  }
};
```

**2. No `arguments` object:**
```javascript
function regular() {
  console.log(arguments); // Works
}
const arrow = () => {
  console.log(arguments); // Error
};
```

**3. Cannot be used as constructors:**
```javascript
function Regular() { }
new Regular(); // Works

const Arrow = () => { };
new Arrow(); // Error
```

**4. Concise syntax:**
```javascript
const add = (a, b) => a + b; // Implicit return
const square = x => x * x; // Single param, no parens
```

**Real-world scenario:** In React, I use arrow functions for event handlers to avoid `this` binding issues. In class methods, I use regular functions when I need `this` to refer to the instance, and arrow functions when I want `this` from the outer scope.

---

<a id="question-23"></a>

### What is lexical scope?

[Back to question index](#question-index)

**Answer:**

Lexical scope means a function's scope is determined by where it's defined, not where it's called.

```javascript
function outer() {
  const outerVar = "I'm outer";

  function inner() {
    console.log(outerVar); // Can access outerVar
  }

  inner(); // "I'm outer"
}
outer();
```

**Real-world scenario:** This is why closures work. When I define a function inside another function, the inner function can access variables from the outer function even after the outer function has finished executing. This is the foundation of closures and is essential for patterns like module patterns and React hooks.

---

<a id="question-24"></a>

### What is a closure?

[Back to question index](#question-index)

**Answer:**

A closure is a function that remembers variables from its outer scope even after the outer function has returned.

```javascript
function createCounter() {
  let count = 0;

  return function() {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

The inner function "closes over" the `count` variable.

**Real-world scenario:** I use closures for:
- Private variables (module pattern)
- Function factories
- React hooks (useState, useEffect rely on closures)
- Event handlers that need to remember state

Once, I had a bug where an event handler always used the initial state value instead of the current value. This was a stale closure - the function captured the old state and never updated.

---

<a id="question-25"></a>

### What are practical uses of closures?

[Back to question index](#question-index)

**Answer:**

**1. Private variables (Module pattern):**
```javascript
function createBankAccount() {
  let balance = 0;

  return {
    deposit(amount) {
      balance += amount;
    },
    getBalance() {
      return balance;
    }
  };
}

const account = createBankAccount();
account.deposit(100);
account.balance; // undefined (private)
account.getBalance(); // 100
```

**2. Function factories:**
```javascript
function createMultiplier(multiplier) {
  return function(num) {
    return num * multiplier;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);
double(5); // 10
triple(5); // 15
```

**3. State preservation:**
```javascript
function setup() {
  let clicks = 0;
  document.addEventListener('click', () => {
    clicks++;
    console.log(clicks);
  });
}
```

**Real-world scenario:** In a React app, I used closures to create a private state manager before Redux. The closure pattern let me hide internal state while exposing controlled methods to modify it.

---

<a id="question-26"></a>

### How can closures accidentally retain unnecessary memory?

[Back to question index](#question-index)

**Answer:**

Closures keep references to variables, preventing garbage collection.

```javascript
function createHandler() {
  const hugeData = new Array(1000000).fill('data');

  return function() {
    console.log('clicked');
  };
}

const handler = createHandler();
// hugeData stays in memory even though handler doesn't use it!
```

**Solutions:**

1. **Null out unused references:**
```javascript
function createHandler() {
  const hugeData = new Array(1000000).fill('data');
  const result = function() {
    console.log('clicked');
  };
  hugeData = null; // Allow GC
  return result;
}
```

2. **Keep scope minimal:**
```javascript
function createHandler() {
  return function() {
    console.log('clicked');
  };
}
```

**Real-world scenario:** I had a memory leak in a single-page app where event handlers retained large objects. I profiled with Chrome DevTools and found closures holding onto unused data. I refactored to keep only necessary data in the closure scope.

---

<a id="question-27"></a>

### What is the difference between parameters and arguments?

[Back to question index](#question-index)

**Answer:**

**Parameters** - Variables in function definition:
```javascript
function greet(name, age) { // name and age are parameters
  console.log(name, age);
}
```

**Arguments** - Values passed when calling:
```javascript
greet("John", 25); // "John" and 25 are arguments
```

**Real-world scenario:** This is mostly terminology, but understanding it helps when reading documentation. When I teach junior developers, I explain: "Parameters are the placeholders, arguments are the actual values."

---

<a id="question-28"></a>

### How do default parameters work?

[Back to question index](#question-index)

**Answer:**

Default parameters provide fallback values when arguments are not provided:

```javascript
function greet(name = "Guest", age = 0) {
  console.log(name, age);
}

greet(); // "Guest", 0
greet("John"); // "John", 0
greet("John", 25); // "John", 25
```

**Important:** Default only works for `undefined`, not other falsy values:
```javascript
greet(null, null); // null, null (not defaults)
greet("", 0); // "", 0 (not defaults)
```

**Real-world scenario:** I use default parameters in API functions to avoid undefined errors:
```javascript
function fetchUsers(options = {}) {
  const { limit = 10, offset = 0 } = options;
  // ...
}
```

This makes the function more robust and self-documenting.

---

<a id="question-29"></a>

### What is the difference between rest parameters and spread syntax?

[Back to question index](#question-index)

**Answer:**

**Rest parameters** - Collect multiple arguments into an array:
```javascript
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4); // 10

function greet(greeting, ...names) {
  names.forEach(name => console.log(greeting, name));
}
greet("Hello", "John", "Jane"); // Hello John, Hello Jane
```

**Spread syntax** - Expand array/object into individual elements:
```javascript
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5]; // [1, 2, 3, 4, 5]

const obj = { name: "John" };
const newObj = { ...obj, age: 25 }; // { name: "John", age: 25 }

function sum(a, b, c) {
  return a + b + c;
}
sum(...arr); // 6
```

**Real-world scenario:** I use rest parameters for flexible function arguments (like console.log), and spread for cloning arrays/objects and merging data. In React, I often use `{...props}` to pass all props to a child component.

---

<a id="question-30"></a>

### What is a callback function?

[Back to question index](#question-index)

**Answer:**

A callback is a function passed as an argument to another function, to be executed later.

```javascript
function doSomething(callback) {
  console.log("Doing something...");
  callback();
}

doSomething(function() {
  console.log("Callback executed!");
});
```

**Real-world scenario:** Callbacks are everywhere:
- Event handlers: `button.addEventListener('click', handler)`
- Array methods: `arr.map(x => x * 2)`
- Async operations: `fs.readFile('file.txt', (err, data) => {})`

I once had "callback hell" with nested callbacks for sequential API calls. I refactored to use Promises and async/await for cleaner code.

---

<a id="question-31"></a>

### What is a higher-order function?

[Back to question index](#question-index)

**Answer:**

A higher-order function either:
1. Takes a function as an argument
2. Returns a function

```javascript
// Takes function as argument
function withLogging(fn) {
  return function(...args) {
    console.log("Calling with:", args);
    const result = fn(...args);
    console.log("Result:", result);
    return result;
  };
}

// Returns function
function createMultiplier(multiplier) {
  return function(num) {
    return num * multiplier;
  };
}
```

**Real-world scenario:** Built-in array methods (map, filter, reduce) are higher-order functions. I create custom higher-order functions for:
- Logging/debugging
- Authentication checks
- Error handling wrappers
- Memoization

They make code reusable and composable.

---

<a id="question-32"></a>

### What is a pure function?

[Back to question index](#question-index)

**Answer:**

A pure function:
1. Always returns the same output for the same input
2. Has no side effects (doesn't modify external state)

```javascript
// Pure
function add(a, b) {
  return a + b;
}

// Not pure (depends on external state)
let count = 0;
function increment() {
  count++;
  return count;
}

// Not pure (side effect)
function addAndLog(a, b) {
  console.log(a + b); // Side effect
  return a + b;
}
```

**Real-world scenario:** In Redux reducers, I write pure functions that take state and action, and return new state without mutations. This makes testing easy and prevents bugs. Pure functions are also easier to debug and optimize.

---

<a id="question-33"></a>

### What are side effects?

[Back to question index](#question-index)

**Answer:**

Side effects are any changes outside the function's scope:
- Modifying external variables
- DOM manipulation
- Network requests
- File I/O
- Console logging
- Database operations

```javascript
// Side effects
let global = 10;
function modifyGlobal() {
  global = 20; // Modifying external state
}

function saveToDB(data) {
  database.save(data); // External I/O
}

function updateDOM() {
  document.body.innerHTML = "Hello"; // DOM mutation
}
```

**Real-world scenario:** I try to separate pure logic from side effects. For example, in a form handler, I first validate (pure), then save to API (side effect). This separation makes code testable and predictable.

---

<a id="question-34"></a>

### What is an immediately invoked function expression?

[Back to question index](#question-index)

**Answer:**

An IIFE is a function that runs immediately after definition:

```javascript
(function() {
  console.log("IIFE executed!");
})();

// With parameters
(function(name) {
  console.log("Hello", name);
})("John");

// Arrow function IIFE
(() => {
  console.log("Arrow IIFE");
})();
```

**Real-world scenario:** I use IIFEs for:
- Creating private scope (before modules)
- Avoiding global variable pollution
- One-time setup code
- Module pattern (before ES6 modules)

In modern code, I mostly use ES6 modules instead, but IIFEs are still useful for scripts that need immediate execution.

---

<a id="question-35"></a>

### What is function currying?

[Back to question index](#question-index)

**Answer:**

Currying transforms a function with multiple arguments into a sequence of functions taking one argument each:

```javascript
// Regular function
function add(a, b, c) {
  return a + b + c;
}

// Curried version
function curriedAdd(a) {
  return function(b) {
    return function(c) {
      return a + b + c;
    };
  };
}

curriedAdd(1)(2)(3); // 6

// Arrow function version
const curriedAdd = a => b => c => a + b + c;
```

**Real-world scenario:** I use currying to create specialized functions:
```javascript
const multiply = a => b => a * b;
const double = multiply(2);
const triple = multiply(3);
double(5); // 10
triple(5); // 15
```

This is useful for function composition and creating reusable, configurable functions.

---

<a id="question-36"></a>

### What is the difference between currying and partial application?

[Back to question index](#question-index)

**Answer:**

**Currying** - Transform to sequence of single-argument functions:
```javascript
const add = a => b => c => a + b + c;
add(1)(2)(3); // 6
```

**Partial application** - Fix some arguments, create new function:
```javascript
function add(a, b, c) {
  return a + b + c;
}

const addFive = add.bind(null, 5);
addFive(2, 3); // 10

// Or using closures
function partial(fn, ...fixedArgs) {
  return function(...remainingArgs) {
    return fn(...fixedArgs, ...remainingArgs);
  };
}

const addFive = partial(add, 5);
addFive(2, 3); // 10
```

**Real-world scenario:** I use partial application more often than full currying. For example, creating a specialized API client:
```javascript
const apiCall = (method, url, data) => { /* ... */ };
const getUsers = partial(apiCall, 'GET', '/users');
const createUser = partial(apiCall, 'POST', '/users');
```

---

<a id="question-37"></a>

### What is recursion, and why is a base case necessary?

[Back to question index](#question-index)

**Answer:**

Recursion is when a function calls itself to solve a problem by breaking it into smaller sub-problems.

```javascript
function factorial(n) {
  if (n <= 1) return 1; // Base case
  return n * factorial(n - 1); // Recursive case
}

factorial(5); // 120
```

**Base case is necessary** to stop recursion. Without it, you get infinite recursion and stack overflow:

```javascript
function infiniteRecursion(n) {
  return n + infiniteRecursion(n - 1); // No base case!
}
infiniteRecursion(5); // Stack overflow
```

**Real-world scenario:** I use recursion for:
- Tree traversal (DOM, file systems)
- Divide and conquer algorithms
- Generating combinations/permutations

In production, I prefer iteration for simple cases to avoid stack overflow, but recursion is cleaner for hierarchical data.

---

<a id="question-38"></a>

### What is memoization, and when is it useful?

[Back to question index](#question-index)

**Answer:**

Memoization caches function results to avoid redundant calculations:

```javascript
function memoize(fn) {
  const cache = {};

  return function(...args) {
    const key = JSON.stringify(args);
    if (key in cache) {
      return cache[key];
    }
    const result = fn(...args);
    cache[key] = result;
    return result;
  };
}

function slowFibonacci(n) {
  if (n <= 1) return n;
  return slowFibonacci(n - 1) + slowFibonacci(n - 2);
}

const fastFibonacci = memoize(slowFibonacci);
fastFibonacci(50); // Fast (cached)
```

**Real-world scenario:** I use memoization for:
- Expensive calculations (Fibonacci, factorial)
- API responses (with cache expiry)
- Repeated DOM queries
- Complex data transformations

In a React app, I used `useMemo` hook to memoize expensive calculations in render to improve performance.

---

<a id="question-39"></a>

### How would you implement a function that runs only once?

[Back to question index](#question-index)

**Answer:**

```javascript
function once(fn) {
  let called = false;
  let result;

  return function(...args) {
    if (called) return result;
    called = true;
    result = fn(...args);
    return result;
  };
}

const initialize = once(() => {
  console.log("Initializing...");
  return "Initialized";
});

initialize(); // "Initializing...", "Initialized"
initialize(); // "Initialized" (no log)
initialize(); // "Initialized" (no log)
```

**Real-world scenario:** I use this for:
- One-time setup (initializing libraries)
- Single event registration
- Preventing duplicate form submissions
- Singleton initialization

In a project, I used `once` to ensure analytics tracking code only ran once even if called multiple times.

---

<a id="question-40"></a>

### How would you compose multiple functions?

[Back to question index](#question-index)

**Answer:**

Function composition combines functions where the output of one becomes input to the next:

```javascript
function compose(...fns) {
  return function(x) {
    return fns.reduceRight((acc, fn) => fn(acc), x);
  };
}

const add = x => x + 1;
const multiply = x => x * 2;
const square = x => x * x;

const composed = compose(square, multiply, add);
composed(3); // ((3 + 1) * 2)^2 = 64

// Pipe (left to right)
function pipe(...fns) {
  return function(x) {
    return fns.reduce((acc, fn) => fn(acc), x);
  };
}

const piped = pipe(add, multiply, square);
piped(3); // ((3 + 1) * 2)^2 = 64
```

**Real-world scenario:** I use composition for data transformation pipelines:
```javascript
const processUser = pipe(
  validateUser,
  sanitizeData,
  transformToAPI,
  sendToServer
);
```

This makes code declarative and easy to test (each function can be tested independently).

---

<a id="question-41"></a>

### What is a stale closure, and where can it cause bugs?

[Back to question index](#question-index)

**Answer:**

A stale closure occurs when a closure captures an old value that has since changed:

```javascript
function createCounter() {
  let count = 0;

  return {
    increment() {
      count++;
      console.log(count);
    },
    getCount() {
      // This closure captures count at creation time
      const snapshot = count;
      return () => snapshot; // Always returns old value!
    }
  };
}

const counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
const getStaleCount = counter.getCount();
counter.increment(); // 3
getStaleCount(); // 2 (stale!)
```

**Real-world scenario:** This commonly happens in React with useEffect:
```javascript
useEffect(() => {
  const interval = setInterval(() => {
    console.log(count); // Stale closure - count is initial value
  }, 1000);
  return () => clearInterval(interval);
}, []); // Empty deps = stale closure
```

Fix: Add dependencies or use functional updates.

---

<a id="question-42"></a>

### How do var and let behave differently inside loops containing callbacks?

[Back to question index](#question-index)

**Answer:**

**var - Function scoped, all callbacks share same variable:**
```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// Output: 3, 3, 3 (all see final value)
```

**let - Block scoped, each callback has its own variable:**
```javascript
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// Output: 0, 1, 2 (each has its own i)
```

**Real-world scenario:** I had a bug where event handlers in a loop all referenced the last value. I fixed it by switching to `let`. Before ES6, I used IIFEs to create new scope:
```javascript
for (var i = 0; i < 3; i++) {
  (function(j) {
    setTimeout(() => console.log(j), 100);
  })(i);
}
```

---

## this, Objects & Prototypes

<a id="question-43"></a>

### How is this determined in a regular function?

[Back to question index](#question-index)

**Answer:**

`this` is determined by how the function is called:

```javascript
function showThis() {
  console.log(this);
}

// 1. Simple call - this = global (or undefined in strict mode)
showThis(); // window (or undefined in strict)

// 2. Method call - this = object
const obj = { method: showThis };
obj.method(); // obj

// 3. call/apply - this = specified
showThis.call({ name: "John" }); // { name: "John" }

// 4. bind - this = bound
const bound = showThis.bind({ name: "Jane" });
bound(); // { name: "Jane" }

// 5. new - this = new instance
new showThis(); // new instance
```

**Real-world scenario:** I lost track of `this` many times before understanding these rules. Now I always ask: "How is this function being called?" In React, I use arrow functions or `.bind()` to ensure `this` refers to the component instance.

---

<a id="question-44"></a>

### How does an arrow function obtain its this value?

[Back to question index](#question-index)

**Answer:**

Arrow functions don't have their own `this` - they inherit it from the surrounding scope:

```javascript
const obj = {
  value: 10,
  regular: function() {
    console.log(this.value); // 10 (obj)
    const arrow = () => {
      console.log(this.value); // 10 (inherited from regular)
    };
    arrow();
  }
};
obj.regular();
```

**Real-world scenario:** In React class components, I use arrow functions for methods to avoid manual binding:
```javascript
class MyComponent extends React.Component {
  handleClick = () => { // Arrow function
    console.log(this); // Always component instance
  };
}
```

This is cleaner than `this.handleClick = this.handleClick.bind(this)` in the constructor.

---

<a id="question-45"></a>

### What happens to this when an object method is assigned to a separate variable?

[Back to question index](#question-index)

**Answer:**

The `this` binding is lost:

```javascript
const obj = {
  value: 10,
  method() {
    console.log(this.value);
  }
};

obj.method(); // 10 (this = obj)

const func = obj.method;
func(); // undefined (this = global/undefined)
```

**Real-world scenario:** This caused bugs when passing methods as callbacks:
```javascript
button.addEventListener('click', obj.method); // this = button, not obj!
```

Solutions:
```javascript
// 1. Arrow function
button.addEventListener('click', () => obj.method());

// 2. bind
button.addEventListener('click', obj.method.bind(obj));

// 3. Use arrow method in object
const obj = {
  method: () => { /* ... */ }
};
```

---

<a id="question-46"></a>

### What are the differences between call(), apply(), and bind()?

[Back to question index](#question-index)

**Answer:**

**call()** - Call function with specific `this` and arguments:
```javascript
function greet(greeting, punctuation) {
  console.log(greeting, this.name, punctuation);
}

const person = { name: "John" };
greet.call(person, "Hello", "!"); // Hello John !
```

**apply()** - Same as call but arguments as array:
```javascript
greet.apply(person, ["Hello", "!"]); // Hello John !
```

**bind()** - Create new function with bound `this`:
```javascript
const boundGreet = greet.bind(person, "Hello");
boundGreet("!"); // Hello John !
```

**Real-world scenario:**
- `call`/`apply` for one-time calls with specific context
- `bind` for event handlers and callbacks that need permanent context
- `apply` with spread for variadic functions: `fn.apply(null, args)`

---

<a id="question-47"></a>

### Can call(), apply(), or bind() change an arrow function's this?

[Back to question index](#question-index)

**Answer:**

No, arrow functions cannot have their `this` changed:

```javascript
const arrow = () => {
  console.log(this);
};

arrow.call({ name: "John" }); // Still original this
arrow.apply({ name: "John" }); // Still original this
const bound = arrow.bind({ name: "John" });
bound(); // Still original this
```

**Real-world scenario:** I tried to use `.bind()` on an arrow function and it didn't work. This is because arrow functions lexically bind `this` at creation time. If you need dynamic `this`, use a regular function.

---

<a id="question-48"></a>

### What happens when a function is called with new?

[Back to question index](#question-index)

**Answer:**

The `new` operator:
1. Creates a new object
2. Sets `this` to the new object
3. Links the object's prototype to the function's prototype
4. Returns the new object (unless function returns an object)

```javascript
function Person(name) {
  this.name = name;
}

const john = new Person("John");
console.log(john.name); // John
console.log(john instanceof Person); // true
```

**Real-world scenario:** I use `new` for constructor functions and classes. Without `new`, `this` is the global object, causing bugs:
```javascript
const jane = Person("Jane"); // Oops, no new!
console.log(name); // "Jane" (polluted global!)
```

---

<a id="question-49"></a>

### What is the difference between a constructor function and a class?

[Back to question index](#question-index)

**Answer:**

**Constructor function:**
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log("Hello", this.name);
};
```

**Class:**
```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log("Hello", this.name);
  }
}
```

**Key differences:**
- Classes have cleaner syntax
- Classes are not hoisted (must declare before use)
- Classes have stricter mode by default
- Classes can't be called without `new`
- Classes support private fields

**Real-world scenario:** I prefer classes for modern code - they're more readable and familiar to developers from other languages. Constructor functions are still useful for simple cases or when working with older codebases.

---

<a id="question-50"></a>

### What is a prototype?

[Back to question index](#question-index)

**Answer:**

A prototype is an object that other objects inherit properties from. Every JavaScript object has a prototype.

```javascript
const person = {
  name: "John"
};

console.log(person.toString); // Exists (inherited from Object.prototype)
console.log(person.hasOwnProperty("name")); // true (inherited)
```

**Real-world scenario:** Prototypes enable inheritance and method sharing. Instead of copying methods to every object, we put them on the prototype and all instances share them. This saves memory and allows runtime modification of behavior.

---

<a id="question-51"></a>

### How does the prototype chain work?

[Back to question index](#question-index)

**Answer:**

When accessing a property, JavaScript searches up the prototype chain:

```javascript
const grandparent = { a: 1 };
const parent = Object.create(grandparent);
parent.b = 2;
const child = Object.create(parent);
child.c = 3;

child.a; // 1 (found in grandparent)
child.b; // 2 (found in parent)
child.c; // 3 (found in child)
child.d; // undefined (not found anywhere)
```

**Real-world scenario:** This is why arrays have methods like `map` and `filter` - they're on `Array.prototype`. The prototype chain enables method inheritance and the `instanceof` operator. Understanding this helps debug why certain properties/methods are available on objects.

---

<a id="question-52"></a>

### What is the difference between a constructor's .prototype and an object's internal prototype?

[Back to question index](#question-index)

**Answer:**

**Constructor's .prototype** - The object that will be the prototype of instances:
```javascript
function Person() { }
Person.prototype.greet = function() { };

const john = new Person();
john.greet(); // Works (inherited from Person.prototype)
```

**Object's internal prototype** - The object's actual prototype (__proto__):
```javascript
const john = new Person();
john.__proto__ === Person.prototype; // true
Object.getPrototypeOf(john) === Person.prototype; // true
```

**Real-world scenario:** The constructor's `.prototype` is where you add methods for all instances. The object's internal prototype (accessed via `__proto__` or `Object.getPrototypeOf`) is the actual prototype link. Understanding this distinction helps when debugging inheritance chains.

---

<a id="question-53"></a>

### What is the difference between an own property and an inherited property?

[Back to question index](#question-index)

**Answer:**

**Own property** - Directly on the object:
```javascript
const obj = { name: "John" };
obj.hasOwnProperty("name"); // true
```

**Inherited property** - From prototype:
```javascript
const obj = {};
obj.toString; // Inherited from Object.prototype
obj.hasOwnProperty("toString"); // false
```

**Real-world scenario:** When iterating over object properties, I use `Object.keys()` (own only) or `for...in` (includes inherited). This distinction matters when you want to avoid iterating over prototype methods or when checking if a property truly belongs to the object.

---

<a id="question-54"></a>

### How do Object.hasOwn() and the in operator differ?

[Back to question index](#question-index)

**Answer:**

**Object.hasOwn()** - Checks for own properties only:
```javascript
const obj = { name: "John" };
Object.hasOwn(obj, "name"); // true
Object.hasOwn(obj, "toString"); // false (inherited)
```

**in operator** - Checks own and inherited:
```javascript
const obj = { name: "John" };
"name" in obj; // true
"toString" in obj; // true (inherited)
```

**Real-world scenario:** I use `Object.hasOwn()` (or `hasOwnProperty`) when I need to check if a property is directly on the object, and `in` when I want to check if the property is accessible (including from prototype). This prevents false positives from inherited methods.

---

<a id="question-55"></a>

### What is the difference between Object.create() and an object literal?

[Back to question index](#question-index)

**Answer:**

**Object literal** - Creates object with Object.prototype as prototype:
```javascript
const obj = {}; // __proto__ = Object.prototype
```

**Object.create()** - Creates object with specified prototype:
```javascript
const proto = { greet() { console.log("Hello"); } };
const obj = Object.create(proto); // __proto__ = proto
obj.greet(); // Works
```

**Real-world scenario:** I use `Object.create()` when I need custom prototypes or prototype-only objects (no own properties). For example, creating objects that inherit from a specific base without using constructors. Object literals are simpler for most cases.

---

<a id="question-56"></a>

### What are property descriptors?

[Back to question index](#question-index)

**Answer:**

Property descriptors define how a property behaves:

```javascript
const obj = {};

Object.defineProperty(obj, "name", {
  value: "John",
  writable: false, // Cannot be reassigned
  enumerable: true, // Shows in for...in
  configurable: false // Cannot be deleted or reconfigured
});

obj.name = "Jane"; // Fails silently (or throws in strict)
delete obj.name; // Fails
```

**Real-world scenario:** I use property descriptors to create read-only properties or hidden properties. For example, in a library, I might make certain configuration properties read-only to prevent users from modifying them accidentally.

---

<a id="question-57"></a>

### What are getters and setters?

[Back to question index](#question-index)

**Answer:**

Getters and setters control property access:

```javascript
const person = {
  _age: 25,
  get age() {
    return this._age;
  },
  set age(value) {
    if (value < 0) throw new Error("Invalid age");
    this._age = value;
  }
};

person.age; // 25 (calls getter)
person.age = 30; // Calls setter
person.age = -5; // Error
```

**Real-world scenario:** I use getters/setters for:
- Validation (like age above)
- Computed properties
- Logging/debugging property access
- Lazy initialization

In Vue.js, computed properties use this pattern extensively.

---

<a id="question-58"></a>

### What is the difference between Object.freeze(), Object.seal(), and Object.preventExtensions()?

[Back to question index](#question-index)

**Answer:**

**Object.preventExtensions()** - Can't add new properties:
```javascript
const obj = { a: 1 };
Object.preventExtensions(obj);
obj.b = 2; // Fails
obj.a = 3; // Works
delete obj.a; // Works
```

**Object.seal()** - Can't add/delete, can modify:
```javascript
const obj = { a: 1 };
Object.seal(obj);
obj.b = 2; // Fails
delete obj.a; // Fails
obj.a = 3; // Works
```

**Object.freeze()** - Can't add/delete/modify:
```javascript
const obj = { a: 1 };
Object.freeze(obj);
obj.b = 2; // Fails
delete obj.a; // Fails
obj.a = 3; // Fails
```

**Real-world scenario:** I use `Object.freeze()` for immutable state (like Redux initial state), `Object.seal()` for configuration objects that shouldn't change structure, and `Object.preventExtensions()` rarely. Freezing helps catch accidental mutations in development.

---

<a id="question-59"></a>

### Does Object.freeze() freeze nested objects?

[Back to question index](#question-index)

**Answer:**

No, `Object.freeze()` is shallow:

```javascript
const obj = {
  nested: { value: 1 }
};

Object.freeze(obj);
obj.nested.value = 2; // Works! (nested not frozen)
```

**Deep freeze solution:**
```javascript
function deepFreeze(obj) {
  Object.freeze(obj);
  for (const prop of Object.values(obj)) {
    if (typeof prop === 'object' && prop !== null) {
      deepFreeze(prop);
    }
  }
}
```

**Real-world scenario:** I was surprised when a frozen object's nested property still changed. Now I use a deep freeze function or libraries like `immer` for true immutability. For shallow freezes, I document that nested objects can still change.

---

<a id="question-60"></a>

### What is the difference between static methods and instance methods?

[Back to question index](#question-index)

**Answer:**

**Static methods** - Called on the class/constructor, not instances:
```javascript
class MathUtils {
  static add(a, b) {
    return a + b;
  }
}

MathUtils.add(1, 2); // 3
const utils = new MathUtils();
utils.add(1, 2); // Error
```

**Instance methods** - Called on instances:
```javascript
class Calculator {
  add(a, b) {
    return a + b;
  }
}

const calc = new Calculator();
calc.add(1, 2); // 3
Calculator.add(1, 2); // Error
```

**Real-world scenario:** I use static methods for utility functions that don't need instance data (like `Math.random()`, `Array.from()`). Instance methods are for operations on specific instances (like `array.map()`, `string.toUpperCase()`).

---

<a id="question-61"></a>

### How do extends and super work?

[Back to question index](#question-index)

**Answer:**

**extends** - Creates a class that inherits from another:
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(this.name, "makes a sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Must call super() first
    this.breed = breed;
  }

  speak() {
    super.speak(); // Call parent method
    console.log("Woof!");
  }
}
```

**super** - Calls parent constructor or method:
- `super()` in constructor calls parent constructor
- `super.method()` calls parent method

**Real-world scenario:** I use inheritance sparingly - composition is often better. But when I do, I ensure to call `super()` in the constructor before using `this`. This is a common mistake that causes "Must call super before using this" errors.

---

<a id="question-62"></a>

### What are private class fields?

[Back to question index](#question-index)

**Answer:**

Private fields (using `#`) are only accessible within the class:

```javascript
class BankAccount {
  #balance = 0;

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(100);
account.#balance; // Error: Private field
account.getBalance(); // 100
```

**Real-world scenario:** I use private fields for true encapsulation - data that shouldn't be accessed from outside the class. Before private fields, I used `_` prefix convention (like `_balance`), but that wasn't truly private. Private fields make intentions clear and prevent accidental access.

---

<a id="question-63"></a>

### Why can modifying built-in prototypes cause problems?

[Back to question index](#question-index)

**Answer:**

Modifying built-in prototypes affects all code in your application and third-party libraries:

```javascript
// Bad practice
Array.prototype.map = function() {
  console.log("Custom map!");
};

[1, 2, 3].map(x => x * 2); // Breaks! Doesn't work as expected
```

**Problems:**
- Breaks built-in functionality
- Conflicts with future JavaScript versions
- Affects other developers' code
- Hard to debug

**Real-world scenario:** A team member once added a method to `Array.prototype` that conflicted with a library expecting the original behavior. It took hours to debug. Now I never modify built-in prototypes - I use utility functions or extend classes instead.

---

<a id="question-64"></a>

### What is prototype pollution?

[Back to question index](#question-index)

**Answer:**

Prototype pollution is when malicious code modifies Object.prototype, affecting all objects:

```javascript
// Vulnerable code
function merge(target, source) {
  for (const key in source) {
    target[key] = source[key];
  }
}

// Attack
const malicious = { "__proto__": { "isAdmin": true } };
const user = {};
merge(user, malicious);
// Now ALL objects have isAdmin = true!
```

**Real-world scenario:** This is a security vulnerability in libraries that merge objects without sanitization. I always validate and sanitize keys when merging user-provided objects, especially keys like `__proto__`, `constructor`, and `prototype`.

---

## Arrays, Strings & Data Transformation

<a id="question-65"></a>

### What is the difference between map(), forEach(), filter(), and reduce()?

[Back to question index](#question-index)

**Answer:**

**map()** - Transform each element, returns new array:
```javascript
const nums = [1, 2, 3];
const doubled = nums.map(x => x * 2); // [2, 4, 6]
```

**forEach()** - Execute function for each element, returns undefined:
```javascript
nums.forEach(x => console.log(x)); // Logs 1, 2, 3
// Returns undefined
```

**filter()** - Keep elements that pass test, returns new array:
```javascript
const evens = nums.filter(x => x % 2 === 0); // [2]
```

**reduce()** - Reduce array to single value:
```javascript
const sum = nums.reduce((acc, x) => acc + x, 0); // 6
```

**Real-world scenario:** I use `map` for transformations, `filter` for selection, `reduce` for aggregation, and `forEach` only for side effects (like logging). I avoid `forEach` when I could use `map` or `reduce` for better composability.

---

<a id="question-66"></a>

### What is the difference between find() and filter()?

[Back to question index](#question-index)

**Answer:**

**find()** - Returns first matching element:
```javascript
const nums = [1, 2, 3, 2];
const found = nums.find(x => x === 2); // 2 (first match)
```

**filter()** - Returns all matching elements:
```javascript
const filtered = nums.filter(x => x === 2); // [2, 2]
```

**Real-world scenario:** I use `find` when I need one element (like finding a user by ID), and `filter` when I need all matches (like finding all active users). Using `filter()[0]` is inefficient when you only need the first match.

---

<a id="question-67"></a>

### What is the difference between findIndex(), indexOf(), and includes()?

[Back to question index](#question-index)

**Answer:**

**findIndex()** - Find index using callback:
```javascript
const users = [{ id: 1 }, { id: 2 }];
const index = users.findIndex(u => u.id === 2); // 1
```

**indexOf()** - Find index using strict equality:
```javascript
const nums = [1, 2, 3];
const index = nums.indexOf(2); // 1
const index = nums.indexOf(4); // -1 (not found)
```

**includes()** - Check if element exists:
```javascript
nums.includes(2); // true
nums.includes(4); // false
```

**Real-world scenario:** I use `includes` for simple existence checks, `indexOf` when I need the position, and `findIndex` for complex searches (like finding by object property). `includes` is more readable than `indexOf !== -1`.

---

<a id="question-68"></a>

### What is the difference between some() and every()?

[Back to question index](#question-index)

**Answer:**

**some()** - Returns true if any element passes:
```javascript
const nums = [1, 2, 3];
nums.some(x => x > 2); // true (3 > 2)
nums.some(x => x > 5); // false
```

**every()** - Returns true if all elements pass:
```javascript
nums.every(x => x > 0); // true
nums.every(x => x > 2); // false
```

**Real-world scenario:** I use `some` to check if any items meet a condition (like "any errors?"), and `every` to check if all items meet a condition (like "all required fields filled?"). These are more readable than manual loops.

---

<a id="question-69"></a>

### What is the difference between slice() and splice()?

[Back to question index](#question-index)

**Answer:**

**slice()** - Returns copy of portion (non-mutating):
```javascript
const arr = [1, 2, 3, 4, 5];
const sliced = arr.slice(1, 3); // [2, 3]
console.log(arr); // [1, 2, 3, 4, 5] (unchanged)
```

**splice()** - Modifies array in place:
```javascript
const arr = [1, 2, 3, 4, 5];
const spliced = arr.splice(1, 3); // Removes 3 elements from index 1
console.log(arr); // [1, 5] (changed)
console.log(spliced); // [2, 3, 4] (removed elements)
```

**Real-world scenario:** I use `slice` when I need a copy (like pagination), and `splice` when I need to modify the array (like removing items). The names are confusing - I remember "slice" like slicing bread (no harm to original), "splice" like splicing a rope (changes it).

---

<a id="question-70"></a>

### Which common array methods mutate the original array?

[Back to question index](#question-index)

**Answer:**

**Mutating methods:**
- push(), pop()
- shift(), unshift()
- splice()
- sort(), reverse()
- fill()
- copyWithin()

**Non-mutating methods:**
- map(), filter(), reduce()
- slice(), concat()
- forEach(), find(), includes()
- flat(), flatMap()
- toSorted(), toReversed(), toSpliced() (new methods)

**Real-world scenario:** In React, I avoid mutating methods because they don't trigger re-renders. I use non-mutating methods or spread operator instead. For example, instead of `arr.push(item)`, I use `setArr([...arr, item])`.

---

<a id="question-71"></a>

### Why does numeric sorting need a comparator?

[Back to question index](#question-index)

**Answer:**

Default sort converts to strings:
```javascript
const nums = [1, 10, 2, 20];
nums.sort(); // [1, 10, 2, 20] (sorted as strings: "1", "10", "2", "20")
```

With comparator:
```javascript
nums.sort((a, b) => a - b); // [1, 2, 10, 20] (numeric sort)
```

**Real-world scenario:** I once had a bug where sorting [1, 2, 10] gave [1, 10, 2]. Now I always provide a comparator for numeric sorts. For strings, default sort is usually fine, but I use `localeCompare` for internationalization.

---

<a id="question-72"></a>

### What is the difference between sort() and toSorted()?

[Back to question index](#question-index)

**Answer:**

**sort()** - Mutates original array:
```javascript
const arr = [3, 1, 2];
arr.sort();
console.log(arr); // [1, 2, 3] (mutated)
```

**toSorted()** - Returns new sorted array (non-mutating):
```javascript
const arr = [3, 1, 2];
const sorted = arr.toSorted();
console.log(arr); // [3, 1, 2] (unchanged)
console.log(sorted); // [1, 2, 3]
```

**Real-world scenario:** In React and functional programming, I prefer `toSorted()` to avoid mutations. If `toSorted()` isn't available (older browsers), I use `[...arr].sort()` to create a copy first.

---

<a id="question-73"></a>

### How do flat() and flatMap() differ?

[Back to question index](#question-index)

**Answer:**

**flat()** - Flattens nested arrays:
```javascript
const nested = [1, [2, [3]]];
nested.flat(); // [1, 2, [3]] (1 level)
nested.flat(2); // [1, 2, 3] (2 levels)
nested.flat(Infinity); // [1, 2, 3] (all levels)
```

**flatMap()** - Maps then flattens one level:
```javascript
const arr = [1, 2, 3];
arr.flatMap(x => [x, x * 2]); // [1, 2, 2, 4, 3, 6]
// Equivalent to: arr.map(x => [x, x * 2]).flat(1)
```

**Real-world scenario:** I use `flatMap` when I need to transform and flatten in one step (like mapping words to characters and flattening). It's more efficient than `map().flat()` and clearer about intent.

---

<a id="question-74"></a>

### What is a sparse array, and how do array methods handle empty slots?

[Back to question index](#question-index)

**Answer:**

**Sparse array** - Array with empty slots:
```javascript
const sparse = [1, , , 4]; // Empty slots at index 1, 2
console.log(sparse.length); // 4
console.log(sparse[1]); // undefined
```

**How methods handle empty slots:**
```javascript
sparse.map(x => x * 2); // [2, empty, empty, 8] (preserves empties)
sparse.filter(x => true); // [1, 4] (removes empties)
sparse.forEach(x => console.log(x)); // Logs 1, 4 (skips empties)
```

**Real-world scenario:** Sparse arrays can cause bugs. I avoid creating them and use `undefined` instead. When I encounter them, I use `filter(() => true)` to remove empty slots or `Array.from()` to convert to dense array.

---

<a id="question-75"></a>

### What is the difference between for...in and for...of?

[Back to question index](#question-index)

**Answer:**

**for...in** - Iterates over enumerable properties (including inherited):
```javascript
const arr = [1, 2, 3];
for (const i in arr) {
  console.log(i); // "0", "1", "2" (indices as strings)
}
```

**for...of** - Iterates over values:
```javascript
for (const val of arr) {
  console.log(val); // 1, 2, 3 (values)
}
```

**Real-world scenario:** I use `for...of` for arrays (cleaner, gives values), and `for...in` only for objects when I need keys. Using `for...in` on arrays is a common mistake - it gives indices, not values, and includes inherited properties.

---

<a id="question-76"></a>

### When would you use a normal loop instead of an array method?

[Back to question index](#question-index)

**Answer:**

I use normal loops when:
1. Performance is critical (loops are faster)
2. Need to break early (array methods can't break)
3. Need to access index efficiently
4. Complex control flow (continue, multiple conditions)

```javascript
// Break early - normal loop
for (let i = 0; i < arr.length; i++) {
  if (arr[i] === target) break;
}

// Array method - can't break easily
arr.find(x => x === target); // Always iterates all
```

**Real-world scenario:** In performance-critical code (game loops, data processing), I use normal loops. For everyday code, array methods are more readable. I've replaced many loops with array methods for better maintainability.

---

<a id="question-77"></a>

### How do you remove duplicates while preserving order?

[Back to question index](#question-index)

**Answer:**

**Using Set:**
```javascript
const arr = [1, 2, 2, 3, 1];
const unique = [...new Set(arr)]; // [1, 2, 3]
```

**Using filter:**
```javascript
const unique = arr.filter((item, index) => arr.indexOf(item) === index);
```

**Using reduce:**
```javascript
const unique = arr.reduce((acc, item) => {
  return acc.includes(item) ? acc : [...acc, item];
}, []);
```

**Real-world scenario:** I use the Set approach - it's the most readable and efficient (O(n)). The filter approach is O(n²) for large arrays. I used this recently to deduplicate API responses before displaying to users.

---

<a id="question-78"></a>

### How do you group an array of objects by a property?

[Back to question index](#question-index)

**Answer:**

**Using reduce:**
```javascript
const users = [
  { name: "John", age: 25 },
  { name: "Jane", age: 25 },
  { name: "Bob", age: 30 }
];

const grouped = users.reduce((acc, user) => {
  const key = user.age;
  if (!acc[key]) acc[key] = [];
  acc[key].push(user);
  return acc;
}, {});

// { 25: [{John}, {Jane}], 30: [{Bob}] }
```

**Real-world scenario:** I use this pattern for grouping data by category, date, or status. For example, grouping messages by conversation ID or grouping products by category. It's cleaner than manual loops and more functional.

---

<a id="question-79"></a>

### How do you calculate totals using reduce()?

[Back to question index](#question-index)

**Answer:**

**Sum numbers:**
```javascript
const nums = [1, 2, 3, 4, 5];
const total = nums.reduce((acc, num) => acc + num, 0); // 15
```

**Sum object property:**
```javascript
const items = [{ price: 10 }, { price: 20 }, { price: 30 }];
const total = items.reduce((acc, item) => acc + item.price, 0); // 60
```

**Group and sum:**
```javascript
const sales = [
  { product: "A", amount: 10 },
  { product: "B", amount: 20 },
  { product: "A", amount: 15 }
];

const totals = sales.reduce((acc, sale) => {
  acc[sale.product] = (acc[sale.product] || 0) + sale.amount;
  return acc;
}, {});
// { A: 25, B: 20 }
```

**Real-world scenario:** I use reduce for all kinds of aggregations - calculating totals, averages, counts, and complex transformations. It's more powerful than people realize and can replace many manual loops.

---

<a id="question-80"></a>

### What are object and array destructuring?

[Back to question index](#question-index)

**Answer:**

**Array destructuring:**
```javascript
const nums = [1, 2, 3];
const [first, second, third] = nums;
// first = 1, second = 2, third = 3

const [first, ...rest] = nums;
// first = 1, rest = [2, 3]
```

**Object destructuring:**
```javascript
const user = { name: "John", age: 25, city: "NYC" };
const { name, age } = user;
// name = "John", age = 25

const { name: userName, age: userAge } = user;
// userName = "John", userAge = 25
```

**Real-world scenario:** I use destructuring constantly - for function parameters, extracting API responses, swapping variables, and more. It makes code more readable by showing exactly what properties are being used.

---

<a id="question-81"></a>

### How do destructuring defaults behave with null and undefined?

[Back to question index](#question-index)

**Answer:**

**Destructuring with defaults:**
```javascript
const { name = "Guest" } = {}; // name = "Guest"
const { name = "Guest" } = { name: null }; // name = null (not default!)
const { name = "Guest" } = { name: undefined }; // name = "Guest"
```

**Key:** Defaults only apply for `undefined`, not `null` or other falsy values.

**Real-world scenario:** I once had a bug where a destructured value was `null` instead of the default. Now I remember: defaults only for `undefined`. If I want to handle `null`, I need explicit checks: `const { name } = obj; const finalName = name ?? "Guest";`

---

<a id="question-82"></a>

### What is the difference between Object.keys(), Object.values(), and Object.entries()?

[Back to question index](#question-index)

**Answer:**

**Object.keys()** - Returns array of keys:
```javascript
const obj = { a: 1, b: 2 };
Object.keys(obj); // ["a", "b"]
```

**Object.values()** - Returns array of values:
```javascript
Object.values(obj); // [1, 2]
```

**Object.entries()** - Returns array of [key, value] pairs:
```javascript
Object.entries(obj); // [["a", 1], ["b", 2]]
```

**Real-world scenario:** I use `keys` for iterating over property names, `values` when I only need the data, and `entries` when I need both (like converting object to Map or for transformations). `entries` is especially useful with `Object.fromEntries()` to transform objects.

---

<a id="question-83"></a>

### What is the difference between Map and a plain object?

[Back to question index](#question-index)

**Answer:**

**Map advantages:**
- Keys can be any type (objects, functions)
- Maintains insertion order
- Has size property
- Better performance for frequent additions/removals
- Has built-in methods (get, set, has, delete)

**Object advantages:**
- Simpler syntax
- JSON serialization/deserialization
- Better for string keys only

```javascript
const map = new Map();
const obj = {};

map.set({}, "value"); // Works
obj[{}] = "value"; // Creates string key "[object Object]"
```

**Real-world scenario:** I use Map when I need non-string keys or frequent modifications. For configuration and data transfer, I use plain objects (easier to work with JSON). Maps are also useful for caching with object keys.

---

<a id="question-84"></a>

### What is the difference between Map and Set?

[Back to question index](#question-index)

**Answer:**

**Map** - Key-value pairs:
```javascript
const map = new Map();
map.set("key", "value");
map.get("key"); // "value"
```

**Set** - Unique values only:
```javascript
const set = new Set();
set.add(1);
set.add(1); // Ignored (duplicate)
set.has(1); // true
```

**Real-world scenario:** I use Map for associations (like caching, lookups), and Set for uniqueness (like removing duplicates, tracking seen items). Sets are great for checking membership - `set.has(x)` is O(1) vs `arr.includes(x)` which is O(n).

---

<a id="question-85"></a>

### What are WeakMap and WeakSet, and when are they useful?

[Back to question index](#question-index)

**Answer:**

**WeakMap** - Like Map but keys are weakly referenced (garbage collected if no other references):
```javascript
const weakMap = new WeakMap();
let key = {};
weakMap.set(key, "value");
key = null; // Key can be garbage collected
```

**WeakSet** - Like Set but weakly referenced:
```javascript
const weakSet = new WeakSet();
let obj = {};
weakSet.add(obj);
obj = null; // Can be garbage collected
```

**Use cases:**
- Caching without memory leaks
- Private data storage
- DOM node metadata

**Real-world scenario:** I use WeakMap to store private data for objects without preventing garbage collection. For example, attaching metadata to DOM nodes - when nodes are removed, the metadata is automatically cleaned up.

---

<a id="question-86"></a>

### What is the difference between a shallow copy and a deep copy?

[Back to question index](#question-index)

**Answer:**

**Shallow copy** - Copies top level, nested objects are shared:
```javascript
const original = { a: 1, nested: { b: 2 } };
const shallow = { ...original };
shallow.nested.b = 3;
console.log(original.nested.b); // 3 (modified!)
```

**Deep copy** - Copies all levels:
```javascript
const deep = JSON.parse(JSON.stringify(original));
deep.nested.b = 3;
console.log(original.nested.b); // 2 (unchanged)
```

**Real-world scenario:** I use shallow copies for performance when nested objects won't be modified. For state updates in Redux/React, I need deep copies or use libraries like Immer that handle it efficiently. Shallow copies are faster but can cause bugs if nested objects are modified.

---

<a id="question-87"></a>

### What are the limitations of cloning with JSON.parse(JSON.stringify(value))?

[Back to question index](#question-index)

**Answer:**

**Limitations:**
- Loses functions
- Loses undefined values
- Loses Symbol keys
- Loses Date objects (becomes strings)
- Loses circular references (throws error)
- Loses Map, Set, WeakMap, WeakSet

```javascript
const obj = {
  fn: () => {},
  date: new Date(),
  undef: undefined,
  [Symbol("id")]: 123
};

const cloned = JSON.parse(JSON.stringify(obj));
console.log(cloned.fn); // undefined
console.log(cloned.date); // "2024-01-01..." (string, not Date)
console.log(cloned.undef); // missing
```

**Real-world scenario:** I tried to clone an object with functions and they disappeared. Now I use `structuredClone()` (modern) or libraries like Lodash's `cloneDeep` for complex objects. JSON method only works for simple data.

---

<a id="question-88"></a>

### What can structuredClone() clone, and what can it not clone?

[Back to question index](#question-index)

**Answer:**

**Can clone:**
- Objects, arrays
- Date, RegExp
- Map, Set (with contents)
- ArrayBuffer, TypedArray
- Error objects
- Circular references

**Cannot clone:**
- Functions
- DOM nodes
- Class instances (becomes plain objects)
- Properties with getters/setters

```javascript
const obj = {
  date: new Date(),
  map: new Map([["key", "value"]]),
  fn: () => {}
};

const cloned = structuredClone(obj);
console.log(cloned.date instanceof Date); // true
console.log(cloned.map instanceof Map); // true
console.log(cloned.fn); // undefined
```

**Real-world scenario:** `structuredClone()` is my go-to for deep cloning now. It handles more cases than JSON.stringify and is built into modern browsers. For legacy support, I fall back to libraries or implement custom cloning logic.

---

<a id="question-89"></a>

### Are JavaScript strings mutable?

[Back to question index](#question-index)

**Answer:**

No, JavaScript strings are immutable:

```javascript
let str = "hello";
str[0] = "H"; // Fails silently
console.log(str); // "hello" (unchanged)

str = str.toUpperCase(); // Creates new string
console.log(str); // "HELLO"
```

**Real-world scenario:** String immutability means operations like `toUpperCase()`, `slice()`, `replace()` always return new strings. This is why string concatenation in loops can be slow - each concatenation creates a new string. For performance, I use array `join()` for many concatenations.

---

<a id="question-90"></a>

### What is the difference between substring() and slice()?

[Back to question index](#question-index)

**Answer:**

**substring()** - Swaps arguments if start > end, treats negative as 0:
```javascript
const str = "hello";
str.substring(3, 1); // "el" (swaps to 1, 3)
str.substring(-1); // "hello" (negative becomes 0)
```

**slice()** - Returns empty if start > end, supports negative from end:
```javascript
str.slice(3, 1); // "" (empty)
str.slice(-1); // "o" (last character)
str.slice(1, -1); // "ell"
```

**Real-world scenario:** I prefer `slice()` because negative indices are useful (like getting last N characters). `substring()` is mostly for legacy code. Both handle start/end beyond length gracefully.

---

<a id="question-91"></a>

### How do replace() and replaceAll() differ?

[Back to question index](#question-index)

**Answer:**

**replace()** - Replaces first occurrence:
```javascript
const str = "hello world hello";
str.replace("hello", "hi"); // "hi world hello"
str.replace(/hello/g, "hi"); // "hi world hi" (with global flag)
```

**replaceAll()** - Replaces all occurrences:
```javascript
str.replaceAll("hello", "hi"); // "hi world hi"
```

**Real-world scenario:** I use `replaceAll()` for simple all-replacements. Before it was available, I used `replace()` with global regex. Note that `replaceAll()` with a regex still needs the global flag, which is a common gotcha.

---

<a id="question-92"></a>

### Why can reversing a string with split("") produce incorrect results for some Unicode characters?

[Back to question index](#question-index)

**Answer:**

Some Unicode characters are made of multiple code points (surrogate pairs, combining characters):

```javascript
const str = "hello 👋";
const reversed = str.split("").reverse().join("");
console.log(reversed); // " ��olleh" (broken emoji!)
```

**Correct approach with Array.from:**
```javascript
const reversed = Array.from(str).reverse().join("");
console.log(reversed); // "👋 olleh" (correct!)
```

**Real-world scenario:** I had a bug where reversing strings with emojis broke them. `Array.from()` (or spread operator) correctly handles Unicode by iterating over grapheme clusters. This is important for international applications.

---

## Promises, Async/Await & Event Loop

<a id="question-93"></a>

### Is JavaScript single-threaded, and how can it handle asynchronous operations?

[Back to question index](#question-index)

**Answer:**

JavaScript is single-threaded - it can only do one thing at a time. But it uses an event loop to handle async operations:

1. Main thread executes code
2. Async operations (fetch, setTimeout) are offloaded to browser APIs
3. When async operation completes, callback goes to task queue
4. Event loop moves callbacks from queue to call stack when stack is empty

```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
console.log("3");
// Output: 1, 3, 2
```

**Real-world scenario:** Understanding this helped me debug why setTimeout with 0ms didn't run immediately. The event loop prioritizes synchronous code first. This is crucial for understanding execution order in async code.

---

<a id="question-94"></a>

### What are the call stack, task queue, and microtask queue?

[Back to question index](#question-index)

**Answer:**

**Call stack** - Where function execution happens:
```javascript
function a() { b(); }
function b() { console.log("b"); }
a(); // a and b are on call stack
```

**Task queue (macrotask queue)** - setTimeout, setInterval, I/O callbacks:
```javascript
setTimeout(() => console.log("task"), 0);
```

**Microtask queue** - Promise callbacks, queueMicrotask:
```javascript
Promise.resolve().then(() => console.log("microtask"));
```

**Execution order:** Call stack → Microtasks → Tasks

**Real-world scenario:** This explains why Promise callbacks run before setTimeout. Microtasks have higher priority. I use this knowledge to predict execution order and debug race conditions.

---

<a id="question-95"></a>

### How does the event loop work?

[Back to question index](#question-index)

**Answer:**

The event loop continuously:
1. Executes all code in call stack
2. When stack empty, processes all microtasks
3. When microtasks empty, processes one task
4. Repeats

```javascript
console.log("start");
setTimeout(() => console.log("timeout"), 0);
Promise.resolve().then(() => console.log("promise"));
console.log("end");
// Output: start, end, promise, timeout
```

**Real-world scenario:** Understanding the event loop helped me understand why async code doesn't block. It also helped me optimize code by knowing that microtasks (Promises) run before the next frame render, which is important for animations.

---

<a id="question-96"></a>

### What is the difference between synchronous and asynchronous execution?

[Back to question index](#question-index)

**Answer:**

**Synchronous** - Code blocks until complete:
```javascript
console.log("1");
const data = fs.readFileSync("file.txt"); // Blocks
console.log("2"); // Runs after file read
```

**Asynchronous** - Code doesn't block:
```javascript
console.log("1");
fs.readFile("file.txt", (err, data) => {
  console.log("2"); // Runs later
});
console.log("3"); // Runs immediately
```

**Real-world scenario:** In web apps, I use async for everything that might take time (API calls, file I/O) to avoid blocking the UI. Synchronous code can freeze the browser, which is terrible UX. Async keeps the app responsive.

---

<a id="question-97"></a>

### Why does setTimeout(callback, 0) not execute immediately?

[Back to question index](#question-index)

**Answer:**

Because of the event loop - setTimeout puts the callback in the task queue, which only runs after the call stack is empty and all microtasks are done:

```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
console.log("3");
// Output: 1, 3, 2
```

**Real-world scenario:** I used setTimeout(fn, 0) to defer code execution (like letting UI render before heavy computation). But I learned that Promise.resolve().then() is better for this because microtasks run sooner than tasks.

---

<a id="question-98"></a>

### What is the execution order of synchronous code, Promise callbacks, and timers?

[Back to question index](#question-index)

**Answer:**

**Order:**
1. Synchronous code
2. Microtasks (Promise callbacks)
3. Tasks (setTimeout, setInterval)

```javascript
console.log("sync 1");
Promise.resolve().then(() => console.log("microtask"));
setTimeout(() => console.log("timer"), 0);
console.log("sync 2");
// Output: sync 1, sync 2, microtask, timer
```

**Real-world scenario:** This knowledge is crucial for debugging async code. Once, I had a race condition where I expected a timer to run before a Promise callback, but it ran after. Understanding this order fixed the bug.

---

<a id="question-99"></a>

### What happens when a microtask schedules another microtask?

[Back to question index](#question-index)

**Answer:**

The new microtask is added to the end of the microtask queue and runs before any tasks:

```javascript
Promise.resolve().then(() => {
  console.log("microtask 1");
  Promise.resolve().then(() => {
    console.log("microtask 2");
  });
});
setTimeout(() => console.log("timer"), 0);
// Output: microtask 1, microtask 2, timer
```

**Real-world scenario:** This can cause infinite loops if not careful. I once had a Promise chain that kept scheduling new microtasks, blocking the UI forever. Now I'm cautious about recursive microtask scheduling.

---

<a id="question-100"></a>

### How can long-running JavaScript block the browser UI?

[Back to question index](#question-index)

**Answer:**

Since JavaScript is single-threaded, long computations block everything:

```javascript
// This freezes the browser for ~5 seconds
function heavy() {
  const start = Date.now();
  while (Date.now() - start < 5000) {
    // Busy wait
  }
}
heavy();
```

**Solutions:**
- Use Web Workers for heavy computation
- Break work into chunks with setTimeout
- Use requestIdleCallback for non-urgent work

**Real-world scenario:** I had a bug where processing a large CSV froze the browser. I fixed it by using a Web Worker to do the processing off the main thread. This kept the UI responsive while the heavy work ran in the background.

---

<a id="question-101"></a>

### What is callback hell, and how can it be avoided?

[Back to question index](#question-index)

**Answer:**

**Callback hell** - Deeply nested callbacks:
```javascript
getData((data) => {
  processData(data, (processed) => {
    saveData(processed, (saved) => {
      notifyUser(saved, () => {
        // And so on...
      });
    });
  });
});
```

**Avoid with:**
1. **Named functions:**
```javascript
function onData(data) { /* ... */ }
function onProcessed(processed) { /* ... */ }
getData(onData);
```

2. **Promises:**
```javascript
getData()
  .then(processData)
  .then(saveData)
  .then(notifyUser);
```

3. **Async/await:**
```javascript
const data = await getData();
const processed = await processData(data);
await saveData(processed);
await notifyUser(saved);
```

**Real-world scenario:** I refactored a legacy codebase from callback hell to async/await. The code went from unreadable nested functions to linear, easy-to-understand code. Async/await is now my go-to for async code.

---

<a id="question-102"></a>

### What are the states of a Promise?

[Back to question index](#question-index)

**Answer:**

**Three states:**
1. **Pending** - Initial state, not settled
2. **Fulfilled** - Operation completed successfully
3. **Rejected** - Operation failed

Once settled, a Promise cannot change state:

```javascript
const promise = new Promise((resolve, reject) => {
  // Pending state here
  resolve("success"); // Now fulfilled
  reject("error"); // Ignored - already settled
});
```

**Real-world scenario:** Understanding states helped me debug why some error handlers weren't running - the Promise was already fulfilled. Once settled, a Promise is immutable, which is good for predictability.

---

<a id="question-103"></a>

### Does a Promise executor run synchronously or asynchronously?

[Back to question index](#question-index)

**Answer:**

The executor runs synchronously:

```javascript
console.log("1");
const promise = new Promise((resolve) => {
  console.log("2"); // Runs synchronously
  resolve("3");
});
console.log("4");
// Output: 1, 2, 4
```

But the callbacks run asynchronously:

```javascript
promise.then((value) => console.log(value));
// Output: 1, 2, 4, 3
```

**Real-world scenario:** This surprised me when I tried to put async code in the executor expecting it to run asynchronously. Now I know: executor = sync, callbacks = async. I use the executor for setup, and the callbacks for handling results.

---

<a id="question-104"></a>

### What do .then(), .catch(), and .finally() return?

[Back to question index](#question-index)

**Answer:**

They all return new Promises, enabling chaining:

```javascript
Promise.resolve(1)
  .then(x => x + 1) // Returns Promise(2)
  .then(x => x * 2) // Returns Promise(4)
  .catch(err => { /* ... */ }) // Returns Promise
  .finally(() => { /* ... */ }); // Returns Promise
```

**Real-world scenario:** This is why Promise chaining works. Each handler returns a new Promise that resolves with the return value. I use this for sequential async operations and error handling that doesn't break the chain.

---

<a id="question-105"></a>

### How does returning a value or Promise from .then() affect the chain?

[Back to question index](#question-index)

**Answer:**

**Return value** - Wrapped in resolved Promise:
```javascript
Promise.resolve()
  .then(() => 42)
  .then(x => console.log(x)); // 42
```

**Return Promise** - Unwrapped and chained:
```javascript
Promise.resolve()
  .then(() => fetch("/api"))
  .then(response => response.json())
  .then(data => console.log(data));
```

**Real-world scenario:** This automatic unwrapping is what makes Promise chaining work. I don't need to manually resolve returned Promises - the chain handles it. This is cleaner than nested .then() callbacks.

---

<a id="question-106"></a>

### How are thrown errors propagated through a Promise chain?

[Back to question index](#question-index)

**Answer:**

Errors skip to the nearest .catch():

```javascript
Promise.resolve()
  .then(() => { throw new Error("Oops"); })
  .then(() => console.log("Never runs"))
  .catch(err => console.log(err.message)); // "Oops"
```

Rejections in later .then() also propagate:

```javascript
Promise.resolve()
  .then(() => Promise.reject("Failed"))
  .then(() => console.log("Never runs"))
  .catch(err => console.log(err)); // "Failed"
```

**Real-world scenario:** This makes error handling centralized - one .catch() at the end can handle errors from anywhere in the chain. I don't need error handlers in every .then(), which keeps code clean.

---

<a id="question-107"></a>

### What happens if you forget to return a Promise inside .then()?

[Back to question index](#question-index)

**Answer:**

The Promise runs independently (fire and forget):

```javascript
Promise.resolve()
  .then(() => {
    fetch("/api"); // Forgot return!
  })
  .then(() => {
    // This runs before fetch completes!
  });
```

**Correct:**
```javascript
Promise.resolve()
  .then(() => {
    return fetch("/api"); // Return it!
  })
  .then(() => {
    // This runs after fetch completes
  });
```

**Real-world scenario:** I had a bug where UI updated before data loaded because I forgot to return the Promise. Now I always return Promises in .then() when I need to wait for them. Async/await makes this mistake less likely.

---

<a id="question-108"></a>

### What are the differences between Promise.all(), allSettled(), race(), and any()?

[Back to question index](#question-index)

**Answer:**

**Promise.all()** - All must resolve, one rejects = all reject:
```javascript
Promise.all([p1, p2, p3])
  .then(results => console.log(results)) // [r1, r2, r3]
  .catch(err => console.log(err)); // If any reject
```

**Promise.allSettled()** - Waits for all, never rejects:
```javascript
Promise.allSettled([p1, p2, p3])
  .then(results => console.log(results));
// [{status: "fulfilled", value: ...}, ...]
```

**Promise.race()** - First to settle wins:
```javascript
Promise.race([p1, p2, p3])
  .then(result => console.log(result)); // First to resolve/reject
```

**Promise.any()** - First to resolve wins:
```javascript
Promise.any([p1, p2, p3])
  .then(result => console.log(result)); // First to resolve
```

**Real-world scenario:** I use `all` for parallel operations where all must succeed, `allSettled` when I need all results regardless of failures, `race` for timeouts, and `any` for fallback servers (first response wins).

---

<a id="question-109"></a>

### Does Promise.all() cancel the remaining operations when one rejects?

[Back to question index](#question-index)

**Answer:**

No, remaining operations continue running:

```javascript
const p1 = new Promise(resolve => setTimeout(() => resolve(1), 1000));
const p2 = new Promise((_, reject) => setTimeout(() => reject("Error"), 500));
const p3 = new Promise(resolve => setTimeout(() => resolve(3), 2000));

Promise.all([p1, p2, p3])
  .catch(err => console.log(err)); // "Error" after 500ms
// p1 and p3 still running in background!
```

**Real-world scenario:** This can waste resources. For cancellation, I use AbortController or check if the Promise is still needed before doing work. I don't rely on Promise.all rejection to stop background work.

---

<a id="question-110"></a>

### Does Promise.all() preserve input order in its results?

[Back to question index](#question-index)

**Answer:**

Yes, results are in the same order as input Promises:

```javascript
const p1 = Promise.resolve(1);
const p2 = new Promise(resolve => setTimeout(() => resolve(2), 1000));
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3])
  .then(results => console.log(results)); // [1, 2, 3] (preserved order)
```

**Real-world scenario:** This is great for maintaining correspondence between inputs and results. I use it when fetching multiple related resources - the results array always matches the order of the requests array.

---

<a id="question-111"></a>

### What happens when each Promise combinator receives an empty iterable?

[Back to question index](#question-index)

**Answer:**

**Promise.all([])** - Resolves with empty array:
```javascript
Promise.all([]).then(results => console.log(results)); // []
```

**Promise.allSettled([])** - Resolves with empty array:
```javascript
Promise.allSettled([]).then(results => console.log(results)); // []
```

**Promise.race([])** - Never settles (hangs forever):
```javascript
Promise.race([]); // Never resolves or rejects
```

**Promise.any([])** - Rejects with AggregateError:
```javascript
Promise.any([]).catch(err => console.log(err)); // AggregateError
```

**Real-world scenario:** The hanging `Promise.race([])` caught me off guard. Now I always check for empty arrays before using race. For dynamic arrays, I add a fallback: `Promise.race(promises.length ? promises : [fallback])`.

---

<a id="question-112"></a>

### What is an AggregateError?

[Back to question index](#question-index)

**Answer:**

An error that contains multiple errors:

```javascript
Promise.any([
  Promise.reject("Error 1"),
  Promise.reject("Error 2"),
  Promise.reject("Error 3")
]).catch(err => {
  console.log(err instanceof AggregateError); // true
  console.log(err.errors); // ["Error 1", "Error 2", "Error 3"]
});
```

**Real-world scenario:** I use this with `Promise.any()` to see all the rejection reasons when all Promises fail. It's useful for debugging why multiple fallback options all failed.

---

<a id="question-113"></a>

### What does an async function always return?

[Back to question index](#question-index)

**Answer:**

An async function always returns a Promise:

```javascript
async function getData() {
  return 42;
}

const result = getData();
console.log(result instanceof Promise); // true
result.then(x => console.log(x)); // 42
```

Even if you don't explicitly return:

```javascript
async function noReturn() {
  console.log("No return");
}
noReturn().then(x => console.log(x)); // undefined
```

**Real-world scenario:** This means I can call async functions from non-async code and handle the Promise, or use async/await inside other async functions. It also means async functions can be used anywhere Promises are expected.

---

<a id="question-114"></a>

### Does await block the entire JavaScript thread?

[Back to question index](#question-index)

**Answer:**

No, await only blocks the async function, not the entire thread:

```javascript
async function main() {
  console.log("1");
  await Promise.resolve();
  console.log("2");
}

console.log("start");
main();
console.log("end");
// Output: start, 1, end, 2
```

The function pauses at await, but other code can run.

**Real-world scenario:** This is why async/await doesn't freeze the UI. The await yields control back to the event loop, allowing other code to run. I can have multiple async functions "waiting" concurrently without blocking each other.

---

<a id="question-115"></a>

### How do you handle errors with async/await?

[Back to question index](#question-index)

**Answer:**

**try/catch:**
```javascript
async function fetchData() {
  try {
    const response = await fetch("/api");
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error:", error);
    throw error; // Re-throw or handle
  }
}
```

**catch() on Promise:**
```javascript
fetchData()
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

**Real-world scenario:** I prefer try/catch for error handling in async functions - it's more like synchronous code and easier to read. I use catch() on the Promise when calling from non-async code or when I want centralized error handling.

---

<a id="question-116"></a>

### What is the difference between sequential and concurrent asynchronous operations?

[Back to question index](#question-index)

**Answer:**

**Sequential** - One after another:
```javascript
const data1 = await fetch("/api/1");
const data2 = await fetch("/api/2");
const data3 = await fetch("/api/3");
// Total time = sum of all
```

**Concurrent** - All at once:
```javascript
const [data1, data2, data3] = await Promise.all([
  fetch("/api/1"),
  fetch("/api/2"),
  fetch("/api/3")
]);
// Total time = slowest one
```

**Real-world scenario:** I use concurrent operations for independent tasks (like fetching multiple API endpoints) to reduce total time. Sequential is for dependent tasks (where step 2 needs step 1's result). Concurrency can significantly improve performance.

---

<a id="question-117"></a>

### Why does forEach(async () => ...) not wait for its callbacks?

[Back to question index](#question-index)

**Answer:**

forEach doesn't handle Promises - it just calls the function:

```javascript
const results = [];
[1, 2, 3].forEach(async (num) => {
  const result = await fetch(`/api/${num}`);
  results.push(result);
});
console.log(results); // [] (empty - forEach didn't wait)
```

**Solutions:**
```javascript
// 1. for...of
for (const num of [1, 2, 3]) {
  const result = await fetch(`/api/${num}`);
  results.push(result);
}

// 2. Promise.all
await Promise.all([1, 2, 3].map(async (num) => {
  const result = await fetch(`/api/${num}`);
  results.push(result);
}));
```

**Real-world scenario:** I wasted hours debugging why forEach with async didn't work as expected. Now I use for...of for sequential async loops and Promise.all with map for concurrent operations.

---

<a id="question-118"></a>

### How would you process asynchronous tasks sequentially?

[Back to question index](#question-index)

**Answer:**

**Using for...of:**
```javascript
async function processSequentially(items) {
  for (const item of items) {
    await process(item);
  }
}
```

**Using reduce:**
```javascript
async function processSequentially(items) {
  await items.reduce(async (promise, item) => {
    await promise;
    await process(item);
  }, Promise.resolve());
}
```

**Real-world scenario:** I use for...of for readability when processing items sequentially. It's cleaner than reduce and easier to understand. I use this when each operation depends on the previous one completing.

---

<a id="question-119"></a>

### How would you limit the number of concurrent asynchronous tasks?

[Back to question index](#question-index)

**Answer:**

**Using a pool:**
```javascript
async function limitConcurrency(tasks, limit) {
  const results = [];
  const executing = [];

  for (const task of tasks) {
    const promise = task().then(result => {
      executing.splice(executing.indexOf(promise), 1);
      return result;
    });

    results.push(promise);
    executing.push(promise);

    if (executing.length >= limit) {
      await Promise.race(executing);
    }
  }

  return Promise.all(results);
}
```

**Real-world scenario:** I use this when hitting rate-limited APIs - I can only make 5 requests per second, so I limit concurrency to 5. This prevents hitting rate limits while still being faster than sequential processing.

---

<a id="question-120"></a>

### Can a Promise itself be cancelled, and how does AbortController help cancel an operation?

[Back to question index](#question-index)

**Answer:**

Promises cannot be cancelled directly. AbortController is the standard way:

```javascript
const controller = new AbortController();

fetch("/api", { signal: controller.signal })
  .then(response => response.json())
  .catch(err => {
    if (err.name === "AbortError") {
      console.log("Request cancelled");
    }
  });

// Cancel after 1 second
setTimeout(() => controller.abort(), 1000);
```

**Real-world scenario:** I use AbortController for:
- Canceling API requests when user navigates away
- Implementing request timeouts
- Canceling long-running operations when user clicks cancel
- Cleaning up requests in React useEffect cleanup

---

## API Handling & Production Scenarios

<a id="question-121"></a>

### Does fetch() reject automatically for HTTP errors such as 404 or 500?

[Back to question index](#question-index)

**Answer:**

No, fetch only rejects on network errors. HTTP errors (404, 500) are considered successful responses:

```javascript
fetch("/not-found")
  .then(response => {
    console.log(response.ok); // false
    console.log(response.status); // 404
    return response.json(); // This might fail
  })
  .catch(err => {
    // Only runs on network error, not 404
  });
```

**Real-world scenario:** I had a bug where 404 errors weren't caught. Now I always check `response.ok` and throw manually:
```javascript
const response = await fetch("/api");
if (!response.ok) throw new Error(`HTTP ${response.status}`);
```

---

<a id="question-122"></a>

### How do you distinguish network failures, HTTP failures, and response-parsing failures?

[Back to question index](#question-index)

**Answer:**

```javascript
async function safeFetch(url) {
  try {
    const response = await fetch(url);

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}: ${response.statusText}`);
    }

    try {
      const data = await response.json();
      return data;
    } catch (parseError) {
      throw new Error("Failed to parse response");
    }
  } catch (networkError) {
    if (networkError.name === "TypeError") {
      throw new Error("Network failure");
    }
    throw networkError;
  }
}
```

**Real-world scenario:** I separate these error types because they need different handling - network errors might need retry, HTTP errors might need different UI, parse errors might indicate API contract changes.

---

<a id="question-123"></a>

### Why should you check response.ok?

[Back to question index](#question-index)

**Answer:**

`response.ok` is true for status 200-299, false otherwise:

```javascript
const response = await fetch("/api");
if (!response.ok) {
  // Handle 404, 500, etc.
  throw new Error(`Request failed: ${response.status}`);
}
```

Without this check, you might process error responses as successful data.

**Real-world scenario:** I once processed a 500 error response as if it were valid data, causing bugs downstream. Now I always check `response.ok` before processing the response body.

---

<a id="question-124"></a>

### Can you read a response body more than once?

[Back to question index](#question-index)

**Answer:**

No, response bodies can only be read once:

```javascript
const response = await fetch("/api");
const data1 = await response.json();
const data2 = await response.json(); // Error: Body already consumed
```

**To read multiple times, clone first:**
```javascript
const response = await fetch("/api");
const clone = response.clone();
const data1 = await response.json();
const data2 = await clone.json();
```

**Real-world scenario:** I needed to log the response and also process it. Cloning the response let me do both. This is also useful when you need to check the response before fully consuming it.

---

<a id="question-125"></a>

### How do you cancel an API request?

[Back to question index](#question-index)

**Answer:**

Using AbortController:

```javascript
const controller = new AbortController();

fetch("/api", { signal: controller.signal })
  .then(response => response.json())
  .catch(err => {
    if (err.name === "AbortError") {
      console.log("Cancelled");
    }
  });

// Cancel
controller.abort();
```

**Real-world scenario:** In React, I cancel requests in useEffect cleanup:
```javascript
useEffect(() => {
  const controller = new AbortController();
  fetch("/api", { signal: controller.signal });
  return () => controller.abort();
}, []);
```

This prevents state updates on unmounted components.

---

<a id="question-126"></a>

### How do you prevent an older API response from overwriting newer results?

[Back to question index](#question-index)

**Answer:**

**Using a sequence number:**
```javascript
let requestId = 0;

async function fetchData() {
  const currentId = ++requestId;
  const data = await fetch("/api").then(r => r.json());

  if (currentId === requestId) {
    setState(data); // Only update if still current
  }
}
```

**Using AbortController:**
```javascript
let controller;

async function fetchData() {
  if (controller) controller.abort();
  controller = new AbortController();

  try {
    const data = await fetch("/api", { signal: controller.signal });
    setState(data);
  } catch (err) {
    if (err.name !== "AbortError") throw err;
  }
}
```

**Real-world scenario:** In search autocomplete, rapid typing triggers many requests. Without this, old responses could overwrite newer ones. AbortController or sequence numbers ensure only the latest response updates the UI.

---

<a id="question-127"></a>

### How would you implement request timeouts?

[Back to question index](#question-index)

**Answer:**

**Using Promise.race:**
```javascript
async function fetchWithTimeout(url, timeout = 5000) {
  const controller = new AbortController();
  const timeoutId = setTimeout(() => controller.abort(), timeout);

  try {
    const response = await fetch(url, { signal: controller.signal });
    clearTimeout(timeoutId);
    return response;
  } catch (err) {
    clearTimeout(timeoutId);
    if (err.name === "AbortError") {
      throw new Error("Request timeout");
    }
    throw err;
  }
}
```

**Real-world scenario:** I add timeouts to all API calls to prevent hanging indefinitely. Without timeouts, a slow server could make the app feel frozen. 5-10 seconds is a reasonable default for most web apps.

---

<a id="question-128"></a>

### What is exponential backoff?

[Back to question index](#question-index)

**Answer:**

Exponential backoff increases delay between retries exponentially:

```javascript
async function fetchWithBackoff(url, maxRetries = 3) {
  let delay = 1000; // Start with 1 second

  for (let i = 0; i < maxRetries; i++) {
    try {
      const response = await fetch(url);
      if (response.ok) return response;
      throw new Error(`HTTP ${response.status}`);
    } catch (err) {
      if (i === maxRetries - 1) throw err;
      await new Promise(resolve => setTimeout(resolve, delay));
      delay *= 2; // Double the delay
    }
  }
}
```

**Real-world scenario:** I use this for retrying failed requests. Exponential backoff gives the server time to recover without overwhelming it. The delay grows: 1s, 2s, 4s, 8s, etc.

---

<a id="question-129"></a>

### Why should retry logic include jitter?

[Back to question index](#question-index)

**Answer:**

Without jitter, all clients retry at the same time, causing thundering herd:

```javascript
// Without jitter - all retry at exactly 1s, 2s, 4s
delay = baseDelay * Math.pow(2, attempt);

// With jitter - random variation
delay = baseDelay * Math.pow(2, attempt) * (0.5 + Math.random());
```

**Real-world scenario:** When a server fails, all clients retrying simultaneously can overwhelm it again. Jitter spreads out the retries, making the system more resilient. It's a simple addition that significantly improves stability.

---

<a id="question-130"></a>

### Which requests are safe to retry, and how does idempotency affect that decision?

[Back to question index](#question-index)

**Answer:**

**Safe to retry (idempotent):**
- GET requests
- HEAD requests
- PUT requests (if designed to be idempotent)
- DELETE requests (usually idempotent)

**Not safe to retry (non-idempotent):**
- POST requests (creates new resource each time)
- PATCH requests (can have different effects)

**Real-world scenario:** I never retry POST requests automatically - they might create duplicate orders or charges. For POST, I show an error and let the user decide to retry. GET requests are safe to retry as they don't modify data.

---

<a id="question-131"></a>

### How should a client handle 429 Too Many Requests and Retry-After?

[Back to question index](#question-index)

**Answer:**

```javascript
async function fetchWithRateLimit(url) {
  const response = await fetch(url);

  if (response.status === 429) {
    const retryAfter = response.headers.get("Retry-After");
    const delay = retryAfter ? parseInt(retryAfter) * 1000 : 5000;
    await new Promise(resolve => setTimeout(resolve, delay));
    return fetchWithRateLimit(url); // Retry
  }

  return response;
}
```

**Real-world scenario:** APIs often have rate limits. When I get 429, I respect the Retry-After header (if provided) or wait a default delay before retrying. This prevents getting blocked and is respectful of the API's limits.

---

<a id="question-132"></a>

### How would you prevent duplicate API requests?

[Back to question index](#question-index)

**Answer:**

**Using a pending requests map:**
```javascript
const pendingRequests = new Map();

async function fetchOnce(url) {
  if (pendingRequests.has(url)) {
    return pendingRequests.get(url);
  }

  const promise = fetch(url).then(r => r.json());
  pendingRequests.set(url, promise);

  try {
    return await promise;
  } finally {
    pendingRequests.delete(url);
  }
}
```

**Real-world scenario:** In React, I use this to prevent duplicate requests when the same component mounts multiple times or when users click a button rapidly. It saves bandwidth and prevents race conditions.

---

<a id="question-133"></a>

### How would you cache API results and expire stale entries?

[Back to question index](#question-index)

**Answer:**

```javascript
const cache = new Map();

async function fetchWithCache(url, ttl = 60000) {
  const cached = cache.get(url);

  if (cached && Date.now() - cached.timestamp < ttl) {
    return cached.data;
  }

  const data = await fetch(url).then(r => r.json());
  cache.set(url, { data, timestamp: Date.now() });
  return data;
}
```

**Real-world scenario:** I cache GET requests that don't change often (like user profiles, configuration). This reduces API calls and improves performance. The TTL ensures data doesn't get too stale.

---

<a id="question-134"></a>

### How would you implement debounced search?

[Back to question index](#question-index)

**Answer:**

```javascript
function debounce(fn, delay) {
  let timeoutId;

  return function(...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  };
}

const debouncedSearch = debounce(async (query) => {
  const results = await fetch(`/search?q=${query}`);
  return results.json();
}, 300);

// Usage
input.addEventListener("input", (e) => {
  debouncedSearch(e.target.value);
});
```

**Real-world scenario:** I debounce search inputs to avoid making an API call for every keystroke. A 300ms delay means the user can type "hello" and only one API call is made for "hello", not one for each letter.

---

<a id="question-135"></a>

### How would you combine debouncing with cancellation of previous requests?

[Back to question index](#question-index)

**Answer:**

```javascript
let controller;
let timeoutId;

function debouncedFetch(query, delay = 300) {
  clearTimeout(timeoutId);
  if (controller) controller.abort();

  timeoutId = setTimeout(async () => {
    controller = new AbortController();
    try {
      const results = await fetch(`/search?q=${query}`, {
        signal: controller.signal
      });
      return results.json();
    } catch (err) {
      if (err.name !== "AbortError") throw err;
    }
  }, delay);
}
```

**Real-world scenario:** This is the best pattern for search - debounce prevents too many requests, and cancellation ensures old results don't overwrite newer ones. I use this in all autocomplete implementations.

---

<a id="question-136"></a>

### How would you fetch independent resources concurrently?

[Back to question index](#question-index)

**Answer:**

```javascript
const [users, posts, comments] = await Promise.all([
  fetch("/api/users").then(r => r.json()),
  fetch("/api/posts").then(r => r.json()),
  fetch("/api/comments").then(r => r.json())
]);
```

**Real-world scenario:** When a page needs data from multiple independent endpoints, I fetch them concurrently instead of sequentially. This can reduce load time from 3 seconds (1+1+1) to 1 second (max of 1, 1, 1).

---

<a id="question-137"></a>

### How would you display partial results when some requests fail?

[Back to question index](#question-index)

**Answer:**

```javascript
const results = await Promise.allSettled([
  fetch("/api/users").then(r => r.json()),
  fetch("/api/posts").then(r => r.json()),
  fetch("/api/comments").then(r => r.json())
]);

results.forEach((result, index) => {
  if (result.status === "fulfilled") {
    console.log(`Success ${index}:`, result.value);
  } else {
    console.log(`Failed ${index}:`, result.reason);
  }
});
```

**Real-world scenario:** In a dashboard, if one API fails, I still want to show the data from the others. `allSettled` lets me handle successes and failures separately, providing a better UX than all-or-nothing.

---

<a id="question-138"></a>

### How would you prevent multiple simultaneous token-refresh requests?

[Back to question index](#question-index)

**Answer:**

```javascript
let refreshPromise = null;

async function getValidToken() {
  const token = getToken();

  if (isTokenValid(token)) {
    return token;
  }

  if (refreshPromise) {
    return refreshPromise; // Wait for existing refresh
  }

  refreshPromise = refreshToken()
    .then(newToken => {
      setToken(newToken);
      return newToken;
    })
    .finally(() => {
      refreshPromise = null;
    });

  return refreshPromise;
}
```

**Real-world scenario:** When multiple API calls happen simultaneously and the token is expired, they all try to refresh. This pattern ensures only one refresh happens, and all calls wait for the same new token.

---

<a id="question-139"></a>

### How would you handle pagination and prevent duplicate records?

[Back to question index](#question-index)

**Answer:**

```javascript
let allData = [];
let lastId = null;
let isLoading = false;

async function loadMore() {
  if (isLoading) return;

  isLoading = true;
  const url = lastId ? `/api?after=${lastId}` : "/api";

  const newData = await fetch(url).then(r => r.json());

  // Filter duplicates
  const uniqueNewData = newData.filter(
    item => !allData.some(existing => existing.id === item.id)
  );

  allData = [...allData, ...uniqueNewData];
  lastId = newData[newData.length - 1]?.id;
  isLoading = false;

  return uniqueNewData;
}
```

**Real-world scenario:** I use cursor-based pagination (lastId) instead of offset-based for better performance. I also filter duplicates to handle cases where records might be returned twice due to concurrent modifications.

---

<a id="question-140"></a>

### How would you implement optimistic updates and rollback on failure?

[Back to question index](#question-index)

**Answer:**

```javascript
async function updateItem(id, updates) {
  // Optimistic update
  const previousState = [...items];
  const optimisticItems = items.map(item =>
    item.id === id ? { ...item, ...updates } : item
  );
  setItems(optimisticItems);

  try {
    const result = await fetch(`/api/items/${id}`, {
      method: "PATCH",
      body: JSON.stringify(updates)
    });

    if (!result.ok) throw new Error("Update failed");

    return await result.json();
  } catch (err) {
    // Rollback on failure
    setItems(previousState);
    throw err;
  }
}
```

**Real-world scenario:** Optimistic updates make the UI feel instant. If the API call fails, I rollback to the previous state. This provides a snappy experience while handling errors gracefully. I use this for likes, comments, and other quick actions.

---

## DOM, Events & Browser APIs

<a id="question-141"></a>

### What is the DOM?

[Back to question index](#question-index)

**Answer:**

The DOM (Document Object Model) is a tree-like representation of HTML that JavaScript can interact with:

```html
<div id="app">
  <h1>Hello</h1>
  <p>World</p>
</div>
```

```javascript
const h1 = document.querySelector("h1");
h1.textContent = "Changed"; // Updates DOM
```

**Real-world scenario:** The DOM is how JavaScript changes the page dynamically. When I update a React component's state, React updates the DOM behind the scenes. Understanding the DOM helps debug performance issues and understand how frameworks work.

---

<a id="question-142"></a>

### What is the difference between querySelector() and querySelectorAll()?

[Back to question index](#question-index)

**Answer:**

**querySelector()** - Returns first matching element:
```javascript
const element = document.querySelector(".item"); // First .item
```

**querySelectorAll()** - Returns all matching elements as NodeList:
```javascript
const elements = document.querySelectorAll(".item"); // All .items
```

**Real-world scenario:** I use `querySelector` when I need a single element (like finding a button), and `querySelectorAll` when I need all elements (like finding all list items). `querySelectorAll` returns a NodeList, which has `forEach` in modern browsers.

---

<a id="question-143"></a>

### What is the difference between a live collection and a static collection?

[Back to question index](#question-index)

**Answer:**

**Live collection** - Updates when DOM changes:
```javascript
const live = document.getElementsByClassName("item");
// If you add a .item to DOM, live automatically updates
```

**Static collection** - Snapshot at time of query:
```javascript
const static = document.querySelectorAll(".item");
// Adding .item to DOM doesn't affect static
```

**Real-world scenario:** Live collections (like `getElementsByClassName`) can cause performance issues if the DOM changes frequently. I prefer `querySelectorAll` (static) for predictable behavior and better performance in most cases.

---

<a id="question-144"></a>

### What is the difference between textContent, innerText, and innerHTML?

[Back to question index](#question-index)

**Answer:**

**textContent** - Gets/sets text content (fast, safe):
```javascript
element.textContent = "<script>alert('xss')</script>";
// Sets literal text, doesn't execute
```

**innerText** - Gets rendered text (slow, respects CSS):
```javascript
element.innerText; // Text as it appears to user (hidden elements excluded)
```

**innerHTML** - Gets/sets HTML (dangerous if untrusted):
```javascript
element.innerHTML = "<b>Bold</b>"; // Renders HTML
element.innerHTML = user input; // XSS risk!
```

**Real-time scenario:** I use `textContent` for setting text (safe from XSS), `innerHTML` only for trusted HTML, and avoid `innerText` (slow and inconsistent). For user input, always use `textContent` to prevent XSS attacks.

---

<a id="question-145"></a>

### What are event capturing, target, and bubbling phases?

[Back to question index](#question-index)

**Answer:**

**Capturing phase** - Event goes from root to target:
```javascript
element.addEventListener("click", handler, true); // true = capture
```

**Target phase** - Event reaches target element

**Bubbling phase** - Event bubbles from target to root (default):
```javascript
element.addEventListener("click", handler); // false = bubble
```

```html
<div id="outer">
  <div id="inner">Click me</div>
</div>
```

Clicking inner: outer (capture) → inner (target) → outer (bubble)

**Real-world scenario:** Most of the time I use bubbling (default). Capturing is rare but useful for intercepting events before they reach children. Understanding phases helps with event delegation and debugging why events aren't firing as expected.

---

<a id="question-146"></a>

### What is event delegation, and when is it useful?

[Back to question index](#question-index)

**Answer:**

Event delegation attaches one listener to a parent to handle events on children:

```javascript
// Instead of:
items.forEach(item => item.addEventListener("click", handler));

// Use delegation:
list.addEventListener("click", (e) => {
  if (e.target.matches(".item")) {
    handler(e);
  }
});
```

**Useful when:**
- Many similar elements
- Dynamic elements (added/removed)
- Performance (one listener vs many)

**Real-world scenario:** I use event delegation for lists, tables, and grids where items are added dynamically. Instead of adding listeners to each item, I add one to the container. This is more efficient and handles dynamic elements automatically.

---

<a id="question-147"></a>

### What is the difference between event.target and event.currentTarget?

[Back to question index](#question-index)

**Answer:**

**event.target** - The element that was actually clicked:
```javascript
<div onclick="handle(event)">
  <button>Click me</button>
</div>

function handle(e) {
  console.log(e.target); // button
  console.log(e.currentTarget); // div
}
```

**event.currentTarget** - The element the listener is attached to

**Real-world scenario:** I use `target` to know which child was clicked (for delegation), and `currentTarget` to know which element has the listener. This distinction is crucial for event delegation patterns.

---

<a id="question-148"></a>

### What is the difference between preventDefault(), stopPropagation(), and stopImmediatePropagation()?

[Back to question index](#question-index)

**Answer:**

**preventDefault()** - Stops default behavior:
```javascript
form.addEventListener("submit", (e) => {
  e.preventDefault(); // Don't submit form
});
```

**stopPropagation()** - Stops event from bubbling/capturing further:
```javascript
child.addEventListener("click", (e) => {
  e.stopPropagation(); // Parent won't see this click
});
```

**stopImmediatePropagation()** - Stops other listeners on same element:
```javascript
element.addEventListener("click", handler1);
element.addEventListener("click", (e) => {
  e.stopImmediatePropagation(); // handler2 won't run
});
element.addEventListener("click", handler2);
```

**Real-world scenario:** I use `preventDefault` for form validation, `stopPropagation` to prevent parent handlers from running (like in nested clickable elements), and `stopImmediatePropagation` rarely (only when I need complete control over listener execution).

---

<a id="question-149"></a>

### Why must you preserve the callback reference when removing an event listener?

[Back to question index](#question-index)

**Answer:**

Event listeners are removed by reference, not by function code:

```javascript
// Won't work - different function reference
element.addEventListener("click", () => console.log("click"));
element.removeEventListener("click", () => console.log("click"));

// Works - same reference
const handler = () => console.log("click");
element.addEventListener("click", handler);
element.removeEventListener("click", handler);
```

**Real-world scenario:** In React, I save the handler in a ref or use useCallback to maintain the same reference when removing listeners. This is a common bug - the listener isn't removed because the function reference changed.

---

<a id="question-150"></a>

### What do the once, passive, and signal listener options do?

[Back to question index](#question-index)

**Answer:**

**once** - Listener runs once then auto-removes:
```javascript
element.addEventListener("click", handler, { once: true });
```

**passive** - Improves scroll performance (can't preventDefault):
```javascript
element.addEventListener("touchstart", handler, { passive: true });
```

**signal** - Listener can be removed via AbortController:
```javascript
const controller = new AbortController();
element.addEventListener("click", handler, { signal: controller.signal });
controller.abort(); // Listener removed
```

**Real-world scenario:** I use `passive: true` for scroll/touch events to improve performance (browser knows you won't call preventDefault). `once` is great for one-time handlers. `signal` is the modern way to remove listeners (cleaner than removeEventListener).

---

<a id="question-151"></a>

### How do you handle events on dynamically added elements?

[Back to question index](#question-index)

**Answer:**

**Event delegation (recommended):**
```javascript
container.addEventListener("click", (e) => {
  if (e.target.matches(".dynamic-item")) {
    // Handle click on dynamically added item
  }
});
```

**Or add listener when element is created:**
```javascript
function createItem() {
  const item = document.createElement("div");
  item.className = "dynamic-item";
  item.addEventListener("click", handler);
  container.appendChild(item);
}
```

**Real-world scenario:** Event delegation is my go-to for dynamic elements. It's simpler - I don't need to add/remove listeners as elements are added/removed. The container handles everything.

---

<a id="question-152"></a>

### What is the difference between debounce and throttle?

[Back to question index](#question-index)

**Answer:**

**Debounce** - Run after delay from last event:
```javascript
// Input "hello" → runs once after 300ms of no typing
input.addEventListener("input", debounce(handler, 300));
```

**Throttle** - Run at most once per delay:
```javascript
// Scroll → runs at most once every 100ms
window.addEventListener("scroll", throttle(handler, 100));
```

**Real-world scenario:** I use debounce for inputs (search, autocomplete) - user finishes typing before action runs. I use throttle for scroll/resize events - action runs periodically but not too frequently. Both improve performance.

---

<a id="question-153"></a>

### How does requestAnimationFrame() differ from setTimeout()?

[Back to question index](#question-index)

**Answer:**

**requestAnimationFrame** - Syncs with browser repaint (60fps):
```javascript
function animate() {
  element.style.transform = `translateX(${x}px)`;
  requestAnimationFrame(animate);
}
```

**setTimeout** - Runs after delay, not synced to repaint:
```javascript
setTimeout(() => {
  element.style.transform = `translateX(${x}px)`;
}, 16); // ~60fps but not guaranteed
```

**Real-world scenario:** I use `requestAnimationFrame` for animations - it's smoother, pauses when tab is inactive (saves battery), and syncs with the display. `setTimeout` is for general timing, not animations.

---

<a id="question-154"></a>

### What is IntersectionObserver, and how would you use it for infinite scrolling?

[Back to question index](#question-index)

**Answer:**

IntersectionObserver detects when elements enter/leave viewport:

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      loadMoreItems();
    }
  });
}, { threshold: 0.1 });

observer.observe(sentinelElement);
```

**Infinite scroll:**
```javascript
function loadMoreItems() {
  // Fetch and append items
  // New sentinel is last item
  observer.observe(newSentinel);
}
```

**Real-world scenario:** I use IntersectionObserver for lazy loading images and infinite scroll. It's more performant than scroll event listeners because the browser handles the detection efficiently.

---

<a id="question-155"></a>

### What is ResizeObserver, and when is it useful?

[Back to question index](#question-index)

**Answer:**

ResizeObserver detects when element size changes:

```javascript
const observer = new ResizeObserver(entries => {
  entries.forEach(entry => {
    console.log("Size changed:", entry.contentRect);
  });
});

observer.observe(element);
```

**Useful for:**
- Responsive layouts without media queries
- Canvas resizing
- Charts that need to redraw on resize

**Real-world scenario:** I use ResizeObserver when I need to respond to element size changes (not just window resize). For example, resizing a chart when its container changes size. It's more precise than window resize listeners.

---

<a id="question-156"></a>

### What is the difference between localStorage, sessionStorage, and cookies?

[Back to question index](#question-index)

**Answer:**

**localStorage** - Persists indefinitely (5-10MB):
```javascript
localStorage.setItem("key", "value");
localStorage.getItem("key"); // "value"
```

**sessionStorage** - Persists until tab closed (5-10MB):
```javascript
sessionStorage.setItem("key", "value");
```

**cookies** - Sent with HTTP requests, can have expiration (4KB):
```javascript
document.cookie = "key=value; max-age=3600";
```

**Real-world scenario:** I use localStorage for user preferences (theme, language), sessionStorage for temporary data (form state), and cookies for authentication tokens (need to be sent with requests). Each has different use cases based on persistence and size limits.

---

<a id="question-157"></a>

### Why should browser storage not be treated as secure storage?

[Back to question index](#question-index)

**Answer:**

**Insecure because:**
- Accessible by any JavaScript on the domain
- XSS attacks can read/write storage
- Not encrypted
- User can clear/change storage
- Synced across devices (for localStorage)

**For secure data, use:**
- HttpOnly cookies (not accessible by JS)
- Server-side sessions
- Encrypted storage with server validation

**Real-world scenario:** I never store sensitive data (auth tokens, personal info) in localStorage. I use HttpOnly cookies for auth tokens (immune to XSS) and validate all data from storage on the server side.

---

<a id="question-158"></a>

### What is the same-origin policy?

[Back to question index](#question-index)

**Answer:**

Same-origin policy restricts how documents/scripts from different origins interact:

**Same origin:** Same protocol, domain, and port
- https://example.com and https://example.com:443 ✓
- https://example.com and http://example.com ✗ (different protocol)
- https://example.com and https://api.example.com ✗ (different subdomain)

**Restrictions:**
- Can't read cookies/localStorage from different origin
- Can't make AJAX requests to different origin (without CORS)
- Can't access DOM of different origin iframe

**Real-world scenario:** This is a security feature that prevents malicious sites from accessing data from other sites. When I need cross-origin communication, I use CORS, postMessage, or proxy requests through my own server.

---

<a id="question-159"></a>

### What is CORS, and why does using mode: "no-cors" not solve ordinary cross-origin API access?

[Back to question index](#question-index)

**Answer:**

**CORS (Cross-Origin Resource Sharing)** - HTTP headers that allow cross-origin requests:
```javascript
fetch("https://api.example.com", {
  mode: "cors" // Default, allows reading response
});
```

**mode: "no-cors"** - Makes opaque request (can't read response):
```javascript
fetch("https://api.example.com", {
  mode: "no-cors" // Request sent, but response is opaque
});
// Can't read response body, status, or headers
```

**Real-world scenario:** `no-cors` is for requests where you don't need to read the response (like analytics pings). For actual API calls where you need the data, you need proper CORS headers on the server, not `no-cors` mode.

---

<a id="question-160"></a>

### How does postMessage() work, and why should you validate the sender's origin?

[Back to question index](#question-index)

**Answer:**

**postMessage** - Send messages between windows/iframes:
```javascript
// Send
otherWindow.postMessage({ type: "data", value: 123 }, "https://trusted.com");

// Receive
window.addEventListener("message", (e) => {
  if (e.origin !== "https://trusted.com") return; // Validate!
  console.log(e.data);
});
```

**Validate origin to prevent:**
- Malicious sites sending fake messages
- Data theft
- Unauthorized actions

**Real-world scenario:** I use postMessage for iframe communication (like embeddable widgets). I always validate the origin to ensure messages only come from trusted sources. This prevents security vulnerabilities.

---

## Modules, Errors, Memory & Performance

<a id="question-161"></a>

### What is the difference between named exports and default exports?

[Back to question index](#question-index)

**Answer:**

**Named exports:**
```javascript
// utils.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// main.js
import { add, subtract } from "./utils";
```

**Default export:**
```javascript
// utils.js
export default (a, b) => a + b;

// main.js
import add from "./utils";
```

**Real-world scenario:** I use named exports for utilities and components (multiple exports per file), and default exports for the main export of a file (like a React component). Named exports are better for tree-shaking and auto-importing.

---

<a id="question-162"></a>

### What is the difference between static imports and dynamic import()?

[Back to question index](#question-index)

**Answer:**

**Static import** - Loaded at compile time:
```javascript
import { utils } from "./utils";
// Loaded when module is evaluated
```

**Dynamic import()** - Loaded at runtime:
```javascript
const utils = await import("./utils");
// Loaded when this line executes
```

**Real-world scenario:** I use dynamic imports for code splitting - loading heavy components or libraries only when needed. This reduces initial bundle size and improves load time. Static imports are for everything that's needed immediately.

---

<a id="question-163"></a>

### What are live bindings in ES modules?

[Back to question index](#question-index)

**Answer:**

ES modules have live bindings - imports always see the current value:

```javascript
// counter.js
export let count = 0;
export function increment() {
  count++;
}

// main.js
import { count, increment } from "./counter";
console.log(count); // 0
increment();
console.log(count); // 1 (live binding - sees updated value)
```

**Real-world scenario:** This is different from CommonJS where imports get a copy. Live bindings mean exported values can change and importers see the changes. This is useful for state and configuration that changes over time.

---

<a id="question-164"></a>

### What can go wrong with circular module dependencies?

[Back to question index](#question-index)

**Answer:**

Circular dependencies can cause undefined values or incomplete initialization:

```javascript
// a.js
import { b } from "./b";
export const a = 1;
console.log(b); // Might be undefined if b imports a

// b.js
import { a } from "./a";
export const b = 2;
console.log(a); // Might be undefined if a imports b
```

**Solutions:**
- Restructure to avoid circular dependencies
- Use lazy loading (dynamic import)
- Extract shared code to a third module

**Real-world scenario:** I had a bug where two modules imported each other and one saw undefined values. I fixed it by extracting the shared code to a separate module. Circular dependencies are a code smell and should be avoided.

---

<a id="question-165"></a>

### What is strict mode, and how does it change JavaScript behavior?

[Back to question index](#question-index)

**Answer:**

Strict mode enforces safer JavaScript:

```javascript
"use strict";

// Changes:
// 1. Variables must be declared
x = 10; // Error (x not declared)

// 2. this is undefined in functions (not global)
function fn() {
  console.log(this); // undefined (not window)
}

// 3. Duplicate parameter names not allowed
function fn(a, a) { } // Error

// 4. Silent errors become errors
NaN = 5; // Error (normally silent)
```

**Real-world scenario:** Modern tools (ES modules, bundlers) automatically use strict mode. It catches common bugs early. I never disable it - the stricter rules prevent subtle bugs that are hard to debug.

---

<a id="question-166"></a>

### What is the difference between throw new Error() and throwing a string?

[Back to question index](#question-index)

**Answer:**

**throw new Error()** - Creates proper error object with stack trace:
```javascript
throw new Error("Something went wrong");
// Has: message, stack, name
```

**throw string** - Just throws a string (no stack trace):
```javascript
throw "Something went wrong";
// Just a string, no error properties
```

**Real-world scenario:** I always throw Error objects - they have stack traces for debugging and can be caught specifically. Throwing strings makes debugging harder and error handling less reliable.

---

<a id="question-167"></a>

### What does finally do, and how can a return inside it change the result?

[Back to question index](#question-index)

**Answer:**

**finally** - Always runs, regardless of success/failure:
```javascript
try {
  // Some code
} catch (err) {
  // Handle error
} finally {
  // Always runs
}
```

**Return in finally overrides:**
```javascript
function test() {
  try {
    return 1;
  } finally {
    return 2; // Overrides the 1!
  }
}
test(); // 2
```

**Real-world scenario:** I use finally for cleanup (closing connections, clearing timers). I avoid returns in finally because they override the try/catch return, which is confusing and error-prone.

---

<a id="question-168"></a>

### When does try...catch fail to catch an asynchronous error?

[Back to question index](#question-index)

**Answer:**

When the error happens in an async callback outside the try block:

```javascript
try {
  setTimeout(() => {
    throw new Error("Not caught!");
  }, 100);
} catch (err) {
  // This never runs - error is async
}
```

**Async function:**
```javascript
try {
  await someAsync(); // Works if inside try
} catch (err) {
  // Catches errors from awaited promise
}
```

**Real-world scenario:** I made this mistake when I thought try/catch would catch errors in setTimeout callbacks. Now I use async/await or add try/catch inside the callback. Async errors need async error handling.

---

<a id="question-169"></a>

### What are iterables and iterators?

[Back to question index](#question-index)

**Answer:**

**Iterable** - Object with [Symbol.iterator] method:
```javascript
const iterable = [1, 2, 3];
const iterator = iterable[Symbol.iterator]();
```

**Iterator** - Object with next() method:
```javascript
iterator.next(); // { value: 1, done: false }
iterator.next(); // { value: 2, done: false }
iterator.next(); // { value: 3, done: false }
iterator.next(); // { value: undefined, done: true }
```

**Custom iterable:**
```javascript
const myIterable = {
  [Symbol.iterator]() {
    let i = 0;
    return {
      next() {
        return { value: i++, done: i > 3 };
      }
    };
  }
};

for (const val of myIterable) {
  console.log(val); // 0, 1, 2
}
```

**Real-world scenario:** I rarely create custom iterables, but understanding them helps when working with generators and for...of loops. Built-in iterables (arrays, strings, maps, sets) are used constantly.

---

<a id="question-170"></a>

### What are generator functions, and how does yield work?

[Back to question index](#question-index)

**Answer:**

Generators can pause and resume execution:

```javascript
function* generateNumbers() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = generateNumbers();
gen.next(); // { value: 1, done: false }
gen.next(); // { value: 2, done: false }
gen.next(); // { value: 3, done: false }
gen.next(); // { value: undefined, done: true }
```

**Real-world scenario:** I use generators for:
- Infinite sequences (like unique IDs)
- Async iteration (with async generators)
- Lazy evaluation
- Complex state machines

They're useful when you need to produce values on demand rather than all at once.

---

<a id="question-171"></a>

### How does garbage collection relate to object reachability?

[Back to question index](#question-index)

**Answer:**

JavaScript uses reachability-based garbage collection:

**Reachable objects** (not collected):
- Global variables
- Objects referenced from the stack
- Objects referenced from other reachable objects

**Unreachable objects** (collected):
```javascript
let obj = { data: "value" };
obj = null; // Object is now unreachable, will be collected
```

**Real-world scenario:** Understanding reachability helps identify memory leaks. If I keep references to objects I don't need (in closures, global variables, event listeners), they won't be collected. I use Chrome DevTools Memory tab to find unreachable objects that should be collected.

---

<a id="question-172"></a>

### What commonly causes memory leaks in frontend applications?

[Back to question index](#question-index)

**Answer:**

**Common causes:**
1. **Forgotten event listeners:**
```javascript
// Leak if element removed but listener not removed
element.addEventListener("click", handler);
```

2. **Closures retaining large objects:**
```javascript
function createHandler() {
  const hugeData = new Array(1000000);
  return () => console.log("click");
}
```

3. **Timers not cleared:**
```javascript
setInterval(() => { /* ... */ }, 1000); // Never cleared
```

4. **DOM references:**
```javascript
const removedElement = document.getElementById("old");
// Even if removed from DOM, reference keeps it in memory
```

**Real-world scenario:** I've had memory leaks from not clearing intervals and not removing event listeners. Now I always cleanup in useEffect (React) or have explicit cleanup functions. Chrome DevTools Memory heap snapshots help identify leaks.

---

<a id="question-173"></a>

### How can timers and event listeners retain memory after a component is removed?

[Back to question index](#question-index)

**Answer:**

**Timers:**
```javascript
useEffect(() => {
  const timer = setInterval(() => {
    // Component removed but timer still runs
  }, 1000);

  return () => clearInterval(timer); // Cleanup!
}, []);
```

**Event listeners:**
```javascript
useEffect(() => {
  const handler = () => { /* ... */ };
  element.addEventListener("click", handler);

  return () => element.removeEventListener("click", handler); // Cleanup!
}, []);
```

**Real-world scenario:** In React, I always return cleanup functions from useEffect. Without cleanup, timers keep running and listeners stay attached even after component unmount, causing memory leaks and potential bugs (state updates on unmounted components).

---

<a id="question-174"></a>

### How would you prevent a memoization cache from growing indefinitely?

[Back to question index](#question-index)

**Answer:**

**Size limit with LRU eviction:**
```javascript
class LRUCache {
  constructor(maxSize = 100) {
    this.cache = new Map();
    this.maxSize = maxSize;
  }

  get(key) {
    if (!this.cache.has(key)) return undefined;
    const value = this.cache.get(key);
    this.cache.delete(key);
    this.cache.set(key, value); // Move to end (most recent)
    return value;
  }

  set(key, value) {
    if (this.cache.size >= this.maxSize) {
      const firstKey = this.cache.keys().next().value;
      this.cache.delete(firstKey); // Remove least recent
    }
    this.cache.set(key, value);
  }
}
```

**Real-world scenario:** Unbounded caches cause memory leaks. I use LRU (Least Recently Used) eviction to keep cache size bounded. For simple cases, I just clear the cache periodically or use WeakMap when keys are objects.

---

<a id="question-175"></a>

### What is the difference between a Web Worker and a Service Worker?

[Back to question index](#question-index)

**Answer:**

**Web Worker** - Runs JavaScript off main thread:
```javascript
const worker = new Worker("worker.js");
worker.postMessage(data);
worker.onmessage = (e) => console.log(e.data);
```

**Service Worker** - Runs offline, intercepts network requests:
```javascript
navigator.serviceWorker.register("sw.js");
```

**Web Worker:**
- Heavy computation
- Can't access DOM
- Dedicated to one origin

**Service Worker:**
- Offline support
- Caching
- Push notifications
- Runs even when page closed

**Real-world scenario:** I use Web Workers for CPU-intensive tasks (image processing, data analysis) to keep UI responsive. I use Service Workers for PWA features (offline caching, background sync). They serve different purposes.

---

<a id="question-176"></a>

### When would you move work into a Web Worker?

[Back to question index](#question-index)

**Answer:**

**Use Web Worker for:**
- Heavy computation (data processing, calculations)
- Image/video processing
- Cryptographic operations
- Large dataset operations

**Example:**
```javascript
// main.js
const worker = new Worker("processor.js");
worker.postMessage({ data: largeDataset });
worker.onmessage = (e) => {
  const result = e.data;
  updateUI(result);
};
```

**Real-world scenario:** I moved CSV parsing into a Web Worker - the UI froze for 5 seconds before. After moving to Worker, the UI stayed responsive while parsing happened in the background. Web Workers are essential for keeping the main thread free.

---

<a id="question-177"></a>

### How would you split a long-running task to keep the page responsive?

[Back to question index](#question-index)

**Answer:**

**Using setTimeout to yield:**
```javascript
async function processLargeDataset(data) {
  const chunkSize = 1000;
  for (let i = 0; i < data.length; i += chunkSize) {
    const chunk = data.slice(i, i + chunkSize);
    processChunk(chunk);

    // Yield to main thread
    await new Promise(resolve => setTimeout(resolve, 0));
  }
}
```

**Or using requestIdleCallback:**
```javascript
function processDuringIdle(data) {
  let i = 0;

  function processChunk(deadline) {
    while (deadline.timeRemaining() > 0 && i < data.length) {
      processData(data[i]);
      i++;
    }

    if (i < data.length) {
      requestIdleCallback(processChunk);
    }
  }

  requestIdleCallback(processChunk);
}
```

**Real-world scenario:** When Web Workers aren't an option, I break long tasks into chunks and yield to the main thread. This keeps the UI responsive even during heavy processing. requestIdleCallback is even better - it only runs when the browser is idle.

---

<a id="question-178"></a>

### What are time complexity and space complexity?

[Back to question index](#question-index)

**Answer:**

**Time complexity** - How runtime grows with input size:
- O(1) - Constant (array access)
- O(n) - Linear (simple loop)
- O(n²) - Quadratic (nested loops)
- O(log n) - Logarithmic (binary search)

**Space complexity** - How memory grows with input size:
- O(1) - Constant (fixed variables)
- O(n) - Linear (array copy)
- O(n²) - Quadratic (nested data structures)

**Real-world scenario:** I consider complexity when writing algorithms. A nested loop (O(n²)) on 10,000 items is 100 million operations, which is slow. I look for O(n) or O(n log n) solutions. Understanding complexity helps write efficient code.

---

<a id="question-179"></a>

### How would you identify and fix an unnecessary nested loop?

[Back to question index](#question-index)

**Answer:**

**Identify with performance profiling:**
```javascript
// Slow - O(n²)
function findDuplicates(arr) {
  const duplicates = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] === arr[j]) duplicates.push(arr[i]);
    }
  }
  return duplicates;
}
```

**Fix with better algorithm:**
```javascript
// Fast - O(n)
function findDuplicates(arr) {
  const seen = new Set();
  const duplicates = new Set();

  for (const item of arr) {
    if (seen.has(item)) {
      duplicates.add(item);
    } else {
      seen.add(item);
    }
  }

  return Array.from(duplicates);
}
```

**Real-world scenario:** I had a slow function with nested loops processing 10,000 items. Profiling showed it was the bottleneck. I rewrote it using a Set for O(n) complexity, reducing runtime from seconds to milliseconds. Chrome DevTools Performance tab is great for identifying slow code.

---

<a id="question-180"></a>

### How would you investigate a slow function or memory leak using browser developer tools?

[Back to question index](#question-index)

**Answer:**

**Performance investigation:**
1. Open Chrome DevTools → Performance tab
2. Record while running the slow function
3. Stop recording and analyze the flame chart
4. Look for long-running functions
5. Identify hot paths and optimize

**Memory leak investigation:**
1. Open Chrome DevTools → Memory tab
2. Take heap snapshot before
3. Run the suspected leaky code
4. Take heap snapshot after
5. Compare snapshots (look for objects that shouldn't be there)
6. Find retaining paths to see what's holding references

**Real-world scenario:** I used heap snapshots to find a memory leak where event listeners weren't being removed. The comparison showed thousands of handler objects still in memory. I traced the retaining path to find the DOM element and added proper cleanup.

---

## Summary

This comprehensive guide covers the most important JavaScript interview questions with detailed, experience-based answers. The key takeaways are:

1. **Variables & Scope** - Understand var, let, const, hoisting, and closures
2. **Data Types** - Know primitives vs objects, type coercion, and equality
3. **Functions** - Master closures, this, arrow functions, and higher-order functions
4. **Objects & Prototypes** - Understand prototypes, inheritance, and object manipulation
5. **Arrays & Strings** - Know array methods, immutability, and transformations
6. **Async & Promises** - Master event loop, async/await, and error handling
7. **API Handling** - Understand fetch, error handling, caching, and best practices
8. **DOM & Events** - Know event delegation, performance, and browser APIs
9. **Modules & Performance** - Understand modules, errors, memory, and optimization

Remember: Experience comes from building real applications and debugging real problems. These answers reflect practical knowledge gained from years of development.
