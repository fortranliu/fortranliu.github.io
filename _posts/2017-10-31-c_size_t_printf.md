---
layout: 'post'
title: 'size_t格式'
date:   2017-10-31 10:22
categories: 技术文档
tags: c
---

size_t 为 unsigned int，从文件中读取时要注意格式，如：

```c
//...
size_t N;
//...

//...
fp=fopen("data","r");
fscanf(fp,"%d",&N); //读取235到N
//...
```
data文件为：
```
235
0.0 0.0
0.1 0.1
```

程序运行时可能产生段错误，利用gdb调试时，`print N`打印出来的值为257698037995，转换为16进制为3c000000eb，而eb转换为10进制刚好为235，而利用`x &N` 打印出来的值为0x000000eb。由此可见，采用`%d`格式读入数据到`size_t`格式的变量中时，符号位变成了数据位，自然不能正确地存储数据。将`%d`改为`%zu`即可。

Use the z modifier:
```c
size_t x = ...;
ssize_t y = ...;
printf("%zu\n", x);  // prints as unsigned decimal
printf("%zx\n", x);  // prints as hex
printf("%zd\n", y);  // prints as signed decimal
```

参考链接：
[How can one print a size_t variable portably using the printf family?](https://stackoverflow.com/questions/2524611/how-can-one-print-a-size-t-variable-portably-using-the-printf-family)