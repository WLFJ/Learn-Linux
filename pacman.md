# Pacman  使用指南

## 安装软件

-S 同步功能 y 获取更新 y强制刷新 u安装更新软件包

-Ss 搜索软件，通过名字或这简介，支持正则表达式

## 删除软件安装包（缓存）

-Sc

## 删除软件

-R 直接删除软件，不删除相关依赖 n删除全局配置文件 s删除依赖

## 查询本地安装软件

-Q e查看用户自己安装的软件 q隐藏版本号 s查询本地安装的软件

## 灵活使用

### 批量删除不再依赖的软件包？

`sudo pacman -R $(pacman -Qdtq)`

(在fish中不使用$)

