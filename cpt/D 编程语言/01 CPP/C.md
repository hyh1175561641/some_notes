
C Primer Plus [美]Stephen Prata Sixth Edition
1
2
3*
4*
5
6
7
8
9
10
11
12
13
14
15
16
17
A
B




# gcc编译器

```c
gcc c.c -o c
// 错误信息表明程序有错误, 不能进行编译
// 警告信息表明代码虽然有效, 但不是程序员想要的, 可以通过编译


```

# C Language


标识符命名规则, 可以使用字母数字下划线组成,但数字不能开头


```c
// 单行注释
/* 多行注释 */


```


# 数据类型

bit(位0/1), Byte(字节8位), Word(字16/32/64位)
Byte = 8bit (0-255  -128-127)
Word = 16bit (0-65535  -32768-32767)
Double Word = 32bit (0-4294967295  -2147483648-2147483647)
Quad Word = 64bit (0-FFFF FFFF FFFF FFFF, 0-18446744073709551615)

常量constant, 整个程序的运行过程没有变化
变量variable, 程序运行期间可能会改变或被赋值

C语言把不含有小数点和指数的数视为int或long int, 而把含有小数点和指数的数视为double


```c

// sizeof运算符
printf("%zd",sizeof(int)); // %zd sizeof运算符, 不支持C99/C11可以用%u %lu 
sizeof name; // 对于特定的量, sizeof可以不使用圆括号, 但是建议加上
sizeof(int); // 对于类型, 可以加上圆括号

// 初始化字符常量, ASCII表为参考
char grade = 'A'; //字符常量
char grade = 65; // 初始化为数字, 同效上
char beep = 7/'\a'; // 蜂鸣字符
char a1='\101', a2='\x41'; // 八进制十六进制

// 常量
const int a = 6; // 声明一个常量, 这个常量值不可被更改

// 关键字
void // 无类型
signed unsigned // 整型符号修饰符
char short int long // 整型
float double // 浮点型
_Bool _Complex _Imaginary // C99添加的新关键字

// 声明变量指定其类型
char str; // 指定字符或者整型 8bit
unsigned short int / short int / short a; // 无符号short类型 16bit
int a; // 16/32bit
unsigned un; // 相当于unsigned int
long int / long a; // 32bit
long long int / long long a; // 64bit

// 声明变量
int a, b, c, d; //声明多个变量, 仅分配了内存空间,值取决于上次内存的值
a=2; b=3;//之后再赋值
int a=2, b=-23, c=2345; // 声明变量时赋值, 初始化变量
int a, b=94; // 初始化b,a还未赋值

// 前缀后缀
int a=16, b=020, c=0x10; // 添加前缀表示八进制和十六进制
int l=16l/L, ll=16ll/LL; // 添加后缀默认识别成long或long long类型
unsigned long long ull=16ull; // 添加后缀u/U识别成无符号类型



// 浮点类型, 储存小数
float weight; // 32位, 8位表示符号和指数的值, 24位表示非指数部分, 至少能表示6位有效数字, 取值范围是10-37-10+37
double weight; // 64位, 至少能表示13位有效数字
long double weight; // 至少比double精度相同

double a=3.14, b=2.00, c=3.16E7, d=2e-8, f=1e2(100.0); // 可以使用指数计数法
// 在计算机浮点存储中, 第一位是符号位, 前半部分表示值, 后半部分表示浮点
0.7E1 (=7.0)
.314159E1 (=3.14159)
0xa.1fp10 //十六进制表示小数, p表示指数, 幂是2的幂 等效于(10+1/16+15/256)x1024=10364.0
2.3f/F //F后缀, 编译器默认识别成float
54.3l/L // L后缀, 建议大写, 小写l容易混淆, 编译器默认识别成long double

float toobig = 3.4e38 * 100.0f; // 超出float表示范围, 称为上溢, 输出为inf 或 infinity
float underflow = 最小值 / 2; // 下溢, 趋向于0, 丢失精度
float notanumber = asin(2); // NaN(not a number), 

// C99添加新类型
_Bool boolean; // 布尔类型, 需要头文件<stdbool.h>
_Bool b=true/1, b2=false/0; // 原则上占用1位存储空间
// 复数和虚数都是基于浮点类型来构成
_Complex complex; // 复数
_Imaginary imaginary; // 虚数




```





# 指针

指针pointer



```c

int a; // 声明变量a
&a; // 获取a的地址



```

# 复合数据类型


```c
// 数组 array




```


```c
// 字符串 character string
// 字符串存储在连续的内存空间当中, 结尾是空字符\0
char name[40] = "Jone"; // 使用双引号括起来
sizeof name; // 字符串占用内存空间大小
strlen(name); // 字符串大小


```

```c
// 结构体 struct

```

```c
// 联合体 union



```













# 运算符

```c

= 赋值
+-*/% 加减乘除取模
> < == 大于小于等于





sizeof()





```
 位运算













# 语句
```c

while(true){
    pass;
}


for(){}


if(){}else{}

switch
```












# 函数
```c


int main(void){

    return 0;
}





// 函数的使用
printf("World!!!"); // 输出信息
scanf("%f",&weight); //获取输入
getchar(); //获取一个字符,会阻塞程序进一步执行, 比如终端防止关闭


```



# 作用域


# 预处理

预处理就是编译时进行替换

```c

#define DEF 3 // 定义一个宏

```


# 头文件




# C标准库

assert.h
complex.h
ctype.h
errno.h
fenv.h
float.h
inttypes.h
iso646.h
limits.h
locale.h
math.h
setjmp.h
signal.h
stdalign.h
stdarg.h
stdatomic.h
stdbit.h
stdbool.h
stdckdint.h
stddef.h
stdint.h
stdio.h
stdlib.h
stdnoreturn.h
string.h
tgmath.h
threads.h
time.h
uchar.h
wchar.h
wctype.h

```c

# include <math.h>
pow(3.5, 2.2);



```



```c

# include <float.h> // 浮点类型大小限制
# define FLT_DIG // float有效数字位数
# define DBL_DIG // double有效数字位数

FLT_MANT_DIG
FLT_DIG
FLT_MIN_10_EXP
FLT_MAX_10_EXP
FLT_MIN
FLT_MAX
FLT_EPSILON




````




```c
# include <limits.h> // 整数类型大小限制
# define INT_MAX +32767
# define INT_MIN -32768
CHAR_BIT
CHAR_MAX
CHAR_MIN
SCHAR_MAX
SCHAR_MIN
UCHAR_MAX
SHRT_MAX
SHRT_MIN
USHRT_MAX
INT_MAX
INT_MIN
UINT_MAX
LONG_MAX
LONG_MIN
ULONG_MAX
LLONG_MAX
LLONG_MIN
ULLONG_MAX










```



```c

# include <string.h>
strlen(); // 获取字符串实际长度




```



```c

# include <stdio.h> // 标准输入输出
// 常用函数表示
// printf();
printf(); // 返回打印字符的个数
printf("%d %o %x", 100, 100, 100); // 100 144 64
printf("%d %#o %#x", 100, 100, 100); // 100 0144 0x64
c char
s char* char[]
p pointer
n 
d or i int
u unsigned int
o unsigned int 八进制
x or X unsigned int 十六进制
f or F float
e or E 科学计数法
g or G 根据值自动选择%f或%e
a or A 十六进制浮点P计数法
% %% 打印一个百分号

修饰字符
* 指定字段宽度和浮点精度, ("%*d",width,n), ("%*.*f",width,precision,flt)
数字 %4d 最小字段宽度
.数字 %5.2f 字段宽度为5,小数点后面2位数字 %.f=%.0f仅保留整数
h 表示short, %hu %hx %6.4hd
hh 表示signed char或unsigned char
j 表示intmax_t uintmax_t %jd %8jx
l long int或unsigned long int
ll long long int 或 unsigned long long int
L long double
t 表示两个指针差值的类型ptrdiff_t, %td %12ti
z sizeof运算符

标记
- 左对齐, 从字段左侧打印 %-20s
+ 显示数值的正负号, %+6.2f
空格 正号不显示,负号则显示
# 显示八进制和十六进制的前缀
0 前面用0填充 %010d

eg.
%u unsigned int %lu unsigned long %hu unsigned short
%lld long long %llu unsigned long long 
%ld long
%lo %lx long //八进制十六进制
%hd %ho %hx short // short格式输出
%Lf %Le %La long double 
%zd sizeof运算符
%5.3d 字段宽度为5,显示3位, 如6显示为<*  0006*>
%24.5s 字符串占用24个空间, 仅显示前5个字符
//字符串断行
printf("abc\
def"); // 反斜杠加回车断行
printf("abc"
        "def"); // 两个字符串可以拼接起来


// scanf() 输入, 遇到空格,制表符,换行就停止了, 返回成功读取的项目数
// 输入的字符串转换成整数, 浮点数, 字符或字符串
scanf("%d", &a); // 第二个参数需要地址
c 字符
s 字符串
d or i 有符号十进制整数
u 无符号整数
o xX 八进制十六进制
eE fF gG aA 浮点数
p 把输入解释成指针
// 修饰符
* 抑制赋值 ("%*d %*d %d",&n) 跳过两个整数,第三个数赋值给n
数字 最大字段宽度 %10s
hh 把整数作为signed/unsigned char读取 %hhd %hhu
ll 把整数作为long long/unsigned long long读取 %lld %llu
h %hd %hi short int, %ho %hx %hu unsigned short int
l %ld %li long, %lo %lx %lu unsigned long, %le %lf %lg double
L %Le %Lf %Lg long double
j intmax_t uintmax_t 类型
z sizeof返回值类型
t 两个指针的差值
scanf("%d,%d",&m,&n); // 终端输入必须加上逗号,否则不匹配 *2,3*



// fgets() 输入一般字符串
// getchar(); 读取单个字符

```

```c
// 可移植整数类型的别名
# include <stdint.h>
精确宽度整数类型
int32_t 32位有符号整数类型
最小宽度类型
int_least8_t 最少容纳8位的类型
最快最小宽度类型
int_fast8_t 运算速度最快的可容纳8位整数类型
intmax_t 最大有符号整数类型, 可存储任何有效的有符号整数值
unitmax_t 最大无符号整数类型

# include <inttypes.h>
字符串宏
PRId32对应int32_t类型
int32_t me32=45933945; // 32位有符号整型变量
printf("me32=%" PRId32 "\n", me32); // 等效于("me32=%" "d" "\n"), 字符串会合并








```









# C Library

https://www.runoob.com/cprogramming/c-standard-library.html

```
合格的ctype, stdio, stdlib, string
熟练的assert, limits, stddef, time
优秀的errno, float, locale, math, setjmp, signal, stdarg

<cctype> (ctype.h) Character handling functions (header)
<cstdio> (stdio.h) C library to perform Input/Output operations (header)
<cstdlib> (stdlib.h) C Standard General Utilities Library (header)
<cstring> (string.h) C Strings (header)

<cassert> (assert.h) C Diagnostics Library (header)
<climits> (limits.h) Sizes of integral types (header)
<cstddef> (stddef.h) C Standard definitions (header)
<ctime> (time.h) C Time Library (header)

<cerrno> (errno.h) C Errors (header)
<cfloat> (float.h) Characteristics of floating-point types (header)
<clocale> (locale.h) C localization library (header)
<cmath> (math.h) C numerics library (header)
<csetjmp> (setjmp.h) Non local jumps (header)
<csignal> (signal.h) C library to handle signals (header)
<cstdarg> (stdarg.h) Variable arguments handling (header)

<ciso646> (iso646.h) ISO 646 Alternative operator spellings (header)

<cstdbool> (stdbool.h) Boolean type (header)
<cstdint> (stdint.h) Integer types (header)
<cuchar> (uchar.h) Unicode characters (header)
<cwchar> (wchar.h) Wide characters (header)
<cwctype> (wctype.h) Wide character type (header)
```


#include <string.h>

memcmp();
memcpy();
strcmp();
strlen();


string .h 头文件定义了一个变量类型、一个宏和各种操作字符数组的函数。
库变量

下面是头文件 string.h 中定义的变量类型：
序号	变量 & 描述
1	size_t
这是无符号整数类型，它是 sizeof 关键字的结果。
库宏

下面是头文件 string.h 中定义的宏：
序号	宏 & 描述
1	NULL
这个宏是一个空指针常量的值。
库函数

下面是头文件 string.h 中定义的函数：
序号	函数 & 描述
1	void *memchr(const void *str, int c, size_t n)
在参数 str 所指向的字符串的前 n 个字节中搜索第一次出现字符 c（一个无符号字符）的位置。
2	int memcmp(const void *str1, const void *str2, size_t n)
把 str1 和 str2 的前 n 个字节进行比较。
3	void *memcpy(void *dest, const void *src, size_t n)
从 src 复制 n 个字符到 dest。
4	void *memmove(void *dest, const void *src, size_t n)
另一个用于从 src 复制 n 个字符到 dest 的函数。
5	void *memset(void *str, int c, size_t n)
复制字符 c（一个无符号字符）到参数 str 所指向的字符串的前 n 个字符。
6	char *strcat(char *dest, const char *src)
把 src 所指向的字符串追加到 dest 所指向的字符串的结尾。
7	char *strncat(char *dest, const char *src, size_t n)
把 src 所指向的字符串追加到 dest 所指向的字符串的结尾，直到 n 字符长度为止。
8	char *strchr(const char *str, int c)
在参数 str 所指向的字符串中搜索第一次出现字符 c（一个无符号字符）的位置。
9	int strcmp(const char *str1, const char *str2)
把 str1 所指向的字符串和 str2 所指向的字符串进行比较。
10	int strncmp(const char *str1, const char *str2, size_t n)
把 str1 和 str2 进行比较，最多比较前 n 个字节。
11	int strcoll(const char *str1, const char *str2)
把 str1 和 str2 进行比较，结果取决于 LC_COLLATE 的位置设置。
12	char *strcpy(char *dest, const char *src)
把 src 所指向的字符串复制到 dest。
13	char *strncpy(char *dest, const char *src, size_t n)
把 src 所指向的字符串复制到 dest，最多复制 n 个字符。
14	size_t strcspn(const char *str1, const char *str2)
检索字符串 str1 开头连续有几个字符都不含字符串 str2 中的字符。
15	char *strerror(int errnum)
从内部数组中搜索错误号 errnum，并返回一个指向错误消息字符串的指针。
16	size_t strlen(const char *str)
计算字符串 str 的长度，直到空结束字符，但不包括空结束字符。
17	char *strpbrk(const char *str1, const char *str2)
检索字符串 str1 中第一个匹配字符串 str2 中字符的字符，不包含空结束字符。也就是说，依次检验字符串 str1 中的字符，当被检验字符在字符串 str2 中也包含时，则停止检验，并返回该字符位置。
18	char *strrchr(const char *str, int c)
在参数 str 所指向的字符串中搜索最后一次出现字符 c（一个无符号字符）的位置。
19	size_t strspn(const char *str1, const char *str2)
检索字符串 str1 中第一个不在字符串 str2 中出现的字符下标。
20	char *strstr(const char *haystack, const char *needle)
在字符串 haystack 中查找第一次出现字符串 needle（不包含空结束字符）的位置。
21	char *strtok(char *str, const char *delim)
分解字符串 str 为一组字符串，delim 为分隔符。
22	size_t strxfrm(char *dest, const char *src, size_t n)
根据程序当前的区域选项中的 LC_COLLATE 来转换字符串 src 的前 n 个字符，并把它们放置在字符串 dest 中。





# End



# 32bit.c

```c
/*
*	结构体的内存排列
*/
#include <stdio.h>

int main()
{
	struct AAA{
		char a[5];
		int b;
		short int c;
	};

	struct BBB{
		char * d;
		short int e;
		struct AAA f;
		char g;
	};
	union {
        struct BBB bbb;
        unsigned char u[sizeof(struct BBB)];
    } abc;
    int len=sizeof(struct BBB);
    int i;

    for(i=0;i<len;i++)abc.u[i]=0xaa;
    abc.bbb.d=(char*)(0-1);
    abc.bbb.e=0-1;
    abc.bbb.f.a[0]=0-1;
    abc.bbb.f.a[1]=0-1;
    abc.bbb.f.a[2]=0-1;
    abc.bbb.f.a[3]=0-1;
    abc.bbb.f.a[4]=0-1;
    abc.bbb.f.b=0-1;
    abc.bbb.f.c=0-1;
    abc.bbb.g=0-1;

	for(i=0;i<len;i++){
		printf("%3x  ",abc.u[i]);
		if(i%4==3)putchar('\n');
	}
	return 0;
}

```



# union.c

```c
/*
*   利用union共用空间特点，用两种格式输出空间内容
*/

#include <stdio.h>

int main()
{
    union {
        float aaa;
        unsigned char bbb[sizeof(float)];
    } abc;
    int a=sizeof(float),i;
    
    
    abc.aaa=0.5;
    for(i=a-1;i>-1;i--) {
        printf("%02X",(unsigned char)abc.bbb[i]);}
    putchar('\n');
    
    abc.aaa=0.25;
    for(i=a-1;i>-1;i--) {
        printf("%02X",(unsigned char)abc.bbb[i]);}
    putchar('\n');
    
    abc.aaa=0.75;
    for(i=a-1;i>-1;i--) {
        printf("%02X",(unsigned char)abc.bbb[i]);}
    putchar('\n');
    
    
    abc.bbb[0]=0x00;
    abc.bbb[1]=0x00;
    abc.bbb[2]=0x00;
    abc.bbb[3]=0x00;


    printf("%f\n",abc.aaa);
    
    return 0;
}
```



# float.c

```c
/*
*   float内存表示
*/

#include <stdio.h>
int booll(unsigned int n){
    int a[32]={0};
    int i=0;
    while (n>0)
    {
        a[i]=n%2;
        i=i+1;
        n=n/2;
    }
    for(i=31;i>=0;i--){printf("%d",a[i]);if(i==31){putchar(' ');}if(i==23){putchar(' ');}}
    return 0;
}

int main(int argc, const char * argv[]) {
    
    union{
        float f;
        unsigned int c;
    } aaa;
    float i=256+128+64+32+16+8+4+2+1+0.5+0.25+0.125+0.0625+0.03125+0.015625+0.0078125+0.00390625;
    
    i=1.3456;
    for(i; i<999999;i*=2)
    {aaa.f = i;printf("%015.7f__  ",i);booll(aaa.c);putchar('\n');}
    
    aaa.c = 0x3F000000;
    //    printf("%06.7f__  ",aaa.f);booll(aaa.c);
    
    
    printf("\n");
    return 0;
}

```

Memcpy.c

```c
/*
*   字符串空间重叠
*   2019.4.24
*/
#include <string.h>
#include <stdio.h>

void * omemcpy(void *s1, const void * s2,size_t n)
{
    char *su1;
    const char *su2;
    
    //for(su1=s1,su2=s2;0<n;++su1,++su2,--n)*su1 = *su2;
    su1=s1;
    su2=s2;
    for(su1+=n,su2+=n;0<n;--n)*--su1=*--su2;
    return 0;
}

int main() {
    char a[]="1234567890";
    printf("a=%s\n",a);
    char * b=a+1;
    printf("b=%s\n",b);
    //omemcpy(a,b,9);
    memcpy(b,a,9);
    printf("a=%s\n",a);


    
    return 0;
}

```



# Sort.c

```c
/*
*	选择排序
*/
#include <stdio.h>


int * sort(int * arr,int a){
	int index,temp,i,j;
	
	for(i=0;i<(a-1);i++){
		index=i;
		for(j=i+1;j<a;j++){
			if(arr[j]<arr[index])index=j;
		}
		temp=arr[index];
		arr[index]=arr[i];
		arr[i]=temp;
	}
	return 0;
}

int main()
{
	int arr[5]={3,4,2,5,1};
	int i;

	sort(arr,5);
	for(i=0;i<5;i++){printf("  %d",arr[i]);}
   
	return 0;
}
```

# simple calculator.c

```c
/*
*   简易计算器  + - * / %
*   2019.4.25
*/

#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int ownstring(const char * str,int * a,int * b,char * bl)
{
    const char * p;
    ptrdiff_t cha;
    char temp[10];

    p = strpbrk(str,"+-*/%");
    cha = p-str;
    *a=atoi(strncpy(temp,str,cha));
    *bl=p[0];
    *b=atoi(strcpy(temp,p+1));
    return 0;
}

int calcu(int a,int b,char bl )
{
    int r;
    
    switch (bl) {
        case '+':
            r = a+b;
            break;
        case '-':
            r = a-b;
            break;
        case '*':
            r = a*b;
            break;
        case '/':
            r = a/b;
            break;
        case '%':
            r = a%b;
            break;
        default:
            r = 0;
            break;
    }
    
    return r;
}

int main() {
  
    char str[100]="  45 +  54  ";
    //scanf("%s",str);

    int a=0;
    int b=0;
    int r=0;
    char bl=' ';
    
    ownstring(str,&a,&b,&bl);
    r = calcu(a,b,bl);
    if(bl=='%'){
        printf("%d%c%d=%d...%d\n",a,bl,b,calcu(a,b,'/'),r);
    }
    else
    {
        printf("%d%c%d=%d\n",a,bl,b,r);
    }
    return 0;
}

```

