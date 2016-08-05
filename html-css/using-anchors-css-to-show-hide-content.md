---
headline: 'Using anchors and :target to show/hide content'
date: 2016-07-17
category: html-css
tags:
  - css
---

A simple CSS way to show and hide page content.

- `html`

```html
<a href="#a">a</a>
<a href="#b">b</a>
<a href="#c">c</a>

<div id="a" class="page">this is a id</div>
<div id="b" class="page">this is b id</div>
<div id="c" class="page">this is c id</div>
```

- `css`

```css
#a, #b, #c {
    display:none;
}
#a:target {
    display:block;
}
#b:target {
    display:block;
}
#c:target {
    display:block;
}
```

---
- [source](https://stackoverflow.com/questions/18849520/css-show-hide-content-with-anchor-name#18849682)