# docker-wordpress

Docker compose installation of a single site Wordpress instance using Nignix as the web server and MariaDB as the database.

- `nginx:1.13.5-alpine`
- `wordpress:php7.2-fpm`
- `mariadb:latest`


## Installation

```
$ cd docker-wordpress
$ touch .env
```
write Environment Variables `.env`

```
# .env

WORDPRESS_DB_NAME=wordpress
WORDPRESS_TABLE_PREFIX=wp_
WORDPRESS_DB_HOST=mysql
WORDPRESS_DB_PASSWORD=password

MYSQL_ROOT_PASSWORD=password

```

```
$ docker-compose up -d
```

`https://localhost`

## Backup wordpress data command

```
$ docker exec -it blog_db_1 sh -c 'mysqldump WORDPRESS_DB_NAME -u root -pWORDPRESS_DB_PASSWORD 2> /dev/null' > db-data/mysql.dump.sql
````

For example
```
$ docker exec -it blog_db_1 sh -c 'mysqldump wordpress -u root -ppassword 2> /dev/null' > db-data/mysql.dump.sql
``

## Stop

```
$ docker-compose down
```
