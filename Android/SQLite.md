## SQLite:（操作和检索关系数据库的标准语言）
1. MYSQL命令语句：
  * show databases; （查看当前实例的数据库）
  * create database if not exists 数据库名; （创建新的数据库）
  * drop database 数据库名; （删除数据库）
  * use 数据库名; （进入数据库）
    * show tables;  （进入数据库后查询数据库包含多少数据表）
  * desc 表名;  （查看指定数据表的表结构）
2. SQLite数据库数据类型：
        Integer  varchar(10)  float  double  char(10)  text
3. 常见数据库对象：table、constraint（约束）、view、index、function、procedure、trigger
4. 标准SQL语句类型：
  * 查询语句：主要由select关键字完成。
  * DML（数据操作语言）语句：主要由insert、update和delete三个关键字完成。
  * DDL（数据定义语言）语句：主要由create、alter
  、drop、`truncate`（相当于先删除指定数据表，然后再重建该数据表）四个关键字完成。
  * DCL（数据控制语言）语句：主要由grant和revoke两个关键字完成。
  * 事务控制语句：主要由commit、rollback和savepoint三个关键字完成。
5. DDL语句：操作数据库对象的语句，包括创建（create）、删除（drop）和修改（alter）数据库对象。

  * 创建表的语法：
      * 常见建表语句：
            create table [模式名.]表名(列名 列类型 [defult 默认值]，列名 列类型 [defult 默认值]......);

            create table test(
              # 整型数据
              test_id int,
              # 小数点数
              test_price decimal,
              # 普通长度文本，使用defult指定默认值
              test_name varchar(255) defult 'xxx',
              # 大文本类型
              test_desc text,
              # 图片
              test_img blob,
              # 日期时间类型
              test_date datetime
              );

            create table person(m_id int primary key,name varchar(20),age int not null);
      * 子查询建表语句：
            create table [模式名.]表名
  * 修改表结构的语法：
          alter table 表名 add(列名 数据类型 [default 默认值]);
          alter table 表名 modify 列名 数据类型;  （修改列定义）
          alter tabel 表名 drop 列名;
          alter tabel 表名 rename to 新表名;   （重命名数据表名）
          alter tabel 表名 change 旧列名 新列名 数据类型;

          alter table person add hehe_id int;

          alter table person
          add(
            aaa varchar(255) default 'xxx',
            bbb varchar(255)
          );
  * 删除表的语句：
          drop table 表名;
          drop table person;
  * truncate表：删除表中的全部结构，但保留表结构。
          truncate 表名;
6. DML语句：
  * 插入数据：
          insert into 表名(列名,列名...) values(值1,值2...);
          insert into person(m_id,age) values(1,20);
          insert into person values(2,"z5",30);
  * 修改数据：
          update 表名 set 列名=新值 where 修改条件
          # 若没有where语句，则修改表中所有数据
          update person set name="ls",age=20 where m_id=1;
  * 删除数据：
          delete from 表名 where 删除条件;
          # 若没有where语句，则删除表中所有数据
          delete from person where m_id=2;
7. 查询语句：
  * 查询语句：
          select 列名 from 表名 where 查询条件 group by 列名 having 筛选条件 order by 排序字段;
          select * from person;  （* 代表所有）
          select m_id,name from person;
          select * from person where m_id=1;
          select * from person where m_id=1 and age>18;
          select * from person where name like "%小%";
          select * from person where age between 10 and 20;

          
### SQLite中关于Cursor类：
1. Cursor是每行的集合，使用moveToFirst()定位第一行，Cursor是一个随机的数据源，所有数据都通过下标取得。
2. 关于Cursor的重要方法：
  * close():关闭游标，释放资源。
  * copyStringToBuffer(int columnIndex, CharArrayBuffer buffer)：在缓冲区中检索请求列的文本，将其存储。
  * getColumnCount()：返回所有列的总数
  * getColumnIndex(String columnName)：返回指定列的名称，若不存在，返回-1
  * getColumnNames()
返回一个字符串数组的列名
  * getColumnName(int columnIndex)
从给定的索引返回列名
  * getCount()
返回Cursor 中的行数
  * moveToFirst()
移动光标到第一行
  * moveToLast()
移动光标到最后一行
  * moveToPosition(int position)
移动光标到一个绝对的位置
  * moveToPrevious()
移动光标到上一行
  * isBeforeFirst()
返回游标是否指向之前第一行的位置
  * isAfterLast()
返回游标是否指向第最后一行的位置
  * isClosed()
如果返回 true 即表示该游戏标己关闭
3. 在Android中查询数据是通过Cursor类实现的，当我们使用SQLiteDatabase.query()方法时，就会得到Cursor对象，Cursor所指向的就是每一条数据。
