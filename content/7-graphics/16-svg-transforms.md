---
title: "SVG Transforms"
pre: "16. "
weight: 160
date: 2018-08-24T10:53:26-05:00
---

As with CSS and the canvas, SVGs _also_ support transformations. In an SVG, these are specified by the `transform` attribute and thus apply to a specific element. For example, to rotate our ellipse from the previous section by 15 degrees around its center, we would use:

<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="cornflowerblue" transform="rotate(15 100 50)"/>
</svg>

```svg
<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="cornflowerblue" transform="rotate(15 100 50)"/>
</svg>
```

Notice how the ellipse is clipped at the view box - this is another important role the view box plays.

Multiple transformations can be concatenated into the `transform` attribute, separated by spaces:

<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="goldenrod" transform="rotate(15 100 50) translate(100)"/>
</svg>

```svg
<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="goldenrod" transform="rotate(15 100 50) translate(100)"/>
</svg>
```

Note that the transformation functions are applied in the _opposite_ order they are specified.  In this case, translating the ellipse forward moves it along a rotated axis - 15 degrees downward!

## Transformation Functions

As with the other transformation approaches we've seen, SVG transforms are based on matrix math. And, as in those prior approaches, a variety of helpful functions are provided to create the most common kinds of transformation matrices.  The specific transformation functions available in the SVG standard are:

**Translate** The `translate(tx [ty])` translates along the x-axis by `tx` and the y axis by `ty`.  If no value for `ty` is supplied, the value of 0 is assumed.

**Scale** The `scale(sx [sy])` scales the image by `sx` along the x axis, and by `sy` along the y axis. If a value for `sy` is not supplied, then it uses the same value as `sx` (i.e. the element is scaled along both axes equally).

**Rotate** The `rotate(angle [x y])` rotates the element around the point (`x`, `y`) by `angle` degrees.  If `x` and `y` are omitted, the origin (0,0) is the center of rotation.

**Skew** The `skewX(angle)` skews along the x axis by `angle` degrees. Likewise, the `skewY(angle)` skews along the y axis by `angle` degrees.

## Grouping Elements

The `<g>` element can be used to group elements together, and apply transformations to the whole group:

<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <g transform="translate(10 -20) rotate(45) skewX(20) scale(0.5)">
    <ellipse cx="100" cy="50" rx="100" ry="50" fill="cornflowerblue" />
    <rect x="60" y="10" width="80" height="80" fill="goldenrod"/>
  </g>
</svg>

```svg
<svg viewBox="0 0 300 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <g transform="translate(10 -20) rotate(45) skewX(20) scale(0.5)">
    <ellipse cx="100" cy="50" rx="100" ry="50" fill="cornflowerblue" />
    <rect x="60" y="10" width="80" height="80" fill="goldenrod"/>
  </g>
</svg>
```


