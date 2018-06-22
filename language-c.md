# C语言学习笔记

[TOC]

## qsort 函数说明

qsort包含在<stdlib.h>头文件中，此函数根据你给的比较条件进行快速排序，通过指针移动实现排序。排序之后的结果仍然放在原数组中。使用qsort函数必须自己写一个比较函数。

### 函数原型 

***void qsort ( void * base, size_t num, size_t size, int ( * comparator ) ( const void *, const void * ) );***

Sorts the num elements of the array pointed by base, each element size bytes long, using the comparator function to determine the order.
The sorting algorithm used by this function compares pairs of values by calling the specified comparator function with two pointers to elements of the array.
The function does not return any value, but modifies the content of the array pointed by base reordering its elements to the newly sorted order.

- **base** Pointer to the first element of the array to be sorted.(数组起始地址)
- **num** Number of elements in the array pointed by base.(数组元素个数)
- **size** Size in bytes of each element in the array.(每一个元素的大小)
- **comparator** Function that compares two elements.(函数指针，指向比较函数)

1、The function must accept two parameters that are pointers to elements, type-casted as void*. These parameters should be cast back to some data type and be compared.
2、The return value of this function should represent whether elem1 is considered less than, equal to, or greater than elem2 by returning, respectively, a negative value, zero or a positive value.

### 使用qsort进行排序 ##

- 定义比较函数
- 调用qsort

### 排序例子

- char 字符排序
```
#include <stdio.h>
#include <stdlib.h>

int cmp(const void *a , const void *b)
{
	return *(char *)a - *(char *)b;
}

int main()
{
	char num[] = {'2','3','4','1','2','6','1','2','3','4'};
	int i;
	qsort(num,10,sizeof(num[0]),cmp);
	for(i = 0;i < 10;i++)
	{
		printf("%c ",num[i]);
	}
	printf("\n");
	return 0;
}
```

- int值排序
``` C
#include <stdio.h>
#include <stdlib.h>

int cmp(const void *a , const void *b)
{
	return *(int *)a - *(int *)b;
}

int main()
{
	int num[] = {2, 3, 4, 1, 2, 6, 1, 2, 3, 4};
	int i;
	qsort(num,10,sizeof(num[0]),cmp);
	for(i = 0;i < 10;i++)
	{
		printf("%c ",num[i]);
	}
	printf("\n");
	return 0;
}
```
- double值排序
```C
#include <stdio.h>
#include <stdlib.h>

int cmp(const void *a , const void *b)
{
	return *(double *)a > *(double *)b ? 1 : -1;
}

int main()
{
	double num[] = {2.4,3.2,4.5,1.2,2.7,0.6,1.234,2.0,3,4};
	int i;
	qsort(num,10,sizeof(num[0]),cmp);
	for(i = 0;i < 10;i++)
	{
		printf("%f ",num[i]);
	}
	printf("\n");
	return 0;
}
```

- struct结构体排序
```C
/* qsort example */
#include <stdio.h>
#include <stdlib.h>

typedef struct
{
    int price;
    int id;
} order;
order list[10];
int i = 0;

int compare (const void *a, const void *b)
{

    order *orderA = (order *)a;
    order *orderB = (order *)b;

    if ( orderB->price  != orderA->price )
        return orderB->price - orderA->price;
    else
        return orderB->id - orderA->id;
}

int main ()
{

    int n;
    srand ( time(NULL) );
    printf("Before sorting\n");
    for(i = 0; i < 10; i++)
    {
        list[i].price = rand() % 10;
        list[i].id = i;
        printf ("Order id = %d Price = %d \n", list[i].id, list[i].price);
    }
    printf("AFTER sorting\n");

    qsort (list, 10, sizeof(order), compare);
    for (n = 0; n < 10; n++)
        printf ("Order id = %d Price = %d \n", list[n].id, list[n].price);
    return 0;
}
```

## C语言标准库：字符串转换为数字

### 1. atoi函数（将字符串转换成整型数）
- 相关函数 : atof，atol，atrtod，strtol，strtoul
- 表头文件 : stdlib.h
- 定义函数 : ***int atoi(const char *nptr)***;
- 函数说明 : atoi()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，而再遇到非数字或字符串结束时('\0')才结束转换，并将结果返回。
- 返回值 : 返回转换后的整型数。
- 附加说明 : atoi()与使用strtol(nptr，(char**)NULL，10)；结果相同。
- 例程序 :
```
#include <ctype.h>
#include <stdio.h>
int atoi (char s[]);
int main(void )
{
    char s[100];
    gets(s);
    printf("integer=%d\n", atoi(s));
    return 0;
}
int atoi (char s[])
{
    int i, n, sign;
    for(i = 0; isspace(s[i]); i++) //跳过空白符 ;
        sign = (s[i] == '-') ? -1 : 1;
    if(s[i] == '+' || s[i] == ' -') //跳过符号 i++;
        for(n = 0; isdigit(s[i]); i++)
            n = 10 * n + (s[i] - '0'); //将数字字符转换成整形数字
    return sign * n;
}
```

### 2. itoa（把一整数转换为字符串 ）
- 例程序：
```
#include <ctype.h>
#include <stdio.h>
void itoa (int n, char s[]); //atoi 函数：将ｓ转换为整形数
int main(void )
{
    int n;
    char s[100];
    printf("Input n:\n");
    scanf("%d", &n);
    printf("the string : \n");
    itoa (n, s);
    return 0;
}
void itoa (int n, char s[])
{
    int i, j, sign;
    if((sign = n) < 0)     //记录符号
        n = -n;                //使n成为正数
    i = 0;
    do
    {
        s[i++] = n % 10 + '0'; //取下一个数字
    }
    while ((n /= 10) > 0); //删除该数字
    if(sign < 0)
        s[i++] = '-';
    s[i] = '\0';
    for(j = i; j >= 0; j--) //生成的数字是逆序的，所以要逆序输出
        printf("%c", s[j]);
}
```
> 注意，atoi是标准库函数，itoa不是，用到itoa的时候可以用sprintf()a函数代替。

### 3. atof（将字符串转换成浮点型数） 
- 相关函数 : atoi，atol，strtod，strtol，strtoul
- 表头文件 : stdlib.h
- 定义函数 : ***double atof(const char *nptr)***;
- 函数说明 : atof()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，而再遇到非数字或字符串结束时('\0')才结束转 换，并将结果返回。参数nptr字符串可包含正负号、小数点或E(e)来表示指数部分，如123.456或123e-2。返回值 返回转换后的浮点型数。
- 附加说明 : atof()与使用strtod(nptr,(char**)NULL)结果相同。 

### 4. atol（将字符串转换成长整型数） 
- 相关函数 : atof，atoi，strtod，strtol，strtoul
- 表头文件 : stdlib.h
- 定义函数 : ***long atol(const char *nptr)***;
- 函数说明 : atol()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，而再遇到非数字或字符串结束时('\0')才结束转换，并将结果返回。
- 返回值 : 返回转换后的长整型数。
- 附加说明 : atol()与使用strtol(nptr,(char**)NULL,10)；结果相同。 

### 5. gcvt（将浮点型数转换为字符串，取四舍五入） 
- 相关函数 : ecvt，fcvt，sprintf
- 表头文件 : stdlib.h
- 定义函数 : ***char *gcvt(double number，size_t ndigits，char *buf)***;
- 函数说明 : gcvt()用来将参数number转换成ASCII码字符串，参数ndigits表示显示的位数。gcvt()与ecvt()和fcvt()不同的地方 在于，gcvt()所转换后的字符串包含小数点或正负符号。若转换成功，转换后的字符串会放在参数buf指针所指的空间。
- 返回值 : 返回一字符串指针，此地址即为buf指针。

### 6. strtod（将字符串转换成浮点数） 
- 相关函数 : atoi，atol，strtod，strtol，strtoul
- 表头文件 : stdlib.h
- 定义函数 : ***double strtod(const char *nptr,char **endptr)***;
- 函数说明 : strtod()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，到出现非数字或字符串结束时('\0')才结束转 换，并将结果返回。若endptr不为NULL，则会将遇到不合条件而终止的nptr中的字符指针由endptr传回。参数nptr字符串可包含正负号、 小数点或E(e)来表示指数部分。如123.456或123e-2。
- 返回值 : 返回转换后的浮点型数。

### 7. strtol（将字符串转换成长整型数）
- 相关函数 : atof，atoi，atol，strtod，strtoul
- 表头文件 : stdlib.h
- 定义函数 : ***long int strtol(const char *nptr,char **endptr,int base)***;
- 函数说明 : strtol()会将参数nptr字符串根据参数base来转换成长整型数。参数base范围从2至36，或0。参数base代表采用的进制方式，如 base值为10则采用10进制，若base值为16则采用16进制等。当base值为0时则是采用10进制做转换，但遇到如'0x'前置字符则会使用 16进制做转换。一开始strtol()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，再遇到非数字或字符串结束 时('\0')结束转换，并将结果返回。若参数endptr不为NULL，则会将遇到不合条件而终止的nptr中的字符指针由endptr返回。
返回值 返回转换后的长整型数，否则返回ERANGE并将错误代码存入errno中。
附加说明 ERANGE指定的转换字符串超出合法范围。 

### 8. strtoul（将字符串转换成无符号长整型数） 
- 相关函数 : atof，atoi，atol，strtod，strtol
- 表头文件 : stdlib.h
- 定义函数 : ***unsigned long int strtoul(const char *nptr,char **endptr,int base)***;
- 函数说明 : strtoul()会将参数nptr字符串根据参数base来转换成无符号的长整型数。参数base范围从2至36，或0。参数base代表采用的进制方 式，如base值为10则采用10进制，若base值为16则采用16进制数等。当base值为0时则是采用10进制做转换，但遇到如'0x'前置字符则 会使用16进制做转换。一开始strtoul()会扫描参数nptr字符串，跳过前面的空格字符串，直到遇上数字或正负符号才开始做转换，再遇到非数字或 字符串结束时('\0')结束转换，并将结果返回。若参数endptr不为NULL，则会将遇到不合条件而终止的nptr中的字符指针由endptr返 回。
返回值 返回转换后的长整型数，否则返回ERANGE并将错误代码存入errno中。
附加说明 ERANGE指定的转换字符串超出合法范围。 

### 9. toascii（将整型数转换成合法的ASCII 码字符） 
- 相关函数 : isascii，toupper，tolower
- 表头文件 : ctype.h
- 定义函数 : ***int toascii(int c)***;
- 函数说明 : toascii()会将参数c转换成7位的unsigned char值，第八位则会被清除，此字符即会被转成ASCII码字符。
- 返回值 : 将转换成功的ASCII码字符值返回。

## C库函数手册(string.h)
### 分类函数,所在函数库为string.h

### 1. strcpy 
- 函数名 : ***strcpy***
- 功 能 : 拷贝一个字符串到另一个
- 用 法 : **char *strcpy(char *destin, char *source)**;
- 程序例:
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char string[10];
    char *str1 = "abcdefghi";
    strcpy(string, str1);

    printf("%s\n", string);
    return 0;
}
```

### 2. strncpy
- 函数名 : ***strncpy***
- 功能 ： 将字符串src中最多n个字符复制到字符数组dest中(它并不像strcpy一样遇到NULL才停止复制，而是等凑够n个字符才开始复制），返回指向dest的指针
- 原型 ： **char * strncpy(char *dest, char *src, size_t n)**; 　
- 程序例 :
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char string[10];
    char *str1 = "abcdefghi";
    strncpy(string, str1, 3);

    printf("%s\n", string);
    return 0;
}
```

### 3. strcat
- 函数名 : ***strcat***
- 功能 : 字符串拼接函数
- 用法 : **char *strcat(char *destin, char *source)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char destination[25];
    char *blank = " ", *c = "C++", *Borland = "Borland";
    strcpy(destination, Borland);
    strcat(destination, blank);
    strcat(destination, c);
    printf("%s\n", destination);
    return 0;
}
```

### 4. strchr
- 函数名 : ***strchr***
- 功能 : 在一个串中查找给定字符的第一个匹配之处
- 用法 : **char *strchr(char *str, char c)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char string[15];
    char *ptr, c = 'r';
    strcpy(string, "This is a string");
    ptr = strchr(string, c);
    if (ptr)
        printf("The character %c is at position: %d\n", c, ptr - string);
    else
        printf("The character was not found\n");
    return 0;
}
```

### 5. strcmp
- 函数名 : ***strcmp***
- 功能 : 串比较看Asic码，str1 > str2，返回值 > 0；两串相等，返回0
- 用法 : **int strcmp(char *str1, char *str2)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *buf1 = "aaa", *buf2 = "bbb", *buf3 = "ccc";
    int ptr;
    ptr = strcmp(buf2, buf1);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 1\n");
    else
        printf("buffer 2 is less than buffer 1\n");
    ptr = strcmp(buf2, buf3);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 3\n");
    else
        printf("buffer 2 is less than buffer 3\n");
    return 0;
}
```

### 6. strnicmp
- 函数名 : ***strnicmp***
- 功能 : 将一个串中的一部分与另一个串比较, 不管大小写
- 用法 : **int strnicmp(char *str1, char *str2, unsigned maxlen)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *buf1 = "BBB", *buf2 = "bbb";
    int ptr;
    ptr = strnicmp(buf2, buf1);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 1\n");
    if (ptr < 0)
        printf("buffer 2 is less than buffer 1\n");
    if (ptr == 0)
        printf("buffer 2 equals buffer 1\n");
    return 0;
}
```

### 7. strlen
- 函数名 : ***strlen***
- 功能 : strlen函数求的是字符串的长度，它求得方法是从字符串的首地址开始到遇到第一个'\0'停止计数,如果你只定义没有给它赋初值，这个结果是不定的，它会从字符串首地址一直记下去，直到遇到'\0'才会停止。
- 原型 : **size_t strlen(const char *s)**;
- 程序例 : 
```
#include<stdio.h>
#include <string.h>
int main()
{
    int i = 0;
    char *he = "Hello,world";
    i = strlen(he);
    printf("字符串长度为%d\n", i);
    return 0;
}
//运行结果：字符串长度为11
```

### 8. strcspn
- 函数名 : ***strcspn***
- 功能 : 在串中查找第一个给定字符集内容的段
- 用法 : **int strcspn(char *str1, char *str2)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
#include <alloc.h>
int main(void)
{
    char *string1 = "1234567890";
    char *string2 = "747DC8";
    int length;
    length = strcspn(string1, string2);
    printf("Character where strings intersect is at position %d\n", length);
    return 0;
}
```

### 9. strdup
- 函数名 : ***strdup***
- 功能 : 将串拷贝到新建的位置处
- 用法 : **char *strdup(char *str)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
#include <alloc.h>
int main(void)
{
    char *dup_str, *string = "abcde";
    dup_str = strdup(string);
    printf("%s\n", dup_str);
    free(dup_str);
    return 0;
}
```

### 10. stricmp
- 函数名 : ***stricmp***
- 功能 : 以大小写不敏感方式比较两个串
- 用法 : **int stricmp(char *str1, char *str2)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *buf1 = "BBB", *buf2 = "bbb";
    int ptr;
    ptr = stricmp(buf2, buf1);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 1\n");
    if (ptr < 0)
        printf("buffer 2 is less than buffer 1\n");
    if (ptr == 0)
        printf("buffer 2 equals buffer 1\n");
    return 0;
}
```

### 11. strerror
- 函数名 : ***strerror***
- 功能 : 返回指向错误信息字符串的指针
- 用法 : **char *strerror(int errnum)**;
- 程序例 :
```
#include <stdio.h>
#include <errno.h>
int main(void)
{
    char *buffer;
    buffer = strerror(errno);
    printf("Error: %s\n", buffer);
    return 0;
}
```

### 12. strcmpi
- 函数名 : ***strcmpi***
- 功能 : 将一个串与另一个比较, 不管大小写
- 用法 : **int strcmpi(char *str1, char *str2)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *buf1 = "BBB", *buf2 = "bbb";
    int ptr;
    ptr = strcmpi(buf2, buf1);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 1\n");
    if (ptr < 0)
        printf("buffer 2 is less than buffer 1\n");
    if (ptr == 0)
        printf("buffer 2 equals buffer 1\n");
    return 0;
}
```

### 13. strnicmp
- 函数名 : ***strnicmp***
- 功能: 不注重大小写地比较两个串
- 用法: **int strnicmp(char *str1, char *str2, unsigned maxlen)**;
- 程序例:
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *buf1 = "BBBccc", *buf2 = "bbbccc";
    int ptr;
    ptr = strnicmp(buf2, buf1, 3);
    if (ptr > 0)
        printf("buffer 2 is greater than buffer 1\n");
    if (ptr < 0)
        printf("buffer 2 is less than buffer 1\n");
    if (ptr == 0)
        printf("buffer 2 equals buffer 1\n");
    return 0;
}
```

### 14. strnset
- 函数名 : ***strnset***
- 功能 : 将一个字符串前n个字符都设为指定字符
- 用法 : **char *strnset(char *str, char ch, unsigned n)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char *string = "abcdefghijklmnopqrstuvwxyz";
    char letter = 'x';
    printf("string before strnset: %s\n", string);
    strnset(string, letter, 13);
    printf("string after strnset: %s\n", string);
    return 0;
}
```

### 15. strpbrk
- 函数名 : ***strpbrk***
- 功能 : 在串中查找给定字符集中的字符
- 用法 : **char *strpbrk(char *str1, char *str2)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char *string1 = "abcdefghijklmnopqrstuvwxyz";
    char *string2 = "onm";
    char *ptr;
    ptr = strpbrk(string1, string2);
    if (ptr)
        printf("strpbrk found first character: %c\n", *ptr);
    else
        printf("strpbrk didn't find character in set\n");
    return 0;
}
```

### 16. strrchr
- 函数名: ***strrchr***
- 功能: 在串中查找指定字符的最后一个出现
- 用法: **char *strrchr(char *str, char c)**;
- 程序例:
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char string[15];
    char *ptr, c = 'r';
    strcpy(string, "This is a string");
    ptr = strrchr(string, c);
    if (ptr)
        printf("The character %c is at position: %d\n", c, ptr - string);
    else
        printf("The character was not found\n");
    return 0;
}
```

### 17. strrev
- 函数名 : ***strrev***
- 功能 : 串倒转
- 用法 : **char *strrev(char *str)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char *forward = "string";
    printf("Before strrev(): %s\n", forward);
    strrev(forward);
    printf("After strrev(): %s\n", forward);
    return 0;
}
```

### 18. strset
- 函数名 : ***strset***
- 功能: 将一个串中的所有字符都设为指定字符
- 用法: **char *strset(char *str, char c)**;
- 程序例:
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char string[10] = "123456789";
    char symbol = 'c';
    printf("Before strset(): %s\n", string);
    strset(string, symbol);
    printf("After strset(): %s\n", string);
    return 0;
}
```

### 19. strstr
- 函数名 : ***strstr***
- 功能 : 在串中查找指定字符串的第一次出现
- 用法 : **char *strstr(char *str1, char *str2)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char *str1 = "Borland International", *str2 = "nation", *ptr;
    ptr = strstr(str1, str2);
    printf("The substring is: %s\n", ptr);
    return 0;
}
```

### 20. strtod
- 函数名 : ***strtod***
- 功能 : 将字符串转换为double型值
- 用法 : **double strtod(char *str, char **endptr)**;
- 程序例 :
```
#include <stdio.h>
#include <stdlib.h>
int main(void)
{
    char input[80], *endptr;
    double value;
    printf("Enter a floating point number:");
    gets(input);
    value = strtod(input, &endptr);
    printf("The string is %s the number is %lf\n", input, value);
    return 0;
}
```

### 21. strtok
- 函数名 : ***strtok***
- 功能 : 查找由在第二个串中指定的分界符分隔开的单词
- 用法 : **char *strtok(char *str1, char *str2)**;
- 程序例 :
```
#include <string.h>
#include <stdio.h>
int main(void)
{
    char input[16] = "abc,d";
    char *p;
    /* strtok places a NULL terminator
    in front of the token, if found */
    p = strtok(input, ",");
    if (p) printf("%s\n", p);
    /* A second call to strtok using a NULL
    as the first parameter returns a pointer
    to the character following the token */
    p = strtok(NULL, ",");
    if (p) printf("%s\n", p);
    return 0;
}
```

### 22. strtol
- 函数名 : ***strtol***
- 功能 : 将串转换为长整数
- 用法 : **long strtol(char *str, char **endptr, int base)**;
- 程序例 :
```
#include <stdlib.h>
#include <stdio.h>
int main(void)
{
    char *string = "87654321", *endptr;
    long lnumber;
    /* strtol converts string to long integer */
    lnumber = strtol(string, &endptr, 10);
    printf("string = %s long = %ld\n", string, lnumber);
    return 0;
}
```

### 23. strupr
- 函数名 : ***strupr***
- 功能 : 将串中的小写字母转换为大写字母
- 用法 : **char *strupr(char *str)**;
- 程序例 :
```
#include <stdio.h>
#include <string.h>
int main(void)
{
    char string[ ] = "abcdefghijklmnopqrstuvwxyz", *ptr;//定义为数组才能修改
    /* converts string to upper case characters */
    ptr = strupr(string);
    printf("%s\n", ptr);
    return 0;
}
```

### 24. swab
- 函数名: ***swab***
- 功能: 交换字节
- 用法: **void swab (char *from, char *to, int nbytes)**;
- 程序例:
```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
char source[15] = "rFna koBlrna d";
char target[15];
int main(void)
{
    swab(source, target, strlen(source));
    printf("This is target: %s\n", target);
    return 0;
}
```

## C库函数手册(ctype.h)
### 分类函数,所在函数库为ctype.h

- **int isalpha(int ch)**  
若ch是字母('A'-'Z','a'-'z')返回非0值,否则返回0

- **int isalnum(int ch)**  
若ch是字母('A'-'Z','a'-'z')或数字('0'-'9')返回非0值,否则返回0

- **int isascii(int ch)**  
若ch是字符(ASCII码中的0-127)返回非0值,否则返回0

- **int iscntrl(int ch)**  
若ch是作废字符(0x7F)或普通控制字符(0x00-0x1F)返回非0值,否则返回0

- **int isdigit(int ch)**  
若ch是数字('0'-'9')返回非0值,否则返回0

- **int isgraph(int ch)**  
若ch是可打印字符(不含空格)(0x21-0x7E)返回非0值,否则返回0

- **int islower(int ch)**  
若ch是小写字母('a'-'z')返回非0值,否则返回0

- **int isprint(int ch)**  
若ch是可打印字符(含空格)(0x20-0x7E)返回非0值,否则返回0

- **int ispunct(int ch)**  
若ch是标点字符(0x00-0x1F)返回非0值,否则返回0

- **int isspace(int ch)**  
若ch是空格(' '),水平制表符('	'),回车符(' '),走纸换行('f'),垂直制表符('v'),换行符(' ')返回非0值,否则返回0

- **int isupper(int ch)**  
若ch是大写字母('A'-'Z')返回非0值,否则返回0

- **int isxdigit(int ch)**  
若ch是16进制数('0'-'9','A'-'F','a'-'f')返回非0值,否则返回0

- **int tolower(int ch)**  
若ch是大写字母('A'-'Z')返回相应的小写字母('a'-'z')

- **int toupper(int ch)**
若ch是小写字母('a'-'z')返回相应的大写字母('A'-'Z')
