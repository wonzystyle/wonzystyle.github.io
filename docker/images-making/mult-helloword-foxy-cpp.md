# Hello Word foxy c++
### 拉取ros:foxy镜像
```
docker pull ros:foxy
```

### 创建Dockerfile
```
mkdir ~/myImages
mkdir ~/myImages/helloword
mkdir ~/myImages/helloword/helloword-foxy-cpp
cd ~/myImages/helloword/helloword-foxy-cpp
nano Dockerfile
```

### 在Dockerfile中，添加
```
FROM --platform=$TARGETPLATFORM ros:foxy
# 镜像作者信息
MAINTAINER wonzystyle
# 设定时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get upgrade -y  #告警提示
RUN git clone https://ghproxy.com/github.com/wonzystyle/helloword-ros2-cpp.git
RUN rm -rf /var/lib/apt/lists/*
# RUN echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ~/.bashrc
# 多机通信
RUN echo "export ROS_DOMAIN_ID=101" >> ~/.bashrc
# 设置编译变量
ARG ROS_DISTRO=foxy
ARG ROS_VERSION=2
ARG ROS_PYTHON_VERSION=3
ARG ROS_DOMAIN_ID=101
ARG AMENT_PREFIX_PATH=/opt/ros/${ROS_DISTRO}
ARG PYTHONPATH=/opt/ros/${ROS_DISTRO}/lib/python3.8/site-packages
ARG LD_LIBRARY_PATH=/opt/ros/${ROS_DISTRO}/opt/yaml_cpp_vendor/lib:/opt/ros/${ROS_DISTRO}/lib/aarch64-linux-gnu:/opt/ros/${ROS_DISTRO}/lib
ARG ROS_LOCALHOST_ONLY=0
ARG PATH=/opt/ros/${ROS_DISTRO}/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
#ARG ROS_DISTRO=foxy
# 编译
WORKDIR /helloword-ros2-cpp
RUN colcon build --packages-select talkandlisten
# RUN . /helloword-ros2-cpp/install/setup.bash
RUN echo "source install/setup.bash" >> /opt/ros/${ROS_DISTRO}/setup.bash
# 移除原代码及编译过程文件
RUN rm -rf build
RUN rm -rf log
RUN rm -rf src
```

### 移除原镜像编译环境缓存
```
# 移除容器
sudo docker rm $(sudo docker ps -a -q)
# 移除过程镜像
docker rmi $(docker images | grep "none" | awk '{print $3}')
# 移除原镜像
docker rmi wonzystyle/helloword-foxy-cpp
```

###  登陆Docker
```
docker login
```

### 编译Dockerfile
```
docker buildx build --platform linux/amd64,linux/arm64 -t wonzystyle/helloword-foxy-cpp -f Dockerfile . --push
```

### 退出Docker
```
docker logout
```

### 拉取镜像
```
docker pull wonzystyle/helloword-foxy-cpp
```