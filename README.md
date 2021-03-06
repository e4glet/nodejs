# nodejs web开发框架
### 作者：eaglet liyaohua8468@gmail.com
### 天津市工业大学 计算机科学与软件学院 天津市大学软件学院

#### 目录

- 简介
- 目录结构介绍
- 环境要求
- 初始化环境
- 如何启动

#### 一、简介
  本框架是基于nodejs express框架二次开发的，参考之前的一些项目结构和ASP.NET MVC框架修改而成，本框架包含数据库操作示例和注解。
  适合nodejs入门学习或者nodejs开发人员开发中小型web项目。

#### 二、目录结构介绍
    –bin            项目的底层核心，路由配置文件
	-conf           配置目录（数据库连接信息和数据库工具模块）
	-Controller     控制器目录
	-DAL            数据层目录
    –node_modules   项目中依赖的包
    –public         公共资源放的目录
    –routes         学名 路由，里面放着一些路由文件
    –views          放着就是页面文件了
    –app.js         项目的入口文件。当然你也可以改成其他的名字。
    –package.json    项目版本信息文件
	-move.sql        mysql导出文件 
    
#### 三、环境要求
- nodejs 6.0以上版本
- 系统环境：windows/linux/Mac OS
- 开发工具：Sublime Text

###  四、初始化环境
1. 在命令行输入命令;
```c
npm install express -gd
```

2. 最新express4.0版本中将命令工具分家出来了,所以我们还需要安装一个命令工具,命令如下:
```c
npm install -g express-generator
``` 

```c
npm install
``` 

3. NodeJS热部署工具 — supervisor
```c
npm install supervisor -g
```

以上三个命令均为全局安装，其他模块已经包含在项目中


#### 五、如何启动？
以windows系统为例：
打开CMD，进入项目目录
运行npm start

打开浏览器：http://localhost:3000/
即可访问项目。
```c
D:\nodejs\nodejs_http_framework>npm start

> web@0.0.0 start D:\nodejs\nodejs_http_framework
> supervisor ./bin/www


Running node-supervisor with
  program './bin/www'
  --watch '.'
  --extensions 'node,js,/bin/www'
  --exec 'node'

Starting child process with 'node ./bin/www'
Watching directory 'D:\nodejs\nodejs_http_framework' for changes.
Press rs for restarting the process.

```

## Docker部署

```c
#提取镜像
FROM hub.c.163.com/lightingfire/nodejs:6.9.1-alpine
#版本信息
MAINTAINER eaglet
#设置工作目录
RUN mkdir -p /home/www
WORKDIR /home/www
COPY package.json /home/www
RUN npm i --registry https://registry.npm.taobao.org && npm cache clean && npm install express -gd && npm install -g express-generator && npm install && npm install supervisor -g
COPY . /home/www
EXPOSE 3000
CMD [ "npm", "start" ]
```
## 小结
这个web项目框架不一定是最好的框架，但是希望可以帮助一些想学习nodejs的朋友。如果你有更好改进建议，欢迎指正。
邮箱：liyaohua8468@gmail.com
