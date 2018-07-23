---
title: test
date: 2018-07-18 15:39:27
categories:
- 测试一级目录文档
---
# ftp成功 监听成功
##### 查看开发的端口 `netstat -anp`
##### 打开端口 `iptables -A INPUT -ptcp --dport  端口号-j ACCEPT`
##### 关闭端口 `iptables -A INPUT -p tcp --drop 端口号-j DROP``iptables -A OUTPUT -p tcp --dport 端口号-j DROP`
