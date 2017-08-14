# HTML

## Syntax and formatting
Roughly, we want:
- tabs, not spaces;
- nested tags are indented consistently;
- meaningful use of whitespace;
- no commented-out code.

## Linting
HTML code is linted by [HTMLHint](https://www.npmjs.com/package/htmlhint). See the Handlebars POC for configuration.

In addition to HTMLHint, the following standards should be followed. Source: [Linting HTML using CSS](https://bitsofco.de/linting-html-using-css/)

## Specify document language
Specify a document language with the `<html>` tag's `lang` attribute:
```html
<html lang="en">
<!-- To specify a country code too -->
<html lang="en-US">
```

## Specify document character encoding
```html
<meta charset="UTF-8">
```
This tag tells the browser to use the UTF-8 form of character encoding, which is presently the recommended form for HTML documents. Having this tag is therefore required for valid HTML. Ideally, this tag should also be the first element after the opening `<head>` tag.

## Avoid unaccessible viewport attributes
It is generally advised that we avoid restricting the user's ability to manipulate the viewport by shrinking and enlarging it. So, using `user-scalable=no`, `maximum-scale`, or `minimum-scale` should never be used.

## Label form elements
Check that all form elements have an ID, and that they are linked to a label with that ID using the `for` attribute. Also, all form elements should have a `name` attribute.

Also, any form element (`<form>`) should have an `id` and `name` attribute.

## Avoid empty interactive elements
Interactive elements like links or buttons are typically labelled by their content. Although it is possible to label these elements using other methods, such as an aria-label attribute, having them be empty is likely a sign of something wrong.

## Avoid unnecessary or deprecated attributes
```html
<!-- Yep -->
<script src="_assets/js/main.js"></script>
<link rel="stylesheet" href="/_assets/css/main.css">

<!-- Nope -->
<script type="text/javascript" src="_assets/js/main.js"></script>
<link rel="stylesheet" type="text/css" href="/_assets/css/main.css">
```

## Avoid closing void elements
Since you are using the HTML5 doctype, closing void elements is unnecessary. Void elements include the following tags:
`<area>`, `<base>`, `<br>`, `<col>`, `<embed>`, `<hr>`, `<img>`, `<input>`, `<keygen>`, `<link>`, `<menuitem>`, `<meta>`, `<param>`, `<source>`, `<track>`, `<wbr>`
```html
<!-- Yep -->
<link href="/_assets/css/main.css">

<!-- Nope -->
<link href="/_assets/css/main.css" />
```

## Special characters
If using HTML5 and UTF-8 character encoding, it is preferable to use characters instead of named character references whenever possible. This increases readability of the text within the code and decreases file size. However, for the following special characters, using the named character references is required in HTML:
- `&lt; (<)`
- `&gt; (>)`
- `&amp; (&)`

It is also required to use named character references for the single and double quote characters when used inside of attribute text surrounded with the same characters.
- `&quote; (")`
- `&apos; (')`

Source: https://www.w3.org/International/questions/qa-escapes#use

## Avoid JS files that block parsing
Linked JS files should not unnecessarily block parsing the rest of the page. `asyc` and `defer` attributes should be used where appropriate. See more info in [Asynchronous vs Deferred JavaScript](https://bitsofco.de/async-vs-defer/)
