### **Math Operations Between Strings and Numbers**

#### **Example 37: Addition Between a String and a Number**
```javascript
console.log("10" + 5); // "105"
```
**Explanation:**  
The `+` operator concatenates when one operand is a string, so `"10" + 5` results in `"105"`.

---

#### **Example 38: Subtraction Between a String and a Number**
```javascript
console.log("10" - 5); // 5
```
**Explanation:**  
The `-` operator converts the string `"10"` into a number, and the result is `5`.

---

#### **Example 39: Multiplication Between a String and a Number**
```javascript
console.log("10" * 5); // 50
```
**Explanation:**  
The `*` operator converts the string `"10"` into a number, resulting in `50`.

---

#### **Example 40: Division Between a String and a Number**
```javascript
console.log("10" / 2); // 5
```
**Explanation:**  
The `/` operator converts the string `"10"` into a number, so the result is `5`.

---

#### **Example 41: Modulus Between a String and a Number**
```javascript
console.log("10" % 3); // 1
```
**Explanation:**  
The `%` operator converts the string `"10"` into a number and computes the remainder, which is `1`.

---

#### **Example 42: Adding a String Representing a Non-Numeric Value**
```javascript
console.log("hello" - 5); // NaN
```
**Explanation:**  
The string `"hello"` cannot be converted into a number, so the operation results in `NaN`.

---

#### **Example 43: Multiplying a String with Non-Numeric Value**
```javascript
console.log("hello" * 2); // NaN
```
**Explanation:**  
The string `"hello"` cannot be converted to a number, so the result is `NaN`.

---

#### **Example 44: Adding Numbers as Strings**
```javascript
console.log("5" + "5"); // "55"
```
**Explanation:**  
Both operands are strings, so they are concatenated, resulting in `"55"`.

---

#### **Example 45: Adding Empty Strings**
```javascript
console.log("" + 1); // "1"
```
**Explanation:**  
An empty string concatenated with a number results in the number being converted to a string.

---

### **More Type Coercion Quirks**

#### **Example 46: Mixed Type Comparisons**
```javascript
console.log(5 == "5"); // true
```
**Explanation:**  
Loose equality (`==`) converts the string `"5"` into the number `5`.

---

#### **Example 47: Strict Equality with Different Types**
```javascript
console.log(5 === "5"); // false
```
**Explanation:**  
Strict equality (`===`) checks type and value, so `5` and `"5"` are not strictly equal.

---

#### **Example 48: NaN in Comparisons**
```javascript
console.log(NaN == NaN); // false
```
**Explanation:**  
`NaN` is not equal to itself by definition.

---

#### **Example 49: Boolean and Strings**
```javascript
console.log("true" == true); // false
```
**Explanation:**  
`"true"` as a string is not coerced into a boolean value.

---

#### **Example 50: `null` and Zero**
```javascript
console.log(null == 0); // false
console.log(null < 1);  // true
```
**Explanation:**  
`null` loosely equals `undefined` but not `0`. However, comparisons like `<` coerce `null` to `0`.

---

### **Array and Object Quirks**

#### **Example 51: Adding Arrays**
```javascript
console.log([1, 2] + [3, 4]); // "1,23,4"
```
**Explanation:**  
Both arrays are converted to strings (`"1,2"` and `"3,4"`) and concatenated.

---

#### **Example 52: Array to Number**
```javascript
console.log(+[10]); // 10
```
**Explanation:**  
The unary `+` converts the array to its numeric equivalent. `[10]` becomes `10`.

---

#### **Example 53: Empty Array to Number**
```javascript
console.log(+[]); // 0
```
**Explanation:**  
An empty array converts to an empty string, which is coerced to `0`.

---

#### **Example 54: Object to String**
```javascript
console.log({} + "hello"); // "[object Object]hello"
```
**Explanation:**  
The object is coerced into the string `"[object Object]"`.

---

#### **Example 55: Array Equality**
```javascript
console.log([] == []); // false
```
**Explanation:**  
Arrays are compared by reference, not value.

---

### **Function and Scope Quirks**

#### **Example 56: Function Returning `this`**
```javascript
function foo() {
  return this;
}
console.log(foo()); // global object (or `undefined` in strict mode)
```
**Explanation:**  
`this` in a non-strict function refers to the global object.

---

#### **Example 57: `this` in Arrow Functions**
```javascript
const foo = () => this;
console.log(foo()); // global object
```
**Explanation:**  
Arrow functions inherit `this` from their surrounding lexical scope.

---

#### **Example 58: Duplicate Function Parameters**
```javascript
function foo(a, a) {
  console.log(a);
}
foo(1, 2); // 2
```
**Explanation:**  
The second parameter overwrites the first.

---

#### **Example 59: Function Length Property**
```javascript
function foo(a, b, c) {}
console.log(foo.length); // 3
```
**Explanation:**  
The `length` property of a function represents the number of parameters.

---

#### **Example 60: Modifying Function's `arguments`**
```javascript
function foo(a) {
  arguments[0] = 2;
  console.log(a);
}
foo(1); // 2
```
**Explanation:**  
The `arguments` object is linked to parameters in non-strict mode.

---

### **Event Loop Quirks**

#### **Example 61: Order of Promises and `setTimeout`**
```javascript
console.log(1);
setTimeout(() => console.log(2), 0);
Promise.resolve().then(() => console.log(3));
console.log(4);
```
**Output:**
```
1
4
3
2
```
**Explanation:**  
Promises are executed before `setTimeout` callbacks in the event loop.

---

#### **Example 62: `setTimeout` Inside a Loop**
```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```
**Output:**
```
3
3
3
```
**Explanation:**  
`var` is function-scoped, so all callbacks share the same `i` after the loop finishes.

---

### **Example 1: Adding Arrays**
```javascript
console.log([] + []);
```
**Output:**
```
""
```

**Explanation:**
- When `+` is used with arrays, JavaScript converts them to strings. Since both arrays are empty, their string representation is `""`, resulting in an empty string.

---

### **Example 2: Adding an Array and a Number**
```javascript
console.log([] + 1);
```
**Output:**
```
"1"
```

**Explanation:**
- The empty array is converted to an empty string (`""`), and `1` is then concatenated as a string. The result is `"1"`.

---

### **Example 3: Subtracting Arrays**
```javascript
console.log([] - []);
```
**Output:**
```
0
```

**Explanation:**
- The `-` operator does not perform string concatenation; it attempts to coerce both arrays into numbers. Both arrays are coerced into `0`, so the result is `0`.

---

### **Example 4: `null` vs `undefined` in Equality**
```javascript
console.log(null == undefined);  // true
console.log(null === undefined); // false
```

**Explanation:**
- `null` and `undefined` are loosely equal (`==`) because they both represent "no value."
- Strict equality (`===`) checks both type and value, so `null` and `undefined` are not strictly equal.

---

### **Example 5: Implicit Boolean Conversion**
```javascript
console.log([] == true);  // false
console.log([] == false); // true
```

**Explanation:**
- `[]` is truthy in a boolean context, but during loose equality (`==`) comparison, it's coerced into a string (`""`) which is falsy. Thus, `[] == false` is `true`.

---

### **Example 6: NaN Comparisons**
```javascript
console.log(NaN == NaN);  // false
console.log(Object.is(NaN, NaN)); // true
```

**Explanation:**
- `NaN` (Not-a-Number) is not equal to itself. This behavior is defined by IEEE 754 floating-point standards.
- Use `Object.is` to check strict equality for `NaN`.

---

### **Example 7: Misleading Type Coercion**
```javascript
console.log('5' - 3);  // 2
console.log('5' + 3);  // "53"
```

**Explanation:**
- `-` triggers numeric conversion, so `'5'` becomes `5`, and the result is `2`.
- `+` triggers string concatenation when one operand is a string, so `3` is converted to `"3"`, and the result is `"53"`.

---

### **Example 8: Comparing Objects**
```javascript
console.log({} + []); // "[object Object]"
console.log([] + {}); // "[object Object]"
```

**Explanation:**
- The `{}` object is converted to its string representation, `"[object Object]"`.
- Similarly, the empty array `[]` is converted to an empty string, and concatenation occurs.

---

### **Example 9: Array Holes**
```javascript
const arr = [1, , 3];
console.log(arr.length); // 3
console.log(arr[1]);     // undefined
```

**Explanation:**
- Creating an array with a hole (missing element) still allocates the index but leaves it undefined.

---

### **Example 10: Double Negation Quirk**
```javascript
console.log(![]);  // false
console.log(!![]); // true
```

**Explanation:**
- `[]` is truthy, so `![]` is `false`. Double negation (`!!`) converts the truthy value back to `true`.

---

### **Type Coercion Quirks**

#### **Example 11: Coercion with `null`**
```javascript
console.log(null + 1); // 1
```
**Explanation:**  
`null` is coerced to `0` when used in numeric operations.

---

#### **Example 12: Coercion with `undefined`**
```javascript
console.log(undefined + 1); // NaN
```
**Explanation:**  
`undefined` cannot be coerced into a number, so the result is `NaN`.

---

#### **Example 13: Boolean to Number**
```javascript
console.log(true + true); // 2
```
**Explanation:**  
`true` is coerced to `1`, so `1 + 1 = 2`.

---

#### **Example 14: Multiplying Strings**
```javascript
console.log("3" * "3"); // 9
```
**Explanation:**  
JavaScript converts strings to numbers during multiplication.

---

#### **Example 15: Concatenation in Objects**
```javascript
console.log({} + 2); // "[object Object]2"
```
**Explanation:**  
The object is converted to a string (`"[object Object]"`) and concatenated with `2`.

---

#### **Example 16: Coercion with Boolean and String**
```javascript
console.log(true + "test"); // "truetest"
```
**Explanation:**  
`true` is converted to `"true"` and concatenated with `"test"`.

---

#### **Example 17: Division by Zero**
```javascript
console.log(1 / 0); // Infinity
```
**Explanation:**  
JavaScript represents division by zero as `Infinity`.

---

#### **Example 18: Subtracting Booleans**
```javascript
console.log(true - false); // 1
```
**Explanation:**  
`true` becomes `1`, and `false` becomes `0`. Thus, `1 - 0 = 1`.

---

#### **Example 19: Combining Boolean and String**
```javascript
console.log(false + " is false"); // "false is false"
```
**Explanation:**  
`false` is coerced into the string `"false"`.

---

#### **Example 20: Adding an Empty Object**
```javascript
console.log({} + {}); // "[object Object][object Object]"
```
**Explanation:**  
Both objects are converted to their string representations.

---

### **Equality Quirks**

#### **Example 21: Loose Equality with Numbers and Strings**
```javascript
console.log(0 == ""); // true
```
**Explanation:**  
`""` is coerced to `0` in loose equality.

---

#### **Example 22: Comparing Empty Arrays**
```javascript
console.log([] == 0); // true
```
**Explanation:**  
`[]` is coerced into a string, then into `0`, so the comparison is true.

---

#### **Example 23: Comparing `null` and `0`**
```javascript
console.log(null > 0); // false
console.log(null == 0); // false
console.log(null >= 0); // true
```
**Explanation:**  
`null` is only coerced in certain comparisons but not in equality checks.

---

#### **Example 24: `false` and Zero**
```javascript
console.log(false == 0); // true
```
**Explanation:**  
`false` is coerced to `0`.

---

#### **Example 25: `undefined` and `null` in Comparisons**
```javascript
console.log(undefined > 0); // false
console.log(undefined == 0); // false
console.log(undefined < 0); // false
```
**Explanation:**  
`undefined` cannot be converted to a meaningful numeric value.

---

### **Object Quirks**

#### **Example 26: Array as an Object**
```javascript
const arr = [1, 2, 3];
console.log(typeof arr); // "object"
```
**Explanation:**  
Arrays are technically objects in JavaScript.

---

#### **Example 27: Adding Properties to a Function**
```javascript
function foo() {}
foo.bar = "test";
console.log(foo.bar); // "test"
```
**Explanation:**  
Functions are objects and can have properties.

---

#### **Example 28: Adding Properties to a Number**
```javascript
let num = 5;
num.test = "hello";
console.log(num.test); // undefined
```
**Explanation:**  
Primitive values like numbers are not objects, so properties cannot be added.

---

#### **Example 29: Comparing Two Objects**
```javascript
console.log({} === {}); // false
```
**Explanation:**  
Objects are compared by reference, not value.

---

#### **Example 30: `toString` on an Object**
```javascript
console.log({}.toString()); // "[object Object]"
```
**Explanation:**  
The default `toString` method returns this string for objects.

---

### **Function and Scope Quirks**

#### **Example 31: Hoisting in Functions**
```javascript
console.log(a); // undefined
var a = 10;
```
**Explanation:**  
Variables declared with `var` are hoisted, but their value remains `undefined`.

---

#### **Example 32: Default Parameters**
```javascript
function foo(a, b = 5) {
  console.log(a + b);
}
foo(3); // 8
```
**Explanation:**  
Default parameters are used if no value is provided.

---

#### **Example 33: `this` Inside a Function**
```javascript
function foo() {
  console.log(this);
}
foo(); // Window or global object
```
**Explanation:**  
In non-strict mode, `this` in a function refers to the global object.

---

#### **Example 34: Arrow Functions and `this`**
```javascript
const obj = {
  method: () => console.log(this),
};
obj.method(); // Window or global object
```
**Explanation:**  
Arrow functions do not have their own `this`; they inherit it from the outer scope.

---

#### **Example 35: Function Overwriting**
```javascript
function foo() {
  return 1;
}
function foo() {
  return 2;
}
console.log(foo()); // 2
```
**Explanation:**  
The second declaration overwrites the first.

---

### **Event Loop Quirks**

#### **Example 36: Order of `setTimeout`**
```javascript
console.log(1);
setTimeout(() => console.log(2), 0);
console.log(3);
```
**Output:**
```
1
3
2
```
**Explanation:**  
`setTimeout` is pushed to the event loop queue and executes after synchronous code.

---

Callback functions are a fundamental concept in JavaScript. They are functions passed as arguments to other functions to be executed later. Below are several examples of how callback functions work, along with their quirks and uses.

---

### **Example 1: Basic Callback**
```javascript
function greet(name, callback) {
  console.log("Hello, " + name + "!");
  callback();
}

function sayGoodbye() {
  console.log("Goodbye!");
}

greet("Alice", sayGoodbye);
// Output:
// Hello, Alice!
// Goodbye!
```
**Explanation:**  
The `sayGoodbye` function is passed as a callback to `greet` and executed after the greeting.

---

### **Example 2: Anonymous Callback**
```javascript
function processNumber(num, callback) {
  console.log("Processing number:", num);
  callback(num);
}

processNumber(5, function (n) {
  console.log("The square is:", n * n);
});
// Output:
// Processing number: 5
// The square is: 25
```
**Explanation:**  
Instead of passing a named function, an anonymous function is used as the callback.

---

### **Example 3: Callback with a Timeout**
```javascript
setTimeout(() => {
  console.log("This message is delayed by 2 seconds.");
}, 2000);
// Output (after 2 seconds):
// This message is delayed by 2 seconds.
```
**Explanation:**  
The `setTimeout` function accepts a callback that executes after the specified delay.

---

### **Example 4: Callback Inside an Array Method**
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach((num) => {
  console.log(num * 2);
});
// Output:
// 2
// 4
// 6
// 8
// 10
```
**Explanation:**  
The `forEach` method iterates over the array, calling the callback function for each element.

---

### **Example 5: Callback with `map`**
```javascript
const numbers = [1, 2, 3, 4, 5];
const squares = numbers.map((num) => num * num);
console.log(squares);
// Output:
// [1, 4, 9, 16, 25]
```
**Explanation:**  
The `map` method applies the callback to each element and returns a new array with the results.

---

### **Example 6: Chaining Callbacks**
```javascript
function step1(callback) {
  console.log("Step 1 complete");
  callback();
}

function step2(callback) {
  console.log("Step 2 complete");
  callback();
}

function step3() {
  console.log("Step 3 complete");
}

step1(() => step2(step3));
// Output:
// Step 1 complete
// Step 2 complete
// Step 3 complete
```
**Explanation:**  
Callbacks can be nested or chained for sequential execution of functions.

---

### **Example 7: Error Handling with Callbacks**
```javascript
function fetchData(callback, errorCallback) {
  const success = Math.random() > 0.5; // Simulate success or failure
  if (success) {
    callback("Data loaded successfully!");
  } else {
    errorCallback("Failed to load data.");
  }
}

fetchData(
  (data) => console.log(data),
  (error) => console.error(error)
);
// Output (randomly):
// "Data loaded successfully!"
// OR
// "Failed to load data."
```
**Explanation:**  
Callbacks can be used for error handling by providing a separate error callback.

---

### **Example 8: Callback in Event Listeners**
```javascript
document.body.addEventListener("click", () => {
  console.log("Body clicked!");
});
// Output (on click):
// Body clicked!
```
**Explanation:**  
Event listeners use callbacks to define what happens when an event occurs.

---

### **Example 9: Callback Hell**
```javascript
setTimeout(() => {
  console.log("Step 1");
  setTimeout(() => {
    console.log("Step 2");
    setTimeout(() => {
      console.log("Step 3");
    }, 1000);
  }, 1000);
}, 1000);
// Output (with delays):
// Step 1
// Step 2
// Step 3
```
**Explanation:**  
Nested callbacks like this can lead to "callback hell," making code difficult to read and maintain.

---

### **Example 10: Using Callbacks with Promises**
```javascript
function doTask(callback) {
  setTimeout(() => {
    callback("Task complete");
  }, 1000);
}

doTask((message) => {
  console.log(message);
});
// Output (after 1 second):
// Task complete
```
**Explanation:**  
Traditional callbacks can be used to handle asynchronous operations, but Promises are often preferred to avoid deeply nested callbacks.

---

### **Example 11: Passing Multiple Callbacks**
```javascript
function processText(text, successCallback, errorCallback) {
  if (text) {
    successCallback(text.toUpperCase());
  } else {
    errorCallback("No text provided");
  }
}

processText(
  "hello",
  (result) => console.log("Success:", result),
  (error) => console.error("Error:", error)
);
// Output:
// Success: HELLO

processText(
  "",
  (result) => console.log("Success:", result),
  (error) => console.error("Error:", error)
);
// Output:
// Error: No text provided
```
**Explanation:**  
Multiple callbacks allow for more flexible handling of different scenarios.

---

### **Example 12: Callback with `reduce`**
```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum);
// Output:
// 10
```
**Explanation:**  
The `reduce` method uses a callback to accumulate values from an array.

---


## **Promises**

A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation.

### **Example 1: Basic Promise**
```javascript
const myPromise = new Promise((resolve, reject) => {
  const success = Math.random() > 0.5;
  if (success) {
    resolve("Promise resolved!");
  } else {
    reject("Promise rejected!");
  }
});

myPromise
  .then((message) => console.log(message)) // Handles resolve
  .catch((error) => console.error(error)); // Handles reject
```
**Explanation:**  
- The `then` method is used for resolved values.
- The `catch` method is used for errors.

---

### **Example 2: Chaining Promises**
```javascript
const promise = new Promise((resolve) => {
  resolve(2);
});

promise
  .then((value) => {
    console.log(value); // 2
    return value * 2;
  })
  .then((value) => {
    console.log(value); // 4
    return value * 2;
  })
  .then((value) => {
    console.log(value); // 8
  });
```
**Explanation:**  
Each `then` returns a new Promise, allowing chaining.

---

### **Example 3: `Promise.all`**
```javascript
const promise1 = Promise.resolve(10);
const promise2 = new Promise((resolve) => setTimeout(() => resolve(20), 1000));
const promise3 = Promise.resolve(30);

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values); // [10, 20, 30]
});
```
**Explanation:**  
`Promise.all` resolves when all promises are resolved or rejects if any promise fails.

---

### **Example 4: `Promise.race`**
```javascript
const promise1 = new Promise((resolve) => setTimeout(() => resolve("First"), 1000));
const promise2 = new Promise((resolve) => setTimeout(() => resolve("Second"), 2000));

Promise.race([promise1, promise2]).then((value) => {
  console.log(value); // "First"
});
```
**Explanation:**  
`Promise.race` resolves or rejects as soon as the first promise settles.

---

### **Example 5: Handling Errors in Promises**
```javascript
const faultyPromise = new Promise((_, reject) => {
  reject("Something went wrong!");
});

faultyPromise
  .then((value) => console.log(value))
  .catch((error) => console.error(error)) // Handles the error
  .finally(() => console.log("Cleanup done."));
// Output:
// Something went wrong!
// Cleanup done.
```
**Explanation:**  
The `finally` method executes regardless of the promise's outcome.

---

---

## **Async/Await**

The `async/await` syntax simplifies working with promises and allows you to write asynchronous code that looks synchronous.

### **Example 6: Basic `async/await`**
```javascript
async function fetchData() {
  return "Data loaded!";
}

fetchData().then((data) => console.log(data));
// Output:
// Data loaded!
```
**Explanation:**  
An `async` function always returns a Promise. The `return` value becomes the resolved value.

---

### **Example 7: Using `await` with Promises**
```javascript
function delayedPromise() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Delayed data"), 1000);
  });
}

async function getData() {
  const result = await delayedPromise();
  console.log(result);
}

getData();
// Output (after 1 second):
// Delayed data
```
**Explanation:**  
The `await` keyword pauses execution until the promise resolves.

---

### **Example 8: Error Handling with `async/await`**
```javascript
async function riskyOperation() {
  throw new Error("Operation failed!");
}

async function execute() {
  try {
    await riskyOperation();
  } catch (error) {
    console.error(error.message); // Operation failed!
  }
}

execute();
```
**Explanation:**  
Use `try/catch` to handle errors in `async/await`.

---

### **Example 9: Parallel Execution with `await`**
```javascript
async function parallelExecution() {
  const promise1 = new Promise((resolve) => setTimeout(() => resolve(10), 1000));
  const promise2 = new Promise((resolve) => setTimeout(() => resolve(20), 2000));

  const [result1, result2] = await Promise.all([promise1, promise2]);
  console.log(result1, result2); // 10, 20
}

parallelExecution();
```
**Explanation:**  
`Promise.all` allows running promises in parallel instead of awaiting them sequentially.

---

### **Example 10: Sequential Execution**
```javascript
async function sequentialExecution() {
  const result1 = await new Promise((resolve) => setTimeout(() => resolve(10), 1000));
  console.log(result1); // 10

  const result2 = await new Promise((resolve) => setTimeout(() => resolve(20), 2000));
  console.log(result2); // 20
}

sequentialExecution();
```
**Explanation:**  
Each `await` waits for the previous operation to complete before proceeding.

---

### **Example 11: Combining Promises and `async/await`**
```javascript
async function fetchAndProcess() {
  const promise1 = Promise.resolve(5);
  const promise2 = Promise.resolve(10);

  const data = await Promise.all([promise1, promise2]);
  return data.reduce((sum, val) => sum + val, 0);
}

fetchAndProcess().then((result) => console.log(result)); // 15
```
**Explanation:**  
`async/await` and Promises can be used together for complex workflows.

---

### **Example 12: Avoiding Deadlocks**
```javascript
async function process() {
  await new Promise((resolve) => setTimeout(resolve, 1000));
  console.log("Done!");
}

process();
// Output (after 1 second):
// Done!
```
**Explanation:**  
Ensure that all `await` calls are inside `async` functions to avoid deadlocks.

---

### **Example 13: Handling Multiple Errors**
```javascript
async function fetchWithError() {
  const promise1 = Promise.reject("Error 1");
  const promise2 = Promise.resolve("Success");

  try {
    const [result1, result2] = await Promise.all([promise1, promise2]);
    console.log(result1, result2);
  } catch (error) {
    console.error("Caught error:", error); // Caught error: Error 1
  }
}

fetchWithError();
```
**Explanation:**  
If one promise in `Promise.all` fails, the entire batch fails.

---

### **Example 14: Returning a Promise from `async`**
```javascript
async function returnPromise() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Resolved!"), 1000);
  });
}

returnPromise().then((result) => console.log(result)); // Resolved!
```
**Explanation:**  
`async` functions can return promises, making them compatible with `.then()`.

---
