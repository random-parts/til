---
headline: 'Changing file permissions [chmod]'
date: 2016-06-21
category: bash
tags:
  - permissions
---

### Reading the file information list

```sh
$ ls -l

# returns
 -rwxrwxrwx 1 owner group file.txt
```

- `-` shows this is a normal file a `d` here would incicate a directory
- `rwx` the next 3 characters show the `owner` permissions
- `rwx` the next 3 characters show the `group` permissions
- `rwx` the next 3 characters show the `all users` permissions
-  `1` number of hard links to file
- `owner group` the file owner, then the group level access
- `file.txt` the file the permission refer to

```sh
# using chmod symbolic mode
$ chmod a-x file.txt

# new permissions
-rw-rw-rw- 1 owner group file.txt
```

`$ chmod [who] [op] [perm] [filename]`

 `who` | desc | `op` | desc | `perm` | desc |
:---: | :---: | :---: | :---: | :---: | :---: |
`u` | User | `+` | add | `r` | Read
`g` | Group | `-` | remove | `w` | Write
`a` | All users | `=` | set exactly | `x` | Execute

---

### Using Binary References

**permission** | `r` | `w` | `x`
**value** | 4 | 2 | 1


sum of values | permission
--- | ---
`7` = 4+2+1 | `rwx` (read/write/execute)
`6` = 4+2 | `rw-` (read/write)
`5` = 4+1 | `r-x` (read/execute)
`4` = 4 | `r--` (read)
`3` = 2+1 | `-wx` (write/execute)
`2` = 2 | `-w-` (write)
`1` = 1 | `--x` (execute)
`0` | `---` (none)

Add the `values` for the `permission` that we want, then place the permission `sum of values` into one of the 3 positions `u``g``a` next to each other to get the 3 digit permission.

```sh
# chmod binary mode
$ chmod 764 file.txt

# new permissions
-rwxrw-r-- 1 owner group file.txt
```

`$ chmod 764`

- `7` = `rwx` in the `U`ser posistion
- `6` = `rw-` in the `G`roup position
- `4` = `r--` in the `A`ll position

---
- [source](http://ss64.com/bash/chmod.html)
- [source](http://www.linux.org/threads/file-permissions-chmod.4094/)