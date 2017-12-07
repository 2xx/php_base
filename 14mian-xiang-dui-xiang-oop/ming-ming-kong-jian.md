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

#### 4. 解决重名

#### 格式: use 空间名称\类名称 as 别名;

```php
       use aaaa\A;
       use bbbb\A;
       use xx\oo\A;

       new A;     // 重名
       new A;     // 重名
       new A;     // 重名


    use  aaaa\A   as  X;   // 起一个别名
    use  bbbb\A   as  Y;   // 起一个别名
    use  xx\oo\A  as  Z;   // 起一个别名

    new X;   // 直接使用类名
    new Y;   // 直接使用类名
    new Z;   // 直接使用类名
```

### 5. 补充说明

#### new \系统类;

所有系统类, 在某个命名空间下使用的时候, 也需要指明其所在空间, \ 代表顶层空间

比如 new**\PDO**\($dsn, 'root', ''\);

也可以这样:

#### use 系统类;

#### new 系统类;



**use aa\bb\User;**

**User::class**会被转化为字符串 "**aa\bb\User**"



**\aa\bb\User::class**会被转化为字符串 "**aa\bb\User**"

## 

​



#### 必须知道的潜规则

#### 1. 一个类 =&gt; 一个php文件

#### 2. 类的名称, 应该是 php文件名称的一部分

​ UserController.php 或 UserController.class.php

​ require\("{**$clsName**}Controller.php"\);

​ 或者

​ require\("{**$clsName**}Controller.class.php"\);

#### 3. 每个类 开头写一个 命名空间.

#### 4. 命名空间的名称 写成 类文件所在的路径

​ 如果 UserController.php 存放在 Controller/admin 目录下

​ 命名空间就应该写成:**namespace Controller\admin;**

