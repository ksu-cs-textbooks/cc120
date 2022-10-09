By default HTML elements are positioned in the page using the HTML flow algorithm.  You can find a detailed discussion in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow).  However, you may want to override this and manually position elements, which you can do with the CSS properties `position`, `left`, `top`, `right`, and `bottom`.

## The Positioning Context 
First, we need to understand the positioning context, this is basically the area an element is positioned within.  The `left`, `top`, `right`, and `bottom` properties affect where an element appears within its context.  

![Positioning Context](.guides/img/positioning-context.png)

You can think of the context as a box.  The `left` property determines how far the element is from the left side of this context, the `top` from the top, `right` from the right, and `bottom` from the bottom. These values can be numeric or percentage values, and can be negative.

__GOTCHA__ However, if you define both a `left` and `right` value, only the `left` value will be used.  Similarly, if both `top` and `bottom` are supplied, only `top` is used.  Use the `width` and `height` properties in conjunction with the positioning rules if you want to control the element's dimensions.

What constitutes the positioning context depends on the elements `position` property, which we'll discuss next.

## The Position Property

The `position` property can be one of several values:

### Static Positioning
The default `position` value is `static`.  It positions the element where it would normally be in the flow and ignores any `left`, `top`, `right`, and `bottom` properties.

### Relative Positioning
The `position` value of `relative` keeps the element where it would normally be in the flow, just like `static`.  However, the `left`, `top`, `right`, and `bottom` properties move the element relative to this position - in effect, the positioning context is the hole the element would have filled with `static` positioning.  

### Absolute Positioning 
Assigning the `position` property the value of `absolute` removes the element from the flow.  Other statically positioned elements will be laid out as though the absolutely positioned element was never there.  The positioning context for an absolutely positioned element is its first non-statically positioned ancestor, or (if there is none), the viewport.

A common CSS trick is to create a relatively-positioned element, and then absolutely position its children.

### Fixed Positioning 
Assigning the value of `fixed` to the `position` property also removes the element from the flow.  However, its positioning context is _always_ the viewport.  Moreover, if the page is scrolled, a fixed-position element stays in the same spot (an absolutely-positioned element will scroll with the page). This makes fixed position elements useful for dialogs, pop-ups, and the like.

## Z-Order 
By default, elements are drawn in the browser in the order they appear in the HTML.  Thus, if we position an element further down the page, it may be covered up by succeeding elements.  The `z-index` property provides us with a fix. The default value for the `z-index` is 0.  Items with a larger `z-index` are drawn later. 
