# Sphinx教程

Sphinx 是一个基于 Python 的文档生成项目。最早只是用来生成 Python 的项目文档，使用 reStructuredText 格式。但随着 Sphinx 项目的逐渐完善，目前已发展成为一个大众可用的框架，很多非 Python 的项目也采用 Sphinx 作为文档写作工具，甚至完全可以用 Sphinx 来写书。


Sphinx 是 Python 社区编写和使用的文档构建工具，由 Georg Brandl 在 BSD 许可证下开发，它可以令人轻松的撰写出清晰且优美的文档。除了天然支持 Python 项目以外，Sphinx 对 C/C++ 项目也有很好的支持，并在不断增加对其它开发语言的支持，有需要的小伙伴可以持续关注。


Sphinx 网站：[http://**sphinx-doc.org/**](https://link.zhihu.com/?target=http%3A//sphinx-doc.org/)

Sphinx 使用手册：https://zh-sphinx-doc.readthedocs.io/en/latest/index.html


## 环境搭建

1.需要安装Python3、Git、Make等基础软件

Window在官网下载安装包安装。

Linux系统可参考：

```
 sudo apt install git
 sudo apt install make
 sudo apt install python3
 sudo apt install python3-pip 
```


2.安装Sphinx及其依赖

```
 pip3 install -U Sphinx
```



3.安装Sphinx插件

```
pip3 install sphinx-autobuild
pip3 install sphinx_rtd_theme
pip3 install recommonmark
pip3 install sphinx_markdown_tables
```



## 快速开始

1.创建项目

```
sphinx-quickstart
```

输入项目框架基本信息

* 项目名称
* 作者名称

* 项目版本
* 项目语种

生成项目文件，目录结构如下

```
Makefile：可以看作是一个包含指令的文件，在使用 make 命令时，可以使用这些指令来构建文档输出。
build：生成的文件的输出目录。
make.bat：Windows 用命令行。
_static：静态文件目录，比如图片等。
_templates：模板目录。
conf.py：存放 Sphinx 的配置，包括在 sphinx-quickstart 时选中的那些值，可以自行定义其他的值。
index.rst：文档项目起始文件。
```


2.执行Make操作，生成html文件

在项目文件夹下执行该命令

```
make html
```

在 build/html 目录生成 html 相关文件


3.启动HTTP服务

```text
 sphinx-autobuild source build/html
```

默认启动 8000 端口，在浏览器输入 [http://127.0.0.1:8000](https://link.zhihu.com/?target=http%3A//127.0.0.1%3A8000/)，可看的文档首页。


4.修改主题

打开 conf.py 文件，找到 html_theme 字段，修改自己喜欢的主题。

```text
html_theme = 'alabaster'
html_theme = 'classic'
html_theme = 'sphinx_rtd_theme'
```


5.修改文档目录结构

简单结构

```
一级标题
=================================

.. toctree::
   :maxdepth: 2
#目录名称
   :caption: Contents:

   about
```


更复杂的结构

```
A
 ├── A1.rst
 ├── B1
 │   └── B1.rst
 ├── B2
 │   └── B2.rst
 ├── B3
 │   └── B3.rst
 └── B4
     └── B4.rst
```

```text
A
 =================================
 
 .. toctree::
    :maxdepth: 2
 
    B1/B1
    B2/B2
    B3/B3
    B4/B4
 
```


6.上传Github

在个人Github新建该项目仓库

在本地 diary 目录中添加 README.md 和 .gitignore 文件，在 .gitignore 文件中写入下面一行。

```text
 build/
```

表示不跟踪 build 目录，因为我们后面将使用 Read the Docs 进行文档的构建和托管。

接着依次执行如下命令即可。

```text
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:luhuadong/diary.git
git push -u origin main
```


6.网页托管

在 Read the Docs 网站 [https://**readthedocs.org/**](https://link.zhihu.com/?target=https%3A//readthedocs.org/) 注册，并绑定 GitHub 账户。点击“Import a Project”导入项目，输入项目名称和仓库地址即可。
