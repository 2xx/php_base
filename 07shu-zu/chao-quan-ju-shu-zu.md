#### 超全局数组

超全局, 是指 超越页面, 可以在两个文件之间传递的变量.

$\_GET       URL地址      表单, 超连接

$\_POST    表单

$\_REQUEST      包含 $\_GET 和 $\_\_POST

$\_COOKIE       

$\_SESSION

$\_FILES

$\_SERVER

```php
<?php

    $_SERVER['SERVER_NAME']      // 主机名
    $_SERVER['SERVER_ADDR']      // 本服务器IP地址
    $_SERVER['REMOTE_ADDR']      // 浏览当前脚本的用户IP地址
    $_SERVER['DOCUMENT_ROOT']    // 根目录的路径
    $_SERVER['REQUEST_URI']      // 用来指定要访问的页面
    $_SERVER['QUERY_STRING']     // 问号后面的检查字符串
    $_SERVER['SCRIPT_NAME']      // 当前脚本文件名称,从网站根目录开始
    $_SERVER['PHP_SELF']         // 文件自己

?>
```



