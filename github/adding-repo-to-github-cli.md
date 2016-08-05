---
headline: 'Adding new repositories to Github from CLI'
date: 2016-07-17
category: github
tags:
  - git
  - github-pages
---

```sh
# Replace USER with your username and REPO-NAME with the name of your project
$ curl -u 'USER' https://api.github.com/user/repos -d '{"name":"REPO-NAME","description":"Created from CLI"}'

$ git remote add origin git@github.com:USER/REPO-NAME.git

$ git push origin master
```

- replace `USER/REPO-NAME` with proper github account info

---
- [source](http://stackoverflow.com/a/7563830)