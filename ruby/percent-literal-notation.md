---
headline: 'Percent %{} literal notation'
date: 2016-09-26
category: ruby
tags:
  - ruby
  - syntax
---

Browsing through ruby's `FileUtils` methods, almost every example has `%w(x y z)`. It was interesting; sometimes `x y z` were commands like `cp mv mkdir` other times they held filenames or directories. Looked like a list of some sort, but felt like I was missing something. To [StackOverflow] I went.

> `%w(foo bar)` is a shortcut for `["foo", "bar"]`. Meaning it's a notation to write an array of strings separated by spaces instead of commas and without quotes around them.

I like it. 

Being curious, I followed a couple links provided and found even more interesting `%(...)` uses.

```ruby
# foo = 'bar'

%i(one two three)                       # Array of Symbols
#=> [:one, :two, :three]

%q(Some String of "Characters")         # Single Quoted String - when using "" inside ''
#=> 'Some String of "Characters"'

%Q() or %(Some String of "Characters")  # Double Quoted String - escape "" inside ""
#=> "Some String of \"Characters\""

%r(/usr/bin/#{foo})                     # Regular Expression - use to escape `/`
#=> /\/usr\/bin\/bar/

%s(one)                                 # Symbol 
#=> [:one]

%w(#{foo}, one one-hundred\ one)        # Array - single quoted string
#=> ["\#{foo}", one", "one-hundred one"]

%W(#{foo}, one one-hundred\ one)        # Array - double quoted string
#=> ["bar", one", "one-hundred one"]

%x(ls /usr/local)                       # Backtick (call system commands/capture subshell result)
#=> `ls /usr/local` 
```

- The `()` can be replaced with other non-alphanumeric characters:`[],{},<>,!!` etc.
- An uppercase letter allows interpolation/expression substitution and escaped characters.
- A lowercase letter disables them.

---

- [source](http://ruby-doc.org/stdlib-2.3.1/libdoc/fileutils/rdoc/FileUtils.html#method-c-cp)
- [source](http://ruby-doc.org/core-2.3.1/doc/syntax/literals_rdoc.html#label-Percent+Strings)
- [source](http://chillibear.org/2012/03/ruby-percent-syntax-percent-functions.html)

[StackOverflow]: http://stackoverflow.com/a/1274703