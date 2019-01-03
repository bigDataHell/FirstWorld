# node.js 安装

## 1 从官网下载node.js

## 2 安装node.js

* 选择默认安装路径: C:\Program Files\

## 3 检查npm和node是否安装成功

* node -v
* npm -v

## 4 在node.js的安装目录中创建两个文件夹

* node_cache
* node_global

## 5 打开cmd,输入以下命令

* npm config set prefix "C:\Program Files\nodejs\node_global"
* npm config set cache "C:\Program Files\nodejs\node_cache"

## 6 设置环境变量

### 6.1 用户变量

* 1 在用户变量中新建: NODE_PATH 
* 2 内容 : C:\Program Files\nodejs\node_global
* 3 将NODE_PATH 添加到path中

### 6.2 系统变量

* 1 在系统变量中新建: NODE_PATH 
* 2 内容: C:\Program Files\nodejs\node_global\node_modules
* 3 将NODE_PATH 添加到path中
* 4 直接在path中添加:C:\Program Files\nodejs
* 5 点击确定即可

