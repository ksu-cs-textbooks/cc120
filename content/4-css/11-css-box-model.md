---
title: "CSS Box Model"
pre: "11. "
weight: 110
date: 2018-08-24T10:53:26-05:00
---

As the browser lays out HTML elements in a page, it uses the __CSS Box Model__ to determine the size and space between elements.  The CSS box is composed of four nested areas (or outer edges): the content edge, padding edge, border edge, and margin edge.  

## Box Areas

![CSS Box Model]({{<static "images/B.11.1.png">}})

__Content Area__ contains the actual content of the element (the text, image, etc).  By default the CSS properties `width` and `height` set this size, and the `min-width`, `min-height`, `max-width`, `max-height` constrain it (but see the discussion of `box-sizing` below).  

__Padding Area__ provides space between the content and the border of the HTML element.  It is set by the `padding` properties (`padding-top`, `padding-right`, `padding-bottom`, and `padding-left`, as well as the shorthand versions).

__Border Area__ draws a border around the element.  Its size is set with the `border-width` property.  Borders can also be dashed, inset, and given rounded corners. See the [MDN Border Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/border) for details.

__Margin Area__ provides the space between the border and neighboring elements.  Its size is set with the `margin` properties (`margin-top`, `margin-right`, `margin-bottom`, and `margin-left`, as well as the shorthand versions).

## Box-Sizing

By default, an element's `width` and `height` properties set the width and height of the _content area_, which means any padding, borders, and margins increase the size the element consumes on-screen.  This can be altered with the `box-sizing` CSS rule, which has the following possible values:

`content-box` (the default) the `width` and `height` properties set the content area's size.

`border-box` includes the border area, padding area, and content area within the `width` and `height` of the HTML element.  Using the CSS rule `box-sizing: border-box` therefore makes it easier to lay out elements on the page consistently, without having to do a lot of by-hand calculations.

## Backgrounds 

The `background` property allows you to set a color, pattern, or image as the background of an HTML element. By default the background extends to the border-area edge, but can be altered with the `border-clip` property to `border-box`, `padding-box`, or `content-box`.  See the [MDN Background Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/background) for more details on creating backgrounds.

## Box-Shadow 

The `box-shadow` property allows you to set a drop shadow beneath the HTML element.  See the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) for more details on creating box shadows.
