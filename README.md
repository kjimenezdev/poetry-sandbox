
# Poetry sandbox

>  This repository is intended to be used to dig into poetry's basic usage

The main goal is to be able to setup project depenencies using poetry.

## About poetry

*From the documentation*

> Poetry is a tool to hanle dependency installation as well as building and packaging of Python pacages. It only needs one file to do all of that: the new, standardized pyproject.toml. In other words, poetry uses pyproject.toml to replace setup.py, requirements.txt, setup.cfg, MANIFEST.in and the newly added Pipfile.


### Poetry installation

```sh
curl -sSL https://raw.githubusercontent.com/sdispater/poetry/master/get-poetry.py | python

```

### Poetry autocompletion

```sh
# Bash
poetry completions bash > /etc/bash_completion.d/poetry.bash-completion

# Bash (macOS/Homebrew)
poetry completions bash > $(brew --prefix)/etc/bash_completion.d/poetry.bash-completion # Fish poetry completions fish > ~/.config/fish/completions/poetry.fish # Zsh
poetry completions zsh > ~/.zfunc/_poetry

```

### .toml Syntax

Add the following lines to your .vimrc

```
Plug 'cespare/vim-toml'
Plug 'maralla/vim-toml-enhance'

```

## Commands

### new

`poetry new poetry-sandbox`

* Creates the proyect with the poetry sandbox structure

### init

`poetry init`

* Adds poetry files to the proyect

*Options*
--name: Name of the pacage.
--description: Description of the package.
--author: Author of the package.
--dependency: Package to require with a version constraint. Should be in format foo:1.0.0.
--dev-dependency: Development requirements, see --require.

### install

* Reads the project.toml file resolves and installs the dependencies

` poetry install `

*Options*

` poetry install --no-dev `
` poetry install --extras "mysql pgsql" `
` poetry install -E mysql -E pgsql `

> This will generate a poetry.lock file that contains the version of the dependencies

### update

* Allos updating the depencencies and writing the exact versions to the poetry.lock file

` poetry update `

*Options*

```
--dry-run : Outputs the operations but will not execute anything (implicitly enables --verbose).
--no-dev : Do not install dev dependencies.
--lock : Do not perform install (only update the lockfile).
```

### add <package>

* Adds required packages to {}.toml file and installs them

` poetry add requests`

*Options*

```
--D|dev: Add package as development dependency.
--optional : Add as an optional dependency.
--dry-run : Outputs the operations but will not execute anything.
--version: Specifies the version os the package

```

### remove <package>

* Removes required packages from {}.toml file and installs them

` poetry remove requests`

*Options*

```
--D|dev: Removes a package from the development dependencies.
--dry-run : Outputs the operations but will not execute anything .

```

### show

* Lists all the available packages

*Options*

```
--no-dev: Do not list the dev dependencies.
--tree: List the dependencies as a tree.
-l|--latest: Show the latest version.
-o|--outdated: Show the latest version but only for packages that are outdated.
```

### build

* Builds the source and wheels archives.

`poetry build`

### publish

*Options*

```
-r|--repository: The repository to register the package to (default: pypi). Should match a repository name set by the config command.
--username (-u): The username to access the repository.
--password (-p): The password to access the repository.
```

### config

* Allows to edit poetry config settings and repositories.

`poetry config --list`

*Options*
```
--unset: Remove the configuration element named by setting-key.
--list: Show the list of current config variables.
```

### search

`poetry search requests`

*Options*

`-N|--only-name: Search only in name.`

### lock

* Locks (without installing) the dependencies specified in pyproject.toml.

## Aditional references

[Github repo] (https://github.com/sdispater/poetry)
[Website] (https://poetry.eustace.io/)
