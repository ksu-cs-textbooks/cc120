---
title: "SVG Animation"
pre: "17. "
weight: 160
date: 2018-08-24T10:53:26-05:00
---

SVG has several build-in approaches to add animation to a drawing, the `<animate>` and `<animateMotion>` elements. 

## The &lt;animate&gt; Element

The `<animate>` element is used to animate the attributes of an element over time.  It must be declared as a _child_ of the element it will animate, i.e.:

<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <circle cx="50" cy="50" r="50" fill="cornflowerblue">
    <animate attributeName="r" values="10;50;20;50;10" dur="10s" repeatCount="indefinite"/>
  </circle>
</svg>

```svg
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <circle cx="50" cy="50" r="50" fill="cornflowerblue">
    <animate attributeName="r" values="10;50;20;50;10" dur="10s" repeatCount="indefinite"/>
  </circle>
</svg>
```

Here we have a 10 second duration repeating animation that alters the radius of a circle between a number of different values. We can combine multiple `<animate>` elements in one parent:

<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <rect x="25" y="25" width="50" height="50" fill="goldenrod">
    <animate attributeName="rx" values="0;50;0" dur="3s" repeatCount="indefinite"/>
    <animate attributeName="x" values="0;150;0" dur="5s" repeatCount="indefinite"/>
  </circle>
</svg>

## The &lt;animateMotion&gt; Element

The `<animateMotion>` element moves an element along a path (using the same rules to define a path as the `<path>` element):

<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <path
    fill="none"
    stroke="lightgrey"
    d="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />

  <circle r="5" fill="red">
    <animateMotion
      dur="10s"
      repeatCount="indefinite"
      path="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />
  </circle>
</svg>

```svg
<svg viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg" height="200">
  <path
    fill="none"
    stroke="lightgrey"
    d="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />

  <circle r="5" fill="red">
    <animateMotion
      dur="10s"
      repeatCount="indefinite"
      path="M20,50 C20,-50 180,150 180,50 C180-50 20,150 20,50 z" />
  </circle>
</svg>
```

{{% notice info %}}
The examples on this page have been adapted from the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/SVG). You are encouraged to visit these documents for a much more detailed discussion of the concepts and techniques presented here.
{{% /notice %}} 