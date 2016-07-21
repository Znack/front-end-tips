# HTML

## Semantics

#### Divide elements by meaning
Sometimes there is easy way to divide block by their appearance because it requires less styles. But it is wrong way that will confuse colleagues and make the app less scalable

#### Don't insert block element inside inlines
Avoid such code: ```<a><div></div></a>```

#### Check all text element with a large content
Use long names and long descriptions for all available text elements

#### Use tags ```<h1>...<h6>``` only for headings
And ```<h1>``` span should be only one per page

#### Use ```<table>``` only for real tables
If table has headings - use ```<thead>``` span and nested ```<th>``` span for the first raw

#### Don't use ```<br>```
```<br>```s seem to only be appropriate where all of the following conditions apply:
1. Newlines are semantically meaningful
2. Indentation is not semantically meaningful (otherwise you should use a ```<pre>```)
3. There exists no other semantically appropriate tag, like a paragraph or header tag

## Tags
