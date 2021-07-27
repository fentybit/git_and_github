# Git Behind The Scenes - Hashing & Objects

## Working with the Local Config File

**config**<br />
The config file is for.. configuration. We have seen how to configure global settings like our name and email across all Git repos, but we can also configure things on a per-repo basis.<br />
[Git Config Documentation](https://git-scm.com/docs/git-config)<br />

## Inside Git: The Refs Directory

**Refs Folder**<br />
Inside of refs, you will find a heads directory. `refs/heads` contains one file per branch in a repository. Each file is named after a branch and contains the hash of the commit at the tip of the branch.<br />
For example `refs/heads/master` contains the commit hash of the last commit on the master branch.<br />
Refs also contains a `refs/tags` folder which contains one file for each tag in the repo.<br />

## Inside Git: The HEAD File

**HEAD**<br />
HEAD is just a text file that keeps track of where HEAD points.<br />
If it contains refs/heads/master, this means that HEAD is pointing to the master branch.<br />
In detached HEAD, the HEAD file contains a commit hash instead of a branch reference.<br />

## Inside Git: The Objects Directory

**Objects Folder**<br />
The objects directory contains all the repo files. This is where Git stores the backups of files, the commits in a repo, and more.<br />
The files are all compressed and encrypted, so they won't look like much!<br />
There are 4 types of Git objects: commit, tree, blob and annotated tag.<br />

## A Crash Course on Hashing Functions

**Hashing Functions**<br />
Hashing functions are functions that map input data of some arbitrary size to fixed-size output values.<br />

**Cryptographic Hash Functions**<br />

- One-way function which is infeasible to invert
- Small change in input yields large change in the output
- Deterministic - same input yields same output
- Unlikely to find 2 outputs with same value

**SHA-1**<br />
Git uses a hashing function called SHA-1 (though this is set to change eventually).<br />

- SHA-1 always generates 40-digit hexadecimal numbers
- The commit hashes we have seen a million times are the output of SHA-1

## Git as a Key-Value Datastore

**Git Database**<br />
Git as a **key-value data store**. We can insert any kind of content into a Git repository, and Git will hand us back a unique key we can later use to retrieve that content. These keys that we get back are SHA-1 checksums.<br />

## Hashing with Git Hash-Object

```
echo 'hello' | git hash-object --stdin
```

The `--stdin` option tells git hash-object to use the content from stdin rather than a file. In our example, it will hash the word 'hello'.<br />
The echo command simply repeats whatever we tell it to repeat to the terminal. We pipe the output of echo to `git hash-object`.<br />

```
git hash-object <file>
```

The `git hash-object` command takes some data, stores in our .git/objects directory and gives us back the unique SHA-1 hash that refers to that data object.<br />
In the simplest form (shown on the right), Git simply takes some content and returns the unique key that WOULD be used to store our object. But it does not actually store anything.<br />
[Git Hash-Object Documentation](https://git-scm.com/docs/git-hash-object)<br />

## Retrieving Data with Git Cat-File

```
git cat-file -p <object-hash>
```

Now that we have data stored in our Git object database, we can try retrieving it using the git cat-file command.<br />
The `-p` option tells Git to pretty print the contents of the object based on its type.<br />
[Git Cat-File Documentation](https://git-scm.com/docs/git-cat-file)

## Deep Dive into Git Objects: Blobs

**Blobs**<br />
Git blobs (binary large object) are the object type Git uses to store the **contents of files** in a given repository. Blobs don't even include the filenames of each file or any other data. They just store the contents of a file!<br />

## Deep Dive into Git Objects: Trees

**Trees**<br />
Trees are Git objects used to store the contents of a directory. Each tree contains pointers that can refer to blobs and to other trees.<br />
Each entry in a tree contains the SHA-1 hash of a blob or tree, as well as the mode, type, and filename.<br />

```
git cat-file -p master^{tree}
```

Remember that `git cat-file` prints out Git objects. In this example, the `master^{tree}` syntax specifies the tree object that is pointed to by the tip of our master branch.<br />

## Deep Dive into Git Objects: Commits

**Commits**<br />
Commit objects combine a tree object along with information about the context that led to the current tree. Commits store a reference to parent commit(s), the author, the committer, and of course the commit message!<br />
When we run git command, Git creates a new commit object whose parent is the **current HEAD commit** and whose tree is the current content of the index.<br />
