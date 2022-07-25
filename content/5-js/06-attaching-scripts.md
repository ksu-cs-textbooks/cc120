---
title: "Attaching Scripts"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---

Much like there are multiple ways to apply CSS to a web app, there are multiple ways to bring JavaScript into one.  We can use a `<script>` tag with a specified `src` attribute to load a separate document, put our code into the `<script>` tag directly, or even add code to attributes of an HTML element.  Let's look at each option.

## Script Tag with Source
We can add a `<script>` tag with a `src` attribute that gives a url pointing to a JavaScript file.  This is similar to how we used the `<link>` element for CSS:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JS Example</title>
  </head>
  <body>
    <script src="example.js"></script>
  </body>
</html>
```

A couple of important differences though.  First, the `<script>` element is not a void tag, so we a closing `</script>`.  Also, while traditionally we would also place `<script>` elements in the `<head>`, current best practice is to place them as the last children of the `<body>` element.

## Script Tag with Content 
The reason the `<script>` element isn't a void element is that you can place JavaScript code directly into it - similar to how we used the `<style>` element for CSS.  Typically we would also place this tag at the end of the body:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>JS Example</title>
  </head>
  <body>
    <script>
      console.log(1 + 3);
    </script>
  </body>
</html>
```

## Why at the End of the Body?
The reason for placing `<script>` tags at the end of the body is twofold. First, JavaScript files have grown increasingly large as web applications have become more sophisticated.  And as they are parsed, there is no visible sign of this in the browser - so it can make your website appear to load more slowly when they are encountered in the `<head>` section.  Second, JavaScript is interpreted as it is loaded - so if your code modifies part of the web page, and tries to do so before the webpage is fully loaded, it may fail.

A good trick is to place any code that should not be run until all the web pages' assets have been downloaded within the body of an event handler tied to the `'load'` event, i.e.

```js
window.addEventListener('load', function() {
  
  // Put any JavaScript that should not be
  // run until the page has finished loading 
  // here..
  
});
```

## As an Attribute
A third alternative is to define our JavaScript as an [on-event handler](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Event_handlers) directly on an element.  For example:

```html 
<button onclick="console.log(1+3)">click me</button>
```

This once-common strategy has fallen out of favor as it does not provide for good separation of concerns, and can be difficult to maintain in large HTML files.  Also, only one event handler can be set using this approach; we'll see an alternative method, [Element.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) in the next section that is more powerful.

However, component-based development approaches like React's JSX make this approach more sensible, so it has seen some resurgence in interest.

## Mix-and-Match
It is important to understand that all JavaScript on a page is interpreted within the same scope, regardless of what file it was loaded from.  Thus, you can invoke a function in one file that was defined in a separate file - this is commonly done when incorporating JavaScript libraries like JQuery.  

{{% notice warning %}} 
There is one aspect you need to be aware of though.  Before you reference code artifacts like functions and variables, they must have been loaded in the interpreter.  If you are using external files, these have to be retrieved by the browser as a separate request, and even though they may be declared in order in your HTML, they may be received out of order, and they will be interpreted _in the order they are received_

There are a couple of strategies that can help here.  First, you can use the window's `load` event as we discussed above to avoid triggering any JavaScript execution until all the script files have been loaded.  And second, we can combine all of our script files into one single file (a process known as _concatenation_).  This is often done with a build tool that also _minifies_ the resulting code.  We'll explore this strategy later in the course.
{{% /notice %}}