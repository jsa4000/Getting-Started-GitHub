#Fixing mistakes and undoing bad Commits

##1 Basic Commands

For this section there are some basic commands you need to know:

- **"git branch"** this tell you all the branches you currently have in the repository. The selected are your current (checkout) branch.
- **"git status"** this is going to tell you the current status of your branch, stage area, uncommited changes, etc..
- **"git log"** this will print all the commits done in the current branch. Basically this is the historical of your repository. 
	
	> - You need to know that every change and commit have different hash or "Id". Including the command --amend is going to give you different hash.
	> - In case you don't want to change the commit (overwrite), you need to use the "--amend" parameter in the commit command.
	> - use "git log --stat" to get more detailed view of the changes made.
- **"git reflog"** this will print all the commits and actions done in the current bracnh. This will include all the actions, including, rest, revert, amend, etc..
 	
	> - This command is used to recover some branches that you deleted by mistake.
 	> - This log are deleted monthly by Git for maintenance task.
- **"git diff"**, by using this command you could get the differences between some branches or commits.

##2 Options
##1 Undo a File from current change.

In order to get back to and old version of a file that have been modified: git checkout your_file
This action will undo the changes of that file.

###2.1 Modify the comment of the previous commit without alter the history. 

This case is to modify the previous commit done. Note that the Hash of the commit will also change after this operation.
 In order to do tha the command is the following:

git commit --amend -m "Override the previous comment"


###2.2 Change committed files from the previous commit without create a new one.


git add .
git commit --amend

Git will prompt the committed changes and the previous comment, so it can be modified if needed.
Type ":wq" to write and quit. This is a command from vi.


###2.3 Reset the repository to a Commit point.


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

###2.4 Clean modified files or untracked files from Commit.


When you use "git status", you are going to see all the files untracked or changed for the future commit.
Some times you need to remove these files from the commit. For example you have added some files, but you don't neccesay needed them for this commit. 
The command to clean these changes is:
git clean -df


###2.5 Recover deleted branch or Commit from historical reference log.


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

###2.6 Revert changes to a point with historical.


Revert will do the same as reset how ever this will maintain the log. So the log will remain and this will act a new commit.
In order to revert to a current committed point you should need the hash
git revert commit-hash


###2.7 Cherry-Picking specific commits from another branch to the current.


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

###2.8 Differences between Git Revert, Checkout and Reset.

These three commands have entirely different purposes. They are not even remotely similar.

"git revert"
This command creates a new commit that undoes the changes from a previous commit. This command adds new history to the project (it doesn't modify existing history).

"git checkout"
This command checks-out content from the repository and puts it in your work tree. It can also have other effects, depending on how the command was invoked. For instance, it can also change which branch you are currently working on. This command doesn't make any changes to the history.

"git reset"
This command is a little more complicated. It actually does a couple of different things depending on how it is invoked. It modifies the index (the so-called "staging area"). Or it changes which commit a branch head is currently pointing at. This command may alter existing history (by changing the commit that a branch references).

"git cherry-pick"

This command let you pick one change from anywhere in the repository and will apply it on your local branch. It is handy if you're on a different branch for any reason but still need that specific change. Be aware that if you cherry-pick without pushing that change that this change is not persistent. It's committed to your local repository but not to the remote (it might be what you need in cases though).

##3. References

- A very good tutorial on youtube with the same materials is https://www.youtube.com/watch?v=FdZecVxzJbk
- Also this link could be a very good lecture for this topic: https://davidzych.com/difference-between-git-reset-soft-mixed-and-hard/
