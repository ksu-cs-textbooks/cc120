---
title: "CSS Timing Functions"
pre: "17. "
weight: 170
date: 2018-08-24T10:53:26-05:00
---

The `transition` property (and the animations we'll look at shortly) both make use of timing functions - functions that define how the values of a CSS property change over time as we transition from one state to the next.

The simplest (and default) transition function is _linear_, which means the value smoothly transitions from its starting value to its ending value. It is specified as `linear`.  

While linear is easy to reason about and represent mathematically, transitions often look more realistic if the start or end more slowly, speeding up in the middle. Graphically, these functions look like a curve, and can be mathematically represented by a Bezier curve.  We can specify this curve with `cubic-bezier(<x1>, <y1>, <x2>, <y2>)` where the arguments are the coordinates of control points.

But for ease of use (and so we don't need to learn the math behind Bezier curves), CSS also provides several pre-defined Bezier curves we can use instead:

* `ease` - starts and ends slowly, with a rapid speeding up in the middle
* `ease-in` - starts slowly, speeds up, and stops suddenly
* `ease-out` - starts quickly but slows down at the end
* `ease-in-out` - similar to `ease`, but the start and end transitions are more even

The transition timing functions we've just discussed are the most commonly employed in web design.  But there are other transitions functions available in the CSS standards, and if you understand the mathematics behind Bezier curves, you can define your own as well.  You can read more about the subject in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function).
