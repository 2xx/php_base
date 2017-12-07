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



