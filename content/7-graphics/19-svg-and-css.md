---
title: "SVG and CSS"
pre: "18. "
weight: 180
date: 2018-08-24T10:53:26-05:00
---

When using inline SVG, you can apply CSS to the SVG using any of the methods we've used with HTML - inline styles, the `<style>` element, or a CSS file. The rules work exactly the same - you select a SVG element using a CSS selector, and apply style rules.  SVG elements have tag name, and can also specify `id` and `class` attributes just like HTML. For example:

<style>
  rect {
    fill: purple;
    stroke: black;
    stroke-width: 5;
  }
  #my-circle {
    fill: violet;
    stroke: #333;
  }
</style>
<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg">
  <rect x="10" y="10" width="80" height="80"/>
  <circle id="my-circle" cx="200" cy="50" r="40"/>
</svg>

```html
<style>
  rect {
    fill: purple;
    stroke: black;
    stroke-width: 5;
  }
  #my-circle {
    fill: violet;
    stroke: #333;
  }
</style>
<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg">
  <rect x="10" y="10" width="80" height="80"/>
  <circle id="my-circle" cx="200" cy="50" r="40"/>
</svg>
```
