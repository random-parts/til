---
headline: 'Using a link library to change reference links'
date: 2016-07-17
category: jekyll
tags:
  - github-pages
  - liquid
  - markdown
---

I had been using markdowns inline links when typing notes. However, it only allowed for the link between notes to work in the [github repo][til-repo] or to work between notes on [random.parts]. I wanted jekyll to change the linked notes url so they would work in both locations without extra editing. Thats where [reference style links] and a [link library][site-repo-link-library] `_includes` solved things. As a bonus, it makes it easier to change any broken links, as they are in one location and don't have to search for them inline.

- Make an `_include/link-library.md` file that will loop through the `include.collection` and use the article `item.slug` as the `[_text_]:` and then build the reference link with `item.url | prepend: site.baseurl | prepend: site.url`

{% raw %}

```liquid
<!-- _includes/link-library.md -->

{% assign collection = include.collection %}

{% for item in site[collection] %}
  [{{ item.slug }}]: {{ item.url | prepend: site.baseurl | prepend: site.url }}
{% endfor %}
```

- At the bottom of the markdown `.md` notes/file, add the referance style links and the `include` liquid tag

```md
<!-- note.md -->

[slug-of-collection-article]: /path/on/github/slug-of-collection-article.md

{% include link-library.md collection="COLLECTION-NAME" %}
```
{% endraw %}

Now the link will work if viewing on the repo they are located in and also on the gihub pages site.

---
- [source](http://stackoverflow.com/a/32757152)

[reference style links]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links
[random.parts]: https://random.parts
[site-repo-link-library]: https://github.com/random-parts/random-parts.github.io/blob/master/_includes/link-library.md
[til-repo]: https://github.com/random-parts/til/

{% include link-library.md collection="til" %}