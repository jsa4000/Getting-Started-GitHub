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

###3.3 Fork and Clone an existing repository
	
The Fork in Git it's basically a copy (clone) of a repository into another. After the fork, both repositories are totally independent from each other.  
Forking a repository allows you to freely experiment with changes without affecting the original project. Most commonly, forks are used to either propose 
changes to someone else's project or to use someone else's project as a starting point for your own idea.


##3. GIT CONTEXT STAGE AREA vs REPOSITORY AREA


##4. UDATE THE CONTENT FROM THE SERVER


##5. COMMIT CHANGES



##6. BRANCHES FROM REPOSITORY


##7. PULL REQUEST

##8. MERGE COMMITED CHANGES


##9. BASIC WORKFLOW


##10. FAQ
