---
layout: post
title: 你使用最多的10条命令是什么？
excerpt: 打印出前十名你使用最多的命令 
published: true
---

{% highlight ruby %}
history | awk '{CMD[$2]++;count++;} END { for (a in CMD )print CMD[ a ]" " CMD[ a ]/count*100 "% " a }' | grep -v "./" | column -c3 -s " " -t |sort -nr | nl | head -n10 

{% endhighlight %}

