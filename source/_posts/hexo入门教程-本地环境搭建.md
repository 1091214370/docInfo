---
title: hexo入门教程--本地环境搭建
date: 2018-07-19 13:31:47
tags: 入门教程
categories:
- hexo入门教程--本地环境搭建
---

## 简介
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

由于生成的是纯静态文件，所以你可以直接放在github上面，把github当做自己的服务器使用，比如[这里](https://1091214370.github.io/doc/)。当然也可以直接部署到服务器上面，比如[这里](http://47.104.188.184:8080/doc/)，算上本篇文章将有三篇文章详细的介绍hexo环境本地搭建以及部署到github和自己服务器的详细步骤。
## 本地环境搭建（window系统）
本地需要你有node环境，还需要git，自行准备。(以下所有npm安装命令均可使用cnpm执行)

### 安装

安装hexo：

`npm install -g hexo-cli`

创建一个文件夹hexoDemo，然后执行以下命令：

```
hexo init
npm install

```
至此你已经得到了包含如下结构目录的文件夹：

```
.
├── _config.yml // 配置文件
├── package.json  // 应用信息
├── scaffolds  // 模板
├── source // 静态文件存储位置
|   └── _posts
└── themes // 主题

```

这里简单介绍一下目录里文件和文件夹的功能：
- _config.yml 配置文件

网站的配置文件，需要在这个文件里面进行必要的配置，比如网站的一些资料和部署选项等等，具体参考 [这里](https://hexo.io/zh-cn/docs/configuration.html)


- package.json 网站信息文件

这个就没必要多介绍了。网站基本信息和必要的环境都在这里面。


- scaffolds

模版文件夹。新建文章时，Hexo 会根据 scaffold 来建立文件。模板内容会在新建md文件时自动加在头部，存放文件的一些信息。具体参考[这里](https://hexo.io/zh-cn/docs/writing.html)

```
---
title: {{ title }}
date: {{ date }}
tags:
---

```


- source

资源文件夹是存放用户资源的地方。除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。

- themes

主题文件夹。Hexo 会根据主题来生成静态页面。具体参考[这里](https://hexo.io/zh-cn/docs/themes.html)。


### 开始使用

1. 写作 ` hexo new [layout] <title>`

新建一篇文章。如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

2. 生成静态文件 `hexo generate`

选项 | 描述
---|---
`-d, --deploy` | 文件生成后立即部署网站
`-w, --watch` | 监视文件变动

命令可简写为 `hexo g`

3. 启动服务 `hexo server`

启动服务器。默认情况下，访问网址为： http://localhost:4000/。


选项 | 描述
---|---
`-p, --port` | 重设端口
`-s, --static` | 仅使用静态文件
`-l, --log` | 启动日记记录，使用覆盖记录格式

4. 部署网站 `hexo deploy`

选项 | 描述
---|---
`-g, --generate` | 部署之前先生成静态文件

命令可简写为
```
hexo g
```

综合2、4两条：
`hexo d -g` 和 `hexo g -d`功能一样，都可以完成生成静态文件并完成部署。

更多指令请点击[这里](https://hexo.io/zh-cn/docs/commands.html)

