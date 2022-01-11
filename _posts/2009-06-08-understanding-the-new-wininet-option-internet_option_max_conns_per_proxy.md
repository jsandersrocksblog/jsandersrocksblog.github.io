The documentation on this is very straight forward (<a href="http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx">http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx</a>).&nbsp; At the time of publishing however the documentation has a slight error.&nbsp; You cannot pass a handle in for the first argument.&nbsp; It must be NULL or the call will return false and GetLastError() will show the error is: <font size=2>ERROR\_INTERNET\_INVALID_OPERATION.</font>

&nbsp;The default value for this option is 4 connections.

&nbsp;Also see this post: <http://blogs.msdn.com/jpsanders/archive/2009/06/29/understanding-connection-limits-and-new-proxy-connection-limits-in-wininet-and-internet-explorer.aspx>

Let me know if this article was useful to you!