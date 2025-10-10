














# Node

https://nodejs.org/en/
https://nodejs.org/download/release/v16.13.1/docs/api/
https://github.com/nodejs/node



https://www.runoob.com/nodejs/nodejs-tutorial.html



```bash

# 配置
mac安装位置
/usr/local/bin/node
/usr/local/bin/npm
确保/usr/local/bin is in your $PATH


```





# NPM

https://www.npmjs.com/



https://npmmirror.com/ 镜像站
```bash
# 使用淘宝镜像的命令
npm get registry # 查看镜像地址
# 设置默认淘宝镜像地址（不要加-g全局参数）
npm config set registry https://registry.npm.taobao.org 
# 临时使用淘宝镜像地址 安装cnpm可以使用中国定制版npm,速度更快
npm install -g cnpm --registry=https://registry.npmmirror.com
# 如果后悔了,想恢复默认设置,删除用户目录下的.npmrc文件（因为windows默认打开用户目录执行npm命令,如果加上-g参数,.npmrc文件就不是在用户目录找了）
```


```bash
# NPM包管理工具
npm -v # 查看版本
npm init --yes # 初始化,在当前目录下多了一个package包
npm install # 安装所有package.json依赖中的包
sudo npm install npm -g # 升级旧版npm
npm install npm -g # window系统升级npm
npm install moduleName # 安装模块到项目目录下
npm install moduleName -g # -g的意思是将模块安装到全局
# 具体安装到哪个目录下,要查看npm -config prefix -g目录下
npm install moduleName -save 
# -save的意思是将模块安装到项目目录下,并在package文件的dependencies节点写入依赖
npm install moduleName -save-dev # -save-dev的意思是将模块安装到项目目录下
# 并在package文件的devDependencecies节点写入依赖
# -D 表示开发环境的包
npm uninstall express # 卸载模块

npm ls # 查看包是否存在
npm update express # 更新模块
npm search express # 搜索模块

npm list -g # 查看已安装的模块
npm list grunt # 查看某个模块的版本号

```

```bash
# 全局和本地
全局安装是在node库中 (/usr/local/lib/node_modules/npm/docs)安装,全局安装加参数 -g
本地安装是在命令行的当前目录~下安装

```

```bash
# 调试命令
打开chrome://inspect配合调试
node --inspect --inspect-brk server.js

```


https://docs.npmjs.com/creating-a-package-json-file/
```js
// Package.json
package.json 位于模块的目录下,用于定义包的属性。接下来让我们来看下 express 包的 package.json 文件,位于 node_modules/express/package.json

name - 包名。
version - 包的版本号。
description - 包的描述。
homepage - 包的官网 url 。
author - 包的作者姓名。
contributors - 包的其他贡献者姓名。
dependencies - 依赖包列表。如果依赖包没有安装,npm 会自动将依赖包安装在 node_module 目录下。
repository - 包代码存放的地方的类型,可以是 git 或 svn,git 可在 Github 上。
main - main 字段指定了程序的主入口文件,require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。
keywords - 关键字


```



# Node Model


https://nodejs.org/docs/latest/api/
https://nodejs.org/docs/latest/api/documentation.html


内置模块是安装完nodejs可以直接使用的模块,也叫核心模块
第三方的模块是需要下载别人写好的模块
自定义模块是自己写的模块,也叫文件模块


ES是js的语法糖,是更高级的js,浏览器不一定支持ES
custom是自定义模块,node要用js来编写


https://v8.dev/
https://tc39.es/ecma262/
https://ecma-international.org/publications-and-standards/standards/ecma-262/
https://nodejs.org/api/modules.html
CJS(CommonJS), 是nodejs第三方的规范,后端的js,浏览器不支持的规范
ESM(ESModule), 是ECMAScript自己的模块体系



使用模块四个步骤：定义模块,暴露模块接口,定义模块,调用模块

webpack也使用commonjs










```javascript
// commonjs
// 自定义模块

//name.js
//第一步:定义模块
const name = {surname: 'zhang',
    sayName() {console.log(this.surname);},}
const age = {age: 100,}
//第二步:暴露模块
// module.exports = name;//单个模块
// module.exports = {name, age};//多个模块
// exports.name = name;exports.age = age;//也能成立
// exports = module.exports; //exports是一个引用
// exports = {name,age};//不能这样写,因为这样重新给exports引用到另一个对象上
exports.nameage = {name, age}

//app.js
//第三步:引入模块
// const nameage = require("./name");//单个名称
const {name,age} = require('./name')//解构模块
//第四步:使用模块
// nameage.name.sayName();console.log(nameage.age.age);//单个模块
name.sayName();console.log(age.age);//解构用法
//还可以导出
module.exports = app;

//app2.js // 可以引用到name.js
const app = require('./app.js')
console.log(app)

```


```js
// module URL
const url = require('url')
// console.log(url);
const urlString = "http://www.example.com:8080/demo/server/user/login.html?username=zhangsan&password=lisi#tag=3";
console.log(url.parse(urlString))// 把字符串解析成对象

const urlObject = {
    protocol: 'http:', slashes: true, auth: null,
    host: 'www.example.com:8080', port: '8080',
    hostname: 'www.example.com', hash: '#tag=3',
    search: '?username=zhangsan&password=lisi',
    query: 'username=zhangsan&password=lisi',
    pathname: '/demo/server/user/login.html',
    path: '/demo/server/user/login.html?username=zhangsan&password=lisi',
    href: 'http://www.example.com:8080/demo/server/user/login.html?username=zhangsan&password=lisi#tag=3'
}
const urlObject = url.parse(urlString);
urlObject.hash = "";
console.log(url.format(urlObject)) //把对象转换成字符串

// 路径寻找url
console.log(url.resolve('http://www.abc.com/a','../'))
console.log(url.resolve('http://www.abc.com/a','/b'))

//解析url地址的参数
const urlParams = new URLSearchParams(url.parse(urlString).search)
console.log(urlParams);
console.log(urlParams.get('username'));
console.log(urlParams.get('password'));


```

https://nodejs.org/docs/latest/api/fs.html
```js
// File
const fs = require('fs');
const fsP = require('fs').promises;

fs.mkdir('./logs',(err) => {console.log('mkdone.');})//创建文件夹
fs.rename('./logs','./log',(err) => {console.log('redone.');})//文件夹重命名
fs.rmdir('./log',() => {console.log('rmdone.');})//创建文件夹
fs.readdir('./logs',(err, result) => {console.log(result);})//读取文件夹内容

fs.writeFile('./logs/log1.txt','hello',(err) => {//把hello字段写入文件里
    if(err){console.log(err.message);}
    else {console.log('文件创建成功！');}
})
fs.appendFile('./logs/log1.txt','!!!',(err) => {console.log('done.')})//追加内容
fs.unlink('./logs/log1.txt',(err)=>{console.log('done.')})//删除文件
fs.readFile('./logs/log1.txt','utf-8',(err,content)=>{console.log(content.toString());})//读取文件

//以上操作都是异步的,文件操作总是后执行
const content = fs.readFileSync('./logs/log1.txt');//同步操作
console.log(content.toString());//先执行
console.log('continue...');//最后执行

```






```js
// HTTP
// node不需要使用Apache或者NGINX来充当服务器,nodejs自带服务器模块,分为下面三步
// 1引入required模块 2创建服务器 3接收请求与响应请求

// server.js
var http = require('http');//使用require指令来载入http模块
http.createServer(function (request, response) {
    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});
    // 发送响应数据 "Hello World"
    response.end('Hello World\n');
}).listen(8888);
// 终端打印如下信息
console.log('Server running at http://127.0.0.1:8888/');



```









# 第三方模块

## expressjs

http://expressjs.com/
https://www.npmjs.com/package/express
https://github.com/expressjs/express



```js
// Web开发框架
// npm install express --save

// 使用ajax请求获取这些响应
const express = require('express'); // 引入包名
const app = express(); //创建应用对象


app.get('/',(request,response)=>{ //创建路由规则
    //设置响应内容
    response.send("Hello Express");//返回响应内容
});
app.get('/server',(request,response)=>{ //路由规则
    response.setHeader('Access-Control-Allow-Origin','*'); //设置响应头
    response.send("Hello Ajax"); // 返回响应内容
})
let server = app.listen(8080, () => { // 监听端口启动服务
    let host = server.address().address
    let port = server.address().port
    console.log("Application Demo, visit http://%s:%s", host, port)
})
// app.listen(8080,()=>{console.log("服务已启动,8080端口监听中...")})

```


## Log4JS

https://www.npmjs.com/package/log4js log4js日志系统


```js
// log4js 日志系统
// npm i log4js --save -D
// ALL,TRACE,DEBUG,INFO,WARN,ERROR,FATAL,MARK,OFF
const log4js = require('log4js')

/*//error级别以上的信息，输出到文件中的配置
log4js.configure({ 
    appenders: {cheese: {type: "file", filename: "cheese.log"}},
    categories: {default: {appenders: ["cheese"], level: "error"}}})
let logger = log4js.getLogger("cheese");*/

let logger = log4js.getLogger();
logger.level = "ALL";
logger.trace("trace blue");
logger.debug("debug cyan");
logger.info("info green");
logger.warn("warn yellow");
logger.error("error red");
logger.fatal("fatal magenta");
logger.mark("mark grey");



```





# Yarn
https://yarnpkg.com/


# add-one

```bash
# node进程管理工具
supervisor   forever   pm2

nodemon (npm install nodemon -g & nodemon server.js)用这个管理工具能自动重启脚本,修改代码后不需要手动重启
npm install --save-dev nodemon
```





```bash
# Babel转码器 es6->es5
npm install -g babel-cli


```







# nvm

Linux 和 macOS 使用
https://github.com/nvm-sh/nvm

Windows 版本使用
https://github.com/coreybutler/nvm-windows



https://www.runoob.com/w3cnote/nvm-manager-node-versions.html

C:\Program Files\nodejs文件夹删除掉, 否则nvm无法创建快捷方式

# pnpm

https://pnpm.io/



