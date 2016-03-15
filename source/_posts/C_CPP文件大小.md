---
title: C/C++检查文件大小
date: 2016-03-15 13:49:08
categories: C++
description: C与C++下查看文件大小
tags: 
- C
- C++
- 文件
- 面试

---

### C/C++检查文件大小

![文件大小](http://pic.baike.soso.com/p/20121025/20121025162509-156696453.jpg)

今天V2EX社区有伙伴贴出了面试阿里后端的内容，其中涉及使用C获取文件大小的问题。因为本人对C++比较熟悉，将可以使用C++风格的两种方式总结如下：

**备注：以下代码均为C++实现**

#### C++使用ifstream查看

``` c++
#include <fstream>
using namespace std;

ifstream i("file");
if (i.is_open())
{
    i.seekg(0, i.end); // i.end是枚举类型
    cout<<"c++ length:"<<i.tellg()<<endl;
}
i.close();
```

重点函数有两个，平时可能不太常用，函数还有其他的重载实现，但在本例子中只用了以下两种实现：

1. seekg(0, i.end)
2. tellg()

#### C++使用C代码库查看

``` C
#include <cstdio>
using namespace std;

FILE *f = fopen("file", "r");
fseek(f, 0, SEEK_END);
cout<<"c length: "<<ftell(f)<<endl;;
fclose(f);
```

本例子中重点使用以下函数与命令：

1. FILE *f = fopen(xx, xx)
2. fseek(f, 0, SEEK_END)
3. ftell()

#### Linux使用Shell命令查看

``` shell
ls -lh | grep XXX | awk '{print $x}'
```

#### 备注

在C下面还有使用**struct _stat**结构体获取文件大小的办法，具体请参考相关资料。

#### 相关资料

* [AWK 命令的使用方式](http://www.cnblogs.com/ggjucheng/archive/2013/01/13/2858470.html)
* [C语言获取文件大小两种办法](http://www.2cto.com/kf/201405/298713.html)

