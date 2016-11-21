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

<hr>

**Atom packages:**

Algunas las comento porque son interesantes pero actualmente no las utilizo.

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

```
