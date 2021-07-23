# The Ins and Outs of Stashing

## Why We Need Git Stash

<ul>
  <li>My changes come with me to the destination branch</li>
  <li>Git won't let me switch if it detects potential conflicts</li>
</ul>

## Stashing Basics: Git Stash Save & Pop

<strong>Stashing</strong><br />
Git provides an easy way of stashing these uncommitted changes so that we can return to them later, without having to make unnecessary commits.<br />
<a href="https://git-scm.com/docs/git-stash">Git Stash Documentation</a>

```
git stash
git stash save
```

`git stash` is super useful command that helps you save changes that you are not yet ready to commit. You can stash changes and then come back to them later. Running `git stash` will take all uncommitted changes (staged and unstaged) and stash them, reverting the changes in your working copy.

```
git stash pop
```

Use `git stash pop` to remove the most recently stashed changes in your stash and re-apply them to your working copy. My stashed changes are restored!

## Git Stash Apply

```
git stash apply
```

You can use `git stash apply` to apply whatever is stashed away, without removing it from the stash. This can be useful if you want to apply stashed changes to multiple branches.

## Working with Multiple Stashes

```
git stash
// do some other stuff...
git stash
// do some other stuff...
git stash
```

You can add multiple stashes onto the stack of stashes. They will all be stashed in the order you added them. You can run `git stash list` to view all stashes.<br />

```
git stash list
git stash apply stash@{2}
```

<strong>Applying Specific Stashes</strong><br />
git assumes you want to apply the most recent stash when you run `git stash apply`, but you can also specify a particular stash like `git stash apply stash@{2}`.

## Dropping and Clearing The Stash

```
git stash drop stash@{2}
```

To delete a particular stast, you can use `git stash drop <stash-id>`.

```
git stash clear
```

To clear out all stashes, run `git stash clear`.
