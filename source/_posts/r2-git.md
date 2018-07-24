---
title: 部署到git服务器
date: 2018-07-23 15:25:27
categories:
- hexo入门教程
top: 3
---
首先纠正自己一个错误，之前说部署到github，其实全面的说法应该是部署到git服务器---包括github和自己搭建的git服务器。我们可以在服务器上面搭建一个自己的git服务，设置hook，当我们在本地完成push后，服务端自动将push的内容复制到网站服务器的预留的目录下，完成网站服务器的部署。

### 主角登场
安装 `hexo-deployer-git`

`npm install hexo-deployer-git --save`

修改配置：
```
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
  
```


参数 | 描述
---|---
repo | 库（Repository）地址
branch | 分支名称。如果您使用的是 GitHub 或 GitCafe 的话，程序会尝试自动检测。
message | 自定义提交信息 (默认为 Site updated: now('YYYY-MM-DD HH:mm:ss') )

在_config.yml里面添加配置，然后执行`hexo clear && hexo g -d` 便可以将编译后的静态文件提交到git服务器。

### 部署到github

以我个人配置为例：
```
 type: git
  repo: git@github.com:1091214370/doc.git
  branch: master

```

执行`hexo clean && hexo g -d`，系统会自动的将public文件夹里的内容提交到配置好的git仓库。

在github里面打开github page，即可访问。

github page打开方法，在项目的setting里。向下翻，找到github page一栏，Source选项下的按钮save一下，就会在上方多一个链接，点击链接即可查看。


### 部署服务器上面自己搭建的git

具体详细的步骤可以参考[这里](https://segmentfault.com/a/1190000009363890)。文章介绍的很详细，里面有个坑，注意看评论哦。

end