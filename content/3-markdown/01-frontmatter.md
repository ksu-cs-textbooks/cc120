---
title: "Frontmatter"
pre: "1. "
weight: 10
date: 2018-08-24T10:53:26-05:00
---

{{% notice note %}}

This content details additions to the the original version in the [Hugo Theme Learn Documentation](https://learn.netlify.app/en/cont/pages/#front-matter-configuration).

{{% /notice %}}

## Front Matter configuration

The following items are unique to this theme.

```toml
+++
# Set the page as a section, changing the way it's displayed
section = false
+++
```

The **section** item tells Hugo to use a slightly different CSS layout on the rendered page (similar to a **chapter** but with different text formatting).

### Reveal.js Slides

For Reveal.js slides, the frontmatter is as follows:

```yaml
---
type: "reveal"
hidden: true
---
```

These items are unique:

* **type**: this tells Hugo to render this page as a Reveal.js page, which will use a different template
* **hidden**: this will remove this item from the menu on the left. This can be added to any page.

There are many other items that can be added. See [Hugo Frontmatter](https://gohugo.io/content-management/front-matter/) for details.

{{% notice note %}}

Yes, I realize that most pages are using the YAML format for frontmatter (as indicated by the `---` surrounding the block as described in the Hugo documentation), but the chapter pages are using TOML (surrounded by `+++` instead). I did this simply because the template pages were set that way, but not for any particular reason.

{{% /notice %}}