# GitHub CLI

`gh` talks to GitHub: login, clone, pull requests, issues. Git itself is `linux/git.md`. The package name is `github-cli`.

```bash
$ sudo pacman -S github-cli
$ gh auth login
$ gh auth status
```

`auth login` asks how to sign in and where to store the token. `auth status` prints the account that is logged in.

```bash
$ gh repo clone <owner>/<repo>
$ gh repo view
$ gh pr list
$ gh pr view <number>
$ gh pr create
$ gh pr checkout <number>
$ gh issue list
$ gh release list
```

`repo view` with no arguments uses the Git repository you are in. `pr create` opens an editor for the title and body. `pr checkout` creates a local branch for that pull request.
