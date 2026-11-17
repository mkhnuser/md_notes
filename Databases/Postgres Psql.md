# Postgres Psql

## psql

### Default role and default database

Psql uses the current user for the role and the database name to be connected to.

### Execute a file

        psql -h 127.0.0.1 -U app -d movies_database -f movies_database.ddl
        docker exec -it postgres psql -U postgres -c "\i /home/streaming_data.sql"

### List schemas

Use `\dn` to list schemas.

### List roles

Use `\du` to list roles.
