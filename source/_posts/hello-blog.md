---
title: Hexo + Next + GitHub 搭建博客
tags:
  - Blog
  - Hexo
  - GitHub
categories:
  - Hexo
---

&emsp;&emsp;秃头一族怎么能没有自己的 Blog 呢? 本想着自己买服务器与域名,使用 Node React 纯手撸 ,奈何钱包与时间它不允许, 所以就有了本站与这篇文章了.

> 相关链接

[Hexo 文档](https://hexo.io/)
[NexT 文档](https://theme-next.iissnan.com/)
[参考大神博客](https://cuiqingcai.com/7625.html)

> 一.全局安装 Hexo

```bash
  npm install -g hexo-cli
```

> 二.创建博客项目

```bash
  # 使用终端进入准备存放博客项目的目录 输入以下命令
  hexo init hexo-blog # hexo-blog 自己取名即可
  cd hexo-blog
  npm install
```

> 三.本地预览博客

```bash
  hexo server # 使用浏览器开大 http://localhost:4000 即可
```

> 四.打包部署

```bash
$ hexo d -g
```
