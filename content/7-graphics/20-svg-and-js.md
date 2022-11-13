---
title: "SVG and JavaScript"
pre: "18. "
weight: 180
date: 2018-08-24T10:53:26-05:00
---

Likewise, inline SVG elements are part of the DOM tree, and can be manipulated with JavaScript in _almost_ the same way as any HTML element. You can retrieve a SVG node with the various query methods: `document.getElementsByName(name)`, `document.getElementById(id)`, `document.getElementsByClassName(className)`, `document.querySelector()`, and `document.querySelectorAll(selector)`. This works just like it does with HTML elements.

However, to work with the attributes of a SVG element, you must use the `setAttributeNS(ns, attr)` and `getAttributeNS(ns, attr)` respectively, as the SVG attributes are part of the SVG namespace, _not_ the HTML (default) namespace. 

The example below uses JavaScript to resize the circle based on a HTML `<input>` element:

<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg">
  <circle id="my-circle" cx="150" cy="50" r="40" fill="rgb(121, 60, 204)"/>
</svg>
<input id="radius-input" type="number" value="50" max="100" min="0">
<script>
  var input = document.getElementById('radius-input');
  input.addEventListener('change', function(event)
  {
    event.preventDefault();
    var radius = event.target.value;
    var circle = document.getElementById('my-circle');
    circle.setAttributeNS(null, 'r', radius);
  });
</script>

```html
<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg">
  <circle id="my-circle" cx="150" cy="50" r="40"/>
</svg>

<input id="radius-input" type="number" value="50" max="100" min="0" fill="rgb(121, 60, 204)">

<script>
  var input = document.getElementById('radius-input');
  input.addEventListener('change', function(event)
  {
    event.preventDefault();
    var radius = event.target.value;
    var circle = document.getElementById('my-circle');
    circle.setAttributeNS(null, 'r', radius);
  });
</script>
```

