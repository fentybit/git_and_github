# The Power of Reflogs - Retrieving "Lost" Work

## Introducint Reflogs

**reflogs**<br />
Git keeps a record of when the tips of branches and other references were updated in the repo.<br />
We can view and update these reference logs using the `git reflog` command.<br />

## The Limitations of Reflogs

Git only keeps reflogs on your **local** activity. They are not shared with collaborators.<br />
Reflogs also expire. Git cleans out old entries after around 90 days, though this can be configured.<br />

## The Git Reflog Show Command

```
git reflog show HEAD
git reflog
```

The git reflog command accepts subcommands **show**, **expire**, **delete**, and **exists**. Show is the only commonly used variant, and it is the default subcommand.<br />
**git reflog show** will show the log of a specific reference (it defaults to HEAD).<br />
For example, to view the logs for the tip of the main branch we could run `git reflog show main`.<br />
[Git Reflog Documentation](https://git-scm.com/docs/git-reflog)<br />

## Passing Reflog References Around

```
name@{qualifier}
```

We can access specific git refs is `name@{qualifier}`. We can use this syntax to access specific ref pointers and can pass them to other commands including checkout, reset, and merge.<br />

## Time-Based Reflog Qualifiers

```
git reflog master@{one.week.ago}
git checkout bugfix@{2.days.ago}
git diff main@{0} main@{yesterday}
```

Every entry in the reference logs has a timestamp associated with it. We can filter reflogs entries by time/date by using time qualifiers like:

- 1.day.ago
- 3.minutes.ago
- yesterday
- Fri, 12 Feb 2021 14:06:21-0800

## Rescuing Lost Commits with Reflog

**Reflogs Rescue**<br />
We can sometimes use reflog entries to access commits that seem lost and are not appearing in git log.<br />
