---
title: "SVG Shapes"
pre: "15. "
weight: 150
date: 2018-08-24T10:53:26-05:00
---

Much like the `CanvasRenderingContext2d` we used with the `<canvas>` earlier allowed us to render rectangles outside of the path, the SVG format _also_ provides mechanisms for rendering common shapes. These are specified using their own tags (like HTML elements), and there are a wide variety of shapes available:

## Rectangle 
The `<rect>` element defines a rectangle, specified by the now-familiar `x`, `y,`, `width` and `height` attributes, and with optional rounded corners with radius specified by the `rx` attribute.

<svg viewBox="0 0 220 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <!-- Simple rectangle -->
  <rect width="100" height="100" fill="cornflowerblue"/>

  <!-- Rounded corner rectangle -->
  <rect x="120" width="100" height="100" rx="15" fill="goldenrod"/>
</svg>

```svg
<svg viewBox="0 0 220 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <!-- Simple rectangle -->
  <rect width="100" height="100" fill="cornflowerblue"/>

  <!-- Rounded corner rectangle -->
  <rect x="120" width="100" height="100" rx="15" fill="goldenrod"/>
</svg>
```

## Circle
The `<circle>` elements defines a circle with radius and center defined by the `r`, `cx`, and `cy` attributes:

<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <circle cx="50" cy="50" r="50" fill="cornflowerblue"/>
</svg>

```svg
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="50" fill="cornflowerblue"/>
</svg>
```

## Ellipse

The `<ellipse>` element represents an ellipse, with center (`cx`, `cy`) horizontal radius (`rx`) and vertical radius (`ry`) specified by the corresponding attributes:

<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="goldenrod"/>
</svg>

```svg
<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <ellipse cx="100" cy="50" rx="100" ry="50" fill="goldenrod"/>
</svg>
```

## Polygon

The `<polygon>` specifies an arbitrary polygon using a series of points defined by the `points` attribute:

<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <!-- Example of a polygon with the default fill -->
  <polygon points="0,100 50,25 50,75 100,0" fill="magenta"/>

  <!-- Example of the same polygon shape with stroke and no fill -->
  <polygon points="100,100 150,25 150,75 200,0" fill="none" stroke="black" />
</svg>

```xml
<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <!-- Example of a polygon with the default fill -->
  <polygon points="0,100 50,25 50,75 100,0" fill="magenta"/>

  <!-- Example of the same polygon shape with stroke and no fill -->
  <polygon points="100,100 150,25 150,75 200,0" fill="none" stroke="black" />
</svg>
```


{{% notice info %}}
The examples on this page have been adapted from the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/SVG). You are encouraged to visit these documents for a much more detailed discussion of the concepts and techniques presented here.
{{% /notice %}} 