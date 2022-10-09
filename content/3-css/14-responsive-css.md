The World-Wide-Web was developed at a time when the desktop computer was the primary means of accessing the Internet.  As tablets and mobile devices emerged, the smaller screen sizes and resolutions, as well as the need to be able to trigger links and buttons with a finger instead of the much smaller mouse pointer created serious challenges.

Early solutions were to design _two_ web sites (one intended for desktop use, and one for mobile) or develop a native app (that would install on the phone).  The drawback of these approaches would often result in a watered-down mobile experience and duplication of code. As we moved forward into the 2000's, a new option emerged through new versions of the CSS standards.  New rules were introduced, and old ones adapted into an approach now called _responsive CSS_, which alters the appearance of a web application to make a better user experience on mobile devices, without any changes to the HTML.

## Media Queries 
At the heart of the responsive CSS approach is a CSS technique called _media queries_.  These are implemented with a CSS media at-rule (at-rules modify the behavior of CSS, and are proceeded by an at symbol (`@`), hence the name).  The original purpose of the media rule was to define different media types - i.e. `screen` and `print`, which would be selectively applied based on the media in play.  For example, the rule:

```css 
@media print {
  img {
    display: none;
  }
  .advertisement {
    display: none;
  }
}
```

would hide all images and elements with the `advertisement` class when printing a web page.  You can also specify the media type with the `media` attribute in a `<link>` element, i.e. `<link href="print.css" rel="stylsheet" media="print">` would apply the rules from `print.css` only when printing the website.

However, the real usefulness of the `@media` rule is when it is combined with a _media query_, which determines if its nested rules should be applied based on some aspect of the display.  Media queries are expressed in parenthesis following the `@media` and optional type, i.e.:

```css
@media (orientation: portrait) {
  /* rules for a portrait orientation go here... */ 
}
```

Will apply conditional rules when the screen is in portrait orientation (taller than it is wide).  We can also combine multiple queries into a single `@media` rule:

```css
@media (orientation: landscape) and (max-width: 700px) {
  /* rules for a landscape-oriented screen 700 pixels or less wide */
}
```

The `and` in this case works like a logical `and`.  You can also use the `not` keyword, which inverts the meaning of the query, or commas `,`, which operate like a logical `or`.

More details on the use of media queries can be found in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) on the subject.

By combining the use of media queries, and CSS layout techniques, you can drastically alter the presentation of a web application for different devices.  Most browser development tools will also let you preview the effect of these rules by selecting a specific device size and orientation.  See the [Chrome Device Mode](https://developers.google.com/web/tools/chrome-devtools/device-mode/) documentation, Safari [Developer Documentation](https://developer.apple.com/safari/tools/), and Firefox [Responsive Design Mode Documentation](https://developer.mozilla.org/en-US/docs/Tools/Responsive_Design_Mode) for details.


## Viewport Meta Element 

When mobile phones first started browsing the web, the disparity in screen sizes caused some serious challenges, as many web pages designed for the desktop broke horribly on smaller screens.  What became the standard technique was for browsers to render the HTML page at a desktop resolution, then apply a scaling factor to fit the page onto the phone.  In effect, you could see the entire web page, but would have to zoom in to actually read any part of it.  It was clearly a compromise, but worked well enough for the time.

This default approach will not work for responsive design, however, as assuming a desktop resolution will not trigger our media queries based on screen size.  Instead, we need to signal to the mobile browser that we wish to render the page at the device's native resolution, with no scaling applied.  This is done by adding a `<meta>` element to our `<head>` section of the HTML page:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

A `<meta>` element is used to convey metadata about the HTML page.  Traditionally it was used to add keywords that search engines could reference (though this traditional use was abused by search-engine optimization hacks, and has largely been abandoned).  The `name` attribute lets the browser know the purpose of the `<meta>` element; the value of `viewport` indicates we want to define the viewport (the size of the portion of the web page appearing on screen).  By setting the `width` to `device-width`, we indicate we want to render our page at the screen size, and the `initial-scale` value of `1.0` indicates we don't want to apply any scaling.  

Remember, without this `<meta>` element, responsive designs do not behave as expected on mobile devices!
