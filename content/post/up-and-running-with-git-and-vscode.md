---
title: "Up and Running with Git and VS Code"
date: 2017-11-18T18:05:43+10:00
author: "Peter Puglisi"
tags: ["Git", "VS Code"]
---

## Up and Running with Git and VS Code

Developer tools and plugins are intended to make developers more productive. Git and VS Code are the 2 main tools I use to update content for adaptiveprogrammer.com. In this post I'll outline some of the core things you need to know about using Git and VS Code. 

### Tip 1: VS Code's Terminal Tab

VSCode has a Terminal tab that can be used instead of a command prompt box (on Windows) or Terminal window (on Mac).

To invoke the Terminal tab, select `View -> Integrated Terminal` or ``Ctrl +`` 

Select the 'TERMINAL' tab.

![VS Code Terminal Tab](/media/posts/up-and-running-with-git-and-vscode/vscode-terminal.png)

Running `git --version` will verify if Git is already installed.


### Tip 2: How to install Git on Windows

* Setup a Github acccount.

* Download the windows 32 bit or 64 bit version of Git tools from [https://git-scm.com](https://git-scm.com/).

### Tip 3: How to fix "Failed to execute Git" errors

If it's the first time you're using Git with VS Code and haven't used Git before from the command line, you may get "Failed to execute Git" error. Clicking on the `OUTPUT` tab and filter the output on `Git`.

If you see some message about `git config --global ...` etc., it means you need to configure your Git identity so that the command line interface can pass these credentials to github.com and interact with Git successfully.

You'll need to run the commands below from the `TERMINAL` window using your Git credentials from your github.com account. 

```
git config --global user.email "peter@peterpuglisi.com"
git config --global user.name "Peter Puglisi"
git config --global user.password "??????????"
```

### Tip 4: How to interact with Git from the VS Code menu

If you click on the branch icon near the `(1)` label below, VS Code will bring up the Git status for files you've modified locally:

![VS Code Source Control](/media/posts/up-and-running-with-git-and-vscode/vscode-git-source-control.png)

Note the status of each file is shown on the right as highlighted by the `(2)` label. We can see 3 types of status indiators - `U`, `D` and `M` where

`U` - indicated untracked items in our working tree (i.e local workpace files). These are new files that Git has detected but not committed to the local repository as yet.

`D` - indicated files that have been deleted from the local Git repository

`M` - indicates files that been modified in my local workspace

### Tip 5 - Staging and unstaging changes 

Staging changes is an intermediary step when you only want to commit some of your existing changes to the repository but not all of them. This can analogous to checking in some of your files to your local Git repository.

As an example, I'll stage one file to be committed to the database.

![VS Code Git Staged](/media/posts/up-and-running-with-git-and-vscode/vscode-git-staged.png)

`A` - indicate the file will be added to the Git repository in the next commit

Note how this filw appears under a separate `STAGED CHANGES` section.

