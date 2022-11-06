---
title: "Raster Graphic Files"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---

Unsurprisingly, graphic files that store their data in a raster format borrow heavily from the representations discussed [previously]({{<ref "7-graphics/01-introduction">}}).  Typically, a graphic file consists of two parts, a _head_ and a _body_.  This is very much like how the `<head>` of a HTML file provides metadata about the page and the `<body>` contains the actual page contents. For a raster graphic file, the head of the file contains metadata describing the image itself - the color format, along with the width and height of the image.  The body contains the actual raster data, in a linear array much like that used by the computer screen.  

This data may be compressed, depending on the file format used.  Some compression algorithms, like the one used in JPEG files, are lossy (that is, they “lose” some of the fine detail of the image as a side-effect of the compression algorithm).  Tagged image file format (tiff), bitmaps (bmp), and portable network graphics (png) are popular formats for the web with the latter (png) especially suitable for websites.

The origin of a raster graphic file is also in the upper left corner, and the raster data is typically comprised of three or four eight-bit color channels corresponding to Red, Green, Blue, and Alpha (the alpha channel is typically used to represent the opacity of the pixel, with 255 being completely solid and 0 being completely transparent).  Because the raster data for video memory and for raster graphic files are ordered in the same way, putting a raster graphic on-screen simply requires copying the pixel data from one linear array into the other - a relatively fast process (Computer scientists would describe it as having a complexity of $O(n)$).