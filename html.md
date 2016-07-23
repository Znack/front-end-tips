# HTML

## Semantics

#### Divide elements by meaning
Sometimes there is easy way to divide block by their appearance because it requires less styles. But it is wrong way that will confuse colleagues and make the app less scalable

#### Don't insert block element inside inlines
Avoid such code: `<a><div></div></a>`

#### Check all text element with a large content
Use long names and long descriptions for all available text elements

#### Use tags `<h1>...<h6>` only for headings
And `<h1>` span should be only one per page

#### Use `<table>` only for tabular data
If table has headings - use `<thead>` span and nested `<th>` span for the first raw

#### Don't use `<br>`
`<br>`s seem to only be appropriate where all of the following conditions apply:
1. Newlines are semantically meaningful
2. Indentation is not semantically meaningful (otherwise you should use a `<pre>`)
3. There exists no other semantically appropriate tag, like a paragraph or header tag

## Tags
#### Start new .html file with `<!DOCTYPE html>`
Don't do this if this file is for extending by template engine

#### Don't put any symbols before `<!DOCTYPE html>`
Don't put even spaces and line breaks

#### Tag `<meta charset="utf-8">` should be first inside the `<head>`
It can save `<title>` from incorrect encoding

#### Each page should contain meta tags and favicon
Define tags title, keywords and description in the `<head>`

#### Define viewport meta tag for each page
Usually the default `<meta name="viewport" content="initial-scale=1.0, width=device-width">` will be enough

#### Avoid self closing for tags that can have children
This is correct `<img />` or `<input />`. This is not correct `<div />` and `<span />`

#### All tags should have classes
Avoid simple unnamed `<div></div>` and `<span></span>`

#### Don't use inline styles and event handlers
There should not be something like this: `<div onclick="func()">`

#### All images should have `alt` attribute
Avoid simple `<img />` tags because sometimes links can be broken and web-site should be still functional

#### Use new types of inputs where it is possible
Use email, number, color, etc, old browsers will just use them as simple text

#### Don't create links with blank addresses `<a href="#">`
Use simple `<span>`. And all links should be able to open new tabs with third mouse button

#### Use `mailto`, `tel` and `skype` prefixes for contacts links
Examples
```
<a href="tel: +74951234567">+7 (495) 123-45-67</a>
<a href="mailto: example@mail.ru">example@mail.ru</a>
<a href="skype: someskype?call">someskype</a>
```

#### Use tag `<code>`
Sometimes for educational or other purpose we can display code samples (here document we do it very often as you can see). It is good practice to wrap all code snippets in the `<code>` tag and use only mono-spaced fonts.

## Assets files
#### All files should have unique names in context of project and don't contain non-latin symbols
If there is no special conventions, all names should be also "lower-case-hyphenated"

#### Project should always contain favicon
If you can't find it - spend some time to ask manager or designer for it

#### All images should be optimized
Use http://www.jpegmini.com or https://tinypng.com for example, but prefer CLI-clients

#### All photos should have .jpeg extension
Images without transparency should be also .jpeg

