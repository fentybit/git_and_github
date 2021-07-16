# The Very Basics of Git: Adding & Committing

## What is Repository?

<strong>A Git "Repo" is a workspace which tracks and manages files within a folder.</strong> Anytime we want to use Git with a project, app, etc we need to create a git repository. We can have as many repos on our machine as needed, all with separate histories and contents.

```
git --version
git log
```

## Git Init and Git Status

`git status` gives information on the current status of a git repository and its contents. It's very useful, but at the moment we don't have any repos to check the status of.<br />

Use `git init` to create a new git repository. Before we can do anything git-related, we must initialize a repo first! This is something you do once per project. Initialize the repo in the top-level folder containing your project.

## The Mysterious `.git` Folder

This will be in the folder where you initialize `git`. There is a lot more stuff inside of the `.git` folder.

## A Common Early Git Mistake

Git tracks a directory and all nested subdirectories.<br />
Do not init a repo inside of a repo! Before running `git init`, use `git status` to verify that you are not currently inside of a repo.

## The Committing Workflow Overview

<strong>Work On Stuff</strong><br />
Make new files, edit files, delete files, etc.<br />
<strong>Add Changes</strong><br />
Group specific changes together, in preparation of committing.<br />
<strong>Commit</strong><br />
Commit everything that was previously added.<br />

## Staging Changes with Git Add

<strong>Adding</strong><br />
We use the `git add` command to stage changes to be committed. It's a way of telling Git, "please include this change in our next commit". Use `git add` to add specific files to the staging area. Separate files with spaces to add multiple at once.

```
git add file1 file2
```

You can use `git add .` to stage all changes at once.

## Git Commit

We use the `git commit` command to actually commit changes from the staging area. When making a commit, we need to provide a commit message that summarizes the changes and work snapshotted in the commit.<br />

```
git commit
```

Running `git commit` will commit all staged changes. It also opens up a text editor and prompts you for a commit message. This can be overwhelming when you are starting out, so instead you can use..<br />
The -m flag allows us to pass in an inline commit message, rather than launching a text editor.<br />

```
git commit -m "my message"
```
