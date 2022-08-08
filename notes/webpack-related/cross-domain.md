# Basic

值得注意的是，发送ajax请求的是你的浏览器，所谓User Agent，而【跨域】的限制仅仅在浏览器和服务器之间。我们不能强制远程服务器都像例子中那样允许【跨域】请求，所以我们能做的就是不要使用浏览器发送请求。所以在前端开发中，一种常见的规避跨域的方法就是：

把ajax请求发送到你的本地开发服务器，然后本地开发服务器再把ajax请求转发到远端去，从网络拓扑上看本地服务器起着【反向代理】的作用。本地服务器和远端服务器是【服务器和服务器间的通信】，就不存在跨域问题了。

配置代理只需要在配置文件config/config.js中与routes同级处增加proxy字段，代码如下：
```
proxy:{
        '/dev':{
            target:'https://08ad1pao69.execute-api.us-east-1.amazonaws.com',',
            changeOrigin:true,
        },
},
```
配置的含义是：去往本地服务器localhost:8080的ajax调用中，如果是以/dev开头的，那么就转发到远端的https://08ad1pao69.execute-api.us-east-1.amazonaws.com',服务器中，/dev也会保留在转发地址中。  

参考链接：[在model中请求服务端数据](https://www.yuque.com/ant-design/course/ig6mzb)