---
title: 'CSAPP17: virtual memory concept'
date: 2020-02-05 19:59:29
tags:
    - 课程
    - 笔记
categories: 
    - CSAPP
    - virtual memory
    - concept
---
<!-- TOC -->

- [1.what is virtual memory](#1what-is-virtual-memory)
- [2.why VM](#2why-vm)
    - [2.1 for cache](#21-for-cache)
        - [2.1.1 overview](#211-overview)
        - [2.1.2 PTE](#212-pte)
    - [2.2 for memory management](#22-for-memory-management)
    - [2.3 for memory protection](#23-for-memory-protection)
- [3 detail VA virtual address](#3-detail-va-virtual-address)
- [4 Summary](#4-summary)

<!-- /TOC -->

# 1. What is virtual memory
cpu访问的都是虚拟内存通过MMU

# 2.Why VM
## 2.1 for cache
### 2.1.1 overview
如下图
![image.png](https://i.loli.net/2020/02/05/yc96l5gPtokXm7O.png)
**注意** ：

+ virtual pages代表着磁盘上的地址 
+ 有些被缓存了 
+ 有些没有还在磁盘上 
+ 有些未分配代表连磁盘上都没

DRAM slower than SRAM 10x

Disk slower 10000x than DRAM

so
* page sizes 4KB to 4MB
* 全相缓存 （尽管要很久搜索）

### 2.1.2 PTE
使用Page table entries 去map VP 到 PP
![image.png](https://i.loli.net/2020/02/05/qPa5F8gHERhOb61.png)

如果CPU给的VP没有page hit 会有page falut 然后和缓存一样替代进去

## 2.2 for memory management
**关键点** 每个进程都有独立的虚拟地址从0开始 似乎都有独立的空间 共享库也得益于此 每个进程似乎
单独拥有一个共享库函数代码
![image.png](https://i.loli.net/2020/02/05/1E94grucImyD2YR.png)

## 2.3 for memory protection
在PTE上对每个PP 有4个bit位
intel 虚拟内存是48位的 剩下的地址有些只能内核去用 高位
![image.png](https://i.loli.net/2020/02/05/IQbFqrRsKTo8mNV.png)

# 3 detail VA virtual address

![image.png](https://i.loli.net/2020/02/05/GnjrcmY6t2JWH9L.png)
![2.png](https://i.loli.net/2020/02/06/qcUxJmFO3vaWLdb.png)
![3.png](https://i.loli.net/2020/02/06/7f5OK1IrH9FkqTd.png)

# 4 Summary
* 程序角度角度 VM
    * 每个进程有独立空间 不会被其他进程打乱
* 系统角度 VM
    * 使得内存 更好缓存 （局部性是关键）
    * 简化了内存管理 
    * 内存保护





