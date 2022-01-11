<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">With the&nbsp;release of Internet Explorer 8 comes a new option for WinInet&nbsp;programming: INTERNET_OPTION_SUPPRESS_SERVER_AUTH.&nbsp; The MSDN documentation is very specific and describes how the option affects authorization, but I like to see things in action!&nbsp; How about some sample code for INTERNET_OPTION_SUPPRESS_SERVER_AUTH?<?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">This option is documented here: <a href="http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx"><font color=#0000ff>http://msdn.microsoft.com/en-us/library/aa385328(VS.85).aspx</font></a> (note that if you are not using the latest SDK headers, the value for this option is also documented here).<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">To sum it up, use this option so your WinInet application will allow you to use credentials to authorize through a proxy, but don&#8217;t pass credentials to the endpoint server.<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">To understand this option you can modify the HttpAuth example in the Platforms SDK and see how this option can be used to create a sample.&nbsp; Then you can use Fiddler (<a href="http://www.fiddlertool.com/" mce_href="http://www.fiddlertool.com/"><font color=#0000ff>http://www.fiddlertool.com</font></a>) to request proxy credentials and verify that you cannot pass credentials to an endpoint server.<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">Since this is an option for the request you set this on the request handle just before you execute the request:<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">InternetSetOption(hRequest,INTERNET_OPTION_SUPPRESS_SERVER_AUTH,NULL,0);<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; COLOR: green; FONT-SIZE: 10pt">// Send request.<br /></span><span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">fRet = HttpSendRequest( hRequest, <span style="COLOR: green">// request handle<br /></span><span style="COLOR: #a31515">&#8220;&#8221;</span>, <span style="COLOR: green">// header string<br /></span>0, <span style="COLOR: green">// header length<br /></span>NULL, <span style="COLOR: green">// post data<br /></span>0 <span style="COLOR: green">// post length<br /></span>);<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">Next configure Fiddler to require proxy authentication by selecting the menu item &#8216;Rules&#8217; and check the &#8216;Require Proxy Authentication&#8217; option.&nbsp; If you look at the help documentation on this feature you will discover the password and user id is &#8216;1&#8217; for this setting.<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">Finally run the HttpAuth sample and see that it will prompt you for the Proxy authorization, and once you enter these credentials you cannot send credentials to the end point server.&nbsp; Even if you use the custom UI and use InternetSetOption to set the username and password, WinInet will not send these credentials.<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">&nbsp;Note that in the documentation for this option, it suggests you use the INTERNET_OPTION_NO_COOKIES option as well to prevent Cookie based Authentication to the end point server.<o:p></o:p></span>

<span style="FONT-FAMILY: 'Arial','sans-serif'; FONT-SIZE: 10pt">Let me know if this was useful to you!<o:p></o:p></span>