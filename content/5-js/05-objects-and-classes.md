---
title: "Objects and Classes"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---

{{< console >}}

JavaScript is also an object-oriented language, but the way it implements objects is derived from the ideas of the Self programming language, rather than the C++ origins of Java and C#'s object-oriented approaches.  

## Object Properties

Let's start with what an object _is_ in JavaScript.  It's basically a collection of properties - key/value pairs, similar to the concept of a Dictionary in other languages.  The properties play both the role of fields and methods of the object, as a property can be assigned a primitive value or a function.

We've already seen how to create an object with literal syntax, but let's see another example:

```js
var bob = {
  name: "Bob",
  age: 29,
  mother: {
    name: "Mary",
    age: 53
  }
}
```

Look at the property `mother` - it is its own object, nested within `bob`. Objects can nest as deep as we need them to (or at least, until we run out of memory).  

We can then access properties with either dot notation or bracket notation, i.e.:

```js
// dot notation
console.log(bob.name);
console.log(bob.mother.name);
bob.father = {name: "Mark"};

// bracket notation
console.log(bob["name"]);
console.log(bob["mother"]["name"]);
bob["father"] = {name: "Mark"}
```

Property names should conform to JavaScript variable naming rules (start with a letter, `$`, or `_`, be composed of letters, numbers, `$`, and `_`, and contain no spaces) though we can use bracket notation to sidestep this:

```js
bob["favorite thing"] = "macaroni";
```

However, if a property set with bracket notation does not conform to the naming rules, it cannot be accessed with dot notation.  Other than that, you're free to mix and match.

You can also use the value of a variable as a property name:

```js
var field = "key";
var tricky = {
  [field]: 1
}
console.lo(tricky.key);
```
This is a handy trick when you need to set property names at runtime.

## Constructors

A constructor in JavaScript is simply a function that is invoked with the keyword `new`.  Inside the body of the function, we have access to a variable named `this`, which can have values assigned to it.  Here is an example:

```js
function Bear(name) {
  this.name = name;
}
var pooh = new Bear("pooh");
```

There is nothing that inherently distinguishes a constructor from any other function; we can use the `new` keyword with any function.  However, it only makes sense to do so with functions intended to be used as constructors, and therefore JavaScript programmers have adopted the convention of starting function names intended to be used as constructors with a capital letter, and other functions with a lowercase one.

## Object Methods
Methods are simply functions attached to the object as a property, which have access to the `this` (which refers back to the object) i.e.:

```js 
pooh.greet = function() {
  console.log(`My name is ${this.name}`);
}
```

We can also attach a method to all objects created with a constructor by attaching them to its prototype, i.e.:

```js
Bear.prototype.growl = function() {
  console.log(`Grrr.  My name is ${this.name} and I'll eat you up!`)
}
```

Now we can invoke `pooh.growl()` and see the same message.  If we create a few new Bear instances:

```js 
var smokey = new Bear("Smokey");
var shardik = new Bear("Shardik");
```

They also has access to the `growl()` method, but not `greet()`, because that was declared on the `pooh` instance, _not_ the prototype. 

Of course, it doesn't seem appropriate for Smokey the Bear to threaten to eat you.  Let's tweak his behavior:

```js
smokey.growl = function() {
  console.log("Only you can prevent forest fires!");
}
```

Now try invoking:

```js
smokey.growl();
shardik.growl();
pooh.growl();
```

Pooh and Shardick continue to growl menacingly, but Smokey warns us about the dangers of forest fires.  This leads us to the topic of prototypes.

## Object Prototypes
JavaScript adopts an approach to inheritance known as [prototype-based programming](https://en.wikipedia.org/wiki/Prototype-based_programming), which works a bit differently than you're used to.  

In JavaScript, each object keeps a reference to its constructor (in fact, you can see this for our bears with `pooh.constructor`, `smokey.constructor`, etc.).  Each constructor in turn has a `prototype` property, which is an `object` with methods and properties attached to it.

When we invoke `pooh.growl()`, JavaScript first checks to see if the `growl` property is defined on the Bear instance we know as `pooh`.  If not, then it checks the constructor's prototype for the same property.  If it exists, then it invokes it.

Inheritance in JavaScript takes the form of a prototype chain - as each prototype is an `object`, each prototype can have its own prototype in turn.  Thus, when we invoke a method, the interpreter walks down this chain and invokes the first matching property found.


## ECMA Script 2015 Class Syntax

If you find this all confusing, don't worry, you're not alone.  ECMAScript decided to introduce a new class syntax in the 2015 version (ES6). It will look a lot more familiar:

```js
class Bear {
  constructor(name) {
    this.name = name;
    this.growl = this.growl.bind(this);
  }
  
  growl() {
    console.log(`Grrr! My name is ${this.name} and I'll eat you!`);
  }
}
```

Here we've recreated our Bear class using the new syntax.  We can construct a bear the same way, and invoke its `growl()` method:

```js
var yogi = new Bear("Yogi");
yogi.growl();
```

### Method Binding

Under the hood we're still using the same prototypical inheritance, which throws a slight wrench in the works.  Notice the line:

```js
this.growl = this.growl.bind(this);
```

in the constructor?  This uses the [function.prototype.bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind) method to bind the scope of the growl function to the `this` object of our class (remember, functions start a new scope, and a new scope means a new `this` object).  

So remember when using ES6 class syntax, you need to bind your methods, or declare them in the constructor itself as arrow functions, i.e.:

```js
class Bear {
  constructor(name) {
    this.name = name;
    this.growl = () => { 
      console.log(`Grrr! My name is ${this.name} and I'll eat you!`);
    }
  }
}
```

As the arrow function declaration does not open a new scope, the this object doesn't change, and refers to the bear instance.

### Inheritance 

Specifying inheritance is also simplified.  For example:

```js
class Mammal {
  constructor() {
    this.hasFur = true;
    this.givesMilk = true;
    this.heartChambers = 4;
  }
}

class Bear extends Mammal {
  constructor(name) {
    super();
  }
}
```

Remember to always invoke the parent constructor with `super()` as the first thing in your child class constructor.