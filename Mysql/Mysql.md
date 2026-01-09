# Mysql Intro

[toc]

## 1. Mysql login

### 1) mysql login

```shell
mysql -u<user-name> -p
<password>
```

## 2. Mysql config

### 1) Inquire variables related to 'timeout'

```sql
show global variables like '%timeout%';
```

### 2) Inquire variables related to 'packet'

```sql
show global variables like '%packet%';
```

## 2. Mysql users and hosts

### 1) Inquire users and hosts

```sql
SELECT User, Host FROM mysql.user;
```

### 2) Remove user a user hosts

```sql
DROP USER <user-name>@<host-name>;
```

## 4. Users and hosts' privileges

### 1) Inquiry

#### a. All users and hosts

```sql
SHOW GRANTS;
```

#### b. A user and host

```sql
SHOW GRANTS FOR <user-name>@<host>;
```

### 2) Grant Privileges

#### [1] Create a user

From 'ERROR 1410 (42000): You are not allowed to create a user with GRANT'

```sql
CREATE USER <user-name>@'%' IDENTIFIED BY <password>;
```

#### [2] Grants privileges

```sql
GRANT ALL PRIVILEGES ON <database>.<table-name or *(if all)> TO '<user-name>'@'%';
FLUSH PRIVILEGES;
```

## 5. Database

### 1) Inquiry

```sql
SHOW database;
```

### 2) Create

```sql
CREATE DATABASE <db-name>;
```

### 3) Select 

```sql
USE <db-name>;
```

## 6. Create table

```sql
CREATE TABLE <table-name> (<col-name> <data-type> [constraints]);
```

- Example

```sql
CREATE TABLE terra ("id INT AUTO_INCREMENT PRIMARY KEY NOT NULL, name TEXT NOT NULL, flag BOOLEAN NOT NULL");
```

## 7. Table contents initialization

```sql
TRUNCATE TABLE <table-name>;
```

## 8. Table property

```sql
DESCRIBE <table-name>;
```

## 9. Modification table

 ### 1) Adding a Column

```sql
ALTER TABLE <table-name> ADD COLUMN <col-name> <data-type> [constraints] [FIRST | AFTER <existing-col-name>];
```

- `constraints`: Optional, specifies column constraints (e.g., `NOT NULL`, `DEFAULT 'value'`, `AUTO_INCREMENT`).

- `FIRST`: Optional, adds the column as the first column in the table.

- `AFTER existing_column_name`: Optional, adds the column after a specified existing column. 

  If neither `FIRST` nor `AFTER` is used, the column is added at the end.

### 2) Dropping a Column

```sql
ALTER TABLE <table-name> DROP COLUMN <col-name>;
```

### 3) Modifying a Column (Changing Data Type or Constraints)

```sql
ALTER TABLE <table-name> MODIFY COLUMN <col-name> <new-data-type> [new-constraints];
```

### 4) Renaming a Column:

```sql
ALTER TABLE <table-name> CHANGE COLUMN <old-col-name> <new-col-name> <data-type> [constraints];
```

## 10. Query



### 1) CASE







