# Scripts and configuration

**`.bashrc`**

```bash
# Add the next lines in ~/.bashrc (when you have git installed):
parse_git_branch() {
  if ! git rev-parse --git-dir > /dev/null 2>&1; then
    return 0
  fi
  git_branch=$(git branch 2>/dev/null| sed -n '/^\*/s/^\* //p')
  echo "[$git_branch]"
}
PS1="${debian_chroot:+($debian_chroot)}\[\033[01;36m\]\u@\h\[\033[00m\]:\[\033[01;32m\]\w\[\033[00m\]\[\033[01;31m\]\$(parse_git_branch)\[\033[00m\]$ "
```

<hr>

**`.bash_aliases`**

<hr>

**`.gitconfig`**

https://githowto.com/aliases

```
[credential]
  helper = cache --timeout=360000
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  lo = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
  type = cat-file -t
  dump = cat-file -p
```

<hr>

**`.editorconfig`

# editorconfig.org

root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = true
max_line_length = 120
trim_trailing_whitespace = true

[*.md]
max_line_length = 0
trim_trailing_whitespace = false

[*.js]
max_line_length = 120

[*.jsx]
max_line_length = 120

[COMMIT_EDITMSG]
max_line_length = 0
