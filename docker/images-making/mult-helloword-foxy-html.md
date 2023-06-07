# Hello Word foxy html
### 拉取ros:foxy镜像
```
docker pull ros:foxy
```

### 创建Dockerfile
```
mkdir ~/myImages
mkdir ~/myImages/helloword
mkdir ~/myImages/helloword/helloword-ros2-html
cd ~/myImages/helloword/helloword-ros2-html
nano Dockerfile
```

### 在Dockerfile中，添加
```
# FROM --platform=$TARGETPLATFORM ros:foxy
FROM --platform=$TARGETPLATFORM wonzystyle/helloword-foxy-cpp
# 镜像作者信息
MAINTAINER wonzystyle

RUN apt-get update
# RUN apt-get upgrade -y
# 设定时区
# ENV TZ=Asia/Shanghai
# RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
# 安装foxy，html前端接口
RUN apt-get install -y ros-foxy-rosbridge-server
# 安装firefox浏览器
RUN apt-get install -y firefox
# 安装中文字体
RUN apt-get install fonts-arphic-uming
# 创建launch文件 
RUN cat <<EOF > start.xml
<launch>
    <include file="/opt/ros/foxy/share/rosbridge_server/launch/rosbridge_websocket_launch.xml" />
    <node name="talker" pkg="talkandlisten" exec="talker"  output="screen" />
    <node name="listener" pkg="talkandlisten" exec="listener"  output="screen" />
</launch>
EOF


rm -rf /var/lib/apt/lists/*
# 运行
CMD ros2 launch start.xml & sleep 5s; firefox www.baidu.com
```

### 移除原镜像编译环境缓存
```
# 移除容器
sudo docker rm $(sudo docker ps -a -q)
# 移除过程镜像
docker rmi $(docker images | grep "none" | awk '{print $3}')
# 移除原镜像
docker rmi wonzystyle/helloword-foxy-html
```

###  登陆Docker
```
docker login
```

### 编译Dockerfile
```
docker buildx build --platform linux/amd64,linux/arm64 -t wonzystyle/helloword-foxy-html -f Dockerfile . --push
```

### 退出Docker
```
docker logout
```

### 拉取镜像
```
docker pull wonzystyle/helloword-foxy-html
```

### 允许使用当前显示
```
xhost +
```

### 启动
```
docker run --rm -it --net=host -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY --device /dev/dri wonzystyle/helloword-foxy-html
```
