#### 创建数据库

### `create database 库名 default charset=utf8;`

创建数据库会在 mysql/data 中创建相应的文件夹.

#### 

#### 查看数据库

### `show databases;  -- 显示所有数据库`

### `show database like 'xxoo%';   -- 显示名字以xxoo开头的数据库`

### `show create database 库名;   -- 显示创建数据库的语句`

#### 

#### 删除数据库

### `drop database 库名;`

#### 

#### 打开数据库

### `use 库名;  -- 通常先打开数据库,再进行之后的表操作和数据操作`

#### 

#### 修改数据库字符集

### `alter database 库名 charset utf8;`

不建议修改.当库中已经有数据时,之前的数据不会变更.

