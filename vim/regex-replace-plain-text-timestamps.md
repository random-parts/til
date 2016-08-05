---
headline: 'Regex: Replace plain text timestamps'
date: 2016-07-17
category: vim
tags:
  - regex
  - search
  - replace
---

Wanted a way to add links to a text file of youtube timestamps for future reference. I started with the idea of making a vim script to add extra functionality. But really I just wanted something quick & dirty to get it done and move on. Using Search/Replace regex worked and did what it needed to do. Using Markdown links for their versatility.

```markdown
Before
======
- 4:01 Configuration XML
  - 9:21 Reset the Lucee Admin Password
  - 11:08 Compiling into RAM
  - 14:06 Lucee Constants
  - 14:23 Copy the XML file to maintain settings
  - 15:01 Using the DEPLOY folder
...etc

After
=======
- [4:01](https://youtu.be/C4MGHlOKzLI?t=4m01s) Configuration XML
  - [9:21](https://youtu.be/C4MGHlOKzLI?t=9m21s) Reset the Lucee Admin Password
  - [11:08](https://youtu.be/C4MGHlOKzLI?t=11m08s) Compiling into RAM
  - [14:06](https://youtu.be/C4MGHlOKzLI?t=14m06s) Lucee Constants
  - [14:23](https://youtu.be/C4MGHlOKzLI?t=14m23s) Copy the XML file to maintain settings
  - [15:01](https://youtu.be/C4MGHlOKzLI?t=15m01s) Using the DEPLOY folder
...etc
```

---
- Replace `VIDEO_ID` with the video id `youtube.com/watch?v={VIDEO_ID}`

```viml
" Videos 59:59 or less
:%s/\s\([0-9]\{1,2}\):\([0-9]\{1,2}\)\s/\ \[\1\:\2\]\(https:\/\/youtu.be\/VIDEO_ID?t=\1m\2s\)\ /gc

" Videos 1:00:00+
:%s/\s\([0-9]\{1,2}\):\(\d\d\):\([0-9]\{1,2}\)\s/\ \[\1\:\2\:\3\]\(https:\/\/youtu.be\/VIDEO_ID?t=\1h\2m\3s\)\ /gc
```

---

#### what. is. that?

```yaml
# Search `s` the entire document `%`

:%s/

# For a `space` before matching 1-2 `{1,2}` digits in range `[0-9]`, a `:` 
# and another set of digits `\([0-9]\{1,2}\)` with a `space` after

\s\([0-9]\{1,2}\):\([0-9]\{1,2}\)\s

# Start replace with a `space` & `[` then the first reference `\1`
# or results of search within the first set of `()` a `:` then the second reference `\2`

/\ \[\1\:\2\]

# Add opening `(` then the link, escaping `/` `https:\/\/youtu.be\/VIDEO_ID?t=` 
# and the contents of group `\1`, `m` for minute, then group `\2`, `s` for seconds,
# and a closing `)` & `space`

\(https:\/\/youtu.be\/VIDEO_ID?t=\1m\2s\)\

# Add flags `g` global, replace every occurrence on line. `c` to confirm the change.

/gc
```