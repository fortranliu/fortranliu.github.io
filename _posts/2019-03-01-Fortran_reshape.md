---
layout: post
title:  "reshape of Fortran"
date:   2019-03-01 10:22
categories: 技术文档
tags: Fortran
---

# reshape of Fortran

## 示例

考虑如下代码：

```fortran
integer,dimension(3,3,2) :: &
mat = reshape( &
     (/1,2,3,  &
       4,5,6   &
       7,8,9,  &
       
       -1,-2,-3, &
       -4,-5,-6, &
       -7,-8,-9/),(/3,3,2/))
       
write(*,*) mat(1,:,1)
write(*,*) mat(2,:,1)
write(*,*) mat(3,:,1)

write(*,*) mat(1,:,2)
write(*,*) mat(2,:,2)
write(*,*) mat(3,:,2)
```

输出结果为：

```
 1  4  7
 2  5  8
 3  6  9

-1 -4 -7
-2 -5 -8
-3 -6 -9
```

若加上参数`ORDER`：

```fortran
integer,dimension(3,3,2) :: &
mat = reshape( &
     (/1,2,3,  &
       4,5,6   &
       7,8,9,  &
       
       -1,-2,-3, &
       -4,-5,-6, &
       -7,-8,-9/),(/3,3,2/),ORDER=(/3,2,1/))
       
write(*,*) mat(1,:,1)
write(*,*) mat(2,:,1)
write(*,*) mat(3,:,1)

write(*,*) mat(1,:,2)
write(*,*) mat(2,:,2)
write(*,*) mat(3,:,2)
```

输出结果为：

```
 1  3  5
 7  9 -2
-4 -6 -8

 2  4  6
 8 -1 -3
-5 -7 -9
```





建议直观写法为：

```fortran
integer,dimension(2,3,3) :: &
mat = reshape( &
     (/1,2,3,  &
       4,5,6   &
       7,8,9,  &
       
       -1,-2,-3, &
       -4,-5,-6, &
       -7,-8,-9/),(/2,3,3/),ORDER=(/3,2,1/))
       
write(*,*) mat(1,1,:)
write(*,*) mat(1,2,:)
write(*,*) mat(1,3,:)

write(*,*) mat(2,1,:)
write(*,*) mat(2,2,:)
write(*,*) mat(2,3,:)
```

此时，输出结果为：

```
  1  2  3
  4  5  6
  7  8  9
 
 -1 -2 -3
 -4 -5 -6
 -7 -8 -9
```



##ORDER 的含义

没有ORDER时，数据按照column-major的方式填充。ORDER=(/1,2,3,...,n/)或者其排列组合(permutation)，n为数组被reshape的维数。

```fortran
matB = reshape(matA, [n1,n2,n3])
```

等价于

```fortran
k = 0
do i3 = 1,n3
do i2 = 1,n2
do i1 = 1,n1
  k = k + 1
  matB(i1,i2,i3) = matA_seq(k) !matA_seq is a sequential view of matA
end do
end do
end do
```

加上order这个参数之后：

```fortran
matB = reshape(matA, [n1,n2,n3], order=[2,3,1])
```

等价于

```fortran
k = 0
do i1 = 1,n1
do i3 = 1,n3
do i2 = 1,n2
  k = k + 1
  matB(i1,i2,i3) = matA_seq(k)
end do
end do
end do
```



