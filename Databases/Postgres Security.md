# Postgres Security

## Roles and Access

### Roles

Each connection has an associated role with it.

### postgres role

postgres role is all-permissive and should be avoided for production purposes.

### Role creation

        CREATE ROLE coffee_chain_admin WITH LOGIN PASSWORD 'password';
        GRANT CONNECT ON DATABASE coffee_chain TO coffee_chain_admin;
        REVOKE CONNECT ON DATABASE coffee_chain FROM PUBLIC;

See roles discussion in "Just Use Postgres", 2.8 Roles and access control.

