# Notes On Git

## Creating a new repository
git init  
Add entries to .gitignore. Like for example /bak/  
Add all files and commit using:  
git add -A && git commit -m "a usefull commit message"  
The above command can be used for each commit.


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
