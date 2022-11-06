---
title: "Stroke and Fill"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---

The stroke and fill work with the current path of the context, defining how the outline and interior of a shape defined by the path are drawn.

## Stroke
The `stroke()` draws all of the path segments where the pen was "down".  The appearance of the stroke can be altered with specific properties of the canvas:

* `strokeStyle` allows you to set the color of the stroke, i.e. `ctx.strokeStyle = 'orange';`.  You can use one of the named colors, i.e. `'green'`, a hexidecimal value, i.e. `#fafafa`, one of the color functions `rgb(233,23,155)`, `rgba(23,23,23, 0.4)`, or a gradient or pattern (see more detail in the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/strokeStyle)).
* `lineWidth` allows you to set the width of the drawn line, in coordinate units (pixels of the canvas), i.e. `ctx.lineWidth = 3.0;` 
* `lineCap` defines what the end of a line looks like, `"Butt"` for a squared-off end, `"round"` for a rounded end, or `"square"` for a box with width and height equal to the line's thickness, centered on the end.
* `lineDashOffset` adds an offset to the first dash in a dashed line.  See the discussion of dashed lines below.

Lines can also be dashed. The nature of the dash is set wit the `setLineDash(segmentArray)` function of the context. The `segmentArray` is an array of distances which indicate the length of alternating lines and gaps forming the dash. For example:

```js
ctx.setLineDash([5, 4]);
```

Creates a dash pattern of 5 units of line followed by 4 units of space.  Then the pattern repeats, so another 5 units of line, and so on.

Let's redraw our previous shape with some changes to our stroke:

<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  ctx.strokeStyle = 'green';
  ctx.beginPath();
  ctx.moveTo(100, 100);
  ctx.lineTo(100, 200);
  ctx.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx.stroke();
  ctx.beginPath();
  ctx.strokeStyle = 'blue';
  ctx.setLineDash([5,2,1,2]);
  ctx.arc(300, 200, 100, 0, Math.PI, true);
  ctx.closePath();
  ctx.stroke();
</script>

```html
<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  ctx.strokeStyle = 'green';
  ctx.beginPath();
  ctx.moveTo(100, 100);
  ctx.lineTo(100, 200);
  ctx.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx.stroke();
  // begin a new path so a different line style is applied
  ctx.beginPath();
  ctx.strokeStyle = 'blue';
  ctx.setLineDash([5,2,1,2]);
  ctx.arc(300, 200, 100, 0, Math.PI, true);
  ctx.closePath();
  ctx.stroke();
</script>
```

{{% notice info %}}
Note how we added a `beginPath()` to change the line style, and also how that altered the behavior of the `closePath()` function (instead of closing with the original point of the first path, it closes with the first point of the second path).  When drawing complex shapes, you'll need to pay careful attention to your subpaths.
{{% /notice %}}

## Fill

The `fill()` function fills in the shape outlined by the path (both the parts where the pen was "down" and also "up"). The appearance of the fill can _also_ be altered with the `fillStyle` property of the canvas.

The `fillStyle` property allows you to change the color of the fill with one of several possible values: color i.e. `ctx.fillStyle='purple';`. It can use named colors (i.e. `'green'`), hexidecimal values (i.e. `#ffffdd`), one of the color functions (i.e. `rgb(0.4, 0.4. 0.9)`), a gradient, which can be linear, conic, or radial, or a pattern, such as repeating images.  You can find more about using each in the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle).

<canvas id="example-2" width="500" height="300"></canvas>
<script>
  var canvas2 = document.getElementById('example-2');
  var ctx2 = canvas2.getContext('2d');
  ctx2.fillStyle = 'purple';
  ctx2.moveTo(100, 100);
  ctx2.lineTo(100, 200);
  ctx2.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx2.arc(300, 200, 100, 0, Math.PI, true);
  ctx2.closePath();
  ctx2.fill();
</script>

```html
<canvas id="example-2" width="500" height="300"></canvas>
<script>
  var canvas2 = document.getElementById('example-2');
  var ctx2 = canvas2.getContext('2d');
  ctx2.fillStyle = 'purple';
  ctx2.moveTo(100, 100);
  ctx2.lineTo(100, 200);
  ctx2.bezierCurveTo(100, 300, 300, 300, 300, 200);
  ctx2.arc(300, 200, 100, 0, Math.PI, true);
  ctx2.closePath();
  ctx2.fill();
</script>
```