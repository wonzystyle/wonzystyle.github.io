# Ubuntu安装docker
### 删除旧版本
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 安装
```
# 更新资源库
sudo apt update
# 安装证书
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
# 安装官方GPG key
sudo mkdir -p /etc/apt/keyrings
################  这段可以替换为国内阿里云镜像地址 开始
### 将2块 `https://download.docker.com/linux/ubuntu` 替换为 `https://mirrors.aliyun.com/docker-ce/linux/ubuntu`
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
# 建立docker资源库
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
################### 这段可以替换为国内阿里云镜像地址 结束
# 再次更新资源库
sudo apt update
# 开始安装
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
# 验证 是否安装成功
sudo docker -v
# Docker version 20.10.17, build 100c701
```