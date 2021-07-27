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

**What now?**<br />
In our text editor, we will see a list of commits alongside a list of commands that we can choose from. Here are a couple of the more commonly used commands:<br />

- pick - use the commit
- reword - use the commit, but edit the commit message
- edit - use commit, but stop for amending
- fixup - use commit contents but meld it into previous commit and discard the commit message
- drop - remove commit

```
pick f7f3f6d Change my name a bit
pick 310154e Update README
pick a5f4a0d Add cat-file
```

```
drop f7f3f6d Change my name a bit
pick 310154e Update README
reword a5f4a0d Add cat-file
```
