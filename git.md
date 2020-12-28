
## **Git Cheat Sheet**

```
Configuration
```

| Command | Description |
| :------- | :----------- |
| `$ git config --list  ` | git configuration listing |
| `$ git config --global user.name "jp"` | Configure user name |
| `$ git config --global help.autocorrect 1` | enable auto correction | 
| `$ git config --global user.email "jp@gmail.com"` | configure user email address |
| `$ git config --global alias.hist "log --one-line --all --graph --decorate"` | creating an alias 'git hist' to display git logs |
| `$ git config --global alias.gc "gc --prune=now --aggressive"` | garbage collection and optimizing the repo |

</br>

```
Basics
```
| Command | Description |
| ------- | ----------- |
| `$ git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |
| `$ git init` | Initialize a local Git repository |
| `$ git add [file-name.txt]` | Add a file to the staging area |
| `$ git status` | Check status |
| `$ git commit -a -m "add files and commit in same command"` | Add files and commit in a single command|
| `$ git add remote origin https://github.com/jrpamid/reponame.git` | add a remote repo as origin |
| `$ git push -u origin master `| push local master branch to  remote origin same branch name |
| `$ git commit  --amend`| Fix last wrong commit message |
| `$ git rm -rf [file-name]` | Remove a file/folder forcefully from staging|
| `$ git rm --dry-run *` | Just a dry-run, no actual delete |
| `$ git ls-files -s` | Debug uility for  inspecting the staging index tree. |
| `$ git show <commit_id>` | Show meta data and details about a specific commit |

</br>

```
 Branching & Merging ( Every branch must be updated and  managed individually )
```
| Command | Description |
| ------- | ----------- |
| `$ git branch` | List branches (the asterisk denotes the current branch) |
| `$ git branch -a` | List all branches (local and remote) |
| `$ git branch -d [branch name]` | Delete a branch |
| `$ git push -d origin [branch name]` | Delete a remote branch |
| `$ git checkout -b [branch name]` | Create a new branch from current branch and switch to it |
| `$ git checkout -b [new feature branch name] [from src branch name]` | create a new branch from  a specified branch and checkout |
| `$ git checkout -b [branch name] origin/[branch name]` | Checkout a remote branch and switch to it |
| `$ git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `$ git checkout [branch name]` | Switch to a branch |
| `$ git checkout -- [file-name.txt]` | Discard changes to a file |
| `$ git merge [branch_name]` | Merge a branch into the active branch |
| `$ git merge [source_branch] [target_branch]` | Merge a branch into a target branch |
| `$ git merge -no-ff [the feature branch] ` | Merges a feature branch with active branch, no fast forward merge is done. Feature branch history is maintained. If fast forward merge is  done, the commit history is lost |
| `$ git stash` | Stash changes in a dirty working directory |
| `$ git stash clear` | Remove all stashed entries |

</br>

```
Merge & Rebase 

Merge and Rebase are 2 ways to integrate changes from one branch to  another.
* A merge results in a new commit, with changes that have occurred in the merged branch and master.
* A  merge commut results in a cluttered git logs, and  makes it difficult to understand the project flow.
* A merge commit should be used in cases where the commit should stand out. Should be reserved for large refactors, major commits etc.
* A merge commit preserves history where as a  rebase rewrites it.

* rebasing can be understood as “moving the base of a branch onto a different position”. When bringing in a mster branch changes into a feature branch its better to  rebase than merge.
* A rebase doesnt create  a new commit.
* A rebase results in a  clean, linear code commit history/logs.
* Rebasing doesnt work with PUll  request.
```
| Command | Description | 
| ------- | ----------- |
| `$ git checkout  feature-branch01` | Checkout to the feature branch |
| `$ git merge master ` | Merge the master branch to the feature-branch01 to bring the master updates to feature-branch01 |
| `$ git merge -no-ff [the feature branch] ` | Merges a feature branch with active branch, no fast forward merge is done. Feature branch history is maintained. If fast forward merge is  done, the commit history is lost |
| `$ git rebase master` | rebase feature-branch01 with master branch  |

</br>

```
Sharing & Updating Projects 
```
| Command | Description |
| ------- | ----------- |
| `$ git push origin [branch name]` | Push a branch to your remote repository |
| `$ git push -u origin [branch name]` | Push changes to remote repository (and remember/track the branch) |
| `$ git push` | Push changes to remote repository (remembered/tracked branch) |
| `$ git push -d [branch name]` | Delete a remote branch |
| `$ git pull origin` | Update local repository to the newest commit. pull = fetch + merge |
| `$ git pull origin [branch name]` | Pull changes from speified remote branch |
| `$ git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `$ git remote remove origin` | Remove a remote repository |
| `$ git remote rename origin origin1` | Rename a remote repository |
| `$ git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |
 

</br> 

```
Revert & Reset 

* Revert rolls back  any changes committed. A  revert creates a new  commit in the history.
* Reset has 3 modes --soft, --hard, --mixed (defaut  mixed)
```
| Command | Description |
| ------- | ----------- |
| `$ git reset HEAD~ `| revert the last commit |
| `$ git reset <commit>` | moves the HEAD and refs t |
| `$ git reset --hard <commit id>` | 
| `$ git revert HEAD~` | creates a new commit by moving the HEAD to previous commit |
| `$ git revert <commmitid>` | creates a new commit by moving HEAD to specified commit id |

</br>

``` 
Inspection & Comparison
```
| Command | Description |
| ------- | ----------- |
| `$ git log` | View changes |
| `$ git log -10` | view only last 10 commits |
| `$ git log --summary` | View changes (detailed) |
| `$ git log --oneline --decorate --graph --all` | detailed,coloured one line log info | 
| `$ git diff [source branch] [target branch]` | Preview changes before merging |
| `$ git diff  --staged ` | lists all the changes between staged area  and local repo. |
| `$ git diff` | lists the changes between working dir and staged area |


</br>

``` 
Tagging
```
| Command | Description |
| ------- | ----------- |
| `$ git tag -a release1.1.0 -m "release 1.1.0 on in q1" <COMMITID/HEAD> ` | tagging a specific commit or head with a tag |
| `$ git tag `| | list the tags |
| `$ git show release1.1.0` | get details of a specific release | 
| `$ git tag -d release1.1.0` | delete a tag |
| `$ git push origin release1.1.0`| push a tag to  repo |

</br>

```
Misc & Advance git commands
```
| Command | Description |
| ------- | ----------- |
| `$ git fsck ` | run a file system check and identify corrupted or dangling commits |
| `$ git show <branch_name>:<file_name> ` | cat/read a specific file from a specified branch |
| `$ git grep "image: jrpamid"  ` | unix like grep on files in the current active branch |
| `$ git rev-list --all | xargs git grep -F 'image: jrpamid'` | execute a grep command across the repo (all branches and commits) |  

</br>

## **GitFlow Branching Model**
![Branching Model](pics/git-model.png)


## *Feature branch workflow*
* feature branch work starts off from the develop branch

```bash
# create a new  feature branch from the develop branch
$ git checkout -b feature-021 develop

# after feature done merge to develop branch
$ git checkout develop
# merge the feature branch to develop
$ git merge --no-ff feature-021
$ git push origin develop
# feature branches are short lived  and can be deleted. not tracked  on remote repo
$ git branch -d feature-021
```


## *Release branch workflow*
* release branch - can branch off develop  branch.
* prep for a prod release. last minute work for prod release. preparing release meta data.
* develop  branch gets freed up for next release.
* must  merge back to master.
* naming convention release-*

```bash
# branching from the develop 
$ git checkout -b release-01212010 develop

# after meta data fixes, release prep work done.
$ git checkout master
$ git merge --no-ff release-01212020

# tag the release in amster branch
$ git tag -a 1.2.0

# the changes must also be merged  abck to  develop branch
$ git checkout develop
$ git merge --no-ff release-01212020
# delete the release branch if not needed
$ git branch -d release-01212020
```


## *Hotfix branch workflow*
* hotfixes are done on prod release version ie by branching out of master - only if critical issue
* hotfix done must be merged to master
* hotfix must also be pulled into the develop branch
* naming convention - hotfix-*
* follow semantic versioning major.minor.hotfix

```bash
# branch out from  master
$ git checkout -b hotfix-1.2.1 master

# hotfix changes committed 
$ git commit -a -m 'hotfix 1.2.1 for prod critical issue# 13281 '
$ git checkout master
$ git merge --no-ff  hotfix-1.2.1

# properly tag on the master branch to reflect the hotfix
$ git tag -a 1.2.1

# the hotfix must also be merged to develop branch
$ git  checkout develop
$ git merge --no-ff hotfix-1.2.1

# delete the hotfix branch if not needed
$ git branch -d hotfix-1.2.1

```


