---
title: "HTML Raster Graphics"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---

The most obvious use of raster graphics in HTML is the `<img>` element, a HTML element that embodies a single raster graphic image.  It is defined with the an img tag:

```html
<img src="" alt="">
```

The `src` attribute is a relative or absolute url of an image file, and the `alt` attribute provides a textual description of what the image portrays.  It is what the browser displays if the image file does not load, and is also important for screen readers (as discussed in [Chapter 6]({{<ref "6-accessibility">}})).  

Any HTML element can also be given a raster graphic to use as a background through the CSS `background-image` property:

```html
background-image(url([route/to/file]));
```

The  `url()` function converts a relative or absolute path (`[route/to/file]`) for the browser to retrieve with a hTTP request (relative paths are relative to the file containing the rule declaration).  By default, the image will have its origin in the upper left corner of the HTML element the rule is applied to, and will extend pixel-by-pixel until the edge of the containing element is reached (this means that to display the full image, you may need to set the `width` and `height` attributes for the element as well).  If the image is smaller than the containing element, it will be tiled.  Tiling can be conditionally turned off through the  `background-repeat property`, in the X, Y, or both axes.  You can also stretch, crop, and shift the image’s origin with other background properties.

In addition to these two strategies for including graphics in a web site, HTML provides a third option in the `<canvas>` element. We'll discuss that next.