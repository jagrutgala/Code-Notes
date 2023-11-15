## Advance Snapshotting

git advance topics related to snapshotting

## git restore

`git restore` take you back to previous commits, without affecting the commit history. A simple example of git reset is `git restore --source=<commit-hash> <file-path>`. This command with take you back to whatever state the file was at the time of `<commit-hash>`. You can use git restore to discard changes in the working directory or unstage changes from the staging area.

commonly used flags with `git restore` are
- `--source`: Using this flag you can specify a commit to which you want to restore to.
- `--staged`: This flag is used to unstage changes that you've added to the staging area.
- `--worktree`: This is the default behavior of git restore. It restores the file to the state it has in the HEAD commit, effectively discarding any local changes in the working directory.

## git reset

`git reset` take you back to previous commits, undoing the changes. A simple example of git reset is `git reset --hard <commit-hash>`. This command with take you back to whatever state your repository was at the time of `<commit-hash>`.

> Note: It edits your commit history. The commits itself are gone. Be careful when using this command.

commonly used flags with `git reset` are
- `--hard`: Using this flag with git reset will remove changes completely.
> Note: Changes will be lost forever.
- `--soft`: Using this flag with git reset will remove the commits but keep the changes. The changes will be unstaged.
- `--mixed`: This flag is a mix of `--soft` and `--hard` where the commits are remove and changes are unstaged. Plus, you can decide which changes to put back on the remove completely and which to keep.

## git rm
`git rm` command is used to remove files from the git. It is also frequently used to remove files from staging area. For example, Say we have a file we no longer want to be tracked. We will use this command to remove it completely, then add the file to gitignore.

Syntax for `git rm`:
```
$ git rm [options] [<file/path>]
```

commonly used flags for `git rm` are:
- `-r`: recursive flag used on a directory to remove the directory and all its children
- `--cached`: cached flag is used to signify to remove from staging area

Example of `git rm` to remove all files from staging area:
```
$ git rm --cached
```

## git mv
`git mv` command is used to **move files** or **rename files** in the git.

Syntax for `git mv`:
```
$ git mv [options] <source> <destination>
```

Example of `git mv` to rename a file:
```
$ git mv hello.txt world.txt
```

