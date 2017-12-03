### 定义常量

##### 1.通过 define\( \) 方式

```php
<?php

    define('LOVE', 'i love you!');
    define('PI', 3.1415926);

    echo LOVE;
    echo PI * 7; // 常量是可以参与运算的

?>
```

##### 2.通过 const 方式

```php
<?php

    const LOVE = 'i love you!';
    const PI = 3.1415926;

    echo LOVE;
    echo PI * 7;
    
?>
```



