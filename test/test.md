# Introduction

Cette application doit permettre la saisie de fichier au format MarkDown et d'en faire un rendu que ce soit en version desktop ou en version mobile.

# Titre 1
## Titre 2
### Titre 3
#### Titre 4
##### Titre 5
###### Titre 6

Un exemple de tableau

|   C1     |   C2    |   C3      |
|:---------|:-------:|----------:|
| label 1  | label 2 | value     |
| label 1  | label 2 | value     |
| label 1  |         | _value_   |
| label 1  | label 2 | **value** |

Inline-style: 
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Inline link : [link](http://post-it.zedesk.net)

- item 1
- item 2
  - item 2.1

    it's also easy to add a paragraphe in a item list

  - item 2.2
- item 3
  1. item 3.1
  2. item 3.2

code HTML de la page de test

```HTML
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <title>Test Marked</title>
    <link href="styles/test.css" rel="stylesheet" />
    <link rel="stylesheet" href="styles/highlight/magula.css" >
    <!-- <script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script> -->
    <script src="highlight.pack.js" type="text/javascript" charset="utf-8"></script>
    <script src="../node_modules/marked/lib/marked.js" type="application/javascript" ></script>
    <link rel="stylesheet" href="styles/markdown.css" type="text/css" charset="utf-8">
</head>
<body>
    <div class="MMDEdit">
        <textarea id="editor"></textarea>
    </div>
    <div id="MMD" class="markdown"></div>
</body>
</HTML>
```

code Javascript

```javascript
var render = document.querySelector("#MMD");
var editor = document.getElementById("editor");

editor.addEventListener("keypress", convert, false);
hljs.initHighlightingOnLoad();

marked.setOptions({
    gfm: true,
    highlight: function (code, lang) {
        return hljs.highlightAuto( code).value;
    },
    tables: true,
    breaks: false,
    pedantic: false,
    sanitize: false,
    smartLists: true,
    smartypants: false,
    langPrefix: 'lang-'
});

function convert(evt) {
    marked(editor.value,{}, function (err, content) {
      render.innerHTML = content;
    });
}
```
