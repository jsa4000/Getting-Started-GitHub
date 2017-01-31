#Installation

##1. Installing Git

Depending on the Operative System do you use: Linux, Microsoft Windows or MacOS you will need to use a different setup to correctly install Git into the machine.
Also, Git provides two ways of managing the repositories. One is by using the command line (by using standard Unix Bash or standard Cmd on Windows) and the other is by using a tool with a graphical interface. However, some of functionality couldn't be implemented, so in most of the cases solving an error or a conflict requires to switch to the command interface.

From GitHub you can also manage the repositories. However, this is more tedious to maintain and slow. 
GitHub is very good for tasks like: watch the contents, small changes, read files (markdown), creating new remote repositories, performing Merges for the received Pull-Request, etc...

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

The installation of Git requires to set a Global variable wiht the full path where the main executable "git.exe" is located. The standard folder installation on Ms Windows is the following:
		
	"C:\Program Files\Github\mingw64\bin"
			
To access to the main Control Panel on Ms Windows (without Admin privileges) from Command line:
		
	"rundll32 sysdm.cpl,EditEnvironmentVariables"

##1.3 Global Configuration 		
	
Git has no configuration by default (vanilla settings). To be able to start creating new repositories, commit changes, etc it's necessary to configure some global variables.
In order to set your user-name and email account you need to use the following commands:
	
	git config --global user.name "user-name"
	git config --global user.email user-email@example.com

The settings are stored in a file .gitconfig, that it's located in the current user folder, "\users\username\". This file looks like this:

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

You can also configure an additional tool that will be launched to compare files. This is used to check the differences and do merges manually.

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
	
##2.Configuring the Repositery

In order to configure your Git repository you have several choices.

###2.1 Create a New Repository

In order to create a new repository, the main workflow is the following:
		
- First create a local repository in the local machine, adding all the structure and source files.
- Create some constraints (.gitignore) and initial files for the repository (.gitattribute, README.md, etc.. ). 
- Add a remote repository. Eventually it will be a GitHub origin, but a remote Git could be created in a another server instead.
- Finally, upload (push) all the content of the repository into the origin (remote).
	
A .gitignore file specifies intentionally untracked files that Git should ignore. Files already tracked by Git are not affected; see the NOTES below for details.
An useful way to indentfy these constraints for untracked files, is to use the default pre-sets provided in GitHub site.
Another web-site that generate this file from some custom pre-sets, like OS, programming language, Developer UI, etc.. is "https://www.gitignore.io/"
	
In order to create a new repository, the main workflow will be:
- First create a local repository in the local machine , adding all the structure and necessary files.
- Create some constraints (.gitignore) and initial files remote repository, in this case a GitHub origin.

###2.2 Clone an Existing repository

This is the common way to proceed in most of the cases and projects.

In this case a entire repository (remote) is cloned into a local machine. Once you have cloned the repository, you can create new branches from this one, modify source-code, add new functionality,
fix bugs, add new files, delete, etc.. When all changes and modifications are done, you can finally can commit and push all the changes by using a "Pull-Request".
This action is used to notify to the remote repository (administrators), to check the changes done, differences and conflicts. Finally this branch will be merged with the new changes into the master branch.

Basically the local work-flow is the same as described in the previous point, However the way we create the repository and the way we push back the changes is different.

In this case a entire repository (remote) is cloned into a local machine. Once you have cloned the repository, you can create new branches from this one, modify source-code, add new functionality,
fix bugs, add new files, delete, etc.. When all changes and modifications are done, you can finally can commit and push all the changes by using a "Pull-Request".
This action is used to notify to the remote repository (administrators), to check the changes done, differences and conflicts. Finally this branch will be merged with the new changes into the master branch.

Basically the local work-flow is the same as described in the previous point, However the way we create the repository and the way we push back the changes is different.

In order to clone you basically need to call the following instruction:
	git clone https://github.com/YOUR-USERNAME/Spoon-Knife

This will create a new directory inside the current folder with the name of the respository. This will retrieve all the content inside the master branch of the remoe respository.

You can get the information of the remote address by typing the following command:
	git remote -v          (-v or --verbose)
	
###2.3 Fork and Clone an Existing repository

This Fork operation doesn't exist in Git. This is an extension of Git that Github has taken into consideration.

A Fork is basically a copy (clone) of a repository into another. After the Fork, both repositories are totally independent from each other.  
Forking a repository allows you to freely experiment with changes without affecting the original project. Most commonly, forks are used to either propose 
changes to someone else's project or to use someone else's project as a starting point for your own idea.

In a normal situation, your origin is also your remote (upstream) repository to perform pull-request your changes. However a fork it's different since this origin is your
copy and the upstream is the original repository of your fork. This is done to request some changes or modifications.

In order to do a Fork, you need some more additional steps:
		
>1. First, perform a Fork operation suing GitHub to copy the repository into your account.
>2. Clone the Fork into your local machine by doing a Clone.
'''
	git clone https://github.com/YOUR-USERNAME/Spoon-Knife
'''
>3. Press "git remote -v "to see the current configuration for the remote location (fetch and push)
>4. Add new remote repository called upstream
```
	git remote add upstream https://github.com/octocat/Spoon-Knife.git
```

The idea behind this operation is that you can fetch and push the changes into both remote repositories.
> This will push the local master into your origin remote respoitory
	git push origin master
> This will update (also pull) your local master branch with the upstream master copy of the remote repository
	git fetch upstream master 








 


