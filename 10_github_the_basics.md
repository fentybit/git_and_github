# GitHub: The Basics

## What is GitHub?

GitHub is a hosting platform for git repositories. You can put your own Git repos on GitHub and access them from anywhere and share them with people around the world.<br />
Beyond hosting repos, GitHub also provides additional collaboration features that are not active to Git (but are super useful). Basically, GitHub helps people share and collaborate on repos.<br />
GitHub is not your only option.. There are tons of competing tools that provide similar hosting and collaboration features, including GitLab, BitBucket and Gerrit. GitHub was founded in 2008, GitHub is now <strong>the world's largest host of source code</strong>. In early 2020, GitHub reported having over 40 million users and over 190 million repositories on the platform. It is free. GitHub offers basic services for free! While GitHub does offer paid Team and Enterprise tiers, the basic Free tier allows for unlimited public and private repos, unlimited collaorators and more!<br />

<strong>Why you should use GitHub?</strong><br />

<ul>
  <li><strong>Collaboration.</strong> If you ever plan on working on a project with at least one other person, GitHub will make your life easier! Whether you are building a hobby project with your friend or you are collaborating with the entire world, Github is essential!</li>
  <li><strong>Open Source Projects.</strong> Today GitHub is THE home of open source projects on the internet. Project ranging from React to Swift are hosted on GitHub. If you plan on contributing to open source projects, you will need to get comfortable working with GitHub.</li>
  <li><strong>Exposure.</strong> Your GitHub profile showcases your own projects and contributions to others' projects. It can act as a sort of resume that many employers will consult in the hiring process. Additionally, you can gain some clout on the platform for creating or contributing to popular projects.</li>
  <li><strong>Stay Up To Date.</strong> Being active on GitHub is the best way to stay up to date with the projects and tools you rely on. Learn about upcoming changes and the decisions/debate behind them.</li>
</ul>

## Cloning GitHub Repos with Git Clone

So far we have created our own Git repositories from scratch, but often we want to get a <strong>local copy of an existing repository</strong> instead. To do this, we can clone a remote repository hosted on GitHub or similar websites. All we need is a URL that we can tell Git to clone for use.<br />
<a href="https://git-scm.com/docs/git-clone">Git Clone Documentation</a><br />

```
git clone <url>
```

Make sure you are not inside of a repo when you clone! To clone a repo, simply run `git clone <url>`. Git will retrieve all the files associated with the repository and will copy them to your local machine. In addition, Git initializes a new repository on your machine, giving you access to the full Git history of the cloned project.

## Cloning Non-GitHub Repos

<strong>Permissions?</strong><br />
Anyone can clone a repository from GitHub, provided the repo is public. You do not need to be an owner or collaborator to clone the repo locally to your machine. You just need the URL from GitHub. Pushing up your own changes to the GitHub repo.. that's another story entirely. You need permission to do that!<br />

<strong>We are not limited to GitHub Repos!</strong><br />
`git clone` is a standard git command.<br />
It is NOT tied specifically to GitHub. We can use it to clone repository that are hosted anywhere! It just happens that most of the hosted repos are on GitHub these days.

## GitHub Setup: SSH Config

<strong>SSH Keys</strong><br />
You need to be authenticated on GitHub to do certain operations, like pushing up code from your local machine. Your terminal will prompt you every single time for your GitHub email and password, unless..<br />
You generate and configure an SSH key! Once configured, you can connect to GitHub without having to supply your username/password.<br />

<a href="https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh">Connecting to GitHub with SSH</a><br />

## Creating Our First GitHub Repo!

<strong>Option 1: Existing Repo</strong><br />
If you already have an existing repo locally that you want to get on GitHub..

<ul>
  <li>Create a new repo on GitHub</li>
  <li>Connect your local repo (add a remote)</li>
  <li>Push up your changes to GitHub</li>
</ul>

<strong>Option 2: Start From Scratch</strong><br />
If you haven't begun work on your local repo, you can...

<ul>
  <li>Create a brand new repo on GitHub</li>
  <li>Clone it down to your machine</li>
  <li>Do some work locally</li>
  <li>Push up your changes to GitHub</li>
</ul>

## A Crash Course on Git Remotes

<strong>Remote</strong><br />
Before we can push anything up to GitHub, we need to tell Git about our remote repository on GitHub. We need to setup a "destination" to push up to.<br />
In Git, we refer to these "destinations" as remotes. Each remote is simply a URL where a hosted repository lives.<br />

<strong>Viewing Remotes</strong><br />

```
git remote -v
```

To view any existing remotes for your repository, we can run `git remote` or `git remote -v` (verbose, for more info). This just displays a list of remotes. If you haven't added any remotes yet, you won't see anything!<br />

<strong>Adding a New Remote</strong><br />
A remote is really two things: a URL and a label.<br />
To add a new remote, we need to provide both to Git.<br />

```
git remote add <name> <url>
git remote add origin https://github.com/blah/repo.git
```

The example above is when we use the name `origin`, we are referring to this particular GitHub repo URL.<br />

<strong>Origin?</strong><br />
Origin is a conventional Git remote name, but it is not at all special. It is just a name for a URL.<br />
When we clone a GitHub repo, the default remote name setup for us is called origin. You can change it. Most people leave it.<br />

<strong>Checking our Work</strong><br />

Try viewing your remotes with `git remote -v`, and you should now see a remote showing up!
Remember, by setting up a remote we are just telling Git about a remote repository URL. We have not "communicated" with the GitHub repo at all yet.<br />

<strong>Other Commands</strong><br />
They are not commonly used, but there are commands to rename and delete remotes if needed.

```
git remote rename <old> <new>
git remote remove <name>
```

## Introducing Git Push

<strong>Pushing</strong><br />

```
git push <remote> <branch>
```

Now that we have a remote set up, let's push some work up to GitHub! To do this, we need to use the `git push` command.<br />
We need to specify the remote we want to push up to AND the specific local branch we want to push up to that remote.<br />

```
git push origin master
```

`git push origin master` tells git to push up the master branch to our origin remote.<br />
<a href="https://git-scm.com/docs/git-push">Git Push Documentation</a><br />

<strong>Push In Detail</strong><br />

```
git push <remote> <local-branch>:<remote-branch>
git push origin pancake:waffle
```

While we often want to push a local branch up to a remote branch of the same name, we do not have to!<br />
To push our local pancake branch up to a remote branch called waffle we could do: `git push origin pancake:waffle`.<br />

<strong>What does `git push -u` mean?</strong><br />

```
git push -u origin master
git push --set-upstream origin master
```

The -u option allows us to set the upstream of the branch we are pushing. You can think of this as a link connecting our local branch to a branch on GitHub.<br />
Running `git push -u origin master` sets the upstream of the local master branch so that it tracks the master branch on the origin repo.<br />
What this means.. Once we have set the upstream for a branch, we can use the `git push` shorthand which will push our current branch to the upstream.<br />
