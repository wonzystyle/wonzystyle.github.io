# Docker ROS2 跨主机通信
### 同一网段 不同主机
```
docker run --rm -it --net=host wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
docker run --rm -it --net=host wonzystyle/helloword-foxy-cpp ros2 run talkandlisten listener
```

### 同一网段 同一主机
```
docker run --rm -it --net=host wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten listener
```
或
```
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
docker run --rm -it --net=host wonzystyle/helloword-foxy-cpp ros2 run talkandlisten listener
```
或
```
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten talker
docker run --rm -it wonzystyle/helloword-foxy-cpp ros2 run talkandlisten listener
```