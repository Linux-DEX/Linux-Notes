# Git

## Who you are on commits

```bash
$ git config --global user.name "<name>"
$ git config --global user.email "<email>"
```

This writes `~/.gitconfig`. It does not change an existing commit.

## Clone and inspect

```bash
$ git clone <url>
$ git status
$ git diff
$ git log --oneline
```

`status` is what changed. `diff` is the unstaged text of that change. `log --oneline` is one line per commit.

## Save a commit

```bash
$ git add <file>
$ git commit -m "<message>"
```

`add` stages the file. `commit` records the staged files. A commit does not upload anything.

## Throw away uncommitted work

```bash
$ git restore <file>
$ git restore --staged <file>
```

`restore` puts the file back to the last commit and drops the edits. `restore --staged` unstages the file and leaves the edits in the working tree.

## Branch

```bash
$ git switch -c <branch>
$ git switch <branch>
$ git branch
```

`switch -c` creates the branch and moves onto it. `branch` with no arguments lists them. The current one is marked.

## Remote

```bash
$ git remote -v
$ git pull
$ git push -u origin HEAD
```

`pull` brings remote commits into the current branch. `push -u` uploads this branch and sets it to track `origin`. The next `git push` and `git pull` on this branch need no arguments.

## Ignore files

A file named `.gitignore` in the repo lists paths git should not offer to add. One pattern per line. A line that is already tracked stays tracked until you remove it from the index:

```bash
$ git rm --cached <file>
```

That takes it out of the next commit and leaves the copy on disk.
