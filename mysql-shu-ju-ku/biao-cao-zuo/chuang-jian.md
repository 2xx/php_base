### 创建表

```
create table 表名(
    字段名  数据类型,
    字段名  数据类型
);
```

```
-- 如果数据表不存在,则创建
create table if not exists 表名(
    字段名  数据类型,    -- 字段之间用逗号隔开
    字段名  数据类型
);
```

```
create table 表名(
    字段名  数据类型,
    字段名  数据类型
)engine=innodb default charset=utf8;  -- 表引擎  字符集
```

例子:

```
create table users(
    uid int,
    uname char(4),
    sex char(1),
    age int
);
```



