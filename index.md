# 读书随笔


### Linux
* [下载烧录工具](Linux/images-burn-tools.md)
* 安装
  * [ubuntu](Linux/ubuntu.md)
  * [RaspberryPi](Linux/RaspberryPi.md)
  * [ubuntu-On-RaspberryPi](Linux/ubuntu-On-RaspberryPi.md)
* [网络访问](Linux/networking.md)
* [远程接入](Linux/remote-access.md)

### ROS2
##### 版本
* [foxy官网](http://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Configuring-ROS2-Environment.html)

##### 代码
* c++
  * [helloword-ros2-cpp](https://github.com/wonzystyle/helloword-ros2-cpp)

### github
##### 注册
* 国外邮箱（如[outlook.com](https://outlook.live.com/owa/)）
* [github.com](https://github.com/signup?source=login)账号

##### 设置令牌[access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

##### 仓库
* [创建仓库](https://docs.github.com/cn/get-started/quickstart/hello-world)
*  推送本地仓库
创建本地仓库目录，将仓库内容拷贝到该目录下
   - [helloword-ros2-cpp](github/Update-helloword-ros2-cpp-Repository.md)
   - [wonzystyle.github.io](github/Update-wonzystyle.github.io-Repository.md)

##### README.md格式
* [官方文档](https://docs.github.com/cn/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github)
* [CSDN文档](https://blog.csdn.net/Strive_For_Future/article/details/120956016)

### Docker
##### 安装Docker
*  [RUNOOB文档](https://www.runoob.com/docker/ubuntu-docker-install.html)
* [Ubuntu](docker/installation/install-docker-on-ubuntu.md)
* [Raspberry Pi OS Lite](https://www.runoob.com/docker/debian-docker-install.html)
* [添加当前用户](docker/installation/add-user-to-docker.md)
* [更改Docker国内源](https://www.daocloud.io/mirror)
* [添加registry-1.docker.io地址](/docker/installation/add-registry-1-docker-io-address.md)

##### 镜像资源
* [官网](https://hub.docker.com/)
* [ros:foxy镜像](https://hub.docker.com/_/ros/tags?page=1&name=foxy)

##### 注册[hub.docker.com](https://hub.docker.com/)

##### 镜像制作
* 单架构
  * [wonzystyle/helloword-foxy-cpp](docker/images-making/uni-helloword-foxy-cpp.md)

* 多架构
  * [wonzystyle/helloword-foxy-cpp](docker/images-making/mult-helloword-foxy-cpp.md)
  * [wonzystyle/helloword-foxy-html](docker/images-making/mult-helloword-foxy-html.md)

##### 镜像删除及应用
* [wonzystyle/helloword-foxy-cpp](docker/images-applications/app-helloword-foxy-cpp.md)

##### Docker其他事项
* [图形界面](docker/gui/display-gui.md)
* [ROS2多机通信](docker/communication/mult-hosts.md)
  
### Web部署
##### [开发环境](web/DevelopmentEnvironment.md)

##### [创建项目](web/buildProject.md)

##### [开发备忘](web/developMemo.md)

##### [部署服务器](web/deploy.md)

