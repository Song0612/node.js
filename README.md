# NVM的安装

## nvm是什么？

nvm 是node版本管理工具 （学习node，首先要安装node的环境，nvm是一款工具，使用这款工具可以很方便的下载所需版本的node文件以及npm，十分的方便。）

## windows下的安装：

windows下的离线安装：

* nvm 的windows下载地址：[https://github.com/coreybutler/nvm-windows/releases](https://github.com/coreybutler/nvm-windows/releases) , 选择第二个nvm-setup.zip(第一次安装默认到底，减少后面环境出错的几率，等玩熟了在自定义位置)

* 将下载的文件进行解压：nvm-setup.exe，单击开始安装，直接点击下一步解可以，当然我们需要注意一下两个界面：
  > ![设置nvm路径](https://img-blog.csdn.net/20170209085726130?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmFpZHVfMzIyNjIzNzM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  > ![设置node路径](https://img-blog.csdn.net/20170209085757334?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmFpZHVfMzIyNjIzNzM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  
## 安装完成后： 

* nvm安装路径默认为: C://Users/Administrator/AppData/Roming/nvm 
* nvm安装的node路径默认为: C://ProgramFile/nodejs （其实是个快捷方式） 
* nvm安装多个版本的node，原理是替换C://ProgramFile/nodejs中的node.exe

## 安装完成以后需要进行配置

```

这两行代码就是链接淘宝镜像，在下载node和npm速度会快很多（不用去国外的github上下了）
/**
*node下载源
*/
nvm node_mirror https://npm.taobao.org/mirrors/node/
/**
*npm下载源
*/
nvm npm_mirror  https://npm.taobao.org/mirrors/npm/

```


## windows下nvm的命令([]中的参数可有可无)：


```
nvm arch                         查看当前系统的位数和当前nodejs的位数
nvm install <version> [arch]     安装制定版本的node 并且可以指定平台 version 版本号  arch 平台
nvm list [available]         
  - nvm list   查看已经安装的版本
  - nvm list installed 查看已经安装的版本
  - nvm list available 查看网络可以安装的版本
nvm version         // 查看nvm版本
nvm install 4.6.2   // 安装node4.6.2版本（附带安装npm）
nvm uninstall 4.6.2 // 卸载node4.6.2版本
nvm list            // 查看node版本
nvm use 4.6.2       // 将node版本切换到4.6.2版本
nvm root　　　　     // 查看nvm安装路径 
nvm install latest  //下载最新的node版本和与之对应的npm版本
```




# nodejs具体安装过程：


应为需要我们这里安装的是nodejs5.3.0版本，
windows（安装windows 32位 nodejs5.3.0）:
```
nvm install 5.3.0 32
```

# nvm安装常见问题：
1. 安装完成后在cmd中输入 nvm 提示nvm不是内部命令或方法？（一般默认到底的安装都自动配好了环境变量，没有的话手动加一下，类似java环境变量配法）

原因：没有配置环境变量。找到nvm安装路径cd C:\Users\Administrator\AppData\Roaming\nvm,再键入nvm即可

2. settings.txt 系统不能找到指定的文件？

解答：替换 C://Users/Administrator/AppData/Roming/nvm目录中settings.txt的内容

```
root: C:\Users\Administrator\AppData\Roaming\nvm 
path: C:\Program Files\nodejs 
arch: 64 
proxy: none 
node_mirror: https://npm.taobao.org/mirrors/node/ 
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

## Linux 命令：
```
1.	ls 查看文件/目录
2.	pwd  显示当前的工作目录 
3.	cd    进入目录
   [例子]： 
   cd 回到注册进入时的目录 
   cd /tmp 进入 /tmp 目录 
   cd ../ 进入上级目录 
4.	mkdir  创建目录
5． rmdir  删除目录
6． cat  显示文件至标准输出
7．cp   拷贝
     [例子]: 
    cp file1 file2 将文件 file1 拷贝到文件 file2 
8. mv 移动
     - i 在覆盖已存在文件时作提示，若回答 y 则覆盖，其他则中止
[例子]: 
     mv file1 file2 将文件 file1 改名为 file2 
     mv file1 file2 /tmp 将文件 file1 和文件 file2 移动到目录 /tmp 下
9. touch 创建文件
10.vi 编辑 
    i 插入  编辑内容
    esc  退出编辑
    ：wq 保存并退出
   
   ```
   
### 解决乱码问题

```
  res.setHeader('Content-Type','text/html;charset=utf-8')
```
   
### 注册登录前端
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    
    <form action="http://localhost:8888/home/list/li/abc" method="post">
 
       用户名：<input type="text" name='user'> <br>
       密码：<input type="password" name='pass'>  <br>
       <button type="submit">登录</button>

    </form>
</body>
</html>
```

### 后端

```
var http=require('http');

var fs=require('fs');

var app=http.createServer(function(req,res){
    
    console.log(req.url)//     /aaa?user=lisi&pass=1234567889


    // var url='/aaa';

    // var obj={user:'lisi',pass:123456789}


    var str=req.url; // /aaa?user=lisi&pass=1234567889


      var obj={}

    var url_str=str.split('?');//字符串 以 指定字符 分割成数组   ['/aaa','user=lisi&pass=1234567889']

        var url=url_str[0];  //   路径 /aaa

        var arr=url_str[1].split('&');  //   ['user=lisi','pass=1234567889']

         for(var i=0;i<arr.length;i++){
              var arr1= arr[i].split("=") //  [uaer,lisi]  
              obj[arr1[0]]=arr1[1]
         }


   console.log(url,obj)




   
})


app.listen(8888,function(){
    console.log('服务器运行成功')
})
```

### querystring 模块

```
//参数解析模块
var querystring=require('querystring');

var str= '/aaa?user=lisi&pass=1234567889';


 var arr=str.split('?');


 var url=arr[0];

 var objstr=arr[1];  //  user=lisi&pass=1234567889

 var query=querystring.parse(objstr)


console.log(url,query)

```
### url 模块


// url模块 解析 url
var urlLib=require('url')

var str= '/aaa?user=lisi&pass=1234567889';


var obj=urlLib.parse(str,true);

var url=obj.pathname; //路径

var urlObj=obj.query


console.log(url,urlObj)


### post请求
```
    var url=urlLib.parse(req.url,true).pathname;

    var str=''
    req.on('data',function(thunk){
        str+=thunk;
    })

    req.on('end',function(){
        console.log(url,querystring.parse(str))
    })

  
```

### data 分次发送

```

    var str=req.url;//  /home

    var url=urLib.parse(str,true).pathname;

    var str=''
      
    var i=0;

    //分段传送  每当有一段数据提交过来 data事件就会触发一次
    req.on('data',function(thunk){
        i++
        console.log("当前次数为"+i)
        str+=thunk;
    });

    req.on('end',function(){
        console.log(querystring.parse(str));
    })

```


### npm 包发布


1.创建文件  loverqq

2.cd loverqq

3.执行 npm init  

       配置向导  name  version  description .....

       生成package.json  文件
      
       创建 index.js   
              --------定义模块 并且导出

4.注册  npm 账号 

   执行  npm adduser    // 注册npm

         username:tianxing
         password:11111111
         email:25554544@xx.com

     Logged in as tianxing on       https://registry.npmjs.org/.


5.发布 模块

    执行 npm publish


6.使用

  npm install loverqq     cnpm install loverqq
  
  
### 通过HTTP请求响应过程了解HTTP协议
      首先了解一次完整的HTTP请求到响应的过程需要的步骤

      1. 域名解析 
      2. 发起TCP的3次握手 
      3. 建立TCP连接后发起http请求 
      4. 服务器端响应http请求，浏览器得到html代码 
      5. 浏览器解析html代码，并请求html代码中的资源 
      6. 浏览器对页面进行渲染呈现给用户
      1.域名解析
      就是将网站名称转变成IP地址：localhost-->127.0.0.1
      DNS域名解析等等可以实现这种功能
      2.发起TCP的3次握手
      在客户机和服务器之间建立正常的TCP网络连接时：

      客户机首先发出一个SYN消息，

      服务器使用SYN+ACK应答表示接收到了这个消息，

      最后客户机再以ACK消息响应。

      这样在客户机和服务器之间才能建立起可靠的TCP连接，数据才可以在客户机和服务器之间传递。
      下面一段内容引自一次完整的HTTP事务是怎样一个过程？

      拿到域名对应的IP地址之后，User-Agent（一般是指浏览器）会以一个随机端口（1024 < 端口 < 65535）向服务器的WEB程序（常用的有httpd,nginx等）80端口发起TCP的连接请求。这个连接请求（原始的http请求经过TCP/IP4层模型的层层封包）到达服务器端后（这中间通过各种路由设备，局域网内除外），进入到网卡，然后是进入到内核的TCP/IP协议栈（用于识别该连接请求，解封包，一层一层的剥开），还有可能要经过Netfilter防火墙（属于内核的模块）的过滤，最终到达WEB程序（本文就以Nginx为例），最终建立了TCP/IP的连接。
      
      3.发起HTTP请求(HTTP Request)
      所谓的HTTP请求，也就是Web客户端向Web服务器发送信息，这个信息由如下三部分组成：

      （1）请求行

      例如：GET www.cnblogs.com HTTP/1.1
      请求行写法是固定的，由三部分组成，

      第一部分是请求方法：

      除了常见的只有Get和Post方法，实际上HTTP请求方法还有很多，比如： PUT方法，DELETE方法，HEAD方法，CONNECT方法，TRACE方法

      第二部分是请求网址，

      第三部分是HTTP版本。
      （2）HTTP头

      HTTP头在HTTP请求可以是3种HTTP头：1. 请求头(request header)  2. 普通头(general header)  3. 实体头(entity header)

      通常来说，由于Get请求往往不包含内容实体，因此也不会有实体头。
      （3）内容

      只在POST请求中存在，因为GET请求并不包含任何实体
      4.服务器端HTTP响应(HTTP Response)请求
      当Web服务器收到HTTP请求后，会根据请求的信息做某些处理(这些处理可能仅仅是静态的返回页，或是包含Asp.net, PHP, Jsp等语言进行处理后返回)，相应的返回一个HTTP响应。HTTP响应在结构上很类似于HTTP请求，也是由三部分组成，分别为:

      1.状态行

      例如：HTTP/1.1 200 OK

      第一部分是HTTP版本

      第二部分是响应状态码
      第三部分是状态码的描述

          信息类 (100-199)
          响应成功 (200-299)
          重定向类 (300-399)
          客户端错误类 (400-499)
          服务端错误类 (500-599)
      详细HTTP 状态消息请看:HTTP 状态消息
      
      常见状态代码、状态描述的说明如下。
      200 OK：客户端请求成功。
      400 Bad Request：客户端请求有语法错误，不能被服务器所理解。
      401 Unauthorized：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用。
      403 Forbidden：服务器收到请求，但是拒绝提供服务。
      404 Not Found：请求资源不存在，举个例子：输入了错误的URL。
      500 Internal Server Error：服务器发生不可预期的错误。
      503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能恢复正常，举个例子：HTTP/1.1 200 OK（CRLF）。

      2.HTTP头

      HTTP响应中包含的头包括：1. 响应头(response header) 2. 普通头(general header) 3. 实体头(entity header)。
      3.返回内容

      HTTP响应内容就是HTTP请求所请求的信息。这个信息可以是一个HTML，也可以是一个图片。响应的数据格式通过Content-Type字段来获得：Content-Type：image/png；或者我们熟悉的Content-Type：text/html
      下面是一些常见的Content-Type字段的值。

          text/plain
          text/html
          text/css
          image/jpeg
          image/png
          image/svg+xml
          audio/mp4
          video/mp4
          application/javascript
          application/pdf
          application/zip
          application/atom+xml

      5.浏览器解析html代码，并请求html代码中的资源
      了解持久连接

      有时候我们获取一个HTML页面，在对浏览器对HTML解析的过程中，如果发现额外的URL需要获取的内容，会再次发起HTTP请求去服务器获取，比如样式文件，图片。许多个HTTP请求，只依靠一个TCP连接就够了，这就是所谓的持久连接。也是所谓的一次HTTP请求完成。


### express
 1. cnpm install -g express   全局安装express 
     //跳过1直接安装4.0以上版本
  
 2. cnpm install -g express-generator  安装4.0之后的express
 3. express -V                检测express 版本号
 4. express -e blog && cd blog
         （ blog是安装的文件夹名）

5. npm install
       （安装express及依赖）

6. npm start
（这里需要注意 express 4.x 无法以 node app.js 为启动方式，而是用指令 npm start 作为启动）

 访问 http://localhost:3000/ 出现熟悉的Welcome to Express，证明安装成功。
---------------------------------------------------------------------------------------
项目创建成功之后，生成四个文件夹，

app.js 是主文件

packetage.json 是配置信息文件

bin是项目的启动文件，配置以什么方式启动项目，默认 npm start

public是项目的静态文件，放置js css img等文件

routes是项目的路由信息文件,控制地址路由

views是视图文件，放置模板文件ejs或jade,swig等（其实就相当于html形式文件啦~)

node_modules 是项目依赖的各种插件

express这样的MVC框架模式，是一个Web项目的基本构成。
-----------------------------------------------------------------------------------------
app.js 探究

补充：
```
全局对象
__dirname  表示当前执行脚本所在的目录。
—filename  表示当前执行脚本文件路径（绝对路径）

path 模块

var path = require("path");

// 格式化路径   注意'..' 和 '.'。
console.log(path.normalize('/test/test1//2slashes/1slash/tab/..'));
//   /test/test1/2slashes/1slash


// 连接路径
console.log(path.join('/test', 'test1', '2slashes/1slash', 'tab', '..'));
//    /test/test1/2slashes/1slash

// 转换为绝对路径
console.log(path.resolve('main.js'));
//   /web/com/1427176256_27423/main.js
```
