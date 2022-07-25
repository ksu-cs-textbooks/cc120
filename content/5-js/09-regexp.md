---
title: "Regular Expressions"
pre: "9. "
weight: 90
date: 2018-08-24T10:53:26-05:00
---

{{< console >}}

The JavaScript [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) prototype has some very powerful methods, such as [String.prototype.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes) which recognizes when a string contains a substring - i.e.:

```js
"foobarwhen".includes("bar")
```

would evaluate to true.  But what if you needed a more general solution?  Say, to see if the text matched a phone number pattern like XXX-XXX-XXXX?  That's where [Regular Expressions](https://en.wikipedia.org/wiki/Regular_expression) come in.

Regular Expressions are a sequence of characters that define a _pattern_ that can be searched for within a string.  Unlike substrings, these patterns can have a _lot_ of flexibility.  For example, the phone number pattern above can be expressed as a JavaScript [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) like this:

```js
/\d{3}-\d{3}-\d{4}/
```

Let's break down what each part means.  First, the enclosing forward slashes (`/`) indicate this is a RegExp literal, the same way single or double quotes indicate a string literal.  The backslash d (`\d`) indicates a decimal character, and will match a 0,1,2,3,4,5,6,7,8, or 9.  The three in brackets `{3}` is a quantifier, indicating there should be three of the proceeding character - so three decimal characters.  And the dash (`-`) matches the actual dash character.

## Writing Regular Expressions and Scriptular 

As you can see, regular expressions make use of a decent number of special characters, and can be tricky to write.  One of the greatest tools in your arsenal when dealing with Regular Expressions is the web app <a href="https://scriptular.com/" target="_blank">Scriptular.com</a> (click the link to open it in a new tab).  It lists characters with special meanings for regular expressions on the right, and provides an interactive editor on the left, where you can try out regular expressions against target text. 

You can, of course, do the same thing on the console, but I find that using Scriptular to prototype regular expressions is faster.  You can also clone the [Scriptular Github repo](https://github.com/jonmagic/scriptular) and use it locally rather than on the internet.  A word of warning, however, always test your regular expressions in the context you are going to use them - sometimes something that works in Scriptular doesn't quite in the field (especially with older browsers and Node versions).

## Regular Expressions and Input Validation

So how are regular expressions used in Web Development?  One common use is to _validate_ user input - to make sure the user has entered values in the format we want.  To see if a user entered string matches the phone format we declared above, for example, we can use the [RegExp.prototype.test()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test) method.  It returns the boolean `true` if a match is found, `false` otherwise:

```js
if(/\d{3}-\d{3}-\d{4}/.test(userEnteredString)) {
  console.log("String was valid");
} else {
  console.log("String was Invalid");
}
```

But what if we wanted to allow phone numbers in more than one format?  Say X-XXX-XXX-XXXX, (XXX)XXX-XXXX, and X(XXX)XXX-XXXX)?

We can do this as well:

```js
/\d?-?\d{3}-\d{3}-\d{4}|\d?\s?\(\d{3}\)\s?\d{3}-\d{4}/
```

The pipe (`|`) in the middle of the RexExp acts like an OR; we can match against the pattern before OR the pattern after.  The first pattern is almost the same as the one we started with, but with a new leading `\d` and `-`.  These use the quantifier `?`, which indicates 0 or 1 instances of the character.

The second pattern is similar, except we use a backslash s (`/s`) to match whitespace characters (we could also use the literal space ` `, `\s` also matches tabs and newlines).  And we look for parenthesis, but as parenthesis have special meaning for RegExp syntax, we must escape them with a backslash: (`\(` and `\)`). 


## Regular Expressions and Form Validation

In fact, the use of Regular Expressions to validate user input is such a common use-case that when HTML5 introduced [form data validation](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Form_validation) it included the `pattern` attribute for HTML5 forms.  It instructs the browser to mark a form field as invalid unless input matching the pattern is entered.  Thus, the HTML:

```html 
<label for="phone">Please enter a phone number
  <input name="phone" pattern="\d{3}-\d{3}-\d{4}" placeholder="xxx-xxx-xxxx">
</label>
```

Will ensure that only validly formatted phone numbers can be submitted. Also, note that we omitted the leading and trailing forward slashes (`/`) with the `pattern` attribute.

However, be aware that older browsers may not have support for [HTML5 form data validation](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Form_validation) (though all modern ones do), and that a savvy user can easily disable HTML5 form validation with the Developer Tools.  Thus, you should aways validate on both the client-side (for good user experience) _and_ the server-side (to ensure clean data).  We'll discuss data validation more in our chapter on persisting data on the server.

## Constructing RegExp

Besides using literal notation, We can also [construct regular expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) from a string of characters:

```js
var regexp = new RegExp("\d{3}-\d{3}-\d{4}")
```

This is especially useful if we won't know the pattern until runtime, as we can create our regular expression "on the fly."

## RegExp flags

You can also specify one or more flags when defining a JavaScript Regular Expression, by listing the flag after the literal, i.e. in the RegExp:

```js
/\d{3}-\d{3}-\d{4}/g 
```

The flag `g` means _global_, and will find _all_ matches, not just the first.  So if we wanted to find all phone numbers in a body of text, we could do:

```js
/\d{3}-\d{3}-\d{4}/g.match(bodyOfText);
```

Here the [RegExp.prototype.match()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match) function returns an array of phone numbers that matched the pattern and were found in `bodyOfText`.

The flags defined for JavaScript regular expressions are:

* `g` global match - normally RegExp execution stops after the first match.
* `i` ignore case - upper and lowercase versions of a letter are treated equivalently
* `m` multiline - makes the beginning end operators (`^` and `$`) operate on lines rather than the whole string. 
* `s` dotAll - allows `.` to match newlines (normally `.` is a wildcard matching everything _but_ newline characters)
* `u` unicode - treat pattern as a sequence of unicode code points 
* `y`sticky - matches only from the `lastIndex` property of the Regular Expression

## Capture Groups 

We saw above how we can retrieve the strings that matched our regular expression patterns
Matching patterns represents only _part_ of the power of regular expressions.  One of the most useful features is the ability to _capture_ pieces of the pattern, and expose them to the programmer.  

Consider, for example, the common case where we have a comma delimited value (CSV) file where we need to tweak some values.  Say perhaps we have one like this:

```txt 
Name,weight,height
John Doe,150,6'2"
Sara Smith,102,5'8"
"Mark Zed, the Third",250,5'11"
... 100's more values....
```

which is part of a scientific study where they need the weight in Kg and the height in meters.  We could make the changes by hand - but who wants to do that?  We could also do the changes by opening the file in Excel, but that would also involve a lot of copy/paste and deletion, opening the door to human error. Or we can tweak the values with JavaScript. 

Notice how the Mark Zed entry, because it has a comma in the name, is wrapped in double quotes, while the other names aren't?  This would make using something like [String.prototype.split()]() impossible to use without a ton of additional logic, because it splits on the supplied delimiter (in this case, a comma), and would catch these additional commas.  However, because a RegExp matches a _pattern_, we can account for this issue.  

But we want to go one step farther, and _capture_ the weight and height values.  We can create a _capture group_ by surrounding part of our pattern with parenthesis, i.e. the RegExp:

```js
/^([\d\s\w]+|"[\d\s\w,]+"),(\d+),(\d+'\d+)"$/gm
```

Will match each line in the file.  Let's take a look at each part:

`/^ ... $/mg` the `m` flag indicates that `^` and `$` should mark the start and end of each line.  This makes sure we only capture values from the same line as par to a match, and the `g` flag means we want to find all matching lines in the file.

`([\d\s\w]+|"[\d\s\w,]+")` is our first capture group, and we see it has two options (separated by `|`).  The square brackets (`[]`) represent a set of characters, and we'll match any character(s) listed inside.  So `[\d\s\w]` means any decimal (`\d`), whitespace (`\s`), or word (`\w`) character, and the `+` means one or more of these.  The second option is _almost_ the same as the first, but surrounded by double quotes (`"`) and includes commas (`,`) in the set of matching characters.  This means the first group will always match our name field, even if it has commas.

`,(\d+),` is pretty simple - we match the comma between name and weight columns, capture the weight value, and then the comma between weight and height.

`(\d+'\d+)"` is a bit more interesting.  We capture the feet value (`\d+`), the apostrophe (`'`) indicating the unit of feet, and the inches value (`\d+`).  While we match the units for inches (`"`), it is not part of the capture group.

So our line-by-line captures would be:

<pre>
Line 0: No match
Line 1: John Doe, 150, 6'2
Line 2: Sara Smith, 102, 5'8
Line 3: "Mark Zed, the Third", 250, 5'11
</pre>

We can use this knowledge with [String.prototype.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) to reformat the values in our file.  The `replace()` can work as you are probably used to - taking two strings - one to search for and one to use as a replacement.  But it can also take a RegExp as a _pattern_ to search for and replace.  And the replacement value can also be a _function_, which receives as its parameters 1) the full match to the pattern, and 2) the capture group values, as subsequent parameters.  

Thus, for the Line 1 match, it would be invoked with parameters: `("John Doe,150,6'2\"", "John Doe", "150", "6'2\"")`.  We can use this understanding to write our conversion function:

```js
function convertRow(match, name, weight, height) {
  
   // Convert weight from lbs to Kgs 
   var lbs = parseInt(weight, 10);
   var kgs = lbs / 2.205;
  
   // Convert height from feet and inches to meters 
   var parts = height.split("'");
   var feet = parseInt(parts[0], 10);
   var inches = parseInt(parts[1], 10);
   var totalInches = inches + 12 * feet;
   var meters = totalInches * 1.094;
  
   // Return the new line values:
   return `${name},${kgs},${meters}`;
}
```

And now we can invoke that function as part of [String.prototype.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) on the body of the file:

```js
var newBody = oldBody.replace(/^([\d\s\w]+|"[\d\s\w,]+"),(\d+),(\d+'\d+)"$/gm, convertRow);
```

And our `newBody` variable contains the revised file body (we'll talk about how to _get_ the file body in the first place, either in the browser or with Node, later on).

