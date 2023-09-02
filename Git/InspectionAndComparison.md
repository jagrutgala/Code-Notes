# Inspection and Comparison

## git show

## git log

## git diff

The `git diff` command is used to show the differences between the working directory, the staging area (index), and the most recent commit in your Git repository.

`git diff` (default) with no arguments will show the differences between the _working directory_ and the _staging area_.

`git diff --staged` or `git diff --cached` will show the differences between the _staging area_ and the _most recent commit_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

You can also use git diff to compare the differences between two different commits, branches, or tags. For example, to compare the changes between the current branch and a different branch, you can use the command git diff <branch-name>.

