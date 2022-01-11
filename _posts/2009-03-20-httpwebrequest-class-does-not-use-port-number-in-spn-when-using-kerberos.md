If you look at a Kerberos ticket when HttpWebRequest is trying to retrieve a resource, you will notice that it does not have the port number in the SPN.

For example you are trying to retrieve a WebService <a href="http://someserver:8888/webservice/webservice.asmx" mce_href="http://someserver:8888/webservice/webservice.asmx">http://someserver:8888/webservice/webservice.asmx</a>&nbsp;and you notice the Kerberos ticket request does not specify the SPN in the request.

If you are using .NET 1.1, you will not be able to work around this due to a design limitation of the classes.&nbsp; You will need to upgrate and use the .NET 2.0 framework.

To use the SPN with the port number specified in the URI of the request for the .NET 2.0 framework you must use the&nbsp;AuthenticationManger.CustomTargetNamedDictionary property and&nbsp;add the appropriate parameters.&nbsp;<a href="http://msdn.microsoft.com/en-us/library/system.net.authenticationmanager.customtargetnamedictionary.aspx" mce_href="http://msdn.microsoft.com/en-us/library/system.net.authenticationmanager.customtargetnamedictionary.aspx">http://msdn.microsoft.com/en-us/library/system.net.authenticationmanager.customtargetnamedictionary.aspx</a>

From this article:

When a <span><a id=ctl00_rs1_mainContentContainer_ctl45 onclick="javascript:Track('ctl00_rs1_mainContentContainer_cpe427611_c|ctl00_rs1_mainContentContainer_ctl45',this);" href="http://msdn.microsoft.com/en-us/library/system.net.webrequest.aspx" mce_href="http://msdn.microsoft.com/en-us/library/system.net.webrequest.aspx">WebRequest</a></span> requires mutual authentication, the SPN for the destination must be supplied by the client. If you know the SPN, you can add it to the <span><span class=selflink>CustomTargetNameDictionary</span></span> before sending the request. If you have not added SPN information to this dictionary, the <span><a id=ctl00_rs1_mainContentContainer_ctl46 onclick="javascript:Track('ctl00_rs1_mainContentContainer_cpe427611_c|ctl00_rs1_mainContentContainer_ctl46',this);" href="http://msdn.microsoft.com/en-us/library/system.net.authenticationmanager.aspx" mce_href="http://msdn.microsoft.com/en-us/library/system.net.authenticationmanager.aspx">AuthenticationManager</a></span> uses the <span><a id=ctl00_rs1_mainContentContainer_ctl47 onclick="javascript:Track('ctl00_rs1_mainContentContainer_cpe427611_c|ctl00_rs1_mainContentContainer_ctl47',this);" href="http://msdn.microsoft.com/en-us/library/system.net.webrequest.requesturi.aspx" mce_href="http://msdn.microsoft.com/en-us/library/system.net.webrequest.requesturi.aspx">RequestUri</a></span> method to compose the most likely SPN; however, this is a computed value and might be incorrect. 

For example, here is how you could workaround this issue for the&nbsp;URI&nbsp;I listed above:

// do this step in the WebService client before calling the service

AuthenticationManager.CustomTargetNameDictionary.Add(“<a href="http://someserver:8888/webservice/webservice.asmx" mce_href="http://someserver:8888/webservice/webservice.asmx">http://someserver:8888/webservice/webservice.asmx</a>”,  
“http/<u><font color=#0066cc>someserver:8888</font></u>”);

Here’s an example whereby the SPN is automatically determined from the URL:

**[Copy Code](javascript:CopyCode('spnuricodesection1');):**<div style="BACKGROUND-COLOR: #e0e0e0" id=spnuricodesection1>Uri uri = new Uri(url);

  
string spn = uri.Scheme + &#8216;/&#8217; + uri.Authority;  
AuthenticationManager.CustomTargetNameDictionary.Add(url, spn);</div> 

&nbsp;Thanks to Hui Zhu for this info!