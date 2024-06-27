---
title: "Shape Functions"
pre: "7. "
weight: 70
date: 2018-08-24T10:53:26-05:00
---

For ease of use, the context also supplies a number of functions for drawing shapes. Some of these just define the shape as a series of subpaths to be used with the `stroke()` and `fill()` functions.

## Arcs and Circles
Of these, we've already seen the `arc(x, y, radius, startAngle, endAngle)` function. It can be used to draw an arc, or when filled, a wedge - like a pie slice. When a `startAngle` of 0 and `endAngle` of `2 * Math.PI` is used, it instead draws a complete circle.

<canvas id="arc-example" width="500" height="200"></canvas>
<script>
  var canvas = document.getElementById('arc-example');
  var ctx = canvas.getContext('2d');
  
  ctx.strokeStyle = 'green';
  ctx.arc(100, 100, 50, 0, Math.PI * 2);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.fillStyle = 'purple';
  ctx.arc(250, 100, 50, 0, Math.PI * 2);
  ctx.fill();

  ctx.beginPath();
  ctx.moveTo(400, 100);
  ctx.arc(400, 100, 50, Math.PI, Math.PI / 4);
  ctx.stroke();
  ctx.fill();
</script>

```html
<canvas id="arc-example" width="500" height="200"></canvas>
<script>
  var canvas = document.getElementById('arc-example');
  var ctx = canvas.getContext('2d');
  
  ctx.strokeStyle = 'green';
  ctx.arc(100, 100, 50, 0, Math.PI * 2);
  ctx.stroke();
  
  ctx.beginPath();
  ctx.fillStyle = 'purple';
  ctx.arc(250, 100, 50, 0, Math.PI * 2);
  ctx.fill();

  ctx.beginPath();
  ctx.moveTo(400, 100);
  ctx.arc(400, 100, 50, Math.PI, Math.PI / 4);
  ctx.stroke();
  ctx.fill();
</script>
```

## Ellipse
There is also an `ellipse(x, y, radiusX, radiusY, startAngle, endAngle)` function. It works in a similar way, creating an ellipse centered on the point (`x`, `y`) with a horizontal radius of `radiusX` and a vertical radius of `radiusY`, and starting and ending angles of `startAngle` and `endAngle` (specified in radians).  As with the `arc()` method, a `startAngle` of 0 and `endAngle` of `2 * Math.PI` creates a full ellipse.

## Rectangle
The `rect(x, y, width, height)` function draws a rectangle with upper left corner at `(x, y)` and dimensions `width` and `height`. In addition to the `rect()` function, there are some shorthand functions that _also_ stroke or fill the rect _without altering the current path_.

The first of these is `fillRect(x, y, width, height)` which uses the same arguments as `rect()` and fills the resulting rectangle with the current fill style. We used this in the [introduction]({{% ref "7-graphics/01-introduction" %}}).

The second is the `clearRect(x, y, width, height)` function, which fills the rect defined by the arguments with _transparent black_ (`rgba(0,0,0,0)`), effectively erasing everything in that rectangle on the canvas.

{{% notice info %}}
Why the extra rectangle shorthands, and not other shapes? Remember, computer graphics have traditionally been _rectangular_, i.e. windows are rectangles. So programmers have gotten used to using rectangles in a lot of places, so having the extra shorthands made sense to the developers. Also, both `fillRect()` and `clearRect()` are used to quickly clear `<canvas>` elements of any prior drawing, especially when creating canvas animations.
{{% /notice %}}