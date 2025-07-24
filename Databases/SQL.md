# SQL

Role = User in the database world.
*psql* terminal client uses the current user for the role and the database name to be connected to.
PK = NOT NULL + UNIQUE CONSTRAINT.
Recall that a PK can be natural and surrogate.

Think about always adding created_at, updated_at, deleted_at attributes.

COUNT(*) counts all strings, whereas COUNT(COLUMN) counts only NOT NULL strings.

Use IS NULL or IS NOT NULL for NULL comparison. != behaviour is tricky for NULL.
When you do ORDER BY remember about NULLS LAST, NULLS FIRST.

Normalization allows you to reduce data redundancy within a table; remove duplicates.
Normalization is achieved through a table schema restructuring.
Normalization is a gradual process; there are many normal forms.
If a table is in a normal form, it satisfies some set of constraints which is imposed on the table.

You usually use 1NF, 2NF, 3NF.

You can implement one-to-one relation using REFERENCES with UNIQUE constraint.
A foreign key must reference a primary key or a unique column.
