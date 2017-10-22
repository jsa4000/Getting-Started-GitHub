# The Definitive Guide for Git

This document describes **basic** and **advanced** functionalities when working with Git. It also provides and Step By Step guide of how to configure a **Github** account to **clone** it **locally** and start working with **branches**, **tags**, **releases**, etc..

## 1. Introduction

Git is a **source-sode management** tool based on **logs**; also called **Event Sourcing**. All the modifications and changes are written into these logs.

The **installation** of Git it is very straigh-forward. It consists basically on uncompressing the **package** with the Git version to use, and finally add the folder with the binaries into as a **environment variable**; usually the env. variable is called **path**.

The first time you run **git**, it shows up all the basic commands that it provides:

    usage: git [--version] [--help] [-C <path>] [-c name=value]
            [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
            [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
            [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
            <command> [<args>]

    These are common Git commands used in various situations:

    start a working area (see also: git help tutorial)
    clone      Clone a repository into a new directory
    init       Create an empty Git repository or reinitialize an existing one

    work on the current change (see also: git help everyday)
    add        Add file contents to the index
    mv         Move or rename a file, a directory, or a symlink
    reset      Reset current HEAD to the specified state
    rm         Remove files from the working tree and from the index

    examine the history and state (see also: git help revisions)
    bisect     Use binary search to find the commit that introduced a bug
    grep       Print lines matching a pattern
    log        Show commit logs
    show       Show various types of objects
    status     Show the working tree status

    grow, mark and tweak your common history
    branch     List, create, or delete branches
    checkout   Switch branches or restore working tree files
    commit     Record changes to the repository
    diff       Show changes between commits, commit and working tree, etc
    merge      Join two or more development histories together
    rebase     Reapply commits on top of another base tip
    tag        Create, list, delete or verify a tag object signed with GPG

    collaborate (see also: git help workflows)
    fetch      Download objects and refs from another repository
    pull       Fetch from and integrate with another repository or a local branch
    push       Update remote refs along with associated objects

    'git help -a' and 'git help -g' list available subcommands and some
    concept guides. See 'git help <command>' or 'git help <concept>'
    to read about a specific subcommand or concept.

There exist some (hidden) options such as **hooks** or **pull-request** functionality that can be also done. Following it's provided the usage to perform pull-request for a Fork.

    usage: git request-pull [options] start url [end]

        -p                    show patch text as well

The commands that Git provides are divided into:

- **Initialize** clone, init, remote
- **Change:** add, mv, reset, rm 
- **Profiler:** bisect, grep, log, show, status
- **Local:** branch, checkout, commit, diff, merge, rebase and tag 
- **Collaborate:** fetch, pull, push

## 2. Basic Terminology

Each **log** represents a **snapshot** or **state** of the current repository. Each log also stores a **pointer** to the previous log. Logs are created after the **commit** operation, in this case the ***HEAD** will point to the last commit or change made.

> It's important to define **HEAD** as the pointer for the last log **commit** done into the repositry and **branch**. Whereas the commit has been inside the **master** or a particular **branch**, this pointer **changes** when moving through branches. Git also allows to define an offset when it's neccesay to move using **HEAD** pointer. This is by using **HEAD~X**, where X is the offset to apply to the **HEAD**

Git stores variables that points into a specifics **commits** or **logs**, also called **pointers**. There are several type of pointers such as: **master**, **branches** and **tags**.

> Each logs are identified by an unique **hash-key** so it can be accessed any time. This is useful to perform operations after the log was created such as **restore**, **tagging**, etc.

> In other SCM **master** is also called **trunk**. This *root* element, **master** or **trunk**, is unique and allows teams to work into specific projets using the same source-code: this is to be aligned.

As it has been said, **Branches** are pointers to a particular **log**. Branches *always* points to the **last** commited log for that particular branch. This means, once a **branch** is checked-out the ***HEAD** will also point to the last item commited.

## 3. Basic Workflow

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

### 3.1 Basic Commands

This section show how to move from one state to another:

- Check the current **branch** of the repository. This also tell the current **HEAD** pointer with the last commit performed for that particular branch.

    git branch

    > Once the branch has been changed or checked-out all the changes will be lost. So make sure all your changes have been commited before moving to other branches.

- Check the current **status** of the current branch. If ny changes have been perform previously, this command prompt if the current state for the files: **untracked**, **modified**, **stagged**, etc..

    git status

- **Add** current changes to the Stage Area. Files are considered modified if the file has been **delete**, **modified** or **created**.

    git add .

    > Individual files can be added manually replacing "." with the file or files to be addded into the stage are to be commited.

- **Commit** current changes into the current **master/branch**

    git commit -m "Message to the commit"

    > In the commit command it can be added a description, tags, etc..

- Finally, all commited logs can be listed through the following command:

    git log

> A particular **log** (state) can be **checked-out** using the hash-key: git checkout 2334&3

## 4. Collaborative

Since Git is a **distributed** source-code management, it needs a **centralized** repository that is used for all members working in the same project. This global respository is the **remote** repository; also called bt default **origin**.

Once the repository has been **cloned** locally, the **origin** won't be used unless we specify it. In order to interact with the **remote** repository it can be used commands such as: **fetch**, **pull**, **push** or **checkout**. Remote repositories always use the prefix **remote/branch**, where remote usually is named as **origin** and branch could be **master** or a particular **branch-name**.

### 4.1 Clone Command

In general, there are multiple ways to perform the same action using Git, this depends on the Workflow used by each particular project. In this particular case the remote repository is cloned.

The **clone** command clones a remote repository entirely (branches, logs, tags, etc..) to the current folder, by default the remote repository is named **origin**. To diferenciate branches that belongs to **local** or **remote**, the name of the remote is used as a prefix. i.e. **origin/master**.

    git clone  https://github.com/jsa4000/mytest.git

### 4.2 Branch Command

This command can be used to get the current branch **checked-out**. The user can only see one **branch** t the same time, where all operations are **performed** and **applied**.

    git branch

Also, this command can be used to list all the current branches in the repository, both **local** and **remotes** branches.

    git branch -a

### 4.3 Remote Command

This command is used to manage **remote** respositories. This means it can be added, removed, modified, etc..

To get the current remote/s repository use the following commands:

    git remote
    git remote -v   # To show URLs and operation (fetch and push) assigned for each remote repository.

> No result means there is no remote repository configured yet.

In order to create a Git **local** repository from a **remote** it's needed to **initialize** the folder as a git repository and then **add** the remote repository. Finally, the **pull** command can be used to get all the content.

    git init
    git remote add origin https://github.com/jsa4000/mytest.git
    git pull origin master

Remote repository can be renamed, removed, modified, etc.. to see more commands and how to used them use the following parameter:

    git remote -h

### 4.4 Push Command

This command will update all the changes and commits done for the current branch into the remote repository.

    git push origin master

> If no branch has been specified, (e.j. origin or nothing), the **HEAD** pointer will be used for that particular branch.

This operation **push** into the remote repository configured **origin** the content of the current local **master**.

> Remember **origin/master** and **master** are not the same thing. The first one belongs to the **remote** repository, where **origin** denotes a **remote** repository (could be added more if needed) and **master**, a particular **branch** from the remote repository. On the other hand, **master** is the **local** (cloned) copy of the repository. When the data it's **fetched** from the local repository **origin/master** gets updated, however , it's necessary to use the **merge** command in order to update the **local** master repository to catch up the **HEAD** pointing to the **origin/master**.

**Push** command automatially creates the branch in the remote repository that is pushed locally.

    git push origin new-branch

> This creates a new branch in the remote repository with the same name. Following there is an option to map the local name of the branch to a new remote name.

**Push** command allows to upload content into a different branch onto the remote **origin** by using **local-branch:remote-branch**.

    git push origin master:master2

> If remote branch doesn't exist it will be created in the remote automatically.

With the **push** command is also possible to **remove** branches that exist in the remote repository. 

    git push origin --delete new-branch

> Since **push** command has been designed to work with remote, this cannot be done using **branch** command that is intended to perform operations locally.

If the user hasn't configured **upstream** remote, because the repository has been set manually without using clone. It's needed to set the upstream by using the following command>

    git push --set-upstream origin master
    git push -u origin master               # Sort way

In order to know if the upstream (push) has been correctly configured, the following command must be used:

    git remote -v

    origin  https://github.com/jsa4000/mytest.git (fetch)
    origin  https://github.com/jsa4000/mytest.git (push)  # upstream remote

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

Tags are just **labels** that points to the **previous** commit. This tags can be used to label **releases** or some **points** in the development to be remembered.

> Tags can be seen as a **new** commit since it's performed after the commit of the release. This tag will point to this last commit, so this cannot be changed. Be sure to tag the version or release after merging the changes with the master branch and after the Testing.

A tag can be **created** using two similar ways. The second way it's also called **annotated way**

    git tag v1.0.0
    git tag -a v1.0.0 -m "Message for the current release"

All tags can be listed using the following commands

    git tag
    git tag -l "v1.*"
    git show v1.0.0

Once the tag (or tags) has been created, it is needed to **push** into the remote repository using:

    git push origin v1.0.0
    git push origin --tags

To **delete** tags **locally**, use the following command:

    git tag -d v1.0.0

To **delete** tags in the **remote** repository is similar as branches, since both are just **pointer** to a commit.

    git push origin -d v1.0.0


 A simple workflow could be the following


    git

## 9. Forks

A **fork** is basically a **clone** from one repository to another but in different accounts; it is supported for Github, BitBucket, ect... Both respositories are locally configured as **remote**. **Fork** repository will act as the **origin**, in order to **fetch** and **pull** the data from, and the **original-source** will act as the **upstream** repository to **push** the data to or perform **pull-request** operations.

The workflow is the following for contributors:

1. **Fork** a repository from an account to another account. This is done by using the API from Git provider.

2. **Clone** the **forked** repository locally. By default, **cloned** remote repository (by default **origin**) is used to fetch the data from.

    git clone https://github.com/jsa4000/mytest.git

3. **Add** another remote repository called **upstream** using the URL from the original source-code to push the data to.

    git remote add upstream https://github.com/jsa4000/mytest.git

> The URL in the previous example use the same git remote repository, however this is not a real scenario.

4. Check current **remotes** repositories configured locally.

    git remote -v

    origin  https://github.com/jsa4000/mytest.git (fetch)
    origin  https://github.com/jsa4000/mytest.git (push)
    upstream        https://github.com/jsa4000/mytest.git (fetch)
    upstream        https://github.com/jsa4000/mytest.git (push)

4. **Implement** the features or new functionalities into the local repository.

5. **Push** the changes into remote **origin** repository

    git push origin master

5. Perform a **pull-request** so the changes are integrated into the original source. 

    git request-pull v1.0 upstream master:master_remote    # local_branch:remote_branch, it redirect orgin to the proper branch

    git request-pull HEAD upstream master

> In the example, The operation **pull-request** includes from the **HEAD** in the remote **upstream** to the **HEAD** in local master. This parameter can be: **tag**, **hash-key** or **HEAD~X**.

6. Finally the administrator will **review** the changes made in the **pull-request** operation and decide if the are going to be added.

## 9. Workflow Strategies

Depending on the members of the team that are involved in the development, some **strategy** will be required for better management and effectiveness.

> https://www.atlassian.com/git/tutorials/comparing-workflows