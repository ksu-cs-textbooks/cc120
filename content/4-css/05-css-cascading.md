---
title: "CSS Cascade"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---

Now that we know how to create an apply CSS rules to our HTML, let's explore how they actually are used.  A core idea behind CSS is the __cascade algorithm__, the _cascading_ in _cascading style sheets (CSS)_.  The core idea behind the cascade algorithm is that as the browser encounters and parses CSS rules, they are collectively applied to the elements they match with.  If the same rule is set multiple times, say `color`, the cascading algorithm decides which should be applied. 

## CSS Sources
Before we look at how cascades work, we need to understand the sources of CSS rules.  So far we've focused on CSS rules created by the _author_ - that is, the developer of the website.  But there are two other sources of CSS rules, the _user-agent_ and the _user_.

### User-Agent
The term __user-agent__ is the technical way of describing the browser (or other software) that is accessing the webpage.  Most browsers define default styles for their browser that help differentiate them from other browsers.  These default values work well for less-styled websites, but for a carefully designed user experience, an unexpected rule can wreak havoc.

For this reason, many websites use a special CSS file that overrides user-agent sheets to allow the website to start from a well-known state.  This is possible because rules appearing in sheets defined by the author override those defined in user-agent sheets.

### Author 
The __author__ is simply the creator of the webpage.  Thus, rules included with the `<link>` or `<style>` elements, as well as in-line styles defined on the elements themselves with the `style` attribute, fall into this category.  Author styles always override user-agent styles, and are overridden in turn by user styles.

### User 
The __user__ is the actual user of the browser, and they can add their own styles to an HTML document in a variety of ways.  One that you may encounter the most is adding custom styles with the web developer tools.  One that you may have not encountered, but is common in practice, are styles intended to make the website easier for the vision impaired to read and work with.  Increasing or decreasing text size with `[CTRL] + [+]` or `[CTRL] + [-]` is a simple example of this kind of tool.

## Cascading Order

Thus, the general order of rules applied by the cascading algorithm is user-agent, author, user.  However, there is also the `!important` directive that can be added to CSS rules, i.e.:

```css
p {
  color: red !important
}
```

which escalates them to a higher pass.  Also, CSS animations and transitions are evaluated at their own priority level.  Thus, we have a cascade order of:

<table class="standard-table">
		<thead>
			<tr>
				<th scope="col">&nbsp;</th>
				<th scope="col">Origin</th>
				<th scope="col">Importance</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>1</td>
				<td>user agent</td>
				<td>normal</td>
			</tr>
			<tr>
				<td>2</td>
				<td>user</td>
				<td>normal</td>
			</tr>
			<tr>
				<td>3</td>
				<td>author</td>
				<td>normal</td>
			</tr>
			<tr>
				<td>4</td>
				<td>animations</td>
				<td>&nbsp;</td>
			</tr>
			<tr>
				<td>5</td>
				<td>author</td>
				<td><code>!important</code></td>
			</tr>
			<tr>
				<td>6</td>
				<td>user</td>
				<td><code>!important</code></td>
			</tr>
			<tr>
				<td>7</td>
				<td>user agent</td>
				<td><code>!important</code></td>
			</tr>
			<tr>
				<td>8</td>
				<td>transitions</td>
				<td>&nbsp;</td>
			</tr>
		</tbody>
	</table>

A more thorough discussion of the Cascade Algorithm can be found in the [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade).
