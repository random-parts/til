---
headline: 'Alternate element background colors'
date: 2016-07-24
category: html-css
tags:
  - css
---

- Alternate the `background` of an element or class with `:nth-of-type(odd)`

```css
/* .css */

.row:nth-of-type(odd) {
    background: #ccc;
  }
```

- Use `:hover` to change the `background` (& other styles) when the cursor is positioned over the element

```css
/* .css */

label:hover {
  background: #ccc;
}
```

---
- [source](http://stackoverflow.com/a/15004661)
- [hover source](http://stackoverflow.com/a/3359409)