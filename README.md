# node-app-portable

该项目为便携式NodeJS应用模板。

## 懒人包

你可以从该项目的[release](https://github.com/yuri2peter/node-app-portable/releases)中下载到带完整环境的模板，替换为自己的app源码后即可投入使用。
- [懒人包1.1.0](https://github.com/yuri2peter/node-app-portable/releases/tag/1.1.0) 
> “懒”才是推进科技进步的第一生产力。

## 为什么需要它？

便携式NodeJS应用有着免安装、免部署、运行环境稳定等优点。
适用于体量较小，需要随用户携带或经常被拷贝的小型软件。

相较于Electron解决方案而言，它更简单、轻量，免去了Electron的打包工程的步骤和额外的文件。
但由于不自带chromium内核，在使用网页作为APP前端时，做不到像Electron一样提供一个稳定的、类桌面APP的使用体验。

## 软件要求

- win64操作系统
- 无全局依赖包

## 目录结构

```bash
|- node-app-portable # 根目录
  |- app # 应用
    |- data # 数据
    |- html # html静态文件
    |- dist # 源码目录
      |- main.js # 入口文件
  |- node # NodeJS运行环境目录
    |- node.exe # NodeJS二进制文件
  |- start.bat # 项目启动器
```

## start.bat

```bat
@echo off
rem start.bat

rem 修改CMD标题
title 我的应用

rem 记录当前目录
set node_app_runtime_path=%cd%

rem 前往node目录
cd %node_app_runtime_path%/node

rem 临时声明node环境变量
call nodevars.bat

rem 前往app目录
cd %node_app_runtime_path%/app/dist

rem 运行app项目
node main.js

echo "运行完毕"
pause
```

> 1. 该文件如果出现中文字符，一定要按ANSI编码保存。
> 2. 可按实际需求修改文件内容，如：修改CMD标题、修改入口文件路径。

## 关于获取NodeJS

NodeJS运行环境可以从[官网下载](https://nodejs.org/en/download/)，选择`Windows Binary (.zip)`，
将下载得到的zip文件解压缩，并按`目录结构`放置到对应位置即可。

由于NodeJS运行环境文件较大，且由官网持续更新，本项目并不会将其纳入源码库。
