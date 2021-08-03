## 效果演示

![image-20210803153258545](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210803153258.png)



## 教程

- 直接复制下面代码复制到主题根目录的`functions.php` 中。



```php
/**
 * 统计全站总访问量/今日总访问量/当前是第几个访客
 * @return [type] [description]
 */
function wb_site_count_user(){
    $addnum = rand(2,6);  //每个访客增加的访问数 5 - 10的随机数
    session_start();
    $date = date('ymd',time());
    if(!isset($_SESSION['wb_'.$date]) && !$_SESSION['wb_'.$date]){        
        $count = get_option('site_count');
        if(!$count || !is_array($count)){
            $newcount = array(
                'all' => 57670,
                'date' => $date,
                'today' => $addnum
            );
            update_option( 'site_count', $newcount );
        }else{
            $newcount = array(
                'all' => ($count['all']+$addnum),
                'date' => $date,
                'today' => ($count['date'] == $date) ? ($count['today']+$addnum) : $addnum
            );
            update_option( 'site_count', $newcount );
        }
        $_SESSION['wb_'.$date] = $newcount['today'];
    }
    return;
}
add_action('init', 'wb_site_count_user');
//输出访问统计
function wb_echo_site_count(){
    session_start();
    $sitecount = get_option('site_count');    
    $date = date('ymd',time());
    // echo '<p>总访问量：<span style="color:red">'.absint($sitecount['all']).'</span> &nbsp;&nbsp; 今日访问量：<span style="color:red">'.absint($sitecount['today']).'</span> &nbsp;&nbsp; 您是今天第：<span style="color:red">'.absint($_SESSION['wb_'.$date]).'</span> 个访问者</p>';   
    echo '总访问量：<span style="color:red">'.absint($sitecount['all']).'</span>';
}
```

- 然后在要显示的地方添加下面的代码（一般都是 `footer.php` 文件）


```php
<?php wb_echo_site_count(); ?>
```

然后直接刷新一下看效果！！！

