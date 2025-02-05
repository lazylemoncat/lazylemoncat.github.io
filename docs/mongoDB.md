[TOC]

# 安装 MongoDB

1.   进入官网下载 MongoDB Community Edition
2.   安装时选择 Custom， 下方可以选择安装地址，确认时取消选择安装 Compass（否则时间会非常长）
3.   添加 MongoDB 安装位置的 bin 目录到环境变量中
4.   `mongod --version` 查看版本和确认安装成功

# 运行 MongoDB

1.   在安装位置中新建文件夹，类似于 ‘D:\Mongodb\Server\data\db’
2.   命令行输入 `mongod   --dbpath D:\Mongodb\Server\data\db`
3.   找到 pid 和 port, 端口号一般为27017
4.   浏览器输入 `http://localhost:27017`, 若出现 `It looks like you are trying to access MongoDB over HTTP on the native driver port.`, 则运行成功
5.   连接 mongoDB, `mongo` 或 `mongo --host=localhost --port=27017`

>   错误: 'mongo' 不是内部或外部命令，也不是可运行的程序
>   或批处理文件。
>
>   解决方案: 1.配置环境变量 2.mongoshell 在 mongoDB6 前是已经包含在内,6之后需要单独安装, 去官网找到mongoshell 并安装, 将安装后的文件放到bin目录下, 使用 `mongosh`

​	`mongosh` 或 `mongosh --host=localhost --port=27017`