#### 实际代码中的变量与字符串

```php
<?php

    $p = 'abc.jpg';

    //  显示一张图片
    echo "<img src='./images/{$p}' />";


?>

<!--  在html代码中嵌入php代码，需要注意，代码所有的文件必须是php类型的文件    -->
<img src="./images/<?php echo $p; ?>" />
```

#### . 在php中被称为 字符串连接符

```php
<?php

    $a = 'abc';
    $b = 'def';

    $c = $a.$b;
    echo $c;     // 'abcdef'

?>
```

#### 用 echo 输出的说明

```php
<?php

    $a = 'abc';
    $b = 'def';

    echo $a.$b;  // 将两个变量的值连接到一起，再输出

    echo $a,$b;  // 先输出$a, 再输出$b
    
    /*
        两次echo的输出结果一样，但后者不需要进行连接操作，所以后者执行速度更快一些
    */

?>
```



