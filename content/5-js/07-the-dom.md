---
title: "The Document Object Model"
pre: "7. "
weight: 70
date: 2018-08-24T10:53:26-05:00
---

Now that we've reviewed the basic syntax and structure of the JavaScript language, and how to load it into a page, we can turn our attention to what it was created for - to interact with web pages in the browser.  This leads us to the _Document Object Model (DOM)_.

The DOM is a tree-like structure that is created by the browser when it parses the HTML page.  Then, as CSS rules are interpreted and applied, they are attached to the individual nodes of the tree.  Finally, as the page's JavaScript executes, it may modify the tree structure and node properties.  The browser uses this structure and properties as part of its rendering process.

## The Document Instance 
The DOM is exposed to JavaScript through an instance of the [Document](https://developer.mozilla.org/en-US/docs/Web/API/Document) class, which is attached to the `document` property of the window (in the browser, the window is the top-level, a.k.a global scope.  Its properties can be accessed with or without referencing the `window` object, i.e. `window.document` and `document` refer to the same object).

This document instance serves as the entry point for working with the DOM.

## The Dom Tree
The DOM tree nodes are instances of the [Element](https://developer.mozilla.org/en-US/docs/Web/API/Element) class, which extends from the [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node) class, which in turn extends the [EventTarget](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget) class. This inheritance chain reflects the [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns) design principle: the EventTarget class provides the functionality for responding to events, the Node class provides for managing and traversing the tree structure, and the Element class maintains the element's appearance and properties. 

<div id="interfaceDiagram" style="display: inline-block; position: relative; width: 100%; padding-bottom: 11.666666666666666%; vertical-align: middle; overflow: hidden;"><svg style="display: inline-block; position: absolute; top: 0; left: 0;" viewBox="-50 0 600 70" preserveAspectRatio="xMinYMin meet"><a xlink:href="https://developer.mozilla.org/en-US/docs/Web/API/EventTarget" target="_top"><rect x="1" y="1" width="110" height="50" fill="#fff" stroke="#D4DDE4" stroke-width="2px"></rect><text x="56" y="30" font-size="12px" font-family="Consolas,Monaco,Andale Mono,monospace" fill="#4D4E53" text-anchor="middle" alignment-baseline="middle">EventTarget</text></a><polyline points="111,25  121,20  121,30  111,25" stroke="#D4DDE4" fill="none"></polyline><line x1="121" y1="25" x2="151" y2="25" stroke="#D4DDE4"></line><a xlink:href="https://developer.mozilla.org/en-US/docs/Web/API/Node" target="_top"><rect x="151" y="1" width="75" height="50" fill="#fff" stroke="#D4DDE4" stroke-width="2px"></rect><text x="188.5" y="30" font-size="12px" font-family="Consolas,Monaco,Andale Mono,monospace" fill="#4D4E53" text-anchor="middle" alignment-baseline="middle">Node</text></a><polyline points="226,25  236,20  236,30  226,25" stroke="#D4DDE4" fill="none"></polyline><line x1="236" y1="25" x2="266" y2="25" stroke="#D4DDE4"></line><a xlink:href="https://developer.mozilla.org/en-US/docs/Web/API/Element" target="_top"><rect x="266" y="1" width="75" height="50" fill="#F4F7F8" stroke="#D4DDE4" stroke-width="2px"></rect><text x="303.5" y="30" font-size="12px" font-family="Consolas,Monaco,Andale Mono,monospace" fill="#4D4E53" text-anchor="middle" alignment-baseline="middle">Element</text></a></svg></div>

### Selecting Elements on the Page 
One of the most important skills in working with the DOM is understanding how to get a reference to an element on the page.  There are many approaches, but some of the most common are:

#### Selecting an Element by its ID
If an element has an `id` attribute, we can select it with the [Document.getElementByID()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById) method.  Let's select our button this way. Add this code to your _playground.js_ file:

```js
var button = document.getElementById("some-button");
console.log(button);
```

You should see the line `[object HTMLButtonElement]` - the actual instance of the DOM node representing our button (the class HTMLButtonElement is an extension of Element representing a button).

#### Selecting a Single Element by CSS Selector
While there are additional selectors for selecting by tag name, class name(s), and other attributes, in practice these have largely been displaced by functions that select elements using a CSS selector.  

[Document.querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) will return the _first_ element matching the CSS selector, i.e.:

```js
var button = document.querySelector('#some-button');
```

Works exactly like the `document.getElementById()` example. But we could also do:

```js 
var input = document.querySelector('input[type=text]');
```

Which would grab the first `<input>` with attribute `type=text`.  

#### Selecting Multiple Elements by CSS Selector 
But what if we wanted to select more than one element at a time?  Enter [document.querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll).  It returns a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) containing all matching nodes.  So the code:

```js
var paras = document.querySelectorAll('p.highlight');
```

Will populate the variable `paras` with a `NodeList` containing all `<p>` elements on the page with the highlight class.

{{% notice warning %}}
While a `NodeList` is an iterable object that behaves much like an array, it is not an array.  Its items can also be directly accessed with bracket notation (`[]`) or [NodeList.item()](https://developer.mozilla.org/en-US/docs/Web/API/NodeList/item).  It can be iterated over with a `for .. of` loop, and in newer browsers, [NodeList.forEach()](https://developer.mozilla.org/en-US/docs/Web/API/NodeList/forEach).  Alternatively, it can be converted into an array with [Array.from()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from).  
{{% /notice %}}

#### Element.querySelector() and Element.querySelectorAll()
The query selector methods are also implemented on the element class, with [Element.querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Element/querySelector) and [Element.querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Element/querySelectorAll).  Instead of searching the entire document, these only search their descendants for matching elements.

### Events
Once we have a reference to an element, we can add an event listener with [EventTarget.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener).  This takes as its first argument, the name of the event to listen for, and as the second, a method to invoke when the event occurs.  There are additional optional arguments as well (such as limiting an event listener to firing only once), see the MDN documentation for more details.

For example, if we wanted to log when the user clicks our button, we could use the code:

```js
document.getElementById("some-button").addEventListener('click', function(event) {
  event.preventDefault();
  console.log("Button was clicked!");
});
```

Notice we are once again using method chaining - we could also assign the element to a `var` and invoke `addEventListener()` on the variable.  The event we want to listen for is identified by its name - the string `'click'`.  Finally, our event handler function will be invoked with an event object as its first argument.  

Also, note the use of `event.preventDefault()`.  Invoking this method on the event tells it that we are taking care of its responsibilities, so no need to trigger the default action. If we don't do this, the event will continue to bubble up the DOM, triggering any additional event handlers.  For example, if we added a `'click'` event to an `<a>` element and did not invoke `event.preventDefault()`, when we clicked the `<a>` tag we would run our custom event handler and then the browser would load the page that the `<a>` element's `href` attribute pointed to.

#### Common Event Names
The most common events you'll likely use are 
* `"click"` triggered when an item is clicked on
* `"input"` triggered when an input element receives input
* `"change"` triggered when an input's value changes 
* `"load"` triggered when the source of a image or other media has finished loading
* `"mouseover"` and `"mouseout"` triggered when the mouse moves over an element or moves off an element
* `"mousedown"` and `"mouseup"` triggered when the mouse button is initially pressed and when it is released (primarily used for drawing and drag-and-drop)
* `"mousemove"` triggered when the mouse moves (used primarily for drawing and drag-and-drop)
* `"keydown"`, `"keyup"`, and `"keypressed"` triggered when a key is first pushed down, released, and held.

Note that the mouse and key events are only passed to elements when they have _focus_.  If you want to always catch these events, attach them to the `window` object.

There are many more events - refer to the MDN documentation of the specific element you are interested in to see the full list that applies to that element.

#### Event Objects
The function used as the event handler is invoked with an object representing the event.  In most cases, this is a descendant class of [Event](https://developer.mozilla.org/en-US/docs/Web/API/Event) that has additional properties specific to the event type.  Let's explore this a bit with our text input.  Add this code to your _playground.js_, reload the page, and type something into the text input:

```js 
document.getElementById("some-input").addEventListener("input", function(event) {
  console.log(event.target.value);
});
```

Here we access the event's `target` property, which gives us the target element for the event, the original `<input>`.  The input element has the `value` property, which corresponds to the `value` attribute of the HTML that was parsed to create it, and it changes as text is entered into the `<input>`.

### Modifying DOM Element Properties
One of the primary uses of the DOM is to alter properties of [element](https://developer.mozilla.org/en/docs/Web/API/Element) objects in the page. Any changes to the DOM structure and properties are almost immediately applied to the appearance of the web page. Thus, we use this approach to alter the document in various ways.

#### Attributes
The attributes of an HTML element can be accessed and changed through the DOM, with the methods [element.getAttribute()](https://developer.mozilla.org/en/docs/Web/API/Element/getAttribute), [element.hasAttribute()](https://developer.mozilla.org/en-US/docs/Web/API/Element/hasAttribute) and [element.setAttribute()](https://developer.mozilla.org/en/docs/Web/API/Element/setAttribute).

Let's revisit the button in our playground, and add an event listener to change the input element's `value` attribute:

```js
document.getElementById("some-button").addEventListener("click", function(event) {
  document.getElementById("some-input").setAttribute("value", "Hello World!")
});
```

Notice too that _both_ event handlers we have assigned to the button trigger when you click it.  We can add as many event handlers as we like to a project.

#### Styles
The [style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style) property provides access to the element's inline styles.  Thus, we can set style properties on the element:

```js
document.getElementById("some-button").style = "background-color: yellow";
```

Remember from our discussion of the CSS cascade that inline styles have the highest priority.

#### Class Names
Alternatively, we can change the CSS classes applied to the element by changing its [element.classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList) property, which is an instance of a DOMTokensList, which exposes the methods:

* `add()` which takes one or more string arguments which are class names added to the class list
* `remove()` which takes one or more string arguments which are class names removed from the class list
* `toggle()` which takes one or more strings as arguments and toggles the class name in the list (i.e. if the class name is there, it is removed, and if not, it is added)

By adding, removing, or toggling class names on an element, we can alter what CSS rules apply to it based on its CSS selector.

### Altering the Document Structure
Another common use for the DOM is to add, remove, or relocate elements in the DOM tree.  This in turn alters the page that is rendered.  For example, let's add a paragraph element to the page just after the `<h1>` element:

```js
var p = document.createElement('p');
p.innerHTML = "Now I see you";
document.body.insertBefore(p, document.querySelector('h1').nextSibling);
```

Let's walk through this code line-by-line.
1. Here we use [Document.createElement()](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) to create a new element for the DOM.  At this point, the element is _unattached_ to the document, which means it will not be rendered.  
2. Now we alter the new `<p>` tag, adding the words `"Now I see you"` with the [Element.innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) property.
3. Then we attach the new `<p>` tag to the DOM tree, using [Node.insertBefore()](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore) method and [Node.nextSibling](https://developer.mozilla.org/en-US/docs/Web/API/Node/nextSibling) property.

The [Node](https://developer.mozilla.org/en-US/docs/Web/API/Node) interface provides a host of properties and methods for traversing, adding to, and removing from, the DOM tree.  Some of the most commonly used are:
* [Node.parent](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentNode) the parent of this Node 
* [Node.childNodes](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes) a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) of this node's children
* [Node.nextSibling](https://developer.mozilla.org/en-US/docs/Web/API/Node/nextSibling) returns the node following this one at the same level in the DOM tree
* [Node.previousSibling](https://developer.mozilla.org/en-US/docs/Web/API/Node/previousSibling) returns the node proceeding this one in the DOM tree at the same level
* [Node.appendChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) adds the an element as the last child of the node
* [Node.removeChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild) removes a child from the node and returns it (this means the element becomes _unattached_)
* [Node.replaceChild()](https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild) replaces a child element with another

