#### \_\_construct\(\) 构造方法

###### 构造函数 对象被创建的时候自动执行

> 函数名是固定的, 构造函数的名称也可以和类同名

```php
    class Student
    {
        public $name;
        public $sex;

        function __construct()
        {
            echo '对象被创建时执行这个函数';
        }
    }

    $obj = new Student;         // 这里就会自动调用 __construct()函数
```

##### 利用 构造函数 和 $this 给对象的属性赋值

```php
    class User
    {
        public $name;
        public $sex;
        public $age;

        function __construct($a, $b, $c)
        {
            $this -> name = $a;
            $this ->  sex = $b;
            $this ->  age = $c;
        }
    }


    $obj = new User('小明', '男', 24);        // 创建对象的同时 赋值
```



