There can be many reasons for this error.&nbsp; In some cases this error&nbsp;can be confusing.&nbsp; I have seen a few instances where an ASP.Net webservice call resulted in this error.&nbsp; More perplexing is the fact that Internet Explorer on the same machine can reach the WebService fine.&nbsp; If a firewall was blocking the traffic, most likely the Internet Explorer request to the same port would also be blocked.&nbsp; Also to add to the confusion is when adding the usesystemdefault=true (default setting) did the proxy not get used.&nbsp; The reason that usesystemdefault did not get the proxy is that IE stores the hard coded proxy information in the registry of the logged on user.&nbsp; When ASP.Net runs, it is not running in the context of the currently logged on user (normally) and so it cannot read the same information that IE is reading to connect to the proxy.

Some other errors around this exeption include: WebException: Unable to connect to the remote server, SocketException (0x2751): A socket operation was attempted to an unreachable host, Socket operation encountered a dead network

Typical call stacks look something like this.  
Exception Details: System.Net.Sockets.SocketException: A socket operation was attempted to an unreachable host  
[SocketException (0x2751): A socket operation was attempted to an unreachable host <<ipaddr:port>>]  
&nbsp;System.Net.Sockets.Socket.DoConnect(EndPoint endPointSnapshot, SocketAddress socketAddress) +1073657  
&nbsp;&nbsp; System.Net.Sockets.Socket.InternalConnect(EndPoint remoteEP) +33  
&nbsp;&nbsp; System.Net.ServicePoint.ConnectSocketInternal

WebException: Unable to connect to the remote server  
&nbsp;&nbsp; System.Net.HttpWebRequest.GetRequestStream() +1534317  
&nbsp;&nbsp; System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke

Each time, these issues were related to proxy settings.&nbsp; IE was able to get to the WebService but .NET could not.&nbsp; The reason is, the Proxy information was manually configured for IE.&nbsp; 

A simple change to the Web.Config fixes the issue:  
You will need to change &#8220;<a href="http://192.168.1.10:3128/" mce_href="http://192.168.1.10:3128/">http://192.168.1.10:3128</a>&#8221;&nbsp; to be the address of your proxy server.&nbsp; You should be able to determine the proxy from your Internet Explorer Settings.  
<configuration>  
&nbsp; <system.net>  
&nbsp;&nbsp;&nbsp; <defaultProxy>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <proxy  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; proxyaddress=&#8221;<a href="http://192.168.1.10:3128/" mce_href="http://192.168.1.10:3128/">http://192.168.1.10:3128</a>&#8220;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bypassonlocal=&#8221;true&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; />  
&nbsp;&nbsp;&nbsp; </defaultProxy>  
&nbsp; </system.net>  
</configuration>

Here is an article on how proxy detection works in the 2.0 framework:  
<a href="http://msdn.microsoft.com/en-us/magazine/cc300743.aspx" mce_href="http://msdn.microsoft.com/en-us/magazine/cc300743.aspx">http://msdn.microsoft.com/en-us/magazine/cc300743.aspx</a>

&nbsp;You may also now need to provide credentials to get through the proxy.&nbsp; If the call does not go through and the exception indicates an HTTP 407 error, you can add the credentials to your config as well.&nbsp; Here are articles on the <system.net> schema and proxy setting: <a href="http://msdn.microsoft.com/en-us/library/kd3cf2ex(VS.80).aspx" mce_href="http://msdn.microsoft.com/en-us/library/kd3cf2ex(VS.80).aspx">http://msdn.microsoft.com/en-us/library/kd3cf2ex(VS.80).aspx</a>, <a href="http://msdn.microsoft.com/en-us/library/sa91de1e(VS.80).aspx" mce_href="http://msdn.microsoft.com/en-us/library/sa91de1e(VS.80).aspx">http://msdn.microsoft.com/en-us/library/sa91de1e(VS.80).aspx</a>

If the proxy settings are not the issue, ProcMon may help you identify any permissions related issues on the server.&nbsp; You can download this tool from <a href="http://www.microsoft.com/sysinternals" mce_href="http://www.microsoft.com/sysinternals">http://www.microsoft.com/sysinternals</a><p mce_keep="true">Leave me a message if you were able to solve a problem with this article!</p> <p mce_keep="true">&nbsp;</p>