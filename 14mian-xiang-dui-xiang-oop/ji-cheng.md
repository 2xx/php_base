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



