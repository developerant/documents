# MySQL Commands

### Add DB

CREATE DATABASE db_name;

### Drop DB

DROP DATABASE db_name;
FLUSH PRIVILEGES;

### Show DBs

SHOW databases;

### Add user

CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';

FLUSH PRIVILEGES;

### Drop user

DROP USER 'anthony'@'localhost';

### Show users

SELECT User, Host, Password FROM mysql.user;

### Set password

SET PASSWORD FOR 'user'@'localhost' = PASSWORD('enterpassword');

### Grant Privileges

GRANT ALL PRIVILEGES ON db_name.* to username@localhost;

### Show grants

SHOW GRANTS;

SHOW GRANTS FOR 'user'@'localhost';

### Permissions

Here is a short list of other common possible permissions that users can enjoy.

ALL PRIVILEGES- as we saw previously, this would allow a MySQL user all access to a designated database (or if no database is selected, across the system)

CREATE- allows them to create new tables or databases

DROP- allows them to them to delete tables or databases

DELETE- allows them to delete rows from tables

INSERT- allows them to insert rows into tables

SELECT- allows them to use the Select command to read through databases

UPDATE- allow them to update table rows

GRANT OPTION- allows them to grant or remove other users' privileges


GRANT [type of permission] ON [database name].[table name] TO ‘[username]’@'localhost’;

### Login

mysql -u username -p

## String Replace
UPDATE your_table
SET your_field = REPLACE(your_field, 'articles/updates/', 'articles/news/')
WHERE your_field LIKE '%articles/updates/%'

## DB Dump
mysqldump -u user -p dbname > dbname.sql;