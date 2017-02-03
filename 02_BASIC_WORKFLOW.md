
#Workflow

In this document, I will describe the basic procedure working with a distributed repository like GitHub, dealing with respositories, branches, update, commits, etc.. These guidelines will depend on the type of project and number of people you are working with.

##1. Branches

Firstly, you must have a repository already **created**.

*_In order to create your repository, you can use one of the creation methods in the [Installation document](https://github.com/jsa4000/Getting-Started-GitHub/blob/master/01_INSTALLATION.md)_*

***The Golder Rule for every GitHub repository, is to keep your master branches clean. By clean, I mean without any changes, like that you can create at any time a branch from your master. Each time, that you want to commit a bug or a feature, you need to create a branch for it, which will be a copy of your master branch.***

When you do a **pull request** on a branch, you can continue to work on another branch and make another pull request on this other branch.

###1.1 Creation

In order to create a new branch, be sure you pull the changes from the up stream to your if it needs to be up to date.

Firstly, create a branch on your local machine and switch to it. There are several ways to create them:

- New way that automatically creates the branch and do the checkout:

		git checkout -b [name_of_your_new_branch]
	
- Old way, that you have to first, create the bracnh and finally, do the checkout to that branch:

 		git branch [name_of_your_new_branch]
 		git checkout newbranch

Secondly, push the branch onto GitHub. (_In order to commit something in your branch, be sure to be in your branch_).

	git push origin [name_of_your_new_branch]


You can see all branches created by using :

	git branch

 Which will show :

 >	* approval_messages
 
 > 	 master
 
 > 	 master_clean

Finally, **add** a new **remote repositoty** to your new branch. This remote repository will be used to fetch (_update_) or commit (_pull-request_) depending on your needs.

	git remote add [name_of_your_remote] [url_remote_ropsitory]
	
ej.

	git remote add upstream https://github.com/octocat/Spoon-Knife

>Usually, **origin** and **upstream** will be common names that you would use to configure your remote repositories. 

###1.2 Update

In order to commits your changes from your local bracnh to your remote repositry, you have to **push** your changes from your current commit. The remote repository will be the new **upstream** you added in previuos step:

	git checkout develop
	git add .
	git commit -m "Some message to this commit"
	git push [name_of_your_new_remote] [name_of_your_branch]
	
>ej.	git push upstream develop

Update your branch when the original branch from official repository has been updated :

	git fetch [name_of_your_remote]

Then you need to apply to merge changes, if your branch is derivated from develop you need to do :

	git merge [name_of_your_remote]/develop
	
>When you use the fetch command the changes will be on your **remote-local branches** that will differs from your **local branches**. 

For example, supose you already have a branch called "develop", then you fetch from a remote branch called "origin". 

	git fetch origin develop

Finally, this fetch is going to be copied to your temporary **local remote-branch** that will be origin/develop. In order to merge the local branch (develop) to your fetched bracnh (origin/develop) you need to checkout your develop branch that you want to merge with the local remote branch and finally.

	git merge origin/develop

![alt text](https://git-scm.com/book/en/v2/images/remote-branches-1.png "Git Local/Remote Bracnhes")


Delete a branch on your local filesystem :

	git branch -d [name_of_your_new_branch]

To force the deletion of local branch on your filesystem :

	git branch -D [name_of_your_new_branch]

Delete the branch on github :

	git push origin :[name_of_your_new_branch]


###1.2 Merge vs Rebase

When you rebase your branch onto their branch, you tell Git to make it look as though you checked out their branch cleanly, then did all your work starting from there. That makes a clean, conceptually simple package of changes that someone can review. You can repeat this process again when there are new changes on their branch, and you will always end up with a clean set of changes "on the tip" of their branch.
 
 https://wac-cdn.atlassian.com/dam/jcr:5b153a22-38be-40d0-aec8-5f2fffc771e5/03.svg?cdnVersion=ex
 
When you merge their branch into your branch, you tie the two branch histories together at this point. If you do this again later with more changes, you begin to create an interleaved thread of histories: some of their changes, some of my changes, some of their changes. Some people find this messy or undesirable.

![alt text](http://hostingadvice.digitalbrandsinc.netdna-cdn.com/wp-content/uploads/2014/12/git-merge.gif "Git Merge vs Rebase")

https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg?cdnVersion=ex

The Golden Rule of Rebasing

Once you understand what rebasing is, the most important thing to learn is when not to do it. The golden rule of git rebase is to never use it on public branches.

Resumen

And that’s all you really need to know to start rebasing your branches. If you would prefer a clean, linear history free of unnecessary merge commits, you should reach for git rebase instead of git merge when integrating changes from another branch.

On the other hand, if you want to preserve the complete history of your project and avoid the risk of re-writing public commits, you can stick with git merge. Either option is perfectly valid, but at least now you have the option of leveraging the benefits of git rebase.



##2. Differences between Git add ., git add -A,git -u /A, git add *

In Git you can use several methods to add your files from Working Folder to the Stage area. 

"Git add -A", will add all the files that are untracked, deleted or modified. This will look at all the files that are locally in the repository independently of the folder you are. 
However you can specify a folder after the sentence, "git add -A /my_folder"  

"Git add ." will add all the files (untracked, deleted or modified) that are inside the current folder and subfolders.


"Git add *" will add al the files untracked and modified. The deleted files since they are no more in the folder, they won't be included.




#5. UDATE THE CONTENT FROM THE SERVER (PULL vs FETCH)
	
	
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
		

##References

- https://juristr.com/blog/2013/04/git-explained/
- http://rogerdudler.github.io/git-guide/
- https://es.atlassian.com/git/tutorials/svn-to-git-prepping-your-team-migration
- https://git-scm.com/book/en/v2/Getting-Started-Git-Basics
- https://blog.udemy.com/git-tutorial-a-comprehensive-guide/

 


