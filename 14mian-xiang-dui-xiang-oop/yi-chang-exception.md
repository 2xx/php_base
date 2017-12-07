#### 异常处理

1\) 异常不完全等于错误. 它不属于那种因编码问题出现的错误. 而是在运行时, 因不一样的操作,不正常的数据等等,

​ 从而出现不正常的状况. 这叫异常.

2\) 在面向对象的编程中, 把 "不正常的状况" 归为一个类, 把每次出现的"不正常状况"当做一个对象.

3\) Exception 是 PHP 系统的异常处理类.

​**发生异常时,**

​**首先, 需要动态的创建一个异常处理对象**

```php
    $obj = new Exception('图片太黄了', '1024');  //  构造方法  错误信息, 错误号

    // 该对象可以获取一些信息
    $obj -> getMessage();   // 获取 异常信息
    $obj -> getCode();      // 获取 异常编号
    $obj -> getFile();      // 获取 异常所在的文件完整路径
    $obj -> getLine();      // 获取 异常出现的代码行号
```

**其次, 把这个异常处理对象抛出\( throw \), 交由特定代码去处理**

```php
    try{
           $a = 7;
         $b = 0;
           if ($b==0){    // 判断是否有异常情况
             throw new Exception('除数不能为0', 1234);  // 将创建的异常对象抛出
           }
           echo $a/$b,'<br>';    // 如果上面有异常抛出, 这里的代码就不会执行
    } catch(Exception $e) {
         echo $e->getMessage(),'<br>';
           $b = 1;
    }

    echo '我是下面的代码';
```

PDOException 是专门处理PDO错误的异常处理类. 

用PDO操作数据库发生错误时, 会自动将错误异常抛出.

```php
	try{
      
      $dsn = 'mysql:host=localhost;dbname=myshop;charset=utf8';
      $pdo = new PDO($dsn, 'root', '');   // 如果有错, 自动抛出异常
      
	} catch(PDOException $e) {    // 捕获异常
         // 处理异常
	}
```



