[TOC]

# 创建 docker 容器

1.   编写 **Dockerfile** (大小写敏感)

2.   终端输入 `docker build -t <镜像名>:<标签> <Dockerfile路径>`, 例如: `docker build -t wechat_test:latest .`

     ```
     -t 指定镜像的名称和标签
     <镜像名> 镜像的命名
     <标签> 是镜像的标签，通常用来表示版本号，如果不指定，默认为 latest
     <Dockerfile路径> 是Dockerfile所在的路径，如果不指定，默认为当前目录
     ```

     >   错误： ERROR: error during connect: Head "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/_ping": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.
     >
     >   解决方案： 启动docker 服务或启动 docker desktop

# 启动 docker 容器

```
docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
--name: 为容器指定一个名称
-d: 在后台运行容器（守护态）
-it: 以交互模式运行容器，并为容器分配一个伪终端
-p: 将容器的端口映射到宿主机的端口
-v: 绑定挂载卷，将宿主机的文件或目录挂载到容器中
-e 环境变量, 多个环境变量使用多个 -e 分隔
例如: docker run --name wechat_test -d -it -e MYSQL_ROOT_PASSWORD='root' lazylemonkitty/test:latest
```

# 推送容器至 docker hub

1.   登录 docker，`docker login` 或 `docker login -u <用户名>`

     >   提前在 docker desktop 上登录可节省时间

2.   docker hub 上创建一个仓库将其命名与镜像名一致

3.   标记镜像 `docker tag <本地镜像名>:<标签> <你的用户名>/<仓库名>:<标签>`

4.   推送镜像 `docker push <你的用户名>/<仓库名>:<标签>`

# 查看日志

`docker logs <容器名>`

# 删除容器

`docker ps -a` 查看所有包括已经停止的容器

`docker stop <容器名>` 停止运行中的容器

`docker rm <容器名>` 删除容器

`docker images` 查看所有的镜像

`docker rmi <镜像名>` 删除指定的镜像