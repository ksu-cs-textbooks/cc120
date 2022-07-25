---
title: "Strict Mode"
pre: "8. "
weight: 80
date: 2018-08-24T10:53:26-05:00
---

JavaScript has been around a long time, and a lot of JavaScript code has been written by inexperienced programmers.  Browser manufacturers compensated for this by allowing lenient interpretation of JavaScript programs, and by ignoring many errors as they occurred.  

While this made poorly-written scripts run, arguably they didn't run well.  In ECMA5, _strict mode_ was introduced to solve the problems of lenient interpretation.

Strict mode [according to the Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode):
1. Eliminates some JavaScript silent errors by changing them to throw errors.
2. Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode.
4. Prohibits some syntax likely to be defined in future versions of ECMAScript.

You can place the interpreter in strict mode by including this line at the start of your JavaScript file:

```js
"use strict";
```

In interpreters that don't support strict mode, this expression will be interpreted as a string and do nothing.