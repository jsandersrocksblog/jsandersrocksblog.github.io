<table border=0 cellSpacing=0 cellPadding=0 minmax_bound="true"> <tbody minmax_bound="true"> <tr minmax_bound="true"> <td width="100%" minmax_bound="true"> <div class=BlogPostContent minmax_bound="true"> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal minmax_bound="true"><font size=3 minmax_bound="true"><font face=Calibri minmax_bound="true"><strong minmax_bound="true">UPDATE: Replace ATLServer with WWSAPI!&nbsp;</strong></font></font><a title="Windows Web Services Walkthrough" href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/windows-web-services-api-client-code-walkthrough-on-windows-7.aspx" minmax\_bound="true" mce\_href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/windows-web-services-api-client-code-walkthrough-on-windows-7.aspx"><font color=#000000 minmax_bound="true"><strong minmax_bound="true">Windows Web Services API Client code walkthrough</strong></font></a><strong minmax_bound="true">&nbsp;</strong></p> </div> </td> </tr> </tbody> </table> 

Using the following code:

<font size=2>CoInitialize (NULL);  
CServiceT <CSoapSocketClientT<>> * myclient = </font><font color=#0000ff size=2>new</font><font size=2> CServiceT<CSoapSocketClientT<>>; </font><font color=#008000 size=2>//socket client</font>

<font color=#008000 size=2>

</font><font size=2>BSTR results;  
HRESULT hr = myclient->BigString(1024*32,&results);</font>

<font size=2>&nbsp;The hr value was E_FAIL.</font><p mce_keep="true">&nbsp;</p> 

This is because the Socket Based class cannot handle a return buffer bigger than 2K.

The solution is to use one of the following derivations:

<font size=2>

CServiceT <CSoapWininetClient> * myclient = </font><font color=#0000ff size=2>new</font><font size=2> CServiceT<CSoapWininetClient>; </font><font color=#008000 size=2>//wininet client

</font><font size=2><font size=2>

CServiceT <CSoapMSXMLInetClient> * myclient = </font><font color=#0000ff size=2>new</font><font size=2> CServiceT<CSoapMSXMLInetClient>; </font><font color=#008000 size=2>//winhttp client  
</font><font color=#008000 size=2>&nbsp;</font>

<font color=#008000><font size=2><font size=2><font color=#000000>Neither of these have the 2K limit</font></font></font></font>

<font color=#008000><font size=2><font size=2>&nbsp;

</font></font></font></font>