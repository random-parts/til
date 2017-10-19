---
headline: 'Gist search cheatsheet'
date: 2016-02-20
category: github
tags:
  - cheatsheet
  - gist
---

#### Basic search

This search | Finds repositories with…
--- | ---
`cat stars:>100` | Find cat gists with greater than 100 stars.
`user:defunkt` | Get all gists from the user defunkt.
`cat anon:true` | Include anonymous gists in your search for cat-related gists.
`NOT cat` | Excludes all results containing cat.
`cat fork:only` | Search all forked gists for results containing cat.



#### Contents search

This search | Finds gists with…
--- | ---
`filename:.bashrc` | Find all gists with a ".bashrc" file.
`cat language:html` | Find all cat gists with HTML files.
`join extension:coffee` | Find all instances of join in gists with a coffee extension.
`system size:>1000` | Find all instances of system in gists containing a file larger than 1000kbs.

---
- [source](https://gist.github.com/search#search_cheatsheet_pane)
