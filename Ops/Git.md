# Git

## HEAD

HEAD is a pointer which either (points to a specific branch which in turns points to a specific commit) or (points to a specific commit directly [a detached HEAD]).

## Remotes

A remote is a remote destination with which you can interact: make fetch, pull, push, etc.
Usually you have only one remote called origin.
A shorter syntax for `git pull origin main` is just `git pull` if a remote tracking branch in configured.

## Config

`git config` command by default applies to local level. Here are the levels: local, global, system.
