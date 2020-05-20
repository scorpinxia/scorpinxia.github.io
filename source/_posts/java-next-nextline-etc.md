---
title: java-next()&&nextline()etc
date: 2020-04-10 12:01:28
tags:
    - 课堂
    - 实验
categories: 
    - JAVA
    - API
---

>**next（）**:  一定要读取到有效字符后才可以结束输入，对输入有效字符之前遇到的空格键、Tab键或Enter键等结束符，next（）方法会自动将其去掉，只有在输入有效字符之后，next（）方法才将其后输入的空格键、Tab键或Enter键等视为分隔符或结束符。简单地说，next（）查找并返回来自此扫描器的下一个完整标记。完整标记的前后是与分隔模式匹配的输入信息，所以next方法不能得到带空格的字符串。

只有第一个单词


>而**nextLine（）**  方法的结束符只是Enter键，即nextLine（）方法返回的是Enter键之前的所有字符，它是可以得到带空格的字符串的。

nextline（）会自动读取next() nextIn 等 的enter

字节流和字符流 比较好的规范用法： 
```java
1） File file = new File ("hello.txt"); 
FileInputStream in=new FileInputStream (file); 

2） File file = new File ("hello.txt"); 
FileInputStream in=new FileInputStream (file); 
InputStreamReader inReader=new InputStreamReader (in,"UTF-8"); 
BufferedReader bufReader=new BufferedReader(inReader); 

3） File file = new File ("hello.txt"); 
FileReader fileReader=new FileReader(file); 
BufferedReader bufReader=new BufferedReader(fileReader);
```