---
 title: Hexo+github 搭建博客 (超级详细版，精细入微)
 date: 2021-1-31
---





# 前言

你了解 [Hexo](https://hexo.io/zh-cn/) 吗？ Hexo 是一个静态博客框架，基于 Node.js，将 Markdown 文章通过渲染引擎，生成一个静态网页，再结合 Git 命令（ssh），Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

几个月前偶然间了解到了 Hexo 这个静态博客网站，很适合那些喜欢写作的朋友们，最重要的是它是免费的，里面有许多的博客主题模板，这些主题都是一些很牛的大佬们开发的，而且设计的主题都很棒，让我很心动，心动不如行动，于是开始整理搭建属于自己的博客。直到今天，这中间经历了许多的坎坷荆棘，我将我的博客搭建的流程分享出来，能为那些博客小石榴们提供一些帮助吧，如果有错的话，请给我留言，我会及时修改，废话不多说，直接上教程。

> **如果下面的教程有错误之处，请在评论区留言，收到后，我会尽快修改，谢谢支持！**

# 一、博客环境搭建

> 本文系统环境信息：Win10 专业版，64 位（10.0 版本 18362）
>
> Node.js：12.13.0 Git：2.24.0
>
> 修改配置文件要用到的软件（可选）：
>
> 1. [Visual Studio Code](https://code.visualstudio.com/)（适合有开发基础的程序员，非常好用）
> 2. Sublime Text3，可免费使用，[百度网盘](https://pan.baidu.com/s/1uKA-aBHm_CsmJI5GolrV1Q)（提取码：mh0y）
> 3. [NodePad++](https://notepad-plus-plus.org/downloads/) 7.8.1（最新的，也可以在官网选择其他版本）

## 1. 下载 Git 和 Node.js

### 1.1 Node.js 的安装与配置

首先去 [Node.js 官网](https://nodejs.org/en/download/) 下载 node.js 的安装程序，根据你电脑系统的配置信息，下载对应的安装程序，然后开始进行下面的步骤。

[![Node.js下载以及版本的选择](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/nodejs-0.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/nodejs-0.png)

Node.js 下载以及版本的选择



下载好与电脑系统对应的安装程序后，开始安装流程：

1. 打开下载好的 Node.js 安装程序，点击 Next，进行下一步的安装；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-1.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-1.png)

img



1. 将”I accept the terms in the License Agreement” 前面的复选框勾选，同意安装协议，再点击 Next，进行下一步操作；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-2.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-2.png)

img



1. 选择 Node.js 安装程序的安装位置，在这里我以”C:\Program Files\nodejs” 为例，点击 Next，进入下一步操作；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-3.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-3.png)

img



1. 选择安装的模块和功能，这里全部安装，并添加到系统环境变量 ，继续点击 Next，进入下一步操作；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-4.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-4.png)

img



1. 这一步可以跳过，这个选项的意思是安装一些编译本地模块的工具，比如 python，C/C++ 等，点击 Next，进入下一步；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-5.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-5.png)

img



1. 点击”Install”，等待 Node.js 安装完成；

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-6.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-6.png)

img



1. 当看到下图所显示的情况，Node.js 就成功安装完毕。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-7.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-7.png)

img



1. 验证安装，并测试 Node.js 是否加入环境变量，当出现如下图的情况，Node.js 安装大功告成。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-8.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-8.png)

img



如果执行 `node -v` 报错的话，那么手动将 Node.js 的安装路径添加到环境变量中，右击点击我的电脑 -> 属性 -> 高级系统设置 -> 环境变量，在系统变量下找到名为 path 的变量名，如下图：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117191107.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117191107.png)

img



选中 path，或者双击，然后将你 node.js 的安装路径放在 path 变量值的最后面，如果添加之前 path 值最后有 英文的分号，则直接将路径添加进去即可，如果没有，先添加分号，然后点击保存，回到桌面，打开 cmd（Win+R），执行 `node -v`，看是否成功。

1. 设置 npm 的镜像源：

```
# 查看npm的配置
npm config list
# 默认源
npm config set registry https://registry.npmjs.org
# 临时改变镜像源
npm --registry=https://registry.npm.taobao.org
# 永久设置为淘宝镜像源
npm config set registry https://registry.npm.taobao.org
# 另一种方式，编辑 ~/.npmrc 加入下面内容
registry = https://registry.npm.taobao.org
```

1. 设置 npm 的内置路径 ——> 全局模块路径和缓存路径（*可选*）

如果不改变内置路径也可，除非你的 C 盘空间足够 bigger，这一步可以略过，不改变的话，它的路径在：

> 此处参考：[jyjin 的 node 环境变量配置，npm 环境变量配置](https://blog.csdn.net/jianleking/article/details/79130667)

- npm 包全局目录：

```
C:/Users/[username]/AppData/Roaming/npm/node_modules
```

- npm 包全局命令目录：

```
C:/Users/[username]/AppData/Roaming/npm
```

- npm 实际去找全局命令的目录：`C:/Users/[username]/.npmrc` 文件内容的 `prefix` 值
- npm 包全局 cache 目录：`C:/Users/[username]/.npmrc` 文件内容的 `cache` 值

首先在你 Node.js 的安装位置，新建两个文件夹，`node_global` 和 `node_cache`，我的路径是：

```
C:\Program Files\nodejs\node_global
C:\Program Files\nodejs\node_cache
```

然后分别执行的命令就是：

```
npm config set prefix "C:\Program Files\nodejs\node_global"
npm config set cache "C:\Program Files\nodejs\node_cache"
```

然后在配置环境变量，右击我的电脑 -> 属性 -> 高级系统设置 -> 环境变量同样的位置，在用户变量的地方，找到 path 变量进行修改，修改值如下图：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-11.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-11.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-12.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/node-12.png)

img



然后就大功告成了，Node.js 就安装完毕了，下面开始 Git 安装。👇👇👇

### 1.2 Git 的安装与配置

首先就是去 [Git 官网](https://git-scm.com/)下载 Git，根据你电脑系统的配置信息，下载对应的安装程序，然后开始进行下面的步骤。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117193737.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117193737.png)

img



1. 下载好 Git 的安装包，开始安装，打开安装包，出现如图的界面，点击 Next：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-1.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-1.png)

img



1. 选择你要安装的位置，我以 C 盘为例，路径为图中所示，安装到其他位置的话，点击 Browse，选择你要安装的位置，然后点击 Next，进入下一步：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-2.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-2.png)

img



1. 选择你是否创建桌面快捷放方式，其他默认即可，点击 Next，进入下一步：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-3.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-3.png)

img



1. 是否将 Git 快捷方式的目录加入开是菜单栏

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-4.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-4.png)

img



1. 这个是选择文本编辑器的方式，默认是 Vim，也可以选择其他的方式，自主选择，在这里我选择的 Vim 默认方式。选择好文本编辑器的方式后，点击 Next，进入下一个流程：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-5.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-5.png)

img



1. 选择安装 Git 时对环境变量 PATH 的影响，第一种影响较小，第三种会影响到 Windows 的自带工具，默认勾选中间项，建议不要修改，直接点击 “Next” 继续安装：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-6.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-6.png)

img



1. 选择 Git 在使用 HTTPS 时使用的库，若无特殊需求，可保持默认选项，点击 “Next” 继续安装：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-7.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-7.png)

img



1. 选择提交与拉取记录时，对换行符的处理方式，若无特殊需要，默认选择即可，点击 “Next” 继续安装：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-8.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-8.png)

img



1. 选择模拟终端软件（即命令行窗口软件），若无特殊需要，可默认选择，点击 “Next” 继续安装：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-9.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-9.png)

img



1. 最新功能的询问，若不想尝试尚未保证稳定性的新功能，默认不勾选，点击 “Install” 即可完成安装：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-10.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-10.png)

img



1. 安装完成

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-11.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-11.png)

img



1. 回到桌面，点击鼠标右键，会出现两个选项 `Git GUI Here` 和 `Git Bash Here`，在打开 Cmd (Win+R)，分别输入 `git` 和 `git --version`，如果出现如下图的情况，即安装成功！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-12.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-12.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-13.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/git-13.png)

img



# 二、Github 注册以及 Github Pages 创建

1. 打开 Github [官网首页](https://github.com/)，点击右上角的 **Sign Up** ，然后在出现的页面上填写你的相关信息，进行注册：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117203432.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117203432.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117204639.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117204639.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117204955.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117204955.png)

img



验证完成后，点击 Next：Select a plan，会出现如上图的验证界面，同理，只需要将其中的动物调整为正向显示即可。接着会出现下图的界面，选择 Free，下方的两个选项可选可不选，点击 **Continue** 继续：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117211431.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117211431.png)

img



这时 Github 会给你发一封邮件，验证一下即可，验证过后才可以创建库。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117212721.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117212721.png)

img



验证完成后，开始创建库，如下图所示，仓库名创建格式必须为：`<用户名>.github.io`，`Description` 为描述仓库，自定义写，填写必要的描述，也可不填。勾选 `Initialize this repository with a README` 点击 `Creat repository` 进行创建。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117212538.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117212538.png)

img



然后就会出现如图所示的界面，即仓库创建成功！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117213321.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117213321.png)

img



我们来测试一下，点击 `Create new file`，出现如下界面，然后命名文件名为 `index.html`，在填写如图的内容，再点击 `Commit new file`，即创建成功，然后打开一个新的网页，输入网址 `https://<你的用户名>.github.io`，即可以看见一个新的网页，其中的内容就是你写的内容。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117214029.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117214029.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117213957.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117213957.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117214450.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117214450.png)

img



至此，Github 的注册以及 Github Pages 已经创建完成了。

# 三、配置 Git 用户名和邮箱

在桌面点击鼠标右键，点击 `Git Bash Here`，会出现一个界面如下图所示：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117215118.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117215118.png)

img



然后分别输入下面的两个命令，并回车：

```
git config --global user.name "此处填写你注册时的用户名"
git config --global user.email "此处填写你注册时的邮箱"
# 一般只要不报错，可以跳过下面寻找.gitconfig文件
```

然后找到`.gitconfig` 文件，文件存放位置在 `C:/Users/[username]/.gitconfig`（未找到的话，请开启显示隐藏文件的功能），用编辑器打开，看到如下图所示的内容，即配置成功！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117220016.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117220016.png)

img



# 四、本地安装 hexo 静态博客框架以及发布到 Github Pages

1. 首先选择一个磁盘作为你博客文件的存放位置，然后新建一个文件夹，比如名为 blogtest 的文件夹，创建完后，先不要点进去，在此处点击鼠标右键，选择 `Git Bash Here`，然后依次输入如下命令，：

```
# hexo框架的安装
npm install -g hexo-cli
# 等上一个命令完成后，在输入下面的命令
hexo init <新建文件夹的名称>  #初始化文件夹
cd <新建文件夹的名称>
npm install  # 安装博客所需要的依赖文件
```

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221129.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221129.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221144.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221144.png)

img



等待运行完成，此时文件夹中多了许多文件。 **注意**：**后续的命令均需要在站点目录下（即文件夹内）使用 Git Bash 运行。** 此时 Hexo 框架的本地搭建已经完成了。我们来运行一下看看，命令行依次输入以下命令 :

```
hexo g
hexo s
```

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221157.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221157.png)

img



浏览器中打开 [http://localhost:4000 或者 127.0.0.1:4000，可以看到一个网页，说明 Hexo 博客已经成功在本地运行。](http://xn--localhost:4000127-kd18a6585a.0.0.1:4000，可以看到一个网页，说明Hexo博客已经成功在本地运行。/)

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221206.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117221206.png)

img



## 1. 本地博客发布到 Github Pages

之前的步骤中，我们已经完成了对 Github 账户的注册以及 Github Pages 的创建，接下来是将本地博客发布至 Github Pages。

1. 首先需要安装发布的插件，在站点目录下执行下面的命令，也就是创建的博客目录下：

```
npm install hexo-deployer-git --save
```

1. 紧接着，将本地目录与 GitHub 关联起来，输入下面的命令行：

```
ssh-keygen -t rsa -C "你的邮箱地址"
```

输入后一直回车，然后在 `C:/Users/[username]` 目录下找到名为`.ssh` 的文件夹， 文件夹内会有两个文件，一个 `id_rsa.pub` 一个 `id_rsa`，用文本编辑器打开 `id_rsa.pub`，复制里面的的内容。 然后打开 Github，点击右上角的头像 **Settings** 选择 **SSH and GPG keys**

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117222746.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117222746.png)

img



点击 **New SSH key** 将之前复制的内容粘帖到 Key 的框中。 上面的 **Title** 可以随意，点击 **Add SSH key** 完成添加。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117223049.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117223049.png)

img



然后回到 Git 的命令行界面，测试一下是否与 GitHub 连接成功。输入下面的命令行：

```
ssh -T git@github.com
```

点击回车，然后会出现一个询问内容，输入 `yes`，回车，会出现一段内容，`Hi ! You've successfully authenticated, but GitHub doesnot provide shell access.`。 说明连接成功。此处这个 `` 应该是你 Github 的用户名。

1. 进入博客站点目录，用文本编辑器打开`_config.yml`，这个`_config.yml` 是博客的配置文件，在以后的博客修改，如个性化修改，博客 SEO 优化等都会使用到，修改如下图的几个地方：

```
title: 你的博客名
subtitle: 博客的副标题，有些主题支持
description: 博客描述
keywords: 博客关键词
author: 作者，在文章中显示
language: 博客语言语种   
timezone: 时区
```

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117224138.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117224138.png)

img



滑到文件最底部，有一个 deploy，在 deploy 下面添加一个 repo 项 ，一个 branch 项。填入如下代码，并如下图所示：

```
type: git
repo: git@github.com:Github用户名/github用户名.github.io.git  
//也可使用https地址，如：https://github.com/Github用户名/Github用户名.github.io.git            
branch: master
```

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117224151.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191117224151.png)

img



1. 最后就是生成页面，并发布至 Github Pages，执行如下命令：

```
# Hexo会根据配置文件渲染出一套静态页面
hexo g
# 将上一步渲染出的一系列文件上传至至Github Pages
hexo d
# 也可以直接输入此命令，直接完成渲染和上传
hexo g -d
```

上传完成后，在浏览器中打开 **https://<用户名>.github.io**，查看上传的网页。如果页面变成了之前本地调试时的样子，说明上传以及完成了。没变的话查看一下上传时命令行窗口的信息有没有错误信息，没有的话清除一下浏览器缓存试试。

# 五、hexo 博客主题安装以及一些个性化修改

> **转自：**[🇺🇸English Document](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README.md) | [演示示例](https://blinkfox.github.io/) | QQ 交流群 1（已满）: [`926552981`](https://jq.qq.com/?_wv=1027&k=5zMDYHT) | QQ 交流群 2（推荐）: [`971887688`](https://jq.qq.com/?_wv=1027&k=53q2Ayp)
>
> 这是一个采用 `Material Design` 和响应式设计的 Hexo 博客主题。

## 主题特性

- 简单漂亮，文章内容美观易读
- [Material Design](https://material.io/) 设计
- 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- 首页轮播文章及每天动态切换 `Banner` 图片
- 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- 时间轴式的归档页
- **词云**的标签页和**雷达图**的分类页
- 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- 可自定义的数据的友情链接页面
- 支持文章置顶和文章打赏
- 支持 `MathJax`
- `TOC` 目录
- 可设置复制文章内容时追加版权信息
- 可设置阅读文章时做密码验证
- [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Gitalk`）
- 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- 支持在首页的音乐播放和视频播放功能
- 支持 `emoji` 表情，用 `markdown emoji` 语法书写直接生成对应的能**跳跃**的表情。
- 支持 [DaoVoice](http://www.daovoice.io/)、[Tidio](https://www.tidio.com/) 在线聊天功能。

## 1. 主题下载与安装

点击 [传送门](https://github.com/blinkfox/hexo-theme-matery) 下载 `master` 分支的最新稳定版的代码，解压缩后，将 `hexo-theme-matery` 的文件夹复制到你 Hexo 的 `themes` 文件夹中即可。

当然你也可以在你的站点目录文件夹下使用 `git clone` 命令来下载：直接在站点根目录下执行下面的命令，即可进行主题的下载，主题有两个版本，稳定版本和最新版本 (不定期更新优化)，自主选择版本。

```
git clone https://github.com/blinkfox/hexo-theme-matery themes/matery     # 稳定版
git clone -b develop https://github.com/blinkfox/hexo-theme-matery themes/matery   #最新版(不定期进行优化更新)
```

如果主题下载速度比较慢的话，可以从我的码云仓库进行下载，我的码云仓库地址：[传送门](https://gitee.com/yafine66/hexo-theme-matery)

注意：在下载主题仓库之前，请先比对仓库更新时间是否与原作者仓库时间一致，如果一致，请执行下面的命令，如果不一致，请联系我进行仓库更新，当然你也可以自己进行相关的更新操作，自主选择！

```
git clone https://gitee.com/yafine66/hexo-theme-matery themes/matery     # 稳定版
git clone -b develop https://gitee.com/yafine66/hexo-theme-matery themes/matery   #最新版(不定期进行优化更新)
```

## 2. 主题配置

### 2.1 切换主题

> **注意：**首先需要明白什么是站点配置文件，什么是主题配置文件，站点配置文件就是根目录下的配置文件，比如我的博客文件在 `F:\blog` 下，那么站点配置文件就是 `F:\blog\_config.yml`，主题配置文件就是 `F:\blog\themes\matery\_config.yml`。
>
> 另外注意，配置文件中的标点符号不要出现中文格式的标点符号，不然运行会出错。

主题下载完成后，将站点配置文件中的 `theme` 值修改为你下载主题的文件名，此处为 `matery`，那么值就修改为 `theme: matery`。

一些站点配置文件的其他地方的修改：

- 语言选择：如果为中文用户，则在 `language:` 后添加值 `zh-CN`，如果不修改，默认为英语；
- 网址修改：`url:` 的值为你的网址名，如 `http://xxxx.github.io`，如果有域名，则修改为你的域名即可，至于有关域名的修改解析，后面我会说到，这里先不说了。
- 站点配置文件有个 `per_page属性`，建议修改为 6 的倍数，这样网站在适应设备时，有较好的显示效果。

### 2.2 新建标签 tags 页面

`tags` 页是用来展示所有标签的页面，如果在你的博客 `source` 目录下还没有 `tags/index.md` 文件，那么你就需要新建一个，命令如下：

```
hexo new page "tags"
```

编辑你刚刚新建的页面文件 `/source/tags/index.md`，至少需要以下内容：

```
---
title: tags
date: 2018-09-30 18:23:38
type: "tags"
layout: "tags"
---
```

### 2.3 新建分类 categories 页面

`categories` 页是用来展示所有分类的页面，如果在你的博客 `source` 目录下还没有 `categories/index.md` 文件，那么你就需要新建一个，命令如下：

```
hexo new page "categories"
```

编辑你刚刚新建的页面文件 `/source/categories/index.md`，至少需要以下内容：

```
---
title: categories
date: 2018-09-30 17:25:30
type: "categories"
layout: "categories"
---
```

### 2.4 新建关于我 about 页面

`about` 页是用来展示**关于我和我的博客**信息的页面，如果在你的博客 `source` 目录下还没有 `about/index.md` 文件，那么你就需要新建一个，命令如下：

```
hexo new page "about"
```

编辑你刚刚新建的页面文件 `/source/about/index.md`，至少需要以下内容：

```
---
title: about
date: 2018-09-30 17:25:30
type: "about"
layout: "about"
---
```

### 2.5 新建留言板 contact 页面 (可选)

`contact` 页是用来展示**留言板**信息的页面，如果在你的博客 `source` 目录下还没有 `contact/index.md` 文件，那么你就需要新建一个，命令如下：

```
hexo new page "contact"
```

编辑你刚刚新建的页面文件 `/source/contact/index.md`，至少需要以下内容：

```
---
title: contact
date: 2018-09-30 17:25:30
type: "contact"
layout: "contact"
---
```

> **注**：本留言板功能依赖于第三方评论系统，请**激活**你的评论系统才有效果。并且在主题的 `_config.yml` 文件中，第 `19` 至 `21` 行的 “**菜单**” 配置，取消关于留言板的注释即可。

### 2.6 新建友情链接 friends 页面 (可选)

`friends` 页是用来展示**友情链接**信息的页面，如果在你的博客 `source` 目录下还没有 `friends/index.md` 文件，那么你就需要新建一个，命令如下：

```
hexo new page "friends"
```

编辑你刚刚新建的页面文件 `/source/friends/index.md`，至少需要以下内容：

```
---
title: friends
date: 2018-12-12 21:25:30
type: "friends"
layout: "friends"
---
```

同时，在你的博客 `source` 目录下新建 `_data` 目录，在 `_data` 目录中新建 `friends.json` 文件，文件内容如下所示：

```
[{
    "avatar": "http://image.luokangyuan.com/1_qq_27922023.jpg",
    "name": "码酱",
    "introduction": "我不是大佬，只是在追寻大佬的脚步",
    "url": "http://luokangyuan.com/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/4027734.jpeg",
    "name": "闪烁之狐",
    "introduction": "编程界大佬，技术牛，人还特别好，不懂的都可以请教大佬",
    "url": "https://blinkfox.github.io/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/avatar.jpg",
    "name": "ja_rome",
    "introduction": "平凡的脚步也可以走出伟大的行程",
    "url": "https://me.csdn.net/jlh912008548",
    "title": "前去学习"
}]
```

### 2.7 菜单导航配置

#### 2.7.1. 配置基本菜单导航的名称、路径 url 和图标 icon.

1. 菜单导航名称可以是中文也可以是英文 (如：`Index` 或`主页`)
2. 图标 icon 可以在 [Font Awesome](https://fontawesome.com/icons) 中查找

```
menu:
  Index:
    url: /
    icon: fas fa-home
  Tags:
    url: /tags
    icon: fas fa-tags
  Categories:
    url: /categories
    icon: fas fa-bookmark
  Archives:
    url: /archives
    icon: fas fa-archive
  About:
    url: /about
    icon: fas fa-user-circle
  Friends:
    url: /friends
    icon: fas fa-address-book
```

#### 2.7.2. 二级菜单配置方法

如果你需要二级菜单则可以在原基本菜单导航的基础上如下操作

1. 在需要添加二级菜单的一级菜单下添加 `children` 关键字 (如:`About` 菜单下添加 `children`)
2. 在 `children` 下创建二级菜单的 名称 name, 路径 url 和图标 icon.
3. 注意每个二级菜单模块前要加 `-`.
4. 注意缩进格式

```
menu:
  Index:
    url: /
    icon: fas fa-home
  Tags:
    url: /tags
    icon: fas fa-tags
  Categories:
    url: /categories
    icon: fas fa-bookmark
  Archives:
    url: /archives
    icon: fas fa-archive
  About:
    url: /about
    icon: fas fa-user-circle-o
  Friends:
    url: /friends
    icon: fas fa-address-book
  Medias:
    icon: fas fa-list
    children:
      - name: Musics
        url: /musics
        icon: fas fa-music
      - name: Movies
        url: /movies
        icon: fas fa-film
      - name: Books
        url: /books
        icon: fas fa-book
      - name: Galleries
        url: /galleries
        icon: fas fa-image
```

### 2.8 添加 emoji 表情支持（可选的）

本主题新增了对 `emoji` 表情的支持，使用到了 [hexo-filter-github-emojis](https://npm.taobao.org/package/hexo-filter-github-emojis) 的 Hexo 插件来支持 `emoji` 表情的生成，把对应的 `markdown emoji` 语法（`::`, 例如：`:smile:`）转变成会跳跃的 `emoji` 表情，安装命令如下：

```
npm install hexo-filter-github-emojis --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```
githubEmojis:
  enable: true
  className: github-emoji
  inject: true
  styles:
  customEmojis:
```

执行 `hexo clean && hexo g` 重新生成博客文件，然后就可以在文章中对应位置看到你用 `emoji` 语法写的表情了。

### 2.9 代码高亮

由于 Hexo 自带的代码高亮主题显示不好看，所以主题中使用到了 [hexo-prism-plugin](https://github.com/ele828/hexo-prism-plugin) 的 Hexo 插件来做代码高亮，安装命令如下：

```
npm i -S hexo-prism-plugin
```

然后，修改 Hexo 根目录下 `_config.yml` 文件中 `highlight.enable` 的值为 `false`，并新增 `prism` 插件相关的配置，主要配置如下：

```
prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css:
```

### 2.10 搜索

本主题中还使用到了 [hexo-generator-search](https://github.com/wzpan/hexo-generator-search) 的 Hexo 插件来做内容搜索，安装命令如下：

```
npm install hexo-generator-search --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```
search:
  path: search.xml
  field: post
```

### 2.11 中文链接转拼音（可选的）

如果你的文章名称是中文的，那么 Hexo 默认生成的永久链接也会有中文，这样不利于 `SEO`，且 `gitment` 评论对中文链接也不支持。我们可以用 [hexo-permalink-pinyin](https://github.com/viko16/hexo-permalink-pinyin) Hexo 插件使在生成文章时生成中文拼音的永久链接。

安装命令如下：

```
npm i hexo-permalink-pinyin --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```
permalink_pinyin:
  enable: true
  separator: '-' # default: '-'
```

> **注**：除了此插件外，[hexo-abbrlink](https://github.com/rozbo/hexo-abbrlink) 插件也可以生成非中文的链接。

### 2.12 文章字数统计插件（可选的）

如果你想要在文章中显示文章字数、阅读时长信息，可以安装 [hexo-wordcount](https://github.com/willin/hexo-wordcount) 插件。

安装命令如下：

```
npm i --save hexo-wordcount
```

然后只需在本主题下的 `_config.yml` 文件中，激活以下配置项即可：

```
wordCount:
  enable: false # 将这个值设置为 true 即可.
  postWordCount: true
  min2read: true
  totalCount: true
```

### 2.13 添加 RSS 订阅支持（可选的）

本主题中还使用到了 [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed) 的 Hexo 插件来做 `RSS`，安装命令如下：

```
npm install hexo-generator-feed --save
```

在 Hexo 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
```

执行 `hexo clean && hexo g` 重新生成博客文件，然后在 `public` 文件夹中即可看到 `atom.xml` 文件，说明你已经安装成功了。

### 2.14 添加 [DaoVoice](http://www.daovoice.io/) 在线聊天功能（可选的）

前往 [DaoVoice](http://www.daovoice.io/) 官网注册并且获取 `app_id`，并将 `app_id` 填入主题的 `_config.yml` 文件中

### 2.15 添加 [Tidio](https://www.tidio.com/) 在线聊天功能（可选的）

前往 [Tidio](https://www.tidio.com/) 官网注册并且获取 `Public Key`，并将 `Public Key` 填入主题的 `_config.yml` 文件中。

### 2.16 修改页脚

页脚信息可能需要做定制化修改，而且它不便于做成配置信息，所以可能需要你自己去再修改和加工。修改的地方在主题文件的 `/layout/_partial/footer.ejs` 文件中，包括站点、使用的主题、访问量等。

### 2.17 修改社交链接

在主题的 `_config.yml` 文件中，默认支持 `QQ`、`GitHub` 和邮箱等的配置，你可以在主题文件的 `/layout/_partial/social-link.ejs` 文件中，新增、修改你需要的社交链接地址，增加链接可参考如下代码：

```
<% if (theme.socialLink.github) { %>
    <a href="<%= theme.socialLink.github %>" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
        <i class="fab fa-github"></i>
    </a>
<% } %>
```

其中，社交图标（如：`fa-github`）你可以在 [Font Awesome](https://fontawesome.com/icons) 中搜索找到。以下是常用社交图标的标识，供你参考：

- Facebook: `fab fa-facebook`
- Twitter: `fab fa-twitter`
- Google-plus: `fab fa-google-plus`
- Linkedin: `fab fa-linkedin`
- Tumblr: `fab fa-tumblr`
- Medium: `fab fa-medium`
- Slack: `fab fa-slack`
- Sina Weibo: `fab fa-weibo`
- Wechat: `fab fa-weixin`
- QQ: `fab fa-qq`
- Zhihu: `fab fa-zhihu`

> **注意**: 本主题中使用的 `Font Awesome` 版本为 `5.11.0`。

### 2.18 修改打赏的二维码图片

在主题文件的 `source/medias/reward` 文件中，你可以替换成你的的微信和支付宝的打赏二维码图片。

### 2.19 配置音乐播放器（可选的）

> 新版主题支持接入第三方音乐，如 QQ 音乐，网易云音乐，酷狗音乐等等

要支持音乐播放，在主题的 `_config.yml` 配置文件中激活 music 配置即可：

```
# 是否在首页显示音乐
music:
  enable: true
  title:            #非吸底模式有效
    enable: true
    show: 听听音乐
  server: netease   #require music platform: netease, tencent, kugou, xiami, baidu
  type: playlist    #require song, playlist, album, search, artist
  id: 503838841     #require song id / playlist id / album id / search keyword
  fixed: false      # 开启吸底模式
  autoplay: false   # 是否自动播放
  theme: '#42b983'
  loop: 'all'       # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'random'   # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto'   # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7       # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: true  # 列表默认折叠
```

> `server` 可选 `netease`（网易云音乐），`tencent`（QQ 音乐），`kugou`（酷狗音乐），`xiami`（虾米音乐），
>
> `baidu`（百度音乐）。
>
> `type` 可选 `song`（歌曲），`playlist`（歌单），`album`（专辑），`search`（搜索关键字），`artist`（歌手）
>
> `id` 获取示例：浏览器打开网易云音乐，点击我喜欢的音乐歌单，地址栏有一串数字，`playlist` 的 `id` 即为这串数字。

## 3. 文章 Front-matter 介绍

### Front-matter 选项详解

`Front-matter` 选项中的所有内容均为**非必填**的。但我仍然建议至少填写 `title` 和 `date` 的值。

| 配置选项      | 默认值                         | 描述                                                         |
| ------------- | ------------------------------ | ------------------------------------------------------------ |
| title         | `Markdown` 的文件标题          | 文章标题，强烈建议填写此选项                                 |
| date          | 文件创建时的日期时间           | 发布时间，强烈建议填写此选项，且最好保证全局唯一             |
| author        | 根 `_config.yml` 中的 `author` | 文章作者                                                     |
| img           | `featureImages` 中的某个值     | 文章特征图，推荐使用图床 (腾讯云、七牛云、又拍云等) 来做图片的路径。如: http://xxx.com/xxx.jpg |
| top           | `true`                         | 推荐文章（文章是否置顶），如果 `top` 值为 `true`，则会作为首页推荐文章 |
| cover         | `false`                        | `v1.0.2` 版本新增，表示该文章是否需要加入到首页轮播封面中    |
| coverImg      | 无                             | `v1.0.2` 版本新增，表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片 |
| password      | 无                             | 文章阅读密码，如果要对文章设置阅读验证密码的话，就可以设置 `password` 的值，该值必须是用 `SHA256` 加密后的密码，防止被他人识破。前提是在主题的 `config.yml` 中激活了 verifyPassword 选项 |
| toc           | `true`                         | 是否开启 TOC，可以针对某篇文章单独关闭 TOC 的功能。前提是在主题的 `config.yml` 中激活了 `toc` 选项 |
| mathjax       | `false`                        | 是否开启数学公式支持 ，本文章是否开启 `mathjax`，且需要在主题的 `_config.yml` 文件中也需要开启才行 |
| summary       | 无                             | 文章摘要，自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要 |
| categories    | 无                             | 文章分类，本主题的分类表示宏观上大的分类，只建议一篇文章一个分类 |
| tags          | 无                             | 文章标签，一篇文章可以多个标签                               |
| reprintPolicy | cc_by                          | 文章转载规则， 可以是 cc_by, cc_by_nd, cc_by_sa, cc_by_nc, cc_by_nc_nd, cc_by_nc_sa, cc0, noreprint 或 pay 中的一个 |

> **注意**:
>
> 1. 如果 `img` 属性不填写的话，文章特色图会根据文章标题的 `hashcode` 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图**各有特色**。
> 2. `date` 的值尽量保证每篇文章是唯一的，因为本主题中 `Gitalk` 和 `Gitment` 识别 `id` 是通过 `date` 的值来作为唯一标识的。
> 3. 如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 `_config.yml` 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：[开源中国在线工具](http://tool.oschina.net/encrypt?type=2)、[chahuo](http://encode.chahuo.com/)、[站长工具](http://tool.chinaz.com/tools/hash.aspx)。
> 4. 您可以在文章 md 文件的 front-matter 中指定 reprintPolicy 来给单个文章配置转载规则

以下为文章的 `Front-matter` 示例。

### 最简示例

```
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
---
```

### 最全示例

```
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
author: 赵奇
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories: Markdown
tags:
  - Typora
  - Markdown
---
```

## 4. 效果截图

> **最新版本进行了优化更新，效果图与最初的效果图有差别，下面的图不是最新版本的。**

[![首页](http://static.blinkfox.com/matery-20181202-1.png)](http://static.blinkfox.com/matery-20181202-1.png)

首页



[![首页推荐文章](http://static.blinkfox.com/matery-20181202-2.png)](http://static.blinkfox.com/matery-20181202-2.png)

首页推荐文章



[![首页文章列表](http://static.blinkfox.com/matery-20181202-3.png)](http://static.blinkfox.com/matery-20181202-3.png)

首页文章列表



[![关于我页面](http://static.blinkfox.com/matery-20181202-7.png)](http://static.blinkfox.com/matery-20181202-7.png)

关于我页面



[![文章详细页面](http://static.blinkfox.com/matery-20181202-8.png)](http://static.blinkfox.com/matery-20181202-8.png)

文章详细页面



## 5. 自定制修改

在本主题的 `_config.yml` 中可以修改部分自定义信息，有以下几个部分：

- 菜单
- 我的梦想
- 首页的音乐播放器和视频播放器配置
- 是否显示推荐文章名称和按钮配置
- `favicon` 和 `Logo`
- 个人信息
- TOC 目录
- 文章打赏信息
- 复制文章内容时追加版权信息
- MathJax
- 文章字数统计、阅读时长
- 点击页面的’爱心’效果
- 我的项目
- 我的技能
- 我的相册
- `Gitalk`、`Gitment`、`Valine` 和 `disqus` 评论配置
- [不蒜子统计](http://busuanzi.ibruce.info/)和谷歌分析（`Google Analytics`）
- 默认特色图的集合。当文章没有设置特色图时，本主题会根据文章标题的 `hashcode` 值取余，来选择展示对应的特色图

**我认为个人博客应该都有自己的风格和特色**。如果本主题中的诸多功能和主题色彩你不满意，可以在主题中自定义修改，很多更自由的功能和细节点的修改难以在主题的 `_config.yml` 中完成，需要修改源代码才来完成。以下列出了可能对你有用的地方：

### 5.1 修改主题颜色

在主题文件的 `/source/css/matery.css` 文件中，搜索 `.bg-color` 来修改背景颜色：

```
/* 整体背景颜色，包括导航、移动端的导航、页尾、标签页等的背景颜色. */
.bg-color {
    background-image: linear-gradient(to right, #4cbf30 0%, #0f9d58 100%);
}
/*如果想去掉banner图的颜色渐变效果，请将以下的css属性注释掉或者删除掉即可*/
@-webkit-keyframes rainbow {
   /* 动态切换背景颜色. */
}
@keyframes rainbow {
    /* 动态切换背景颜色. */
}
```

### 5.2 修改 banner 图和文章特色图

你可以直接在 `/source/medias/banner` 文件夹中更换你喜欢的 `banner` 图片，主题代码中是每天动态切换一张，只需 `7` 张即可。如果你会 `JavaScript` 代码，可以修改成你自己喜欢切换逻辑，如：随机切换等，`banner` 切换的代码位置在 `/layout/_partial/bg-cover-content.ejs` 文件的 `` 代码中：

```
$('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
```

在 `/source/medias/featureimages` 文件夹中默认有 24 张特色图片，你可以再增加或者减少，并需要在 `_config.yml` 做同步修改。

如果想改为每小时或者每分钟切换 banner 图的话，需要将 `getDay()` 改为 `getHours()` 或者 `getMinutes()` 即可。

### 5.3 修改网站相关信息

首先看一个图，如下：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115115221.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115115221.png)

img



紧接着放上相关的配置文件信息：

1. 网站信息的修改

```
#这是根目录下的配置文件信息
title: 过客~励む   #这是网站标题
subtitle: 励む    #这是网站副标题subtitler
# 下面两个description,keywords，需要填上，如果想让搜索引擎收录，这个做SEO优化必不可忽视的两个属性
description: 专注于Web,分享生活,分享知识  #网站描述
keywords: [HTML, CSS, JavaScript, JQuery, React, Vue.js等]  #网站的关键词
author: YangAir  #作者，文章版权所显示的
language: zh-CN  #网站语言，不填写，默认为英文
timezone:   #时区，可以不填写
# 这是主题配置文件的相关信息
# 配置网站favicon和网站LOGO
# 此处我用的CDN，也可以使用本地文件
favicon: https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/favicon.png
logo: https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/logo.png

# 网站副标题，打字效果
# 如果有符号 ‘ ，请在 ’ 前面加上 \
subtitle: 
  enable: true
  loop: true # 是否循环
  showCursor: true # 是否显示光标
  startDelay: 300 # 开始延迟
  typeSpeed: 100 # 打字速度
  backSpeed: 50 # 删除速度
  sub1: 志之所向，金石为开，谁能御之？
  sub2: 花开不是为了花落，而是为了开的更加灿烂。
  sub3: 没有伞的孩子必须努力奔跑！
  sub4: 欲望以提升热忱，毅力以磨平高山。
  sub5: 如果放弃太早，你永远都不知道自己会错过什么。
  sub6: 没有礁石，就没有美丽的浪花；没有挫折，就没有壮丽的人生。
```

**注意：**

网站打字效果副标题默认有两个，即 `sub1` 和 `sub2`，如果想写多个，则需要修改两处地方，首先修改配置文件，如上面所示，在 `sub1` 和 `sub2` 后面继续添加即可，然后在去主题目录下的 `layout` 文件夹下的`_partial` 文件夹，修改 `bg-cover-content.ejs` 文件，大约在 12 行左右，如下面所示：

```
 <div class="description center-align">
     <% if (theme.subtitle.enable) { %>
         <span id="subtitle"></span>
         <script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.11"></script>
        <script>
            var typed = new Typed("#subtitle", {
                strings: ['<%= theme.subtitle.sub1 %>',
                          '<%= theme.subtitle.sub2 %>',
                          '<%= theme.subtitle.sub3 %>',
                          '<%= theme.subtitle.sub4 %>',
                          '<%= theme.subtitle.sub5 %>',
                          '<%= theme.subtitle.sub6 %>'],
                 startDelay: <%= theme.subtitle.startDelay %>,
                 typeSpeed: <%= theme.subtitle.typeSpeed %>,
                 loop: <%= theme.subtitle.loop %>,   
                 backSpeed: <%= theme.subtitle.backSpeed %>,
                 showCursor: <%= theme.subtitle.showCursor %>
              });
          </script>
      <% } else { %>
            <%= config.description %>
      <% } %>
</div>
```

1. 社交链接的修改

默认的配置信息为：

```
# 首页 banner 中的第二行个人信息配置，留空即不启用
socialLink:
  github:  https://github.com/blinkfox
  email: 1181062873@qq.com
  facebook: # https://www.facebook.com/xxx
  twitter: # https://twitter.com/xxx
  qq: 1181062873
  weibo: # https://weibo.com/xxx
  zhihu: # https://www.zhihu.com/xxx
  rss: true # true、false
```

如果想添加简书，CSDN，掘金，博客园等等，需要在主题配置文件添加相关配置，如下是我个人的配置：

```
socialLink:
  qq: 1035800145
  weixin: https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/wechat.png
  github: https://github.com/Yafine
  email: mailto:1035800145@qq.com
  facebook: # https://www.facebook.com/xxx
  twitter: # https://twitter.com/xxx
  weibo: # https://weibo.com/xxx
  zhihu: https://www.zhihu.com/people/xuan-tian-40-64/activities
  juejin: https://juejin.im/user/5a902053f265da4e7527ae71/activities
  csdn: https://blog.csdn.net/victoryxa
  jianshu: https://www.jianshu.com/u/3b3856869772
  cnblogs: https://www.cnblogs.com/yafine/
  rss: true # true、false
```

其中的 `weixin` 我是用的图片链接，会跳转到一个新的标签页，之后还需要修改 `ejs` 文件，文件在主题目录下的 `layout` 文件夹下的`_partial` 文件夹，修改 `social-link.ejs`，添加相关的配置，我个人添加的配置如下：

```
<% if (theme.socialLink.jianshu) { %>
    <a href="<%= theme.socialLink.jianshu %>" class="tooltipped" target="_blank" data-tooltip="关注我的简书: <%= theme.socialLink.jianshu %>" data-position="top" data-delay="50">
        <i class="fab fa-jianshu">简</i>
    </a>
<% } %>

<% if (theme.socialLink.csdn) { %>
    <a href="<%= theme.socialLink.csdn %>" class="tooltipped" target="_blank" data-tooltip="关注我的CSDN: <%= theme.socialLink.csdn %>" data-position="top" data-delay="50">
        <i class="fab fa-csdn">C</i>
    </a>
<% } %>
<% if (theme.socialLink.juejin) { %>
    <a href="<%= theme.socialLink.juejin %>" class="tooltipped" target="_blank" data-tooltip="关注我的掘金: <%= theme.socialLink.juejin %>" data-position="top" data-delay="50">
        <i class="fab fa-juejin">掘</i>
    </a>
<% } %>

<% if (theme.socialLink.cnblogs) { %>
    <a href="<%= theme.socialLink.cnblogs %>" class="tooltipped" target="_blank" data-tooltip="关注我的博客园: <%= theme.socialLink.cnblogs %>" data-position="top" data-delay="50">
        <i class="fab fa-juejin">博</i>
    </a>
<% } %>
<% if (theme.socialLink.weixin) { %>
    <a href="<%= theme.socialLink.weixin %>" class="tooltipped" target="_blank" data-tooltip="微信联系我: <%= theme.socialLink.weixin %>" data-position="top" data-delay="50">
        <i class="fab fa-weixin"></i>
    </a>
<% } %>
```

## 6. 版本记录

- v1.3.2
  - 新增了繁体字的支持；
  - 新增了 404 页面；
  - 其他小问题修改；
- v1.3.1
  - 新增了 `kbd` 样式；
  - 修复了子目录部署时词云中链接有误的问题；
  - 移除了 TOC 中的竖线；
  - 修复了首页 icon 图标中的 tooltip 不显示的问题；
  - 修复生成静态文件时，每天切换 banner 不生效的问题；
  - 更新了 `miniValine` 中的一些配置；
- v1.3.0
  - 新增了支持子目录部署的功能（如：`Gitee`）；
  - 新增了 `MiniValine` 评论系统；
  - 新增了 `jsdelivr` 的支持；
  - 修复了诸多发现的 bug；
- v1.2.2
  - 新增了自定义文章 `keywords` 的功能；
  - 新增静态彩带点击切换的功能和配置；
  - 将文章字数统计、彩带和站点运行时间等功能默认设置为 `false`；
  - 修改了文章的 `description` 的 meta 属性优先读取文章的 `summary` 属性；
  - 修改了文章标题的 HTML 标签，从 `div` 改成了 `h1` 标题；
  - 修改了页脚年份显示不正确的问题；
  - 去掉了站点运行时间中多余的 `setTimeout` 代码；
- v1.2.1
  - 新增了 TOC 的展开目录层级设置和滚动条功能，防止目录较多的时候目录溢出；
  - 修改了首页的展示方式为以前的模式；
  - 修复首页按钮没有边框的问题；
  - 修复了音乐及吸底模式、视频、推荐文章等不激活时仍然生成首页卡片的问题；
  - 修复 wordCount 插件未安装的问题，修改了部分配置；
  - 修复音乐的 JSON 配置中有单引号的情况页面不显示的音乐的问题
  - 修复标签云在 Hexo4.0 下链接失效的问题；
- v1.2.0
  - 新增了 [DaoVoice](http://www.daovoice.io/)、[Tidio](https://www.tidio.com/) 的在线聊天功能；
  - 新增了两级菜单的功能；
  - 新增了打字效果的副标题；
  - 新增了网页内容预加载的功能；
  - 新增了首页 banner 是否每日切换的配置功能；
  - 新增了显示 ICP 备案信息的功能，默认未开启；
  - 新增了百度分析的配置；
  - 新增了代码块的语言显示、一键复制、显示行号等功能；
  - 新增了首页轮播图和推荐文章可自定义配置的功能；
  - 新增了文章页面显示更新日期；
  - 新增了转载规则的图标；
  - 修改了分享的布局和显示方式；
  - 升级更新了部分依赖库的版本；
  - 其他细节修改和优化；
- v1.1.0
  - 新增了 `emoji` 的支持；
  - 新增了站点运行时间统计及配置；
  - 新增了留言板的功能，默认未开启；
  - 新增了 `Twitter`、`Facebook`、知乎的社交链接；
  - 更新了 `Valine` 的版本为最新版；
  - 其他小细节的修改；
- v1.0.4
  - 新增了能为每篇文章都自定义转载规则的功能；
  - 修复上一页、下一页的自定义 `summary` 不显示的问题；
  - 修复了友情链接显示错位的问题，改为了瀑布流的布局方式；
  - 其他小细节 bug 的修改；
- v1.0.3
  - 新增了 `TOC` 展开、收缩的按钮和相关配置，默认显示此按钮；
- v1.0.2
  - 升级了 [Materialize](https://materializecss.com/) 框架版本为 `1.0.0`，重构和修改了升级过程中的部分文件或问题；
  - 新增了首页封面的全屏轮播特效，可以将更重要的文章设置到首页轮播中；
  - 修复首页第一个按钮是中文的问题
  - 修复了 iPhone 上点击搜索输入获取焦点的问题；
  - 修复了 iPhone 上输入框获取焦点后页面放大的问题；
  - 修复一些文章或 UI 显示问题；
- v1.0.1
  - 调整 `css`、`js` 的文件请求路径在主题的`_config.yml` 中配置，便于你更快捷的配置自己的 CDN；
  - 新增代码是否折行为可配置，默认为折行；
  - 默认激活 `TOC` 功能，并新增为某篇文章关闭 `TOC` 的 `Front-matter` 配置选项；
  - 修复文章滚动时，高亮的目录选项不准确的问题；
  - `IOS` 下移除搜索框自动获得焦点属性，防止自动获得焦点后导致视图上移；
- v1.0.0
  - 新增了所有基础功能；

# 六、其他一些 DIY (可选)

> 主题 DIY 会涉及到 js 文件和 css 文件等的修改，个人建议新增的 js 文件放在 `themes/matery/layout/layout.ejs` 这个文件下，这样会稍微加快博客访问的速度。不想花钱最好的方式是使用 cdn.jsdeliver。以后会说到。

## 1. 动态标题

先放上效果图再说：

[![离开当前页面时](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191201224219.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191201224219.png)

离开当前页面时

[![返回当前页面时](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191201224258.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191201224258.png)

返回当前页面时



实现方法，引入 js 文件，在主题文件下的 `/source/js/` 下新建 `FunnyTitle.js`，然后在添加到 `themes/matery/layout/layout.ejs` 或者添加到 `themes/matery/layout/_partial/head.ejs`，其代码如下：

```
<!--浏览器搞笑标题-->
 var OriginTitle = document.title;
 var titleTime;
 document.addEventListener('visibilitychange', function () {
     if (document.hidden) {
         $('[rel="icon"]').attr('href', "https://cdn.jsdelivr.net/gh/Yafine/cdn@2.5/source/favicon.png");
         document.title = 'ヽ(●-`Д´-)ノ你要玩捉迷藏嘛';
         clearTimeout(titleTime);
     }
     else {
         $('[rel="icon"]').attr('href', "https://cdn.jsdelivr.net/gh/Yafine/cdn@2.5/source/favicon.png");
         document.title = 'ヾ(Ő∀Ő3)ノ好哦！' + OriginTitle;
         titleTime = setTimeout(function () {
             document.title = OriginTitle;
         }, 2000);
     }
 });
```

我的链接：**https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/FunnyTitle.js**（理论上一直有效）

或者直接在 `themes/matery/layout/layout.ejs` 文件中添加如下代码：

```
<script type="text/javascript">
    var OriginTitile=document.title,st;
    document.addEventListener("visibilitychange",function(){
        document.hidden?(document.title="ヽ(●-`Д´-)ノ你要玩捉迷藏嘛",clearTimeout(st)):(document.title="(Ő∀Ő3)ノ好哦！",st=setTimeout(function(){document.title=OriginTitile},3e3))
    })
</script>
```

## 2. 修改导航栏颜色以及透明效果

打开 `themes/matery/source/css/matery.css` 文件，大约在 250 行，有一个`.bg-color` 属性，修改其属性值即可，代码如下：

```
.bg-color {
    background-image: linear-gradient(to right, #4cbf30 0%, #0f9d58 100%); //修改成自己喜欢的颜色值
    opacity: 0.8;  //透明效果 值范围 0~1，看情况自己修改
}
```

## 3. 添加动态诗词

采用的是[今日诗词](https://www.jinrishici.com/)，每次返回一句诗词，根据时间、地点、天气、事件智能推荐。官网有 [API 文档](https://www.jinrishici.com/doc/)，可以去看一下，有多种安装方式，最简单的方式就是从官网获取代码，在 `/themes/matery/layout/_partial/head.ejs` 添加下面的一行代码：

```
<script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
```

然后再将 `/themes/matery/layout/_partial/bg-cover-content.ejs` 中的 `<%= config.description %>` 修改为把 `<%= config.description %>` 改为 `<span id="jinrishici-sentence">正在加载今日诗词....</span>' %>`，这个使用前提是将主题配置文件的 `subtitle` 的值改为 `false`。

## 4. 鼠标点击文字特效

实现方法，引入 js 文件，在主题文件下的 `/source/js/` 下新建 `click_show_text.js`，其代码如下：

```
var a_idx = 0;
jQuery(document).ready(function ($) {
    $("body").click(function (e) {
        var a = new Array("富强", "民主", "文明", "和谐", "自由", "平等", "公正", "法治", "爱国", "敬业", "诚信", "友善");
        var $i = $("<span/>").text(a[a_idx]);
        a_idx = (a_idx + 1) % a.length;
        var x = e.pageX,
            y = e.pageY;
        $i.css({
            "z-index": 5,
            "top": y - 20,
            "left": x,
            "position": "absolute",
            "font-weight": "bold",
            "color": "#FF0000"
        });
        $("body").append($i);
        $i.animate({
                "top": y - 180,
                "opacity": 0
            },
            3000,
            function () {
                $i.remove();
            });
    });
    setTimeout('delay()', 2000);
});

function delay() {
    $(".buryit").removeAttr("onclick");
}
```

或者使用我的 cdn 链接，理论上一直有效 **https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/click_show_text.js**，然后在添加到 `themes/matery/layout/layout.ejs`。

## 5. 修改原有相册

> 参考教程：https://yafine-blog.cn/posts/3b98.html

## 6. 添加天气小插件

首先去中国天气官网：[https://cj.weather.com.cn/plugin/pc，配置自己的插件，选择自定义插件 —> 自定义样式 ——> 生成代码，然后会生成一段代码，复制粘贴到](https://cj.weather.com.cn/plugin/pc，配置自己的插件，选择自定义插件—>自定义样式——>生成代码，然后会生成一段代码，复制粘贴到) `themes/matery/layout/layout.ejs` 即可。

## 7. 关于我页面添加个人简历

打开 `theme/matery/layout/about.ejs` 文件，大约在 13 行。有一个 `` 标签，找出其对应结尾的标签，大约在 61 行左右，然后在新增如下代码：

```
<div class="card">
     <div class="card-content">
         <div class="card-content article-card-content">
             <div class="title center-align" data-aos="zoom-in-up">
                 <i class="fa fa-address-book"></i>&nbsp;&nbsp;<%- __('个人简历') %>
              </div>
                 <div id="articleContent" data-aos="fade-up">
                     <%- page.content %>
                 </div>
           </div>
      </div>
</div>
```

注意粘贴的位置和空格要正确，这里的位置随你自己设置，你也可以把简历作为第一个 card，然后 `/source/about/index.md` 下面写上你的简历了（就像写博客一样）。

## 8. 豆瓣书单电影页面

注意：首先需要检查你的 hexo 版本是多少，在你的博客目录下执行命令 hexo -v 即可，这个豆瓣插件需要的版本需要 < 4.2.0，否则会出现 bug，比如点击书单的在读，想读或者已读会出现一个新的弹出页面，解决办法就是降低 hexo 的版本，先卸载目前的 hexo 版本，再安装 4.0.0 版本的 hexo 即可，我的版本为 4.0.0。

```
npm uninstall hexo
npm install hexo@4.0.0 -g
```

1. 首先在博客站点目录执行下面的命令安装豆瓣插件：

```
npm install hexo-douban --save
```

1. 紧接着在博客站点目录的配置文件`_config.yml` 下，添加如下配置：

```
douban: 
  user: 252345665    #这个需要修改为你个人的id  
  builtin: false   #如果想生成豆瓣页面，这个需要设置为true
  book: 
    title: 'This is my book title' 
    quote: 'This is my book quote' 
  movie: 
    title: 'This is my movie title' 
    quote: 'This is my movie quote' 
  game: 
    title: 'This is my game title' 
    quote: 'This is my game quote' 
  timeout: 10000
```

- **user**:：你的豆瓣 ID。打开豆瓣，登入账户，然后在右上角点击 ” 个人主页 “，这时候地址栏的 URL 大概是这样：https://www.douban.com/people/xxxxxx/ ，其中的”xxxxxx” 就是你的个人 ID 了。
- **builtin**：是否将生成页面的功能嵌入 `hexo s` 和 `hexo g` 中，默认是 `false` ，另一可选项为 `true` 。
- **title**： 该页面的标题。
- **quote**： 写在页面开头的一段话，支持 html 语法。
- **timeout**： 爬取数据的超时时间，默认是 10000ms，如果在使用时发现报了超时的错 (ETIMEOUT) 可以把这个数据设置的大一点。

如果只想显示某一个页面 (比如 movie)，那就把其他的配置项注释掉即可。

1. 然后再主题配置文件`_config.yml` 中添加关于此页面的菜单：(下面是我的配置)

```
menu:
    媒体:
       url: /
       icon: fas fa-list
       children:
         - name: 电影
           url: /movies
           icon: fas fa-film
         - name: 书单
           url: /books
           icon: fas fa-book
         - name: 游戏
           url: /games
           icon: fas fa-gamepad
```

1. 适配 Matery 主题：在 `/themes/hexo-theme-matery/layout` 文件夹下面创建一个名为 `douban.ejs` 的文件，并将下面的内容复制进去：

```
<%- partial('_partial/post-cover') %> 
<style> 
    .hexo-douban-picture img {
        width: 100%; 
    } 
</style>
<main class="content"> 
    <div id="contact" class="container chip-container"> 
        <div class="card"> 
            <div class="card-content" style="padding: 30px"> 
                <h1 style="margin: 10px 0 10px 0px;"><%= page.title %></h1> 
                <%- page.content %> 
            </div> 
        </div> 
        <div class="card"> 
            <div class="card-content" style="text-align: center"> 
                <h3 style="margin: 5px 0 5px 5px;">如果你有好的内容推荐，欢迎在下面留言！</h3> 
            </div> 
        </div> 
        <div class="card"> 
            <% if (theme.gitalk && theme.gitalk.enable) { %>
                <%- partial('_partial/gitalk') %>
            <% } %> 
            <% if (theme.gitment.enable) { %> 
                <%- partial('_partial/gitment') %> 
            <% } %> 
            <% if (theme.disqus.enable) { %> 
                <%- partial('_partial/disqus') %> 
            <% } %> 
            <% if (theme.livere && theme.livere.enable) { %> 
                <%- partial('_partial/livere') %> 
            <% } %> 
            <% if (theme.valine && theme.valine.enable) { %> 
                <%- partial('_partial/valine') %> 
            <% } %> 
        </div> 
    </div> 
</main>
```

1. 然后在博客站点目录下的 `node_modules` 文件夹下找到 `hexo-douban/lib`，文件夹下有三个 js 文件，分别为：`books-generator.js` 、`games-generator.js` 、`movies-generator.js`，用文本编辑器打开这三个文件，并将其文件内容末尾的代码修改为一下内容：

```
/* 原文件内容为 layout: [`page`, `post`] ，将其修改为下面的内容*/
layout: [`page`, `douban`]
```

1. 最后就是使用并生成相应的页面，执行命令如下:

```
hexo douban
```

**需要注意的是**，通常大家都喜欢用 `hexo d` 来作为 `hexo deploy` 命令的简化，但是当安装了 `hexo douban` 之后，就不能用 `hexo d` 了，因为 `hexo douban` 跟 `hexo deploy` 的前缀都是 `hexo d` ，你以后执行的 `hexo d` 将不再是 Hexo 页面的生成，而是豆瓣页面的生成。

以下是可选的命令参数：

```
-h, --help    # 帮助页面
-b, --books   # 只生成书单页面
-g, --games   # 只生成游戏页面
-m, --movies  # 只生成电影页面
```

**当站点配置文件的 builtin 的值为 true 时，生成页面的功能会嵌入到 `hexo g` 和 `hexo s` 中，在进行部署生成操作，会自动生成相应的页面**。

## 9. 外链跳转插件

> [hexo-external-link](https://blog.hvnobug.com/go.html?url=aHR0cHM6Ly9naXRodWIuY29tL2h2bm9idWcvaGV4by1leHRlcm5hbC1saW5r) 是一个跳转外链相关插件。自动为所有 html 文件中外链的 a 标签生成对应的属性。 比如 设置 `target=’_blank’, rel=’external nofollow noopener noreferrer’` 告诉搜索引擎这是外部链接，不要将该链接计入权重。 同时自动生成外链跳转页面，默认在根目录下 go.html;

使用 npm 或者 yarn 安装

```
## npm 安装
npm install hexo-external-link --save
## yarn 安装
yarn add hexo-external-link
```

之后再 hexo 博客站点根目录下添加如下配置：

```
hexo_external_link:
  enable: true
  enable_base64_encode: true
  url_param_name: 'u'
  html_file_name: 'go.html'
  target_blank: true
  link_rel: 'external nofollow noopener noreferrer'
  domain: 'your_domain' # 如果开启了防盗链，填写你的域名
  safety_chain: true
```

- **enable** - 是否开启 `hexo_external_link` 插件 - 默认 false
- **enable_base64_encode** - 是否对跳转 `url` 使用 `base64编码` - 默认 fasle
- **url_param_name** - url 参数名，在跳转到外链传递给 `html_file_name` 的参数名 - 默认 ‘u’
- **html_file_name** - 跳转到外链的页面文件路径 - 默认 ‘go.html’
- **target_blank** - 是否为外链的 `a` 标签添加 `target='_blank'` - 默认 true
- **link_rel** - 设置外链的 `a` 标签的 rel 属性 - 默认 ‘external nofollow noopener noreferrer’
- **domain** - 如果开启了防盗链，除了 localhost 和 domain (你的域名) 之外调用会跳到主页，同时也是判断链接是否为外链的依据 - 默认 window.location.host
- **safety_chain** - go.html 为了防止外链盗用 对域名进行的判断 - 默认 false

## 10. 添加动态科技线条背景

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/04.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/04.gif)

img



在 `themes/matery/layout/layout.ejs` 文件中添加如下代码：

```
<!--动态线条背景-->
<script type="text/javascript"
color="122 103 238" opacity='0.7' zIndex="-2" count="200" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js">
</script>
```

其中：

- color：表示线条颜色，三个数字分别为 (R,G,B)，默认：（0,0,0）
- opacity：表示线条透明度（0~1），默认：0.5
- count：表示线条的总数量，默认：150
- zIndex：表示背景的 z-index 属性，css 属性用于控制所在层的位置，默认：-1

## 11. 添加鼠标点击烟花爆炸效果

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/03.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/03.gif)

img



首先在 `themes/matery/source/js` 目录下新建 `fireworks.js` 文件，打开这个网址[传送门](https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/fireworks.js)，将内容复制粘贴到 `fireworks.js` 即可。

然后再 `themes/matery/layout/layout.ejs` 文件内添加下面的内容：

```
<canvas class="fireworks" style="position: fixed;left: 0;top: 0;z-index: 1; pointer-events: none;" ></canvas> 
<script type="text/javascript" src="//cdn.bootcss.com/animejs/2.2.0/anime.min.js"></script> 
<script type="text/javascript" src="/js/fireworks.js"></script>
```

然后 `hexo clean && hexo g && hexo s` 即可，就可以看到效果了。

## 12. 添加樱花飘落效果

先看效果：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/02.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/02.gif)

img



在 `themes/matery/source/js` 目录下新建 `sakura.js` 文件，打开这个网址[传送门](https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/sakura.js)，将内容复制粘贴到 sakura.js 即可。

然后再 `themes/matery/layout/layout.ejs` 文件内添加下面的内容：

```
<script type="text/javascript">
//只在桌面版网页启用特效
var windowWidth = $(window).width();
if (windowWidth > 768) {
    document.write('<script type="text/javascript" src="/js/sakura.js"><\/script>');
}
</script>
```

## 13. 添加鼠标彩虹星星掉落跟随效果

先看看效果，再决定要不要用。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/01.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/01.gif)

img



在 `themes/matery/source/js` 目录下新建 `cursor.js` 文件，打开这个网址[传送门](https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/cursor.js)，将内容复制粘贴到 cursor.js 即可。

然后再 `themes/matery/layout/layout.ejs` 文件内添加下面的内容：

```
<script src="/js/cursor.js"></script>
```

## 14. 添加雪花飘落效果

先看看效果吧！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/1.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/1.gif)

img

) 在 `themes/matery/source/js` 目录下新建 `snow.js` 文件，打开这个网址[传送门](https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/js/snow1.js)，将内容复制粘贴到 cursor.js 即可。



然后再 `themes/matery/layout/layout.ejs` 文件内添加下面的内容：

```
<script src="/js/snow.js"></script>
```

## 15. 添加自定义页面

首先看一下效果吧，我自己写的，写的不好，不要笑我哦！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115.gif)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115.gif)

img



以我的配置为例：

首先在站点目录下的 source 文件夹下新建 `aboutme` 文件，文件名可自定义，然后编写一个 `index.html` 放入 `aboutme` 文件夹下，然后在主题配置文件下的导航配置信息添加下面的配置：

```
About:
    url: /
    icon: fas fa-address-card
    children:
      - name: 关于我
        url: /about
        icon: fas fa-user-circle
      - name: Another    #这是新添加的，在原有配置基础上添加
        url: /aboutme
        icon: fa fa-user-secret
```

然后在站点配置文件下，找到 `skip_render`，在后面添加属性，如下：

```
skip_render: aboutme/**  # 其意思为在对文件进行渲染时跳过aboutme文件下的所有文件
```

如果添加需要跳过多个目录下的文件时，配置如下：

```
skip_render: 
    - aboutme/** 
    - box/**
    - 2020/**
```

知道方法后，你可以添加你自己想要添加的页面，让你的博客内容更加充实。

## 16. 添加 404 页面

我的 404 页面是这样的：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200117142120.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200117142120.png)

img



开始说一下配置步骤，首先再站点根目录下的 source 文件夹下新建 `404.md` 文件，里面内容如下：

```
---
title: 404
date: 2019-10-28 16:41:10
type: "404"
layout: "404"
description: "Oops～，我崩溃了！找不到你想要的页面了"
---
```

紧接着再新建主题文件夹的 layout 目录下新建 `404.ejs` 文件，添加内容如下：

```
<style type="text/css">
    /* don't remove. */
    .about-cover {
        height: 90.2vh;
    }
</style>
<div class="bg-cover pd-header about-cover">
    <div class="container">
        <div class="row">
            <div class="col s10 offset-s1 m8 offset-m2 l8 offset-l2">
                <div class="brand">
                    <div class="title center-align">
                        404
                    </div>
                    <div class="description center-align">
                        <%= page.description %>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
    // 每天切换 banner 图.  Switch banner image every day.
    $('.bg-cover').css('background-image', 'url(https://cdn.jsdelivr.net/gh/Yafine/cdn@3.3.4/source/medias/banner/' + new Date().getDay() + '.jpg)');
</script>
```

然后部署，再看看效果即可。

## 17. 文章生成永久链接

主题默认的文章链接配置是

```
permalink: :year/:month/:day/:title
```

这种生成的链接地址很长，文章版权的链接地址会出现一大串字符编码，一点也不好看。因此需要修改文章生成链接的格式。

首先再根目录下执行下面的命令：

[hexo-abbrlinkGitHub 地址](https://github.com/rozbo/hexo-abbrlink)

```
npm install hexo-abbrlink --save
```

然后再站点配置文件下添加如下配置：

```
abbrlink:
    alg: crc16   #算法： crc16(default) and crc32
    rep: hex     #进制： dec(default) and hex: dec #输出进制：十进制和十六进制，默认为10进制。丨dec为十进制，hex为十六进制
```

再将站点配置文件的 `permalink` 的值修改为：

```
permalink: posts/:abbrlink.html  # 此处可以自己设置，也可以直接使用 :/abbrlink
```

生成文章的链接格式就会是如下样例（官方样例）:

```
crc16 & hex
https://post.zz173.com/posts/66c8.html

crc16 & dec
https://post.zz173.com/posts/65535.html
crc32 & hex
https://post.zz173.com/posts/8ddf18fb.html

crc32 & dec
https://post.zz173.com/posts/1690090958.html
```

生成完后，原 md 文件的 Front-matter 内会增加 `abbrlink` 字段，值为生成的 ID 。这个字段确保了在我们修改了 `Front-matter` 内的博客标题 title 或创建日期 date 字段之后而不会改变链接地址。

## 18. 页面获取标题 (可选)

看两个图就知道是怎么回事了。

客官说：小二儿，上图。

小二儿说：来喽！

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200215202242.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200215202242.png)

img



[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200215202340.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200215202340.png)

img



看图中所指出的文字，和你的比较一下，你就知道差别在哪了！不说这么多的废话了，上教程！看下面。

以我的博客位置为例，修改 `F:\blog\themes\matery\layout\_partial` 中的 `bg-cover-content.ejs` 文件，其中原主题中这个文件的代码为 (大约在第 4 行)：

```
<div class="title center-align">
     <% if (config.subtitle && config.subtitle.length > 0) { %>
            <%= config.subtitle %>
     <% } else { %>
            subtitle
     <% } %>
</div>
```

修改过后的代码为：

```
<div class="title center-align">
     <% if (is_home() && config.subtitle && config.subtitle.length > 0) { %>
        <%= config.subtitle %>
     <% } else { %>
        <%= page.title %>
     <% } %>
</div>
```

> 这个有一点 bug，归档页面标题无法显示，解决办法目前还没有，以后如果解决，会更新文档的！

然后保存，执行 `hexo cl && hexo g && hexo s` 查看效果即可。

**注意：**获取的 `title` 标题在 md 文档中的 `fromt-matter` 属性中 `title` 的值，可自定义，你只需要去本地找到页面所在的 md 文档中，将其值修改为中文或者英文即可。

例如：友情链接这一块，你去博客文件的 `F:\blog\source\friends`（这是我的本地路径）目录，打开目录下的 index.md 文档，将 `title` 后面的值由原来的 `friends` 值修改为中文的友情链接或者友人帐或者其他（自定义），然后保存，执行命令，查看效果即可，如没有问题，在部署到代码托 i 管平台。完美！

# 七、添加评论系统

我只说几个常用的评论系统的配置方法，其他的就不说了。

## 7.1 添加来必力评论系统

首先去[来必力官网](https://livere.com/)，点击导航栏上的安装，会出现如下图的页面：

- City 版：是一款适合所有人使用的免费版本；
- Premium 版：是一款能够帮助企业实现自动化管理的多功能收费版本。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115142313.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115142313.png)

img



注册完之后，会提示你填写网站的相关信息，如网站链接，网站名称等等，填写完毕之后，会给你一段代码，如下图所示：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/image-20200115142709585.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/image-20200115142709585.png)

img



```
# Livere comment configuration, the default is not activated
# Livere 来必力评论模块的配置，默认为不激活
livere:
  enable: true   # true即为开启评论系统
  uid: #这里填写你的uid
```

然后在执行相关的部署命令，然后查看效果即可。

## 7.2 添加 Valine 评论系统

[Valine 官方文档](https://valine.js.org/)

如果注册过 LeanCloud，请点击此处进行[登录](https://leancloud.cn/dashboard/login.html#/signin)，未注册的请点击[注册](https://leancloud.cn/dashboard/login.html#/signup)

经过登录或者注册之后再登录，就会进入如下的页面：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115145855.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115145855.png)

img



创建应用完成后，会出现如下页面，然后点击设置

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115150319.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115150319.png)

img



会出现下面的页面，将其中 APPID 和 APPKey 复制，添加到配置文件中。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115150641.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115150641.png)

img



```
# The configuration of the Valine comment module is not activated by default.
# To use it, activate the configuration item and set appId and appKey.
# Valine 评论模块的配置，默认为不激活，如要使用，就请激活该配置项，并设置 appId 和 appKey.
valine:
  enable: false  # true即为开启评论系统
  appId:   #此处填写你的appid
  appKey:  #此处填写你的appkey
  notify: false
  verify: false
  visitor: true
  avatar: 'mm' # Gravatar style : mm/identicon/monsterid/wavatar/retro/hide
  pageSize: 10
  placeholder: 'just go go' # Comment Box placeholder
  background:  https://cdn.jsdelivr.net/gh/Yafine/cdn@3.1.1/social/comment_bg.png
```

然后执行相关部署命令，查看效果即可。

## 7.3 添加 Gitalk 评论模块

首先去这个地方看一下 Gitalk 的效果吧！[传送门](https://gitalk.github.io/)

安装步骤如下：

1. **注册 OAuth Application**

当别人评论你的文章时，会需要它是授权。点击[注册 OAuth Application](https://github.com/settings/applications/new) 进行注册，注册界面如下：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115154248.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115154248.png)

img



- **Application name：**应用名称，自己随意起名。
- **Homepage URL：**博客主页地址，如果有域名，此处填写域名，无域名，填写你的默认 github 地址：如 `https://username.github.io`。
- **Application description：**应用描述，可选，可以写也可以不写。
- **Authorization callback URL：**授权后返回的地址，需要与 **Homepage URL** 一致。

点击 **Register application**（注册）会出现 **Client ID/Secret**，接下来就是将信息填入配置文件中。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115155054.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20200115155054.png)

img



1. **新建 GitHub 仓库**

新建仓库就不在多说了，相信大家都会，如果不会的话，上面有写。

1. **配置 _config.yml 文件**

```
# the Gitalk config，default disabled
# Gitalk 评论模块的配置，默认为不激活
gitalk:
  enable: true    # true即开启评论模块
  owner: Yafine  # 填写你的 github 账户名即可
  repo: Yafine-gitalks   # 新建一个仓库或者使用博客托管的仓库也可
  oauth:
    clientId: #填写你的clientId
    clientSecret:  #填写你的clientSecret
  admin: Yafine  #填写你的 github 账户名即可
```

1. 然后再进行部署步骤即可，第一次查看效果需要登录 github 账号，关联授权后，就可以使用评论系统了。

> 友情提醒：开启这个评论系统会对主题中的表格有影响，所以根据个人喜好决定是否开启。

## 7.4 添加 Disqus 评论模块

还在完善，这个貌似得通过特殊途径才能注册。有时间再写吧。

你也可以参考这位作者的文档，作者自己搭建的代理：https://disqusjs.skk.moe/

# 八、域名解析与绑定

域名的购买流程我就不说了，相信大家应该都会购买吧，一般都会去阿里云或者腾讯云购买域名。下面就简单的说一下，如何绑定域名并进行解析。

在这里以腾讯云解析为例（我的域名是在腾讯云购买的），登录腾讯云的控制台，进入到域名管理页面，然后点击解析，进行域名的解析，如下图所示：

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205232306.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205232306.png)

img



进入云解析列表，添加记录值如下图所示：

IP 地址可以提供 cmd 命令得到，命令为 **ping username.github.com**，会得到来自 `xxx.xxx.xxx.xxx` 的回复，这个就是 github 的 IP 地址，将得到的 IP 地址填入记录值即可，如下图所示。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205231816.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205231816.png)

img



> 上面第一个行的线路类型第一次先选择默认，上面的境外路线，这是我后来配置的双部署，国内访问走 coding 路线，国外访问走 GitHub 路线。

**说明：**

以我的域名为例：yafine-blog.cn

> **提示：**要解析 `www.yafine-blog.cn`，请填写 www。主机记录就是域名前缀，常见用法如下：

| 主机记录 | 说明                                                     |
| -------- | -------------------------------------------------------- |
| www      | 解析后的域名为 `www.yafine-blog.cn`                      |
| @        | 直接解析主域名 yafine-blog.cn                            |
| *        | 泛解析，匹配其他所有域名 *.yafine-blog.cn                |
| mail     | 将域名解析为 mail.yafine-blog.cn，通常用于解析邮箱服务器 |
| 二级域名 | 如 abc.yafine-blog.cn，填写 abc                          |
| 手机网站 | 如 m.yafine-blog.cn，填写 m                              |

> **提示:**
>
> 将域名指向云服务器，请选择**「A」**； 将域名指向另一个域名，请选择**「CNAME」**； 建立邮箱请选择**「MX」**，根据邮箱服务商提供的 MX 记录填写。

| 记录类型 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| A        | 用来指定域名的 IPv4 地址（如 8.8.8.8），如果需要将域名指向一个 IP 地址，就需要添加 A 记录。 |
| CNAME    | 如果需要将域名指向另一个域名，再由另一个域名提供 IP 地址，就需要添加 CNAME 记录。 |
| MX       | 如果需要设置邮箱，让邮箱能收到邮件，就需要添加 MX 记录。     |
| TXT      | 在这里可以填写任何东西，长度限制 255。绝大多数的 TXT 记录是用来做 SPF 记录（反垃圾邮件） |
| NS       | 域名服务器记录，如果需要将子域名交给其他 DNS 服务商解析，就需要添加 NS 记录。 |
| AAAA     | 用来指定主机名（或域名）对应的 IPv6 地址（例如：ff06:0:0:0:0:0:0:c3）记录。 |
| SRV      | 记录了哪台计算机提供了哪个服务。格式为：服务的名字、点、协议的类型，例如：_xmpp-server_tcp。 |
| 显性 URL | 从一个地址 301 重定向到另一个地址的时候，就需要添加显性 URL 记录（注：DNSPod 目前只支持 301 重定向）。 |
| 隐性 URL | 类似于显性 URL，区别在于隐性 URL 不会改变地址栏的域名。      |

> **注意**：在这之前需要在站点根目录的 source 目录下新建一个 CNAME 文件，里面写入自己的域名，然后保存，在进行如下的步骤。这样到最后当你在地址栏输入 xxx.github.io 时，才会自动跳转到你的域名。

然后在你的 GitHub 仓库的设置里找到这个页面，将你的域名填到 Custom domain 选项下，强制开启 https，即当你在地址栏输入域名，会自动识别域名为 https 开头。然后进行保存。

[![img](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205230514.png)](https://cdn.jsdelivr.net/gh/Yafine/Yafine-imgs/images/20191205230514.png)

img



# 九、 博客优化

## 1. 图片懒加载

> **知识小课堂：**图片加载方式有两种，一个是预加载，另一个就是懒加载，那你了解什么是预加载和懒加载吗？下面来学习一下。
>
> 参考：[图片预加载与图片懒加载（缓载）的区别与实现](https://blog.csdn.net/alex8046/article/details/50388050)

- 图片预加载：顾名思义，图片预加载就是在网页全部加载之前，提前加载图片。当用户需要查看时可直接从本地缓存中渲染，以提供给用户更好的体验，减少等待的时间。否则，如果一个页面的内容过于庞大，没有使用预加载技术的页面就会长时间的展现为一片空白，这样浏览者可能以为图片预览慢而没兴趣浏览，把网页关掉，这时，就需要图片预加载。当然这种做法实际上牺牲了服务器的性能换取了更好的用户体验。
- 图片懒加载（缓载）：延迟加载图片或符合某些条件时才加载某些图片。这样做的好处是减少不必要的访问数据库或延迟访问数据库的次数，因为每次访问数据库都是比较耗时的即只有真正使用该对象的数据时才会创建。懒加载的主要目的是作为服务器前端的优化，减少请求数或延迟请求数。

**预加载与懒加载的区别之处：**

两者的行为是相反的，一个是提前加载，一个是迟缓甚至不加载。懒加载对服务器前端有一定的缓解压力作用，预载则会增加服务器前端压力。

使用图片懒加载需要安装插件：[hexo-lazyload-image](https://github.com/Troy-Yang/hexo-lazyload-image)

在站点根目录执行下面的命令：

```
npm install hexo-lazyload-image --save
```

之后在站点配置文件下添加下面的代码：

```
lazyload:
  enable: true  # 是否开启图片懒加载
  onlypost: false  # 是否只对文章的图片做懒加载
  loadingImg: # eg ./images/loading.gif
```

最后执行 `hexo clean && hexo g && hexo s` 就可以看到效果了。

注意，以下几个小问题针对 matery 主题而言，其他主题是否会出现以下情况目前我也不清楚，如果出现，你在尝试下以下解决方法。(暴力解决法，而不是直接修改懒加载插件😂😂😂)

- 问题 1：查看大图，发现全部为 loading 加载图，原因是因为懒加载插件与 **lightgallery 插件**冲突，解决办法如下：

修改主题文件下的 **matery.js**，在 108 行左右添加以下代码：

```
$(document).find('img[data-original]').each(function(){
    $(this).parent().attr("href", $(this).attr("data-original"));
});
```

- 问题 2：点击首页 **logo** 不是跳转到首页，而是查看 **logo** 图片，解决办法如下：

修改主题的 **header.ejs** 文件，原代码为：

```
<div class="brand-logo">
    <a href="<%- url_for() %>" class="waves-effect waves-light">
         <% if (theme.logo !== undefined && theme.logo.length > 0) { %>
         <img src="<%= theme.logo %>" class="logo-img" alt="LOGO">
         <% } %>
         <span class="logo-span"><%- config.title %></span>
    </a>
</div>
```

修改为：

```
<div class="brand-logo">
    <a href="<%- url_for() %>" class="waves-effect waves-light">
        <div>
            <% if (theme.logo !== undefined && theme.logo.length > 0) { %>
            <img src="<%= theme.logo %>" class="logo-img" alt="LOGO">
            <% } %>
            <span class="logo-span"><%- config.title %></span>
        </div>
    </a>
</div>
```

### 懒加载优化

> 经过以上操作就已经很完美了，以下内容可做可不做

- 其实第一次加载后本地都是有缓存的，如果每次都把 loading 显示出来就不那么好看

- 所以我们需要对插件进行魔改，让图片稍微提前加载，避开加载动画

- 打开 `Hexo根目录` >`node_modules` > `hexo-lazyload-image` > `lib` > `simple-lazyload.js` 文件

- 第 9 行修改为：

  ```
  && rect.top <= (window.innerHeight +240 || document.documentElement.clientHeight +240)
  ```

- 作用：提前 240 个像素加载图片；当然这个值也可以根据自己情况修改

> 参考：https://blog.sky03.cn/posts/42790.html#toc-heading-5

## 2. 代码压缩

### 方法一：gulp 代码压缩

因为 hexo 生成的 html、css、js 等都有很多的空格或者换行，而空格和换行也是占用字节的，所以需要将空格换行去掉也就是我要进行的 “压缩”。

有人说空格换行能占多少字节？确实占不了多少，但是一个人访问是这么多字节，那么一百人，一万人呢？加起来这量就不少了吧，这都是流量啊！这也是很多 css/js 文件的后缀为*.min.js 或*.min.css 的原因。虽然我们可能没那么多访问量，但是能减小一点资源文件的大小也是对访问速度有那么一点提升的。

我们采用 gulp 代码压缩方式。

**使用方法：**

1. 进入站点根目录下依次执行下面的命令：

```
# 全局安装gulp模块
npm install gulp -g
# 安装各种小功能模块  执行这步的时候，可能会提示权限的问题，最好以管理员模式执行
npm install gulp gulp-htmlclean gulp-htmlmin gulp-minify-css gulp-uglify gulp-imagemin --save
# 额外的功能模块
npm install gulp-debug gulp-clean-css gulp-changed gulp-if gulp-plumber gulp-babel babel-preset-es2015 del @babel/core --save
```

1. 在 Hexo 根目录新建文件 `gulpfile.js`，并复制以下内容到文件中，有中文注释，可以根据自己需求修改。（注意：文件名不能错，一定为 `gulpfile.js`，否则会出错！）

```
var gulp = require("gulp");
var debug = require("gulp-debug");
var cleancss = require("gulp-clean-css"); //css压缩组件
var uglify = require("gulp-uglify"); //js压缩组件
var htmlmin = require("gulp-htmlmin"); //html压缩组件
var htmlclean = require("gulp-htmlclean"); //html清理组件
var imagemin = require("gulp-imagemin"); //图片压缩组件
var changed = require("gulp-changed"); //文件更改校验组件
var gulpif = require("gulp-if"); //任务 帮助调用组件
var plumber = require("gulp-plumber"); //容错组件（发生错误不跳出任务，并报出错误内容）
var isScriptAll = true; //是否处理所有文件，(true|处理所有文件)(false|只处理有更改的文件)
var isDebug = true; //是否调试显示 编译通过的文件
var gulpBabel = require("gulp-babel");
var es2015Preset = require("babel-preset-es2015");
var del = require("del");
var Hexo = require("hexo");
var hexo = new Hexo(process.cwd(), {}); // 初始化一个hexo对象

// 清除public文件夹
gulp.task("clean", function () {
    return del(["public/**/*"]);
});

// 下面几个跟hexo有关的操作，主要通过hexo.call()去执行，注意return
// 创建静态页面 （等同 hexo generate）
gulp.task("generate", function () {
    return hexo.init().then(function () {
        return hexo
            .call("generate", {
                watch: false
            })
            .then(function () {
                return hexo.exit();
            })
            .catch(function (err) {
                return hexo.exit(err);
            });
    });
});

// 启动Hexo服务器
gulp.task("server", function () {
    return hexo
        .init()
        .then(function () {
            return hexo.call("server", {});
        })
        .catch(function (err) {
            console.log(err);
        });
});

// 部署到服务器
gulp.task("deploy", function () {
    return hexo.init().then(function () {
        return hexo
            .call("deploy", {
                watch: false
            })
            .then(function () {
                return hexo.exit();
            })
            .catch(function (err) {
                return hexo.exit(err);
            });
    });
});

// 压缩public目录下的js文件
gulp.task("compressJs", function () {
    return gulp
        .src(["./public/**/*.js", "!./public/libs/**"]) //排除的js
        .pipe(gulpif(!isScriptAll, changed("./public")))
        .pipe(gulpif(isDebug, debug({ title: "Compress JS:" })))
        .pipe(plumber())
        .pipe(
            gulpBabel({
                presets: [es2015Preset] // es5检查机制
            })
        )
        .pipe(uglify()) //调用压缩组件方法uglify(),对合并的文件进行压缩
        .pipe(gulp.dest("./public")); //输出到目标目录
});

// 压缩public目录下的css文件
gulp.task("compressCss", function () {
    var option = {
        rebase: false,
        //advanced: true, //类型：Boolean 默认：true [是否开启高级优化（合并选择器等）]
        compatibility: "ie7" //保留ie7及以下兼容写法 类型：String 默认：''or'*' [启用兼容模式； 'ie7'：IE7兼容模式，'ie8'：IE8兼容模式，'*'：IE9+兼容模式]
        //keepBreaks: true, //类型：Boolean 默认：false [是否保留换行]
        //keepSpecialComments: '*' //保留所有特殊前缀 当你用autoprefixer生成的浏览器前缀，如果不加这个参数，有可能将会删除你的部分前缀
    };
    return gulp
        .src(["./public/**/*.css", "!./public/**/*.min.css"]) //排除的css
        .pipe(gulpif(!isScriptAll, changed("./public")))
        .pipe(gulpif(isDebug, debug({ title: "Compress CSS:" })))
        .pipe(plumber())
        .pipe(cleancss(option))
        .pipe(gulp.dest("./public"));
});

// 压缩public目录下的html文件
gulp.task("compressHtml", function () {
    var cleanOptions = {
        protect: /<\!--%fooTemplate\b.*?%-->/g, //忽略处理
        unprotect: /<script [^>]*\btype="text\/x-handlebars-template"[\s\S]+?<\/script>/gi //特殊处理
    };
    var minOption = {
        collapseWhitespace: true, //压缩HTML
        collapseBooleanAttributes: true, //省略布尔属性的值 <input checked="true"/> ==> <input />
        removeEmptyAttributes: true, //删除所有空格作属性值 <input id="" /> ==> <input />
        removeScriptTypeAttributes: true, //删除<script>的type="text/javascript"
        removeStyleLinkTypeAttributes: true, //删除<style>和<link>的type="text/css"
        removeComments: true, //清除HTML注释
        minifyJS: true, //压缩页面JS
        minifyCSS: true, //压缩页面CSS
        minifyURLs: true //替换页面URL
    };
    return gulp
        .src("./public/**/*.html")
        .pipe(gulpif(isDebug, debug({ title: "Compress HTML:" })))
        .pipe(plumber())
        .pipe(htmlclean(cleanOptions))
        .pipe(htmlmin(minOption))
        .pipe(gulp.dest("./public"));
});

// 压缩 public/medias 目录内图片
gulp.task("compressImage", function () {
    var option = {
        optimizationLevel: 5, //类型：Number 默认：3 取值范围：0-7（优化等级）
        progressive: true, //类型：Boolean 默认：false 无损压缩jpg图片
        interlaced: false, //类型：Boolean 默认：false 隔行扫描gif进行渲染
        multipass: false //类型：Boolean 默认：false 多次优化svg直到完全优化
    };
    return gulp
        .src("./public/medias/**/*.*")
        .pipe(gulpif(!isScriptAll, changed("./public/medias")))
        .pipe(gulpif(isDebug, debug({ title: "Compress Images:" })))
        .pipe(plumber())
        .pipe(imagemin(option))
        .pipe(gulp.dest("./public"));
});
// 执行顺序： 清除public目录 -> 产生原始博客内容 -> 执行压缩混淆 -> 部署到服务器
gulp.task(
    "build",
    gulp.series(
        "clean",
        "generate",
        "compressHtml",
        "compressCss",
        "compressJs",
        "compressImage",
        gulp.parallel("deploy")
    )
);

// 默认任务
gulp.task(
    "default",
    gulp.series(
        "clean",
        "generate",
        gulp.parallel("compressHtml", "compressCss", "compressJs","compressImage")
    )
);
//Gulp4最大的一个改变就是gulp.task函数现在只支持两个参数，分别是任务名和运行任务的函数
```

1. 以后的执行方式有两种：

- 直接在 Hexo 根目录执行 `gulp` 或者 `gulp default` ，这个命令相当于 `hexo cl&&hexo g` 并且再把代码和图片压缩。
- 在 Hexo 根目录执行 `gulp build` ，这个命令与第 1 种相比是：在最后又加了个 `hexo d` ，等于说生成、压缩文件后又帮你自动部署了。

> 值得注意的是：这个加入了图片压缩，如果不想用图片压缩可以把第 154 行的 `"compressImage",` 和第 165 行的 `,"compressImage"` 去掉即可

### 方法二：hexo-neat 插件实现代码压缩

可能以上方法比较复杂，来介绍个简单的，[hexo-neat](https://github.com/rozbo/hexo-neat) 插件也是用来压缩代码的，底层也是通过 gulp 来实现的。

但是这个插件是有 Bug 的：

- 压缩 md 文件会使 markdown 语法的代码块消失
- 会删除全角空格

在博客站点根目录执行安装代码：

```
npm install hexo-neat --save
```

紧接着在站点根目录下的配置文件添加如下代码：

```
neat_enable: true
neat_html:
  enable: true
  exclude:
neat_css:
  enable: true
  exclude:
    - '*.min.css'
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '*.min.js'
```

然后直接 `hexo cl&&hexo g` 就可以了，会自动压缩文件 。

**补充**：为了解决以上 Bug，**对于 matery 主题**（其他主题自行解决）需要将以上默认配置修改为：

```js
#hexo-neat 优化提速插件（去掉HTML、css、js的blank字符）
neat_enable: true
neat_html:
  enable: true
  exclude:
    - '**/*.md'
neat_css:
  enable: true
  exclude:
    - '**/*.min.css'
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/**/instantpage.js'
    - '**/matery.js'
```

## 3. CDN 加速

> 请看我的另一篇博客文章：https://yafine-blog.cn/posts/ee35.html

## 4. 打造稳定快速、高效免费图床

> 请移步另一篇博文：https://yafine-blog.cn/posts/eb3a.html

# 十、SEO 优化

> 请参考这篇博文：https://blog.sky03.cn/posts/42790.html#toc-heading-18

# 十一、部署到 Coding 和码云

> 请参考我的另一篇文章：https://yafine-blog.cn/posts/51fb.html

# 十二、新建文章自动打开本地 Markdown 编辑器

写新文章时，需要控制台执行 `hexo new "文章名字"`，这样就会在`_posts` 下生成一篇新文章，但需要手动打开，挺麻烦，只需要在站点根目录下新建 `scripts` 目录，然后在新建 `auto_open.js`，在文件填入一下内容：

```javascript
var spawn = require('child_process').exec;

// Hexo 2.x 用户复制这段
//hexo.on('new', function(path){
  //spawn('start  "markdown编辑器绝对路径.exe" ' + path);
//});

// Hexo 3 用户复制这段
hexo.on('new', function(data){
  spawn('start  "D:\Program Files\Typora\Typora.exe" ' + data.path);
});
```

其中 `"D:\Program Files\Typorae\Typora.exe"` 是我本地编辑器的路径，只需要改为你本地编辑器的路径即可，然后在执行 `hexo cl && hexo g -d`，部署到 GitHub 即可，以后在发布文章就会自动打开编辑器。

**文章参考来源**

- [matery 主题文档](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)
- [Matery 主题配置豆瓣插件](https://blog.licardo.cn/posts/11199/)
- [Hexo 博客主题个性化](https://www.itrhx.com/2018/08/27/A04-Hexo-blog-topic-personalization/)
- [Hexo 进阶之各种优化](https://blog.sky03.cn/posts/42790.html)
- [hexo 博客美化](https://blog.hvnobug.com/post/hexo-optimize.html)

<iframe name="easyXDM_default268_provider" id="easyXDM_default268_provider" src="https://embed.widgetpack.com/widget/xdm/index.html?xdm_e=https%3A%2F%2Fyafine-blog.cn&amp;xdm_c=default268&amp;xdm_p=1" frameborder="0" style="box-sizing: border-box; outline: none; margin: 0px; padding: 0px; color: rgb(76, 73, 72); font-family: -apple-system, BlinkMacSystemFont, &quot;Segoe UI&quot;, &quot;Helvetica Neue&quot;, Lato, Roboto, &quot;PingFang SC&quot;, &quot;Microsoft YaHei&quot;, sans-serif; font-size: 14px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-thickness: initial; text-decoration-style: initial; text-decoration-color: initial; position: absolute !important; top: -2000px !important; left: 0px !important;"></iframe> 