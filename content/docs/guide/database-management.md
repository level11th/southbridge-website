
---
title: Database Management
weight: 3
---

## Setup

After starting PostgreSQL with a superuser account, create a non-superuser account for the application to improve database access security.
Follow these steps:

{{% steps %}}

### Log in to PostgreSQL as the superuser

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
Grant the user access to the database and its tables.
The following example grants these table privileges:

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
-   **`GRANT USAGE, SELECT, UPDATE ON ALL SEQUENCES IN SCHEMA public TO newuser`**: Grants the specified permissions (`USAGE`, `SELECT`, `UPDATE`) on all sequences within the `public` schema of the database.
-   **`GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO newuser`**: Grants the specified permissions (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) on all tables within the `public` schema of the database.

### Grant Permissions on Future Tables

To automatically grant `newuser` these permissions on future tables and sequences, use the following commands:

```sql
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO newuser;
ALTER DEFAULT PRIVILEGES IN SCHEMA public
GRANT USAGE, SELECT, UPDATE ON SEQUENCES TO newuser;
```

This ensures that new tables and sequences in the `public` schema inherit the same permissions for `newuser`.

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
  - **`-C`**: Creates the database before restoring it. The target database is dropped and recreated only if `--clean` is also specified.
  - **`-v`**: Enables verbose mode, providing detailed output during the restoration process.
  - **`-d postgres`**: Specifies the name of the database to connect to for executing the restore process. The database `postgres` is often used as a placeholder for restoration.
- **`< db.dump`**: Redirects the contents of the `db.dump` file on the host machine to the `pg_restore` command inside the container.

#### Restore to a specific database

This example shows how to restore a backup file to a specific database:
```bash
docker exec -i pg pg_restore -U postgres -Fc -v -d my_foo_db < db.dump
```
Other useful flags:

- **--no-privileges**: Prevents restoration of access privileges (grant/revoke commands).
- **--no-owner**: Omits commands that set object ownership to match the original database.
- **--disable-triggers**: Instructs `pg_restore` to temporarily disable triggers during a data-only restore. This requires superuser privileges.

#### Restore only a specific table
```bash
docker exec -i pg pg_restore -U postgres --data-only --disable-triggers -Fc -v -d my_foo_db -t my_foo_table < db.dump
```

#### Restore by piping pg_dump output to pg_restore
```bash
docker exec -i pg pg_dump -Fc -d "conn string" | docker exec -i pg pg_restore -U postgres -d my_foo_db --no-privileges --no-owner
```

#### More details
- [pg_dump official docs](https://www.postgresql.org/docs/current/app-pgdump.html)
- [pg_restore official docs](https://www.postgresql.org/docs/current/app-pgrestore.html)
