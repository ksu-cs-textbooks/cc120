---
title: "JSON"
pre: "10. "
weight: 100
date: 2018-08-24T10:53:26-05:00
---
{{< console >}}

JSON is an acronym for _JavaScript Object Notation_, a serialization format that was developed in conjunction with ECMAScript 3.  It is a standard format, as set by [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf). 

## JSON Format
Essentially, it is a format for transmitting JavaScript objects.  Consider the JavaScript object literal notation:

```js
var whilma = {
  name: "Wilma Flintstone",
  relationship: "wife"
}
var pebbles = {
  name: "Pebbles Flintstone",
  age: 3,
  relationship: "daughter"
}
var fred = {
  name: "Fred Flintstone",
  job: "Quarry Worker",
  payRate: 8,
  dependents: [whilma, pebbles]
}
```

If we were to express the same object in JSON:

```json
{
  "name": "Fred Flintstone",
  "job": "Quarry Worker",
  "payRate": 8,
  "dependents": [
    {
      "name": "Wilma Flintstone",
      "relationship": "wife"
    },
    {
      "name": "Pebbles Flintstone",
      "age": 3,
      "relationship": "daughter"
    }
  ]
}
```

As you probably notice, the two are very similar.  Two differences probably stand out: First, references (like whilma and pebbles) are replaced with a JSON representation of their values.  And second, all property names (the keys) are expressed as strings, not JavaScript symbols.

A discussion of the full syntax can be found in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) and also at [json.org](https://json.org/).

## The JSON Object

The JavaScript language provides a JSON object with two very useful functions: [JSON.stringify()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) and [JSON.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse).  The first converts any JavaScript variable into a JSON string.  Similarly, the second method parses a JSON string and returns what it represents.

The `JSON` object is available in browsers and in Node.  Open the console and try converting objects and primitives to JSON strings with `JSON.stringify()` and back with `JSON.parse()`.


{{% notice info %}}

While JSON was developed in conjunction with JavaScript, it has become a popular exchange format for other languages as well.  There are parsing libraries for most major programming languages that can convert JSON strings into native objects:

* [Java](https://www.oracle.com/technetwork/articles/java/json-1973242.html)
* [C#](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data)
* [Python](https://docs.python.org/3/library/json.html)
* [C](https://github.com/json-c/json-c)
* [C++](https://github.com/nlohmann/json)

Some (like the Python one) are core language features.  Others are open-source projects.  There are many more available, just search the web!

{{% /notice %}}

## JSON Nesting and Circular References

While `JSON.parse()` will handle almost anything you throw at it.  Consider this object:

```js
var guy = {
  name: "Guy",
  age: 25,
  hobbies: ["Reading", "Dancing", "Fly fishing"]
};
```

It converts just fine - you can see for yourself by pasting this code into the console.  But what if we add reference to another object?

```js
var guyMom = {
  name: "Guy's Mom",
  age: 52,
  hobbies: ["Knitting", "Needlework", "International Espionage"]
};
guy.mother = guyMom;
```

Try running `JSON.stringify()` on `guy` now:

```js
JSON.stringify(guy);
```

Notice it works just fine, with Guy's mother now serialized as a part of the `guy` object.  But what if we add a reference from `guyMother` back to her son?

```js
guyMom.son = guy;
```

And try `JSON.stringify()` on `guy` now...

```js
JSON.stringify(guy);
```

We get a `TypeError: Converting circular structure to JSON`.  The `JSON.stringify` algorithm cannot handle this sort of circular reference - it wants to serialize `guy`, and thus needs to serialize `guyMom` to represent `guy.mother`, but in doing so it needs to serialize `guy` _again_ as `guyMother.son` references it.  This is a potentially infinitely recursive process... so the algorithm stops and throws an exception as soon as it detects the existence of a circular reference.

Is there a way around this in practice?  Yes - substitute direct references for keys, i.e.:

```js
var people = {guy: guy, guyMom: guyMom}
guy.mother = "guyMom";
guyMom.son = "guy";
var peopleJSON = JSON.stringify(people);
```

Now when you deserialize `people`, you can rebuild the references:

```js
var newPeople = JSON.parse(peopleJSON);
newPeople["guy"].mother = newPeople[newPeople["guy"].mother];
newPeople["guyMom"].son = newPeople[newPeople["guyMother"].son];
```

Given a standardized format, you can write a helper method to automate this kind of approach.

{{% notice info %}}
The fact that JSON serializes references into objects makes it possible to create deep clones (copies of an object where the references are also clones) using JSON, i.e.:

```js
function deepClone(obj) {
  return JSON.parse(JSON.stringify(obj));
}
```
If we were to use this method on `guy` from the above example:

```js
var guyClone = deepClone(guy);
```

And then alter some aspect of his mother:

```js
var guyClone.mother.hobbies.push("Skydiving");
```

The original `guy`'s mother will be unchanged, i.e. it will _not_ include Skydiving in her hobbies.

{{% /notice %}}