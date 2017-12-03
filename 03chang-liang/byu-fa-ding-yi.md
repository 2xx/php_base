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

#### 区别：

流程控制中： 只可以使用define

成员属性是常量：只能使用  const



#### 注意：

旧有代码中，多用define

php语法规范中，推荐尽量使用 const



