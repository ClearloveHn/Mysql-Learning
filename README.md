## Mysql操作详解
https://www.imooc.com/article/312463

## Mysql重要操作(个人感觉)
### 1.in关键字
1.1 语法格式：SELECT 字段名 FROM 表名 WHERE 字段 in (数据1, 数据2...);  

1.2 in里面的每个数据都会作为一次条件，只要满足条件的就会显示。  
例子：查询id是1或3或5的英雄
```
SELECT * FROM hero WHERE id in(1,3,5)
```
### 2.like模糊查询
2.1 语法格式：SELECT * FROM 表名 WHERE 字段名 LIKE '通配符字符串';  

2.2 满足通配符字符串规则的数据就会显示出来  

2.3 MySQL通配符有两个：  
 %: 表示0个或多个字符(任意个字符)  
 _: 表示一个字符  

### 3.排序
1.通过ORDER BY子句,可以将查询出的结果进行排序。  
2. 语法格式:SELECT 字段名 FROM 表名 WHERE 字段=值 ORDER BY 字段名 [ASC|DESC]   
ASC:升序  
DESC:降序  
3.例子:查询年龄小于等于35岁的英雄,按照年龄升序排列。(单例排序)    
```
SELECT *FROM hero where age <= 35 ORDER BY age ASC
```
例子:查询年龄小于等于35岁的英雄,按照年龄升序排列,如果年龄相同,按照生命的升序排列。
```
SELECT *FROM hero WHERE age <=35 ORDER BY age ASC,life ASC
```
### 4.聚合函数
聚合函数查询是纵向查询，它是对一列的值进行计算，然后返回一个结果值。另外聚合函数会忽略空值

count:统计指定列记录数,记录为NULL的不统计。  
sum:计算指定列的数值和,如果不是数值类型,那么计算结果为0。    
max:计算指定列的最大值。  
min:计算指定列的最小值。  
avg:计算指定列的平均值，如果不是数值类型，那么计算结果为0。  

### 5.分组
1. 分组查询是指使用 GROUP BY语句对查询信息进行分组，相同数据作为一组。
2. 多用于和聚合函数使用。  
3. 例子:查询年龄小于30岁的人,按性别分组,统计每组的人数。
```
SELECT sex,COUNT(*) FROM hero WHERE age < 30 GROUP BY sex  
```
例子2:查询年龄大于25岁的人,按性别分组,统计每组的人数,并只显示性别人数大于2的数据
```
SELECT sex,COUNT(*) FROM hero WHERE age>25 GROUP BY sex HAVING COUNT(*) > 2
```
4. Having和Where的区别
having是在分组后对数据进行过滤。  
where是在分组前对数据进行过滤。  
having后面可以使用聚合函数。  
where后面不可以使用聚合函数。  

### 5.Limit
1. LIMIT是限制的意思,所以LIMIT的作用就是限制查询记录的条数。  
2. LIMIT放在查询语句最后。  
3. 语法格式:
LIMIT offset,length; 或者limit length;  
offset: 偏移量,可以认为是跳过的记录数量,默认为0。  
length: 指显示的总记录数。  
4. 例子: 查询hero表中数据，从第三条开始显示，显示6条。  
```
SELECT *FROM hero LIMIT 2,6
```
### 6.Join
1. SQL JOIN子句用于把来自两个或多个表的行结合起来,基于这些表之间的共同字段。  
2. 先确定一个主表作为结果集,然后,把其他表的行有选择性地“连接”在主表结果集上。  
#### 6.1 inner Join
1. 内部链接INNER JOIN关键字选择两个表中具有匹配值的记录。(类似于两个集合的交集->两个表中相同的数据)
2. SQL INNER JOIN 从多个表中返回满足 JOIN 条件的所有行。
#### 6.2 ON关键字
两个表联接时才用ON,ON是两个表连接时的约束条件。

#### 6.2 left Join
1.SQL左链接LEFT JOIN关键字返回左表(表1)中的所有行,即使在右表(表2)中没有匹配。如果在正确的表中没有匹配,结果是NULL。
2.不需要在乎约束条件,都会返回左表中的所有行,除非左表中没有匹配,这样的结果是NULL。 

#### 6.3 right Join
1.SQL右链接RIGHT JOIN关键字返回右表(表2)中的所有行,即使在左表(表1)中没有匹配。如果在正确的表中没有匹配,结果是NULL。
2.不需要在乎约束条件,都会返回右表中的所有行,除非右表中没有匹配,这样的结果是NULL。






