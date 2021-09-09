# **我的Blog搭建(一)**

----------------------------------------

2021年9月9日更新

GitHub 还是需要科学上网才可以访问，大家可以用文中的办法使用GitHub.

----------------------------------------

2021年8月3日更新

最近一段时间的 GitHub 没有被墙，可以直接访问，正好方便大家使用 GitHub Pages 服务建站.

----------------------------------------

作为本blog的首篇文章，就在此记录一下搭建这篇blog的过程，希望可以帮到各位同志！

⚠️注：本篇博客的全部内容均在 **macOS Big Sur** 和 **Ubuntu 18.04 LTS** 系统中测试，并未实际在 Windows 系统下实现，小邵同学建议大家尽量使用 **Linux 系统** 进行博客的搭建工作，相信这会大大减少搭建过程与后期维护过程的工作量. 

## **一、为什么要搭建blog？**

早在大二上（2020学年第一学期）软件工程导论课程中，余阳和潘茂林老师就已经向我们强调过：作为一名“合格的”程序员，学会搭建并将撰写blog作为习惯是十分重要的. 在这门课中我们也学习了搭建blog的方法，并通过该blog上交本门课程的作业.

但是当时搭建的博客并不完备，仅用于作业上交之用途，搭建过程也十分潦草，并不能实际用于博客发布. 
再者，经过设备的更新代换，博客源码未做备份，已经遗失，仅剩网站文件于[gitee](https://gitee.com)，故而弃之. 

今学期（2020学年第二学期）操作系统课程，蒙蔡国扬老师教诲，自觉应该建起本篇博客，培养一下凡事写博客的习惯，于是图得假期之空，于 GitHub 搭建本博客，同时也将搭建过程记录于此. 

## **二、为什么用GitHub而不是Gitee？**

当我进入后者准备搭建时，发现Gitee的Pages服务不能使用了：

![GiteePage](https://mypicbank.oss-cn-beijing.aliyuncs.com/blog/image/things/blog/giteepage.png)

冇计啦，只能翻山越岭上GitHub. （SYSU-SECURE可以访问GitHub还是蛮不错的，~~虽然也经常性地无法访问~~）

PS：GitHub主页的大地球是可以拖动的！超棒！

![GitHubHost](https://mypicbank.oss-cn-beijing.aliyuncs.com/blog/image/things/blog/githubhost.png)

## **三、准备工作**

### **(一)、Markdown基础**

要同人说话，我们学会了中文、英文这些自然语言以与人交流；要写程序，我们则学习了C、C++、Python等编程语言同机器交流；那么要写博客，也需要掌握一门专属于文档撰写的语言. 

这就是：**Markdown**.

{{< details "Markdown简介" close >}}
## Markdown
Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯。它允许人们使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML（或者HTML）文档。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。

*[维基百科：Markdown](https://zh.wikipedia.org/wiki/Markdown)*
{{< /details >}}

关于MarkDown的具体用法，可以参考 [@LearnShare](https://github.com/learnshare) 发布的 [Learning-Markdown](http://xianbai.me/learn-md/index.html). 考虑到本文主要介绍的是博客的搭建方法，关于Markdown的相关知识这里不再赘述. 

### **(二)、确定目标**

有了Markdown这个得力工具，是时候该真正考虑我们搭建博客的目的了. 只有确定了目的，我们才能搭建出最符合我们要求的博客。

一般来说，大学生博客有这样两个用途：

1. 软件工程专业导论的作业上交（~~滑稽~~）
2. 记录自己的学习、生活，整理笔记、报告，为其他人提供帮助

如果只是为了**上交作业**，那么我们只需要最简单的博客搭建基础就好，这一部分我会放在下面的`正式开始`章节. 

如果我们的目的是为了搭建一个**完整、易用、易读且稳定的博客**，我将域名申请与使用、证书申请和图床的搭建等进阶内容放在了下一篇文章`我的Blog搭建之法(二)`中，对于博客的进一步完善有兴趣的同志可作参考. 

下面，就让我们正式开始吧！

## **四、正式开始**

首先，我们不要急于直接实现网络中的博客，我们应该考虑如何首先在本地将博客搭建起来. 

### **(一)、工具选择**

网络上有许多优秀的博客建站软件，例如 Hugo, Hexo, FarBox 等等，大家都可以选用，我的搭建过程选择的是 Hugo，本篇博客的后述内容也将以此为例. 

关于如何选用软件，大家可以参考知乎[@shuibaco](https://www.zhihu.com/people/shuibaco)的回答[FarBox、Jekyll这些博客程序有什么特点？](https://www.zhihu.com/question/21981094/answer/20585133). 

首先，我们打开[Hugo官方网站](https://gohugo.io)，点击`Quick Start`，我们就可以根据提示安装Hugo. 

![hugosite](https://mypicbank.oss-cn-beijing.aliyuncs.com/blog/image/things/blog/hugo.png)

根据各种系统的不同，可以参考如下安装方式：

{{< tabs "uniqueid" >}}
{{< tab "macOS" >}}
### macOS 下安装 Hugo

在 macOS 下，可以直接使用 Homebrew 或 Macports 安装 Hugo
```
brew install hugo
# or
port install hugo
```
{{< /tab >}}
{{< tab "Linux" >}}
### Linux 下安装 Hugo

在 Linux 下（以Ubuntu为例），可以直接使用 apt 安装 Hugo
```
sudo apt-get install hugo
```
{{< /tab >}}
{{< tab "Windows" >}}
### Windows 下安装 Hugo

关于如何在 Windows 下安装 Hugo 我并未尝试，可以参考 Hugo中文站 的引导文章：[在 Windows 上安装 Hugo](https://www.gohugo.org/doc/tutorials/installing-on-windows/). 
{{< /tab >}}
{{< /tabs >}}

安装完成后，我们选定一个目录，使用如下语句即可建立简单的网站：

```
hugo new site [FolderName]
```

网站文件夹就会出现在该目录下. 

### **(二)、在本地建立静态网站**

上文的建站方法固然简单，但我们**并不建议**白手起家直接建站，因为这样需要手动配置许许多多的项目，十分麻烦. 

更好的选择是**套模板**. 

打开 [Hugo官方网站](https://gohugo.io)，选择 `Themes` 页项，我们可以看到许多可用的主题. 

![hugo_themes](https://mypicbank.oss-cn-beijing.aliyuncs.com/blog/image/things/blog/hugo_themes.png)

随心挑选一款主题，这里以Even主题为例. 

![hugo_even](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/hugo_even.png)

我们可以选择点击 Download 按钮下载，也可以选择下方给出的直接使用 git 克隆到本地，由于本文还没有给出 git 的安装和使用方法，这里我们先选择 Download 下载. 

点击 Download 按钮后，会转到该主题的 GitHub 页面，点击绿色的 Code 按钮，我们就可以看到 Download ZIP，下载源码的打包文件. 

![hugo_download](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/hugo_download.png)

{{< hint info >}}
如果无法连接到 GitHub，我们可以将页面网址中：

```
github.com
# 替换为
hub.fastgit.org
```

```
# 示例：
# https://github.com/olOwOlo/hugo-theme-even
# 变更为
# https://hub.fastgit.org/olOwOlo/hugo-theme-even
```
{{< /hint >}}

下载完成，我们在上一步最后建立好的网站文件夹中，找到`theme`，新建一个even文件夹，将压缩包内的文件解压至该文件夹内. 这样，主题就算安装完成了. 

怎么套模板呢？在网页的文件夹中，我们的 Markdown 文件是存储在 `content` 文件夹中的，网页也是按照该文件夹内数组的存储结构组织的. 我们先在之前解压的文件中，一般可以找到一个 `exampleSite` 的文件夹（名称可能不尽一样），将其中所有文件复制并覆盖到网页文件夹根目录. 

```
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── resources
├── static
└── themes
    └── even
        ├── CHANGELOG.md
        ├── LICENSE.md
        ├── Makefile
        ├── README-zh.md
        ├── README.md
        ├── archetypes
        ├── assets
        ├── exampleSite
        │   ├── config.toml
        │   └── content
        ├── i18n
        ├── images
        ├── layouts
        ├── netlify.toml
        ├── resources
        ├── static
        └── theme.toml
```

在网页根目录下打开终端，使用

```
hugo server -D
# 当然，也可以在后方添加 `-p[portNum]` 参数指定端口，例如：
hugo server -D -p1314
# 该命令就将本地网页的端口转移到1314，下方访问时1313端口也相应改为1314.
```

命令即可在本地运行网站预览，我们打开浏览器，输入 [localhost:1313](localhost:1313). 

锵锵！你就可以看到自己搭建的网站了！

![even_site](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/even_site.png)

我们可以通过在 `content` 文件夹中添加 Markdown 文件来为网站添加内容. 
网站头信息可以直接从现有示例文件中复制，根据需要自己修改. 也可以自行探索. 由于各种主题的头信息各不相同，这里不赘述除本主题外其他示例. 

```
# Even主题的部分示例：
---
title: "Example"                        # 标题信息
date: 2017-08-20T21:38:52+08:00         # 创建日期
lastmod: 2017-08-28T21:41:52+08:00      # 最后修改日期
menu: "main"                            # 在菜单栏中的何处显示
weight: 50                              # 字号？
---
```

值得注意的是，只要终端的 Hugo 程序是运行中的，在 `content` 中的任何保存都将实时更新在浏览器网页中以供预览. 超方便！

### **(三)、Git的安装与使用**

Git 是一个分布式版本控制软件，其最主要的用途就是建立本地与远程仓库的通信. 

一般来说，Git 套件是内置于 macOS 系统和一个完整安装的 Linux 发行版中的，我们**无须手动安装**. 
但如果你使用的系统没有内置 Git，那么可以参考下面的方法安装. (由于经我测试的系统中均内置了该软件，以下安装方法并未经过测试，如按以下方法不能安装，请自行百度/谷歌. )

{{< tabs "uniqueid" >}}
{{< tab "macOS" >}}
### macOS 下安装 Git

在 macOS 下，可以直接使用 Homebrew 或 Macports 安装 Git
```
brew install git
# or
port install git
```
{{< /tab >}}
{{< tab "Linux" >}}
### Linux 下安装 Git

在 Linux 下（以Ubuntu为例），可以直接使用 apt 安装 Git
```
sudo apt-get install git
```
{{< /tab >}}
{{< tab "Windows" >}}
### Windows 下安装 Git

关于如何在 Windows 下安装 Git 我并未尝试，各位可以自行下载、安装. 
{{< /tab >}}
{{< /tabs >}}

安装完成，我们只需要经过下面简单的设置就可以使用了. 

```
git config --global user.name "Your Name"
git config --global user.email "exampleuser@example.com"
# 注意：双引号是必要的. 
```

在后续的使用中，我们仅需要掌握如下 Git 操作就可以完成博客的搭建了. 

```
git clone https://github.com/exmaple/example.git    # 将远程仓库克隆到本地
git add .                                           # 将本目录下所有文件更新到暂存区
git commit -m "commit"                              # 为暂存区文件添加注释并准备就绪
git push origin master                              # 将准备就绪的文件推送到远程仓库中
git status                                          # 查看当前暂存区信息
```

Git 准备就绪，让我们进入下一部分. 

### **(四)、远程仓库的创建、克隆和推送**

我们在本地的网站已经成功搭建并可以浏览了，现在我们要做的是想办法把它放到网上去，供任意设备访问. 

打开 [GitHub 官网](https://github.com) （无法打开 GitHub 的话可以使用镜像网站 [hub.fastgit.org](hub.fastgit.org)），注册并登陆. 我们就能在左上角的 Repositories 看到 New 按钮，点击就可以开始创建仓库. 

![new_repositories](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/new_repositories.png)

表中项目可以按照自己的需求选择填写，但需要注意的是，仓库的访问权限需要设置为 **Public(公开)**，在 GitHub 中，私有仓库的 Pages 服务是有偿💰的. 

建好仓库我们就可以在仓库主页看到仓库的 HTTPS 链接，我们将链接复制. 

回到本地的网站文件夹，打开 `config.toml` 文件，作如下修改.

```
# 将 baseURL 项
baseURL = "https://example.com/"
# 修改为
baseURL = "https://YourUserName.github.io/YourRepositoryName/"
# 其中 YourUserName 表示你在 GitHub 注册的用户名，YourRepositoryName 则表示仓库名. 
```

在根目录下打开 Git，输入下面的命令将远程仓库克隆至本地. 

```
git clone [Your link]
# 在演示实例中克隆的命令如下
git clone https://github.com/qhszd/example.git
```

如果创建时没有勾选创建 README 文件选项，Git 会提示正在克隆一个空的仓库，我们不必管他，仓库就在网页根目录中克隆好了.

{{< hint info >}}
这一步作用是直接克隆得到仓库中 `.git` 隐藏文件，以避免使用 Git 手动设置产生的繁琐步骤. 
{{< /hint >}}

将克隆到本地的仓库文件夹更名为 `public`. 

下一步，生成静态网站. 

在网页根目录中打开终端，使用如下命令编译生成静态网站文件. 

```
hugo -D
```

![hugo_as](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/hugo_as.png)

出现这样的提示即编译成功了，生成的文件将会放在上文 `public` 文件夹中. 

我们在 `public` 文件夹下打开 Git，依次输入如下命令. 

```
git add .                   # 注意add后是有一个空格和一个小数点的
                            # 表明将文件夹中所有内容存入暂存区
git commit -m "commit"      # 引号中的内容可以随意修改，为暂存区中的文件添加注释并就绪
git status                  # 可选，可于任意位置输入，查看准备状态信息
git push origin master      # 将就绪的文件推送至远程仓库
```

如果没有出现意外，我们就把 `public` 文件夹中的内容（即编译生成的静态网站源码）推送至了远程仓库. 

![repository_after_push](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/repository_after_push.png)

### **(五)、使用 GitHub Pages 服务的网页浏览实现**

现在，仓库里已经有我们的网页源码了，但是这个仓库也只是一堆源码而已. 我们需要使用 Pages 服务将源码变成网页. 

![github_pages](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/github_pages.png)

在仓库主页中选择 `Settings`，在左侧找到 `Pages` 卡片，点击进入，在 `Source` 的 `branch` 下拉菜单里选择 `master`，点击 `Save` 保存. 

![github_pages_saved](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/github_pages_saved.png)

可以看到已经出现了操作成功的提示，并且给出了网站的地址，打开该地址，你就会发现你的本地网站已经~~神奇的~~出现在了互联网上，可以放心大胆地把链接分享给好朋友们炫耀或者发给助教当作作业上交地址啦！

{{< hint info >}}
如果出现主题格式无法载入、点击链接后 404 的情况. 

请仔细检查 第四步：远程仓库的创建、克隆和推送 的修改 `config.toml` 文件部分. 

检查是否修改及修改后 URL 是否和 GitHub Pages 页面提示的博客网址相同.

检查后继续执行剩余步骤即可.
{{< /hint >}}

![even_finish](https://mypicbank.oss-cn-beijing.aliyuncs.com/uPic/even_finish.png)

<br/>

---

本篇博客的主要内容就结束了，如果觉得本文对你有帮助，何不将它分享给更多需要的同志呢？

如果对后续进一步完善博客感兴趣，同志们可以参考本文的续篇：

[我的Blog搭建之法(二)](./docs/things/blog_2) (未更)

感谢各位同志的耐心阅读，如需转载请注明文章为 `小邵同学(shaozhd_SYSU)` 撰写，并给出本文链接. 

如对文章内容有疑问或有任何建议，欢迎致信我的邮箱：

<qhszd@protonmail.com>

我将非常乐于答复你的来信！