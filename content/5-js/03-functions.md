---
title: "JavaScript Functions"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---

{{< console >}}

While JavaScript may look like an imperative language on the surface, much of how it behaves is based on _functional_ languages like Scheme.  This leads to some of the common sources of confusion for programmers new to the language.  Let's explore just what its functional roots mean.

JavaScript implements [first-class functions](https://en.wikipedia.org/wiki/First-class_function), which means they can be assigned to a variable, passed as function arguments, returned from other functions, and even nested inside other functions.  Most of these uses are not possible in a traditional imperative language, though C# and Java have been adding more functional-type behavior.   

## Defining Functions
Functions in JavaScript are traditionally declared using the `function` keyword, followed by an identifier, followed by parenthesized arguments, and a body enclosed in curly braces, i.e.:

```js
function doSomething(arg1, arg2, arg3) {
  // Do something here...
}
```

Alternatively, the name can be omitted, resulting in an _anonymous_ function:

```js 
function (arg1, arg2, arg3) {
  // Do something here...
}
```

Finally ES6 introduced the arrow function syntax, a more compact way of writing anonymous functions, similar to the lambda syntax of C#:

```js
(arg1, arg2, arg3) => {
  // Do something here...
}
```

However, arrow function syntax also has special implications for scope, which we will discuss shortly.

## Invoking Functions 

Functions are invoked with a parenthetical set of arguments, i.e. 

```js
function sayHello(name) {
  console.log(`Hello, ${name}`);
}
```

Go ahead and define this function by typing the definition into your console.  

Once you've done so, it can be invoked with `sayHello("Bob")`, and would print `Hello, Bob` to the console.  Give it a try:

<iframe src="https://jsconsole.com/" style="width:100%"></iframe>

Functions can also be invoked using two methods defined for all functions, [call()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) and [apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply).

## Function Arguments

One of the bigger differences between JavaScript and imperative languages is in how JavaScript handles arguments.  Consider the `hello()` function we defined above. What happens if we invoke it with no arguments?  Or if we invoke it with two arguments?

Give it a try:

```js 
sayHello()
sayHello("Mary", "Bob");
```

What are we seeing here?  In JavaScript, the number of arguments supplied to a function when it is invoked is _irrelevant_.  The same function will be invoked regardless of the _arity_ (number) or _type_ of arguments.  The supplied arguments will be assigned to the defined argument names within the function's scope, according to the order. If there are less supplied arguments than defined ones, the missing ones are assigned the value `undefined`.  And if there are extra arguments supplied, they are not assigned to a value.

Can we access those extra arguments?  Yes, because JavaScript places them in a variable `arguments` accessible within the function body.  Let's modify our `sayHello()` method to take advantage of this knowledge, using the `for .. of` loop we saw in the last section:

```js
function sayHello() {
  for(name of arguments) {
    console.log(`Hello, ${name}`);
  }
}
```

And try invoking it with an arbtrary number of names:

```js
sayHello("Mike", "Mary", "Bob", "Sue");
``` 

{{% notice warning %}}
JavaScript does not have a mechanism for [function overloading](https://en.wikipedia.org/wiki/Function_overloading) like C# and Java do. In JavaScript, if you declare a second "version" of a function that has different named arguments, you are not creating an overloaded version - you're replacing the original function!
{{% /notice %}}

Thus, when we entered our second `sayHello()` definition in the console, we overwrote the original one.  Each function name will _only_ reference a single definition at a time within a single scope, and just like with variables, we can change its value at any point.

Finally, because JavaScript has first-order functions, we can pass a function as an argument.  For example, we could create a new function, `greet()` that takes the greeter's name, a function to use to greet others, and uses the arguments to greet an arbitrary number of people:

```js 
function greet(name, greetingFn) {
  for(var i = 2; i < arguments.length; i++) {
    greetingFn(arguments[i]);
  }
  console.log(`It's good to meet you.  I'm ${name}`);
}
```

We can then use it by passing our `sayHello()` function as the second argument:

```js
greet("Mark", sayHello, "Joe", "Jill", "Jack", "John", "Jenny");
```

Note that we don't follow the function name with the parenthesis (`()`) when we pass it.  If we did, we'd inovke the function _at that point_ and what we'd pass was the return value of the function, not the function itself.

## Return Values
Just like the functions you're used to, JavaScript functions can return a value with the `return` statement, i.e.:

```js
function foo() { 
  return 3;
}
```

We can also return nothing, which is `undefined`:

```js
function bar() {
  return;
}
```

This is useful when we want to stop execution immediately, but don't have a real return value.  Also, if we don't specify a return value, we _implicity_ return `undefined`.

And, because JavaScript has first-order functions, we can return a function:

```js 
function giveMeAFunction() {
  return function() {
    console.log("Here I am!")
  }
}
```

## Function Variables 

Because JavaScript has first-order functions, we can also assign a function to a variable, i.e.:

```js
var myFn = function(a, b) {return a + b;}

var greetFn = greet;

var otherFn = (a, b) => {return a - b;}

var oneMoreFn = giveMeAFunction();
```

## Functional Scope

We've mentioned scope several times now.  Remember, [scope](https://en.wikipedia.org/wiki/Scope_(computer_science)) simply refers to where a binding between a symbol and a value is valid (here the symbol could be a `var` or `function` name).  JavaScript uses _functional scope_, which means a new scope is created within the body of every function.  Moreover, the parent scope of that function remains accessible as well.

Consider the JavaScript code:

```js
var a = "foo";
var b = "bar";

console.log("before coolStuff", a, b);

function coolStuff(c) {
  var a = 1;
  b = 4;
  console.log("in coolStuff", a, b, c);
}
coolStuff(b);

console.log("after coolStuff", a, b);
```

What gets printed before, in, and after `coolStuff()`?

1. Before we invoke `coolStuff()` the values of `a` and `b` are `"foo"` and `"bar"` respectively.
2. Inside the body of `coolStuff()`:
  * The named argument `c` is assigned the value passed when `coolStuff()` is invoked - in this case, the value of `b` at the time, `"bar"`.
  * A new variable `a` is declared, and set to a value of `1`.  This `a` only exists within `coolStuff()`, the old `a` remains unchanged outside of the function body.
  * The value of `4` is assigned to the variable `b`.  Note that we did not declare a new `var`, so this is the same `b` as outside the body of the function.
3. After the function is invoked, we go back to our original `a` which kept the value `"foo"` but our `b` was changed to `4`.

That may not seem to bad.  But let's try another example:

```js 
var a = 1;
function one() {
  var a = 2;
  function two() {
    var a = 3;
    function three() {
      var a = 4;
    }
    three();
  }
}
```

Here we have nested functions, each with its own scope, and its own variable `a` that exists for that scope.

## Block Scope
Most imperative programming langauges use _block scope_, which creates a new scope within any block of code.  This includes function bodies, but also loop bodies and conditional blocks.  Consider this snippet:

```js
for(var i = 0; i < 10; i++) {
  var j = i;
}
console.log(j);
```

What will be printed for the value of `j` after the loop runs?  

You might think it should have been `undefined`, and it certainly would have been a null exception in an imperative language like Java, as the variable `j` was defined within the block of the `for` loop. Because those languages have _block scope_, anything declared within that scope only exists there.  

However, with JavaScript's _functional_ scope, a new scope is only created within the body of a function - not loop and conditional blocks!  So anything created within a conditional block actually exists _in the scope of the function it appears in_.  This can cause some headaches.  

Try running this (admittedly contrived) example in the console:

```js
for(var i = 0; i < 10; i++) {
  setTimeout(function() {
    console.log(i);
  }, 10);
}
```

The [setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) will trigger the supplied function body 10 ms in the future.  

Notice how all the values are 10?  That's because we were accessing the same variable `i`, because it was in the same scope each time!  

The keyword `let` was introduced in ES6 to bring block scope to JavaScript.  If we use it instead, we see the behavior we're more used to:

```js
for(let i = 0; i < 10; i++) {
  setTimeout(function() {
    console.log(i);
  }, 10);
}
```

