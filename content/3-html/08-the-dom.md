---
title: "Document Object Model"
pre: "8. "
weight: 80
date: 2018-08-24T10:53:26-05:00
---
The Document Object Model (or DOM) is a data structure representing the content of a web page, created by the browser as it parses the website. The browser then makes this data structure accessible to scripts running on the page.  The DOM is essentially a tree composed of objects representing the HTML elements and text on the page.

Consider this HTML:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello DOM!</title>
        <link href="site.css"/>
    </head>
    <body>
        <div class="banner">
            <h1>Hello DOM!</h1>
            <p>
                The Document Object Model (DOM) is a programming API for HTML and XML documents. It defines the logical structure of documents and the way a document is accessed and manipulated. In the DOM specification, the term "document" is used in the broad sense - increasingly, XML is being used as a way of representing many different kinds of information that may be stored in diverse systems, and much of this would traditionally be seen as data rather than as documents. Nevertheless, XML presents this data as documents, and the DOM may be used to manage this data.
            </p>
            <a href="https://www.w3.org/TR/WD-DOM/introduction.html">From w3.org's What is the Document Object Model?</a>
        </div>
    </body>
<html>
```

When it is parsed by the browser, it is transformed into this tree:

![The DOM for the supplied HTML](/images/3.8.1.png)

### The DOM Tree and Developer Tools

Most browsers also expose the DOM tree through their developer tools.  Try opening the example page in Chrome or your favorite browser using <a href='/examples/3.8.1/index.html' target='_blank'>this link</a>.

Now open the developer tools for your browser:
* **Chrome** `CTRL + SHIFT + i` or right-click and select 'Inspect' from the context menu.
* **Edge** `CTRL + SHIFT + i` or right-click and select 'Inspect element' from the context menu.
* **Firefox** `CTRL + SHIFT + i` or right-click and select 'Inspect Element' from the context menu.
* **Safari** Developer tools must be enabled.  See the [Safari User Guide](https://support.apple.com/guide/safari/use-the-developer-tools-in-the-develop-menu-sfri20948/mac)

You should see a new panel open in your browser, and under its 'elements' tab the DOM tree is displayed:

![The Elements tab of the Chrome Developer Tools](/images/3.8.2.png)

Collapsed nodes can be expanded by clicking on the arrow next to them.  
Try moving your mouse around the nodes in the DOM tree, and you'll see the corresponding element highlighted in the page.  You can also _dynamically edit_ the DOM tree from the elements tab by right-clicking on a node.

Try right-clicking on the `<h1>` node and selecting 'edit text'.  Change the text to "Hello Browser DOM".  See how it changes the page?  

The page is rendered from the DOM, so editing the DOM changes how the page appears.  However, the initial structure of the DOM is derived from the loaded HTML.  This means if we refresh the page, any changes we made to the DOM using the developer tools will be lost, and the page will return to its original state.  Give it a try - hit the refresh button.

{{% notice note %}}
For convenience, this textbook will use the [Chrome browser](https://www.google.com/chrome) for all developer tool reference images and discussions, but the other browsers offer much of the same functionality.  If you prefer to use a different browser's web tools, look up the details in that browser's documentation.
{{% /notice %}}

You've now seen how the browser creates the DOM tree by parsing the HTML document and that DOM tree is used to render the page.  We'll revisit this concept in the chapters on [CSS]({{<ref 4-css>}}) and [JavaScript]({{<ref 5-js>}}) when we see how those technologies interact with the DOM.
