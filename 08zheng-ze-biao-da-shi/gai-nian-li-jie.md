#### 正则表达式

```
"/[^0-9]{4}/"      "/-?\d{3}/"
```

* 它是一个字符串
* 一些字符有特殊含义, 代表着一些规则与限制
* 通过函数, 对另外一个字符串发生作用        

##### 可以这样理解:

正则表达式,  是一个字符串, 用它作为规则去匹配另外的字符串, 

然后, 对匹配到的正好符合规则的内容进行操作. \(搜索, 分割, 替换\)

##### 学习两部分内容:

* 学写正则表达式
* 正则表达式处理函数

##### 正则表达式的组成:

* 定界符          通常用 / ...  /     代表正则的开始与结束
* 原子              可以是字母数字下划线以及其它可见字符     表示要匹配的内容
* 元字符          有特殊意义的字符,  用来修改原子
* 模式修正符  对正则表达式的补充说明  比如是否区分大小写等


