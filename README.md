# Elasticsearch + Kibana 部署



## Elasticsearch 

**Elasticsearch官网**：https://www.elastic.co/cn/elasticsearch/

`Elaticsearch，简称为es，es是一个开源的高扩展的分布式全文检索引擎，它可以近乎实时的存储、检索数据;本身扩展性很好，可以扩展到上百台服务器，处理PB级别(大数据时代）的数据。`es也使用java开发并使用Lucene作为其核心来实现所有索引和搜索的功能，但是它的目的是通过简单的RESTful API来隐藏Lucene的复杂性，从而让全文搜索变得简单。



据国际权威的数据库产品评测机构DB Engines的统计，在2016年1月，ElasticSearch已超过Solr等，成为排名第一的搜索引擎类应用。

![image-20220807223925392](https://raw.githubusercontent.com/isicman/image/main/img/image-20220807223925392.png)







## Kibana

**Kibana官网：**https://www.elastic.co/guide/en/kibana/current/introduction.html

![image-20220807221933336](https://raw.githubusercontent.com/isicman/image/main/img/image-20220807221933336.png)



## 部署步骤

### 1. 拉取镜像

```shell
$ docker pull elasticsearch:7.11.1
$ docker pull kibana:7.11.1
```



### 2.创建数据卷

```shell
$ docker volume create --name=elasticsearch
$ docker volume create --name=kibana
```



### 3.部署服务

```shell
$ cd es/docker-compose/
$ docker-compose up -d
```



### 4.安装插件

```shell
$ docker exec -it elasticsearch /bin/bash
$ cd /usr/share/elasticsearch/plugins/
$ elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.11.1/elasticsearch-analysis-ik-7.11.1.zip

$ vi config/elasticsearch.yml
http.cors.enabled: true
http.cors.allow-origin: "*"

$ docker-compose restart
```

