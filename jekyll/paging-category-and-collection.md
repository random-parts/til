---
headline: 'Add next/prev category paging in collections'
date: 2016-07-24
category: jekyll
tags:
  - github-pages
  - liquid
---

{% raw %}

### Cycle through [category pages][generate-category-pages-with-submodules]

- Create an array of categories to cycle through. Since we only need the category name use `map: "name"` 

```liquid
<!-- template/layout page-->
{% assign paging = site[page.collection] | group_by: "category" | sort: "name" | map: "name" %} 
```

- Loop throuugh the categories. Once it finds the current `page.category` in the array, assign `next` to the current `forloop.index0  + 1` and `prev` to `forloop.index0 - 1` & `break` looping. If it is the first iteration, assign the offest `prev` to `array.size - 1`. It the last iteration, assign the offest `next` to `0`. Finally, get the element at the array index using `offset` and `limit`.

```liquid
<!-- template/layout page -->

{% for item in paging %}
  {% if item == page.category %}
    {% assign next = forloop.index0 | plus: 1 %}
    {% assign prev = forloop.index0 | minus: 1 %}
    
<!-- arrays start at 0; minus 1 from size -->
    {% if forloop.first %}
      {% assign prev = paging | size | minus: 1 %}
    {% endif %}

    {% if forloop.last %}
      {% assign next = 0 %}
    {% endif %}

    {% break %}
  {% endif %}
{% endfor %}

<!-- get the next/prev elements from the array -->
{% for item in paging limit: 1 offset: next %}
  {% assign next = item %}
{% endfor %}

{% for item in paging limit: 1 offset: prev %}
  {% assign prev = item %}
{% endfor %}
```

- Add html for `next|prev` links

```html
<!-- template/layout page-->
<section class="paging">
  <div class="left">
    <a href="{{ prev | prepend:site.baseurl }}">
      ‹ prev
    </a>
  </div>
  <div class="right">
    <a href="{{ next | prepend: site.baseurl }}">
      next ›
    </a>
  </div>
</section>
```

---

### Cycle through collection pages, grouped by category

- To loop through the articles of a collection, by category, [create a new array][creating-a-new-array] using the article urls. This creates an array of all collection entries grouped by `category`. Use the same `next|prev` looping from above to get the `next|prev` elements from the articles `paging` array.

```liquid
{% assign collections = site[page.collection] | group_by: "category" |  sort: "name", "first" %}

<!-- initialize paging array -->
{% assign paging = "" | split: "|" %}

{% for group in collections %}
  {% for item in group.items %}
    {% assign paging = paging | push: item.url %}
  {% endfor %}
{% endfor %}
```

{% endraw%}

[generate-category-pages-with-submodules]: generate-category-pages-with-submodules.md
[creating-a-new-array]: creating-a-new-array.md

{% include link-library.md collection="til" %}