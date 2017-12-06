#### 声明一个类

> **描述了一个存储结构**

```php
<?php

    class Student
    {
          public $name;
          public $sex;
          public $age;

          function say()
          {
              echo '水哥好';
          }
    }

?>
```

> **概括**

```php
class 类名
{
	修饰符 成员属性;     ( 常量, 变量 )  public 为默认值  公共的意思

	修饰符 成员方法;     ( 函数 )

}
```

#### 生成一个对象 \(实例化\)

```php
<?php
        /*
	    参考类的样子定义一个变量
	    这个变量中,也有 name sex age 这些变量
	    这个变量中,也有 say() 这个函数
	*/

    	$obj = new Student; 
?>
```



