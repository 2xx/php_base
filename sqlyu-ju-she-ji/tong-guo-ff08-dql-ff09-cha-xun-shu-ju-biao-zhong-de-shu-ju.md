数据的DQL操作：数据查询

==============================================

```
格式：

    select \[字段列表\]\|\* from 表名

    \[where 搜索条件\]

    \[group by 分支字段 \[having 子条件\]\]

    \[order by 排序 asc\|desc\]

    \[limit 分页参数\]
```

字段部分

```
1\)所有字段

  select \* from users;



2\)部分字段

  select uid,uname,age from users;



3\)查询10年后的年龄

  select uid,uname,age+10 from users;



4\)别名

  select uid,uname,age+10 xxoo from users;  给字段起别名

  select uid,uname,age from users u;    给表名起别名



5\)列合并,合并年龄与性别

  select uid,uname,concat\(sex,age\) from users;



6\)去除重复的字段,班级,性别

  select distinct uname from users;



7\)在查询结果中无中生有添加一列

  select \*,'北京校区' school from users;  在查询结果中,添加校区
```

条件部分

```
8\)php197的学生

  select \* from users where classid='lamp197';



9\)php197的女生

  select \* from users where classid='lamp197' and sex='w';



10\)年龄大于20的学生

  select \* from users where age&gt;20;



11\)年龄 在 30 到 40 的人

  select \* from users where age&gt;=30 and age&lt;=40;

  select \* from users where age between 30 and 40;



12\)age 不在 20 到 30 的人 

  select \* from users where age&lt;20 or age&gt;30;

  select \* from users where age not between 20 and 30;  不包含 20和30



13\)php197班和php185班的女生

  select \* from users where \(classid='lamp197' or classid='lamp185'\) and sex='w';



  a. 和应该理解为 or      

  b. and 比 or 优先级要高,所以这里加\(\)



14\)185班的男生和197班的女生

  select \* from users where \(classid='lamp185' and sex='m'\) or \(classid='lamp197' and sex='w'\);



15\)找uid为 3,5,8,9,12 的人

   // select \* from users where uid=3 or uid=5 or uid=8 or uid=9 or uid=12;

   select \* from users where uid in\(3,5,8,9,12\);



  找uid 不是 12,15,17 的人

   select \* from users where uid not in\(3,5,8,9,12\)



16\)查询classid值不为NULL的人

   select \* from users is NULL;

   select \* from users is not NUll;



17\)找名字为2个字的人

\_ 匹配任意一个字符

  select \* from users where uname like '\_\_';



18\)找名字中以'李'开头的

d匹配任意个任意字符

  select \* from users where uname like '李%';



19\)找名字中以'春'结尾的

  select \* from users where uname like '%林';



20\)找包含'虎'的人

  select \* from users where uname like '%虎%';
```

分组查询  group by   分组伴随着统计  男生多少  女生多少

统计函数:

```
  count\(\*\) 统计个数   count\(classid\) 不会统计值为NULL的记录

  sum\(\)    求和   比如符合条件的人的总年龄

  avg\(\)    平均数

  max\(\)  min\(\)



1\)lamp197总共多少人

  select count\(\*\) from users where classid='lamp197';



2\)每个班人数

  select classid,count\(\*\) from users group by classid;



3\)最大年龄,最小年龄,平均年龄



    //查找年龄最大的那个人

    select \* from users where age=\(select max\(age\) from users\);



4\)在平均年龄之上的人

    select \* from users where age&gt;平均年龄

    select \* from users where age&gt;\(select avg\(age\) from users\);





5\)每个班的男生,女生各多少人

    select classid,sex,count\(\*\) from users group by classid,sex;



6\)每个班的男生女生各多少人,要求在20-30岁的

    select classid,sex,count\(\*\) from users where age&gt;=20 and age&lt;=30 group by classid,sex;



7\)每个班多少人,只显示班级人数大于12的

   select classid,count\(\*\) from users group by classid having count\(\*\)&gt;12;





8\)按班级分组,并获取每个班中学生的姓名

   select classid,group\_concat\(uname\) from users group by classid;
```

排序  order by 字段名   默认 asc升序    desc降序

```
1\)年龄从小到大排序

  select \* from users order by age;



2\)年龄从大到小排序

  select \* from users order by age desc;



3\)先女后男,年龄再小到大     先按性别排序,相同性别再按年龄排序

  select \* from users order by sex,age



  先男后女,年龄从大到小

  select \* from users order by sex desc,age desc;



4\)先按班级排序,再按年龄从大到小

  select \* from users order by classid,age desc;
```

分页  获取部分数据  limit m,n;

```
    m 代表跳过的记录数

    n 代表要显示的记录数
```

1\) select \* from users limit 5;    跳过0条,显示5条记录

2\) select \* from users limit 2,3;  跳过2条,显示3条记录

条件: 每页显示5条记录

```
   第一页   limit 0,5

   第二页   limit 5,5

   第三页   limit 10,5

   第四页   limit 15,5

   第五页   limit 20,5
```

第n分页公式:  limit \(n-1\)\*5,5

1\)年龄最大的3个人,\(如果第3名和第4名年龄相同,取uid最大的\)

```
 select \* from users order by age desc limit 3;

 select \* from users order by age desc,uid desc limit 3;
```

2\)185班女生年龄最小的3个人

```
 select \* from users where classid='lamp185' and sex='w' order by age limit 3;
```

3\)女生最多的班级

```
 select classid,count\(\*\) from users where sex='w' group by classid order by count\(\*\) limit 1;
```



