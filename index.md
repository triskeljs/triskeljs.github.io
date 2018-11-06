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
### Triskel Structured List (`TSList`)

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

- [parser](https://github.com/triskeljs/parser#readme)
  Converts String HTML to a [TSList](#triskel-structured-list-tslist)

- [stringify](https://github.com/triskeljs/stringify#readme)
  Converts back a [TSList](#triskel-structured-list-tslist) to a HTML String
  
- [tinyhtml](https://github.com/triskeljs/tinyhtml#readme)
  Based on previous libraries, converts HTML String into a TSList and the resulting list back to a HTML String.
  Using Options for remove comments, spaces, etc resulting a minified HTML.

- [render](https://github.com/triskeljs/render#readme)
  Renders recursivelly a TSList into a DOM node. Render library offers two time processing callbacks:
    - `withNode` *Function*, this callbacks allows process every single node rendered and set when to, replace by a comment or attach a initNode callback
    - `initNode` *Function*, this callback is executed only for the nodes determined by `withNode` for initialize the node before all nodes are rendered

- [con-text](https://github.com/triskeljs/con-text#readme)
  Provides a context for processing text in rendering time.
  Context allows to define filters for evaluating text expressions ` person.first_name | toUpperCase ` (` expression | filterFn `) and for interpolating texts with expressions `Hi {{ person.first_name }}! How are you?`

- [app](https://github.com/triskeljs/app#readme)
  On top of render and con-text, `app` offers a service for rendering data into DOM using `con-text` for formatting Text Nodes.
  `app` allows to define:
    - `components`: helper for initialize DOM Nodes based on Tag Names
    - `directives`: helper for initialize DOM Nodes based on attributes (allows RegExp format)
   `app` also interpolates automatically Text Nodes
   
- [template](https://github.com/triskeljs/template#readme)
  Based on `con-text` and using decission tokens renders a String template into a resulting String (like [EJS](https://ejs.co/))
  
*[HTML]: HyperText Markup Language
