---
title: 'CSAPP18: virtual memory(real system)'
date: 2020-02-07 09:07:28
tags:
    - 课程
    - 笔记
categories: 
    - CSAPP
    - virtual memory
    - real system
---
<!-- TOC -->

- [1 symple system memory address translastion](#1-symple-system-memory-address-translastion)
- [2 i7 linux memory system](#2-i7-linux-memory-system)
- [3 memory mapping](#3-memory-mapping)

<!-- /TOC -->

# 1 symple system memory address translastion
![](/CSAPP18-virtual-memory-real-system/1.png)
步骤如下
1. 得到一个VA 拆解成VPN VPO
2. VPN=TLBI+TLBT 去look看TLBI上hit了没
3. hit 直接得到PPN 然后VPO和PPO是完全相等的
4. 再去Cache里面找  CI 找 然后匹配tag 然后取出CO位置

![](/CSAPP18-virtual-memory-real-system/1.png)
步骤如下
1. 得到一个VA 拆解成VPN VPO
2. VPN=TLBI+TLBT 去look看TLBI上hit了没
3. 没有hit 得去PTE里面找了 发现在里面 没有page falut 
4. 得到了PPN 
4. 再去Cache里面找  CI 找 然后匹配tag 然后取出CO位置

# 2 i7 linux memory system
![](/CSAPP18-virtual-memory-real-system/3.png)
Key  Point
* L1:4 cycle L2:10 cycle L3: 40-50 cyclce ps:L3是四核共用
* 有d-cache 和i-cache d-TLB 和 i-TLB
* 为什么不把L2 L1 合并原因有: d i占比不一定一样 还有就是缓存的限制大小 
具体流程
![](/CSAPP18-virtual-memory-real-system/4.png)

技巧可以VPO=PPO=CI+CO先找到对应的位置在等tag（translation）匹配
![](/CSAPP18-virtual-memory-real-system/6.png)

linux 把VM看做一个链表类似 
![](/CSAPP18-virtual-memory-real-system/8.png)

# 3 memory mapping

两种分享方式
1. 共享地址
![](/CSAPP18-virtual-memory-real-system/9.png)

2. 私密的共享（such as fork and execve)
![](/CSAPP18-virtual-memory-real-system/11.png)
