# Commits in Detail (and Related Topics)

## Navigating the Git Documentation

https://git-scm.com/docs

## Atomic Commits

When possible, a commit should encompass a single feature, change or fix. In other words, try to <strong>keep each commit focused on a single thing</strong>. This makes it much easier to undo or rollback changes later on. It also makes your code or project easier to review.

## Commit Messages: Present or Past Tense?

Present or past tense? Does it really matter?<br />
<strong><a href="https://medium.com/@corrodedlotus/which-tense-should-be-used-on-a-git-commit-message-121cb641134b">Present-Tense Imperative Style</a></strong>. Describe your changes in imperative mood, e.g. "make xyz do xyz" instead of "[This patch] makes xyz do xyz" or "I change xyz to do xyz", as if you are giving orders to the codebase to change its behavior.<br />
Though the Git docs suggest using present-tense imperative messages, many developers prefer to use past-tense messages. All that matters is consistency, especially when working on a team with many people making commits.

## Escaping VIM & Configuring Git's Default Editor

<a href="https://git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config">Git Commands - Setup and Config</a>

## A Closer Look at the Git Log Command

<a href="https://git-scm.com/docs/git-log">Git Log Documentation</a>

## Fixing Mistakes with Amend

<strong>Amending Commits</strong><br />
Suppose you just made a commit and then realized you forgot to include a file! Or, maybe you made a typo in the commit message that you want to correct. Rather than making a brand new separate commit, you can "redo" the previous commit using the `--amend` option.<br />
<a href="https://git-scm.com/docs/git-commit">Git Commit Documentation</a><br />

```
git commit -m "some commit"
git add forgotten_file
git commit --amend
```

## Ignoring Files with `.gitignore`

<strong>Ignoring Files</strong><br />
We can tell Git which files and directories to ignore in a given repository, using a `.gitignore` file. This is useful for files you know you NEVER want to commit, including:<br />
<a href="https://git-scm.com/docs/gitignore">Git Ignore Documentation</a><br />

<ul>
  <li>Secrets, API keys, credentials, etc.</li>
  <li>Operating System files (.DS_Store on Mac)</li>
  <li>Log files</li>
  <li>Dependencies & packages</li>
</ul>

<a href="https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files">GitHub Ignoring Files Documentation</a><br />

<strong>`.gitignore`</strong><br />
Create a file called `.gitignore` in the root of a repository. Inside the file, we can write patterns to tell Git which files and folders to ignore:<br />

<ul>
  <li>.DS_Store will ignore files named .DS_Store</li>
  <li>folderName/ will ignore an entire directory</li>
  <li>*.log will ignore any files with the .log extension</li>
</ul>
