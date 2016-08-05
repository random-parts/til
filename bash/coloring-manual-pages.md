---
headline: 'Coloring manual pages [man]'
date: 2016-06-11
category: bash
tags:
  - macOS
---

```sh
# place in `.bashrc` or `.bash_profile`
man() {
    env \
    LESS_TERMCAP_mb=$(printf "\e[1;31m") \
    LESS_TERMCAP_md=$(printf "\e[1;38;5;45m") \
    LESS_TERMCAP_me=$(printf "\e[0m") \
    LESS_TERMCAP_se=$(printf "\e[0m") \
    LESS_TERMCAP_so=$(printf "\e[0;38;5;164m") \
    LESS_TERMCAP_ue=$(printf "\e[0m") \
    LESS_TERMCAP_us=$(printf "\e[04;38;5;170m") \
    man "$@"
}
```

 part | desc
--- | ---
`LESS_TERMCAP_*` | [Capabilities Codes] to change
`=$(printf` | format and print data
`"\e[SRG;` | [SRG Parameters]
`38;5;#m` | [Xterm color escape sequence]

- `38` foreground color
- `48` background color
- `5;COLOR#m` for xterm
- `2:<r>;<g>;<b>m` for RGB

[Capabilities Codes]: http://linux.die.net/man/5/termcap
[SRG Parameters]: https://en.wikipedia.org/wiki/ANSI_escape_code#graphics
[Xterm color escape sequence]: https://en.wikipedia.org/wiki/ANSI_escape_code#Colors