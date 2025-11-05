

https://docs.microsoft.com/zh-cn/shows/


https://support.microsoft.com/zh-cn/help/12445/windows-keyboard-shortcuts win10快捷键

# 端口被占用的解决方法

```bat
netstat -ano | findstr 8080
最后一项是PID
tasklist | findstr 11416 -kill
```

# hosts文件的修改方式

hosts属性右键->安全->组或用户名->Administrators或Users权限都打开

```bash
# 添加语句
# 用浏览器打开www.aaa.com:8080会映射到127.0.0.1:8080
127.0.0.1 demo.com

# 下面的写法无效，不能连续跳转
127.0.0.1 192.168.0.103
192.168.0.103 dd.com
```




# Batch

https://en.wikipedia.org/wiki/Batch_file

https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-xp/bb490890(v=technet.10)

https://www.jb51.net/list/list_106_1.htm


```bat
::一直调试
@echo off
set n=0
:abc
set /a n+=1

@echo ---------------------------
python.exe a.py

echo WScript.sleep 2000 > sleep.vbs
Wscript sleep.vbs
cls
if %n%==600 exit
goto abc
```


```bat

netstat -ano 查询端口
```






# Win32 API
https://learn.microsoft.com/en-us/windows/win32/api/




# Windbg
windows dbg可以查看系统寄存器内存之类的信息
https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/



# DebugView
www.sysinternals.com
https://learn.microsoft.com/zh-cn/sysinternals/
https://learn.microsoft.com/zh-cn/archive/blogs/markrussinovich/















