接口——类的规范, 要定义一个类, 必须遵守这个规范, 符合接口要求.

#### 声明一个接口

```php
    interface 接口名
    {
                           // 不能有成员属性

         function a();   // 1)没有函数体  2)必须是public
         function b();
    }
```

#### 实现接口, 形成一个类

按照接口定义类时,**要求:**

​ 1\) 必须实现接口中的所有方法. \(或者是抽象类\)

​ 2\) 方法名称必须相同.

​ 3\) 方法中参数的类型, 个数必须一致. \(如果实现方法中参数个数多, 多出的参数可以给默认值\)

```php
    interface animal     // 声明接口
    {
         public run();
         public call();
    }

    class yang  implements animal    // 实现接口
    {
         public run(){ echo '四蹄狂奔'; }    // 实现成员方法
         public call(){ echo '咩咩咩'; }     
    }

    $obj = new yang;
    $obj -> call();
```

##### 声明一个接口, 同时继承多个接口 \(了解\)

```php
    interface aaa     // 声明接口
    {
       ....
    }

    interface bbb     // 声明接口
    {
      ....
    }

    // 继承其他接口
    interface xxoo extends aaa,bbb
    {

    }
```

##### 一个类, 同时实现多个接口 \(了解\)

```php
    interface aaa       // 声明接口
    {
         function a();
    }

    interface bbb       // 声明接口
    {
         function b();
    }

    // 同时实现多个接口
    class xxoo implements aaa,bbb
    {
         function a(){ echo '实现a方法'; }
         function b(){ echo '实现b方法'; }
    }
```

#### 接口的用处

```php
    class Leg     // 腿类
    {
        function to(){ echo '走路去'; }
    }

	class Car    // 汽车类
    {
        function go(){ echo '坐车去'; }
    }
	
	class Ship   // 轮船类
    {
        function qu(){ echo '乘船去'; }
    }
    
	class Plane   // 飞机类
    {
        function fei(){ echo '搭飞机去'; }
    }

	
    
	class Person   // 人类
    {
        // 去旅游
        function toTravel()
        {
              $obj = new Car;  // 这里代码写死了,  这里称为 依赖,耦合
              $obj -> go();
        }
    }
```



