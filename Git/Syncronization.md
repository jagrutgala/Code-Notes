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
