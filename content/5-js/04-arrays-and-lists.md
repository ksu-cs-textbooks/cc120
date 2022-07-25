---
title: "Arrays - Lists by Another Name"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

{{< console >}}

You might have noticed we used an array in discussing the `for .. in` loop, but didn't talk about it in our data type discussion.  This is because in JavaScript, an `array` is not a primitive data type.  Rather, it's a special kind of `object`.

This is one of those aspects of JavaScript that breaks strongly with imperative languages.  Brandon Eich drew heavily from Scheme, which is a functional language that focuses heavily on list processing... and the JavaScript array actually has more to do with lists than it does arrays.   

## Declaring Arrays
JavaScript arrays can be declared using literal syntax:

```js 
var arr = [1, "foo", true, 3.2, null];
```

Notice how we can put any kind of data type into our array?  We can also put an array in an array:

```js 
var arr2 = [arr, [1,3,4], ["foo","bar"]];
```

We can create the effect of an n-dimensional array, though in practice we're creating what we call [jagged arrays](https://en.wikipedia.org/wiki/Jagged_array) in computer science.

Clearly if we can do this, the JavaScript array is a very different beast than a Java or C# one.

## Accessing Array Values

We can access an element in an array with bracket notation, i.e.:

```js 
var arr = [1, "foo", true, 3.2, null];
console.log(arr[3])
```

will print `true`.  We index arrays starting at 0, just as we are used to .  
But what if we try accessing an index that is "out of bounds"?  Try it:

```js
var arr = [1,2,3,4];
console.log(arr[80]);
```

We don't get an exception, just an `undefined`, because that value doesn't exist yet. Let's take the same array and give it a value there:

```js
arr[80] = 5;
console.log(arr[80]);
```

Now we see our value.  But what about the values between `arr[3]` and `arr[80]`?  If we try printing them, we'll see a value of `undefined`.  But remember how we said an array is a special kind of object?  Let's iterate over its keys and values with a `for .. in` loop:

```js 
for(key in arr) {
  console.log(`The index ${key} has value ${arr[key]}`);
}
```

Notice how we only print values for indices 0,1,2,3, and 80?  The array is really just a special case of the `object`, using indices as property keys to store values. Everything in the array is effectively stored by reference... which means all the rules we learned about optimizing array algorithms won't apply here.

## Arrays as Special-Purpose Data Structures

You've also learned about a lot of specialty data structures in prior courses - stacks, queues, etc.  Before you write one in JavaScript though, you may be interested to know that JavaScript arrays can emulate these with their built-in methods.  

__Stacks__ We push new elements to the top of the stack, and pop them off.  The array methods [push()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) and [pop()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) duplicate this behavior by pushing and popping items from the end of the array.

__FIFO queues__ A first-in-first-out queue can be mimicked with the array methods [push()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) and [shift()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) which push new items to the end of the array and remove the first item, respectively.

Another useful method is [unshift()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift), which adds a new element to the front of the array.  

Most data types you've learned about in prior courses can be emulated with some combination of JavaScript arrays and objects, including various flavors of trees, priority queues, and tries.  Granted, these will not be as performant as their equivalents written in C, but they will serve for most web app needs.

## Map Reduce

One of the most powerful patterns JavaScript adopted from list-processing languages is the map and reduce patterns.  You may have heard of [MapReduce](https://en.wikipedia.org/wiki/MapReduce) in terms of Big Data - that is exactly these two patterns used in combination. Let's examine how they are used in JavaScript.

### Map

The basic idea of mapping is to process a list one element at a time, returning a new list containing the processed elements.  In JavaScript, we implement it with the [map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) method of the array. It takes a function as an argument, which is invoked on each item in the array, and returns the newly processed array (the old array stays the same).  

The function supplied to _map()_ is supplied with three arguments - the item currently iterated, the index of the item in the array, and a reference to the original array. Of course, you don't have to define your function with the second or third arguments.  

Let's try a simple example:

```js 
var squares = [1,2,3,4].map((item) => {return item * item})
```

This code squares each of the numbers in the array, and sets `squares` to have as a value the array of newly-created squares. 

Notice too how by passing a function into the map function, we create a new scope for each iteration?  This is how JavaScript has long dealt with the challenge of functional scope - by using functions!

### Reduce

The reduce pattern also operates on a list, but it _reduces_ the list to a single result.  In JavaScript, it is implemented with the array's [reduce()]() method.  The method takes two arguments - a reducer function and an initial accumulator value.  Each time the reduce function iterates, it performs an operation on the currently iterated item and the accumulator.  The accumulator is then passed forward to the next iteration, until it is returned at the end.

The function supplied to _reduce_ has four arguments - the current accumulator value, the current iterated item, the item's index, and the original array.  As with `map()`, we can leave out the last two arguments if we don't need to use them.

A common example of `reduce()` in action is to sum an array:

```js
var sum = [1, 2, 3, 4, 5].reduce((acc, item) => {return acc + item}, 0);
```

We supply the initial value of the accumulator as identity for addition, `0`, and each iteration the current item in the array is added to it.  At the end, the final value is returned.

### MapReduce 

And as we said before, MapReduce is a combination of the two, i.e. we can calculate the sum of squares by combining our two examples:

```js
var sumOfSquares = [1,2,3,4,5].map((item) => {
  return item * item
}).reduce((acc, item) => {
  return acc + item
});
```

Notice how we invoked the `map()` function on the original array, and then invoked `reduce()` on the returned array?  This is a syntax known as [method chaining](https://en.wikipedia.org/wiki/Method_chaining), which can make for concise code. We could also have assigned each result to a variable, and then invoked the next method on that variable.
