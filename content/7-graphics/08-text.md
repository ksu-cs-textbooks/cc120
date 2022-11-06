---
title: "Canvas Text"
pre: "8. "
weight: 80
date: 2018-08-24T10:53:26-05:00
---

While the canvas is primarily used to draw graphics, there are times we want to use text as well.  We have two methods to draw text: `fillText(text, x, y)` and `strokeText(text, x, y)`. The `text` parameter is the text to render, and the `x` and `y` are the upper left corner of the text.

As with the `fillRect()` and `strokeRect()` functions, `fillText()` and `strokeText()` fill and stroke the text, respectively, and the text does not affect the current path. The text properties are set by properties on the context:

* `font` is the font to use for the text. It uses the same syntax as the CSS font property. I.e. `ctx.font = 10pt Arial;`
* `textAlign` sets the alignment of the text. Possible values are `start`, `end`, `left`, `right`, or `center`.
* `textBaseline` sets the baseline alignment for the text. Possible values are `top`, `hanging`, `middle`, `alphabetic`, `ideographic`, or `bottom`.
* `direction` the directionality of the text. Possible values are `ltr` (left-to-right), `rtl` (right-to-left), and `inherit` (inherit from the page settings).

<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.font = "40pt symbol";
  ctx.strokeText("Foo", 100, 100);
  ctx.fillText("Bar", 100, 200);
</script>

```html
<canvas id="example" width="500" height="300"></canvas>
<script>
  var canvas = document.getElementById('example');
  var ctx = canvas.getContext('2d');
  
  ctx.font = "40pt symbol";
  ctx.strokeText("Foo", 100, 100);
  ctx.fillText("Bar", 100, 200);
</script>
```

{{% notice info %}}
Sometimes you might want to know how large the text will be rendered in the canvas.  The `measureText(text)` function returns a `TextMetrics` object describing the size of a rectangle that the supplied `text` would fill, given the current canvas text properties.
{{% /notice %}}