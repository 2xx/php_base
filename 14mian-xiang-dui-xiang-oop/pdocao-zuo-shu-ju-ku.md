## PDO \( PHP Data Object \)

​ 市场上常见的数据库管理系统有很多, 在使用PDO之前, php连接操作mysql数据库时,有一套增删除改查的函数, 连接Oracle数据库时有另一套函数, 针对不同的数据库php要使用不同的操作函数, 这样使项目开发与扩展变得十分繁琐, PDO针对不同的数据库采用统一的操作接口\(同一套函数\), 从而可以提高项目开发效率.

通常 PDO 是默认开启的, 可以通过 phpinfo\(\) 查看系统是否开启了这个扩展![](/assets/2017-03-29_222650.png)**如果没有看到上面的字, 那么再去 php.ini 中看是否开启**![](/assets/2017-03-29_222837.png)

## 连接

DSN \( Data Source Name \) 数据源名

```php
    $dsn = 'mysql:host=localhost;dbname=xxoo;charset=utf8;port=3306';

    $pdo = new PDO( $dsn, 'root', '123456');   // 通过 $pdo 这个对象  操作数据库
```

#### $pdo -&gt; exec\( sql语句 \);

1\) 向数据库服务器 发送**insertdeleteupdate**类型的SQL语句.

2\) 返回 受影响行数.

#### $pdo -&gt; query\( sql语句 \);

1\) 向数据库服务器 发送**select**类型的SQL语句

2\) 返回`一个结果集对象`

#### $stmt -&gt; fetchAll\( PDO::FETCH\_CLASS \); 通过结果集对象获取所有数据

```php
    .... 连接

    $sql = 'select * from users limit 10';

    $stmt = $pdo -> query( $sql );  // 发送sql语句, 返回 结果集对象

    $users = $stmt -> fetchAll( PDO::FETCH_CLASS );  // 获取所有查询结果
                                                     // PDO::FETCH_CLASS  表示返回对象形式的结果
```

#### 判断SQL语句 语法错误

```php
    // 如果有语法错误, 就打印错误信息, 结束代码执行
    if ( $pdo -> errorCode() ) {
        die( $pdo->errorInfo()[2] );
    }

    /*
        $pdo -> errorCode()    没有错误 返回0     
                                 有错误 返回非0

        $pdo -> errorInfo()  返回一个数组, 数组中[2] 是错误信息                         
    */
```

### 判断SQL语句 执行结果

#### 受影响行数

$pdo -&gt; exec\( \) 的返回值

insert delete update 语句. 需要通过 受影响行数 来判断是否执行成功.



#### 返回记录数

select 语句. 需要通过 返回记录数 来判断有没有符合条件的记录.

$sql = "select \* from users where age&lt;20";

$stmt = $pdo -&gt; query\( $sql \);

$users = $stmt -&gt; fetchAll\( PDO::FETCH\_CLASS \); 如果没有符合条件的记录, 会返回空数组

**方法一:**count\( $users \); 返回结果是一个数组, 统计数组元素个数就可以

**方法二:**select count\(\*\) from users where 条件;





### 封装, 强调围绕着对象的操作编写代码



