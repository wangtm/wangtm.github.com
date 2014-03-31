---

layout : post

category : 数据库

tags : [oracle   oracle常见问题]

title : oracle常见问题及解决办法

---

根据公司的需要，在学习oracle，像我这样的小白来说，没接触到oracle，不知道怎么玩，
在安装和使用中出现了很多小问题，在网上也找到了很多解决办法，我这里把我在使用的过
程中出现的问题记录下来，方便以后查找，当然网上也有很多。当然有些是在网上找的，自己没有亲自测试和碰到过，这里做收藏

1. Oracle安装完成后的初始口令? 
　　internal/oracle 
　　sys/change_on_install 
　　system/manager 
　　scott/tiger 
　　sysman/oem_temp

2. ORACLE9IAS WEB CACHE的初始默认用户和密码？ 
　 administrator/administrator

3. oracle 8.0.5怎么创建数据库? 
　 用orainst。如果有motif界面，可以用orainst /m

4. oracle 8.1.7怎么创建数据库? 
　 dbassist

5. oracle 9i 怎么创建数据库? 
　 dbca

6. oracle中的裸设备指的是什幺? 
　裸设备就是绕过文件系统直接访问的储存空间

7. oracle如何区分 64-bit/32bit 版本？？？ 
$ sqlplus '/ AS SYSDBA' 
SQL*Plus: Release 9.0.1.0.0 - Production on Mon Jul 14 17:01:09 2003 
(c) Copyright 2001 Oracle Corporation. All rights reserved. 
Connected to: 
Oracle9i Enterprise Edition Release 9.0.1.0.0 - Production 
With the Partitioning option 
JServer Release 9.0.1.0.0 - Production 
SQL> select * from v$version; 
BANNER 
---------------------------------------------------------------- 
Oracle9i Enterprise Edition Release 9.0.1.0.0 - Production 
PL/SQL Release 9.0.1.0.0 - Production 
CORE 9.0.1.0.0 Production 
TNS for Solaris: Version 9.0.1.0.0 - Production 
NLSRTL Version 9.0.1.0.0 - Production 
SQL>

8. SVRMGR什幺意思？ 
svrmgrl，Server Manager.

9i下没有，已经改为用SQLPLUS了 
sqlplus /nolog 
变为归档日志型的

9. 请问如何分辨某个用户是从哪台机器登陆ORACLE的? 
SELECT machine , terminal FROM V$SESSION;

10. 用什幺语句查询字段呢？ 
desc table_name 可以查询表的结构 
select field_name,... from ... 可以查询字段的值 
select * from all_tables where table_name like '%' 
select * from all_tab_columns where table_name='??'

11. 怎样得到触发器、过程、函数的创建脚本？ 
desc user_source 
user_triggers

12. 怎样计算一个表占用的空间的大小？ 
select owner,table_name, 
NUM_ROWS, 
BLOCKS*AAA/1024/1024 "Size M", 
EMPTY_BLOCKS, 
LAST_ANALYZED 
from dba_tables 
where table_name='XXX';

Here: AAA is the value of db_block_size ; 
XXX is the table name you want to check

13. 如何查看最大会话数？ 
SELECT * FROM V$PARAMETER WHERE NAME LIKE 'proc%'; 
SQL> 
SQL> show parameter processes

NAME TYPE VALUE 
------------------------------------ ------- ------------------------------ 
aq_tm_processes integer 1 
db_writer_processes integer 1 
job_queue_processes integer 4 
log_archive_max_processes integer 1 
processes integer 200

这里为200个用户。

select * from v$license; 
其中sessions_highwater纪录曾经到达的最大会话数

14. 如何查看系统被锁的事务时间？ 
select * from v$locked_object ;

15. 如何以archivelog的方式运行oracle。
init.ora 
log_archive_start = true 
RESTART DATABASE

16. 怎么获取有哪些用户在使用数据库 
select username from v$session;

17. 数据表中的字段最大数是多少? 
表或视图中的最大列数为 1000

18. 怎样查得数据库的SID ? 
select name from v$database; 
也可以直接查看 init.ora文件

19. 如何在Oracle服务器上通过SQLPLUS查看本机IP地址 ? 
select sys_context('userenv','ip_address') from dual; 
如果是登陆本机数据库，只能返回127.0.0.1，呵呵

20. unix 下怎么调整数据库的时间？ 
su -root 
date -u 08010000

21. 在ORACLE TABLE中如何抓取MEMO类型字段为空的资料记录? 
select remark from oms_flowrec where trim(' ' from remark) is not null ;

22. 如何用BBB表的资料去更新AAA表的资料(有关联的字段) 
UPDATE AAA SET BNS_SNM=(SELECT BNS_SNM FROM BBB WHERE AAA.DPT_NO=BBB.DPT_NO) WHERE BBB.DPT_NO IS NOT NULL;

23. P4计算机安装方法 
将SYMCJIT.DLL改为SYSMCJIT.OLD

24. 何查询SERVER是不是OPS? 
　 SELECT *　FROM V$OPTION; 
　 如果PARALLEL SERVER=TRUE则有OPS能

25. 何查询每个用户的权限? 
　　SELECT *　FROM DBA_SYS_PRIVS;

26. 如何将表移动表空间? 
　ALTER TABLE TABLE_NAME MOVE TABLESPACE_NAME;

27. 如何将索引移动表空间? 
　 ALTER INDEX INDEX_NAME REBUILD TABLESPACE TABLESPACE_NAME;

28. 在LINUX,UNIX下如何激活DBA STUDIO? 
　　OEMAPP　DBASTUDIO

29. 查询锁的状况的对象有? 
　　V$LOCK,　V$LOCKED_OBJECT,　V$SESSION,　V$SQLAREA,　V$PROCESS ; 
　　查询锁的表的方法: 
SELECT S.SID SESSION_ID, S.USERNAME, DECODE(LMODE, 0, 'None', 1, 'Null', 2, 'Row-S (SS)', 3, 'Row-X (SX)', 4, 'Share', 5, 'S/Row-X (SSX)', 6, 'Exclusive', TO_CHAR(LMODE)) MODE_HELD, DECODE(REQUEST, 0, 'None', 1, 'Null', 2, 'Row-S (SS)', 3, 'Row-X (SX)', 4, 'Share', 5, 'S/Row-X (SSX)', 6, 'Exclusive', TO_CHAR(REQUEST)) MODE_REQUESTED, O.OWNER||'.'||O.OBJECT_NAME||' ('||O.OBJECT_TYPE||')', S.TYPE LOCK_TYPE, L.ID1 LOCK_ID1, L.ID2 LOCK_ID2 FROM V$LOCK L, SYS.DBA_OBJECTS O, V$SESSION S WHERE L.SID = S.SID AND L.ID1 = O.OBJECT_ID ;

30. 如何解锁? 
　　ALTER SYSTEM KILL SESSION　‘SID,SERIR#’;

31. SQLPLUS下如何修改编辑器?

DEFINE _EDITOR="<编辑器的完整路经>"　-- 必须加上双引号 
来定义新的编辑器，也可以把这个写在$ORACLE_HOME/sqlplus/admin/glogin.sql里面使它永久有效。

32. ORACLE产生随机函数是? 
　　DBMS_RANDOM.RANDOM

33. LINUX下查询磁盘竞争状况命令? 
　　Sar　-d

33. LINUX下查询CPU竞争状况命令? 
　　sar　 -r

34. 查询当前用户对象? 
　　SELECT *　FROM USER_OBJECTS;

　　SELECT *　FROM DBA_SEGMENTS;

35. 如何获取错误信息? 
　 SELECT *　FROM　USER_ERRORS;

36. 如何获取链接状况? 
　 SELECT * FROM DBA_DB_LINKS;

37. 查看数据库字符状况? 
　　SELECT *　FROM NLS_DATABASE_PARAMETERS; 
　　SELECT *　FROM V$NLS_PARAMETERS;

38. 查询表空间信息?

SELECT *　FROM　DBA_DATA_FILES;

39. ORACLE的INTERAL用户要口令? 
　 修改 SQLNET.ORA 
　 SQLNET.AUTHENTICATION_SERVICES=(NTS)

40. 出现JAVA.EXE的解决办法? 
　 一般是将ORACLEORAHOMEXIHTTPSERVER改成手工激活可以的 
　 X是8或9

41. 如何给表、列加注释？ 
SQL>comment on table 表 is '表注释'; 
注释已创建。 
SQL>comment on column 表.列 is '列注释'; 
注释已创建。 
SQL> select * from user_tab_comments where comments is not null;

42. 如何查看各个表空间占用磁盘情况？ 
SQL> col tablespace format a20 
SQL> select b.file_id 文件ID号, b.tablespace_name 表空间名, 
b.bytes 
字节数, 
(b.bytes-sum(nvl(a.bytes,0)))
已使用, 
sum(nvl(a.bytes,0))　 
剩余空间, 
sum(nvl(a.bytes,0))/(b.bytes)*100 剩余百分比 
from dba_free_space a,dba_data_files b 
where a.file_id=b.file_id 
group by b.tablespace_name,b.file_id,b.bytes 
order by b.file_id

43. 如把ORACLE设置为MTS或专用模式？ 
#dispatchers="(PROTOCOL=TCP) (SERVICE=SIDXDB)" 
加上就是MTS，注释就是专用模式，SID是指你的实例名。

44. 如何才能得知系统当前的SCN号 ? 
select max(ktuxescnw * power(2, 32) + ktuxescnb) from x$ktuxe;

45. 请问如何在ORACLE中取毫秒? 
9i之前不支持,9i开始有timestamp. 
9i可以用select systimestamp from dual;

46. 如何在字符串里加回车？ 
　　select 'Welcome to visit'||chr(10)||'www.CSDN.NET' from dual ;

47. 中文是如何排序的？ 
　　Oracle9i之前，中文是按照二进制编码进行排序的。 
　　在oracle9i中新增了按照拼音、部首、笔画排序功能。设置NLS_SORT值 
　　SCHINESE_RADICAL_M 按照部首（第一顺序）、笔划（第二顺序）排序 
　　SCHINESE_STROKE_M 按照笔划（第一顺序）、部首（第二顺序）排序 
　　SCHINESE_PINYIN_M 按照拼音排序

48.　Oracle8i中对象名可以用中文吗？ 
　　可以

49. 如何改变WIN中SQL*Plus启动选项？ 
SQL*PLUS自身的选项设置我们可以在$ORACLE_HOME/sqlplus/admin/glogin.sql中设置。

50. 怎样修改oracel数据库的默认日期? 
　 alter session set nls_date_format='yyyymmddhh24miss'; 
　 OR 
　 可以在init.ora中加上一行 
nls_date_format='yyyymmddhh24miss'

51. 如何将小表放入keep池中? 
　 alter table xxx storage(buffer_pool keep);

52. 如何检查是否安装了某个patch? 
　　check that　oraInventory

53. 如何使select语句使查询结果自动生成序号? 
select rownum,COL from table;

54. 如何知道数据裤中某个表所在的tablespace? 
select tablespace_name from user_tables where table_name='TEST'; 
select * from user_tables中有个字段TABLESPACE_NAME，（oracle）; 
select * from dba_segments where …;

55. 怎么可以快速做一个和原表一样的备份表? 
　　create table new_table as (select * from old_table);

55. 怎么在sqlplus下修改procedure? 
　select line,trim(text) t from user_source where name =’A’ order by line;

56. 怎样解除PROCEDURE被意外锁定? 
　 alter system kill session ,把那个session给杀掉，不过你要先查出她的session id

or 
　 把该过程重新改个名字就可以了。

57. SQL Reference是个什幺东西？ 
　 是一本sql的使用手册，包括语法、函数等等，oracle官方网站的文档中心有下载.

58. 如何查看数据库的状态? 
　 unix下 
ps -ef | grep ora 
windows下 
看服务是否起来 
是否可以连上数据库

59. 请问如何修改一张表的主键?

alter table aaa 
drop constraint aaa_key ; 
alter table aaa 
add constraint aaa_key primary key(a1,b1) ;

60. 改变数据文件的大小? 
用 ALTER DATABASE .... DATAFILE .... ; 
手工改变数据文件的大小，对于原来的 数据文件有没有损害。

61. 怎样查看ORACLE中有哪些程序在运行之中？ 
　 查看v$sessions表

62. 怎么可以看到数据库有多少个tablespace? 
select　*　 from dba_tablespaces;

63. 如何修改oracle数据库的用户连接数？ 
修改initSID.ora，将process加大，重启数据库.

64. 如何查出一条记录的最后更新时间? 
　可以用logminer 察看

65. 如何在PL/SQL中读写文件？ 
UTL_FILE包允许用户通过PL/SQL读写操作系统文件。

66. 怎样把“&”放入一条记录中？ 
insert into a values (translate ('at{&}t','at{}','at'));

67. EXP　如何加ＱＵＥＲＹ参数？ 
EXP USER/PASS FILE=A.DMP TABLES(BSEMPMS) 
QUERY='"WHERE EMP_NO=\'S09394\'\" ﹔

68. 关于oracle8i支持简体和繁体的字符集问题？ 
　 ZHS16GBK可以支

69. Data Guard是什幺软件？ 
就是Standby的换代产品

70. 如何创建SPFILE?

SQL> connect / as sysdba 
SQL> select * from v$version; 
SQL> create pfile from spfile; 
SQL> CREATE SPFILE FROM PFILE='E:\ora9i\admin\eygle\pfile\init.ora';

文件已创建。 
SQL> CREATE SPFILE='E:\ora9i\database\SPFILEEYGLE.ORA' FROM PFILE='E:\ora9i\admin\eygle\pfile\init.ora'; 
文件已创建。

71. 内核参数的应用? 
shmmax 
　　含义：这个设置并不决定究竟Oracle数据库或者操作系统使用多少物理内存，只决定了最多可以使用的内存数目。这个设置也不影响操作系统的内核资源。 
　　设置方法：0.5*物理内存 
　　例子：Set shmsys:shminfo_shmmax=10485760 
　　shmmin 
　　含义：共享内存的最小大小。 
　　设置方法：一般都设置成为1。 
　　例子：Set shmsys:shminfo_shmmin=1： 
　　shmmni 
　　含义：系统中共享内存段的最大个数。 
　　例子：Set shmsys:shminfo_shmmni=100 
　　shmseg 
　　含义：每个用户进程可以使用的最多的共享内存段的数目。 
　　例子：Set shmsys:shminfo_shmseg=20： 
　　semmni 
　　含义：系统中semaphore identifierer的最大个数。 
　　设置方法：把这个变量的值设置为这个系统上的所有Oracle的实例的init.ora中的最大的那个processes的那个值加10。 
　　例子：Set semsys:seminfo_semmni=100 
　　semmns 
　　含义：系统中emaphores的最大个数。 
　　设置方法：这个值可以通过以下方式计算得到：各个Oracle实例的initSID.ora里边的processes的值的总和（除去最大的Processes参数）＋最大的那个Processes×2＋10×Oracle实例的个数。 
　　例子：Set semsys:seminfo_semmns=200 
　　semmsl: 
　　含义：一个set中semaphore的最大个数。 
　　设置方法：设置成为10＋所有Oracle实例的InitSID.ora中最大的Processes的值。 
　　例子：Set semsys:seminfo_semmsl=-200

72. 怎样查看哪些用户拥有SYSDBA、SYSOPER权限？ 
SQL>conn sys/change_on_install 
SQL>select * from V_$PWFILE_USERS;

73. 如何单独备份一个或多个表？ 
exp 用户/密码 tables=(表1,…,表2)

74. 如何单独备份一个或多个用户？ 
　exp system/manager owner=(用户1,用户2,…,用户n) file=导出文件

75. 如何对CLOB字段进行全文检索？ 
SELECT * FROM A WHERE dbms_lob.instr(a.a,'K',1,1)>0;

76. 如何显示当前连接用户? 
　 SHOW　USER

77. 如何查看数据文件放置的路径 ? 
col file_name format a50 
SQL> select tablespace_name,file_id,bytes/1024/1024,file_name from dba_data_files order by file_id;
