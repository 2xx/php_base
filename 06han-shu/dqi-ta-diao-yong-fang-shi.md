#### 变量函数

把**函数的名称**放在一个变量中，之后可以通过变量调用这个函数。

```php
<?php

    $a = 'test';   // 1.把函数名称存放在变量中
    $a();          // 2.通过变量调用函数

    function test()
    {
        echo '我是test函数!';
    }

    // 变量函数的方式, 让代码书写更加灵活，一期项目中会用到
?>
```

#### 匿名函数

把**函数的定义**放在一个变量中，之后可以通过变量调用这个函数。

```php
<?php

    // 把函数的定义赋值给一个变量, 这个函数可以没有名字
    $a = function(){
        echo '我是一个匿名函数';
    };   // 注意最后的分号不能少


    $a();  // 调用函数    注意: 匿名函数不会提前加载到内存

?>
```

**普通函数中的匿名函数**

```php
<?php

    function test()
    {
        $name = '小甜甜';
        return function()use($name){   // use 让匿名函数可以使用父函数中的变量
            echo '我是test函数内部的一个匿名函数<br>';
            echo '我可以使用test函数中的局部变量$name,它的值是 '.$name;
        };
    }

    $a = test(); // 调用 test() 函数, 返回匿名函数赋值给$a
    $a();        // 通过 $a调用匿名函数

?>
```

**匿名函数调用自己**

```php
<?php

    $a = function xxoo($n)use(&$a){
            echo $n,'<br>';
            if ($n > 1) {
                $a($n - 1);
            }
    };

    $a(5);

?>
```

#### 回调函数

```php
<?php

    xxoo('test');    // 调用xxoo函数, $n='test'
                     // 该函数反回来调用 test 这个函数, 当然也算是变量函数

    /*
      实参是一个匿名函数, 赋值给$n, 函数内部反回来调用这个匿名函数
    */
    xxoo(function(){
        echo '我是一个匿名函数<br>';
    });


    function xxoo($n)
    {
        $n();
    }

    function test()
    {
        echo '我是test函数<br>';
    }

?>
```

#### 递归函数   自己调用自己, 每次参数不同

```php
<?php
    // 简单回文数

    function test($n)
    {
        echo $n,'<br>';
        if ($n>1) {
            test($n - 1);  
        }
        echo $n,'<br>';
    }


?>
```

```php
<?php
    // n ~ 1 的和

    function sum($n)
    {
        if ($n > 1) {
            return $n + sum($n - 1);
        }
        return 1;
    }

?>
```

**补充说明：**

递归思路是，把一个大问题拆解成若干个小问题，获得小问题的结果，

最后将小问题的结果汇总计算得到大问题的最终结果。

