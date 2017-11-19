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

Staging changes is an optional intermediary step when you only want to commit some of your existing changes to the repository but not all of them. This can analogous to checking in some of your files to your local Git repository.

As an example, I'll stage one file to be committed to the database.

![VS Code Git Staged](/media/posts/up-and-running-with-git-and-vscode/vscode-git-staged.png)

`A` - indicate the file will be added to the Git repository in the next commit

Note how this file appears under a separate `STAGED CHANGES` section.

In most cases when updating this blog I just want to commit all my recent edits so I generally don't stage anything and just commit everything in one batch.

### Tip 6 - Click on the file in the `CHANGES` area to see differences made

To see what changes you've made to local files

`Label (1)` - Select the modified file from the `CHANGES` section

`Label (2)` - Navigate through the differences showing up in the left and right file panes. As you can see the right pane clearly shows the additional content I've added to the blog post.

![VS Code Git Difference](/media/posts/up-and-running-with-git-and-vscode/vscode-git-diffs.png)

### Tip 7 - How to Undo or Rollback the last commit made in VS Code

If you've accidently committed some changes to your local Git repository, you can undo these changes using the `Undo Last Commit` command:

![VS Code undo Last Commit](/media/posts/up-and-running-with-git-and-vscode/vscode-git-undo-commit.png)

`Label (1)` - Select the `Source Control` icon

`Label (2)` - Select the `More` button to bring up the additonal Git operations that can be executed from within VS Code

`Label (3)` - Select the `Undo Last Commit` command to rollback the last commit (Note: If you want to see what Git commands VS Code has sent to Git, just view the `OUTPUT` tab and filter by `Git`)

If you're completely new to VS Code and Git and want to get up and running as quickly as possible, I wholeheartedly recommend the Udemy course `Git Beginner in VS Code`. I purchased this course myself and totally recommend it if you're new to Git and VS Code on Windows or even a Mac. The information covered in the course is practical,concise and covers the essentials of usnig Git and VS Code. The instructor's teaching style is very unique and he explains what you need to know to be effective and not everything this is to know.

[![Git Beginner in VS Code Online Course](/media/posts/up-and-running-with-git-and-vscode/udemy-git-vscode.png)](/out/git-beginner-in-vs-code)








