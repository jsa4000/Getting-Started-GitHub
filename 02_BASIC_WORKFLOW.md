

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
		
	

#8. BRANCHES FROM REPOSITORY


>>old way
git branch newbranch
git checkout newbranch

>>new way
git checkout -b newbranch
	

#11. BASIC WORKFLOW


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

#12. FAQ

##12.1 Differences between Git add ., git add -A,git -u /A, git add *

In Git you can use several methods to add your files from Working Folder to the Stage area. 

"Git add -A", will add all the files that are untracked, deleted or modified. This will look at all the files that are locally in the repository independently of the folder you are. 
However you can specify a folder after the sentence, "git add -A /my_folder"  

"Git add ." will add all the files (untracked, deleted or modified) that are inside the current folder and subfolders.


"Git add *" will add al the files untracked and modified. The deleted files since they are no more in the folder, they won't be included.














 

