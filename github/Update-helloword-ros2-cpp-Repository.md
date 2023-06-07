终端命令
```
cd ~/myGithub/helloword/helloword-ros2-cpp #本地仓库目录
sudo rm -rf .git
# echo "# helloword" >> README.md
git init
git add --all
git commit -m "first commit"
git branch -M main
# 加上代理GitHub Proxy：https://ghproxy.com/
git remote add origin https://ghproxy.com/github.com/wonzystyle/helloword-ros2-cpp.git #github仓库
# git push -u origin main
git push -u origin +main
```