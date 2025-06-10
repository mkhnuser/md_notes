# Bash

See ```help test``` on how to do testing in Bash.
Scripts always exit with the exit code of the last executed command unless an explicit exit is present.
Functions always return the exit code of the last executed command unless an explicit return is present.

Note the difference in terminology: shell variables (local variables) verses environment variables.
You use ```export``` keyword to declare an environment variable, which will be copied into child processes. Note that it will be *copied*, so any changes you make to this var remain local to the shell you are in. Captain reports: any command you invoke is actually a child process.

The following syntax `$()` is called command substitution. It runs a command and replaces the syntax with the output from the command: `mv $(grep -l "Artist: Kansas" *.txt) kansas`.

The following syntax `<()` runs a command and presents its content as a file.
