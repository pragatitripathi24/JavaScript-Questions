**JavaScript Interview Notes: Detailed Explanation with Examples**

---

... (existing content remains unchanged)

---

### 11. What is a First-Class Function?

In JavaScript, functions are **first-class citizens**. This means functions can be:
- Assigned to variables
- Passed as arguments to other functions
- Returned from other functions
- Stored in data structures like arrays or objects

**Example:**
```js
function greet() {
  return "Hello";
}
const sayHello = greet; // assigned to a variable
console.log(sayHello());

function execute(fn) {
  return fn();
}
console.log(execute(greet));
```

**Key Insight:**
> First-class functions make functional programming possible in JavaScript.

---

### 12. What is a First-Order Function?

A **first-order function** is a function that:
- **Does not accept** another function as an argument
- **Does not return** another function

**Example:**
```js
function add(a, b) {
  return a + b;
}
```
- Simple and direct
- Works only on basic values

---

### 13. What is a Higher-Order Function?

A **higher-order function** is a function that **takes one or more functions as arguments** or **returns another function**.

**Examples:**
```js
// Takes a function as input
function greet(fn) {
  return fn();
}

// Returns a new function
function multiplier(factor) {
  return function(num) {
    return num * factor;
  };
}
const triple = multiplier(3);
console.log(triple(5)); // 15
```

Common higher-order functions in JavaScript:
- `map`, `filter`, `reduce`

---

### 14. What is a Unary Function?

A **unary function** is a function that takes exactly **one argument**.

**Example:**
```js
function square(x) {
  return x * x;
}
```

**Use Cases:**
- Used in `map()`, `filter()` where a single input is needed
- Common in mathematical and functional programming

---

### 15. What is Currying?

**Currying** is the technique of converting a function that takes multiple arguments into a sequence of **functions that each take a single argument**.

#### 🔹 Traditional function:
```js
function add(a, b) {
  return a + b;
}
add(2, 3); // 5
```

#### 🔹 Curried version:
```js
function curriedAdd(a) {
  return function(b) {
    return a + b;
  };
}
curriedAdd(2)(3); // 5
```

#### 🔹 Real-World Example:
```js
function log(level) {
  return function(message) {
    console.log(`[${level}] ${message}`);
  };
}
const info = log("INFO");
const error = log("ERROR");
info("Server started");   // [INFO] Server started
error("Crash detected"); // [ERROR] Crash detected
```

#### 🔹 Why Use Currying?
- Helps create **reusable specialized functions**
- Enables **function composition**
- Supports **partial application** (fix some arguments)

---

### 16. What is a Pure Function?

A **pure function** is a function that:
1. **Returns the same result** when given the same inputs
2. Has **no side effects**

#### 🔹 Pure Function Example:
```js
function multiply(a, b) {
  return a * b;
}
console.log(multiply(2, 2)); // always 4
```
- Always consistent output
- Doesn’t modify anything outside its scope

#### 🔸 Impure Function Example:
```js
let count = 0;
function increment() {
  count++;
}
```
- Modifies `count` outside the function → side effect → not pure

#### 🔹 How to Identify Pure Functions:
- No reliance on external state
- No modification of global variables
- No console, DOM, API calls inside
- Deterministic (same input → same output)

---

### 17. What are the Benefits of Pure Functions?

Pure functions are central to **functional programming**. Key benefits:

1. ✅ **Predictable**
   - Always behaves the same for the same input

2. ✅ **Easy to Test**
   - No external dependencies

3. ✅ **Debug-Friendly**
   - Fewer places to look for bugs

4. ✅ **Concurrency-Safe**
   - No shared mutable state, safe for parallel execution

5. ✅ **Reusability**
   - Easy to combine and reuse across the codebase

---

### 18. What is the Purpose of the `let` Keyword?

The `let` keyword (introduced in ES6) is used to **declare block-scoped variables**.

#### 🔹 Why `let` is useful:
- Limits scope to `{}` block → safer code
- Avoids accidental variable leaks

**Example:**
```js
for (let i = 0; i < 3; i++) {
  console.log(i); // 0,1,2
}
console.log(i); // ReferenceError
```

---

### 19. What is the Difference Between `let` and `var`?

| Feature        | `var`                         | `let`                          |
|----------------|-------------------------------|---------------------------------|
| Scope          | Function-scoped               | Block-scoped                   |
| Hoisting       | Hoisted (initialized to `undefined`) | Hoisted but not initialized      |
| Redeclaration  | Allowed                       | Not allowed in the same scope |
| Temporal Dead Zone | No                       | Yes – can't access before declaration |

**Example:**
```js
console.log(a); // undefined
var a = 10;

console.log(b); // ReferenceError
let b = 20;
```

---

### 20. What is the Reason to Choose the Name `let` as a Keyword?

The keyword `let` was inspired by older programming languages like **Scheme**, **Haskell**, and **ALGOL**, where `let` was used to **bind variables**.

#### 🔹 Why the name `let`?
- Short and intuitive for variable declaration
- Indicates “binding” a value
- Clear distinction from `var`, avoids confusion with function-scoping

**Conclusion:**
> `let` was chosen for clarity, expressiveness, and familiarity to developers with a background in functional programming.

