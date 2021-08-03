## 前言

辛辛苦苦写的教程，不想让人很容易的就复制走，办法还是有的。

关于如何防止别人偷到自己的文章，自己的wordpress主题源码等等方法，数不胜数，然而防不胜防。

其实，别人要想搞你，怎么都能搞到。没什么卵用。

今天给大家一段，防君子不防小人的网页禁止右键和F12的js

## WP防扒教程

把下面的代码放入wordpress主题文件footer.php最下方前面即可，不多解释，懂的人一看就懂，不懂的解释了他也不懂。我们只是做了个测试，随机取消了限制，知识就是拿来分享的，不过，也尊重下之前分享的人！

![image-20210730144157619](https://cdn.jsdelivr.net/gh/wilbur147/cdnPictureBed/article/20210730144158.png)



**直接复制代码放到上图中第四步位置即可，有两种可自行选择**

```javascript
// 网页禁止右键和F12和Ctrl + S（保存）
document.onkeydown=function(){
    var e = window.event||arguments[0];
    if(e.keyCode==123){
            return false;
    }else if((e.ctrlKey)&&(e.shiftKey)&&(e.keyCode==73)){
            return false;
    }else if((e.ctrlKey)&&(e.keyCode==85)){
            return false;
    }else if((e.ctrlKey)&&(e.keyCode==83)){
           return false;
    }
}
document.oncontextmenu=function(){
    return false;
}
```

```javascript
// 网页禁止 左/右键 和F12和Ctrl + S（保存）
<script language=javascript>      
    function stop(){  
        return false;   
    }   
    document.oncontextmenu=stop;   
    document.onkeydown =document.onkeyup = document.onkeypress=function(){   
            return(false);   
    }  
    document.onselectstart=new Function('event.returnValue=false;');  
</script>
```

