

![image-20210803105840099](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210803105840.png)

## 前言

做网站得知道存在大量死链，将影响网站的站点评级，一个博客网站长时间下来肯定死链会很多，特别是喜欢折腾的博客站长们，博客出现死链的可能性会非常的大。其中 WordPress 的页面可以说是“死链”的重灾区了。

死链产生的原因有很多，一般都是：人为链接输入错误、网站页面删除、内容位置变动、动态数据库、路径更改、网站还没有做好就上传到服务器也有可能会导致产生死链，还有就是服务器的问题导致出现死链（含有中文的文件名称在转移文档时经常会出现死链）。

## 死链产生的危害

死链会降低搜索引擎对网站的友好度。试着想一下如果搜索引擎蜘蛛来爬取你网站的时候，爬一个链接发现是死链接，爬一个链接又是死链接，发现的死链接多了，搜索引擎蜘蛛就会认为你这个网站的链接都是死链接，然后不再来爬取你网站的链接，没有搜索引擎蜘蛛来爬取，网站内容就不会被搜索引擎收录。

死链影响用户体验。当用户访问你网站的时候随便点一个链接出现无法访问，随便点一个链接又出现无法访问，用户就不会再继续访问，然后离开网站。原本有一个很好的用户，就因为死链的存在导致用户离开。

死链会造成网站排名下降，死链接会导致搜索引擎快照不更新，收录减少，使网站排名下降导致网站被降权。

![image-20210803104635778](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210803104635.png)

从上图可以看出，发现死链时要及时的向搜索引擎反馈，也就是提交给搜索引擎来判断后搜索引擎会从收录和索引里面清理掉这些死链。

对于我们的新博客站来说，手动的分析网站日志就可以轻松的解决这个问题了。但是对于上线 很久的老博客网站来说，这样的手动方式绝对是个噩梦了。

## 正文

下面给大家分享的这段代码就是可以自动记录百度搜索来的死链记录代码，这段代码需要放到主题根目录下的 `404.php` 里的，不是 **`function.php`** 里看清楚了。



```php
//WordPress 实现自动记录死链地址
if(is_404() && strpos($_SERVER['HTTP_USER_AGENT'],'Baiduspider') !== false){
        $file = @file("silian.txt");//silian.txt 就是在网站根目录的记录死链的文件
	$check = true;
	if(is_array($file) && !empty($file))
	foreach($file as &$f){
		if($f == home_url($_SERVER['REQUEST_URI'])."\n")
		$check = false;
	}
	if($check){
		$fp = fopen("silian.txt","a");
		flock($fp, LOCK_EX) ;
		fwrite($fp, home_url($_SERVER['REQUEST_URI'])."\n");
		flock($fp, LOCK_UN);
		fclose($fp);
	}
}
```

- 添加好上面代码后，记得把生成的`silian.txt`上传至百度站长平台，这样等待 24 小时以后你就可以在“死链提交”里看到这个文档里已经有死链了，如果没有的话，那么恭喜你，你的网站死链是 0，说明你整理得很好！！！

## 小技巧

在我们使用过程中，发现有时候我们会看到百度站长平台后台有错误提示，有个别链接地址不对，这时候我们可以额外再新建一个文本，把 `silian.txt` 所有的链接都复制到新的文本中，然后删除报错的链接，这样可以更快的删除已存在的死链也不影响新的死链。





























