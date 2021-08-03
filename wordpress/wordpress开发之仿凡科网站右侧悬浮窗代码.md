最近有些朋友一直在问我的网站右侧悬浮框是如何实现的，其实代码的话我也是参考了钻芒博客的相关代码的，今天分享给大家。

 

可以自己自定义图标，在css更改图片链接即可（背景图标和鼠标hover浮动图标）。
如果要自己添加在css里写好就可以了。图标可以使用https://www.iconfont.cn
预览:

![](https://www.weiye.link/wp-content/uploads/2021/07/111.gif)

```php+HTML
<div class="wapnone fk_service">
	<ul>
		<li>
			<div class="fk_service_consult_cont1" style="display: none;"> <span class="fk_service_triangle"></span> 在线咨询 </div>
		</li>
		<li class="fk_service_box fk_service_consult">
			<div class="fk_service_consult_cont"> <span class="fk_service_triangle"></span>
				<div class="fk_service_consult_cont_top"> <span class="fk_service_hint"> <span class="fk_service_icon"></span>
						<span> 如遇问题，请联系站长 </span> </span> <span class="fk_service_button" onclick="window.open('https://wpa.qq.com/msgrd?v=3&uin=20838641&site=qq&menu=yes')">QQ联系</span>
					<span class="fk_service_button" onclick="window.open('https://mail.qq.com/cgi-bin/qm_share?t=qm_mailme&email=cpol@qq.com')">在线邮件</span>
				</div> <span class="fk_service_phone"> QQ 请注明来意 ：20838641 </span> <span class="fk_service_check_site"> <span class="fk_service_icon"></span>
					<span onclick="window.open('http://tool.zmki.cn')">更多：极客导航</span> </span>
			</div>
		</li>
		
		<li class="fk_service_box fk_service_qr">
			<div class="fk_service_qr_cont"> <span class="fk_service_triangle"></span>
				<div class="fk_service_qrimg"> <span class="fk_service_qrimg_site"></span> 微信公众号 </div>
				<div class="fk_service_qrtext"><span>奇思妙想 · 科技小新</span></div>
			</div>
		</li>
		<!-- 不需要图标的注释或删除即可 -->
		<li class="fk_service_box fk_service_ax" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_ax_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>

		<li class="fk_service_box fk_service_dh" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_dh_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>

		<li class="fk_service_box fk_service_jk" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_jk_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>

		<li class="fk_service_box fk_service_ws" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_ws_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>

		<li class="fk_service_box fk_service_sd" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_sd_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>



		<li class="fk_service_box fk_service_dz" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_dz_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>
		
		<li class="fk_service_box fk_service_feedback" onclick="window.open('https://tool.zmki.cn/index.php/t.html')">
			<div class="fk_service_feedback_cont"> <span class="fk_service_triangle"></span> 提交收录，站长收到留言后即刻处理！ </div>
		</li>
		
		<li class="fk_service_box fk_service_upward" onclick="FkService.fk_upWard();" style="display: block;">
			<div class="fk_service_upward_cont"> <span class="fk_service_triangle"></span> <span> 返回顶部 </span> </div>
		</li>
	</ul>
</div>
```

```css
/*<link rel="stylesheet" href="https://fe.faisys.com/fkService_1_0/css/fk_service.min.css?v=201908151449">*/
<style>
	.fk_service {
		max-height: 232px;
		position: fixed;
		right: 10px;
		top: 40%;
		/* 垂直位置 */
		font-family: "寰蒋闆呴粦";
		font-size: 14px;
		color: #243558;
		z-index: 10000
	}


	.fk_service ul {
		margin: 0;
		padding: 0;
		position: absolute;
		right: 0
	}

	.fk_service li {
		list-style-type: none
	}

	.fk_service li>div {
		box-sizing: border-box;
		box-shadow: 0 0 9px 0 rgba(0, 0, 0, 0.1)
	}

	.fk_service_box {
		width: 40px;
		height: 40px;
		background: #fff;
		margin-bottom: 10px;
		border-radius: 4px;
		box-sizing: border-box;
		box-shadow: 0 0 9px 0 rgba(0, 0, 0, 0.1)
	}

	.fk_service_triangle {
		top: 12px;
		right: -11px;
		position: absolute;
		border-top: 7px solid transparent;
		border-bottom: 7px solid transparent;
		border-left: 11px solid #e1e6ec;
		z-index: 1010
	}

	.fk_service_triangle:after {
		content: "\20";
		top: -6px;
		right: 1px;
		position: absolute;
		border-top: 6px solid transparent;
		border-bottom: 6px solid transparent;
		border-left: 10px solid #fff;
		z-index: 1000
	}

	.fk_service_triangle:before {
		content: "\20";
		width: 80px;
		height: 45px;
		top: -20px;
		right: -52px;
		position: absolute;
		background: rgba(0, 0, 0, 0)
	}

	@keyframes fade-in {
		0% {
			opacity: .4;
			right: 82px
		}

		100% {
			opacity: 1;
			right: 62px
		}
	}

	.fk_service_consult {
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -366px -16px #fff
	}

	.fk_service_consult:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -410px -16px #4f7cfc
	}

	.fk_service_consult:hover .fk_service_consult_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}

	.fk_service_consult_cont {
		width: 200px;
		min-height: 210px;
		max-height: 268px;
		border-radius: 3px;
		background: #fff;
		right: 62px;
		position: absolute;
		text-align: center;
		border: 1px solid #e1e6ec;
		display: none;
		opacity: 0
	}

	.fk_service_consult_cont1 {
		width: 70px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}

	.fk_service_consult_cont1 .fk_service_triangle:before {
		width: 0 !important
	}

	.fk_service_consult_cont>.fk_service_triangle:after {
		border-left: 10px solid #f6f8fb !important
	}

	.fk_service_consult_cont span {
		float: left
	}

	.fk_service_consult_cont_top {
		width: 100%;
		height: 157px;
		background: #f6f8fb;
		border-radius: 3px;
		border-bottom: 1px solid #eef2f8
	}

	.fk_service_hint {
		width: 100%;
		height: 40px;
		line-height: 40px;
		font-size: 12px;
		color: #9aa8c2;
		text-align: center
	}

	.fk_service_hint>.fk_service_icon {
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -460px -25px;
		width: 15px;
		height: 15px;
		margin: 13px 2px 0 18px
	}

	.fk_service_button {
		width: 160px;
		height: 38px;
		line-height: 38px;
		background: #4f7cfc;
		border-radius: 18px;
		text-align: center;
		color: #fff;
		margin: 5px 0 10px 20px;
		cursor: pointer
	}

	.fk_service_button:hover {
		background: #618aff
	}

	.fk_service_phone {
		width: 100%;
		height: 53px;
		line-height: 53px;
		font-size: 14px;
		text-align: center
	}

	.fk_service_check_site {
		width: 100%;
		height: 48px;
		line-height: 48px;
		color: #3b6bf4;
		border-top: 1px solid #eaeef5;
		cursor: pointer
	}

	.fk_service_check_site>.fk_service_icon {
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -461px -75px;
		width: 20px;
		height: 20px;
		margin: 15px 2px 0 45px
	}

	.fk_service_feedback {
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -363px -64px #fff
	}

	.fk_service_feedback:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -407px -64px #4f7cfc;
		cursor: pointer
	}

	.fk_service_feedback:hover .fk_service_feedback_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}

	.fk_service_feedback_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}


	.fk_service_qr {
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -365px -113px #fff
	}

	.fk_service_qr:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -409px -113px #4f7cfc
	}

	.fk_service_qr:hover .fk_service_qr_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}

	.fk_service_qr_cont {
		width: 143px;
		height: 202px;
		border-radius: 3px;
		background: #fff;
		right: 62px;
		position: absolute;
		text-align: center;
		border: 1px solid #e1e6ec;
		background-color: #f6f8fb;
		display: none;
		opacity: 0
	}

	.fk_service_qr_cont>.fk_service_triangle:after {
		border-left: 10px solid #f6f8fb !important
	}

	.fk_service_qr_cont>.fk_service_qrimg {
		width: 100%;
		height: 164px;
		float: left
	}

	.fk_service_qrimg_site {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -41px -26px
	}

	.fk_service_qrimg_hd {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -198px -26px
	}

	.fk_service_qrimg_wxast {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(../image/fk_service.png?v=201905151200) no-repeat -198px -328px
	}

	.fk_service_qrimg_flyer {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -41px -177px
	}

	.fk_service_qrimg_wxapp {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -198px -177px
	}

	.fk_service_qrimg_fkmall {
		width: 119px;
		height: 119px;
		float: left;
		margin: 12px 12px 5px 12px;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -41px -326px
	}

	.fk_service_qr_cont>.fk_service_qrtext {
		width: 100%;
		height: 35px;
		font-size: 12px;
		color: #7b89a6;
		background-color: #fff;
		float: left;
		bottom: 0;
		display: table
	}

	.fk_service_qr_cont>.fk_service_qrtext>span {
		display: table-cell;
		vertical-align: middle
	}

	.fk_service_upward {
		display: none;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -363px -159px #fff
	}

	.fk_service_upward:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20190827-5d652476ab305.png) no-repeat -407px -159px #4f7cfc;
		cursor: pointer
	}

	.fk_service_upward:hover .fk_service_upward_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}

	.fk_service_upward_cont {
		width: 84px;
		height: 40px;
		line-height: 40px;
		border-radius: 3px;
		background: #fff;
		right: 62px;
		position: absolute;
		text-align: center;
		border: 1px solid #e1e6ec;
		display: none;
		opacity: 0
	}

	.fk_service_upward_cont span {
		font-size: 14px
	}
	/* ----------------------------------------------------------------------- */
	/* 新增图标->zmki 开始*/
	.fk_service_jk {
		/* 前景图标 */
		background: url(https://a-oss.zmki.cn/2019/20191218-c9feba3074fcf.png) no-repeat center center #fff;
		background-size: 40%40%;
	}
	
	.fk_service_jk:hover {
		border: 0;
		/* 鼠标悬浮图标 */
		background: url(https://a-oss.zmki.cn/2019/20191218-9e8acd5341cdc.png) no-repeat center center #4f7cfc;
		background-size: 40%40%;
		cursor: pointer
	}
	
	.fk_service_jk:hover .fk_service_jk_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_jk_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/* 新增图标->zmki 结束*/
	
	/* 新增图标->zmki 开始*/
	.fk_service_ws {
		background: url(https://a-oss.zmki.cn/2019/20191218-61b4baac98ee7.png) no-repeat center center #fff;
		background-size: 50%50%;
	}
	
	.fk_service_ws:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20191218-8ded04c01bb3c.png) no-repeat center center #4f7cfc;
		background-size: 50%50%;
		cursor: pointer
	}
	
	.fk_service_ws:hover .fk_service_ws_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_ws_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/* 新增图标->zmki 结束*/
	
	
	/* 闪电 新增图标->zmki 开始*/
	.fk_service_sd {
		background: url(https://a-oss.zmki.cn/2019/20191218-94664bd399372.png) no-repeat center center #fff;
		background-size: 50%50%;
	}
	
	.fk_service_sd:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20191218-fab840acee28b.png) no-repeat center center #4f7cfc;
		background-size: 50%50%;
		cursor: pointer
	}
	
	.fk_service_sd:hover .fk_service_sd_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_sd_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/*闪电 新增图标->zmki 结束*/
	
	/* 导航 新增图标->zmki 开始*/
	.fk_service_dh {
		background: url(https://a-oss.zmki.cn/2019/20191218-711bcdc875f32.png) no-repeat center center #fff;
		background-size: 60%60%;
	}
	
	.fk_service_dh:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20191218-8d9cf4c72a239.png) no-repeat center center #4f7cfc;
		background-size: 60%60%;
		cursor: pointer
	}
	
	.fk_service_dh:hover .fk_service_dh_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_dh_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/*导航 新增图标->zmki 结束*/
	
	/* 爱心 新增图标->zmki 开始*/
	.fk_service_ax {
		background: url(https://a-oss.zmki.cn/2019/20191218-bf1792e790a39.png) no-repeat center center #fff;
		background-size: 40%40%;
	}
	
	.fk_service_ax:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20191218-f379809ce7aef.png) no-repeat center center #4f7cfc;
		background-size: 40%40%;
		cursor: pointer
	}
	
	.fk_service_ax:hover .fk_service_ax_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_ax_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/*爱心 新增图标->zmki 结束*/
	
	/* 点赞 新增图标->zmki 开始*/
	.fk_service_dz {
		background: url(https://a-oss.zmki.cn/2019/20191218-3d077e8df0bf0.png) no-repeat center center #fff;
		background-size: 50%50%;
	}
	
	.fk_service_dz:hover {
		border: 0;
		background: url(https://a-oss.zmki.cn/2019/20191218-986a9393f3e9e.png) no-repeat center center #4f7cfc;
		background-size: 50%50%;
		cursor: pointer
	}
	
	.fk_service_dz:hover .fk_service_dz_cont {
		display: block;
		opacity: 1;
		transition: linear .2s;
		animation-name: fade-in;
		animation-duration: .3s;
		animation-iteration-count: 1;
		animation-delay: 0s
	}
	
	.fk_service_dz_cont {
		width: 264px;
		height: 40px;
		line-height: 40px;
		background: #fff;
		border-radius: 5px;
		right: 62px;
		text-align: center;
		position: absolute;
		display: none;
		border: 1px solid #e1e6ec
	}
	
	/*点赞 新增图标->zmki 结束*/

        /* 手机端自动隐藏 开始 */
	@media screen and (max-width: 1221px) { .wapnone{display:none; }
	}
	/* 手机端自动隐藏 结束 */
</style>
```

