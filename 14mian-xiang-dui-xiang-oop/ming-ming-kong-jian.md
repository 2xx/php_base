## namespace \( 命名空间 \)

用来解决, 函数重名、常量重名、类重名的问题.

lamp185班的 小明

lamp188班的 小明

都是小明, 名字相同,`lamp185班lamp188班`就被称为命名空间

​

**1\) 命名空间的范围: 从定义位置开始, 到下一个命名空间之前**

**2\) 命名空间之前不能有任何输出**

**3\) 定义命名空间后, 紧跟一行空白行. \( 代码规范 \)**

#### 1.定义命名空间

#### 格式: namespace 空间名称;

```php
    namespace  aaaa;    // 定义一个命名空间aaaa, 它的范围是从当前位置到下一次命名空间之前
    class A
    {
       function say(){ echo 'aaaa空间下<br>'; }
    }


    namespace  bbbb;    // 定义一个命名空间bbbb
    class A
    {
       function say(){ echo 'bbbb空间下<br>'; }
    }


    namespace  xx\oo;   // 定义一个命名空间xx\oo
    class A
    {
       function say(){ echo 'xx\oo空间下<br>'; }
    }
```

#### 2.使用命名空间下的类

#### 格式: new \空间名称\类名称;

```php
    $a = new \aaaa\A;        
    $b = new \bbbb\A;
    $c = new \xx\oo\A;
    $d = new A;   // 因为这里仍然是 xx\oo 空间,  所以可以不写空间

    // 每次实例化时, 都要写上命名空间, 比较麻烦
```

#### 3.为了方便书写

#### 格式: use 空间名称\类名称;

```php
    // 为了举例, 与上面代码无关
   
    use  aa\bb\cc\dd\A;   // 之后new的时候就不用加命名空间了
    use  xx\yy\zz\nn\B;
    
    new A;   
    new B;
```



