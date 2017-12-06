#### 错误种类

* **语法错误: **     代码不会被执行. 直接报告代码中的错误.
* **运行时错误:**  代码会被执行, 执行到错误的地方, 才报错.
* **逻辑错误: **     代码执行, 不会报错,  但就不是想要的结果.

#### 错误级别

* **提示：Notice:** Undefined variable: a
* **警告：Warning:** gettype\(\) expects exactly 1 parameter, 0 given    
* **致命：Fatal error:** Call to undefined function getTypee\(\) 

##### 举例:

```php
<?php

    getType($a);   // 未定义变量, 提示性错误
    getType( );    // 缺少参数, 警告性错误
    gettype1( );   // 函数名不对, 致命性错误

?>
```

#### 通过修改 php.ini  决定错误处理方式

display\_errors  = On/Off         是否在页面上显示错误信息

log\_errors = On/Off                 是否把发生的错误记录在日志文件中

error\_log="\xampp\php\logs\php\_error\_log"      日志文件的位置

error\_reporting =   E\_ALL & ~E\_NOTICE    设置哪些错误需要报告, 所有错误都报告, 除了提示性错误

**补充说明:**



