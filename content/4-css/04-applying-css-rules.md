---
title: "Applying CSS Rules"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

There are multiple ways CSS rules can be applied to HTML elements.  A document containing CSS rules can be attached to a HTML document with a `<link>` element, embedded directly into the html page with a `<style>` element, or applied directly to a HTML element with the `style` attribute.  Let's look at each option.

## Linked CSS Documents
The `<link>` HTML element can be used to link the HTML page it appears in to a text file of CSS rules. These rules will then be applied to the HTML elements in the HTML document.

The `<link>` element should provide a hypertext reference attribute (`href`) providing a location for the linked document, and a relationship attribute (`rel`) describing the relationship between the HTML document and the stylesheet (hint: for a stylesheet the relationship is `"stylesheet"`).  If either of these attributes is missing or invalid, the stylesheet's rules will not be used.  

For example, if the stylesheet is in the file styles.css, and our page is page.html, and both reside at the root of our website, the `<link>` element would be:

`<link href="/styles.css" rel="stylesheet" type="text/css"/>`

By placing our CSS rules in a separate file and linking them to where they are used, we can minimize code duplication.  This approach also contributes to the [separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns).  Thus, it is widely seen as a best practice for web development.  

The `<link>` element should be declared within the `<head>` element.

## HTML &lt;style&gt; Element
The `<style>` HTML element can be used to embed CSS rules directly in an HTML page.  Its content is the CSS rules to be applied.  The `<style>` element must be a child of a `<head>` or `<body>` element, though placing it into the `<head>` element is best practice.

To repeat our earlier efforts of making paragraphs have red text and green backgrounds with the `<style>` element:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Style Element Example</title>
    <style>
      p { 
        color: 'red';
        background-color: 'green';
      }
    </style>
  </head>
  <body>
  </body>
</html>
```

Unlike the `<link>` element approach, CSS rules defined with the `<style>` element can only be used with one file - the one in which they are embedded.  Thus, it can lead to code duplication.  And embedding CSS rules in an HTML document also breaks the [separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns) design principle. 

However, there are several use cases for which the `<style>` element is a good fit.  Most obvious is a HTML page that is being distributed as a file, rather than hosted on a server.  If the style information is embedded in that HTML file, the recipient only needs to receive the one file, rather than two.  Similarly, emails with HTML bodies typically use a `<style>` element to add styling to the email body.

## The HTML Element Style Attribute

The `style` attribute of any HTML element can be used to apply CSS rules to that specific element. These rules are provided a string consisting of key/value pairs separated by semicolons. For example:

```html
<p>This is a normal paragraph.</p>
<p style="color: orange; font-weight: bold">But this one has inline styles applied to it.</p>
```

Produces this:

<p>This is a normal paragraph.</p>
<p style="color: orange; font-weight: bold">But this one has inline styles applied to it.</p>

It should be clear from a casual glance that inline styles will make your code more difficult to maintain, as your styling rules will be scattered throughout a HTML document, instead of collected into a `<style>` element or housed in a separate CSS file.  And while inline styles can be used to selectively modify individual elements, CSS selectors (covered in the previous section) are typically a better approach.

Where inline styles make the most sense is when we manipulate the elements on the page directly using JavaScript.  Also, the browser developer tools let us manipulate inline styles directly, which can be helpful when tweaking a design.  Finally, some component-based design approaches (such as React) pivot the Separation of Concerns design principle to break a user interface into autonomous reusable components; in this approach content, style, and functionality are merged at the component level, making inline styles more appropriate.