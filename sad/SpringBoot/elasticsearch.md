## 1.为什么使用elasticsearch

直接使用mysql的like查询语句会影响系统的性能，最重要的是非关系型数据不能模糊查询，而且遍历数据库查询很慢，所以采用elasticsearch来实现站内搜索

除了要搜索还要分析

## 技术栈

Elasticsearch kibanna beats logstash  

### 全文搜索引擎



## 2.springboot整合elasticsearch

本文使用的SpringBoot版本为**2.3.7.RELEASE**
对应的Elasticsearch版本为**7.6.2**

```xml
<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-data-elasticsearch</artifactId>
</dependency>



<dependency>     

<groupId>org.springframework.boot</groupId>    

  <artifactId>spring-boot-starter-data-jpa</artifactId> 

</dependency> 
```

## 3.elasticsearch

elasticsearch面向文档型数据库      

### 倒排索引

根据关键字查询   (一般关系型数据库查询要遍历数据库)

一般没有表的概念，创建索引等于创建数据库

### 创建索引







正向索引

根据编号设置主键和索引  再去查找信息