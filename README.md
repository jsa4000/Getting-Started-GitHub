#  Getting Started in GitHub

0. ##OVERVIEW.

	In the next chapters I'm going to go through basic **Workflows** currently used in Computer Science.
	Current workflows are going to be based in **Git** and **Github** for source-code and web hosting repository.
 
1. ##HISTORY. (Git vs GitHub)

	This is a topic that people often confuse a lot. I'm talking about the main differences between Git and GitHub since both words are totally different from each other.
	
	1.1 ###Git 
	
		"Git is a free and **open source distributed version control system** designed to handle everything from small to very large projects with speed and efficiency"
		
		Git is a distributed peer-peer version control system. Each node in the network is a peer, storing entire repositories which can also act as a multi-node 
		distributed back-ups. There is no specific concept of a central server although nodes can be head-less or 'bare', taking on a role similar to the central 
		server in centralised version control systems.
		
		Git works as a **local repository**. However, it acts as **Back-up** for distributed repository version control system.
		
	1.2 ###GitHub
		
		"GitHub is a **web-based Git repository hosting service**, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features."

		Github provides access control and several collaboration features such as wikis, task management, and bug tracking and feature requests for every project.
	
		
2. ##INSTALLING GIT

	2.2 ###Installing on Linux

		If you want to install the basic Git tools on Linux via a binary installer, you can generally do so through the basic package-management tool that comes with your distribution. If you’re on Fedora for example, you can use yum:

		$ sudo yum install git-all

		If you’re on a Debian-based distribution like Ubuntu, try apt-get:

		$ sudo apt-get install git-all

		For more options, there are instructions for installing on several different Unix flavors on the Git website, at http://git-scm.com/download/linux.


	2.1 ### Installing on Windows
	
		There are also a few ways to install Git on Windows. The most official build is available for download on the Git website. Just go to http://git-scm.com/download/win and the download will start automatically. Note that this is a project called Git for Windows, which is separate from Git itself; for more information on it, go to https://git-for-windows.github.io/.

		To get an automated installation you can use the Git Chocolatey package. Note that the Chocolatey package is community maintained.

		Another easy way to get Git installed is by installing GitHub for Windows. The installer includes a command line version of Git as well as the GUI. It also works well with Powershell, and sets up solid credential caching and sane CRLF settings. We’ll learn more about those things a little later, but suffice it to say they’re things you want. You can download this from the GitHub for Windows website, at http://windows.github.com.

		The installation of Github on Windows requires a Global variable to access to the main "git.exe" executable globally. In order to do this it's necessary to add the Path of the current executable versión of Git. In my case it was:
		
			"C:\Program Files\Github\mingw64\bin"
			
		To access from Comman line to the main control panel on windows (without Admin privileges) :
		
			"rundll32 sysdm.cpl,EditEnvironmentVariables"
		

3. ##CONFIGURING THE PROJECT

	In order to configure your Git repository you have several choices.
	
	3.1 Create a new Repository.
	
		In order to create a new repository, the main workflow will be:
		
			- First create a local repository in the local machine , adding all the structure and necessary files.
			- Create some constraints (.gitignore) and initial files 
			emote repository, in this case a GitHub origin.
	
	3.2 Clone an existing repository
	
	3.3 Fork and Clone an existing repository
	


3. ##GIT CONTEXT STAGE AREA vs REPOSITORY AREA


4. ##UDATE THE CONTENT FROM THE SERVER


5. ##COMMIT CHANGES



6. ##BRANCHES FROM REPOSITORY


7. ##PULL REQUEST

8. ##MERGE COMMITED CHANGES


9. ##BASIC WORKFLOW


10. ##FAQ