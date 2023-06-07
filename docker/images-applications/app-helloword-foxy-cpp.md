# Hello Word foxy c++
### 运行镜像
```
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten listener
```
或
```
docker run --rm -it wonzystyle/helloword-foxy-cpp bash -c "ros2 run talkandlisten talker & sleep 10s; ros2 run talkandlisten listener"
```

### 相关Docker命令
##### 查看镜像
```
docker images
```

##### 进入镜像
终端窗口启动镜像
```
docker run --rm -it wonzystyle/helloword-foxy-cpp
```
发布话题
```
ros2 topic pub /chatter std_msgs/msg/String 'data: "Hello wonzystyle"'
ros2 run talkandlisten talker
```
终端窗口启动镜像
```
docker run --rm -it wonzystyle/helloword-foxy-cpp
```
查看话题
```
ros2 topic list
```
查看、订阅话题内容
```
ros2 topic echo /chatter
ros2 run talkandlisten listener
```

##### 后台运行镜像
```
docker run --name talker-ros-app -itd wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
``` 
查看后台运行容器运行情况
```
docker logs talker-ros-app
```
进入后台正在运行的容器
```
docker exec -it talker-ros-app bash
source /opt/ros/${ROS_DISTRO}/setup.bash
```

##### 查看运行容器
```
docker ps -a
```

##### 移除容器
```
docker stop talker-ros-app
docker rm talker-ros-app
```