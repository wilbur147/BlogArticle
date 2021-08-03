### 研究思路

用 CSS3 伪元素 :bfore 或 :after 添加一段扫光层代码；
用 transform:rotate(-45deg) 旋转 45 度（角度可自定义）；
CSS 控制位置和动画时间等。

### :before 选择器介绍

:before 选择器在被选元素的内容前面插入内容。
使用 content 属性来指定要插入的内容。
所有主流浏览器都支持:before选择器。
before在IE8中运行，必须声明 <!DOCTYPE> 。
:befor、:after是CSS的伪元素。

### 代码复制

绑定logo对应标签代码如下，效果可参考本网站logo（网站左上角）。

```scss
.header-logo {position:relative;float:left;margin-right:10px;padding:5px 0;overflow: hidden;}
.header-logo  a:before{
content:"";
position: absolute;
left: -665px;
top: -460px;
width: 200px;
height: 15px;
background-color: rgba(255,255,255,.5);
-webkit-transform: rotate(-45deg);
-moz-transform: rotate(-45deg);
-ms-transform: rotate(-45deg);
-o-transform: rotate(-45deg);
transform: rotate(-45deg);/*角度倾斜45*/
-webkit-animation: searchLights 1s ease-in 1s infinite;
-o-animation: searchLights 1s ease-in 1s infinite;
animation: searchLights 1s ease-in 1s infinite;/*光扫过去的时间，自己修改，可以加快*/1s ease-in表示扫过去时间
}
@-webkit-keyframes searchLights {
0% { left: -100px; top: 0; }
to { left: 120px; top: 100px; }
}
@-o-keyframes searchLights {
0% { left: -100px; top: 0; }
to { left: 120px; top: 100px; }
}
@-moz-keyframes searchLights {
0% { left: -100px; top: 0; }
to { left: 120px; top: 100px; }
}
@keyframes searchLights {
0% { left: -100px; top: 0; }
to { left: 120px; top: 100px; }
}
```

### 参数配置

**#header .logo**   根据每个网站style.css而定，可能为.logo、#logo等，可参考自己网站的css文件配置。

**#header .logo a:before**   一般网站logo都带有A标签跳转，所以在此设置a:before的CSS，即在A标签生效前执行该段CSS。

**overflow: hidden**   这个代码非常重要，可以限制扫光效果在logo所占的范围内，避免扫光效果溢出，影响美观。

**@keyframes**   规则可以控制扫光动画的起始位置和终止位置,以上的参数根据自己的 logo 的大小和布局进行调整即可（按F12可以修改参数自行调试）。

 

## 怎么使用

将以上CSS代码添加至主题根目录下的`style.css`底部保持即可，前台刷新本地浏览器缓存即可看到效果。

## 代码解释

第一行的`.header-logo`是确定特效的位置，各位可以自行修改，推荐指定一个更加准确的位置，例如：`.header-logo`   `.logo`



