---
title: C语言中字符数组的初始化与赋值，字符串相关函数！
categories: c语言
---



1.字符数组初始化
在C语言中，字符串是当做字符数组来处理的；所以字符串有两种声明方式，一种是字符数组，一种是字符指针。

（1）直接逐个初始化字符数组：字符数组的初始化，最容易理解的方式就是逐个字符赋给数组中各元素。

char str[10]={ 'I',' ','a','m',' ',‘h’,'a','p','p','y'};
注意：如果花括号中提供的字符个数大于数组长度，则按语法错误处理；若小于数组长度，则只将这些字符数组中前面那些元素，其余的元素自动定为空字符（即'\0' )。

（2）用字符串常量来初始化字符数组：在c语言中，将字符串作为字符数组来处理。因此可以使用字符串来初始化字符数组。

char str[]={"I am happy"};
也可以省略花括号：
char str[]="I am happy";
但是，上述这种字符数组的整体赋值只能在字符数组初始化时使用，不能用于字符数组的赋值，字符数组的赋值只能对其元素一一赋值，下面的赋值方法是错误的。

char str[];
str="I am happy";//错误，字符数组的赋值只能按元素一一赋值（错误的原因： C语言并没有提供可以直接操作字符串的运算符；“=”可以用于其他数据类型的赋值，但是不可以直接给字符串赋值。
这是字符数组初始化的两种方式，但是这两种方式其实是不等价的；他们的数组长度不同。

#include<stdio.h>

int main() 
{
    
char parr[] = "zifuchuanshuzu";  
//与charr[]不等价 
char charr[] = { 'z','i','f','u','c','h','u','a','n','s','h','u','z','u' };  
//等价于charr[]  
char charr_test[] = { 'z','i','f','u','c','h','u','a','n','s','h','u','z','u' ,'\0'};

  

int num_parr = sizeof(parr);
int num_charr = sizeof(charr); 
int num_charr_test = sizeof(charr_test);


printf("The parr[] is : %s\n", parr); 
printf("The size of parr[] is : %d\n\n", num_parr);


//与charr[]不等价
printf("The charr[] is : %s\n", charr); 
printf("The size of charr[] is : %d\n\n", num_charr);


//等价于charr[]
printf("The charr_test[] is : %s\n", charr_test);
printf("The size of charr_test[] is : %d\n", num_charr_test); 
return 0;

}

运行结果：


从结果可以看到第二种初始化方式，打印的结果有问题，但是字符数量没有问题。这是因为字符串默认是以’\0’结束的，第二种初始化方式中没有’\0’,而我们以字符串方式打印，所以出错； 

第一种是系统自动添加了’\0’;我们可以看到其字符数量是15（与第三种相同）。

 

（3）字符指针：在C语言中我们也可以使用字符指针来存储字符串。

  字符指针初始化：

char* str="zifuchuanshuzu";
C语言对字符串常量是按照字符数组来处理的，在内存中开辟了一个字符数组用来存放字符串常量，程序在定义字符串指针变量str时，只是把字符串首地址赋值给str。 

输出：

printf("%s\n",str);
系统首先输出str指向的字符，而后自加1，直至遇到’\0’;与数组的输出方式相同。

 字符指针的赋值：

char *str;
str="zifuzhizhen";
对于字符指针这种赋值方式是正确的。与字符数组不同。
2.字符串处理函数：strcpy函数和strcat函数
（1）char *strcpy(char *dest,const char*src);
头文件：string.h和stdio.h 

功能：将src地址开始且包含’\0’结束符的字符串复制到以dest开始的空间。 

注： 字符数组dest必须是数组名形式，src可以是数组名也可以是字符串常量 可以用strcpy将src的前若干个字符复制到字符数组中.

（2）char *strcat(char *dest,const char *src);
头文件：string.h 

功能： 把src中的内容复制到dest结尾处(覆盖’\0’)。 

注： src和dest内存区域不可以重叠，dest必须有足够的空间来容纳src； 字符数组dest必须是数组名形式，src可以是数组名也可以是字符串常量； 返回指向dest的指针；

#include<stdio.h>

#include<string.h>

int main() 
{
    
//利用strcpy为字符数组赋值
    
char parr[40];
    
strcpy(parr,"zifuchuanshuzu");
    
printf("The parr[] is : %s\n\n", parr);
    
//赋值字符串的一部分
    
char charr[] = "_test_strcat_redundance";
    
char tarr[13];
    
charr[12] = '\0';
//复制charr的前12个字符

 strcpy(tarr, charr);
    
printf("The tarr[] is : %s\n\n", tarr);
    
//字符串链接
    
strcat(parr, charr);
    
printf("The parr and tarr[] is : %s\n", parr);
    
return 0;

}

结果：



3.总结
（1）在C语言中并没有直接提供字符串的操作，其字符串操作是通过转化为字符串完成的，例如字符数组，字符指针，其本质是对字符的操作。

（2）作为字符数组，与普通数组相同，区别在于它的每一个元素是一个字符，所以不可以直接用“=”对字符数组赋值（parr[]=”zhifushuzu”，是错误的赋值方式），但是可以对每一个元素进行赋值（charr[12]=’\0’是正确的）。

（3）字符串一定是以’\0’结尾的；字符数组和字符指针我们当做字符串整体初始化，系统会自动添加’\0’;对于字符数组，如果采用单个字符的方式进行初始化或者赋值一定要考虑结束符’\0’.
（4）strcpy和strcat内部也是对字符的操作，以‘\0’作为字符串结束的标志。
————————————————
版权声明：本文为CSDN博主「魏波-」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weibo1230123/article/details/82824814