## Synchronization
### git remote

`git remote` command used to manage remote connections in a Git repository. The `git remote` command allows you to view, add, and remove connections to repositories. A Git Remote is a cloud server of sorts that stores a copy of your code, as a back up. It also serves as a platform for sharing you code with your colleagues and friends for collaboration.

> Note
> Using synchronization commands usually involve authentication, i.e. putting username & password.

`git remote` subcommands are:

- `add`: adds a new remote connection with the given 'name' and 'url'.

```
$ git remote add <name> <url>
```

- `remove`: removes an existing remote connection with the given 'name'.

```
$ git remote remove <name>
```

- `set-url`: changes the URL of an existing remote connection with the given 'name'.

```
$ git remote set-url <name> <new-url>
```

- `-v`:  displays a list of all remote connections with their names and URLs.

```
$ git remote -v
```

### git pull
`git pull` is command that checks if there are any new commits to the remote and if there are, then pull the commits from the remote to your repository and merges them in the current branch.
```
$ git pull <remote> <branch>
```
commonly used flags with `git pull` are

- `--ff-only`: This only allows fast-forward merges. If a fast-forward merge is not possible (meaning your local branch has diverged from the remote branch), the pull will fail.
- `--no-commit`: This fetches changes and attempts a merge, but it doesn't create a new commit. It's useful if you want to review and possibly modify the merge before committing it.
- `--allow-unrelated-histories`: his allows you to pull changes even if the local and remote branches have unrelated commit histories. This can be useful when initializing a new repository with existing code.

### git push
`git push` is command that you to uploads new commits from your local repository to the remote repository. If someone else has pushed changes to the remote branch since your last fetch, there might be conflicts. Git will notify you about these conflicts, and you'll need to resolve them locally before you can successfully push.

```
$ git push <remote> <branch>
```
commonly used flags with `git push` are

- `--force`: Use of this flag is not recommended, but it allows you to forcefully push new commits to the repository. Event if it's not fast-forward merge.
- `-u, --set-upstream`: This establishes a tracking relationship between your local branch and the remote branch, so you can simply use git push in the future without specifying the remote and branch.
- `--all`: This pushes all local branches to the remote repository. Be careful when using this, as it might clutter the remote repository with branches that are only relevant locally.

> Note:
> `$ git push origin <commit-hash>:<branch>` to push commits up to that commit.

### git fetch
`git fetch` is command that checks if there are any new commits to the remote and if there are, then pull index from the remote to your repository. `git fetch` only updates the index, meaning it does not bring the commits or merge the commits from the remote to your repository. It's a safe way to see what changes are available on the remote repository and update your local references accordingly
```
$ git fetch
```
- `--all`: This fetches changes from all remote repositories that are configured in your local repository.
- `--prune`: This prunes (deletes) references to remote branches on your local repository that have been deleted on the remote repository. It helps keep your local references up-to-date.
