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

#### continue  中止本次循环, 继续下一次循环

```php
<?php

    for($i = 1; $i <= 10; $i++){

        if ($i == 4) {
            continue;
        }
        echo $i,'<br>';  // 输出 1  2  3     5  6  7  8  9  10
    }

    echo '循环后的代码';  // 输出

?>
```

#### exit  和  die     使整个php文件结束

```php
<?php

    // exit 和 die 是同义词,用法一样

    for($i = 1; $i <= 10; $i++){

        if ($i == 4) {
            // die('代码结束前可以输出一些内容');
            die;   
        }
        echo $i,'<br>';  // 输出 1  2  3
    }

    echo '循环后的代码';  // 不执行

?>
```



