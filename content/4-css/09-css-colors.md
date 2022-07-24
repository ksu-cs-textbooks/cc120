---
title: "CSS Colors"
pre: "9. "
weight: 90
date: 2018-08-24T10:53:26-05:00
---

CSS also has many properties that can be set to a color, i.e. `color`, `background-color`, `border-color`, `box-shadow`, etc. Colors consist of three or four values corresponding to the amount of red, green, and blue light blended to create the color. The optional fourth value is the alpha, and is typically used to specify transparency.  

Colors are stored as 24-bit values, with 8 bits for each of the four channels (R,G,B,and A), representing 256 possible values (2^8) for each channel.

Colors can be specified in one of several ways:

* __Color Keywords__ like `red`, `dark-gray`, `chartreuse` correspond to well-defined values.  You can find the full list [in the MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#Color_keywords).

* __Hexidecimal Values__ like `#6495ed`, which corresponds to cornflower blue.  The first two places represent the red component, the second the green, and the third the blue.  If an additional two places are provided the last pair represents the alpha component.  Each pair of hex values can represent 256 possible values (16^2), and is converted directly to the binary color representation in memory.

* __RGB Function__ a third option is to use the `RGB()` CSS function.  This take decimal arguments for each channel which should be in the range 0-255

* __HSL Function__ a fourth option is the `HSL()` function, which specifies colors in terms of an alternative scheme of [hue, saturation, and lightness](https://en.wikipedia.org/wiki/HSL_and_HSV#Basic_principle). 

* __RGBA and HSLA Functions__ finally, the `RGBA()` and `HSLA()` functions take the same arguments as their siblings, plus a value for the alpha channel between 0 and 1.
