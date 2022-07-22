---
title: "Forms"
pre: "6. "
weight: 60
date: 2018-08-24T10:53:26-05:00
---
Forms were also amongst the first additions to the HTML standard, and provide the ability to submit data to a web server.  A web form is composed of `<input>`, `<textarea>`, `<select>` and similar elements nested within a `<form>` element.

## The Form Element

The form element primarily is used to organize input elements and specify how they should be submitted.  In its simplest form, it is simply a tag that other elements are nested within:

`<form></form>`

However, it can be modified with a number of attributes:

* __action__ The `action` attribute specifies the url that this form data should be sent to. By default, it is the page the form exists on (i.e. if the form appears on http://foo.com/bar, then it will submit to http://foo.com/bar).  The url can be relative to the current page, absolute, or even on a different webserver.  See the discussion of URLs in the HTTP section.

* __enctype__ The `enctype` attribute specifies the format that form data will be submitted in.  The most common values are `application/x-www-form-urlencoded` (the default), which serializes the key/value pairs using the urlencoding strategy, and `multipart/form-data`, which uses the multipart encoding scheme, and can interweave binary (file) data into the submission.  These encoding strategies are discussed more thoroughly in the chapter on submitting form data.

* __method__ The `method` attribute specifies the HTTP method used to submit the form.  The values are usually `GET` or `POST`. If the method is not specified, it will be a `GET` request.

* __target__ The target attribute specifies how the server response to the form submission will be displayed. By default, it loads in the current frame (the `_self`) value.  A value of `_blank` will load the response in a new tab.  If `<iframe>` elements are being used, there are additional values that work within `<iframe>` sets.

## The Input Element 

Most inputs in a form are variations of the `<input>` element, specified with the `type` attribute.  Many additional specific types were introduced in the HTML5 specification, and may not be available in older browsers (in which case, they will be rendered as a _text_ type input).  Currently available types are (an asterisk indicate a HTML5-defined type):

* __button__: A push button with no default behavior.
* __checkbox__: A check box allowing single values to be selected/deselected.  It has an extra attributed `checked`, which is a boolean specifying if it is checked.
* __color*__: A control for specifying a color. 
* __date*:__ A control for entering a date (year, month, and day, with no time).
* __datetime-local*__: A control for entering a date and time, with no time zone.
* __email:__ HTML5 A field for editing an e-mail address.
* __file:__ A control that lets the user select a file. Use the accept attribute to define the types of files that the control can select.
* __hidden:__ A control that is not displayed but whose value is submitted to the server.
* __image:__ A graphical submit button. You must use the src attribute to define the source of the image and the alt attribute to define alternative text. You can use the height and width attributes to define the size of the image in pixels.
* __month*:__ A control for entering a month and year, with no time zone.
* __number*:__ A control for entering a number.
* __password:__ A single-line text field whose value is obscured. 
* __radio:__ A radio button, allowing a single value to be selected out of multiple choices.
* __range*:__ A control for entering a number whose exact value is not important.
* __reset:__ A button that resets the contents of the form to default values.
* __search*:__ A single-line text field for entering search strings. Line-breaks are automatically removed from the input value.
* __submit:__ A button that submits the form.
* __tel*:__ A control for entering a telephone number.
* __text:__ A single-line text field. Line-breaks are automatically removed from the input value.
* __time*:__ A control for entering a time value with no time zone.
* __url*:__ A field for entering a URL.
* __week*:__ A control for entering a date consisting of a week-year number and a week number with no time zone.

In addition to the _type_ attribute, some other commonly used input attributes are:

* __name__ The name of the attribute, which is used to identify the submitted value (the name and value attributes define a key/value pair)
* __value__ The input's current value
* __placeholder__ A string to display in the input until a value is entered (typically used as a prompt).  The placeholder is never submitted as a value.
* __readonly__ A boolean attribute that when true, indicates the input value cannot be changed
* __required__ A boolean value indicating that the input is required to have a value before it can be submitted.
* __tabindex__ Indicates the order in which inputs can be reached by hitting the tab key.  For dense input forms, this can be important.
* __disabled__ A boolean value that when true, means the input is disabled (does not submit a value, cannot be interacted with, and is grayed out)

## Other "Input" Elements

In addition to the `<input>` element, some other elements exist that provide input-type functionality within a form, and implement the same attributes as an `<input>`.  These are:

### Textarea 

The `<textarea>` element provides a method for entering larger chunks of text than a `<input type="text">` does.  Most importantly, it preserves line-breaks (the `<input type="text">` removes them).  Instead of using the `value` attribute, the current value appears inside the opening and closing tags, i.e.:

```html
<textarea name="exampleText">
  This text is displayed within the textarea
</textarea>
```

In addition, the `rows` and `cols` attribute can be used to specify the size of the textarea in characters.

### Select 

The `<select>` element allows you to define a drop-down list.  It can contain as children, `<option>` and `<optgroup>` elements.  The `<select>` element should have its `name` attribute specified, and each `<option>` element should have a unique `value` attribute.  The selected `<option>`'s value is then submitted with the `<select>`'s name as a key/value pair.

Each `<select>` element should also have a closing tag, and its child text is what is displayed to the user.  

The `<optgroup>` provides a way of nesting `<option>` elements under a category identifier (a `label` attribute specified on the `<optgroup>`).

An example `<select>` using these features is:

```html
<select name="headgear">
  <option value="none">None</option>
  <optgroup label="Hats">
    <option value="ball cap">Ball Cap</option>
    <option value="derby">Derby</option>
    <option value="fedora">Fedora</option>
  </optgroup>
  <optgroup value="Ceremonial">
    <option value="crown">Crown</option>
    <option value="mitre">Mitre</option>
    <option value="war bonnet">War Bonnet</option>
  </optgroup>
</select>
```

Finally, multiple selections can be allowed by specifying a `multiple` attribute as `true`.  

## Labels 

In addition to inputs, a `<form>` often uses `<label>` elements to help identify the inputs and their function.  A label will typically have its `for` attribute set to match the `name` attribute of the `<input>` it corresponds to.  When connected in this fashion, clicking the label will give focus to the input.  Also, when the `<input type="checkbox">`, clicking the label will also toggle the `checked` attribute of the checkbox.

## Fieldsets

Finally, the `<fieldset>` element can be used to organize controls and labels into a single subcontainer within the form.  Much like `<div>` elements, this can be used to apply specific styles to the contained elements.  