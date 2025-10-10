# 4-8Log

今天爬虫爬取标题时，编码出现问题，爬下来标题出现乱码，其余还好。python中的decode函数和encode函数还没看懂

```python
# 将第二行文字以UTF8储存，再打开变成ascii时，会出现第一行的样子
[XIURENç§äººç½] å¥¶æ²¹å¦¹å¦¹ NO.3121-æ¥åå¾çç½
[XIUREN秀人网] 奶油妹妹 NO.3121-春光图片网
http://www.cgtpw.com/xgmn/12852.html

# test.py
a = '[XIUREN秀人网] 奶油妹妹 NO.3121-春光图片网'
print(a.encode()) # 如何转码才能出现第一行的样子？
```



```python
# 再附上源代码
# spider.py
#-*- encoding:utf-8 -*-
import os
import sys
import requests
import parsel
import time
headers = {
# 'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9',
# 'Accept-Encoding': 'gzip, deflate',
# 'Accept-Language': 'zh-CN,zh;q=0.9',
# 'Cache-Control': 'max-age=0',
# 'Connection': 'keep-alive',
# 'Cookie': 'UM_distinctid=17ffcb6483914c-0657be7cf7f564-1a343370-1fa400-17ffcb6483ab7c; __gads=ID=9656cc6e692cea76-2268782f87d1008d:T=1649212277:RT=1649212277:S=ALNI_Ma3tHdUscfNzbNkMJE6LcJTwlpunw; _d_id=58746bada902217e7109d9847f0356; CNZZDATA1278034378=2125848296-1649206623-https%253A%252F%252Fwww.baidu.com%252F%7C1649378236; Hm_lvt_b11fc0072159af68d01aba088367c6ab=1649228999,1649291853,1649302574,1649380617; Hm_lpvt_b11fc0072159af68d01aba088367c6ab=1649380617',
# 'Host': 'www.cgtpw.com',
# 'If-Modified-Since': 'Thu, 07 Apr 2022 04:06:39 GMT',
# 'If-None-Match': '"081bfe1344ad81:0"',
# 'Upgrade-Insecure-Requests': '1',
'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.75 Safari/537.36'

}
def printlog(str,path):
  fp = open(path,'a+')
  fp.write(str)
  fp.close()

main_page = 'http://www.cgtpw.com'
main_html = requests.get(url=main_page,headers=headers).text
main_urls = parsel.Selector(main_html).css('h2 a::attr(href)').getall()

list_page = 'http://www.cgtpw.com/xgmn/index_2.html'
list_html = requests.get(url=list_page,headers=headers).text
selector = parsel.Selector(list_html)
list_urls = selector.css('.listBox2 li p a::attr(href)').getall()
list_next_html = selector.css('a').get()
printlog('=============== START DOWNLOAD '+list_page+'\n','root/cgtpw/log.txt') # 重要的输出
for link in list_urls:
  pass
  img_page = main_page + link
  printlog('\npage:'+img_page+'\n','root/cgtpw/log.txt') # 重要的输出
  print(img_page)
  img_html = requests.get(url=img_page,headers=headers).text
  img_urls = parsel.Selector(img_html).css('.artbody img::attr(src)').getall()
  img_title = parsel.Selector(img_html).css('title::text').get()
  # printlog(img_title +'\n','root/cgtpw/log.txt')
  print(img_title) # 这里的问题不清楚，接受到的标题不是UTF-8内容，转码又不会，标题暂时不写
  print("你好")
  for l in img_urls:
    pass
    printlog(l+'\n','root/cgtpw/log.txt') # 重要的输出
  img_next_page = parsel.Selector(img_html).css('.pages li').getall()
  if img_next_page:
    num = int(img_next_page[-1].split('.')[0].split('_')[1])
    x=2
    while x <= num:
      xx = img_page.split('.htm')
      new_page = xx[0]+'_'+str(x)+'.htm'+xx[1]
      new_html = requests.get(url=new_page,headers=headers).text
      new_urls = parsel.Selector(new_html).css('.artbody img::attr(src)').getall()
      for l in new_urls:
        pass
        printlog(l+'\n','root/cgtpw/log.txt') # 重要的输出
      x=x+1

# 主页链接
# 爬虫主页
# 提取的链接
# 继续再爬
# 再找链接
# 然后下载
```



```python
# 同一天的另外一个爬虫，没遇到什么问题
'''
http://www.cgtpw.com/
https://www.leshetu.com/

mainpage
listpage
imgpage

rootpath='./root/leshetu/'
path='xz/xxxx'

'''

'''
leshetu requests
GET /tags HTTP/2
Host: www.leshetu.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:98.0) Gecko/20100101 Firefox/98.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh,zh-CN;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate, br
DNT: 1
Connection: keep-alive
Cookie: X_CACHE_KEY=9241f6ae3eb53806e02ac796a2426a40; PHPSESSID=acl3pvfk56dk6cuuejekiu4583; Hm_lvt_5bde07362a05ff4688ae366ec16bf3f4=1649230969; Hm_lpvt_5bde07362a05ff4688ae366ec16bf3f4=1649230969; _ga=GA1.2.937571114.1649230969; _gid=GA1.2.433835272.1649230969
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Cache-Control: max-age=0
TE: trailers

'''


# 把信息放在root/leshetu/xz/twyh中，图片保存在一个文件中


import os
import sys
import requests
import parsel
import time
headers = {
  'Host' : 'www.leshetu.com',
  'User-Agent' : 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:98.0) Gecko/20100101 Firefox/98.0',
  'Accept' : 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8'
}

# 输入一个URL，返回HTML
def html(listpage):
  response = requests.get(url=listpage, headers=headers)
  return response.text
# 解析列表的图片URL组
def listurls(listhtml):
  selector = parsel.Selector(listhtml)
  return selector.css('.posts-wrapper h2 a::attr(href)').getall()
# 解析列表的下一个列表
def listnext(listhtml):
  selector = parsel.Selector(listhtml)
  return selector.css('.numeric-pagination .next::attr(href)').get()
# 解析img图片URL组
def imgurls(imghtml):
  selector = parsel.Selector(imghtml)
  return selector.css('.article-content noscript img::attr(src)').getall()
# 确保路径正常
def isPath(path):
  if not os.path.exists(path):
    os.makedirs(path)
    print('Create ' + path + ' successed.')
# 给定文字和路径
def printlog(str,path):
  fp = open(path,'a+')
  fp.write(str)
  fp.close()
# 给定图片地址和路径
def imgdownloader(url,path):
  # print(path+'  '+url)
  pic = requests.get(url)
  fp = open(path+url[32::],'wb')
  fp.write(pic.content)
  fp.close()
  



if __name__ == '__main__':
  print(sys.version)
  listpage = 'https://www.leshetu.com/xz/twyh/page/11'

  for x in range(3):
    x=x+1
    pass
    listpath = 'root/leshetu/' + listpage[24:31:]
    isPath(listpath)
    print(listpage + " " +listpath)
    listhtml = html(listpage)
    listurlss = listurls(listhtml)
    listnextt = listnext(listhtml)
    printlog(listpage+'\n',listpath+'.txt')
    for imgpage in listurlss:
      pass
      imgpath = listpath + imgpage[31:-5:]
      isPath(imgpath)
      printlog('    '+imgpage + '   ' + imgpath+'\n',listpath+'.txt')
      imghtml = html(imgpage)
      # print(imghtml)
      imgurlss = imgurls(imghtml)
      for imgsrc in imgurlss:
        pass
        printlog(str('        '+imgsrc+'\n'),listpath+'.txt')
        imgdownloader(imgsrc,imgpath)
      time.sleep(1)

  str='123'
  printlog(str,'root/leshetu/xz/twyh/ttt.txt')


    # listpage = listnextt

```

