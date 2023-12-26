---
title: "python爬虫前，抓包"
tags:
- Python
- Coding
- Spider
---
https://www.baidu.com/s?wd=%E8%8B%8D%E8%80%81%E5%B8%88&rsv_spt=1&rsv_iqid=0xad707ee600011b25&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=baiduhome_pg&rsv_enter=0&oq=%25E8%258B%258D%25E8%2580%2581%25E5%25B8%2588&rsv_t=5d8eqNDy4ZpyUOz7ByzyIMYfH5Jc7861dr4CFQaY3WCiDnOpBLob6Eouk23%2F3L%2BTD46O&rsv_sug3=15&rsv_pq=996e776f0000df06&rsv_sug4=19123
**Get 请求：** ？后面的内容就是 GET 请求的参数，这些参数以「键值对」的形式实现。GET 请求把请求参数都暴露在 URL 上

**Post 请求：** 而 POST 请求的参数放在 request body 里面，POST 请求方式还对密码参数加了密

**Request Header**：我们在做 HTTP 请求的时候除了提交一些参数之外，我们还有定义一些 HTTP 请求的头部信息。比如 Accept、Host、cookie、User-Agent 等等。这些参数也是我们在做爬虫要用到。通过这些信息，欺骗服务器，告诉它我们是正规请求
比如我们可以在代码里面设置 cookie 告诉服务器我们就是在这个浏览器请求的会话，User-Agent 告诉服务器我们是浏览器请求的 ^359fd2

**Response：** 404，200，301，502都是服务器的响应码，一般服务器返回 200 说明请求成功

**Response Header：** 响应头主要是告诉我们数据以什么样的形式展现，展示 cookie 的设置

