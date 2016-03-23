---
title: C++标准库小记
date: 2016-03-23 10:11:17
categories: C++
description: C++类相关要点，标准库
tags: 
- C++
- 标准库
- 复杂度

---

# C++类相关要点

![C++标准库](http://img.wdjimg.com/mms/icon/v1/8/64/72c6d9759d14a5442bcb414e961aa648_256_256.png)

## set和unordered_Set

```c++
set<int> s1 = {1,2,3,4,5};
if (s1.find(3) != s1.end())
  cout<<"Found it"<<endl;
  
unordered_set<int> s2 = {1,2,3,4,5};
if (s2.find(3) != s2.end())
  cout<<"Found it"<<endl;
```

set.find() 的时间复杂度是O(nlog(n))，采用红黑树实现

unordered_set.find() 的时间复杂度通常是常数，采用哈希实现，当哈希结果不好时会退化到线性