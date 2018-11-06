## Triskel JS

Triskel aims to provide a suite of tools to process triskel HTML format.

### Triskel HTML format

There are several options to incorpotare HTML to a JS bundle code.
- Escaped HTML string
- Preprocessed functions that renders HTML, like EJS, Vue or React
- ~JSON~ JS Objects representing a HTML structure

Triskel JS is based on the last option. So, an HTML like this:

``` html
<ul class="col-md-6">
  <li>foo</li>
  <li>bar</li>
</ul>
Lorem ipsum...
<br/>
```

Is parsed in an Object like that:

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

> Basically is a list of strings or objects, where strings represents DOM Text Nodes and objects represents DOM Element Nodes.

``` js
[Object, String, Object, ...]
```


