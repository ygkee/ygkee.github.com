---
layout: post
title: L2TP通过network-manager插件连接 
excerpt: Network manager插件来管理xl2tp服务了。安装完成后用户即可以在network-manager中添加L2TP VPN连接。
published: true
---

以 Ubuntu 为例简要介绍安装过程，其他发行版可自行编译，也可使用针对其他发行版的软件包。注：该软件包名为 network-manager-l2tp-gnome ，可能只支持gnome环境。

1. 添加PPA

{% highlight ruby %}
sudo apt-add-repository ppa:seriy-pr/network-manager-l2tp  
{% endhighlight %}

2. 刷新软件包缓存

{% highlight ruby %}
sudo apt-get update
{% endhighlight %}

3. 安装network-manager-l2tp

{% highlight ruby %}
sudo apt-get install network-manager-l2tp-gnome
{% endhighlight %}
安装完之后不要忘记运行以下命令
{% highlight ruby %}
sudo service xl2tpd stop
sudo update-rc.d xl2tpd disable
{% endhighlight %}

这样就可以由插件来管理xl2tp服务了。安装完成后用户即可以在network-manager中添加L2TP VPN连接，添加过程不再赘述。注意，如果连接VPN时出现错误：“没有合法的 VPN Secret”，可能是因为和其他正在运行的VPN客户端冲突所致，重启一次计算机即可解决。 
