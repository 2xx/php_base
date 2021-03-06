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

```php
    class Leg     // 腿类
    {
        function go(){ echo '走路去'; }
    }

    class Car    // 汽车类
    {
        function go(){ echo '坐车去'; }
    }

    class Ship   // 轮船类
    {
        function go(){ echo '乘船去'; }
    }

    class Plane   // 飞机类
    {
        function go(){ echo '搭飞机去'; }
    }

    class Person
    {
          // 去旅游
          function toTravel( $obj )    // 以参数形式传入对象
        {
            $obj -> go();
        }
    }

    $s = new Ship;
    $p = new Plane;
    $c = new Car;
    $l = new Leg;

    $ren = new Person;
    $ren -> toTravel( $s );  // 坐轮船去
    $ren -> toTravel( $p );  // 坐飞机去
    $ren -> toTravel( $c );  // 坐汽车去
    $ren -> toTravel( $l );  // 走路去~

    /*  这样的编码要灵活很多  低耦合  */
```

​**问题:**如何保证传入 toTravel\( \)方法的 都有 go\( \) 方法?

​**解决:**

​ 1\) 声明一个 接口 , 要求有 go\( \) 方法

​ 2\) 所有交通工类都要 实现 接口

​ 3\) 对 toTravel\( \) 方法, 指定接口为类型约束

```php
    interface xxoo        // 1.声明一个接口
    {
         function go();
    }

    class Ship implements xxoo  // 轮船类  实现接口
    {
        function go(){ echo '乘船去'; }
    }

    class Plane implements xxoo // 飞机类  实现接口
    {
        function go(){ echo '搭飞机去'; }
    }

    class Person
    {
          // 去旅游
          function toTravel( xxoo $obj )    // 以参数形式传入对象
        {
            $obj -> go();
        }
    }

    $s = new Ship;

    $ren = new Person;
    $ren -> toTravel( $s );  // 坐轮船去


    class UFO    // 宇宙飞船类  但是它没有实现接口
    {
          function fei(){ echo '坐宇宙飞船去'; }
    }
    $u = new UFO;

    $ren -> toTravel( $u );  // 报错,  类型不符合要求
```

接口, 是类之间, 准确的说是不同的类的对象之间交互的手段.

传入不同的对象, 就有不同的实现方式. 最终是要到达到目的地.

所以, 在设计接口时, 不需要关心具体的实现. 它只是规范.

就好像生活中打车去地铁站, 打车,不同的司机可能行驶路线是不同的, 但最终目的地是那个地铁站.

这样的多种实现形态, 就称之为**`多态`**

