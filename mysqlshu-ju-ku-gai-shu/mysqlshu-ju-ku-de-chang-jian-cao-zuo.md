* ### MySQL数据库的连接与关闭

  * ### 连接数据库

    * mysql -h 服务器主机地址 -u 用户名 -p 用户密码

      * -h  指定所连接数据库的服务器位置。【IP地址或者服务器域名】

      * -u  连接数据库服务器使用的域名。【root 超级管理员】

      * -p  连接数据库服务器使用的密码。
  * ### ![](/assets/连接数据库.png)
  * ### 退出数据库

    * \q

    * exit;

    * quit;
* ### MySQL数据库用户权限

  ##### --授权一个用户（zhangsan）密码123，可以对所有的库，所有的表做所有操作。

  mysql&gt;grant all on \*.\* to zhangsan@'%' identified by '123';

  Query OK, 0 rows affected \(0.17 sec\)

  ##### --刷新生效，否则就要重启MySQL服务才可以。

  mysql&gt; flush privileges;

  Query OK, 0 rows affected \(0.00 sec\)

  ##### --浏览当前MySQL用户信息

  **mysql&gt; select user,host,password from mysql.user;**

  +----------+-----------------+-------------------------------------------+

  \| user     \| host            \| password                                  \|

  +----------+-----------------+-------------------------------------------+

  \| root     \| localhost       \| \*23AE809DDACAF96AF0FD78ED04B6A265E05AA257 \|

  \| root     \| 127.0.0.1       \|                                           \|

  \|          \| localhost       \|                                           \|

  \| zhangsan \| %               \| \*23AE809DDACAF96AF0FD78ED04B6A265E05AA257 \|

  \| admin    \| 192.168.112.132 \| \*23AE809DDACAF96AF0FD78ED04B6A265E05AA257 \|

  +----------+-----------------+-------------------------------------------+

  5 rows in set \(0.00 sec\)

  ##### -- 移除一些权限

  ##### -- revoke:只删除了用户权限，但没有删除这个用户

  mysql&gt; revoke insert,delete on \*.\* from admin@192.168.112.132 identified by'123';

  ### -- 查看指定用户的权限信息

  mysql&gt; show grants for xbb@localhost;

  +------------------------------------------------------------------------------------------------------------+

  \| Grants for xbb@localhost                                                                                   \|

  +------------------------------------------------------------------------------------------------------------+

  \| GRANT USAGE ON \*.\* TO 'xbb'@'localhost' IDENTIFIED BY PASSWORD '\*23AE809DDACAF96AF0FD78ED04B6A265E05AA257' \|

  +------------------------------------------------------------------------------------------------------------+

  ### --drop user:删除了整个用户及其权限（包括数据字典中的数据）

  mysql&gt; drop user 'xbb'@'localhost';

  Query OK, 0 rows affected \(0.00 sec\)

  mysql&gt; select user,host from mysql.user;

  +------------------+-----------+

  \| user             \| host      \|

  +------------------+-----------+

  \| root             \| 127.0.0.1 \|

  \| debian-sys-maint \| localhost \|

  \| root             \| localhost \|

  \| root             \| wangxg    \|

  +------------------+-----------+

  4 rows in set \(0.00 sec\)

* ### 创建数据库

  * 查看库: **show databases;**

  * ​创建库: **create database 库名 default charset=utf8;**

  * ​删除库: **drop database 库名;**

  * 使用库: use 库名
* ### 创建数据表

  * 查看表: **show tables;**

  * ​创建表:

    ```
       **create table 表名\(
            **字段名1 类型,字段名2 类型**
       **\)engine=innodb default charset=utf8;**
    ```

  ```
   ​      创建表: 如果表不存在,则创建, 如果存在就不执行这条命令

   ​       **create table if not exists 表名\(**

               ​ **字段1 类型,**

               ​ **字段2 类型**

    ​     **\)engine=innodb default charset=utf8;**
  ```

  * ​ 删除表: **drop table 表名;**

  * ​ 表结构: **desc 表名;**
* ### 数据表内容的简单管理

  * 插入 **insert into 表名\(字段1,字段2,字段3\) values\(值1,值2,值3\);**

    ​ **insert into 表名\(字段1,字段2,字段3\) values\(a值1,a值2,a值3\),\(b值1,b值2,b值3\);**

    ```
     insert into 表名 values\(null,值1，值2，值3\);
    ```

  * 查询 **select \* from 表名;**

    ```
    select 字段1,字段2,字段3 from 表名;
    ```

  ​         **select \* from 表名 where 字段=某个值;**

  * ​ 修改 **update 表名 set 字段=某个值 where 条件;**

    ​ **update 表名 set 字段1=值1,字段2=值2 where 条件;**

  * 删除 **delete from 表名 where 字段=某个值;**



