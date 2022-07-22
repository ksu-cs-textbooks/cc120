---
title: "Common HTML Elements"
pre: "7. "
weight: 70
date: 2018-08-24T10:53:26-05:00
---
This page details some of the most commonly used HTML elements. For a full reference, see MDN's [HTML Element Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

## Document-Level Elements
These elements describe the basic structure of the HTML document.

### &lt;html&gt;
The `<html>` element contains the entire HTML document.  It should have exactly two children, the `<head>` and the `<body>` elements, appearing in that order.

### &lt;head&gt;
The `<head>` element contains any metadata describing the document.  The most common children elements are `<title>`, `<meta>`, and `<link>`.

### &lt;body&gt;
The `<body>` element should be the second child of the `<html>` element.  It contains the actual rendered content of the page, typically as nested HTML elements and text.  Elements that appear in the body can define structure, organize content, embed media, and play many other roles.  

## Metadata Elements 
These elements add properties to the document.

### &lt;link&gt;
The `<link>` element links to an external resource using the `href` attribute and defines that resource's relationship with the document with the `rel` attibute. 

This is most commonly used to link a stylesheet which will modify how the page is rendered by the browser (see the chapter on CSS).  A stylesheet link takes the form:

`<link href="path-to-stylesheet.css" rel="stylesheet"/>`

It can also be used to link a favicon (the icon that appears on your browser tab):

`<link rel="icon" type="image/x-icon" href="http://example.com/favicon.ico" />`

### &lt;meta&gt;
The `<meta>` elements is used to describe metadata not covered by other elements.  In the early days, its most common use was to list keywords for the website for search engines to use:

`<meta keywords="html html5 web development webdev"/>`

However, this was greatly abused and search engines have stopped relying on them.  One of the most common uses today is to set the viewport to the size of the rendering device for responsive design (see the chapter on responsive design):

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

Also, best practice is to author HTML documents in utf-8 character format and specify that encoding with a metadata tag with the `charset` attribute:

`<meta charset="utf-8">`

### &lt;style&gt;
The `style` element allows for embedding CSS text directly into the head section of the HTML page.  The Separation of Concerns discussion discusses the appropriateness of using this approach.

### &lt;title&gt;
The `<title>` element should only appear once in the `<head>` element, and its content should be text (no HTML elements).  It specifies the title of the document.  In modern browsers, the title is displayed on the browser tab displaying the document. In earlier browsers, it would appear in the window title bar.


## Sectioning Elements
Many HTML Elements help define the structure of the document by breaking it into sections. These are intended to hold other elements and text. These elements are _block_ type elements.

### headings 
The `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, and `<h6>` elements are headings and subheadings with six possible levels of nesting.  They are used to enclose the title of the section.  

### &lt;main&gt;
A `<main>` element identifies the content most central in the page. There should be only one per page (or, if multiple main elements are used, the others should have their `visible` attribute set to false).

### &lt;aside &gt;
An `<aside>` element identifies content separate from the main focus of the page. It can be used for callouts, advertisements, and the like.

### &lt;article&gt;
An `<article>` element identifies a stand-alone piece of content.  Unlike an aside, it is intended for syndication (reprinting) in other forms. 

### &lt;header&gt;
The `<header>` element identifies a header for the page, often containing the site banner, navigation, etc.

### &lt;footer&gt;
The `<footer>` element identifies a footer for the page, often containing copyright and contact information.

### &lt;nav&gt;
The `<nav>` element typically contains navigation links and/or menus.

### &lt;section&gt;
A `<section>` element is a general-purpose container for sectioning a page where a more specific container does not make sense.

## Text Content
These HTML elements are used to organize text content.  Each of these is a _block element_, meaning it breaks up the flow of text on the page. 

### &lt;blockquote&gt;
The `<blockquote>` is used to contain a long quotation.

### &lt;figure&gt;
The `<figure>` is used to contain a figure (typically a `<img>` or other media element).

### &lt;figcaption&gt;
The `<figcaption>` provides a caption for a figure 

### &lt;hr&gt;
The `<hr>` provides a horizontal rule (line) to separate text.

### lists 
There are three types of lists available in HTML, ordered, unordered, and definition.  Ordered lists number their contents, and consist of list item elements (`<li>`) nested in an ordered list element (`<ol>`).  Unordered lists are bulleted, and consist of list item elements (`<li>`) nested in an unordered list element (`<ul>`). List items can contain any kind of HTML elements, not just text.

Definition lists nest a definition term (`<dt>`) and its corresponding definition (`<dd>`) inside a definition list (`<dl>`) element.  While rarely used, they can be handy when you want to provide lists of definitions (as in a glossary) in a way a search engine will recognize.

### &lt;div&gt;
The `<div>` element provides a wrapper around text content that is normally used to attach styles to.

### &lt;pre&gt;
The `<pre>` tag informs the browser that its content has been preformatted, and its contents should be displayed exactly as written (i.e. whitespace is respected, and angle brackets (<>) are rendered rather than interpreted as HTML. It is often used in conjunction with a `<code>` element to display source code within a webpage.

## Inline Text Elements
The following elements modify nested text while maintaining the flow of the page. As the name suggests, these are _inline_ type elements.

### &lt;a&gt;
The `<a>` anchor element is used to link to another document on the web (i.e. 'anchoring' it).  This element is what makes HTML hyper-text, so clearly it is important.  It should always have a source (`src`) attribute defined (use `"#"` if you are overriding its behavior with JavaScript).  

### text callouts
A number of elements seek to draw specific attention to a snippet of text, including `<strong>`, `<mark>`, `<em>`, `<b>`, `<i>`

#### &lt;strong&gt;
The `<strong>` element indicates the text is _important_ in some way. Typically browsers will render its contents in boldface.

#### &lt;em&gt;
The `<em>` element indicates _stress emphasis_ on the text.  Typically a browser will render it in italics.

#### &lt;mark&gt;
The `<mark>` element indicates text of specific _relevance_.  Typically the text appears highlighted.

#### &lt;b&gt;
The _bring to attention_ element (`<b>`) strives to bring attention to the text. It lacks the semantic meaning of the other callouts, and typically is rendered as boldface (in early versions of HTML, it referred to bold).

#### &lt;i&gt;
The `<i>` element sets off the contained text for some reason other than emphasis. It typically renders as italic (in early versions of HTML, the i referred to italics).

### &lt;br&gt;
The break element (`<br>`) inserts a line break into the text.  This is important as all whitespace in the text of an HTML document is collapsed into a single space when interpreted by a browser.

### &lt;code&gt;
The `<code>` element indicates the contained text is computer code.

### &lt;span&gt;
The `<span>` element is the inline equivalent of the `<div>` element; it is used primarily to attach CSS rules to nested content.

## Media Elements 
A number of elements bring media into the page.

### &lt;img&gt;
The `<img>` element represents an image.  It should have a source (`src`) attribute defined, consisting of a URL where the image data can be retrieved, and an alternative text (`alt`) attribute with text to be displayed when the image cannot be loaded or when the element is read by a screen reader.

### &lt;audio&gt;
The `<audio>` element represents audio data.  It should also have a source (`src`) attribute to provide the location of the video data.  Alternatively, it can contain multiple `<source>` elements defining alternative forms of the video data.

### &lt;video&gt;
The `<video>` element represents a video.  It should also have a source (`src`) attribute to provide the location of the video data.  Alternatively, it can contain multiple `<source>` elements defining alternative forms of the audio data.

### &lt;source&gt;
The `<source>` element specifies one form of multimedia data, and should be nested inside a `<video>` or `<audio>` element.  Providing multiple sources in this way allows the browser to use the first one it understands (as most browsers do not support all possible media formats, this allows you to serve the broadest possible audience).  Each `<source>` element should have a source attribute (`src`) defining where its multimedia data can be located, as well as a `type` attribute defining what format the data is in. 