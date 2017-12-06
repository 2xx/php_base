#### 声明方式一        数组名\[ 下标 \] = 值;

```php
<?php

    $arr[0] = '张三';         // 数字下标 索引数组
    $arr[1] = '男';
    $arr[2] = 18;

    $brr['name'] = '李四';    // 字串下标 关联数组
    $brr['sex'] = '女';
    $brr['age'] = 20;

?>
```

##### **注意:  ** 当 \[  \]为空时, 会被理解为 索引下标最大值+1

```php
<?php

     $arr[ ] = 'a';      // 数组的第1个元素, 所以这个下标为 0
     $arr[3] = 'b';      // 可以指定随意数字做下标, 不一定是 1
     $arr[ ] = 'c';      // 这个元素的下标为 4,  就是最大下标3 + 1

     $brr['name'] = 'a';
     $brr['sex']  = 'b';
     $brr[  ] = 18;      // 因为 $brr 这个数组之前没有索引下标, 所以这里是 0 

?>
```

#### 数组元素的访问

```php
<?php

    $arr['name'] = '思思';
    $arr['sex']  = '女';
    $arr[] = 18;

    echo $arr['name'];     // 输出某个元素值
    echo $arr[0];       

    $arr['name'] = '甜甜'; // 对元素进行修改
    $arr[0] = 20;

    unset($arr['sex']);    // 销毁某个元素

?>
```

#### 输出查看整个数组

整个数组不能用 echo 会报错, 并且输出一个 'Array' 字符串

```php
<?php

    $arr['name'] = '张三';
    $arr['sex'] = '男';
    $arr['age'] = 18;

    echo '<pre>';
    print_r( $arr );  // 查看整个数组

    var_dump( $arr ); // 查看整个数组

?>
```

#### 其它一些处理

```php
<?php

    $arr['name'] = '张三';
    $arr['sex'] = '男';
    $arr['age'] = 18;

    $k = 'name';
    echo $arr[ $k ];   // 输出 张三

    echo $arr[ name ]; // 报错, 常量未定义, 然后把 name 理解为字串, 输出张三

?>
```


