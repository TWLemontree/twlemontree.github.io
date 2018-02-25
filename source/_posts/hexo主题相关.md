---
title: hexo主题相关
date: 2018-02-23 18:55:42
tags:
---
# 第一步：如果已经有之前的bolg想换主题的话省去这步
```
$ hexo init blog
$ cd blog && npm install
```

# 第二步：添加一些配置文件
```
$ npm install --save hexo-renderer-jade hexo-renderer-scss hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive
```

# 第三步：克隆[下载]主题文件到本地
```
$ git clone https://github.com/littlewin-wang/hexo-theme-casual themes/casual
```

# 第四步：修改配置文件的 theme关键字就好
```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: casual
```
