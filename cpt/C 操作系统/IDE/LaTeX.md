








# 链接


https://mhchem.github.io/MathJax-mhchem/ MathJax_Github

http://support.typora.io/Math/ 数学支持

http://docs.mathjax.org/en/latest/tex.html#supported-latex-commands TeX Commands available in Typora




$$
\begin{align*}
y = y(x,t) &= A e^{i\theta} \\
&= A (\cos \theta + i \sin \theta) \\
&= A (\cos(kx - \omega t) + i \sin(kx - \omega t)) \\
&= A\cos(kx - \omega t) + i A\sin(kx - \omega t)  \\
&= A\cos \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big) + i A\sin \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big)  \\
&= A\cos \frac{2\pi}{\lambda} (x - v t) + i A\sin \frac{2\pi}{\lambda} (x - v t)
\end{align*}
$$

$$
f = \frac{2 \pi}{T}
$$

Here is a labeled equation: 
$$
x+1\over\sqrt{1-x^2}\label{ref1}
$$
This is a referece : $\ref{ref1}$



Here is a labeled equation: $$ x+1\over\sqrt{1-x^2}\label{ref1} $$ This is a referece : $\ref{ref1}$





# 运算符表示法

**换行与分割**
$$
\\表示换行
{表示单个}{元素}\\
a \quad b\\
a\ b\\
a\;b\\
a\,b\\
$$

1. 使用\ 表示空格，以及调整空格的大小
quad空格 a \qquad b 两个m的宽度
quad空格 a \quad b 一个m的宽度
大空格 a\ b 1/3m宽度
中等空格 a\;b 2/7m宽度
小空格 a\,b 1/6m宽度
没有空格 ab
紧贴 a\!b 缩进1/6m宽度
\quad、1em、em、m代表当前字体下接近字符‘M’的宽度。
原文链接：https://blog.csdn.net/luolang_103/article/details/81289529

**上标下标**
$$
下标3_4
上标3^4
3_{4^2}
$$

**分数**
$$
{{表示在上边}\over{表示分子}}\\

{{3}\over{4}}
$$


$$
f = \frac{2 \pi}{T}
$$







**\left(&\right)**

左括号和右括号
$$
\left(
\right)
$$



$$
\left(    aaa\right)^2
$$

**分数**
$$
\frac 3 5
$$



**根号**
$$
4次方x^4，x^2\\
4次方根\sqrt[4]3，\sqrt 2
$$

# \ce

chemical equations (ce) 化学方程，化学反应式



$$
\ce{CO2 + C -> 2CO}
$$





# 符号

$$
约等于\approx approx
$$


# 希腊字母

$$
\\\Omega
$$

$$
\sin(\Omega) \\\cos(\mu A)
$$



| 大写 | 小写 | 英文读音 | 国际音标       | 意义                                         |
| ---- | ---- | -------- | -------------- | -------------------------------------------- |
| Α    | α    | alpha    | /ˈælfə/        | 角度，系数，角加速度                         |
| Β    | β    | beta     | /'beitə/       | 磁通系数，角度，系数                         |
| Γ    | γ    | gamma    | /'g&aelig;mə/  | 电导系数，角度，比热容比                     |
| Δ    | δ    | delta    | /'deltə/       | 变化量，屈光度，一元二次方程中的判别式       |
| Ε    | ε    | epsilon  | /ep'silon/     | 对数之基数，介电常数                         |
| Ζ    | ζ    | zeta     | /'zi:tə/       | 系数，方位角，阻抗，相对粘度                 |
| Η    | η    | eta      | /'i:tə/        | 迟滞系数，效率                               |
| Θ    | θ    | theta    | /'θi:tə/       | 温度，角度                                   |
| Ι    | ι ℩  | iota     | /ai'oute/      | 微小，一点                                   |
| Κ    | κ    | kappa    | /k&aelig;pə/   | 介质常数，绝热指数                           |
| ∧    | λ    | lambda   | /'l&aelig;mdə/ | 波长，体积，导热系数                         |
| Μ    | μ    | mu       | /mju:/         | 磁导系数，微，动摩擦系（因）数，流体动力粘度 |
| Ν    | ν    | nu       | /nju:/         | 磁阻系数，流体运动粘度,光子频率              |
| Ξ    | ξ    | xi       | /ksi/          | 随机数，（小）区间内的一个未知特定值         |
| Ο    | ο    | omicron  | /oumaik'rən/   | 高阶无穷小函数                               |
| ∏    | π    | pi       | /pai/          | 圆周率，π(n)表示不大于n的质数个数            |
| Ρ    | ρ    | rho      | /rou/          | 电阻系数，柱坐标和极坐标中的极径，密度       |
| ∑    | σ ς  | sigma    | /'sigmə/       | 总和，表面密度，跨导，正应力                 |
| Τ    | τ    | tau      | /tau/          | 时间常数，切应力                             |
| Υ    | υ    | upsilon  | /ju:p'silən/   | 位移                                         |
| Φ    | φ    | phi      | /fai/          | 磁通，角，透镜焦度，热流量                   |
| Χ    | χ    | chi      | /kai/          | 统计学中有卡方(χ^2)分布                      |
| Ψ    | ψ    | psi      | /psai/         | 角速，介质电通量                             |
| Ω    | ω    | omega    | /'oumigə/      | 欧姆，角速度，交流电的电角度，质量分数       |







# 流程图

```flow
st=>start: 用户登陆
op=>operation: 登陆操作
cond=>condition: 登陆成功 Yes or No?
e=>end: 进入后台

st->op->cond
cond(yes)->e
cond(no)->op
```

```seq
Andrew->China: Says Hello
Note right of China: China thinks\nabout it
China-->Andrew: How are you?
Andrew->>China: I am good thanks!
```







