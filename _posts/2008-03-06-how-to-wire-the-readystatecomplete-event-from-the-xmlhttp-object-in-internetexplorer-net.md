I have a web page that has a global variable in the jscript called xmlhttp.&nbsp; It is the build in XMLHttp object in Internet Explorer.&nbsp; I am hosting the WebBrowser control in a C# (.NET managed code) application and I want to know when the XMLHttp object is done.&nbsp; This occurs after the document complete event so how do I do this?

&nbsp;Answer:

This worked for me!&nbsp; Using Visual Studio 2008:

Create a new C# Windows Form Application Called XMLHttpReadyState  
Add a WebBrowser control to the form  
Double click on the WebBrowser in the form to add the documentComplete event handler.  
Add a function to wire the XMLHttp Event.

Here is the commented code.&nbsp; Let me know if this is useful and if it works out for you!<p mce_keep="true">&nbsp;</p> 

<font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Collections.Generic;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.ComponentModel;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Data;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Drawing;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Linq;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Text;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Windows.Forms;</font><font color=#0000ff size=2><font color=#0000ff size=2>

using

</font></font><font size=2> System.Runtime.InteropServices;</font><font color=#0000ff size=2><font color=#0000ff size=2>

namespace

</font></font><font size=2> XMLHttpReadyState

{</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>partial</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>class</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>Form1</font></font><font size=2> : </font><font color=#2b91af size=2><font color=#2b91af size=2>Form</font></font><font size=2>

{</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> Form1()

{

InitializeComponent();

}</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>private</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> webBrowser1_DocumentCompleted(</font><font color=#0000ff size=2><font color=#0000ff size=2>object</font></font><font size=2> sender, </font><font color=#2b91af size=2><font color=#2b91af size=2>WebBrowserDocumentCompletedEventArgs</font></font><font size=2> e)

{</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>//when the document is done loading, wire up the XMLHttp object (if it exists)</font></font><font size=2>

wireXMLHttpReadyState();

}</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// This class is used for the readystatechange callback. This callback expects an IDispatch interface.</font></font><font size=2>

</font><font color=#008000 size=2><font color=#008000 size=2>// The constructor takes an Object which is the XMLHttp Obj so we can easily get the readystate.</font></font><font size=2>

</font><font color=#008000 size=2><font color=#008000 size=2>// You could also simply go get the ready state by navigating down from the webbrowser document object.</font></font><font size=2>

[

</font><font color=#2b91af size=2><font color=#2b91af size=2>ComVisible</font></font><font size=2>(</font><font color=#0000ff size=2><font color=#0000ff size=2>true</font></font><font size=2>)] </font><font color=#008000 size=2><font color=#008000 size=2>//this is necessary or you get an Invalid Cast exception</font></font><font size=2>

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>class</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>ReadyState</font></font><font size=2>

{</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> ReadyState(</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> theXMLHttpObj) { setObj( theXMLHttpObj); }

</font><font color=#008000 size=2><font color=#008000 size=2>// DispId 0 is what the XMLHttpObj will call, the name does not matter</font></font><font size=2>

[

</font><font color=#2b91af size=2><font color=#2b91af size=2>DispId</font></font><font size=2>(0)]

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> onMyImplOfreadystatechange()

{</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>if</font></font><font size=2> (m_XMLHttpObj != </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>)

{</p> 

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> theState = </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>;

theState = m_XMLHttpObj.GetType().InvokeMember(

</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;readyState&#8221;</font></font><font size=2>, System.Reflection.</font><font color=#2b91af size=2><font color=#2b91af size=2>BindingFlags</font></font><font size=2>.GetProperty, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>, m_XMLHttpObj, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>);

</font><font color=#2b91af size=2><font color=#2b91af size=2>MessageBox</font></font><font size=2>.Show(theState.ToString());

</font><font color=#008000 size=2><font color=#008000 size=2>// State 4 means done</font></font><font size=2>

</font><font color=#0000ff size=2><font color=#0000ff size=2>if</font></font><font size=2> ((</font><font color=#0000ff size=2><font color=#0000ff size=2>int</font></font><font size=2>)theState == 4)

{<p mce_keep="true">&nbsp;</p> </p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// done so release the XMLHttpObj</font></font><font size=2>

setObj(

</font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>);

}

}</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>else</font></font><font size=2>

{</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// should not happen!</font></font><font size=2>

</font><font color=#2b91af size=2><font color=#2b91af size=2>MessageBox</font></font><font size=2>.Show(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;XMLHTTP obj not set&#8221;</font></font><font size=2>);

}<p mce_keep="true">&nbsp;</p> 

}</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>public</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> setObj(</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> theObj){m_XMLHttpObj=theObj;}

</font><font color=#0000ff size=2><font color=#0000ff size=2>private</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> m_XMLHttpObj;

}</p> 

</font><font color=#0000ff size=2><font color=#0000ff size=2>private</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> wireXMLHttpReadyState()

{</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// get the DomDocument</font></font><font size=2>

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> aDomObj = webBrowser1.Document.DomDocument;

</font><font color=#0000ff size=2><font color=#0000ff size=2>if</font></font><font size=2> (aDomObj!=</font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>)

{</p> 

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> theScript = aDomObj.GetType().InvokeMember(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;Script&#8221;</font></font><font size=2>, System.Reflection.</font><font color=#2b91af size=2><font color=#2b91af size=2>BindingFlags</font></font><font size=2>.GetProperty, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>, aDomObj, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>);

</font><font color=#0000ff size=2><font color=#0000ff size=2>if</font></font><font size=2> (theScript != </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>)

{</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// Get the script engine interface</font></font><font size=2>

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> theXMLHttpObj = theScript.GetType().InvokeMember(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;xmlHttp&#8221;</font></font><font size=2>, System.Reflection.</font><font color=#2b91af size=2><font color=#2b91af size=2>BindingFlags</font></font><font size=2>.GetProperty, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>, theScript, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>);

</font><font color=#0000ff size=2><font color=#0000ff size=2>if</font></font><font size=2> (theXMLHttpObj != </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>)

{</p> 

</font><font color=#008000 size=2><font color=#008000 size=2>// wrap the Object as an IDispatch COM interface and&#8230;</font></font><font size=2>

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2> toPass = </font><font color=#0000ff size=2><font color=#0000ff size=2>new</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>DispatchWrapper</font></font><font size=2>(</font><font color=#0000ff size=2><font color=#0000ff size=2>new</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>ReadyState</font></font><font size=2>(theXMLHttpObj));

</font><font color=#008000 size=2><font color=#008000 size=2>// pass it to the method in an argument array</font></font><font size=2>

</font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2>[] aArgs = </font><font color=#0000ff size=2><font color=#0000ff size=2>new</font></font><font size=2> </font><font color=#2b91af size=2><font color=#2b91af size=2>Object</font></font><font size=2>[1];

aArgs[0] = toPass;

theXMLHttpObj.GetType().InvokeMember(

</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;onreadystatechange&#8221;</font></font><font size=2>, System.Reflection.</font><font color=#2b91af size=2><font color=#2b91af size=2>BindingFlags</font></font><font size=2>.SetProperty, </font><font color=#0000ff size=2><font color=#0000ff size=2>null</font></font><font size=2>, theXMLHttpObj, aArgs);

}

}

}

}

}

}<p mce_keep="true">&nbsp;</p> 

Sample HTML:

<html>  
<body onload=&#8217;doxmlstuff();&#8217;>  
<script language=&#8221;javascript&#8221;>  
var xmlHttp = null;  
if (window.XMLHttpRequest) {  
&nbsp; // If IE7, Mozilla, Safari, and so on: Use native object.  
&nbsp; xmlHttp = new XMLHttpRequest();  
}  
else  
{  
&nbsp; if (window.ActiveXObject) {  
&nbsp;&nbsp;&nbsp;&nbsp; // &#8230;otherwise, use the ActiveX control for IE5.x and IE6.  
&nbsp;&nbsp;&nbsp;&nbsp; xmlHttp = new ActiveXObject(&#8216;MSXML2.XMLHTTP.3.0&#8217;);  
&nbsp; }  
}  
var MyName = &#8220;Bill Gates&#8221;;  
function ShowName()  
{  
alert(&#8220;MyName = &#8221; + MyName);  
}  
function doxmlstuff()  
{  
&nbsp; if(xmlHttp)  
&nbsp;{&nbsp;

xmlHttp.open(&#8220;GET&#8221;, &#8220;<http://jsandersrvista/test.xml>&#8220;, true);  
xmlHttp.send();  
&nbsp;}  
}  
</script>  
Hello there.<br>  
</body>  
</html>  
&nbsp;<p mce_keep="true">&nbsp;</p> 

</font>