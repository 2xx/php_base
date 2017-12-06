#### 变长参数列表

```php
<?php

    function test()
    {
       $arr = func_get_args();   // 以数组形式,返回调用函数时的所有参数
       echo func_get_arg[1];     // 返回参数列表数组中的某一项
       echo func_num_args();     // 返回参数个数
    }
    
?>
```



