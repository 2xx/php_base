#### 与短路

```php
<?php

    $a = 1;
    $b = (5 < 3) && ($a = 3);  
    var_dump( $a, $b ); // 1  false
    
    /*
        
    */
    
?>
```



