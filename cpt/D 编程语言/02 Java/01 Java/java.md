



在成熟的工业软件中，需要检测输入值和形参的区间

我的代码和老师的代码相比：老师的输出比较简单，但是本质算法都差不多

```java
// 修改一：在真实代码当中，需要输入检测区间
Scanner in = new Scanner(System.in);
System.out.println("请输入一个正整数：");
int n = in.nextInt();
while (n <= 0) {
    System.out.println("请重新输入一个正整数：");
    n = in.nextInt();
}
```



```java
// 修改二：在这个地方是不是有什么发现呢。循环所做的事情就比上一行添加一个东西
// 找一找这一行比上一行所添加的东西是什么，多出来一些什么，而不是按照顺序想办法输出
    System.out.print(i + "的阶乘：");
    for (int j = i; j >= 1; j--) {
        if (factorial > 1) {
            System.out.print(j + "*");
        }
    }
    if (factorial == 1) {
        System.out.println(factorial);
    } else {
        System.out.println("\b=" + factorial);
	}
	// 老师的输出
    if (i == 1) {
        expr = "1";
    } else {
        expr = i + "*" + expr; //字符串拼接，倒序拼接，从1开始在开头拼接，妙啊
    }
    System.out.println(i + "的阶乘：" + (i == 1 ? "1" : (expr + "=" + result)));
/* 输出的目标
1的阶乘：1
2的阶乘：2*1=2
3的阶乘：3*2*1=6
4的阶乘：4*3*2*1=24
5的阶乘：5*4*3*2*1=120
*/
```



```java
// 这个地方是否修改成更好的代码
    for (int i = 1; i <= c; i++) {
        if (i == 1) {
            System.out.print(i);
        } else {
            System.out.print("+" + i + "!");
        }
    }
    System.out.println("=" + result);
    
/*
老师的 1+2!+...+5!=153
我的一 1+2!+3!+4!+5!+6!+7!+8!+9!+10!+11!+12!=522956313
*/
```





```java
// 老师写的代码
package lianxis04;
import java.util.Scanner;
public class LianXi02 {
    public static void main(String[] args) {
        //1.控制台输入一个正整数
        Scanner in = new Scanner(System.in);
        System.out.println("请输入一个正整数：");
        int n = in.nextInt();
        System.out.println();

        //2.遍历求从1-n：
        // 计算每个数的阶乘；
        // 累加每个数的阶乘；
        // 输出每个数的阶乘表达式；
        int sum = 0;       //求和
        int result = 1;    //每个数的阶乘结果
        String expr = "";  //每个数的阶乘表达式
        for (int i = 1; i <= n; i++) {
            result *= i;   //计算i的阶乘结果 result= result*i;
            sum += result; //将i的阶乘结果累加到sum和

            //输出i的阶乘表达式
            if (i == 1) {
                expr = "1";
            } else {
                expr = i + "*" + expr;
            }
            System.out.println(i + "的阶乘：" + (i == 1 ? "1" : (expr + "=" + result)));
        }
        System.out.println();
        //3.输出结果
        System.out.println("1+2!+...+" + n + "!=" + sum);
    }
}

// 我写的代码
public static void main(String[] args){
	// 阶乘之和
    Scanner sc = new Scanner(System.in);
    System.out.print("请输入一个正整数：");
    int c = sc.nextInt();
    //int c = 5;
    int result = 0;
    int factorial = 1;
    for (int i = 1; i <= c; i++) {
        factorial *= i;
        System.out.print(i + "的阶乘：");
        for (int j = i; j >= 1; j--) {
            if (factorial > 1) {
                System.out.print(j + "*");
            }
        }
        if (factorial == 1) {
            System.out.println(factorial);
        } else {
            System.out.println("\b=" + factorial);
        }
        result += factorial;
    }
    for (int i = 1; i <= c; i++) {
        if (i == 1) {
            System.out.print(i);
        } else {
            System.out.print("+" + i + "!");
        }
    }
    System.out.println("=" + result);
}
```

