**Further adventures with the WWSAPI Beta.&nbsp; If you find this useful please take the time to Jot me a quick comment or note!**

I decided to investigate these API&#8217;s and make a simple call to the same WebService in my <a title="WWSAPI walkthrough on Windows 7" href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/windows-web-services-api-client-code-walkthrough-on-windows-7.aspx" mce_href="http://blogs.msdn.com/jpsanders/archive/2009/03/24/windows-web-services-api-client-code-walkthrough-on-windows-7.aspx">previous blog post</a> using Kerberos.&nbsp; I first copied the WebService inside my network so I could use Kerberos and configured the IIS 6 WebSite to use Windows Integrated authentication only.

There are several examples of using Negotiate with SSL but I did not want to use SSL.&nbsp; I figured all I needed to do was remove the SSL bindings from the samples&#8230;&nbsp; WRONG!

Here are the other steps I took and the challenges I faced:

<div style="BACKGROUND-COLOR: #e0e0e0">
  <font size=2></p> 
  
  <p>
    </font><font color=#008000 size=2><font color=#008000 size=2>// use the default client credential if the thread opening the channel/proxy is impersonating,<br /></font></font><font color=#008000 size=2><font color=#008000 size=2>// the thread token will be used; otherwise, the process token will be used<br /></font></font><font size=2>WS_DEFAULT_WINDOWS_INTEGRATED_AUTH_CREDENTIAL defaultCred = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct
  </p>
  
  <p>
    </font></font><font size=2>
  </p>
  
  <p>
    defaultCred.credential.credentialType = WS_DEFAULT_WINDOWS_INTEGRATED_AUTH_CREDENTIAL_TYPE;
  </p>
  
  <p>
    </font><font color=#008000 size=2><font color=#008000 size=2>// declare and initialize properties to set the authentication scheme to Negotiate<br /></font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>// Since the default scheme for WWSAPI header authentication is Negotiate, this property <br /></font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>// may be omitted but included for clarity.<br /></font></font><font size=2>ULONG scheme = WS_HTTP_HEADER_AUTH_SCHEME_NEGOTIATE;</font>
  </p>
  
  <p>
    <font size=2><font size=2>&nbsp;
  </p>
  
  <p>
    WS_SECURITY_BINDING_PROPERTY headerAuthBindingProperties [1] =<br />{<br />&nbsp;&nbsp;&nbsp; { WS_SECURITY_BINDING_PROPERTY_HTTP_HEADER_AUTH_SCHEME, &scheme, </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(scheme) }<br />};
  </p>
  
  <p>
    </font><font color=#008000 size=2><font color=#008000 size=2>// declare and initialize an header authentication security binding<br /></font></font><font size=2>WS_HTTP_HEADER_AUTH_SECURITY_BINDING headerAuthBinding = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct
  </p>
  
  <p>
    </font></font><font size=2>
  </p>
  
  <p>
    headerAuthBinding.binding.bindingType = WS_HTTP_HEADER_AUTH_SECURITY_BINDING_TYPE;<br />headerAuthBinding.binding.properties = headerAuthBindingProperties;<br />headerAuthBinding.binding.propertyCount = WsCountOf(headerAuthBindingProperties);<br />headerAuthBinding.clientCredential = &defaultCred.credential;
  </p>
  
  <p>
    <font size=2>
  </p>
  
  <p>
    </font><font color=#008000 size=2><font color=#008000 size=2>// declare and initialize the array of all security bindings<br /></font></font><font size=2>WS_SECURITY_BINDING* securityBindings[1] = { &headerAuthBinding.binding };</font>
  </p>
  
  <p>
    <font size=2><font size=2>
  </p>
  
  <p>
    </font><font color=#008000 size=2><font color=#008000 size=2>// declare and initialize the security description<br /></font></font><font size=2>WS_SECURITY_DESCRIPTION securityDescription = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct<br /></font></font><font size=2>securityDescription.securityBindings = securityBindings;<br />securityDescription.securityBindingCount = WsCountOf(securityBindings);<br />securityDescription.properties = securityProperties;<br />securityDescription.propertyCount = WsCountOf(securityProperties);<br /></font>
  </p>
  
  <p>
    <font size=2><font color=#008000 size=2><font color=#008000 size=2>
  </p>
  
  <p>
    // Create the proxy<br /></font></font><font size=2>hr = WsCreateServiceProxy(<br />WS_CHANNEL_TYPE_REQUEST, <br />WS_HTTP_CHANNEL_BINDING, <br />&securityDescription, </font><font color=#008000 size=2><font color=#008000 size=2>// added for Negotiate<br /></font></font><font size=2>NULL, <br />0, <br />NULL,<br /></font><font size=2>,<br /></font><font size=2>&serviceProxy, <br />error);</font>
  </p>
</div>

<font size=2>This looked good but failed with an error when I called the WebService method:</font>

<font size=2>E_INVALIDARG.</font><p mce_keep="true">&nbsp;</p> 

Further investigation revealed that I needed to set the <font size=2>WS\_PROTECTION\_LEVEL appropriately.&nbsp; Since the message is NOT using SSL we need to set this property as follows:</font>

<div style="BACKGROUND-COLOR: #e0e0e0">
  <p>
    <font color=#008000 size=2><font color=#008000 size=2>// set the protection level to none &#8211; you have to do this to avoid the error: E_INVALIDARG when you call a SOAP method<br /></font></font><font size=2>WS_PROTECTION_LEVEL protectionLevel = WS_PROTECTION_LEVEL_NONE;<br />WS_SECURITY_PROPERTY securityProperties[1] = {<br />{WS_SECURITY_PROPERTY_TRANSPORT_PROTECTION_LEVEL, &protectionLevel, </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(protectionLevel)}<br />};<br /></font><font size=2><font size=2>
  </p>
</div>

and then set these on the securityDescription like this:

<div style="BACKGROUND-COLOR: #e0e0e0">
  <p>
    securityDescription.properties = securityProperties;<br />securityDescription.propertyCount = WsCountOf(securityProperties);
  </p>
</div>

OK, home free right?&nbsp; No&#8230;&nbsp; Now I was getting this error from the call to _HelloWorld.

&nbsp;&nbsp;hr&nbsp;0x803d0000 The input data was not in the expected format or did not have the expected value.&nbsp;&nbsp;

Since the &#8216;input data&#8217; seemed to be the issue I took a Network Monitor trace and found that the difference between my anonymous test and this new Kerberos Test (other than the Negotiate headers etc&#8230;) was that the SOAP envelope looked totally different!&nbsp; In the Kerberos case I found this: <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri><s:Envelope xmlns:a=&#8221;</font><a href="http://www.w3.org/2005/08/addressing" mce_href="http://www.w3.org/2005/08/addressing"><font color=#0000ff size=3 face=Calibri>http://www.w3.org/2005/08/addressing</font></a><font size=3 face=Calibri>&#8221; xmlns:s=&#8221;</font><a href="http://www.w3.org/2003/05/soap-envelope" mce_href="http://www.w3.org/2003/05/soap-envelope"><font color=#0000ff size=3 face=Calibri>http://www.w3.org/2003/05/soap-envelope</font></a><font size=3 face=Calibri>&#8220;><s:Header

<span style="BACKGROUND: yellow; mso-highlight: yellow">><a:Action</span> s:mustUnderstand=&#8221;1&#8243;></font><a href="http://tempuri.org/HelloWorld%3c/a:Action%3e%3ca:MessageID%3eurn:uuid:ba48938e-97a2-4dba-9e3f-cf9378533f8f%3c/a:MessageID%3e%3ca:To" mce_href="http://tempuri.org/HelloWorld%3c/a:Action%3e%3ca:MessageID%3eurn:uuid:ba48938e-97a2-4dba-9e3f-cf9378533f8f%3c/a:MessageID%3e%3ca:To"><font color=#0000ff size=3 face=Calibri>http://tempuri.org/HelloWorld</a:Action><a:MessageID>urn:uuid:ba48938e-97a2-4dba-9e3f-cf9378533f8f</a:MessageID><a:To</font></a><font size=3 face=Calibri> s:mustUnderstand=&#8221;1&#8243;></font><a href="http://jsandershv2003/WebSite/MyWebService.asmx%3c/a:To%3e%3c/s:Header%3e%3cs:Body%3e%3cHelloWorld" mce_href="http://jsandershv2003/WebSite/MyWebService.asmx%3c/a:To%3e%3c/s:Header%3e%3cs:Body%3e%3cHelloWorld"><font color=#0000ff size=3 face=Calibri>http://jsandershv2003/WebSite/MyWebService.asmx</a:To></s:Header><s:Body><HelloWorld</font></a><font size=3 face=Calibri> xmlns=&#8221;</font><a href="http://tempuri.org/" mce_href="http://tempuri.org/"><font color=#0000ff size=3 face=Calibri>http://tempuri.org/</font></a><font size=3 face=Calibri>&#8220;/></s:Body></s:Envelope></font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p><font size=3 face=Calibri>&nbsp;</font></o:p></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>Error:</font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><o:p><font size=3 face=Calibri>&nbsp;</font></o:p></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>System.Web.Services.Protocols.SoapHeaderException: SOAP header 

<span style="BACKGROUND: yellow; mso-highlight: yellow">Action</span> was not understood&#8230;&nbsp;&nbsp; </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>at System.Web.Services.Protocols.SoapHeaderHandling.SetHeaderMembers(SoapHeaderCollection headers, </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>Object target, </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>SoapHeaderMapping[] mappings, </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>SoapHeaderDirection direction, Boolean client)..&nbsp;&nbsp; </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>at System.Web.Services.Protocols.SoapServerProtocol.CreateServerInstance()..&nbsp;&nbsp; </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>at System.Web.Services.Protocols.WebServiceHandler.Invoke()..&nbsp; </font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><font size=3 face=Calibri>&nbsp;at System.Web.Services.Protocols.WebServiceHandler.CoreProcessRequest()</font></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><o:p><font size=3 face=Calibri>&nbsp;</font></o:p></p> 

After investigation I found that to get rid of the Messaging headers I needed to set some channel properties:

<div style="BACKGROUND-COLOR: #e0e0e0">
  <p mce_keep="true"><font size=2>WS_CHANNEL_PROPERTY channelProperties[1];<br />ULONG channelPropertyCount = 0;<br />WS_ADDRESSING_VERSION addressingVersion = WS_ADDRESSING_VERSION_TRANSPORT;<br />channelProperties[channelPropertyCount].id = WS_CHANNEL_PROPERTY_ADDRESSING_VERSION;<br />channelProperties[channelPropertyCount].value = &addressingVersion ;<br />channelProperties[channelPropertyCount].valueSize = </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(addressingVersion );<br />channelPropertyCount++; // in this case only one property</font></p> 
  
  <p>
    <font size=2>
  </p>
  
  <p>
    // Then you pass the channelProperties and channelPropertyCount to WsCreateServiceProxy (or WsCreateChannel if you are working at channel layer).
  </p>
  
  <p>
    hr = WsCreateServiceProxy(<br />WS_CHANNEL_TYPE_REQUEST, <br />WS_HTTP_CHANNEL_BINDING, <br />&securityDescription, </font><font color=#008000 size=2><font color=#008000 size=2>// added for Negotiate<br /></font></font><font size=2>NULL, <br />0, <br />channelProperties, </font><font color=#008000 size=2><font color=#008000 size=2>// channel properties<br /></font></font><font size=2>channelPropertyCount, </font><font color=#008000 size=2><font color=#008000 size=2>// channel property count<br /></font></font><font size=2>&serviceProxy, <br />error);<br /></font>
  </p>
</div>

<font size=2>**Success!**</font>

**Now the complete code listing for your enjoyment ([Copy Code](javascript:CopyCode('wwsapikerbcodesection1');)):**<div style="BACKGROUND-COLOR: #e0e0e0" id=wwsapikerbcodesection1><font color=#008000 size=2><font color=#008000 size=2></p> 

// WWSAPITest.cpp : Defines the entry point for the console application.  
//

</font></font><font color=#0000ff size=2><font color=#0000ff size=2>

#include</font></font><font size=2> </font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;stdafx.h&#8221;  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>#include</font></font><font size=2> </font><font color=#a31515 size=2><font color=#a31515 size=2><WebServices.h>  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>#include</font></font><font size=2> </font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;.\wsdl\MyWebService.wsdl.h&#8221;  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>int</font></font><font size=2> mainHttpKerb(</font><font color=#0000ff size=2><font color=#0000ff size=2>int</font></font><font size=2> argc, _TCHAR* argv[])  
{  
&nbsp;&nbsp;&nbsp; HRESULT hr;  
&nbsp;&nbsp;&nbsp; WS_ERROR* error;  
&nbsp;&nbsp;&nbsp; WS_HEAP* heap;  
&nbsp;&nbsp;&nbsp; WS\_SERVICE\_PROXY* serviceProxy;  
&nbsp;&nbsp;&nbsp; hr = S_OK;  
&nbsp;&nbsp;&nbsp; error = NULL;  
&nbsp;&nbsp;&nbsp; heap = NULL;  
&nbsp;&nbsp;&nbsp; serviceProxy = NULL;  
</font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // Creating error object  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; hr = WsCreateError(NULL, 0, &error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; if</font></font><font size=2> (FAILED(hr))  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; wprintf (L</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;Failed to create Error object\n&#8221;</font></font><font size=2>);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font><font color=#0000ff size=2><font color=#0000ff size=2>return</font></font><font size=2> -1;&nbsp;  
&nbsp;&nbsp;&nbsp; }  
</font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp;&nbsp;// Creating heap handle  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; hr = WsCreateHeap(10000000, 0, NULL, 0, &heap, error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; if</font></font><font size=2> (FAILED(hr))&nbsp;  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; wprintf (L</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;Failed to create Heap object\n&#8221;</font></font><font size=2>);  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if</font></font><font size=2> (heap != NULL)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeHeap(heap);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; heap = NULL;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if</font></font><font size=2> (error != NULL)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeError(error);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; error = NULL;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return</font></font><font size=2> -1;</font>  
<font size=2>&nbsp;&nbsp;&nbsp; }  
</font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; ////////////////kerberos  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; //// declare and initialize a windows credential  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // use the default client credential if the thread opening the channel/proxy is impersonating,&nbsp;  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // the thread token will be used; otherwise, the process token will be used  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_DEFAULT\_WINDOWS\_INTEGRATED\_AUTH_CREDENTIAL defaultCred = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; defaultCred.credential.credentialType = WS\_DEFAULT\_WINDOWS\_INTEGRATED\_AUTH\_CREDENTIAL\_TYPE;  
</font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // declare and initialize properties to set the authentication scheme to Negotiate  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // Since the default scheme for WWSAPI header authentication is Negotiate, this property&nbsp;  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // may be omitted.  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; ULONG scheme = WS\_HTTP\_HEADER\_AUTH\_SCHEME_NEGOTIATE;  
</font><font color=#008000 size=2><font color=#008000 size=2>&nbsp;&nbsp;&nbsp; // set the protection level to none &#8211; you have to do this to avoid the error: E_INVALIDARG when you call a SOAP method  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_PROTECTION\_LEVEL protectionLevel = WS\_PROTECTION\_LEVEL_NONE;  
&nbsp;&nbsp;&nbsp; WS\_SECURITY\_PROPERTY securityProperties[1] = {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {WS\_SECURITY\_PROPERTY\_TRANSPORT\_PROTECTION_LEVEL, &protectionLevel, </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(protectionLevel)}  
&nbsp;&nbsp;&nbsp; }; </font>

<font size=2>&nbsp;&nbsp;&nbsp; WS\_SECURITY\_BINDING_PROPERTY headerAuthBindingProperties [1] =  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; { WS\_SECURITY\_BINDING\_PROPERTY\_HTTP\_HEADER\_AUTH_SCHEME, &scheme, </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(scheme) }  
&nbsp;&nbsp;&nbsp; };  
</font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// declare and initialize an header authentication security binding  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_HTTP\_HEADER\_AUTH\_SECURITY_BINDING headerAuthBinding = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; headerAuthBinding.binding.bindingType = WS\_HTTP\_HEADER\_AUTH\_SECURITY\_BINDING\_TYPE;  
&nbsp;&nbsp;&nbsp; headerAuthBinding.binding.properties = headerAuthBindingProperties;  
&nbsp;&nbsp;&nbsp; headerAuthBinding.binding.propertyCount = WsCountOf(headerAuthBindingProperties);  
&nbsp;&nbsp;&nbsp; headerAuthBinding.clientCredential = &defaultCred.credential;  
</font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// declare and initialize the array of all security bindings  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_SECURITY\_BINDING* securityBindings[1] = { &headerAuthBinding.binding };  
</font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// declare and initialize the security description  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_SECURITY\_DESCRIPTION securityDescription = {}; </font><font color=#008000 size=2><font color=#008000 size=2>// zero out the struct  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; securityDescription.securityBindings = securityBindings;  
&nbsp;&nbsp;&nbsp; securityDescription.securityBindingCount = WsCountOf(securityBindings);  
&nbsp;&nbsp;&nbsp; securityDescription.properties = securityProperties;  
&nbsp;&nbsp;&nbsp; securityDescription.propertyCount = WsCountOf(securityProperties);  
</font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// size this array to the number of properties you will have  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; WS\_CHANNEL\_PROPERTY channelProperties[1];  
&nbsp;&nbsp;&nbsp; ULONG channelPropertyCount = 0;  
&nbsp;&nbsp;&nbsp; WS\_ADDRESSING\_VERSION addressingVersion = WS\_ADDRESSING\_VERSION_TRANSPORT;  
&nbsp;&nbsp;&nbsp; channelProperties[channelPropertyCount].id = WS\_CHANNEL\_PROPERTY\_ADDRESSING\_VERSION;  
&nbsp;&nbsp;&nbsp; channelProperties[channelPropertyCount].value = &addressingVersion ;  
&nbsp;&nbsp;&nbsp; channelProperties[channelPropertyCount].valueSize = </font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(addressingVersion );  
&nbsp;&nbsp;&nbsp; channelPropertyCount++;

</font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// add more channel properties here  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>/*WS\_ENVELOPE\_VERSION soapVersion = WS\_ENVELOPE\_VERSION\_SOAP\_1_1;  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>channelProperties[channelPropertyCount].id = WS\_CHANNEL\_PROPERTY\_ENVELOPE\_VERSION;  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>channelProperties[channelPropertyCount].value = &soapVersion;  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>channelProperties[channelPropertyCount].valueSize = sizeof(soapVersion);  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>channelPropertyCount++;*/  
<font color=#000000>&nbsp;&nbsp;&nbsp;&nbsp;</font>  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// Then you pass the channelProperties and channelPropertyCount to WsCreateServiceProxy (or WsCreateChannel if you are working at channel layer).  
</font></font><font size=2></font><font color=#008000 size=2><font color=#008000 size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>// Create the proxy  
</font></font><font size=2>&nbsp;&nbsp;&nbsp; hr = WsCreateServiceProxy(  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WS\_CHANNEL\_TYPE_REQUEST,&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WS\_HTTP\_CHANNEL_BINDING,&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &securityDescription, </font><font color=#008000 size=2><font color=#008000 size=2>// added for Negotiate  
</font></font><font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NULL,&nbsp;&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0,&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; channelProperties, </font><font color=#008000 size=2><font color=#008000 size=2>// channel properties  
</font></font><font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; channelPropertyCount, </font><font color=#008000 size=2><font color=#008000 size=2>// channel property count  
</font></font><font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &serviceProxy,&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2>  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (FAILED(hr))&nbsp;  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeHeap(heap);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeError(error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;<font color=#000000>&nbsp;&nbsp;&nbsp; </font>return</font></font><font size=2> -1;  
&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp; WS\_ENDPOINT\_ADDRESS address = {};  
</font>

<font size=2>

&nbsp;&nbsp;&nbsp;&nbsp;WS\_STRING Url = WS\_STRING_VALUE(L</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;http://jsandershv2003/WebSite/MyWebService.asmx&#8221;</font></font><font size=2>);

&nbsp;&nbsp;&nbsp; address.url = Url;  
&nbsp;&nbsp;&nbsp; hr = WsOpenServiceProxy(serviceProxy, &address, NULL, error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (FAILED(hr))&nbsp;  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeServiceProxy(serviceProxy);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeHeap(heap);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeError(error);  
</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp;&nbsp;</font>&nbsp;&nbsp;&nbsp; return</font></font><font size=2> -1;  
&nbsp;&nbsp;&nbsp; }

&nbsp;&nbsp;&nbsp; WCHAR *aResult = NULL;

&nbsp;&nbsp;&nbsp; hr = WebServiceSoap12_HelloWorld(  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; serviceProxy,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &aResult,&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; heap,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NULL, 0,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; NULL,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; error);</font>

<font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (SUCCEEDED(hr))  
</font><font size=2>&nbsp;&nbsp;&nbsp; {&nbsp;&nbsp;&nbsp;&nbsp;  
</font><font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; wprintf(L</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;%s\n&#8221;</font></font><font size=2>, aResult);  
&nbsp;&nbsp;&nbsp; }  
</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>else</font></font><font size=2>&nbsp;  
&nbsp;&nbsp;&nbsp; {</font>  
<font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; wprintf(L</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;failed\n&#8221;</font></font><font size=2>);  
&nbsp;&nbsp;&nbsp; }

</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (serviceProxy != NULL)  
&nbsp;&nbsp;&nbsp; {&nbsp;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsCloseServiceProxy(serviceProxy, NULL, error);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeServiceProxy(serviceProxy);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; serviceProxy = NULL;  
&nbsp;&nbsp;&nbsp; }

</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (heap != NULL)  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeHeap(heap);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; heap = NULL;  
&nbsp;&nbsp;&nbsp; }  
</font><font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>&nbsp;&nbsp;&nbsp; </font>if</font></font><font size=2> (error != NULL)  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WsFreeError(error);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; error = NULL;  
&nbsp;&nbsp;&nbsp; }&nbsp;&nbsp;&nbsp;&nbsp;  
</font><font color=#0000ff size=2><font color=#0000ff size=2>  
<font color=#000000>&nbsp;&nbsp;&nbsp; </font>return</font></font><font size=2> 0;  
}

</font><font color=#0000ff size=2><font color=#0000ff size=2>

int</font></font><font size=2> _tmain(</font><font color=#0000ff size=2><font color=#0000ff size=2>int</font></font><font size=2> argc, _TCHAR* argv[])  
{&nbsp;&nbsp;&nbsp; </font>  
&nbsp;&nbsp;&nbsp; <font color=#0000ff size=2><font color=#0000ff size=2>return</font></font><font size=2> mainHttpKerb(argc,argv);  
}</font><font size=2>

</font></font></font></font></font></font></font></div>