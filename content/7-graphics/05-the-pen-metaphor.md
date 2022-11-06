---
title: "The Pen Metaphor"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---

Most 2D graphics libraries adopt a "pen" metaphor to model how they interact with the graphics they draw.  Think of an imaginary pen that you use to draw on the screen.  When you put the pen down and move it across the screen you draw a line - the _stroke_.  When you lift the pen, you no longer make a mark. The movements of the pen across the canvas also define a _path_.

There are a number of methods that move this imaginary pen:

* `moveTo(x, y)` picks up the imaginary pen and puts it back down at the position specified by `x` and `y`).
* `lineTo(x, y)` moves the imaginary pen across the canvas, drawing a line from its prior position to the position specified by `x` and `y`.
* `bezierCurveTo(c1x, c1y, c2x, c2y, x, y)` moves the imaginary pen across the canvas following a [Bezier curve](https://en.wikipedia.org/wiki/B%C3%A9zier_curve) defined by the starting point, control points `(c1x, c1y)`, `(c2x, c2y)`, and ending point `(x, y)`.
* `arc(x, y, radius, startAngle, endAngle)` draws an arc (a segment of a circle) centered at `(x,y)` with radius `radius` and starting at `startAngle` and ending at `endAngle` (both measured in radians with the positive x-axis representing 0 radians). An optional final boolean parameter `counterclockwise`  draws the arc counterclockwise instead of clockwise when `true`. 
* `arcTo(x, y, radius, startAngle, endAngle)` works as the `arc()` method, but it picks up the pen.

It is important to understand that the path defined by these methods does get drawn into the canvas until one or both of the context's `stroke()` or `fill()` functions is called. These methods apply to the current path of the pen - we can also begin a new path with the `beginPath()` function, which clears all of the previous path.  We can also make the path return to its starting point with the `closePath()` function.

We'll discuss stroke and fill next, but for now, here is an example of a canvas using the ideas we just discussed:

<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.beginPath();
  ctx.moveTo(100, 100);
  ctx.lineTo(100, 200);
  ctx.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx.arc(300, 200, 100, 0, Math.PI, true);
  ctx.closePath();
  ctx.stroke();
</script>

```html
<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.beginPath();
  ctx.moveTo(100, 100);
  ctx.lineTo(100, 200);
  ctx.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx.arc(300, 200, 100, 0, Math.PI, true);
  ctx.stroke();
</script>
```