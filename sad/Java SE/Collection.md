# 一、集合基础

## 1.概述

数组固定，不能改变，选集合

集合类特点：存储空间可变

arraylist:

### 1.2

arraylist构造方法和添加方法

```java
public Arraylist()  
public  boolean add(E e)  //将指定元素追加到此集合的末尾
public void add (int index,E element)//在指定位置添加元素
```

数组索引越界   根据指定索引添加元素时，如果指定的位置没有元素 会造成越界

### 1.3 常用方法

remove 删除可以根据索引也可以根据值删除

get 查询

array.size()  获取元素个数

### 1.4 存储字符串并遍历

思路：创建学生类 和   test类

创建动态数组 arraylist 

创建学生对象  或者  使用键盘录入的方式创建对象

将对象添加到动态数组中

for循环遍历数组

# 二、Collection集合

- jdk没有提供 collection的实现    提供了更具体的子接口的实现   如set和list
- collection表示一组对象

创建Collection对象

采用多态方式     使用arraylist去建 

> 坑（小知识）：   遇到一个问题，遍历一个集合时，经常会输出地址
>
> 原因：new出的对象  赋给的都是地址值  
>
> 而直接添加元素  就会正常输出值
>
> ```java
> 
>         //new的对象
>         Collection<Student> arr = new ArrayList<Student>();
>         Student s2=new Student(22,"11");
>         Student s1=new Student(22,"33");
>         arr.add(s1);
>         arr.add(s2);
> 
>         //添加地址值
>         ArrayList<String> arrayList = new ArrayList<>();
>         arrayList.add("sad");
> 
> ```
>
> 虽然 arr也是new出来的  但是arraylist重写了toString方法
>
> 也侧面说明了多态的特性



```
/**
*/
```

## 1.集合常见方法

## 2.Collection

Iterator 迭代器  集合的遍历方式

collection中有个迭代器方法

## 3.list 

有序集合 (序列)      用户可以控制插入位置    也可以通过整数索引访问      

与set不同  允许重复的元素



### $\textcolor{WildStrawberry}{3.1并发修改异常(重要)}$

```java
/**
 * ConcurrentModificationException
 * 迭代器有个修改次数和预期次数判断  两者不同会引起并发，引起不同的原因：在循环中添加或者删除数据
 * get方法没有这个步骤(源码)   
 * 下面分别展示迭代器遍历和for循环遍历(foreach的本质就是迭代器)
 */


        for (int i=0;i< list.size();i++){
            String s=list.get(i);
            if (s.equals("world")){
                list.add("javase");
            }
            System.out.println(s);
        }

```

在Java开发中Exception in thread "main" java.util.ConcurrentModific                                                                                                                                                                ationException, 这是一个并发修改异常，主要原因是[迭代器](https://so.csdn.net/so/search?q=迭代器&spm=1001.2101.3001.7020)遍历元素的时候，通过集合是不能修改元素的

### 3.2列表迭代器

listIterator   继承自 Iterator

可以从任意方向遍历   

listIterator 里的新方法 ：hasPrevious        previous（）返回上一个数据      。      listIterator  还能获取列表中当前迭代器的位置

### 3.3增强for循环

格式

```java
int[]  arr={1，2，3，4，5}
for(int str :arr){
    sout{
        str
    }
}//str 就是把arr遍历一遍的对象
```

## 4.set集合

set集合特点   不包含重复元素  没有带索引的方法 所以不能用==普通的for循环遍历==，foreach循环遍历的原理是迭代器Iterator所以可以去遍历set集合

### 4.1哈希值

哈希值是JDK根据对象地址 或者字符串算出来的int类型的数值

hashCode（）该方法可以返回对象的hash值

> 多次调用一个对象的hash值不变
>
> 不同对象即使值相同，hash值也不同
>
> 因为set不包含重复元素  所以给两个set对象赋相同的值   它们的哈希值相同

重写hashCode（）方法，可以使哈希值相同
