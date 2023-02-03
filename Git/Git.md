# Git

Git is a open-source distributed version control tool. It is designed to handle everything from small to large projects with speed and efficiency.

It is used for tracking changes in the source code of a software project, managing different versions (or `snapshots`) of the code, and collaborating with other developers.

With Git, developers can work simultaneously on the same project without causing conflicts and track the history of the changes made to the code.

**Version Control**

A `version control system (VCS)` is a software tool that tracks and manages changes to the source code of a software project over time.

Some other Version Control systems other than Git are :

- [Mercurial](https://www.mercurial-scm.org/)
- [Apache Subversion](https://subversion.apache.org/)

## Git Commands Categories

**Repository setup and management**: commands for initializing a repository, cloning an existing repository, and managing remote repositories. Examples: git `clone`, git `init`, git `remote`.

**Snapshotting**: commands for creating, viewing, and managing snapshots (commits) of the repository. Examples: git `add`, git `commit`, git `log`.

**Branching and Merging**: commands for creating, managing, and merging branches in a Git repository. Examples: git `branch`, git `checkout`, git `merge`.

**Synchronization**: commands for synchronizing the repository with remote repositories. Examples: git `pull`, git `push`.

**Inspection and Comparison**: commands for viewing the changes in the repository and comparing different snapshots. Examples: git `diff`, git `show`.

**Miscellaneous**: various other Git commands not fitting into the above categories. Examples: git `stash`, git `rebase`.

## Repository setup

### git clone

`git clone` command used to copy a remote repository onto a local machine. It allows you to download a full copy of a project's source code and history, including all branches and commits, onto your local machine.

```
$ git clone <repository-url> [<directory>]
```

### git init

`git init` command used to initialize a new Git repository. This command creates an empty Git repository in the current directory or in a specified directory.

```
$ git init [<directory>]
```

## Snapshotting

### git add

### git status

### git diff

### git commit

### git notes

### git restore

### git reset

### git rm

### git mv

## Branching and Merging

### git branch

### git checkout

### git switch

### git merge

### git mergetool

### git stash

### git tag

### git worktree

## Synchronization

### git pull

### git push

### git fetch

### git remote

`git remote` command used to manage remote connections in a Git repository. The `git remote` command allows you to view, add, and remove connections to repositories.

`git remote` subcommands are:

- `add` -> adds a new remote connection with the given 'name' and 'url'.

```
$ git remote add <name> <url>
```

- `remove` - removes an existing remote connection with the given 'name'.

```
$ git remote remove <name>
```

- `set-url` - changes the URL of an existing remote connection with the given 'name'.

```
$ git remote set-url <name> <new-url>
```

- `-v` - displays a list of all remote connections with their names and URLs.

```
$ git remote -v
```

## Inspection and Comparison

### git show

### git log

### git diff

### git difftool

### git range-diff

### git shortlog

### git describe

## Miscellaneous

## Git Config



<!-- # Git Ignore File -->

<!-- future topics -->
<!--
alias
stash
bare
rm
mv
switch
git server

 -->
