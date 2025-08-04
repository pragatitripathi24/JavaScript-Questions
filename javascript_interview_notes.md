**JavaScript Interview Notes: Detailed Explanation with Examples**

---

### 1. What are the possible ways to create objects in JavaScript?

JavaScript provides multiple ways to create objects. Each method has its own use case depending on the situation.

#### 1.1 Using Object Literal (Most Common)

```js
const person = {
  name: "Alice",
  age: 25
};
```

- Easy to read and use.
- Good for creating single objects with known properties.

#### 1.2 Using `new Object()`

```js
const person = new Object();
person.name = "Alice";
person.age = 25;
```

- Less preferred, same effect as literal.

#### 1.3 Using Constructor Function

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
const person = new Person("Alice", 25);
```

- Useful when creating multiple similar objects.

#### 1.4 Using `Object.create()`

```js
const proto = {
  greet() { return "Hello"; }
};
const person = Object.create(proto);
person.name = "Alice";
```

- Allows creation with a specific prototype.

#### 1.5 Using ES6 Classes

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
const person = new Person("Alice", 25);
```

- Modern and preferred way for reusable object blueprints.

---

### 2. What is a Prototype Chain?

In JavaScript, objects inherit properties and methods from other objects via the **prototype chain**.

- Every object has a hidden property `[[Prototype]]` (or `__proto__`) that points to another object.
- When you try to access a property, JavaScript first checks the object itself.
- If not found, it looks up the prototype chain until it reaches `null`.

**Example:**

```js
const parent = { greet() { return "Hello"; } };
const child = Object.create(parent);
console.log(child.greet()); // "Hello"
```

The chain here is: `child` → `parent` → `Object.prototype` → `null`

---

### 3. What is the Difference Between `call`, `apply`, and `bind`?

All three are used to manually set the `this` value inside a function.

#### `call()`

- Calls the function immediately.
- Arguments passed individually.

```js
function greet(greeting) {
  console.log(greeting + ", " + this.name);
}
const person = { name: "Alice" };
greet.call(person, "Hi"); // Hi, Alice
```

#### `apply()`

- Same as `call` but arguments passed as an array.

```js
greet.apply(person, ["Hello"]); // Hello, Alice
```

#### `bind()`

- Returns a new function with `this` bound. Does not call it immediately.

```js
const greetPerson = greet.bind(person);
greetPerson("Hey"); // Hey, Alice
```

---

### 4. What is JSON and its Common Operations?

**JSON (JavaScript Object Notation)** is a lightweight format to store and exchange data.

#### Features:

- Text format, easy to read/write.
- Key-value pairs, with keys as strings.
- Used widely in APIs and configuration.

#### Operations:

- ``: Converts object to JSON string.

```js
const obj = { name: "Alice" };
const str = JSON.stringify(obj); // '{"name":"Alice"}'
```

- ``: Converts JSON string to object.

```js
const parsed = JSON.parse(str); // { name: "Alice" }
```

---

### 5. What is the purpose of the array `slice()` method?

- Returns a **copy** of a portion of an array.
- **Does not modify** the original array.

**Syntax:** `array.slice(start, end)` (end is exclusive)

**Example:**

```js
const arr = [10, 20, 30, 40];
const sliced = arr.slice(1, 3); // [20, 30]
```

Use cases:

- Cloning arrays: `arr.slice()`
- Extracting sub-arrays

---

### 6. What is the purpose of the array `splice()` method?

- Used to **add/remove/replace** elements in the array.
- **Modifies** the original array.

**Syntax:** `array.splice(start, deleteCount, item1, item2, …)`

**Example:**

```js
const arr = [1, 2, 3, 4];
arr.splice(1, 2); // removes 2 elements at index 1 → [2, 3]
console.log(arr); // [1, 4]
```

**Insert Example:**

```js
arr.splice(1, 0, "a", "b"); // [1, "a", "b", 4]
```

---

### 7. What is the Difference Between `slice()` and `splice()`?

| Feature      | `slice()`                   | `splice()`                    |
| ------------ | --------------------------- | ----------------------------- |
| Effect       | Non-destructive (no change) | Destructive (modifies array)  |
| Purpose      | Extract sub-array           | Add, remove, replace elements |
| Return Value | New sub-array               | Removed elements              |

**Example:**

```js
let arr = [1, 2, 3, 4];
let sliced = arr.slice(1, 3); // [2, 3], arr is unchanged
let spliced = arr.splice(1, 2); // arr is now [1, 4]
```

---

### 8. How do you compare Object and Map?

| Feature     | Object                     | Map                             |
| ----------- | -------------------------- | ------------------------------- |
| Key types   | Strings, Symbols only      | Any data type                   |
| Key order   | Not guaranteed             | Insertion order maintained      |
| Iteration   | Not iterable by default    | Easily iterable with `for...of` |
| Size        | Use `Object.keys().length` | Use `.size`                     |
| Performance | Slower in large datasets   | Optimized for frequent updates  |

Use `Map` when:

- You need any data type as key.
- You require ordered entries.
- You want fast frequent updates.

---

### 9. What is the difference between `==` and `===`?

#### `==` (Loose Equality):

- Compares **values only**.
- Performs **type coercion**.

```js
"5" == 5 // true
null == undefined // true
```

#### `===` (Strict Equality):

- Compares **value and type**.
- No type coercion.

```js
"5" === 5 // false
null === undefined // false
```

**Best Practice:** Always use `===` to avoid unexpected bugs due to coercion.

---

### 10. What are Lambda Expressions or Arrow Functions?

Arrow functions provide a **concise syntax** for writing functions. Introduced in ES6.

**Syntax:**

```js
const add = (a, b) => a + b;
```

**Key Features:**

- Shorter syntax
- **No own **`` – uses lexical `this`
- Cannot be used as constructors
- Good for short functions, callbacks

**Example:**

```js
const nums = [1, 2, 3];
const squares = nums.map(n => n * n); // [1, 4, 9]
```

Avoid arrow functions in:

- Class methods needing `this`
- Event handlers when `this` is required

---

These are essential JavaScript concepts frequently asked in interviews. Understanding them deeply will help both in technical interviews and writing robust JavaScript code.

