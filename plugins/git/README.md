# git plugin

The git plugin provides many [aliases](#aliases) and a few useful [functions](#functions).

To use it, add `git` to the plugins array in your zshrc file:

```zsh
plugins=(... git)
```

## Aliases

| Alias                | Command                                                                                                                                                                                  |
| :------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| g                    | git                                                                                                                                                                                      |
| ga                   | git add                                                                                                                                                                                  |
| gaa                  | git add --all                                                                                                                                                                            |
| gb                   | git branch                                                                                                                                                                               |
| gc                   | git commit --verbose                                                                                                                                                                     |
| gc!                  | git commit --verbose --amend                                                                                                                                                             |
| gcn!                 | git commit --verbose --no-edit --amend                                                                                                                                                   |
| gca                  | git commit --verbose --all                                                                                                                                                               |
| gca!                 | git commit --verbose --all --amend                                                                                                                                                       |
| gcan!                | git commit --verbose --all --no-edit --amend                                                                                                                                             |
| gcans!               | git commit --verbose --all --signoff --no-edit --amend                                                                                                                                   |
| gcam                 | git commit --all --message                                                                                                                                                               |
| gcas                 | git commit --all --signoff                                                                                                                                                               |
| gcasm                | git commit --all --signoff --message                                                                                                                                                     |
| gcsm                 | git commit --signoff --message                                                                                                                                                           |
| gcb                  | git checkout -b                                                                                                                                                                          |
| gcf                  | git config --list                                                                                                                                                                        |
| gcl                  | git clone --recurse-submodules                                                                                                                                                           |
| gccd                 | git clone --recurse-submodules "<span>$</span>@" && cd "<span>$</span>(basename <span>$</span>\_ .git)"                                                                                  |
| gclean               | git clean --interactive -d                                                                                                                                                               |
| gpristine            | git reset --hard && git clean -dffx                                                                                                                                                      |
| gcm                  | git checkout $(git_main_branch)                                                                                                                                                          |
| gcd                  | git checkout $(git_develop_branch)                                                                                                                                                       |
| gcmsg                | git commit --message                                                                                                                                                                     |
| gco                  | git checkout                                                                                                                                                                             |
| gcor                 | git checkout --recurse-submodules                                                                                                                                                        |
| gcount               | git shortlog --summary -n                                                                                                                                                                |
| gcs                  | git commit -S                                                                                                                                                                            |
| gcss                 | git commit -S -s                                                                                                                                                                         |
| gcssm                | git commit -S -s -m                                                                                                                                                                      |
| gf                   | git fetch                                                                                                                                                                                |
| gfa                  | git fetch --all --prune                                                                                                                                                                  |
| gfg                  | git ls-files \| grep                                                                                                                                                                     |
| gfo                  | git fetch origin                                                                                                                                                                         |
| ggl                  | git pull origin $(current_branch)                                                                                                                                                        |
| ggp                  | git push origin $(current_branch)                                                                                                                                                        |
| ggpnp                | ggl && ggp                                                                                                                                                                               |
| ggpull               | git pull origin "$(git_current_branch)"                                                                                                                                                  |
| ggpur                | ggu                                                                                                                                                                                      |
| ggpush               | git push origin "$(git_current_branch)"                                                                                                                                                  |
| ggsup                | git branch --set-upstream-to=origin/$(git_current_branch)                                                                                                                                |
| gpsup                | git push --set-upstream origin $(git_current_branch)                                                                                                                                     |
| gl                   | git pull                                                                                                                                                                                 |
| glg                  | git log --stat                                                                                                                                                                           |
| glp                  | git log --pretty=\<format\>                                                                                                                                                              |
| gp                   | git push                                                                                                                                                                                 |
| gpd                  | git push --dry-run                                                                                                                                                                       |
| gpv                  | git push --verbose                                                                                                                                                                       |
| grev                 | git revert                                                                                                                                                                               |
| grh                  | git reset                                                                                                                                                                                |
| grhh                 | git reset --hard                                                                                                                                                                         |
| groh                 | git reset origin/$(git_current_branch) --hard                                                                                                                                            |
| gru                  | git reset --                                                                                                                                                                             |
| gsb                  | git status --short -b                                                                                                                                                                    |
| gss                  | git status --short                                                                                                                                                                       |
| gst                  | git status                                                                                                                                                                               |
| gsw                  | git switch                                                                                                                                                                               |
| gswc                 | git switch -c                                                                                                                                                                            |
| gswm                 | git switch $(git_main_branch)                                                                                                                                                            |
| gswd                 | git switch $(git_develop_branch)                                                                                                                                                         |

| Command                | Description                                                                                              |
| :--------------------- | :------------------------------------------------------------------------------------------------------- |
| `grename <old> <new>`  | Rename `old` branch to `new`, including in origin remote                                                 |
| current_branch         | Return the name of the current branch                                                                    |
| git_current_user_name  | Returns the `user.name` config value                                                                     |
| git_current_user_email | Returns the `user.email` config value                                                                    |
| git_main_branch        | Returns the name of the main branch: `main` if it exists, `master` otherwise                             |
| git_develop_branch     | Returns the name of the develop branch: `dev`, `devel`, `development` if they exist, `develop` otherwise |


### Main branch preference

Following the recent push for removing racially-charged words from our technical vocabulary, the git plugin favors using
a branch name other than `master`. In this case, we favor the shorter, neutral and descriptive term `main`. This means
that any aliases and functions that previously used `master`, will use `main` if that branch exists. We do this via the
function `git_main_branch`.

### Deprecated aliases

These are aliases that have been removed, renamed, or otherwise modified in a way that may, or may not, receive further support.

| Alias  | Command                                                | Modification                                           |
| :----- | :----------------------------------------------------- | :----------------------------------------------------- |
| gap    | `git add --patch`                                      | new alias `gapa`                                       |
| gcl    | `git config --list`                                    | new alias `gcf`                                        |
| gdc    | `git diff --cached`                                    | new alias `gdca`                                       |
| gdt    | `git difftool`                                         | no replacement                                         |
| ggpull | `git pull origin $(current_branch)`                    | new alias `ggl` (`ggpull` still exists for now though) |
| ggpur  | `git pull --rebase origin $(current_branch)`           | new alias `ggu` (`ggpur` still exists for now though)  |
| ggpush | `git push origin $(current_branch)`                    | new alias `ggp` (`ggpush` still exists for now though) |
| gk     | `gitk --all --branches`                                | now aliased to `gitk --all --branches`                 |
| glg    | `git log --stat --max-count = 10`                      | now aliased to `git log --stat --color`                |
| glgg   | `git log --graph --max-count = 10`                     | now aliased to `git log --graph --color`               |
| gwc    | `git whatchanged -p --abbrev-commit --pretty = medium` | new alias `gwch`                                       |

## Functions

### Current

### Work in Progress (WIP)

These features allow to pause a branch development and switch to another one (_"Work in Progress"_,  or wip). When you want to go back to work, just unwip it.

| Command          | Description                                     |
| :--------------- | :---------------------------------------------- |
| work_in_progress | Echoes a warning if the current branch is a wip |
| gwip             | Commit wip branch                               |
| gunwip           | Uncommit wip branch                             |

### Deprecated functions

| Command            | Description                             | Reason                                                          |
| :----------------- | :-------------------------------------- | :-------------------------------------------------------------- |
| current_repository | Return the names of the current remotes | Didn't work properly. Use `git remote -v` instead (`grv` alias) |
