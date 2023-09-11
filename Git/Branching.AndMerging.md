# Branching and Merging

Git's branching system allows developers to work and on the same repository.

## git branch

`git branch` command is used to create new branches. You can also inspect branches on local & remote. Branch command can be used to create, rename, delete and view branches using different flags.

Syntax for `git branch` is:
```
$ git branch [<options>]
```

commonly used flags with `git branch` are:
- `-d`: lets you delete a branch
- `-m`: lets you move/ rename a branch
- `-c`: lets you copy a branch
- `-l`: lists all the branches following a regular-expression
- `-v`: verbose output
- `<branch-name>`: creates a branch of that name

To create a new branch from a old branch you can use the following syntax:
```
$ git branch <new-branch> <old-branch>
```


## git checkout

`git checkout` lets you move between branches. As its name suggests you can look at a branch. Using checkout you can also look at individual commits, not recommended for beginners. Checkout does not allow you to go to another branch if there are changes on your current branch, you can check if there are the current branches using the `git status` command. So make sure, you commit or stash your changes before committing.

Syntax for `git checkout` is:
```
$ git checkout [<options>] <branch|commit>
```

commonly used flags with `git checkout` are:
- `-b`: allows you to checkout and create a branch at the same time from the current branch
- ``

## git switch

## git merge

## git mergetool

## git stash

## git tag

## git worktree
