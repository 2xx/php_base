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

####  对象运算符

> **成员属性 赋值**

```php
	$obj -> name = '小明';   // 要注意 属性前面没有$
	$obj -> sex  = '男';
	$obj -> age  = 23;
```

> **成员属性 输出**

```php
	echo $obj -> name;
	echo $obj -> sex;
	echo $obj -> age;
```

> **成员方法 调用**

```php
        $obj -> say();
```

> **成员属性的添加与删除**

```php
	$obj -> xxoo = 'abcdefg';

	unset($obj->xxoo);
```

### $this

##### $this 代表它所在的对象

```php
	class Student
	{
		public $name;

		function say()
		{
			echo '名字: '.$this->name;
		}
	}

	$xm = new Student;          // 定义一个$xm变量, 它是一个对象类型

	$xm -> name = '小明';       // 给对象中的 name 赋一个值

	$xm -> say();              // 输出   名字: 小明
```

##### return $this 连贯操作

```php
   class xxoo
   {
         public function a()
         {
            echo 'a方法<br>';
            return $this;     // 返回对象自身.
         }
         
         public function b()
         {
            echo 'b方法<br>';
            return $this;    // 返回对象自身
         }
         
         public function c()
         {
            echo 'c方法<br>';
            return $this;   // 返回对象自身
         }
    }

    
    $obj = new xxoo;

    $obj -> a() -> b() -> c();  // 可以这样调用成员方法
```



