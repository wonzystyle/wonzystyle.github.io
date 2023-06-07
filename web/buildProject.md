### 创建项目
#### 构建项目
```
# npm create vue@latest wonzy
npm create vue@3 wonzy
...
```


#### 下载安装需要的插件
在项目目录下
* express
```
npm install express
```
* cors，用于处理接口跨域问题
```
npm install cors
```
* mysql
```
npm install mysql
```
* axios
```
npm install axios
```
* 安装chinese-lunar-calendar
```
npm install --save chinese-lunar-calendar
```
* 安装安装print-js
```
npm install print-js --save
```
* 安装shelljs，用于关闭服务器
```
npm install shelljs --save
```
* 安装粘贴版
```
npm install --save vue-clipboard2
```

* vue无法识别require，执行命令：
```
npm install @types/node --save-dev
```

#### 开发
vscode打开项目目录wonzy，路慢慢其修远兮......

* 让 ts 文件可以识别 vue 文件，识别mysql模块
  在env.d.ts 文件中，添加以下代码

```
declare module "*.vue" {
  import { defineComponent } from "vue";
  const Component: ReturnType<typeof defineComponent>;
  export default Component;
}
declare module 'mysql'
```

* 解决‘require’is not defined ( no-undef )问题，在 .eslinttrc.cjs文件module.exports中，添加
```
env: {
    node: true
  },
```
* 查看ip及端口占用情况
```
netstat -tunlp
```
* 按例程修改项目后，启动连接MySQL数据库服务
```
sudo node app.js
```
通过浏览器，访问127.0.0.1/user，OK！



#### 参考
* [Vue项目通过node连接MySQL数据库并实现增删改查操作](https://blog.csdn.net/weixin_52580677/article/details/123204092)
* [MySQL基本语法](https://blog.csdn.net/liustreh/article/details/123411958)
* [使用Express快速部署vue项目](https://www.bilibili.com/read/mobile?id=15263164&plat_id=5&share_from=article&share_medium=android&share_plat=android&share_session_id=22c3107e-1f58-4787-afab-53c7300929fb&share_source=WEIXIN&share_tag=s_i&timestamp=1680525140&unique_k=NTUcz6X)
