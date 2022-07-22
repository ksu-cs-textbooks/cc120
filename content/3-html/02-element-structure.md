---
title: "HTML Element Structure"
pre: "2. "
weight: 20
date: 2018-08-24T10:53:26-05:00
---
HTML was built from the SGML (Structured Generalized Markup Language) standard, which provides the concept of "tags" to provide markup and structure within a text document.  Each element in HTML is defined by a unique opening and closing tag, which in turn are surrounded by angle brackets (<>).  

For example, a top-level heading in HTML would be written:

`<h1>Hello World</h1>`

And render:

<h1>Hello World</h1>


The `<h1>` is the _opening tag_ and the `</h1>` is the closing tag.  The name of the tag appears immediately within the <> of the opening tag, and within the closing tag proceeded by a forward slash (/).  Between the opening tag and closing tag is the _content_ of the element.  This can be text (as in the case above) or it can be another HTML element. 

For example:

`<h1>Hello <i>World</i>!</h1>`

Renders:

<h1>Hello <i>World</i></h1>


## Nesting Elements
An element nested inside another element in this way is called a _child_ of the element it is nested in.  The containing element is a _parent_.  If more than one tag is contained within the parent, the children are referred to as _siblings_ of one another.  Finally, a element nested several layers deep inside another element is called a _descendant_ of that element, and that element is called an _ancestor_.
 
## Matching Tags
Every opening tag __must__ have a matching closing tag.  Moreover, nested tags must be matched in order, much like when you use parenthesis and curly braces in programming.  While whitespace is ignored by HTML interpreters, best developer practices use indentation to indicate nesting, i.e.:

```
<div>
  <h1>Hello World!</h1>
  <p>
    This is a paragraph, followed by an unordered list...
  </p>
  <ul>
    <li>List item #1</li>
    <li>List item #2</li>
    <li>List item #3</li>
  </ul>
</div>
```

Getting tags out of order results in invalid HTML, which may be rendered unpredictably in different browsers.

## Void Elements
Also, some elements are not allowed to contain content, and should not be written with an end tag, like the break character: 

`<br>`

However, there is a more strict version of HTML called XHTML which is based on XML (another SGML extension).  In XHTML void tags are self-closing, and must include a `/` before the last `>`, i.e.:

`<br/>`

In practice, most browsers will interpret `<br>` and `<br/>` interchangeably, and you will see many websites and even textbooks use one or the other strategy (sometimes both on the same page).  But as a computer scientist, you should strive to use the appropriate form based type of document you are creating.

## Tag Name Case 
Similarly, by the standards, HTML is case-insensitive when evaluating tag names, but the W3C recommends using lowercase characters.  In XHTML tag names __must__ be in lowercase, and React's JSX format uses lowercase to distinguish between HTML elements and React components. Thus, it makes sense to always use lowercase tag names.

{{% notice info %}}
XHTML is intended to allow HTML to be interpreted by XML parsers, hence the more strict formatting. While it is nearly identical to HTML, there are important structural differences that need to be followed for it to be valid.  And since the point of XHTML is to make it more easily parsed by machines, these __must__ be followed to meet that goal. Like HTML, the XHTML standard is maintained by W3C: [https://www.w3.org/TR/xhtml11/](https://www.w3.org/TR/xhtml11/).
{{% /notice %}}


## Attributes 
In addition to the tag name, tags can have _attributes_ embedded within them. These are key-value pairs that can modify the corresponding HTML element in some way.  For example, an image tag _must_ have a `src` (source) attribute that provides a URL where the image data to display can be found:

`<img src="img/Light_Bulb_or_Idea_Flat_Icon_Vector.svg" alt="Light Bulb">`

This allows the image to be downloaded and displayed within the browser:

<img src="{{<static "Light_Bulb_or_Idea_Flat_Icon_Vector.svg">}}" alt="Light Bulb">

Note that the `<img>` element is another void tag.  Also, `<img>` elements should always have an `alt` attribute set - this is text that is displayed if the image cannot be downloaded, and is also read by a screen reader when viewed by the visually impaired.

Attributes come in the form of key-value pairs, with the key and value separated by an equal sign (`=`) and the individual attributes and the tag name separated by whitespace.  Attributes can only appear in an opening or void tag.  Some attributes (like `readonly`) do not need a value.  

There should be no spaces between the attribute key, the equal sign (`=`), and the attribute value.  Attribute values should be quoted using single or double quotes if they contain a space character, single quote, or double quote character.

Additionally, while there are specific attributes defined within the HTML standard that browsers know how to interpret, specific technologies like Angular and React add their own, custom attributes.  Any attribute a browser does not know is simply ignored by the browser.

