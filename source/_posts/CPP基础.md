---
title: C++基础
date: 2016-03-25 10:56:58
categories: C++
description: C++基础
tags: 
- C++
- 面试

---

# C++类相关要点

![C++基础](http://img005.hc360.cn/g7/M03/9C/A9/wKhQtFNE6VeEaALDAAAAAJHYSdw491.jpg)

## 指针常量和常量指针

C++中“指针常量”和“常量指针”这两个概念往往很令人困惑，有时候一时理解下来，过一段时间也会忘记。但抛去概念名字，只看代码，却可以发现有明显的规律。

```c++
int *p;                 // int指针
int * const p;          // int指针常量，指针指向的地址为常量
const int *p;           // int常量指针，指针指向的int变量为常量
int const *p;           // int常量指针，指针指向的int变量为常量
const int * const p;    // 两者均是
int const * const p;    // 两者均是
```

其实只需要记住，**星号之后的const修饰的是指针本身，星号之前的const修饰的是指向的类型**。

而对于“常量指针”和“指针常量”的概念名来说，可以采用从右至左读的方式，即：

* “常量指针”是指向常量的指针，const在*前面
* “指针常量”是指指针本身是常量，*在const前面

## const的具体实现

C++ 只规定了编译器的行为：C++ 要求编译器拒绝所有直接修改 const 对象的情况，所以具体实现是和编译器相关的。

* C和C++中const的具体实现是和编译器相关的
* 一般进行的是在编译期间的检查，检查有无试图修改const的变量
* 有的编译器可能将*const int i = 10*中的i在代码中替换为10
* 有的编译器会将const变量编译在read-only的内存中

## new 和 malloc() 的区别

两者都是进行动态内存分配的函数，具体有以下区别：

* new是操作符而malloc()是标准库函数
* 两者在C++都可使用，而C只能使用malloc()（所以在C++中没有被淘汰）
* new与delete对应，malloc()和free()对应
* new自动返回带有类型的指针，malloc()需要强制转换返回指针的类型
* new会自动计算分配内存大小，而malloc()需要人工计算，如`sizeof(int) * 20`
* new和delete在动态创建或销毁C++类对象的时候，可以自动调用类的构造函数和析构函数（所以在C++中对类使用new和delete）

## sizeof

```c++
cout<<sizeof(short)<<endl;
cout<<sizeof(int)<<endl;
cout<<sizeof(long)<<endl;
cout<<sizeof(long long)<<endl;
```
在64位mac系统测试得到：

- 32位下：2 4 4 8
- 64位下：2 4 8 8

只有long发生变化，**long的长度与指针的长度相同，都为当前位数地址总线长度**

## 指针和引用

引用和指针的不同：

* 没有“空引用”，引用必须初始化
* 引用初始化之后不可指向其他的变量
* vector等模板类中不可存储引用
* 引用的实现根据编译器的不同而不同，有的是通过指针常量实现的