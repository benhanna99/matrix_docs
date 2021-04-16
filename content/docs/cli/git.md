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

To add all files we use the **git add** command followed by a **dot**. The dot means the current working directory. Using ```git add  .``` we stage all the files in current directory to be committed.


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

If you run the command ```git branch``` it will give you a list of available branches.

## Creating Branches

A core aspect of Git is that it allows multiple developers to work on different branches at the same time.

The core reason we use branches is to keep changes isolated and away from the master branch. The master branch is the branch we will have ready to deploy, if we anted to add a new feature we would **branch** off master and then **merge** back in when we are done.

To create a new branch we run the command ```git branch``` followed by the name we will give it - a common naming convention is to prefix your name to the name of the branch:

```

git branch bernard_my_new_branch

```

## Switch Branch

To switch to this branch we use the ```checkout``` command:

```

git checkout bernard_my_new_branch

```

Now we can't impact the master branch until we merge branches.

## Merge Branches

Make sure all changes are committed before merging, using ```git status```.

We should have a clean, working tree.

We should then ```git checkout master``` before merging. Its important to **checkout** the branch we are merging INTO.

Now we are on the master branch. we can check the state of this again using ```git status```.

Now we run ```git merge``` followed by the branch we are merging, and a message:

```

git merge bernard_my_new_branch -m "first merge"

```


## Set up a Remote Repository

Here we would have multiple people collaborating on a project, working locally, and pushing changes to a server where the project lives with ```git push```

To pull down a repository with commits that others have pushed up we would use ```git pull```

After setting up a repository in github we would connect to it by copying the SSH address under "quick set up", and giving the remote a nmae, in the below example its **origin**.

```
git remote add origin REPLACE_WITH_URL_WE_GOT_FROM_GIT_HUB.git

```

Its possible to set up multiple remotes. 

To check what remote we are on, we can use ```git remote```


## Push to a Remote Repository

To push all changes to the remote we set up we use ```git push``` followed by the name of the remote and then name of the branch we are pushing. If we don't specify the branch, git will push all available branches.

```

git push origin master

```

If you get a fatal error "...no upstream branch" we can set one with ```git push --set-upstream origin master```

# Clone Remote Repository

You can get the URL of the repository you need to clone from the Green "code" dropdown whe you open it on github. 

```

git clone https://github.com/XXXXXXXXXXX/XXXXXXXXX_XXXXXX.git

```

If you do a ```git log``` you can see the while repository history.

We could then push commits to the repository


# Merge Conflicts

Git will flag merge conflicts.

If you open the file it will highlight the conflicts with Left and Right arrows with the names of the Branches, separated by equal signs. You just need to decide which one you want to keep

```
<<<< Bills_Branch

<h1>My Blog</h1>

====================

<h2>My Blog</h2> Johns_Branch

>>>> master

```

git commit -am "fixing a merge conflict"

```