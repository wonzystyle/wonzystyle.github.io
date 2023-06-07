### 开发环境
#### 安装Node.js
* 命令安装
```
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs
```
* 查看版本
```
node -v
npm -v
```

* 安装 http-server
```
sudo npm install http-server -g
```


应用程序源目录
```
/etc/apt/sources.list.d
```

#### 部署vscode
##### 配置vscode
A.安装Vue Language Features (Volar)插件，是vue语法的高亮插件。
B.TypeScript Vue Plugin插件，使得写法为 lang=ts 的组件能用 *.vue 引入。
C.安装eslint插件，是智能错误检测插件。
D.安装typeorm插件。
先要打开：查看-〉扩展，在搜索框中输入vetur，找到后安装。eslint同理。


#### 创建MySQL挂载目录
```
sudo mkdir /mydata
cd /mydata
sudo mkdir mysql
cd mysql
sudo mkdir log
sudo mkdir data
sudo mkdir conf
```

#### 安装MySQL
* 拉取镜像
```
docker pull mysql:5.7
```
* 启动MySQL
```
# docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
docker run -p 3306:3306 --name  wonzy-mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
```
* 解决中文乱码
在文件conf文件夹下创建: my.cnf文件，将下面内容复制进去
```
[client]
default-character-set=utf8
 
[mysql]
default-character-set=utf8
 
[mysqld]
init_connect=‘SET collation_connection = utf8_unicode_ci‘
init_connect=‘SET NAMES utf8‘
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
default-time-zone = '+8:00'
```
* 外挂启动MySQL

```
docker run -p 3306:3306 --name  wonzy-mysql -e MYSQL_ROOT_PASSWORD=123456 -v /mydata/mysql/log:/var/log/mysql -v /mydata/mysql/data:/var/lib/mysql -v /mydata/mysql/conf:/etc/mysql/conf.d -d mysql:5.7
```
/mydata/mysql/log: 自己宿主机上的一个目录路径 映射 容器中的 /var/log/mysql
/mydata/mysql/data:自己宿主机上的一个目录路径 映射 容器中的 /var/lib/mysql
/mydata/mysql/conf:自己宿主机上的一个目录路径 映射 容器中的 /etc/mysql/conf.d


* 进入MySQL容器中
````
docker exec  -it wonzy-mysql /bin/bash
````
* 登录MySQL
```
mysql -uroot -p123456
```
* 授权
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
```
* 退出
```
exit
```


#### 参考资料
* [Vite中文官方文档](https://cn.vitejs.dev/guide/)
* [vue-element-plus-admin](https://gitee.com/kailong110120130/vue-element-plus-admin)
* [快速上手](https://cn.vuejs.org/guide/quick-start.html)
* [Pinia](https://pinia.vuejs.org/zh/core-concepts/state.html)