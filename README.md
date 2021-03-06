# [gitnim osx](https://gitnim.com/)

[![tests](https://github.com/disruptek/gitnim/workflows/CI/badge.svg?branch=master)](https://github.com/disruptek/gitnim/actions?query=workflow%3ACI)
![devel](https://img.shields.io/badge/nim-1.5.1-informational?style=flat&logo=nim)
[![License](https://img.shields.io/badge/license-MIT-brightgreen)](#license)

choosenim for choosey nimions

## What is It?

This program adds a git subcommand for Nim `git nim` and installs itself
next to your Nim compiler so that if your compiler is in your `PATH`, so is
**gitnim**.

The `git nim` subcommand allows you to choose from precompiled Nim releases and
download/install them directly by managing your Nim installation as any other
git repository.

This Nim repository also links to the distribution from
https://github.com/disruptek/dist, which is a hand-curated monorepo holding the
most useful Nim modules from the ecosystem.

When run, **gitnim** displays or switches branches in the Nim repository and
updates the **dist** submodules to ensure you always have easy access to the
latest features and fixes as matched to your compiler.

## Installation

### Clone the Repository

We use git for distribution; what else?

```bash
$ git clone https://github.com/disruptek/gitnim_osx gitnim
```

### Add `bin` to `$PATH`

A critical step; humor me on this one. The location of the compiler is used to
infer the installation directory for **gitnim** itself.

```bash
$ export PATH=`pwd`/gitnim/bin:$PATH
```

### Build **gitnim**

You now have a statically-linked Nim binary for your Linux-x64 system, so
you can immediately compile **gitnim**.

This will automatically install the **gitnim** binary next to the compiler
binary according to your `PATH`, enabling the `git nim` subcommand.

```bash
$ cd gitnim
$ nim c gitnim/gitnim.nim
```

## Usage

### List Available Releases

With no additional arguments, `git nim` will check the network for updates and
present the available Nim releases for selection.

The current distribution will be updated from the network, if necessary.

```bash
$ git nim
```
![git nim](https://github.com/disruptek/gitnim/raw/master/docs/gitnim.svg "git nim")

### Choose a Release by Version

When a version is provided, `git nim` will switch to that version immediately
without querying the network, provided the version exists locally.

The distribution will be updated without querying the network, if possible.

```bash
$ git nim 1.4.3
```
![git nim 1.4.3](https://github.com/disruptek/gitnim/raw/master/docs/gitnim143.svg "git nim 1.4.3")

### Choose a Release by Tag

When a tag is provided, `git nim` will switch to the tagged version immediately
without querying the network, provided the tagged reference exists locally.

The distribution will be updated without querying the network, if possible.

```bash
$ git nim devel
```
![git nim devel](https://github.com/disruptek/gitnim/raw/master/docs/gitnimdevel.svg "git nim devel")

```bash
$ git nim stable
```
![git nim stable](https://github.com/disruptek/gitnim/raw/master/docs/gitnimstable.svg "git nim stable")

## Advanced Usage

### Creating Your Own Nim Distribution
```bash
$ git checkout -b "my favorite nims"
```

### Publishing Your Nim Distribution
```bash
$ git remote rename origin upstream
$ git remote add origin "git@github.com:your_name/gitnim.git"
$ git push --set-upstream origin "your branch name"
```

### Adding a Custom Release Tag
```bash
$ git tag -a "tag_name" -m "your description"
```

### Sharing Your Tags With Others
```bash
$ git push --tags
```

### Revoking Your Tags With Others
```bash
$ git push --delete origin tag_name
```

### Adding a Friend's Tags
```bash
$ git remote add jeff https://github.com/jeff/gitnim
```

### Using a Friend's Tag
```bash
$ git nim jeff/1.3.3
```

## Contributing

[https://github.com/disruptek/gitnim](https://github.com/disruptek/gitnim)

## License
MIT
