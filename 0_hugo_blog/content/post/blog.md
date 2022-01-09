---
title: "解决访问github慢的问题"
date: 2021-12-05T22:33:28+08:00
draft: true
---


## 使用的系统
Arch Linux

## 参考文档

https://www.cnblogs.com/sochishun/p/14505669.html

## 操作步骤

### 1. 打开这个网站https://www.ipaddress.com/， 查询下面三个网址的IP地址
```
github.com
assets-cdn.github.com
github.global.ssl.fastly.net
```

### 2. 把下面的内容追加到/etc/hosts
```
140.82.114.4	github.com
199.232.69.194	github.global.ssl.fastly.net
185.199.108.153	asserts-cdn.github.com
185.199.109.153	asserts-cdn.github.com
185.199.110.153	asserts-cdn.github.com
185.199.111.153	asserts-cdn.github.com
```

### 3. 刷新DNS缓存
systemctl restart nscd

### 4. 发现使用上面获取的IP有时候还是慢，可以试试下面别人分享的IP
```
## GitHub Start
192.30.253.112 http://github.com
192.30.253.113 http://github.com
151.101.184.133 http://assets-cdn.github.com
151.101.185.194 http://github.global.ssl.fastly.net
192.30.253.112 http://github.com
192.30.253.113 http://github.com
192.30.253.118 http://gist.github.com
151.101.185.194 http://github.global.ssl.fastly.net
151.101.129.194 http://github.global.ssl.fastly.net
151.101.65.194 http://github.global.ssl.fastly.net
151.101.1.194 http://github.global.ssl.fastly.net
151.101.193.194 http://github.global.ssl.fastly.net
151.101.77.194 http://github.global.ssl.fastly.net
151.101.229.194 http://github.global.ssl.fastly.net
151.101.113.194 http://github.global.ssl.fastly.net
151.101.196.133 http://assets-cdn.github.com
151.101.24.133 http://assets-cdn.github.com
185.199.111.153 http://assets-cdn.github.com
185.199.110.153 http://assets-cdn.github.com
185.199.108.153 http://assets-cdn.github.com
185.199.109.153 http://assets-cdn.github.com
151.101.112.133 http://assets-cdn.github.com
151.101.112.133 http://avatars0.githubusercontent.com
151.101.112.133 http://avatars1.githubusercontent.com
151.101.184.133 http://avatars2.githubusercontent.com
151.101.12.133 http://avatars3.githubusercontent.com
151.101.12.133 http://avatars4.githubusercontent.com
151.101.184.133 http://avatars5.githubusercontent.com
151.101.184.133 http://avatars6.githubusercontent.com
151.101.184.133 http://avatars7.githubusercontent.com
151.101.12.133 http://avatars8.githubusercontent.com
151.101.184.133 http://raw.githubusercontent.com
151.101.112.133 http://gist.githubusercontent.com
151.101.184.133 http://cloud.githubusercontent.com
151.101.112.133 http://camo.githubusercontent.com
52.216.227.168 http://github-cloud.s3.amazonaws.com
192.30.253.112 http://github.com
185.199.108.153 http://assets-cdn.github.com
151.101.185.194 http://github.global.ssl.fastly.net
140.82.113.10 http://codeload.github.com

# 下载慢问题
219.76.4.4 http://github-cloud.s3.amazonaws.com

## GitHub End
```