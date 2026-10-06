# YouTube Interview Question List — Answers and Coding Practice

<a id="question-index"></a>

## Question Index

Click any question to jump directly to its answer. Each answer has a link back to this index.

### JavaScript

- [1. What are the differences between `var`, `let`, and `const` regarding scope, hoisting, re-declaration, and reassignment?](#question-1)
- [2. What is lexical scope, and how does scope chain resolution work across nested functions?](#question-2)
- [3. What are the different types of scope in JavaScript (Global, Function, Block, Lexical)?](#question-3)
- [4. What is the Temporal Dead Zone (TDZ), and how does hoisting differ for `let`/`const` versus `var`?](#question-4)
- [5. What happens when a variable is assigned without a declaration keyword, and how does `"use strict"` mode alter this behavior?](#question-5)
- [6. What are the differences between `undeclared`, `undefined`, and `null`?](#question-6)
- [7. Why can elements of a `const`-declared array or properties of a `const`-declared object be modified, but a primitive `const` variable cannot be reassigned?](#question-7)
- [8. What are first-class functions, and can a standard function declaration be assigned to a variable?](#question-8)
- [9. What are the differences between function declarations and function expressions?](#question-9)
- [10. What is an Immediately Invoked Function Expression (IIFE) / self-invoking function?](#question-10)
- [11. What is an anonymous function, and how does it differ from a named function?](#question-11)
- [12. What is function currying, and how do you implement infinite currying?](#question-12)
- [13. What is a Polyfill, and why do developers write custom polyfills?](#question-13)
- [14. What is recursion, and what causes a "maximum call stack size exceeded" error?](#question-14)
- [15. How do `call()`, `apply()`, and `bind()` methods differ?](#question-15)
- [16. How does `this` binding work in arrow functions compared to traditional function expressions?](#question-16)
- [17. What is the difference between pre-increment (`++x`) and post-increment (`x++`)?](#question-17)
- [18. What happens when a `return` statement has a line break immediately following it before the returned value or block?](#question-18)
- [19. What happens when properties are attached directly to a function object (e.g., `fn.abc = 400`)?](#question-19)
- [20. What are the differences between primitive and non-primitive data types regarding mutability and referential equality?](#question-20)
- [21. Is `function` a primitive or non-primitive data type?](#question-21)
- [22. What is implicit type coercion, and how do loose equality (`==`) and strict equality (`===`) behave during evaluations like `[] == ![]` or `[] == true`?](#question-22)
- [23. Why does floating-point arithmetic precision cause unexpected outcomes like `0.1 + 0.2 !== 0.3`?](#question-23)
- [24. What is `NaN` (Not a Number), and what does `typeof NaN` return?](#question-24)
- [25. What is the type of `null`, and how does `null` differ from `undefined`?](#question-25)
- [26. What are the outputs when evaluating expressions with mixed types, such as `"2" + 2 + 3`, `"2" - 2 + 3`, `"ABC" - 100`, `"wow" - "money"`, `+"100"`, `+true`, `!"test"`, `[] + []`, or `[] + {}`?](#question-26)
- [27. What is the output of `parseInt("FF78")` versus `parseInt("78F")`?](#question-27)
- [28. What is the purpose of optional chaining (`?.`) and the nullish coalescing operator (`??`)?](#question-28)
- [29. How does a wrapper object created via constructors (`new String("web")`, `new Number(10)`) differ from its primitive literal when evaluated with `==` versus `===`?](#question-29)
- [30. How does the exponentiation operator (`**`) differ from standard multiplication (`*`)?](#question-30)
- [31. What is the difference between `slice()` and `splice()` array methods?](#question-31)
- [32. What is the difference between `map()` and `forEach()` array methods?](#question-32)
- [33. How does the `reduce()` method function, and what roles do the `accumulator` and `index` arguments play?](#question-33)
- [34. What are the functional differences between `some()`, `every()`, `find()`, and `findIndex()`?](#question-34)
- [35. What will `map()` return if an inline condition (`if (e > 0)`) executes inside the callback without an explicit return statement?](#question-35)
- [36. What are the differences between `pop()` and `shift()` array methods?](#question-36)
- [37. How do shallow copies differ from deep copies, and how do you create a shallow copy using spread operators or `Object.assign()`?](#question-37)
- [38. What happens when an object key is assigned as another object (e.g., `obj[b] = 600` where `b` is an object)?](#question-38)
- [39. How do array destructuring and object destructuring work (including property aliasing like `pqr: P`)?](#question-39)
- [40. How can you delete a specific property from an object?](#question-40)
- [41. How can you convert an object's keys into an array (`Object.keys()`) or convert an object to a string?](#question-41)
- [42. How are objects and arrays compared in JavaScript (referential equality)?](#question-42)
- [43. What is the difference between `WeakSet` and `WeakMap`?](#question-43)
- [44. How do `for...in` and `for...of` loops differ during iteration?](#question-44)
- [45. How does `JSON.parse()` work in JavaScript?](#question-45)
- [46. How are asynchronous operations managed in JavaScript (Callbacks, Promises, `async/await`)?](#question-46)
- [47. What is Callback Hell (Pyramid of Doom), and how do Promises or `async/await` resolve it?](#question-47)
- [48. What are the three states of a Promise (`pending`, `fulfilled`, `rejected`)?](#question-48)
- [49. What is the Event Loop, and what is the execution priority between Promises (Microtask queue) and `setTimeout` / `setInterval` (Macrotask queue)?](#question-49)
- [50. What is the difference between `setTimeout()` and `setInterval()`, and how do you cancel their execution?](#question-50)
- [51. What are the phases of event propagation (Event Capturing, Event Bubbling)?](#question-51)
- [52. What is event targeting (`event.target`), and what is event delegation?](#question-52)
- [53. What are standard DOM event categories (Mouse, Keyboard, Form, and Window events)?](#question-53)
- [54. What are the differences between `localStorage` and `sessionStorage` regarding persistence, capacity, and tab lifecycle?](#question-54)
- [55. What is the difference between named exports and default exports in JavaScript modules?](#question-55)
- [56. What error types exist in JavaScript (e.g., `ReferenceError`, `SyntaxError`, `TypeError`, runtime errors)?](#question-56)
- [57. What built-in popup boxes exist in JavaScript (`alert`, `prompt`, `confirm`)?](#question-57)

### React and package management

- [58. What is ReactJS, and what are its primary architectural advantages?](#question-58)
- [59. What is the difference between the Real DOM and the Virtual DOM?](#question-59)
- [60. What are the Reconciliation algorithm, Diffing algorithm, and batching mechanisms in React?](#question-60)
- [61. What is JSX, can web browsers parse JSX directly, and how is it transpiled?](#question-61)
- [62. What are the roles of module bundlers (e.g., Parcel, Webpack) and transpilers (e.g., Babel)?](#question-62)
- [63. Why are `key` props required when rendering lists, and why is using the array index as a key discouraged?](#question-63)
- [64. What is Shimmer UI / skeleton loading screen?](#question-64)
- [65. What is the difference between Client-Side Rendering (CSR), Server-Side Rendering (SSR), and Hydration?](#question-65)
- [66. What are the differences between Class components and Functional components?](#question-66)
- [67. How do you manage component lifecycle phases (mounting, updating, unmounting/cleanup) in functional components using `useEffect`?](#question-67)
- [68. What happens if `useEffect` is passed without a dependency array, with an empty array `[]`, or with specific state/prop dependencies (or `null`)?](#question-68)
- [69. What is the difference between `useEffect` and `useLayoutEffect` hooks?](#question-69)
- [70. What is the difference between `useMemo` and `useCallback` hooks, and how does memoization work?](#question-70)
- [71. What is the difference between `useState` and `useReducer` hooks?](#question-71)
- [72. Is `useState` synchronous or asynchronous, and why?](#question-72)
- [73. What are Higher-Order Components (HOCs), and in what scenarios are they applied?](#question-73)
- [74. What are custom hooks, and why are they created?](#question-74)
- [75. What is the difference between controlled and uncontrolled components?](#question-75)
- [76. Why are React Fragments (`<>...</>`) preferred over container `<div>` elements?](#question-76)
- [77. How do you prevent memory leaks in React applications?](#question-77)
- [78. What techniques can be used to optimize React application performance (e.g., image optimization, lazy loading, code splitting, memoization, Lighthouse audits)?](#question-78)
- [79. What is the difference between state and props?](#question-79)
- [80. What is prop drilling, and how can it be avoided?](#question-80)
- [81. What is the Context API, and how does it compare to Redux / Redux Toolkit?](#question-81)
- [82. What are the core building blocks of Redux (Store, Actions, Reducers / Slices, `useSelector`)?](#question-82)
- [83. What is the role of a Reducer function in Redux?](#question-83)
- [84. Which package handles routing in React (`react-router-dom`), and how do normal routing and dynamic routing work (`useParams`, `useLocation`)?](#question-84)
- [85. What is the difference between the caret (`^`) and tilde (`~`) version operators in `package.json`?](#question-85)
- [86. What is the difference between `package.json` and `package-lock.json`?](#question-86)
- [87. What is the difference between regular `dependencies` and `devDependencies`?](#question-87)

### HTML

- [88. What is the difference between `<div>` and `<span>` tags (Block-level vs Inline elements)?](#question-88)
- [89. What list types exist in HTML (`<ul>`, `<ol>`, `<dl>`)?](#question-89)
- [90. What text formatting tags are available in HTML (`<b>`, `<i>`, `<u>`, `<strong>`, `<em>`, `<mark>`, `<sup>`, `<sub>`)?](#question-90)
- [91. What is the difference between `<b>` and `<strong>` tags, and `<i>` vs `<em>` tags?](#question-91)
- [92. What are void / empty / self-closing elements in HTML (e.g., `<img>`, `<br>`, `<hr>`)?](#question-92)
- [93. What is the purpose of the `required` attribute in form inputs?](#question-93)
- [94. What is the purpose of the `alt` attribute in `<img>` tags?](#question-94)
- [95. What is the difference between `cellpadding` and `cellspacing` in HTML tables?](#question-95)
- [96. What tags are used to build HTML tables (`<table>`, `<thead>`, `<tbody>`, `<tr>`, `<td>`, `<th>`)?](#question-96)
- [97. How do you merge adjacent table cells across rows or columns (`colspan`, `rowspan`)?](#question-97)
- [98. What is an image map (`<map>`, `<area>`), and how are clickable coordinates defined?](#question-98)
- [99. What are HTML character entities (e.g., `&copy;`, `&gt;`, `&lt;`)?](#question-99)
- [100. What are Web Workers in HTML5?](#question-100)
- [101. What is the difference between the `<figure>` tag and `<img>` tag?](#question-101)
- [102. What is the purpose of the `<figcaption>` tag?](#question-102)
- [103. What is the difference between `<meter>` and `<progress>` tags?](#question-103)
- [104. How can you embed one web page inside another web page (`<iframe>`)?](#question-104)

### CSS

- [105. What are the different methods to hide elements in CSS (`display: none`, `visibility: hidden`, `opacity: 0`), and how do they differ in viewport layout space allocation?](#question-105)
- [106. How do you create animations in CSS (Transitions vs `@keyframes`)?](#question-106)
- [107. What is the universal selector (`*`) in CSS?](#question-107)
- [108. What are the three types of CSS styling (Inline, Internal, External)?](#question-108)
- [109. What is the specificity and priority order among Inline, Internal, and External CSS?](#question-109)
- [110. What is the CSS Box Model, and what is the sequence of layers from inside to outside (Content, Padding, Border, Margin)?](#question-110)
- [111. What is the difference between CSS `border` and `outline`?](#question-111)
- [112. What is the difference between CSS pseudo-classes and pseudo-elements?](#question-112)
- [113. What are the different CSS `position` values (`static`, `relative`, `absolute`, `fixed`, `sticky`)?](#question-113)
- [114. What is `z-index`, and how does it control element stacking order and parent-child constraints?](#question-114)
- [115. What are CSS combinators?](#question-115)
- [116. What are CSS counters?](#question-116)
- [117. How do you vertically center text using Flexbox?](#question-117)
- [118. What are the key differences between Flexbox and CSS Grid?](#question-118)

### Node.js, APIs, databases, and architecture

- [119. How does Node.js execute JavaScript on the server using Google Chrome's V8 engine?](#question-119)
- [120. What is Express.js, and how do route parameters and route handlers work in Express?](#question-120)
- [121. What is middleware in Express.js, and how do you set up global error handling middleware (`next(err)`)?](#question-121)
- [122. What is JWT authentication, and how do Access Tokens differ from Refresh Tokens?](#question-122)
- [123. What are cluster mode and worker threads in Node.js?](#question-123)
- [124. How do you implement API rate limiting in Node.js?](#question-124)
- [125. How do you handle Cross-Origin Resource Sharing (CORS) in Express.js?](#question-125)
- [126. What is NestJS, and how does its architecture (Modules, Controllers, Services) differ from Express?](#question-126)
- [127. What is the structural difference between SQL databases (relational, fixed schema) and NoSQL databases like MongoDB (schemaless, document-based)?](#question-127)
- [128. How do you handle data consistency, reference modeling, and schema migrations in MongoDB?](#question-128)
- [129. How do you execute database transactions in MongoDB?](#question-129)
- [130. What is Apache Kafka, and how is it used in event-driven microservices messaging?](#question-130)
- [131. What is Docker, and how are containers used to package and deploy web applications?](#question-131)
- [132. What are microservices, and how do services communicate (REST vs gRPC vs Message Queues)?](#question-132)

### Worked coding tasks

- [C1. Implement arbitrary-length currying](#coding-c1)
- [C2. Implement a simplified map](#coding-c2)
- [C3. Group records by a key](#coding-c3)
- [C4. Flatten nested arrays without flat](#coding-c4)
- [C5. Two Sum](#coding-c5)
- [C6. Longest substring without repeats](#coding-c6)
- [C7. React data loading with cancellation and stale-result protection](#coding-c7)
- [C8. A reusable debounced value hook](#coding-c8)
- [C9. A controlled form with async submission](#coding-c9)
- [C10. Express validation and a central error boundary](#coding-c10)
- [C11. A guarded MongoDB transfer transaction](#coding-c11)
- [C12. Memoize a pure one-argument function](#coding-c12)

This guide answers **all 132 questions in your pasted list**, in the same order. It uses simple English and aims at developers with 4–5 years of experience.

**Source boundary:** Your attachment says the questions were extracted from 24 sources. The attachment contains questions, but no video URLs, transcripts, or timestamps. This guide answers that supplied list; it does not claim to have watched or independently verified the videos. The answers and worked exercises are written for your preparation. Official documentation links support framework and platform details.

**How to use:** Read the interview answer first. Then explain the example without reading the explanation. Finish with the practical limitation. Code snippets are independent examples; do not paste the whole document into one program. Browser, React, Node, and database examples need their stated environments. Comments show expected results where useful.

# JavaScript

<a id="question-1"></a>

## 1. What are the differences between `var`, `let`, and `const` regarding scope, hoisting, re-declaration, and reassignment?

[Back to question index](#question-index)

**Interview answer:** `var` is function-scoped, while `let` and `const` are block-scoped. Var allows redeclaration and reassignment; let allows reassignment but not same-scope redeclaration; const allows neither. I default to const and use let for changing bindings.

```js
if (true) { var a = 1; let b = 2; }
console.log(a); // 1
// console.log(b); // ReferenceError
```

**Explanation:** Var is initialized to undefined before its assignment. Let and const bindings exist before their declarations execute but are uninitialized, so reading them throws. Hoisting does not move assignments. Const protects a binding, not the contents of an object.

<a id="question-2"></a>

## 2. What is lexical scope, and how does scope chain resolution work across nested functions?

[Back to question index](#question-index)

**Interview answer:** A function's outer scope comes from where it was defined. JavaScript searches the current scope first, then enclosing scopes, stopping at the first matching binding.

```js
const name = "outer";
function read() { return name; }
function run() { const name = "inner"; return read(); }
console.log(run()); // outer
```

**Explanation:** Read was defined outside run, so run's local name is not in read's scope chain. The caller does not decide lexical scope. Closures keep access to this chain when functions are used later.

<a id="question-3"></a>

## 3. What are the different types of scope in JavaScript (Global, Function, Block, Lexical)?

[Back to question index](#question-index)

**Interview answer:** Global scope belongs to the global environment, function scope belongs to a function, and block scope belongs to a block. Module scope belongs to an ES module. Lexical scope describes how these scopes are connected; it is not just another container.

```js
const app = "shop";
function work() {
  const local = 1;
  if (true) { const block = 2; console.log(app, local, block); }
}
work(); // shop 1 2
```

**Explanation:** Inner code can read accessible outer bindings. Outer code cannot read a function's locals or a block's locals. Keep variables in the smallest useful scope to reduce accidental sharing.

<a id="question-4"></a>

## 4. What is the Temporal Dead Zone (TDZ), and how does hoisting differ for `let`/`const` versus `var`?

[Back to question index](#question-index)

**Interview answer:** The TDZ is the time between entering a scope and initializing its let or const binding. Reading it then throws. Var instead starts as undefined.

```js
console.log(a); // undefined
var a = 10;
try { console.log(b); let b = 20; }
catch (error) { console.log(error.name); } // ReferenceError
```

**Explanation:** Both kinds of binding are created early, but only var is initialized early. Even `typeof b` would throw inside b's TDZ. This avoids silently using a variable before it is ready.

<a id="question-5"></a>

## 5. What happens when a variable is assigned without a declaration keyword, and how does `"use strict"` mode alter this behavior?

[Back to question index](#question-index)

**Interview answer:** Assignment to an unresolved name can create a global property in non-strict code. In strict mode it throws ReferenceError. ES modules are already strict.

```js
"use strict";
try { accidentalTotal = 10; }
catch (error) { console.log(error.name); } // ReferenceError
```

**Explanation:** The name must actually be unresolved; assigning an existing outer variable does not create a new global. Declare variables and use linting so a typo does not become hidden shared state.

<a id="question-6"></a>

## 6. What are the differences between `undeclared`, `undefined`, and `null`?

[Back to question index](#question-index)

**Interview answer:** Undeclared means no binding exists for the name. Undefined is a primitive value commonly used for a missing or unassigned result. Null is a primitive commonly used for an intentional empty value.

```js
let value;
console.log(value); // undefined
console.log({}.missing); // undefined
console.log(typeof noSuchName); // undefined (a string from typeof)
console.log(null === undefined); // false
```

**Explanation:** Reading an undeclared name directly throws. Undefined is a value that a declared variable can hold. Null and undefined loosely compare equal but are different under strict equality.

<a id="question-7"></a>

## 7. Why can elements of a `const`-declared array or properties of a `const`-declared object be modified, but a primitive `const` variable cannot be reassigned?

[Back to question index](#question-index)

**Interview answer:** Const prevents assigning a different value to a binding. It does not make the referenced object immutable. Array and object contents can still change.

```js
const values = [1];
values.push(2);
console.log(JSON.stringify(values)); // [1,2]
// values = []; // TypeError
```

**Explanation:** Push edits the existing array; reassignment would replace the stored reference. A primitive has no mutable contents. `Object.freeze()` protects an object's own data properties, but is shallow, so nested objects need separate consideration.

<a id="question-8"></a>

## 8. What are first-class functions, and can a standard function declaration be assigned to a variable?

[Back to question index](#question-index)

**Interview answer:** Functions are first-class values: we can assign them, pass them as arguments, return them, and store them in data structures. A declared function can be assigned to another variable.

```js
function add(a, b) { return a + b; }
const operation = add;
console.log(operation(2, 3)); // 5
console.log(operation === add); // true
```

**Explanation:** `add` without parentheses reads the function value. `add(2, 3)` calls it and gives a result. Assigning the function does not copy its implementation; both bindings hold the same function object. This supports callbacks and higher-order functions.

<a id="question-9"></a>

## 9. What are the differences between function declarations and function expressions?

[Back to question index](#question-index)

**Interview answer:** A function declaration is generally initialized before its scope's code runs. A function expression becomes available when its containing assignment executes.

```js
console.log(add(1, 2)); // 3
function add(a, b) { return a + b; }
const subtract = function (a, b) { return a - b; };
console.log(subtract(3, 1)); // 2
```

**Explanation:** Calling subtract before its const declaration would throw ReferenceError. With var, the early binding would contain undefined, and calling it would throw TypeError. Declarations are useful for named operations; expressions are useful for passing and choosing functions.

<a id="question-10"></a>

## 10. What is an Immediately Invoked Function Expression (IIFE) / self-invoking function?

[Back to question index](#question-index)

**Interview answer:** An IIFE is a function expression called immediately after creation. It creates a private scope and can return a value or API.

```js
const counter = (() => {
  let count = 0;
  return () => ++count;
})();
console.log(counter()); // 1
```

**Explanation:** The outer arrow executes once. Its returned function keeps count through a closure. IIFEs were widely used to avoid globals before modules. Modules and block scope cover many current uses, but an IIFE can still be useful for one-time setup. It is called by the expression; it does not invoke itself magically.

<a id="question-11"></a>

## 11. What is an anonymous function, and how does it differ from a named function?

[Back to question index](#question-index)

**Interview answer:** An anonymous function expression has no explicit function name. A named function can be easier to identify in debugging and can refer to itself for recursion.

```js
const double = function (n) { return n * 2; };
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
};
console.log(factorial(4)); // 24
```

**Explanation:** JavaScript can infer a name such as double from assignment. The expression's explicit name fact is available inside its own body, not as a new outer binding. Naming does not decide whether a function is asynchronous or whether it has a dynamic this.

<a id="question-12"></a>

## 12. What is function currying, and how do you implement infinite currying?

[Back to question index](#question-index)

**Interview answer:** Currying turns a multi-argument operation into successive function calls. “Infinite currying” usually means accepting an arbitrary number of calls until an agreed stopping signal.

```js
const multiply = a => b => a * b;
function sum(total = 0) {
  return function next(value) {
    if (arguments.length === 0) return total;
    return sum(total + value);
  };
}
console.log(multiply(2)(3)); // 6
console.log(sum(1)(2)(0)(3)()); // 6
```

**Explanation:** Each call returns a function holding the updated total. Empty parentheses finish the chain. Checking argument count, rather than truthiness, allows zero. See C1 for validation, boundary cases, and complexity. This interface is useful for interview practice; a normal sum function may be clearer in product code.

<a id="question-13"></a>

## 13. What is a Polyfill, and why do developers write custom polyfills?

[Back to question index](#question-index)

**Interview answer:** A polyfill implements a missing standard API for an older environment. It helps code use that API consistently, but must follow its behavior closely.

```js
// Feature detection; this is an API-selection example, not a full polyfill.
const hasOwn = Object.hasOwn
  ? (object, key) => Object.hasOwn(object, key)
  : (object, key) => Object.prototype.hasOwnProperty.call(object, key);
console.log(hasOwn({ id: 1 }, "id")); // true
```

**Explanation:** Check feature existence rather than browser names. Syntax such as optional chaining needs transpilation for parsers that cannot read it; a runtime polyfill cannot fix unsupported syntax. A simplified interview implementation is not automatically a complete standards-compatible polyfill. See C2 for a map helper.

<a id="question-14"></a>

## 14. What is recursion, and what causes a "maximum call stack size exceeded" error?

[Back to question index](#question-index)

**Interview answer:** Recursion is a function calling itself to solve a smaller part of a problem. It needs a stopping condition and progress toward that condition. Too many active calls can exceed the stack limit.

```js
function factorial(n) {
  if (n === 0) return 1;
  return n * factorial(n - 1);
}
console.log(factorial(4)); // 24
```

**Explanation:** This example assumes a small non-negative integer. A negative input never reaches zero. Even correct recursion can overflow for deeply nested input. Use iteration or an explicit stack where depth is large; do not depend on tail-call optimization being available in your target environment.

<a id="question-15"></a>

## 15. How do `call()`, `apply()`, and `bind()` methods differ?

[Back to question index](#question-index)

**Interview answer:** Call invokes with separate arguments; apply invokes with an array-like argument list; bind creates a function with a saved receiver and optional preset arguments.

```js
function greet(prefix) { return `${prefix} ${this.name}`; }
const user = { name: "Sam" };
console.log(greet.call(user, "Hi")); // Hi Sam
console.log(greet.apply(user, ["Hi"])); // Hi Sam
const sayHi = greet.bind(user, "Hi");
console.log(sayHi()); // Hi Sam
```

**Explanation:** Bind does not call greet immediately. Save the returned function if you must later remove it as a listener; another bind call creates a different function. None of these methods can replace an arrow function's inherited this.

<a id="question-16"></a>

## 16. How does `this` binding work in arrow functions compared to traditional function expressions?

[Back to question index](#question-index)

**Interview answer:** A regular function's this is usually determined by its call. An arrow inherits this from the enclosing scope. Arrow functions are useful for callbacks that should keep the surrounding receiver.

```js
const user = {
  name: "Sam",
  makeReader() { return () => this.name; },
};
const read = user.makeReader();
console.log(read.call({ name: "Alex" })); // Sam
```

**Explanation:** MakeReader gets user as this, and its arrow keeps that value. An arrow defined as a top-level object property would not automatically get the object as this. Arrows also lack their own arguments and cannot be constructors.

<a id="question-17"></a>

## 17. What is the difference between pre-increment (`++x`) and post-increment (`x++`)?

[Back to question index](#question-index)

**Interview answer:** Both increment the variable. Prefix returns the updated numeric value; postfix returns the previous numeric value.

```js
let value = "5";
console.log(value++); // 5 (number)
console.log(value); // 6
console.log(++value); // 7
```

**Explanation:** Increment converts the numeric string before updating it. This differs from `value += 1`, which can concatenate a string. Avoid several increments in one expression because evaluation order becomes harder to follow.

<a id="question-18"></a>

## 18. What happens when a `return` statement has a line break immediately following it before the returned value or block?

[Back to question index](#question-index)

**Interview answer:** A newline immediately after return ends the return statement through automatic semicolon insertion. The function returns undefined, even if a value appears on the next line.

```js
function wrong() {
  return
  { value: 1 };
}
function right() {
  return { value: 1 };
}
console.log(wrong()); // undefined
console.log(right().value); // 1
```

**Explanation:** The parser treats the first function as `return;`. The later statement is unreachable. Keep the returned expression on the return line, or begin parentheses on that line for a multiline expression. Formatting and linting can catch this mistake.

<a id="question-19"></a>

## 19. What happens when properties are attached directly to a function object (e.g., `fn.abc = 400`)?

[Back to question index](#question-index)

**Interview answer:** Functions are objects, so they can have properties while remaining callable. A property assignment does not change the function's returned result unless the body uses it.

```js
function fn() { return 100; }
fn.abc = 400;
console.log(fn.abc); // 400
console.log(fn()); // 100
console.log(typeof fn); // function
```

**Explanation:** The function object holds both callable behavior and properties. All references to that same function can see abc. Use such state carefully; a closure or explicit configuration object often communicates ownership more clearly.

<a id="question-20"></a>

## 20. What are the differences between primitive and non-primitive data types regarding mutability and referential equality?

[Back to question index](#question-index)

**Interview answer:** Primitives are string, number, bigint, boolean, undefined, symbol, and null. Their values are immutable. Non-primitives are objects, including arrays and functions, and usually have mutable properties. Object equality checks identity.

```js
let a = 1;
let b = a;
b = 2;
const first = { count: 1 };
const second = first;
second.count = 2;
console.log(a, first.count); // 1 2
```

**Explanation:** Primitive assignment copies a value. Object assignment copies a reference value, so two bindings can share one object. Arguments are passed by value too; assigning a new object to a parameter does not replace the caller's binding.

<a id="question-21"></a>

## 21. Is `function` a primitive or non-primitive data type?

[Back to question index](#question-index)

**Interview answer:** No. A function is a callable object. `typeof` reports function to help distinguish it from other objects, but function is not an eighth primitive type.

```js
const fn = () => 1;
fn.label = "work";
console.log(typeof fn, fn.label); // function work
console.log(fn === (() => 1)); // false
```

**Explanation:** The two arrows create different objects even though their bodies match. Functions can store properties and participate in reference identity checks. Comparing function source text is not a reliable way to establish equal behavior.

<a id="question-22"></a>

## 22. What is implicit type coercion, and how do loose equality (`==`) and strict equality (`===`) behave during evaluations like `[] == ![]` or `[] == true`?

[Back to question index](#question-index)

**Interview answer:** Coercion is automatic type conversion. Strict equality avoids loose equality's cross-type conversions, so I use it by default.

```js
console.log([] == ![]); // true
console.log([] == true); // false
console.log([] === false); // false
```

**Explanation:** `![]` is false because arrays are truthy. Loose comparison with false converts false to zero and the array to an empty string, then zero. Comparing the empty array with true instead compares zero with one. Loose equality does not simply Boolean-convert both operands. Learn each operator's rules instead of assuming one universal conversion.

<a id="question-23"></a>

## 23. Why does floating-point arithmetic precision cause unexpected outcomes like `0.1 + 0.2 !== 0.3`?

[Back to question index](#question-index)

**Interview answer:** Number uses binary floating-point, so some decimal fractions are only approximations. Their sum may differ slightly from the expected decimal value.

```js
console.log(0.1 + 0.2); // 0.30000000000000004
console.log(0.1 + 0.2 === 0.3); // false
```

**Explanation:** Use a tolerance suitable for the numeric scale when comparing measurements. Number.EPSILON alone is not universal. For money, choose a clear rounding policy and integer minor units or decimal arithmetic where appropriate. Formatting with toFixed returns a string; it does not repair the underlying representation.

<a id="question-24"></a>

## 24. What is `NaN` (Not a Number), and what does `typeof NaN` return?

[Back to question index](#question-index)

**Interview answer:** NaN is a special number value representing an invalid numeric result. Its type is number, and it is not equal to itself under ordinary equality.

```js
console.log(typeof NaN); // number
console.log(NaN === NaN); // false
console.log(Number.isNaN(Number("hello"))); // true
console.log(Number.isNaN("hello")); // false
```

**Explanation:** Number.isNaN checks the actual NaN value without conversion. Global isNaN converts first, so it answers a different question. Use Number.isFinite after conversion if the allowed input must exclude both NaN and infinities.

<a id="question-25"></a>

## 25. What is the type of `null`, and how does `null` differ from `undefined`?

[Back to question index](#question-index)

**Interview answer:** Null means an intentional empty value by convention; undefined commonly means no supplied value. Null is a primitive despite typeof null returning object, which is a historical quirk.

```js
console.log(typeof null, typeof undefined); // object undefined
console.log(null == undefined); // true
console.log(null === undefined); // false
```

**Explanation:** Defaults in parameters and destructuring apply to undefined, not null. A consistent API contract should say whether missing, null, and empty text mean different things. Do not use typeof null as proof that null is a normal object.

<a id="question-26"></a>

## 26. What are the outputs when evaluating expressions with mixed types, such as `"2" + 2 + 3`, `"2" - 2 + 3`, `"ABC" - 100`, `"wow" - "money"`, `+"100"`, `+true`, `!"test"`, `[] + []`, or `[] + {}`?

[Back to question index](#question-index)

**Interview answer:** I evaluate intermediate values and identify whether each operator requests string, numeric, or Boolean conversion.

```js
console.log("2" + 2 + 3); // 223
console.log("2" - 2 + 3); // 3
console.log("ABC" - 100); // NaN
console.log("wow" - "money"); // NaN
console.log(+"100"); // 100
console.log(+true); // 1
console.log(!"test"); // false
console.log(JSON.stringify([] + [])); // ""
console.log([] + {}); // [object Object]
```

**Explanation:** Addition groups left to right and joins strings when appropriate. Subtraction converts numerically, with invalid numeric text producing NaN. Unary plus converts to Number; negation uses truthiness. Arrays convert to strings for these additions; the empty array becomes empty text and the ordinary object becomes `[object Object]`. The first result is a string; the second is a number.

<a id="question-27"></a>

## 27. What is the output of `parseInt("FF78")` versus `parseInt("78F")`?

[Back to question index](#question-index)

**Interview answer:** Without a radix or recognized hex prefix, these strings are parsed as decimal. ParseInt accepts an initial valid integer sequence and stops at an invalid character.

```js
console.log(parseInt("FF78")); // NaN
console.log(parseInt("78F")); // 78
console.log(parseInt("FF78", 16)); // 65400
console.log(parseInt("78F", 16)); // 1935
```

**Explanation:** F is invalid as the first decimal digit, so the first call fails. In 78F, the initial 78 is valid decimal and is retained. Explicit radix sixteen changes what counts as a valid digit. Use a radix and validate the whole input if trailing junk should be rejected.

<a id="question-28"></a>

## 28. What is the purpose of optional chaining (`?.`) and the nullish coalescing operator (`??`)?

[Back to question index](#question-index)

**Interview answer:** Optional chaining stops when the checked value is null or undefined. Nullish coalescing supplies a fallback only for those missing values.

```js
const user = { profile: null, count: 0 };
console.log(user.profile?.city); // undefined
console.log(user.count ?? 10); // 0
console.log(user.count || 10); // 10
```

**Explanation:** This safely reads optional data while preserving meaningful zero, false, or empty text. It does not protect undeclared root variables, and optional calls still throw if a present value is not callable. Validate required data rather than hiding every error with optional chaining.

<a id="question-29"></a>

## 29. How does a wrapper object created via constructors (`new String("web")`, `new Number(10)`) differ from its primitive literal when evaluated with `==` versus `===`?

[Back to question index](#question-index)

**Interview answer:** New String and new Number create objects around primitive values. Loose equality can unwrap them when comparing with primitives, but strict equality sees different types.

```js
const text = new String("web");
console.log(typeof text); // object
console.log(text == "web"); // true
console.log(text === "web"); // false
console.log(new Number(10) == 10); // true
console.log(Boolean(new Boolean(false))); // true
```

**Explanation:** The last wrapper is an object and therefore truthy, even though its contained Boolean is false. Avoid primitive wrapper constructors in ordinary application code. Use `String(value)` and `Number(value)` without new when conversion is intended.

<a id="question-30"></a>

## 30. How does the exponentiation operator (`**`) differ from standard multiplication (`*`)?

[Back to question index](#question-index)

**Interview answer:** Multiplication multiplies two values. Exponentiation raises a base to a power. Exponentiation groups right to left.

```js
console.log(2 * 3); // 6
console.log(2 ** 3); // 8
console.log(2 ** 3 ** 2); // 512: 2 ** (3 ** 2)
console.log((-2) ** 2); // 4
```

**Explanation:** Eight means two multiplied by itself three times. Right-to-left grouping makes the third expression two to the ninth power, not eight squared. Parenthesize a negative base; `-2 ** 2` is invalid syntax. Avoid confusing exponentiation with the bitwise XOR operator `^`.

<a id="question-31"></a>

## 31. What is the difference between `slice()` and `splice()` array methods?

[Back to question index](#question-index)

**Interview answer:** Slice copies a range without changing the source. Splice edits the source and returns removed items.

```js
const values = [1, 2, 3, 4];
console.log(JSON.stringify(values.slice(1, 3))); // [2,3]
console.log(JSON.stringify(values.splice(1, 2, 9))); // [2,3]
console.log(JSON.stringify(values)); // [1,9,4]
```

**Explanation:** Slice's second argument is an excluded end index; splice's second is a deletion count. Their matching return values here hide different source effects. Copies are shallow, so object elements can remain shared.

<a id="question-32"></a>

## 32. What is the difference between `map()` and `forEach()` array methods?

[Back to question index](#question-index)

**Interview answer:** Map creates an array of callback results. ForEach runs callbacks for their actions and returns undefined. Neither automatically awaits async callbacks.

```js
console.log(JSON.stringify([1, 2].map(n => n * 2))); // [2,4]
const result = [1, 2].forEach(n => n * 2);
console.log(result); // undefined
```

**Explanation:** Use map when the returned transformed data is needed. Use forEach for side effects, or a loop when you need break, continue, or sequential await. Both can mutate objects through their callbacks even though the methods themselves do not require source mutation.

<a id="question-33"></a>

## 33. How does the `reduce()` method function, and what roles do the `accumulator` and `index` arguments play?

[Back to question index](#question-index)

**Interview answer:** Reduce carries an accumulator through array entries. The callback receives accumulator, current value, index, and source array. Its return becomes the next accumulator.

```js
const total = [10, 20, 30].reduce((accumulator, value, index) => {
  console.log(index); // 0, then 1, then 2
  return accumulator + value;
}, 0);
console.log(total); // 60
```

**Explanation:** The initial zero controls the starting accumulator and allows empty input. Without an initial value, the first present entry starts the accumulator and callbacks start later; an empty array throws. The index is the array index, not the number of callback executions on sparse input. See C3 for grouping.

<a id="question-34"></a>

## 34. What are the functional differences between `some()`, `every()`, `find()`, and `findIndex()`?

[Back to question index](#question-index)

**Interview answer:** Some asks whether any entry passes; every asks whether all pass; find returns the first passing value; findIndex returns its position.

```js
const values = [1, 2, 3];
console.log(values.some(n => n > 2)); // true
console.log(values.every(n => n > 2)); // false
console.log(values.find(n => n > 2)); // 3
console.log(values.findIndex(n => n > 2)); // 2
```

**Explanation:** These stop when their answer is known. No match gives undefined for find and -1 for findIndex. Empty some is false and empty every is true. Compare a found index with -1; testing its truthiness wrongly rejects index zero.

<a id="question-35"></a>

## 35. What will `map()` return if an inline condition (`if (e > 0)`) executes inside the callback without an explicit return statement?

[Back to question index](#question-index)

**Interview answer:** For present entries, a callback with no returned value produces undefined. A conditional statement alone does not provide a result to map.

```js
const result = [-1, 2].map(e => { if (e > 0) { e * 2; } });
console.log(result.length, result[0], result[1]); // 2 undefined undefined
```

**Explanation:** The multiplication result is discarded. If the intention is to keep only positive entries, use filter. If the intention is transformation, return a value for each relevant path. Map preserves source length, including holes, rather than removing entries with undefined results.

<a id="question-36"></a>

## 36. What are the differences between `pop()` and `shift()` array methods?

[Back to question index](#question-index)

**Interview answer:** Pop removes and returns the last array entry. Shift removes and returns the first. Both mutate the array and return undefined when empty.

```js
const values = [1, 2, 3];
console.log(values.pop()); // 3
console.log(values.shift()); // 1
console.log(JSON.stringify(values)); // [2]
```

**Explanation:** Removing the front generally requires updating positions of remaining entries; repeatedly shifting a large array can be costly. A queue with a moving head index can avoid that repeated work. Choose the end according to the data structure's behavior.

<a id="question-37"></a>

## 37. How do shallow copies differ from deep copies, and how do you create a shallow copy using spread operators or `Object.assign()`?

[Back to question index](#question-index)

**Interview answer:** A shallow copy duplicates the outer object but shares nested reference values. A deep copy duplicates supported nested data.

```js
const source = { nested: { value: 1 } };
const a = { ...source };
const b = Object.assign({}, source);
console.log(a.nested === b.nested); // true
const deep = structuredClone(source);
console.log(deep.nested === source.nested); // false
```

**Explanation:** Spread and assign are shallow. StructuredClone handles many built-in values and cycles, but not functions or arbitrary custom class behavior. JSON copying loses or changes several values. Prefer copying only the changed nested path when updating application state.

<a id="question-38"></a>

## 38. What happens when an object key is assigned as another object (e.g., `obj[b] = 600` where `b` is an object)?

[Back to question index](#question-index)

**Interview answer:** A normal object's property key must be a string or symbol. An ordinary object used as a key converts to a string, which can cause collisions. Map preserves object identity as a key.

```js
const obj = {};
const a = {};
const b = {};
obj[a] = 500;
obj[b] = 600;
console.log(obj[a]); // 600
console.log(Object.keys(obj)[0]); // [object Object]
```

**Explanation:** Both key objects convert to the same text. The second write replaces the first. A Map could store both separately because a and b are different objects. Custom conversion can produce other keys, but relying on it often makes data ownership less clear.

<a id="question-39"></a>

## 39. How do array destructuring and object destructuring work (including property aliasing like `pqr: P`)?

[Back to question index](#question-index)

**Interview answer:** Destructuring extracts values into bindings. Array patterns use positions; object patterns use property names. A colon in an object pattern can rename the local variable.

```js
const [first, ...rest] = [1, 2, 3];
const { pqr: P, age = 18 } = { pqr: "Sam" };
console.log(first, rest.join(","), P, age); // 1 2,3 Sam 18
```

**Explanation:** P is the new binding; pqr is the source key. Defaults apply to undefined, not null. Destructuring does not deep-copy extracted objects. For a possibly null source, validate it or supply an appropriate fallback before destructuring.

<a id="question-40"></a>

## 40. How can you delete a specific property from an object?

[Back to question index](#question-index)

**Interview answer:** Delete removes a configurable own property. An immutable alternative is to create a new object using rest destructuring.

```js
const user = { name: "Sam", password: "secret" };
const { password, ...safe } = user;
console.log(Object.hasOwn(safe, "password")); // false
delete user.password;
console.log(Object.hasOwn(user, "password")); // false
```

**Explanation:** Rest leaves user unchanged; delete edits it. Assigning undefined leaves the property present, which differs from deletion. Non-configurable properties cannot be deleted; strict mode throws for that failure. Deleting an own property can also reveal an inherited property of the same name.

<a id="question-41"></a>

## 41. How can you convert an object's keys into an array (`Object.keys()`) or convert an object to a string?

[Back to question index](#question-index)

**Interview answer:** Object.keys returns own enumerable string keys. JSON.stringify serializes supported data to JSON text. String(object) is a general conversion and usually does not show an ordinary object's fields.

```js
const user = { name: "Sam", age: 25 };
console.log(Object.keys(user).join(",")); // name,age
console.log(JSON.stringify(user)); // {"name":"Sam","age":25}
console.log(String(user)); // [object Object]
```

**Explanation:** These answer different questions. JSON omits some unsupported values and throws for cycles and BigInt without special handling. Object.keys excludes symbols and non-enumerable properties. Use the representation appropriate to your storage or debugging task.

<a id="question-42"></a>

## 42. How are objects and arrays compared in JavaScript (referential equality)?

[Back to question index](#question-index)

**Interview answer:** Both arrays and objects compare by identity. Matching contents do not make separate objects equal under == or ===.

```js
const a = [1];
const b = a;
console.log(a === b); // true
console.log(a === [1]); // false
console.log({ id: 1 } == { id: 1 }); // false
```

**Explanation:** A shared reference compares equal. For data equality, decide which fields matter and whether nested values, ordering, cycles, and special types must be supported. Comparing JSON strings is not a universal deep-equality implementation.

<a id="question-43"></a>

## 43. What is the difference between `WeakSet` and `WeakMap`?

[Back to question index](#question-index)

**Interview answer:** WeakSet tracks membership; WeakMap associates keys with values. Their weak entries do not keep eligible keys or members alive by themselves. They do not expose normal iteration or size.

```js
const object = {};
const visited = new WeakSet([object]);
const metadata = new WeakMap([[object, { count: 1 }]]);
console.log(visited.has(object), metadata.get(object).count); // true 1
```

**Explanation:** Objects are the common weak keys/members; modern JavaScript also supports non-registered symbols. WeakMap values can be any type. Use these for object-linked metadata. Collection timing is unpredictable, so weak collections do not replace explicit timer and subscription cleanup.

<a id="question-44"></a>

## 44. How do `for...in` and `for...of` loops differ during iteration?

[Back to question index](#question-index)

**Interview answer:** For-in visits enumerable string property keys, including inherited ones. For-of visits values from an iterable.

```js
const values = ["a", "b"];
for (const key in values) console.log(key); // 0, then 1 (string keys)
for (const value of values) console.log(value); // a, then b
for (const [key, value] of Object.entries({ id: 1 })) {
  console.log(key, value); // id 1
}
```

**Explanation:** Plain objects are not iterable by default. Object.entries produces an iterable array of their own enumerable string entries. Avoid for-in for array values because additional properties can appear. Check Object.hasOwn when a property loop should exclude inherited entries.

<a id="question-45"></a>

## 45. How does `JSON.parse()` work in JavaScript?

[Back to question index](#question-index)

**Interview answer:** JSON.parse reads valid JSON text and returns the represented JavaScript value. Invalid JSON throws SyntaxError. Parsing does not validate your application's schema.

```js
const user = JSON.parse('{"name":"Sam","age":25}');
console.log(user.name); // Sam
try { JSON.parse("{name: 'Sam'}"); }
catch (error) { console.log(error.name); } // SyntaxError
```

**Explanation:** JSON requires double-quoted property names and strings, and does not support comments or trailing commas. It can represent an array or primitive, not just an object. Validate types and required fields afterward; do not replace JSON.parse with eval.

<a id="question-46"></a>

## 46. How are asynchronous operations managed in JavaScript (Callbacks, Promises, `async/await`)?

[Back to question index](#question-index)

**Interview answer:** A callback is passed for an operation to invoke. A promise represents an eventual outcome. Async/await lets us write promise-based flow in a readable sequence without blocking the whole thread.

```js
async function readUser() {
  const response = await fetch("/api/user");
  if (!response.ok) throw new Error(`HTTP ${response.status}`);
  return await response.json();
}
```

**Explanation:** The function always returns a promise. The caller must await it or attach handlers. Fetch can fulfill for HTTP errors, so status is checked explicitly. Async syntax does not move CPU-heavy work to another thread. Callbacks can also be synchronous, as in map.

<a id="question-47"></a>

## 47. What is Callback Hell (Pyramid of Doom), and how do Promises or `async/await` resolve it?

[Back to question index](#question-index)

**Interview answer:** Callback hell is deeply nested async flow that makes sequencing and failure handling hard to follow. Returning promises or awaiting them gives a flatter structure and a clear error boundary.

```js
async function loadDashboard() {
  const user = await loadUser();
  const orders = await loadOrders(user.id);
  return { user, orders };
}
// loadUser and loadOrders are your application API helpers.
```

**Explanation:** Orders depend on user, so the sequence is intentional. Independent requests can use Promise.all. Do not just convert callback syntax while keeping unnecessary sequential waits. Handle errors at the layer that can decide recovery or display useful feedback.

<a id="question-48"></a>

## 48. What are the three states of a Promise (`pending`, `fulfilled`, `rejected`)?

[Back to question index](#question-index)

**Interview answer:** A promise starts pending and can settle as fulfilled with a value or rejected with a reason. Once settled, its outcome cannot change.

```js
const promise = new Promise(resolve => resolve("done"));
promise.then(value => console.log(value)); // done, asynchronously
```

**Explanation:** The executor runs immediately, but promise handlers run as microtasks. Resolving with another pending promise adopts its eventual state, so “resolved” is not always “already fulfilled.” Repeated settlement attempts are ignored. Promises coordinate results; they do not inherently cancel operations or start threads.

<a id="question-49"></a>

## 49. What is the Event Loop, and what is the execution priority between Promises (Microtask queue) and `setTimeout` / `setInterval` (Macrotask queue)?

[Back to question index](#question-index)

**Interview answer:** The host event loop coordinates queued callbacks. Synchronous code finishes first; queued microtasks are drained at checkpoints before the next task. Promise reactions are microtasks; timers schedule task work.

```js
console.log("A");
setTimeout(() => console.log("B"), 0);
Promise.resolve().then(() => console.log("C"));
console.log("D");
// A, D, C, B
```

**Explanation:** Zero timeout is not immediate execution. Continuously scheduling microtasks can delay timers and rendering. Browser rendering opportunities and Node's event-loop phases need separate treatment; this output example does not define every scheduling situation.

<a id="question-50"></a>

## 50. What is the difference between `setTimeout()` and `setInterval()`, and how do you cancel their execution?

[Back to question index](#question-index)

**Interview answer:** SetTimeout schedules a callback once after a minimum requested delay. SetInterval schedules repeated callbacks. ClearTimeout and clearInterval cancel their scheduled future executions.

```js
const timeout = setTimeout(() => console.log("later"), 1000);
clearTimeout(timeout);
const interval = setInterval(() => console.log("tick"), 1000);
clearInterval(interval);
```

**Explanation:** This snippet prints nothing because cancellation happens immediately. Timing can be delayed by a busy thread or browser throttling. SetInterval does not await an async callback; operations can overlap. Recursive setTimeout after awaited work is useful when each polling request should finish before the next starts.

<a id="question-51"></a>

## 51. What are the phases of event propagation (Event Capturing, Event Bubbling)?

[Back to question index](#question-index)

**Interview answer:** An event travels through capturing ancestors toward its target, reaches the target, and then bubbles through ancestors if it is a bubbling event.

```js
const parent = document.querySelector("#parent");
parent.addEventListener("click", () => console.log("capture"), true);
parent.addEventListener("click", () => console.log("bubble"));
```

**Explanation:** Clicking a descendant runs the parent capture listener before its bubble listener, assuming propagation is not stopped. StopPropagation controls propagation; preventDefault controls default browser behavior. They are independent. Not every event bubbles, and stopPropagation does not stop other listeners already on the same element.

<a id="question-52"></a>

## 52. What is event targeting (`event.target`), and what is event delegation?

[Back to question index](#question-index)

**Interview answer:** Target is where the event originated, subject to retargeting in systems such as Shadow DOM. CurrentTarget is the element whose listener is running. Delegation puts one listener on a parent to handle child interactions.

```js
const list = document.querySelector("#list");
list.addEventListener("click", event => {
  if (!(event.target instanceof Element)) return;
  const button = event.target.closest("button[data-id]");
  if (!button || !list.contains(button)) return;
  console.log(button.dataset.id);
});
```

**Explanation:** Closest also handles clicking an icon inside the button. Delegation supports children added later and reduces individual listeners. The containment guard keeps the match inside the intended container. Use events that bubble or use an appropriate capture listener.

<a id="question-53"></a>

## 53. What are standard DOM event categories (Mouse, Keyboard, Form, and Window events)?

[Back to question index](#question-index)

**Interview answer:** Common categories include mouse/pointer interactions, keyboard input, form changes and submission, and window or document lifecycle events.

```js
input.addEventListener("input", event => console.log(event.target.value));
form.addEventListener("submit", event => event.preventDefault());
window.addEventListener("resize", () => console.log(window.innerWidth));
// input and form must be existing DOM elements.
```

**Explanation:** Prefer input for value editing instead of assuming keydown captures pasting and all input methods. Pointer events support more input devices than mouse-only handling. Use semantic buttons so keyboard interaction works. Debounce or throttle high-frequency work and remove persistent listeners during cleanup.

<a id="question-54"></a>

## 54. What are the differences between `localStorage` and `sessionStorage` regarding persistence, capacity, and tab lifecycle?

[Back to question index](#question-index)

**Interview answer:** LocalStorage persists across sessions subject to browser policy and deletion. SessionStorage is per origin and tab/page session, normally survives reloads, and ends with that session. Both store strings synchronously.

```js
localStorage.setItem("theme", "dark");
sessionStorage.setItem("step", "2");
console.log(localStorage.getItem("theme")); // dark
```

**Explanation:** Do not promise a universal capacity number; quotas and behavior vary by browser and mode. Writes can throw. Use IndexedDB for larger structured async storage. Same-origin JavaScript can read these stores, so they are not a secure vault for secrets. A new tab can initially copy opener session data, then have independent storage. [Web Storage documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API).

<a id="question-55"></a>

## 55. What is the difference between named exports and default exports in JavaScript modules?

[Back to question index](#question-index)

**Interview answer:** A module can have multiple named exports and at most one default export. Named imports use the exported name, optionally aliased. A default import can choose its local name.

```js
// math.js
export const add = (a, b) => a + b;
export default function multiply(a, b) { return a * b; }

// main.js (a separate file)
import multiplyNumbers, { add as sum } from "./math.js";
console.log(sum(2, 3), multiplyNumbers(2, 3)); // 5 6
```

**Explanation:** The braces select named bindings, not object destructuring. ES module imports are live read-only bindings. Consistent named exports can make refactoring clearer, while default exports are useful when a module has one central value.

<a id="question-56"></a>

## 56. What error types exist in JavaScript (e.g., `ReferenceError`, `SyntaxError`, `TypeError`, runtime errors)?

[Back to question index](#question-index)

**Interview answer:** SyntaxError means invalid syntax or invalid parsed data; ReferenceError commonly means a missing or uninitialized binding; TypeError means an operation is invalid for the value; RangeError means an invalid range. Runtime error describes when an error happens, not one specific class.

```js
try { JSON.parse("invalid"); }
catch (error) { console.log(error.name); } // SyntaxError
try { null.name; }
catch (error) { console.log(error.name); } // TypeError
```

**Explanation:** Catch handles executed exceptions and awaited rejections, not arbitrary errors thrown later in separate callbacks. A syntax error that prevents the surrounding file from parsing cannot be caught by a try statement in that same unparsed file. Preserve causes when adding context and avoid silently swallowing unexpected failures.

<a id="question-57"></a>

## 57. What built-in popup boxes exist in JavaScript (`alert`, `prompt`, `confirm`)?

[Back to question index](#question-index)

**Interview answer:** Alert shows a message, prompt requests text and returns a string or null, and confirm requests a Boolean decision. These are browser APIs, not universal JavaScript APIs.

```js
const name = prompt("Your name?");
if (name !== null) alert(`Hello ${name}`);
const accepted = confirm("Continue?");
console.log(accepted); // true for OK; false for Cancel
```

**Explanation:** Null means prompt was canceled; an empty string means the user submitted empty text. Native dialogs block script interaction while open in typical use and browsers may suppress them. Accessible application dialogs usually provide better control over focus, validation, and styling.

# React and Package Management

React examples use function components and hooks. Put hook calls at the top level of a component or custom hook. JSX requires a build tool or framework setup; it is not directly runnable in Node's ordinary JavaScript parser. Version-specific notes use current official documentation, checked on October 6, 2026.

<a id="question-58"></a>

## 58. What is ReactJS, and what are its primary architectural advantages?

[Back to question index](#question-index)

**Interview answer:** React is a library for building interfaces from components. I describe the UI from state and props, and React manages rendering and DOM updates. Components make behavior reusable and easier to test.

```jsx
function Greeting({ name }) {
  return <h1>Hello {name}</h1>;
}
```

**Explanation:** Props provide the input and JSX describes the result. React supports composition and declarative updates, but does not supply every application concern by itself. Routing, server rendering, data fetching, and build setup depend on the chosen framework or libraries. React does not automatically make every page faster; architecture and workload still matter.

<a id="question-59"></a>

## 59. What is the difference between the Real DOM and the Virtual DOM?

[Back to question index](#question-index)

**Interview answer:** The DOM is the browser's document tree. “Virtual DOM” is a common name for React's in-memory UI descriptions used to decide updates. React eventually commits changes to the real DOM.

```jsx
function Label({ count }) {
  return <span>{count}</span>;
}
```

**Explanation:** A new render describes the span with its new text. React can reuse the existing DOM element and update what changed. Rendering a component does not mean recreating all its DOM nodes. Comparing descriptions also costs work, so do not claim a virtual DOM is always faster than direct DOM updates.

<a id="question-60"></a>

## 60. What are the Reconciliation algorithm, Diffing algorithm, and batching mechanisms in React?

[Back to question index](#question-index)

**Interview answer:** Reconciliation determines how the new UI relates to the previous UI. Type, position, and keys help establish identity. Diffing is the comparison used during that work. Batching groups state updates to reduce separate renders.

```jsx
setCount(count => count + 1);
setCount(count => count + 1);
// If count starts at 0, the next state is 2.
```

**Explanation:** Updater functions operate on the queued state, so each increment is retained. Changing a component's type or key can reset its state. Do not describe reconciliation as a guarantee of the mathematically smallest set of DOM operations. Render work and committed DOM changes are different phases. [React state queueing](https://react.dev/learn/queueing-a-series-of-state-updates).

<a id="question-61"></a>

## 61. What is JSX, can web browsers parse JSX directly, and how is it transpiled?

[Back to question index](#question-index)

**Interview answer:** JSX is syntax for describing UI in JavaScript. Ordinary browser JavaScript parsers do not understand JSX; a compiler transforms it into JavaScript calls that create React elements.

```jsx
const title = <h1 className="title">Hello</h1>;
// The JSX transform produces JavaScript using a JSX runtime or createElement.
```

**Explanation:** JSX is not an HTML string. Expressions go inside braces, and components are normally capitalized. Modern automatic JSX transforms do not require importing React only to use JSX, but hooks and other APIs still need the appropriate imports. Compilation does not execute the component for the browser by itself.

<a id="question-62"></a>

## 62. What are the roles of module bundlers (e.g., Parcel, Webpack) and transpilers (e.g., Babel)?

[Back to question index](#question-index)

**Interview answer:** A bundler follows dependencies and prepares assets for delivery, often with code splitting and optimization. A transpiler transforms source syntax, such as JSX, into code the target environment can parse.

```js
import { add } from "./math.js";
console.log(add(2, 3));
// A build tool follows this import and prepares the application output.
```

**Explanation:** These responsibilities can be combined within one toolchain. Webpack and Parcel are bundlers; Babel is a transformation tool. A transformed async function may still rely on runtime support. Understand both the build output and the APIs available in target browsers instead of assuming compilation supplies every missing feature.

<a id="question-63"></a>

## 63. Why are `key` props required when rendering lists, and why is using the array index as a key discouraged?

[Back to question index](#question-index)

**Interview answer:** A key gives a list child a stable identity among siblings. I use a persistent data ID. Index keys can connect the wrong local state to an item after insertion, deletion, or reordering.

```jsx
function Users({ users }) {
  return <ul>{users.map(user => <li key={user.id}>{user.name}</li>)}</ul>;
}
```

**Explanation:** Keys need not be globally unique, but must be stable among those siblings. Random keys on every render cause remounts. Index keys can be acceptable for a truly static list. Key is not passed as an ordinary prop; pass id separately if the child needs it. [React list keys](https://react.dev/learn/rendering-lists).

<a id="question-64"></a>

## 64. What is Shimmer UI / skeleton loading screen?

[Back to question index](#question-index)

**Interview answer:** A skeleton shows the approximate shape of loading content. It can make progress clearer and reserve layout space, but should not pretend data has arrived.

```jsx
function LoadingCard() {
  return <div role="status" aria-label="Loading profile" className="skeleton" />;
}
```

**Explanation:** Match approximate content dimensions to reduce layout shifts. Provide an accessible status, handle error and empty states, and respect reduced-motion preferences for shimmer animation. Avoid showing a large skeleton for very fast operations if it produces distracting flashes. Skeletons improve presentation, not request speed.

<a id="question-65"></a>

## 65. What is the difference between Client-Side Rendering (CSR), Server-Side Rendering (SSR), and Hydration?

[Back to question index](#question-index)

**Interview answer:** CSR builds UI in the browser. SSR produces initial HTML on the server. Hydration connects client React behavior to server-rendered HTML.

```jsx
import { hydrateRoot } from "react-dom/client";
hydrateRoot(document.getElementById("root"), <App />);
// App is your imported application component; root contains server HTML.
```

**Explanation:** SSR can improve initial content availability, but client JavaScript and hydration still cost time. The initial client and server output must match; random values, local times, and browser-only state can cause mismatches. Choose based on content, interactivity, caching, and hosting needs. Server Components and SSR are related but different concepts; do not use the terms interchangeably.

<a id="question-66"></a>

## 66. What are the differences between Class components and Functional components?

[Back to question index](#question-index)

**Interview answer:** Class components use instance state, this, and lifecycle methods. Function components use props and hooks. I normally choose functions for new code because hooks make reusable stateful logic easier.

```jsx
import { useState } from "react";
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(value => value + 1)}>{count}</button>;
}
```

**Explanation:** Functions are not limited to stateless display. Hooks provide state and synchronization. Existing classes still work, and traditional React error boundaries are implemented with class lifecycle APIs or a library/framework wrapper. A class-to-function rewrite is not automatically a performance improvement.

<a id="question-67"></a>

## 67. How do you manage component lifecycle phases (mounting, updating, unmounting/cleanup) in functional components using `useEffect`?

[Back to question index](#question-index)

**Interview answer:** Effects synchronize a component with external systems. After a commit, setup can subscribe or connect. Cleanup undoes that setup before a changed-dependency rerun and when the component is removed.

```jsx
import { useEffect } from "react";
function ResizeLogger() {
  useEffect(() => {
    const handler = () => console.log(window.innerWidth);
    window.addEventListener("resize", handler);
    return () => window.removeEventListener("resize", handler);
  }, []);
  return null;
}
```

**Explanation:** Keep setup and cleanup symmetrical. Development Strict Mode can run an extra setup/cleanup cycle to expose mistakes. An effect is not required for a value that can be calculated during rendering. [Synchronizing with effects](https://react.dev/learn/synchronizing-with-effects).

<a id="question-68"></a>

## 68. What happens if `useEffect` is passed without a dependency array, with an empty array `[]`, or with specific state/prop dependencies (or `null`)?

[Back to question index](#question-index)

**Interview answer:** Omitting dependencies runs the effect after each relevant commit. Empty dependencies mean no reactive values trigger reruns. A dependency list reruns when an entry changes according to Object.is. Use an array or omit the argument; null is not the documented dependency-list interface.

```jsx
useEffect(() => { console.log("each commit"); });
useEffect(() => { console.log("setup"); }, []);
useEffect(() => { console.log(userId); }, [userId]);
// Inside a component, with useEffect imported and userId supplied.
```

**Explanation:** Include every reactive value used by setup. Do not hide dependencies to suppress a rerun. Empty dependencies do not mean once for the whole application's lifetime: remounts and development checks matter. Object/function dependencies created each render may change identity unnecessarily. [useEffect reference](https://react.dev/reference/react/useEffect).

<a id="question-69"></a>

## 69. What is the difference between `useEffect` and `useLayoutEffect` hooks?

[Back to question index](#question-index)

**Interview answer:** UseEffect is the usual choice for external synchronization. UseLayoutEffect runs before repaint and can measure layout and update UI before it becomes visible. It blocks painting, so use it only when that timing is necessary.

```jsx
import { useLayoutEffect, useRef, useState } from "react";
function MeasuredBox() {
  const ref = useRef(null);
  const [height, setHeight] = useState(0);
  useLayoutEffect(() => {
    setHeight(ref.current.getBoundingClientRect().height);
  }, []);
  return <div ref={ref}>Height: {height}</div>;
}
```

**Explanation:** This is an initial-measurement demonstration, not a continuously accurate resize monitor. Layout effects do not run during server rendering. Avoid the absolute claim that useEffect always runs after paint; interaction-driven timing can differ. [useLayoutEffect reference](https://react.dev/reference/react/useLayoutEffect).

<a id="question-70"></a>

## 70. What is the difference between `useMemo` and `useCallback` hooks, and how does memoization work?

[Back to question index](#question-index)

**Interview answer:** UseMemo caches a calculation result between renders. UseCallback caches a function identity. Dependencies control when a new result or function is needed.

```jsx
const visible = useMemo(() => items.filter(item => item.active), [items]);
const onSave = useCallback(() => save(userId), [save, userId]);
// Inside a component, with hooks imported and inputs provided.
```

**Explanation:** Use these for measured expensive work or useful stable props, not by default everywhere. Unstable dependencies can defeat the cache. Memoization must not be required for correctness. Projects using React Compiler may need less manual memoization; do not assume every project uses it. [useMemo](https://react.dev/reference/react/useMemo), [useCallback](https://react.dev/reference/react/useCallback).

<a id="question-71"></a>

## 71. What is the difference between `useState` and `useReducer` hooks?

[Back to question index](#question-index)

**Interview answer:** UseState fits simple independent updates. UseReducer centralizes related transitions in a reducer receiving current state and an action, which helps with complex workflows.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "increment": return { ...state, count: state.count + 1 };
    case "reset": return { count: 0 };
    default: return state;
  }
}
const [state, dispatch] = useReducer(reducer, { count: 0 });
// Hook line belongs inside a component with useReducer imported.
```

**Explanation:** A reducer should be pure. Keep API calls outside it and dispatch actions describing outcomes. UseReducer is local component state, not automatically a global store. Choose based on transition complexity rather than just the number of fields.

<a id="question-72"></a>

## 72. Is `useState` synchronous or asynchronous, and why?

[Back to question index](#question-index)

**Interview answer:** A state setter requests an update for a later render. It does not change the current render's variable. React can batch updates. Calling it asynchronous is a useful shorthand, but it is not a promise you can await.

```jsx
// Inside a click handler where count is currently 0:
setCount(count + 1);
console.log(count); // 0: this handler sees the current render's snapshot.
setCount(value => value + 1);
```

**Explanation:** The first update requests one; the updater then computes two from that queued value. Each render provides its own state snapshot and callbacks close over it. Use functional updates when the new value depends on previous state. Awaiting setCount does not wait for DOM changes. [useState reference](https://react.dev/reference/react/useState).

<a id="question-73"></a>

## 73. What are Higher-Order Components (HOCs), and in what scenarios are they applied?

[Back to question index](#question-index)

**Interview answer:** An HOC takes a component and returns an enhanced component. It can add behavior such as shared loading presentation. Hooks often simplify shared logic, but HOCs remain useful in existing APIs.

```jsx
function withLoading(Component) {
  return function Enhanced({ loading, ...props }) {
    if (loading) return <p role="status">Loading...</p>;
    return <Component {...props} />;
  };
}
```

**Explanation:** The wrapper preserves remaining props and conditionally renders. Create the enhanced component outside another component's render to avoid generating a new component type every time. HOCs can introduce wrapper nesting and prop naming conflicts. Client-side permission wrappers improve UI, but server authorization is still required.

<a id="question-74"></a>

## 74. What are custom hooks, and why are they created?

[Back to question index](#question-index)

**Interview answer:** A custom hook is a function named with use that composes hooks into reusable logic. It shares the logic, not necessarily one shared state instance.

```jsx
import { useState } from "react";
function useToggle(initial = false) {
  const [value, setValue] = useState(initial);
  const toggle = () => setValue(current => !current);
  return [value, toggle];
}
```

**Explanation:** Two components calling useToggle get independent states. To share one value, lift it up or use an appropriate provider/store. Custom hooks must follow hook ordering rules. Use a clear return contract and keep dependencies visible. See C8 for a debounced value hook.

<a id="question-75"></a>

## 75. What is the difference between controlled and uncontrolled components?

[Back to question index](#question-index)

**Interview answer:** A controlled input gets its current value from React state and reports edits through onChange. An uncontrolled input keeps its current value in the DOM and can be read through a ref or FormData.

```jsx
const [name, setName] = useState("");
return <input value={name} onChange={event => setName(event.target.value)} />;
// Inside a component with useState imported.
```

**Explanation:** Controlled state helps live validation and dependent UI. Uncontrolled forms can reduce updates and fit simple submissions. DefaultValue supplies an uncontrolled initial value; value controls it. Do not switch an input between undefined and a defined controlled value. Add a label in a complete UI; see C9.

<a id="question-76"></a>

## 76. Why are React Fragments (`<>...</>`) preferred over container `<div>` elements?

[Back to question index](#question-index)

**Interview answer:** A Fragment groups sibling elements without adding a DOM wrapper. This avoids unwanted layout structure and can preserve valid markup, such as table rows containing cells.

```jsx
function Cells() {
  return <><td>Sam</td><td>25</td></>;
}
// Render Cells inside a table row.
```

**Explanation:** A div inside a row would be invalid structure. Use an actual wrapper when styling or layout needs an element. The short fragment form cannot take a key; use `<Fragment key={id}>` with an import for keyed groups in a list. Fragments have no element to target with ordinary CSS classes.

<a id="question-77"></a>

## 77. How do you prevent memory leaks in React applications?

[Back to question index](#question-index)

**Interview answer:** Clean up subscriptions, timers, observers, and global listeners. Cancel or ignore outdated async results. A component disappearing does not automatically release external resources that still retain references.

```jsx
useEffect(() => {
  const timer = setInterval(() => setCount(value => value + 1), 1000);
  return () => clearInterval(timer);
}, []);
// Inside a component with useEffect and setCount available.
```

**Explanation:** The functional update avoids closing over an old count. Not every late state update proves a memory leak; retained resources are the real concern. Use heap snapshots for suspected leaks. A request cleanup should also protect against stale responses when cancellation alone is insufficient. See C7 for a complete pattern. [Effect cleanup](https://react.dev/learn/synchronizing-with-effects).

<a id="question-78"></a>

## 78. What techniques can be used to optimize React application performance (e.g., image optimization, lazy loading, code splitting, memoization, Lighthouse audits)?

[Back to question index](#question-index)

**Interview answer:** I measure the slow interaction first, then fix the main cost. Options include reducing unnecessary renders, localizing state, virtualizing large lists, splitting code, optimizing images, and caching requests appropriately.

```jsx
import { lazy, Suspense } from "react";
const Reports = lazy(() => import("./Reports.jsx"));
function Page() {
  return <Suspense fallback={<p>Loading reports...</p>}><Reports /></Suspense>;
}
```

**Explanation:** Lazy defers loading that module; the default export must be a component in this example. Suspense handles waiting for the lazy module, not arbitrary fetch calls in effects. Use an error boundary for load failures. React Profiler finds render costs; browser tools and Lighthouse measure broader page behavior. Recheck with production builds and representative devices.

<a id="question-79"></a>

## 79. What is the difference between state and props?

[Back to question index](#question-index)

**Interview answer:** Props are inputs supplied by a parent. State is data owned by a component or state system that changes over time. Treat both as read-only during rendering.

```jsx
function Counter({ step }) {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(value => value + step)}>{count}</button>;
}
// Import useState in this component's module.
```

**Explanation:** Step comes from the parent; count is locally owned. Mutating an object prop can silently change shared data without the expected render behavior. Avoid copying props into state unless independent state is intended; otherwise the copy can become stale.

<a id="question-80"></a>

## 80. What is prop drilling, and how can it be avoided?

[Back to question index](#question-index)

**Interview answer:** Prop drilling passes data through intermediate components that do not use it. I first consider composition or moving ownership closer to consumers. Context or a store helps when many distant components need the data.

```jsx
<Layout sidebar={<UserMenu user={user} />} />
// Composition lets Layout position the sidebar without receiving each user field.
```

**Explanation:** A few explicit prop levels are not automatically a problem. Globalizing every value makes ownership harder. Context is useful for broad concerns such as theme; rapidly changing shared data may benefit from selective store subscriptions. Choose based on actual consumers and update patterns.

<a id="question-81"></a>

## 81. What is the Context API, and how does it compare to Redux / Redux Toolkit?

[Back to question index](#question-index)

**Interview answer:** Context distributes a value through a subtree. Redux provides a structured external store with actions, reducers, subscriptions, and tooling. Redux Toolkit is the usual way to write Redux with less boilerplate.

```jsx
const theme = useContext(ThemeContext);
// ThemeContext must be created and provided by an ancestor.
```

**Explanation:** Context consumers update when their provider value changes; splitting contexts can reduce unrelated updates. Context is not a server-data cache by itself. Redux suits complex shared transitions and tracing. Server data can use a query cache such as RTK Query or another library. Avoid adding a global store solely to remove one prop.

<a id="question-82"></a>

## 82. What are the core building blocks of Redux (Store, Actions, Reducers / Slices, `useSelector`)?

[Back to question index](#question-index)

**Interview answer:** A store holds state; an action describes an event; a reducer calculates the next state. Toolkit slices group reducer logic and generated action creators. UseSelector reads a selected value and subscribes a React component.

```jsx
import { configureStore, createSlice } from "@reduxjs/toolkit";
const counterSlice = createSlice({
  name: "counter",
  initialState: { value: 0 },
  reducers: { increment(state) { state.value += 1; } },
});
const store = configureStore({ reducer: { counter: counterSlice.reducer } });
store.dispatch(counterSlice.actions.increment());
console.log(store.getState().counter.value); // 1
```

**Explanation:** Toolkit's Immer integration turns this draft change into an immutable update. In React, provide the store using Provider, then read `useSelector(state => state.counter.value)`. Do not mutate the actual stored state outside reducers. [createSlice documentation](https://redux-toolkit.js.org/api/createSlice).

<a id="question-83"></a>

## 83. What is the role of a Reducer function in Redux?

[Back to question index](#question-index)

**Interview answer:** A reducer returns next state from previous state and an action. It should be deterministic and free of side effects, so transitions can be reproduced and tested.

```js
function counterReducer(state = { value: 0 }, action) {
  if (action.type === "increment") return { ...state, value: state.value + 1 };
  return state;
}
```

**Explanation:** This plain reducer creates a changed object and preserves state for unrelated actions. Do not fetch, schedule timers, or generate random values inside it. Put those operations in an appropriate async layer and dispatch results. Toolkit draft mutation syntax is permitted by its wrapper; arbitrary mutation in a plain reducer is not the same thing.

<a id="question-84"></a>

## 84. Which package handles routing in React (`react-router-dom`), and how do normal routing and dynamic routing work (`useParams`, `useLocation`)?

[Back to question index](#question-index)

**Interview answer:** React Router maps locations to UI. A path like `/users/:id` has a dynamic parameter available through useParams. UseLocation exposes the current location, including pathname and search.

```jsx
import { BrowserRouter, Routes, Route, useParams } from "react-router-dom";
function UserPage() {
  const { id } = useParams();
  return <h1>User {id}</h1>;
}
function App() {
  return <BrowserRouter><Routes>
    <Route path="/users/:id" element={<UserPage />} />
  </Routes></BrowserRouter>;
}
```

**Explanation:** This uses the familiar DOM package API; current router documentation also uses react-router imports. Match your installed version and mode. Parameters are strings to validate. Query values can be read with useSearchParams. Use links for navigation, handle missing routes, and configure hosting for deep-link reloads. [Routing documentation](https://reactrouter.com/start/declarative/routing).

<a id="question-85"></a>

## 85. What is the difference between the caret (`^`) and tilde (`~`) version operators in `package.json`?

[Back to question index](#question-index)

**Interview answer:** For normal versions above zero, caret allows compatible minor and patch updates; tilde usually allows patch updates within the stated minor. Pre-1.0 caret ranges are more restrictive.

```text
^1.2.3  => >=1.2.3 and <2.0.0
~1.2.3  => >=1.2.3 and <1.3.0
^0.2.3  => >=0.2.3 and <0.3.0
^0.0.3  => >=0.0.3 and <0.0.4
```

**Explanation:** These are permitted ranges, not a guarantee that every install takes the newest version. A matching lockfile fixes resolved versions. Compatibility also depends on package authors following semantic versioning. Review upgrades and run checks rather than trusting the symbol alone. [npm semver rules](https://github.com/npm/node-semver#caret-ranges-123-025-004).

<a id="question-86"></a>

## 86. What is the difference between `package.json` and `package-lock.json`?

[Back to question index](#question-index)

**Interview answer:** Package.json declares project metadata, scripts, and dependency ranges. Package-lock records the resolved dependency tree and integrity details so installs can be reproduced.

```json
{
  "scripts": { "test": "node --test" },
  "dependencies": { "example-package": "^1.2.3" }
}
```

**Explanation:** This is an illustrative manifest, not an instruction to install that example package. Commit the lockfile for an application. npm ci requires a matching manifest and lockfile and is suitable for reproducible CI installs. A lockfile does not mean dependencies are automatically safe or never need updates. [npm lockfile documentation](https://docs.npmjs.com/files/package-lock.json/).

<a id="question-87"></a>

## 87. What is the difference between regular `dependencies` and `devDependencies`?

[Back to question index](#question-index)

**Interview answer:** Dependencies are needed by the application in its intended runtime or distribution. DevDependencies support development tasks such as tests and builds. Classification depends on how the project is built and deployed.

```json
{
  "dependencies": { "react": "^19.0.0" },
  "devDependencies": { "typescript": "^5.0.0" }
}
```

**Explanation:** These are example ranges, not recommendations for latest versions. A frontend deployment may serve built files without node_modules, but its build still needs compiler tools. A Node server needs its runtime packages available after dev dependencies are omitted. Do not assume moving a package to devDependencies automatically removes it from a browser bundle.

# HTML

Use native semantics first. HTML examples are markup fragments unless they name separate files. In an interview, connect semantics to accessibility, default browser behavior, and maintainability.

<a id="question-88"></a>

## 88. What is the difference between `<div>` and `<span>` tags (Block-level vs Inline elements)?

[Back to question index](#question-index)

**Interview answer:** Div is a generic container with block display by default. Span is a generic phrasing container with inline display by default. Neither adds meaningful semantics by itself.

```html
<div class="card">Hello <span class="name">Sam</span></div>
```

**Explanation:** The div normally starts a block; the span stays within the text flow. CSS can change either display, so tag meaning and display are separate. Use a heading, button, section, or other semantic element when it represents the content better. Do not use a clickable div where a real button fits.

<a id="question-89"></a>

## 89. What list types exist in HTML (`<ul>`, `<ol>`, `<dl>`)?

[Back to question index](#question-index)

**Interview answer:** Ul is an unordered list, ol is an ordered list, and dl represents groups of terms and descriptions. Use li inside ul/ol and dt/dd inside dl.

```html
<ul><li>JavaScript</li><li>React</li></ul>
<ol><li>Install</li><li>Run</li></ol>
<dl><dt>API</dt><dd>Application Programming Interface</dd></dl>
```

**Explanation:** Choose ol when sequence matters, such as instructions. Use ul when item order is not essential. A description list can express metadata as well as dictionary definitions. Proper list markup communicates relationships beyond visual bullets.

<a id="question-90"></a>

## 90. What text formatting tags are available in HTML (`<b>`, `<i>`, `<u>`, `<strong>`, `<em>`, `<mark>`, `<sup>`, `<sub>`)?

[Back to question index](#question-index)

**Interview answer:** Strong represents importance, em represents stress emphasis, mark highlights relevant text, and sup/sub represent superscripts/subscripts. B draws attention without added importance; i marks text in an alternate voice or convention. U represents an annotation, such as a spelling issue.

```html
<p><strong>Warning:</strong> This action <em>cannot</em> be undone.</p>
<p>Water: H<sub>2</sub>O. Area: m<sup>2</sup>.</p>
<p>Search match: <mark>JavaScript</mark></p>
```

**Explanation:** Use CSS when the purpose is only visual styling. An underline can look like a link, so avoid confusing users. These elements describe meaning; their default bold or italic appearance can be changed. [HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements).

<a id="question-91"></a>

## 91. What is the difference between `<b>` and `<strong>` tags, and `<i>` vs `<em>` tags?

[Back to question index](#question-index)

**Interview answer:** Strong means importance; b means attention without extra importance. Em means stress emphasis; i means alternate voice or convention. Their default appearances may match, but their meanings differ.

```html
<p><strong>Do not share this password.</strong></p>
<p>Click <b>Save</b> to continue.</p>
<p>I said <em>today</em>, not tomorrow.</p>
```

**Explanation:** Do not claim every screen reader always speaks these in a particular way; support and settings differ. Choose the semantic element for the content and CSS for design. Accessibility is based on the complete structure and interaction, not just selecting strong instead of b.

<a id="question-92"></a>

## 92. What are void / empty / self-closing elements in HTML (e.g., `<img>`, `<br>`, `<hr>`)?

[Back to question index](#question-index)

**Interview answer:** Void elements such as img, input, br, hr, meta, and link cannot contain children and have no end tag. HTML's optional trailing slash does not create a general self-closing mechanism.

```html
<img src="avatar.png" alt="Sam">
<br>
<input type="text" name="name">
```

**Explanation:** `<div />` does not mean a self-closed div in ordinary HTML. JSX has different syntax rules and requires closing elements, often using `<img />`. Br represents a line break and hr a thematic break, not merely spacing tools. Use CSS spacing instead of repeated breaks.

<a id="question-93"></a>

## 93. What is the purpose of the `required` attribute in form inputs?

[Back to question index](#question-index)

**Interview answer:** Required participates in browser constraint validation. A supported required field must have an acceptable value before a normal validated form submission proceeds.

```html
<form>
  <label for="email">Email</label>
  <input id="email" name="email" type="email" required>
  <button type="submit">Submit</button>
</form>
```

**Explanation:** Type=email also checks basic format. Required alone does not enforce every business rule, and whitespace may satisfy some required text inputs. Users or direct requests can bypass browser validation, so validate again on the server. Provide clear labels and errors, not only a visual asterisk.

<a id="question-94"></a>

## 94. What is the purpose of the `alt` attribute in `<img>` tags?

[Back to question index](#question-index)

**Interview answer:** Alt supplies a text alternative for an image. It should describe the image's purpose in context. Decorative images should normally have empty alt text.

```html
<img src="sales-chart.png" alt="Sales increased from 20 to 35 orders">
<img src="decoration.png" alt="">
```

**Explanation:** A chart may need a fuller nearby description or data table. A linked or button image should explain the action when it provides the control's accessible name. A filename is rarely helpful. Alt is not a tooltip, and figcaption does not automatically replace it.

<a id="question-95"></a>

## 95. What is the difference between `cellpadding` and `cellspacing` in HTML tables?

[Back to question index](#question-index)

**Interview answer:** Legacy cellpadding controls space inside cells; cellspacing controls gaps between cells. Use CSS instead because these presentational attributes are obsolete.

```css
table { border-collapse: separate; border-spacing: 8px; }
td, th { padding: 12px; }
```

**Explanation:** Padding separates cell content from its edge. Border-spacing applies gaps with the separate border model. With border-collapse: collapse, border-spacing does not create those gaps. Keep structure in HTML and presentation in CSS.

<a id="question-96"></a>

## 96. What tags are used to build HTML tables (`<table>`, `<thead>`, `<tbody>`, `<tr>`, `<td>`, `<th>`)?

[Back to question index](#question-index)

**Interview answer:** Table contains tabular data. Thead groups header rows, tbody groups body rows, tr represents a row, th a header cell, and td a data cell. Caption describes the table.

```html
<table>
  <caption>Team members</caption>
  <thead><tr><th scope="col">Name</th><th scope="col">Role</th></tr></thead>
  <tbody><tr><td>Sam</td><td>Developer</td></tr></tbody>
</table>
```

**Explanation:** Header associations help users understand data relationships. Use tables for data, not general page layout. Large or complex tables may need additional header associations and responsive handling rather than stripping semantics to make them look smaller.

<a id="question-97"></a>

## 97. How do you merge adjacent table cells across rows or columns (`colspan`, `rowspan`)?

[Back to question index](#question-index)

**Interview answer:** Colspan makes one cell span multiple columns. Rowspan makes it span multiple rows. Plan the table grid so later cells do not accidentally overlap the spanned area.

```html
<table>
  <tr><th colspan="2">Contact</th></tr>
  <tr><td rowspan="2">Sam</td><td>Email</td></tr>
  <tr><td>Phone</td></tr>
</table>
```

**Explanation:** The first header occupies two columns. Sam occupies the first column across two rows, so the last row needs only its second-column cell. This is a structural example; a real table needs useful headings and caption. Excessive merged cells can make data harder to navigate.

<a id="question-98"></a>

## 98. What is an image map (`<map>`, `<area>`), and how are clickable coordinates defined?

[Back to question index](#question-index)

**Interview answer:** An image map connects regions of an image to links using map and area. Shape decides how coords is interpreted: rectangle, circle, or polygon.

```html
<img src="floor.png" usemap="#rooms" alt="Office floor plan">
<map name="rooms">
  <area shape="rect" coords="0,0,100,80" href="/meeting-room" alt="Meeting room">
</map>
```

**Explanation:** Rectangle coordinates give left, top, right, bottom positions. Circle uses center x, center y, radius; polygon uses point pairs. Supply useful area alternatives and test keyboard access. Fixed coordinates can become incorrect when the displayed image scales; responsive SVG or ordinary links may be easier to maintain.

<a id="question-99"></a>

## 99. What are HTML character entities (e.g., `&copy;`, `&gt;`, `&lt;`)?

[Back to question index](#question-index)

**Interview answer:** HTML character references represent reserved or special characters. Common ones include ampersand, less-than, greater-than, and copyright.

```html
<p>&copy; 2026</p>
<code>&lt;button&gt;</code>
<p>A &amp; B</p>
```

**Explanation:** The browser displays ©, `<button>`, and `A & B`. Encoding angle brackets keeps literal text from being parsed as tags. Escaping must fit the context; HTML text escaping alone is not a universal defense for JavaScript, CSS, or URLs. For dynamic text, prefer textContent or normal framework text rendering.

<a id="question-100"></a>

## 100. What are Web Workers in HTML5?

[Back to question index](#question-index)

**Interview answer:** A Web Worker runs JavaScript off the page's main thread. It communicates with messages and cannot directly edit the page DOM.

```js
// main.js in a browser:
const worker = new Worker("worker.js");
worker.onmessage = event => console.log(event.data);
worker.postMessage(5);

// worker.js, a separate file:
self.onmessage = event => self.postMessage(event.data * 2);
// Main receives 10. Call worker.terminate() when it is no longer needed.
```

**Explanation:** Workers suit expensive computation, not trivial work where communication costs dominate. Data is usually cloned; transferable buffers can reduce copying. Worker is a Web API, not an HTML tag. Worker scripts and security/origin rules require an appropriate served environment.

<a id="question-101"></a>

## 101. What is the difference between the `<figure>` tag and `<img>` tag?

[Back to question index](#question-index)

**Interview answer:** Img embeds an image. Figure groups self-contained content that can be referenced separately from the surrounding text. A figure can contain an image, diagram, code, or other content.

```html
<figure>
  <img src="architecture.png" alt="Browser connects to API, which connects to database">
  <figcaption>Application request flow</figcaption>
</figure>
```

**Explanation:** Figure provides grouping; it does not replace img. Not every image needs a figure. Use it when the content and optional caption form a meaningful unit. Keep the alt text and caption useful without unnecessary repetition.

<a id="question-102"></a>

## 102. What is the purpose of the `<figcaption>` tag?

[Back to question index](#question-index)

**Interview answer:** Figcaption supplies a caption for a figure and belongs as its first or last child. It explains or labels the grouped content.

```html
<figure>
  <pre><code>const total = price * quantity;</code></pre>
  <figcaption>Calculating a line-item total</figcaption>
</figure>
```

**Explanation:** Captions can apply to code and diagrams, not only photographs. Figcaption is not a general caption for any arbitrary div. It does not automatically give an image its text alternative, so images still need appropriate alt handling.

<a id="question-103"></a>

## 103. What is the difference between `<meter>` and `<progress>` tags?

[Back to question index](#question-index)

**Interview answer:** Meter represents a measurement within a known range, such as disk usage. Progress represents completion of a task. Omitting progress's value gives an indeterminate progress indicator.

```html
<label for="disk">Disk usage</label>
<meter id="disk" min="0" max="100" value="70">70%</meter>
<label for="upload">Upload</label>
<progress id="upload" max="100" value="40">40%</progress>
```

**Explanation:** A 70% disk reading is not a task heading toward completion, so meter fits. An upload's 40% is completion, so progress fits. Provide a meaningful accessible label and relevant nearby status text rather than relying only on color.

<a id="question-104"></a>

## 104. How can you embed one web page inside another web page (`<iframe>`)?

[Back to question index](#question-index)

**Interview answer:** An iframe embeds another browsing context. Give it a useful title and restrict its capabilities as appropriate. Whether a remote page allows embedding depends on its response policy.

```html
<iframe src="/help" title="Help information" loading="lazy" sandbox></iframe>
```

**Explanation:** An empty sandbox is deliberately restrictive; add specific allowances only when required. Same-origin rules limit direct access to cross-origin iframe contents. Cross-origin communication can use postMessage with explicit origin checks. A site's frame-ancestors policy or X-Frame-Options may block embedding. Do not assume a page can be embedded just because its URL loads in a tab.

# CSS

<a id="question-105"></a>

## 105. What are the different methods to hide elements in CSS (`display: none`, `visibility: hidden`, `opacity: 0`), and how do they differ in viewport layout space allocation?

[Back to question index](#question-index)

**Interview answer:** Display none removes the element's layout box. Visibility hidden preserves its layout space but hides it. Opacity zero makes it transparent while retaining layout and generally preserving interaction and accessibility exposure.

```css
.removed { display: none; }
.reserved { visibility: hidden; }
.transparent { opacity: 0; }
```

**Explanation:** An opacity-zero button can still receive clicks and keyboard focus. Pointer-events none blocks pointer targeting, not keyboard focus. Display-none and visibility-hidden content is generally not available in the accessibility tree. If the goal is screen-reader-only text, use a tested visually-hidden pattern rather than these hiding techniques.

<a id="question-106"></a>

## 106. How do you create animations in CSS (Transitions vs `@keyframes`)?

[Back to question index](#question-index)

**Interview answer:** A transition animates a property when its value changes. Keyframes define a timed animation sequence that can repeat and include multiple stages.

```css
.button { transition: transform 150ms ease; }
.button:hover { transform: translateY(-2px); }
@keyframes pulse { from { opacity: .5; } to { opacity: 1; } }
.loading { animation: pulse 1s ease-in-out infinite alternate; }
@media (prefers-reduced-motion: reduce) {
  .button { transition: none; }
  .loading { animation: none; }
}
```

**Explanation:** Transform and opacity often avoid repeated layout work, but measure actual behavior. Avoid excessive animation, and respect reduced-motion preferences. A transition needs a change between values; a keyframe animation can run without user hover.

<a id="question-107"></a>

## 107. What is the universal selector (`*`) in CSS?

[Back to question index](#question-index)

**Interview answer:** The universal selector matches elements regardless of their tag name. It does not by itself add specificity. Pseudo-elements need to be selected separately for a reset.

```css
*, *::before, *::after { box-sizing: border-box; }
```

**Explanation:** This makes declared sizes easier to reason about by including padding and border. The universal selector does not mean every conceivable style automatically inherits. Avoid broad resets that remove useful default focus indicators or semantics-related presentation without providing accessible replacements.

<a id="question-108"></a>

## 108. What are the three types of CSS styling (Inline, Internal, External)?

[Back to question index](#question-index)

**Interview answer:** Inline CSS uses a style attribute, internal CSS uses a style element, and external CSS uses a linked stylesheet. External styles are usually easiest to share and maintain across pages.

```html
<link rel="stylesheet" href="styles.css">
<style>.notice { color: navy; }</style>
<p class="notice" style="font-weight: bold">Saved</p>
```

**Explanation:** The stylesheet and style element both contribute CSS rules to the cascade. Inline styling applies declarations directly to the element. These locations do not by themselves provide a complete priority ranking; question 109 explains why internal styles do not always beat external ones.

<a id="question-109"></a>

## 109. What is the specificity and priority order among Inline, Internal, and External CSS?

[Back to question index](#question-index)

**Interview answer:** There is no universal “inline, then internal, then external” ranking. The cascade considers relevance, origin and importance, layers, specificity, scoping proximity where applicable, and source order. Internal and external rules are both author rules.

```css
#message { color: red; }
.notice { color: blue; }
/* For the same element in comparable cascade positions, the ID selector wins. */
```

**Explanation:** An external ID rule can beat a later internal class rule. Inline normal declarations generally beat normal author stylesheet rules, but important rules and other cascade stages can change the winner. Among otherwise comparable selectors, IDs outrank classes/attributes/pseudo-classes, which outrank types/pseudo-elements. Equal rules can be resolved by later order. Important is not a specificity score. [Specificity and the cascade](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascade/Specificity).

<a id="question-110"></a>

## 110. What is the CSS Box Model, and what is the sequence of layers from inside to outside (Content, Padding, Border, Margin)?

[Back to question index](#question-index)

**Interview answer:** From inside outward, a box has content, padding, border, and margin. With content-box, width describes content; with border-box, width includes content, padding, and border.

```css
.box { width: 200px; padding: 20px; border: 5px solid; box-sizing: border-box; }
```

**Explanation:** This box's border-box width is 200px and content width is 150px. With content-box, its border-box width would be 250px. Margins are outside that width. Vertical margins can collapse in certain block layouts, so total spacing is not always the sum of every listed margin.

<a id="question-111"></a>

## 111. What is the difference between CSS `border` and `outline`?

[Back to question index](#question-index)

**Interview answer:** Border participates in the box model. Outline is drawn around the element without reserving layout space. Outlines are useful for visible keyboard focus.

```css
.button { border: 1px solid #444; }
.button:focus-visible { outline: 3px solid blue; outline-offset: 3px; }
```

**Explanation:** Increasing border width can change dimensions under content-box. An outline does not push neighbors away and can overlap them. Do not remove outline without providing a visible, accessible focus indicator. Outline is not suitable when a layout needs real reserved border space.

<a id="question-112"></a>

## 112. What is the difference between CSS pseudo-classes and pseudo-elements?

[Back to question index](#question-index)

**Interview answer:** A pseudo-class selects an element based on state or a relationship, such as hover or first-child. A pseudo-element targets a generated part or part of an element, such as before or first-line.

```css
button:hover { background: navy; color: white; }
p::first-line { font-weight: bold; }
.required::after { content: " *"; }
```

**Explanation:** Use single colon for pseudo-classes and double colon for pseudo-elements in current style. Do not put essential instructions only in generated content because accessibility exposure can vary. Important labels and errors belong in actual markup. Hover-only interactions also need keyboard support.

<a id="question-113"></a>

## 113. What are the different CSS `position` values (`static`, `relative`, `absolute`, `fixed`, `sticky`)?

[Back to question index](#question-index)

**Interview answer:** Static follows normal flow. Relative stays in flow and can be offset. Absolute leaves normal flow and uses a containing block. Fixed usually uses the viewport. Sticky stays in flow and sticks at an inset within its scrolling constraints.

```css
.card { position: relative; }
.badge { position: absolute; top: 8px; right: 8px; }
.header { position: sticky; top: 0; }
```

**Explanation:** The card provides the badge's positioning context in this example. Sticky needs an inset such as top and enough available scrolling space. Ancestor overflow and containing blocks affect results. Transformed ancestors can change the containing block for fixed descendants, so “fixed always means viewport” is incomplete.

<a id="question-114"></a>

## 114. What is `z-index`, and how does it control element stacking order and parent-child constraints?

[Back to question index](#question-index)

**Interview answer:** Z-index orders eligible boxes within a stacking context. A child cannot escape its parent's stacking context just by using a huge z-index. First inspect the surrounding contexts.

```css
.panel { position: relative; z-index: 1; }
.panel .popup { position: absolute; z-index: 9999; }
.other-panel { position: relative; z-index: 2; }
```

**Explanation:** The popup still belongs to panel's lower context and can be covered by other-panel. Opacity, transforms, and other properties can create contexts. Flex/grid items can use z-index without conventional positioning. Use a portal or appropriate top-layer mechanism for overlays where suitable, rather than endlessly increasing numbers.

<a id="question-115"></a>

## 115. What are CSS combinators?

[Back to question index](#question-index)

**Interview answer:** Combinators express relationships between selectors: descendant space, direct child `>`, next sibling `+`, and subsequent sibling `~`.

```css
.card p { color: navy; }      /* Any descendant paragraph. */
.card > p { padding: 4px; }  /* Direct child paragraph. */
h2 + p { font-weight: bold; } /* Immediately following sibling paragraph. */
h2 ~ p { margin-left: 8px; }  /* Later sibling paragraphs under the same parent. */
```

**Explanation:** Sibling combinators require a shared parent; they do not mean any later element in the document. Combinators do not add specificity by themselves. Avoid very brittle selectors tied to unnecessary nesting when a clear component class would be easier to maintain.

<a id="question-116"></a>

## 116. What are CSS counters?

[Back to question index](#question-index)

**Interview answer:** Counters maintain a CSS-controlled count and display it through generated content. They can number sections or custom presentations.

```css
.sections { counter-reset: section; }
.sections h2 { counter-increment: section; }
.sections h2::before { content: counter(section) ". "; }
```

**Explanation:** Reset establishes the counter, increment changes it for matching headings, and counter renders it. For a real ordered list, use ol rather than replacing semantic numbering solely with generated content. Counter scope and nested resets matter when numbering nested sections.

<a id="question-117"></a>

## 117. How do you vertically center text using Flexbox?

[Back to question index](#question-index)

**Interview answer:** With the default row direction, align-items centers on the vertical cross axis and justify-content centers on the horizontal main axis. The axes change with flex-direction.

```css
.center {
  display: flex;
  min-height: 200px;
  align-items: center;
  justify-content: center;
}
```

**Explanation:** The height gives visible vertical space to center within. With column direction, justify-content is vertical and align-items is horizontal. These center the flex items; text-align controls inline text alignment inside a wider item. Do not memorize vertical/horizontal names without checking the axis.

<a id="question-118"></a>

## 118. What are the key differences between Flexbox and CSS Grid?

[Back to question index](#question-index)

**Interview answer:** Flexbox primarily arranges content along one axis. Grid controls rows and columns together. I use Flexbox for a toolbar or aligned row, and Grid for a two-dimensional page or card layout.

```css
.toolbar { display: flex; gap: 12px; align-items: center; }
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 240px), 1fr));
  gap: 16px;
}
```

**Explanation:** The grid adds as many suitable columns as fit; the inner min avoids forcing a 240px track into a narrower container. Flex wrapping still organizes each line independently. The two systems can be combined. Avoid visual reordering that makes keyboard and screen-reader order confusing.

# Node.js, APIs, Databases, and Architecture

Backend snippets explain patterns. They are not a complete production application: authentication, authorization, validation, logging, configuration, and deployment must match the system. Express examples distinguish version 5 behavior from version 4.

<a id="question-119"></a>

## 119. How does Node.js execute JavaScript on the server using Google Chrome's V8 engine?

[Back to question index](#question-index)

**Interview answer:** Node is a JavaScript runtime built around V8 and host facilities such as networking and filesystem APIs. V8 runs JavaScript; Node's event loop and libuv help coordinate async I/O.

```js
import { readFile } from "node:fs/promises";
const text = await readFile("notes.txt", "utf8");
console.log(text);
// Run as an ES module; notes.txt must exist.
```

**Explanation:** Node does not contain the browser DOM just because it uses the same engine family as Chrome. One thread normally executes an isolate's JavaScript, while I/O facilities and other threads can do other work. CPU-heavy JavaScript blocks that event loop unless moved or split. Not every async operation uses the thread pool; network I/O and filesystem work have different host mechanisms.

<a id="question-120"></a>

## 120. What is Express.js, and how do route parameters and route handlers work in Express?

[Back to question index](#question-index)

**Interview answer:** Express is a web framework for Node. Routes match a method and path, then run handlers. Route parameters represent named path segments.

```js
app.get("/users/:id", async (req, res) => {
  const user = await repository.findUser(req.params.id);
  if (!user) return res.status(404).json({ error: "User not found" });
  res.json(user);
});
// Express 5; app and repository are provided by your application.
```

**Explanation:** Params are strings, while query parameters and body data come from other inputs. Validate identifiers and authorize access before returning private data. Return after sending an early response to avoid another response attempt. Express 5 forwards rejected returned handler promises; Express 4 needs explicit forwarding or a wrapper.

<a id="question-121"></a>

## 121. What is middleware in Express.js, and how do you set up global error handling middleware (`next(err)`)?

[Back to question index](#question-index)

**Interview answer:** Middleware can inspect or change a request, respond, or pass control with next. Error middleware has four arguments and is registered after routes. Next(error) forwards a failure to it.

```js
app.use(express.json());
app.use((req, res, next) => { console.log(req.method, req.path); next(); });
// Register routes before the error handler.
app.use((error, req, res, next) => {
  if (res.headersSent) return next(error);
  console.error(error);
  res.status(500).json({ error: "Unexpected server error" });
});
```

**Explanation:** If headers were sent, delegate rather than trying to send another response. Do not expose raw stacks to users. Middleware must either finish or advance the request. Detached async work still needs explicit handling even in Express 5. See C10 for a runnable demonstration. [Express error handling](https://expressjs.com/en/5x/guide/error-handling/).

<a id="question-122"></a>

## 122. What is JWT authentication, and how do Access Tokens differ from Refresh Tokens?

[Back to question index](#question-index)

**Interview answer:** A JWT is a structured token carrying claims. A signed JWT protects integrity; its payload is generally readable, not encrypted. An access token permits short-lived API access. A refresh token obtains new access tokens and needs stronger lifecycle controls.

```text
Login -> verify credentials -> issue short-lived access token + refresh token
API -> verify signature, allowed algorithm, issuer, audience, expiry -> authorize
Refresh -> verify stored/session-backed refresh token -> rotate -> new tokens
Logout/reuse detection -> revoke appropriate refresh session
```

**Explanation:** Decoding is not verification, and verification is not authorization. Never store passwords in claims. Use a maintained library, an algorithm allowlist, and correct key management. Refresh tokens need not be JWTs. HttpOnly cookies reduce JavaScript access, but cookie-authenticated flows also need CSRF protections. Storage, expiry, rotation, and revocation depend on the threat model. [JWT best practices](https://datatracker.ietf.org/doc/html/rfc8725).

<a id="question-123"></a>

## 123. What are cluster mode and worker threads in Node.js?

[Back to question index](#question-index)

**Interview answer:** Cluster runs separate Node processes, commonly to handle connections across CPU cores. Worker threads run separate JavaScript execution environments within a process and suit CPU-heavy tasks. Neither shares ordinary JavaScript variables automatically.

```js
import { Worker } from "node:worker_threads";
const worker = new Worker(new URL("./calculate.js", import.meta.url));
worker.on("message", result => console.log(result));
worker.on("error", error => console.error(error));
// calculate.js is your separate worker module.
```

**Explanation:** Threads can use explicit shared buffers or transferred data, but synchronization and communication cost matter. Pools avoid creating a worker for every small task. Cluster processes need shared infrastructure for sessions and limits rather than process-local assumptions. Async I/O usually does not need a worker thread. [Node worker documentation](https://nodejs.org/api/worker_threads.html).

<a id="question-124"></a>

## 124. How do you implement API rate limiting in Node.js?

[Back to question index](#question-index)

**Interview answer:** Rate limiting restricts request volume within a policy. Choose keys such as client IP or authenticated account, choose a window/token algorithm, and return 429 when exceeded.

```js
import { rateLimit } from "express-rate-limit";
app.use("/api", rateLimit({
  windowMs: 60_000,
  limit: 100,
  standardHeaders: "draft-8",
  legacyHeaders: false,
}));
```

**Explanation:** This demonstrates a process-local default store, not a distributed deployment. Multiple instances need a shared store or gateway policy. Configure trusted proxies accurately so an attacker cannot choose an arbitrary IP through headers. Login and expensive endpoints may need stricter separate limits. Decide how limiter-store outages behave. [Rate-limit configuration](https://express-rate-limit.mintlify.app/reference/configuration).

<a id="question-125"></a>

## 125. How do you handle Cross-Origin Resource Sharing (CORS) in Express.js?

[Back to question index](#question-index)

**Interview answer:** CORS lets a server permit browser response access from selected origins. Configure an allowlist and credentials policy; do not use it as authentication.

```js
import cors from "cors";
app.use(cors({
  origin: "https://app.example.com",
  credentials: true,
}));
```

**Explanation:** Place middleware where preflight requests can be handled. Credentialed requests cannot use a wildcard allowed origin. The browser client must also opt into credentials when needed, and cookie policy still applies. CORS does not prevent non-browser clients or every unwanted request; authorization and CSRF handling are separate. `no-cors` is not a fix for needing to read an API response.

<a id="question-126"></a>

## 126. What is NestJS, and how does its architecture (Modules, Controllers, Services) differ from Express?

[Back to question index](#question-index)

**Interview answer:** Nest provides a structured Node application framework. Modules group capabilities, controllers handle requests, and services hold reusable business logic. Dependency injection connects these pieces.

```ts
import { Controller, Get, Injectable, Module } from "@nestjs/common";
@Injectable()
class UsersService { list() { return [{ id: 1 }]; } }
@Controller("users")
class UsersController {
  constructor(private readonly users: UsersService) {}
  @Get() list() { return this.users.list(); }
}
@Module({ controllers: [UsersController], providers: [UsersService] })
export class UsersModule {}
```

**Explanation:** This is TypeScript with the Nest project's decorator setup. Nest commonly uses Express underneath and can use other adapters. Express offers more freedom; Nest adds conventions and testing boundaries. Use services for business rules instead of putting all logic in controllers. More structure helps teams but also adds concepts and boilerplate. [Nest controllers](https://docs.nestjs.com/controllers).

<a id="question-127"></a>

## 127. What is the structural difference between SQL databases (relational, fixed schema) and NoSQL databases like MongoDB (schemaless, document-based)?

[Back to question index](#question-index)

**Interview answer:** Relational databases commonly model rows, tables, relationships, constraints, and joins. MongoDB stores BSON documents with flexible structure. “Flexible” does not mean no schema or no transactions, and SQL schemas can evolve too.

```text
Relational:
users(id, name)
orders(id, user_id, total)

Document:
{ _id: ..., userId: ..., items: [...], total: ... }
```

**Explanation:** Choose based on access patterns, relationships, consistency, indexes, and operational needs. MongoDB supports validation and multi-document transactions; relational databases can support JSON. Neither family is universally faster. Normalize or embed deliberately instead of deciding solely from the label SQL/NoSQL.

<a id="question-128"></a>

## 128. How do you handle data consistency, reference modeling, and schema migrations in MongoDB?

[Back to question index](#question-index)

**Interview answer:** Embed related data when it is read and updated together and stays bounded. Reference when entities have independent lifecycles or large/shared relationships. Add validators and indexes, and evolve stored document versions deliberately.

```js
// Example document with explicit versioning:
const order = { schemaVersion: 2, customerId: "customer-1", items: [], status: "open" };
```

**Explanation:** A single-document update is atomic. Cross-document rules may need transactions, conditional writes, or application coordination. References do not automatically provide relational foreign-key enforcement. Use repeatable migration scripts, staged rollout compatibility, backups, and verification. Avoid unbounded embedded arrays and assume old documents can coexist during deployment.

<a id="question-129"></a>

## 129. How do you execute database transactions in MongoDB?

[Back to question index](#question-index)

**Interview answer:** Use a session and transaction when related operations across documents must commit together. Pass the session to every participating operation and always end it. A suitable replica-set or sharded deployment is required.

```js
const session = client.startSession();
try {
  await session.withTransaction(async () => {
    await orders.insertOne({ status: "created" }, { session });
    await audit.insertOne({ event: "order-created" }, { session });
  });
} finally {
  await session.endSession();
}
// client is a connected MongoClient; orders/audit are collection handles.
```

**Explanation:** The transaction helper can retry certain failures, so its callback must not perform irreversible external side effects such as sending an email. Keep operations sequential within the transaction; driver parallel operations there are unsupported. Prefer good document design when single-document atomicity is enough. See C11 for a guarded transfer example. [MongoDB driver transactions](https://www.mongodb.com/docs/drivers/node/current/crud/transactions/).

<a id="question-130"></a>

## 130. What is Apache Kafka, and how is it used in event-driven microservices messaging?

[Back to question index](#question-index)

**Interview answer:** Kafka is a distributed event-streaming platform. Producers append records to partitioned topics; consumer groups process records and track offsets. It supports retained events and replay.

```json
{
  "eventId": "event-123",
  "type": "OrderCreated",
  "orderId": "order-456",
  "schemaVersion": 1
}
```

**Explanation:** Ordering is within a partition, not automatically across a whole topic. An order ID can be a partition key when per-order ordering matters. Plan retries, duplicate handling, schema evolution, and consumer lag monitoring. Kafka's transactional features do not automatically make external database side effects exactly-once. An outbox helps coordinate database writes with event publishing. [Kafka introduction](https://kafka.apache.org/intro/).

<a id="question-131"></a>

## 131. What is Docker, and how are containers used to package and deploy web applications?

[Back to question index](#question-index)

**Interview answer:** Docker packages an application and its runtime dependencies into an image. Containers run instances of that image with isolation and share the host kernel through the container platform, rather than each containing a full guest OS.

```dockerfile
# Example only: choose a supported version and pin an approved image digest.
FROM node:24-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
COPY --chown=node:node . .
USER node
CMD ["node", "server.js"]
```

**Explanation:** This assumes a plain Node app with a committed lockfile and no build step. A compiled app needs a build stage first. Use .dockerignore to exclude node_modules, secrets, and local files. Inject secrets at runtime, plan health checks and shutdown, and use volumes/external stores for persistent data. Images need vulnerability management. [Docker overview](https://docs.docker.com/get-started/docker-overview/).

<a id="question-132"></a>

## 132. What are microservices, and how do services communicate (REST vs gRPC vs Message Queues)?

[Back to question index](#question-index)

**Interview answer:** Microservices split a system into independently deployable capabilities with clear ownership. REST suits interoperable request-response APIs; gRPC adds typed contracts and efficient RPC; messaging suits asynchronous events and decoupled processing.

```text
Client -> Orders API -> Orders database
                    -> Outbox -> Event broker -> Notifications service
```

**Explanation:** Service boundaries add network failure, tracing, deployment, and consistency costs. Use timeouts, bounded retries, idempotency, and explicit ownership. A database transaction should not be assumed to span independent services; sagas or compensation may be needed. A modular monolith is often a better starting point until independent scaling or team boundaries justify separation.

# Worked Coding Tasks

These are additional practice tasks chosen to reinforce the pasted questions, not claimed verbatim video excerpts. C1–C6 and C12 are standalone JavaScript. C7–C9 are React examples. C10 requires Express. C11 requires a connected MongoDB deployment that supports transactions.

<a id="coding-c1"></a>

## C1. Implement arbitrary-length currying

[Back to question index](#question-index)

**What to say:** “I will use an empty call as the stopping signal. Each call captures a total and returns the next function. I will allow zero and reject invalid numeric input.”

```js
function sumCurry(total = 0) {
  if (!Number.isFinite(total)) throw new TypeError("Expected a finite number");
  return function next(value) {
    if (arguments.length === 0) return total;
    if (!Number.isFinite(value)) throw new TypeError("Expected a finite number");
    return sumCurry(total + value);
  };
}
console.log(sumCurry(1)(2)(0)(3)()); // 6
console.log(sumCurry()()); // 0
```

**Step-by-step:**

1. The initial call sets total to one.
2. Calling the returned function with two creates another closure with total three.
3. Zero is accepted because finishing depends on argument count, not truthiness.
4. Three produces total six, and the empty call returns it.

**Edge cases and complexity:** Explicit undefined is rejected as a chained value. Non-finite input or an overflowed accumulated total is rejected. For k calls, work and total function allocations are O(k). In ordinary single-chain use, previous closures need not remain retained; keeping every intermediate function retains O(k) closure storage. There is no k-deep recursive call stack because each call returns before the next chained call starts.

<a id="coding-c2"></a>

## C2. Implement a simplified map

[Back to question index](#question-index)

**What to say:** “I will capture the starting length, create an equally sized result, and call the callback only for present indices. This preserves holes.”

```js
function mapArray(array, callback, thisArg) {
  if (!Array.isArray(array)) throw new TypeError("Expected an array");
  if (typeof callback !== "function") throw new TypeError("Expected a callback");
  const length = array.length;
  const result = new Array(length);
  for (let index = 0; index < length; index++) {
    if (index in array) {
      result[index] = callback.call(thisArg, array[index], index, array);
    }
  }
  return result;
}
console.log(JSON.stringify(mapArray([1, 2, 3], n => n * 2))); // [2,4,6]
```

**Step-by-step:** Length is captured before callbacks can change the source. The `in` check skips holes while including an inherited indexed property, like native map. Call supplies the requested receiver and the callback's value/index/source arguments. Each returned value is stored at its matching index.

**Edge cases and complexity:** Empty input returns an empty array; a callback error propagates. Appended entries beyond starting length are not visited. O(n) time plus callback work, O(n) output space. This helper does not implement generic array-like receivers or subclass species rules, so it is not a full polyfill.

<a id="coding-c3"></a>

## C3. Group records by a key

[Back to question index](#question-index)

**What to say:** “I will make one pass and use a Map from group keys to arrays. This preserves key types and avoids ordinary object-key collisions.”

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
const grouped = groupBy([
  { name: "Sam", team: "web" },
  { name: "Alex", team: "api" },
  { name: "Lee", team: "web" },
], user => user.team);
console.log(grouped.get("web").map(user => user.name).join(",")); // Sam,Lee
```

**Step-by-step:** The first web entry creates a bucket. Api creates another bucket. The final web entry reuses the first bucket. Inputs are not mutated, but output groups hold the same record references.

**Edge cases and complexity:** Empty input gives an empty map. Missing keys group under undefined unless you choose to reject them. Typical expected O(n) time and O(n) storage; keyFn cost must be included. Ask whether the caller needs a Map or a JSON-compatible object.

<a id="coding-c4"></a>

## C4. Flatten nested arrays without flat

[Back to question index](#question-index)

**What to say:** “For finite acyclic arrays, I will visit each nested array and append its non-array values in order. I will skip holes and preserve actual undefined entries.”

```js
function flattenNested(input) {
  const output = [];
  function visit(array) {
    for (let index = 0; index < array.length; index++) {
      if (!(index in array)) continue;
      const value = array[index];
      if (Array.isArray(value)) visit(value);
      else output.push(value);
    }
  }
  visit(input);
  return output;
}
console.log(JSON.stringify(flattenNested([1, [2, [3]], 4]))); // [1,2,3,4]
```

**Step-by-step:** One is appended. The nested array is entered, two is appended, and its child produces three. Once nested calls return, four is appended. One output array avoids repeatedly copying increasingly large results.

**Edge cases and complexity:** Empty arrays add nothing; repeated primitive values remain repeated. The contract excludes cycles and excessive depth. O(n) visited-index work, O(m) output storage for m flattened values, and O(d) stack space for depth d. An explicit stack handles deep inputs; active-path cycle detection can reject cycles without rejecting harmless repeated subarrays.

<a id="coding-c5"></a>

## C5. Two Sum

[Back to question index](#question-index)

**What to say:** “For each number I will look for its complement among earlier numbers. Checking before storing prevents reusing one index.”

```js
function twoSum(numbers, target) {
  const seen = new Map();
  for (let index = 0; index < numbers.length; index++) {
    const needed = target - numbers[index];
    if (seen.has(needed)) return [seen.get(needed), index];
    seen.set(numbers[index], index);
  }
  return [];
}
console.log(JSON.stringify(twoSum([2, 7, 11, 15], 9))); // [0,1]
console.log(JSON.stringify(twoSum([3, 3], 6))); // [0,1]
```

**Step-by-step:** At two, seven is absent, so store two at zero. At seven, two is already stored, so return zero and one. With duplicates, the previous three is found before storing the current three.

**Edge cases and complexity:** This returns one pair of indices and an empty array for none. Assume finite numbers with suitable equality behavior, commonly integers in interview tasks. Typical expected O(n) time and O(n) space. Floating-point totals may need a different domain policy; do not silently introduce approximate matching.

<a id="coding-c6"></a>

## C6. Longest substring without repeats

[Back to question index](#question-index)

**What to say:** “I will maintain a window with no duplicates and remember each character's last position. I only move the left boundary forward.”

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
console.log(longestUniqueLength("abcabcbb")); // 3
console.log(longestUniqueLength("abba")); // 2
```

**Step-by-step:** For abba, the first two characters form a length-two window. The second b moves left past the previous b. The final a's previous occurrence is outside the current window, so Math.max prevents moving left backward.

**Edge cases and complexity:** Empty text returns zero. Typical O(n) time and O(k) storage for k distinct code points. For-of counts Unicode code points here, not user-perceived graphemes. Define that requirement before handling emoji sequences. To return the actual substring, track best start/end using an indexing representation that matches your character definition.

<a id="coding-c7"></a>

## C7. React data loading with cancellation and stale-result protection

[Back to question index](#question-index)

**What to say:** “I will start a request when the user ID changes. Cleanup aborts the request and marks that effect inactive. I will prevent old responses from updating the newer screen.”

```jsx
import { useEffect, useState } from "react";

export function UserProfile({ userId }) {
  const [state, setState] = useState({ id: null, status: "idle" });
  useEffect(() => {
    const controller = new AbortController();
    let active = true;
    setState({ id: userId, status: "loading" });

    async function load() {
      try {
        const response = await fetch(`/api/users/${encodeURIComponent(userId)}`, {
          signal: controller.signal,
        });
        if (!response.ok) throw new Error(`HTTP ${response.status}`);
        const data = await response.json();
        if (!data || typeof data.name !== "string") {
          throw new Error("Invalid user response");
        }
        if (active) setState({ id: userId, status: "success", data });
      } catch (error) {
        if (active && !controller.signal.aborted) {
          setState({ id: userId, status: "error", error: error.message });
        }
      }
    }
    load();
    return () => { active = false; controller.abort(); };
  }, [userId]);

  if (state.id !== userId || state.status === "idle" || state.status === "loading") {
    return <p role="status">Loading profile...</p>;
  }
  if (state.status === "error") return <p role="alert">{state.error}</p>;
  return <h1>{state.data.name}</h1>;
}
```

**Step-by-step:** Each effect has its own controller and active flag. HTTP status is checked before parsing. Minimal response validation prevents blindly rendering a wrong shape. Cleanup deactivates the old effect before later async results are applied. Tagging state with its requested ID also avoids displaying the previous user's result during the render before the new effect runs.

**Limits:** UserId is assumed to be a valid supplied identifier. Authentication, full validation, caching, retry controls, and missing-user UX belong to the application. Framework loaders or query libraries can handle these concerns better for larger systems. Abort does not undo work already performed by the server.

<a id="coding-c8"></a>

## C8. A reusable debounced value hook

[Back to question index](#question-index)

**What to say:** “I will return a value that updates only after input stays unchanged for the delay. Cleanup cancels the previous timer.”

```jsx
import { useEffect, useState } from "react";
export function useDebouncedValue(value, delay = 300) {
  const [debounced, setDebounced] = useState(value);
  useEffect(() => {
    const timer = setTimeout(() => setDebounced(value), delay);
    return () => clearTimeout(timer);
  }, [value, delay]);
  return debounced;
}
```

**Step-by-step:** State begins with the supplied value. Changing it schedules a timer. Another change first cleans up the old timer and then creates a new one. Only the latest uninterrupted timer updates state. Removing the component also clears it.

**Limits:** The initial value is available immediately; later changes are delayed. Validate delay at a boundary if it is untrusted. Debounce reduces request frequency but does not solve response-order races; combine with C7's protection. Object inputs use identity, so creating a fresh object each render can keep restarting the timer.

<a id="coding-c9"></a>

## C9. A controlled form with async submission

[Back to question index](#question-index)

**What to say:** “State owns the input. Submission validates, shows a pending state, checks HTTP status, and presents errors. The server repeats validation and enforces its own duplicate-write protection.”

```jsx
import { useRef, useState } from "react";
export function ContactForm() {
  const [email, setEmail] = useState("");
  const [status, setStatus] = useState("idle");
  const [error, setError] = useState("");
  const submitting = useRef(false);

  async function submit(event) {
    event.preventDefault();
    if (submitting.current) return;
    const normalized = email.trim();
    if (!normalized) { setError("Email is required"); return; }
    submitting.current = true;
    setStatus("saving");
    setError("");
    try {
      const response = await fetch("/api/contacts", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ email: normalized }),
      });
      if (!response.ok) throw new Error(`Unable to save: HTTP ${response.status}`);
      setStatus("saved");
    } catch (failure) {
      setError(failure.message);
      setStatus("error");
    } finally {
      submitting.current = false;
    }
  }

  return <form onSubmit={submit}>
    <label htmlFor="contact-email">Email</label>
    <input id="contact-email" name="email" type="email" required
      value={email} disabled={status === "saving"}
      onChange={event => { setEmail(event.target.value); setStatus("idle"); setError(""); }} />
    <button disabled={status === "saving"} type="submit">Save</button>
    {status === "saving" && <p role="status">Saving...</p>}
    {status === "saved" && <p role="status">Saved</p>}
    {error && <p role="alert">{error}</p>}
  </form>;
}
```

**Step-by-step:** PreventDefault avoids navigation. The ref guards duplicate handler entry immediately, while state drives the UI. Native required/email validation handles ordinary form submission and the server must still validate. A failed HTTP status becomes a caught error. Finally releases the guard regardless of outcome.

**Limits:** This does not guarantee server-side idempotency. A production flow may need a request timeout, unmount cleanup, stronger accessible error association, and appropriate cookie/CSRF handling. Canceling a write does not prove that the server did not save it.

<a id="coding-c10"></a>

## C10. Express validation and a central error boundary

[Back to question index](#question-index)

**What to say:** “I will validate input before business work, send consistent JSON responses, and handle unexpected errors centrally. This example targets Express 5.”

```js
// Save as server.mjs in a project with Express 5 installed.
import express from "express";
const app = express();
app.use(express.json({ limit: "10kb" }));

app.get("/health", (req, res) => res.json({ status: "ok" }));
app.post("/sum", async (req, res) => {
  const { a, b } = req.body ?? {};
  if (!Number.isFinite(a) || !Number.isFinite(b)) {
    return res.status(400).json({ error: "a and b must be finite numbers" });
  }
  const result = a + b;
  if (!Number.isFinite(result)) {
    return res.status(400).json({ error: "Result is outside the allowed range" });
  }
  res.json({ result });
});
app.use((req, res) => res.status(404).json({ error: "Route not found" }));
app.use((error, req, res, next) => {
  if (res.headersSent) return next(error);
  if (error.type === "entity.parse.failed") {
    return res.status(400).json({ error: "Invalid JSON" });
  }
  if (error.type === "entity.too.large") {
    return res.status(413).json({ error: "Request body is too large" });
  }
  console.error(error);
  res.status(500).json({ error: "Unexpected server error" });
});
app.listen(3000, () => console.log("Listening on port 3000"));
```

**Example:** POST `/sum` with `{"a":2,"b":3}` returns `{"result":5}`. Sending `{"a":"2","b":3}` returns 400; numeric strings are intentionally rejected instead of coerced.

**Step-by-step:** JSON parsing runs first. Finite-number checks reject wrong types, NaN, and infinities. Invalid input returns early. Unknown routes get a separate 404 response. Four-argument middleware handles parsing and unexpected errors. In Express 4, rejected async operations require an explicit wrapper or next(error).

**Limits:** This small API demonstrates mechanics, not a full service. Add authentication, rate limits, logs, observability, shutdown, and tests according to the requirements. Do not install packages merely to read this guide.

<a id="coding-c11"></a>

## C11. A guarded MongoDB transfer transaction

[Back to question index](#question-index)

**What to say:** “I will validate the amount, debit only if funds are sufficient, and credit the destination in one transaction. Any failed condition aborts both updates.”

```js
async function transfer(client, accounts, fromId, toId, amount) {
  if (fromId === toId) throw new Error("Choose different accounts");
  if (!Number.isSafeInteger(amount) || amount <= 0) {
    throw new Error("Amount must be a positive safe integer in minor units");
  }
  const session = client.startSession();
  try {
    return await session.withTransaction(async () => {
      const debit = await accounts.updateOne(
        { _id: fromId, balance: { $gte: amount } },
        { $inc: { balance: -amount } },
        { session },
      );
      if (debit.matchedCount !== 1) throw new Error("Missing account or insufficient funds");
      const credit = await accounts.updateOne(
        { _id: toId },
        { $inc: { balance: amount } },
        { session },
      );
      if (credit.matchedCount !== 1) throw new Error("Destination account missing");
      return { transferred: amount };
    });
  } finally {
    await session.endSession();
  }
}
```

**Step-by-step:** The conditional debit checks funds within the write, rather than a separate unprotected read. Both writes receive the same session. A missing destination throws, so the debit does not commit by itself. The helper coordinates commit and certain retries; finally ends the session even after a failure.

**Assumptions:** IDs are canonical strings, balances are validated numeric minor-unit values kept inside safe limits, and the deployment supports transactions. ObjectId equality needs value comparison rather than the string-ID check shown here. A real financial design needs exact types/ranges, authorization, an immutable ledger, and idempotency for retries of the overall request. The transaction alone does not supply those guarantees.

<a id="coding-c12"></a>

## C12. Memoize a pure one-argument function

[Back to question index](#question-index)

**What to say:** “I will use a closure to keep a Map cache private. A cache hit returns the previous result without recomputing it.”

```js
function memoizeOne(fn) {
  const cache = new Map();
  return function (input) {
    if (cache.has(input)) return cache.get(input);
    const result = fn(input);
    cache.set(input, result);
    return result;
  };
}
let calls = 0;
const square = memoizeOne(n => { calls++; return n * n; });
console.log(square(4), square(4), calls); // 16 16 1
```

**Step-by-step:** The first call misses and computes sixteen. The second finds the key and returns sixteen without invoking fn. Has distinguishes a stored undefined result from an absent key. The cache remains private but reachable through the returned closure.

**Limits and complexity:** This contract expects one argument and no this-dependent result. Object keys use identity; mutating a key object can make cached output stale. Expected lookup cost is typically O(1), while storage grows with distinct inputs. Production caches may need size limits, expiry, or eviction. Caching promises also needs a policy for rejected results.

# Interview Answer Strategy

Use four parts: **definition, example, practical use, limitation**. Speak naturally rather than reading a paragraph word for word.

Example: “A closure lets a function keep access to its surrounding variables. In a debounced search handler, I keep the timer private through a closure. A new keystroke cancels that timer and starts another. I also guard the API response order because debounce alone does not prevent an old response from replacing newer results.”

For coding rounds:

1. Clarify input, output, duplicates, missing results, and allowed operations.
2. Explain a simple solution and why you can improve it.
3. Write the code in small steps and name intermediate values clearly.
4. Walk through one normal and one difficult input.
5. Explain time and memory costs, including callbacks and copying.
6. Name one production concern without pretending the demo handles everything.

# Preparation Checklist for 4–5 Years of Experience

- Explain scope, closure, coercion, this, and promise ordering without guessing.
- Write the standalone coding tasks and test empty and duplicate inputs.
- Build a React form and an API screen with loading, errors, cancellation, and cleanup.
- Explain keys, state ownership, dependencies, and render versus commit.
- Use semantic HTML, labels, keyboard access, visible focus, and responsive layouts.
- Explain input validation, authorization, retries, rate limiting, and error handling.
- Discuss database indexes, query patterns, transactions, and data ownership.
- Prepare real project stories for debugging, performance, testing, and tradeoffs.

Your list is broad, but interviews may also include TypeScript, testing, accessibility, network caching, browser security, SQL queries, and system design. Prepare those according to the target role. No question collection guarantees success in every interview.

# Companion Guides

- `javascript.md`: deeper JavaScript concepts and additional topics.
- `console-based-questions.md`: 65 output questions with detailed conversion and execution explanations.

# Verification

- Confirmed that all 132 question headings match the attachment verbatim and retain its order.
- Checked all 77 JavaScript code blocks for syntax using Node's ES module parser; no syntax failures.
- Ran assertions for C1–C6 and C12, including empty inputs, duplicate values, sparse arrays, callback receivers, invalid curry inputs, cached undefined results, and Unicode code-point handling. All passed.
- Checked Markdown code-fence balance.
- React JSX, DOM behavior, Express endpoints, Nest TypeScript, Docker, and MongoDB transactions were not integration-tested. They require the relevant application setup or services. Syntax validation of an illustrative JavaScript block does not establish that its external dependencies or runtime behavior work.
