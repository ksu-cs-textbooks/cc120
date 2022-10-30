---
title: "CSS Transformations"
pre: "15. "
weight: 150
date: 2018-08-24T10:53:26-05:00
---

With powerful graphics cards becoming commonplace, the W3C standards expanded the CSS rules to take advantage of their abilities. Specifically, the CSS `transform` property allows us to apply a transformation (scaling, rotating, translating, stretching, skewing, or any combination) to elements on a page. These are performed using a mathematical operation based on the use of [matrices](https://en.wikipedia.org/wiki/Matrix_(mathematics)). Graphics cards are optimized to perform these matrix operations in parallel, allowing them to quickly transform graphical objects in 3-dimensional space. While a full discussion of the underlying mathematical operations is outside the scope of this course, we don't have to create the matrices ourselves - the CSS rules provide function for building and combining the most common transformation matrices.

To explore these transformations, we will use a demonstration `<div>` and css rules:

```html
<div class="transform-example">Element to be Transformed</div>
```
```css
div.transform-example {
  display: flex;
  align-items: center;
  justify-content: center;
  border: solid;
  color: purple;
  width: 230px;
  height: 120px;
}
```
<style>
div.transform-example {
  display: flex;
  align-items: center;
  justify-content: center;
  border: solid;
  color: purple;
  width: 230px;
  height: 120px;
}
</style>
<div class="transform-example">Element to be Transformed</div>

### Coordinate Space

An important concept to grasp before tackling transformations is the concept of coordinate spaces.  A coordinate space is simply a way of expressing position, relative to an origin point.  You have likely studied the [Cartesian coordinate system](https://en.wikipedia.org/wiki/Cartesian_coordinate_system) in your math courses. CSS uses a similar approach for applying transforms in 2d or 3d space, with one important difference - the **y-axis is reversed**.  Thus, the 2d coordinate system looks like:


### Translation

The first transformation we'll discuss is _translation_, moving an element along the x, y, or z axes. In most cases, we're focused on just the x and y coordinates, for which we can use the `translate(x, y)` function: 

```html
<div class="transform-example" id="translation-example">Element to be Translated</div>
```
```css
div#translation-example {
  transform: translate(100px, -30px);
}
```
<div class="transform-example" id="translation-example">Element to be Translated</div>
<style>
div#translation-example {
  transform: translate(100px, -30px);
}
</style>

We can also translate in three dimensions with the `translate3d()` function, but note that visually a change in the z position will not be visually apparent in most cases (unless we are using a perspective transformation). Additionally, we can create a translation matrix with only the x, y, or z axis using `translateX(x)`, `translateY(y)`, and `translateZ(z)`, respectively.

### Rotation

Rotation can happen around any of the primary axes, facilitated by the `rotateX(angle)`, `rotateY(angle)`, and `rotateZ(angle)`. Rotation angles can be expressed in degrees (`deg`) or radians (`rad`).  Rotation about the z is perhaps the most commonly used, as it "spins" an element on the page:

```html
<div class="transform-example" id="rotation-z-example">Element to be Rotated</div>
```
```css
div#rotation-z-example {
  transform: rotateZ(45deg);
}
```
<div class="transform-example" id="rotation-z-example">Element to be Rotated</div>
<style>
div#rotation-z-example {
  transform: rotateZ(45deg);
}
</style>

But rotations about the x or y can also be interesting, as they rotate _around_ the screen, but to avoid looking like a squished version of the untransformed element, should be combined with a perspective transform.  We'll revisit this after discussing combining transformations.

### Scale

Scaling refers to increasing or decreasing the size of the element, either all together or along a single axis. We can use the `scale(x, y)` to scale in two dimensions, `scale(x, y, z)` to scale in three, or `scaleX(x)`, `scaleY(y)`, or `scaleZ(z)` to scale along a single axis. Scale values are expressed as floating point numbers (1 = 100%, 1.5 = 150%, -0.5 = -50%).

```html
<div class="transform-example" id="scale-example">Element to be Scaled</div>
```
```css
div#scale-example {
  transform: scale(0.5, 0.5);
}
```
<div class="transform-example" id="scale-example">Element to be Scaled</div>
<style>
div#scale-example {
  transform: scale(0.5, 0.5);
}
</style>

### Skew

Skewing distorts an element, distorting each point in the element by a certain angle in the horizontal, vertical, or both (CSS skew functions are only expressed in two dimensions). You can use `skew(xAngle, yAngle)` to specify both vertical and horizontal, or `skewX(angle)` and `skewY(angle)` to do skew separately.

```html
<div class="transform-example" id="skew-example">Element to be Skewed</div>
```
```css
div#skew-example {
  transform: skewX(10deg);
}
```
<div class="transform-example" id="skew-example">Element to be Skewed</div>
<style>
div#skew-example {
  transform: skewX(-10deg);
}
</style>

### Combining Transformations

To combine multiple transformations, just list the transformation function one after another. For example, to translate and rotate we could:

```html
<div class="transform-example" id="combo-example">Element to be Transformed</div>
```
```css
div#combo-example {
  transform: translateX(50%) rotateZ(60deg);
}
```
<div class="transform-example" id="combo-example">Element to be Transformed</div>
<style>
div#combo-example {
  transform: translateX(200px) rotateZ(60deg);
}
</style>

### Perspective

When using three dimensions, it is helpful to apply a [perspective projection](https://en.wikipedia.org/wiki/3D_projection#Perspective_projection).  This is a mathematical transformation that makes points far from the viewer appear closer to one another than those closer to the viewer.  This mimics how our eyes and brain interpret what we see in the world as depth.

The perspective projection is specified with the `projection(distance)` function, where the distance is how far you are from the element being transformed along the z-axis. In general, a small number will create a more dramatic transformation than a large one.

```html
<div class="transform-example" id="projection-example">Element to be Transformed</div>
```
```css
div#transform-example {
  transform: perspective(300px) rotateX(45deg);
}
```

<div class="transform-example" id="projection-example">Element to be Transformed</div>
<style>
div#projection-example {
  transform: perspective(300px) rotateX(45deg);
}
</style>