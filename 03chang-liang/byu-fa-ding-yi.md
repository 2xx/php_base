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

#### 扩展知识：

可以通过 defined\('名称'\) 判断某个常量是否已经定义

get\_defined\_constants\(\)  获取所有常量

get\_defined\_constants\(true\) 获取所有常量，并分好组

get\_defined\_constants\(true\)\['user'\]  获取所有自定的常量

