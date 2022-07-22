---
title: "HTML Document Structure"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---
When authoring an HTML page, HTML elements should be organized into an _HTML Document_.  This format is defined in the HTML standard.  HTML that does not follow this format are technically invalid, and may not be interpreted and rendered correctly by all browsers.  Accordingly, it is important to follow the standard.

The basic structure of a valid HTML5 document is:

```
<!doctype HTML>
<html lang="en">
  <head>
    <title>Page Title Goes Here</title>
  </head>
  <body>
    <p>Page body and tags go here...</p> 
  </body>
</html>
```

We'll walk through each section of the page in detail.

## Doctype 
The SGML standard that HTML is based on requires a `!doctype` tag to appear as the first tag on the page. The doctype indicates what kind of document the file represents. For HTML5, the doctype is simply _HTML_.  Note the doctype is not an element - it has no closing tag and is not self-closing.  

{{% notice info %}}
For SGML, the doctype normally includes a URL pointing at a definition for the specific type of document.  For example, in HTML4, it would have been `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`.  HTML5 broke with the standard by only requiring HTML be included, making the doctype much easier to remember and type.  
{{% /notice %}}

## HTML Element 
The next element should be an `<html>` element.  It should include all other elements in the document, and its closing tag should be the last tag on the page. It is best practice to include a `lang` attribute to indicate what language is used in the document - here we used `"en"` for English.  The `<html>` element should only contain two children - a `<head>` and `<body>` tag in that order.

{{% notice info %}}
The list of valid langauge subtags are maintained by the Internet Assigned Numbers Authority [(IANA)](https://www.iana.org/), which also oversees domains and IP addresses.  The full list can be reached [here](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry).
{{% /notice %}}

## The Head Element 
The next element is the `<head>` element.  A valid HTML document will only have one head element, and it will always be the first child of the `<html>` element.  The head section contains metadata about the document - information about the document that is not rendered in the document itself.  This typically consists of `meta` and `link` elements, as well as a `<title>`.  Traditionally, `<script>` elements would also appear here, though current best practice places them as the last children of the `<body>` tag.

### The Title Element 
The `<head>` element should always have exactly one child `<title>` element, which contains the title of the page (as text; the `<title>` element should __never__ contain other HTML elements).  This title is typically displayed in the browser tab.

## The Body Element 
The next element is the `<body>` element.  A valid HTML document will only have one body element, and it will always be the second child of the `<html>` element.  The `<body>` tag contains all the HTML elements that make up the page.  It can be empty, though that makes for a very boring page.

