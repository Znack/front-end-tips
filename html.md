# HTML

## Semantics

#### Divide elements by meaning
 Sometimes there is an easy way to divide blocks by their appearances because it requires fewer styles. But it is the wrong way that will confuse your teammates and make the app less scalable

#### Don't insert block elements inside inlines
 Avoid such a code: `<span><div></div></span>`

#### Check all text elements with large content
 Use long names and long descriptions for all available text elements

#### Use tags `<h1>...<h6>` only for headings
 Only one  `<h1>` is supposed to be on one page

#### Use `<table>` only for tabular data
 If a table has a heading row - use `<thead>` and nested `<th>` for the first raw

#### Don't use `<br>`
 `<br>`is supposed to be appropriate only where all of the following conditions are applied:
 1. Newlines are semantically meaningful
 2. Indentation is not semantically meaningful (otherwise, you should use a `<pre>`)
 3. There exists no other semantically appropriate tag, like a paragraph or header tag

## Tags
#### Start new `.html` file with `<!DOCTYPE html>`
 Don't do this if this file is for extending by template engine

#### Don't put any symbols before `<!DOCTYPE html>`
 Don't even put spaces and line breaks there

#### Tag `<meta charset="utf-8">` should be inside the `<head>`
 It can save `<title>` from incorrect encoding

#### Each page should contain meta tags and favicon
 Define tags title, keywords, and description in the `<head>`

#### Define viewport meta tag for each page
 Usually `<meta name="viewport" content="initial-scale=1.0, width=device-width">`default is enough

#### Avoid self-closing for tags that might have children
 Good: `<img />` or `<input />`.  
 Bad: `<div />` and `<span />`

#### Wrap  all attributes with double quotes
 Don't do like this:
 ```
<img width=200 />
<div class=block></div>
<a href='/some/url'></a>
```

#### Don't use `id` unless they are functionally needed
 Always try to guarantee that id is unique (for example get it only from database unique field). Use it only when you need:
 * In-page navigation (example is Wikipedia web-site)
 * Bind `<label>` and `<input>` if they placed in different DOM branches. However, always prefer to put `<input>` inside `<label>`, here `id` is not required

#### All tags should have classes
Avoid simple unnamed `<div></div>` and `<span></span>`

#### Don't use inline styles and event handlers
 There should not be something like this: `<div onclick="func()">`. Of course except of projects with frameworks that make you to do such things (like Angular or React)

#### All images should have `alt` attribute
 Avoid simple `<img />` tags because sometimes links to the images can be broken. Nevertheless web-site should be still functional

#### Try to wrap all interactive elements with `<form>` tag
 This will allow submiting by hitting Enter key and will semantically bind all elements 
 
#### Never use nested `<form>`
 You can have several forms on a page but they should not be nested.

#### Use various types of inputs where it is possible
 Use email, number, color, etc, old browsers will just use them as simple text

#### Don't create links with blank addresses `<a href="#">`
 Use simple `<span>`. And all links should be able to open new tabs with third mouse click

#### Use `mailto`, `tel` and `skype` prefixes for contact links
 Examples
```
<a href="tel: +74951234567">+7 (495) 123-45-67</a>
<a href="mailto: example@mail.ru">example@mail.ru</a>
<a href="skype: someskype?call">someskype</a>
```

#### Use tag `<code>`
 Sometimes for educational or another purposes we can display code samples (we often do it in this document). It is good practice to wrap all code snippets in  `<code>` tag and use only monospaced fonts.

## Assets files
#### All files should have unique names in context of project and don't contain non-latin symbols
 If there are no special conventions, all names should be also "lower-case-hyphenated"

#### Project should always contain favicon
 If you can't find it - spend some time to ask manager or designer for it

#### All images should be optimized
 Use http://www.jpegmini.com or https://tinypng.com for example, but prefer CLI-clients

#### All photos should have `.jpeg` extension
 Images without transparency should have `.jpeg`

