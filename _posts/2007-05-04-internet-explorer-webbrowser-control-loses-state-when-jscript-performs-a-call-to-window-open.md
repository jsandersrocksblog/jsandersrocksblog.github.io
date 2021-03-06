Session state for a web site is often stored in cookies.&nbsp; If you use the WebBrowser control in an program and the target website responds to an action with a call to _Window.Open_, then mysteriously the cookies for that site are not transmitted with the request.

**Cause:&nbsp;  
** _Window.Open_ creates a window using the IExplore.exe process since it does not have a parent window handle.&nbsp; You cannot share cookies across processes.

**Correct methods to use:**

**  
1.&nbsp; Change the jscript**

You can _change the jscript_ to use the parent application window handle and that will host that window in your application’s process.&nbsp; 

function MyShowModal()  
{  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; var args = new Object;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; args.window = window;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; showModalDialog(&#8220;modal.asp&#8221;, args);  
}

**2.&nbsp; Your application can host the New Window**

If your application goes to web sites that are not under your control, you handle the _NewWindow2_ event from the browser control as covered in these KB articles: 

How To Use the WebBrowser Control NewWindow2 Event&nbsp;&nbsp;  
<http://support.microsoft.com/kb/184876/EN-US/>

How to use the WebBrowser control NewWindow2 event in Visual Basic .NET .Net Version: <http://support.microsoft.com/kb/311282/EN-US/>

How to use the WebBrowser control NewWindow2 event in Visual C# .NET or in Visual C# 2005  
<http://support.microsoft.com/kb/815714>

Related article:  
How to maintain the ASP.NET session state  
<http://support.microsoft.com/kb/932474><p mce_keep="true">&nbsp;</p>