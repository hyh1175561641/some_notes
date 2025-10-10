

# ElasticSearch

https://www.elastic.co/
https://www.elastic.co/elasticsearch/
https://www.elastic.co/cn/elasticsearch/


Elastic Stack包括Elasticsearch,Kibana,Beats,Logstash.(这些项目的组合简称是ELK Stack).能够安全可靠地获取任何来源,任何格式数据,然后实时的对数据进行搜索,分析,可视化.

ElasticSearch简称ES,是一个开源的高扩展的分布式全文搜索引擎,是整个ElasticStack技术栈的核心.它可以近乎实时的存储,检索数据,本身的扩展性很好,可以扩展到上百台服务器,处理PB级别的数据.

Beats,LogStack是采集和传输数据的项目.
Kibana是用来展示数据的项目.




```bash

# 下载ElasticSearch





# 9300端口为ElasticSearch集群间组件通信端口
# 9200端口为浏览器访问的http协议RESTful端口


```

ElasticSearch是面向文档型的数据库,一条数据在这里就是一个文档.Types概念逐渐弱化,ElasticSearch6.X中,一个index下只能包含一个type,ElasticSearch7.X中Types概念已经被删除了
ElasticSearch 相当于数据库
Index 索引,相当于数据库
Type 类型,相当于表
Documents 文档,相当于行
Fields 字段,相当于列



# 基本操作

```bash

# 索引不能使用POST请求
# 创建索引
PUT http://127.0.0.1:9200/shopping
# 获取索引,创建时间,UUID,版本号
GET http://127.0.0.1:9200/shopping
# 删除索引
DELETE http://127.0.0.1:9200/shopping
# 查看所有的索引,详细信息
http://127.0.0.1:9200/_cat/indices?v


```

```bash

# 添加文档数据,添加数据必须指定body,是json格式的数据
POST http://127.0.0.1:9200/shopping/_doc
body-json{
    "title":"小米手机",
    "category":"小米",
    "images":"http://www.gulixueyuan.com/xm.jpg",
    "price":3999.00
}
POST http://127.0.0.1:9200/shopping/_doc/1001 # 指定id值
PUT http://127.0.0.1:9200/shopping/_doc/1001 # PUT请求同样的效果
PUT http://127.0.0.1:9200/shopping/_create/1001 # 添加文档数据

11集视频




```















