The following code worked fine on IIS 6 but when used on IIS it failed:

<font size=2>

System.DirectoryServices.</font><font color=#2b91af size=2><font color=#2b91af size=2>DirectoryEntry</font></font><font size=2> iisServer;  
iisServer = </font><font color=#0000ff size=2><font color=#0000ff size=2>new</font></font><font size=2> System.DirectoryServices.</font><font color=#2b91af size=2><font color=#2b91af size=2>DirectoryEntry</font></font><font size=2>(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;IIS://jsanders4/W3SVC/1&#8221;</font></font><font size=2>);  
System.DirectoryServices.</font><font color=#2b91af size=2><font color=#2b91af size=2>DirectoryEntry</font></font><font size=2> rootFolder = iisServer.Children.Find(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;Root&#8221;</font></font><font size=2>, </font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;IIsWebVirtualDir&#8221;</font></font><font size=2>); </font><font color=#008000 size=2><font color=#008000 size=2>//exception here</font></font>

The exception was as follows:&nbsp;

[System.Runtime.InteropServices.COMException]&nbsp;{&#8220;Unknown error (0x80005000)&#8221;}&nbsp;  
System.Runtime.InteropServices.COMException

Unknown error (0x80005000)  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.Bind(Boolean throwIfFail)  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.Bind()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.get_IsContainer()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntries.CheckIsContainer()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntries.Find(String name, String schemaC  
lassName)&nbsp;<p mce_keep="true">&nbsp;</p> 

The error code is not translated to&nbsp;anything.&nbsp; This indicates that the ADSI provider for&nbsp;<font color=#a31515>IIS://jsanders4/W3SVC/1 </font><font color=#000000>does not exist or it is inaccessible.</font>

Opening up IIS manager you can see that the webserver &#8216;jsanders4&#8217; is up and running and the primary website ID is indeed 1.&nbsp; The logical conclusion then is that the ADSI provider for IIS://jsanders4 must be the problem.

IIS 7 does not install an ADSI provider by default.&nbsp; You can enable it however as a Role Service for the IIS Web Server.&nbsp; You need to enable the _IIS 6 Metabase Compatiblity_ role service.&nbsp; Probably a better way to proceed is to change your code to use the WMI provider for IIS 7 <a href="http://msdn.microsoft.com/en-us/library/aa347459.aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa347459.aspx">http://msdn.microsoft.com/en-us/library/aa347459.aspx</a><p mce_keep="true">After&nbsp;installing the 

_IIS 6 Metabase Compatiblity_ role service&nbsp;the error changed:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</p> <p mce_keep="true">[System.Runtime.InteropServices.COMException]&nbsp;{&#8220;Access is denied.\r\n&#8221;}&nbsp;System.Runtime.InteropServices.COMException  
ErrorCode&nbsp;0x80070005</p> <p mce_keep="true">Access is denied.</p> <p mce_keep="true">&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.Bind(Boolean throwIfFail)  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.Bind()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntry.get_IsContainer()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntries.CheckIsContainer()  
&nbsp;&nbsp; at System.DirectoryServices.DirectoryEntries.Find(String name, String schemaClassName)</p> <p mce_keep="true">This is because&nbsp;Windows Server 2008 is locked down with UAC.&nbsp; You need to run the program as&nbsp;Administrator to execute this program.&nbsp;Another alternative is to set the account that is running this program with the rights: Logon as a Service&#8221;/ &#8220;Logon as a Batch Job&#8221;</p> <p mce_keep="true">I hope this helps you!&nbsp; Let me know if you used it to solve an issue.</p>