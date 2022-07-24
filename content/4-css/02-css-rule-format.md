---
title: "CSS Rules"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---

CSS properties consist of key-value pairs separated by a colon (`:`).  For example:

`color: red`

indicates that the styled HTML elements should be given a red color.

Multiple properties are separated by semicolons (`;`), i.e.:

```
color: red;
background-color: green;
```

Rules are CSS properties grouped within curly braces (`{}`) and proceeded by a CSS selector to identify the HTML element(s) they should be applied to:

```
p {
  color: red;
  background-color: green;
}
```

In this example, all paragraph elements (`<p>`) should have red text on a green background (how festive!).

<p style="color: red; background-color: green;">
  And difficult to read!
</p>

## Short Forms
Some properties have multiple forms allowing for some abbreviation.  For example, the CSS property:

`border: 1px solid black` 

is a short form for three separate border-related properties:

```
border-width: 1px;
border-style: solid;
border-color: black;
```

## Experimental Features and Prefixes
As new features are considered for inclusion in CSS, browsers may adopt experimental implementations.  To separate these from potentially differing future interpretations, these experimental properties are typically _prefixed_ with a browser-specific code:


* __-webkit-__ Webkit Browsers (Chrome, Safari, newer Opera  versions, and iOS)
* __-moz-__ Mozilla 
* __-ms-__ Microsoft browsers (IE, Edge)
* __-o-__ Older Opera versions

For example, most browsers adopted the `box-shadow` property before it achieved candidate status, so to use it in the Mozilla browser at that point you would use:

`-moz-box-shadow: black 2px 2px 2px`

To make it work for multiple browsers, and future browsers when it was officially adopted, you might use:

```
-webkit-box-shadow: black 2px 2px 2px;
-moz-box-shadow: black 2px 2px 2px;
-ms-box-shadow: black 2px 2px 2px;
box-shadow: black 2px 2px 2px;
```

The browser will ignore any properties it does not recognize, hence in Chrome 4, the `-webkit-box-shadow` will be used and the rest ignored, while in Chrome 10+ the `box-shadow` property will be used. 

{{% notice note %}}
 You should always place the not-prefixed version last, to override the prefixed version if the browser supports the official property.
{{% /notice %}}

{{% notice tip %}}
[The Mozilla Developer Network](https://developer.mozilla.org) maintains a wiki of comprehensive descriptions of CSS properties and at the bottom of each property's page is a table of detailed browser support. For example, the box-shadow property description can be found at: [https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow). By combining the css property name and the keyword __mdn__ in a Google search, you can quickly reach the appropriate page.
{{% /notice %}}
