---
title: "CSS Units"
pre: "7. "
weight: 70
date: 2018-08-24T10:53:26-05:00
---

When specifying CSS rules, you often need to provide a unit of measurement.  Any time you provide a measurement in a CSS rule, you must provide the units that measurement is being expressed in, following the value.  For example:

```css
#banner {
  width: 300px;
}
```

sets the width of the element with id `banner` to 300 pixels.

There are actually a lot of units available in CSS, and we'll summarize the most common in this section.

## Units of Absolute Size 

Absolute units don't change their size in relation to other settings, hence the name.  The most common one encountered is pixels, which are expressed with the abbreviation `px`.

Other absolute measurements include:

* `q`, `mm`, `cm`, `in` which are quarter-millimeters, millimeters, centimeters, and inches.  These are rarely used outside of rules applied when printing websites.

* `pt`, `pc` which are [points](https://en.wikipedia.org/wiki/Point_(typography)) and [picas](https://en.wikipedia.org/wiki/Pica_(typography)), common units of measurement within the publishing industry.

## Units of Relative Size

Relative units are based on (relative to) the `font-size` property of the element, the viewport size, or grid container sizes. These are expressed as proportions of the units they are relative to, i.e. 

```css
.column {
  width: 30vw;
}
```

sets columns to be 30% of the width of the viewport.

### Units Relative to Font Size 

Setting dimensions of borders, padding, and margins using units relative to font sizes can help make these appear consistent at different resolutions.  Consider a margin of `70px` - it might make sense on a screen 1024 pixels wide, but on a phone screen 300 pixels wide, nearly half the available space would be margins!  

Units that are relative to the `font-size` include:

* `em` one [em](https://en.wikipedia.org/wiki/Em_(typography)) is the font-size of the current element (which may be inherited from a parent).  
* `rem` is same measurement as `em`, but disregards inherited font sizes.  Thus, it is more consistent with intent than `em`, and is largely displacing its use (though it is not supported in older versions of Internet Explorer).

### Units Relative to Viewport Size 

The units `vh` and `vw` refer to 1/100th the height of the viewport (the size of the screen space the page can appear within).  

It may be helpful to think of these as the percentage of the viewport width and viewport height, and they work much like percentages. However, in specifying heights, the `vh` will always set the height of an element, unlike `%`. 

### Fraction Units

The Grid model introduced the fraction (`fr`) unit, which is a fraction of the available space in a grid, after subtracting gutters and items sized in other units.  See the discussion of the CSS Grid Model or CSS Tricks' [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) for more details.

## Percentage Units

You can also specify percentages (`%`) for many properties, which are typically interpreted as a percentage of the parent element's width or height.  For example:

```css 
.column {
  width: 33%;
}
```

sets elements with the class `column` to be 33% the width of their parent element.  Similarly:

```css 
.row {
  height: 20%;
}
```

sets elements with a class `row` to be 20% the height of their parent element.

If the parent does not have an explicit width, the width of the next ancestor with a supplied width is used instead, and if no ancestor has a set width, that of the viewport is used.  The same is _almost_ true of the height; however, if no elements have a specified height, then the percentage value is ignored - the element is sized according to its contents, as would be the case with `height: auto`.  

{{% notice tip %}}
One of the most frustrating lessons beginning HTML authors must learn is the difference in how width and height are handled when laying out a webpage.  Using the percentage unit (`%`) to set the height almost never accomplishes the goal you have in mind - it only works if the containing element has a set height.

While there are hacky techniques that can help, they only offer partial solutions.  It is usually best not to fight the design of HTML, and adopt layouts that can flow down the page rather than have a height determined at render time.

{{% /notice %}}