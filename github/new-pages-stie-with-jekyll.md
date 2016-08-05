---
headline: 'New User Pages site with Jekyll'
date: 2016-03-17
category: github
tags:
  - git
  - github-pages
  - jekyll
---

- Required [GitHub Account], [Git] & [Jekyll]

- Recommended [github-pages Gem]

### User Pages
Create a [new] empty repository named `username.github.io`, where _username_ is your github username.

```sh
# clone the new repository into the project folder
~ $ git clone https://github.com/username/username.github.io ~/path/to/project/folder

# create new Jekyll site scaffold in PATH
~ $ jekyll new ~/path/to/project/folder

# goto new Jekyll project
~ $ cd ~/path/to/project/folder

# add, commit & push site
$ git add --all
$ git commit -m "Init"
$ git push -u origin master
```

Visit the page at `https://username.github.io`, where _username_ is your github username.

[GitHub Account]: https://github.com/
[git]: https://git-scm.com/book/en/v1/Getting-Started-Installing-Git#Installing-on-Mac
[Jekyll]: https://jekyllrb.com/
[github-pages Gem]: https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/
[new]: https://github.com/new