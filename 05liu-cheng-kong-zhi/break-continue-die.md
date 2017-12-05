#### break  退出当前循环

```php
<?php

    for($i = 1; $i <= 10; $i++){

        if ($i == 4) {
            break;
        }
        echo $i,'<br>';
    }

    echo '循环后的代码';

?>
```



