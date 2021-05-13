SQLite version 3.35.5 2021-04-19 18:32:05
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
sqlite> .oepn c:\\dd\\mydb
Error: unknown command or invalid arguments:  "oepn". Enter ".help" for help
sqlite> .open 'c:\\dd\\mydb'
sqlite> .mode column
sqlite> .header on
sqlite> .import.open 'c:\\dd\\mydb'
Error: unknown command or invalid arguments:  "import.open". Enter ".help" for help
sqlite>    sqlite> .mode column
   ...>    sqlite> .header on
   ...> 

   ...>
   ...> ;
Error: near "sqlite": syntax error
sqlite> create table movie(tititle, director, actor, audience
   ...> );
Error: table movie already exists
sqlite> .schema
CREATE TABLE movie(title,director,actor,audience);
CREATE TABLE IF NOT EXISTS "movi;e"(
  "해운대" TEXT,
  "윤제균" TEXT,
  "설경구" TEXT,
  "1139 " TEXT
);
CREATE TABLE IF NOT EXISTS "movie;"(
  "해운대" TEXT,
  "윤제균" TEXT,
  "설경구" TEXT,
  "1139 " TEXT
);
sqlite> .import 'c:\\dd\\m.txt' movie
sqlite> select * from movie;
title  director  actor  audience
-----  --------  -----  --------
해운대    윤제균       설경구    1139
광해     추창민       이병헌    1232
국제시장   윤재균       황정민    1318
도둑들    최동훈       전지현    1302
변호인    양우석       송강호    1137
sqlite> insert into movie values(명량, 김한민,최민식,1761);
Error: no such column: 명량
sqlite> insert into movie values('명량', '김한민','최민식',1761);
sqlite> select * from movie;
title  director  actor  audience
-----  --------  -----  --------
해운대    윤제균       설경구    1139
광해     추창민       이병헌    1232
국제시장   윤재균       황정민    1318
도둑들    최동훈       전지현    1302
변호인    양우석       송강호    1137
명량     김한민       최민식    1761
sqlite> update movie set actor='김혜수' where actor='전지현';
sqlite> select * from movie;
title  director  actor  audience
-----  --------  -----  --------
해운대    윤제균       설경구    1139
광해     추창민       이병헌    1232
국제시장   윤재균       황정민    1318
도둑들    최동훈       김혜수    1302
변호인    양우석       송강호    1137
명량     김한민       최민식    1761
sqlite> delete from movie where title ='국제시장';
sqlite> select * from movie;
title  director  actor  audience
-----  --------  -----  --------
해운대    윤제균       설경구    1139
광해     추창민       이병헌    1232
도둑들    최동훈       김혜수    1302
변호인    양우석       송강호    1137
명량     김한민       최민식    1761
sqlite> select * from Man;
name  age
----  ---
김연아   32
손흥민   30
이강인   21
sqlite> select * from ovie order by audience desc
   ...> ;
Error: no such table: ovie
sqlite> select * from movie order by audience desc;
title  director  actor  audience
-----  --------  -----  --------
도둑들    최동훈       김혜수    1302
광해     추창민       이병헌    1232
해운대    윤제균       설경구    1139
변호인    양우석       송강호    1137
명량     김한민       최민식    1761
sqlite> select * from movie order by audience asc
   ...> ;
title  director  actor  audience
-----  --------  -----  --------
명량     김한민       최민식    1761
변호인    양우석       송강호    1137
해운대    윤제균       설경구    1139
광해     추창민       이병헌    1232
도둑들    최동훈       김혜수    1302
sqlite> insert into movie values('명량', '김한민','최민식','1761');
sqlite> select * from movie order by audience desc;
title  director  actor  audience
-----  --------  -----  --------
명량     김한민       최민식    1761
도둑들    최동훈       김혜수    1302
광해     추창민       이병헌    1232
해운대    윤제균       설경구    1139
변호인    양우석       송강호    1137
  
import sqlite3 as s

con = s.connect('c:\\dd\\mydb')
c=con.cursor()
c.execute('drop table if exists Man')
c.execute('create table Man(name,age)')
c.execute('insert into Man values("김연아",32)')
c.execute('insert into Man values("손흥민",30)')
c.execute('insert into Man values("이강인",21)')


c.execute('select * from Man')

con.commit()
c.close()
con.close()
mysql> create database mydb;
Query OK, 1 row affected (0.01 sec)

mysql> use mydb
Database changed

mysql> create table movie(title char(30), actor char(10), audience int);
Query OK, 0 rows affected (0.04 sec)

mysql> desc movie;
+----------+----------+------+-----+---------+-------+
| Field    | Type     | Null | Key | Default | Extra |
+----------+----------+------+-----+---------+-------+
| title    | char(30) | YES  |     | NULL    |       |
| actor    | char(10) | YES  |     | NULL    |       |
| audience | int      | YES  |     | NULL    |       |
+----------+----------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> insert into movie values('해운대', '설경구', 1139);
Query OK, 1 row affected (0.01 sec)

mysql> insert into movie values('광해', '이병헌', 1139);
Query OK, 1 row affected (0.01 sec)

mysql> insert into movie values('도둑들', '전지현', 1302);
Query OK, 1 row affected (0.01 sec)

###
mysql> update movie set audience = 1232 where title = '광해';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> update movie set actor = '전지현' where audience = 1302;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0
###

mysql> select * from movie;
+--------+--------+----------+
| title  | actor  | audience |
+--------+--------+----------+
| 해운대 | 설경구 |     1139 |
| 광해   | 이병헌 |     1232 |
| 도둑들 | 전지현 |     1302 |
+--------+--------+----------+
3 rows in set (0.00 sec)





mysql> use mydb;
Database changed

mysql> select * from Man;
+--------+------+
| name   | age  |
+--------+------+
| 김연아 |   32 |
| 손흥민 |   30 |
| 이강인 |   21 |
+--------+------+
3 rows in set (0.00 sec)

