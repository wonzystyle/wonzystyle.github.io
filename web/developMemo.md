### 开发备忘
#### 外挂启动MySQL
```
docker run -p 3306:3306 --name  wonzy-mysql -e MYSQL_ROOT_PASSWORD=123456 -v /mydata/mysql/log:/var/log/mysql -v /mydata/mysql/data:/var/lib/mysql -v /mydata/mysql/conf:/etc/mysql/mysql/conf.d -d mysql:5.7

```
/mydata/mysql/log: 自己宿主机上的一个目录路径 映射 容器中的 /var/log/mysql
/mydata/mysql/data:自己宿主机上的一个目录路径 映射 容器中的 /var/lib/mysql
/mydata/mysql/conf:自己宿主机上的一个目录路径 映射 容器中的 /etc/mysql/conf.d

#### 运行dist包

  进入dist包目录，运行
```
http-server -p 3000
```

#### http镜像制作

* 进入项目目录
```
touch Dockerfile
nano Dockerfile
``` 

* 在Dockerfile中，添加
  
```
FROM schoolbox/bionic-nodejs
# 镜像作者信息
MAINTAINER wonzy
# 设定时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get upgrade -y  #告警提示
# 指定工作目录
RUN mkdir proveEffect
RUN cd /proveEffect
WORKDIR /proveEffect
# 安装http-server服务
# RUN npm install http-server -g
# express
RUN npm install express
# cors，用于处理接口跨域问题
RUN npm install cors
# mysql
RUN npm install mysql
# axios
RUN npm install axios
 # 安装chinese-lunar-calendar
RUN npm install chinese-lunar-calendar
# 安装安装print-js
RUN npm install print-js
# 安装shelljs，用于关闭服务器
RUN npm install shelljs

# 项目复制
COPY dist /proveEffect/dist/
# 后端服务
COPY src/server /proveEffect/src/server/
# 启动文件
COPY webapp.js /proveEffect/
RUN rm -rf /var/lib/apt/lists/*

# 建立express连接
# RUN ln -s /usr/local/nodejs/bin/express /usr/local/bin/
# 启动
CMD [ "node", "webapp.js" ]
```

* 编译Dockerfile

```
docker build -t wonzystyle/prove-effect  .
```

* 启动服务
```
docker run --rm -it --net=host wonzystyle/prove-effect
```

* 镜像推送
```
docker login
docker push wonzystyle/prove-effect
docker logout
```

