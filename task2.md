Problem: Create MySQL database docker image with:
• volume called mysql_data to /var/lib/mysql
• Set ENV variable MYSQL_ROOT_PASSWORD to P4sSw0rd0!.
```
$mkdir /mysql
$cd /mysql
```
```
$vim dockerfile
```
FROM ubuntu


VOLUME mysql_data /var/lib/mysql


RUN apt update -y


RUN apt install mysql-server -y


ENV MYSQL_ROOT_PASSWORD P4sSw0rd0!


CMD ["mysqld"]

```
$docker bulid -t sql:v1
```
