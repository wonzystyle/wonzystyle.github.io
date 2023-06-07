# ubuntu
### 下载镜像
* [ubuntu](https://cn.ubuntu.com/download/)

### 烧录镜像
### server版本
##### 配置ip地址
* 打开配置文件
  文件名有可能不同
```
sudo nano /etc/netplan/00-installer-config.yaml
```
* 修改
```
 # This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
#      dhcp4: true
      addresses:
        - 192.168.1.114/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 114.114.114.114
          - 8.8.8.8
  version: 2
```
* 重启网络
  ```
  sudo netplan generate
  sudo netplan apply
  ```
* 查看ip
```
ifconfig
```

##### 更换腾讯源
* 打开配置文件
```
sudo nano /etc/apt/sources.list 
```
* 修改
```
deb https://mirrors.cloud.tencent.com/ubuntu/ jammy main restricted universe multiverse
deb-src https://mirrors.cloud.tencent.com/ubuntu/ jammy main restricted universe multiverse
deb https://mirrors.cloud.tencent.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src https://mirrors.cloud.tencent.com/ubuntu/ jammy-security main restricted universe multiverse
deb https://mirrors.cloud.tencent.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src https://mirrors.cloud.tencent.com/ubuntu/ jammy-updates main restricted universe multiverse
deb https://mirrors.cloud.tencent.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb-src https://mirrors.cloud.tencent.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb https://mirrors.cloud.tencent.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src https://mirrors.cloud.tencent.com/ubuntu/ jammy-backports main restricted universe multiverse
```
* 执行
```
sudo apt clean all
sudo apt update
```

##### 设置时区
```
sudo dpkg-reconfigure tzdata
```

##### 安装NVIDIA显卡
