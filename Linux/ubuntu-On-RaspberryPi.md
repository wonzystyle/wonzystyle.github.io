# ubuntu-On-RaspberryPi
### 下载镜像
* [ubuntu](https://cn.ubuntu.com/download/raspberry-pi)

### 烧录镜像
### server版本
##### 修改密码
* 树莓派安装的Ubuntu server镜像， 默认的初始用户及密码：  
用户名:
ubuntu 
密码: 
ubuntu  
* 默认密码修改
在登录界面 输入初始化的用户名和密码后， 会提示是第一次登录， 需要先输入默认密码之后 ， 再输两次新设置密码即可重置默认密码成功。

##### 配置WIFI
* 打开配置文件
  文件名有可能不同
```
sudo nano /etc/netplan/50-cloud-init.yaml
```
* 修改
```
 wifis:
        wlan0:
            access-points:
                "Edges":
                    password: "stdx.com"
            #dhcp4: true
            #optional: true
            addresses:
                - 192.168.1.253/24
            routes:
                - to: default
                  via: 192.168.1.1
            nameservers:
                addresses:
                    - 114.114.114.114
                    - 8.8.8.8
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

##### 设置时区
```
sudo dpkg-reconfigure tzdata
```