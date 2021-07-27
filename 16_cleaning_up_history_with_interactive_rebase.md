# Git Tags: Marking Important Moments in History

## The Idea behind Git Tags

**Git Tags**<br />
Tags are pointers that refer to particular points in Git history. We can mark a particular moment in time with a tag. Tags are most often used to mark version releases in projects (v4.1.0, v4.1.1, etc.).<br />
Think of tags as branch references that do NOT CHANGE. Once a tag is created, it always refers to the same commit. It's just a label for a commit.<br />

**The Two Types**<br />
There are two types of Git tags we use: lightweight and annotated tags.<br />

- _lightweight tags_ are.. lightweight. They are just a name/label that points to a particular commit.
- _annotated tags_ store extra meta data including the author's name and email, the date, and a tagging message (like a commit message).

## A Side Note on Semantic Versioning

**Semantic Versioning**<br />
The semantic versioning spec outlines a standardized versioning system for software releases. It provides a consistent way for developers to give meaning to their software releases (how big of a change is this release??).<br />
Versions consist of three numbers separated by periods.<br />
[Semantic Versioning Documentation](https://semver.org/)<br />

**Initial Release**<br />
Typically, the first release is _1.0.0_<br />

**Patch Release**<br />
Patch releases normally do not contain new features or significant changes. They typically signify bug fixes and other changes that do not impact how the code is used. _1.0.1_<br />

**Minor Release**<br />
Minor releases signify that new features or functionality have been added, but the project is still backwards compatible. No breaking changes. The new functionality is optional and should not force users to rewrite their own code. _1.1.0_<br />

**Major Release**<br />
Major releases signify significant changes that is no longer backwards compatible. Features may be removed or changed substantially. _2.0.0_<br />

## Viewing & Searching Tags

**Viewing Tags**<br />

```
git tag
git tag -l
```

`git tag` will print a list of all the tags in the current repository.<br />

```
git tag -l "*beta*"
```

We can search for tags that match a particular pattern by using `git tag -l` and then passing in a wildcard pattern. For example, `git tag -l "*beta*"` will print a list of tags that include "beta" in their name.<br />
[Git Tag Documentation](https://git-scm.com/docs/git-tag)<br />

## Comparing Tags with Git Diff

**Checking Out Tags**<br />

```
git checkout <tag>
```

To view the state of a repo at a particular tag, we can use `git checkout <tag>`. This puts us in a detached HEAD!<br />

## Creating Lightweight Tags

```
git tag <tagname>
```

To create a lightweight tag, use `git tag <tagname>`.<br />
By default, Git will create the tag referring to the commit that HEAD is referencing.<br />

## Creating Annotated Tags

```
git tag -a <tagname>
```

Use `git tag -a` to create a new annotated tag. Git will then open your default text editor and prompt you for additional information.<br />
Similar to git commit, we can also use the `-m` option to pass a message directly and forgo the opening of the text editor.<br />

## Tagging Previous Commits

```
git tag <tagname> <commit>
```

So far we have seen how to tag the commit that HEAD references. We can also tag an older commit by providing the commit hash: `git tag -a <tagname> <commit-hash>`<br />

## Replacing Tags with Force

```
git tag -f <tagname>
```

Git will yell at us if we try to reuse a tag that is already referring to a commit. If we use the `-f` option, we can FORCE our tag through.<br />

## Deleting Tags

```
git tag -d <tagname>
```

To delete a tag, use `git tag -d <tagname>`.<br />

## Pushing Tags

```
git push --tags
```

By default, the `git push` command does not transfer tags to remote servers. If you have a lot of tags that you want to push up at once, you can use the --tags option to the `git push` command. This will transfer all of your tags to the remote server that are not already there.<br />
