## Setup a local mysql db ##

### Get a mariaDB container in docker ###
```
docker run --name db -e MYSQL_ROOT_PASSWORD=[your password here] -p 3306:3306 --restart=always -d mariadb:latest
```
### Get mysql cli for terminal###
```
sudo dnf install mysql-community
mysql -host=172.17.0.1 -uroot -p
```

### Mysql commands to change user ###
```mysql
CREATE SCHEMA DBNAME CHARSET 'utf8mb4' collate 'utf8mb4_unicode_ci'
GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'%' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```

### Mysql command to import database from sql ###
Try:
```mysql
mysql -u username -p database_name < file.sql
```
Check MySQL Options.

Note-1: It is better to use the full path of the SQL file file.sql.

Note-2: Use -R and --triggers to keep the routines and triggers of original database. They are not copied by default.
