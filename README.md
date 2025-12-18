https://silver-engine-6q6pwvxjxwrh9xx-8080.app.github.dev/#!/welcome

docker exec -it petclinic-mysql mysql -uroot -p

GRANT REPLICATION CLIENT ON *.* TO 'exporter'@'%';
FLUSH PRIVILEGES;
docker restart mysql-exporter
