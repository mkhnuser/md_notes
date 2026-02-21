# Git

## HEAD

HEAD is a pointer which either (points to a specific branch which in turns points to a specific commit) or (points to a specific commit directly [a detached HEAD]).

## Remotes

A remote is a remote destination with which you can interact: make fetch, pull, push, etc.
Usually you have only one remote called origin.

Understand: git remote add <name> <uri> means that URI can be anything.
For example: git remote add secret_origin ../../secret_local_project.

A shorter syntax for `git pull origin main` is just `git pull` if a remote tracking branch in configured.

## Config

`git config` command by default applies to local level.
Here are the levels: local, global, system.

## Reflog

Having located a reflog entry, you can `git merge` it back.

## Rebasing vs Merging

### HEAD

When you do a rebase, HEAD points to a branch you are rebasing onto
since this is the place from which commits start to be reapplied,
so HEAD represents "ours" changes; the branch which is being rebased
represents "theirs" changes because of the HEAD switch.

However, when you merge into your current branch,
HEAD points to "ours" branch. "theirs" branch is a branch which is being merged.

The text above motivates the usage of: `git checkout --ours` and `git checkout --theirs`.

### Revertability (important!)

`git revert` reverts changes introduced by a particular commit.
You should prefer rebases to merges since you might want to revert a merge commit
in the future. However, merge commits are difficult to revert since they have two parents:

https://stackoverflow.com/questions/7099833/how-do-i-revert-a-merge-commit-that-has-already-been-pushed-to-remote

### Commits drop

Rebase might choose to drop empty commits, commits which delete files, for example.

## Rerere

The name means "Reuse Recorded Resolution".
This part of git allows you to automatically resolve conflicts which have been resolved.

## Bisect

A great binary search feature for bug introduction finding or performance shift finding.
