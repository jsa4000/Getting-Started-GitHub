# The Definitive Guide for Git

This document describes both **basic** and **advanced** functionalities when working with Git. It also provides and Step By Step of how to configure a **Github** account to **clone** it **locally** and start working with **branches**, **tags**, **releases**, etc..

## 1. Introduction

Git is a **source-sode management** tool based on **logs**; also called **Event Sourcing**. All the modifications and changes are written into these logs.

> It's important to define **HEAD** as the pointer for the last log **commit** done into the repositry and **branch**. Whereas the commit has been inside the **master** or a particular **branch**, this pointer **changes** when moving through branches. Git also allows to define an offset when it's neccesay to move using **HEAD** pointer. This is by using **HEAD~X**, where X is the offset to apply to the **HEAD**

Each **log** represents a **snapshot** or **state** of the current repository. Each log also stores a **pointer** to the previous log. Logs are created after the **commit** operation, in this case the ***HEAD** will point to the last commit or change made.

> Each logs are identified by an unique **hash-key** so it can be accessed any time. This is useful to perform operations after the log was created such as **restore**, **tagging**, etcc.

Git stores variables that points into a specifics **commits** or **logs**, also called **pointers**. There are several type of pointers such as: **master**, **branches** and **tags**.

> In other SCM **master** is also called **trunk**. This *root* element, **master** or **trunk**, is unique and allows teams to work into specific projets using the same source-code: this is to be aligned.

As it has been said, **Branches** are pointers to a particular **log**. Branches *always* points to the **last** commited log for that particular branch. This means, once a **branch** is checked-out the ***HEAD** will also point to the last item commited.

## 2. States

Git uses a pipeline to manage the changes done in the source-code. This pipeline differs from other **SCM** such as SVN, Sourcesafe, etc.. And it makes easier to work in a **distributed** way.

The states are the following:

- **Untracked:** there is nothing to track. This state is after a commit is perfored where any changes or files has been added, deleted or modified.

- **UnModified:** There are files in the repository but they haven't been modified from previous state.

- **Modified:** There are files that have been modified. In this case, these files must be **stagged** and then **commited**, so Git could create a Log with the current state.

- **Staged:** This is a state which files has been prepared to be commited. It can be **added** individually or all-at-once. Files that haven't been added to the stage are are not going to be commited.

- **Commited:** this is the last Step of the (local) Pipeline. All the files added into the stage are are going to be commited, creating a new Log with all the changes performed into the **master** or **branch**. Once the **commit** has been performed, pointer will be updated such as **HEAD** and **master/branch**.

Following there is a scheme showing the different states:

    Untracked -> UnModified -> Modified -> Staged (added) -> Commited --
    ^                                                                   |
    |                                                                   |    
    ---------------------------------------------------------------------

> If **not** all **modified** files are staged, the initial state could vary. i.e if some files remain unstaged but modified, the state once has been commited will be **Modified**

### 2.1 Commands

This section show how to move from one state to another:

- Check the current **branch** of the repository. This also tell the current **HEAD** pointer with the last commit performed for that particular branch.

    git branch

    > Once the branch has been changed or checked-out all the changes will be lost. So make sure all your changes have been commited before moving to other branches.

- Check the current **status** of the current branch. If ny changes have been perform previously, this command prompt if the current state for the files: **untracked**, **modified**, **stagged**, etc..

    git status

- **Add** current changes to the Stage Area.

    git add .

    > Individual files can be added manually replacing "." with the file or files to be addded into the stage are to be commited.

- **Commit** current changes into the current **master/branch**

    git commit -m "Message to the commit"

    > In the commit command it can be added a description, tags, etc..

## 3. Remote

Since Git is a **distributed** source-code management, it needs a **centralized** repository that is used for all members working in the same project. This global respository is the **remote** repository; also called bt default **origin**.

Once the repository has been **cloned** locally, the **origin** won't be used unless we specify it. In order to interact with the **remote** repository it can be used commands such as: **fetch**, **pull**, **push** or **checkout**. Remote repositories always use the prefix **remote/branch**, where remote usually is named as **origin** and branch could be **master** or a particular **branch-name**.

### 3.1 Commands

There are several ways to do the samething using Git, and tis depends on the Workflow used by that particular project.

- **clone:** this will clone a remote repository to the current folder, by default the remote repository is named **origin**. To diferenciate branches into **local** and **remote**, the name of the remote is used as a prefix. ie **origin/master**.

    git clone https://github.com/jsa4000/Getting-Started-Microservices.git

- **branch:**: this command can be used to get the **current** branch **checked-out** and also all the current branches in the repository, both **local** and **remotes** branches.

    git branch -a

- **remote:** this command is used to manage remote respositories. 

- **push:** this command will update all the changed and commits done for the current branch into the remote repository.


    
> If no branch has been specified, (e.j. origin or nothing), the **HEAD** pointer will e used for that particular branch.


> Remember **origin/master** and **master** are not the same thing. The first one belongs to the **remote** repository, where **origin** denotes a **remote** repository (could be added more if needed) and **master**, a particular **branch** from the remote repository. On the other hand, **master** is the **local** (cloned) copy of the repository. When the data it's **fetched** from the local repository **origin/master** gets updated, however , it's necessary to use the **merge** command in order to update the **local** master repository to catch up the **HEAD** pointing to the **origin/master**.




## 4. Branches

Branches are basically **pointers** to a particular **commit** or **Log**. Since a Log denotes a partucular **state** of the Respository, this means a **Branch** also stores the state of the current repository at that moment.

Branch is a very **important** concept it Git since it allows to work in a **distributed** way since each feature, issue, etc can be **forked** as a Branch to finally be merged into the **master** or **remote** repository.

To get all branches from the repository use:

    git branch -a

 As it has been said, to checkout (branch + checkout) a particular branch from the repository (**origin/branch**) to a local **branch** directly, it can be used the following command:
 
     git checkout -b issue/CFP-438 origin/master21

> It's neccesary to create a new branch using: **-b issue/ticket-id**.

Also, it can be done manually by using first, **creating** the new branch (automatically it will change to that branch) and checkout the content from a particular branch in the origin.

    git branch issue/CFP-438   
    git checkout origin/master21

Finally, commit the changes locally and start woring normally in the issue

    git add .
    git commit -m "Changes made for he issue"

Finally, when all chanes have beend implemented and tested, push and merge the changes into the proper branch. This branch could be a new branch or usign the same origin/branch from initially.

## 5. Merge

### 5.1 Fast-Forward

### 5.2 Squash

### 5.2 Rebase

### 5.3 Conflicts



## 6. Reset

## 7. Alter

## 8.Tags

## 9. Workflow Strategies


Depending on the members of the team that are involved in the development, some **strategy** will be required for better management and effectiveness.

> https://www.atlassian.com/git/tutorials/comparing-workflows