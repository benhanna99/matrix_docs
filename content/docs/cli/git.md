---
title: "Git CLI"
description: "Get Up and Running Using GIT"
lead: "Get Up and Running Using GIT"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "cli"
weight: 140
toc: true
---

# Clone a Repo

Cloning a repo is a useful time saving tool.

We can clone a repo with ```git clone```. 

You pass a path (usually a URL) of the Git repository you want to clone to the git clone command. EG:

```

git clone  https://github.com/udacity/course-git-blog-project

```

We could also clone and rename instead:

```

git clone https://github.com/udacity/course-git-blog-project  blog-project

```

# Initialize a Repository

The **init** command initializes a new repository. The **dot** syntax does it in current working directory.  

```

git init .

```

Running the git init command sets up all of the necessary files and directories that Git will use to keep track of everything.

All of these files are stored in a directory called .git. 

The .git directory is the "repo". This is where git records all of the commits and keeps track of everything.

Other than the "hooks" directory, you shouldn't mess with pretty much any of the content in this directory.

# The Git Status Command

```git status```  will tell us what Git is thinking and the state of our repository as Git sees it.

When you're first starting out, you should be using the git status command all of the time. You should get into the habit of running it after any other command.

This will help you learn how Git works and it'll help you from making (possibly) incorrect assumptions about the state of your files/repository.


## Add File to Repository

When we want to add a file to the repo to be tracked, we use the **add** command and then the file we want to track.

```

git add index.html 

```

We get a new comand prompt back meaning it worked. If you run ```git status``` you will see we have changes ready to be committed, it will say "new file: index.html",

If we were now to create a commit the file would be included in that commit.

## Commit to Repository

A commit is a record of what the repository looked like at a given point in time.

Each commit has a message to briefly explain the changes we made.

**Commits should contain as small a set of changes as possible.**

The more commits you have, the more flexibility you have to roll back or cherry pick changes - Remember Git does not charge by commit so feel free to make as many as you need!

To create a commit we use the commit command followed by *dash* **m** and our message in quotes:

```

git commit -m "added a new file"

```

## Add all files in Current Working Directory

To add all files we use the **git add** command followed by a **dot**. The dot means the current working directory. Using ``git add  .``` we stage all the files in current directory to be committed.


```
git add .

git commit -m "A line on what changes got made"

```


## Push all files in Current Working Directory

We use ```git push``` to push the changes live. This could be done on one file, here we will do it with the whole all files in Current Working Directory:

```

git add .
git commit -m "A line on what changes got made"
git push

```

## Use Git Add & Git Commit in one step

You can do an **add and commit** at the same time to save time.

Note this will track ALL files not yet staged, so if you have files not ready to be committed just yet, this command is not recommended.

```

git commit -am "message here"

```


## Reviewing a Repo's History

Git log is basically like a journal of commits on the project we are working on.

```
git log

```

Press ``q``` to quit the log.

By default, this command displays:

- the SHA
- the author
- the date
- and the message

The most important line is usually the message.

We can condense what displays by using ```git log --oneline```  This command:

- lists one commit per line
- shows the first 7 characters of the commit's SHA
- shows the commit's message

The ```--stat``` flag is used to alter how git log displays information:

```

$ git log --stat

```

This command:

- displays the file(s) that have been modified
- displays the number of lines that have been added/removed
- displays a summary line with the total number of modified files and lines that have been added/removed


We can also use the ```-p``` flag (which is the same as the ```--patch``` flag) to alter how git log displays information:

```

git log -p

```

Finally, The ```git show``` command will show **only one commit**.

It can be combined with most of the other flags we've looked at/ 

```

git show --stat 60b6067

```

## Ignoring files with .gitignore

Sometimes we don't want to add or track a file inside a project but we still want it to live inside the project directory and we also don't want it to always show up as untracked. For example a to do list, a file other devs on the team will have that we don't want to over write like their personal notes, or a config file specific to our personal machine that may contain our passwords.

To prevent this:

Create a file in the project root called **.gitignore**

Inside here, on each line we would have the files we want to ignore, eg, something like **dev-notes.txt**


## Branches

Every Git repository has at least one branch. When you intialize a Git repository it creates a master branch. 

You can have as many branches as you want, and name them as you wish. Branches are independent of each other, but you can merge them into each other.

The current state of a branch (called Head) always references a commit object.

Always think of the state of the branch as the state of last commit. Until we commit it is not part of the branch.

## Creating Branches

A core aspect of Git is that it allows multiple developers to work on different branches at the same time.


