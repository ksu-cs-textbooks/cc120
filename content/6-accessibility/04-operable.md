---
title: "Operable Content"
pre: "4. "
weight: 40
date: 2018-08-24T10:53:26-05:00
---

In short, the user should be able to interact effectively with your website. There are two primary tools we use to interact with websites - the mouse and the keyboard.  Additionally, many assistive technologies mimic one or both of these.

### Keyboard-Only Control

While most of us use a mouse as our primary control tool for working with any software, many users cannot use a mouse effectively.  For these users, it is important that the entire web page can be controlled using the keyboard.

### Tab Order
An important mechanism for replacing mouse movement in a keyboard-only control scheme is the use of the `[Tab]` key to move focus to a particular element on the page.  Try using your tab key on this page - you'll notice that different interactive elements of the page are highlighted in turn (i.e. links, buttons, videos, inputs, etc.).  Pressing `[Enter]` while a link is focused will follow the link.  Pressing `[Space]` will start or stop a media element (video or audio).

The order that the `[Tab]` key moves through the elements on the page is known as the _tab order_, and generally will be in the order the elements appear on the page.  However, this can be overridden in HTML by the setting the `tabindex` attribute.  This attribute can also make an element that is not normally in the tab order (like a `<p>` tag, tabbable).

### Accessible Rich Internet Applications (ARIA)

Many web applications utilize regular HTML elements to create interactive experiences. When these rely on vision and mouse interaction (for example, image carousels), they can be inaccessible for many people. The roles and attributes defined by ARIA seeks to provide a mechanism to allow these widgets to interact more effectively with assistive technologies.

They do this in two ways - through the use of roles (which describe the role of the element in the page) and through attributes (which convey information to assistive technologies).

#### ARIA Roles
The roles describe the intent of an HTML tag that has no semantic meaning - i.e. a `<div>`. This can help convey through a screen reader what most users would deduce visually.  For example, if we were displaying a math equation, we could use the `math` role:

```html
<div role="math">
  y = 1/2x + 3
</div>
```

Likewise, an image containing an equation could be labeled with the `math` role:

```html
<img src="line-eq.png" alt="The equation for the line y = 1/2x + 3" role="math">
```

ARIA began as an extension to HTML, but many of its ideas have now been integrated directly into HTML through semantic equivalents.Where possible, use HTML5 equivalents, i.e.

* `article` use `<article>`
* `figure` use `<figure>`
* `img` use `<image>` or `<picture>`
* `main` use `<main>`
* `navigation` use `<nav>`
* `region` use `<section>`

You can find a complete list of roles and recommendations for using them [in the MDN documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles).

#### ARIA Attributes

ARIA attributes convey information to assistive technologies. For example, the `aria-hidden` attribute signals to assistive technologies that a particular element can be ignored by the assistive technology. Consider a product logo that appears in multiple locations on the page. 

```html
<img src="logo.png" alt="logo" aria-hidden="true"/>
```

The `aria-hidden` here indicates to a screen reader that it does not need to call out to the viewer the existence of the logo.

You can find a full list of ARIA attributes [in the MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes).


<!--

There are six categories of ARIA roles:

#### Document Structure Roles 
These identify the _structural_ purpose for a section of content.  I.e. a <div> that only appears when an associated element is hovered over we would call a _tooltip_:

```html
When you hover over this 
<span class="tooltip-wrapper">
  term
  <div class="tooltip" role="tooltip">
    Hello! I'm a tooltip!
  </div>
</span>
, you will get a surprise!
<style>
  .tooltip { 
    display: none; 
  }
  .tooltip-wrapper { 
    font-weight: bold;
  }
  .tooltip-wrapper:hover>.tooltip 
  {
    position: absolute;
    display: block;
    border: 2px gray;
    padding: 5px;    
    background-color: yellow;
  }
</style>
```

<div style="border: 1px solid black; padding: 2rem;">
When you hover over this 
<span class="tooltip-wrapper">
  term
  <div class="tooltip" role="tooltip">
    Hello! I'm a tooltip!
  </div>
</span>
, you will get a surprise!
<style>
  .tooltip { 
    display: none; 
  }
  .tooltip-wrapper { 
    font-weight: bold;
  }
  .tooltip-wrapper:hover>.tooltip 
  {
    position: absolute;
    display: block;
    border: 2px gray;
    padding: 5px;    
    background-color: yellow;
  }
</style>
</div>

ARIA began as an extension to HTML, but many of its ideas have now been integrated directly into HTML through semantic equivalents.Where possible, use HTML5 equivalents, i.e.

* `article` use `<article>`
* `figure` use `<figure>`
* `img` use `<image>` or `<picture>`

You can find a full list of structural roles [in the MDN documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles#1._document_structure_roles)

#### Widget Roles 
These describe common interactive patterns found in websites.  The most common of these are:

* scrollbar
* searchbox
* separator (when focusable)
* slider
* spinbutton
* switch
* tab
* tabpanel
* treeitem
* combobox
* menu
* menubar
* tablist
* tree
* treegrid

You can find a full list [in the MDN documentation](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles#2._widget_roles)

#### Landmark Roles

Landmark roles help identify the organization and structure of a web page - i.e. what is the most important part (`main`), complementary information (`complementary`), or search controls (`search`).  Many of these have been replaced by semantic HTML elements.

* `banner` typically use `<header>`
* `complementary` use (`<aside>`)
* `contentinfo` typically use `<footer>`
* `main` use `<main>`
* `navigation` use `<nav>`
* `region` use `<section>`
* `search`

You can read more about these roles [in the MDN web docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles#3._landmark_roles).

#### Live Region Roles

These indicate content that will be dynamically changed:

* `alert`
* `log`
* `marquee`
* `status`
* `timer`

#### Window Roles

These are sub-windows to the main document window, i.e. dialogs.

* `alertdialog`
* `dialog`

#### Abstract Roles

These are used by browsers to organize and streamline document loading.  You should not use them in your HTML.

-->