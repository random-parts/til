---
headline: 'The @ symbol in the information file list'
date: 2016-06-21
category: bash
tags:
  - macOS
---

Never really paid attention to the `@` before, then one day I got curious.

```sh
$ ls -al

-rw-r--r--@   1 user  staff  26628 Jun 21 18:09 .DS_Store
```

It indicates that the file has extended attributes.

- `$ ls -l@` to see them
- `$ xattr` to edit

---
[source](http://superuser.com/a/155459)