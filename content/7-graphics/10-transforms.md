---
title: "Transforms and State"
pre: "10. "
weight: 100
date: 2018-08-24T10:53:26-05:00
---

Much like we can use CSS to apply transformations to HTML elements, we can use transforms to change how we draw into a canvas. The rendering context has a transformation matrix much like those we discussed in the CSS chapter, and it applies this transform to any point it is tasked with drawing.

We can replace the current transformation matrix with the `setTransform()` function, or multiply it by a new transformation (effectively combining the current transformation with the new one) by calling `transform()`. 

With this in mind, it can be useful to know two other functions of the context, `save()` and `restore()`.  These save the current context state by pushing and popping from a stack.  Think of it as a pile of papers. When we call `save()` we write down the current state of the context object, and drop that paper in the stack.  When we call `restore()`, we take the topmost paper from the stack, and set context's state back to what was written on that sheet.

So what exactly constitutes the state of our rendering context? As you might imagine, this includes the transformation matrix we just talked about.  But it _also_ includes all of the stroke and fill properties.

Now, back to the transforms.  As with CSS transforms, we can define the matrix ourselves, but there also exist a number of helper functions we can leverage, specifically:

* `translate(tx, ty)` translates by `tx` in the x axis, and `ty` along the y
* `rotate(angle)` rotates around the z-axis by the supplied `angle` (specified in radians)
* `scale(sx,sy)` scales by `sx` along the x axis, and `sy` along the y axis. This is expressed as a decimal value: `1.0` indicates 100%, `0.5` for 50%, and `1.75` for 175%

<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.font = "40pt Tahoma";
  var metrics = ctx.measureText("Hello Canvas");
  var tx = 100 + metrics.width / 2;
  var ty = 180;
  
  ctx.translate(tx, ty);
  ctx.rotate(Math.PI/4);
  ctx.translate(-tx, -ty);

  ctx.strokeText("Hello Canvas", 100, 180);
</script>

```html
<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.font = "40pt Tahoma";
  var metrics = ctx.measureText("Hello Canvas");
  var tx = 100 + metrics.width / 2;
  var ty = 180;
  
  ctx.translate(tx, ty);
  ctx.rotate(Math.PI/4);
  ctx.translate(-tx, -ty);

  ctx.strokeText("Hello Canvas", 100, 180);
</script>
```

{{% notice info %}}
In this example, we translate the text so that its center is at the origin _before_ we rotate it, then translate it back. As any rotation we specify is around the origin, this makes it so the text is rotated around its center and stays on canvas, rather than rotating off the canvas.

Also notice that we call the transformation functions in the _opposite_ order we want them applied.  
{{% /notice %}}