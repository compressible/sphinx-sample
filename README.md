[toc]

# sphinx-sample
A sample sphinx document system

# sphinx-doc简介

sphinx-doc原本用于python语言的文档系统，目前python的在线帮助系统就是用sphinx生成的。sphinx可以将restructured text写就的源文件渲染成html系统或者pdf。

用sphinx构建帮助系统的模式是，用reST文本来写文档，人眼可读。然后用git、svn等工具来管理这些rst文件。写完后，用sphinx-build工具生成html文档或者pdf。

具体的帮助可以上网搜索，几个好用的链接如下：

[使用sphinx制作简洁而又美观的文档](www.ibm.com/developerworks/cn/opensource/os-sphinx-documentation)
[sphinx使用手册](http://zh-sphinx-doc.readthedocs.org/en/latest/tutorial.html)

# 安装以及修改pngmath
由于文档中经常会有公式。如果要处理公式，一个方法就是使用latex。sphinx依赖latex系统来将公式处理成png，然后嵌入到网页中。
##sphinx安装
主要参考[sphinx官方安装文档](http://www.sphinx-doc.org/en/stable/install.html#installing-sphinx-with-pip)
**注意官方文档中没有提把python27/scripts加入到path中，但这是必须的，否则命令行中pip.exe无法启动**
- sphinx安装
    - 安装python2.7以上
    - 安装pip
    - pip install sphinx
    - 将shpinx-build.exe所在的目录加入到path
    - 修改python/site-packages/pngmath.py， 过程如下：

原始文件中DOC_HEAD字符串如下：
```py
DOC_HEAD = r'''
\documentclass[12pt]{article}
\usepackage[utf8x]{inputenc}
\usepackage{amsmath}
\usepackage{amsthm}
\usepackage{amssymb}
\usepackage{amsfonts}
\usepackage{bm}
\pagestyle{empty}
'''
```
改成这样，去掉了哪个utf8x的引用，documentclass也改成了ctexart
```py
##------------------------------------------------- 
DOC_HEAD = r'''
\documentclass{ctexart}
\usepackage{amsmath}
\usepackage{amsthm}
\usepackage{amssymb}
\usepackage{amsfonts}
\usepackage{bm}
\pagestyle{empty}
'''
```


## 安装Ctex
直接下载最新版本安装就行了。无需配置。安装完后启动命令行，敲入latex，如果有反应，说明安装无误。


## 使用
安装之后就可以按照网上的教程，用sphinx-quickstart命令来生成一个简单的帮助系统了。
如果要添加帮助文件，可以写一个rst文件（关于restructured text的介绍请看[这里](http://www.sphinx-doc.org/en/stable/rest.html)和[这里](http://zh-sphinx-doc.readthedocs.org/en/latest/rest.html) )，然后加入到index.rst中的toctree下边。

## 一个示例
我在github上留下了一个例子
```git
git clone https://github.com/XIE-Yuanfeng/sphinx-sample.git
```

