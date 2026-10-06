# JavaScript Console Output Questions

Predict the output first. Then read the answer and explain the reason aloud. These questions focus on type conversion and string joining, with scope, objects, arrays, functions, and async questions for interviews at 4–5 years of experience.

**How to run:** Run each question separately. The examples use strict mode, and the async examples assume a normal JavaScript environment with timers. Outputs show the text printed by `console.log`, without a browser console's extra styling. Arrays and objects are usually printed with `JSON.stringify()` so their display is predictable. A caught error prints its name because exact error messages can differ between engines.

`+` does not always add numbers. First, JavaScript converts operands to primitive values. If either resulting primitive is a string, it joins strings. Otherwise, it performs numeric addition. Other operators have their own conversion rules.

## 1. Number followed by a string

**Question:** What is the output?

```js
"use strict";
console.log(10 + "20");
console.log(typeof (10 + "20"));
```

**Output:**

```text
1020
string
```

**Detailed reason:** One operand is a string, so `+` performs string concatenation. The number `10` becomes `"10"`, and JavaScript joins `"10"` and `"20"`. The result is a string, even though the text contains only digits. This is why adding values from form inputs can give the wrong total.

## 2. Addition runs from left to right

```js
"use strict";
console.log(1 + 2 + "3");
console.log("1" + 2 + 3);
```

**Output:**

```text
33
123
```

**Detailed reason:** These `+` operations are grouped left to right. In the first expression, `1 + 2` produces the number `3`, then `3 + "3"` produces `"33"`. In the second expression, `"1" + 2` produces `"12"`, then `"12" + 3` produces `"123"`. Once the intermediate result is a string, later additions in this example also join strings.

## 3. Parentheses change the order

```js
"use strict";
console.log("Result: " + 2 + 3);
console.log("Result: " + (2 + 3));
```

**Output:**

```text
Result: 23
Result: 5
```

**Detailed reason:** The first line joins `2` to the label and then joins `3`. The second line computes the parenthesized numeric addition first, producing `5`. It then joins that result to the label. Use parentheses or a separate numeric calculation when building messages.

## 4. Subtraction behaves differently from addition

```js
"use strict";
console.log("10" - 3);
console.log("10" * "2");
console.log("10" / "2");
console.log("10" + 3);
```

**Output:**

```text
7
20
5
103
```

**Detailed reason:** Subtraction, multiplication, and division perform numeric operations here, so numeric strings become numbers. `+` supports both numeric addition and string concatenation. With a string operand, it chooses concatenation. Do not assume all arithmetic-looking operators handle strings the same way.

## 5. A string result can become a number again

```js
"use strict";
console.log("5" + 2 - 1);
console.log("5" - 2 + "1");
```

**Output:**

```text
51
31
```

**Detailed reason:** First, `"5" + 2` produces the string `"52"`. Subtraction then converts it to `52` and produces the number `51`. In the second line, subtraction produces the number `3`, then addition with `"1"` produces the string `"31"`. The two printed values look numeric, but their types are different.

## 6. Unary plus converts a value to a number

```js
"use strict";
console.log(+"42");
console.log(+"");
console.log(+"   ");
console.log(+"hello");
console.log(+true);
```

**Output:**

```text
42
0
0
NaN
1
```

**Detailed reason:** Unary `+` requests numeric conversion. A valid numeric string becomes a number. Empty and whitespace-only strings become zero. A non-numeric string becomes `NaN`, and `true` becomes `1`. This is useful but can incorrectly treat empty input as zero if you do not validate the input first.

## 7. Booleans in addition

```js
"use strict";
console.log(true + true);
console.log(true + false);
console.log("true" + false);
console.log(false + "0");
```

**Output:**

```text
2
1
truefalse
false0
```

**Detailed reason:** Without a string operand, numeric addition converts `true` to `1` and `false` to `0`. With a string operand, concatenation converts the Boolean to its text form, `"true"` or `"false"`. The word `"true"` is a string, not a Boolean value.

## 8. `null` and `undefined` in arithmetic

```js
"use strict";
console.log(null + 1);
console.log(undefined + 1);
console.log("value:" + null);
console.log("value:" + undefined);
```

**Output:**

```text
1
NaN
value:null
value:undefined
```

**Detailed reason:** Numeric conversion changes `null` to zero, but changes `undefined` to `NaN`. Adding a number to `NaN` still gives `NaN`. With a string operand, these values become the text `"null"` and `"undefined"`. Their numeric and string conversions are different operations.

## 9. Explicit conversion of missing values

```js
"use strict";
console.log(Number(null));
console.log(Number(undefined));
console.log(String(null));
console.log(String(undefined));
console.log(Boolean(null), Boolean(undefined));
```

**Output:**

```text
0
NaN
null
undefined
false false
```

**Detailed reason:** `Number`, `String`, and `Boolean` ask for different conversions. Neither `null` nor `undefined` is truthy, so both become `false` in Boolean conversion. The string output lines are strings containing those words; they are not the original primitive values. Always identify which conversion an operator requests.

## 10. Empty arrays in addition

```js
"use strict";
console.log(JSON.stringify([] + []));
console.log([] + 1);
console.log([1] + 2);
console.log([1, 2] + 3);
```

**Output:**

```text
""
1
12
1,23
```

**Detailed reason:** Arrays are objects. In these expressions, their primitive conversion produces strings: `[]` becomes `""`, `[1]` becomes `"1"`, and `[1, 2]` becomes `"1,2"`. `+` then concatenates. Even `[] + 1` returns the string `"1"`, not the number `1`. JSON quoting makes the empty string visible.

## 11. Arrays in numeric conversion

```js
"use strict";
console.log(Number([]));
console.log(Number([5]));
console.log(Number([1, 2]));
console.log(Number([null]));
```

**Output:**

```text
0
5
NaN
0
```

**Detailed reason:** The arrays first become strings. Their strings are `""`, `"5"`, `"1,2"`, and `""`. Empty strings become zero; `"5"` becomes five; `"1,2"` is not a valid number. Array string conversion treats `null` and `undefined` elements as empty entries. These are conversion rules, not a recommendation to use arrays as numbers.

## 12. Objects in addition

```js
"use strict";
console.log(({}) + ({}));
console.log([] + ({}));
console.log(({}) + []);
```

**Output:**

```text
[object Object][object Object]
[object Object]
[object Object]
```

**Detailed reason:** An ordinary object's default primitive conversion for these operations produces `"[object Object]"`. An empty array produces `""`. The strings are then joined. Parentheses make `{}` clearly an object expression. A bare `{} + []` typed into a console can be parsed differently because `{}` may be treated as an empty block. Do not memorize a console result without checking the parsing context.

## 13. Custom object conversion

```js
"use strict";
const amount = {
  valueOf() { return 10; },
  toString() { return "ten"; },
};
console.log(amount + 5);
console.log(String(amount));
console.log(`${amount}`);
```

**Output:**

```text
15
ten
ten
```

**Detailed reason:** For this ordinary object, addition's default primitive conversion tries `valueOf()` first. It returns the primitive number `10`, so addition gives `15`. Explicit string conversion and a template literal request a string-oriented conversion, which tries `toString()` first. It returns `"ten"`. Objects can therefore behave differently depending on the conversion hint.

## 14. `Symbol.toPrimitive` receives a hint

```js
"use strict";
const value = {
  [Symbol.toPrimitive](hint) {
    return hint === "number" ? 10 : "item";
  },
};
console.log(value + 1);
console.log(value - 1);
console.log(String(value));
```

**Output:**

```text
item1
9
item
```

**Detailed reason:** Addition requests the `"default"` hint here, so the method returns `"item"` and concatenation gives `"item1"`. Subtraction requests `"number"`, receives `10`, and gives `9`. `String()` requests `"string"`, so it receives `"item"`. A custom conversion method must return a primitive; returning an object causes a TypeError.

## 15. Loose equality versus strict equality

```js
"use strict";
console.log(0 == false);
console.log(0 === false);
console.log("5" == 5);
console.log("5" === 5);
```

**Output:**

```text
true
false
true
false
```

**Detailed reason:** Loose equality applies its conversion rules: `false` becomes zero, and the string `"5"` becomes the number five when compared with a number. Strict equality does not perform those conversions, so different types are unequal. Prefer strict equality for ordinary application comparisons.

## 16. Missing values have a special equality rule

```js
"use strict";
console.log(null == undefined);
console.log(null === undefined);
console.log(null == 0);
console.log(undefined == 0);
```

**Output:**

```text
true
false
false
false
```

**Detailed reason:** Loose equality has a special rule that makes `null` and `undefined` equal to each other. It does not generally convert `null` to zero for equality with a number. Numeric arithmetic does convert `null` to zero, but equality follows different rules. This is a common reason that guessing from arithmetic results fails.

## 17. The surprising `null` comparison

```js
"use strict";
console.log(null > 0);
console.log(null == 0);
console.log(null >= 0);
```

**Output:**

```text
false
false
true
```

**Detailed reason:** Relational comparisons with zero numerically convert `null` to zero. Zero is not greater than zero, but is greater than or equal to zero. Loose equality uses a separate algorithm and does not treat `null` as equal to zero. Do not explain `>=` as simply “`>` or `==`”; that is not how its conversion rules work.

## 18. `undefined` comparisons

```js
"use strict";
console.log(undefined > 0);
console.log(undefined < 0);
console.log(undefined >= 0);
console.log(undefined == null);
```

**Output:**

```text
false
false
false
true
```

**Detailed reason:** Numeric conversion of `undefined` gives `NaN`. Relational comparisons involving `NaN` do not establish either greater-than or less-than ordering, and these operators return false. Equality with `null` is true because of the special loose-equality rule, not because they become the same number.

## 19. An empty array is truthy but loosely equals false

```js
"use strict";
console.log(Boolean([]));
console.log([] == false);
console.log([] === false);
```

**Output:**

```text
true
true
false
```

**Detailed reason:** Boolean conversion treats an ordinary array object as truthy, regardless of its length. Loose equality does not simply call `Boolean()` on both sides. It converts `false` to zero and the array to an empty string, which then converts to zero. Strict equality rejects the different types. Truthiness and loose equality are different checks.

## 20. Why does `[] == ![]` return true?

```js
"use strict";
console.log(![]);
console.log([] == ![]);
```

**Output:**

```text
false
true
```

**Detailed reason:** `![]` runs first. An array is truthy, so negating it produces `false`. The remaining comparison is `[] == false`, which follows the conversions explained in question 19 and becomes a comparison of zero with zero. This example is useful for understanding rules, but code like this should be avoided in real applications.

## 21. Whitespace and loose equality

```js
"use strict";
console.log("" == 0);
console.log("   " == 0);
console.log("0" == false);
console.log("false" == false);
```

**Output:**

```text
true
true
true
false
```

**Detailed reason:** Empty and whitespace-only strings numerically convert to zero. When a Boolean participates in loose equality, it converts to a number. `"0"` can then become zero and match `false` converted to zero. The string `"false"` becomes `NaN` under numeric conversion, so it does not match. Text that spells a Boolean is not automatically parsed as a Boolean.

## 22. String ordering versus numeric ordering

```js
"use strict";
console.log("10" < "2");
console.log("10" < 2);
console.log("2" > "12");
console.log(Number("2") > Number("12"));
```

**Output:**

```text
true
false
true
false
```

**Detailed reason:** When both compared primitives are strings, JavaScript compares their UTF-16 code units in order. The first character `"1"` comes before `"2"`, so `"10" < "2"`. With a numeric operand, `"10"` converts to ten and ten is not less than two. Convert validated input explicitly when the business rule requires numeric ordering.

## 23. Chained comparisons are not mathematical chains

```js
"use strict";
console.log(1 < 2 < 3);
console.log(3 > 2 > 1);
```

**Output:**

```text
true
false
```

**Detailed reason:** The first line becomes `true < 3`, then `1 < 3`, so it is true. The second becomes `true > 1`, then `1 > 1`, so it is false. JavaScript does not treat these as “all adjacent comparisons must pass.” Write `a < b && b < c` to express that rule clearly.

## 24. `NaN` is not equal to itself

```js
"use strict";
console.log(NaN === NaN);
console.log(NaN == NaN);
console.log(Number.isNaN(NaN));
console.log(Object.is(NaN, NaN));
console.log(typeof NaN);
```

**Output:**

```text
false
false
true
true
number
```

**Detailed reason:** `NaN` is a special value of the number type representing an invalid numeric result. Both ordinary equality operators treat it as unequal to everything, including itself. `Number.isNaN()` checks specifically for this value. `Object.is()` uses different equality rules and recognizes two `NaN` values as the same.

## 25. `isNaN()` versus `Number.isNaN()`

```js
"use strict";
console.log(isNaN("hello"));
console.log(Number.isNaN("hello"));
console.log(isNaN(""));
console.log(Number.isNaN(Number("hello")));
```

**Output:**

```text
true
false
false
true
```

**Detailed reason:** Global `isNaN()` first tries numeric conversion. `"hello"` converts to `NaN`, so the result is true; an empty string converts to zero, so the result is false. `Number.isNaN()` performs no conversion and only returns true for the actual numeric `NaN` value. Choose the check based on whether you mean “is already NaN” or “fails numeric conversion.”

## 26. Truthy strings and falsy values

```js
"use strict";
console.log(Boolean("false"));
console.log(Boolean("0"));
console.log(Boolean(""));
console.log(Boolean({}));
console.log(Boolean(0n));
```

**Output:**

```text
true
true
false
true
false
```

**Detailed reason:** Every non-empty string is truthy, regardless of what its text says. The empty string is falsy. Ordinary objects are truthy even when they have no properties. The BigInt zero `0n` is falsy. Do not use `Boolean("false")` to parse a text setting; compare the string against the allowed values explicitly.

## 27. Logical operators return values

```js
"use strict";
console.log("hello" && 42);
console.log(0 && "hello");
console.log("" || "fallback");
console.log("ready" || "fallback");
```

**Output:**

```text
42
0
fallback
ready
```

**Detailed reason:** `&&` returns the first falsy operand, or the last operand if none is falsy. `||` returns the first truthy operand, or the last operand if none is truthy. They use truthiness to decide whether to continue, but they do not necessarily return a Boolean. This is why they can be used to select values.

## 28. `||` versus `??`

```js
"use strict";
console.log(0 || 10);
console.log(0 ?? 10);
console.log(false ?? true);
console.log(JSON.stringify("" ?? "default"));
console.log(null ?? "default");
```

**Output:**

```text
10
0
false
""
default
```

**Detailed reason:** `||` replaces any falsy left operand. `??` replaces only `null` or `undefined`. Zero, false, and an empty string can be legitimate values, so `??` keeps them. Use `??` when “missing” is the rule, and `||` only when all falsy values should trigger the fallback.

## 29. Short-circuiting skips function calls

```js
"use strict";
function work() {
  console.log("work ran");
  return 7;
}
console.log(false && work());
console.log(true || work());
console.log(null ?? work());
```

**Output:**

```text
false
true
work ran
7
```

**Detailed reason:** The first expression stops at false, so `work()` is not called. The second stops at true. The third needs a fallback because its left operand is null, so it calls `work()`. That function logs before returning seven, then the outer `console.log()` prints seven. Operator evaluation affects side effects as well as values.

## 30. Default parameters only replace `undefined`

```js
"use strict";
function show(value = "default") { console.log(value); }
show();
show(undefined);
show(null);
show(0);
```

**Output:**

```text
default
default
null
0
```

**Detailed reason:** An omitted argument becomes `undefined`, which activates the default. Explicit `undefined` also activates it. `null` and zero are supplied values, so they are preserved. Destructuring defaults use the same missing-value rule. If null should also mean missing, use a separate nullish check.

## 31. `parseInt()` versus `Number()`

```js
"use strict";
console.log(parseInt("12px", 10));
console.log(Number("12px"));
console.log(parseInt("3.9", 10));
console.log(Number("3.9"));
console.log(parseInt("", 10), Number(""));
```

**Output:**

```text
12
NaN
3
3.9
NaN 0
```

**Detailed reason:** `parseInt()` reads an integer prefix and stops at a character it cannot use. `Number()` requires the whole trimmed string to be a valid numeric representation. `parseInt()` stops before the decimal point in `"3.9"`; `Number()` keeps the fraction. Neither choice replaces validation of what input formats your application allows.

## 32. The `map(parseInt)` trap

```js
"use strict";
console.log(["10", "10", "10"].map(parseInt).join("|"));
console.log(["10", "10", "10"].map(value => parseInt(value, 10)).join("|"));
```

**Output:**

```text
10|NaN|2
10|10|10
```

**Detailed reason:** `map()` passes the value, index, and array to its callback. `parseInt()` interprets its second argument as a radix. The calls therefore use radices zero, one, and two. Radix zero infers decimal here, radix one is invalid, and binary `"10"` is two. Wrapping the call lets you supply radix ten instead of accidentally accepting the index.

## 33. Post-increment versus pre-increment

```js
"use strict";
let value = "5";
console.log(value++);
console.log(value);
console.log(++value);
```

**Output:**

```text
5
6
7
```

**Detailed reason:** Increment performs numeric conversion, so the original string becomes a numeric value. Post-increment returns the previous numeric value and then updates the variable. Pre-increment updates first and returns the new value. The first printed five is a number. Avoid combining many increments into one expression; separating updates makes intent clearer.

## 34. Addition assignment versus subtraction assignment

```js
"use strict";
let a = "5";
let b = "5";
a += 1;
b -= 1;
console.log(a, typeof a);
console.log(b, typeof b);
```

**Output:**

```text
51 string
4 number
```

**Detailed reason:** `a += 1` performs the same kind of operation as `a = a + 1`, so the string causes concatenation. `b -= 1` performs subtraction, which numerically converts the string. Similar-looking assignment operators can therefore produce different types. Convert form values before updating a numeric counter or total.

## 35. Floating-point precision

```js
"use strict";
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 === 0.3);
console.log((0.1 + 0.2).toFixed(2));
console.log(typeof (0.1 + 0.2).toFixed(2));
```

**Output:**

```text
0.30000000000000004
false
0.30
string
```

**Detailed reason:** Binary floating-point cannot represent these decimal fractions exactly. The stored approximations produce a small difference, so strict equality with the stored value of `0.3` fails. `toFixed(2)` formats the result as a string with two decimal places; it does not change the underlying arithmetic. Use a problem-appropriate tolerance or a suitable decimal representation.

## 36. BigInt conversion and mixed arithmetic

```js
"use strict";
console.log(String(1n + 2n));
console.log(1n == 1);
console.log(1n === 1);
try { console.log(1n + 1); } catch (error) { console.log(error.name); }
try { console.log(+1n); } catch (error) { console.log(error.name); }
```

**Output:**

```text
3
true
false
TypeError
TypeError
```

**Detailed reason:** Two BigInts can be added. Loose equality allows this integer BigInt and Number to compare equal, while strict equality rejects different types. Arithmetic addition cannot mix BigInt and Number. Unary plus also does not accept BigInt. Explicit conversion is possible, but converting a large BigInt to Number can lose precision.

## 37. Symbol conversion is not ordinary concatenation

```js
"use strict";
const id = Symbol("id");
console.log(String(id));
try { console.log("key:" + id); } catch (error) { console.log(error.name); }
```

**Output:**

```text
Symbol(id)
TypeError
```

**Detailed reason:** `String(symbol)` has special support for producing a descriptive string. Implicit symbol-to-string conversion during concatenation throws instead. A symbol's description is a label for debugging; it does not define its identity. Two separate calls to `Symbol("id")` create different symbols.

## 38. Common `typeof` surprises

```js
"use strict";
console.log(typeof null);
console.log(typeof []);
console.log(typeof function () {});
console.log(typeof missingName);
console.log(Array.isArray([]));
```

**Output:**

```text
object
object
function
undefined
true
```

**Detailed reason:** `typeof null` is a historical language quirk. Arrays are objects, so use `Array.isArray()` to recognize them. Callable functions report `"function"`. `typeof` can safely check this undeclared name, but it does not safely access a `let` or `const` binding still in its temporal dead zone.

## 39. Objects compare by identity

```js
"use strict";
const a = { value: 1 };
const b = { value: 1 };
const c = a;
console.log(a === b);
console.log(a === c);
console.log([] == []);
```

**Output:**

```text
false
true
false
```

**Detailed reason:** `a` and `b` refer to separate objects even though their properties match. `c` holds the same object reference as `a`, so they are equal. Two arrays are also separate objects. Loose equality does not convert two object operands to compare their contents. Choose a domain-specific comparison if matching fields should count as equal.

## 40. Shallow copying shares nested objects

```js
"use strict";
const original = { score: 1, address: { city: "Chennai" } };
const copy = { ...original };
copy.score = 2;
copy.address.city = "Pune";
console.log(original.score);
console.log(original.address.city);
console.log(original === copy);
```

**Output:**

```text
1
Pune
false
```

**Detailed reason:** Spread creates a new outer object and copies property values. The primitive score is copied independently. The address property's value is a reference, so both objects share the same address object. Reassigning `copy.score` affects only the copy; editing the shared address affects both. Copy the changed nested path for an immutable update.

## 41. `const` and shallow freezing

```js
"use strict";
const user = Object.freeze({ profile: { name: "Sam" } });
user.profile.name = "Alex";
console.log(user.profile.name);
try { user.profile = {}; } catch (error) { console.log(error.name); }
try { user = {}; } catch (error) { console.log(error.name); }
```

**Output:**

```text
Alex
TypeError
TypeError
```

**Detailed reason:** Freeze protects the outer object's data properties, but does not freeze the nested profile. Replacing the frozen profile property fails in strict mode. Reassigning `user` fails because its binding is const, independently of freezing. Binding protection and object protection are separate rules.

## 42. `var` before assignment

```js
"use strict";
console.log(score);
var score = 10;
console.log(score);
```

**Output:**

```text
undefined
10
```

**Detailed reason:** Before the code runs, the `var` binding is created and initialized to undefined. The assignment of ten happens only when execution reaches that line. Hoisting does not move the assignment to the beginning. Accessing the binding early is allowed, but it does not give the later value.

## 43. The temporal dead zone also affects `typeof`

```js
"use strict";
try {
  console.log(typeof count);
  let count = 10;
} catch (error) {
  console.log(error.name);
}
```

**Output:**

```text
ReferenceError
```

**Detailed reason:** The block's `count` binding exists but is uninitialized when `typeof count` runs. It is inside the TDZ, so even `typeof` throws. Execution jumps to the catch, so the declaration line is not executed and no value from the first `console.log()` is printed. This differs from checking a completely undeclared name.

## 44. Function declaration versus function expression

```js
"use strict";
console.log(add(2, 3));
function add(a, b) { return a + b; }

try { console.log(multiply(2, 3)); }
catch (error) { console.log(error.name); }
var multiply = function (a, b) { return a * b; };
console.log(multiply(2, 3));
```

**Output:**

```text
5
TypeError
6
```

**Detailed reason:** The function declaration is initialized before its call. The `var` binding for `multiply` exists early, but contains undefined until assignment. Attempting to call undefined causes a TypeError. After assignment, it contains a function and works. A const expression accessed early would instead fail with a TDZ ReferenceError.

## 45. Closures read the current binding

```js
"use strict";
let value = 1;
function read() { return value; }
value = 2;
console.log(read());

function createCounter() {
  let count = 0;
  return () => ++count;
}
const first = createCounter();
const second = createCounter();
console.log(first(), first(), second());
```

**Output:**

```text
2
1 2 1
```

**Detailed reason:** A closure retains access to a variable binding, not a fixed snapshot of the value. `read()` therefore sees two. Each call to `createCounter()` creates a new local count binding. The first counter's two calls share one count, while the second counter starts with its own count of zero.

## 46. Losing `this` when extracting a method

```js
"use strict";
const user = {
  name: "Sam",
  greet() { return this.name; },
};
console.log(user.greet());
const greet = user.greet;
try { console.log(greet()); } catch (error) { console.log(error.name); }
console.log(greet.call({ name: "Alex" }));
```

**Output:**

```text
Sam
TypeError
Alex
```

**Detailed reason:** `user.greet()` supplies `user` as the receiver. Extracting the method into a variable does not preserve that receiver. The plain strict-mode call has undefined as `this`, so reading `this.name` throws. `call()` explicitly supplies another receiver. This can happen when passing an object method to a timer or event handler.

## 47. An arrow retains surrounding `this`

```js
"use strict";
const user = {
  name: "Sam",
  makeReader() { return () => this.name; },
};
const read = user.makeReader();
console.log(read());
console.log(read.call({ name: "Alex" }));
```

**Output:**

```text
Sam
Sam
```

**Detailed reason:** The regular method is called on user, so its `this` is user. The arrow created inside inherits that `this`. Later, `call()` cannot give the arrow a different `this`. Using an arrow inside a method is different from defining the method itself as an arrow at the top level.

## 48. A missing return in `map()`

```js
"use strict";
const wrong = [1, 2].map(value => { value * 2; });
const right = [1, 2].map(value => value * 2);
console.log(wrong.length, wrong[0], wrong[1]);
console.log(JSON.stringify(right));
```

**Output:**

```text
2 undefined undefined
[2,4]
```

**Detailed reason:** An arrow with a block body needs an explicit return. The multiplication runs, but its result is discarded, so each callback returns undefined. An expression-bodied arrow returns the expression automatically. The first result has two present undefined entries, not two holes. JSON would turn those undefined array entries into null, so direct indexed logging is clearer here.

## 49. Default sorting joins numeric values with string rules

```js
"use strict";
const values = [2, 10, 1];
console.log(JSON.stringify(values.sort()));
console.log(JSON.stringify(values.sort((a, b) => a - b)));
console.log(JSON.stringify(values));
```

**Output:**

```text
[1,10,2]
[1,2,10]
[1,2,10]
```

**Detailed reason:** Default sort compares values using string ordering, so `"10"` comes before `"2"`. A numeric comparator returns a negative, zero, or positive difference to establish numeric ordering. Both sorts mutate the same original array, so the final line shows the second sort's result. Copy before sorting when other code needs the original order.

## 50. `slice()` versus `splice()` output

```js
"use strict";
const values = [10, 20, 30, 40];
console.log(JSON.stringify(values.slice(1, 3)));
console.log(JSON.stringify(values));
console.log(JSON.stringify(values.splice(1, 2, 99)));
console.log(JSON.stringify(values));
```

**Output:**

```text
[20,30]
[10,20,30,40]
[20,30]
[10,99,40]
```

**Detailed reason:** Slice copies from index one up to, but not including, index three. It preserves the source. Splice starts at index one, removes two entries, inserts 99, and returns the removed entries. Matching return values in this example do not mean the methods do the same thing; their effects on the source are different.

## 51. Empty arrays with `some()` and `every()`

```js
"use strict";
console.log([].some(() => true));
console.log([].every(() => false));
console.log([1, 2, 3].some(value => value > 2));
console.log([1, 2, 3].every(value => value > 2));
```

**Output:**

```text
false
true
true
false
```

**Detailed reason:** An empty array contains no item that passes, so some returns false. It also contains no item that fails, so every returns true. The callbacks are not called for the empty arrays. On the populated array, three passes the condition for some, but one fails it for every. Check length separately if validation requires at least one item.

## 52. Sparse arrays versus undefined entries

```js
"use strict";
const values = [1, , 3];
let calls = 0;
const result = values.map(value => { calls++; return value * 2; });
console.log(values.length, calls);
console.log(1 in result);
console.log(JSON.stringify([...values]));
```

**Output:**

```text
3 2
false
[1,null,3]
```

**Detailed reason:** The source has length three but no property at index one. Map skips that absent index and preserves the hole, so only two callbacks run. Spread uses array iteration and creates a present undefined entry for the hole. JSON serialization then displays that undefined array entry as null. The original hole, spread's undefined, and JSON's null are three different stages.

## 53. `Set` uses identity for objects

```js
"use strict";
console.log(new Set([1, 1, NaN, NaN]).size);
console.log(new Set([{ id: 1 }, { id: 1 }]).size);
const user = { id: 1 };
console.log(new Set([user, user]).size);
```

**Output:**

```text
2
2
1
```

**Detailed reason:** Set removes repeated primitive values and treats NaN as equal to NaN for membership. Separate object literals remain separate entries despite matching properties. Repeating the same object reference adds only one entry. To remove duplicate records by ID, track their IDs instead of putting whole records into a set.

## 54. Optional chaining is only nullish protection

```js
"use strict";
const user = { profile: null, score: 0 };
console.log(user.profile?.name);
console.log(user.score ?? 100);
try { console.log((user.profile?.address).city); }
catch (error) { console.log(error.name); }
```

**Output:**

```text
undefined
0
TypeError
```

**Detailed reason:** The first access stops because profile is null. The score stays zero because nullish coalescing does not replace zero. In the final expression, the parenthesized optional chain produces undefined; the later ordinary `.city` tries to read a property from undefined and throws. Keep optional chains continuous when each level may be missing.

## 55. JSON changes or drops some values

```js
"use strict";
console.log(JSON.stringify({ a: undefined, b: null, c: NaN }));
console.log(JSON.stringify([undefined, null, NaN]));
console.log(typeof JSON.stringify(undefined));
```

**Output:**

```text
{"b":null,"c":null}
[null,null,null]
undefined
```

**Detailed reason:** In an object, an undefined-valued property is omitted. In an array, undefined becomes null so the position remains represented. NaN becomes null in both cases. Stringifying top-level undefined returns actual undefined, not a JSON string. These changes are one reason JSON stringify/parse is not a general deep-copy solution.

## 56. Promise executor, microtask, and timer order

```js
"use strict";
console.log("A");
new Promise(resolve => {
  console.log("B");
  resolve();
}).then(() => console.log("C"));
setTimeout(() => console.log("D"), 0);
console.log("E");
```

**Output:**

```text
A
B
E
C
D
```

**Detailed reason:** The promise executor runs immediately, so B is synchronous. Its then handler is a microtask, so C waits until the current synchronous code finishes. E therefore appears before C. The timer callback runs later as task work, after the queued promise reaction in this example. A zero-delay timer does not run immediately.

## 57. `await` pauses only the async function

```js
"use strict";
async function run() {
  console.log("A");
  await 1;
  console.log("B");
}
console.log("C");
run();
console.log("D");
```

**Output:**

```text
C
A
D
B
```

**Detailed reason:** Calling run starts its body synchronously, so A prints before the caller continues. Awaiting even a plain value causes the continuation to run asynchronously. The caller prints D while run is paused, and B prints afterward. Await does not freeze the whole JavaScript thread or turn the function's initial work into background work.

## 58. Promise error recovery changes the next value

```js
"use strict";
Promise.resolve(2)
  .then(value => {
    console.log(value);
    throw new Error("failed");
  })
  .then(() => console.log("skipped"))
  .catch(error => {
    console.log(error.message);
    return 7;
  })
  .finally(() => console.log("cleanup"))
  .then(value => console.log(value));
```

**Output:**

```text
2
failed
cleanup
7
```

**Detailed reason:** Throwing rejects the next promise, so the following fulfillment-only handler is skipped. Catch receives the error and returns seven, recovering the chain into fulfillment. Finally logs cleanup and normally preserves the result, so the final then receives seven. If catch rethrew, the chain would stay rejected instead.

## 59. `Promise.all()` preserves input order

```js
"use strict";
const slow = new Promise(resolve => setTimeout(() => resolve("slow"), 20));
const fast = Promise.resolve("fast");
Promise.all([slow, fast]).then(values => console.log(values.join("|")));
```

**Output:**

```text
slow|fast
```

**Detailed reason:** The fast promise fulfills first, but Promise.all waits for both and places results in the order of the input iterable. Completion order does not determine result order. The timer's duration is a scheduling request, not an exact completion guarantee. If either input rejected, all would reject without automatically canceling the other operation.

## 60. Loop variables and timer closures

```js
"use strict";
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log("var", i), 0);
}
for (let j = 0; j < 3; j++) {
  setTimeout(() => console.log("let", j), 0);
}
```

**Output:**

```text
var 3
var 3
var 3
let 0
let 1
let 2
```

**Detailed reason:** All three var callbacks share one binding. By the time timers run, the loop has finished and that binding is three. Let creates a separate binding for each loop iteration, so each callback retains its corresponding value. The timers are registered in the displayed order and run after synchronous loop execution in this example.

## 61. Async callbacks do not make `forEach()` wait

```js
"use strict";
[1, 2].forEach(async value => {
  await Promise.resolve();
  console.log(value);
});
console.log("done");
```

**Output:**

```text
done
1
2
```

**Detailed reason:** ForEach calls each async callback but ignores the returned promises. Each callback pauses at await. ForEach then finishes and the synchronous done log runs. The callback continuations print afterward. Use `for...of` with await for sequential work, or `await Promise.all(items.map(async ...))` for independent concurrent work with a joined result.

## 62. New microtasks join the microtask queue

```js
"use strict";
Promise.resolve().then(() => {
  console.log("A");
  queueMicrotask(() => console.log("C"));
});
queueMicrotask(() => console.log("B"));
setTimeout(() => console.log("D"), 0);
```

**Output:**

```text
A
B
C
D
```

**Detailed reason:** The promise reaction is queued before B's microtask. When A runs, it appends C to the queue; B was already waiting, so B runs before C. The queue is drained before the timer task runs. A microtask created by another microtask does not automatically jump ahead of existing microtasks.

## 63. The bound function keeps its receiver

```js
"use strict";
function read() { return this.name; }
const bound = read.bind({ name: "Sam" });
console.log(bound());
console.log(bound.call({ name: "Alex" }));
console.log(bound === read.bind({ name: "Sam" }));
```

**Output:**

```text
Sam
Sam
false
```

**Detailed reason:** For ordinary calls, the bound function uses its saved receiver, even if call supplies another one. Each bind call creates a new function object, so the two bound functions are not equal. Save a bound callback if it must later be passed to removeEventListener. Constructor calls have additional bind behavior and are not demonstrated here.

## 64. Reassigning a parameter does not replace the caller's variable

```js
"use strict";
function change(user) {
  user.name = "Alex";
  user = { name: "New" };
  return user.name;
}
const original = { name: "Sam" };
console.log(change(original));
console.log(original.name);
```

**Output:**

```text
New
Alex
```

**Detailed reason:** The parameter receives a copy of the object reference. Initially it points to the caller's object, so the name mutation is shared. Reassigning the parameter changes only the local binding to point at another object. It does not reassign original. JavaScript passes values; an object reference is one such value.

## 65. Property keys can turn numbers into strings

```js
"use strict";
const object = {};
object[1] = "number key";
object["1"] = "string key";
console.log(object[1]);

const map = new Map();
map.set(1, "number key");
map.set("1", "string key");
console.log(map.size);
console.log(map.get(1));
```

**Output:**

```text
string key
2
number key
```

**Detailed reason:** Ordinary object keys are strings or symbols. The numeric key one becomes the string `"1"`, so the second assignment overwrites the same property. Map retains key types, so numeric one and string one are different keys. Choose Map when key identity and type should be preserved.

---

# How to Solve an Output Question

Use this order instead of guessing:

1. **Check syntax and context.** Is it an expression, script, module, or strict-mode function? Are errors caught?
2. **Check evaluation order.** Resolve parentheses and operator precedence; left-to-right grouping does not override precedence.
3. **Write intermediate values and types.** For `1 + 2 + "3"`, write `3 (number)` and then `"33" (string)`.
4. **Apply the operator's own rules.** Boolean conversion, loose equality, numeric conversion, and string comparison are different operations.
5. **Check references and scope.** Are values separate objects, shared nested objects, or bindings in a TDZ?
6. **Separate sync and async work.** Print synchronous logs first, then track queued microtasks and later tasks for the specific runtime.
7. **Explain the practical mistake.** Connect the example to form input, stale API responses, missing returns, lost receivers, or shared state.

# Quick Conversion Reference

| Value | `Number(value)` | `String(value)` | `Boolean(value)` |
| --- | --- | --- | --- |
| `undefined` | `NaN` | `"undefined"` | `false` |
| `null` | `0` | `"null"` | `false` |
| `true` | `1` | `"true"` | `true` |
| `false` | `0` | `"false"` | `false` |
| `""` | `0` | `""` | `false` |
| `" "` | `0` | `" "` | `true` |
| `"0"` | `0` | `"0"` | `true` |
| `"false"` | `NaN` | `"false"` | `true` |
| `[]` | `0` | `""` | `true` |
| `[1]` | `1` | `"1"` | `true` |
| `[1, 2]` | `NaN` | `"1,2"` | `true` |
| Ordinary `{}` | `NaN` | `"[object Object]"` | `true` |

This table assumes ordinary built-in behavior, without custom conversion methods. Do not apply the numeric column blindly to `==`; loose equality has its own algorithm.

# Interview Practice

- Start with questions 1–37 until you can explain every conversion step.
- Continue with questions 38–55 for references, scope, arrays, and missing values.
- Use questions 56–62 to practice async order; run each snippet separately.
- Finish with questions 63–65 and explain their practical use cases.
- Read the broader concepts in `javascript.md` alongside this guide.

Aim to explain why the output happens, not only to remember the output. In application code, prefer clear conversions and simple expressions over clever combinations of operators.
