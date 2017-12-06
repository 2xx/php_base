#### 文件上传下载

##### 一. 表单部分

```php
<form  action='./xxoo.php'  method='POST'  enctype='multipart/form-data'>
     <input type='file' name='pic' />
     <input type='submit' value='提交' />
</form>
<!--
	 1) method   必须是 POST
	 2) enctype='multipart/form-data'   这一项必须有
	 3) input 标签中 type='file'   必须有 name 值

	多文件上传:
	   方式一:   
	     <input type='file' name='pic[]' />
             <input type='file' name='pic[]' />

       方式二:
            <input type='file' name='pic[]' multiple />
-->
```



##### 二. 接收数组信息

```php
<?php

	echo '<pre>';
	print_r( $_FILES['pic'] );   // 接收表单传过来的 上传文件信息

?>
```

**$\_FILES\[ 'pic' \]**中的具体信息

> $\_FILES \[ 'pic' \] \[ 'name' \]   原始文件名
>
> $\_FILES \[ 'pic' \] \[ 'type' \]     文件类型
>
> $\_FILES \[ 'pic' \] \[ 'tmp\_name' \]   上传以后的 临时文件名
>
> $\_FILES \[ 'pic' \] \[ 'error' \]   错误号, 不同的错误号, 代表着不同的错误
>
> $\_FILES \[ 'pic' \] \[ 'size' \]    上传文件的大小, 单位为字节

​

##### 三. php.ini 中关于上传文件的一些设置

> ​**post\_max\_size**=8M 表单提交的最大数据量
>
> ​**file\_uploads=On**是否开启文件上传功能
>
> ​**upload\_tmp\_dir**="\xampp\tmp" 文件上传后的 临时存放目录
>
> ​**upload\_max\_filesize**=2M 单个上传文件 最大限制
>
> ​**max\_file\_uploads**=20 一次可以同时上传多少个文件

​

##### 四. 错误号的含义

> ​ 0 上传成功
>
> ​ 1 文件过大, 超过 php.ini 中 upload\_max\_filesize 的要求
>
> ​ 2 文件过大, 超过表单中 MAX\_FILE\_SIZE 的大小
>
> ​ 3 部分文件被上传
>
> ​ 4 没有文件被上传
>
> ​ 6 找不到临时文件夹
>
> ​ 7 写入文件失败

```php
<?php
	$error = $_FILES['pic']['error'];
	
	$msg = '';
	switch($error){
      	    case 0: $msg='上传成功'; break;
            case 1: $msg='文件过大'; break;
            case 2: $msg='文件过大'; break;
            case 3: $msg='部分文件被上传'; break;
            case 4: $msg='没有文件被上传'; break;
            case 6: $msg='找不到临时目录'; break;
            case 7: $msg='写入文件失败'; break;
	}

?>
```

​

##### 五. 判断文件类型

```php
<?php

	$type = ['image/jpeg', 'image/png', 'image/gif'];
	
	$ty = $_FILES['pic']['type'];
	if (!in_array($ty, $type)) {
      		die('上传文件的类型不符合要求');
	}

?>
```

​

##### 六. 判断文件大小

```php
<?php

	$max_size = 4096;
	
	$size = $_FILES['pic']['size'];
	
	if ($size > $max_size) {
            die('上传文件超过要求大小');
	}

?>
```

​

##### 七. 生成一个随机文件名

```php
<?php
	
    $path = './uploads/';
    $ext = pathinfo($_FILES['pic']['name'], PATHINFO_EXTENSION);  // 取得 扩展名
  
    do{
      
       $dstName = $path.date('YmdHis').rand(1000,9999).'/'.$ext; // 拼装 目标文件名
      
    } while ( file_exists( $dstName ) );  // 判断目标文件是否存在, 如果存在,循环生成一个新名字

?>
```



##### 八. 专门用于文件上传的两个函数

> ​**is\_uploaded\_file\(**临时文件名**\)**判断文件是否是通过 HTTP POST 上传的
>
> ​**move\_uploaded\_file\(**临时文件名, 目标文件名**\)**将临时文件移动到指定的新位置

```php
<?php
 
    $tmpName = $_FILES['pic']['tmp_name'];
    
    if (is_uploaded_file($tmpName)) {
        move_uploaded_file($tmpName, $dstName);
    }

?>
```



##### 九. 多文件上传数组变形

```php
<?php

	foreach($_FILES['pic']['name'] as $k => $v){
    		$uploads[$k]['name']     = $v;
               $uploads[$k]['type']     = $_FILES['type'][$k];
      		$uploads[$k]['tmp_name'] = $_FILES['tmp_name'][$k];
      		$uploads[$k]['error']    = $_FILES['error'][$k];
      		$uploads[$k]['size']     = $_FILES['size'][$k];
	}

?>
```



##### 十. 文件下载



