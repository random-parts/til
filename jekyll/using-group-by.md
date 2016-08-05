---
headline: 'Using group_by'
date: 2016-03-28
category: jekyll
tags:
  - github-pages
  - liquid
---

Very useful for working with categories in a collection.

- The `group_by` filter creates a new array grouped by a given property, for example, `category` 

```liquid
[
  {"name"=>"jekyll", "items"=>[#,#,#]},
  {"name"=>"liquid", "items"=>[#,#,#]},
  {"name"=>"github", "items"=>[#,#,#]}
]
```

- Loop through the array and for each category `name` loop through the `items` to get property values associated with that category.
{% raw %}

```liquid
{% assign collection = site[collection] | group_by: "category" %}

{% for group in collection %}
  <h1>{{ group.name }}</h1>
  <ul>
    {% for item in group.items %}
    <li>{{ item.title }}</li>
    {% endfor %}
  </ul>
{% endfor %}
```

{% endraw %}
---
- [source](https://stackoverflow.com/questions/26176317/cannot-group-by-custom-jekyll-collection)
- [Jekyll Docs](https://jekyllrb.com/docs/templates/)