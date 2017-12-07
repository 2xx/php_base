### 一. 类型约束

​ 类型约束, 是调用成员方法时, 对**参数类型**加以限制.

* 如果约束的类型为**四种标准类型**, 当调用时参数的类型不对, 会尝试类型转换

```php
    class A
    {
         static function xxoo(int $a)   // 约束 参数应该是 整数型
        {
             echo '<pre>';
             var_dump( $a );    
        } 
    }
    A::xxoo('2b');    // 2 因为类型约束   函数中会尝试进行类型转换
    A::xxoo(true);    // 1
    A::xxoo(2.34);    // 2
```

如果约束的类型为**数组**或者是**类**, 或者是**接口**当调用时参数的类型不对, 会报错

### instanceof

判断一个**对象**是否属于某个**类**或该类的**子类**

```php
	class Person
    {
      .....
    }
	
	class Student extends Person
    {
      .....
    }

	$obj = new Student;
    $xxoo = 10;
    var_dump( $obj instanceof Student );  // true
	var_dump( $obj instanceof Person  );  // true
    var_dump( $xxoo instanceof Student);  // false
```



