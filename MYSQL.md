## MySQL Stuff

* [MySQL Views](https://stackoverflow.com/questions/2834016/how-to-get-a-list-of-mysql-views)


Show views:

```

SHOW FULL TABLES IN database_name WHERE TABLE_TYPE LIKE 'VIEW';

```

Dump from remote server:

```

mysqldump -h hostname-of-the-server -u mysql_user -p database_name > file.sql

```

#### Grant syntax:


```

GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';

```

