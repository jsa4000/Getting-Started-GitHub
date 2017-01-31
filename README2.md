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

The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit. It’s sometimes referred to as the “index”, but it’s also common to refer to it as the staging area.

The basic Git workflow goes something like this:

- You modify files in your working tree.
- You stage the files, adding snapshots of them to your staging area.
- You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.

If a particular version of a file is in the Git directory, it’s considered committed. If it has been modified and was added to the staging area, it is staged. And if it was changed since it was checked out but has not been staged, it is modified. In Git Basics, you’ll learn more about these states and how you can either take advantage of them or skip the staged part entirely.



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

		
git checkout -b iss53		
		
##5. COMMIT CHANGES



##6. FIXING MISTAKES AND UNDOING BAD COMMITS

NOTE: A very good tutorial on youtube with the same materials is https://www.youtube.com/watch?v=FdZecVxzJbk
	  Also this link could be a very good lecture for this topic: https://davidzych.com/difference-between-git-reset-soft-mixed-and-hard/

For this section there are some basic commands you need to know:

	"git branch" this tell you all the branches you currently have in the repository. The selected are your current (checkout) branch.
	"git status" this is going to tell you the current status of your branch, stage area, uncommited changes, etc..
	"git log" this will print all the commits done in the current branch. Basically this is the historical of your repository. 
		>> You need to know that every change and commit have different hash or "Id". Including the command --amend is going to give you different hash.
		>> In case you don't want to change the commit (overwrite), you need to use the "--amend" parameter in the commit command.
		>> use "git log --stat" to get more detailed view of the changes made.
	"git reflog" this will print all the commits and actions done in the current bracnh. This will include all the actions, including, rest, revert, amend, etc..
		>> This command is used to recover some branches that you deleted by mistake.
		>> This log are deleted monthly by Git for maintenance task.
	"git diff", by using this command you could get the differences between some branches or commits.
	
Depending on the case you would need different commands and actions:

###6.1. Undo a File

In order to get back to and old version of a file that have been modified: git checkout your_file
This action will undo the changes of that file.

###6.2. Modify the comment of the previous commit without alter the history. 

This case is to modify the previous commit done. Note that the Hash of the commit will also change after this operation.
 In order to do tha the command is the following:

git commit --amend -m "Override the previous comment"

###6.3. Change committed files from the previous commit without create a new one.

git add .
git commit --amend

Git will prompt the committed changes and the previous comment, so it can be modified if needed.
Type ":wq" to write and quit. This is a command from vi.

###6.4. Reset the repository to a Commit point 

This is used when you want to revert the repository to a certain commit. (Similar to a Restore point)
The hash of the commit is needed to perform this operation.

There are 3 several ways to reset the repository to a certain point: "--soft", "--mixed" and "--hard".

The command to reset the repository is as follows:
"git reset --soft commit-hash"
 
Where commit-hash is the first (eight for example) numbers of the commit (e.j. d5f5a722ba9)
	commit d5f5a722ba95f9a914d8db3a8ac226c3d1d7bfcd
	Author: jsa4000 <jsa4000@gmail.com>
	Date:   Mon Jan 30 16:42:50 2017 +0100

The differences between those parameters depend on the status of the current reset regarding the staged files.
In some cases you want to reset totally to a commit branch (hard), or sometimes you need to add some more files or do some modification after do the commit again. 

###6.5. Clean staged or untracked files

When you use "git status", you are going to see all the files untracked or changed for the future commit.
Some times you need to remove these files from the commit. For example you have added some files, but you don't neccesay needed them for this commit. 
The command to clean these changes is:
git clean -df

###6.6. Recover deleted branch or Commit

This is used when you want to recover a bracnh that has been totally delete from the log (hoistorial of commits)
To see all the logs (not only the commited or the valid ones) you have to use the following command:
	"git reflog"
This command will retrieve all the actions (not only the current commits) of the current branf
To recover one of the branches from this log you need to checkout using the hash
"git checkout to_recover_action_hash"
In this moment if you use "git status" oe "git log" you will see that you are just after this action performed.
However your branch keep with the same temporary number. So you need to create a new one from this point.
"git branch backup"
At this stage you will have a new branch with the recovered branch.

###6.7. Revert changes to a point with historical

Revert will do the same as reset how ever this will maintain the log. So the log will remain and this will act a new commit.
In order to revert to a current committed point you should need the hash
git revert commit-hash


###6.8. Cherry-Picking specific commits from another branch

NOTE: For further explanation you could read the following link:  https://ariejan.net/2010/06/10/cherry-picking-specific-commits-from-another-branch/

Cherry picking in git means to choose a commit from one branch and apply it onto another.
This is in contrast with other ways such as merge and rebase which normally applies many commits onto a another branch.

dd2e86 - 946992 - 9143a9 - a6fd86 - 5a6057 [master]
           \
            76cada - 62ecb3 - b886a0 [feature]
	
1. Checkout the master Branch and apply the commit "62ecb3" of the branch [feature]
git checkout master
git cherry-pick 62ecb3

2. You could also copy the entire log history from 76cada - 62ecb3 to the master 
git checkout -b newbranch 62ecb3
git rebase --onto master 76cada^

###6.9. Differences between Git Revert, Checkout and Reset

These three commands have entirely different purposes. They are not even remotely similar.

"git revert"
This command creates a new commit that undoes the changes from a previous commit. This command adds new history to the project (it doesn't modify existing history).

"git checkout"
This command checks-out content from the repository and puts it in your work tree. It can also have other effects, depending on how the command was invoked. For instance, it can also change which branch you are currently working on. This command doesn't make any changes to the history.

"git reset"
This command is a little more complicated. It actually does a couple of different things depending on how it is invoked. It modifies the index (the so-called "staging area"). Or it changes which commit a branch head is currently pointing at. This command may alter existing history (by changing the commit that a branch references).

"git cherry-pick"

This command let you pick one change from anywhere in the repository and will apply it on your local branch. It is handy if you're on a different branch for any reason but still need that specific change. Be aware that if you cherry-pick without pushing that change that this change is not persistent. It's committed to your local repository but not to the remote (it might be what you need in cases though).

##7. BRANCHES FROM REPOSITORY


>>old way
git branch newbranch
git checkout newbranch

>>new way
git checkout -b newbranch

##8. PULL REQUEST

##9. MERGE COMMITED CHANGES


##10. BASIC WORKFLOW

In your github fork, you need to keep your master branch clean, by clean I mean without any changes, like that you can create at any time a branch from your master. Each time, that you want to commit a bug or a feature, you need to create a branch for it, which will be a copy of your master branch.

When you do a pull request on a branch, you can continue to work on another branch and make another pull request on this other branch.

Before creating a new branch, pull the changes from upstream. Your master needs to be up to date.

Create the branch on your local machine and switch in this branch :

$ git checkout -b [name_of_your_new_branch]

Push the branch on github :

$ git push origin [name_of_your_new_branch]

When you want to commit something in your branch, be sure to be in your branch.

You can see all branches created by using :

$ git branch

Which will show :

* approval_messages
  master
  master_clean

Add a new remote for your branch :

$ git remote add [name_of_your_remote] 

Push changes from your commit into your branch :

$ git push [name_of_your_new_remote] [name_of_your_branch]

Update your branch when the original branch from official repository has been updated :

$ git fetch [name_of_your_remote]

Then you need to apply to merge changes, if your branch is derivated from develop you need to do :

$ git merge [name_of_your_remote]/develop

Delete a branch on your local filesystem :

$ git branch -d [name_of_your_new_branch]

To force the deletion of local branch on your filesystem :

$ git branch -D [name_of_your_new_branch]

Delete the branch on github :

$ git push origin :[name_of_your_new_branch]

##11. FAQ

###11.1 Differences between Git add ., git add -A,git -u /A, git add *
In Git you can use several methods to add your files from Working Folder to the Stage area. 

"Git add -A", will add all the files that are untracked, deleted or modified. This will look at all the files that are locally in the repository independently of the folder you are. 
However you can specify a folder after the sentence, "git add -A /my_folder"  

"Git add ." will add all the files (untracked, deleted or modified) that are inside the current folder and subfolders.


"Git add *" will add al the files untracked and modified. The deleted files since they are no more in the folder, they won't be included.













 


