[![](https://img.shields.io/badge/OS-Unix-blue.svg?longCache=True)]()
[![](https://img.shields.io/pypi/v/repo-config.svg?maxAge=3600)](https://pypi.org/project/repo-config/)
[![](https://img.shields.io/npm/v/repo-config.svg?maxAge=3600)](https://www.npmjs.com/package/repo-config)
[![Travis](https://api.travis-ci.org/looking-for-a-job/repo-config.svg?branch=master)](https://travis-ci.org/looking-for-a-job/repo-config/)

<b>store repo config in dotfiles</b>

#### Install
```bash
$ [sudo] npm i -g repo-config
```
```bash
$ [sudo] pip install repo-config
```

#### Features
+   store repos config in dotfiles
    +   **exclude unwanted files from commit**
    +   you can symlink dotfiles to a special backup repo
    +   easy to perform search and commands

#### How it works
`path/to/repo/.config/` - repo config

git@host:**owner/repo**.git - git remote, required for save/load

`~/.config/repo-config/owner/repo/` - dotfiles

#### Config
```bash
$ echo "/.config" >> ~/.gitignore
```

optional. environment variables:
```bash
$ export REPO_CONFIG_DOTFILES=~/.config/repo-config # $XDG_CONFIG_HOME/repo-config by default
$ export REPO_CONFIG_DIR=.config                    # .config by default
```

#### CLI
```bash
usage: repo-config command [args]

Available commands:
    init                    create .config/ directory
    load                    load .config/ from dotfiles
    save                    save .config/ to dotfiles

run `repo-config COMMAND --help` for more infos
```

#### Examples
```bash
$ cd path/to/repo
$ repo-config init
$ ... # generate and edit config/tmp files
$ repo-config save
.config/ saved to ~/.config/repo-config/owner/repo
$ repo-config load
.config/ loaded from ~/.config/repo-config/owner/repo
```


symlink dotfiles to a special backup repository:

```bash
$ ln -fs path/to/backup-repository/repo-config ~/.config/repo-config
```

##### save/load multiple repos config
```bash
$ find ~/git -type d -name ".config" -maxdepth 3 -execdir repo-config save \;
```

using **execdir** package ([pypi.org/project/execdir/](https://pypi.org/project/execdir/) or [npmjs.com/package/execdir/](https://pypi.org/project/execdir/))
```bash
$ execdir run all repo-config save
```

<p align="center"><a href="https://pypi.org/project/readme-md/">readme-md</a> - README.md generator</p>