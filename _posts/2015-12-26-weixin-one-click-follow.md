---
layout: post
title: 微信协议：实现一键关注公众号【尚未解决】
tags: 尚未解决 微信 一键关注
categories: 微信相关
---

## 缘起
用最便利的方式引导用户关注，无疑对运营微信公众平台有着极大的意义。网上查来的各种一键关注的方式都被标着**已失效**，一度以为只能止步于扫描二维码。直到遇到了**招商银行**！

他们做到了，像这样：

[http://cmbt.cn/MYQeF2](http://cmbt.cn/MYQeF2)

![招行一键关注示例](http://cl.ly/0n070i3N2N02/Image%202015-12-26%20at%2000.02.55.png)

然后，本来并没有打开微信，点了一下，微信神奇地打开了（前提是得用手机，而且装微信了）！而且直接到了招行公众号的关注界面（如果已经关注的话，则是直接进入公众号）！而且还收到了一条回复，特别的回复！居然和扫描带参数的二维码是一个效果！！！

于是震惊了，于是开始研究……


***
## 招行都做了啥？
chrome调试，查看Network

![chrome调试](http://cl.ly/243O0X221f0g/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202015-12-26%2000.12.25.png)

点击之后，先是图上红框的三个请求。第三个之后，由于不是在手机上打开，网页被重定向。

注意到第三个请求的url是
> weixin://dl/business/?ticket=t7c07ffeff492f56fe5f5d4d9c32bc0cf

以`weixin://`开头，貌似比较关键。

另外带了一个`ticket`参数，而且每次是不一样的。

所以可能是这样的：
* `weixin://`打开了微信APP
* `ticket`是一个即时生成的票据，标志了招行的公众号


***
## 微信协议weixin://
百度说，`weixin://`叫做微信协议，有一堆功能：
> weixin://dl/scan 扫一扫  
weixin://dl/feedback 反馈  
weixin://dl/moments 朋友圈  
weixin://dl/settings 设置  
weixin://dl/notifications 消息通知设置  
weixin://dl/chat 聊天设置  
weixin://dl/general 通用设置  
weixin://dl/officialaccounts 公众号  
weixin://dl/games 游戏  
weixin://dl/help 帮助  
weixin://dl/feedback 反馈  
weixin://dl/profile 个人信息  
weixin://dl/features 功能插件  
来源：[知乎某问答](http://www.zhihu.com/question/30616809?sort=created)

测试了几个，有效，然并卵…… 打开公众号那个是打开订阅号文件夹，都和一键关注相去甚远……

> ![方倍一键关注](http://cl.ly/023u27032205/Image%202015-12-26%20at%2000.56.50.png)  
来源：[方倍工作室-一键关注微信公众平台账号](http://www.cnblogs.com/txw1958/p/weixin41-follow-method.html)

iphone无效是真的……安卓是这样的：
![并木有卵用](http://cl.ly/2n3C3b1n382k/error.jpg)

**只有有效的才是王道，专心研究怎么用`weixin://dl/business`吧。**

***
## ticket是神马？
【】未完待续……