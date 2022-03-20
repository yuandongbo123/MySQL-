# MySQL-学习笔记

## 0.基础用法
[参考原文链接]"https://blog.csdn.net/weixin_45851945/article/details/114287877"
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
> **1、DDL(Data Definition Language) 数据定义语言，用来操作数据库、表、列等； 常用语句：CREATE、 ALTER、DROP
> 2、DML(Data Manipulation Language) 数据操作语言，用来操作数据库中表里的数据；常用语句：INSERT、 UPDATE、 DELETE
> 3、DCL(Data Control Language) 数据控制语言，用来操作访问权限和安全级别； 常用语句：GRANT、DENY
> 4、DQL(Data Query Language) 数据查询语言，用来查询数据 常用语句：SELECT**


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
> create database 数据库名称;
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
> ···
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
>  ```
>  有时，希望对表中的某些信息进行修改，例如：修改表名、修改字段名、修改字段 数据类型…等等。在MySQL中使用**alter table**修改数据表.
> ```
> - rename 修改名字
>  alter table student rename to stu; #rename 修改命令
>  ```
>  - 修改字段名 MySQL命令：change
>  ```
>  alter table stu change name sname varchar(10); #change 修改字段命令
>  ```
>  - 修改字段数据类型 MySQL命令：modify
>  ```
>  alter table stu modify sname int; #modify修改数据类型
>  ···
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
? id int primary key,  #说明主键是id
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
> 字段名 数据类型 DEFAULT 默认值；
> ```
> create table student03(
> id int,
> name varchar(20),
> gender varchar(10) default 'male'
> );
> ```

### 5.唯一性约束
唯一性约束即UNIQUE用于保证数据表中字段的唯一性，**即表中字段的值不能重复出现，其基本的语法格式如下所示：**
> 字段名 数据类型 UNIQUE;
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
> 


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
***1、从表里的外键通常为主表的主键
2、从表里外键的数据类型必须与主表中主键的数据类型一致
3、主表发生变化时应注意主表与从表的数据一致性问题**

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










