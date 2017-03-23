# Scripts and configuration

- [Shell](#shell)
- [Git](#git)
- [Navegadores](#navegadores)
- [Editores](#editores)
  - [Config. general](#config-general)
  - [Atom](#atom)
  - [Vim](#vim)
- [Gnome-shell](#gnome-shell)
- [NPM](#npm)
- [Yarn](#yarn)
 

## Shell

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

**`.bash_aliases`**

...

<hr>

## Git

**`.gitconfig`**

https://githowto.com/aliases

```
[core]
  editor = vim
  pager = less -x1,3
[color]
  ui = true
[user]
  name = myusername
  email = myuseremail
[push]
  default = simple
[credential]
  helper = cache --timeout=360000
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  unstage = reset HEAD --
  last = log -1 HEAD
  lo = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
  lgb = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset%n' --abbrev-commit --date=relative --branches
  type = cat-file -t
  dump = cat-file -p
```

<hr>

## Navegadores

### Google Chrome

Instalar Google Chrome (varios) y extensiones

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get install google-chrome-beta
sudo apt-get install google-chrome-stable
```

### Firefox Developer Edition

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/firefox-aurora
sudo apt-get update
```

## Editores

### Config. general

**`.editorconfig`**

```
editorconfig.org

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
```

<hr>

### Atom

**Atom packages:**

Algunos están comentados porque aunque son interesantes actualmente no los utilizo:

```bash
# Seti: Extensión con tema y sintaxis específica
apm install monokai-seti
apm install seti-ui

# atom-typescript: soporte del Lenguaje TypeScript
apm install atom-typescript

# language-postcss: soporte de PostCSS
#  apm install language-postcss # https://atom.io/packages/language-postcss

# HTML Linter: para evitar fallos tontos a la hora de escribir tu HTML:
# apm install linter-htmlhint

# SASS Linter: para prevenir errores escribiendo SASS/SCSS:
apm install linter-sass-lint

# linter-eslint: para JavaScript
apm install linter-eslint

# linter-tslint: para TypeScript
apm install linter-tslint

# linter-jsonlint: para ficheros JSON
apm install linter-jsonlint

# autoclose-html: extensión para autocerrar tags, solo HTML :-( investigar como cerrar cualquier tag
# apm install autoclose-html

# less-than-slash: extensión para cerrar tags. En teoría no haría falta la anterior :-/
apm install less-than-slash

# pigments: extensión que muestra en el CSS y en el color final la variable de color (#ff0000 se vería en rojo)
apm install pigments

# git-time-machine: Ver los cambios de un fichero en una linea temporal
# apm install git-time-machine # https://atom.io/packages/git-time-machine

# open-recent: Extensión para abrir ficheros recientemente cerrados.
apm install open-recent

# expose: Extensión para hacer exposé de documentos abiertos (como Ubuntu y Mac) con alt+shift+e (gestión de ventanas):
# apm install expose

# todo-show: Extensión que muestra un panel lateral con el contenido de ficheros TODO CHANGED etc. encontrados junto al fichero abierto
# apm install todo-show # no sé si le daré mucho uso...

# minimap: Extensión con una lateral con miniatura (como en Sublime)
apm install minimap

# highlight-selected: Extensión para destacar palabras seleccionadas
apm install highlight-selected
apm install minimap-highlight-selected

# File Type Icons: Te añade iconos estándares en tu árbol de ficheros para poder distinguir visualmente el tipo de cada fichero.
apm install file-type-icons

# jumpy: Saltar entre palabras y lineas en el editor mediante: shift+enter y las dos primeras letras del lugar al que se quiera saltar:
apm install jumpy # https://atom.io/packages/jumpy

# linter-flow 
# https://github.com/AtomLinter/linter-flow
npm install -g flow flow-bin
flow init
apm install linter-flow

# React plugin 
# https://atom.io/packages/react
apm install react
```

Hints: teclas rápidas con fuzzy-finder: ctrl+t y ctrl+b

<hr>

### vim

```
if has("syntax")
  syntax on
endif

set number
set tabstop=2
```
## Gnome-shell

### How to move window buttons to right in Ubuntu 16.04

http://askubuntu.com/questions/764166/how-to-move-window-buttons-to-right-in-ubuntu-16-04

```sh
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'
```

### Extensions

- https://extensions.gnome.org/extension/921/multi-monitors-add-on/  escritorios virtuales en varios monitores
- https://extensions.gnome.org/extension/820/minimum-workspaces/ mínimo de escritorios permanente
- https://extensions.gnome.org/extension/15/alternatetab/ miniaturas con alt-tab y facilidades
- https://extensions.gnome.org/extension/977/recent-items/ últimos archivos accedidos
- https://extensions.gnome.org/extension/826/suspend-button/ añadir botón para suspender
- https://extensions.gnome.org/extension/8/places-status-indicator/
- https://extensions.gnome.org/extension/7/removable-drive-menu/
- https://extensions.gnome.org/extension/6/applications-menu/

## npm

~/.bashrc

```
# No utilizar sudo con NPM para evitar problemas de permisos:
# https://fettblog.eu/snippets/node.js/npm-without-sudo/
npm config set prefix ~/npm
export PATH="$PATH:$HOME/npm/bin" # en ~/.bashrc
```

Fix para problema frecuente (demasiados inodos en tareas watch) en Linux:

```
echo 524288 | sudo tee -a /proc/sys/fs/inotify/max_user_watches
```

## Yarn

https://yarnpkg.com/lang/en/docs/install/

Fix para problema frecuente con `yarn test:watch`:

Error: watch ENOSPC
at errnoException (fs.js:1019:11)    

```
# https://github.com/gulpjs/gulp/issues/217#issuecomment-61039024
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
