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

**1. 现实世界有不同的类, 那么就有相应的不同的对象, 对象不是孤立的, 各种对象之间应该发生关系.**

**2. 上面的代码有缺限**

**问题:**在 Person 类的 toTravel 方法中, 必须是坐车去, 代码是写死了, 如果想改坐飞机, 必须修改类代码.

**解决 :**

​ 第一, 在外部创建对象, 以参数的形式传入到 toTravel\( \) 方法

```php
    class Person
    {
          // 去旅游
          function toTravel( $obj )    // 以参数形式传入对象
        {
            $obj -> go();
        }
    }

    $p = new Person;   // 创建一个 人 对象
    $c = new Car;      // 创建一个 车 对象

    $p -> toTravel( $c );  // 把  车对象 传入
```

**问题:**其它的类的方法 不统一, toTravel\( \) 中 只能调用对象的 go\( \) 方法

**解决:**把 Leg、Car、Ship、Plane 类的方法名全部改成 go\( \)

