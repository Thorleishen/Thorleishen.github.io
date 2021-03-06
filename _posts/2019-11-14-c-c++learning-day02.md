---
layout: post
title: 'c/c++学习第二天（数据类型）'
categories: c/c++
tags: c/c++ linux
author: thorleishen
---

* content
{:toc}
## 学习路线

c语言的数据类型之基本数据类型



## c语言的基本数据类型
int整型

字符型

浮点型

标识符的命名规则：
1. 数字、字母、下划线
2. 不能以数字开头
3. 见名知意
4. 不能和其他标识符重复定义
5. 不能和关键字重命名
6. 标识符区分大小写

常量的定义：
const 数据类型 常量名 = value
\#define 常量名 值【宏定义】
注：
1. const定义的常量修改是不安全的
2. 通过#define定义的常量是根据值来匹配数据类型的

进制在程序中的打印：
1. 二进制在c语言中不能表示; %d
2. 八进制 int b = 010; %o
3. 十六进制 int c = 0x10; %x %X

一个有符号的整数分为两个部分：
1. 一部分为符号位，0代表正数，1代表负数；
2. 另一部分为数值。

注：
1. 64位机器可以运行32位的程序，反之不行；由于32位中的总线宽为32位；
2. cpu为32位，总线为32位，该系统为32位；cpu位64位，总线为32位，该系统为32位。

正数的原码、反码、补码相同；
负数的原码为正数的原码最高改为1；
负数的反码为原码取反，最高位不变；
负数的补码为反码加1；
溢出：在数据进行操作的时候可能会导致超出数据类型大小，会向前进1，多于原始数据类型大小，会被系统自动舍弃，保留后面开始的数据类型大小的位数。

有符号数和无符号数区别：
1. 有符号：最高位为符号位
2. 无符号：数据类型只包含数字位部分



## 总结

在数据类型这张节需要注意以下几点：
1. 原码、反码、补码之间的关系，及数值的运算
2. 数值溢出计算
3. 宏定义（#defind）
4. 十进制、二进制、八进制以及十六进制之间的转换