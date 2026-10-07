# SQLAlchemy

## naming_conventions

Use naming_conventions while working with SQLAlchemy.

## Session

Session does not create a database connection, an engine does.

## Transient and Persistent States

An ORM object in SQLAlchemy is called transient if it is not in the db.
Once objects are in DB, you call them persistent.

## Expired State

Once you've run session.commit(), the objects are in expired state:
further attribute access results in issuing SQL queries.

Moreover, once you've issued `session.rollback()`, objects expire too.
To control this behavior, use `expire_on_commit` flag.

## Expunged State

Once a session is closed, it expunges objects from itself: they are no longer associated with a particular session and, therefore, are in detached state.
So, implicit I/O will result in an error.

## Concurrency Safety

Remember that SQLAlchemy objects are not thread-safe and not task-safe:
you should use a separate session per thread and a separate session per task.
