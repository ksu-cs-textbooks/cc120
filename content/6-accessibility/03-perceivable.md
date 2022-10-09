---
title: "Perceivable Content"
pre: "3. "
weight: 30
date: 2018-08-24T10:53:26-05:00
---

What makes web content _perceivable_? Broadly speaking, the user must be able to _see_ the content through one of their senses. We primarily think about this in terms of sight - the user should be able to see the content of the rendered page. But what we hear can also be a critical piece of perception.

### Vision

We often think of vision as the primary sense for engaging with web content - after all we read text and view pictures and videos. So where does perception through vision have potential issues?

#### Screen Resolutions

Let's start by revisiting an idea we covered in Chapter 4, [responsive design]({{<ref "4-css/14-responsive-css">}}).  When a website that does not use responsive design is viewed on a cell phone screen, it is rendered at a larger screen size, then scaled down to fit in the actual viewport. This helps preserve the layout of the page as it was designed, but also means the text is scaled too small to read, and the user must zoom in and pan to see it. Responsive design avoids this pitfall by using a more appropriate layout on a smaller screen.

#### Browser Zoom

Most browsers also support zooming in and out using either a keyboard shortcut (`[ctrl]` + `[+]` to increase, or `[ctrl]` + `[-]` to decrease) or a menu option.  This can make it easier to read (much like large-print books), but changes the viewport size much like described above.  Thus, responsive websites work much better with browser zoom.l

#### Screen Magnification

This also reflect the experience of using a computer for many low-vision users. They often utilize magnification tools that are built into modern operating systems to zoom in on a section of the screen. Try it yourself using the tool available on your operating system:

* [Windows Magnifier](https://support.microsoft.com/en-us/windows/use-magnifier-to-make-things-on-the-screen-easier-to-see-414948ba-8b1c-d3bd-8615-0e5e32204198)
* [Mac Zoom](https://support.apple.com/en-us/HT210978)
* [Chromebook Magnifier](https://support.google.com/accessibility/answer/6320705?hl=en-GB)
* [Android Magnification](https://support.google.com/accessibility/android/answer/6006949?hl=en)
* [iOS Magnifier](https://support.apple.com/guide/iphone/magnify-nearby-objects-iphe867dc99c/ios)

You will likely find that while it makes a portion of the screen easier to see, you now must pan carefully to see the full content of a page.  Keep this in mind as you consider complex layouts where text flows around elements.  While they may be visually appealing at normal sizes, these disjunctions can be difficult to follow when using a magnification tool.

#### Colorblindness

Colorblindness is a condition where a person cannot distinguish the difference between certain colors.  It is a very common condition affecting 1 in 12 men, and 1 in 200 women.  Broadly it is categorized into categories by what colors are difficult to perceive differences between:
* Shades of red and green 
* Shades of blue and yellow
* Any colors
In addition, as eyes age the lenses yellow, which causes blue light to scatter when entering the eye.  Older people may therefore have trouble distinguishing shades of blue, green, and violet.

When using colors to convey meaning to your users, it is therefore a good idea to:
* Use strongly contrasting colors (i.e. opposites on the color wheel, along with highly contrasting shades)
* Provide an alternative method for communicating the meaning implied by color choices (i.e. use icons or words along with the color)

#### Screen Readers

A second important tool for the visually impaired is a _screen reader_ - a program that reads the content of a screen.  As with magnifier tools, screen readers are built into modern operating systems. Find yours and give it a try:

* [Windows Narrator](https://support.microsoft.com/en-us/windows/chapter-1-introducing-narrator-7fe8fd72-541f-4536-7658-bfc37ddaf9c6#WindowsVersion=Windows_10)
* [Mac Voiceover](https://www.apple.com/voiceover/info/guide/_1121.html)
* [Chromebook ChromeVox](https://support.google.com/chromebook/answer/7031755?hl=en)
* [Android TalkBack](https://support.google.com/chromebook/answer/7031755?hl=en)
* [iOS Spoken Content](https://support.apple.com/guide/iphone/spoken-content-iph96b214f0/ios)

Some important things to keep in mind for screen readers: 
1. Images should always have a descriptive `alt` attribute to describe what the image conveys.
2. [Table-based layouts](https://thehistoryoftheweb.com/tables-layout-absurd/) (a staple of 90's web development) are a bane for screen readers.  Try using a screen reader to read the [1996 Space Jam Website](https://www.spacejam.com/1996/) - you'll quickly see why that is a _terrible_ idea.  Tables should be reserved for tabular data. 
3. Interactive widgets constructed from DOM elements are largely ignored by screen readers, unless you've used ARIA tag attributes.  Whenever possible, use the widgets that are part of standard HTML, as these will be read correctly. If not, make sure you use ARIA (we'll discuss that soon).
4. Likewise, elements like `<div>` don't convey any kind of role to a screen reader.  Consider using the semantic equivalents, i.e. `<main>` for main content, `<aside>` for sidebars, `<nav>` for navigation elements, etc.  Otherwise, include `aria-role` attributes in your `<div>` elements.
5. Labels and inputs need to be linked with the `for` attribute so that the screen reader associates the label with the right input.

### Audio 

Other content is delivered through sound - especially video and audio recordings.  Video can (and should) be provided with the option of closed captioning.  Audio and video both can have a script provided.
