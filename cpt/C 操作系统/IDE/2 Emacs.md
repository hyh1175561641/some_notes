







# Emacs


https://www.gnu.org/software/emacs
https://jblevins.org/projects/markdown-mode/ Markdown

https://emacsformacosx.com Emacs For Mac OS X

https://blog.csdn.net/SCHOLAR_II/article/details/80976314 工欲善其事，必先利其器之—MAC下安装与配置emacs
https://blog.csdn.net/redguardtoo/article/details/7222501 一年成为Emacs高手(像神一样使用编辑器)

《学习GNU Emacs (第二版)》[美]卡马伦著 机械工业出版社 ISBN 978-7111103486


概念
buffer缓冲区：整个文件的内容区域
：最下方输入命令的一行



快捷键:C-表示CONTROL键，有时以CTRL或者CTL表示
M-表示META键，有时用EDIT或者ALT表示，如果没有适合的键，可以用ESC代替

帮助信息
C-h ? 帮助命令
C-h k C-f 下一个字母命令的文档



命令行操作
C-g退出一个正在运行中的命令
错误摁下Esc时，连摁两次Esc取消命令

```
# 前缀参数
C-u重复执行命令（填写一个数字）
或者按住 META 键不放，然后输入数字
C-u 8 C-f向前移动8个字符
C-u 8 C-v文本向下滚动8行
C-u 0 C-l光标显示在第几行
```

```
# 有些命令被禁用了，会显示提示消息，然后询问是否执行
C-x C-l用n回答询问
```




```bash
# 光标移动
C-n下一行（Next）
C-p上一行（previous）
C-f下一个字母（forward）
C-b上一个字母（Backward）
M-f下一个单词
M-b上一个单词
C-l光标移动到屏幕中央，上端，下端切换（line）
C-v移动到下一屏（PageDn）
M-v移动到上一屏（PageUp）
C-a移动到行首（beginning）
C-e移动到行尾（end）
M-a移动到句首
M-e移动到句尾
M-<移动到最开头（摁下shift）
M->移动到最末尾（摁下shift）

```


```bash
# 插入删除
普通字符键输入字符
C-u 8 \*插入8个\*字符
Return换行
Delete删除上一个字符
C-d删除下一个字符

# 移除
M-Delete移除上一个单词
M-d移除下一个单词
C-k移除光标到行尾之间的字符(kill-line)
M-k移除光标到句尾之间的字符

# 通用的移除（剪切）
设置起点之后移动光标，移动到合适的位置再剪切，
C-SPACE 设置起点（Mark set标志）
C-w 两点之间的文字被移除

```


```bash
# 复制粘贴
“移除（kill）”和“删除（delete）”的不同在于被移除的东西可以被重新插入（在任何位置），而被删除的就不能使用相同的方法重新插入了（不过可以通过撤销一个删除命令来做到）

连续的移除操作会拼接起来


```









```bash
# 文件操作
C+x C+f 打开文件
C+x C+s 保存文件

```

```bash
# 窗口操作
C-x 1保留一个窗口

```










配置

解决emacs自动产生备份文件的烦恼
给  ~/.emacs 文件末尾添加两行代码

```shell
;; all backups goto ~/.backups instead in the current directory
(setq backup-directory-alist (quote (("." . "~/.backups"))))
```











