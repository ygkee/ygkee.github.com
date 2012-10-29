---
layout: post
title: git push & pull using terminal
excerpt: git sshkey push & pull 
published: true
---

在terminal下，用git进行pull和push，一直要提示输入id和pws，

发现原因：

创建项目一直from github模式，

zendstudio开始只有https方式clone库，

使得.git/config文件的remote定义为了https方式

切换之~，又能使用得心的terminal做push和pull了

{% highlight ruby %}
[remote "original"]
	url = git@github.com:ygkee/71SRM_NEW.git 
	fetch = +refs/heads/*:refs/remotes/original/*
	pushurl = git@github.com:ygkee/71SRM_NEW.git
	push = HEAD:refs/for/refs/heads/master

{% endhighlight %}

