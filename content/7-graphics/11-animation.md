---
title: "Animation"
pre: "11. "
weight: 110
date: 2018-08-24T10:53:26-05:00
---

The canvas element provides a powerful tool for creating animations by allowing us to erase and re-draw its contents over and over. Ideally, we only want to redraw the canvas contents only as quickly as the screen is updated (typically every 1/30th or 1/60th of a second).  The `window.requestAnimationFrame(callback)` provides an approach for doing this - it triggers the supplied callback every time the monitor refreshes.

Inside that callback, we want to erase the canvas and then draw the updated scene. Here is an example animating a ball bouncing around the canvas:

<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  var x = 100;
  var y = 100;
  var dx = Math.random();
  var dy = Math.random();
  
  function animate(timestamp)
  {
    ctx.fillStyle = 'pink';
    ctx.fillRect(0,0,500,300);
    ctx.fillStyle = 'blue';
    ctx.beginPath();
    ctx.arc(x, y, 25, 0, 2*Math.PI);
    ctx.fill();
    ctx.stroke();
    x += dx;
    y += dy;
    if(x < 25 || x > 475) dx = -dx;
    if(y < 25 || y > 275) dy = -dy;
    window.requestAnimationFrame(animate);
  }

  animate();

</script>

```html
<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  var x = 100;
  var y = 100;
  var dx = Math.random();
  var dy = Math.random();
  
  function animate(timestamp)
  {
    ctx.fillStyle = 'pink';
    ctx.fillRect(0,0,500,300);
    ctx.fillStyle = 'blue';
    ctx.beginPath();
    ctx.arc(x, y, 25, 0, 2*Math.PI);
    ctx.fill();
    ctx.stroke();
    x += dx;
    y += dy;
    if(x < 25 || x > 475) dx = -dx;
    if(y < 25 || y > 275) dy = -dy;
    window.requestAnimationFrame(animate);
  }

  animate();

</script>
```

{{% notice info %}}
On monitors with different refresh rates, the ball will move at a different speed. The callback function supplied to `requestAnimationFrame()` will receive a high-resolution timestamp (the current system time). You can save the previous timestamp and subtract it from the current time to determine how much time elapsed between frames, and use this to calculate your animations. An example doing this can be found in the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame).
{{% /notice %}}
