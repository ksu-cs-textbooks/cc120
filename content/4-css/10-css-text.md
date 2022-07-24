---
title: "CSS and Text"
pre: "10. "
weight: 100
date: 2018-08-24T10:53:26-05:00
---

As the original purpose of the World-Wide-Web was to disseminate written information, it should be no surprise that CSS would provide many properties for working with text.  Some of the most commonly employed properties are:

* `font-family` defines the font to use for the text.  Its value is one or more font family or generic font names, i.e. `font-family: Tahoma, serif`, `font-family: cursive` or `font-family: "Comic Sans"`.  Font family names are typically capitalized and, if they contain spaces or special characters, double-quoted.  
* `font-size` determines the size of the font. It can be a measurement or a defined value like `x-small`.
* `font-style` determines if the font should use its `normal` (default), `italic`, or `oblique` face.
* `font-weight` determines the weight (boldness) of the font.  It can be `normal` or `bold` as well as `lighter` or `darker` than its parent, or specified as a numeric value between 1 and 1000.  Be aware that many fonts have a limited number of weights.
* `line-height` sets the height of the line box (the distance between lines of text).  It can be `normal`, or a numeric or percent value.
* `text-align` determines how text is aligned. Possible values are `left` (default), `center`, `right`, `justify`, along with some newer experimental values.
* `text-indent` indents the text by the specified value.
* `text-justify` is used in conjunction with `text-align: justify` and specifies how space should be distributed.  A value of `inter-word` distributes space between words (appropriate for English, Spanish, Arabic, etc), and `inter-character` between characters (appropriate for Japanese, Chinese, etc).
* `text-transform` can be used to capitalize or lowercase text. Values include `capitalize`, `uppercase`, and `lowercase`.

## Choosing Fonts

An important consideration when working with HTML text is that not all users will have the same fonts you have - and if the font is not on their system, the browser will fall back to a different option.  Specifying a generic font name after a Font Family can help steer that fallback choice; for example:

```
body {
  font-family: Lucinda, cursive
}
```

will use Lucinda if available, or another cursive font if not.  Some guidelines on font choice:
* `cursive` fonts should typically only be used for headings, not body text.
* `serif` fonts (those with the additional feet at the base of letters) are easier to read printed on paper, but more difficult on-screen.
* `sans-serif` fonts are easier to read on-screen; your body text should most likely be a sans-serif.

### Web-Safe Fonts 

Fonts that commonly appear across computing platforms and have a strong possibility of being on a users' machine have come to be known as _web-safe_.  Some of these are:

* <span style='font-family: Arial'>Arial</span>
* <span style='font-family: Helvetica'>Helvetica</span>
* <span style='font-family: Times'>Times</span>
* <span style='font-family: "Courier New"'>Courier New</span>
* <span style='font-family: Courier'>Courier</span>
* <span style='font-family: Georgia'>Georgia</span>
* <span style='font-family: "Lucidia Console"'>Lucidia Console</span>
* <span style='font-family: Palatino'>Palatino</span>
* <span style='font-family: Verdana'>Verdana</span>

### Font-Face at Rule 

Alternatively, if you wish to use a less-common font, you can provide it to the browser using the `@font-face` rule. This defines a font and provides a source for the font file:

```css
@font-face {
  font-family: examplefont;
  src: url('examplefont.ttf');
}
```

You can then serve the font file from your webserver.

{{% notice warning %}} 
Be aware that _distributing_ fonts carries different legal obligations than distributing something _printed in_ the font.  Depending on the font license, you may not be legally allowed to distribute it with the `@font-face` rule. Be sure to check.
{{% /notice %}}
