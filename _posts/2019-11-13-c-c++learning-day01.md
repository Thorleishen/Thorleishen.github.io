---
layout: post
title: ''c/c++学习第一天'
categories: c/c++
tags: c/c++ linux
author: thorleishen
---

* content
{:toc}
## 背景

一心从事c/c++方向的第一天学习

## 学习内容

c程序编译步骤：
1. 预处理：头文件展开、宏定义展开、条件编译等，删除注释，这一步并不会检查语法；
2. 编译：检查语法，将预处理文件编译成汇编文件；
3. 汇编：将汇编文件生成目标文件（二进制文件）；
4. 链接：c语言程序需要依赖各种库，编译之后需要需要把库链接到最终可执行程序上。

c程序被编译之后存储在外存储器（硬盘、U盘）上，内部存储被划分（编译文件）

内存四区（执行过程）：
1. 代码区
2. 数据区
3. 栈区
4. 堆区

中央处理器（cpu）：
1. 运算器
2. 控制器
3. 寄存器：是cpu内部最基础的存储单元

ldd命令：查看文件链接库

## 总结

熟悉c编译过程，了解简单的汇编语言以及cpu中的内部结构