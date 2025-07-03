# SQLAlchemy and Alembic

Use naming_conventions while working with SQLAlchemy.

An ORM object in SQLAlchemy is called transient if it is not in the db; once objects are in DB, you call them persistent.

Once you've run session.commit(), the objects are in expired state: further attribute access results in issuing SQL queries. To control this behavior, use expire_on_commit flag. Moreover, once you've issued session.rollback(), objects expire too!

Once a session is closed, it expunges objects from itself: they are no longer associated with a particular session and, therefore, are in detached state. So, implicit I/O will result in an error.

Remember that SQLAlchemy objects are not threadsafe and not "async task safe": you should use a separate session per thread and a separate session per task.
