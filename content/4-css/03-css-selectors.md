---
title: "CSS Selectors"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---

In the example from the previous section, we saw:

```
p {
  color: red;
  background-color: green;
}
```

Here the `p` is a _CSS Selector_, which tells us what elements on the page the CSS rules should be applied to.

## Simple Selectors
The most basic CSS selectors come in several flavors, which we'll take a look at next.  Simple selectors are a string composed of alphanumeric characters, dashes (`-`), and underscores (`_`).  Certain selectors also use additional special characters.

### Type Selector
Type selectors apply to a specific type of HTML element.  The `p` in our example is a type selector matching the paragraph element.  

A type selector is simply the name of the HTML element it applies to - the tag name from our discussion of HTML element structure.  

### Class Selector 
A class selector is a proceeded by a period (`.`), and applies to any HTML element that has a matching `class` attribute.  For example, the CSS rule:

```css 
.danger { 
  color: red;
}
```

would apply to both the paragraph and button elements:

```html 
<h1>Hello</h1>
<p class="danger">You are in danger</p>
<button class="danger">Don't click me!</button>
```

as both have the class `danger`.  A HTML element can have multiple classes applied, just separate each class name with a space:

```html
<p class="danger big-text">I have two classes!</p>
```

### ID Selector
An ID selector is proceeded by a hash (`#`) and applies to the HTML element that has a matching `id` attribute. Hence:

```html 
<p id="lead">This paragraph has an id of "lead"</p>
```

would be matched by:

```css 
#lead {
  font-size: 16pt;
}
```

It is important to note that the `id` attribute _should be unique within the page_.  If you give the same id to multiple elements, the results will be unpredictable (and doing so is invalid HTML).  

### Universal Selector

The asterisk (`*`) is the universal selector, and applies to all elements.  It is often used as part of a *reset* - CSS rules appearing at the beginning of a CSS document to remove browser-specific styles before applying a site's specific ones.  For example:

```css
* {
  margin: 0;
  padding: 0;
}
```

sets all element margins and paddings to 0 instead of a browser default.  Later rules can then apply specific margins and padding.

### Attribute Selector 

The attribute selector is wrapped in square brackets (`[]`) and selects HTML elements with matching attribute values, i.e.:

```css
[readonly] {
  color: gray;
}
```

will make any element with a `readonly` attribute have gray text.  The value can also be specified exactly, i.e.

```css
[href="www.k-state.edu"]
```

or partially.  See [MDN's documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors#Syntax) for details.


## Compound Selectors 

Simple selectors can be used in conjunction for greater specificity.  For example, `a.external-link` selects all `<a>` elements with a class of `external-link`, and `input[type=checkbox]` selects all `<input>` elements with an attribute `type` set to `checkbox`.

## Pseudo-Class 

Pseudo-class selectors are proceeded with a single colon (`:`), and refer to the state of the element they modify.  Pseudo-classes must therefore be appended to a selector.  

The most commonly used pseudo-class is `:hover`, which is applied to an element that the mouse is currently over.  Moving the mouse off the element will make this selector no longer apply. For example, `a:hover` applies only to `<a>` elements with the mouse directly over them.

Another extremely useful pseudo-class is `:nth-child()`, which applies to the nth child (specify as an argument), i.e. `ul:nth-child(2)` will apply to the second child of any unordered list.  Additionally, `tr:nth-child(odd)` will apply to the odd-numbered rows of a table.

Additional pseudo-classes can be found in the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

## Combinators

Combinators can be used to combine both simple and compound selectors using an operator.

### Adjacent Sibling Combinator

The plus symbol (`+`) can be used to select an adjacent sibling HTML element.  To be siblings, the first element must be followed by the second, and both must be children of a shared parent.  I.e.:

```css
h1 + p {
  font-weight: bold;
}
```

will bold all paragraphs that directly follow a first-level header.

### General Sibling Combinator

The tilde symbol (`~`) also selects a sibling, but they do not need to be adjacent, just children of the same parent.  The first element must still appear before the second (just not immediately after).

### Child Combinator 

The greater than symbol (`>`) selects elements that are direct children of the first element.  For example:

```css 
p > a {
  font-weight: bold;
}
```

Will bold all anchor elements that are direct children of a paragraph element.

### Descendant Combinator

A space (` `) selects elements that are descendants of the first element. 


## Multiple Selectors 

Finally, we can apply the same rules to a collection of selectors by separating the selectors with commas, i.e.:

```css 
a, p, span {
  font-family: "Comic Sans", sans-serif;
}
```

Applies Comic Sans as the font for all `<a>`, `<p>`, and `<span>` elements.

## Pseudo-Elements

An interesting newer development in CSS is the development of _psuedo-elements_, selectors that go beyond the elements included in the HTML of the page.  They are proceeded by _two_ colons (`::`).  For example, the `::first-letter` selector allows you to change the first letter of a HTML element.  Thus:

```css 
p:first-child::first-letter {
  font-size: 20px;
  font-weight: bold;
  float: left;
}
```

creates drop caps for all initial paragraphs.

A second use of pseudo-elements is to create new elements around existing ones with `::before` or `::after`.  For example:

```css
a.external-link::after {
 content: url(external-link-icon.png); 
}
```

Would add the `external-link-icon.png` image after any `<a>` elements with the `external-link` class.

More information can be found in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements).