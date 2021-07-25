# Cleaning Up History with Interactive Rebase

## Introducing Interactive Rebase

**Rewriting History**<br />
Sometimes we want to rewrite, delete, rename or even re-order commits (before sharing them).<br />
We can do this using `git rebase`!<br />

**Interactive Rebase**<br />

```
git rebase -i HEAD~4
```

Running git rebase with the -i option will enter the interactive mode, which allows us to edit commits, add files, drop commits, etc. Note that we need to specify how far back we want to rewrite commits.<br />
Also, notice that we are not rebasing onto another branch. Instead, we are rebasing a series of commits onto the HEAD they currently are based on.<br />
