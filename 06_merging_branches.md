# Merging Branches, Oh Boy!

## An Introduction to Merging

<strong>Merging</strong><br />
Branching makes it super easy to work within self-contained contexts, but often we want to incorporate changes from one branch into another! We can do this using the `git merge` command.<br />
<a href="https://git-scm.com/docs/git-merge">Git Merge Documentation</a><br />
The merge command can sometimes confuse students early on. Remember these two merging concepts:

<ul>
  <li>We merge branches, not specific commits.</li>
  <li>We always merge to the current HEAD branch.</li>
</ul>

To merge, follow these basic steps:

<ul>
  <li>Switch to or checkout the branch you want to merge the changes into (the receiving branch).</li>
  <li>Use the git merge command to merge changes from a specific branch into the current branch.</li>
</ul>

```
git switch master
git merge bugfix
```

This is called a fast-forward since master simply caught up on the commits from Bugfix. Master and Bugfix now point to the same commit, until they diverge again.

## Generating Merge Commits

Not all merges are fast forwards. This happens all the time! Imagine one of your teammates merged in a new feature or change to master while you were working on a branch.<br />
What happens when I try to merge? Rather than performing a simple fast forward, git performs a "merge commit." We end up with a new commit on the master branch. Git will prompt you for a message.

## Resolving Merge Conflicts

Depending on the specific changes you are trying to merge, Git may not be able to automatically merge. This results in `merge conflicts`, which you need to manually resolve.

```
CONFLICT(content): Merge conflict in blah.txt
Automatic merge failed; fix conflicts and then commit the result
```

When you encounter a merge conflict, Git warns you in the console that it could not automatically merge. It also changes the contents of your files to indicate the conflicts that it wants you to resolve.

```
<<<<<<< HEAD
I have 2 cats
I also have chickens
=======
I used to have a dog :(
>>>>>>> bug-fix
```

<strong>Conflict Markers</strong><br />
The content from your current HEAD (the branch you are trying to merge content into) is displayed between the `<<<<<<<HEAD` and `=======`.<br />
The content from the branch you are trying to merge from is displayed between the `=======` and `>>>>>>>` symbols.<br />

<strong>Resolving Conflicts</strong><br />
Whenever you encounter merge conflicts, follow these steps to resolve them:

<ul>
  <li>Open up the file(s) with merge conflicts.</li>
  <li>Edit the file(s) to remove the conflicts. Decide which branch's content you want to keep in each conflict. Or keep the content from both.</li>
  <li>Remove the conflict "markers" in the document.</li>
  <li>Add your changes and then make a commit!</li>
</ul>
