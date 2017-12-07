### 抽象类 abstract

* 不具体的类
* 某个成员方法,**没有函数体**, 视为"不具体".
* **不能实例化对象**, 没有具体的函数体, 实例化出对象也是废品.
* 子类**继承**抽象类,**重写抽象方法**的函数体,使之变具体, 然后通过子类实例化对象

```php
	abstract class Person
	{
        function eat(){ echo '咋吃也不胖'; }
        abstract function sa();   // 抽象方法  没有函数体, 直接加分号
	}

	class Boy extends Person     // 子类 继承 抽象类
    {
        function sa(){ echo '顶风尿三丈'; }  // 重写方法  填加函数体
    }
```



