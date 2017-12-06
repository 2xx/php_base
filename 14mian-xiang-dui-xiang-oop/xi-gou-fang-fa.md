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



