# GTK

linux下c图形化编程之gtk+2.0简单学习 https://www.cnblogs.com/kingos/p/4531738.html
GTK官网 https://www.gtk.org

```bash
# Mac OS 下装GTK

brew install gtk
# ~/.bash_profile 加一行代码
export PKG_CONFIG_PATH="/usr/X11/lib/pkgconfig:/usr/local/Cellar/cairo/1.12.16/lib/pkgconfig/"

gcc gui.c -o gui `pkg-config --cflags --libs gtk+-3.0`
gcc $(pkg-config gtk+-3.0 --cflags) $(pkg-config gtk+-3.0 --libs) gui.c -o gui
./gui
```
```c
//测试代码
#include <gtk/gtk.h>                            //必须引用gtk/gtk.h这个头文件
int main(int argc,char *argv[])                //标准c语言主函数的声明
{
    GtkWidget *window;                        //声明一个窗口控件的指针，其中GtkWidget是gtk+2.0控件类型。window是变量名，与变量类型无关

    gtk_init(&argc,&argv);                    //初始化gtk+环境，在gtk+程序中是必须的

    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    /*用来创建窗口。函数gtk_window_new 创建一个窗口并返回这个窗口的控件指针,这里把指针的值赋给了window这个变量；参数GTK_WINDOW_TOPLEVEL指明窗口的类型为最上层的主窗口，还有一个参数GTK_WINDOW_POPUP指明窗口类型为弹出式无边框窗口*/

    gtk_window_set_title(GTK_WINDOW(window),"hello World");//给window窗口设置标题

    gtk_window_set_default_size(GTK_WINDOW(window),500,500);//给window窗口设置大小
    g_signal_connect(G_OBJECT(window),"destroy",G_CALLBACK(gtk_main_quit),NULL);
    /*事件监听函数，意思是，对于对象window，当"destroy"时间发生的时候，调用gtk_main_quit函数，传递这个函数的参数为NULL，也就是当你点击窗口关闭按钮的时候，结束程序*/

    gtk_widget_show(window);        //显示上一步创建的窗口

    gtk_main();
    /*这个函数是最关键的，它是gtk+2.0的主事件循环，每个gtk+2.0程序都要有一个否则程序无法运行*/
    return FALSE;
    /*代码最后的逻辑返回值为FALSE它相当于整型的0。*/
}
```

# gtk



安装GTK

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
//1安装gcc/g++/gdb/make 等基本编程工具
sudo apt-get install build-essential

//2安装 libgtk2.0-dev libglib2.0-dev 等开发相关的库文件
sudo apt-get install gnome-core-devel

//3用于在编译GTK程序时自动找出头文件及库文件位置
sudo apt-get install pkg-config

//4安装 devhelp GTK文档查看程序
sudo apt-get install devhelp

//5安装 gtk/glib 的API参考手册及其它帮助文档
sudo apt-get install libglib2.0-doc libgtk2.0-doc

//6安装基于GTK的界面GTK是开发Gnome窗口的c/c++语言图形库 
sudo apt-get install glade libglade2-dev

//7安装gtk2.0 或者 将gtk+2.0所需的所有文件统通下载安装完毕
sudo apt-get install libgtk2.0-dev
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

Step 3

验证是否安装成功

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
//1查看 2.x 版本
pkg-config --modversion gtk+-2.0

//2查看pkg-config的版本
pkg-config --version

//3查看是否安装了gtk
pkg-config --list-all grep gtk
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

用一个简单的程序测试一下

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```c
 1 #include <gtk/gtk.h>
 2 
 3 int main(int argc, char *argv[])
 4 {
 5     GtkWidget   *window;
 6     GtkWidget   *label;
 7     
 8     gtk_init(&argc,&argv);
 9     
10     window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
11     gtk_window_set_title(GTK_WINDOW(window),"title");
12     /*
13     label = gtk_label_new("label");
14     gtk_container_add(GTK_CONTAINER(window),label);
15     */
16     
17     // connect the destroy signal of the window to gtk_main_quit
18     // when the window is about to be destroyed we get a notification and
19     // stop the main GTK+ loop
20     
21     g_signal_connect(window,"destroy",G_CALLBACK(gtk_main_quit),NULL);
22 
23     gtk_widget_show_all(window);
24     
25     // start the main loop, and let it rest until the application is closed
26     gtk_main();
27     
28 
29     return 0;
30 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

编译

```
gcc -o ggg gtk.c `pkg-config --cflags --libs  gtk+-2.0`
```

运行

```
./ggg
```

运行时有警告，忽视即可。

https://github.com/memnoth/i8086emu_lnx







# PyGTK

https://pygobject.readthedocs.io/en/latest/

简介 https://www.cnblogs.com/ruiy/p/11639458.html
