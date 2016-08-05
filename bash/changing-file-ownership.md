---
headline: 'Changing file ownership [chown]'
date: 2016-06-21
category: bash
tags:
  - permissions
  - ownership
---

For those times when you forget you are in `$ sudo vim ` and create new project files.

```sh
# if wrong owner &/or group
-rw-r--r-- 1 owner group file.txt

# change owner and group, then display file list
$ chown user:staff file.txt
$ ls -l

# returns
-rw-r--r-- 1 user staff file.txt
```

#### Syntax
- `$ chown [Options] [NewOwner] [file|dir]`
- `$ chown [Options] [:Group] [file|dir]`
- `$ chown [Options] [NewOwner:Group] [file|dir]`

#### Options - flags
- `-R` recursive all files in dir
- `-v` verbose

---
- [source](http://ss64.com/bash/chown.html)