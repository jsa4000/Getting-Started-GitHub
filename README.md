#  Getting Started in GitHub

##0. OVERVIEW.

In the next chapters I'm going to go through basic **Workflows** currently used in Computer Science.
Current workflows are going to be based in **Git** and **Github** for source-code and web hosting repository.
 
##1. HISTORY. (Git vs GitHub)

This is a topic that people often confuse a lot. I'm talking about the main differences between Git and GitHub since both words are totally different from each other.
	
###1.1 Git 
	
"Git is a free and **open source distributed version control system** designed to handle everything from small to very large projects with speed and efficiency"
	
Git is a distributed peer-peer version control system. Each node in the network is a peer, storing entire repositories which can also act as a multi-node distributed back-ups. There is no specific concept of a central server although nodes can be head-less or 'bare', taking on a role similar to the central server in centralised version control systems.
		
Git works as a **local repository**. However, it acts as **Back-up** for distributed repository version control system.
		
###1.2 GitHub
		
"GitHub is a **web-based Git repository hosting service**, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features."

Github provides access control and several collaboration features such as wikis, task management, and bug tracking and feature requests for every project.
	
		
##2. INSTALLING GIT

Depending on the Operative System do you have: Linux, Microsoft Windows or MacOS you will need to use different setup to correctly install Git into the machine.
Also ,Git provide two ways of managing the repositories. One is by using command line (bash or standard cmd on windows) and the other us by using a tool with UI
that allows the same operations that using commands. However some functionality in the UI are omitted to simplify the work, this mean you can get lost very quickly if
some error happens.

From GitHub you can also manage the repositories. However, this is more tedious to maintain and slow. 
GitHub is very good for some other tasks like: watch the contents, read files, creating new remote repositories, performing Merges for the received Pull-Request, etc...

###2.1 Installing on Linux

If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the basic package-management tool that comes with your distribution. If you’re on Fedora for example, you can use yum:

	$ sudo yum install git-all

If you’re on a Debian-based distribution like Ubuntu, try apt-get:

	$ sudo apt-get install git-all

For more options, there are instructions for installing on several different Unix flavors on the Git website, at http://git-scm.com/download/linux.


###2.2 Installing on Windows
	
There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to http://git-scm.com/download/win and the download will start automatically. Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to https://git-for-windows.github.io/.

To get an automated installation you can use the Git Chocolatey package. Note that the Chocolatey package is community maintained.

Another easy way to get Git installed is by installing GitHub for Windows. The installer includes a command line version of Git as well as the GUI. It also works well with Powershell, and sets up solid credential caching and sane CRLF settings. We’ll learn more about those things a little later, but suffice it to say they’re things you want. You can download this from the GitHub for Windows website, at http://windows.github.com.

The installation of Github on Windows requires a Global variable to access to the main "git.exe" executable globally. In order to do this it's necessary to add the Path of the current executable versión of Git. In my case it was:
		
	"C:\Program Files\Github\mingw64\bin"
			
To access from Comman line to the main control panel on windows (without Admin privileges) :
		
	"rundll32 sysdm.cpl,EditEnvironmentVariables"

###2.3  Git Configuration 		
	
In the initial state, GitHub has no configuration at all, regarding the repositories, user accounts, etc.. For this reason configuring Git it's somthing you 
have to do after Git is installed in the Machine.		
	
##3. CONFIGURING THE REPOSITORY

In order to configure your Git repository you have several choices.
	
###3.1 Create a New Repository	
	
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

###3.2 Clone an existing repository
	
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


###3.3 Fork and Clone an existing repository

This Fork operation doesn't exist in Git. This is an extension of Git that Github has taken into consideration.

A Fork is basically a copy (clone) of a repository into another. After the Fork, both repositories are totally independent from each other.  
Forking a repository allows you to freely experiment with changes without affecting the original project. Most commonly, forks are used to either propose 
changes to someone else's project or to use someone else's project as a starting point for your own idea.

In a normal situation, your origin is also your remote (upstream) repository to perform pull-request your changes. However a fork it's different since this origin is your
copy and the upstream is the original repository of your fork. This is done to request some changes or modifications.

In order to do a Fork, you need some more additional steps:
		
1. First, perform a Fork operation suing GitHub to copy the repository into your account.
2. Clone the Fork into your local machine by doing a Clone.
	git clone https://github.com/YOUR-USERNAME/Spoon-Knife
3. Press "git remote -v "to see the current configuration for the remote location (fetch and push)
4. Add new remote repository called upstream
	git remote add upstream https://github.com/octocat/Spoon-Knife.git


The idea behind this operation is that you can fetch and push the changes into both remote repositories.
	Ej. git push origin master -> This will push the local master into your origin remote respoitory
		git fetch upstream master -> This will update (also pull) your local master branch with the upstream master copy of the remote repository

##3. GIT CONTEXT STAGE AREA vs REPOSITORY AREA



##4. UDATE THE CONTENT FROM THE SERVER (PULL vs FETCH)

In order to update the current repository with another branch or remote repository, you need to know some different ways that will depend on your workflow or complexity of the changes you need to add or merge.

There are two ways to update the current branch with another, this update doesn't necesary mean, the changes will be automatically be merged. In this case, you have to decide if first you want to see the diffs or let Git to merge automatically the changes.

Rebase will mean the changes that are retrieved from the remote server are firstly taken into consideration. So the merge are done upon this update opeation.

Runs git-pull means Fetch from and Merge with another repository or a local branch.	With --rebase, calls git-rebase instead of git-merge.

Runs git-fetch with the given parameters, and calls git-merge to merge the retrieved head(s) into the current branch. 


In the simplest terms, git pull does a git fetch followed by a git merge. Fetch it's a more controlled way to see the changes prior to merge, if it's necessary or make sense.

	
	Simple Workflow to update a repository using pull:
		git pull origin master
		git checkout foo-branch
		git rebase master
		git push origin foo-branch
	
	Simple Workflow to update a repository using fetch:
	
		- git checkout master                                                  
		- git fetch                                        
		- git diff origin/master
		- git rebase origin master

	Some people claims that the most useful way to update the respository is doinf the following:
	
		git pull --rebase

##5. COMMIT CHANGES


##5.1 FIXING MISTAKES AND UNDOING BAD COMMITS

For this section there are some basic commands you need to know:

	"git branch" this tell you all the branches you currently have in the repository. The selected are your current (checkout) branch.
	"git status" this is going to tell you the current status of your branch, stage area, uncommited changes, etc..
	"git log" this will print all the commits done in the current branch. Basically this is the historical of your repository. 
		>> You need to know that every change and commit have different hash or "Id". Including the command --amend is going to give you different hash.
		>> In case you don't want to change the commit (overwrite), you need to use the "--amend" parameter in the commit command.
	"git reflog" this will print all the commits and actions done in the current bracnh. This will include all the actions, including, rest, revert, amend, etc..
		>> This command is used to recover some branches that you deleted by mistake.
		>> This log are deleted monthly by Git for maintenance task.
	"git diff", by using this command you could get the differences between some branches or commits.
	
Depending on the case you would need different commands and actions:

1. Undo a File

In order to get back to and old version of a file that have been modified: git checkout your_file
This action will undo the changes of that file.

2. Modify the comment of the previous commit without alter the history. 

This case is to modify the previous commit done. Note that the Hash of the commit will also change after this operation.
 In order to do tha the command is the following:

git commit --amend -m "Override the previous comment"

3. Change committed files from the previous commit without create a new one.

git add .
git commit --amend

Git will prompt the committed changes and the previous comment, so it can be modified if needed.

4.






##6. BRANCHES FROM REPOSITORY


##7. PULL REQUEST

##8. MERGE COMMITED CHANGES


##9. BASIC WORKFLOW


##10. FAQ

###10.1 Differences between Git add ., git add -A,git -u /A, git add *
In Git you can use several methods to add your files from Working Folder to the Stage area. 

"Git add -A", will add all the files that are untracked, deleted or modified. This will look at all the files that are locally in the repository independently of the folder you are. 
However you can specify a folder after the sentence, "git add -A /my_folder"  

"Git add ." will add all the files (untracked, deleted or modified) that are inside the current folder and subfolders.


"Git add *" will add al the files untracked and modified. The deleted files since they are no more in the folder, they won't be included.













 


