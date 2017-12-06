#### 懒惰模式

?  号在正则表达式中还有一个意思. 就是 拒绝贪婪.   要求尽量少的匹配:

`/a{1,4}?/   `   表示尽量匹配1次

`/<b>.*?<\/b>/`    \* 表示匹配0次1次或多次, 后面加? 就表示尽量少的匹配

`<b>a?aa</b><b>ccb>c</b><b>ddd</b>

/&lt;b&gt;.\*&lt;\/b&gt;/     会把整个字符串匹配成一个结果, 因为默认为最大贪婪

/&lt;b&gt;.\*?&lt;\/b&gt;/   会匹配为   &lt;b&gt;a?aa&lt;/b&gt;    &lt;b&gt;ccb&gt;c&lt;/b&gt;      &lt;b&gt;ddd&lt;/b&gt;
