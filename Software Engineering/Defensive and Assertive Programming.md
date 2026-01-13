# Defensive and Assertive Programming

## General Defenses

* Always use the default close in the switch / case statement
which generates a custom runtime error which signifies to you
that something is wrong.
* Always use the else statement in the if / else statement
which generates a custom runtime error which signifies to you
that something is wrong.
* Fail fast.

## Exception Handling

Perhaps sometimes it is better to handle exception on the level above
and not to handle it on the current level.

Sometimes this:

        try:
            do_work()
        except IamtootiredException:
            logger.error("He is too tired!!!")
            raise
        except IamtoolazyException:
            logger.error("He is too lazy!!!")
            raise
        except IamdaydreamingException:
            logger.error("He is daydreaming!!!")
            raise

Is worse than this (no exception handling):

            do_work()

## Assertive Programming

* Assertions ensure that something never happens; they document your assumptions about the code.
* Exceptions allow you to handle something that can happen.
* If blocks handle logical scenarios: you expect your code to branch out.
* Perhaps, instead of comments, you should sometimes use assertions.
