## 自动加载类 \_\_autoload\( \)

触发时机:

​ 1\) 实例化对象时, 类的定义不存在

​ 2\) 被其它类继承, 类的定义不存在

​ 3\) 在类中使用的 trait 未定义

形 参:

​**$clsName**缺少定义的类名\( 包括命名空间 \)

函数位置:**与其它魔术方法不同, \_\_autoload\(\)是一个单独的函数, 不存在某个类中.**

```php
  function __autoload( $clsName )
  {  
       require("{$clsName}.php");
  }

  new User;   // 没有User类定义, 所以会触发  __autoload('User');

  new \xx\oo\User;  // 没有User类定义,所以会触发 __autoload('xx\oo\User');
```

##### 注册自动加载类处理函数 \( 了解 \)

```php
    function xx( $clsName ){ echo "xx处理函数:加载{$clsName}类"; }
    function oo( $clsName ){ echo "oo处理函数:加载{$clsName}类"; }

    spl_autoload_register('xx');
    spl_autoload_register('oo');

    new User;   // 没有User类定义,  1)触发xx()函数  2)触发oo()函数

				// 如果 xx()函数执行了, 加载了 User 类的定义, 那么 oo() 函数就不会执行了
```



