#### 自增运算 --

```php
<?php

    $a = 5;
    $a--;    // 相当于 $a=$a-1
    echo $a; // 4  


    $a = 5;
    --$a;    // 相当于 $a=$a-1
    echo $a; // 4

?>
```

#### $a-- 与  --$a 的区别

```php
<?php

    $a = 5;
    echo $a--; // 5   先使用$a原有的值输出，再让$a减1
    echo $a;   // 4


    $a = 5;
    echo --$a; // 4   先让$a减1，再使用$a的值输出
    echo $a;   // 4

?>
```

```php
<?php

    $a = 5;
    echo $a-- + 2;  // 5+2  显示输出 7   然后再 (5-1)


    $a = 5;
    echo --$a + 2;  // (5-1) + 2  显示输出 6


?>
```



