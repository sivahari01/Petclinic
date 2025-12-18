
@sivahari01 ➜ /workspaces/Petclinic/prometheous (master) $ docker exec -it petclinic-mysql mysql -uroot -proot
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 158
Server version: 8.0.44 MySQL Community Server - GPL

Copyright (c) 2000, 2025, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SELECT user, host, plugin FROM mysql.user WHERE user='exporter';
Empty set (0.00 sec)

mysql> 
mysql> ALTER USER 'exporter'@'%' IDENTIFIED WITH mysql_native_password BY 'exporterpass';
ERROR 1396 (HY000): Operation ALTER USER failed for 'exporter'@'%'
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> DROP USER IF EXISTS 'exporter'@'%';
xporter'@'%' IDENTIFIED WITH mysql_native_password BY 'exporterpass';
GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
FLUSH PRIVILEGES;
Query OK, 0 rows affected, 1 warning (0.23 sec)

mysql> CREATE USER 'exporter'@'%' IDENTIFIED WITH mysql_native_password BY 'exporterpass';
Query OK, 0 rows affected (0.01 sec)

mysql> GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

mysql> exit
Bye
