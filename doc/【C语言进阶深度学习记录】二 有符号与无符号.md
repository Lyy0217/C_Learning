> 今天学习C语言中的有符号与无符号

 

## 1  计算机中的符号位

 

C语言中，数据类型的最高位，用于标识数据的符号。

- 最高位为1，表明这个数为负数
- 最高位为0，表明这个数为正数

 

比如下图：

![](http://m.qpic.cn/psb?/V12UXsXm3z1Xes/DoXET3RCkmBBwZ0lzvXhXkp6sEln*EUK*fKwoBSZCtg!/b/dLkAAAAAAAAA&bo=3wHrAAAAAAADBxc!&rf=viewer_4)

 

### 1.1 有符号数的表示法

 

- 在计算机内部用补码表示负数

1. 正数的补码为正数本身
2. 负数的补码为负数的绝对值各位取反后加1

 

比如下图中的：

![](http://m.qpic.cn/psb?/V12UXsXm3z1Xes/6D55wvw7ojznif4wUe6VKEmCBjMHT8XkTs7GZeCyTnE!/b/dFIBAAAAAAAA&bo=9ALuAAAAAAADFyo!&rf=viewer_4)

 

### 1.2 无符号数的表示法

 

- 在计算机内部，用源码表示无符号数。

1. 无符号数默认为正数
2. 无符号数没有符号位

 

- 对于固定长度的无符号数有：

1. MAX_VALUE +1  --> MIN_VALUE
2. MIN_VALUE - 1 --> MAX_VALUE

 

### 1.3 signed 和 unsigned

 

- 在C语言中，变量默认为有符号的类型
- unsigned 关键字声明变量为无符号类型

> 但是要注意一点，只有整数类型（int，char，long，short）能够声明unsigned变量

 

 

## 2 实验-当有符号数与无符号数进行运算

 

如下程序的运行代码：


```c
#include <stdio.h>
 
int main()
{
unsigned int i = 5;
int j = -10;
 
if( (i + j) > 0 )
{
    printf("i + j > 0\n");
}
else
{
    printf("i + j <= 0\n");
}
 
return 0;
}
```

运行结果将是i+j >0 。

 

- 因为有符号数与无符号数进行混合运算时，会将有符号数转换成无符号数后再进行计算，计算结果就变成了无符号数了。所以上述结果为正数

 

## 3 错误的使用了unsigned

 

当错误的使用了下面的方式来写代码的时候，会产生错误：

 

```c
#include <stdio.h>
 
int main()
{
 
    unsigned int i = 0;
 
    for(i=9; i>=0; i--)
    {
        printf("i = %u\n", i);
    }
 
    return 0;
}
 
```

 

上述程序的运行结果为无限循环打印。

 

- 因为变量i是无符号数，所以i肯定大于等于0，上述的for循环会一直循环下去。

 

## 4 总结

 

- 有符号数用补码表示

1. 正数的符号位为0
2. 负数的符号位为1

- 无符号数用源码表示

1. 无符号数没有符号位
2. 无符号数只能用于表示正数以及0

- unsigned 只能用于修饰正数类型的变量
- 有符号数与无符号数进行混合运算时，会将有符号数转换成无符号数后再进行计算，计算结果就变成了无符号数了