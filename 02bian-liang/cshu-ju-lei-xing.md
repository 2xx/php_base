## 数据类型

所有可以存储到变量中的数据，我们把它分类八种类型：

##### 四种标准类型

```
布尔类型    bool

整数类型    int

浮点类型    float

字符串型    string
```

##### 两种复合类型

```
数组类型    array

对象类型    object
```

##### 两种特殊类型

```
资源类型    resource

空类型      null
```

##### 

##### 变量中存储一个整数，这个变量就叫整型变量，存储什么样的数据，就是什么类型的变量

.

#### 查看变量的类型和值 var\_dump\( 变量 \)

```php
<?php

    $a = 7;

    echo '<pre>';
    var_dump( $a ); // int(7)

?>
```

#### 只获取变量的类型  getType\( 变量 \)

```php
<?php

    $a = 7;

    echo getType( $a );  // integer

?>
```



