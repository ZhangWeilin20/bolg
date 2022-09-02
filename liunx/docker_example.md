# docker 安装 mariadb
1.conf目录创建my.cnf
```
[mysqld]
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci
skip-character-set-client-handshake
skip-name-resolve

server_id=1
log-bin=mariadb-bin
max_binlog_size=500m
binlog_cache_size=100m
binlog_format=ROW
expire_logs_days=7

```
2.创建并运行容器
```
docker run -p 0.0.0.0:3306:3306 --name mariadb -v /home/weilin/DockerData/mariadb/log:/var/log/mysql -v /home/weilin/DockerData/mariadb/data:/var/lib/mysql -v /home/weilin/DockerData/mariadb/conf:/etc/mysql -e MARIADB_ROOT_PASSWORD=Smile520 --restart=always -d mariadb:latest
```
# docker 安装 redis
1.conf目录创建redis.conf
```
appendonly yes
```
2.创建并运行容器
```
docker run -p 0.0.0.0:6379:6379 --name redis -v /home/weilin/DockerData/redis/data:/data -v /home/weilin/DockerData/redis/conf/redis.conf:/etc/redis/redis.conf --restart=always -d redis:latest redis-server /etc/redis/redis.conf
```
# docker 安装 nginx
创建并运行容器
```
docker run -p 80:80 --name nginx -v /data/home/smile/MyDockerData/Nginx/html:/usr/share/nginx/html -v /data/home/smile/MyDockerData/Nginx/logs:/var/log/nginx -v /data/home/smile/MyDockerData/Nginx/conf:/etc/nginx  --restart=always -d nginx
```
# docker 安装 portainer
```
docker volume create portainer_data
docker run --name portainer -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.14.2
```