# Undoing Changes and Time Traveling

## Checking Out Old Commits

<strong>Checkout</strong><br />
The `git checkout` command is like Git Swiss Army knife. Many developers think it is overloaded, which is what lead to the addition of the `git switch` and `git restore` commands.<br />
We can use `checkout` to create branches, switch to new branches, restore files, and undo history!

```
git checkout d8194d6
```

We can use `git checkout <commit-hash>` to view a previous commit. Remember, you can use the `git log` command to view commit hashes. We just need the first 7 digits of a commit hash.<br />

<strong>Detached HEAD??</strong><br />
You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by switching back to a branch.<br />
Usually, HEAD points to a specific `branch` reference rather than a particular commit. HEAD is a pointer to the current branch reference. The branch reference is a pointer to the last commit made on a particular branch. When we make a new commit, the branch reference is updated to reflect the new commit. <strong>The HEAD remains the same, because it's pointing at the branch reference.</strong> If we switch to the bugfix branch, HEAD is now pointing at the bugfix reference. This is all to say that HEAD usually refers to a branch NOT a specific commit.<br />
When we checkout a particular commit, <strong>HEAD points at that commit</strong> rather than at the branch pointer.

## Re-attaching Our Detached HEAD!

Do not panic when this happens!<br />
You have a couple options:<br />

<ul>
  <li>Stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.</li>
  <li>Leave and go back to wherever you were before - reattach the HEAD.</li>
  <li>Create a new branch and switch to it. You can now make and save changes, since HEAD is no longer detached.</li>
</ul>

## Referencing Commits Relative to HEAD

```
git checkout HEAD~1
```

`git checkout` supports a slightly odd syntax for referencing previous commits relative to a particular commit.<br />
HEAD~1 refers to the commit before HEAD (parent)<br />
HEAD~2 refers to 2 commits before HEAD (grandparent)<br />

## Discarding Changes with Git Checkout

Suppose you have made some changes to a file but don't want to keep them. To revert the file back to whatever it looked like when you last committed, you can use:<br />

```
git checkout HEAD <file>
```

`git checkout HEAD <filename>` to discard any changes in that file, reverting back to the HEAD.<br />

```
git checkout -- <file>
```

Another shorter option to revert a file. Rather than typing HEAD, you can substitute -- followed by the file(s) you want to restore.<br />

## Un-Modifying with Git Restore

`git restore` is a brand new Git command that helps with undoing operations. Because it is so new, most of the existing Git tutorials and books do not mention it, but it is worth knowing! Recall that `git checkout` does a million different things, which many git users find very confusing. `git restore` was introduced alongside `git switch` as alternatives to some of the users for `checkout`.<br />
<a href="https://git-scm.com/docs/git-restore">Git Restore Documentation</a>

```
git restore <file-name>
```

The above command is not "undoable" if you have uncommitted changes in the file, they will be lost!<br />
Suppose you have made some changes to a file since your last commit. You have saved the file but then realize you definitely do NOT want those changes anymore! To restore the file to the contents in the HEAD, use `git restore <file-name>`.<br />

```
git restore --source HEAD~1 app.js
```

`git restore <file-name>` restores using HEAD as the default source, but we can change that using the `--source` option. For example, `git restore --source HEAD~1 home.html` will restore the contents of home.html to its state from the commit prior to HEAD. You can also use a particular commit hash as the source.

## Un-Staging Changes with Git Restore

```
git restore --staged <file-name>
```

If you have accidentally added a file to your staging area with `git add` and you do not wish to include it in the next commit, you can use `git restore` to remove it from staging.<br />

## Undoing Commits with Git Reset

```
git reset <commit-hash>
```

Suppose you have just made a couple of commits on the master branch, but you actually meant to make them on a separate branch instead. To undo those commits, you can use `git reset`.<br />
`git reset <commit-hash>` will reset the repo back to a specific commit. The commits are gone.<br />
<a href="https://git-scm.com/docs/git-reset">Git Reset Documentation</a>

```
git reset --hard <commit>
```

If you want to undo both the commits AND the actual changes in your files, you can use the `--hard` option. For example, `git reset --hard HEAD~1` will delete the last commit and associated changes.<br />

## Reverting Commits with Git Revert

```
git revert <commit-hash>
```

`git revert` is similar to `git reset` in that they both "undo" changes, but they accomplish it in different ways.<br />
`git reset` actually moves the branch pointer backwards, eliminating commits.<br />
`git revert` instead creates a brand new commit which reverses / undos the changes from a commit. Because it results in a new commit, you will be prompted to enter a commit message.<br />

<a href="https://git-scm.com/docs/git-revert">Git Revert Documentation</a><br />

<strong>Which one should I use?</strong><br />
Both `git reset` and `git revert` help us reverse changes, but there is a significant difference when it comes to collaboration.<br />
If you want to reverse some commits that other people already have on their machines, you should use revert.<br />
If you want to reverse commits that you haven't started with others, use reset and no one will ever know!<br />
