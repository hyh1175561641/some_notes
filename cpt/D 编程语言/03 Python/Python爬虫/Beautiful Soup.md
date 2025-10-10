# 简介

网页解析器

Python第三方库，用于从HTML或XML中提取数据

## 安装和配置

```
pip install beautifulsoup4
import bs4
```





## 运行环境





# 基础语法

把下载的HTML网页

创建对象BeautifulSoup

搜索节点find_all搜索全部、find搜索第一个、select选择器

访问节点的名称、属性和文字

```python
from bs4 import BeautifulSoup
# 根据HTML网页字符串创建BeautifulSoup对象
soup = BeautifulSoup(html_doc,
                    'html.parser',
                     from_encoding='utf8')


# 方法find_all(name,attrs,string)
#查找所有标签为a的节点
soup.find_all('a')

#查找所有标签为a，链接符合/view/123.htm的节点,可以使用正则
soup.find_all('a',href='/view/123.htm')
soup.find_all('a',href=re.compile(r'/view/\d+\.htm'))

#查找所有标签为div，class为abc，文字为python的节点,python语言有关键字class，为了避免冲突，写成class_
soup.find_all('div',class_='abc',string='Python')


#访问节点信息
#得到节点<a href='1.html'>python</a>
#获取查找到的节点的标签名称
node.name
#获取查找到的a节点的href属性
node['href']
#获取查找到的a节点的链接文字
node.get_text()
```



```python
# bs4简单语法
from bs4 import BeautifulSoup

# 生成soup对象
soup = BeautifulSoup(open('soup.html', encoding='utf8'), 'lxml')
print(type(soup))

print(soup.a.attrs)
print(soup.a.attrs['href'])
print(soup.a['href'])

print(soup.a.string)
print(soup.a.text)
print(soup.a.get_text())

print(soup.div.string)
print(soup.div.text)
print(soup.div.get_text())

ret = soup.find('a')
ret = soup.find('a', title='清明')
ret = soup.find('a', class_='dumu')
print(ret)

import re
ret = soup.find('a', id='xiaoge')
ret = soup.find('a', id=re.compile(r'^x'))
print(ret.string)

ret = soup.find_all('a')
print(ret[1].string)

ret = soup.find_all('a', class_='wang')
print(ret)

ret = soup.find_all('a', id=re.compile(r'^x'))
print(ret)

ret = soup.select('a')
ret = soup.select('#muxiong')
print(ret[0]['title'])

ret = soup.select('.wang')
print(ret)

ret = soup.select('div > a')
print(ret)

ret = soup.select('a[title=东坡肉]')

print(ret)

odiv = soup.select('.tang')[0]

ret = odiv.select('a')

print(ret)

```





# 单词

soup 汤，羹，马力，加速

# 链接



[Beautiful Sopu](https://www.crummy.com/software/BeautifulSoup/)

[Beautiful Sopu Doc](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

[Beautiful Sopu Doc 中文](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)

[中文文档](https://beautifulsoup.readthedocs.io/zh_CN/v4.4.0/)

[简书bs4语法](https://www.jianshu.com/p/9254bdc467b2)

[这也是个中文文档](https://beautifulsoup.readthedocs.io/zh_CN/v4.4.0/)
























