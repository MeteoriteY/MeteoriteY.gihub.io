title: Hello Hexo
date: 2015-01-03

categories:
- 软件笔记
tags:
- Hexo
- GitHub
- 博客
- 建站
toc: true
---
本博客使用 [Hexo](http://hexo.io/) 强力驱动! 这是我的第一篇博客。同时也是我对 hexo 使用的笔记。
选择 hexo 的原因主要是想用静态 Blog 来学习一下 GitHub 的使用，也能多学习一些 css 和 html 知识。
还有一个好处，就是可以熟悉 Markdown 的使用！<ruby><rp>(</rp><span class="heimu"title=" 你知道的太多了 "> 以及提升逼格 </span><rp>)</rp></ruby>
感谢 [Litten](http://litten.github.io/) 提供的 [yilia](https://github.com/litten/hexo-theme-yilia) 主题，我挺喜欢这种简约风格的，现在所使用的主题略有修改。

<!-- more -->

---

## HEXO + GitHub Page = Static Blog

> 为什么选择 GitHub Pages
1、GitHub Pages 有免费的代码托管空间，资料自己管理，保存可靠；
2、学着用 GitHub，享受 GitHub 的便利，上面有很多大牛，眼界会开阔很多；
3、顺便理解 GitHub 工作原理，最好的团队协作流程；
4、GitHub 建立私有仓库才会收费，所以会有很多开源代码。

>GitHub Pages 是什么
应用 GitHub Pages 创建属于自己的个人博客，GitHub 将提供免费的空间。
免费空间最大不能超过仓库上限 1G，同时也不建议添加大于 100M 的单个文件到仓库中。
GitHub 提供的域名（用户名 + github+io）, 在 Repository name 对应处填写资源名，其需要使用自己的用户名，每个用户名下面只能建立一个，并且资源命名必须符合这样的规则 username/username.github.io，之后勾选下面的”Initialize this repository with a README” 。

>hexo 出自何人
hexo 出自台湾大学生 tommy351 之手，是一个基于 Node.js 的静态博客程序，其编译上百篇文字只需要几秒。hexo 生成的静态网页可以直接放到 GitHub Pages，BAE，SAE 等平台上。


### 安装 Hexo
在安装前，检查电脑中是否已安装下列应用程序：（以下地址仅针对 Windows）
Node.js ：[下载](http://nodejs.org/)    
Git ：[下载](https://git-scm.com/download/win) （PS: 这步可以跳过，因为后面会使用 [GitHub Windows](https://github-windows.s3.amazonaws.com/GitHubSetup.exe)，其安装时自带了 git）

如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。
```bash
$ npm install -g hexo-cli
```

### 部署 Hexo
安装 Hexo 完成后，需要先创建一个文件夹 <folder>，文件目录随意（最好是英文路径），再执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
```bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建完成后，指定文件夹的目录如下：
```bash
.
├── _config.yml #网站的 配置 信息，您可以在此配置大部分的参数。
├── package.json #应用程序的信息。EJS, Stylus 和 Markdown renderer 已默认安装，您可以自由移除。
├── scaffolds #模版文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。
├── source #资源文件夹是存放用户资源的地方。
|   ├── _drafts #除 _posts 文件夹之外，开头命名为 _ (下划线) 的文件 / 文件夹和隐藏的文件将会被忽略。
|   └── _posts
└── themes #主题 文件夹。Hexo 会根据主题来生成静态页面。
```

接下来需要为 Hexo 安装一些插件：    
** 注意：下面的 hexo 命令需要在初始化 hexo 时的文件夹中执行，注意切换地址。**
```bash
npm install hexo-generator-index --save #首页生成插件
npm install hexo-generator-archive --save #归档页生成插件
npm install hexo-generator-category --save #分类页生成插件
npm install hexo-generator-tag --save #标签页生成插件
npm install hexo-server --save #hexo 本地服务器插件
npm install hexo-deployer-git --save #git 部署插件
npm install hexo-deployer-heroku --save #heroku 部署插件（选装）
npm install hexo-deployer-rsync --save #rsync 部署插件（选装）
npm install hexo-deployer-openshift --save #openshift 部署插件（选装）
npm install hexo-renderer-marked --save #markdown 语法渲染插件
npm install hexo-renderer-stylus --save #Stylus 渲染插件
npm install hexo-generator-feed --save #feed 生成插件
npm install hexo-generator-sitemap --save #sitemap 生成插件
npm install hexo-git-backup --save #使用 github 备份博客
npm install hexo-renderer-ejs --save #ejs 渲染插件
npm install hexo-tag-bilibili --save #在文章中嵌入 bilibili 视频

```
更多详细信息可以访问 [插件](https://hexo.io/plugins/) 页面查看相关内容。

执行下面命令成功后，即可在浏览器中打开 http://localhost:4000 来查看效果。
```bash
$ hexo server
```

### 同步静态网页到 GitHub

1. 需要一个 [GitHub](https://github.com/) 的账号。<ruby><rp>(</rp><span class="heimu"title=" 你知道的太多了 "> 全世界最大同性交友网站客官不来一发吗: D</span><rp>)</rp></ruby>
2. 在主页找到创建仓库按钮 `New repository`，name 必须和自己的用户名一致，即 `meteoritey.github.io`。而这个地址也是将来的 Blog 地址。
3. 下载 [GitHub Windows](https://github-windows.s3.amazonaws.com/GitHubSetup.exe) 并双击安装。
4. 打开 GitHub Windows 后，在其右上角设置按钮中修改一个适合的 `Clone Path` 和习惯的 shell。
5. 运行桌面上的 `Git Shell`。
6. 使用 `cd` 命令切换到上面初始化后的 hexo 文件夹中。
7. 使用文本编辑器如 Atom，来编辑文件夹中的 `_config.yml`：
```bash
deploy:
  type: git
  repo: <repository url> #库（Repository）地址。例如：https://github.com/MeteoriteY/MeteoriteY.github.io
  branch: [branch] #分支名称。程序会尝试自动检测。例如: master
  message: [message] #自定义提交信息 (默认为 Site updated: {{ now("YYYY-MM-DD HH:mm:ss")}})。非必需项可省略。
```
8. 运行 `hexo g` 生成静态文件，这些文件都会保存在 `Public` 文件夹中。
9. 使用命令 `hexo s` 后，在浏览器中登陆 http://localhost:4000 查看新生成的网页。
10. 如果效果满意，可以使用命令 `hexo d` 一键部署到 GitHub 仓库。
11. 稍等一会儿即可访问 http://meteoritey.github.io


## HEXO 的基本操作

### 创建一篇新文章

``` bash
$ hexo new "My New Post" #创建一篇新文章，引号内为标题
```

More info: [Writing](http://hexo.io/docs/writing.html)

---
### 用本地服务器跑 hexo

启用 hexo 服务器，可登录 http://localhost:4000 查看博客最新修改效果。

``` bash
$ hexo server  
$ hexo s #命令简写
```

More info: [Server](http://hexo.io/docs/server.html)


### 生成静态文件
在配置完博客或者发布文章后需要进行生成静态文件
``` bash
$ hexo generate
$ hexo g #命令简写，每次改动后都需要生成一次。
```

More info: [Generating](http://hexo.io/docs/generating.html)


### 部署静态文件到远程站点

``` bash
$ hexo deploy
$ hexo d #命令简写
```

More info: [Deployment](http://hexo.io/docs/deployment.html)

### 一键生成静态文件并部署到远程站点
``` bash
$ hexo g -d

```

### 清除 public 文件夹和数据库
```bash
$ hexo clean #改动没效果时可先执行此命令，再生成静态文件。
```

## 参考资料
1. [Hexo 官方文档](https://hexo.io/zh-cn/docs/)
2. luuman 的 [使用 GitHub 搭建 Hexo 博客](http://luuman.github.io/2015/12/21/GitHub+Hexo/)
3. wsgzao 的 [使用 GitHub 和 Hexo 搭建免费静态 Blog](http://wsgzao.github.io/post/hexo-guide/# 注册设置 GitHub)
4. [仓库空间说明](https://help.github.com/articles/what-is-my-disk-quota/)
5. [主题选择](https://hexo.io/themes/)