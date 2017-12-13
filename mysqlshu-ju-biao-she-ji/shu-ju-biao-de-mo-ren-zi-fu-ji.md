### 设置默认字符集

#### 1、创建时直接设置字符集

#### 2、配置文件中修改字符集

* ##### liunx  -- /etc/my.cnf
* ##### windows  my.ini文件

  * 设置MySQL服务器的字符集
* ```
           character-set-server=gbk
  ```

  * 设置排序方式
* ```
            collation-server=gbk_chinese_ci
  ```
* ##### 控制台中设置
* ```
         CREATE DATABASE IF NOT EXISTS mydb DEFAULT CHARCTER SET utf8 COLLATE utf8_general_
  ```



