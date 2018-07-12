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
CREATE SCHEMA DBNAME CHARSET 'utf8' COLLATE 'utf8_general_ci';
GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'%' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```
