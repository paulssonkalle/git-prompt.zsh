# Informative Git Prompt for Zsh

<img src="screenshot.png" width="400" />

A lightweight and fast Git prompt for Zsh heavily inspired by Olivier Verdier's
[zsh-git-prompt](https://github.com/olivierverdier/zsh-git-prompt) and very similar to the "Informative VCS" prompt of
fish shell. 

This prompt requires Git with `--porcelain=v2` support, which is available since version 2.11.0. You can check if your
installation is compatible by executing `git status --branch --porcelain=v2` inside a Git repository.


## Installation
Clone this repo or [download](https://raw.githubusercontent.com/woefe/zsh-git-prompt/master/git-prompt.zsh) the
`git-prompt.zsh` file. Then add following lines to your `.zshrc`.

```
prompt off  # Optional in some cases
source path/to/git-prompt.zsh
PROMPT='%B%40<..<%~ %b$(gitprompt)%(?.%F{blue}❯%f%F{cyan}❯%f%F{green}❯%f.%F{red}❯❯❯%f) '
```


## Prompt Structure
The structure of the prompt is the following:

```
[<branch_name><tracking_status>|<local_status>]
```

* `branch_name`: Name of the current branch or commit hash if HEAD is detached. When in 'detached HEAD' state, the
    `branch_name` will be prefixed with a colon `:` to indicate that it is actually a hash and not a branch name.
* `tracking_status`:
    * `↑n`: ahead of remote by `n` commits
    * `↓n`: behind remote by `n` commits
    * `↓m↑n`: branches diverged; other by `m` commits, yours by `n` commits
* `local_status`:
    * `✔`: repository is clean
    * `✖n`: there are `n` unmerged files
    * `●n`: there are `n` staged files
    * `✚n`: there are `n` unstaged and changed files
    * `…n`: there are `n` untracked files


## Features / Non-Features
* A pure shell implementation using awk; no Python, no Haskell required
* Fast; git command is called only once
* (Currently) no customization via environment variables. To customize the prompt you will have to edit the
    `git-prompt.zsh` file.

