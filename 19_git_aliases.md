# Writing Custom Git Aliases

## The Global Git Config File

Git looks for the global config file at either `~/.gitconfig` or `~/.config/git/config`. Any configuration variales that we change in the file will be applied across all Git repos.<br />
We can also alter configuration variables from the command line if preferred.<br />

## Writing Our First Git Alias

**Adding Aliases**<br />

```
[alias]
  s = status
  l = log
```

We can easily set up Git aliases to make our Git experience a bit simpler and faster.<br />
For example, we could define an alias `git ci` instead of having to type `git commit`.<br />
Or, we could define a custom `git lg` command that prints out a custom formatted commit log.<br />

[Git Alias Documentation](https://github.com/GitAlias/gitalias)<br />
