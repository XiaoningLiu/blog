---
title: C++类相关要点
date: 2016-03-21 12:45:12
categories: C++
description: C++类相关要点，构造函数，重载函数
tags: 
- C++
- 类
- 重载函数
- 面试
- 构造函数
- 虚函数

---

# C++类相关要点

![C++类](http://image.coolapk.com/apk_logo/2014/1113/257251_1415867697_4166.png)

## 空间

``` C++
class a{};
class b{};
class c:public a
{
	virtual void fun()=0;
};
class d:public b,public c{};

// g++ class.cpp -m32
cout<<"sizeof(a)"<<sizeof(a)<<endl; // 1byte
cout<<"sizeof(b)"<<sizeof(b)<<endl; // 1byte
cout<<"sizeof(c)"<<sizeof(c)<<endl; // 包含虚函数指针4bytes
cout<<"sizeof(d)"<<sizeof(d)<<endl; // 包含c的虚函数指针4bytes
```

使用32bit编译，**结果如下：**

```C++
sizeof(a)1
sizeof(b)1
sizeof(c)4
sizeof(d)4
```

使用64bit编译，**结果如下：**

```C++
sizeof(a)1
sizeof(b)1
sizeof(c)8
sizeof(d)8
```

注意：C++中指针本身的长度、long变量的长度是和内存地址位宽一致的

## 构造函数


``` C++
class Tran
{
public:
	string val;
	Tran(const string & str): val(str)
	{
		cout<<"隐式转换函数调用"<<endl;
	} // 构造函数，实现了隐式转换功能
	Tran(const Tran & tr): val(tr.val)
	{
		cout<<"赋值构造函数调用"<<endl;
	} // 赋值构造函数
	const Tran & operator= (const Tran & tr)
	{
		cout<<"复制函数调用"<<endl;
		val = tr.val;
		return *this;
	}
};

// Tran tran = "hello";       // 错误：字符串常量不是string类型的，无法调用隐式转换函数
// Tran tran;                 // 错误：在定义了其他构造函数之后，编译器不会生成默认无参数的构造函数
Tran tran2 = string("hello"); // 调用了Tran的第一个构造函数，第一个是隐式转换构造函数
Tran tran3 = tran2;           // 调用了Tran的第二个构造函数，第二个是赋值构造函数
tran3 = tran2;                // 调用了Tran的第三个冲在函数，第三个是复制重载函数
cout<<tran2.val<<endl;
```

**输出如下：**

```C++
隐式转换函数调用
赋值构造函数调用
复制函数调用
hello
```
