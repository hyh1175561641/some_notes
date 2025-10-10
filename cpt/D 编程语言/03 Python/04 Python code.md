# socket

```python
#server.py
#简单服务器
import socket
s = socket.socket()
host = socket.gethostname()
port = 1234
s.bind((host,port))
s.listen(5)
while True:
        c, addr = s.accept()
        print 'Got connection from' , addr
        c.send('Thank you for connection')
        c.close()
```



```python
#client.py
#简单客户端
import socket 
s = socket.socket()
host = socket.gethostname()
host = '192.168.0.103'
port = 1234
s.connect((host,port))
print s.recv(1024)
```

# SimpleHTTPServer.py

```python
#SimpleHTTPServer.py
# coding:utf-8

import socket
import re

from multiprocessing import Process

# 设置静态文件根目录
HTML_ROOT_DIR = "./html"


def handle_client(client_socket):
    """
    处理客户端请求
    """
    # 获取客户端请求数据
    request_data = client_socket.recv(1024)
    print("request data:", request_data)
    request_lines = request_data.splitlines()
    # 解析请求报文
    request_start_line = request_lines[0]
    # 提取用户请求的文件名
    file_name = re.match(r"\w+ +(/[^ ]*) ", request_start_line.decode("utf-8")).group(1)

    if "/" == file_name:
        file_name = "/index.html"

    # 打开文件，读取内容
    try:
        file = open(HTML_ROOT_DIR + file_name, "rb")
    except IOError:
        response_start_line = "HTTP/1.1 404 Not Found\r\n"
        response_headers = "Server: My server\r\n"
        response_body = "The file is not found!"
    else:
        file_data = file.read()
        file.close()

        # 构造响应数据
        response_start_line = "HTTP/1.1 200 OK\r\n"
        response_headers = "Server: My server\r\n"
        response_body = file_data.decode("utf-8")

    response = response_start_line + response_headers + "\r\n" + response_body
    print("response data:", response)

    # 向客户端返回响应数据
    client_socket.send(bytes(response, "utf-8"))

    # 关闭客户端连接
    client_socket.close()


if __name__ == "__main__":
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    server_socket.bind(("", 80))
    server_socket.listen(128)

    while True:
        client_socket, client_address = server_socket.accept()
        print("[%s, %s]用户连接上了" % client_address)
        handle_client_process = Process(target=handle_client, args=(client_socket,))
        handle_client_process.start()
        client_socket.close()

```

# Fibonacci.py

```python
# -*- coding: utf-8 -*-
#斐波那契数列
# Fibonacci sequence
index = 3
a = 1
print 1,a

b = 1
print 2,b

#while:{
c = a + b
print index,c
index=index+1
a = b + c 
print index,a
index=index+1
b = c + a 
print index,b
index=index+1
#}
```



# mmoney.py

```python
#mmonly.py
#爬虫练习

import urllib,urllib2
import re
import os 

def main(url,total):
	head = url[0:31]
	end = url[31:-5]
	if not os.path.exists("./pic/%s_%s"%(end,total)):os.makedirs("./pic/%s_%s"%(end,total))
	for x in xrange(9,total+1):
		html = urllib2.urlopen(url).read()
		image = re.compile(r"""class="down-btn" href='(.+?\.jpg)'""")
		imglist = re.findall(image,html)
		print x,end
		urllib.urlretrieve(imglist[0] , './pic/%s_%s/%s_%s.jpg' % (end,total,end,x))
		url = head+"%s_%s.html" % (end,(x+1))

url='http://www.mmonly.cc/mmtp/xgmn/131197.html'
total = 43
if not os.path.exists("./pic/"):os.makedirs("./pic/")
main(url,total)
```





# 2717.py

```python
import urllib.request
import bs4
import os
import requests

def save_img(img_url,dir):
    with open(dir+'/pic.txt','a+') as urlhub:
        urlhub.write(img_url+'\n')
    try:
        img = requests.get(img_url).content
        print(img_url+'下载到'+dir)
        with open(dir + '/' + img_url.split('/')[-1][0:],'wb') as pic:
            pic.write(img)
    except:
        pass

url = 'http://www.2717.com/ent/lianglimeimo'
#url = 'http://www.2717.com/ent/lianglimeimo/list_12_2.html'
#url = 'http://www.2717.com/ent/meinvtupian/'
#url = 'http://www.2717.com/ent/meinvtupian/list_11_2.html'
#url = 'http://www.2717.com/ent/meinvtupian/list_11_3.html'

with urllib.request.urlopen(url) as response:
    html_main = response.read().decode('gbk').encode('utf-8').decode('utf-8')
    soup = bs4.BeautifulSoup(html_main,'lxml')
    items = soup.select(".MeinvTuPianBox ul li .tit")
for item in items:
    item_url = 'http://www.2717.com' + item['href']
    item_n = item_url.split('/')[-1][0:-5]
    item_dir = './pic/' + item_n + item.text
    if not os.path.exists(item_dir):os.makedirs(item_dir)
    while item_url:
        print("开始处理 "+item_url)
        html_img = urllib.request.urlopen(item_url).read().decode('gbk')
        soup_img = bs4.BeautifulSoup(html_img,'lxml')
        img_url = soup_img.select("#picBody img")[0]['src']
        save_img(img_url,item_dir)
        if soup_img.select(".thisclass+li") == soup_img.select("#nl"):
            break
        item_url = item_url[0:item_url.rfind('/')+1] + soup_img.select(".thisclass+li a")[0]['href']
```





# xiaohua.py

```python
#xiaohua.py
#爬虫练习，代码已失效

#!/usr/bin/env python
# -*- coding:utf-8 -*-
from urllib import request
from bs4 import BeautifulSoup
import re
import time
import gevent
from gevent import monkey
monkey.patch_all()

def parser(html):
    try:
        soup = BeautifulSoup(html, 'html.parser', from_encoding='gbk')
        imgs = soup.find_all('img', src=re.compile(r'/d/file/\d+/\w+\.jpg'))
        return imgs
    except Exception as e:
        print('in parser error=%s' % e)
        return None

def save_img(path, data):
    try:
        with open(path, 'wb') as f:
            f.write(data)
    except Exception as e:
        print('in save_img error=%s' % e)

def download(url):
    header = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36'
    }
    try:
        req = request.Request(url=url, headers=header)
        response = request.urlopen(req, timeout=10)
        return response.read()
    except Exception as e:
        print('in download error=%s' % e)

def spider():
    first_url = "http://www.xiaohuar.com/list-1-%s.html"
    imgs = []
    for i in range(10):
        html = download(first_url%i)
        if html:
            temp = parser(html)
        if temp !=[]:
            imgs += temp

    s_time = time.time()
    glist = []
    if imgs != []:
        for img in imgs:
            data = download("http://www.xiaohuar.com%s" % img['src'])
            g = gevent.spawn(save_img,'%s.jpg' % img['alt'], data)
            glist.append(g)
        gevent.joinall(glist)
        e_time = time.time()
        print('耗费%s秒' % (e_time-s_time))
    else:
        print('网络错误')

if __name__ == '__main__':
    spider()
```

# mm131_pic.py

```python
#mm131_pic.py
#爬虫练习

#!/usr/bin/env python3
#-*- coding:utf-8 -*-
"""
#!usr/bin/env python3
2016/10/2
"""

import requests
import bs4
from urllib.parse import urljoin

headers={"connection":"keep-alive",
        "upgrader-insecure-requests":"1",
        "user-agent":"Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.116 Safari/537.36",
        "Accept-Encoding":"gzip,deflate,sdch,br",
        "Accept-Language":"zh-CN,zh"}

def this_img_url(bs4_obj):
    tag=bs4_obj.find("div",class_="content-pic")
    if not tag:
        return
    else:
        return tag.a.img["src"]


def next_img_url(bs4_obj):
    tags=bs4_obj.find_all("a",class_="page-ch")
#     if not tags:
#         print("1")
#         tags=bs4_obj.find_all("a",class_="updown-r")
#         if not tags:
#             print("没有下一篇了，需要修改其实url")
#         else:
#             return tags["href"]
#     else:
    for tag in tags:
        #显示的时候出现乱码，就用乱码即可
        if tag.string=="ÏÂÒ»Ò³":
            return tag["href"]
    else:
        print("没有下一页了，正在跳转到下一篇")
        tags=bs4_obj.find_all("a",class_="updown_r")
        if not tags:
            print("没有下一篇了，需要修改其实url")
            return
        else:
            return tags[0]["href"]

def save_img(img_url, name):
    with open("./%s.jpg" % name, "wb") as jpg:
        jpg.write(requests.get(img_url,headers=headers,stream=True).raw.read())


def full_img_url(root_url, join_url):
    return urljoin(root_url,join_url)


init_url="http://www.mm131.com/xinggan/2386.html"
total_num=input("请输入图片数目：")
full_url=init_url
html=requests.get(full_url,headers=headers)
bs4_obj=bs4.BeautifulSoup(html.text,"html.parser")

for i in range(0,int(total_num)+1):
    print(full_url)
    this_url=this_img_url(bs4_obj)
    save_img(this_url, i)
    next_url=next_img_url(bs4_obj)
    full_url=full_img_url(init_url,next_url)
    html=requests.get(full_url,headers=headers)
    bs4_obj=bs4.BeautifulSoup(html.text,"html.parser")
    
print("done")
```

