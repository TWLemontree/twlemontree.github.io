---
title: 将hexo博客备份至GitHub
date: 2018-02-25 11:11:34
tags: hexo
---
## 前言
使用Hexo在github搭建的博客，github上仅仅只保存有Hexo生成的静态网页文件，而没有我们创建修改过的Hexo源文件。当我们换一台电脑，或者重装了系统时，我们就无法用我们之前创建的Hexo源文件修改博客了。

## 备份
1. 在github上创建新的仓库 Username.github.io，这个仓库将存储你的Hexo源文件和Hexo生成的博客静态页面。如果您之前有该重名文件（比如您之前用Hexo搭建过博客），请将其重命名或者删除（我们将重新生成博客并上传，抛弃您之前搭建的博客）；
2. 创建两个分支：master 和 hexo （其中master分支用于存储静态网页文件，hexo用于存储hexo源文件）；
3. 设置hexo为默认分支；
4. 将刚刚创建的新仓库 ```clone``` 至本地，将之前你创建过的hexo源文件中的```_config.yml```、```themes/```、```source/```、```scaffolds/```、```package.json```和```.gitignore```复制至你刚刚克隆至本地的文件夹内；
5. 将themes/next/（如果你下载并使用了其他hexo主题）中的```.git/```删除，否则将无法push主题文件夹；
6. 在你克隆至本地的Username.github.io文件夹中执行```npm install```和```npm install hexo-deployer-git```（这里可以看一看分支是不是hexo）
7. 执行```git add```、```git commit -m ""```、```git push origin hexo```来提交hexo网站源文件;
8. 执行```hexo g -d```将生成的静态网页部署至GitHub上。
这样，Username.github.io仓库就有了master分支和hexo分支，分别保存静态网页和源文件。

## 修改
在本地对博客修改（包括修改主题样式、发布新文章等）后：
1. 依次执行```git add```、```git commit -m ""```和```git push origin hexo```来提交hexo网站源文件；
2. 执行```hexo g -d```将生成的静态网页部署至GitHub上。

## 恢复
重装电脑后，或者想在其它电脑上修改博客：
1. 安装git；
2. 安装Node.js；
3. 克隆远程仓科至本地；
4. 在文件夹内执行以下命令```npm install hexo-cli -g```、```npm install```、```npm install hexo-deployer-git```。

## 参考文章
1. [GitHub创建新分支](http://blog.csdn.net/top_code/article/details/51931916)
2. [ Hexo 博客备份](https://blog.itswincer.com/posts/7efd2818/)
