# Git

## HEAD

HEAD is a pointer which either:

* Points to a specific branch which in turns points to a commit;
* Points to a specific commit directly which is called a detached HEAD.

## Remotes

Understand: git remote add <name> <uri> means that URI can be anything.
For example: git remote add secret_origin ../../secret_local_project.

## Push

`git push origin main` pushes your local branch main to an origin.
Remote main will be created if it has not been already.

`git push origin main:remote` pushes your local main branch to the remote branch.

## Config

`git config` command by default applies to local level.
Here are the levels: local, global, system.

## Reflog

Having located a reflog entry, you can `git merge` it back to your branch.

## Rebasing vs Merging

### HEAD

#### HEAD during Rebase

When you rebase,
HEAD points to a branch you rebase onto,
since this is the place from which commits start to be consecutively reapplied.

Therefore, the branch on which you rebase represents "ours" changes,
whereas the branch which is being rebased represents "theirs" changes.

#### HEAD during Merge

When you merge into your current branch,
HEAD points to "ours" branch;
"theirs" branch is a branch which is being merged.

The text above motivates the usage of: `git checkout --ours` and `git checkout --theirs`.
The commands above are used to specify that you want to only preserve "ours" changes
or "theirs" changes during potential conflicts.

### Revertability (important!)

You should prefer rebasing to merging in terms of merge commit revertability.
Merge commits are difficult to revert since they have two parents.
Moreover, revert of a merge commit has consequences:

https://stackoverflow.com/questions/7099833/how-do-i-revert-a-merge-commit-that-has-already-been-pushed-to-remote

Rebasing does not have such problems since you obtain linear history as a rebasing result.

### Commits drop during rebasing

Rebasing might choose to drop empty commits; commits which delete files, for example.
Therefore, the resulting number of commits might differ after rebasing.

## Rerere

The name means "Reuse Recorded Resolution".
This part of git allows you to automatically resolve conflicts which have been previously resolved.

## Bisect

A great binary search feature for bug introduction finding or performance shift finding.

## Git Worktrees

# TODO: Investigate this concept.
