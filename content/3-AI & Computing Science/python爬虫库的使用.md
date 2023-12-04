---
title: "python爬虫库的使用"
tags:
- Python
- Coding
- Spider
---
# Urllib 库
>[!Tip]  Urllib 库是 Python 的爬虫库，内置四个模块：request、error、parse、robotparser
>- request：用它来发起请求
>- error：当我们在使用 request 模块遇到错了，就可以用它来进行异常处理
>- parse：用来解析我们的 URL 地址的，比如解析域名地址，URL 指定的目录等
>- robotparser：用来解析网站的 robot.txt

## request 模块
```
import urllib.request
urllib.request.urlopen('http://www.bing.com')
print(response.read().decode('utf.8'))
```
### request. urlopen
request 模块 的 urlopen 方法，可以传入的参数**主要**有 3 个
`urllib.request.``urlopen`(_url_, _data=None_, [_timeout_, ]_*)_
1. 第一个 **url** 就是我们请求的链接，比如我们刚刚就请求百度
2. 第二个参数 **data**，就是专门给我们 post 请求携带参数的。比如我们在登录的时候可以把用户名密码封装成 data 传过去。在这里的 data 的值我们可以用 byte 的类型传递
3. 第三个参数 **timeout** 就是设置请求超时时间，如果等好久服务器都没有给我们返回数据就停止请求
### request. Request
如果要欺骗服务器说我们是浏览器或者手机请求时，这个时候我们需要添加请求头信息，即：[[content/3-AI & Computing Science/python爬虫前，抓包#^359fd2|Request header]] 
Request 方法主要的参数
`urllib.request.``Request`(_url_, _data=None_, _headers={}_, _method=None_)
除了定义 url 和 data 之外还可以定义请求头信息，urlopen 默认是 Get 请求，当我们传入参数它就为 Post 请求了。
而 Request 可以让我们自己定义请求的方式，这样我们就可以使用 Request 来封装我们的请求信息
```
from urllib import request,parse 
```
网站用的是 https，我们可以使用 ssl 未经验证的上下文
```
import ssl
context = ssl._create_unverified_context()
```
定义请求 url 和 header
```
url = 'https://biihu.cc//account/ajax/login_process/'  
headers = {  
    #假装自己是浏览器  
    'User-Agent':' Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36',  
}
```
定义请求参数
```
dict = {  
    'return_url':'https://biihu.cc/',  
    'user_name':'xiaoshuaib@gmail.com',  
    'password':'123456789',  
    '_post_type':'ajax',  
}
```
