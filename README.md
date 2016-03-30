# 微信相框

@(微信相框)

**微信相框** 是一款可以和微信、手机相册同步的电子数码相框。功能方面，通过微信扫码绑定相框之后，可以通过一个名为“微信相框”的公众号来管理自己的相册，用户可将照片、描述发送给公众号，然后会自动上传到微信相框里。

特点概述：
 
- **微信云端** ：用户扫码绑定相框后照片直传微信云端服务器；
- **安全可靠** ：用户照片存放云端和本地存储不会造成隐私泄露；
- **操作简单，微信直达** ：扫码即可绑定，一键发送到相框。

-------------------

[TOC]

## 产品介绍

> 微信相框的英文名为“moment”，翻译过来就是“瞬间”、“片刻”的意思，这也正是微信相框所要表达的意思，随时随地可以将照片分享到微信相框上来，在机身屏幕的贴纸上也写着“分享，每时每刻”的字样。

###关于诉求
>以相框为纽带，增进子女和父母，长辈之间的沟通，用照片传递感情交流，通过微信这个平台，将照片传送给家人。

### 功能配置
*  操作系统：   Android4.4
*  LCD分辨率： 1024*768; 4:3（比例）
*  CPU处理器： A7双核处理器
*  RAM： 512MB
*  触摸： 电容式触摸
*  WIFI： 内置
*  麦克风： 内置
*  电池：锂电池3.7V/3000mAH
*  产品尺寸：197*143*50.6mm
*  产品重量： 0.58kg
*  内存： 8GB，用户可用空间不少于5GB（不少于5000张照片存储）


### 使用方法
1. 扫描相框的二维码即可绑定相框公众号
2. 拍照后将相片发送到公众号即可上传至相框
3. 相框展现照片，轮播形式等播放模式可通过设置界面进行设置



## 开发调试相关

### adb 调试
**微信相框** 由于外包装不提供usb数据接口，故无法完成相框与电脑连接进行adb调试。
>**注意：** 需要将外包装进行拆除才可以连接数据接口与电脑相连

### 调试关键点
**微信相框** 调试需要注意一下几点：
1. 开启设备蓝牙功能
	```
	@RequestMapping(LOGIN)
    public String login(HttpServletRequest request, HttpServletResponse response) throws BusinessException {
        HttpRequestInfo requestInfo = new HttpRequestInfo(request);
        String eqAccount = requestInfo.getParameter("eqAccount", "admin");
        String eqPasswd = requestInfo.getParameter("eqPasswd", "");
        String returnUrl = "redirect:"+ requestInfo.getParameter("returnUrl", INDEX);
		User user = adminSdk.login(eqAccount,eqPasswd);
		if (user == null) {
            throw new BusinessException("user.login.username.not.exist");
        }
		HttpResponseUtil.setCookie(response, CookieConfig.COOKIE_ADMIN_USER_ID, user.getId().toString(), WebSiteEnum.ROOT.getUrl(), "/",                                 CookieConfig.expireOneDaySeconds);
		HttpResponseUtil.setCookie(response, CookieConfig.COOKIE_ADMIN_VERIFY_CODE, user.getVerify(), WebSiteEnum.ROOT.getUrl(), "/",                                    CookieConfig.expireOneDaySeconds);
		return returnUrl;
    }
	```
2. 	重启设备
3. 	至此相框已打开了蓝牙的功能可以进行相关操作
>**注意：** 相关文件会以邮件附件形式发送


## 反馈与建议
- 电话：18688483205
- 微信：[jzkangta]
- 邮箱：<wangjun@frogshealth.com>

---------
感谢阅读这份文档，如有疑问，请与我联系。


