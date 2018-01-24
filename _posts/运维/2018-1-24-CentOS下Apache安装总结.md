---
layout: post
title: CentOS下Apache安装总结
categories: 运维
description: CentOS下Apache安装总结
keywords: CentOS, Apache, smallclover
---
# CentOS下Apache安装总结

## 环境（Environment）

操作系统：CentOS 6.8
服务器：Apache 2.4.29
其他关键依赖库：apr 1.6.3、apr-util 1.6.1、pcre-8.41

## 命令（Command）

+ 解压命令

命令格式|命令说明|命令参数解释
----------|----------|---------------
tar zxvf [dir1] -C [dir2] |将dir1下的文件解压到dir2指定的目录下|无
rpm -qa [software-name] | 查询指定的软件|无
rpm -e --nodeps [software-full-name]|卸载指定名称的软件|--nodeps：不做软件之间的依赖检查
./configure --prefix=[dir] --with-[lib]|无|--prefix：指定安装目录</br>--with-[lib]：依赖（个人理解）

+ Apache安装

+ 编译安装（make install）

## 问题（problem）

发生时间|**错误内容**|解决方案（个人）|解决方案（网络）|权重
----------|----------|--------------------|-------------------|---------
Apache 安装时|**error:Cannot use an external APR with the bundled APR-util**|对apr-util重新进行编译安装|Google|低
Apache 安装时|**error:Did not find pcre-config script at [dir]**|将pcre2替换为pcre，然后进行编译安装|Google|低
pcre安装时|**error: You need a C++ Compiler for C++ Support**|Google|yum install -y gcc gcc-c++|低
Apache 安装时|**error:pcre-config for libpcre not found**|在./configure 配置时使用--with-pcre=[dir]指定pcre安装目录|重新安装或者第一次安装pcre|低
Apache 安装时|**error:no acceptable C complier found in $PATH**|Google|yum -y install gcc|高
apr-util 安装时|（一部分错误提示）**error:'apr_xml_parser' has no memebr named 'xp'**|Google|yum install expat-devel|低
Apache 安装时|（一部分错误提示）**error:openssl version is too old**|Google|yum install openssl-devel</br>yum update openssl|高