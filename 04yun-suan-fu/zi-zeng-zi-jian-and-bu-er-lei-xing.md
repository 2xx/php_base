#### 布尔类型变量 自增自减是无效的

```php
<?php

    $a = true;
    $b = false;

    $a--;
    $b++;

    var_dump($a, $b); // $a还是true  $b还是false

?>
```



