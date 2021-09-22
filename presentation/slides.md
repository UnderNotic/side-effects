---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Tree shaking using webpack

- **Dead code elimation** - decrease size of your spa app
- **Side effects** - specify that module doesn't contain side effects to further optimize tree shaking
- **Traps when using side effect** - how can I know if module if free from side effects

<!--
How to decrease chuck size???
Tree shaking
Code splitting
Minifying

How does tree shaking works
Maybe sth about source-map-analyzers

Example:
* how sideEffects affects bundle size (tree shaking lodash)
* how sideEffects can affect logic of your app
* types of side effects:
* mutating global objects (window)
* event handlers
* pollyfils (changing behaviour of existing api or adding new global api)
-->