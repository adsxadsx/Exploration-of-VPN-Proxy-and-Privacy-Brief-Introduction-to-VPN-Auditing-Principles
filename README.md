# Exploration-of-VPN-Proxy-and-Privacy-Brief-Introduction-to-VPN-Auditing-Principles
VPN机场代理与隐私的一些探索,  以及VPN机场审计原理简单介绍

首先是关于机场的一些简单介绍：
假定我们使用https访问twitter。
使用机场之后,  用户访问网址，客户端到 vps 使用加密，vps 再访问 twitter 。
但是 机场 vps 端仍然可以看到你的访问域名。
因为twitter域名的dns解析是由机场端的VPS负责, 甚至VPS端到twitter之间访问是否加密也不可知。


很多人一位自己的机子上有https搞个dns over https就万事大吉, 这是万万不可能的。


可以做一个简单的实验, 浏览器设置安全dns开启doh后访问 1.1.1.1/help检查doh加密情况。
再浏览器设置安全dns开启doh,  通过机场访问后访问 1.1.1.1/help检查doh加密情况。
你会惊喜的发现, 你的doh没了。

这就是为什么机场能通过审计来控制你的上网行为, 包括且不限于限制访问某些网站, 在youtube等平台放标评论, 等等等。

# ---------------------------------------------------------

怎么解决这一问题呢？ 介绍一个一东西叫加密代理

以下面的配置说明，它的工作原理是：
来源：https://toutyrater.github.io/advanced/outboundproxy.html、

1基本代理转发
使代理转发可以实现由一个Shadowsocks服务器或者V2Ray(VMess)服务器来中转你的网络流量，并且
中转服务器只能到你加密的数据而不知道原始的数据是什么。
以下面的配置说，它的工作原理是

![image](https://github.com/adsxadsx/Exploration-of-VPN-Proxy-and-Privacy-Brief-Introduction-to-VPN-Auditing-Principles/assets/118355125/66ba75ad-46f3-49f5-bfce-73fcc6a56a92)


介绍到此为止, 具体实现方式搜 cloudflare 、warp nekoray链式代理。

