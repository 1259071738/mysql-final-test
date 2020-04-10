# mysql-final-test

2019-2020 mysql final test

姓名：刘飞虎

学号：17061518

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
~~~sql
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:01:10 |
+---------------------+
1 row in set (0.06 sec)
~~~

2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果

~~~sql
mysql> select concat("刘飞虎+",17061518);
+-------------------------------+
| concat("刘飞虎+",17061518)    |
+-------------------------------+
| 刘飞虎+17061518               |
+-------------------------------+
1 row in set (0.13 sec)
~~~

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptno,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```

~~~sql
mysql> create database text_db;
Query OK, 1 row affected (0.20 sec)

mysql> use text_db;
Database changed
mysql> create table biao1
    -> (
    -> deptno int(10) primary key,
    -> dname varchar(25),
    -> loc varchar(25)
    -> );
Query OK, 0 rows affected (1.53 sec)

mysql> insert into biao1
    -> (deptno,dname,loc)
    -> values(10,'ACCOUNTING','NEW YORK'),(20,'RESEARCH','DALLAS'),(30,'SALES','CHICAGO'),(40,'OPERATIONS','BOSTON');
Query OK, 4 rows affected (0.11 sec)
Records: 4  Duplicates: 0  Warnings: 0
~~~

表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```

~~~sql
mysql> use text_db;
Database changed
mysql> create table biao
    -> (
    -> deptno INT NOT NULL,
    -> empno INT  PRIMARY KEY,
    -> ename VARCHAR(20),
    -> job  VARCHAR(20),
    ->     MGR  INT,
    -> Hiredate Date,
    -> sal float,
    -> comm float
    -> );
Query OK, 0 rows affected (0.48 sec)
mysql> INSERT INTO biao(empno, ename, job, MGR, Hiredate, sal, comm, deptno)
    -> values(7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
    -> ;
Query OK, 13 rows affected (0.17 sec)
Records: 13  Duplicates: 0  Warnings: 0
~~~

3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`

~~~sql
mysql> INSERT INTO biao(empno, ename, job, MGR, Hiredate, sal, comm, deptno)
    -> values(17061518,"liufeihu","std",0219,"1998-02-19",null,null,10);
Query OK, 1 row affected (0.14 sec)
~~~
3.2 表中入职时间（Hiredate字段）最短的人。
~~~sql
mysql> select*from biao where Hiredate =(select max(Hiredate) from biao);
+--------+----------+----------+------+------+------------+------+------+
| deptno | empno    | ename    | job  | MGR  | Hiredate   | sal  | comm |
+--------+----------+----------+------+------+------------+------+------+
|     10 | 17061518 | liufeihu | std  |  219 | 1998-02-19 | NULL | NULL |
+--------+----------+----------+------+------+------------+------+------+
1 row in set (0.17 sec)
~~~

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？

~~~sql
mysql> select distinct job from biao;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
| std       |
+-----------+
6 rows in set (0.14 sec)
~~~
由运行结果可以看到，这次查询结果返回了6条记录的 age 值，且没有重复的值.

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
~~~sql
mysql> update biao
    -> set comm=100
    -> where empno=7934;
Query OK, 1 row affected (0.17 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select*from biao where comm<100;
+--------+-------+--------+----------+------+------------+------+------+
| deptno | empno | ename  | job      | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+----------+------+------------+------+------+
|     30 |  7844 | TURNER | SALESMAN | 7689 | 1981-03-12 | 1500 |    0 |
+--------+-------+--------+----------+------+------------+------+------+
1 row in set (0.01 sec)
~~~


3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
~~~sql
mysql> select ename,sal+comm,count(ename) counts,AVG(sal+comm) average_sal_comm from biao;
+-------+----------+--------+------------------+
| ename | sal+comm | counts | average_sal_comm |
+-------+----------+--------+------------------+
| SMITH |     NULL |     14 |             1950 |
+-------+----------+--------+------------------+
1 row in set (0.01 sec)
~~~
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
~~~sql
mysql> select t1.ename My_b_b_name,t2.ename My_b_name ,t3.ename My_name
    -> from (biao t1 inner join biao t2 on t1. empno= t2. mgr)  inner join biao t3
    -> on t2.empno = t3.mgr;
+-------------+-----------+---------+
| My_b_b_name | My_b_name | My_name |
+-------------+-----------+---------+
| JONES       | FORD      | SMITH   |
| KING        | BLAKE     | ALLEN   |
| KING        | BLAKE     | WARD    |
| KING        | BLAKE     | MARTIN  |
| KING        | JONES     | SCOTT   |
| JONES       | SCOTT     | ADAMS   |
| KING        | BLAKE     | JAMES   |
| KING        | JONES     | FORD    |
+-------------+-----------+---------+
8 rows in set (0.05 sec)
~~~

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
~~~sql
mysql> select * from biao1 t1 inner join biao t2 on t1.deptno=t2.deptno;
+--------+------------+----------+--------+----------+----------+-----------+------+------------+------+------+
| deptno | dname      | loc      | deptno | empno    | ename    | job       | MGR  | Hiredate   | sal  | comm |
+--------+------------+----------+--------+----------+----------+-----------+------+------------+------+------+
|     20 | RESEARCH   | DALLAS   |     20 |     7369 | SMITH    | CLERK     | 7902 | 1981-03-12 |  800 | NULL |
|     30 | SALES      | CHICAGO  |     30 |     7499 | ALLEN    | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 | SALES      | CHICAGO  |     30 |     7521 | WARD     | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 | RESEARCH   | DALLAS   |     20 |     7566 | JONES    | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 | SALES      | CHICAGO  |     30 |     7654 | MARTIN   | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 | ACCOUNTING | NEW YORK |     10 |     7698 | BLAKE    | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 | RESEARCH   | DALLAS   |     20 |     7788 | SCOTT    | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 | ACCOUNTING | NEW YORK |     10 |     7839 | KING     | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 | SALES      | CHICAGO  |     30 |     7844 | TURNER   | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 | RESEARCH   | DALLAS   |     20 |     7878 | ADAMS    | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 | SALES      | CHICAGO  |     30 |     7900 | JAMES    | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 | RESEARCH   | DALLAS   |     20 |     7902 | FORD     | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 | ACCOUNTING | NEW YORK |     10 |     7934 | MILLER   | CLERK     | 7782 | 1981-03-12 | 1300 |  100 |
|     10 | ACCOUNTING | NEW YORK |     10 | 17061518 | liufeihu | std       |  219 | 1998-02-19 | NULL | NULL |
+--------+------------+----------+--------+----------+----------+-----------+------+------------+------+------+
14 rows in set (0.00 sec)

mysql> create view biao3
    -> as
    -> select empno,ename,job,loc from biao1 t1 inner join biao t2 on t1.deptno=t2.deptno;
Query OK, 0 rows affected (0.14 sec)
~~~

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？


3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引

3.10 将表2的 sal 字段改名为 salary
~~~sql
mysql> ALTER TABLE biao
    -> CHANGE sal salary float;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
~~~


3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。


4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
~~~sql
mysql> create user 'liufeihu'
    -> identified by '17061518';
Query OK, 0 rows affected (0.43 sec)
~~~

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。


4.2 显示该账号权限


4.3 `with grant option` 是什么意思。

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？<br/>
答：外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据百库的数据视图，是与某一应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录度(外模式)，也可以利用数据操纵语言(Data Manipulation Language，DML)对这些数据记录进行操作。外模式反映了数据库的用户观知。
    内模式：内模式又称存储模式，对应于物理级，它是数据库中全体数据的内部表示或底道层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义，它是数据库的存储观内。
   在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式容和定义、描述数据库逻辑结构的模式，也是唯一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是唯一的，也不可能是唯一的。
8 什么是ACID？<br/>
     ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。
8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？<br/>
一般情况下，mysql会默认百提供多种存储引擎,你可以通过下面的查看:
看你的度mysql现在已提供什么存储引擎:
mysql> show engines;
看你的mysql当前默认的存储引擎:
mysql> show variables like '%storage_engine%';
你要看某个表用了什么引擎(在显示专结果里参数engine后面的属就表示该表当前用的存储引擎):
mysql> show create table 表名;
8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？<br/>
如数据版备份、复杂连接查询、一致性数据存储等，还是使用MySQL或者其他传统的关系型数据库最合适；如果需要短时间响应的查权询操作，没有良好模式定义的数据存储，或者模式更改频繁的数据存储还是用NoSQL。
