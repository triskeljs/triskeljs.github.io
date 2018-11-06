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

Basically is a list of strings or objects, where strings represents DOM Text Nodes and objects represents DOM Element Nodes.



You can use the [editor on GitHub](https://github.com/triskeljs/triskeljs.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/triskeljs/triskeljs.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
