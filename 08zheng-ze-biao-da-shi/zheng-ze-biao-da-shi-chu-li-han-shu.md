#### 正则表达式处理函数

> **preg\_match\_all\(**正则表达式, 被匹配的字符串, 存放匹配结果的数组**\)**

```php
<?php

    // 正则表达式
    $ptn = '/a+/';       
​
    // 要匹配的字符串
    $str = 'axaaxaaa';
​
    // 执行匹配处理函数, 返回匹配成功的次数
    preg_match_all($ptn, $str, $arr);

    // 查看匹配结果
    echo '<pre>';
    print_r( $arr );

?>
```

> **preg\_split\(**正则表达式, 要匹配的目标**\)**   以正则表达式来分割字符串

```php
<?php

    // 正则表达式
    $ptn = '/[:,;#]/';

    // 目标字符串
    $str = "23,45;67#89;08:76";
​
    // 分割字符串, 分割结果为一个数组
    $arr = preg_split($ptn, $str);

?>
```

> **preg\_grep\(**正则表达式, 数组**\) **  返回符合条件的数组元素,生成新数组

```php
<?php

    // 正则表达式
    $ptn = '/\d{4}[-,]\d{2}[-,]\d{2}/';
    
    // 目录数组
    $arr = ["2015-12-20", "2014,10-18", "2015,10,20", "2016-11,11"];
    
    // 匹配数组中元素, 把符合条件的生成新数组
    $res = preg_grep($ptn, $arr);

?>
```

> **preg\_replace\(**正则表达式, 目标字串或数组**\)**      自行查阅php手册



