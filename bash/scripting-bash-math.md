---
headline: 'Scripting bash math'
date: 2016-09-07
category: bash
tags:
  - ImageMagick
---

While making an [ImageMagick] script I wanted to `+ 100` to `${w}` & `${h}` in `"${w}x${h}"`. Double parentheses makes this happen.

```sh
# if w=100, h=100
"$((w + 100))x$((h + 100))"           # 200x200

# test output in cli
$ w=100; h=100
$ echo "$((w + 100))x$((h + 100))"    # 200x200
```

- Other [Arithmetic Expansion]

```sh
# if w=100

$ echo w=$((w + 100)) # w=200
# or
$ echo $((w + 100))   # 200

# if w=0
$ ((w += 1))          # increment w
$ echo "w = $w"       # w = 1
```

---
- [source](https://stackoverflow.com/a/8385669)

[ImageMagick]:http://www.imagemagick.org
[Arithmetic Expansion]:http://tldp.org/LDP/abs/html/arithexp.html