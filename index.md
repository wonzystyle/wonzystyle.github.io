# 读书随笔

### ubuntu
* [ubuntu-On-RaspberryPi](ubuntu/ubuntu-On-RaspberryPi.md)
* [网络访问](ubuntu/networking.md)
* [VPN](ubuntu/VPN.md)

### ROS2
* [foxy官网](http://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html)

### github
##### 注册
* 国外邮箱（如[outlook.com](https://outlook.live.com/owa/)）
* [github.com](https://github.com/signup?source=login)账号
##### 设置令牌[access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
##### 仓库
* [创建仓库](https://docs.github.com/cn/get-started/quickstart/hello-world)
*  推送本地仓库
创建本地仓库目录，将仓库内容拷贝到该目录下
   - [helloword-foxy-cpp](github/Update-helloword-foxy-cpp-Repository.md)
   - [wonzystyle.github.io](github/Update-wonzystyle.github.io-Repository.md)

##### README.md格式
* [官方文档](https://docs.github.com/cn/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github)
* [CSDN文档](https://blog.csdn.net/Strive_For_Future/article/details/120956016)

### Docker
##### 安装Docker
*  [RUNOOB文档](https://www.runoob.com/docker/ubuntu-docker-install.html)
  
* Ubuntu
  * [安装步骤](docker/installation/install-docker-on-ubuntu.md)
  * [更改Docker国内源](https://www.daocloud.io/mirror)
  * [模拟多平台环境](docker/buildx/build-multi-platform.md)用于编译多架构镜像

##### 镜像资源
* [官网](https://hub.docker.com/)
* [ros:foxy镜像](https://hub.docker.com/_/ros/tags?page=1&name=foxy)

##### 注册[hub.docker.com](https://hub.docker.com/)

##### 镜像制作
* 单架构
  * [wonzystyle/helloword-foxy-cpp](docker/images-making/uni-helloword-foxy-cpp.md)

* 多架构
  * [wonzystyle/helloword-foxy-cpp](docker/images-making/mult-helloword-foxy-cpp.md)

##### 镜像删除及应用
* [wonzystyle/helloword-foxy-cpp](docker/images-applications/app-helloword-foxy-cpp.md)
##### Docker其他事项
* [图形界面](docker/gui/display-gui.md)