# Git Collaboration Workflows

## The Pitfalls of a Centralized Workflow

**Centralized Workflow**<br />
AKA everyone works on master/main<br />
AKA the most basic workflow possible<br />

The simplest collaborative workflow is to have everyone work on the master branch (or main, or any other single branch).<br />
It's straightforward amd can work for tiny teams, but it has quite a few shortcomings!<br />

**The Problem**<br />
While it's nice and easy to only work on the master branch, this leads to some serious issues on teams!<br />

- Lots of time spent resolving conflicts and merging code, especially as team size scales up.
- No one can work on anything without disturbing the main code base. How do you try adding something radically different in? How do you experiment?
- The only way to collaborate on a feature together with another teammate is to push incomplete code to master. Other teammates now have broken code..

## The All-Important Feature Branch Workflow

**Feature Branches**<br />
Rather than working directly on master/main, all new development should be done on separate branches!<br />

- Treat master/main branch as the official project history.
- Multiple teammates can collaborate on a single feature and share code back and forth without polluting the master/main branch.
- Master/main branch won't contain broken code (or at least, it won't unless someone messes up).

## Merging in Feature Branches

At some point the new work on feature branches will need to be merged in to the master branch! There are a couple of options for how to do this..<br />

- Merge at will, wihout any sort of discussion with teammates - just do it whenever you want.
- Send an email or chat message or something to your team to discuss if the changes should be merged in.
- **Pull Requests!**

## Introducing Pull Requests

Pull Requests are a feature built in to products like GitHub and Bitbucket. **They are not native to Git itself.**<br />
They allow developers to alert team-members to new work that needs to be reviewed. They provide a mechanism to approve or reject the work on a given branch. They also help facilitate discussion and feedback on the specific commits.<br />
_"I have this new stuff I want to merge in to the master branch.. what do you all think about it?"_<br />

**The Workflow**<br />

- Do some work locally on a feature branch.
- Push up the feature branch to GitHub.
- Open a pull request using the feature branch just pushed up to GitHub.
- Wait for the PR to be approved and merged. Start a discussion on the PR. This part depends on the team structure.

## Merging Pull Requests with Conflicts

Just like any other merge, **sometimes there are conflicts** that need to be resolved when merging a pull request. This is fine. Don't panic.<br />
You can perform the merhe and fix the conflicts on the command line like normal, or you can use GitHub's interative editor.<br />

- Switch to the branch in question. Merge in master and resolve the conflicts.
- Switch to master. Merge in the feature branch (now with no conflicts). Push changes up to github.

## Introducing Forking

**Fork & Clone: Another Workflow**
The "fork & clone" workflow is different from anything we have seen so far. Instead of just one centralized GitHub repository, every developer has their own GitHub repository in addition to the "main" repo. Developers make changes and push to their own forks before making pull requests.<br />
It is very commonly used on large open-source projects where there may be thousands of contributors with only a couple maintainers.<br />

**Forking**
GitHub (and similar tools) allow us to create personal copies of other people's repositories. We call those copies of "fork" of the original. When we fork a repo, we are basically asking GitHub "Make me my own copy of this repo please".<br />
As with pull requests, forking is not a Git feature. The ability to fork is implemented by GitHub.<br />

## The Fork & Clone Workflow

Now that I have forked, I have my very own copy of the repo where I can do whatever I want!<br />
I can clone my fork and make changes, add features, and break things without fear of disturbing the original repository. If I do want to share my work, I can make a pull request from my fork to the original repo.<br />

Summary:<br />

- Fork the project
- Clone the fork
- Add upstream remote
- Do some work
- Push to origin
- Open PR

This "Fork & Clone" workflow might seem complicated, but it's extremely common for good reason!<br />
It allows a project maintainer to accept contributions from developers all around the world without having to add them as actual owners of the main project repository or worry about giving them all persmission to push to the repo (which could be disastrous!).
