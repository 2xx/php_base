### 数据表

#### 1.查看所有表         SHOW TABLES

```
![](/assets/import4.png)
```

#### 2.创建表

```
        CREATE TABLE表名(
             字段名1字段类型 [列的完整性约束],
             字段名2…………
        )ENGINE=MYISAM DEFAULT CHARSET=utf8;
```

```
  ENGINE=指定表引擎

  MYISAM=引擎，快速存储。

  INNODB=带有事物回滚的引擎（高级课PDO会讲）

 ![](/assets/import3.png)
```

#### 3.修改表

##### 修改表名

```
  ALTER TABLE原表名RENAME新表名ALTER TABLE原表名RENAME新表名
```

##### 添加字段

```
  alter table 表名 add 字段名 字段属性;
```

##### ​       删除字段

```
  alter table 表名 drop 字段名;
```

##### ​       修改字段

```
  alter table 表名 modify 字段名 新属性;
​                      
  alter table 表名 change 字段原名 字段新名字 新属性;
```

##### 查看表的所有字段

```
  desc 表名;
```

##### ​ 修改表名

```
  alter table 旧表名 rename 新表名;
```

##### ​       修改自增起如值

```
  alter table 表名 auto_increment=1;
```

#### 4.删除表

```
DROP TABLE表名

DROP TABLE IF EXISTS表名
```

#### 4.1删除多个表

```
DROP TABLE表名1,表名2，……；
```

**注意：**

**       \[IF EXISTS\]如果存在**

**       \[IF NOT EXISTS \]如果不存在**

#### 5.查看表结构    **  DESC表名**

```
mysql> desc shop_cate;
+-------+------------------+------+-----+---------+----------------+
| Field | Type             | Null | Key | Default | Extra          |
+-------+------------------+------+-----+---------+----------------+
| cid   | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| cname | varchar(20)      | YES  |     | NULL    |                |
| pid   | int(10) unsigned | YES  |     | NULL    |                |
| path  | varchar(100)     | YES  |     | NULL    |                |
+-------+------------------+------+-----+---------+----------------+
4 rows in set (0.04 sec)
```

```
   Field字段名

   \| Type字段的类型以及对字段的约束是否是有符号的约束

   \| Null是否为空\|

   Key \|是否设置健

   Default默认值

  \| Extra额外的 -&gt;自增
```

MySQL数据库中的表类型一般常用两种：MyISAM和InnoDB

```
区别：MyISAM类型的数据文件有三个frm\(结构\)、MYD（数据）、MYI（索引）

      MyISAM类型中的表数据增 删 改速度快，不支持事务，没有InnoDB安全。



      InnoDB类型的数据文件只有一个 .frm

      InnoDB类型的表数据增 删 改速度没有MyISAM的快，但支持事务，相对安全。
```

### 数据备份与恢复

#### mysqldump 实现数据备份

​ **mysqldump -u root -p 数据库名 表1 表2 &gt; 导出文件名** 导出数据库中的指定的表

​ **mysqldump -u root -p 数据库名 &gt; 文件名** 导出整个库中的所有表 不包含库本身



#### 备份多个数据库

​ `DOS命令行`

​ **mysqldump -u root -p --databases 库名1 库名2 &gt; 导出文件名**

  


#### 备份所有数据库

​ `DOS命令行`

​ **mysqldump -u root -p --all-databases &gt; 导出文件名**

  


#### 还原数据库

​ `DOS命令行`

​ **mysql -u root -p 已存在的库名 &lt; 要导入的文件**

​ **mysql -u root -p &lt; 要导入的文件** \(该文件是以整库的形式导出的\)

​  


​ `mysql中`

​ **在选中某个数据库之后 source 数据库文件**



#### 导出数据库的结构

​ **mysqldump -u 用户名 -p -d 数据库名 &gt; 导出的文件名**

