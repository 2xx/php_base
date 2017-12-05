#### break  退出当前循环

```php
<?php

    for($i = 1; $i <= 10; $i++){

        if ($i == 4) {
            break;
        }
        echo $i,'<br>';   // 输出 1  2  3
    }

    echo '循环后的代码';   // 输出

?>
```



