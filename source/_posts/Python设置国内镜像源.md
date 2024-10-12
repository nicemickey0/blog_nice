---
abbrlink: '30363'
ai: 由于 python 自带的源下载速度非常慢，特别是安装一些库的时候，甚至有时会失败。  因此，建议将下载源替换成国内的，下载速度会快很多。总共有两种方法  代码替换
  （推荐使用这一种） 手动替换
categories: []
cover: https://pic3.zhimg.com/v2-332353a013a240048c9b7bb975bad3de_720w.jpg?source=172ae18b
date: '2024-10-12T12:47:20.101640+08:00'
excerpt: python官方各版本下载地址： https://www.python.org/ftp/python/ Python 第三方库国内镜像下载地址 豆瓣  https://pypi.douban.com/simple  阿里云  https://mirrors.aliyun.com/pypi/simple  清华大学  https://pypi.tuna.tsinghua.edu.cn/simple ...
sticky: '9'
tags: []
title: Python设置国内镜像源
top_img: https://pic3.zhimg.com/v2-332353a013a240048c9b7bb975bad3de_720w.jpg?source=172ae18b
updated: '2024-10-12T12:59:13.267+08:00'
---
## python官方各版本下载地址：

[https://www.python.org/ftp/python/](https://www.python.org/ftp/python/)

## Python 第三方库国内镜像下载地址

豆瓣

* [https://pypi.douban.com/simple](https://pypi.douban.com/simple)

阿里云

* [https://mirrors.aliyun.com/pypi/simple](https://mirrors.aliyun.com/pypi/simple)

清华大学

* [https://pypi.tuna.tsinghua.edu.cn/simple](https://pypi.tuna.tsinghua.edu.cn/simple)

中国科技大学

* [https://pypi.mirrors.ustc.edu.cn/simple](https://pypi.mirrors.ustc.edu.cn/simple)

### 使用方法为在 pip 命令后加 -i URL 方法，以从阿里云下载 pandas 库为例：

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pandas

pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple pandas
```

### 永久修改，一劳永逸：#

Linux下，修改 \~/.pip/pip.conf (没有就创建一个文件夹及文件。文件夹要加“.”，表示是隐藏文件夹)

内容如下：

```ini
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host=mirrors.aliyun.com
```

windows下，直接在 %userprofile% 目录中创建一个 pip目录，再新建文件 pip.ini。（例如：C:\\Users\\WQP\\pip\\pip.ini）内容同上。
