#Installation

##1. Installing Git

Depending on the OS are you using: Linux, Microsoft Windows or MacOS you will need to use a different Setup to correctly install Git into the machine.
Also, Git provides two ways of managing the repositories. One is by using the **command line** (by using standard Unix Bash or standard Cmd on Windows) and the other one, is by using another tool with a **graphical interface**. However, some of the functionality couldn't be implemented. In most of the cases solving an error or a conflict requires to switch to the command interface.

From GitHub you can also manage your repositories as remote. However, this is more tedious to maintain and slow. The changes and commits have to be done indiviually per file modified.
The GitHub platform is very suitable for tasks like: basic overview of branches and structure, small changes, reading formatted files (markdown), creating new remote repositories, performing Merges due Pull-Request, etc...

##1.1 Installing on Linux

If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the basic package-management tool that comes with your distribution. If you’re on Fedora for example, you can use yum:

	$ sudo yum install git-all

If you’re on a Debian-based distribution like Ubuntu, try apt-get:

	$ sudo apt-get install git-all

For more options, there are instructions for installing on several different Unix flavors on the Git website, at http://git-scm.com/download/linux.

##1.2 Installing on Windows

There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to http://git-scm.com/download/win and the download will start automatically. Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to https://git-for-windows.github.io/.

To get an automated installation you can use the Git Chocolatey package. Note that the Chocolatey package is community maintained.

Another easy way to get Git installed is by installing GitHub for Windows. The installer includes a command line version of Git as well as the GUI. It also works well with Powershell, and sets up solid credential caching and sane CRLF settings. We’ll learn more about those things a little later, but suffice it to say they’re things you want. You can download this from the GitHub for Windows website, at http://windows.github.com.

The installation of Git requires to set the PATH (via Global Variable) where the main executable "git.exe" is located. The standard folder installation on Microsoft Windows is:
		
	"C:\Program Files\Github\mingw64\bin"
			
Additional, in order to access to **Main Control Panel** on Microsoft Windows (without Admin privileges) from Command line:
		
	"rundll32 sysdm.cpl,EditEnvironmentVariables"

##1.3 Global Configuration 		
	
Git has **NO** configuration by default (vanilla settings). To be able to start creating new repositories, commit changes, etc, it's necessary to **configure** some global variables first.
In order to set your user-name and email account you need to use the following commands:
	
	git config --global user.name "user-name"
	git config --global user.email user-email@example.com

The settings are stored in a file *.gitconfig*, that it's located in the current user folder, *"\users\username\"*. This file looks like this:

	[user]
		name = user.name
	[user]
		email = user.name@example.com
	[filter "lfs"]
		clean = git-lfs clean -- %f
		smudge = git-lfs smudge -- %f
		required = true


To list all the variables already configured, you can use the following command:

	git config --list

You can also configure additional tools that will be launched to compare or merge files. This is used to check the differences and do merges manually.

	[mergetool]
		prompt = false
		keepBackup = false
		keepTemporaries = false

	[merge]
		tool = winmerge

	[mergetool "winmerge"]
		name = WinMerge
		trustExitCode = true
		cmd = "/c/Program\\ Files\\ \\(x86\\)/WinMerge/WinMergeU.exe" -u -e -dl \"Local\" -dr \"Remote\" $LOCAL $REMOTE $MERGED

	[diff]
		tool = winmerge

	[difftool "winmerge"]
		name = WinMerge
		trustExitCode = true
		cmd = "/c/Program\\ Files\\ \\(x86\\)/WinMerge/WinMergeU.exe" -u -e $LOCAL $REMOTE 
		
Moreover, If you want to cache your credentials, so you don't have to type it every time, you can use the following command:

	git config --global credential.helper wincred
	
##2.Configuring the Repositery

In order to configure your Git repository you have several ways depending on your needs.

###2.1 Create a New Repository

In order to create a new repository, the main workflow is the following:
		
- First create a local repository in the local machine, adding all the structure and source files. Calling tt the following command inside a folder it will create a folder *".git"*, that will be used to recognize that folder as a Git Repository.
	
		git init

- Create some constraints (.gitignore) and initial files for the repository (.gitattribute, README.md, etc.. ).  To create nwe files into the respoitory directly in the bash you can type the following command:

		touch .gitignore

- Add a remote repository. Eventually the main remote Git will be called "origin", but a remote Git could be whatever name you want.

		git remote add origin https://github.com/user/repo.git
	
 In order to see the changes you can type the following commands  (-v or --verbose).
	
	git remote -v
	git remote show origin

- Finally, upload (push) all the content of the repository into the origin (remote). To push the content of you current Branch/HEAD, you need to specify the branch or head and your remote Git.

		git push origin master

A .gitignore file specifies intentionally untracked files that Git should ignore. Files already tracked by Git are not affected.
An useful way to identify these constraints for not-desired untracked files, is to use the default pre-sets provided in GitHub site.
Another web-site that allows you to generate this file, with some custom pre-sets, like OS, programming language, Developer UI, etc.. is "https://www.gitignore.io/"

###2.2 Clone an Existing repository

This is the **usual** way to proceed in most of the cases for projects you will be working on.

In this case a entire repository (remote Git repository) is **cloned** into a local machine. Once you have cloned the repository, you can create new branches from this one, modify source-code or add new functionality,
When all changes and modifications are done, you can finally stage, commit and push all the changes by using a "Pull-Request".
"Pull-Request" is used to notify to the remote repository (administrators mostly), to check the changes done, differences and conflicts. Finally this branch will be merged with the new changes into the master branch.

Basically the local work-flow is the same as described in the previous point, However the way we create the repository and the way we push back the changes is different.

In order to clone you basically need to call the following instruction:

	git clone https://github.com/YOUR-USERNAME/Spoon-Knife

This will create a new directory inside the current folder with the name of the respository. This will retrieve all the content inside the master branch of the remote repository. The usual way to proceed after the clone, it's to create new branch so the master won't be modified:

	git branch mybranch
	git checkout mybranch
	
Or directly it can be used the following command to create a new branch and do the checkout at the same time.

	git checkout -b mybranch

You can get the information of the remote address by typing the following command. As default the origin will be the remote Git:

	git remote -v         
	
###2.3 Fork and Clone an Existing repository

The **Fork** operation doesn't exist in Git. This is an extension of Git that GitHub has taken into consideration.

A Fork is basically a copy (like a "clone") of another repository. After the Fork, both repositories are totally independent from each other. Forking a repository allows you to freely experiment with changes without affecting the original project. Most commonly, forks are used to either propose changes to someone else's project or to use someone else's project as a starting point for your own idea.

In a normal situation, your origin is also your remote (upstream) repository. This is used to perform a pull-request action for your local changes. However a fork it's different since the origin is your copy and the upstream is the original repository of your fork. This is done to request some changes or modifications.

In order to do a Fork, you need some more additional steps:
		
- First, perform a Fork operation using GitHub to copy the repository into your account.		
- Clone the Fork into your local machine by performing a clone.

    	git clone https://github.com/YOUR-USERNAME/Spoon-Knife
		
- You can type "git remote -v "to see the current configuration for the remote "origin" location (fetch and push)
- Add new remote repository called *"upstream"*. The idea behind this operation is that you can fetch and push the changes into both remote repositories as you need it.

		git remote add upstream https://github.com/octocat/Spoon-Knife.git

- In the case you need to push commits from the local master to your origin remote repository:
	
		git push origin master
	
- In the case you need to update your current repository from the forked repository (we called *"upstream"*). You have some options:
a. Yo can use the pull command:
	
		git pull upstream master
	
b. You can use the fetch command:

	git fetch upstream master 
	git merge upstream/master
	
*We will explain the differences between Pull and Fetch. I could say by instance that Fetch is safer than Pull since you can diff and merge manually. *








 


