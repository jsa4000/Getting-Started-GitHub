
#Workflow

In this document, I will describe the basic procedure working with a distributed repository like GitHub, dealing with respositories, branches, update, commits, etc.. These guidelines will depend on the type of project and number of people you are working with.

##1. Branches

Firstly, you must have a repository already **created**.

*_In order to create your repository, you can use one of the creation methods in the [Installation document](https://github.com/jsa4000/Getting-Started-GitHub/blob/master/01_INSTALLATION.md)_*

***The Golder Rule for every GitHub repository, is to keep your master branches clean. By clean, I mean without any changes, like that you can create at any time a branch from your master. Each time, that you want to commit a bug or a feature, you need to create a branch for it, which will be a copy of your master branch.***

When you do a **pull request** on a branch, you can continue to work on another branch and make another pull request on this other branch.

###1.1 Creation

*In order to create a new branch, be sure you pull the changes from the _upstream_ to your master, if it needs to be up to date.*

Firstly, create a branch on your local machine and switch to it. There are several ways to create them:

- New way, that automatically creates a branch and do the checkout:

		git checkout -b [name_of_your_new_branch]
	
- Old way, that you have to create a branch and finally do the checkout:

 		git branch [name_of_your_new_branch]
 		git checkout newbranch

Secondly, push the branch onto GitHub. (_In order to commit something in your branch, be sure to be inside_).

	git push origin [name_of_your_new_branch]


You can see all branches created by using :

	git branch

 Which will show :

  >	approval_messages
  
  > 	master
  
  > 	master_clean

Finally, **add** a new **remote repositoty** to your new branch. This remote repository will be used to fetch (_update_) or commit (_pull-request_) depending on your needs.

	git remote add [name_of_your_remote] [url_remote_ropsitory]
	
ej.

	git remote add upstream https://github.com/octocat/Spoon-Knife

>Usually, **origin** and **upstream** will be common names that you would use to configure your remote repositories. 

###1.2 Update

In order to do a commit from your local branch to your remote repositry, you have to use the command **push**. This command will upload your changes from your current commit. The remote repository that you would use is the new remote repository you added in previuos step (**upstream**). The main steps to perform this opeartion are:

	git checkout develop
	git add .
	git commit -m "Some message to this commit"
	git push [name_of_your_new_remote] [name_of_your_branch]
	
>ej.	git push upstream develop

Update your branch when the original branch from official repository has been updated :

	git fetch [name_of_your_remote]

Then you need to apply to merge changes, if your branch is derivated from develop you need to do :

	git merge [name_of_your_remote]/develop
	
###1.3 Local vs Remote-local Branches
	
When you use the fetch command the changes will be on your **remote-local branches** that will differs from your **local branches**. 

For example, supose you already have a branch called _"develop"_, then you fetch from a remote branch called _"origin"_. 

	git fetch origin develop

The fetch command is going to copy the changes into a temporary **local remote-branch** that will be called _"origin/develop"_. In order to merge your fetched branch (_"origin/develop"_) to the current branch (_"develop"_) yo have to use the following commands:

	git checkout develop
	git merge origin/develop

![alt text](https://git-scm.com/book/en/v2/images/remote-branches-1.png "Git Local/Remote Bracnhes")


###1.3 Delete

The final step, will be the removal of the branch on your **local** filesystem :

	git branch -d [name_of_your_new_branch]

To force the deletion of a local branch, use instead _"-D"_ :

	git branch -D [name_of_your_new_branch]

Finally, delete the branch on **GitHub** :

	git push origin :[name_of_your_new_branch]


##2. Advanced Workflows 

###2.1 Merge vs Rebase

When you use **rebase**, you tell Git to make it look as though you checked out their branch cleanly, then did all your work starting from there. That makes a clean, conceptually simple package of changes that someone can review. You can repeat this process again when there are new changes on their branch, and you will always end up with a clean set of changes "on the tip" of their branch. This will create a linear history of commits from the merged branches.
 
When you use **merge**,  you tie the two branch histories together at this point. If you do this again later with more changes, you begin to create an interleaved thread of histories: some of their changes, some of my changes, some of their changes. Some people find this messy or undesirable.

![alt text](http://hostingadvice.digitalbrandsinc.netdna-cdn.com/wp-content/uploads/2014/12/git-merge.gif "Git Merge vs Rebase")

Once you understand what rebasing is, the most important thing to learn is when not to do it. The **Golden Rule** of git rebase is to ***never use it on public branches***.

>If you would prefer a clean, linear history free of unnecessary merge commits, you should reach for git rebase instead of git merge when integrating changes from another branch.
>
>On the other hand, if you want to preserve the complete history of your project and avoid the risk of re-writing public commits, you can stick with git merge. Either option is perfectly valid, but at least now you have the option of leveraging the benefits of git rebase.


###2.2 Differences between Git add ., git add -A,git -u /A, git add *

In Git you can use several methods to add your files from Working Folder to the Stage area. 

- **Git add -A** this command will add all the files that are untracked, deleted or modified. This will look at all the files that are locally in the repository independently of the folder you are.  However you can specify a folder after the sentence, 
	"git add -A /my_folder"  

- **Git add .** this command will add all the files (untracked, deleted or modified) that are inside the current folder and subfolders.

- **Git add *** this command will add al the files untracked and modified. The deleted files since they are no more in the folder, they won't be included.


###2.3 Pull vs Fetch
	
In order to update the current repository with another branch or remote repository, you need to know some different ways that will depend on your workflow or complexity of the changes you need to add or merge.

There are two ways to update the current branch with another, this update doesn't necesary mean that the changes will be automatically merged. So, you have to decide if you want to see the differencess (dif) first or let Git to merge automatically the changes.

Runs **git-pull** means Fetch from and Merge with another repository or a local branch.	With --rebase, calls git-rebase instead of git-merge.

> Rebase will mean the changes that are retrieved from the remote server are firstly taken into consideration. So the merge are done upon this update opeation.

Runs **git-fetch** with the given parameters, and calls git-merge to merge the retrieved head(s) into the current branch. 

>In the simplest terms, **git pull** does a **git fetch** followed by a **git merge**. Fetch it's a more **controlled** way to see the changes prior to do the merge operation.
	
- Simple Workflow to update a repository using pull:

			git pull origin master
			git checkout foo-branch
			git rebase master
			git push origin foo-branch
	
- Simple Workflow to update a repository using fetch:
	
			git checkout master                                                  
			git fetch                                        
			git diff origin/master
			git rebase origin master

>Sometimes the fastest way to update the respository is just by using the following command:
>	
>		git pull --rebase
	

##3. References

- https://juristr.com/blog/2013/04/git-explained/
- http://rogerdudler.github.io/git-guide/
- https://es.atlassian.com/git/tutorials/svn-to-git-prepping-your-team-migration
- https://git-scm.com/book/en/v2/Getting-Started-Git-Basics
- https://blog.udemy.com/git-tutorial-a-comprehensive-guide/

 


