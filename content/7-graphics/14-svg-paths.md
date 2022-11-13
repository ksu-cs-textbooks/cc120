---
title: "SVG Paths"
pre: "14. "
weight: 140
date: 2018-08-24T10:53:26-05:00
---

SVGs use the same pen metaphor we saw with the `<canvas>` and one of the most basic approaches to drawing in an SVG is the `<path>` element. Each `<path>` should contain a `d` attribute, which holds the commands used to _draw_ the path. These are very similar to the commands we used with the `<canvas>` and the `CanvasRenderingContext2D` we used earlier, but instead of being written as a function call, they are written as a capital letter (indicating what command to carry out) followed by numbers specifying the action.  Let's take another look at our earlier example:

<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>

The path's data is `M 100 50 L 100 150 L 300 150 Z`.  Let's break it down one command at a time:
1. `M 100 50` indicates we should move our pen to point (100, 50).
2. `L 100 150` indicates we should draw a line from our current position to point (100, 150).
3. `L 300 150` indicates we should draw a line from our current position to point (300, 150).
4. `Z` indicates we should close our path, drawing a line to where we started (the point specified in our first command).

Now that we've worked through a path example, let's discuss the specific commands available to us:

## Move To
The `M x y` command indicates we should _move to_ the point (`x`, `y`), picking up our pen. It corresponds to `ctx.moveTo(x, y)`.

## Line To
The `L x y` command indicates we should draw a _line_ from our current position to the point (`x`, `y`). It corresponds to `ctx.lineTo(x, y)`.

## Horizontal Line To
The `H x` command is shorthand for drawing a horizontal line (the y stays the same) from the current x to the provided `x`.

## Vertical Line To
The `V y` command is shorthand for drawing a vertical line (the x stays the same) from the current y to the provided `y`.

## Curve To
The `C cx1 cy1, cx2 cy2, dx, dy` is the shorthand for drawing a Bézier Curve from the current position to (`dx`, `dy`) using control points (`cx1`, `cy1`) and (`cx2`, `cy2`). It corresponds to `ctx.curveTo(c1x, c1y, c2x, c2y, dx, dy)`. The MDN web docs has an excellent discussion with visual examples of [Bézier curves](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths#b%C3%A9zier_curves). A visual example of the role of the effect control points have on a Bézier curve from that article appears below:

![Bézier curve examples](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths/cubic_b%C3%A9zier_curves_with_grid.png)


## Arc To
The `A rx ry x-axis-rotation large-arc-flag sweep-flag x y a rx ry x-axis-rotation large-arc-flag sweep-flag dx dy` draws an arc. It is roughly analogous to the `ctx.drawArc()` method, but uses a different way of specifying the arc's start, end, and direction. You can read a more detailed discussion on the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths#arcs)


{{% notice info %}}
The examples on this page have been adapted from the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/SVG). You are encouraged to visit these documents for a much more detailed discussion of the concepts and techniques presented here.
{{% /notice %}} 