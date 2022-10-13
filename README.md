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
###2.like模糊查询
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



