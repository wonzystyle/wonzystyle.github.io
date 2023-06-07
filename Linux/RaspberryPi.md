# RaspberryPi
### 下载镜像
* [RaspberryPi](https://www.raspberrypi.com/software/operating-systems/)

### 解压
### 烧录镜像
##### 配置wifi、ssh
```
sudo raspi-config
```

### Raspberry Pi OS Lite版本
##### 配置wifi固定ip
* 修改 wpa_supplicant.conf
  * 打开配置文件
  ```
  sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
  ```
  * 添加
  ```
  network={
          ssid="Yang Office"
          psk="stdx.com"
          key_mgmt=WPA-PSK
          priority=1   #连接优先级
  }
  ```
* 修改 interfaces
   * 打开配置文件
  ```
  sudo nano /etc/network/interfaces
  ```
  * 添加
  ```
  auto wlan0
  allow-hotplug wlan0
  #iface wlan0 inet manual
  # wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
  iface wlan0 inet static
  #wpa-ssid "ssid"
  #wpa-psk "pswd"
  address 192.168.1.113
  netmask 255.255.255.0
  gateway 192.168.1.1
  network 192.168.1.1
  #iface default inet dhcp
  wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
  ```
* 重启网络
```
sudo service networking restart
```
* 查看ip
```
ifconfig
```

##### 设置时区
```
sudo dpkg-reconfigure tzdata
```