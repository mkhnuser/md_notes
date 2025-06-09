# Bash

See ```help test``` on how to do testing in Bash.
Scripts always exit with the exit code of the last executed command unless an explicit exit is present.
Functions always return the exit code of the last executed command unless an explicit exit is present.

Note the difference in terminology: shell variables verses environment variables.
You use ```export``` keyword to declare an environment variable, which will be inherited by child processes.

Captain reports: any command you invoke is actually a child process.
