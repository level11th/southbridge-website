
---
title: Database management
weight: 3
---

## Setup

after start PostgreSQL with a superuser,
we make sure to create a nonroot user for our app, harden our database access security.
follow these steps:

{{% steps %}}

### Log into PostgreSQL as the superuser

Open your terminal and run:

```bash
docker exec -it pg psql -U postgres
```

### Create a new user with a password
Replace `newuser` with the desired username and `secure_password` with the password you want.

```sql
CREATE USER newuser WITH PASSWORD 'secure_password';
```

### Grant Database-Level Permissions
For database-level permissions, you will need to grant specific privileges to the user.
For example, to grant the following privileges:

- `SELECT`
- `INSERT`
- `UPDATE`
- `DELETE`

Use the following commands:

```sql
-- Grant database-level permissions
GRANT CONNECT ON DATABASE mydb TO newuser;
```
```shell
\c mydb; # Switch to the target database
```
```sql
GRANT USAGE ON SCHEMA public TO newuser;
GRANT USAGE, SELECT, UPDATE ON ALL SEQUENCES IN SCHEMA public TO newuser;
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO newuser;
```

#### Explanation of the Grants:

-   **`CONNECT ON DATABASE mydb TO newuser`**: Allows the user `newuser` to connect to the database `mydb`.
-   **`USAGE ON SCHEMA public TO newuser`**: Allows the user `newuser` to use the `public` schema (default schema where tables are created). Without this, they cannot access tables or objects in that schema.
-   **`GRANT USAGE, SELECT, UPDATE ON ALL SEQUENCES IN SCHEMA public TO newuser`**: Grants the specified permissions (`SELECT`, `UPDATE`) on all sequences within the `public` schema of the database.
-   **`GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO newuser`**: Grants the specified permissions (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) on all tables within the `public` schema of the database.

### Grant Permissions on Future Tables

Making `newuser` to automatically have these permissions on any new tables created in the future, use the following command:

```sql
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO newuser;
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT USAGE, SELECT, UPDATE ON SEQUENCES TO newuser;
```

This will ensure that new tables in the `public` schema will inherit the same permissions for `newuser`.

{{% /steps %}}
---

### Summary

```bash
docker exec -it pg psql -U postgres
```

```sql
CREATE USER newuser WITH PASSWORD 'secure_password';

-- Grant database access
GRANT CONNECT ON DATABASE mydb TO newuser;
```
```shell
\c mydb; -- Switch to the target database
```
```sql
GRANT USAGE ON SCHEMA public TO newuser;

-- Grant permissions on existing tables
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO newuser;
-- Grant permissions on existing sequences
GRANT USAGE, SELECT, UPDATE ON ALL SEQUENCES IN SCHEMA public TO newuser;

-- Grant default privileges for future tables
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO newuser;
-- Grant default privileges for future sequences
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT USAGE, SELECT, UPDATE ON SEQUENCES TO newuser;
```

## Backup & Restore

This document explains how to back up and restore a PostgreSQL database using Docker commands. Each command is detailed with explanations of the flags used.

### Backup
```bash
$ docker exec pg pg_dump -U postgres mydb -v -Fc > db.dump
```
Command Breakdown:
- **`docker exec pg`**: Executes a command in the running Docker container named `pg`.
- **`pg_dump`**: The PostgreSQL utility for backing up a database.
- **Flags:**
  - **`-U postgres`**: Specifies the username (`postgres`) to connect to the database.
  - **`mydb`**: The name of the database to be backed up.
  - **`-v`**: Enables verbose mode, which provides detailed output during the execution of the command.
  - **`-Fc`**: Specifies the custom format for the backup file. This format is compact and allows for selective restoration of database objects.
- **`> db.dump`**: Redirects the output of the `pg_dump` command to a file named `db.dump` on the host machine.

### Restore
```bash
$ docker exec -i pg pg_restore -U postgres -Fc -C -v -d postgres < db.dump
```
Command Breakdown:
- **`docker exec -i pg`**: Executes a command in the running Docker container named `pg`, passing input from the host machine to the container.
- **`pg_restore`**: The PostgreSQL utility for restoring a database from a backup.
- **Flags:**
  - **`-U postgres`**: Specifies the username (`postgres`) to connect to the database.
  - **`-Fc`**: Indicates that the input is in the custom format, matching the format used during the backup.
  - **`-C`**: Creates the database before restoring it. If the database already exists, it is dropped and recreated.
  - **`-v`**: Enables verbose mode, providing detailed output during the restoration process.
  - **`-d postgres`**: Specifies the name of the database to connect to for executing the restore process. The database `postgres` is often used as a placeholder for restoration.
- **`< db.dump`**: Redirects the contents of the `db.dump` file on the host machine to the `pg_restore` command inside the container.
