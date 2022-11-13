---
title: "SVG and HTML"
pre: "18. "
weight: 180
date: 2018-08-24T10:53:26-05:00
---

As described earlier, SVG is an image file format. Thus, it can be used as the `src` for an `<img>` element in HTML:

<img src="/images/triangle.svg" alt="A triangle">

```html
<img src="/images/triangle.svg" alt="A triangle">
```

However, the SVG itself is just text. And that text shares a lot of characteristics with HTML, as both are derived from XML. As SVG became more commonplace, the W3C added support for _inline SVGs_ - placing SVG code directly in a HTML document:

<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>

```html
<svg viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
  <path d="M 100 50 L 100 150 L 300 150 Z" stroke="black" fill="#dd3333"/>
</svg>
```

In fact, that is how we handle most of the SVGs we are presenting to you in this chapter. There are some additional benefits to this approach:
1. The SVG is contained in the html document, so there is no need to download additional files as with an `<img>` element.
1. The SVG definition _also_ contains a `<a>` element, which is identical to its HTML counterpart. When you use the SVG inline, it works just like a regular link in the page.
1. The inline SVG can also be modified by CSS and JS - we'll take a look at each next.