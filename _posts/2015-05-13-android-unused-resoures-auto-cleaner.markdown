---
layout: post 
category: "Android" 
title:  "关于Android项目清理的实践" 
tags: [Android]
---
### 无用资源清理的方法
* 1.使用AndroidUnusedResouces库，未成功放弃了
* 2.使用lint加lintAutoCleaner，效果还好，但是还不够智能。

### 原版步骤：
* 1.启动Android studio，使用lint模式运行目标Android项目
* 2.自动生成lint-result.xml文件，目录：项目路径\build\outputs\lint-result.xml
* 3.配置白名单whitelist.txt，过滤掉不需要删去的文件
* 4.点击file文件下的autoCleaner.exe,选择lint-result.xml及其选择要清理的资源
* 5.确定清理，被清理掉的文件备份到file\copyfile\项目原路径下，被清理掉的文件信息以对象形式保存在outResObj.txt

### 我的操作步骤：
* 1.将lintAutoCleaner放到项目所在的父目录
* 2.使用sdk中tools下的lint工具生成xml文件，命令如下：lint --config lint.xml --fullpath --xml unused.xml 项目根目录(也可生成txt ">unused.txt")
* 3.lint.xml检查规则的定制，Properties-》Android lint Prerences可自己定制，会在项目根目录生成lint.xml
* 4.使用autoCleaner.exe清理，我没有发现清理的文件被备份。。。坑爹（后来我发现有的会备份，有待自己去研究了）。

[资源包下载路径](http://download.csdn.net/detail/rjliulei/8650943)