# MySQL Commands

## Add user

CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';

FLUSH PRIVILEGES;

## Permissions

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
