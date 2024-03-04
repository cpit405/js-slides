---
# try also 'default' to start simple
theme: default
presenter: true
title: 'JS'
titleTemplate: '%s - CPIT-405'
# apply any windi css classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: | 
    JavaScript
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
# Make content selectable/copyable
selectable: true
---

# JavaScript
### CPIT-405 Web Applications


<div class="absolute left-30px bottom-30px">
Spring 2024 &copy; Khalid Alharbi, Ph.D.
</div>

---
layout: center
---
## Table of Contents
- Introduction to JavaScript
- Brief history
- Getting Started with JavaScript
- Syntax
- Variables and Constants
- Data Types
- Strings
- Numbers and Math Object
- Dates and Times
- Arrays and Objects
- Functions: scope and invoking
- Logic and Control Flow
- Loops and Iteration
- Events
- DOM Manipulation
- Asynchronous JavaScript

---

# Introduction
- JavaScript is the programming language of the web.
- ECMAScript (ES) is the specification that defines the core syntax, features, and functionalities of JavaScript.
- ECMAScript (ES) has versions while JavaScript does not.
  - JavScript is the implementation of the ECMAScript standard.
  - ECMAScript versions have been abbreviated to ES1, ES2, ES3, ES5, and ES6.
    - Since 2016, versions are named by year (ECMAScript 2016, 2017, 2018, 2019, 2020, etc.)
- JavaScript is an interpreted/JIT language
  - Traditionally, JavaScript engines in web browsers interpreted JavaScript code line by line, translated it into machine code on the fly.
  - However, modern JavaScript engines utilize Just-In-Time (JIT) compilation at run time to improve performance.


---

# Introduction (II)

- JavaScript was primarily a client-side scripting language executing on the user's web browser to create interactive and dynamic web pages.
- With the rise of server-side JavaScript environments (e.g., Node.js), JavaScript is also used for server-side scripting.
- Today, JavaScript is used in various development areas:
  - Web development: front-end and back-end (Node.js).
  - Mobile app development: through frameworks like React Native and Ionic.
  - Desktop app development: through frameworks like Electron.
  - Data science and machine learning: through libraries and frameworks like D3.js, TensorFlow.js, and Brain.js.


---

## History (I)

- **1990**: Tim Berners-Lee created the first web browser called (WorldWideWeb and later renamed to Nexus).
- **1994**: 
  - The Nexus browser was discontinued as more browsers evolved.
  - Netscape web browser was released and became the dominate web browser in the mid 1990s. 
- **1995**: 
  - JavScript was created by Brendan Eich at Netscape (now Mozilla) in the early days of the web.
  - Netscape added built-in support for JavaScript.
  - Microsoft released Internet Explorer.
- **1996**: 
  - Netscape submitted the language to the European Computer Manufacturer's Association (ECMA).
  - Microsoft created their own scripting language called JScript to compete with Netscape.
    - JScript was not fully compatible with ECMAScript and had additional features.


---

## History (II)

- **1997**: 
  - ECMAScript 1 (ES1) released.
  - JavaScript became a trademark issued to Sun Microsystems (now Oracle).
- **1998-1999**: ES2 and ES3 released.
- **2000s**: 
  - With the rise of other browsers, JScript usage continued to decline in favor of JavaScript.
  - Microsoft ended support for JScript in 2009.
  - ES5 was released in 2009.
  - ES6 was released in 2015.
    - ES6 added classes, modules, arrow functions, destructuring assignment, template literals, and more features making JavaScript a powerful general-purpose language.
- **Present**: ECMAScript continued to release annual updates to the specs of the JavaScript language.


---
layout: center
---

# Getting Started with JavaScript

<br/>

You can write and execute JavaScript in multiple ways:
 - Writing JavaScript in the Console
 - Writing JavaScript in a web page
 - Writing JavaScript in the terminal

---

## Writing JavaScript in the Console

- The easiest way to try JavaScript is to use the JavaScript console.
- The JavaScript console is a very useful tool to execute JavaScript code.
- All modern browsers have support for the console:
 - Right-click anywhere on a webpage and select "Inspect" from the context menu. This will open the Developer Tools. Click on the Console tab.
- You can also open the console using the keyboard shortcut:
  - Windows: `F12` or `Ctrl`+`Shift`+`I`
  - macOS: `Command`+`Option`+`I`

![Chrome Dev Tools](/images/chrome-dev-tools.png)


---

# Writing JavaScript in a web page (I)

- In HTML, JavaScript code is inserted between `<script>` and `</script>` tags
 - You can place the `<script>` tag in the `<head>` or `<body>` tags.
 - You can also place JavaScript code in external files and reference it in your HTML document using `<script src="scriptFile.js"></script>`

```javascript
<!DOCTYPE html>
<html>
<head>
    <script>
        console.log("Hello JavaScript from within the head element!")
    </script>
</head>
<body>
    <h2>Hello JavaScript</h2>
    <script>
        console.log("Hello JavaScript from within the body element!")
    </script>
    <script src="externalJSFile.js"></script>
</body>
</html>
```

---

# Writing JavaScript in a web page (II)

- If placed inside the `<head>` tag, JavaScript code will be executed prior to the page being rendered by the browser. This can impact performance of loading and rendering your page.
- An external JavaScript file can be imported using the `src` attribute of the `<script>` tag.
  ```html
  <script src="./path/to/script.js"></script>
  ```
  - Using external JavaScript files provides a better separation of concerns between HTML and code.
  - External JavaScript files can be cached by the browser to speed up page rendering time.


---

# Writing JavaScript in the Terminal
- You can also write and run JavaScript code from the command line: 
- Install Node.js from [nodejs.org](https://nodejs.org).
- Open your Terminal app or PowerShell on Windows
  - You can also save a file, navigate to its directory using `cd`, and execute the JavaScript file using 
  
  ```shell
  node script.js
  ```

  - Or You can run the interactive shell using the `node` command:
  
  ```shell
  node
  ```
  
  ```plaintext
  Welcome to Node.js v20.3.1.
  Type ".help" for more information.
  > console.log("hello JavaScript")
  hello JavaScript
  ```

---

# Syntax
- **Case sensitivity**: JavaScript is a case-sensitive language.
  - Identifier with uppercase and lowercase letters are treated as distinct
- **Statements**: JavaScript programs are composed of a sequence of statements. A statement might declare a variable, loop over items, call a function, or change the value of a variable
- **Semicolons**: In JavaScript, semicolons are usually placed at the end of a statement.
  - However, JavaScript does not enforce the use of semicolons as it has automatic semicolon insertion (ASI) mechanism. If you omit a semicolon, the JavaScript engine will insert it for yous
- **Variables**: Variables are declared using `var`, `let`, or `const`. More on this later.
- **Data Types**: JavaScript has the following data types: Number, BigInt, String, Symbol, Boolean, Object, Null, and Undefined.

---

---
layout: two-cols-header
---

# Variables and Constants: `let` vs `var` (I)

- JavaScript Variables can be declared in one of three ways: let, var, and const

::left::
- Using `var` for function-scoped or globally-scoped variables

```javascript
var x = 10;
if (x == 10) {
  var x = 20;
  console.log(x);
}
console.log(x);
```

<div v-click>

```javascript
var x = 10;
if (x == 10) {
  var x = 20;
  console.log(x); // prints 20
}
console.log(x); // prints 20
```

```
20
20
```
</div>

::right::
- Using `let` for re-assignable, block-scoped local variables.

<div v-click>

```javascript
let x = 10;
if (x == 10) {
  let x = 20;
  console.log(x);
}
console.log(x);
```
</div>

<div v-click>

```javascript
let x = 10;
if (x == 10) {
  let x = 20;
  console.log(x); // prints 20
}
console.log(x); // prints 10
```

```
20
10
```

</div>
---

# Variables and Constants (II)

- Using `const` for variables whose values must not be changed.

```javascript
const discount = 0.20;
discount = 0.50; // Uncaught TypeError: Assignment to constant variable.
console.log(discount); // prints 0.20
```

```
0.20
```

- If a constant is an object, its properties can be updated, added, or removed. More on this later when introducing objects.

```javascript
const course = {name: "CPIT-405", semester: "fall", year: 2023}
course.semester = "spring"
console.log(course) // prints 
```

```
{ name: 'CPIT-405', semester: 'spring', year: 2023 }
```

---

# Data Types

|     Type       |    What it represents?          |            Example    | 
|----------------|:-------------------:|-----------------------:|
|     Null       |    An absent of any object value         | `let foo = null;`      |
|    Undefined       | An absent of a value       |`let foo;`     |
|     Boolean|A boolean value `true` or `false`       |`let foo = true;`      |
|     Number       |A floating-point number|`let foo= 37; let bar=-9.14;`       |
|     Bigint       |    Too large numbers.          |`let foo= = BigInt(Number.MAX_SAFE_INTEGER + 2);`      |
|     String       |    Represents textual data           |            `let foo = "A string primitive";`      |
|     Symbol       |    A unique and immutable value          |            `let foo= Symbol("foo");`      |


---
# Object
- Objects can be seen as a collection of properties.
- Objects are the only mutable values in JavaScript.


---
# Strings

---
# Numbers and Math Object

---
# Dates and Times

---
# Arrays and Objects

---
# Functions: scope and invoking
- In JavaScript, functions are considered first class citizens.
 - Functions are not required to be declared in a class.
- Functions are also objects with an additional capability of being callable (can be invoked).



---
# Logic and Control Flow

---
# Loops and Iteration

---
# Events

---
# Document Object Model (DOM) 
- JavaScript allows us to create dynamic interactive web applications. 
- This is due to the Document Object Model (DOM) interface that represents the HTML document as a logical tree of nodes.
- Each branch of the tree ends in a node, and each node contains objects.
- The HTML DOM API provides access to HTML elements and their attributes, content, and CSS styles. 
- This means we can change the structure, style or content of any HTML document in JavaScript.
- An object in the DOM is called a `node`. 
- The DOM has some built-in nodes such as `document` and `document.body` and HTML element nodes such as `<div>` or `<p>`. 
- A node can also be a `textNode`, which refers to a text contained in an element such as `<p>some text</p>` or a comment node for comments such as `<!- - comment - - >`. 


---

# DOM Node Types

| Node Type | Example |
|-----------|---------|
| `ELEMENT_NODE`  | Any HTML element such as `<p>`, `<ul>`, `<div>`, etc. |
| `ATTRIBUTE_NODE` | Any attribute of an Element such as `href` in `<a>` or `src` in `img`|
| `TEXT_NODE`| The actual text inside an Element or Attribute such as `<p>text</p>` or `<img src="./some-image.png">` |
|`COMMENT_NODE` |A Comment node as in `<!-- this is a comment -->`|
| `DOCUMENT_NODE` | A Document node that represents any web page loaded in the browser |


---

# The `window` object in the DOM
- Each tab or window in a web browser is represented by its own `Window` object.
- Each `window` object has a `document` property that refers to the DOM, which represents the content of the window. 
- The DOM enables creating interactive web pages, where we can add, change, or delete any HTML elements and attributes, CSS styles, or events dynamically. 
- We will explore the main parts of the DOM API that enable these capabilities.

---

# DOM Tree Example
![](/images/dom-example.png)


---
# Asynchronous JavaScript
