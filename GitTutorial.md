%title: Git Tips&Tricks
%author: David Antón
%date: 2017-06-28

                                                 ░░░░████████░░░░
                                                 ░░███░░▓▓▓▓███░░
                                                 ░░█░░░░▓▓▓▓░░█░░
                                                 ░█░░░░▓▓▓▓▓▓░░█░
                                                 ██░░░▓▓░░░░▓▓░██
                                                 █▓▓▓▓▓░░░░░░▓▓▓█
                                                 █▓░░▓▓░░░░░░▓▓▓█
                                                 █░░░░▓░░░░░░▓▓░█
                                                 █░░░░▓▓░░░░▓▓░░█
                                                 █▓░░▓▓▓▓▓▓▓▓▓░░█
                                                 █▓▓▓████████▓▓░█
                                                 ░███░░█░░█░░███░
                                                 ░░█░░░█░░█░░░█░░
                                                 ░░█░░░░░░░░░░█░░
                                                 ░░░█░░░░░░░░█░░░
                                                 ░░░░████████░░░░

                                                ▛▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▜
                                                ▌  PRESH START  ▐
                                                ▙▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▟

---

-> Level 0 <-
======

# Clonar un repositorio

    $> git clone <remote> <localDir>
    $> git clone https://github.com/davidantonlou/gitLunchAndLearn.git
    $> git remote
    $> git remote show origin
    $> git remote rename <old> <new>

---

-> Level 0 <-
======

# Subir contenido al repositorio

    $> git add <file/dir>
    $> git commit -a -m "<mensaje>"
    $> git push

---

-> Level 0 <-
======

# Subir contenido al repositorio

    echo uno >> test.txt
    git add -A && git commit -m "1 el breikindance"
    echo dos >> test.txt
    git add -A && git commit -m "2 el crusaito"
    echo tres >> test.txt
    git add -A && git commit -m "3 el maiquelyason"
    sed -i -e 's/dos/cuatro/g' test.txt
    git add -A && git commit -m "4 el robocop"
    echo cinco >> test.txt
    git add -A && git commit -m "Baila chiqui-chiqui"
    echo seis >> test.txt
    git add -A && git commit -m "Lo bailan los heavys y también los frikis"
    echo siete >> test.txt
    git add -A && git commit -m "Perrea, perrea"

---

-> Level 0 <-
======

# Bajar contenido del repositorio

    $> git pull
    $> git fetch


## Fetch hace la descarga pero no sobrescribe los cambios locales ni realiza merges
## Pull hace la descarga de los cambios y realiza el merge con los cambios locales (Fetch + Merge)


---

-> Level 0 <-
======

# ¿Cómo ver mis cambios locales?

    $> git status
    $> gitk
    $> git diff


## Desde intelliJ -> CACA
## Desde SourceTree -> OK

---

-> Level 0 <-
======

# ¿Cómo ver los commits?

    $> git log
    $> git log --pretty
    $> git log --author=daan
    $> git log --help

---





                                                  ▛▀▀▀▀▀▀▀▀▀▜
                                                  ▌LEVEL UP!▐
                                                  ▙▄▄▄▄▄▄▄▄▄▟

---

-> Level 1 <-
======

# Trabajando con branches

    $> git branch
    $> git branch <branchName>
    $> git checkout <branchName>
    $> git branch -D <branchName>

---

-> Level 1 <-
======

# ¿Puedo guardar mis cambios locales sin subirlos al repositorio?

    $> git stash list
    $> git stash show
    $> git stash drop
    $> git stash pop

---

-> Level 1 <-
======

# ¿Cómo actualizar un commit que ya he realizado?

    $> git ammend
    $> git add <file>
    $> git commit --amend
    $> git push             # Jejeje ERROR! :D hay que hacer force
    $> git push --force     # OJO! Acuérdate de lo que firmaste...

---

-> Level 1 <-
======

# Trabajando con Tags

    $> git tag 2.5
    $> git tag 2.6 <commitHash>
    $> git diff 2.5 2.6	            # Compara el tag 2.6 con el 2.5
    $> git branch <newBranch> 2.5      # Empezar un branch con el estado del tag 2.5
    $> git log 2.5..2.6

---





                                                    ▛▀▀▀▀▀▀▀▀▀▜
                                                    ▌LEVEL UP!▐
                                                    ▙▄▄▄▄▄▄▄▄▄▟

---

-> Level 2 <-
======

# ¿Cómo hago reset de un commit?

    $> git reset <commitHash>
    $> git reset origin/HEAD
    $> git reset --hard origin/master   # OJO! Yo no me hago responsable de lo que ocurra...

---

-> Level 2 <-
======

# ¿Cómo puedo revertir un commit?

    $> git revert <commitHash>
    $> git revert HEAD~2..HEAD      # Revert de los ultimos 2 commits

---

-> Level 2 <-
======

# ¿Cómo puedo realizar la mezcla de dos branches?

    $> git merge <branchName>
    $> git mergetool                # Cuando el merge nos diga que tenemos conflictos

---

-> Level 2 <-
======

# ¿Cómo puedo realizar la mezcla de dos branches?

    $> git rebase <branchName>
    $> git rebase --continue    # En caso de que existan conflictos

## Diferencias con merge:
  * Unifica las ramas dejando un árbol lineal simple.
  * Rebase realiza un commit de menos.
  * El rebase unifica las ramas perdiendo el historial de los commits.
  * Además realiza el commit sin importar la cronología temporal en la que se han hecho los commits.

## Otra opción:

    $> git merge --squash <branchName>     # Similar a aplicar un parche que veremos más adelante

---





                                                    ▛▀▀▀▀▀▀▀▀▀▜
                                                    ▌LEVEL UP!▐
                                                    ▙▄▄▄▄▄▄▄▄▄▟

---

-> Level 3 <-
======

# ¿Quién ha modificado un fichero concreto?

    $> git blame <fileName>

---

-> Level 3 <-
======

# Limpieza de ficheros modificados o untracked

    $> git clean -n      # Muestra la información de limpieza de ficheros a borrar
    $> git clean -f -d   # OJO! Recuerda lo que firmaste! Elimina ficheros y directorios de manera forzada

---

-> Level 3 <-
======

# Limpieza de branches locales

    $> git remote prune origin
    $> git fetch -p

---

-> Level 3 <-
======

# ¿Puedo mover un commit de rama?

    $> git cherry-pick <commitHash>

---

-> Level 3 <-
======

# ¿Puede git ayudarme a encontrar bugs?

    $> git bisect start      # Búsqueda binaria
    $> git bisect bad
    $> git bisect good 2.5

---

-> Level 3 <-
======

# Generación de parches

    $> git format-patch -2 HEAD --stdout > tmpPatch.patch


---

-> Level 3 <-
======

# Workflow de trabajo con Git

    $> git flow <subcommand>
          # Available subcommands are:
            # init      Initialize a new git repo with support for the branching model.
            # feature   Manage your feature branches.
            # release   Manage your release branches.
            # hotfix    Manage your hotfix branches.
            # support   Manage your support branches.
            # version   Shows version information.

---





                                                    ▛▀▀▀▀▀▀▀▀▀▜
                                                    ▌LEVEL UP!▐
                                                    ▙▄▄▄▄▄▄▄▄▄▟

---

-> Level 99 <-
======

# Comandos recomendados por Git para el día a día

    $> git help everyday

---

-> Level 99 <-
======

# Listado de ficheros desde un commit

    $> git ls-tree --name-only -r <commitHash>

---

-> Level 99 <-
======

# Listado branches que ya se han mergeado con master

    $> git branch --merged master

---

-> Level 99 <-
======

# Eliminar las branches ya mergeadas con master

    $> git branch --merged master | grep -v '^\*' | xargs -n 1 git branch -d

---

-> Level 99 <-
======

# Eliminar branches remotas

    $> git push origin --delete <remoteBranch>

---

-> Level 99 <-
======

# Customizar Git

    $> git config --global alias.<handle> <command>
    $> git config --global alias.co commit
    $> git config color.ui true
    $> git config merge.tool vimdiff
    $> git config --list

---

-> Level 99 <-
======

# Ver el árbol de branches

    $> git log --pretty=oneline --graph --decorate --all

---

-> Level 99 <-
======

# Ver los commits de branch1 que no están en branch2

    $> git log Branch1 ^Branch2

---

-> Level 99 <-
======

# Mostrar todos los branch locales ordenados por commits recientes

    $> git for-each-ref --sort=-committerdate --format='%(refname:short)' refs/heads/

---




                                              ▛▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▜
                                              ▌CHALLENGE COMPLETED▐
                                              ▙▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▟

---





                                                  ▛▀▀▀▀▀▀▀▀▀▀▀▀▜
                                                  ▌BONUS LEVEL!▐
                                                  ▙▄▄▄▄▄▄▄▄▄▄▄▄▟


---

-> Git IDEs <-
=====

* Sourcetree
* Gitk
* Github desktop
* Gitkraken
* Tower



----


                                                  ▛▀▀▀▀▀▀▀▀▀▀▀▀▜
                                                  ▌     ?      ▐
                                                  ▙▄▄▄▄▄▄▄▄▄▄▄▄▟


                                  Cada vez que usais Git desde IntelliJ muere un gatito
