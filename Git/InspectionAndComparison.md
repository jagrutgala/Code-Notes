# Inspection and Comparison

<!-- description -->
<!-- use of inspection -->
<!-- use of comparison -->

## git show

`git show` command is used to see a specific commit details.

### Syntax
```bash
$ git show [<options>] [<commit-hash>...]
```

commonly used flags with `git show` are:
- `-p`: shows changes made in the commit, basically a diff
- `--stat`: shows number of lines changed in each file

### Example
- `<commit>` -> see a particular commit details
```bash
$ git show 1f2060f
```

## git log

The `git log` command is used to see all the commit logs. The commits are ordered by time of commit. The log shows the following info:
- commit hash
- which branch the commit was made on
- author of the commit name + email
- commit message

### Syntax
```
$ git log [<option>] [<range>] [path]
```

commonly used flags with `git log` are:

- `--graph`: text-based graphical representation of the commit history. The graph representation helps understand commits & merges on different branches
- `-<n>`: it shows the latest `n` commits
- `--after`: show commits after a date
- `--before`: show commits before a date


### Examples

- `<branch>` -> see log of a branch without being checkout to that branch
```
$ git log feature/git
```

- `branchA..branchB` -> see commit in branchB and not in BranchA
```
$ git log main..feature/git
```

## git diff

The `git diff` command is used to show the differences between the working directory, the staging area (index), and the most recent commit in your Git repository.

<!-- TODO: add git diff syntax block -->

`git diff` (default) with no arguments will show the differences between the _working directory_ and the _staging area_.

`git diff --staged` or `git diff --cached` will show the differences between the _staging area_ and the _most recent commit_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

`git diff <commit-hash> <commit-hash>` will show the differences between the _those two commits_.

You can also use git diff to compare the differences between two different commits, branches, or tags. For example, to compare the changes between the current branch and a different branch, you can use the command git diff <branch-name>.

<!-- TODO: add git diff examples block. add examples for branch diff, staged changes diff -->


# Next Steps
[<-- Snapshotting](Snapshotting.md) | [Synchronization -->](Syncronization.md)

## Also See
- [debugging git](Debugging.md)
