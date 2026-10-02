# Changing default shell
## list the shell in system

```bash
$ chsh -l
```

## select the path from the option given

```bash
$ chsh -s /bin/fish
```

Log out and back in. Already-open terminals keep the old shell.

# bash

Interactive shells read `~/.bashrc`. On Arch the skeleton `~/.bash_profile` sources `~/.bashrc`, so a login shell picks it up too. Put `PATH` and aliases there.

```bash
export PATH="$HOME/bin:$PATH"
alias ll='ls -la'
```

Open a new terminal to test. `source ~/.bashrc` applies it to the current one.

# fish

fish does not read `~/.bashrc`. Its config is `~/.config/fish/config.fish`.

```fish
fish_add_path $HOME/bin
alias ll='ls -la'
```

`fish_add_path` adds the directory to `$fish_user_paths`, which fish keeps. Running it again does not duplicate the entry.

The prompt is the function `fish_prompt`.

```bash
$ funced fish_prompt
```

`funced` opens that function in `$EDITOR` and loads it when you save.

