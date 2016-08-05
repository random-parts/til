---
headline: 'Bundle update github-pages - nokogiri error'
date: 2016-07-17
category: github
tags:
  - gems
  - github-pages
  - homebrew
  - jekyll
---

Tried to `$ bundle update github-pages` and ran into this `nokogiri` error:

```
Installing nokogiri 1.6.8 (was 1.6.7.2) with native extensions

Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory: /usr/local/lib/ruby/gems/2.3.0/gems/nokogiri-1.6.8/ext/nokogiri
/usr/local/opt/ruby/bin/ruby -r ./siteconf20160702-50345-1hesiwb.rb extconf.rb --use-system-libraries
Using pkg-config version 1.1.7
checking if the C compiler accepts ... yes
checking if the C compiler accepts -Wno-error=unused-command-line-argument-hard-error-in-future... no
Building nokogiri using system libraries.
ERROR: cannot discover where libxml2 is located on your system. please make sure `pkg-config` is installed.
*** extconf.rb failed ***
************************************************************************
IMPORTANT NOTICE:

Building Nokogiri with a packaged version of libxml2-2.9.4.

Team Nokogiri will keep on doing their best to provide security
updates in a timely manner, but if this is a concern for you and want
to use the system library instead; abort this installation process and
reinstall nokogiri as follows:

    gem install nokogiri -- --use-system-libraries
        [--with-xml2-config=/path/to/xml2-config]
        [--with-xslt-config=/path/to/xslt-config]

If you are using Bundler, tell it to use the option:

    bundle config build.nokogiri --use-system-libraries
    bundle install

Note, however, that nokogiri is not fully compatible with arbitrary
versions of libxml2 provided by OS/package vendors.
************************************************************************

[. . .]

An error occurred while installing nokogiri (1.6.8), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.6.8'` succeeds before bundling.
```

I was using `Bundler`, so I tried the provided solution:

```sh
$ bundle config build.nokogiri --use-system-libraries
$ bundle install
```

That did not work. After a bit of searching, this is what worked: (Requires [Homebrew]).

```sh
$ brew install libxml2
$ gem install nokogiri -- --use-system-libraries --with-xml2-include=/usr/local/opt/libxml2/include/libxml2
$ bundle update
```

1. `$ brew install libxml2` installs the latest version `libxml2` & makes it easy to update it as needed.
2. `$ gem install nokogiri` with the location of the `libxml2`. For a specfic version use the Cellar location directly:
`/usr/local/Cellar/libxml2/2.9.4/include/libxml2` or any other version in there.
3. `$ bundle update` to finish the update that failed on the above error.

---
- [source 1](http://stackoverflow.com/a/9322045)
- [source 2](http://stackoverflow.com/a/23585885)

[Homebrew]: http://brew.sh/