## extends 继承、扩展

定义一个类 A ,

定义一个类 B, 继承A,

A 中的所有成员 , B 中也都有. A =&gt; 父类 B =&gt; 子类

除此之外,

1\) B 中还可以**添加**新的成员属性和方法

2\) B 中还可以**重写**已有的成员方法.

```php
  class A
  {
     成员属性1;
     成员属性2;

     成员方法1(){}
     成员方法2(){}

  }

  class B extends A   // B 继承 A
  {
     // 这里面什么都不写, 也已经有A中的成员属性和成员方法

     // 添加 成员属性 和 成员方法
     成员属性3;

     成员方法3(){}
  }
```

**注意:**重写成员方法的时候, 参数个数要一致, 构造方法可以不一致

```php
  class A
  {
      function xxoo()
      { 
         echo '111111'; 
      }
  }

  class B extends A
  {
      function xxoo()     // 重新定义了 xxoo 这个成员方法. 
      { 
           echo '222222';
         parent::xxoo();  // 子类中 调用 父类成员方法
      }
  }

  $obj = new B;
  $obj -> xxoo();    // 调用的是 B 中重新定义的 xxoo
```

`父类`**中的 私有成员\( private \) 在**`子类`**中也是无法访问的.**

父类中使用 受保护的 \(**protected**\) 修饰成员, 使成员在**子类中也可以访问.**

|  | 类内部 | 子类中 | 外部 |
| :--- | :---: | :---: | :---: |
| **public** | Y | Y | Y |
| **private** | Y |  |  |
| **protected** | Y | Y |  |

### final

##### 写在成员方法之前, 代表该成员方法不允许被重写.

```php
  class A
  {
       final 方法1(){ }     // 这个方法在子类中不能被重写, 否则报错
             方法2(){ }
  }
```

##### 写在定义类的class之前, 代表这个类不能被继承.

```php
  // 这个类不允许被继承
  final class A
  {

  }
```

### static

写在成员属性之前, 成员称为**静态成员属性**

静态成员属性, 是静态的, 保存在类的定义内存中. 不管对象创建与销毁, 它都存在.

**self::**代表本类的

```php
  class A
  {
      static public $abc = 'jingshui';    // 1.定义静态成员

      function xxoo()
      { 
          echo self::$abc;     // 2.成员方法中访问
      }
  }

  echo A::$abc;     // 3.外部 通过 类名::$属性名 访问

  $obj = new A;
  echo $obj::$abc;  // 4.外部 通过 对象::$属性名 访问  (这样访问慢一点)
```

### 常量 const

##### 在类的内部定义常量, 只能使用 const

```php
  class A
  {
     const XXOO = 'jingshui';   // 1.定义常量

     function say()
     {
         echo self::XXOO;       // 2.成员方法中 访问常量
     }
  }

  echo A::XXOO;     // 3. 外部 类名::常量名

  $obj = new A;
  echo $obj::XXOO;  // 4. 外部 对象::常量名
```

### 单例模式

单例设计模式, 让这个类只能实例化一个对象.

```php
    class A
    {
         static private $obj;    // 1.定义 静态+私有 成员属性

         private function __construct()  // 2.私有化 构造方法  之后就不能 new 了
         {

         }

         static function getObj()      // 3.静态+公有, 获取一个对象
         {
              if ( empty(self::$obj) ) {
                 self::$obj = new self;  // 如果以前没有创建过对象,就创建一个保存起来
              } 
              return self::$obj;   // 返回类中保存的对象实例
         }

    }
```

### trait

与 class 相似, 但是用 trait 定义的结构,不能直接实例化对象

用 trait 定义好的结构, 可以用在定义的类中.

```php
    trait xxx
    {
        private $name;
        function a(){}
        function b(){}
    }

    trait ooo
    {   
        private $sex;
        function c(){}
        function d(){}
    }

    class Person
    {
        use xxx,ooo;     // 把两个 trait 拿进来拼装这个类
       function d(){}    // 重名
       function e()
       {
                ooo::d();   // 调用 trait ooo 中的 d() 方法
       }

    }

    $obj = new Person;
    $obj -> a();  
    xxx::a();   // 可以直接调用 trait xxx 中的 a() 方法
```

##### 成员方法同名时的优先级别: 子类方法  =&gt; trait方法  =&gt; 父类方法



