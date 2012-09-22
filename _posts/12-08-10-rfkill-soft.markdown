---
layout: post
title: wlan无法启动
excerpt: soft blocked AND hard blocked。
published: true
---

昨晚无线网络不稳定，随手把无线关了

早晨发现启动不了，指示灯亮不起来

{% highlight ruby %}
#ifconfig wlan0 up
{% endhighlight %}

出现错误RF-kill

{% highlight ruby %}
#rfkill list
{% endhighlight %}

发现soft blocked：yes

于是

{% highlight ruby %}
#rfkill unblocked all
{% endhighlight %}

再开启，指示灯亮起来了
