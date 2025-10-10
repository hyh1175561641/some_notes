

# office

relatorio
pypdf2
reportlab
pdfminer
pdfminer3k
pdfplumber
pymupdf

win32com 只能在Windows使用的office库
unoconv LibreOffice库
tablib

snowNLP 自然语言处理
textBlob
TextGrocery


密码访问
keyring

任务执行器
schedule

https://pyautogui.readthedocs.io/en/latest/
https://github.com/asweigart/pyautogui


# Excel

小于10万条数据用Excel, 大于10万条数据用MySQL

https://www.python-excel.org/

openpyxl 这个好用,性能不稳定
https://pypi.org/project/openpyxl/
https://openpyxl.readthedocs.io/en/stable/
https://bitbucket.org/openpyxl/openpyxl/src/master/ 空仓库, 重定向到下面链接
https://foss.heptapod.net/openpyxl/openpyxl 有东西

XlsxWriter 必要时这个可以代替xlwt, 不带格式
https://pypi.org/project/XlsxWriter/
https://xlsxwriter.readthedocs.io/
https://github.com/jmcnamara/XlsxWriter

xlrd 读取xlsx
https://pypi.org/project/xlrd/
https://xlrd.readthedocs.io/en/latest/
https://github.com/python-excel/xlrd

xlwt 写入 基本不用
https://pypi.org/project/xlwt/
https://xlwt.readthedocs.io/en/latest/
https://github.com/python-excel/xlwt

xlutils 支持修改格式
https://pypi.org/project/xlutils/
https://xlutils.readthedocs.io/en/latest/
https://github.com/python-excel/xlutils

xlwings


```sh

# install module/packages
pip install xlrd=1.2.0
python -m pip install xlrd==1.2.0
pip install xlwt=1.3.0
pip install xlutils=2.0.0

# open browse documentation
python -m pydoc -b

```
一些概念
workbook(工作簿): 整个xlsx文件
sheet: 一张表格
rows: 行(123456...)
columns: 列(ABCDEF...)
cell: 单元格

```python
import xlrd

# Open workbook
book = xlrd.open_workbook('x.xlsx')
print(book.nsheets)
print(book.sheet_names())

# Select sheet
sheet = book.sheet_by_index(0)
print(sheet.name, sheet.nrows, sheet.ncols)

# Print a cell
print(sheet.cell_value(rowx=1, colx=0))
print(sheet.cell(1, 2).value)

# Print a row or a columns
print(sheet.row(1)[2].value)
print(sheet.col(1)[1].value)

# Print all content by row
for rowx in range(sheet.nrows):
    print(sheet.row(rowx))

# Print all content by columns
for colx in range(sheet.ncols):
    print(sheet.col(colx))

# Print sheet name and first data
for index in range(0, book.nsheets):
    sheet = book.sheet_by_index(index)
    print(sheet.name)
    print(sheet.cell_value(0, 0))

# Print sheet name and first data
for name in book.sheet_names():
    sheet = book.sheet_by_name(name)
    print(name)
    print(sheet.cell_value(0, 0))

```


```py
import xlwt

# Create a new workbook
book = xlwt.Workbook()
# Add a sheet
sheet = book.add_sheet('new_sheet')
# Add new data
sheet.write(0, 0, 'Name')
# Save workbook
book.save('new_xls.xls')

```

```py
# xlutils Lib examples
import xlrd
import xlwt
from xlutils.copy import copy

# 获取到格式信息,才能读取和修改xlsx的格式
# book = xlrd.open_workbook('x.xlsx')  # formatting_info=True
book = xlrd.open_workbook('x.xlsx', formatting_info=True)
sheet = book.sheet_by_index(0)

new_book = copy(book)
new_sheet = new_book.get_sheet(0)

style = xlwt.XFStyle()

# Setting Font
font = style.font
font.name = '微软雅黑'
font.bold = True
font.height = 360  # 18*20
style.font = font

# Setting borders
borders = xlwt.Borders()
borders.top = xlwt.Borders.THIN
borders.bottom = xlwt.Borders.THIN
borders.left = xlwt.Borders.THIN
borders.right = xlwt.Borders.THIN
style.borders = borders

# alignment
alignment = xlwt.Alignment
alignment.horz = xlwt.Alignment.HORZ_CENTER
alignment.vert = xlwt.Alignment.VERT_CENTER
style.alignment = alignment

# Add data 写上style不能用, 这套py库不好用其实
new_sheet.write(2, 1, 12, style)
new_sheet.write(3, 1, 18, style)
new_sheet.write(4, 1, 19, style)
new_sheet.write(5, 1, 15, style)

new_book.save('x2.xlsx')


```



# Word

textract 文字识别与提取
https://pypi.org/project/textract/
https://github.com/deanmalmgren/textract

python-docx
https://pypi.org/project/python-docx/
https://python-docx.readthedocs.io/en/latest/
https://github.com/python-openxml/python-docx
https://blog.csdn.net/Trb601012/article/details/136293590




```py

from docx import Document
from docx.shared import Inches

document = Document()

document.add_heading('Document Title', 0)

p = document.add_paragraph('A plain paragraph having some ')
p.add_run('bold').bold = True
p.add_run(' and some ')
p.add_run('italic.').italic = True

document.add_heading('Heading, level 1', level=1)
document.add_paragraph('Intense quote', style='Intense Quote')

document.add_paragraph(
    'first item in unordered list', style='List Bullet'
)
document.add_paragraph(
    'first item in ordered list', style='List Number'
)

document.add_picture('monty-truth.png', width=Inches(1.25))

records = (
    (3, '101', 'Spam'),
    (7, '422', 'Eggs'),
    (4, '631', 'Spam, spam, eggs, and spam')
)

table = document.add_table(rows=1, cols=3)
hdr_cells = table.rows[0].cells
hdr_cells[0].text = 'Qty'
hdr_cells[1].text = 'Id'
hdr_cells[2].text = 'Desc'
for qty, id, desc in records:
    row_cells = table.add_row().cells
    row_cells[0].text = str(qty)
    row_cells[1].text = id
    row_cells[2].text = desc

document.add_page_break()

document.save('demo.docx')


```





# ppt

python-pptx
https://pypi.org/project/python-pptx/
https://python-pptx.readthedocs.io/en/latest/index.html
https://github.com/scanny/python-pptx


```py

from pptx import Presentation

prs = Presentation()
title_slide_layout = prs.slide_layouts[0]
slide = prs.slides.add_slide(title_slide_layout)
title = slide.shapes.title
subtitle = slide.placeholders[1]

title.text = "Hello, World!"
subtitle.text = "python-pptx was here!"

prs.save('test.pptx')

```














# 数据可视化

numpy
http://www.numpy.org/
https://github.com/numpy/numpy

SciPy
https://www.scipy.org/
https://github.com/scipy/scipy

Matplotlib
https://matplotlib.org/
https://github.com/matplotlib/matplotlib

pandas
https://pandas.pydata.org/
https://pandas.pydata.org/docs/
https://pypi.org/project/pandas/


```py
# python -m pip install pandas
import pandas

one_d = pandas.Series(['a', 'b', 'c', 'd'])
print(one_d)

two_d = pandas.DataFrame({
    'No': ['A2', 'A3'],
    'name': ['Bob', 'John'],
    'art': ['68', '68'],
})
print(two_d)

```


```py
import numpy
import pandas

workbook = pandas.ExcelFile('x.xlsx')
sheet = workbook.parse('Sheet1')
print(sheet)

# 各省的分数和
pt = pandas.pivot_table(sheet, index=['省份'], aggfunc=numpy.sum, margins=True)
# 各省的个数
pt2 = pandas.pivot_table(sheet, index=['省份'], aggfunc=numpy.size, margins=True)
print(pt)
print(pt.iat[0, 0])
print(pt2)
print(pt2.iat[0, 0])

```

```py
import matplotlib.pyplot as mplt

mplt.rcParams['font.sans-serif'] = ['SimHei']
date = ['2020/7/21', '2020/7/22', '2020/7/23', ]
yue = [10, 70, 30]
min = [40, 50, 60]

# 折线图
mplt.plot(date, yue, color='red', label='广东')
mplt.plot(date, min, color='blue', label='福建')
mplt.title('降雨量')
mplt.xlabel('日期')
mplt.ylabel('降雨量')
mplt.legend()
mplt.show()

# 柱状图和水平柱状图
mplt.bar(date, yue, color='red', label='广东')
mplt.barh(date, min, color='blue', label='福建')
mplt.legend()
mplt.show()

# 饼状图
data = [1, 2]
province = ['广东', '福建']
colors = ['red', 'blue']
mplt.pie(x=data, labels=province, colors=colors)
mplt.legend()
mplt.show()

```


```py


```




# wxpy
微信机器人
https://wxpy.readthedocs.io/zh/latest/
https://github.com/youfou/wxpy

钉钉机器人
https://pypi.org/project/DingtalkChatbot/
https://github.com/zhuifengshen/DingtalkChatbot

# email

django-celery-ses 电子邮件库
envelopes
flanker
imbox
inbox
sync-engine
lamson
marrow mailer
modoboa
smtplib
yagmail


```py

import smtplib
from smtplib import SMTP_SSL
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.header import Header

# login info
host_server = 'smtp.sina.com'  # sina email smtp server
user_sina = 'hyh1175561641@sina.com'
pwd_sina = 'd850bdff0d913543' # 新浪自己生成的

# email info
sender_sina_mail = user_sina
receiver = 'hyh1175561641@163.com'
mail_title = 'test自动化邮件'
mail_content = "Hello World!!! It's from sina server"

# email content
msg = MIMEMultipart()
msg['Subject'] = Header(mail_title, 'utf-8')
msg['From'] = sender_sina_mail
msg['To'] = receiver
msg.attach(MIMEText(mail_content, 'plain', 'utf-8'))

# ssl login 这里不能用
smtp = SMTP_SSL(host_server)
smtp.login(user_sina, pwd_sina)
smtp.sendmail(sender_sina_mail, receiver, msg.as_string())
smtp.quit()



```