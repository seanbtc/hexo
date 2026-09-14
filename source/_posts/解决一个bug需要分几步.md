---
title: 解决一个bug需要分几步
date: 2022-05-13 11:41:26
tags:
---


闲来无聊，记录一个工作日常，看看解决一个bug需要分几步
#### 1. 问题接收【时间17:06】
收到问题
{% asset_img 1.png This is an example image %}
询问复现方法，排查问题
{% asset_img 2.png This is an example image %}



#### 2.  问题复现【时间17:14】
拿到机器顺利复现
打开调试
通过打印发现是pid 1267的进程启动的音乐
{% asset_img 3.png This is an example image %}
接着adb查看 1267进程
{% asset_img 4.png This is an example image %}
发现1267进程是TW服务
{% asset_img 5.png This is an example image %}



#### 3.  定位代码【时间17:20】
TW服务找到两处启动音乐的地方
{% asset_img 6.png This is an example image %}
分别是0x3c和0x29指令
接着查看指令文档
{% asset_img 7.png This is an example image %}
定位为0x3c启动的音乐
就此找到问题源头



#### 4.  分析原因【时间17:25】 
那为什么左键功能设为启动音乐？
原因出在上个平台的TW服务代码
是该平台直接移植代码过来导致的问题
原因已经无从考察
{% asset_img 8.png This is an example image %}



#### 5.  回复原因【时间17:28】 
{% asset_img 9.png This is an example image %}



#### 6.  提出修改方案 【时间17:35】
{% asset_img 10.png This is an example image %}



#### 7.  修改代码 【时间17:39】
{% asset_img 11.png This is an example image %}

#### 结束 全程33分钟