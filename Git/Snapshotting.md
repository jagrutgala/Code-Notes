# Snapshotting

In Git, the process of taking a `snapshot` or `image` of the current state of your code at a particular point in time is referred to as "snapshotting." This snapshot contains every file and directory in your repository, along with their contents.

A `commit` is the git version of a snapshot. We can create a commit in Git by using the `git commit` command. Git stages all of your changes and creates a new commit of the repository's history.


## Git Workspace

### untracked
### tracked
### staged


## git add

`git add` command is used to add changes into the staging area. Staging area is a collection of changes that will be committed if you commit.

### Syntax
```bash
$ git add [options] <file/directory-path>
```

commonly used flags with `git add` are:

- `-A` or `--all`: This flag stages all changes, including new files, modifications, and deletions.
- `-u` or `--update`: This flag stages changes to files that are already being tracked by Git. It does not stage new files that have been added.
- `-n` or `--dry-run`: This flag doesn't actually add the file(s), just show if they exist and/or will be ignored.
- `-i` or `--interactive`: This flag provides a interactive menu to add modifications of working directory to the staging area.
- `-p` or `--patch`: This flag allows you to interactively choose which patches you wish to stage. This effectively runs `git add --interactive`, but bypasses the initial command menu and directly jumps to the patch subcommand.

### git add (interactive mode)

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

## git status

`git status` command displays current status of the repository. It shows information like:

- your current branch.
- files modified but not staged yet.
- files staged and are ready to be committed.
- files not being tracked by Git.

### Syntax
```bash
$ git status [options]
```

The output of the `git status` command is usually color-coded, with different colors indicating different types of changes (e.g., unstaged changes, staged changes, untracked files, etc.).

### Example
```bash
$ git status
```

## git commit

`git commit` command takes a snapshot of your changes in staging area. It captures the difference between the last snapshot and current snapshot. You can also add a note to remind yourself about the changes. It is like a save, and a serries of commits tracks the progress & evolution of your project overtime. Example of `git commit` command is: `git commit -m "Initial Commit"`

### Syntax
```bash
$ git commit [options]
```

commonly used flags with `git commit` are:

- `-m`: This flag lets you write a short message right away, just like quickly explaining your changes.
- `--amend`: Imagine you forgot to add a message to your commit. This flag helps you add and edit the last commit. (Note: this overrides the last commit with a new commit).
- `-a`: This flag automatically takes a picture of all your coloring changes without making you do it one by one.
- `--no-edit`: This flag specifies that you are rewording or amending the commit but don't want to change the commit message.
- `--allow-empty`: This flag allows you to commit without any changes to the repository.

### Example
- amend your last commit with a new message.
```bash
$ git commit --amend -m "New commit message"
```

# Next Steps
[<-- Repo Setup](RepositorySetup.md) | [Inspection & Comparison -->](InspectionAndComparison.md)

## Also see
- [gitignore (recommended)](GitIgnore.md)
- [git config](GitConfig.md)
