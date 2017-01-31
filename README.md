#  Getting Started in GitHub

#0. OVERVIEW.

In the next chapters I'm going to go through basic **Workflows** currently used in Computer Science.
Current workflows are going to be based in **Git** and **Github** for source-code and web hosting repository.
 
#1. HISTORY. (Git vs GitHub)

This is a topic that people often confuse a lot. I'm talking about the main differences between Git and GitHub since both words are totally different from each other.
	
##1.1 Git 

"Git is a free and **open source distributed version control system** designed to handle everything from small to very large projects with speed and efficiency"
	
Git is a distributed peer-peer version control system. Each node in the network is a peer, storing entire repositories which can also act as a multi-node distributed back-ups. There is no specific concept of a central server although nodes can be head-less or 'bare', taking on a role similar to the central server in centralised version control systems.
		
Git works as a **local repository**. However, it acts as **Back-up** for distributed repository version control system.
	
##1.2 GitHub
		
"GitHub is a **web-based Git repository hosting service**, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features."

Github provides access control and several collaboration features such as wikis, task management, and bug tracking and feature requests for every project.
	
#2. INSTALLING GIT

Depending on the Operative System do you have: Linux, Microsoft Windows or MacOS you will need to use different setup to correctly install Git into the machine.
Also ,Git provide two ways of managing the repositories. One is by using command line (bash or standard cmd on windows) and the other us by using a tool with UI
that allows the same operations that using commands. However some functionality in the UI are omitted to simplify the work, this mean you can get lost very quickly if
some error happens.

From GitHub you can also manage the repositories. However, this is more tedious to maintain and slow. 
GitHub is very good for some other tasks like: watch the contents, read files, creating new remote repositories, performing Merges for the received Pull-Request, etc...

##2.1 Installing on Linux

If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the basic package-management tool that comes with your distribution. If you’re on Fedora for example, you can use yum:

	$ sudo yum install git-all

If you’re on a Debian-based distribution like Ubuntu, try apt-get:

	$ sudo apt-get install git-all

For more options, there are instructions for installing on several different Unix flavors on the Git website, at http://git-scm.com/download/linux.


##2.2 Installing on Windows

There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to http://git-scm.com/download/win and the download will start automatically. Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to https://git-for-windows.github.io/.

To get an automated installation you can use the Git Chocolatey package. Note that the Chocolatey package is community maintained.

Another easy way to get Git installed is by installing GitHub for Windows. The installer includes a command line version of Git as well as the GUI. It also works well with Powershell, and sets up solid credential caching and sane CRLF settings. We’ll learn more about those things a little later, but suffice it to say they’re things you want. You can download this from the GitHub for Windows website, at http://windows.github.com.

The installation of Github on Windows requires a Global variable to access to the main "git.exe" executable globally. In order to do this it's necessary to add the Path of the current executable versión of Git. In my case it was:
		
	"C:\Program Files\Github\mingw64\bin"
			
To access from Comman line to the main control panel on windows (without Admin privileges) :
		
	"rundll32 sysdm.cpl,EditEnvironmentVariables"

##2.3 Global Configuration 		
	
Git has no configuration by default (vanilla settings). To be able to start creating new repositories, commit changes, etc it's necessary to configure some global variables.
In order to set your user-name and email account you need to use the following commands:
	
git config --global user.name "user-name"
git config --global user.email user-email@example.com

The settings are stored in .gitconfig the current user folder, "\users\username\". This file looks like this:

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

You can also configure the tool that will be used to see the differences between files and do the merges manually.

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

	
	
	
#3. CONFIGURING THE REPOSITORY

##3.1 Create a New Repository	
##3.2 Clone an Existing repository
##3.3 Fork and Clone an Existing repository

#4. GIT CONTEXT. WORKING AREA vs STAGE AREA vs COMMITED AREA

#5. UDATE THE CONTENT FROM THE SERVER (PULL vs FETCH)
	
#6. COMMIT CHANGES

#7. FIXING MISTAKES AND UNDOING BAD COMMITS

##7.1 Undo a File from current change.
##7.2 Modify the comment of the previous commit without alter the history. 
##7.3 Change committed files from the previous commit without create a new one.
##7.4 Reset the repository to a Commit point.
##7.5 Clean modified files or untracked files from Commit.
##7.6 Recover deleted branch or Commit from historical reference log.
##7.7 Revert changes to a point with historical.
##7.8 Cherry-Picking specific commits from another branch to the current.
##7.9 Differences between Git Revert, Checkout and Reset.

#8. BRANCHES FROM REPOSITORY

#9. PULL REQUEST

#10. MERGE COMMITED CHANGES

#11. BASIC WORKFLOW

#12. FAQ

##12.1 Differences between Git add ., git add -A,git -u /A, git add *











 


