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

## 3.elasticsearch（apipost版本）

elasticsearch面向文档型数据库      

### 倒排索引

根据关键字查询   (一般关系型数据库查询要遍历数据库)

一般没有表的概念，创建索引等于创建数据库 

### 修改文档

完全覆盖 幂等性 put操作

```xml
//请求地址
localhost:9200/shopping/_doc/100
//body
{
    "title": "黑米手机",
    "category": "香蕉",
    "price": 3999
}
```

局部更新 非幂等性 post方式

```
//请求地址
localhost:9200/shopping/_update/100
//body
{
    "doc" : {
         "title" : "华为手机"
    }
}
```

全部更新，是直接把之前的老数据，标记为删除状态，然后，再添加一条更新的。

 局域更新，只是修改某个字段。

### 创建索引



创建文档 相当于表数据

> 创建文档必须要用post请求 因为put是幂等性请求   我们创建的文档每次id都是随机的
>
> 在请求路径中添加id就是幂等性操作了，就可以使用put方法了

正向索引 

根据编号设置主键和索引  再去查找信息

### 查询（重要）

#### 分页查询 

```yml
{
    "query":{
        "match_all" :{
            
        }
    },
    "from" : 1,
    "size" : 1
}
```

from  类似数组下标 从0开始数  

size 每页显示的数量

加上"_source"：["title"]    指定数据查询

"sort" : { 

"price" : {"order " : desc}

} //对查询结果进行排序

#### 多条件查询

```yml
{
    "query" :{
        "bool" : {
            "must" : [
                {
                    "match" : {
                        "category" : "香蕉"
                    }
                },
                {
                    "match" : {
                        "price" : 2999
                    }
                }
            ]
        }
    }
}
```

must是and should是or 条件

#### 范围查询

```yml
{
    "query" :{
        "bool" : {
            "must" : [
                {
                    "match" : {
                        "category" : "香蕉"
                    }
                }
            ],
            "filter" : {
                "range" : {
                    "price" : {
                        "gt" : 3000
                    }
                }
            }
        }
    }
}
```

## 4.elasticsearch(javaApi版本)