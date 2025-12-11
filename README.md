
## 📑 Table of Contents
- [LexicalStructure](#LexicalStructure)
- [Expressions](#Expressions)
- [DataTypes](#DataTypes)
- [Variables](#Variables)
- [Operators](#Operators)
- [Conditions](#Conditions)
- [Loops](#Loops)
- [Functions](#Functions)
- [Objects](#Objects)
- [Arrays](#Arrays)
- [Asynchronous](#Asynchronous-JavaScript)
- [TypeCasting](#TypeCasting )

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

Hoisting ဆိုတာ
➡️ JavaScript engine က code run မလုပ်ခင်
➡️ variable declarations (var, let, const)
➡️ function declarations
တွေကို memory ထဲကို အရင် ထားသွားတဲ့ behavior ကို ဆိုလိုတာပါ။

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



# Operators


## **1. What Are Operators?**

Operators are symbols that tell JavaScript to perform some action (calculations, comparisons, assignments, logic, etc.).

Example:

```js
let x = 10 + 5;
```

Here:

* `=` is an **assignment operator**
* `+` is an **arithmetic operator**

---

## **2. Types of Operators**

JavaScript has several categories of operators:

1. **Arithmetic Operators**
2. **Assignment Operators**
3. **Comparison Operators**
4. **Logical Operators**
5. **Unary Operators**
6. **Ternary Operator**
7. **String Operators**
8. **Bitwise Operators**
9. **Type Operators** (`typeof`, `instanceof`)
10. **Optional Chaining & Nullish Coalescing Operators**

---

## **3. Arithmetic Operators**

| Operator | Name                | Example        |
| -------- | ------------------- | -------------- |
| `+`      | Addition            | `5 + 2` → `7`  |
| `-`      | Subtraction         | `5 - 2` → `3`  |
| `*`      | Multiplication      | `5 * 2` → `10` |
| `/`      | Division            | `10 / 2` → `5` |
| `%`      | Modulus (remainder) | `5 % 2` → `1`  |
| `**`     | Exponentiation      | `2 ** 3` → `8` |
| `++`     | Increment           | `x++`          |
| `--`     | Decrement           | `x--`          |

Example:

```js
let a = 10;
a++;
console.log(a); // 11
```

---

## **4. Assignment Operators**

| Operator | Meaning             | Example              |
| -------- | ------------------- | -------------------- |
| `=`      | Assign              | `x = 10`             |
| `+=`     | Add and assign      | `x += 5` (x = x + 5) |
| `-=`     | Subtract and assign | `x -= 5`             |
| `*=`     | Multiply and assign | `x *= 5`             |
| `/=`     | Divide and assign   | `x /= 5`             |
| `%=`     | Modulus and assign  | `x %= 5`             |
| `**=`    | Power and assign    | `x **= 2`            |

---

## **5. Comparison Operators**

These return **true** or **false**.

| Operator | Meaning          | Example             |
| -------- | ---------------- | ------------------- |
| `==`     | Equal (loose)    | `5 == "5"` → true   |
| `===`    | Strict equal     | `5 === "5"` → false |
| `!=`     | Not equal        | `5 != 3`            |
| `!==`    | Strict not equal | `5 !== "5"`         |
| `>`      | Greater than     | `10 > 5`            |
| `<`      | Less than        | `5 < 10`            |
| `>=`     | Greater or equal | `10 >= 10`          |
| `<=`     | Less or equal    | `5 <= 5`            |

Example:

```js
console.log(5 === "5"); // false
```

---

## **6. Logical Operators**
```js
| Operator | Meaning | Example                   |   
| -------- | ------- | ------------------------- | 
| `&&`     | AND     | `true && false` → `false` |    
| `||`     | OR      | `true || false`→`true`    |         
| `!`      | NOT     | `!true` → `false`         |      

```
Example:

```js
let isLoggedIn = true;
let isAdmin = false;
console.log(isLoggedIn && isAdmin); // false
```

---

## **7. Unary Operators**

| Operator | Meaning                         |
| -------- | ------------------------------- |
| `typeof` | Returns data type               |
| `void`   | Evaluates but returns undefined |
| `delete` | Removes object property         |
| `+`      | Convert to number               |
| `-`      | Convert to negative number      |

Example:

```js
console.log(typeof 123); // "number"
```

---

## **8. Ternary Operator** (Conditional Operator)

Shorthand for `if/else`.

```js
condition ? valueIfTrue : valueIfFalse;
```

Example:

```js
let age = 18;
let msg = age >= 18 ? "Adult" : "Minor";
console.log(msg);
```

---

## **9. String Operator**

The `+` operator is used for string concatenation.

```js
let name = "Toe" + "Wai";
console.log(name); // "ToeWai"
```

---

## **10. Nullish Coalescing Operator (`??`)**

Returns the right-hand value when the left side is `null` or `undefined`.

```js
let user;
console.log(user ?? "Guest"); // Guest
```

---

## **11. Optional Chaining Operator (`?.`)**

Avoids errors when accessing properties of `undefined` or `null`.

```js
let user = {};
console.log(user.address?.street); // undefined, no error
```

---

## **12. Bitwise Operators**

Advanced topic — used for low-level operations.
```js
| Operator | Meaning               |    
| -------- | --------------------- | 
| `&`      | AND                   |    
|  ||      | OR                    |  
| `^`      | XOR                   |    
| `~`      | NOT                   |    
| `<<`     | Left shift            |    
| `>>`     | Right shift           |    
| `>>>`    | Zero-fill right shift |    
```
---

## **13. Operator Precedence (Which Runs First?)**

Example:

```js
2 + 3 * 4; // 14 (because * runs before +)
```

Shortcut:

* `()` parentheses highest
* Then unary (`!`, `typeof`)
* Then `* / %`
* Then `+ -`
* Then comparisons
* Then logical
* Last: assignment

---





# Conditions 

A complete guide to how decisions are made in JavaScript — using `if`, `else`, `switch`, ternary, truthy/falsy, and more.

---

## **1. What Are Conditions?**

Conditions allow JavaScript to make decisions based on **true/false** results.

Example:

```js
let age = 18;
if (age >= 18) {
  console.log("You are an adult");
}
```

---

## **2. Types of Conditional Statements**

JavaScript supports:

1. `if` statement
2. `if...else` statement
3. `else if` chain
4. `switch` statement
5. Ternary operator (`? :`)
6. `&&` and `||` short‑circuit conditions
7. Optional chaining (`?.`) with conditions

---

## **3. The `if` Statement**

Runs code only when the condition is **true**.

```js
if (condition) {
  // code
}
```

Example:

```js
let score = 80;
if (score > 50) {
  console.log("Pass");
}
```

---

## **4. `if...else` Statement**

Runs one block if true, another if false.

```js
if (condition) {
  // true block
} else {
  // false block
}
```

Example:

```js
let isOnline = false;
if (isOnline) {
  console.log("User is online");
} else {
  console.log("User is offline");
}
```

---

## **5. `else if` Chain**

Checks multiple conditions one by one.

```js
if (temperature > 30) {
  console.log("Hot");
} else if (temperature > 20) {
  console.log("Warm");
} else {
  console.log("Cold");
}
```

---

## **6. `switch` Statement**

Used when checking one value against many possible cases.

```js
switch (day) {
  case "Mon":
    console.log("Work day");
    break;
  case "Sat":
    console.log("holiday");
  case "Sun":
    console.log("Weekend");
    break;
  default:
    console.log("Unknown day");
}
```

### Why use `switch`?

* Cleaner when many `else if` conditions
* Great for checking a single variable

---

## **7. Ternary Operator (`? :`)**

Short version of `if...else`.

```js
condition ? valueIfTrue : valueIfFalse;
```

Example:

```js
let age = 18;
let message = age >= 18 ? "Adult" : "Minor";
console.log(message);
```

Best used for simple decisions.

---

## **8. Truthy and Falsy Values**

JavaScript treats some values as **true** or **false** automatically.

### Falsy values:

* `false`
* `0`
* `""` (empty string)
* `null`
* `undefined`
* `NaN`

Everything else is **truthy**.

Example:

```js
if ("") console.log("This won't run");
if ("hello") console.log("This will run");
```

---

## **9. Logical Operators in Conditions**

### `&&` (AND)

Runs only if both conditions are true.

```js
if (isLoggedIn && isAdmin) {
  console.log("Welcome Admin");
}
```

### `||` (OR)

Runs if at least one condition is true.

```js
if (day === "Sat" || day === "Sun") {
  console.log("Weekend");
}
```

### `!` (NOT)

Reverses a boolean.

```js
if (!isOnline) {
  console.log("Offline");
}
```

---

## **10. Optional Chaining in Conditions (`?.`)**

Avoids errors when checking nested properties.

```js
if (user?.address?.city) {
  console.log("City found");
}
```

---

## **11. Combining Multiple Conditions**

Example:

```js
let age = 20;
let hasID = true;

if (age >= 18 && hasID) {
  console.log("You may enter");
}
```

---

## **12. Common Mistakes**

### Using `=` instead of `==` or `===`

```js
if (x = 5) { } // WRONG
```

This assigns, not compares.

Correct:

```js
if (x === 5) { }
```

### Forgetting `break` in switch

```js
switch(x) {
  case 1:
    console.log("One");
  case 2:
    console.log("Two"); // Both run ❌
}
```

---

## **13. Summary**

Use conditions to:

* Make decisions
* Control program flow
* Validate data
* React to user input

Tools for conditions:

* `if`, `else`, `else if`
* `switch`
* Ternary operator
* Logical operators
* Truthy/falsy evaluation

---


#  Loops

A complete guide to loops in JavaScript — how to repeat actions, iterate data, and control flow efficiently.

---

## **1. What Are Loops?**

Loops allow you to repeat code multiple times — automatically.

Example:

```js
for (let i = 1; i <= 3; i++) {
  console.log(i);
}
```

Output:

```
1
2
3
```

---

## **2. Types of Loops in JavaScript**

JavaScript supports several loop types:

1. **for** loop
2. **while** loop
3. **do...while** loop
4. **for...of** loop (iterate arrays, strings, etc.)
5. **for...in** loop (iterate object keys)
6. Array iteration methods (not exactly loops but commonly used)

   * `forEach`
   * `map`
   * `filter`
   * `reduce`

---

## **3. The `for` Loop**

Most common and powerful loop.

### Syntax:

```js
for (initialization; condition; update) {
  // code
}
```

### Example:

```js
for (let i = 0; i < 5; i++) {
  console.log("Number:", i);
}
```

---

## **4. The `while` Loop**

Runs as long as the condition is **true**.

```js
let i = 0;
while (i < 3) {
  console.log(i);
  i++;
}
```

Use when you don't know how many times to loop.

---

## **5. The `do...while` Loop**

Runs **at least once**, even if the condition is false.

```js
let i = 5;
do {
  console.log(i);
  i++;
} while (i < 3);
```

---

## **6. The `for...of` Loop**

Used for iterating **iterables**:

* Arrays
* Strings
* Maps
* Sets

### Example:

```js
let colors = ["red", "green", "blue"];
for (const c of colors) {
  console.log(c);
}
```

---

## **7. The `for...in` Loop**

Used to iterate **object keys**.

```js
let user = {
  name: "Toe",
  age: 18,
};

for (const key in user) {
  console.log(key, user[key]);
}
```

⚠️ Avoid using `for...in` for arrays.

---

## **8. Array Iteration Methods**

These are not loops but often replace loops.

### **forEach** (loop through each item)

```js
[1, 2, 3].forEach(n => console.log(n));
```

### **map** (returns new array)

```js
let doubled = [1, 2, 3].map(n => n * 2);
```

### **filter** (filters values)

```js
let even = [1, 2, 3, 4].filter(n => n % 2 === 0);
```

### **reduce** (accumulates values)

```js
let sum = [1, 2, 3].reduce((a, b) => a + b, 0);
```

---

## **9. Loop Control: `break` and `continue`**

### **break** → stops the loop completely.

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) break;
  console.log(i);
}
```

### **continue** → skips current iteration.

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
```

---

## **10. Infinite Loops (Be Careful!)**

```js
while (true) {
  console.log("This never stops");
}
```

Make sure your loop condition eventually becomes **false**.

---

## **11. Nested Loops**

Loop inside a loop.

```js
for (let i = 1; i <= 2; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(i, j);
  }
}
```

---

## **12. When to Use Which Loop?**

| Loop Type    | Best Use                     |
| ------------ | ---------------------------- |
| `for`        | Known number of iterations   |
| `while`      | Unknown number of iterations |
| `do...while` | Run at least once            |
| `for...of`   | Arrays, strings, iterables   |
| `for...in`   | Object keys                  |
| `forEach`    | Simple iteration (no break)  |
| `map`        | Transform array              |
| `filter`     | Filter array                 |
| `reduce`     | Calculate a single value     |

---

## **13. Common Mistakes**

❌ Forgetting to update the counter
❌ Creating infinite loops
❌ Using `for...in` for arrays
❌ Expecting `break` inside `forEach` (it does not work)

---

## **14. Summary**

Loops help you:

* Repeat actions
* Work with collections
* Automate repetitive tasks
* Process arrays/objects

You now know:

* `for`, `while`, `do...while`
* `for...of`, `for...in`
* Array iteration methods
* break/continue

---

#  Functions

A complete guide to JavaScript functions — definitions, types, parameters, return values, arrow functions, scopes, closures, and more.

---

## **1. What Is a Function?**

A function is a reusable block of code designed to perform a task.

Example:

```js
function greet() {
  console.log("Hello!");
}
```

---

## **2. Why Use Functions?**

Functions help you:

* Avoid repeating code
* Organize logic
* Make code cleaner
* Create modular programs
* Return values from operations

---

## **3. Function Declaration**

Also called a **named function**.

```js
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
```

### Features:

* Hoisted (usable before declaration)

---

## **4. Function Expression**

Function stored in a variable.

```js
const multiply = function (a, b) {
  return a * b;
};
```

### Features:

* Not hoisted
* Can be anonymous or named

---

## **5. Arrow Functions**

Short syntax introduced in ES6.

```js
const greet = () => {
  console.log("Hi!");
};
```

Short single-line form:

```js
const square = n => n * n;
```

### Differences from normal functions:

* No `this` binding
* No `arguments` object
* Great for callbacks

---

## **6. Parameters vs Arguments**

**Parameters** → variables written in function definition
**Arguments** → values passed when calling

Example:

```js
function hello(name) { // parameter
  console.log("Hello", name);
}

hello("Toe"); // argument
```

---

## **7. Default Parameters**

```js
function greet(name = "Guest") {
  console.log("Hello", name);
}
```

---

## **8. Rest Parameters (...args)**

Used when the number of arguments is unknown.

```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

---

## **9. Return Statement**

Functions can return a value.

```js
function add(a, b) {
  return a + b;
}
```

If no `return` → returns `undefined`.

---

## **10. Anonymous Functions**

Functions without a name.

Used in callbacks:

```js
setTimeout(function () {
  console.log("Done");
}, 1000);
```

---

## **11. Callback Functions**

A function passed as an argument to another function.

```js
function process(callback) {
  callback();
}

process(() => console.log("Running!"));
```

---

## **12. Higher-Order Functions**

Functions that:

* Take another function as an argument, or
* Return a function

Example:

```js
function createMultiplier(x) {
  return function (y) {
    return x * y;
  };
}

const double = createMultiplier(2);
console.log(double(5)); // 10
```

---

## **13. Function Scope**

Functions create their own scope.

```js
function test() {
  let x = 10;
}
// x is not accessible here
```

---

## **14. Block Scope vs Function Scope**

* `let` & `const` → block scoped
* `var` → function scoped

```js
if (true) {
  let a = 10; // block
  var b = 20; // function
}
// b is still accessible
```

---

## **15. Closures**

A closure is when a function remembers variables from its outer scope.

```js
function outer() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
```

Closures are used in:

* Private variables
* Factory functions
* Module patterns

---

## **16. Named vs Anonymous Functions**

### Named function

```js
function sayHi() {}
```

### Anonymous function

```js
const sayHi = function() {}
```

---

## **17. Immediately Invoked Function Expression (IIFE)**

Runs immediately after creation.

```js
(function () {
  console.log("I am an IIFE");
})();
```

---

## **18. Pure vs Impure Functions**

### Pure

* No side effects
* Same input → same output

```js
function add(a, b) {
  return a + b;
}
```

### Impure

```js
let x = 1;
function addToX(y) {
  x += y; // modifies outside variable
}
```

---

## **19. Functions as Objects**

Functions in JavaScript are **first-class citizens**:

* Can be stored in variables
* Can be passed as arguments
* Can be returned from functions

---

## **20. Summary**

You learned:

* Function declarations & expressions
* Arrow functions
* Parameters, arguments, return values
* Scope & closures
* Callbacks & higher-order functions
* IIFE, pure functions, rest parameters

Functions are the foundation of JavaScript. Mastering them = mastering JS.

---



#  Objects 

JavaScript **objects** are one of the most important parts of the language. They let you store data in key-value pairs and model real-world entities.

---

## 📌 1. What Is an Object?

An **object** is a collection of related data and functions.

```js
const user = {
  name: "Alex",
  age: 18,
  isStudent: true,
};
```

* **Keys** → `name`, `age`, `isStudent`
* **Values** → "Alex", 18, true

---

## 📌 2. Creating Objects

### **A. Object Literal (most common)**

```js
const car = {
  brand: "Toyota",
  model: "Vios",
  year: 2020
};
```

### **B. Using `new Object()`**

```js
const obj = new Object();
obj.x = 10;
obj.y = 20;
```

### **C. Using a Constructor Function**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const p1 = new Person("John", 20);
```

### **D. Using Classes (ES6)**

```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const u1 = new User("Alice", 25);
```

---

## 📌 3. Accessing Object Properties

### **Dot Notation**

```js
console.log(user.name);
```

### **Bracket Notation**

```js
console.log(user["age"]);
```

Useful when:

* key contains spaces
* key is dynamic

---

## 📌 4. Adding / Updating Properties

### **Add new property**

```js
user.email = "alex@example.com";
```

### **Update existing property**

```js
user.age = 19;
```

---

## 📌 5. Deleting Properties

```js
delete user.isStudent;
```

---

## 📌 6. Methods (Functions inside Objects)

```js
const person = {
  name: "Leo",
  greet() {
    console.log(`Hi, I am ${this.name}`);
  }
};

person.greet();
```

`this` refers to the current object.

---

## 📌 7. Nested Objects

```js
const student = {
  name: "Nyein",
  address: {
    city: "Yangon",
    township: "Hlaing"
  }
};
```

---

## 📌 8. Looping Through Objects

### **for…in**

```js
for (let key in user) {
  console.log(key, user[key]);
}
```

### **Object.keys()**

```js
console.log(Object.keys(user));
```

### **Object.values()**

```js
console.log(Object.values(user));
```

### **Object.entries()**

```js
console.log(Object.entries(user));
```

---

## 📌 9. Copying Objects

### **Shallow Copy**

```js
const copy = { ...user };
```

### **Deep Copy**

```js
const deepCopy = JSON.parse(JSON.stringify(user));
```

---

## 📌 10. Object Destructuring

```js
const { name, age } = user;
console.log(name, age);
```

---

## 📌 11. Optional Chaining (?.)

Prevents errors when a property might be missing.

```js
console.log(student.address?.city);
```

---

## 📌 12. Useful Built-in Methods

* `Object.keys(obj)` → returns keys
* `Object.values(obj)` → returns values
* `Object.entries(obj)` → returns key/value pairs
* `Object.assign(target, source)` → merges objects

---

## 📌 13. Real-Life Example

```js
const product = {
  id: 1,
  name: "Laptop",
  price: 980000,
  specs: {
    cpu: "i5",
    ram: "16GB"
  },
  getInfo() {
    return `${this.name} - ${this.price} Ks`;
  }
};
```

---

## 📌 Summary

* Objects store data in key/value pairs
* Methods = functions inside objects
* Dot & bracket notation for access
* Use destructuring for cleaner code
* Objects are used everywhere in JS (React, APIs, Node.js)

---

# Arrays

## 📌 What is an Array?

An **array** is a special data structure in JavaScript used to store **ordered collections** of values.

```js
const numbers = [1, 2, 3];
const mixed = ["Hello", 42, true, null];
```

Arrays are **mutable**, **dynamic**, and **zero‑indexed**.

---

## 📌 Array Indexing

* Index starts from **0**

```js
const fruits = ["apple", "banana", "mango"];
console.log(fruits[0]); // apple
console.log(fruits[2]); // mango
```

* Accessing an out‑of‑range index returns **undefined**.

---

## 📌 Creating Arrays

### 1. Using Array literal (recommended)

```js
const arr = [1, 2, 3];
```

### 2. Using `new Array()`

```js
const arr = new Array(5); // creates empty array of length 5
```

---

## 📌 Common Array Methods

### 🔹 Add & Remove

| Action       | Method      | Example          |
| ------------ | ----------- | ---------------- |
| Add end      | `push()`    | `arr.push(10)`   |
| Remove end   | `pop()`     | `arr.pop()`      |
| Add start    | `unshift()` | `arr.unshift(5)` |
| Remove start | `shift()`   | `arr.shift()`    |

```js
const nums = [1,2,3];
nums.push(4);      // [1,2,3,4]
nums.pop();        // [1,2,3]
```

---

### 🔹 Searching

| Method       | Description            |
| ------------ | ---------------------- |
| `indexOf()`  | Returns index of value |
| `includes()` | Returns true/false     |

```js
const colors = ["red", "blue", "green"];
colors.includes("blue"); // true
```

---

### 🔹 Transforming Arrays

#### `map()` – returns new array

```js
[1, 2, 3].map(n => n * 2); // [2, 4, 6]
```

#### `filter()` – keeps only matching items

```js
[1, 2, 3, 4].filter(n => n % 2 === 0); // [2, 4]
```

#### `reduce()` – accumulates to a single value

```js
[1, 2, 3].reduce((total, n) => total + n, 0); // 6
```

---

## 📌 Looping Through Arrays

### 1. `for` loop

```js
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

### 2. `for...of`

```js
for (const item of arr) {
  console.log(item);
}
```

### 3. `forEach()`

```js
arr.forEach(item => console.log(item));
```

---

## 📌 Array Destructuring

```js
const [a, b] = [10, 20];
console.log(a); // 10
```

Skip items:

```js
const [first, , third] = [1,2,3];
```

---

## 📌 Spread & Rest

### Spread (expand array)

```js
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];
```

### Rest (collect values)

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```

---

## 📌 Useful Utility Methods

### `slice()` – non-destructive

```js
arr.slice(1, 3); // returns part of array
```

### `splice()` – destructive

```js
arr.splice(1, 1); // removes item at index 1
```

### `join()` – convert array to string

```js
["a","b"].join("-"); // "a-b"
```

### `sort()`

```js
[3,1,2].sort(); // [1,2,3]
```

### `reverse()`

```js
[1,2,3].reverse(); // [3,2,1]
```

---

## 📌 Multidimensional Arrays

```js
const matrix = [
  [1, 2],
  [3, 4]
];
console.log(matrix[1][0]); // 3
```

---

## 📌 When to Use Arrays?

Use arrays when you need **ordered data**, such as:

* lists of items
* API responses
* user inputs
* numeric operations
* loops & transformations

---


# Asynchronous-JavaScript

## 📌 Introduction

JavaScript is **single-threaded**, but it can perform non-blocking operations using **asynchronous programming**.

Async JS allows tasks like:

* Fetching data from a server
* Reading files
* Timers
* Events

to run **without blocking** the main thread.

---

## 📌 Why Asynchronous JavaScript?

Without async code:

* Long operations freeze the page
* UI becomes unresponsive
* Slow APIs block execution

Async JS lets the browser handle tasks in the background.

---

# 1. The Event Loop

The **Event Loop** is the system that manages asynchronous operations.

JavaScript uses:

* **Call Stack** → executes code
* **Web APIs** → timers, fetch, DOM
* **Callback Queue** → completed tasks
* **Event Loop** → sends tasks to stack when it's empty

This enables async behavior even though JS has one thread.

---

# 2. Callbacks

A **callback** is a function passed as an argument.

```js
function getData(callback) {
  setTimeout(() => {
    callback("Done!");
  }, 1000);
}

getData(result => {
  console.log(result);
});
```

### ❌ Callback Hell

Nested callbacks become hard to read:

```js
a(() => {
  b(() => {
    c(() => {
      d();
    });
  });
});
```

---

# 3. Promises

A **Promise** represents a value that will be available in the future.

### States:

* **pending**
* **fulfilled**
* **rejected**

### Example

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success"), 1000);
});

promise.then(result => console.log(result));
```

### `.catch()` for errors

```js
promise.catch(err => console.error(err));
```

### `.finally()`

```js
promise.finally(() => console.log("Done"));
```

---

# 4. Async / Await

Introduced in ES2017, **async/await** lets you write asynchronous code like synchronous code.

### Example

```js
async function loadData() {
  const result = await fetch("/api/data");
  const data = await result.json();
  console.log(data);
}

loadData();
```

### Try/Catch for errors

```js
async function run() {
  try {
    const res = await fetch("/invalid");
  } catch (err) {
    console.log("Error:", err);
  }
}
```

---

# 5. Microtasks vs Macrotasks

### Microtasks

* Promise callbacks (`then`, `catch`)

### Macrotasks

* `setTimeout`
* `setInterval`

Execution order:

1. Call Stack
2. **All microtasks**
3. One macrotask
4. Repeat

---

# 6. Common Asynchronous Functions

### `setTimeout`

```js
setTimeout(() => console.log("Hi"), 1000);
```

### `setInterval`

```js
setInterval(() => console.log("Tick"), 1000);
```

### `fetch`

```js
fetch("/api").then(res => res.json()).then(data => console.log(data));
```

---

# 7. Parallel, Sequential, and Race

### Sequential

```js
await task1();
await task2();
```

### Parallel

```js
await Promise.all([task1(), task2()]);
```

### Race

```js
Promise.race([task1(), task2()]);
```

---

# 8. Error Handling

### Promise error

```js
promise.catch(err => console.error(err));
```

### Async/await error

```js
try {
  await something();
} catch (err) {
  console.error(err);
}
```

---

# 9. Real-World Examples

### Fetching API Data

```js
async function getUsers() {
  const res = await fetch("https://jsonplaceholder.typicode.com/users");
  return res.json();
}
```

### File Reading (Node.js)

```js
const fs = require("fs/promises");

async function readFile() {
  const data = await fs.readFile("text.txt", "utf8");
  console.log(data);
}
```


# TypeCasting 

## 📌 Introduction

JavaScript is a **dynamically typed language**, meaning variables can change their type at runtime.
Type casting (also called **type coercion**) is the process of **converting one data type to another**.

JavaScript performs two types of type casting:

* **Implicit (Automatic) Type Coercion**
* **Explicit (Manual) Type Conversion**

---

# 1. Implicit Type Coercion (Automatic)

JavaScript automatically converts types during operations.

## 🔹 String Coercion

When one operand is a string → JS converts the other to **string**.

```js
"5" + 3;   // "53"
5 + "3";   // "53"
```

## 🔹 Number Coercion

When using `-`, `*`, `/`, `%`, JS converts both values to **numbers**.

```js
"10" - 2;   // 8
"6" * "2"; // 12
"20" / 5;   // 4
```

## 🔹 Boolean Coercion

Values are converted to **true/false** in logical contexts.

Falsy values:

```
false, 0, "", null, undefined, NaN
```

Everything else → `true`

```js
Boolean(0);      // false
Boolean("Hi");  // true
```

---

# 2. Explicit Type Conversion (Manual)

You convert types using built-in functions.

---

# 2.1 Convert to Number

Use:

* `Number(value)`
* `parseInt(value)`
* `parseFloat(value)`
* Unary `+value`

```js
Number("10");     // 10
parseInt("10px"); // 10
parseFloat("9.5"); // 9.5
+"5";             // 5
```

### ❗ Invalid conversions

```js
Number("hello"); // NaN
```

---

# 2.2 Convert to String

Use:

* `String(value)`
* `.toString()`

```js
String(123);     // "123"
(100).toString(); // "100"
```

---

# 2.3 Convert to Boolean

Use:

* `Boolean(value)`
* `!!value`

```js
Boolean(1);  // true
Boolean(0);  // false
!!"hi";     // true
```

---

# 3. Common Coercion Scenarios

### 🔹 With `+` operator

* If one operand = string → convert to string

```js
1 + "2"; // "12"
```

### 🔹 With comparison `==`

JavaScript tries to convert values to the same type

```js
"5" == 5; // true
true == 1; // true
false == 0; // true
```

### 🔹 Strict comparison `===`

No type coercion

```js
"5" === 5; // false
```

---

# 4. Type Coercion Table

| Expression      | Result |
| --------------- | ------ |
| `true + 1`      | 2      |
| `false + 1`     | 1      |
| `"5" * 2`       | 10     |
| `"5" + 2`       | "52"   |
| `null + 1`      | 1      |
| `undefined + 1` | NaN    |

---

# 5. Checking Types

```js
typeof "hello"; // "string"
typeof 50;      // "number"
typeof true;    // "boolean"
typeof null;    // "object" (known JS bug)
typeof []       // "object"
```

---

# 6. Best Practices

✔ Use **explicit conversion** instead of relying on coercion
✔ Avoid using loose equality (`==`)
✔ Use strict equality (`===`)
✔ Use `Number()` instead of `parseInt()` when possible
✔ Be careful with `+` → it triggers string coercion

---


