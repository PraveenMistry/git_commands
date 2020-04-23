# Git Commands

## Flow:
Create new branch from base branch
Code
Git add files...
Commit 
Push
Pull request

## Normal Flow 

For checkout : git checkout "frombranch"
             or after create that branch on local 
              git checkout -b "frombranch"

For add   : git add .
For Pull  : git pull "source" "destination"
For Commit: git commit -m "message"
For Push  : git push "source" "destination" 
For reset : git reset --hard upstream/master
For fetch : git fetch "source" "destination"  // clear you local change and pull from remote
For clear local change : git stash
For log check : git log -v


## ADD UPSTREAM
git remote add upstream <upstreamURL>

## SET UPSTREAM 
git remote set-url upstream <upstreamURL>


## PULL 
For Pull
source : upstream
destination : branch name

## PUSH 

For Push
source : origin
destination : branch name

## DIFF 
Check Diff
git diff fileName

To change the remote url: 
git remote set-url origin your-fork-repo
git remote set-url upstream main-repo (destination)

## RESET 

Check recent Commit:
git show HEAD

Reset 1)
git reset HEAD filename

Reset 2)
git reset commit_SHA

git checkout HEAD filename: Discards changes in the working directory.
git reset HEAD filename: Unstages file changes in the staging area.
git reset commit_SHA: Resets to a previous commit in your commit history.



## BRANCHING 

- Create Branch
git branch new_branch

- Switch to the new branch with
git checkout branch_name

-Merging the branch into master 
working branch should be master so switch branch to master. and run following 
git merge branch_name

- delete branch
git branch -d branch_name


## Check THIS 

Git is supposed to understand what files already exist on the server, unless you somehow made a huge difference to your tree and the new changes need to be sent.

To create a new branch with a copy of your current state

git checkout -b new_branch #< create a new local branch with a copy of your code
git push origin new_branch #< pushes to the server
Merge Conflict 

Remove <<===
- Add to staging 
git add .
- commit 
git commit -m "Resolve merge conflict"



## Generalizations

git branch: Lists all a Git project's branches.
git branch branch_name: Creates a new branch.
git checkout branch_name: Used to switch from one branch to another.
git merge branch_name: Used to join file changes from one branch to another.
git branch -d branch_name: Deletes the branch specified.

## Cherry-Pick

When your code commit on a branch and you want to move that commit on another branch.
git cherry-pick "sshId"
git push branch

Syncing a fork
Github Nodes
Local, Fork, Upstream

Steps)
- my current working directory : master (Local)
- fetch all commits from the upstream repository (META DATA), run:  git fetch upstream
- Merge the changes from upstream/master into your local master branch, run: git merge upstream/master

## Add a remote 
git remote add upstream https://github.com/USERNAME/REPOSITORY.git
Changing a remote's URL
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git

10 Git Commands You Should Know

## Inspecting Things
git diff : See all file changes locally. A file name can be appended to show changes for only one file
git log : See all commit history. Can also be used for a file with git log -p my_file. Enter q to exit
git blame my_file : See who changed what and when in my_file ( Help )
git reflog : Show a log of changes to the local repository’s HEAD. Good for finding lost work

## Undoing Things
git reset --head HEAD : 
Discard staged and unstaged changes since the most recent commit.
Specify a different commit instead of HEAD to discard changes since that commit. --hard specifies that both the staged and unstaged changes are discarded.
Make sure you don’t discard a commit from a remote branch that your collaborators are depending upon!


## Git checkout my_commit :
Discard unstaged changes since my_commit.
HEAD is often used for my_commit to discard changes to your local working directory since the most recent commit.
checkout is best used for local-only undos. It doesn’t mess up the commit history from a remote branch that your collaborators are depending upon!
If you use checkout with a branch instead of a commit, HEAD is switched to the specified branch and the working directory is updated to match. This is the more common use of the checkout command
git revert my_commit :
Undo the effects of changes in my_commit. revert makes a new commit when it undoes the changes.
revert is safe for collaborative projects because it doesn’t overwrite history that other users’ branches might depend upon.
git clean -n :
Delete untracked files in the local working directory.
The -n flag is for a dry run where nothing is deleted.
Use the -f flag to actually remove the files.
Use the -d flag to remove untracked directories.
By default files untracked by .gitignore will not be deleted, but this behavior can be altered.


## Tidying Things	
git commit --amend :
Add your staged changes to the most recent commit.
If nothing is staged, this command just allows you to edit the most recent commit message. Only use this command if the commit has not been integrated into the remote master branch!

## git push my_remote -tags :
Send all local tags to the remote repo. Good for versioning changes.

## Check diff in a file:
git diff package.json

## Remove local changes (get from upstream)
git checkout package.json

## Changes Author name
git config --global --edit
git commit --amend --reset-author
