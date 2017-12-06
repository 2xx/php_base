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



