
## 📑 Table of Contents
- [LexicalStructure](#LexicalStructure)
- [Expressions](#Expressions)
- [Installation](#installation)
- [Usage](#usage)
- [API](#api)
- [Contributing](#contributing)
- [License](#license)


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

This README covers all major types of expressions with clear explanations and examples.

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

