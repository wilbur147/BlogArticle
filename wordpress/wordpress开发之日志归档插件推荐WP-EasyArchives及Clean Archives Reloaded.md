## 前言

最近有很多小伙伴留言跟我说，这个文章文档是怎么实现的，wordpress自带的没有这个功能，其实很简单，我们只需要用一个插件就可以实现

## 插件生成归档

# WP-EasyArchives文章归档插件

**`WP-EasyArchives`**能在定制页面显示对搜索引擎友好的树形结构存档列表。

该插件支持过滤功能, 可以按文章作者和月份进行筛选显示; 它使用缓存处理, 执行速度快; 对代码结构进行过优化, 对搜索引擎十分友好，看下效果图：

![image-20210802162801897](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802162801.png)



点我跳转更直观参考： [文章归档](https://www.weiye.link/archive)

### `主题安装及配置`

目前最新版本为：3.1.2，可以直接通过WordPress的插件中搜索安装，配置的选项很人性化，至少我觉得很不错，配置界面如下：

![image-20210802162911664](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802162911.png)

#### 一、激活插件后，进入主题的根目录复制一份page.php改名称改为archives.php

![image-20210802151720666](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802151720.png)



#### 二、编辑archives.php，在头部添加

```php
<?php
/*
Template Name: 文章归档
*/
?>
```

示例图：

![image-20210802163137170](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802163137.png)



#### 三、添加 `<?php wp_easyarchives(); ?>`

**正常主题可直接在 `archive.php`**文件中找到类似 `<?php the_content(); ?>` 带有 `content` 内容字段的直接替换成：

```php
<?php wp_easyarchives(); ?>
```

**本网站主题** [CorePress](https://www.lovestu.com/corepress.html) **配置：**

- 进入主题 `CorePrss -> component` 目录，找到并复制 `post-page.php`文件，重命名 `archives-page.php`

- 编辑 `archives-page.php`找到  `<?php the_content(); ?>` 直接替换成：

```php
<?php
    the_content();
	wp_easyarchives();
?>
```

- 然后再进入主题根目录找到`archive.php`编辑，把文中所有的 `get_template_part('component/post-page');`替换成

`get_template_part('component/archives-page');`即可



#### 三、新建页面，选择 `文章归档模板`

![image-20210802152533866](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802152533.png)



#### 四、调节CSS

将代码加到插件 – 插件编辑器 – WP-EasyArchives – CSS文件的最后面，保存文件，刷新后就能看到效果了，完整的CSS如下：

```css
#ea-filter {height: 50px;}
#ea-filter select{padding: 6px 2px;}
#ea-filter input{visibility:visible;padding:5px 12px;margin-right:10px;border:1px solid #080;border-bottom-color:#2B562B;border-radius:3px;font-size:12px;font-weight:700;cursor:pointer;text-decoration:none;color:#FFF;text-shadow:0 1px 0 #5d4113;background:#080;background:-webkit-gradient(linear, left top, left bottom, from(#C3E5C5), color-stop(0.05, #54B059), to(#080));background:-moz-linear-gradient(top, #C3E5C5, #54B059 5%, #080);background:-o-linear-gradient(top, #C3E5C5, #54B059 5%, #080);background:linear-gradient(to bottom, #C3E5C5, #54B059 5%, #080);}
#ea-filter input:hover{border-bottom-color:#3A693A;background:#44A049;background:-webkit-gradient(linear, left top, left bottom, from(#FFF), color-stop(0.05, #63BC68), to(#44A049));background:-moz-linear-gradient(top, #FFF, #63BC68 5%, #44A049);background:-o-linear-gradient(top, #FFF, #63BC68 5%, #44A049);background:linear-gradient(to bottom, #FFF, #63BC68 5%, #44A049);}
```

按照下图操作即可：

![image-20210802164647078](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802164647.png)



# Clean Archives Reloaded文章归档插件

Clean Archives Reloaded插件可以实现页面调用wordpress博客所有文章列表，通过wordpress年月归档分类列表显示，该插件使用javascript实现折叠效果显示文章列表，不会把页面拉得老长，保证了页面美观。该插件使用简单，而且作者表示该插件不会影响博客服务器和数据库。

**与上面插件对比没有过滤功能，但是配置超级无敌简单**

### `安装及配置`

- 同样首先在插件市场下载该插件 `Clean Archives Reloaded` 安装并启动

- 然后直接新建一个页面 内容输入 `[cleanarchivesreloaded]`即可效果都差不多

```html
[cleanarchivesreloaded]
```

![image-20210802165344594](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802165344.png)





**参考示例图：**

![image-20210802165458736](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210802165458.png)





