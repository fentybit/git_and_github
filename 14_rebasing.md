# Rebasing: The Scariest Git Command?

## Why is Rebasing Scary? Is it?

It is actually very useful, as long as you know when NOT to use it!<br />
There are two main ways to use the git rebase command:<br />

- as an alternative to merging
- as a cleanup tool

## Comparing Merging & Rebasing

If merging, the feature branch has a bunch of merge commits. If the master branch is very active, my feature branch's history is muddied.<br />

**Rebasing!**
We can instead rebase the feature branch onto the master branch. This moves the entire feature branch so that it BEGINS at the tip of the master branch. All of the work is still there, but **we have re-written history**.<br />
Instead of using a merge commit, rebasing rewrites history by **creating new commits** for each of the original feature branch commits.

```
git switch feature
git rebase master
```

We can also wait until we are done with a feature and then rebase the feature branch onto the master branch.<br />

[Git Rebase Documentation](https://git-scm.com/docs/git-rebase)

## The Golden Rule: When NOT to Rebase

**Why Rebase?**<br />
We get a much cleaner project history. No unnecessary merge commits! We end up with a linear project history.<br />

**WARNING!**<br />
Never rebase commits that have been shared with others. If you have already pushed commits up to GitHub.. DO NOT rebase them unless you are positive no one on the team is using those commits.<br />
You do not want to rewrite any git history that other people already have. It is a pain to reconcile the alternate histories!<br />
