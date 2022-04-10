# Notes On Git

- Purpose of staging is to group a set of files into a single commit.

- To go back to an older commit(commitid) which has a working code and make that as head:

That is we want to revert commits from HEAD till commitid (not including).

git revert --no-edit commitid..HEAD 

This will first revert the changes introduced by the commit at HEAD, 

Then it will revert the changes introduced by the previous commit,

So on till it reaches commitid which it does not revert and stops.

--no-edit will disable prompt for commit messages.

- To set editor as vim:

git config --global core.editor vim

- To work with a remote repository:

git clone <url>

make changes locally and commit.

git push



## Creating a new repository
- git init  
- Add entries to .gitignore. 
- Add all files and commit using:  
git add --all; git commit -m "a usefull commit message"  
The above command can be used for each commit.

## Useful git commands  
- To get diff of items before staging. Keep pressing n to not stage.  
git add --all -p

- To show all files in master branch  
git ls-tree -r master

- To recover a file from a previous commit  
git checkout <commit hash> -- <filename>

- To let non bare respository accept a push  
git config receive.denyCurrentBranch updateInstead  
https://stackoverflow.com/questions/804545/what-is-this-git-warning-message-when-pushing-changes-to-a-remote-repository/28262104#28262104

- Convert non bare repository to bare  
https://stackoverflow.com/questions/2199897/how-to-convert-a-normal-git-repository-to-a-bare-one

- To push a local repository to server  
convert it to a bare repository.  
git remote add origin <url>  
git push origin master --all --tags

## Fetch

Ensure: git remote add origin `<url>`

git add origin, sets up a fetch spec of

+refs/heads/_:refs/remotes/origin/_

which is good.

git fetch origin

This will get objects and update remote tracking branches for all branches in remote.

Create master branch from origin/master:

git checkout master

git merge origin/master

Create branch-name from origin/branch-name:

git checkout branch-name

git merge origin/branch-name

The above creates branches but which are tracked branches. We do not need to use the tracked branch feature since we do not use pull. Generally it’s better to simply use the fetch and merge commands explicitly as the magic of git pull can often be confusing(from progit).

Show tracked branches and if they are out of sync:

git branch -vv.

## Push

Ensure: git remote add origin `<url>`

Push works on a branch.

Use the form:

git push origin branch-name

This explicitly states the remote and the branch.

branch-name should exist in remote, else it is created.

To initialize a remote repository with a local repository:

git push origin master - generally pushing master is enough to get started.

If needed use --all and --tags to push all branches and tags.

--dry-run is available.

To delete a branch in server:

git push origin --delete branch-name

## To do a merge dry run

to=branch-name;from=origin/branch-name;git merge-tree $(git merge-base $from $to) $to \$from

More details here: https://stackoverflow.com/a/6283843

## To visualize the history

git log --oneline --graph --all

## Cheatsheet

https://github.github.com/training-kit/downloads/github-git-cheat-sheet/

## Prefer git revert

https://stackoverflow.com/questions/41261474/how-to-delete-a-only-a-specific-commit-in-the-middle-of-the-git-log/41261661#41261661

## A popular workflow

Github Flow: https://guides.github.com/introduction/flow/
