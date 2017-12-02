#### 1.单引号定义

```php
<?php

    $str = 'i love you';

?>
```

#### 2.双引号定义

```php
<?php

    $str = "i love you";

?>
```

#### 3.定界符 heredoc 定义

```php
<?php

    $str = <<<ABCD

     ... ... // 一大段文字

ABCD;

    /*
        注意：
        <<<ABCD 后面立即回车
        ABCD;  要顶头写，分号后立即回车
    */

?>
```



