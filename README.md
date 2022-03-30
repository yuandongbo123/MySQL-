# MySQL-学习笔记

## 0.基础用法
[参考链接](https://blog.csdn.net/weixin_45851945/article/details/114287877)
>- 第一次链接服务器(#cd 到  sql/bin ）
>- 1.net start MySQL80
>- 2.mysql -u root -p    #输入密码(如果在client直接输入密码即可
>- 3.create database my #创建数据库
>- 4.show databases #显示数据库
>- 5.use my;  #创建表格
>...create table mytable;
>- 6.desc mytable; #显示表格
>- 7.drop database my/mytable  #删除数据库/表格

## SQL

### 一.SQL简介
> Structure Query Language(结构化查询语言)简称SQL，它被美国国家标准局(ANSI)确定为关系型数据库语言的美国标准，后被国际化标准组织(ISO)采纳为关系数据库语言的国际标准。数据库管理系统可以通过SQL管理数据库；定义和操作数据，维护数据的完整性和安全性。


### 二.SQL的优点
> 1、简单易学，具有很强的操作性
> 2、绝大多数重要的数据库管理系统均支持SQL
> 3、高度非过程化；用SQL操作数据库时大部分的工作由DBMS自动完成


### 三.SQL的分类
> - 1、DDL(Data Definition Language) 数据定义语言，用来操作数据库、表、列等； 常用语句：CREATE、 ALTER、DROP
> - 2、DML(Data Manipulation Language) 数据操作语言，用来操作数据库中表里的数据；常用语句：INSERT、 UPDATE、 DELETE
> - 3、DCL(Data Control Language) 数据控制语言，用来操作访问权限和安全级别； 常用语句：GRANT、DENY
> - 4、DQL(Data Query Language) 数据查询语言，用来查询数据 常用语句：SELECT


## 2.数据库的三大范式
> 1、第一范式(1NF)是指数据库表的每一列都是不可分割的基本数据线；也就是说：每列的值具有原子性，不可再分割。
> 2、第二范式(2NF)是在第一范式(1NF)的基础上建立起来得，满足第二范式(2NF)必须先满足第一范式(1NF)。如果表是单主键，那么主键以外的列必须完全依赖于主键；如果  > 表是复合主键，那么主键以外的列必须完全依赖于主键，不能仅依赖主键的一部分。
> 3、第三范式(3NF)是在第二范式的基础上建立起来的，即满足第三范式必须要先满足第二范式。第三范式(3NF)要求：表中的非主键列必须和主键直接相关而不能间接相关；也就是说：非主键列之间不能相关依赖。

## 3、数据库的数据类型
> 使用MySQL数据库存储数据时，不同的数据类型决定了 MySQL存储数据方式的不同。为此，MySQL数据库提供了多种数据类型，其中包括整数类型、浮点数类型、定点 数类> > 型、日期和时间类型、字符串类型、二进制…等等数据类型。

### 1.整数类型

>- 根据数值取值范围的不同MySQL 中的整数类型可分为5种，分别是TINYINT、SMALUNT、MEDIUMINT、INT和 BIGINT。下图列举了 MySQL不同整数类型所对应的字节大小和取值> 范围而最常用的为INT类型的，

> | 数据类型 | 字节数 |无符号数的取值范围 |无符号数的取值范围|
> | :-----| :---- | :---- |:---- |
> | TINYINT | 1 | 0~255 |-128~127|
> | SMALLINT | 2 | 0~65535 |-32768~32768|
> | SMALLINT | 2 | 0~65535 |-32768~32768|
> |MEDIUMINT	|3|	0~16777215|	-8388608~8388608|
> |INT|	4	|0~4294967295|	-2147483648~ 2147483648|
> |BIGINT|	8|	0~18446744073709551615|	-9223372036854775808~9223372036854775808|

### 2.浮点数类型和定点数类型

> 在MySQL数据库中使用浮点数和定点数来存储小数。浮点数的类型有两种：单精度浮点数类型（FLOAT)和双精度浮点数类型（DOUBLE)。而定点数类型只有一种即DECIMAL类> > 型。下图列举了 MySQL中浮点数和定点数类型所对应的字节大小及其取值范围：


> |数据类型|	字节|	有符号的取值范围|	无符号的取值范围|
> | :-----| :---- | :---- |:---- |
> |FLOAT|	4|	-3.402823466E+38~-1.175494351E-38|	0和1.175494351E-38~3.402823466E+38|
> |DOUBLE|	8|	-1.7976931348623157E+308~2.2250738585072014E-308	|0和2.2250738585072014E-308~1.7976931348623157E+308|
> |DECIMAL（M,D）	|M+2	|-1.7976931348623157E+308~2.2250738585072014E-308	|0和2.2250738585072014E-308~1.7976931348623157E+308|

### 3.字符串类型
> 在MySQL中常用CHAR 和 VARCHAR 表示字符串。两者不同的是：VARCHAR存储可变长度的字符串。
> 当数据为CHAR(M)类型时，不管插入值的长度是实际是多少它所占用的存储空间都是M个字节；而VARCHAR(M)所对应的数据所占用的字节数为实际长度加1

|插入值|	CHAR(3)|	存储需求|	VARCHAR(3)|	存储需求|
| :-----| :---- | :---- |:---- |:---- |
|‘’|	‘’|	3个字节|	‘’	1个字节|
|‘a’	|‘a’	|3个字节	|‘a’	|2个字节|
|‘ab’	|‘ab’|	3个字节|	‘ab’|	3个字节|
|‘abc’	|‘ab’	|3个字节	|‘abc’	|4个字节|
|‘abcd’|	‘ab’	|3个字节|	‘abc’|	4字节|

### 4.字符串类型
> 文本类型用于表示大文本数据，例如，文章内容、评论、详情等，它的类型分为如下4种：

|数据类型	|储存范围|
|:---- |:---- |
|TINYTEXT|	0~255字节|
|TEXT	|0~65535字节|
|MEDIUMTEXT|	0~16777215字节|
|LONGTEXT	|0~4294967295字节|

### 5.日期与时间类型
> MySQL提供的表示日期和时间的数据类型分别是 ：YEAR、DATE、TIME、DATETIME 和 TIMESTAMP。下图列举了日期和时间数据类型所对应的字节数、取值范围、日期格式以及> 零值：

|数据类型	|字节数	|取值范围	|日期格式	|零值|
| :-----| :---- | :---- |:---- |:---- |
|YEAR	|1|	1901~2155|	YYYY|	0000|
|DATE	|4|	1000-01-01~9999-12-31	|YYYY-MM-DD|	0000-00-00|
|TIME	|3	|-838：59：59~ 838：59：59|	HH:MM:SS	|00:00:00|
|DATETIME	|8|	1000-01-01 00:00:00~9999-12-31 23:59:59|	YYYY-MM-DD| HH:MM:SS	|0000-00-00 00:00:00|
|TIMESTAMP|	4	|1970-01-01 00:00:01~2038-01-19 03:14:07|	YYYY-MM-DD |HH:MM:SS|	0000-00-00 00:00:00|



## 四、数据库、数据表的基本操作
### 1.数据库的基本操作

> ```
>  create database 数据库名称;
>  show create database db1; #创建一个叫db1的数据库
>  drop database db1; #删除数据库
>  show databases; #show所有数据库
>  alter database db1 character set gbk; #将数据库的字符集修改为gbk MySQL命令
>  use db1; #切换数据库命令
>  select database(); # 查看当前使用的数据库 MySQL命令：
>  ```

### 2.数据表的基本操作
数据库创建成功后可在该数据库中创建数据表(简称为表)存储数据。请注意：在操作数据表之前应使用“USE 数据库名;”指定操作是在哪个数据库中进行先关操作，否则会抛出“No database selected”错误。
语法如下：

> ```
>  create table 表名(
>          字段1 字段类型,
>          字段2 字段类型,
>          …
>          字段n 字段类型
> );
> ```

> - 创建学生表 MySQL数据表
> ```
>  create table student(
>  id int,
>  name varchar(20),
>  gender varchar(10),
>  birthday date
>  );
>  ```
> - 查看数据表
> ```
>  show table; 
>  desc student;
>  ```
### 3.修改数据表
>  - 有时，希望对表中的某些信息进行修改，例如：修改表名、修改字段名、修改字段 数据类型…等等。在MySQL中使用**alter table**修改数据表.
> - rename 修改名字
> ```
>  alter table student rename to stu; #rename 修改命令
>  ```
>  - 修改字段名 MySQL命令：change
>  ```
>  alter table stu change name sname varchar(10); #change 修改字段命令
>  ```
>  - 修改字段数据类型 MySQL命令：modify
>  ```
>  alter table stu modify sname int; #modify修改数据类型
>  ```
>  - 增加字段 address

>  ```
>  alter table stu add address varchar(50);
>  ```

>  - 删除字段 MySQL命令：drop
>  ```
>  alter table stu drop address;
>  ```

### 4. 删除数据表
> ```
> drop table 表名;
> ```

## 五、数据表的约束
为**防止错误的数据被插入到数据表**，MySQL中定义了一些维护数据库完整性的规则；这些规则常称为表的约束。常见约束如下：

|约束条件|	说明|
|:----|:----|
|PRIMARY KEY|	主键约束用于唯一标识对应的记录|
|FOREIGN KEY	|外键约束|
|NOT NULL|	非空约束|
|UNIQUE|	唯一性约束|
|DEFAULT	|默认值约束，用于设置字段的默认值|

### 1.主键约束
> ```
> 字段名 数据类型 primary key;
> create table student(
> id int primary key,  #说明主键是id
> name varchar(20)
> );
> ```

### 2.非空约束

> ```
> create table student02(
> id int
> name varchar(20) not null
> );
> ```

### 3.默认值约束

默认值约束即DEFAULT用于给数据表中的字段指定默认值，即当在表中插入一条新记录时若未给该字段赋值，那么，数据库系统会自动为这个字段插人默认值；其基本的语法格式如下所示：
> - 字段名 数据类型 DEFAULT 默认值；
> ```
> create table student03(
> id int,
> name varchar(20),
> gender varchar(10) default 'male'
> );
> ```

### 5.唯一性约束
唯一性约束即UNIQUE用于保证数据表中字段的唯一性，**即表中字段的值不能重复出现，其基本的语法格式如下所示：**
> - 字段名 数据类型 UNIQUE;
> ```
> create table student04(
> id int,
> name varchar(20) unique
> );
> ```

### 6.外键约束
**外键约束即FOREIGN KEY常用于多张表之间的约束**基本语法如下
> - 在创建数据表时语法如下：
> CONSTRAINT 外键名 FOREIGN KEY (从表外键字段) REFERENCES 主表 (主键字段)
> -- 将创建数据表创号后语法如下：
> ALTER TABLE 从表名 ADD CONSTRAINT 外键名 FOREIGN KEY (从表外键字段) REFERENCES 主表 (主键字段);

> - 示例：创建一个学生表 MySQL命令：
> ```
> create table student05(
> id int primary key,
> name varchar(20)
> );
> ```
> - 示例：创建一个班级表 MySQL命令：
> ```
> create table class(
> classid int primary key,
> studentid int
> );
> ```


> - 示例：**学生表作为主表，班级表作为副表设置外键， MySQL命令：**
> ```
> alter table class add constraint fk_class_studentid foreign key(studentid) references student05(id);
> ```

> 显示外键约束
> ```
> show create table class;
> ```




#### 6.1 数据一致性概念
大家知道：建立外键是为了保证数据的完整和统一性。但是，如果主表中的数据被删除或修改从表中对应的数据该怎么办呢？很明显，从表中对应的数据也应该被删除，否则数据库中会存在很多无意义的垃圾数据。

#### 6.2 删除外键
> ```
> alter table 从表名 drop foreign key 外键名；
> ```
> - 删除外键 MySQL命令：
> ```
> alter table class drop foreign key fk_class_studentid;
> ```

#### 6.3 关于外键约束需要注意的细节
**1、从表里的外键通常为主表的主键**
**2、从表里外键的数据类型必须与主表中主键的数据类型一致**
**3、主表发生变化时应注意主表与从表的数据一致性问题**

## 六、数据表插入数据
在MySQL通过INSERT语句向数据表中插入数据。在此，我们先准备一张学生表，代码如下：
> ```
>  create table student(
>  id int,
>  name varchar(30),
>  age int,
>  gender varchar(30)
> );
> ```
### 1. 为表中所有字段插入数据
每个字段与其值是严格一一对应的。也就是说：每个值、值的顺序、值的类型必须与对应的字段相匹配。但是，各字段也无须与其在表中定义的顺序一致，它们只要与 VALUES中值的顺序一致即可。
语法如下：
> ``` 
> INSERT INTO 表名（字段名1,字段名2,...) VALUES (值 1,值 2,...);
> ```
> - 向学生表中插入一条学生信息 MySQL命令：
> ```
> insert into student (id,name,age,gender) values (1,'bob',16,'male');
> ```

### 2. 为表中指定字段插入数据

> ```
> INSERT INTO 表名（字段名1,字段名2,...) VALUES (值 1,值 2,...);
> ```

### 3. 同时插入多条记录
> 插入数据的方法基本和为表中所有字段插入数据，一样，只是需要插入的字段由你自己指定
> ```
> INSERT INTO 表名 [(字段名1,字段名2,...)]VALUES (值 1,值 2,…),(值 1,值 2,…),...;
> ```
> - 示例：向学生表中插入多条学生信息 MySQL命令：
> ```
> insert into student (id,name,age,gender) values (2,'lucy',17,'female'),(3,'jack',19,'male'),(4,'tom',18,'male');
> ```


## 七、更新数据
在MySQL通过UPDATE语句更新数据表中的数据。在此，我们将就用六中的student学生表
### 1. UPDATE基本语法
> ```
> UPDATE 表名 SET 字段名1=值1[,字段名2 =值2,…] [WHERE 条件表达式];
> ```
>  在该语法中：字段名1、字段名2…用于指定要更新的字段名称；值1、值 2…用于表示字段的新数据；WHERE 条件表达式 是可选的，它用于指定更新数据需要满足的条件

### 2. UPDATE更新部分数据
> - 将name为tom的记录的age设置为20并将其gender设置为female MySQL命令：
> ```
> update student set age=20,gender='female' where name='tom';
> ```

### 3. UPDATE更新全部数据

> - 将所有记录的age设置为18 MySQL命令：
> ```
> update student set age=18;
> ```

## 八、删除数据
在MySQL通过DELETE语句删除数据表中的数据。在此，我们先准备一张数据表，代码如下：
> -- 创建学生表
>  create table student(
>  id int,
>  name varchar(30),
>  age int,
>  gender varchar(30)
>  );
>  -- 插入数据
>  insert into student (id,name,age,gender) values (2,'lucy',17,'female'),(3,'jack',19,'male'),(4,'tom',18,'male'),(5,'sal',19,'female'),(6,'sun',20,'male')
> ,(7,'sad',13,'female'),(8,'sam',14,'male');

### 1. DELETE基本语法
- 在该语法中：表名用于指定要执行删除操作的表；[WHERE 条件表达式]为可选参数用于指定删除的条件。
> ```
> DELETE FROM 表名 [WHERE 条件表达式];
> ```

### 2. DELETE删除部分数据
- 示例：删除age等于14的所有记录 MySQL命令：

> ```
> delete from student where age=14;
> ```

### 3. DELETE删除全部数据
- 示例：删除student表中的所有记录 MySQL命令：
> ```
> delete from student;
> ```

### 4. TRUNCATE和DETELE的区别

**TRUNCATE和DETELE都能实现删除表中的所有数据的功能，但两者也是有区别的：
1、DELETE语句后可跟WHERE子句，可通过指定WHERE子句中的条件表达式只删除满足条件的部分记录；但是，TRUNCATE语句只能用于删除表中的所有记录。
2、使用TRUNCATE语句删除表中的数据后，再次向表中添加记录时自动增加字段的默认初始值重新由1开始；使用DELETE语句删除表中所有记录后，再次向表中添加记录时自动增加字段的值为删除时该字段的最大值加1
3、DELETE语句是DML语句，TRUNCATE语句通常被认为是DDL语句**

## 九、MySQL数据表简单查询

### 1.简单查询概述
- 简单查询即不含**where的select**语句。在此，我们讲解简单查询中最常用的两种查询：**查询所有字段和查询指定字段**。在此，先准备测试数据，代码如下：
> -- 创建数据库
> DROP DATABASE IF EXISTS mydb;
> CREATE DATABASE mydb;
> USE mydb;
> -- 创建student表
> CREATE TABLE student (
>    sid CHAR(6),
>    sname VARCHAR(50),
>    age INT,
>    gender VARCHAR(50) DEFAULT 'male'
> );
> 
> -- 向student表插入数据
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1001', 'lili', 14, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1002', 'wang', 15, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1003', 'tywd', 16, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1004', 'hfgs', 17, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1005', 'qwer', 18, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1006', 'zxsd', 19, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1007', 'hjop', 16, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1008', 'tyop', 15, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1009', 'nhmk', 13, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1010', 'xdfv', 17, 'female');
> ```

### 2.查询所有字段（方法不唯一只是举例）
- 查询所有字段 MySQL命令：
> ```
> select * from student;
> ```


### 3.查询指定字段（sid、sname）

- 查询指定字段（sid、sname） MySQL命令：
> ```
> select sid,sname from student;
> ```

### 4.常数的查询

- 在SELECT中除了书写列名，还可以书写常数。可以用于标记常数的查询日期标记 MySQL命令：

> ```
> select sid,sname,'2021-03-02' from student;
> ```

### 5.从查询结果中过滤重复数据
- 在使用DISTINCT 时需要注意：在SELECT查询语句中DISTINCT关键字只能用在第一个所查列名之前。MySQL命令：
> ```
> select distinct gender from student;
> ```

### 6.算术运算符（举例加运算符）
- 在SELECT查询语句中还可以使用加减乘除运算符。 查询学生10年后的年龄 MySQL命令：
> - 查询学生10年后的年龄 MySQL命令：
> ```
>  select sname,age+10 from student;
>  ```



## 十、函数
- 在此，先准备测试数据，代码如下：

> -- 创建数据库
> DROP DATABASE IF EXISTS mydb;
> CREATE DATABASE mydb;
> USE mydb;
> -- 创建student表
> CREATE TABLE student (
>    sid CHAR(6),
>    sname VARCHAR(50),
>    age INT,
>    gender VARCHAR(50) DEFAULT 'male'
> );
> 
> -- 向student表插入数据
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1001', 'lili', 14, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1002', 'wang', 15, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1003', 'tywd', 16, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1004', 'hfgs', 17, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1005', 'qwer', 18, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1006', 'zxsd', 19, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1007', 'hjop', 16, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1008', 'tyop', 15, 'female');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1009', 'nhmk', 13, 'male');
> INSERT INTO student (sid,sname,age,gender) VALUES ('S_1010', 'xdfv', 17, 'female');
> ``

### 1.聚合函数
在开发中，我们常常有类似的需求：**统计某个字段的最大值、最小值、 平均值等等。为此，MySQL中提供了聚合函数来实现这些功能。所谓聚合，就是将多行汇总成一行；其实，所有的聚合函数均如此——输入多行，输出一行。聚合函数具有自动滤空的功能，若某一个值为NULL，那么会自动将其过滤使其不参与运算。
聚合函数使用规则：
只有SELECT子句和HAVING子句、ORDER BY子句中能够使用聚合函数。例如，在WHERE子句中使用聚合函数是错误的。
接下来，我们学习常用聚合函数**

#### 1.1、count（）
> - 统计表中数据的行数或者统计指定列其值不为NULL的数据个数查询有多少该表中有多少人MySQL命令：
> ```
> select count(*) frome student;
> ```

#### 1.2、max（）
- 计算指定列的最大值，如果指定列是字符串类型则使用字符串排序运算

> - 查询该学生表中年纪最大的学生
> ```
> select max(age) from student;
> ```

#### 1.3、min（）
- 计算指定列的最小值，如果指定列是字符串类型则使用字符串排序运算
> - 查询该学生表中年纪最小的学生 MySQL命令：
> ```
> select sname,min(age) from student;
> ```


#### 1.4、sum（）
- 计算指定列的数值和，如果指定列类型不是数值类型则计算结果为0
> - 查询该学生表中年纪的总和 MySQL命令：
> ```
> select sum(age) from student;
> ```


#### 1.5、avg（）
- 计算指定列的平均值，如果指定列类型不是数值类型则计算结果为
> - 查询该学生表中年纪的平均数 MySQL命令：
> ```
> select avg(age) from student;
> ```


### 2.其他常用函数
#### 2.1 时间函数
```
SELECT NOW();
SELECT DAY (NOW());
SELECT DATE (NOW());
SELECT TIME (NOW());
SELECT YEAR (NOW());
SELECT MONTH (NOW());
SELECT CURRENT_DATE();
SELECT CURRENT_TIME();
SELECT CURRENT_TIMESTAMP();
SELECT ADDTIME('14:23:12','01:02:01');
SELECT DATE_ADD(NOW(),INTERVAL 1 DAY);
SELECT DATE_ADD(NOW(),INTERVAL 1 MONTH);
SELECT DATE_SUB(NOW(),INTERVAL 1 DAY);
SELECT DATE_SUB(NOW(),INTERVAL 1 MONTH);
SELECT DATEDIFF('2019-07-22','2019-05-05');
```

#### 2.2、字符串函数
```
--连接函数
SELECT CONCAT ()
--
SELECT INSTR ();
--统计长度
SELECT LENGTH();
```
#### 2.3、数学函数

```
-- 绝对值
SELECT ABS(-136);
-- 向下取整
SELECT FLOOR(3.14);
-- 向上取整
SELECT CEILING(3.14);
```

## 十一、条件查询
- 数据库中存有大量数据，我们可根据需求获取指定的数据。此时，我们可在查询语句中通过**WHERE**子句指定查询条件对查询结果进行过滤。在开始学习条件查询之前，我们先准备测试数据，代码如下：
```
-- 创建数据库
DROP DATABASE IF EXISTS mydb;
CREATE DATABASE mydb;
USE mydb;

-- 创建student表
CREATE TABLE student (
    sid CHAR(6),
    sname VARCHAR(50),
    age INT,
    gender VARCHAR(50) DEFAULT 'male'
);

-- 向student表插入数据
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1001', 'lili', 14, 'male');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1002', 'wang', 15, 'female');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1003', 'tywd', 16, 'male');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1004', 'hfgs', 17, 'female');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1005', 'qwer', 18, 'male');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1006', 'zxsd', 19, 'female');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1007', 'hjop', 16, 'male');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1008', 'tyop', 15, 'female');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1009', 'nhmk', 13, 'male');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1010', 'xdfv', 17, 'female');
INSERT INTO student (sid,sname,age,gender) VALUES ('S_1012', 'lili', 14, 'male');
```

### 1.使用关系运算符查询
- 在**WHERE**中可使用关系运算符进行条件查询，常用的关系运算符如下所示：

> |关系运算符|	说明|
> |:----|:----|
> |=|	等于|
> |<>	|不等于|
> |!=|	不等于|
> |<	|小于|
> |<=	|小于等于|
> |>|	大于|
> |>=	|大于等于|

> - 查询年龄等于或大于17的学生的信息 MySQL命令：
> ```
> select * from student where age>=17;
> ```

### 2.使用IN关键字查询
- **IN关键字**用于判断某个字段的值是否在指定集合中。如果字段的值恰好在指定的集合中，则将字段所在的记录将査询出来。
> - 查询sid为1002和1003的学生信息 MySQL命令：
> ```
> select * from student where sid in('1001','1003');
> ```

> - 查询sid为1001以外的学生的信息 MySQL命令：
> ```
> select * from student where sid not in ('1001');
> ```

### 3.使用BETWEEN AND关键字查询
- **between and**用于判断某个字段的值是否在指定的范围之内。如果字段的值在指定范围内，则将所在的记录将查询出来
查询15到18岁的学生信息 MySQL命令：
> ```
> select * from student where age between 15 and 18;
> ```

### 4.使用空值查询

- 在MySQL中，使用 **is null** 关键字判断字段的值是否为空值。请注意：空值NULL不同于0，也不同于空字符串由于student表没有空值就不演示查询空值的了

> ``` 
> select * from student where sname is  null;
> select * from student where sname is not null;
> ```

### 5.使用AND关键字查询
- 在MySQL中可使用**and**关键字可以连接两个或者多个查询条件。

> - 查询年纪大于15且性别为male的学生信息 MySQL命令：
> ```
> select * from student where age>15 and gender="male";
> ```

### 6.使用OR关键字查询
- 在使用SELECT语句查询数据时可使用**or**关键字连接多个査询条件。在使用OR关键字时，只要记录满足其中任意一个条件就会被查询出来
> - 查询年纪大于15或者性别为male的学生信息 MySQL命令：
> ```
> elect * from student where age>18 or gender="male";
> ```

### 7.使用LIKE关键字查询
- MySQL中可使用**like**关键字可以判断两个字符串是否相匹配

#### 7.1 普通字符串
> - 查询sname中与lihua匹配的学生信息 MySQL命令：
> ```
> select * from student where sname like "lihua";
> ```



#### 7.2 含有%通配的字符串
- %用于匹配任意长度的字符串。例如，字符串“a%”匹配以字符a开始任意长度的字符串
> - 查询学生姓名以li开始的记录 MySQL命令：
> ``
> select * from student where sname like 'li%';
> ```
> - 查询以a结尾的记录
> ```
> select * from student where sname like '%a';
> ```

> - 查询包含u的记录
> ```
> select * from student where sname like "%u%";
> ```

#### 7.3 含有_通配的字符串
- 下划线通配符只匹配单个字符，如果要匹配多个字符，需要连续使用多个下划线通配符。例如，字符串“ab_”匹配以字符串“ab”开始长度为3的字符串，如abc、abp等等；字符串“a__d”匹配在字符“a”和“d”之间包含两个字符的字符串，如"abcd"、"atud"等等。
> - 查询以li开头且长度为5的字符串
> ```
> select * from student where sname like 'li___';
> ```

### 8.使用LIMIT限制查询结果的数量
> - order by... asc 以升序排列
> - 查询年纪最小的三个人
> ```
> select * from student order by age asc limit 4;
> ```

### 9.使用GROUP BY进行分组查询
- **GROUP BY** 子句可像切蛋糕一样将表中的数据进行分组，再进行查询等操作。换言之，可通俗地理解为：通过GROUP BY将原来的表拆分成了几张小表。接下来，我们通过一个例子开始学习GROUP BY，代码如下

```
-- 创建数据库
DROP DATABASE IF EXISTS mydb;
CREATE DATABASE mydb;
USE mydb;

-- 创建员工表
CREATE TABLE employee (
    id int,
    name varchar(50),
    salary int,
    departmentnumber int
);

-- 向员工表中插入数据
INSERT INTO employee values(1,'tome',2000,1001); 
INSERT INTO employee values(2,'lucy',9000,1002); 
INSERT INTO employee values(3,'joke',5000,1003); 
INSERT INTO employee values(4,'wang',3000,1004); 
INSERT INTO employee values(5,'chen',3000,1001); 
INSERT INTO employee values(6,'yukt',7000,1002); 
INSERT INTO employee values(7,'rett',6000,1003); 
INSERT INTO employee values(8,'mujk',4000,1004); 
INSERT INTO employee values(9,'poik',3000,1001);
```

#### 9.1 GROUP BY和聚合函数一起使用

> - 统计各部门员工个数 MySQL命令：
> ```
> select count(*),departmentnumber from employee group by departmentnumber;
> ```

> - 统计部门编号大于1001的各部门员工个数 MySQL命令
> ```
> select count(*), departmentnumber from employee where departmentnumber>1001 group by departmentnumber;
> ```

#### 9.2 GROUP BY和聚合函数以及HAVING一起使用(group by  ..... having 配合聚合函数查询一定范围的数据)
> - 统计工资总和大于8000的部门 MySQL命令
> ```
> select sum(salary), departmentnumber from employee group by departmentnumber having sum(salary)>8000;
> ```

### 10.使用ORDER BY对查询结果排序（order by ... asc/dsc)
- 从表中査询出来的数据可能是无序的或者其排列顺序不是我们期望的。为此，我们可以使用ORDER BY对查询结果进行排序其语法格式如下所示：
```
SELECT 字段名1,字段名2,…
FROM 表名
ORDER BY 字段名1 [ASC 丨 DESC],字段名2 [ASC | DESC];
```

在该语法中：字段名1、字段名2是查询结果排序的依据；参数 ASC表示按照升序排序，DESC表示按照降序排序；默认情况下，按照ASC方式排序。通常情况下，ORDER BY子句位于整个SELECT语句的末尾。
- 查询所有职工按照salary大小升序/降序排列 MySQL命令：
> ```
> select * from employee order by salary asc;
> select * from student order by age desc;
> ```



## 十二、别名设置
- 在査询数据时可为表和字段取別名，该别名代替表和字段的原名参与查询操作。

### 1.为表取别名
- 在查询操作时，假若表名很长使用起来就不太方便，此时可为表取一个別名，用该别名来代替表的名称。语法格式如下所示：
```
select * from 表名 as 表的别名 where ...
```

### 2.为字段取别名
- 在查询操作时，假若字段名很长使用起来就不太方便，此时可该字段取一个別名，用该别名来代替字段的名称。语法格式如下所示：
```
SELECT 字段名1 [AS] 别名1 , 字段名2 [AS] 别名2 , ... FROM 表名 WHERE ... ;
```
> - 更改employee
> ```
> select id as id2,name as names  from employee;
> ```

## 十三、表的关联关系
在实际开发中数据表之间存在着各种关联关系。在此，介绍MySQL中数据表的三种关联关系。
- 多对一
多对一(亦称为一对多)是数据表中最常见的一种关系。例如：员工与部门之间的关系，一个部门可以有多个员工；而一个员工不能属于多个部门只属于某个部门。在多对一的表关系 中，应将外建在多的一方否则会造成数据的冗余。
- 多对多
多对多是数据表中常见的一种关系。例如：学生与老师之间的关系，一个学生可以有多个老师而且一个老师有多个学生。通常情况下，为了实现这种关系需要定义一张中间表(亦称为连接表)该表会存在两个外键分别参照老师表和学生表。
- 一对一
在开发过程中，一对一的关联关系在数据库中并不常见；因为以这种方式存储的信息通常会放在同一张表中。
接下来，我们来学习在一对多的关联关系中如果添加和删除数据。先准备一些测试数据，代码如下：
```
DROP TABLE IF EXISTS student;
DROP TABLE IF EXISTS class;

-- 创建班级表
CREATE TABLE class(
    cid int(4) NOT NULL PRIMARY KEY,
    cname varchar(30) 
);

-- 创建学生表
CREATE TABLE student(
    sid int(8) NOT NULL PRIMARY KEY,
    sname varchar(30),
    classid int(8) NOT NULL
);

-- 为学生表添加外键约束
ALTER TABLE student ADD CONSTRAINT fk_student_classid FOREIGN KEY(classid) REFERENCES class(cid);
-- 向班级表插入数据
INSERT INTO class(cid,cname)VALUES(1,'Java');
INSERT INTO class(cid,cname)VALUES(2,'Python');

-- 向学生表插入数据
INSERT INTO student(sid,sname,classid)VALUES(1,'tome',1);
INSERT INTO student(sid,sname,classid)VALUES(2,'lucy',1);
INSERT INTO student(sid,sname,classid)VALUES(3,'lili',2);
INSERT INTO student(sid,sname,classid)VALUES(4,'domi',2);
```
> ```
> - 为学生表结构添加外键
> alter table student add constraint fk_student_classid foreign key(主键) references class(链接键);
> ```

### 1.关联查询
- 查询Java班的所有学生 MySQL命令：
```
select * from student where classid=(select cid from class where cname='Java');

```

### 2.关于关联关系的删除数据
- 请从班级表中删除Java班级。在此，请注意：班级表和学生表之间存在关联关系；要删除Java班级，应该先删除学生表中与该班相关联的学生。否则，假若先删除Java班那么学生表中的cid就失去了关联
> - 删除Java班 MySQL命令：
> ```
> delete from student where classid=(select cid from class where cname='Java';
> ```

## 十四、多表连接查询
### 1.交叉连接查询
- 交叉连接返回的结果是被连接的两个表中所有数据行的笛卡儿积；比如：集合A={a,b}，集合B={0,1,2}，则集合A和B的笛卡尔积为{(a,0),(a,1),(a,2),(b,0),(b,1),(b,2)}。所以，交叉连接也被称为笛卡尔连接，其语法格式如下：
```
SELECT * FROM 表1 CROSS JOIN 表2;
```
在该语法中：CROSS JOIN用于连接两个要查询的表，通过该语句可以查询两个表中所有的数据组合。
**由于这个交叉连接查询在实际运用中没有任何意义，所以只做为了解即可**

### 2.内连接查询
- 内连接(Inner Join)又称简单连接或自然连接，是一种非常常见的连接查询。内连接使用比较运算符对两个表中的数据进行比较并列出与连接条件匹配的数据行，组合成新的 记录。也就是说在内连接查询中只有满足条件的记录才能出现在查询结果中。其语法格式如下：

```
SELECT 查询字段1,查询字段2, ... FROM 表1 [INNER] JOIN 表2 ON 表1.关系字段=表2.关系字段
```
准备数据，代码如下：
```
-- 若存在数据库mydb则删除
DROP DATABASE IF EXISTS mydb;
-- 创建数据库mydb
CREATE DATABASE mydb;
-- 选择数据库mydb
USE mydb;

-- 创建部门表
CREATE TABLE department(
  did int (4) NOT NULL PRIMARY KEY, 
  dname varchar(20)
);

-- 创建员工表
CREATE TABLE employee (
  eid int (4) NOT NULL PRIMARY KEY, 
  ename varchar (20), 
  eage int (2), 
  departmentid int (4) NOT NULL
);

-- 向部门表插入数据
INSERT INTO department VALUES(1001,'财务部');
INSERT INTO department VALUES(1002,'技术部');
INSERT INTO department VALUES(1003,'行政部');
INSERT INTO department VALUES(1004,'生活部');
-- 向员工表插入数据
INSERT INTO employee VALUES(1,'张三',19,1003);
INSERT INTO employee VALUES(2,'李四',18,1002);
INSERT INTO employee VALUES(3,'王五',20,1001);
INSERT INTO employee VALUES(4,'赵六',20,1004);
```
- 查询员工姓名及其所属部门名称 MySQL命令：
> ```
> select employee.ename,department.dname from department inner join employee on department.did=employee.departmentid;
> ```

### 3.外连接查询
- 在使用内连接查询时我们发现：返回的结果只包含符合查询条件和连接条件的数据。但是，有时还需要在返回查询结果中不仅包含符合条件的数据，而且还包括左表、右表或两个表中的所有数据，此时我们就需要使用外连接查询。外连接又分为左(外)连接和右(外)连接。其语法格式如下：

```
SELECT 查询字段1,查询字段2, ... FROM 表1 LEFT | RIGHT [OUTER] JOIN 表2 ON 表1.关系字段=表2.关系字段 WHERE 条件
```

由此可见，外连接的语法格式和内连接非常相似，只不过使用的是LEFT [OUTER] JOIN、RIGHT [OUTER] JOIN关键字。其中，关键字左边的表被称为左表，关键字右边的表被称为右表；OUTER可以省略。
在使用左(外)连接和右(外)连接查询时，查询结果是不一致的，具体如下：
1、LEFT [OUTER] JOIN 左(外)连接：返回包括左表中的所有记录和右表中符合连接条件的记录。
2、RIGHT [OUTER] JOIN 右(外)连接：返回包括右表中的所有记录和左表中符合连接条件的记录。
```
-- 若存在数据库mydb则删除
DROP DATABASE IF EXISTS mydb;
-- 创建数据库mydb
CREATE DATABASE mydb;
-- 选择数据库mydb
USE mydb;

-- 创建班级表
CREATE TABLE class(
  cid int (4) NOT NULL PRIMARY KEY, 
  cname varchar(20)
);

-- 创建学生表
CREATE TABLE student (
  sid int (4) NOT NULL PRIMARY KEY, 
  sname varchar (20), 
  sage int (2), 
  classid int (4) NOT NULL
);
-- 向班级表插入数据
INSERT INTO class VALUES(1001,'Java');
INSERT INTO class VALUES(1002,'C++');
INSERT INTO class VALUES(1003,'Python');
INSERT INTO class VALUES(1004,'PHP');

-- 向学生表插入数据
INSERT INTO student VALUES(1,'张三',20,1001);
INSERT INTO student VALUES(2,'李四',21,1002);
INSERT INTO student VALUES(3,'王五',24,1002);
INSERT INTO student VALUES(4,'赵六',23,1003);
INSERT INTO student VALUES(5,'Jack',22,1009);
```
准备这组数据有一定的特点，为的是让大家直观的看出左连接与右连接的不同之处
1、班级编号为1004的PHP班级没有学生
2、学号为5的学生王跃跃班级编号为1009，该班级编号并不在班级表中

#### 3.1 左（外）连接查询
- 左(外)连接的结果包括LEFT JOIN子句中指定的左表的所有记录，以及所有满足连接条件的记录。如果左表的某条记录在右表中不存在则在右表中显示为空。查询每个班的班级ID、班级名称及该班的所有学生的名字 MySQL命令：

> ```
> select class.cid,class.cname,student.sname from class left outer join student on class.cid=student.classid;
> ```

展示结果分析：
1、分别找出Java班、C++班、Python班的学生
2、右表的王跃跃不满足查询条件故其没有出现在查询结果中
3、虽然左表的PHP班没有学生，但是任然显示了PHP的信息；但是，它对应的学生名字为NULL

## 十五、子查询
- 子查询是指一个查询语句嵌套在另一个查询语句内部的查询；该查询语句可以嵌套在一个 SELECT、SELECT…INTO、INSERT…INTO等语句中。在执行查询时，首先会执行子查询中的语句，再将返回的结果作为外层查询的过滤条件。在子査询中通常可以使用比较运算符和IN、EXISTS、ANY、ALL等关键字。
准备数据
```
DROP TABLE IF EXISTS student;
DROP TABLE IF EXISTS class;

-- 创建班级表
CREATE TABLE class(
  cid int (4) NOT NULL PRIMARY KEY, 
  cname varchar(20)
);

-- 创建学生表
CREATE TABLE student (
  sid int (4) NOT NULL PRIMARY KEY, 
  sname varchar (20), 
  sage int (2), 
  classid int (4) NOT NULL
);

-- 向班级表插入数据
INSERT INTO class VALUES(1001,'Java');
INSERT INTO class VALUES(1002,'C++');
INSERT INTO class VALUES(1003,'Python');
INSERT INTO class VALUES(1004,'PHP');
INSERT INTO class VALUES(1005,'Android');

-- 向学生表插入数据
INSERT INTO student VALUES(1,'张三',20,1001);
INSERT INTO student VALUES(2,'李四',21,1002);
INSERT INTO student VALUES(3,'王五',24,1003);
INSERT INTO student VALUES(4,'赵六',23,1004);
INSERT INTO student VALUES(5,'小明',21,1001);
INSERT INTO student VALUES(6,'小红',26,1001);
INSERT INTO student VALUES(7,'小亮',27,1002);
```
### 1.带比较运算符的子查询
- 比较运算符前面我们提到过得，就是>、<、=、>=、<=、!=等
查询张三同学所在班级的信息 MySQL命令：
```
select * from class where cid=(select classid from student where sname='张三');
```

### 2.带EXISTS关键字的子查询
EXISTS关键字后面的参数可以是任意一个子查询， 它不产生任何数据只返回TRUE或FALSE。当返回值为TRUE时外层查询才会 执行
假如王五同学在学生表中则从班级表查询所有班级信息 MySQL命令：

```
select * from class where exists (select * from student where sname='王五');
```


### 3.带ANY关键字的子查询
- ANY关键字表示满足其中任意一个条件就返回一个结果作为外层查询条件。

查询比任一学生所属班级号还大的班级编号 MySQL命令：

```
select * from class where cid>any(select classid from student);
```

### 4.带ALL关键字的子查询
- ALL关键字与ANY有点类似，只不过带ALL关键字的子査询返回的结果需同时满足所有内层査询条件。

查询比所有学生所属班级号还大的班级编号 MySQL命令：
```
select * from class where cid > all (select classid from student);
```


## 总结
重要（从关键字分析）：
查询语句的书写顺序和执行顺序t
select ===> from ===> where ===> group by ===> having ===> order by ===> limit
查询语句的执行顺序
from ===> where ===> group by ===> having ===> select ===> order by ===> limit

# MySQL提高部分
## 1存储引擎
### 1.1 存储引擎介绍
- innoDB
> INNODB是默认的mysql存储引擎
> - 特点
> DML 操作遵循ACID模型，支持**事务**;
> **行级锁**，提高并发访问性能
> 支持**外键**FOREIGN KEY 约束，保证数据的完整性和正确性;
> - 文件
> xxz.ibd:xxx代表的是表名，innoDB引擎的每张表都会对应这样一个表空间文件，存储该表的表结构（frm，sdi)、数据和索引。

- **MyISAM**
- 介绍
myisam是早期mysql的存储引擎

- 特点
不支持事务，不支持外键
支持表锁、不支持行锁
访问速度快
- 文件
xxx.sdi:存储表结构信息
xxx.MYD:存储数据
xxx.MYI:存储索引

- **Memory**
- 介绍
 Memony引擎的表数据时存储在**内存**中，由于受到硬件的问题、或者断电问题的影向，只能将这些表作为临时表或缓存使用。
 - 特点
 内存存放
 hash索引
 - 文件
 xxx.sdi:存储表结构信息
 ---------------------查表
 
 ### 1.2.存储引擎选择
 -----插图
 
 - 总结
 > 1、体系结构
 > > 链接层、服务层、引擎层、存储层
 > 2、存储引擎简介
 > 3.存储引擎特点
 > > innodb myisam：事务、锁、
 - 番外安装linux的mysq.....
 1. 启动mysql服务
 ```
 systemctl start mtsql
 systemctl restart mysql
 systemctl stop mysql
 ```
 2.查询自动生成的root用户密码
 ```
 grep 'temporary password' /var/log/mysql.log
 ```
 3.执行命令：
 ```
 mysql -u root -p
 ```
 4.输入查询到的自动生成的密码登陆：
 5.改密码
 ```
 ALTER USER 'root'@'localhost' IDENTIFIED BY '123456'
 ```
 
 
 
 
 ## 2.索引
 
 























