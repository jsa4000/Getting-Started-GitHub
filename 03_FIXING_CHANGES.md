#Fixing Mistakes and Undoing Bad Commits

##1 Basic Commands

For this section there are some basic commands you need to know:

- **git branch** this command will list all the branches that currently are in the repository. The selected item is the current branch checked out.
- **git status** this command give the current status of the current branch. The information are related to the current files in the stage area, uncommited changes, untracked files, etc..
- **git log** this command is used to get all the commits done in the current branch. Basically this is the historical of your repository. 
	> - You need to know that every change and commit have different hash or "Id". Including the command --amend is going to give you different hash.
	> - In case you don't want to change the commit (overwrite), you need to use the "--amend" parameter in the commit command.
	> - use "git log --stat" to get more detailed view of the changes made.
- **git reflog** this will print all the commits and actions done in the current branch. As said, this will include all ctions, including, rest, revert, amend, etc..
 	> - This command is used to recover branches that have been deleted by mistake.
 	> - This log is deleted monthly by Git for maintenance tasks.
- **git diff** and **git difftool**, these commands are used to get the differences between some branches or commits done in the remote.
- **git merge** and **git mergetool**, these commands are used to merge between branches (remote and local).

##2 Options

##2.1 Undo a File

In order to get back to the current HEAD version of a specific file, you need to use the following command: 
	
	git checkout your_file

Another methof to unstage the current state is:

	git reset HEAD "<file>..."

After this command, the file will be back at the same state as previous commit.


###2.2 Modify the comment of previous commit

This case must be used in order to modify the message written in previous commit without alter the log history of the repository. Note that the Hash of the commit will also change after this operation.

	git commit --amend -m "Override the previous comment"

###2.3 Change Pevious Commit.

This is used when a modification need to be done for previous commit.

	git add .
	git commit --amend

Git will prompt the committed changes and the previous comment, so it can be modified if needed.
Type *":wq"* to write and quit. This is a command from vi.

###2.4 Reset the repository to a Commit point.

This is used to revert the repository to a certain commit. (Similar to a Restore point)
The hash of the commit is needed to perform this operation.

There are 3 several ways to reset the repository to a certain point: "--soft", "--mixed" and "--hard".

The command to reset the repository is as follows:
	"git reset --soft commit-hash"
 
	Where commit-hash is the first (eight for example) numbers of the commit (e.j. d5f5a722ba9)
		commit d5f5a722ba95f9a914d8db3a8ac226c3d1d7bfcd
		Author: jsa4000 <jsa4000@gmail.com>
		Date:   Mon Jan 30 16:42:50 2017 +0100

The differences between those parameters depend on the status of the current reset regarding the staged files.
In some cases you want to reset totally to an specific commited branch (hard), or sometimes you need to add some more files or do some modification after do the commit again. 

###2.5 Clean Modified files or Untracked files from Commit.

When you use ***git status***, you see all the files untracked or modified that are not commited or pushed yet.
Sometimes you need to remove these files from the current commit. 

>For example, you have added some files, but you don't neccesay need them for this commit. 

The command to clean these changes is:
	
	git clean -df

###2.6 Recover Deleted Branches or Commits

This is used to recover a branch that has been totally deleted from the log.
Following command is used to see all the operations done in the respository:
	
	git reflog
	
To recover one of the branches from this log you need to checkout using the Hash.

	git checkout to_recover_action_hash
	
After the checkout, you can use ***"git status"*** or ***"git log"***, to see the current status after this action.
However the checked branch will keep with the same temporary number. So you need to create a new one from this point.
	
	git branch backup
	
At this stage you will have a new branch with the recovered branch.

###2.7 Revert changes with Log

By using ***revert*** the outcomes obtained will be very similar as using the command ***reset***. However, the log is not going to be *"reverted"* so it will be logged as a new commit in the historical.
>In order to revert to a current committed point you should need the Hash.
	
	git revert commit-hash

###2.8 Cherry-Picking specific Commits

Cherry picking in git means to choose a commit from one branch and apply it onto another.
This is in contrast with other ways such as merge and rebase which normally applies many commits onto a another branch.

	dd2e86 - 946992 - 9143a9 - a6fd86 - 5a6057 [master]
			\
				76cada - 62ecb3 - b886a0 [feature]
	
1. Checkout the master Branch and apply the commit *"62ecb3"* of the branch [feature]

		git checkout master
 		git cherry-pick 62ecb3

2. You could also copy the entire log history from *"76cada - 62ecb3"* commits from the current bracnh to the master 

		git checkout -b newbranch 62ecb3
 		git rebase --onto master 76cada^

It is handy if you're on a different branch for any reason but still need that specific change. Be aware that if you cherry-pick without pushing that change that this change is not persistent. It's committed to your local repository but not to the remote (it might be what you need in cases though).

>For further explanation you could read the following link:  https://ariejan.net/2010/06/10/cherry-picking-specific-commits-from-another-branch/
	

###2.9 Differences between revert, checkout and reset

These three commands have entirely different purposes.

- **git revert** This command creates a new commit that undoes the changes from a previous commit. This command adds new history to the project (it doesn't modify existing history).

- **git checkout** This command checks-out content from the repository and puts it in your work tree. It can also have other effects, depending on how the command was invoked. For instance, it can also change which branch you are currently working on. This command doesn't make any changes to the history.

- **git reset** This command is a little more complicated. It actually does a couple of different things depending on how it is invoked. It modifies the index (the so-called "staging area"). Or it changes which commit a branch head is currently pointing at. This command may alter existing history (by changing the commit that a branch references).

##3. References

- Tutorial on youtube with a very detailed information: https://www.youtube.com/watch?v=FdZecVxzJbk
- Lecture related to this topic: https://davidzych.com/difference-between-git-reset-soft-mixed-and-hard/
