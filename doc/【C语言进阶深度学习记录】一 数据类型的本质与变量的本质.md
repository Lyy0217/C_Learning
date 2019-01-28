> 今天学习C语言中的数据类型的本质与变量的本质


##  1 什么是数据类型

- 数据类型可以理解为固定内存大小的别名
- 数据类型是创建变量的模子

如同下面的图示，各个数据类型是代表了某一个固定大小的内存，数据类型是这块内存的别名。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190126235007269.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3Mzc1NDI3,size_16,color_FFFFFF,t_70#pic_center)

然后，当我们要创建一个变量时，就使用上述的基本数据类型为模子，产生一个新的变量，如下图所示：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019012623512641.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3Mzc1NDI3,size_16,color_FFFFFF,t_70#pic_center)

这些新的变量，是根据基本数据类型这个模子，来刻画变量所占用的内存空间的大小。

## 2 变量的本质

变量的本质是什么？

- 变量是一段实际连续存储空间的别名，注意与基本数据类型的不同，基本数据类型是一段连续存储空间的别名，但是它不是任何一个实际的存储空间，它相当于一种规则。
- 程序中通过变量来申请并命名存储空间，
- 申请存储空间后，使用变量的名字可以使用该存储空间

如下图所示，即，i，j，k为普通的变量（在这里是int类型的变量），p也是一个变量，但是它是指针变量（指针后面会深度学习）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190126235150426.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3Mzc1NDI3,size_16,color_FFFFFF,t_70#pic_center)

## 3 数据类型与变量的关系

- 上面的学习中发现，变量可以看成是数据类型的一种具体化。变量所对应的数据类型，它们两个所占用存储空间的字节数是相等的。具体看下面的例子：

- 1-1.c
```c
#include <stdio.h>

int main()
{
    char c = 0;
    short s = 0;
    int i = 0;
    
    printf("%d, %d\n", sizeof(char), sizeof(c));
    printf("%d, %d\n", sizeof(short), sizeof(s));
    printf("%d, %d\n", sizeof(int), sizeof(i));
    
    return 0;
}
```
编译运行程序：
- gcc 1-1.c
- ./a.out

运行结果为：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190126235224989.png#pic_center)


## 4 自定义数据类型与创建变量

我们还可以自定义数据类型，然后使用自定义的数据类型来创建变量。如下代码：

1-2.c
```c
#include <stdio.h>

typedef int INT32;
typedef unsigned char BYTE;
typedef struct _tag_ts
{
    BYTE b1;
    BYTE b2;
    short s;
    INT32 i;
} TS;

int main()
{
    INT32 i32;
    BYTE b;
    TS ts;
    
    printf("%d, %d\n", sizeof(INT32), sizeof(i32));
    printf("%d, %d\n", sizeof(BYTE), sizeof(b));
    printf("%d, %d\n", sizeof(TS), sizeof(ts));
    
    return 0;
}
```
- 编译运行的结果为：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190126235252988.png#pic_center)


## 5 总结

- 数据类型的本质是一个模子
- 数据类型代表需要占用内存的大小
- 变量的本质是一段内存的别名
- 变量隶属于某一种数据类型
- 变量所在的内存的大小取决于其所属的数据类型的大小
