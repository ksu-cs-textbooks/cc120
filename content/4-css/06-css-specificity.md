---
title: "CSS Specificity"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---

But what about two rules that conflict that appear in the same level of the cascade order? For example, given the CSS:

```css
p {
  color: black;
}
.warning {
  color: red;
}
```

what would the color of `<p class="warning">` be?  You might say it would be `red` because the `.warning` CSS rules come _after_ the `p` rules.  And that would be true if the two rules had the same _specificity_.  An example of that is:

```css
p {color: black}
p {color: red}
```

Clearly the two selectors are equivalent, so the second `color` rule overrides the first.  But what if we go back to our first example, but flip the rules?

```css
.warning {
  color: red;
}
p {
  color: black;
}
```

In this case, the color is _still_ `red`, because `.warning` is more _specific_ than `p`.  This is the concept of _specificity_ in CSS, which has an actual, calculable value.

## Specificity Calculations

The specificity of a selector increases by the type and number of selectors involved.  In increasing value, these are:

1. Type selectors and pseudo-elements 
2. Class selectors, attribute selectors, and pseudo-classes 
3. ID selectors 

Each of these is trumped by in-line CSS rules, which can be thought of as the highest specificity.  Thus, we can think of specificity as a 4-element tuple (A, B, C, D):

![Specificity Tuple](images/4.6.1.png)

We can then calculate the values of A,B,C,D:
* Count 1 if the declaration is from a ‘style’ attribute (inline style) rather than a rule with a selector, 0 otherwise (= A).
* Count the number of IDs in the selector (= B).
* Count the number of Classes, attributes and pseudo-classes in the selector (= C).
* Count the number of Element names and pseudo-elements in the selector (= D).

## The !important Loophole

Finally, there is an extra trick that we can use when we are having trouble creating enough specificity for a CSS rule.  We can add `!important` to the rule declaration.  For example:

```css
p {
  color: red !important;
}
```

The `!important` rule overrides any other CSS declarations, effectively sidestepping specificity calculations.  It should be avoided whenever possible (by making good use of specificity), but there are occasions it might be necessary.

If multiple rules use `!important`, then their priority is again determined by specificity amongst the group.

