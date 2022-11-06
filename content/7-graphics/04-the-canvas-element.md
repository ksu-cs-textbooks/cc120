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

To draw into a canvas, we also need a _context_, a JavaScript object that allows us to draw onto the canvas. To get one, we:

1. Get a reference to the `canvas` object
2. Call its `getContext2d()` method

The JavaScript to do so looks like:

```js
var canvas = document.getElementById('example-canvas-1');
var ctx = canvas.getContext2d();
```

Once we have the context, we can draw onto the canvas using one of its many commands 


```js
function fillCanvas() {
  ctx.fillRect(0, 0, 200, 400);
}
```

The result can be seen in the canvas above.

## Path, Stroke, and Fill 

Before we get into the individual commands, we should take a moment to describe the model that the Canvas and 2D context use to render. The context uses a _pen_ metaphor - most of the commands you can call move the pen across the canvas, creating line segments. These segements are collectively known as the _path_ that can join up into a shape.  The line following the path is called the _stroke_, and the space inside the path is the _fill_.

We can control the color of the stroke through its `strokeStyle` property.  For example, to draw with a green line we would use `ctx.strokeStyle = "green";`. 

We can set 

The space inside the path is the _fill_, and we can control how it is drawn by modifying the `fillStyle` property. For filling the example canvas above, we used `ctx.fillStyle = "#f99";`. This 

We can provide color values for fill and stroke using a number of strategies: 
* The color name, i.e. `"limegreen"` - these are the same as the color names available in CSS.
* A hexidecimal color code, i.e. `"#FF0000"` for red.
* The `rgb()` function, i.e. `rgb(255,0,0)`, also red.
* The `rgba()` function, i.e. `rgba(255,0,0,0.5)`, for a semi-translucent red 

In addition to straight color, you can use gradients and patterns.  For these techniques, see the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors).

Additional properties for the stroke include:
* `lineWidth` - the width of the line, i.e. `ctx.lineWidth = 5;` sets the stroke to be 5 pixels wide

### Path Drawing




### Canvas Commands



