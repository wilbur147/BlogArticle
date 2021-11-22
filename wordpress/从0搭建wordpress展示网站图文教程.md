## 正文

以前没接触过网站时总感觉网站建设很复杂，其实，如果是要求不高的个人网站，搭建起来其实并不难。今天就给大家分享一篇超简单的wordpress网站安装教程，告诉大家如何快速简单的搭建一个基于wordpress的个人网站。

![wordpress](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122115033.png)

首先，搭建一个个人网站需要三个必备的因素，即：域名、服务器（空间）、程序。

**域名、服务器（空间）**

域名和服务器空间是在搭建网站前期需要准备的东西，同时，在国内购买服务器空间的，还需要考虑“网站备案”（国外的不用，不过速度是个问题）。域名注册好了，空间也购买好了，然后还需要对服务器IP作DNS解析服务。

简单总结起来搭建网站前期要做好的准备工作：域名-空间-网站备案-DNS解析。

域名和网站空间都是需要付费购买，网站备案（免费）一般的服务器销售商会附带提供（但依然要用户自己提供相关的资料）、DNS解析也可以使用免费的DNSPOD。

附：虽说网上也许能找到免费域名或者免费空间，不过请要相信，免费的永远是最贵的。试想一下，当你辛辛苦苦搭建了一个网站，结果，昨天还在用，今天就不能用了，所有的一切就都白费了，毕竟免费的东西大多都是没有保障的。以还是建议大家购买收费域名以及收费空间。

域名可以考虑万网或者gooday注册，空间可以考虑[阿里云](https://www.aliyun.com/daily-act/ecs/activity_selection?userCode=2n8fcnsj)，**新人可享轻量服务器一年只需 `43`元，附上链接**[阿里云新人优惠](https://www.aliyun.com/activity/1111/newuser1st?userCode=2n8fcnsj)

当然，域名和空间还没准备都没关系，我们可以先在本地掌握网站程序的安装方法，熟悉之后再运用到服务器上即可，基本上是大同小异。

**建站程序**

网站程序同样有免费的和收费的、免费的如wordpress、dedecms、discuz等等。

对于个人网站推荐wordpress就可以了，毕竟wordpress是目前全球使用最多的博客程序，网络上还有海量的wordpress主题、wordpress插件下载（其实还有一个原因，毕竟wordpress用户多，有问题也容易在网上找到解决方案）。

选中了wordpress作为建站程序，那我们就需要为服务器安装PHP运行环境（wordpress属PHP程序）。

一般来说PHP运行环境需要安装以下几个组件：

- Apache（阿帕奇）Web服务器软件
- MySQL（小型关系型数据库管理系统）
- PHP（php语言的编译环境）
- phpmyadmin（管理MYSQL的）
- Zend（提高PHP执行速度）

搭建PHP运行环境，对于新手来说是个难题，对于老手来说也是一件烦琐的事，所以建议是直接安装网上现成的PHP环境集成包；

服务器是linux的可以选择：比如lnmp一键安装包、LAMP一键安装包、或者带管理面板的如WDCP、宝塔面板等

服务器是windows的可以选择：phpstudy、Visual NMP/Visual AMP、Xampp等等。

### 主机空间要求

要运行 WordPress，主机空间需满足以下条件。不过现在网络上的空间基本都可以，而且还让你随意定制Php和Mysql版本，至于空间和数据库大小就更不用说了，一句话，有钱就可以任性。

- **环境 ：**Linux+Nginx ( Apache )+Mysql+Php
- **php :** 5.6 +
- **Mysql :** 5.0 +
- **空间 ：**100m+
- **数据库大小 ：**20m+

对于最新版Wordpress，官方推荐运行软件版本：**php7.3和MySQL 5.6**



**本文就主要介绍一下linux系统宝塔面版安装wordpress教程**

## 宝塔面板安装

安装宝塔，在我的上一篇文章已经详细介绍了如何安装，[Linux安装宝塔面板图文教程 - 翔基博客 (weiye.link)](https://www.weiye.link/326.html)

## 新建网站

在我们安装好的宝塔面板，选择网站，新建站点，输入自己要创建的站点信息

![image-20211122123658729](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122123705.png)



进入站点，可以把默认生成的文件都删除掉

![image-20211122123953951](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122123954.png)

## WordPress下载

首先下载最新版的Wordpress，[下载 | WordPress.org ](https://cn.wordpress.org/download/)

下载完成后，直接把下载的压缩包上传至前面创建的站点目录中，**宝塔面板支持直接拖放本地文件至目录**

![image-20211122124238921](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122124239.png)



然后直接右键解压，解压完成后，**需要去掉 wordpress 这一层目录**

![image-20211122124455935](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122124456.png)

## IP配置（二选一）

宝塔面板直接点击前面创建的网站站点设置，选择 `配置文件` 即可配置nginx

nginx配置规则：

```bash
server
{
    listen 1001;
    server_name 113.23.98.169;
    index index.php index.html index.htm default.php default.htm default.html;
    root /www/wwwroot/www.weiye.link;
    
    #SSL-START SSL相关配置，请勿删除或修改下一行带注释的404规则
    #error_page 404/404.html;
    #SSL-END
    
    #ERROR-PAGE-START  错误页配置，可以注释、删除或修改
    #error_page 404 /404.html;
    #error_page 502 /502.html;
    #ERROR-PAGE-END
    
    #PHP-INFO-START  PHP引用配置，可以注释或修改
    include enable-php-74.conf;
    #PHP-INFO-END
    
    #REWRITE-START URL重写规则引用,修改后将导致面板设置的伪静态规则失效
    include /www/server/panel/vhost/rewrite/www.weiye.link.conf;
    #REWRITE-END
    
    #禁止访问的文件或目录
    location ~ ^/(\.user.ini|\.htaccess|\.git|\.svn|\.project|LICENSE|README.md)
    {
        return 404;
    }
    
    #一键申请SSL证书验证目录相关设置
    location ~ \.well-known{
        allow all;
    }
    
    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        expires      30d;
        error_log /dev/null;
        access_log /dev/null;
    }
    
    location ~ .*\.(js|css)?$
    {
        expires      12h;
        error_log /dev/null;
        access_log /dev/null; 
    }
    access_log  /www/wwwlogs/www.weiye.link.log;
    error_log  /www/wwwlogs/www.weiye.link.error.log;
}
```

> `listen`设置：1001 根据自己的选择设置
>
> `server_name` 设置：服务器公网IP

## 域名配置（二选一）

> 如果你只需要IP访问的话，这一步就省略掉，但是你得修改站点Nginx的配置文件中的 server_name 属性为你的 服务器公网IP地址。 域名列表地址：https://dc.console.aliyun.com/next/index?accounttraceid=0050f9ab236f4896866130327de9264fubpf#/domain/list/all-domain 访问域名列表地址前，你需要进行阿里云账号登录。

### 进入解析页面

![image-20211122131402075](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122131402.png)

### 添加解析记录

![image-20211122131610184](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122131610.png)

填写完毕之后，点击“确认”保存，10分钟之后就会生效。你就可以用 二级域名来访问你创建的站点了。

## 安装WordPress

域名直接访问 [www.weiye.link](https://www.weiye.link) 开始安装WordPress

IP直接访问 [http://公网IP:端口](http://公网IP:端口)

![image-20211122141458203](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122141458.png)



#### 1、填写数据库相关信息

![image-20211122141729260](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122141729.png)

#### 2、填写网站相关信息

![image-20211122142105646](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122142105.png)



点击安装，安装成功

![image-20211122142217094](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122142217.png)



点击登录，输入刚才安装时填写的用户名及密码就可以了，登录成功就进入到了wordpress的仪表盘当中

![image-20211122142340942](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122142341.png)



## 访问站点

安装成功后，再访问 [www.weiye.link](www.weiye.link) 域名方式或者 http://IP:端口 IP方式就可以直接访问站点了

后台管理： [www.weiye.link/wp-admin/](www.weiye.link) 或者  http://IP:端口/wp-admin

![image-20211122143542573](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20211122143542.png)

这是 wordpress 默认的一个主题

## 宝塔面板建站总结

好了，文章到此结束了，其实呢，宝塔面板搭建其它开源的，免费的建站程序都是万变不离其宗，本质都是一样的，就是在创建站点之后的根目录下上传 网站安装程序，然后解压，然后完成修改配置文件和绑定域名的两个细节步骤，就可以在线安装网站程序了。写的这么详细，小白也能看懂吧。有不懂的，可以网站留言问我。





























