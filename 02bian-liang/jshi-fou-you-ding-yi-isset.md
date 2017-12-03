### 判断变量是否有定义   isset\( 变量 \)

isset\( 变量 \)

返回一个结果，true 表示变量有定义  false 表示变量未定义

##### **变量未定义的情况：**

1）变量没有存储任何内容，或者变量名都没写过

2）变量存储的是 null

3）变量先有赋值，之后变量被销毁了

```php
<?php
    var_dump( isset($a) );  // false   变量没有写过
    
    $b;
    var_dump( isset($b) );  // false   变量没有赋值
    
    $c = null;
    var_dump( isset($c) );  // false   变量存储的是null

    $d = 7;
    unset( $d );
    var_dump( isset($d) );  // false   变量已经被销毁了
    
?>
```



