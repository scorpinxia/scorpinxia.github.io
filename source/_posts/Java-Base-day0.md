---
title: Java Base day0
date: 2020-02-08 09:39:19
tags:
    - 自学
    - 笔记
categories: 
    - JAVA
    - BASE
    - day0
---
<!-- TOC -->

- [1. ***只写模糊的***](#1-只写模糊的)
- [2. 修饰符](#2-修饰符)
    - [2.1. 访问修饰符](#21-访问修饰符)
    - [2.2. 非访问修饰符](#22-非访问修饰符)
- [3. 运算符](#3-运算符)
- [4. 特殊类](#4-特殊类)
- [5. 数组](#5-数组)
- [6. Arrays 类](#6-arrays-类)
- [7. Data Calendar GregorianCalendar](#7-data-calendar-gregoriancalendar)

<!-- /TOC -->

# 1. ***只写模糊的***


# 2. 修饰符
## 2.1. 访问修饰符
* 默认的，也称为default，在同一包内可见，不使用任何修饰符。
接口里的变量都隐式声明为public static final,而接口里的方法默认情况下访问权限为public。

* 受保护的，以protected修饰符指定，对同一包内的类和所有子类可见（只为了子类访问）
    * Protected访问修饰符不能修饰类和接口，方法和成员变量能够声明为protected，但是接口的成员变量和成员方法不能声明为protected。
    * 父类中声明为protected的方法在子类中要么声明为protected，要么声明为public。不能声明为private。

* 私有的，以private修饰符指定，在同一类内可见。
* 共有的，以public修饰符指定，对所有类可见。

## 2.2. 非访问修饰符
* static修饰符，用来创建类方法和类变量(静态方法使用静态变量)
    * static 变量 类变量
    * static 方法 静态方法不能使用类的非静态变量。静态方法从参数列表得到数据，然后计算这些数据。
* final修饰符，用来修饰类、方法和变量，final修饰的类不能够被继承，修饰的方法不能被继承类重新定义，修饰的变量为常量，是不可修改的。
    * final变量：final变量能被显式地初始化并且只能初始化一次。但是final对象里的数据可以被改变。也就是说final对象的引用不能改变，但是里面的值可以改变。
    * final方法:类中的Final方法可以被子类继承，但是不能被子类修改。声明final方法的主要目的是防止该方法的内容被修改。

final修饰符通常和static修饰符一起使用来创建类常量。

* abstract修饰符，用来创建抽象类和抽象方法。
    * 抽象类：抽象类不能用来实例化对象，声明抽象类的唯一目的是为了将来对该类进行扩充 extend。
    * 抽象方法： 抽象方法是一种没有任何实现的方法，该方法的的具体实现由子类提供。
抽象类不能用来实例化对象，声明抽象类的唯一目的是为了将来对该类进行扩充。

* synchronized和volatile修饰符，主要用于线程的编程。

# 3. 运算符
* instanceOf 运算符
该运算符用于操作对象实例，检查该对象是否是一个特定类型（类类型或接口类型）。

* 增强for循环
~~~JAVA
for(int x : numbers ){
         System.out.print( x );
         System.out.print(",");
      }
~~~

# 4. 特殊类
* Number类：在实际开发过程中，我们经常会遇到需要使用对象，而不是内置数据类型的情形。
![](/Java-Base-day0/1.png)
~~~JAVA
public class Test{

   public static void main(String args[]){
      Integer x = 5; // boxes int to an Integer object
      x =  x + 10;   // unboxes the Integer to a int
      System.out.println(x); 
   }
}
~~~

* Math 类:数学操作

* Character 类:我们经常会遇到需要使用对象，而不是内置数据类型的情况，
    * 装拆箱：例如，将一个char类型的参数传递给需要一个Character类型参数时，那么编译器会自动地将char类型参数转换为Character对象。 这种特征称为装箱，反过来称为拆箱。
* String 类:
    * **注意**:String类是不可改变的，所以你一旦创建了String对象，那它的值就无法改变了。 如果需要对字符串做很多修改，那么应该选择使用StringBuffer & StringBuilder 类。
    * StringBuffer & StringBuilder 类。
    由于StringBuilder相较于StringBuffer有速度优势，所以多数情况下建议使用StringBuilder类。然而在应用程序要求线程安全(数据加锁)的情况下，则必须使用StringBuffer类。

# 5. 数组
dataType[] arrayRefVar;   // 首选的方法
~~~JAVA
    dataType[] arrayRefVar = new dataType[arraySize];
~~~

# 6. Arrays 类
java.util.Arrays类能方便地操作数组，它提供的所有方法都是静态的。具有以下功能：
* 给数组赋值：通过fill方法。

* 对数组排序：通过sort方法,按升序。

* 比较数组：通过equals方法比较数组中元素值是否相等。

* 查找数组元素：通过binarySearch方法能对排序好的数组进行二分查找法操作。

# 7. Data Calendar GregorianCalendar