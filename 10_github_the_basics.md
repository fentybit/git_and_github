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
