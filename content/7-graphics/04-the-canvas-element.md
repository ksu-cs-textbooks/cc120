---
title: "The Canvas Element"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

The `<canvas>` element represents a raster graphic, much like the `<img>` element.  But instead of representing an existing image file, the `<canvas>` is a blank slate - a grid of pixels on which you can draw using JavaScript.  Becuase a canvas doesn't determine its size from an image file, you need to _always_ declare it with a `width` and `height` attribute (otherwise, it has a width and height of 0):

```html
<div style="border 1px solid gray">
  <canvas id="example-canvas-1" width=400 height=200></canvas>
  <button onclick="fillCanvas">Fill Canvas<button>
  <button onclick="clearCanvas">Clear Canvas</button>
</div>
```

<div style="border 1px solid gray">
  <canvas id="example-canvas" width=400 height=200></canvas>
  <br>
  <button id="fill-canvas">Fill Canvas</button>
  <button id="clear-canvas">Clear Canvas</button>
</div>
<script>
  var canvas = document.getElementById('example-canvas');
  var ctx = canvas.getContext('2d');
  document.getElementById('fill-canvas').addEventListener('click', (event) => {
    ctx.fillStyle = '#f99';
    ctx.fillRect(0, 0, 200, 400);
  });
  document.getElementById('clear-canvas').addEventListener('click', (event) => {
    ctx.clearRect(0, 0, 200, 400);
  });
</script>

You probably noticed that there appears to be nothing on the page above - but our canvas is there, it is just empty! Clicking the Fill button will fill it with a solid color, and the Clear button will erase it. So how does this work?

To draw into a canvas, we also need a _context_, a JavaScript object that allows us to draw onto the canvas. We'll specifically be using the `CanvasRenderingContext2D`. To get one, we:

1. Get a reference to the `canvas` object
2. Call its `getContext()` method with an argument of `'2d'` 

The JavaScript to do so looks like:

```js
var canvas = document.getElementById('example-canvas-1');
var ctx = canvas.getContext('2d');
```

Once we have the context, we can draw onto the canvas using one of its many commands 


```js
function fillCanvas() {
  ctx.fillRect(0, 0, 200, 400);
}
```

The result can be seen in the canvas above. Next, let's discuss how the canvas element and context work together.