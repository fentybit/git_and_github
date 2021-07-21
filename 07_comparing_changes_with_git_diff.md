# Comparing Changes with Git Diff

## Introducing the Git Diff Command

<strong>Git Diff</strong><br />
We can use the `git diff` command to view changes between commits, branches, files, our working directory, and more! We often use git diff alongside commands like `git status` and `git log`, to get a better picture of a repository and how it has changed over time.<br />
Without additional options, `git diff` lists all the changes in our working directory that are NOT staged for the next commit, <a href="https://git-scm.com/docs/git-diff">comparing staging area and working directory</a>.<br />

<strong>Compared Files</strong><br />
For each comparison, Git explains which files it is comparing. Usually this is two versions of the same file. Git also declares one file as "A" and the other as "B".<br />

<strong>File Metadata</strong><br />
You really do not need to care about the file metadata. The first two numbers are the hashes of the two files being compared. The last number is an internal file mode identifier.<br />

<strong>Markers</strong><br />
File A and File B are each assigned a symbol.

<ul>
  <li>File A gets a minus sign (-)</li>
  <li>File B gets a plus sign (+)</li>
</ul>

<strong>Chunks</strong><br />
A diff won't show the entire contents of a file, but instead only shows portions or "chunks" that were modified. A chunk also includes some unchanged lines before and after a change to provide some context.<br />

<strong>Changes</strong><br />
Every line that changed between the two files is marked with either a + or - symbol. Lines that begin with `-` come from file A. Lines that begin with `+` come from file B.<br />

## Viewing Working Directory Changes

`git diff HEAD` lists all changes in the working tree since your last commit.

## Viewing Staged Changes

`git diff --staged` or `--cached` will list the changes between the staging area and our last commit. "Show me what will be included in my commit if I run git commit right now."

## Diffing Specific Files

We can view the changes within a specific file by providing git diff with a filename.

```
git diff HEAD [filename]
git diff --staged [filename]
```

## Comparing Changes Across Branches

`git diff branch1..branch2` or `git diff branch1 branch2` will list the changes between the tips of branch1 and branch2.
`git diff branch1 branch2 [filename]` will list the changes in `[filename]` comparing `branch1` and `branch2`.

## Comparing Changes Across Commits

To compare two commits, provide git diff with the commit hashes of the commits in question.

```
git diff commit1..commit2
```
