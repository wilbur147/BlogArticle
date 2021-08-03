## 效果演示

![image-20210803151950995](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210803151951.png)



## 教程

- 直接复制下面代码放到主题根目录的`functions.php` 中即可。（请注意修改成你自己网站建站时间）



```php
// 运行时间
// 设置时区
date_default_timezone_set('Asia/Shanghai');
/**
* 秒转时间，格式 年 月 日 时 分 秒
*
* @author Roogle
* @return html
*/
function getBuildTime(){
// 在下面按格式输入本站创建的时间
$site_create_time = strtotime('2020-02-28 08:00:00');
$time = time() - $site_create_time;
if(is_numeric($time)){
$value = array(
"years" => 0, "days" => 0, "hours" => 0,
"minutes" => 0, "seconds" => 0,
);
if($time >= 31556926){
$value["years"] = floor($time/31556926);
$time = ($time%31556926);
}
if($time >= 86400){
$value["days"] = floor($time/86400);
$time = ($time%86400);
}
if($time >= 3600){
$value["hours"] = floor($time/3600);
$time = ($time%3600);
}
if($time >= 60){
$value["minutes"] = floor($time/60);
$time = ($time%60);
}
$value["seconds"] = floor($time);
 
echo '<span class="btime" style="color: #0196e3;">'.$value['years'].'年'.$value['days'].'天'.$value['hours'].'小时'.$value['minutes'].'分</span>';
}else{
echo '';
}
}

```

编辑成功后，找到合适的位置添加（比如 `footer.php` 文件）

`已稳定运行：<?php getBuildTime(); ?>`

做好以上步骤就 OK 啦，赶紧去试试看效果吧！！！

