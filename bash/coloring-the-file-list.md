---
headline: 'Coloring the file list [ls]'
date: 2016-05-10
category: bash
tags:
  - macOS
---

- Add color to the file list by placing the following into `.bash_profile`

```sh
# ~/.bash_profile or .bashrc

# add color to ls
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
```

[ls environment variables]

```
Describes what color to use
for which attribute when colors are enabled with
CLICOLOR.	This string is a concatenation of pairs of the
format fb, where f is the foreground color and b is the
background color.

color designators are:
a black
b red
c green
d brown
e blue
f magenta
g cyan
h light grey
A bold black, usually shows up as dark grey
B bold red
C bold green
D bold brown, usually shows up as yellow
E bold blue
F bold magenta
G bold cyan
H bold light grey; looks like bright white
x default foreground or background

order of the attributes are:
1. directory
2. symbolic link
3. socket
4. pipe
5. executable
6. block special
7. character special
8. executable with setuid bit set
9. executable with setgid bit set
10. directory writable to others, with sticky bit
11. directory writable to others, without stickybit

The default is “exfxcxdxbxegedabagacad”
```

---
- [source](http://osxdaily.com/2012/02/21/add-color-to-the-terminal-in-mac-os-x/)
- [alt source](http://linux-sxs.org/housekeeping/lscolors.html)
- [alt global dircolors](http://unix.stackexchange.com/a/94306)
- [alt using dircolor](http://linux-sxs.org/housekeeping/dircolor.html)

[ls environment variables]: http://ss64.com/bash/lsenv.html