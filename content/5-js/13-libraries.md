---
title: "JavaScript Libraries"
pre: "13. "
weight: 130
date: 2018-08-24T10:53:26-05:00
---

Up to this point, we've been focused on core JavaScript functionality. However, there are _lots_ of additional JavaScript libraries you can use in your web development efforts. A library is a collection of source code that is _intended_ to be used in other projects. Unlike core libraries, these are written by third parties, and often released under an open-source license which describes how they can legally be used in your projects.  

One of the more important and well-known early JavaScript libraries is [JQuery](https://jquery.com/). JQuery provides many features to support DOM manipulation, and also provides a wrapper that simplifies making AJAX requests.  It was created at a time when browser implementations of JavaScript were inconsistent and often incomplete (especially Internet Explorer) and thus became an important tool for making sure your JavaScript code executed the same in all major browsers.  Over time the features it introduced have been folded into core JavaScript, and browsers have improved their support. While this has reduced the need for JQuery, many legacy sites are still written using it, and many developers prefer its more abbreviated syntax to vanilla JavaScript.

Another library for simplifying requests is [Axios](https://axios-http.com/docs/intro).  Like JQuery, it simplifies making AJAX calls, and adds support for handling redirects, authentication, and other challenging kinds of HTTP requests.

A third category of JavaScript library works in conjunction with CSS libraries to bring cohesive functionality like dialog boxes, dynamically tiled layouts, infinite scrolls, and other features to your web applications.  [Bootstrap](https://getbootstrap.com/) is perhaps the best known of these. [D3](https://d3js.org/) provides support for generating graphs and other views of data. Other libraries provide extra control for drawing with the Canvas or SVG elements.

Finally, there are libraries that represent full rendering frameworks, like [React](https://reactjs.org/), [Angular](https://angular.io/), and [Vue](https://vuejs.org/). These libraries are used to _generate_ the contents of a webpage from data, rather than writing the HTML directly. Moreover, they are what is known as a _single-page application_ as the webpage they create is dynamic and interactive, essentially its own program.  This kind of application will be discussed in the [web application course](https://textbooks.cs.ksu.edu/cis526).