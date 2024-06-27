---
title: "Basic Syntax"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---

{{< console >}}

Because Netscape was adopting Java at the same time they were developing what would become JavaScript, there was a push to make the syntax stay somewhat consistent between the two languages.  As a result, JavaScript has much of the look and feel of an imperative language like C, C#, or Java. 

However, this similarity can be deceptive, because how JavaScript operates can be quite different than those languages.  This can lead to frustration for imperative programmers learning JavaScript.  As we go over the basics of the language, I will strive to call out these tricky differences.

To assist you in learning JavaScript syntax, we've added an interactive console to this textbook where you can type in arbitrary JavaScript code and see the result of its execution, much like the console that Developer Tools provide.  You can click the word "Console" on the purple tab below to expand it, and click it again to minimize it.

## Interpreted Language
JavaScript is an interpreted language, which means instead of being compiled into machine code, it is interpreted by a special program - an interpreter.  Each browser has its own interpreter implementation. 

Let's start with a traditional example:

```js
console.log("hello world");
```

Copy/paste or type this code into the console provided at the bottom of the page. What is the output?

As you might expect, this prints the string "hello world" to standard output.  Notice we didn't need to put this code into a `main` function - JavaScript code is executed as it is encountered by the interpreter.

## Terminating Lines of Code
Also, the semicolon is an optional way to end an expression.  A new line is other way to do so, so these two programs:

```js 
console.log("Hello")
console.log("World")
```

and 

```js 
console.log("Hello");console.log("World");
```

are equivalent.  We can also use both a semicolon and a new line (as in the first example).  A common technique for making JavaScript files smaller, known as _minifying_ takes advantage of this fact to write an entire program in a single line!  We'll discuss how and when to do so later.

## Data Types 
Like any programming language, JavaScript has a number of predefined data types.  We can also query the data type of a value at runtime, using the `typeof` keyword.  Try typing some of these lines into the console:

```js 
typeof 5;
typeof 1.3;
typeof "Hello";
typeof true;
```

### Numbers
Numbers include integers and floats, though JavaScript mostly uses the distinction for how a value is stored in memory and presents the programmer with the `number` type.  This category also includes some special values, like `NaN` (not a number) and `Infinity`.   We can perform all the standard arithmetic operations on any number (`+`, `-`, `*`, `/`).  
These operations are also "safe" in the sense that they will not throw an error. For example, try typing `4/0` in the terminal below.  The value you see as a result is still a number!

The JavaScript interpreter will switch between an integer and float representation internally as it makes sense to.  For example, type `4.0` and you'll see the console echoes `4` to you, showing it is storing the number as an integer.  Try typing `4.1`, and you'll see it stores it as a float.

### Strings
The `string` type in JavaScript can be declared literally using single (`'`) or double (`"`) quotes, and as of ES6, tick marks (`` ` ``).  

Double and single-quoted strings work exactly the same. They must be on the same line, though you can add newline characters to both using `\n`.  The backslash is used as an escape character, so to include it in a string you must use a double-backslash instead `\\`.  Finally, in a single-quoted string you can escape a single quote, i.e. `'Bob\'s Diner'`, and similarly for double-quotes: `"\"That's funny,\" she said."`  Judicious choices of single-or double-quoted strings can avoid much of this complication.

You can also directly reference unicode characters with `\u[ref number]`.  Try typing the sequence `"\u1F63C"`.  

Finally, strings enclosed with tick marks (`` ` ``) are _template literals_ that have a few special properties.  First, they can span multiple lines, i.e.:

```js
`This is a 
multiline string
example`
```

The line breaks will be interpreted as new line characters.  Secondly, you can embed arbitrary JavaScript inside of them using `${}`.  Give it a try:

```js
`The sum of 2 and 3 is ${2 + 3}`
```

{{% notice info %}}
In JavaScript there is no character type.  In practice, the role characters normally play in programs is filled by strings of length one.
{{% /notice %}}

### Booleans
JavaScript also has the boolean literals `true` and `false`.  It also implements the boolean logical operators `&&` (logical and) `||` (logical or), and `!` (logical not).

### Undefined 
JavaScript has a special value `undefined` that means a value hasn't been set.  You probably saw it when you entered the `console.log("Hello World")` example above, which spit out:

```tex
>  Hello World!
<· undefined
```

As the console echoes the value of the prior line, it was printing the return value of `console.log()`.  Since `console.log()` doesn't return a value, this results in `undefined`.  

### Null
JavaScript also defines a `null` type, even though `undefined` fills many of the roles `null` fills in other languages.  However, the programmer must explicitly supply a `null` value.  So if a variable is `null`, you know it was done _intentionally_, if it is `undefined`, it may be that it was accidentally not initialized.

### Objects
The `object` type is used to store more than one value, and functions much like a dictionary in other languages.  Objects can be declared literally with curly braces, i.e.:

```js
{
  first: "Jim",
  last: "Hawkins",
  age: 16
}
```

An object is essentially a collection of key/value pairs, known as __properties__.  We'll discuss objects in more depth in the [Objects and Classes]({{% ref "5-js/05-objects-and-classes" %}}) section.

### Symbols

Finally, the `symbol` type is a kind of identifier.  We'll discuss it more later.

## Variables  
JavaScript uses _dynamic typing_.  This means the type of a variable is not declared in source code, rather it is determined at runtime.  Thus, all variables in JavaScript are declared with the `var` keyword, regardless of type:

```js
var a = "A string";  // A string
var b = 2;           // A number
var c = true;        // A boolean
```

In addition, the type of a variable can be changed at any point in the code, i.e. the statements:

```js 
var a = "A string";
a = true; 
```

is perfectly legal and workable.  The type of `a`, changes from a string to a float when its value is changed.  

In addition to the `var` keyword, constants are declared with `const`.  Constants must have a value assigned with their declaration and cannot be changed. 

Finally, ECMA6 introduced the `let` keyword, which operates similar to `var` but is locally scoped (see the discussion of functional scope for details).

## Type Conversions 

JavaScript does its best to use the specified variable, which may result in a type conversion.  For example:

```js
"foo" + 3
```

Will result in the string `'foo3'`, as the `+` operator means concatenation for strings. However, `/` has no override for strings, so 

```js 
"foo" / 3
```

Will result in `NaN` (not a number).

Additionally, when you attempt to use a different data type as a boolean, JavaScript will interpret its 'truthiness'.  The values `null`, `undefined`, and `0` are considered `false`.  All other values will be interpreted as `true`.  

## Control Structures 

JavaScript implements many of the familiar control structures of conditionals and loops.  

{{% notice warning %}} 
Be aware that variables declared within a block of code using `var` are subject to function scope, and exist outside of the conditional branch/loop body.  This can lead to unexpected behavior.
{{% /notice %}}

### If Else Statements 
The JavaScript `if` and `if else` statements look just like their Java counterparts:

```js
if(<logical test>) {
  <true branch>
}
```

```js
if(<logical test>) {
  <true branch>
} else  {
  <false branch>
}
```

### Loops
As do `while` and `do while` loops:

```js
while(<logical test>) {
  <loop body>
}
```

```js 
do {
  <loop body>
}(<logical test>);
```

And `for` loops:

```js
for(var i = 0; i < 10; i++) {
  <loop body>
}
```

JavaScript also introduces a `for ... in` loop, which loops over properties within an object.  I.e.:

```js
var jim = {
  first: "Jim",
  last: "Hawkins",
  age: 16
}
for(key in jim) {
  console.log(`The property ${key} has value ${jim[key]}`);
}
```

and the `for ... of` which does the same for arrays and other iterables:

```js
var fruits = ["apple", "orange", "pear"];
for(value of fruits) {
  console.log(`The fruit is a ${value}`);
}
```

Try writing some control structures to conditionally log messages to the console!


