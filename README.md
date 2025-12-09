
## 📑 Table of Contents
- [LexicalStructure](#LexicalStructure)
- [Expressions](#Expressions)
- [DataTypes](#DataTypes)
- [Variables](#Variables)


## LexicalStructure

JavaScript's **lexical structure** describes the basic building blocks of the language — the rules for writing code, forming tokens, naming variables, writing comments, and more. This document explains each part clearly.

---

## 1. What is Lexical Structure?

Lexical structure defines **how JavaScript source code is read and broken into tokens**. It includes:

* Character set
* Case sensitivity
* Whitespace
* Line terminators
* Comments
* Literals
* Identifiers & keywords
* Operators & punctuators

---

## 2. Character Set

JavaScript uses the **Unicode** character set.

* This means it supports characters from almost all languages.
* Variable names can include Unicode letters — even emojis (not recommended in production).

```js
let မြန်မာ = "Hello";
let 🚀 = 10;
```

---

## 3. Case Sensitivity

JavaScript is **case-sensitive**.

```js
let name = "A";
let Name = "B"; // different variable
```

Keywords are also case-sensitive.

---

## 4. Whitespace

Whitespace includes spaces, tabs, and newlines.

* JavaScript generally **ignores whitespace**, except in specific cases.

Example:

```js
let x = 10;
let  y    =    20;
```

Both are valid.

---

## 5. Line Terminators

Line terminators are characters such as:

* `\n` (newline)
* `\r` (carriage return)

They can affect automatic semicolon insertion (ASI), so be careful.

Example (dangerous):

```js
return
  5; // returns undefined due to ASI
```

---

## 6. Comments

### Single-line comment

```js
// This is a comment
```

### Multi-line comment

```js
/*
  This is a multi-line comment
*/
```

**Note:** Comments do not nest.

---

## 7. Identifiers

Identifiers are names for:

* variables
* functions
* classes

Rules:

* Must start with: letter, `_`, `$`
* After first char: digits are allowed.

Valid:

```js
let _value;
let $item;
let user123;
```

Invalid:

```js
let 1user; // cannot start with digit
```

---

## 8. Keywords

These words have special meaning and cannot be used as identifiers.
Examples:

```
break, case, class, const, continue, debugger, default,
delete, do, else, export, extends, finally, for, function,
if, import, in, instanceof, let, new, return, super,
switch, this, throw, try, typeof, var, void, while, with, yield
```

---

## 9. Literals

Literals are fixed values appearing directly in code.

### Number literals

```js
let a = 10;
let b = 3.14;
let hex = 0xFF;
let binary = 0b1010;
```

### String literals

```js
let s1 = "hello";
let s2 = 'world';
let s3 = `template literal`;
```

### Boolean literals

```js
true, false
```

### Null & Undefined

```js
null;
undefined;
```

---

## 10. Operators & Punctuators

These include:

* `+ - * / %`
* `= += -= *=`
* `== === != !==`
* `{ } [ ] ( )`
* `, ; . ? :`

JavaScript treats these as tokens during lexical scanning.

---

## 11. Automatic Semicolon Insertion (ASI)

JavaScript automatically inserts semicolons in some cases.
This can cause unexpected behavior.

Bad:

```js
let x = 5
let y = 10
(x + y).toString() // treated as function call
```

Recommended:

* Always use semicolons
  or
* Follow JS formatting rules carefully.

---

## 12. Escape Sequences

Used inside strings:

* `\n` → newline
* `\t` → tab
* `\"` → double-quote
* `\\` → backslash

Example:

```js
let text = "Hello\nWorld";
```

---

## 13. Unicode Escapes

Identifiers may include Unicode escapes:

```js
let \u006Eame = "John"; // same as "name"
```

String Unicode:

```js
"\u{1F600}"; // 😀
```

---

## Summary

JavaScript lexical structure defines **how source code is read**, including:

* Unicode support
* Case sensitivity
* Whitespace handling
* Comments
* Identifiers & keywords
* Literals
* Operators & punctuation
* ASI behavior

Understanding these rules helps you write cleaner and more predictable JavaScript.

---


# Expressions

JavaScript **expressions** are pieces of code that produce a value. They are the building blocks of statements and logic in JavaScript.



---

## 1. What Is an Expression?

An **expression** is any valid unit of code that **evaluates to a value**.

Examples:

```js
5          // number expression
"Hi"       // string expression
x + y      // arithmetic expression
sayHello() // function call expression
```

---

## 2. Primary Expressions

These are the simplest expressions that represent literal values or keywords.

### Examples:

```js
42
true
"hello"
null
undefined
this
```

### Identifier Reference

```js
name;
count;
```

---

## 3. Object & Array Initializer Expressions

### Object Literal

```js
let user = {
  name: "Aye",
  age: 20,
};
```

### Array Literal

```js
let numbers = [1, 2, 3];
```

---

## 4. Arithmetic Expressions

Perform mathematical operations.

```js
x + y
x - y
x * 2
x / 10
x % 3
x ** 2
```

---

## 5. String Expressions

Involves string concatenation or template literals.

```js
"Hello" + " World"
`User: ${username}`
```

---

## 6. Logical Expressions

Use `&&`, `||`, and `!`.

```js
true && false
isLoggedIn || hasToken
!isAdmin
```

Logical operators return **values**, not booleans only.

```js
"A" && "B"  // "B"
"A" || "B"  // "A"
```

---

## 7. Comparison Expressions

```js
x > y
x < y
x >= y
x === y
x !== y
```

They return `true` or `false`.

---

## 8. Assignment Expressions

These assign values and return the assigned value.

```js
x = 10
x += 5
x -= 2
x *= 3
```

Example:

```js
let a;
console.log(a = 5); // prints 5
```

---

## 9. Function Call Expressions

Calling a function is an expression.

```js
doSomething()
alert("Hi")
sum(10, 20)
```

Even methods:

```js
user.getName()
```

---

## 10. Optional Chaining Expression

Safely access nested properties.

```js
user?.address?.city
```

---

## 11. Member Access Expressions

Access properties:

### Dot notation

```js
user.name
```

### Bracket notation

```js
user["name"]
```

---

## 12. Conditional (Ternary) Expression

Short "if...else" that returns a value.

```js
let status = age >= 18 ? "Adult" : "Child";
```

---

## 13. Arrow Function Expressions

Functions used as expressions.

```js
const add = (a, b) => a + b;
```

Arrow function without body braces implicitly returns:

```js
const double = x => x * 2;
```

---

## 14. Spread & Rest Expressions

### Spread

```js
let newArr = [...oldArr];
```

### Rest

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```

---

## 15. Comma Operator Expression

Evaluates multiple expressions but returns the last one.

```js
let x = (1, 2, 3); // x = 3
```

Rarely used.

---

## 16. `new` Expression

Used to create instances.

```js
let date = new Date();
let user = new User("Aye");
```

---

## 17. `typeof`, `void`, and `delete` Expressions

### typeof

```js
typeof 123 // "number"
```

### void

```js
void 0 // undefined
```

### delete

```js
delete obj.key
```

---

## 18. Await Expression

Used in async functions.

```js
let data = await fetch("/api");
```

---

## 19. Grouping Expressions

Control evaluation order.

```js
(2 + 3) * 4
```

---

## Summary

JavaScript expressions:

* Always produce a **value**
* Can be simple (like `5`) or complex (like `user?.profile?.name ?? "Unknown"`)
* Form the core of JavaScript logic

Understanding expressions helps you write more powerful and flexible code.

---

# DataTypes

JavaScript has a flexible and dynamic type system. Every value in JavaScript belongs to a **data type**, and understanding them is essential for writing clean, predictable code.

---

## 1. Overview of Data Types

JavaScript has **8 main data types**:

### **Primitive Data Types** (7 types)

1. **Number**
2. **String**
3. **Boolean**
4. **Undefined**
5. **Null**
6. **Symbol**
7. **BigInt**

### **Non‑Primitive Data Type** (1 type)

8. **Object**

---

# 2. Primitive Data Types

Primitive values:

* are **immutable**
* compared by **value**
* stored directly in memory

---

## 2.1 Number

Represents both integers and floating‑point numbers.

```js
let age = 18;
let price = 19.99;
let infinity = Infinity;
let notNumber = NaN;
```

JavaScript does **not** have separate types for int, float, double.

---

## 2.2 String

Represents text.

```js
let name = "Aye";
let message = 'Hello';
let greeting = `Hi ${name}`; // template literal
```

---

## 2.3 Boolean

Represents logical values.

```js
let isLoggedIn = true;
let hasToken = false;
```

Common Boolean operations:

```js
true && false
true || false
!true
```

---

## 2.4 Undefined

A variable that has been declared but not assigned.

```js
let x;
console.log(x); // undefined
```

---

## 2.5 Null

Represents an **intentional absence of value**.

```js
let user = null;
```

Note:

```js
typeof null; // "object" (JS historical bug)
```

---

## 2.6 Symbol (ES6)

Unique and immutable values, often used as object keys.

```js
let id = Symbol("id");
let obj = {
  [id]: 123,
};
```

---

## 2.7 BigInt (ES2020)

Used for very large integers.

```js
let big = 12345678901234567890n;
let sum = big + 10n;
```

BigInts cannot mix with normal numbers:

```js
10 + 10n; // ❌ error
```

---

# 3. Non‑Primitive Data Type

## 3.1 Object

Objects store key‑value pairs.

```js
let user = {
  name: "Aye",
  age: 20,
};
```

Objects include:

* arrays
* functions
* dates
* regex
* maps
* sets

Everything that is **not primitive** is an **object**.

---

# 4. Special Object Types

## 4.1 Array

Ordered list of values.

```js
let arr = [1, 2, 3];
```

---

## 4.2 Function

Functions are objects with callable behavior.

```js
function greet() {
  return "Hello";
}
```

---

## 4.3 Date

Represents date and time.

```js
let now = new Date();
```

---

## 4.4 Map

Stores key‑value pairs with any key type.

```js
let map = new Map();
map.set("name", "Aye");
```

---

## 4.5 Set

Stores unique values.

```js
let set = new Set([1, 2, 2, 3]); // {1,2,3}
```

---

# 5. Dynamic Typing

JavaScript is **dynamically typed**, meaning variables can change type at runtime.

```js
let x = 10;
x = "ten";
```

---

# 6. Type Checking

### typeof operator

```js
typeof 10;        // "number"
typeof "hi";     // "string"
typeof true;      // "boolean"
typeof undefined; // "undefined"
typeof null;      // "object" (bug)
typeof {};        // "object"
typeof [];        // "object"
typeof function(){}; // "function"
```

---

# 7. Difference Between Primitive & Object

| Feature     | Primitive            | Object                |
| ----------- | -------------------- | --------------------- |
| Storage     | Value                | Reference             |
| Mutable?    | No                   | Yes                   |
| Compared by | Value                | Reference             |
| Examples    | `10`, `"hi"`, `true` | `{}`, `[]`, functions |

Example:

```js
let a = { x: 1 };
let b = { x: 1 };
a === b; // false (different references)
```

---

# 8. Type Conversion

### Implicit Conversion (Coercion)

```js
"5" - 1  // 4
"5" + 1  // "51"
```

### Explicit Conversion

```js
Number("5")
String(123)
Boolean(1)
```

---

# Summary

JavaScript data types include:

* **7 primitive types**: Number, String, Boolean, Undefined, Null, Symbol, BigInt
* **1 non‑primitive type**: Object
* JavaScript is **dynamically typed**
* Primitive values are simple and immutable
* Objects are complex and mutable

Understanding data types helps prevent bugs and write cleaner, more predictable code.

---


# Variables

Variables are one of the most fundamental parts of JavaScript. They allow you to store, update, and reuse values inside your programs.

---

## 1. What Is a Variable?

A **variable** is a named container for storing data.

```js
let message = "Hello World";
```

---

## 2. Variable Declaration Keywords

JavaScript has **3 ways** to declare variables:

### ✔ `var`

### ✔ `let`

### ✔ `const`

Each behaves differently.

---

## 3. `let`

Introduced in ES6, used for **block-scoped** variables.

```js
let age = 20;
age = 21; // reassign allowed
```

### Features:

* Block scoped `{}`
* Can be reassigned
* Cannot be redeclared in the same scope

Example:

```js
if (true) {
  let x = 10;
}
console.log(x); // ❌ Error (x is block-scoped)
```

---

## 4. `const`

Also block-scoped, but **cannot be reassigned**.

```js
const PI = 3.14;
// PI = 3.15; ❌ Error
```

### Important:

`const` does **not** make objects immutable.

```js
const user = { name: "Aye" };
user.name = "Ko"; // ✔ allowed
```

You cannot reassign a new object:

```js
user = {}; // ❌ not allowed
```

---

## 5. `var`

Function-scoped and older keyword.

```js
var name = "Aye";
```

### Problems with `var`:

* Not block scoped
* Can be redeclared
* Causes unexpected behavior due to **hoisting**

Example:

```js
if (true) {
  var x = 10;
}
console.log(x); // ✔ 10 (var ignores block scope)
```

Use `let` or `const` instead.

---

## 6. Scope

Scope determines **where a variable can be used**.

### Types:

1. **Block Scope** (`let`, `const`)
2. **Function Scope** (`var`)
3. **Global Scope**

Example:

```js
let globalVar = "I am global"; // Global scope

function exampleFunction() {
  var functionVar = "I am function-scoped"; // Function scope (var)

  if (true) {
    let blockVar = "I am block-scoped"; // Block scope (let)
    console.log(blockVar); // Accessible here
  }

  // console.log(blockVar); // Error: blockVar is not defined here
  console.log(functionVar); // Accessible here
}

exampleFunction();
console.log(globalVar); // Accessible here
// console.log(functionVar); // Error: functionVar is not defined here
```

---

## 7. Hoisting

Hoisting means declarations are moved to the top of their scope.

### `var` is hoisted with **undefined** value:

```js
console.log(x); // undefined
var x = 10;
```

### `let` and `const` are hoisted but in **Temporal Dead Zone (TDZ)**:

```js
console.log(y); // ❌ Error
let y = 10;
```

---

## 8. Initialization vs Declaration

```js
let x;       // declaration
x = 5;       // initialization

let y = 10;  // declared + initialized
```

---

## 9. Naming Variables

Variable names must follow rules.

### Valid:

```js
let name;
let _counter;
let $money;
let age2;
```

### Invalid:

```js
let 1age;   // cannot start with number
let @name;  // symbols not allowed
```

### Best Practices:

* Use camelCase → `userName`
* Use descriptive names → `totalPrice`
* Constants in ALL_CAPS → `MAX_USERS`

---

## 10. `let` vs `const` vs `var`

| Feature    | var             | let   | const |
| ---------- | --------------- | ----- | ----- |
| Scope      | Function        | Block | Block |
| Redeclare? | ✔ Yes           | ❌ No  | ❌ No  |
| Reassign?  | ✔ Yes           | ✔ Yes | ❌ No  |
| Hoisting   | Yes (undefined) | TDZ   | TDZ   |

### Recommended:

* Use **const** by default
* Use **let** when value will change
* Avoid **var**

---

## 11. Global Variables

Variables declared outside functions.

```js
let a = 10; // global
```

Global variables can cause bugs — use only when needed.

---

## 12. Reassignment Examples

```js
let count = 1;
count = 2; // ✔ allowed

const PI = 3.14;
PI = 3.2; // ❌ not allowed
```

---

## Summary

JavaScript variables:

* Store values for reuse
* Declared using `var`, `let`, or `const`
* `let` & `const` are block-scoped
* `var` is function-scoped and outdated
* `const` prevents reassignment
* Hoisting affects how variables behave

Understanding variables helps you control data flow and avoid bugs.

---
