#  Getting Started into GitHub

## Overview

This repository is intended to go through different **Workflows** and **Tips** working with Git. Aslo, we will be using **Github** for Git remote repository.
 
## Differences between Git and GitHub

First at all, we are going to talk about the main differences between Git and GitHub, since both are misunderstood for some people.
	
### Git

>"Git is a free and **open source distributed version control system** designed to handle everything from small to very large projects with speed and efficiency"
	
Git is a distributed peer-peer version control system. Each node in the network is a **peer**, storing entire repositories which can also act as a multi-node distributed **back-ups**. There is no specific concept of a central server although nodes can be head-less or 'bare', taking on a role similar to the central server in centralised version control systems.

	
### GitHub
			
>"Github provides access control and several collaboration features such as wikis, task management, and bug tracking and feature requests for every project.
	
## Git Explained	
	
>*NOTE:* Following explanation has been extracted from the following link: https://juristr.com/blog/2013/04/git-explained/
	
How is Git different from other VCS (Version Control Systems)? Probably the most obvious difference is that Git is distributed (unlike SVN or TFS for instance). This means, you’ll have a local repository which lives inside a special folder named .git and you’ll normally (but not necessarily) have a remote, central repository where different collaborators may contribute their code. Note that each of those contributors has an exact clone of the repository on their local workstation.

Git itself can be imagined as something that sits on top of your file system and manipulates files. Even better, you can imagine Git as a tree structure where each commit creates a new node in that tree. Nearly all Git commands actually serve to navigate on this tree and to manipulate it accordingly.
Git repository should be seen from the point of view of the tree it constructs. 

![alt text](http://git-scm.com/figures/18333fig0106-tn.png "Git Local Workflow")

## Terminology

- **master**: the repository’s main branch. Depending on the work flow it is the one people work on or the one where the integration happens
- **clone**: copies an existing git repository, normally from some remote location to your local environment.
- **commit**: submitting files to the repository (the local one); in other VCS it is often referred to as “checkin”
- **fetch or pull**: is like “update” or “get latest” in other VCS. The difference between fetch and pull is that pull combines both, fetching the latest code from a remote repo as well as performs the merging.
- **push**: is used to submit the code to a remote repository
- **remote**: these are “remote” locations of your repository, normally on some central server.
- **SHA**: every commit or node in the Git tree is identified by a unique SHA key. You can use them in various commands in order to manipulate a specific node.
- **head**: is a reference to the node to which our working space of the repository currently points.
- **branch**:is just like in other VCS with the difference that a branch in Git is actually nothing more special than a particular label on a given node. It is not a physical copy of the files as in other popular VCS.








 


