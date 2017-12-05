#### 逻辑运算符

逻辑运算的结果是  **布尔值**

**逻辑与    &&**

```php
<?php

    //  与, 并且的意思, 运算符两边同时为真, 结果才为真
    var_dump( 5 > 1  &&  2 < 7 ); // true     真&&真  真
    var_dump( 5 < 1  &&  2 < 7 ); // false    假&&真  假
    var_dump( 5 > 1  &&  2 > 7 ); // false    真&&假  假
    var_dump( 5 < 1  &&  2 > 7 ); // false    假&&假  假

?>
```

**逻辑或     \|\|**

```php
<?php

    // 或, 或者的意思, 运算符两边只要一边为真, 结果就为真
    var_dump( 5 > 1  ||  2 < 7 ); // true    真||真   真
    var_dump( 5 < 1  ||  2 < 7 ); // true    假||真   真
    var_dump( 5 > 1  ||  2 > 7 ); // true    真||假   真
    var_dump( 5 < 1  ||  2 > 7 ); // true    假||假   假

?>
```

**逻辑非     !**

```php
<?php

    // 非, 取反的意思, 非真就是假, 非假就是真
    var_dump( !true  );  // false     !真   假
    var_dump( !false );  // true      !假   真 

?>
```

**逻辑异或    xor**

```php
<?php

    // 异或, 不一样,  符号两边不相同,结果为真  符号两边相同,结果为假
    var_dump( 5 > 1 xor 2 < 7 );  // false       真xor真   假
    var_dump( 5 < 1 xor 2 < 7 );  // false       假xor真   真
    var_dump( 5 > 1 xor 2 > 7 );  // false       真xor假   真
    var_dump( 5 < 1 xor 2 > 7 );  // false       假xor假   假

?>
```



