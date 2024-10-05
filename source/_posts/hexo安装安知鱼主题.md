---
title: hexo安装安知鱼主题
categories: 经典文章
tags: 
  - 知识
  - 前端
  - 美丽
top_img: https://bu.dusays.com/2023/07/24/64bdcbfe96762.webp
date: 2024-10-2 14:32:48
updated: 2024-10-3 14:23:03
cover: https://s2.loli.net/2024/10/03/tg9zYKmc3MNOAFb.png
description: 这是页面描述
keywords: 这是页面关键字
swiper_index: 1
top_group_index: 2
highlight_shrink: # 配置代码框是否展开
top_single_background: https://bu.dusays.com/2023/07/24/64bdcbfe96762.webp
sticky: 1 # 文章置顶
--- 

预览: 👍 [AnZhiYu](https://blog.anheyu.com/) || 🤞 [AnZhiYu](https://index.anheyu.com/)

文档: 📖 [anzhiyu Docs](https://docs.anheyu.com/)

一款基于[hexo-theme-butterfly](https://github.com/jerryc127/hexo-theme-butterfly)修改的主題

# hexo-theme-anzhiyu

![](https://bu.dusays.com/2023/07/24/64bdcbfe96762.webp)
## 💻 安裝

### Git 安裝

在博客根目录里安装最新版【推荐】

```powershell
git clone -b main https://github.com/anzhiyu-c/hexo-theme-anzhiyu.git themes/anzhiyu
```

## ⚙ 应用主题

修改 hexo 配置文件`_config.yml`，把主题改为`anzhiyu`

```
theme: anzhiyu
```

> 如果你没有 pug 以及 stylus 的渲染器，请下载安装： `npm install hexo-renderer-pug hexo-renderer-stylus --save`

## 覆盖配置

覆盖配置可以使`主题配置`放置在 anzhiyu 目录之外，避免在更新主题时丢失自定义的配置。

通过 Npm 安装主题的用户可忽略，其他用户建议学习使用。

- macos/linux
  在博客根目录运行

```bash
cp -rf ./themes/anzhiyu/_config.yml ./_config.anzhiyu.yml
```

- windows
  复制`/themes/anzhiyu/_config.yml`此文件到 hexo 根目录，并重命名为`_config.anzhiyu.yml`

以后如果修改任何主题配置，都只需修改 _config.anzhiyu.yml 的配置即可。

注意：
 - 只要存在于 `_config.anzhiyu.yml` 的配置都是高优先级，修改原 `_config.yml` 是无效的。
 - 每次更新主题可能存在配置变更，请注意更新说明，可能需要手动对 `_config.anzhiyu.yml` 同步修改。
 - 想查看覆盖配置有没有生效，可以通过 `hexo g --debug` 查看命令行输出。
 - 如果想将某些配置覆盖为空，注意不要把主键删掉，不然是无法覆盖的


## 部分功能展示

**沉浸式状态栏**
沉浸阅读。
![沉浸式状态栏](https://upload-bbs.miyoushe.com/upload/2023/09/04/125766904/3bc088e73d07b4dc25fc62fa4cf63261_4205905123525229755.png)

**高低自定义的右键菜单**
高度定制。
![高低自定义的右键菜单](https://upload-bbs.miyoushe.com/upload/2023/09/04/125766904/3f66e33b24a758d53717f6c2c44e50af_1884994888952376370.png)

**AI摘要**
迅速读取文章内容。
![AI摘要](https://upload-bbs.miyoushe.com/upload/2023/09/04/125766904/184e089d64660f5f72390f547c864633_3266246986824356702.png)

**让人眼前一亮的清爽界面**

![让人眼前一亮的清爽界面](https://upload-bbs.miyoushe.com/upload/2023/09/04/125766904/8a16284fd36a9e986d5dbda772f697d0_1356079755877317976.png)

**评论弹幕**

![评论弹幕](https://upload-bbs.miyoushe.com/upload/2023/09/04/125766904/628aef1dbf52b61c0333682e8ee9954e_6905019516821534667.png)

## 贡献者

[![contributors](https://opencollective.com/hexo-theme-anzhiyu/contributors.svg?width=890&button=false)](https://github.com/anzhiyu-c/hexo-theme-anzhiyu/)

主题设计：[@张洪 Heo](https://github.com/zhheo)

文档编写：[@xiaoran](https://github.com/xiaoran)

## 仓库统计

![仓库统计](https://repobeats.axiom.co/api/embed/60fcf455cd02123aebe6249deabf8d48e3debcae.svg "Repobeats analytics image")
