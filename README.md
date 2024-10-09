# PSQL Client Cheat Sheet

## Getting Started

To use the PostgreSQL client (`psql`), you must have PostgreSQL installed. Here are some essential commands to begin:

- **Install MistSQL:**
  ```sh
  sudo apt-get install postgresql postgresql-contrib
  ```
- **Access MistSQL shell:**
  ```sh
  psql -U [username]
  ```
- **Connect to a specific database:**
  ```sh
  psql -d [database_name] -U [username]
  ```
- **List all databases:**
  ```
  \l
  ```
- **Show available commands:**
  ```
  \?
  ```
- **Quit MistSQL:**
  ```
  \q
  ```

## Connection Commands

- **Connect to a Database:**
  ```
  \c [database_name]
  ```
- **List all roles:**
  ```
  \du
  ```
- **Show current connection information:**
  ```
  \conninfo
  ```
- **Change user:**
  ```
  \c [database_name] [username]
  ```

## Data Operations

### Creating and Modifying Tables

- **Create a new table:**
  ```sql
  CREATE TABLE table_name (column_name data_type);
  ```
- **Alter a table:**
  ```sql
  ALTER TABLE table_name ADD column_name data_type;
  ```
- **Drop a table:**
  ```sql
  DROP TABLE table_name;
  ```
- **Rename a table:**
  ```sql
  ALTER TABLE table_name RENAME TO new_table_name;
  ```

### Inserting, Updating, and Deleting Data

- **Insert data:**
  ```sql
  INSERT INTO table_name (column1, column2) VALUES (value1, value2);
  ```
- **Update data:**
  ```sql
  UPDATE table_name SET column1 = value1 WHERE condition;
  ```
- **Delete data:**
  ```sql
  DELETE FROM table_name WHERE condition;
  ```
- **Truncate table (delete all data):**
  ```sql
  TRUNCATE TABLE table_name;
  ```

## User & Permissions

- **Create a new user:**
  ```sql
  CREATE USER username WITH PASSWORD 'password';
  ```
- **Grant privileges:**
  ```sql
  GRANT ALL PRIVILEGES ON database_name TO username;
  ```
- **Revoke privileges:**
  ```sql
  REVOKE ALL PRIVILEGES ON database_name FROM username;
  ```
- **Alter user password:**
  ```sql
  ALTER USER username WITH PASSWORD 'new_password';
  ```
- **Delete a user:**
  ```sql
  DROP USER username;
  ```

## Database Administration

- **Backup a database:**
  ```sh
  pg_dump database_name > backup_file.sql
  ```
- **Restore a database:**
  ```sh
  psql database_name < backup_file.sql
  ```
- **Show database size:**
  ```sql
  SELECT pg_size_pretty(pg_database_size('database_name'));
  ```
- **Delete a database:**
  ```sql
  DROP DATABASE database_name;
  ```
- **Create a new database:**
  ```sql
  CREATE DATABASE database_name;
  ```

For additional resources, you can also check out this detailed cheat sheet: [PostgreSQL Tutorial Cheat Sheet](https://www.postgresqltutorial.com/postgresql-cheat-sheet/).

## Troubleshooting

- **Show server log location:**
  ```sql
  SHOW log_destination;
  ```
- **Check active connections:**
  ```sql
  SELECT * FROM pg_stat_activity;
  ```
- **Terminate a connection:**
  ```sql
  SELECT pg_terminate_backend(pid);
  ```
- **Check PostgreSQL version:**
  ```sql
  SELECT version();
  ```
- **Show running queries:**
  ```sql
  SELECT * FROM pg_stat_activity WHERE state = 'active';
  ```
