

MySQL修改密码

```mysql  

mysqladmin -uroot -pgalaxy password 'oracle';
```



-- mysql 查看已安装的编译参数
-- mysql 5.5
export VISUAL=vim
mysqlbug
-- mysql 5.1
mysqlbug |grep CONFIG

-- 追踪mysql 进程中的所有线程
pstack process

-- MySQL链接
mysql -h localhost -uroot -p 


-- MySQL查看版本
select version();

-- MySQL查看时间
select current_date;

-- MySQL执行OS命令
system clear 或 \! clear			#有空格

-- MySQL查询多个参数
select version(),current_date;

-- MySQL结束符区别
mysql> select version(),current_date;
+-----------+--------------+
| version() | current_date |
+-----------+--------------+
| 5.5.56    | 2018-01-03   |
+-----------+--------------+
1 row in set (0.00 sec)

mysql> select version(),current_date\g
+-----------+--------------+
| version() | current_date |
+-----------+--------------+
| 5.5.56    | 2018-01-03   |
+-----------+--------------+
1 row in set (0.00 sec)

mysql> select version(),current_date\G
*************************** 1. row ***************************
   version(): 5.5.56
current_date: 2018-01-03
1 row in set (0.00 sec)

-- MySQL运算
select 6*7;

-- MySQL查看数据库/表
show databases;
show tables;

-- MySQL查看表属性
describe test1;
desc test1;

-- MySQL创建/删除/修改表
create table test1 as select * from student;
create table test2(id int,name varchar(30));
drop table test1;
alter table test2 rename t2;
alter table t2 add email varchar(100);
alter table t2 drop column email;
alter table t2 modify name varchar(50); 
alter table t2 change column name first_name varchar(50);

-- MySQL插入数据
insert into t2(1,'A');
insert into t2(id,first_name) values(1,'A');

-- MySQL创建/删除数据库
create database testdb;
create database testdb
    [DEFAULT] CHARACTER SET [=] charset_name
  | [DEFAULT] COLLATE [=] collation_name;

drop database testdb;

-- MySQL切换数据库
use testdb;

-- SQL语句分类
-- DDL
create		alter		drop		rename	

-- DML
insert		delete		update		select

-- DCL
grant		revoke

-- TCL
commit		savepoint	rollback

-- MySQL修改用户属性
update mysql.user set host='192.168.45.1' where user='root' and host='localhost'; 
flush privileges;   


-- MySQL where支持的运算符
=		等于
<>		不等于
>		大于
<		小于
>=		大于等于
<=		小于等于
between	范围
like	匹配模式

select distinct first_name from t2;


-- MySQL用户管理
rename galaxy to mapy;
set password=password('oracle');
set password for root = password('oracle');
create user 'test1'@'192.168.45.%' identified by 'oracle';
drop user 'test1'@'192.168.45.%';
drop user test1;


-- MySQL权限层级
1.全局层级
2.数据库层级
3.表层级
4.列层级
5.子程序层级

-- MySQL权限管理
GRANT ALL ON *.* TO 'jeffrey'@'localhost';
GRANT ALL ON db1.* TO 'jeffrey'@'localhost';
GRANT SELECT ON db2.invoice TO 'jeffrey'@'localhost';
GRANT USAGE ON *.* TO 'jeffrey'@'localhost' WITH MAX_QUERIES_PER_HOUR 90;
REVOKE INSERT ON *.* FROM 'jeffrey'@'localhost';

-- MySQL备份/恢复
mysqldump -uroot -poracle -B -a sampdb >sampdb2.sql
mysql -e "source /path-to-backup/backup-file.sql" db_name
mysql db_name < backup-file.sql

-- MySQL字符集
SHOW CHARACTER SET;
SHOW variables like 'collation%';
SHOW variables like 'character_set%';

ALTER {DATABASE | SCHEMA} [db_name]
    alter_specification ...
ALTER {DATABASE | SCHEMA} db_name
    UPGRADE DATA DIRECTORY NAME

alter_specification:
    [DEFAULT] CHARACTER SET [=] charset_name
  | [DEFAULT] COLLATE [=] collation_name