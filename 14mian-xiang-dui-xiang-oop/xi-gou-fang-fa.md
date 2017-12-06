#### \_\_destruct\(\) 析构方法

##### 析构函数 对象被销毁的时候执行

```php
    class User
    {
        public $name;
        public $sex;
        public $age;

        function __destruct()
        {
            echo '对象被销毁了';
        }

    }
```

##### 析构函数被触发的情况

> 1. 销毁变量 unset\( $obj \);
>
> 2. 给变量赋其它的值 $obj = 'a';
>
> 3. php文件程序执行结束 die 之后析构函数依然会执行

**所有对象变量, 在程序结束时, 最后创建的最先被销毁**

