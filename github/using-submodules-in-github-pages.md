---
headline: 'Using submodules in GitHub Pages'
date: 2016-07-17
category: github
tags:
  - git
  - github-pages
  - jekyll
---

Use the same collection of files across different sites and separate content from code with [git submodules]. Submodules can be used as a [Jekyll Collection].

```sh
~/superproject-blog  -> (username.github.io)
    /_posts          -> (submodule - github.com/username/repo-posts)
    /_mycollection   -> (submodule - github.com/username/repo-collections)
    /_includes
    /_layouts
    /index.html
    /.etc
  
```

### Adding submodules
- Add `username/repo-posts.git` & `username/repo-collections.git` as submodules into `superproject-blog`

```sh
$ git submodule add https://github.com/username/repo-posts.git _posts
$ git submodule add https://github.com/username/repo-collections.git _mycollection

# track submodules
$ git add .
```

- Make changes from `~/superproject-blog/_posts` or `~/superproject-blog/_mycolletion`. 
- Once ready, commit & push changes to the remote submodule repo. 
- Do not forget to push the changes, or once `superproject-blog` is published it will be pointing to a local hash that is not there.[`*`]

```sh
# move into the new submodule directory to make changes
$ cd _posts

# add edit change files

# update remote w/ changes
$ git add .
$ git commit -m "save message" && git push
```

- Next, move into the `superproject-blog` and update submodules hash:

```sh
#Change to superproject-blog directory
$ cd ~/superproject-blog

#Check submodule status - a "+" before the hash shows version checked out in the submodule is different from the one in the superproject-blog 
$ git submodule status

#Update to current hash
$ git commit -am "updated submodules"

#Check submodule status - a [space] before the hash shows the versions match
$ git submodule status
```

- [`*`]Once it all looks good, publish the site using `--recurse-submodules=`

```sh
# ~/superproject-blog
# this will check that the local submodule changes were pushed to their remote repos
$ git push --recurse-submodules=check

# use the on-demand to have git try to push the submodules to their remote repos if missing
$ git push --recurse-submodules=on-demand
```

---

### Submodules repositories outside of the superproject

If more than one person contributes to the submodule, or you just want to make changes seperate from the superproject directory, use `$ git submodule update` from `superproject-blog` to pull in the new changes.

```sh
./local/git_projects/superproject-blog -> (username.github.io)
./local/git_projects/blogposts         -> (username/repo-posts.git)
./local/git_projects/blogmycollection  -> (username/repo-collections.git)

./local/git_projects/superproject-blog -> (username.github.io)
                      _posts           -> (submodule - username/repo-posts.git)
                      _mycollection    -> (submodule - username/repo-collections.git)

# From superproject-blog - check submodule status 
 ~/superproject-blog $ git submodule status
# & if behind, pull in new changes
 ~/superproject-blog $ git submodule update --remote --merge

# Publish
$ git commit -am "submodule updated" && git push
```

---
- [GitHub Pages Help](https://help.github.com/articles/using-submodules-with-pages/)

[git submodules]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[Jekyll Collection]: https://jekyllrb.com/docs/collections/