# docker 的安装

1:卸载已安装的docker
```
$ sudo yum remove docker
```
2:安装 yum-utils
```
$ sudo yum install -y yum-utils
```
3:添加 docker 的安装地址
```
$ sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
4:安装docker
```
$ sudo yum install -y docker-ce docker-ce-cli containerd.io
```
5:开机自启docker
```
$ sudo systemctl enable docker --now
```
6:配置docker加速
```
$ sudo mkdir -p /etc/docker
$ sudo tee /etc/docker/daemon.json <<-'EOF' { "registry-mirrors": ["https://nxsgyu2g.mirror.aliyuncs.com"] } EOF
```
7:重启docker进程
```
$ sudo systemctl daemon-reload
```
8:重启docker
```
$ sudo systemctl restart docker
```
# docker 免sudo
1:添加docker group
```
$ sudo groupadd docker
```
2: 将当前用户添加至docker组
```
$ sudo gpasswd -a ${USER} docker
```
3: 重启docker服务
```
$ sudo systemctl restart docker
```
4: 更新用户组
```
$ newgrp docker
```
# docker 使用（免sudo后）

1.查看当前运行的所有容器
```
docker ps -a
```
2.停止所有容器（container），这样才能够删除其中的images：
```
docker stop $(docker ps -a -q)
```
3.如果想要删除所有容器（container）的话再加一个指令：
```
docker rm $(docker ps -a -q)
```
4.查看当前有那些镜像（images）
```
docker images
```
5.删除镜像（images），通过镜像（images）的id来指定删除谁
```
docker rmi <image id>
```
6.想要删除镜像（images）id为<None>的image的话可以用
```
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
```
7.要删除全部镜像（images）的话
```
docker rmi $(docker images -q)
```
8.要容器自启
```
docker update <image id> --restart=always
```