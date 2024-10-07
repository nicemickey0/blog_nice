---
abbrlink: 好
categories:
    - 博客相关
cover: https://s2.loli.net/2024/10/06/IE8YL5bpUlZmSK3.jpg
date: '2024-10-07T00:42:12.206670+08:00'
excerpt: Qexo图床配置 从 2.0.0 开始, Qexo 支持了模块化的图床接入方法, 先前的 S3、FTP、Custom 文档合并至此 远程 API​ Qexo 提供了自定义 API 图床功能, 在配置完成图床设置后即可在文章/页面编辑界面上传图片 API 地址​ 图床图片上传的 API https://7bu.top/api/upload  POST 参数名​ 图床图片上传 API 参数中图片文件的...
tags:
    - 博客
title: Qexo图床配置
updated: '2024-10-07T00:52:00.619+08:00'
ai : 
  - 文档主要介绍了 Qexo 图床从 2.0.0 版本开始支持的模块化图床接入方法，包括远程 API、S3 协议、FTP 协议和 Github（不建议）四种方式的配置。每种方式都详细说明了所需的参数设置，如 API 地址、POST 参数名、JSON 路径、自定义请求头、自定义 BODY、自定义前缀、删除 API、应用密钥 ID、应用密钥、存储桶名、边缘节点、FTP 主机、FTP 端口、用户名、密码、Github 仓库、项目分支、Github 密钥等，以及保存路径和自定义域名的设置规则，并给出了关键词及其意义和示例。
---
# Qexo图床配置

从 2.0.0 开始, Qexo 支持了模块化的图床接入方法, 先前的 S3、FTP、Custom 文档合并至此


## 远程 API[](https://www.oplog.cn/qexo/configs/upload.html#%E8%BF%9C%E7%A8%8B-api)

Qexo 提供了自定义 API 图床功能, 在配置完成图床设置后即可在文章/页面编辑界面上传图片

### API 地址[](https://www.oplog.cn/qexo/configs/upload.html#api-%E5%9C%B0%E5%9D%80)

图床图片上传的 API

```
https://7bu.top/api/upload
```

### POST 参数名[](https://www.oplog.cn/qexo/configs/upload.html#post-%E5%8F%82%E6%95%B0%E5%90%8D)

图床图片上传 API 参数中图片文件的参数名

```
image
```

[![](https://s2.loli.net/2024/07/19/9IJXAxzrCcKvs3Y.png)](https://s2.loli.net/2024/07/19/9IJXAxzrCcKvs3Y.png)

### JSON 路径[](https://www.oplog.cn/qexo/configs/upload.html#json-%E8%B7%AF%E5%BE%84)

图床 API 返回数据中 **图片 URL** 所在的路径, 若为整个返回值请留空 示例：

```
data.url
```

### 自定义请求头[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E8%AF%B7%E6%B1%82%E5%A4%B4)

POST 请求时附带的请求头, 需要标准 JSON 格式, 若不需要请留空

**json**

```
{"key":"value"}
```

### 自定义 BODY[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89-body)

POST 请求时额外的请求主体, 需要标准 JSON 格式, 若不需要请留空

**json**

```
{"key":"value"}
```

### 自定义前缀[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%89%8D%E7%BC%80)

返回 URL 所需要添加的前缀, 若不需要请留空

```
some_text_or_url
```

### 删除 API[](https://www.oplog.cn/qexo/configs/upload.html#%E5%88%A0%E9%99%A4-api)

图床 API 返回数据中 **删除图片 URL** 所在的路径, 若为不存在请留空 示例：

```
data.delete_url
```

## S3协议[](https://www.oplog.cn/qexo/configs/upload.html#s3%E5%8D%8F%E8%AE%AE)

Qexo 为 S3 存储桶提供了支持, 在配置完成 S3 存储桶设置后即可在文章/页面编辑界面上传图片

### 应用密钥 ID[](https://www.oplog.cn/qexo/configs/upload.html#%E5%BA%94%E7%94%A8%E5%AF%86%E9%92%A5-id)

S3 应用程序的 Access Key ID

```
1000000000000080000000000
```

### 应用密钥[](https://www.oplog.cn/qexo/configs/upload.html#%E5%BA%94%E7%94%A8%E5%AF%86%E9%92%A5)

S3 应用程序的 Access Key

```
S12******************6129E
```

### 存储桶名[](https://www.oplog.cn/qexo/configs/upload.html#%E5%AD%98%E5%82%A8%E6%A1%B6%E5%90%8D)

S3 Bucket 名称

```
Bucket
```

### 边缘节点[](https://www.oplog.cn/qexo/configs/upload.html#%E8%BE%B9%E7%BC%98%E8%8A%82%E7%82%B9)

S3 Endpoint

```
https://s3.us-west-002.backblazeb2.com
```

### 保存路径[](https://www.oplog.cn/qexo/configs/upload.html#%E4%BF%9D%E5%AD%98%E8%B7%AF%E5%BE%84)

文件上传后保存的路径 包含文件名


| 关键词       | 意义            | 示例                             |
| ------------ | --------------- | -------------------------------- |
| *{year}*     | 当前年份        | 21                               |
| *{month}*    | 当前月份        | 1                                |
| *{day}*      | 当前日份        | 2                                |
| *{YEAR}*     | 当前年份        | 2021                             |
| *{MONTH}*    | 当前月份        | 01                               |
| *{DAY}*      | 当前日份        | 02                               |
| *{filename}* | 无后缀的文件名  | image                            |
| *{time}*     | 时间戳          | 1640186955.4339228               |
| *{extName}*  | 文件后缀名      | png                              |
| *{md5}*      | 图片的 Md5-Hash | 0c8bfe6821a91c3d96b25e2ea2dcf827 |

```
Qexo/{year}/{month}/{md5}.{extName}
```

### 自定义域名[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9F%9F%E5%90%8D)

返回文件链接的 URL 最终返回的链接, 支持关键词同上

```
https://file.example.com/file/CDN/Qexo/{year}/{month}/{md5}.{extName}
```

## FTP 协议[](https://www.oplog.cn/qexo/configs/upload.html#ftp-%E5%8D%8F%E8%AE%AE)

你可以借助这个模块将图片上传至远程 FTP 位置

### FTP 主机[](https://www.oplog.cn/qexo/configs/upload.html#ftp-%E4%B8%BB%E6%9C%BA)

所连接的 FTP 主机

```
127.0.0.1
```

### FTP 端口[](https://www.oplog.cn/qexo/configs/upload.html#ftp-%E7%AB%AF%E5%8F%A3)

FTP 连接端口 通常为 **21**

```
21
```

### 用户名[](https://www.oplog.cn/qexo/configs/upload.html#%E7%94%A8%E6%88%B7%E5%90%8D)

FTP 登录用户名

```
username
```

### 密码[](https://www.oplog.cn/qexo/configs/upload.html#%E5%AF%86%E7%A0%81)

FTP 登录密码

```
password
```

### 保存路径[](https://www.oplog.cn/qexo/configs/upload.html#%E4%BF%9D%E5%AD%98%E8%B7%AF%E5%BE%84-1)

文件上传后保存的路径 包含文件名


| 关键词       | 意义            | 示例                             |
| ------------ | --------------- | -------------------------------- |
| *{year}*     | 当前年份        | 21                               |
| *{month}*    | 当前月份        | 1                                |
| *{day}*      | 当前日份        | 2                                |
| *{YEAR}*     | 当前年份        | 2021                             |
| *{MONTH}*    | 当前月份        | 01                               |
| *{DAY}*      | 当前日份        | 02                               |
| *{filename}* | 无后缀的文件名  | image                            |
| *{time}*     | 时间戳          | 1640186955.4339228               |
| *{md5}*      | 图片的 Md5-Hash | 0c8bfe6821a91c3d96b25e2ea2dcf827 |
| *{extName}*  | 文件后缀名      | png                              |

```
/Qexo/{year}/{month}/{time}.{extName}
```

### 自定义域名[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9F%9F%E5%90%8D-1)

返回文件链接的 URL 最终返回的链接, 支持关键词同上

```
https://file.example.com/file/CDN/Qexo/{year}/{month}/{time}.{extName}
```

## Github[](https://www.oplog.cn/qexo/configs/upload.html#github)

(不建议)将图片上传至 Github 仓库以借助 Github Action 进行进一步操作

### Github仓库[](https://www.oplog.cn/qexo/configs/upload.html#github%E4%BB%93%E5%BA%93)

您图片上传到的仓库

```
username/repo
```

### 项目分支[](https://www.oplog.cn/qexo/configs/upload.html#%E9%A1%B9%E7%9B%AE%E5%88%86%E6%94%AF)

您图片需要上传仓库的分支

```
master
```

### Github 密钥[](https://www.oplog.cn/qexo/configs/upload.html#github-%E5%AF%86%E9%92%A5)

于 [Github 设置](https://github.com/settings/tokens) 生成的 Token 需要 Repo 下的至少读取和写入权限 *不建议给出所有权限*

```
wrq_P8sYPlYA9fjMlOPEYSKA84xxxxxxxxxxxxxx
```

### 保存路径[](https://www.oplog.cn/qexo/configs/upload.html#%E4%BF%9D%E5%AD%98%E8%B7%AF%E5%BE%84-2)

文件上传后保存的路径 包含文件名


| 关键词       | 意义           | 示例                             |
| ------------ | -------------- | -------------------------------- |
| *{year}*     | 当前年份       | 21                               |
| *{month}*    | 当前月份       | 1                                |
| *{day}*      | 当前日份       | 2                                |
| *{YEAR}*     | 当前年份       | 2021                             |
| *{MONTH}*    | 当前月份       | 01                               |
| *{DAY}*      | 当前日份       | 02                               |
| *{filename}* | 无后缀的文件名 | image                            |
| *{time}*     | 时间戳         | 1640186955.4339228               |
| *{md5}*      | 文件 MD5-Hash  | 0c8bfe6821a91c3d96b25e2ea2dcf827 |
| *{extName}*  | 文件后缀名     | png                              |

```
Qexo/{year}/{month}/{filename}_{md5}.{extName}
```

### 自定义域名[](https://www.oplog.cn/qexo/configs/upload.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9F%9F%E5%90%8D-2)

返回文件链接的 URL 最终返回的链接, 支持关键词同上

```
https://github.com/username/repo/raw/master/Qexo/{year}/{month}/{filename}_{md5}.{ex
```
