---
headline: 'Package management with CommandBox CLI'
date: 2016-08-28
category: lucee-coldfusion
tags:
  - cfx
  - commandbox
  - fw1
  - workflow
---

My desire for efficiency and tidiness finally got the better of my need for a sense of control. Generally, I keep up with [current FW/1 releases]. This ends with many old, duplicated zip files in a download folder and backups in old side projects. By the time I moved the extracted files over I have dismissed the presence of the downloaded zip file entirely. Sure, I could have cloned the git repo, but I really had to have the zip file and manually place the `framework` into projects. Same goes for other dependencies. The mess of files and folders eventually erodes my mental well-being and I expend valuable time/energy clearing the clutter.

---

### Enter [CommandBox]

```sh
# install CommandBox. There's a homebrew formula - I like you already
$ brew install commandbox
```

- Move into the project folder and `$ box install` packages

```sh
$ cd ~/project

# install FW/1 package (from ForgeBox software repository) into ~/projects/wwwroot/
$ box install fw1 wwwroot/
```

- Install packages from GitHub

```sh
# add Github repo ValidateThis to project 
$ box install teamcfadvance/ValidateThis
```

- Other [supported endpoints] examples

```sh
# ForgeBox
$ box install fw1-dev
# HTTP/S
$ box install http://www.site.com/myPackage.zip
# local file
$ box install /var/libs/myPackage.zip
# local folder
$ box install /var/libs/myPackage/
# git
$ box install git://site.com/username/repoName.git#v1.5.6
```

- Updating dependencies the easy way

```sh
# update all 
$ box update

# update list of packages
$ box update fw1, etc
```

#### box.json
Edit the `~/project/`[box.json] for more options and configurations.

---
- [source documents](http://commandbox.ortusbooks.com/content/packages/package_management.html)

[current FW/1 releases]: https://github.com/framework-one/fw1/releases
[CommandBox]: https://www.ortussolutions.com/products/commandbox
[supported endpoints]: http://commandbox.ortusbooks.com/content/packages/endpoints/endpoints.html
[box.json]: http://commandbox.ortusbooks.com/content/packages/boxjson/boxjson.html