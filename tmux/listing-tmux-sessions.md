---
headline: 'Listing tmux sessions'
date: 2016-10-09
category: tmux
tags:
  - cli
---

This is really useful after discovering `tmux` and you have no idea what `tmux` session you were in [if any]. It is even more useful when vim's `:` command line prompt has been remapped to the `spacebar` and instead of `:w` writing the file, the `⌘-w` close terminal window command is hit instead.

- List tmux sessions 

```sh
$ tmux ls
#=> 0: 2 windows (created ...
#=> ruby: 4 windows (created ...
```

- Open the session you want

```sh
# a | at | attach + -t [target-session] + the session number/name

$ tmux a -t 0
#=> emotional happiness
```

---

- [source](https://gist.github.com/MohamedAlaa/2961058)