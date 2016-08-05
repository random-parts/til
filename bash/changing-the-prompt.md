---
headline: 'Changing the prompt'
date: 2016-03-10
category: bash
tags:
  - macOS
---

Customize the prompt, using [tput] for colors.

```sh
# place into `~/.bash_profile` or `~/.bashrc`

# set color vairables with tput
MAGENTA="\[$(tput setaf 5)\]"
RESET="\[$(tput sgr0)\]"

# primary prompt
export PS1="\u@\h: ${MAGENTA}\W${RESET} \$ "

# prompt will display
 user@hostname: ~ $  
```

 Variable | Desc
 ---- | ---- 
 `\d`   | Date, in "Weekday Month Date" format (e.g., "Tue May 26"). 
 `\h`   | Hostname, up to the first . (e.g. deckard) 
 `\H`   | Hostname. (e.g. deckard.SS64.com)
 `\j`   | Number of jobs currently managed by the shell. 
 `\l`   | Basename of the shell's terminal device name.
 `\s`   | Name of the shell, basename of $0 (portion following the final slash). 
 `\t`   | Time, in 24-hour HH:MM:SS format. 
 `\T`   | Time, in 12-hour HH:MM:SS format. 
 `\@`   | Time, in 12-hour am/pm format. 
 `\u`   | Username of the current user. 
 `\v`   | Version of Bash (e.g., 2.00) 
 `\V`   | Release of Bash, version + patchlevel (e.g., 2.00.0) 
 `\w`   | Current working directory. 
 `\W`   | Basename of $PWD. 
 `\!`   | History number of this command. 
 `\#`   | Command number of this command. 
 `\$`   | If not root, inserts a "$"; if root, you get a "#"  (root uid = 0) 
 `\nnn`  | The character whose ASCII code is the octal value nnn. 
 `\n`   | A newline. 
 `\r`   | A carriage return. 
 `\e`   | An escape character (typically a color code). 
 `\a`   | A bell character.
 `\\`   | A backslash. 
 `\[`   | Begin a sequence of non-printing characters. (like color escape sequences). This allows bash to calculate word wrapping correctly.
 `\]`   | End a sequence of non-printing characters.

---
- [source](http://ss64.com/bash/syntax-prompt.html)

[tput]: http://ss64.com/bash/tput.html