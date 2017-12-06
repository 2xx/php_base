#### 用 for 循环遍历数组

```php
<?php

    $arr = ['a', 'b', 'c', 'd'];

    $n = count( $arr );       // 统计数组元素个数

    for($i = 0; $i < $n; $i++){
        echo $arr[ $i ];
    }
​
    /*
        数组的下标, 必须是连续的索引数组
    */

?>
```

#### 用 数组指针 函数遍历数组

reset\( \)    把数组内部指针指向第一个单元

next\( \)     将数组中的内部指针向前移动一位

prev\( \)     将数组中的内部指针倒回一位

end\( \)      将数组的内部指针指向最后一个单元

current\( \)    返回指针当前位置的 值

key\( \)            返回指针当前位置的 下标

```php
<?php

    $arr = ['a', 'b', 'c', 'd'];
    reset($arr);
    while($v = current( $arr )){
       ....
       next($arr);
    }

?>
```

#### 用 list...each 遍历数组

```php
<?php

    $arr = ['a', 'b', 'c', 'd'];
​
    while( list($k, $v) = each($arr) ){
      
        echo $k.'----'.$v;
    
    }
​
    /*
        each(数组)      每一次取出一个元素, 返回一个数组
        list($k, $v)   
            把下标为0的内容赋值给$k
            把下标为1的内容赋值给$v
    */

?>
```



