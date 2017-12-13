### 数据值和列类型

1. #### 数据值：

   * 数值型

   * 字符型

   * 日期型

   * 空值

   * ............
2. #### 列类型

   * 数值类

   * 字符串类

   * 日期/时间类

   * #### 数值类和数据列类型

     1. ![](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image002.jpg)

        **tinyint** 1字节 可以表示 0-255 \(无符号\) 可以表示 -128 ~ 127 \(有符号\)

        **int** 4字节 也分为"有符号"和"无符号"

        ​​ **decimal** 以字符串形式存储的浮点数 decimal\(5, 2\) 表示数值总共5位, 小数占2位

        Smallint小的整型

        Mediumint中等整型

        Bigint大整型

        注意：字段默认情况下有符号的。

     2. ![](/assets/import.png)、

        ```
          Float单精度浮点型

          Double\(m,d\)双精度浮点型

                      M表示多少个数

                      D,小数点后面有多少位 double\(8,2\)

          Decimal\(5,2\);字符串类型的浮点型\(精确\)，金融数据时使用，属于字符串类型，里面经常存钱。

          最大的范围与double相同:m给定decimal的有效范围，D决定小数点后面有几位
        ```

     3. ![](/assets/import1.png)

        ```
          char 定长字符串
        ```

     ​          char\(7\) 不管实际插入多少字符, 它都会占用7个字符位置\(中文一个汉字也是一个位置\)

     ```
          ​ varchar 变长字符串
     ```

     ​          varchar\(7\) 如果实际插入4个字符, 那么它只占4个字符位置

     ```
           enum 枚举类型\( 多选一 \)  
          ​ sex enum\('w','m','x'\) 代表sex这个字段, 可以取 'w', 'm', 'x' 中的一个值

          ​ set 集合类型 \( 多选多 \)

          Text\(\)大文本类型：一般用于文章内容的存储
     ```

     ##### Char\(\)和Varchar\(\)的区别

     ```
           Char\(\)类型限制的字段，如果该字段的内容没有达到括号中指定的长度，那么会用空格占位，占到该长度。浪费空间（硬盘的大小），查询效率高

           Varchar\(\)类型限制的字段，如果该字段的内容没有达到括号中指定的长度，那么不会占位，以实际保存的字符串长度为准，节省了硬盘空间，但是查询效率低。

                  ![](/assets/import2.png)
     ```

     ```
     ![](/assets/import5.png)

          date  年月日
     ```

     ![](/assets/import7.png)

```
      time  时分秒

      datetime 年月日时分秒

      timestamp 时间戳

      year 年
```

NULL值

		NULL意味着“没有值”或“未知值”

		可以测试某个值是否为NULL

		不能对NULL值进行算术计算

		对NULL值进行算术运算，其结果还是NULL

		0或NULL都意味着假，其余值都意味着真



MySQL的运算符：

		算术运算符：+ - \* / % 

		比较运算符：= &gt; &lt; &gt;= &lt;= &lt;&gt; != 

		数据库特有的比较：in，not in, is null,is not null,like, between and 

		逻辑运算符：and or not

