### 增加当前用户入docker组
```
# 增加当前用户入docker组中
sudo groupadd docker
# groupadd: group 'docker' already exists
sudo gpasswd -a $USER docker
# Adding user tester to group docker
newgrp docker
# 再次验证
docker ps -a
```