---
title: CSAPP26-thread-level-Parallelism
date: 2020-02-16 09:55:20
tags:
    - 课程
    - 笔记
categories: 
    - CSAPP
    - Parallelism
---
# 多核和超线程
![](CSAPP26-thread-level-Parallelism/1.png)
现在的计算机都是并行流水线
![](CSAPP26-thread-level-Parallelism/2.png)
超线程(hpyerthreading)意味着在单核的情况下多个线程同时走


# 并行加法
目标：加0到n-1
想法：使用多个进程用互斥量来加globel sum
结果
![](CSAPP26-thread-level-Parallelism/3.png)

改进：信号同步是很慢的，每个进程单独使用数组不同步,主进程等待所有进程结束然后相加
结果:
![](CSAPP26-thread-level-Parallelism/4.png)

再改进：不用每次改数组，而是用局部变量（寄存器)累加，最后给数组
![](CSAPP26-thread-level-Parallelism/5.png)
![](CSAPP26-thread-level-Parallelism/6.png)
可以看到这里超线程并没有帮到我们（本身就在很好的使用寄存器)
**但是实际中的程序复杂的多，并不是这么简单利用**

# Amdahl’s Law（阿姆达尔定律）
研究一部分性能提升（使用并行)对总体性能的影响
![](CSAPP26-thread-level-Parallelism/7.png)

# 快速排序（利用并行）
原来的 排左 排右
![](CSAPP26-thread-level-Parallelism/8.png)

用线程递归  直到够小 
![](CSAPP26-thread-level-Parallelism/9.png)
还要注意的是碎片太小 就不够并行性 太大就线程开销就太大了
![](CSAPP26-thread-level-Parallelism/10.png)

# 线程连续性法则（Thread consistency）
决定了不会出现1，100  或者100,1
![](CSAPP26-thread-level-Parallelism/11.png)
但是如果有不耦合的缓存，就可能出现。
![](CSAPP26-thread-level-Parallelism/12.png)

## Snoopy Cache(史努比缓存)
对缓存进行了三种标记
![](CSAPP26-thread-level-Parallelism/13.png)
![](CSAPP26-thread-level-Parallelism/14.png)