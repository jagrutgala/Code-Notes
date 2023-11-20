# Snapshotting

In Git, "`commit`" is the a saved version of the state/data in the repository. Newer commits lay on top of previous commits, creating a chain of commits, showcasing a history of changes to the state/data in the repository.

What "`Git Snapshotting`" is the process of committing and building this history. Git also allows you to edit and delete parts of this history.

## Git Workspace

In Git, when making changes and updating the data in the repository, git tracks these changes in 3 layers/stages:

### Untracked Files
These are new files that Git hasn't encountered before or files that have been created since the last commit. Essentially, Git is unaware of these files. They're sitting in your working directory, but Git isn't track of all different changes done to them. To start tracking changes in these files, you need to commit them.

### Tracked Files
These are the files that have been there at-least since the last commit. Fundamentally, Git is aware of these files.

### Staged Files
These are the files that have been there at-least since the last commit. And have been selected to be committed in the next commit. These files are in the staging area.

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
