# (my)sql语句

> sql语句主要有以下3类：

* DDL Data Definition Languages  数据定义语言 create ,drop,alter等
* DML Data manipulation Languages 数据操纵语句 insert delete select等
* DCL Data Control Languages 数据控制语句 grant revoke 等

1.DDL语句
 
|语法|说明|
|-|-|
|*create database* dbname | 创建数据库dbname
|*show databases* |查看所有的数据库
|*use* test1|选择数据库test1
|*show tables*|显示数据里的表信息
|*drop database* test1|删除数据库 test1
|*create table* test2|创建数据库 col_name col_type constrains(约束条件)
|*desc* table1 | 查看table1信息
|*show create table* table1|查看table1创建信息
|*drop table* table1|删除table1

> 修改表信息

|语法|说明
|-|-|
|*alter table* table1 *modify* [col] col_def | 修改col的定义(包括定位) 可用after/first定位
|*alter table* table1 *add* col_def | 增加一列col 可指定位置
|*alter table* table1 *drop* col_name|删除表字段col_name
|*alter table* table1 *change* old_col_name col_def| 修改字段名，可修改位置
|*alter table* table1 *rename* new_table1| 修改表名
>> change/first/after col 属于mysql专属，其他不一定适用 

>*show databases;*<br>
> information_schema:存储数据库对象信息，例如：用户表信息 列信息 权限 字符集 分区信息.不是实际存在的库。元数据(数据的数据)。可以批量删表，修改表<br>
> cluster:系统集群信息<br>
> mysql：系统的用户权限信息<br>
> test:系统自动创建的测试数据哭，任何用户都可以使用
-----
2.DML语句

|语法|说明
|-|-|
|*insert into* table1 (f1,f2,f3) values(v1,v2,v3),(w1,w2,w3)|插入记录
|*update* table1 *set* f1=v1 *where* conditon1| 更新记录
|*delete from* table1 *where* conditon1|删除记录
|*select* col *from* table1 | 查询

>查询<br>
>1.不重复：select distinct from table1 where conditon1<br>
>2.limit:属于mysql语法，不通用<br>
>3.聚合：group by ;sum，count(1),max(),min();with rollup 会多一行汇总数据(汇总聚合函数的值)
```
    select sum(col1) from table1 where condtion1 group by col2  [WITH ROLLUP] [HAVING condition2]
```
>4.标连接：内连接(同时满足2表)，外连接(只需要满足1表条件)
```
    select t1.col1 ,t2.col2 from table1 t1,table2 t2 where t1.col1= t2.col2
```
>      外连接：左(包含左表数据，右表可以不匹配)，右(包含右表数据，左表可以不匹配)<br>
```
    select c1 from t1 left join t2 on t1.c1 = t2.c2
```
>5.子查询 in,not in ,= (子查询记录唯一 等同于in),!= ,exists,not exists
子查询有时候可以转化为表连接查询，表连接一般优于子查询
>6.联合 union(去重联合)，union all

3.DCL语句
DBA管理系统权限使用，开发人员很少使用。

