+++
title = "Mermaid in Markdown"
date = "2020-01-06"
disable_comments = false
categories = ["Static site generation"]
tags = ["Mermaid"]
draft = false
mermaid = true
+++

How to use Mermaid for flowcharts in blogs and with Hugo in Markdown documents.

<!--more-->

# Intro

[Mermaid](https://mermaid-js.github.io/mermaid/) is a Markdown language to describe flow charts so you can easily describe things like this:

{{<mermaid>}}
graph TD;
  A-->B;
  A-->C;
  B-->D;
  C-->D;
{{</mermaid>}}

It is surprisingly easy to add Mermaid to your Markdown document.
Either as HTML snippet or with a self made shortcut for the single site generator [Hugo](gohugo.io). 
I am sure its quite possible for other single site generators too.

# Setup in any Markdown doc
Just add this to your markdown doc. HTML snippets are allowed in Markdown.

```
<div class="mermaid">
graph LR;
  A-->B;
</div>
<script async src="https://unpkg.com/mermaid@8.2.3/dist/mermaid.min.js"></script>
```

After the `graph` statement the Mermaid code can be added.

# Setup a shortcut for Hugo

In Hugo add a file layouts/shortcuts/mermaid.html to your site base directory.
Add this snippet to the file,

```
<!-- MermaidJS support -->

<div class="mermaid">
  {{.Inner}}
</div>
{{ if ($.Page.Params.mermaid) }}
<!-- MermaidJS support -->
<script async src="https://unpkg.com/mermaid/dist/mermaid.min.js"></script>
{{ end }}
```

The if statement checks if the front-matter parameter mermaid is set, otherwise the script is not used. This way the script will only be loaded if a parameter in the document specifically states so.

To activate mermaid in a document add this to your front-matter:

`mermaid: true` or `mermaid = true`


Add the mermaid code between the shortcut start and end. Note the additional `/` for the end code.

`{ { < mermaid > } }`           (without the space)

```
graph TD;
  A-->B;
  A-->C;
  B-->D;
  C-->D;
```

`{ { < /mermaid > } }`           (without the space)


# Links:
- https://codewithhugo.com/mermaid-js-hugo-shortcode/
- https://peterlavalle.github.io/post/gohugo-mermaid/