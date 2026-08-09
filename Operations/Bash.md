# Bash

## Command execution

### `$PATH`

One can examine `$PATH` environment variables.
The shell examines the directories in this environment variable from left to right.

### How does one add a new command?

To add a command to only one user, place it in `/home/username/bin`.
To add a command globally, consider adding a command into `/usr/local/bin`.

### How does one locate the command or a file?

You can try using `plocate` command to locate the location of commands.
`which` and bash-builtin `type` are also handy, but are more limited.

## Shell Variables

To see shell variables: `set`, to see environment variables: `env`.
Observe: `set` is a superset of `env`.
To set an environment variables, use `export VAR=VAL`.

## Bash Configuration Files

### Login Shell vs Interactive Shell

There is a separation between a login shell and an interactive shell.
A login shell is executed per a user login or with `--login` option.
An interactive shell is, roughly, any other shell.

### Bash Configuration Files Execution Order

Here is a rough execution order:

1. `/etc/profile` is executed for every user when one logs in.

        This script will load scripts from `/etc/profile.d` directory as well.
        Consider modifying this directory if you want to affect all users.

2. `/etc/bashrc` is executed for every user when an interactive shell is opened.

        User's local `~/.bashrc` file can override some settings set by this file.

3. `~/.bash_profile` is executed for a specific user's log in shell.

        This script usually sources `~/.bashrc` as well.

4. `~/.bashrc` is sourced every time a specific user creates an interactive shell non-login shell.
5. `~/.bash_logout` is sourced every time a specific user logs out (exits the last shell).

## Aliases

Observe: aliases are not inherited into child shells just as shell variables are not.
Define aliases within `~/.bashrc` to obtain them every time you open a new shell.

## Man Pages

Run `man -k mount` to obtain a list of all available man pages on the `mount`.
Use `man 8 mount` to obtain a man page on a mount system administration command.

## File Name Expansions

One can use metacharacters to perform file expansions.

## Output redirection

1. `<` reads the content of a file into a command.
2. `>` redirects the standard output into a file.
3. `2>` redirects the standard error output into a file.
4. `&>` redirects both standard output and standard error into a file.
5. `>>` append the standard output to a file.
