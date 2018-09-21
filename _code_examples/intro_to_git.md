---
layout: code
title: Git and Github Walkthrough
description: This is a brief walkthrough of git.  It includes the initial setup, the steps involved in updating a repository, and the purpose of each command.
---

# Summary

To quote from the <a href="https://git-scm.com/" target="_blank">git homepage</a>:

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
> 
> Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

A git repository is a place where you can maintain version control for your project.  Each project should have its own separate repository so that you can maintain each project individually.  The power of version control is that you can go to any point along the timeline of a development project, and view or alter that code.  Keep in mind that everything located in this folder will be added to your repository, unless you have added it to your .gitignore file, so be careful not to initialze your entire harddrive as a git repository.

You can maintain many copies of the same repository, which allows many different contributors to work on the same project simultaneously, as well as many other benefits outside of the scope of this tutorial.  As you follow through the tutorial, you will notice that I refer to local repositories and remote repositories.  When I refer to the *local repository*, I simply mean the repository copy that exists on your computer.  In the context of this tutorial, when I refer to the *remote repository* (or simply *remote*), I am refering to the repository that exists on Github.  When I refer to a *project*, I am simply talking about (typically) a single folder that contains all of the code for your application, sub-folders, and any other related files.  If you have multiple folders required for your project, you will need to put them all into one single containing folder.  Any text you see surrounded by angle brackets ```<>``` should be treated as a variable, meaning you will need to plug in the actual value, i.e. ```<PROJECT URL FROM ABOVE>``` would be replaced with ```my-awesome-project``` if using the tutorial project name (please note that the angle brackets are also replaced).

## The Walkthrough

### Create a Remote Repository

![Sign up for Github]("/assets/images/github1.png")
Prerequisite: this step requires that you sign up for an account on Github.  Free and paid accounts both can follow this tutorial.

![Create a repository]("/assets/images/github2.png")
* Go to your profile
* Create a new repository
  * Click on ```New```
  * Enter the project name
    * I recommend a naming convention using all lowercase letters, and using hyphens in place of spaces
      *  Do not use anything other than numbers, letters, and hyphens
      *  Spaces are
  * Choose either public or private
  * Optionally select ```Initialize this repository with a README``` (can be added manually later)
  * Optionally select ```Add .gitignore``` (can be added manually later)
  * Optionally select ```Add license``` (can be added manually later)
  * Click ```Create repository```
* Click the copy button next to the project's URL once the repository has been created **(hang on to this, as we will use it in later steps)**

#### README.md

READMEs are a good idea to have if you would like to present information about the repository.  Github automatically displays this file on any folder level, so you don't need to do anything else other than include it where you want it displayed (typically in the root of your git repository folder).  The full filename is actually ```README.md```, and can either be in all upercase, lowercase, or anything in between.  Best practices dictate that it should be in all caps though.

The ```.md``` file extension indicates that this file is what is known as a markdown file.  This file is composed of all plain-text, with some characters that have a specific meaning.  There is a guide to writing markdown text <a href="https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf" target="_blank">here</a>.  The syntax is very simple to understand and remember, and there are many tools out there that can manipulate markdown text, so it can be quite useful.

#### .gitignore

The .gitignore file tells git and Github what files to not include in the repository (no tracking).  While this may not sound immediately useful, you will realize after working with different IDEs or editors that they can create their own files for local use, and therefore should not be added to the repository.  These files can be very long, and could seem a bit overwhelming at first glance.  However there are many tools out there that can help you to create a default .gitignore file, depending on which IDE or editors you use.

The one that I personally use is <a href="https://www.gitignore.io/" target="_blank">github.io</a>.  Try navigating to that link and type in ```visual```.  You will notice that a few Visual Studio related suggestions appear.  Select ```Visual Studio Code```.  You can continue adding additional IDEs or editors as necessary.  Click on ```Create``` and a plain-text file will be displayed.  Right click this text in your browser, and save it to the root folder of any project you wish to add it to.  Now all of your editor settings, and other related files or folders, will no longer be added to your repository.

#### LICENSE.md

The LICENSE.md file tells contributors how they are able to use your source code and software.  There are numerous options to choose from here, so you will probably want to do a search for these to determine which one fits your project the best.  There are many different nuances here so please read over these carefully.  You can also create your own if you like at a later time.


#### Next Steps

The following can be completed in different ways, depending on your situation.  Only one option needs to be followed.  This way should be followed when following this tutorial from beginning to end, and the following options can be used for other situations you may run into in the future.

### Option 1 - Clone the Repository

This is a good way to handle brand new projects with no pre-existing code and no pre-existing local repositories.

Prerequisite:  You must have git bash installed if you are on a PC, which you can <a href="https://git-scm.com/downloads" target="_blank">download here</a>.  Macs should already have this included, but you can access the link above if you do not have it, or need to update your version.  The folder structure we will be creating at a later point in this process will be as follows:

```
/git/project-1/
/git/project-2/
/git/project-3/
...
```

#### PC Instructions
* Open ```git bash```
* In the command prompt that opens, type the following commands
  * ```cd c:```
  * ```mkdir git``` (skip if you have previously created this directory)
    * ```mkdir``` is a command line tool to make a directory
  * ```git clone <PROJECT URL FROM ABOVE>```
  
#### Mac Instructions
* Open ```terminal```
* In the command prompt that opens, type the following commands
  * ```pwd```
    * Ensure that the displayed path is ```/usr/<YOUR USER NAME>```
    *  If it is not, then type ```cd ~```
  * ```mkdir git```
  * ```git clone <PROJECT URL FROM ABOVE>```

#### Explaination

```Clone``` is the command that is used to make an exact copy of a repository.  You can achieve a similar result by downloading the repository from Github, and unzipping it.  However, using ```clone``` is the preferred way as it is faster, and helps prevent user error from causing issues in the process.

### Option 2 - Create and Push a New Local Repository

This is a good way to handle projects that do have pre-existing code, but a local repository has not been set up yet.

Prerequisite:  You must have git bash installed if you are on a PC, which you can <a href="https://git-scm.com/downloads" target="_blank">download here</a>.  Macs should already have this included, but you can access the link above if you do not have it, or need to update your version.  The folder structure we will be creating at a later point in this process will be as follows:

```
/git/project-1/
/git/project-2/
/git/project-3/
...
```

#### PC Instructions
* Open ```git bash```
* In the command prompt that opens, type the following commands
  * ```cd <PATH TO EXISTING PROJECT>```
  * ```git init```
  * ```git add .```
  * ```git commit -a -m "Initial commit"```
  * ```git remote add origin <PROJECT URL FROM ABOVE>```
  * ```git push -u origin master```
  
#### Mac Instructions
* Open ```terminal```
* In the command prompt that opens, type the following commands
  * ```cd <PATH TO EXISTING PROJECT>```
  * ```git init```
  * ```git add .```
  * ```git commit -a -m "Initial commit"```
  * ```git remote add origin <PROJECT URL FROM ABOVE>```
  * ```git push -u origin master```

#### Explaination

```Init``` is how you tell git to create a new repository in the existing folder.  All files in this directory will be added to the repository, unless you have added a .gitignore file.
