### DML语句

* #### 增

  * 方式1：

```
     INSERT INTO表名(字段名1，字段名2……) VALUES（值1，……）;
```

注意：

       如果字段名两边要加引号，加的是反引号，

       如果在之中加入引号，加入单引号或双引号或不加引号。

       对于值什么时候加引号，什么时候不加引号？

       在当前字段的类型为字符串形式的时候，必须加引号，其余情况可以不加，也可以加。

       字段名可以跟数据表中的顺序不对应，但是值与字段的名必须要一一对应。

* #### 增

  * 方式2

```
      INSERT INTO表名VALUES(字段1，字段2……)；
```

注意：

        所有的值必须依照表中的顺序一一对应赋值，不写值的可以写null，但是不能省略

* #### 增

  * 方式3：批量添加

  ```
  INSERT INTO 表名（字段名1，字段名2……） VALUES(值1，值2，……)，（值1，……），……；
  ```

  * 方式4：

  ```
  INSERT INTO表名VALUES(值1，值2……)，（值1，值2）……；
  ```

注意：

       sql语句的特点：相同的地方用（,）隔开，不同的地方用空格隔开

* #### 改

```
UPDATE表名SET字段名=新值，……[更新条件]
```

   更改条件

       Where id=值（id&lt;=值）；

       Where字段Is null

       Where字段Is not null

* #### 删

```
DELETE FROM表名[删除条件];
```

注意：

       在删除某个数据的时候，一定要记住必须给删除条件。

       如果不给删除条件——》孤独终老

     删除条件

       删除指定集合：in

       Where字段 in\(需要的值用逗号分隔开\)

    删除范围：Between

          Where字段between值1 and值2（在什么什么之间）

          在指定的范围内包含值1和值2；

          WHERE id &lt;A值and id &gt;b值

          删除A到b之间的数据

          如果要删除id=1和id=13;

         条件：where id=1 or id=13

    注意：该条件不能给and如果给and将不会被删除

              因为id=1的时候不可能在等于13，所以 where id=1 and id=13是错误的。

     删除 name=‘xiaoniangzi’and sex=0;这种条件可以使用and因为描述的是一个人的信息。

* ### DQL语句
* 方法1
  *  SELECT \* FROM表名
  *  \*：匹配所有字段
* 方法2
  * SELECT字段1，字段2……FROM表名
  * 统计当前表中有多少条数据
  * SELECT COUNT\(字段\) FROM表名
* 查询条件
  *  Not in表示不在这里面
  *  WHERE字段名 NOT IN（值1，值2）
  * 查询到的结果中没有值1，值2

* In查询指定的集合
  *  Where字段in \(值1，值2……\)在这里的都会查询出来

* BETWEEN在指定的范围
  *  WHERE字段BETWEEN值1 and值2

* Like模式匹配
  * WHERE字段like‘%值%’
* 只要在字段中有这个值的出现就会查询出来
  * 例子：SELECT \* FROM user WHERE name like '%j%';

*  WHERE字段 like ‘%值’;
  * 在这个字段中以这个值结尾的内容查询出来
  * 例子：SELECT \* FROM user WHERE name like '%j';
* WHERE字段like ‘值%’;
  * 在这个字段中以这个值开头的内容查询出来
  * 例子：SELECT \* FROM user WHERE name like 'j%';

* Limit限制查询的数量

* ```
  1.SELECT * FROM表名limit查询数量
  2.SELECT * FROM表名LIMIT跳过几条，查询几条
  ```

* 排序查询
  * 一类升序\(asc\)
  * 一类是降序（desc）
  * ORDER BY字段是升序还是降序
  * 按照年龄降序排序

  ```
  SELECT * FROM user ORDER BY age desc;
  ```

  * 按照年龄升序排序

  ```
   SELECT * FROM user ORDER BY age asc;
  ```

* 按照年龄升序排序，年龄相同时按照性别降序排序，性别相同时按照ID升序排序
  * ```
    mysql> SELECT * FROM user ORDER BY age ASC,sex DESC,id ASC;

    +----+--------------+-----+------+
    | id | name | sex | age |
    +----+--------------+-----+------+
    | 11 | zcy | 5 | 18 |
    | 5 | xiaoniangzi | 2 | 18 |
    | 7 | panjinlian | 2 | 18 |
    | 8 | yaoshichen | 2 | 18 |
    | 9 | wcb | 2 | 18 |
    | 10 | zzl | 2 | 18 |
    | 12 | xitao | 2 | 18 |
    | 13 | zy | 2 | 18 |
    | 6 | lijinsi | 2 | 19 |
    | 1 | xuerfei | 2 | 30 |
    | 2 | liuchunchun | 2 | 30 |
    | 3 | tangxiaodong | 2 | 30 |
    | 4 | daguanren | 2 | 30 |
    | 14 | xuxiaona | 1 | 100 |
    +----+--------------+-----+------+
    ```





