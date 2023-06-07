# Docker 图像界面
### 允许使用当前显示
```
xhost +
```

### 启动镜像
~~~
docker run --rm -it -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY --device /dev/dri ros:foxy
~~~

### 容器中测试
~~~
apt-get update
apt-get install xarclock       #安装这个小程序
xarclock
~~~
