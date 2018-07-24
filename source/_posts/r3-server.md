---
title: 部署到自己服务器
date: 2018-07-23 15:26:26
categories:
- hexo入门教程
top: 4
---
我服务器环境是centos7+Apache，只需要将编译好的静态文件上传至Apache服务的根目录下，即算完成。我们可以借助ftp来实现。

### 主角登场

安装 `hexo-deployer-ftpsynct`

`npm install hexo-deployer-ftpsync --save`

修改配置：
```
deploy:
  type: ftpsync
  host: <host>
  user: <user>
  pass: <password>
  remote: [remote]
  port: [port]
  ignore: [ignore]
  connections: [connections]
  verbose: [true|false]
  
```


参数 | 描述 | 默认值
---|--- | ---
host | 远程主机的地址 |
user | 使用者名称 |
pass | 密码 |
remote | 远程主机根目录 | /
port | 端口 | 21
ignore | 忽略的文件或目录 |
connections | 使用的连接数 | 1
verbose | 显示调试信息 | false

在_config.yml里面添加配置，然后执行`hexo clean && hexo g -d` 便可以将编译后的静态文件提交到git服务器。

### 部署到服务器

以我个人配置为例：
```
  type: ftpsync
  host: 47.104.188.184
  user: userName
  pass: ***********
  remote: /home/ftpUpload/doc
  port: 21
  ignore: 
  connections: 
  verbose: false

```

执行`hexo clear && hexo g -d`，系统会自动的将public文件夹里的内容提交到配置好目录。

> FTP部署可能出现的问题：
您可能需要预先通过其他方式将所有文件上传到远程主机中。否则初次使用ftpsync插件就可能出现报错。另外，由于FTP协议的特征，它每传送一个文件就需要一次握手，相对速度较慢。

我使用的是阿里云服务器，需要安装ftp，如果你也需要，请点击[这里](https://blog.csdn.net/Han_Wen2015/article/details/76794842)。

我需要开放21端口：
`iptables -A INPUT -ptcp --dport 21 -j ACCEPT`，如果你不确认是否一打开21端口，可以通过` netstat -anp`查看。

**值得注意的一个地方：配置文件里面的host只需要填写ip，不需要携带协议名称。**刚开始，一直提交不成功，知道吧协议名称去掉，呜呜呜。。。
