# Working with Branches

## Introducing Branches

Each commit has a hash, parent's hash reference, and message.<br />
<strong>Contexts</strong><br />
On large projects, we often work in multiple contexts:

<ul>
  <li>You are working on 2 different color scheme variations for your website at the same time, unsure of which you like best.</li>
  <li>You are also trying to fix a horrible bug, but it's proving tough to solve. You need to really hunt around and toggle some code on and off to figure it out.</li>
  <li>A teammate is also working on adding a new chat widget to present at the next meeting. It is unclear if your company will ned up using it.</li>
  <li>Another coworker is updating the search bar autocomplete.</li>
  <li>Another developer is doing an experimental radical design overhaul of the entire layout to present next month.</li>
</ul>

<strong>Branches</strong><br />
Branches are an essential part of Git!<br />
Think of branches as alternative timelines for a project. They enable us to create separate contexts where we can try new things, or even work on multiple ideas in parallel. If we make changes on one branch, they do not impact the other branches (unless e merge the changes).

## The Master Branch (or is it Main?)

```
on branch master
nothing to commit, working tree clean
```

<strong>The Master Branch</strong><br />
In git, we are always working on a branch* The default branch name is <strong>master</strong>. It does not do anything special or have fancy powers. It's just like any other branch. <em>*technically that's not 100% true as we'll see later</em><br />
<strong>Master</strong><br />
Many people designate the master branch as their "source of truth" or the "official branch" for their codebase, but that is left to you to decide. From Git's perspective, the master branch is just like any other branch. It does not have to hold the "master copy" of your project.<br />
In 2020, GitHub renamed the default branch from <strong>master</strong> to <strong>main</strong>. The default Git branch name is still <strong>master</strong>, though the Git team is exploring a potential change.

## What on earth is HEAD?

<strong>HEAD</strong><br />
We will often come across the term HEAD in Git. HEAD is simply a pointer that refers to the current "location" in your repository. It points to a particular branch reference. So far, HEAD always points to the latest commit you made on the master branch, but soon we will see that we can move around and HEAD will change!<br />
<strong>Viewing all branches with Git Branch</strong><br />
Use `git branch` to view your existing branches. The default branch in every git repo is master, though you can configure this. Look for the \* which indicates the branch you are currently on.<br />
<a href="https://git-scm.com/docs/git-branch">Git Branch Documentation</a>

```
git branch
```

## Creating and Switching Branches

<strong>Creating Branches</strong><br />
Use `git branch <branch-name>` to make a new branch based upon the current HEAD. This just creates the branch. It does not switch you to that branch (the HEAD stays the same).

```
git branch <branch-name>
```

<strong>Switching Branches</strong><br />
Once you have created a new branch, use `git switch <branch-name>` to switch to it. The HEAD will now switch to this selected branch.<br />
<a href="https://git-scm.com/docs/git-switch">Git Switch Documentation</a>

## Another Option: Git Checkout vs. Git Switch

<strong>Another way of switching??</strong><br />
Historically, we used `git checkout <branch-name>` to switch branches. This still works. The `checkout` command does a million additional things, so the decision was made to add a standalone switch command which is much simpler. You will see older tutorials and docs using checkout rather than switch. Both now work.<br />
<a href="https://git-scm.com/docs/git-checkout">Git Switch Documentation</a><br />

```
git checkout <branch-name>
```

<strong>Creating and Switching</strong><br />
Use `git switch` with the `-c` flag to create a new branch AND switch to it all in one go. Remember `-c` as short for "create".

```
git switch -c <branch-name>
```

## Delete and Renaming Branches

```
git branch -d <branch-name>
git branch -m <new-branch-name>
```

## How Git stores HEAD & Branches

<strong>HEAD</strong><br />
We will often come across the term HEAD in Git.<br />
HEAD is simply a pointer that refers
