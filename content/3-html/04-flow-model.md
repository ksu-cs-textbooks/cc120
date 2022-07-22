---
title: "Flow Model"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

Given that the role of HTML is _markup_, i.e. providing structure and formatting to text, HTML elements can broadly be categorized into two categories depending on how they affect the flow of text - inline and block.   

Inline elements referred to elements that maintained the flow of text, i.e. the _bring attention to_ (`<b>`) element used in a paragraph of text, would bold the text without breaking the flow:

`<p>The quick brown <b>fox</b> lept over the log</p>`

The quick brown <b>fox</b> lept over the log

In contrast, block elements break the flow of text. For example, the `<blockquote>` element used to inject a quote into the middle of the same paragraph:

`<p>The quick brown fox <blockquote>What does the fox say? - YLVIS</blockquote> lept over the log</p>`

The quick brown fox <blockquote>What does the fox say? - YLVIS</blockquote> lept over the log

While HTML elements default to either block or inline behavior, this can be changed with the CSS `display` property.
