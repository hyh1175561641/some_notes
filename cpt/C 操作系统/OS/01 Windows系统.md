

https://docs.microsoft.com/zh-cn/shows/


https://support.microsoft.com/zh-cn/help/12445/windows-keyboard-shortcuts win10快捷键









# Win11三步激活


管理员运行CMD


```bash

slmgr # Windows软件授权管理工具

slmgr /ipk PW48G-MNG8W-B9978-YWBRP-76DGY # 安装产品密钥
slmgr /skms kms.loli.best # 设置KMS计算机的名称
slmgr /ato # 激活Windows

# 其他命令
slmgr /xpr # 是否被成功激活
slmgr /dli # 显示许可证信息
slmgr /dlv # 显示详细的许可证信息




# 也行
slmgr -ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr -skms kms.0t.net.cn
slmgr -ato


```

操作系统版本	KMS 客户端产品密钥
Windows 11 专业版
Windows 10 专业版	W269N-WFGWX-YVC9B-4J6C9-T83GX
Windows 11 专业版 N
Windows 10 专业版 N	MH37W-N47XK-V7XM9-C7227-GCQG9
Windows 11 专业工作站版
Windows 10 专业工作站版	NRG8B-VKK3Q-CXVCJ-9G2XF-6Q84J
Windows 11 专业工作站版 N
Windows 10 专业工作站版 N	9FNHH-K3HBT-3W4TD-6383H-6XYWF
Windows 11 专业教育版
Windows 10 专业教育版	6TP4R-GNPTD-KYYHQ-7B7DP-J447Y
Windows 11 专业教育版 N
Windows 10 专业教育版 N	YVWGF-BXNMC-HTQYQ-CPQ99-66QFC
Windows 11 教育版
Windows 10 教育版	NW6C2-QMPVW-D7KKK-3GKT6-VCFB2
Windows 11 教育版 N
Windows 10 教育版 N	2WH4N-8QGBV-H22JP-CT43Q-MDWWJ
Windows 11 企业版
Windows 10 企业版	NPPR9-FWDCX-D2C8J-H872K-2YT43
Windows 11 企业版 N
Windows 10 企业版 N	DPH2V-TTNVB-4X9Q3-TJR4H-KHJW4
Windows 11 企业版 G
Windows 10 企业版 G	YYVX9-NTFWV-6MDM3-9PT4T-4M68B
Windows 11 企业版 G N
Windows 10 企业版 G N	44RPN-FTY23-9VTTB-MP9BX-T84FV 
总结：win11各种版本激活方法+密钥 命令激活无需第三方软件（win10也适用）





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















