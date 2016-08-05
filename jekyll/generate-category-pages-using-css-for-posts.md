---
headline: 'Auto generate category pages; use CSS for posts'
date: 2016-07-17
category: jekyll
tags:
  - github-pages
  - liquid
---

- [GitHub Pages][github-pages]: Does not allow Jekyll plugins, making it more difficult to have both Category indexes and Post pages.

Use [Jekyll Permalinks][jekyll-permalinks] to auto generate `category/index.html` pages, while using anchors and css to create the illusion of single page post once the article link is clicked on. If there are a large amount/size of post in a category, it could create very large file sizes. Also, not everyone likes `#` in their urls, if you want pretty urls, [auto generating with submodules][generate-category-pages-with-submodules] may work out better.

- This example only works with post in a single category.

- Set up `_config.yml`
{% raw %}

```yaml
defaults:
  -
    scope:
      type: posts
    values:
      permalink: /blog/:categories/ # Auto generates all /blog/[CATEGORY]/index.html
      layout: category 

```

- In `_layout/category.html`, get the articles for the current `page.category` and `include` its pseudo-layout. It will be hiden within `div id=* class="collection-single"` until it is `:target`ed.

```liquid
<!-- Add category articles | Show <div id> on :target -->

{% assign collection = site[collection] | where: "category", page.category | sort: "title" %}

  {% for article in collection %}
    {% if article.title %}
    <div id="{{ article.slug }}" class="collection-single">
      {% include collection-single.html collection=page.collection title=article.title %}
    </div>
    {% endif %}
  {% endfor %}
```

- Add the category `<nav>` element, loop through collection of articles, and display linked title. It will hide on `:target`.

```liquid
<!-- Add article category links | Hide nav on :target -->

  <nav>
    <h1>{{ page.category }}</h1>
    <ul>
    {% for article in collection %}
      {% if article.title %}
       <li><a href="{{ page.url | prepend: site.baseurl }}#{{ article.slug }}">{{ article.title }}</a></li>
      {% endif %}
    {% endfor %}
    </ul>
  </nav>
```

- Make an include `_include/collection-single.html` to use as a pseudo-layout for post.

```html
<!-- use the title to find the article in the collection -->

{% assign article = site[include.collection] | where: "title", include.title %}
<h1>{{ article.title }}</h1>
<div>
  {{ article.content }}
</div>
```

{% endraw %}
- Add the SCSS/CSS. This controls which is the hidden or displayed content. 

```scss
.collection-single {
    display: none;
    margin: 20px 0;
    &:target {
        display: block;
        ~ nav {
            display: none;
        }
    }
}
```

[github-pages]: https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
[jekyll-permalinks]: https://jekyllrb.com/docs/permalinks/
[generate-category-pages-with-submodules]: generate-category-pages-with-submodules.md

{% include link-library.md collection="til" %}