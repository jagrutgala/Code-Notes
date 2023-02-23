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

In Git, the process of taking a `snapshot` or `image` of the current state of your code at a particular point in time is referred to as "snapshotting." This snapshot contains every file and directory in your repository, along with their contents.

A `commit` is the git version of a snapshot. We can create a commit in Git by using the `git commit` command. Git stages all of your changes and creates a new commit of the repository's history.

### git add

`git add` command is used to add changes into the staging area. Staging area is a collection of changes that will be committed if you commit.

```
$ git add [options] <file/directory-path>
```

commonly used flags with `git add` are

- `-A` or `--all`: This flag stages all changes, including new files, modifications, and deletions.
- `-u` or `--update`: This flag stages changes to files that are already being tracked by Git. It does not stage new files that have been added.
- `-n` or `--dry-run`: This flag doesn't actually add the file(s), just show if they exist and/or will be ignored.
- `-i` or `--interactive`: This flag provides a interactive menu to add modifications of working directory to the staging area.
- `-p` or `--patch`: This flag allows you to interactively choose which patches you wish to stage. This effectively runs `git add --interactive`, but bypasses the initial command menu and directly jumps to the patch subcommand.

#### git add (interactive mode)

The `-i` or `--interactive` flag for the git add command launches an interactive mode for staging changes. This allows you to selectively stage parts of a file or multiple files, as opposed to staging the entire file(s) with the normal git add command.

In interactive mode, Git will present you with a menu of options, including:

- `s`: stage this hunk.
- `n`: do not stage this hunk.
- `q`: quit; do not stage this hunk nor any of the remaining ones.
- `a`: stage this and all later hunks in the file.
- `d`: do not stage this hunk nor any of the later hunks in the file.
- `g`: select a hunk to go to.
- `/`: search for a hunk matching the given regex.
- `j`: leave this hunk undecided, see next undecided hunk.
- `J`: leave this hunk undecided, see next hunk.
- `k`: leave this hunk undecided, see previous undecided hunk.
- `K`: leave this hunk undecided, see previous hunk.
  Using this interface, you can review the changes to each file and decide which changes to stage and which to leave unstaged.

The git add -i command can be useful when you want to carefully control which changes are staged, especially when working with large or complex changes.

### git status

`git status` command displays current status of the repository. It shows information like:

- your current branch.
- files modified but not staged yet.
- files staged and are ready to be committed.
- files not being tracked by Git.

The output of the `git status` command is usually color-coded, with different colors indicating different types of changes (e.g., unstaged changes, staged changes, untracked files, etc.).

### git diff

The `git diff` command is used to show the differences between the working directory, the staging area (index), and the most recent commit in your Git repository.

`git diff` (default) with no arguments will show the differences between the _working directory_ and the _staging area_.

`git diff --staged` or `git diff --cached` will show the differences between the _staging area_ and the _most recent commit_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

You can also use git diff to compare the differences between two different commits, branches, or tags. For example, to compare the changes between the current branch and a different branch, you can use the command git diff <branch-name>.


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

- [ ] as
