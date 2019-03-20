---
layout: code
title: Git and Github Walkthrough
description: This is a brief walkthrough of git.  It includes the initial setup, the steps involved in updating a repository, and the purpose of each command.
---

# {{ page.title }}

## Summary

To quote from the <a href="https://git-scm.com/" target="_blank">git homepage</a>:

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
>
> Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

A git ```repository``` is a place where you can maintain version control for your project.  Each project should have its own separate ```repository``` so that you can maintain each project individually.  The power of version control is that you can go to any point along the timeline of a development project, and view or alter that code.  Keep in mind that everything located in this folder will be added to your ```repository```, unless you have added it to your .gitignore file, so be careful not to initialze your entire harddrive as a git ```repository```.

You can maintain many copies of the same ```repository```, which allows many different contributors to work on the same project simultaneously, as well as many other benefits outside of the scope of this tutorial.  As you follow through the tutorial, you will notice that I refer to local repositories and remote repositories.  When I refer to the local ```repository```, I simply mean the ```repository``` copy that exists on your computer.  In the context of this tutorial, when I refer to the remote ```repository``` (or simply ```remote```), I am refering to the ```repository``` that exists on Github.  When I refer to a ```project```, I am talking about (typically) a single folder that contains all of the code for your application, sub-folders, and any other related files.  If you have multiple folders required for your project, you will need to put them all into one single containing folder.  Any text you see surrounded by angle brackets ```<>``` should be treated as a variable, meaning you will need to plug in the actual value, i.e. ```<PROJECT URL FROM ABOVE>``` would be replaced with ```my-awesome-project``` if using the tutorial project name (please note that the angle brackets are also replaced).

## The Walkthrough

### Create a Remote Repository

![Sign up for Github]("/assets/images/github1.png")

Prerequisite: this step requires that you sign up for an account on Github.  Free and paid accounts both can follow this tutorial.

![Create a repository]("/assets/images/github2.png")

* Go to your profile
* Create a new ```repository```
  * Click on ```New```
  * Enter the project name
    * I recommend a naming convention using all lowercase letters, no numbers, and using hyphens in place of spaces
      * Numbers are accepted, but can hinder readability and intent
      * Do not use anything other than numbers, letters, and hyphens
      * Spaces are converted to hyphens
      * Other characters are left out entirely
  * Choose either public or private
  * Optionally select ```Initialize this repository with a README``` (can be added manually later)
  * Optionally select ```Add .gitignore``` (can be added manually later)
  * Optionally select ```Add license``` (can be added manually later)
  * Click ```Create repository```
* Click the copy button next to the project's URL once the ```repository``` has been created **(hang on to this, as we will use it in later steps)**

#### README.md

READMEs are a good idea to have if you would like to present information about the ```repository```.  Github automatically displays this file on any folder level, so you don't need to do anything else other than include it where you want it displayed (typically in the root of your git ```repository``` folder).  The full filename is actually ```README.md```, and can either be in all upercase, lowercase, or anything in between.  Best practices dictate that it should be in all caps though.

The ```.md``` file extension indicates that this file is what is known as a markdown file.  This file is composed of all plain-text, with some characters that have a specific meaning.  There is a guide to writing markdown text <a href="https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf" target="_blank">here</a>.  The syntax is very simple to understand and remember, and there are many tools out there that can manipulate markdown text, so it can be quite useful.

#### .gitignore

The .gitignore file tells git and Github what files to not include in the ```repository``` (no tracking).  While this may not sound immediately useful, you will realize after working with different IDEs or editors that they can create their own files for local use, and therefore should not be added to the ```repository```.  These files can be very long, and could seem a bit overwhelming at first glance.  However there are many tools out there that can help you to create a default .gitignore file, depending on which IDE or editors you use.

The one that I personally use is <a href="https://www.gitignore.io/" target="_blank">github.io</a>.  Try navigating to that link and type in ```visual```.  You will notice that a few Visual Studio related suggestions appear.  Select ```Visual Studio Code```.  You can continue adding additional IDEs or editors as necessary.  Click on ```Create``` and a plain-text file will be displayed.  Right click this text in your browser, and save it to the root folder of any project you wish to add it to.  Now all of your editor settings, and other related files or folders, will no longer be added to your ```repository```.

#### LICENSE.md

The LICENSE.md file tells contributors how they are able to use your source code and software.  There are numerous options to choose from here, so you will probably want to do a search for these to determine which one fits your project the best.  There are many different nuances here so please read over these carefully.  You can also create your own if you like at a later time.

#### Next Steps

The following can be completed in different ways, depending on your situation.  Only one option needs to be followed.  This way should be followed when following this tutorial from beginning to end, and the following options can be used for other situations you may run into in the future.

### Option 1 - Clone a New Repository

This is a good way to handle brand new projects with no pre-existing code and no pre-existing local repositories.  You can also use this method to clone existing repositories to a local ```repository```.

Prerequisite:  You must have git bash installed if you are on a PC, which you can <a href="https://git-scm.com/downloads" target="_blank">download here</a>.  Macs should already have this included, but you can access the link above if you do not have it, or need to update your version.  The folder structure we will be creating at a later point in this process will be as follows:

```txt

/git/my-first-project/
/git/my-second-project/
/git/my-third-project/
...

```

#### PC Instructions

* Open ```git bash```
* In the command prompt that opens, type the following commands
  * ```cd c:``` ***(You can enter any drive letter here to siwtch to it; note that this is slightly different from how the Windows command prompt works)***
  * ```mkdir git``` ***(skip if you have previously created this directory)***
    * ```mkdir``` is a command line tool to make a directory
  * ```git clone <PROJECT URL FROM ABOVE>```

#### Mac Instructions

* Open ```terminal```
* In the command prompt that opens, type the following commands
  * ```pwd```
    * Ensure that the displayed path is ```/usr/<YOUR USER NAME>```
    * If it is not, then type ```cd ~```
  * ```mkdir git``` ***(skip if you have previously created this directory)***
    * ```mkdir``` is a command line tool to make a directory
  * ```git clone <PROJECT URL FROM ABOVE>```

#### Explanation

```Clone``` is the command that is used to make an exact copy of a ```repository```.  You can achieve a similar result by downloading the ```repository``` from Github, and unzipping it.  However, using ```clone``` is the preferred way as it is faster, and helps prevent user error from causing issues in the process.

### Option 2 - Create and Push a New Local Repository

This is a good way to handle projects that do have pre-existing code, but a local ```repository``` has not been set up yet.  You can also use this method to push a pre-existing repository up to a new remote repository.

Prerequisite:  You must have git bash installed if you are on a PC, which you can <a href="https://git-scm.com/downloads" target="_blank">download here</a>.  Macs should already have this included, but you can access the link above if you do not have it, or need to update your version.  The folder structure we will be creating at a later point in this process will be as follows:

```txt

/git/my-first-project/
/git/my-second-project/
/git/my-third-project/
...

```

#### PC Instructions

* Open ```git bash```
* In the command prompt that opens, type the following commands
  * ```cd c:``` ***(You can enter any drive letter here to siwtch to it; note that this is slightly different from how the Windows command prompt works)***
  * ```cd <PATH TO EXISTING PROJECT>```
  * ```git init``` ***(skip if you already have initialized the directory; can be determined by using the ```git status``` command)***
  * ```git add .```
  * ```git commit -a -m "Initial commit"```
  * ```git remote add origin <PROJECT URL FROM ABOVE>```
  * ```git push -u origin master```

#### Mac Instructions

* Open ```terminal```
* In the command prompt that opens, type the following commands
  * ```cd <PATH TO EXISTING PROJECT>```
  * ```git init``` ***(skip if you already have initialized the directory; can be determined by using the ```git status``` command)***
  * ```git add .```
  * ```git commit -a -m "Initial commit"```
  * ```git remote add origin <PROJECT URL FROM ABOVE>```
  * ```git push -u origin master```

#### Explanation

```Init``` is how you tell git to create a new ```repository``` in the existing folder.  All files in this directory will be added to the ```repository```, unless you have included the file or file type in the .gitignore file.

```Add``` is how you tell git to begin tracking a file or files in your local ```repository```.  All files in this directory will be tracked and can be pushed up to the remote ```repository```, unless you have included the file or file type in the .gitignore file.  Tracking is the git term for watching a file or files for changes.  We include a period ```.``` at the end of the add command in order to tell git to track all files, except for those file or file types outlined in the .gitignore file.

```Commit``` tells git to take all of the changes from our tracked files, and incorporate them into the repository.  The ```-a``` option tells git that we want to include all changed files in the current commit.  The ```-m "<COMMIT MESSAGE>"``` option tell git that we would like to include a commit message.  If you do not specify the ```-m "<COMMIT MESSAGE>"``` option, then git will open the ```vim``` editor to allow you to add a message to the commmit.  If you find yourself in this mode, you may be confused by how the text editor works.  There are only a few commands that you really need to know here.  Press ```i``` to go into insert mode, and ```esc``` to exit this mode.  ```:wq``` will write, followed by quitting out, and once done, will automatically initiate the commit with the message you entered.  If you make a mistake, or need to back out for any reason, you can use the command ```:q``` to quit out if you have made no changes here, or ```:q!``` to cancel changes and quite.  For a good reference to vim commands, please click <a href="https://www.fprintf.net/vimCheatSheet.html" taget="_blank">here</a>.

```Remote``` is how to manipulate the git configuration for remote repositories.  In the example above, we are adding a remote repository, with the name ```origin``` (a best practice), and it will point to the git repository url specified.  It is worthwhile to note that ```origin``` is a completely arbitrary name, and could be called anything.  You can also specify multiple remote locations, as long as they have different names, but that is beyond the scope of this tutorial.

```Push``` is the command that causes git to push all commits to another location.  The ```-u``` option indicates that we want to make our local branch (more on this term later) a tracking branch.  What this means is that this local repository branch can determine when it has changed versus what is located on the remote repository.  This is how git knows if it needs to push changes up, as well as which changes get pushed.  The ```origin``` option tells git that we are pushing to the repository specified by the ```origin``` keyword, which we defined in the previous step.  The ```master``` option tells git which branch we want to push to.  The main branch is always called ```master```, but you may have numerous branches in a repository with different names.

### Committing

Committing, as explained above, is just adding your changes to the repository.  You can commit as many or few times as necessary, and when you push, all of your commits to this point will be included.  It is much better to perform a commit for every atomic change, so that you can maintain much more granularity in your commits.  Basically, if you make a mistake at some point, and need to roll back, it is much better to be able to rollback to the last commit made 10 minutes ago, rather than the commit made 10 days ago.  If you make lots of changes, and then get into trouble, and you haven't been frequently committing, you have have to undo a large chunk of work, rather than one or two small ones.

### Branching

Branching is how you can create working copies of your repository.  This allows you to be able to make changes to a branch and either bring those changes into your master branch, or discard those changes. The command ```git branch``` will display all of your local branches.  Be aware that this will not show your remote branches.  To create a new branch use the command ```git branch <BRANCH NAME>```, followed by ```git checkout <BRANCH NAME>``` to switch over to that branch.  A nice shorthand for this is ```git checkout -b <BRANCH NAME>```, which will roll both of those commands into one.

If you break your application, or otherwise don't need any of your changes, you can switch to ```master``` by typing ```git checkout master``` followed by ```git branch -d <BRANCH NAME>```.  If this branch has uncommitted changes on the branch to be deleted, git will issue a warning.  If you really want to delete this branch, you can use the command ```git reset --hard HEAD``` followed by ```git branch -d <BRANCH NAME>```.  You may also want to delete a branch that has not been merged yet (more on this term later).  Git will issue a warning for this as well.  If you really intended to delete this branch, you can type ```git branch -D <NBRANCH NAME>```.  Note the capital ```D``` that in used instead of the lowercase ```d``` for this command.

### Merging

Merging is how you combine branches in git.  In Github, this is called a pull request, which is a request that is sent to the repository owner to have them pull your pushed commits over into ```master```, or another branch.  To initiate a merge, you will first need to switch to the branch that you want to merge into, and then issue the command to merge another branch into your current branch.  As an example, let's use the branches ```master``` and ```my-feature```.  You would type the command ```git checkout master``` followed by ```git merge my-feature```.

If you run into merge conflicts, which are places where a line has two different changes, you will need to open the conflicted file in an editor of your choice and look for any lines that look like the following:

```git

<<<<<<< HEAD
your code
======
the other code
>>>>>>> [other branch]

```

You will have to make a determination as to how you which code should be included or removed here, and remove the surrounding markers.  You will then need to commit the changes and do the merge again.  There are many ways this can be done with greater ease in programming text editors, but it varies from product to product, and so is not in the scope of this tutorial.

Github also offers merging, as stated earlier, in the form of pull requests.  It also offers a more visual approach to resolving merge conflicts.  For this reason, I find that it is best to not perform merges into ```master``` on your local repository, as outlined above, but rather push up to Github, issue a pull request, and resolve any conflicts there.  If you do all of your merging on Github, you will likely have a much better experience starting off.

### Stashing and Popping

As stated previously in the branching section, you can change branches at (almost) any time, by using the command ```git checkout <BRANCH NAME>```.  However, sometimes you will have changes that you really need to add to another branch instead.  As an example, let's use the branches ```master``` and ```my-feature```.  You begin working only to realize that you are actually making changes in ```master``` (not a good practice).  You have already added new tracked files, and have performed numerous changes to those files.  As long as you haven't committed anything yet, you can always move these changes over to another branch.  You try to create a new branch using ```git checkout -b my-feature```, but git issues a warning stating that you have uncommitted changes on the current branch.  Enter the command ```git stash``` and all of your current changes will be saved, and the current branch will be rolled back to the ```HEAD``` commit (more on this below).  You can then enter the command ```git checkout -b my-feature``` with no warning.  To  bring all of your stashed changes back into this new branch, enter the command ```git stash pop```.  This cause git to access the stash (temporary storage only), and to pop all of the changes back out into the current branch.  At this point, you can continue working on this new branch.

### Pulling

Pulling is very important when you need to coordinate work from multiple machines.  As stated above, you can have multiple contributors working on the same repository simultaneously.  This can also include a single developer using multiple machines.  When people make changes to a repository, that change needs to be accessible to all of the developers.  When you issue the command ```git pull```, you are telling git to download all changes from the remote repository, and merge them into your local repository.  It will specifically pull from the same branch name as your local branch when performing this operation.  You can also pull from other branches into your local branch.  For instance, if you need to pull numerous changes made to master by other developers into your local feature branch ```my-feature```, you would need to make sure you are in the branch ```my-feature``` first, and then type in ```git pull origin master```, which tells git to pull the ```master``` branch from the remote repository identified by the name ```origin```.  This can be beneficial to do before you attempt to push up your branch and issue a pull request on Github, as it can prevent merge conflicts, and can allow you to ensure that your branch still works with any changes that may have been made to ```master```.

### Fetching

Fetching allows git to download changes from a remore repository, as above, except that is will not perform any merging.  This allows you to get any remote changes to your repository, without making any changes to your current branch.  This can be useful if you really do not want your branch being updated, and potentially broken, by remote changes, but you still need to use the ```checkout``` command to access other branches that have been created on the remote repository by other developers.

### Reset

In git, you are able to roll your repository back to any given point in time.  In order to view your commit, you can type ```git log```, and you will see a list of all commits that you have made.  If you wish to roll back to one of these, there are several ways to accomplish this.  To get rid of current changes, and reset to the last commit, use the command ```git reset --hard HEAD```.  The ```--hard``` option tells git that you wish to discard all changes.  Alternatively, you can use the ```--soft``` option to move the commit reference only, but leave all code changes.  This can allow you to reset back to a specific commit, but leave all changes intact.

In order to go back to a specific commit, in this example, let's say 3 commits back, you can use the command ```git reset --hard HEAD~3```.  If you would prefer to go back using the commit hash number, you can use the first 7 characters from a ```git log``` entry, i.e. ```git reset --hard f7edf77```.

## Conclusion

I hope this guide has helped you at least a little.  Please keep in mind that there are many more commands to use with git, as it is quite a powerful version control tool.  Please click read the <a href="https://git-scm.com/docs" target="_blank">official git documentation</a> to learn more.
