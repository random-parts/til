---
headline: 'Auto generate category index pages w/ submodules'
date: 2016-07-17
category: jekyll
tags:
  - github-pages
  - liquid
---

My goal for the `random.parts` project was to use GitHub Pages for hosting and to only use CSS & liquid - no javascript. I also wanted GitHub to render the `_site` folder, and not be tied to my local set-up. That meant no plugins, but I also really did not want to keep track of any new categories in the [TILs] or future sections. I first attempted to use a [CSS solution][generate-category-pages-using-css-for-posts], but I didnt like the possibility of large file sizes later on.

Permalinks generate the pages needed, based on the `_config`. I just wanted it to generate two separate sets of `/index.html`. That's where I wondered if I could duplicate the collections and set different permalinks. [Git Submodules] make this easy to do. Even if it is a little ugly, it satisfies my requirements of updating efficiency/portability while using Github Pages to render the `_site`.

---

- [GitHub Pages] : Does not allow Jekyll plugins, making it more difficult to have both category indexes and article pages

- [Git Submodules] : Can be used as collections, and allows the content to be separate from the site code.

- [Jekyll Permalinks] : Structures the generated content of the published site.

Use permalinks to generate the `category/index.html` pages &  make `category/title-slug/` pretty urls for the posts by using two submodules of the same content repository. If you dont want to mess with submodules or care about pretty urls/file size, then you could try [anchors, CSS and includes][generate-category-pages-using-css-for-posts] for a similar effect.


- [Add two submodules][using-submodules-in-github-pages] from the same content repo to the site with different names.

```sh
# add submodules from a Public repo
$ git submodule add https://github.com/username/repo-name.git _submod_cat
$ git submodule add https://github.com/username/repo-name.git _submod_slug

# track submodules
$ git add .
```

{% raw %}
- Update `_config.yml` with the collections and default values

```yaml
collections:
  submod_cat:
    output: true
  submod_slug:
    output: true

defaults:
  -
    scope:
      type: submod_cat
    values:
      permalink: /blog/:categories/ # Auto generates all /blog/[CATEGORY]/index.html
      layout: submod_category
  -
    scope:
      type: submod_article
    values:
      permalink: /blog/:categories/:slug/ # Auto generates all /blog/[CATEGORY]/[TITLE-SLUG]/index.html
      layout: submod_article
```

- Make `_layout/submod_category.html`. The layout page that will be use for each `[category]/index.html`

```html
{% assign collection = site[page.collection] | where: "category", page.category | sort: "title" %}

<h1>{{ page.category }}</h1>
<nav>
  <ul>
  {% for article in collection %}
    {% if article.title %}
      <li><a href="{{ page.url | prepend: site.baseurl }}{{ article.slug }}">{{ article.title }}</a></li>
    {% endif %}
  {% endfor %}
  </ul>
</nav>
```

- Make `_layout/submod_article.html`. The layout for the collection articles

```html
<h1>{{ page.title }}</h1>
<div>
  {{ content }}
</div>
```

- Add articles with a `category` in the [YAML Front Matter][yml-front-matter] into the submodule's repo [`*`]

```yaml
---
title: Hello World!
category: Jekyll
---
```

{% endraw %}

- When content is [added to the submodule repository][using-submodules-in-github-pages], update the GitHub Pages submodule links with the newest version

```sh
# from the local github pages site
$ git submodule update --remote --merge

# publish to github pages
$ git commit -am "updated submodules" && git push
```

[`*`]_Note:_ If articles are without a Front Matter `category`, then a new directory will be built with the collection name(s), and the files will be duplicated into them.

[TILs]: https://github.com/random-parts/til
[GitHub Pages]: https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
[Git Submodules]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[Jekyll Permalinks]: https://jekyllrb.com/docs/permalinks/
[generate-category-pages-using-css-for-posts]: generate-category-pages-using-css-for-posts.md
[using-submodules-in-github-pages]: /github/using-submodules-in-github-pages.md
[yml-front-matter]: https://jekyllrb.com/docs/frontmatter/

{% include link-library.md collection="til" %}