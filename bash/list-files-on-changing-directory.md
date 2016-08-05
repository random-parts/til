---
headline: 'List files on changing directory [cd]'
date: 2016-05-10
category: bash
tags:
  - macOS
---

Tried making an alias for `$ cd`, but needed it to take arguments, which alias dont like. Creating a function to override the built-in `cd` works.

```sh
# paste into ~/.bash_profile or .bashrc
cd () { 
  builtin cd "$@";
  ls -al $2; 
  echo;
  (tput setaf 5);    
  PWD;              
  (tput sgr0);
  echo;
}

$ source ~/.bashrc
# run
$ cd [path] [ls extra options]
```

- change directory `builtin cd "$@"`
- list files `ls`, include `.` entries `-a` & list in long format `-l`
- parameter for extra flags `$2`
- print blank new line `echo;`
- set color magenta `(tput setaf 5)`
- print working directory `pwd` (in magenta)
- reset text color `(tput sgr0)`
- print blank new line `echo;`