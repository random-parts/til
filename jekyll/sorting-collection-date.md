---
headline: 'Sorting collection items by date'
date: 2016-07-24
category: jekyll
tags:
  - github-pages
  - liquid
---

Filter `sort:"date"` wants a string and does not like `date: YYYY-MM-DD` front matter in collections. It's a bit misleading since other front matter variables dont require `" "` for strings. Turning `date` into a string should work, but I dont want to go through and change all my `date` FM.

- If using US date format `YYYY-MM-DD`, the collection articles are being date sorted from oldest to newest. Use `reverse|reversed` get the newest first. To iterate a collection with a `limit`, use the `reverse` filter with an `assign` tag, otherwise, use `reversed` when iterating without a limit.

{% raw %}

```liquid
---
date: YYYY-MM-DD <!-- not a string -->
date: "YYYY-MM-DD" <!-- is a string -->
---

<!-- if iterating with a limit, use the assign tag and add filter reverse -->
{% assign collection = site[collection] | reverse %}

{% for item in collection limit: 10 %}
  {{ item.date }}
{% endfor %}

<!-- if iterating w/o limit, use reversed -->
{% for item in site[collection] reversed %}
  {{ item.date }}
{% endfor %}
```

{% endraw %}

---
- [source](http://stackoverflow.com/a/30946672)