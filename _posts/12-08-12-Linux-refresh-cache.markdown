---
layout: post
title: Linux释放内存
excerpt: 及时释放被buffers，cached等占去的内存，避免被占内存释放缓慢。
published: true
---

{% highlight ruby %}
root@ubuntu:/home/kee# free -m 
                  total       used       free     shared    buffers     cached 
    Mem:          3449       2123       1325          0        576        777 
    -/+ buffers/cache:        769       2680 
    Swap:          254          0        254 
{% endhighlight %}

 被buffers,cached等占去的内存，释放的很慢，导致可用内存不够用。
 解决方法：

1，vim free.sh建个脚本

{% highlight ruby %}
free -m |grep -i mem |awk '{if($4 < 300){ printf("3") > "/proc/sys/vm/drop_caches"}}'; 
{% endhighlight %}

2，加到crontab中去

{% highlight ruby %}
 sudo su

crontab -e

    */05 * * * * /home/kee/free.sh 
{% endhighlight %}

 注意：

1,crontab要以root的权限去执行，普通用户是没有drop_caches写的权限的。

2,根据系统的不同，*/05 * * * * /home/kee/free.sh，每隔5分钟执行一次，有的写法是*/5 * * * * /home/kee/free.sh
