### 部署服务器


#### 远程挂载
服务器安装
```
sudo apt install openssh-server
```
挂载
```
ssh -o ServerAliveInterval=600 host@192.168.1.114
sshfs -o ServerAliveInterval=600 host@192.168.1.114:/home/host HostsDir
```
#### 解压数据库及配置文件
```
tar zxvf mydata.tgz 
cd /
sudo cp -r /home/host/mydata .
```
压缩
```
tar -zcvf mydata.tgz mydata
```
#### 拉取镜像
```
docker pull mysql:5.7
docker pull wonzystyle/prove-effect
```
#### 复制mysql数据库等相关文件到相关目录
#### 系统启动文件
* 项目启动文件
```
touch startup.sh
nano startup.sh
```
添加
```
docker stop $(docker ps -a -q) # 停止容器
docker rm $(docker ps -a -q) # 移除容器
docker run -p 3306:3306 --name  wonzy-mysql -e MYSQL_ROOT_PASSWORD=123456 -v /mydata/mysql/log:/var/log/mysql -v /mydata/mysql/data:/var/lib/mysql -v /mydata/mysql/conf:/etc/mysql/conf.d -d mysql:5.7
# docker run --rm -it --net=host --pid=host --privileged=true wonzystyle/prove-effect #开发环境，批处理文件，终端运行
docker run --rm -i -d --net=host --pid=host --privileged=true  wonzystyle/prove-effect #生产环境，自启动服务运行
echo 'web start up'
```
执行权限
```
chmod u+x startup.sh
```
* 添加自启动
```
sudo nano /lib/systemd/system/rc-local.service
```
末尾添加
```
[Install]
WantedBy=multi-user.target
Alias=rc-local.service
```
* 添加服务
```
sudo nano /etc/rc.local
```
填入服务内容
```
#!/bin/sh
echo '/etc/rc.local start'&
/home/host/startup.sh&
echo '/home/host/startup.sh end'&
exit 0
```
执行权限
```
sudo chmod a+x /etc/rc.local
```
* 创建rc-local.service软链接
```
sudo ln -s /lib/systemd/system/rc-local.service /etc/systemd/system/
```
* 远程卸载
```
sudo umount HostsDir
```
* 重新启动
```
sudo reboot
```
* 查看服务启动状态
```
systemctl status rc-local.service
```
* 重新启动服务
```
systemctl restart rc-local
```

sudo systemctl enable rc-local
