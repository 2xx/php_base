#### 算术运算符

```php
<?php

    $a = 7;
    $b = 5;

    echo $a + $b;   // 12
    echo $a - $b;   // 2
    echo $a * $b;   // 35
    echo $a / $b;   // 1.4

    echo $a % $b;   // 2  $a除以$b的余数

?>
```

#### 特别说明：

$a % $b  如果$b为5，不管$a的值从0~n是什么值，余数只能是在 0~4之间

如果$a是负数，余数也是负数。余数的符号只和$a相关。

