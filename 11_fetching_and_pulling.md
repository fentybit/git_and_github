# Fetching and Pulling

## Remote Tracking Branches

When you `git clone` a GitHub repo to your personal computer, it will clone the `master` branch.<br />
This is a <strong>Remote Tracking Branch</strong>. It is a reference to the state of the master branch on the remote. I can't move this myself. It's like a bookmark pointing to the last known commit on the master branch on origin.<br />

"At the time you last communicated with this remote repository, here is where x branch was pointing."<br />

They follow this pattern `<remote>/<branch>`.

<ul>
  <li>origin/master references the state of the master branch on the remote repo named origin.</li>
  <li>upstream/logoRedesign references the state of the logoRedesign branch on the remote named upstream (a common remote name).</li>
</ul>

<strong>Remote Branches</strong><br />

```
git branch -r origin/master
```

Run `git branch -r` to view the remote branches our local repository knows about.

## Checking Out Remote Tracking Branches

When I run `git status`..

```
git status
  On branch master
  Your branch is ahead of 'origin/master' by 2 commits
  (use "git push" to publish your local commits)
```

You can checkout these remote branch pointers..

```
git checkout origin/master
  Note: switching to 'origin/master'
  You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this...
```

## Working with Remote Branches

<strong>Remote Branches</strong><br />

```
git branch
  *master
```

Once you have cloned a repository, we have all the data and Git history for the project at that moment in time. However, that does not mean it is all in my workspace!<br />
The GitHub repo has a branch called `puppies`, but when I run `git branch` I don't see it on my machine! All I see if the master branch. What's going on?

```
git branch -r
  origin/master
  origin/puppies
```

Run `git branch -r` to view the remote branches our local repository knows about.<br />

If I want to work on the puppies branch locally..<br />
I could `git checkout origin/puppies`, but that puts me in detached HEAD. I want my own local branch called `puppies`, and I want it to be connected to `origin/puppies`, just like my local `master` branch is connected to `origin/master`.<br />

```
git switch puppies
  Branch 'puppies' set up to track remote branch 'puppies' from 'origin'
  Switched to a new branch 'puppies'
```

Run `git switch <remote-branch-name>` to create a new local branch from the remote branch of the same name.<br />
`git switch puppies` makes me a local puppies branch AND sets it up to track the remote branch `origin/puppies`.<br />

The new command `git switch` makes this super easy to do. It used to be slightly more complicated using `git checkout`.<br />

```
git checkout --track origin/puppies
```

## Git Fetch: The Basics

Fetching allows us to download changes from a remote repository, BUT those changes will not be automatically integrated into our working files.<br />
It lets you see what others have been working on, without having to merge those changes into your local repo. Think of it as "please go and get the latest information from GitHub, but don't screw up my working directory."<br />

```
git fetch <remote>
```

If not specified, <remote> defaults to `origin`. The `git fetch <remote>` command fetches branches and history from a specific remote repository. It only updates remote tracking branches.<br />
`git fetch origin` would fetch all changes from the origin remote repository.<br />

```
git fetch <remote> <branch>
```

We can also fetch a specific branch from a remote using `git fetch <remote> <branch>`.<br />
For example, `git fetch origin master` would retrieve the latest information from the master branch on the origin remote repository.<br />

## Git Pull: The Basics

`git pull` is another command we can use to retrieve changes from a remote repository. Unlike fetch, pull actually updates our HEAD branch with whatever changes are retrieved from the remote.<br />
"go and download data from GitHub AND immediately update my local repo with those changes."<br />

`git pull = git fetch + git merge`<br />

```
git pull <remote> <branch>
git pull origin master
```

To pull, we specify the particular remote and branch we want to pull using `git pull <remote> <branch>`. Just like with git merge, it matters WHERE we run this command from. Whatever branch we run it from is where the changes will be merged into.<br />
`git pull origin master` would fetch the latest information from the origin's master branch and merge those changes into our current branch.<br />

## Git Pull and Merge Conflicts

Pulls can result in merge conflicts!<br />
I have a commit locally that isnot on GitHub. When I pulled, it was merged with the new commits. As with any other merge, this can result in merge conflicts.<br />

## A Shorter Syntax for Git Pull

```
git pull
```

If we run `git pull` without specifying a particular remote or branch to pull from, git assumes the following:

<ul>
  <li>Remote will default to origin</li>
  <li>Branch will default to whatever tracking connection is configured for your current branch</li>
</ul>

Note:<br />
This behavior can be configured, and tracking connections can be changed manually. Most people don't mess with that stuff.<br />

When I am on my local `master` branch, `git pull` pulls from `origin/master` automatically.<br />
When I am on my local `puppies` branch, `git pull` pulls from `origin/puppies` automatically.<br />

<strong>git fetch</strong><br />

<ul>
  <li>Gets changes from remote branch(es)</li>
  <li>Updates the remote-tracking branches with the new changes</li>
  <li>Does not merge changes onto your current HEAD branch</li>
  <li>Safe to do at anytime</li>
</ul>

<strong>git pull</strong><br />

<ul>
  <li>Gets changes from remote branch(es)</li>
  <li>Updates the current branch with the new changes, merging them in</li>
  <li>Can result in merge conflicts</li>
  <li>Not recommended if you have uncommitted changes!</li>
</ul>
