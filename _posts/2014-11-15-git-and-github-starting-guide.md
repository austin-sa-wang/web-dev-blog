---
layout: post
title: Version Control: git (and Github)
---

Version control is almost a must for any development. It allows one to make incremental progress without the worry of messing up whatever has been development. The concept is intuitive. You make a copy of the current work when you feel you've reached a milestone, then you continue working. This copy can be used as a reference, or a backup to revert to when things go horribly wrong. Without any training to version control, people already do this by creating directories to store different versions of their work. Doing version control manually like this can be messy, tedious, and prone to mistakes. This is where version control tools come in. There are many established and widely used version control tools. The one I'll be using, is [git](http://git-scm.com/).

git is a very popular version control tool in the software world. That includes individual developers, companies, and the open source community. In addition, there is also an extremely well established git repository web-based hosting service called [GitHub](https://github.com/), which I will also be using. It allows you to backup your work online, without all the complication of setting up your own server. At the same time, it can be used to share your own work, see others' work, and collaborate with others.

To clarify the functionality and relationship of git and GitHub:

* __git__: the version control tool, with the most basic way of using it, is local (local repository). You do not need a server(i.e. GitHub) to use git. Every version of the backups is stored in your local repository.
* __GitHub__: the repository hosting service is web based (web repository). It provides a place for you to store your git backups on the internet. It is based on git, so you can use git commands to push your work onto your GitHub web repository directly. Alternatively, you can host your own server if you want to use an internet repository.

------

##Get Started

There are two sites that I used to learn git. The content on both sites are similar, but git-scm has more concept explanations. I use git-scm for concepts or alternative reading on how-to, and atlassian for the how-to.

* [git-scm Documentation](http://git-scm.com/doc): for concepts
* [atlassian git Tutorial](https://www.atlassian.com/git/tutorials): for how-to

------

###On Concept

The **bare minimum** one should know before using git is The basic workflow: [git-scm: The Three States](http://git-scm.com/book/en/v2/Getting-Started-Git-Basics#The-Three-States)
![Working directory, staging area, and Git directory.](http://git-scm.com/book/en/v2/book/01-introduction/images/areas.png)

* __Working directory__: is the directory you are working on
* __staging area__: is a conceptual area to specify which files will be backed up
* __Repository__: is where the committed versions are stored

------

Personally, I like to know the context, the background, and the basics of a new technology before I use it. I read through the documentation which git-scm provides. Since git-scm's documentation is mixed with both concepts and how-to's, you need to skip section for the concepts. Here's the list of the concepts I went through in-order:

1. [About Version Control](http://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
2. [Git Basics](http://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
3. [Branching](http://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

Now, there are much more concepts to learn, such as *git on the server* and *distributed git*, but I found myself comfortable enough to use git after reading the above ones.

------

###On How-To

__To setup git__, follow the instructions on git-scm: [Installing Git](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

For Windows users, I found the easiest way to get git ready is to install [GitHub for Windows](https://windows.github.com/). With this, you will be able to use both the command line(Git Shell) and the GitHub GUI.

------

__To use git__, here are the options: Command line, GUI clients such as GitHub and plug-in's such as EGit for Eclipse.

This section is about the __command line__. git commands are quite simple and intuitive. Knowing command line enables you to use git to its fullest. In addition, you will also be able to adapt to GUI quickly, but not the other way around.

------

__To learn the git command line__, you can

* __Go through a tutorial step by step__: [atlassian git Tutorial](https://www.atlassian.com/git/tutorials), or
* __Jump in and use it__: learn by doing, look up documentation when needed (tutorial/[git reference](http://git-scm.com/docs))

I recommend a mix of both. For example, I set up a project directory and tried out the things in the tutorial, with simple text files as project files. Then, I moved on to setting up this very blog with git, pushed it onto GitHub's remote repository, and started fiddling with the blog. (see [GitHub Pages](https://pages.github.com/) if you're interested in GitHub's web page hosting service)

------

#####Basic commands and workflow

Example of starting from scratch to a working repository + remote repository:

{% highlight HTML %}
git config --global user.name "John Doe"
git config --global user.email john.doe@email.com

git remote add origin https://github.com/johndoe/my_project.git

cd D:\Workspace\Git\my_project
git init
git status
git add newly_created_txt_file.txt
git status
git commit

git push origin master
{% endhighlight %}

Open up the command line. In our case with GitHub installation, use the __Git Shell__ executable. 

Here is a list of basic commands which allow you to get started and use git minimally. All of these can also be learned more in-depth from the tutorials. Remember, these are the most minimal way of using the commands, and they can be much more powerful than these. Either refer to the tutorials, or check [git reference](http://git-scm.com/docs).

_To setup your identity_ (after fresh install)

* `git config --global user.name "[user name]"`
* `git config --global user.email [e-mail address]`


_To setup a git repository for your project_

* `cd [directory path]` to change the working directory to where your project is
* `git init` to setup a repository (This creates the .git directory inside your working directory)

_To back up files_

* `git add [file]` to stage a file for commit (Do this if the file has just been created or modified)
* `git commit` to back up the staged files (This opens up a text editor for you to input the comment for the commit. Simply type in the comment and close the editor to proceed)
* `git commit -a` to commit all, including the un-staged.

_To view the status of the files_

* `git status` to see the general status of the repository (list of modified files, staged file)
* `git log` to view the change history of the files

_To undo changes_ (Refer to a tutorial to do this properly)

* [atlassian:old commits](https://www.atlassian.com/git/tutorials/viewing-old-commits)
* [atlassian:Undoing changes](https://www.atlassian.com/git/tutorials/undoing-changes)
* `git revert [commit id]` to undo (undo the most recent change with `git revert master`)

_To work with a remote repositoy_

* `git remote add [ref. name] [url]` to add a remote repository (ref. name can be anything. It is used as a reference when pushing)
* `git push [remote ref. name] [branch]` to push local repository to the remote repository (typically the [branch] would be `master`)
* `git pull [remote ref. name] [branch]` to pull from remote repository

------

#####GitHub

The goal here is to know how to push your local repository onto GitHub. Again, this merely serves as a starting point of using git and remote repository. First of all, get an account on [GitHub](https://github.com/). The tutorial on GitHub is nice, but it is based on GitHub's own GUI tool. To get your local repository onto GitHub:

1. Create a new repository on GitHub (Uncheck _Initialize this repository with a README_ since if you already have a local repository working)
2. Copy the remote repository link, and use the `remote add` command to add the link (The post-creation page also teaches you what to do)
3. Use the `push` command to push your existing repository

Hint: on the post-creation page

>__…or push an existing repository from the command line__
>
>git remote add origin https://github.com/johndoe/new-repo.git
>
>git push -u origin master

Remember, you have to __push__ manually to have the remote repository reflect the changes you have made in your local repository.