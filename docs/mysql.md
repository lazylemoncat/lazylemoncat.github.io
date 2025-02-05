[TOC]

# 连接 mysql

## python 连接mysql

```python
import mysql.connector  
# 连接数据库  
mydb = mysql.connector.connect(  
    host="localhost",  
    user="root",  
    password="password",  
    database="mydatabase"  
)  
# 创建游标对象  
mycursor = mydb.cursor()  
# 执行SQL查询  
mycursor.execute("SELECT * FROM customers")  
# 获取查询结果  
result = mycursor.fetchall()  
# 打印结果  
for row in result:  
    print(row)  
# 关闭游标和连接  
mycursor.close()  
mydb.close()
```

# mysql docker

## 创建 docker 镜像

1.   在 docker hub 上搜索 mysql, 在 tag 页面找到想要的版本并复制命令 `docker pull mysql:8.0.40`.

>   错误: `error during connect: Post "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/v1.47/images/create?fromImage=mysql&tag=8.0.40": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.`
>
>   解决方案: 打开 docker desktop

>   错误: `Error response from daemon: Get "https://registry-1.docker.io/v2/": context deadline exceeded`
>
>   解决方案: 找到国内正常可用的镜像源, 如 `dockerpull.org`, 使用 `docker pull dockerpull.org/mysql:8.0.40`

2.   `docker images` 或 docker desktop 查看是否存在 mysql 容器。
3.   运行容器 `docker run -d --name mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=root mysql:8.0.40`

# 连接 mysql docker

1.   进入创建的容器中 `docker exec -it mysql bash`

2.   输入 `mysql -u root -p` 并输入密码

3.   ```mysql
     use mysql;  //切换数据库
     update user set host='%' where user='root'; //允许root用户远程访问
     select user,host from user;   //查询
     flush privileges;  //刷新权限立即生效
     ```

>   当执行 `update user set host='%' where user='root';` 时,报错 `ERROR 1062 (23000): Duplicate entry '%-root' for key 'user.PRIMARY'`
>
>   解决方案: 删除后再插入, `DELETE FROM user WHERE Host = '%' AND User = 'root';`

4.   ```python
     mydb = mysql.connector.connect(  
         host="localhost",
         port=3307,
         user="root",
         password="root",
         database="test"
     ) 
     ```
