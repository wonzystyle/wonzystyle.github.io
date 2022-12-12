# 安装模拟多平台环境
### 安装qemu-user-static
qemu-user-static 用来模拟多平台环境，它依赖于binfmt-support，所以这两者都要安装。
```
sudo apt install -y qemu-user-static binfmt-support
```
通知Docker使用qemu
```
docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
```