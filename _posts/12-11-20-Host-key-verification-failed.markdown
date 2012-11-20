---
layout: post
title: Host key verification failed.
excerpt: SSH连接的时候Host key verification failed. 
published: true
---

{% highlight ruby %}
[root@cache001 swftools-0.9.0]# ssh 106.187.1.1
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
05:25:84:ea:dd:92:8d:80:ce:ad:5b:79:58:fe:c9:42.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:10
RSA host key for 192.168.1.90 has changed and you have requested strict checking.
Host key verification failed.

{% endhighlight %}

解决方法：
{% highlight ruby %}
echo > ~/.ssh/known_hosts

{% endhighlight %}
或只清理服务器的信息


