# HTTP

## 简述
HTTP全称是超文本传输协议，拆分来看就是“超文本”、“传输”、“协议”。
```aidl
1、协议的意思是双方提前协商好的规定、规范，这也就说明这个协议是要求最少两个人参与的
2、传输的意思是将数据 A => B，HTTP的模式就是A先向B发送请求，B收到请求之后，将响应内容传向B，
这样才算一次完整请求
3、超文本的解释是超越普通的文本格式，那就是图片、视频、HTML都属于超文本；
```

## 和https区别
https是http+ssl/tls的简写，http主要是明文传输，tls处于http下层，保证数据安全

## 几个版本的对比
- http 0.9
    - 只支持GET方法
    - 响应只支持返回html纯文本
    - 响应后直接关闭tcp连接
    
```http request
GET /index.html
``` 

- http 1.0
    - 增加了POST、HEAD方法
    - 增加了响应状态码
    - 响应内容丰富（图片、视频等）
    - 增加了cache
    - header增加Content-encoding字段进行内容压缩
    
```http request
GET /index.html HTTP/1.0
```

```http response
HTTP/1.0 200
Content-type: image/jpeg

图片转换为文本内容...
``` 
- http 1.1
    - 将访问同一服务器的多个资源请求由原来的多个tcp连接转变为一个tcp连接（管道）
    - 增加了PUT、PATCH、DELETE、OPTIONS等方法
    - header的Connection增加了keep-alive，减少tcp连接开销
    - header中增加了HOST，利于单机器多域名的需要
    - 请求或响应header中增加Transfer-Encoding: chunked分块传输，利于大文件下载
    
- http 2
    - 将请求中header、body部分完全以二进制的形式进行传输
    - 增加server push，减少网络交互
    - 压缩header内容，1.1中header是纯文本的
    - 增加ssl安全
    - tcp连接多路复用，是对1.1的改进，提高响应效率
    
- http 3
    - 发明新协议：QUIC

## 客户端访问url到服务器
## HTTP协议的请求报文和响应报文格式
## HTTP的状态码有哪些?
