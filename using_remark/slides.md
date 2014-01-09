title: remark
description: Introduce remark.
name: inverse
layout: true
class: center, middle, inverse
---
#remark
[ri-mahrk]
---
## What is it and why should I be using it?
---
layout: false
.left-column[
  ## What is it?
]
.right-column[
  A simple, in-browser, Markdown-driven slideshow tool targeted at people who know their way around HTML and CSS, featuring:

- Markdown formatting, with smart extensions

- Automatic syntax highlighting, with optional language hinting

- Slide scaling, thus similar appearance on all devices / resolutions .red[*]

- Touch support for smart phones and pads, i.e. swipe to navigate slides

.footnote[.red[*] At least browsers are trying their best]
]
---
.left-column[
  ## What is it?
  ## Why use it?
]
.right-column[
If your ideal slideshow creation workflow contains any of the following steps:

- Just write what's on your mind

- Do some basic styling

- Easily collaborate with others

- Share with and show to everyone

Then remark might be perfect for your next.red[*] slideshow!

.footnote[.red[*] You probably want to convert existing slideshows as well]
]
---
.left-column[
  ## What is it?
  ## Why use it?
]
.right-column[
As the slideshow is expressed using Markdown, you may:

- Focus on the content, expressing yourself in next to plain text not worrying what flashy graphics and disturbing effects to put where

As the slideshow is actually an HTML document, you may:

- Display it in any decent browser

- Style it using regular CSS, just like any other HTML content

- Use it offline!

As the slideshow is contained in a plain file, you may:

- Store it wherever you like; on your computer, hosted from your Dropbox, hosted on Github Pages alongside the stuff you're presenting...

- Easily collaborate with others, keeping track of changes using your favourite SCM tool, like Git or Mercurial
]
---
template: inverse

## How does it work, then?
---
name: how

.left-column[
  ## How does it work?
### - Markdown
]
.right-column[
A Markdown-formatted chunk of text is transformed into individual slides by JavaScript running in the browser:

    # Slide 1
    This is slide 1

    ---

    # Slide 2
    This is slide 2

.slides[
  .first[
  ### Slide 1
  This is slide 1
  ]
  .second[
  ### Slide 2
  This is slide 2
  ]
]

Regular Markdown rules apply with only a single exception:

  - A line containing three dashes constitutes a new slide
  (not a horizontal rule, `&lt;hr /&gt;`)

Have a look at the [Markdown website](http://daringfireball.net/projects/markdown/) if you're not familiar with Markdown formatting.
]
---
.left-column[
  ## How does it work?
  ### - Markdown
  ### - Inside HTML
]
.right-column[
A simple HTML document is needed for hosting the styles, Markdown and the generated slides themselves:

    <!DOCTYPE html>
    <html>
      <head>
        <script src="remark.js" type="text/javascript"></script>
        <style type="text/css">
          /* Slideshow styles */
        </style>
      </head>
      <body>
        <textarea id="source">
          <!-- Slideshow Markdown -->
        &lt;/textarea&gt;
        <div id="slideshow"><div>
      </body>
    </html>

You may download [`.no-highlight remark.js`](http://gnab.github.com/remark/downloads/remark-0.4.6.min.js) to have your slideshow not depend on any online resources, or reference the latest version online directly.
]
---
template: inverse

## Of course, Markdown can only go so far.
---
.left-column[
  ## Markdown extensions
]
.right-column[
To help out with slide layout and formatting, a few Markdown extensions have been included:

- Slide properties, for naming, styling and templating slides

- Content classes, for styling specific content

- Syntax highlighting, with language hinting
]

---
.left-column[
  ## Markdown extensions
  ### - Slide properties
]
.right-column[
Initial lines containing key-value pairs are extracted as slide properties:

    .remark
    name: agenda
    class: middle, center

    # Agenda

    The name of this slide is {{ name }}.

Slide properties serve multiple purposes:

* Naming and styling slides using properties `name` and `class`

* Using slides as templates using properties `template` and `layout`

* Expansion of `{{ property }}` expressions to property values
]
---
.left-column[
  ## Markdown extensions
  ### - Slide properties
  ### - Content classes
]
.right-column[
Any occurences of one or more dotted CSS class names followed by square brackets are replaced with the contents of the brackets with the specified classes applied:

    .remark
    \.footnote[.red.bold[*] Important footnote]

Resulting HTML extract:

    <span class="footnote">
      <span class="red bold">*</span> Important footnote
    </span>
]
---
.left-column[
  ## Markdown extensions
  ### - Slide properties
  ### - Content classes
  ### - Syntax Highlighting
]
.right-column[
Code blocks are automatically syntax highlighted, based on the number of recognized keywords from a set of [supported languages](https://github.com/gnab/remark/wiki/Configuration-Options#wiki-highlighting).

Both indented code blocks and [GFM](http://github.github.com/github-flavored-markdown/) fenced code blocks are supported, optionally overriding the automatically detected language:

.pull-left[

    .no-highlight
    Code:

        .ruby
        def add(a, b)
          a + b
        end
        &nbsp;
]
.pull-right[

    .no-highlight
    Code:

    ```ruby
    def add(a, b)
      a + b
    end
    ```
]

Inline code is not automatically highlighted, and must be supplied a language to be highlighted:

    .remark
    Inline code: `.ruby a = 5`

To disable syntax highlighting, use the class `.no-highlight no-highlight`.
]
---
.left-column[
  ## Markdown extensions
  ### - Slide properties
  ### - Content classes
  ### - Syntax Highlighting
]
.right-column[
A number of highlighting [styles](https://github.com/gnab/remark/wiki/Configuration-Options#wiki-highlighting) are available, including several well-known themes from different editors and IDEs.

You may specify a style other than the `default` style using the configuration option `highlightStyle`, like this:

    <script src="remark.js" language="text/javascript">
      { "highlightStyle": "sunburst" }
    </script>

If you're using some custom style, you might want to prevent any of the bundled styles from being included. This can be done by specifying `.javascript null` as the style:

    .javascript
    { "highlightStyle": null }
]
---
.left-column[
  ## Slide properties
  ### - Name
]
.right-column[
The `name` property accepts a name used to identify the current slide:

    .remark
    name: agenda

    # Agenda

A slide name may be used to:

* Link a slide directly using URL fragment, i.e. `slideshow.html#agenda`

* Navigate to a slide using the [API](https://github.com/gnab/remark/wiki/API), i.e. `remark.gotoSlide('agenda')`

* Identify slide DOM element, either for scripting or styling purposes:

      <div id="slideshow">
        <div class="slide">
          <div id="slide-agenda" class="content">
            <h1>Agenda</h1>

* Reference slide when used as [template](#template) for some other slide
]
---
.left-column[
  ## Slide properties
  ### - Name
  ### - Class
]
.right-column[
The `class` property accepts a comma-separated list of class names, which are applied to the current slide:

    .remark
    class: center, middle

    # Slide with content centered in both dimensions

Resulting HTML extract:

    <div id="slideshow">
      <div class="slide">
        <div class="content center middle">
          <h1>Slide with content centered in both dimensions</h1>

The `center` and `middle` classes are included along with a few other common case classes.
]
---
name: template
.left-column[
  ## Slide properties
  ### - Name
  ### - Class
  ### - Template
]
.right-column[
The `template` property names another slide to be used as a template for the current slide:

    .remark
    name: other-slide

    Some content.

    ---
    template: other-slide

    Content appended to other-slide's content.


The final content of the current slide will then be this:

    .remark
    Some content.

    Content appended to other-slide's content.

Both template slide content and properties are prepended to the current slide, with the following exceptions:

* `name` and `layout` properties are not inherited
* `class` properties are merged, preserving class order
]
---
name: template
.left-column[
  ## Slide properties
  ### - Name
  ### - Class
  ### - Template
]
.right-column[
The `template` property may be used to (apparantly) add content to a slide incrementally, like bullet lists appearing a bullet at a time.

Using only two dashes (`--`) to separate slides implicitly uses the preceding slide as a template:

    .remark
    # Agenda

    --
    1. Introduction

    --
    2. Markdown formatting

Template slides may also contain a special `\{{content}}` expression to explicitly position the content of derived slides, instead of having it implicitly appended.
]
---
.left-column[
  ## Slide properties
  ### - Name
  ### - Class
  ### - Template
  ### - Layout
]
.right-column[
The `layout` property either makes the current slide a layout slide, which is omitted from the slideshow and serves as the default template used for all subsequent slides:

    .remark
    layout: true

    # Section

    ---

    ## Sub section 1

    ---

    ## Sub section 2

Or, when set to `false`, reverts to using no default template.

Multiple layout slides may be defined throughout the slideshow to define a common template for a series of slides.
]
---
template: inverse

## It's time to get started!
---
.left-column[
  ## Getting started
]
.right-column[
Getting up and running is done in only a few steps:

1. Visit the [project site](http://github.com/gnab/remark)

2. Follow the steps in the Usage section


This slideshow is of course created using remark, and serves as a live reference of use.
]
---
name: last-page
template: inverse

## That's all folks (for now)!

Slideshow created using [remark](http://github.com/gnab/remark).
