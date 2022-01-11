<u><strong>Problem</strong>&nbsp;</u>

Taking a <a title="System.Net Trace" href="http://msdn.microsoft.com/en-us/library/ty48b824.aspx" target=\_blank mce\_href="http://msdn.microsoft.com/en-us/library/ty48b824.aspx">System.Net Trace</a> (see <a title="My Favorite System.Net Tracing File" href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx" target=\_blank mce\_href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx">My Favorite System.Net Tracing File</a>) you will see that the HttpWebRequest is trying to use a .INS file.

System.Net Verbose: 0 : [0371] WebRequest::Create(<a href="http://myserver/ie/update/windows/IEConfig.INS" mce_href="http://myserver/ie/update/windows/IEConfig.INS">http://myserver/ie/update/windows/IEConfig.INS</a>)

It is successfully retrieved but when the request is made you see something similar to this in the .NET log:

System.Net.Sockets Error: 0 : [0371] Exception in the Socket#4094998::Connect &#8211; No connection could be made because the target machine actively refused it 192.168.0.202:443

and 

System.Net Error: 0 : [0371] Exception in the HttpWebRequest#33574999:: &#8211; Unable to connect to the remote server

**<u>Resolution</u>**

System.Net by design does not process .INS files.&nbsp; This results in the HTTP Request being made direct and the Proxy is denying this action.

You need choose one of these methods to resolve the issue:

1. Change your environment to use .PAC files.&nbsp; For example, set this in IE or use the <a title=AutoConfigUrl href="http://msdn.microsoft.com/en-us/library/cc232672(PROT.13).aspx" target=\_blank mce\_href="http://msdn.microsoft.com/en-us/library/cc232672(PROT.13).aspx">AutoConfigUrl</a> key.

2. Change your .NET code to hard code the <a title="proxy information" href="http://msdn.microsoft.com/en-us/library/system.net.httpwebrequest.proxy(VS.80).aspx" target=\_blank mce\_href="http://msdn.microsoft.com/en-us/library/system.net.httpwebrequest.proxy(VS.80).aspx">proxy information</a>

3. Add <a title="proxy configuration" href="http://msdn.microsoft.com/en-us/library/kd3cf2ex.aspx" target=\_blank mce\_href="http://msdn.microsoft.com/en-us/library/kd3cf2ex.aspx">proxy configuration</a> information to your <<application>>.exe.config, web.config&nbsp;or machine.config files.

-Jeff