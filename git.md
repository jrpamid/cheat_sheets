Git Commands
============

### Getting & Creating Projects 
| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |
| `git config --global user.name "jp"` | Configure user name |
| `git config --global user.email "jp@gmail.com"` | configure user email address |
| `git config  --list  ` | git configuration listing |
 

### Basic Snapshotting 
| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |
| `git ls-files -s` | debug uility for  inspecting the staging index tree. |
 


### Branching & Merging ( Every branch must be updated and  managed individually )
| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch from the master|
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [new feature branch name] [from src branch name]` | create a new branch from  specified branch and checkout |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git merge -no-ff [the feature branch] ` | Merges a feature branch with active branch, no fast forward merge is done. Feature branch history is maintained. If fast forward merge is  done, the commit history is lost |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |


### Merge & Rebase 
````
Merge and Rebase are 2 ways to integrate changes from one branch to  another.
* A merge results in a new commit, with changes that have occurred in the merged branch and master.
* A  merge commut results in a cluttered git logs, and  makes it difficult to understand the project flow.
* A merge commit should be used in cases where the commit should stand out. Should be reserved for large refactors, major commits etc.
* A merge commit preserves history where as a  rebase rewrites it.

* rebasing can be understood as “moving the base of a branch onto a different position”. When bringing in a mster branch changes into a feature branch its better to  rebase than merge.
* A rebase doenst create  a new commit.
* A rebase results in a  clean, linear code commit history/logs.
* Rebasing doesnt work with PUll  request.
````
| Command | Description | 
| ------- | ----------- |
| `git checkout  feature-branch01` | Checkout to the feature branch |
| `git merge master ` | Merge the master branch to the feature-branch01 to bring the master updates to feature-branch01 |
| `git merge -no-ff [the feature branch] ` | Merges a feature branch with active branch, no fast forward merge is done. Feature branch history is maintained. If fast forward merge is  done, the commit history is lost |
| `git rebase master` | rebase feature-branch01 with master branch  |


### Sharing & Updating Projects 
| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
|               or      |
| `git push --set-upstream origin [new branch name] `| Push a local branch to remote repo origin to be tracked |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote remove origin` | Remove a remote repository |
| `git remote rename origin origin1` | Rename a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |
 

### Revert & Reset 
````
* Revert rolls back  any changes committed. A  revert creates a new  commit in the history.
* Reset has 3 modes --soft, --hard, --mixed (defaut  mixed)
````
| Command | Description |
| ------- | ----------- |
| `git reset HEAD~ `| revert the last commit |
| `git reset <commit>` | moves the HEAD and refs t |
| `git reset --hard <commit id>` | 
| `git revert HEAD~` | creates a new commit by moving the HEAD to previous commit |
| `git revert <commmitid>` | creates a new commit by moving HEAD to specified commit id |

 
### Inspection & Comparison
| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git log --oneline --decorate --graph --all` | detailed,coloured one line log info | 
| `git diff [source branch] [target branch]` | Preview changes before merging |
| `git diff  --staged ` | lists all the changes between staged area  and local repo. |
| `git diff` | lists the changes between working dir and staged area |
 

### Tags
| Command | Description |
| ------- | ----------- |
| `git tag -a release1.1.0 -m "release 1.1.0 on in q1" <COMMITID/HEAD> ` | tagging a specific commit or head with a tag |
| `git tag `| | list the tags |
| `git show release1.1.0` | get details of a specific release | 
| `git tag -d release1.1.0` | delete a tag |
| `git push origin release1.1.0`| push a tag to  repo |
 