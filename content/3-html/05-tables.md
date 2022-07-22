---
title: "Tables"
pre: "5. "
weight: 50
date: 2018-08-24T10:53:26-05:00
---
Tables were amongst the first addition to HTML (along with images), as they were necessary for the primary role of early HTML, disseminating research.

A table requires a _lot_ of elements to be nested in a specific manner.  It is best expressed through an example:

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Darth Vader</td>
      <td>Antagonist</td>
    </tr>
    <tr>
      <td>Luke Skywalker</td>
      <td>Coming-of-age protagonist</td>
    </tr>
    <tr>
      <td>Princess Lea</td>
      <td>Heroic resistance fighter</td>
    </tr>
    <tr>
       <td>Obi-Wan Kenobi</td>
       <td>Wise old man</td>
    </tr>
    <tr>
      <td>Han Solo</td>
      <td>Likeable scoundrel</td>
    </tr>
    <tr>
      <td>Chewbacca</td>
      <td>The muscle</td>
    </tr>
    <tr>
      <td>Threepio</td>
      <td>Comedic foil</td>
    </tr>
    <tr>
      <td>Artoo Deetoo</td>
      <td>Plot driver</td>
    </tr>
  </tbody>
</table>
```

It renders as:

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Darth Vader</td>
      <td>Antagonist</td>
    </tr>
    <tr>
      <td>Luke Skywalker</td>
      <td>Coming-of-age protagonist</td>
    </tr>
    <tr>
      <td>Princess Lea</td>
      <td>Heroic resistance fighter</td>
    </tr>
    <tr>
       <td>Obi-Wan Kenobi</td>
       <td>Wise old man</td>
    </tr>
    <tr>
      <td>Han Solo</td>
      <td>Likeable scoundrel</td>
    </tr>
    <tr>
      <td>Chewbacca</td>
      <td>The muscle</td>
    </tr>
    <tr>
      <td>3PO</td>
      <td>Comedic foil</td>
    </tr>
    <tr>
      <td>R2-D2</td>
      <td>Plot driver</td>
    </tr>
  </tbody>
</table>

Tables should _only_ be used for displaying tabular data.  There was a time, not long ago, when early web developers used them to create layouts by cutting images into segments and inserting them into table cells.  __This is very bad practice!__  It will not display as expected in all browsers, and wreaks havoc with screen readers for the visually impaired.  Instead, pages should be laid out with CSS, as is discussed in the CSS layouts section.

A far more detailed discussion of tables can be found in [MDN's guides](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics).
