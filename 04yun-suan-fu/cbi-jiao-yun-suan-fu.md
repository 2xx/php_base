#### 比较运算符

**比较运算符的运算结果为  布尔值**

```php
<?php

    $a > 5   // 大于号
    $a < 5   // 小于号
    $a == 5  // 等于号
    $a != 5  // 不等于

    $a >= 5  // 大于等于
    $a <= 5  // 小于等于

    0 === 0.0  // false  全等符号  要求类型相同, 并且值相等
    0 !== 0.0  // true   不全等    要求 或者类型不同  或者值不相等

?>
```

**特别说明**

```php
<?php
    
    (0.1 + 0.2) == 0.3   // false   浮点数因为精度的问题,有时候计算结果不准确

?>
```



