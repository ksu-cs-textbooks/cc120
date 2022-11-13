---
title: "SVG"
pre: "13. "
weight: 130
date: 2018-08-24T10:53:26-05:00
---

The Scalable Vector Graphics (SVG) image format is a file format for creating a vector graphic. It uses the same ideas about path, stroke, and fill and coordinate that we discussed with the canvas.  It _also_ is a text format based on XML, as was HTML.  So the contents of a XML file will look familiar to you. Here is an example:

<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>

```svg
<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>
```

Let's take a close look at the file format. First, like HTML and other XML derivatives, we use tags to specify elements.  The `<svg>` tag indicates the top level of our SVG image, much like the `<html>` tag does for HTML. The `xmlns` links to the specification of the XML format, and should be included in all `<svg>` elements (it's one of the requirements of the XML format - earlier versions of HTML did this as well for the HTML namespace, but HTML5 broke away from the requirement).

Likewise the `<path>` element defines a path, much like those we drew with the `<canvas>` and its rendering context. The `d` attribute in the `<path>` is its _data_, and it provides it a series of commands and values, separated by spaces. These instruct the program rendering the SVG in how to move the imaginary pen around.  The `stroke` and `fill` attributes specify how the resulting path should be stroked and filled.

Finally, the `viewBox` attribute in the `<svg>` tag describes what part of the image should be rendered. This is specified as a rectangle, following the familiar format of `x y width height`, where the point (`x`,`y`) is the upper left corner, and `width` and `height` specify a distance to the left and down, respectively.

The `viewBox` plays an important role in how SVG graphics scale.  If we used this SVG in an `<img>` tag and set it to have a different width, it would automatically scale the view box contents to match:

<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg" width="200">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>

```html
<img src="/images/triangle.svg" width="200">
```

Now that you understand the basics, let's turn our attention to some specific SVG elements.

{{% notice info %}}
There is an important idea in the above discussion - the SVG file format specifies _how_ the image should be drawn. But it is up to the program reading the SVG to actually _carry out the drawing commands_. As this is much more involved than simply copying raster bits, not all image viewing software support SVG files. However, all modern browsers do.
{{% /notice %}}

