








https://en.wikipedia.org/wiki/Algorithm

github
https://the-algorithms.com/
https://github.com/TheAlgorithms



# 算法题库

最适合程序员编程刷题的网站，你用过几个？
https://blog.csdn.net/hello_hxx/article/details/81188321
有哪些好的刷题网站？2017年最受欢迎的编程挑战网站
https://blog.csdn.net/qq_38822390/article/details/82887091

https://leetcode.com LeetCode
https://leetcode-cn.com/ LeetCode-cn
https://www.codility.com/ Codility
https://www.hackerrank.com/ HackerRank 刷完LeetCode,来这个研究算法
https://www.codechef.com/ CodeChef
http://www.programmingbydoing.com/ Programmingbydoing
https://www.nowcoder.com/ Nowcoder
https://www.lintcode.com/ lint code
https://www.coderbyte.com/ coderbyte
https://www.topcoder.com/ topcoder
https://www.freecodecamp.org/ web练习题
http://atcoder.jp 日本算法竞技网站AcCoder
https://acm.timus.ru 俄罗斯的在线测评系统Timus Online Judge
波兰最大的在线测评系统Sphere Online Judge(简称“SPOJ”)
https://www.spoj.com
面向平面设计师和程序员的网站TopCoder
https://www.topcoder.com
一个团队创立的在线测评系统Codeforces
http://codeforces.com/
如何更好的提升自己(程序员)？ - 程序员客栈的回答 - 知乎
https://www.zhihu.com/question/63386327/answer/1519551723
有程序员专门刷题的网站吗？
https://www.zhihu.com/question/36488823
https://www.cs.usfca.edu/~galles/visualization/Algorithms.html






# Algorithm

叫不上名字的算法

## 动态规划算法
动态规划算法(dynamic)

背包问题


## 分治算法

分治(Divide-and-Conquer(P))把一个复杂问题分成两个或多个相同或相似的子问题, 再分解子问题变成更小的子问题, 直到最后求出简单解, 
如 快速排序,归并排序, 傅里叶变换(快速傅里叶变换)
二分搜索 大整数乘法 棋盘覆盖 合并排序 快速排序 线性时间选择 最接近点对问题 循环赛日程表 汉诺塔

分治算法三个步骤: 分解 解决 合并


## 贪心算法

贪心算法(greedy): 在每一步都选择最好或者最优的算法




## KMP

https://blog.csdn.net/weixin_63426509/article/details/125091506
https://blog.csdn.net/qq_43869106/article/details/128753527
https://blog.csdn.net/A642960662/article/details/123150426
https://zhuanlan.zhihu.com/p/634760691
https://blog.csdn.net/DADONGOOO/article/details/128761315


暴力匹配算法
字符串匹配算法, 通过next数组来决定跳过的索引值



## 汉诺塔

汉诺塔(Hanoitower),




## 马踏棋盘算法

马踏棋盘算法(Horse Chess Board), 本质上是图的遍历算法

先用暴力遍历来寻找解
贪心算法,尽可能走最大解












# Data Structures

1.集合：数据结构中的元素之间除了“同属一个集合” 的相互关系外，别无其他关系
2.线性结构：数据结构中的元素存在一对一的相互关系
3.树形结构：数据结构中的元素存在一对多的相互关系
4.图形结构：数据结构中的元素存在多对多的相互关系
在计算机科学的发展过程中，数据结构也随之发展。程序设计中常用的数据结构包括如下几个



# Collection


Recursion
SparseArray





## Array


https://baike.baidu.com/item/数组/3794097 是一种聚合数据类型，它是将具有相同类型的若干变量有序地组织在一起的集合。数组可以说是最基本的数据结构，在各种编程语言中都有对应。一个数组可以分解为多个数组元素，按照数据元素的类型，数组可以分为整型数组、字符型数组、浮点型数组、指针数组和结构数组等。数组还可以有一维、二维以及多维等表现形式



## List
线性表 https://baike.baidu.com/item/线性表/3228081

Operation
InitList(*L) 初始化操作
ListEmpty(L) 判断是否为空 空true/否则false
ClearList(*L) 将线性表清空
GetElem(L,i,*e) 将i个元素返回给e
LocateElem(L,e) 查找给定值与e相等的元素, 成功返回元素序号
ListInsert(*L,i,e) 第i个位置插入新元素e
ListDelete(*L,i,*e) 删除i个位置元素，返回e
ListLength(L) 返回线性表L的元素个数





## Stack

https://baike.baidu.com/item/栈/12808149 栈是一种特殊的线性表，它只能在一个表的一个固定端进行数据结点的插入和删除操作。栈按照后进先出的原则来存储数据，也就是说，先插入的数据将被压入栈底，最后插入的数据在栈顶，读出数据时，从栈顶开始逐个读出。栈在汇编语言程序中，经常用于重要数据的现场保护。栈中没有数据时，称为空栈
实际应用：撤销

## Queue

https://baike.baidu.com/item/队列/14580481 队列和栈类似，也是一种特殊的线性表。和栈不同的是，队列只允许在表的一端进行插入操作，而在另一端进行删除操作。一般来说，进行插入操作的一端称为队尾，进行删除操作的一端称为队头。队列中没有元素时，称为空队列


## Linked List

https://baike.baidu.com/item/链表/9794473 链表是一种数据元素按照链式存储结构进行存储的数据结构，这种存储结构具有在物理上存在非连续的特点。链表由一系列数据结点构成，每个数据结点包括数据域和指针域两部分。其中，指针域保存了数据结构中下一个元素存放的地址。链表结构中数据元素的逻辑顺序是通过链表中的指针链接次序来实现的

# Tree

https://baike.baidu.com/item/树/2699484 树是典型的非线性结构，它是包括，2个结点的有穷集合K。在树结构中，有且仅有一个根结点，该结点没有前驱结点。在树结构中的其他结点都有且仅有一个前驱结点，而且可以有两个后继结点，m≥0



## Binary Tree
二叉树

遍历



## Heap

https://baike.baidu.com/item/堆/20606834 堆是一种特殊的树形数据结构，一般讨论的堆都是二叉堆。堆的特点是根结点的值是所有结点中最小的或者最大的，并且根结点的两个子树也是一个堆结构

## Hash

https://baike.baidu.com/item/散列函数/2366288

散列表源自于散列函数(Hash function)，其思想是如果在结构中存在关键字和T相等的记录，那么必定在F(T)的存储位置可以找到该记录，这样就可以不用进行比较操作而直接取得所查记录



# Graph

https://baike.baidu.com/item/图/13018767 图是另一种非线性数据结构。在图结构中，数据结点一般称为顶点，而边是顶点的有序偶对。如果两个顶点之间存在一条边，那么就表示这两个顶点具有相邻关系



# 算法操作

数据结构研究的内容：就是如何按一定的逻辑结构，把数据组织起来，并选择适当的存储表示方法把逻辑结构组织好的数据存储到计算机的存储器里。算法研究的目的是为了更有效的处理数据，提高数据运算效率。数据的运算是定义在数据的逻辑结构上，但运算的具体实现要在存储结构上进行。一般有以下几种常用运算

(1)检索。检索就是在数据结构里查找满足一定条件的节点。一般是给定一个某字段的值，找具有该字段值的节点
(2)插入。往数据结构中增加新的节点
(3)删除。把指定的结点从数据结构中去掉
(4)更新。改变指定节点的一个或多个字段的值
(5)排序。把节点按某种指定的顺序重新排列。例如递增或递减








# 算法复杂度

```
事后统计法,依据与具体的硬件,运行该程序,进行评测
事前估算法,通过分析某个算法的时间复杂度来判断

时间频度: 算法花费的时间与算法中语句执行的次数成正比,算法中语句执行次数成为时间频度,记为T(n)
时间复杂度忽略常数项,如果有高次方则忽略低次方,次方前的系数
算法时间复杂度由小到大依次为
T(n)=O(1) 常数阶 没有循环等复杂结构,仅按流程执行结束
T(n)=O(log2n) 对数阶 int i=1;while(i<n){i=i*2;}
T(n)=n 线性阶
T(n)=O(nlog2n) 线性对数阶 for(m=1;m<n;m++){i=1;while(1<n){i=i*2;}}
T(n)=O(n^2) 平方阶
T(n)=O(n^3) 立方阶
T(n)=O(n^k) k次方阶
T(n)=O(2^n) 指数阶
其他 O(n!)n的阶乘 

空间复杂度,在算法设计当中,可以牺牲内存空间来换取时间,从而提升程序的执行速度

```




# Sort


https://en.wikipedia.org/wiki/Sorting_algorithm

github project
https://github.com/TheAlgorithms/C/tree/master/sorting


内部排序,在内存中,原地排序,不使用额外的空间进行排序
外部排序,数据量过大,先加载一部分,再加载另一部分,借助外部存储器存储


straight insertion sort Insertion Sorting 直接插入排序
Shell Sorting 希尔排序(分组插入排序)


Select Sorting 选择排序
堆排序


Bubble Sorting 冒泡排序
Quick Sorting 快速排序


Merge Sorting 归并排序
Radix Sorting 基数排序(桶排序升级版)


```c




#include <stdio.h>

//交换两个数
void swap(int *first, int *second) {
    int temp = *first;
    *first = *second;
    *second = temp;
}

// 显示数组
void display(const int *arr, int size) {
    //  int i, a[] = {5, 2, 6, 0, 3, 9, 1, 7, 4, 8};
    printf("arr[] = {");
    for (int i = 0; i < size; i++) {
        printf("%d, ", arr[i]);
    }
    printf("\b\b}\n");
}

//冒泡排序
void bubble_sort(int *arr, int size) {
    char swapped = 1;
    for (int i = 0; i < size - 1 && swapped; i++) {
        swapped = 0;
        for (int j = 0; j < size - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(&arr[j], &arr[j + 1]);
                swapped = 1;
            }
        }
    }
}

//选择排序
void selection_sort(int *arr, int size) {
    for (int i = 0; i < size - 1; ++i) {
        int min_index = i;
        for (int j = i + 1; j < size; ++j) {
            if (arr[min_index] > arr[j]) {
                min_index = j;
            }
        }
        if (min_index != i) {
            swap(&arr[i], &arr[min_index]);
        }
    }
}

// 插入排序
void insertion_sort(int *arr, int size) {
    for (int i = 1; i < size; ++i) {
        int j = i - 1;
        int key = arr[i];
        while (j >= 0 && key < arr[j]) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

// 希尔排序, 插入排序的变体, 分组插入排序
void shell_sort(int *arr, int size) {
    for (int gap = 5; gap > 0; --gap) {
        for (int i = gap; i < size; i += gap) {
            int j = i - gap;
            int key = arr[i];
            while (j >= 0 && key < arr[j]) {
                arr[j + gap] = arr[j];
                j -= gap;
            }
            arr[j + gap] = key;
        }
    }
}

int main(int argc, char *argv[]) {
    int size, arr[] = {5, 2, 6, 0, 3, 9, 1, 7, 4, 8};
    size = sizeof(arr) / sizeof(int);

//    bubble_sort(arr, size);
//    selection_sort(arr, size);
//    insertion_sort(arr, size);
    shell_sort(arr, size);
    display(arr, size);
    return 0;
}




```


# Search

搜索算法

SeqSearch 顺序(线性)查找
BinarySearch 二分查找
InsertValueSearch 插值查找
FibonacciSearch 斐波那契查找













# leetcode

初级算法 https://leetcode-cn.com/leetbook/detail/top-interview-questions-easy/
中级算法 https://leetcode-cn.com/leetbook/detail/top-interview-questions-medium/
高级算法 https://leetcode-cn.com/leetbook/detail/top-interview-questions-hard/

旋转数组，数组第三题

```c++
//给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数
class Solution{
public:
  void rotate(vector<int>& nums, int k){
    int len=nums.size();
    k%=len;
    if(k==0||len==1) return ;
    int temp;        
    temp=nums[0];
    int count = 0;
    for(int i=k,cnt=0;cnt<len;i+=k,cnt++){
  		int t=nums[i%len];
      nums[i%len]=temp;
      temp=t;
      if(i%len==count){
      	count++;
        i = count;
        temp = nums[(i) % len];
      }
    }
  }
};
```

只出现一次的数字，两个数组的交集 II 和 两数之和





















