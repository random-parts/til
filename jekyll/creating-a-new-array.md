---
headline: 'Creating a new array'
date: 2016-07-17
category: jekyll
tags:
  - github-pages
  - liquid
---

{% raw %}

- Create an empty array in `_config.yml`

```yaml
# _config.yml

array: []
```

- `assign` an empty array, then `push` elements into it

```liquid
<!-- template/layout -->

{% assign myArray = site.array %}
{% assign myArray = myArray | push: "hello" %}

{{ myArray }}  --> ["hello"]

{% assign myArray = myArray | push: "world" %}

{{ myArray }}  --> ["hello","world"]
```

### Alternate way to create new arrays

```liquid
<!-- alternately, create a new arry with split filter w/o messing with _config.yml -->
{% assign myArray = "" | split: "|" %}
{% assign myArray = myArray | push: "hello" %}
```

### More array filters
- `pop` {{ myArray \| pop }} -> ["hello"]
- `shift` {{ myArray \| shift }} -> ["world"]
- `unshift` {{ myArray \| unshift: "Well" }} -> ["Well","hello","world"]

{% endraw %}

---
- [source](https://talk.jekyllrb.com/t/how-do-you-add-items-to-an-array-in-jekyll/324/2)
- [Jekyll Templates](https://jekyllrb.com/docs/templates/)