---
title: "CSS Functions"
pre: "8. "
weight: 80
date: 2018-08-24T10:53:26-05:00
---

CSS provides a number of useful functions that calculate values.  Functions are written in the form `name(arg1, arg2, ...)` and are provided as values to CSS properties.  For example, this CSS code sets the height of the content area to the available space on screen  for content after subtracting a header and footer:

```css
#header {height: 150px}
#footer {height: 100px}
#content {
  height: calc(100vh - 150px - 100px);
}
```

Here `100vh` is the height of the viewport, and the header and footer are defined in terms of pixels. 

{{% notice note %}}
You might want to apply the `box-sizing: border-box` on these elements if they have padding and borders, or these additional dimensions will need to be included in the calculation. See the section on the [CSS Box Model]({{<ref "4-css/11-css-box-model.md">}}) for more details.
{{% /notice %}}

## Math Functions 
CSS provides a number of useful math functions:

### The Calc Function
As you have seen above, the `calc()` function can be used to calculate values by performing arithmetic upon values. These values can be in different units (i.e. `calc(200px - 5mm)` or even determined as the webpage is being interpreted (i.e. `calc(80vw + 5rem)`).  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/calc) for more details.

### The Min and Max Functions 
CSS also provides `min()` and `max()` function, which provide the smallest or largest from the provided arguments (which can be arbitrary in number).  As with `calc()`, it can do so with interpretation-time values.

### The Clamp Function
The `clamp()` function clamps a value within a provided range.  Its first argument is the minimum value, the second the preferred value, and the third the max.  If the preferred value is between the min and max value, it is returned.  If it is less than the minimum, the min is instead returned, or if it is greater than the maximum, the max value is returned.

## Color Functions 
Several CSS functions are used to create an modify colors.  These are described in the CSS Color section.

## Transformation Functions
Many CSS functions exist for specifying CSS transforms. See the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) for details.

## Image Filter Functions
CSS allows for filters to be applied to images.  More details can be found in the [Mozilla Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/filter).

## Counter Functions
Finally CSS uses counters to determine row number and ordered list numbers.  These can be manipulated and re-purposed in various ways. See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Lists_and_Counters/Using_CSS_counters) for details.