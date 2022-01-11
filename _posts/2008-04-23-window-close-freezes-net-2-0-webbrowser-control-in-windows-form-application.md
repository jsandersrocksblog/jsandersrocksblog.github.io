In the spirit of my post: <a class="" title="How To: Close the Form hosting the WebBrowser control when scripting calls window.close in the .Net Framework version 2.0" href="http://blogs.msdn.com/jpsanders/archive/2007/05/25/how-to-close-the-form-hosting-the-webbrowser-control-when-scripting-calls-window-close-in-the-net-framework-version-2-0.aspx" target=\_blank mce\_href="http://blogs.msdn.com/jpsanders/archive/2007/05/25/how-to-close-the-form-hosting-the-webbrowser-control-when-scripting-calls-window-close-in-the-net-framework-version-2-0.aspx">How To: Close the Form hosting the WebBrowser control when scripting calls window.close in the .Net Framework version 2.0</a>&nbsp;the .NET 2.0 WebBrowser control has no control over the close events like WindowClosing.&nbsp; One valid solution is to use the ActiveX version of the WebBrowser control.&nbsp; Currently the .NET 2.0 WebBrowser contol simply wraps the ActiveX version anyhow!

**Symptoms:**&nbsp; Create a .NET 2.0 Windows application and drop the Manged WebBrowser control from the toolbox on the form.&nbsp; Navigate to a&nbsp;page that has jscript to close the window, for example:

<html xmlns=&#8221;<http://www.w3.org/1999/xhtml>&#8221; >  
<head runat=&#8221;server&#8221;>  
&nbsp;&nbsp;&nbsp; <title>Untitled Page</title>  
<script language=&#8221;javascript&#8221; type=&#8221;text/javascript&#8221;>  
// <!CDATA[

function Button1_onclick() {  
window.close();  
}

// ]]>  
</script>  
</head>  
<body>  
&nbsp;&nbsp;&nbsp; <a href=&#8221;javascript:window.close();&#8221;>When you click me I close!</a>  
&nbsp;&nbsp;&nbsp; <input id=&#8221;Button1&#8243; type=&#8221;button&#8221; value=&#8221;button&#8221; onclick=&#8221;return Button1_onclick()&#8221; />  
</body>  
</html>

When you click the button or hyperlink, the control will seem to freeze.

**Analysis:**&nbsp; This is a known issue.&nbsp; What is happening is that&nbsp;the control is being released and coming down.&nbsp; It looks like it is freezing.

**Workaround:&nbsp;** 

Remove the WebBrowser from your form and add the UnManaged control to your toolbox.

To add the AxWebBrowser control make sure you are in design mode of a form.&nbsp; Right click on the tool box and choose ‘Choose items…’.&nbsp; Click on the COM Components tab and scroll down to find ‘Microsoft Web Browser’.&nbsp; Check it and hit OK.&nbsp; The WebBrowser will appear under the General Category of your toolbox items.

Then drop the browser you added onto the form and sink the WindowClosing event of the browser from the design view properties.&nbsp; Setting e.cancel to true will keep the Close from happening.&nbsp; If you do nothing (don’t set e.cancel) the app will close.

VB.NET&nbsp;sample:<p mce_keep="true">

<span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp; <span style="COLOR: blue">Private</span> <span style="COLOR: blue">Sub</span> AxWebBrowser1_WindowClosing(<span style="COLOR: blue">ByVal</span> sender <span style="COLOR: blue">As</span> System.Object, <span style="COLOR: blue">ByVal</span> e <span style="COLOR: blue">As</span> AxSHDocVw.DWebBrowserEvents2_WindowClosingEvent) <span style="COLOR: blue">Handles</span> AxWebBrowser1.WindowClosing<?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt">

<span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; e.cancel = <span style="COLOR: blue">True</span> <span style="COLOR: green">&#8216; or do nothing and the app will close<o:p></o:p></span></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp; <span style="COLOR: blue">End</span> <span style="COLOR: blue">Sub</span></span><span style="COLOR: #1f497d"><o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><span style="COLOR: #1f497d"><o:p><font face=Calibri size=3>&nbsp;</font></o:p></span></p> 

<span style="COLOR: #1f497d"><o:p><font face=Calibri size=3></p> 

<p>
  C#&nbsp;sample:
</p>

<p>
  </font></o:p></span><font size=2>
</p>

<p>
  </font><font color=#0000ff size=2><font color=#0000ff size=2>private</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> axWebBrowser1_WindowClosing(</font><font color=#0000ff size=2><font color=#0000ff size=2>object</font></font><font size=2> sender, AxSHDocVw.</font><font color=#2b91af size=2><font color=#2b91af size=2>DWebBrowserEvents2_WindowClosingEvent</font></font><font size=2> e)
</p>

<p>
  {
</p>

<p>
  &nbsp;&nbsp;&nbsp;&nbsp; e.cancel =
</p>

<p>
  </font><font color=#0000ff size=2><font color=#0000ff size=2>true</font></font><font size=2>;
</p>

<p>
  }
</p><p mce_keep="true">&nbsp;</p> 

<p>
  Finally you could&nbsp;keep the Managed WebBrowser control and poll it&#8217;s state with a timer dropped on the form.&nbsp; If it is uninitialized you could use code similar to this to bring it back to&nbsp;life:
</p><p class=MsoNormal style="MARGIN: 0in 0in 0pt">

<span style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes">if</span><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"> (webBrowser1.ReadyState == <span style="COLOR: #2b91af">WebBrowserReadyState</span>.Uninitialized )<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes">{<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-tab-count: 1">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>//code here to deal with the uninitialized control!<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes">}</span><o:p></o:p></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><o:p><font face=Calibri size=3>&nbsp;</font></o:p></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><font size=3><font face=Calibri>Something like this would be your final code (copy the initialization code from the designer.cs file:</font></font></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><font size=3><font face=Calibri><o:p></o:p></font></font>&nbsp;</p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">if</span> (webBrowser1.ReadyState == <span style="COLOR: #2b91af">WebBrowserReadyState</span>.Uninitialized )<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>{<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.SuspendLayout();<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.Controls.Remove(webBrowser1);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>webBrowser1 = <span style="COLOR: blue">null</span>;<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1 = <span style="COLOR: blue">new</span> System.Windows.Forms.<span style="COLOR: #2b91af">WebBrowser</span>();<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.Location = <span style="COLOR: blue">new</span> System.Drawing.<span style="COLOR: #2b91af">Point</span>(109, -5);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.MinimumSize = <span style="COLOR: blue">new</span> System.Drawing.<span style="COLOR: #2b91af">Size</span>(20, 20);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.Name = <span style="COLOR: #a31515">&#8220;webBrowser1&#8221;</span>;<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.Size = <span style="COLOR: blue">new</span> System.Drawing.<span style="COLOR: #2b91af">Size</span>(250, 250);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.TabIndex = 2;<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.webBrowser1.Navigated += <span style="COLOR: blue">new</span> System.Windows.Forms.<span style="COLOR: #2b91af">WebBrowserNavigatedEventHandler</span>(<span style="COLOR: blue">this</span>.webBrowser1_Navigated);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><o:p>&nbsp;</o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><o:p>&nbsp;</o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.Controls.Add(webBrowser1);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="COLOR: blue">this</span>.ResumeLayout(<span style="COLOR: blue">false</span>);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>webBrowser1.Visible = <span style="COLOR: blue">true</span>;<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>webBrowser1.Url = <span style="COLOR: blue">new</span> System.<span style="COLOR: #2b91af">Uri</span>(<span style="COLOR: #a31515">&#8220;http://jsandershv2003/closme.htm&#8221;</span>);<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none"><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: 'Times New Roman'; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>}<o:p></o:p></span></p> <p class=MsoNormal style="MARGIN: 0in 0in 0pt"><o:p><font face=Calibri size=3>&nbsp;</font></o:p></p> <p mce_keep="true">&nbsp;</p> 

<p>
  Let me know if this helps you out!
</p><p mce_keep="true">&nbsp;</p> 

<p>
  </font>
</p>