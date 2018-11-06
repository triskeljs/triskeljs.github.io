# Triskel JS

Triskel aims to provide a suite of tools to process triskel HTML structure.

## Triskel HTML structure

There are several options to incorpotare HTML to a JS bundle code.
- Escaped HTML string
- Preprocessed functions that renders HTML, like EJS, Vue or React
- ~JSON~ JS Objects representing a HTML structure

Triskel JS is based on the last option.

> From a HTML like this:

``` html
<ul class="col-md-6">
  <li>foo</li>
  <li>bar</li>
</ul>
Lorem ipsum...
<br/>
```

> Is parsed into an Object with following structure:

``` js
[
  { $: 'ul', attrs: { 'class': 'col-md-6' }, _: [
    { $: 'li', _: 'foo' },
    { $: 'li', _: 'bar' },
  ] },
  'Lorem ipsum...',
  { $: 'br', self_closed: true },
]
```
### Triskel Nodes List

> Basically Triskel format is a multi-level list of strings or objects, where strings represents DOM Text Nodes and objects represents DOM Element Nodes.

``` js
[Object, String, Object, ...]
```

### Object structure

Every `Object` in list describes a single DOM Element Node using following properties:
  - `$`: HTML Tag (like 'body', 'div', 'span', 'blockquote', ...)
  - `attrs`: Plain Object with a dictionary of Node attributes
    - `{ 'class': 'col-md-6' }`
    - `<script async>` -> `{ $: 'script', attrs: { async: '' } }` (empty attribute)
  - _: Node children `<Array, String>`
    - `Array`: Recursive Nodes List `[Object, String, Object, ...]`
    - `String`: When a child is just a String, it represents a single Text Node child

## TriskelJS suite repos:

- [parser](https://github.com/triskeljs/parser)
  Converts String HTML to a Structured Triskel List

