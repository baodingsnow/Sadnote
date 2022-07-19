```sql
SELECT  student.*  from student //返回student表全部数据，多表查询需要返回全量查询的时候用到
/**
分组查询  比如学生成绩表有多个科目的查询 用分组查询可以把学生名字相同的分数归类成一组并相加
*/
SELECT Customer,SUM(OrderPrice) FROM Orders
GROUP BY Customer

/**
查出最大值
*/
select s_id , max(s_score) AS MAXIMUM
FROM score 
GROUP BY s_id  

```





```sql
/**
 * 查询01课程比02课程成绩高的学生信息及课程分数
*/

select a.* ,b.s_score as 02_score,c.s_score as 03_score from 
student a 
	join score b on a.s_id=b.s_id and b.c_id='01'
	left join score c on a.s_id=c.s_id and c.c_id='02' where b.s_score>c.s_score

	
	SELECT  student.*  from student
```

# 问题

```sql
select s_id,c_id,min(s_score) as mINimum 
from score 
group by c_id;
```

