# MySQL 5.6 설치 및 세팅
### DBMS
Data Base Management System (DB Server + Client tool) 

### 설치 및 세팅
1. 다운로드 : 커뮤니티 GPL 버전으로 다운로드

2. 압축을 풀어서 java_project에 위치

3. 시작은 C:\java_project\mysql-5.6.47-winx64\bin\mysqld.exe로 한다.
프로세스 리스트에서 mysqld.exe가 올라와 있는지 확인한다. 목록에 보인다면 성공적으로 실행된 것이다.

4. 관리자 root 로그인
```
cmd 창
C:\java_project\mysql-5.6.47-winx64\bin>mysql -uroot -p mysql
```
```
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.6.47 MySQL Community Server (GPL)

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```
> mysql -u유저명 -p암호 사용DB

### 명령어
1. DB 목록 보기 : show databases ;
```        
mysql> show databases ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
```
2. 사용할 DB 선택 : use DB명
```
mysql> use test
Database changed
mysql> use mysql
Database changed
```

> DB server > DB > table > 행(레코드) 집합 > 열(컬럼) 집합 > 도메인(데이터)

3. 테이블 목록 보기 : show tables ;
```
mysql> show tables ;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| event                     |
| func                      |
| general_log               |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| innodb_index_stats        |
| innodb_table_stats        |
| ndb_binlog_index          |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| servers                   |
| slave_master_info         |
| slave_relay_log_info      |
| slave_worker_info         |
| slow_log                  |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
```

4. 유저 정보 확인 : select host,user,password from user ;
```
mysql> select host,user,password from user ;
+-----------+------+----------+
| host      | user | password |
+-----------+------+----------+
| localhost | root |          |
| 127.0.0.1 | root |          |
| ::1       | root |          |
| localhost |      |          |
+-----------+------+----------+
```
localhost와 127.0.0.1은 같다. root 권한 없이 익명으로 암호 없이 들어올 수도 있음.

5. root 암호 설정하기 : update user set password=password('1234') where user='root' ;
```
mysql> update user set password=password('1234') where user='root' ;
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0
```

6. 확인하기 : select host,user,password from user ;
```
mysql> select host,user,password from user ;
+-----------+------+-------------------------------------------+
| host      | user | password                                  |
+-----------+------+-------------------------------------------+
| localhost | root | *A4B6157319038724E3560894F7F932C8886EBFCF |
| 127.0.0.1 | root | *A4B6157319038724E3560894F7F932C8886EBFCF |
| ::1       | root | *A4B6157319038724E3560894F7F932C8886EBFCF |
| localhost |      |                                           |
+-----------+------+-------------------------------------------+
```

7. 일반 계정 생성하기 :     
+ 로컬 접근  
grant all privileges on javadb.* to javauser@localhost
identified by '1234' ;      
+ 리모트접근     
grant all privileges on javadb.* to javauser@'%'
identified by '1234' ;

8. 확인하기 : 추가된 계정과 암호를 확인
```
+-----------+----------+-------------------------------------------+
| host      | user     | password                                  |
+-----------+----------+-------------------------------------------+
| localhost | root     | *A4B6157319038724E3560894F7F932C8886EBFCF |
| 127.0.0.1 | root     | *A4B6157319038724E3560894F7F932C8886EBFCF |
| ::1       | root     | *A4B6157319038724E3560894F7F932C8886EBFCF |
| localhost |          |                                           |
| localhost | javauser | *A4B6157319038724E3560894F7F932C8886EBFCF |
| %         | javauser | *A4B6157319038724E3560894F7F932C8886EBFCF |
+-----------+----------+-------------------------------------------+
```

9. DB 생성 : create database javadb ;
```
mysql> create database javadb ;
Query OK, 1 row affected (0.01 sec)
mysql> show databases ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| javadb             |
| mysql              |
| performance_schema |
| test               |
+--------------------+
5 rows in set (0.00 sec)
```

10. 바로 적용하기 : flush privileges ;
```
mysql> flush privileges ;
Query OK, 0 rows affected (0.00 sec)
```

11. 나가기 : quit
```
mysql> quit
Bye

C:\java_project\mysql-5.6.47-winx64\bin>
```

12. 생성한 DB 접근
```
C:\java_project\mysql-5.6.47-winx64\bin>mysql -ujavauser -p1234 javadb

Warning: Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.6.47 MySQL Community Server (GPL)

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```