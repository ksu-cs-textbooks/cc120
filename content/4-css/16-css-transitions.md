---
title: "CSS Transitions"
pre: "16. "
weight: 160
date: 2018-08-24T10:53:26-05:00
---

While most CSS rules are applied as the page is loaded, some are applied at a future point.  One example is pseudo-classes that apply in limited circumstances - like `:hover` which applies only when the mouse is over an element, or `:valid` and `:invalid` which are applied to input elements based on their validation status. Another common instance is when elements are added to the page using JavaScript, as discussed in [Chapter 5 - JavaScript]({{% ref "5-js"  %}}).

In these instances, we may want the change in styling rules to not apply instantly, but rather transition between states over a short duration. The `transition` property provides us this functionality.  It has three sub-properties:

* `transition-property` - the property or properties to transition. This can include any of the CSS properties that are defined as being animatible (basically those that have continuous values).
* `transition-duration` - how long the transition should take, expressed in seconds or milliseconds.
* `transition-timing-function` - one of several timing functions that define how the value transitions over time

We can also express all three with the shorthand `transition: [property] [duration] [timing-function].

Let's see an example:

```html
<div class="transition-example">Hover over me!</div>
```
```css
div.transition-example {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  transition: background-color 1s ease;
}
div.transition-example:hover {
  background-color: #A7A7A7;
}
```
<div class="transition-example">Hover over me!</div>
<style>
div.transition-example {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  transition: background-color 1s ease;
}
div.transition-example:hover {
  background-color: #A7A7A7;
}
</style>

We can combine multiple transitions by providing a comma-separated list to the `transition` shorthand property: 

```html
<div class="transition-example-2">Hover over me!</div>
```
```css
div.transition-example-2 {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  font-size: 1.5rem;
  transition: background-color 1s ease, font-size 2s linear;
}
div.transition-example-2:hover {
  background-color: #A7A7A7;
  font-size: 1rem;
}
```
<div class="transition-example-2">Hover over me!</div>
<style>
div.transition-example-2 {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  font-size: 1.5rem;
  transition: background-color 1s ease, font-size 2s linear;
}
div.transition-example-2:hover {
  background-color: #A7A7A7;
  font-size: 1rem;
}
</style>

Alternatively, we can define multiple transitions with the sub-properties.  In this case, the `transition-property` is a comma-separated list, and the _same_ `transition-duration` and `transition-timing-function` apply to all specified properties:

```html
<div class="transition-example-3">Hover over me!</div>
```
```css
div.transition-example-3 {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  font-size: 1.5rem;
  transition-property: background-color, font-size;
  transition-duration: 500ms;
  transition-timing-function: ease-in;
}
div.transition-example-3:hover {
  background-color: #A7A7A7;
  font-size: 1rem;
}
```
<div class="transition-example-3">Hover over me!</div>
<style>
div.transition-example-3 {
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 200px;
  height: 200px;
  background-color:#512888;
  font-size: 1.5rem;
  transition-property: background-color, font-size;
  transition-duration: 500ms;
  transition-timing-function: ease-in; linear;
}
div.transition-example-3:hover {
  background-color: #A7A7A7;
  font-size: 1rem;
}
</style>