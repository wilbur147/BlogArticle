## 效果演示

![image-20210803152606303](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210803152606.png)



## 教程

- 直接复制下面代码复制到主题根目录的`functions.php` 中。



```php
//页面加载时间自动检测
function wp_page_speed() {
        date_default_timezone_set( get_option( 'timezone_string' ) );
        $content .= '当前页面耗时 ';
        $content .= '<span style="color: #b3c0ce;">';
        $content .= timer_stop( $display = 0, $precision = 2 );
        $content .= ' s';
        $content .= '</span>';
        echo $content;
}
```

- 然后在要显示的地方添加下面的代码（一般都是 `footer.php` 文件）


```php
<?php echo wp_page_speed($content) ?>
```

然后直接刷新一下看效果！！！

