---
title: "Canvas and Images"
pre: "9. "
weight: 90
date: 2018-08-24T10:53:26-05:00
---

The `<canvas>` and `<img>` elements are both raster representations of graphics, which introduces an interesting possibility - copying the data of an image into the canvas.  This can be done with the `drawImage()` family of functions.

The first of these is `drawImage(image, x, y)`. This copies the entire image held in the `image` variable onto the canvas, starting at (`x`, `y`). 

<canvas id="image-example-1" width="500" height="300"></canvas>
<script>
  var canvas1 = document.getElementById('image-example-1');
  var ctx1 = canvas1.getContext('2d');
  var image1 = new Image();
  image1.onload = function() {
    ctx1.drawImage(image1, 0, 0);
  }
  image1.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>

```html
<canvas id="image-example-1" width="500" height="300"></canvas>
<script>
  var canvas1 = document.getElementById('image-example-1');
  var ctx1 = canvas1.getContext('2d');
  var image1 = new Image();
  image1.onload = function() {
    ctx1.drawImage(image1, 0, 0);
  }
  image1.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>
```

The second, `drawImage(image, x, y, width, height)` scales the image as it draws it.  Again the image is drawn starting at (`x`,`y`) but is scaled to be `width` x `height`.

<canvas id="image-example-2" width="500" height="300"></canvas>
<script>
  var canvas2 = document.getElementById('image-example-2');
  var ctx2 = canvas2.getContext('2d');
  var image2 = new Image();
  image2.onload = function() {
    ctx2.drawImage(image2, 0, 0, 300, 300);
  }
  image2.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>

```html
<canvas id="image-example-2" width="500" height="300"></canvas>
<script>
  var canvas2 = document.getElementById('image-example-2');
  var ctx2 = canvas2.getContext('2d');
  var image2 = new Image();
  image2.onload = function() {
    ctx2.drawImage(image2, 0, 0, 300, 300);
  }
  image2.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>
```

The third, `drawImage(image, sx, sy, sWidth, sHeight, x, y, width, height)` draws a sub-rectangle of the source image. The source sub-rectangle starts at point (`sx`, `sy`) and has dimensions `sWidth` x `sHeight`. It draws the contents of the source rectangle into a rectangle in the canvas starting at (`dx`,`dy`) and scaled to dimensions `dWidth` x `dHeight`.

<canvas id="image-example-3" width="500" height="300"></canvas>
<script>
  var canvas3 = document.getElementById('image-example-3');
  var ctx3 = canvas3.getContext('2d');
  var image3 = new Image();
  image3.onload = function() {
    ctx3.drawImage(image3, 200, 200, 300, 300, 0, 0, 300, 300);
  }
  image3.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>

```html
<canvas id="image-example-3" width="500" height="300"></canvas>
<script>
  var canvas3 = document.getElementById('image-example-3');
  var ctx3 = canvas3.getContext('2d');
  var image3 = new Image();
  image3.onload = function() {
    ctx3.drawImage(image3, 200, 200, 300, 300, 0, 0, 300, 300);
  }
  image3.src = "/cc120/images/rubber_duck_debugging.jpg";  
</script>
```

{{% notice warning %}}
If the image is not loaded when the `drawImage()` call is made, nothing will be drawn to the canvas.  This is why in the examples, we move the `drawImage()` call into the `onload` callback of the image - this function will only be invoked when the image finishes loading.
{{% /notice %}}