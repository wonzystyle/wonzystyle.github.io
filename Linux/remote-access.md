# 远程连接
## VPN L2TP

### desktop
#### client
##### 安装组件
```
sudo apt install network-manager-l2tp network-manager-l2tp-gnome
```

##### 设置
打开系统设置(Settings)--->网络(Network)---->点击左下角的“+”号

##### 云电脑（政企版专线）
```
sudo  service  xl2tpd  stop
sudo   update-rc.d  xl2tpd  disable
```

### server
#### client
##### 安装组件
```
sudo apt install xl2tpd
```

##### 配置xl2tpd.conf
```
sudo nano /etc/xl2tpd/xl2tpd.conf
```
添加
```
[lac goHome]
lns = xxx.xxx.xxx.xxx
ppp debug = yes
pppoptfile = /etc/ppp/options.l2tpd.client
length bit = yes
```

##### 设置拨号配置文件
```
sudo nano /etc/ppp/options.l2tpd.client
```
添加
```
ipcp-accept-local
ipcp-accept-remote
refuse-eap
require-mschap-v2
noccp
noauth
idle 1800
mtu 1410
mru 1410
defaultroute
replacedefaultroute
usepeerdns
debug
# lock
connect-delay 5000
name test
password test1234
```

##### 查看路由表
```
netstat -rn
```

#### 添加路由
```
sudo ip ro add xxx.xxxx.xxx.xxx via 192.168.1.1   #vpn服务地址
```

##### 启动xl2tpd
```
sudo service xl2tpd start
```

##### 查看状态
```
sudo service xl2tpd status
```

##### 拨号
```
sudo sh -c "echo 'c goHome' > /var/run/xl2tpd/l2tp-control"
```

sudo route add -net 0.0.0.0 netmask 0.0.0.0 dev ppp0

##### 挂断
```
sudo sh -c "echo 'd goHome' > /var/run/xl2tpd/l2tp-control"
```

##### 停止xl2tpd
```
sudo service xl2tpd stop
```

##### 删除路由
```
sudo ip ro del xxx.xxxx.xxx.xxx via 192.168.1.1   #vpn服务地址
```

##### 查看外网ip
```
curl ifconfig.me
```

##### 查看路由
```
ip route
```

##### 访问路由
```
traceroute  github.com
```

## RDP
### desktop
#### client
##### 安装组件
```
sudo apt install rdesktop
```

##### 连接
```
rdesktop -f -a 32 192.168.1.115
```

##### 退出全屏
Ctrl+Alt+Enter