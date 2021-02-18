---
title: Github Faster Download in China
date: 2020-10-06 21:39:44
tags: git
---
method about how to download faster on Github.
<!--more-->

## gihub 访问
   在中国访问github非常慢。通过在 www.ipaddress.com 中查询 github.com 的IP地址。修改/ect/hosts下的host映射，省去DNS服务器步骤。

## git clone 下载
### 下载加速
   虽然上述修改host对git clone也有效果，但充其量只是从2KB/s上升至20KB/s没有质的提升。更好的方法是通过第三方的镜像网站。这里使用github.com.cnpmjs.org的镜像网站。
例如：
```
git clone https://github.com/repository
```
改成：
```
git clone https://github.com.cnpmjs.org/repository
```
速度直接从2KB/s上升至2MB/s！比原先提升将近1k倍。

### 减少项目不必要文件
   作为辅助，可以使用浅拷贝减小项目大小。尤其是在大项目中，浅拷贝的使用是十分有效的。
> 浅拷贝：在clone时，只获得最新的一层commit。

   由此看出如果commit比较多所需要的下在时间也会变长。我们通过加入--depth=1来执行浅拷贝：
```
git clone --depth=1 https://github.com/repository
```
如果需要最近两次commit来开发，可以写`--depth=2`，以此类推