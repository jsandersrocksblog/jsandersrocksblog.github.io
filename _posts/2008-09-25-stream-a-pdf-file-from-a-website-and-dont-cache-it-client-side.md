I had an issue where someone wanted to stream a file that was generated on the web server and prevent it from caching on the client.&nbsp; The correct way to do this is to specify the Cache-Control: no-cache header.&nbsp; When this was done however the pdf file did not display using https and on Windows XP.&nbsp; After some research the method that worked for this scenario was to define an OBJECT tag and point the SRC attribute to the page that generates the file on the fly.

&nbsp;Example code:

This is an example of the failing page:

<font size=2>

<%</font><font color=#0000ff size=2>@</font><font size=2> </font><font color=#a31515 size=2>Page</font><font size=2> </font><font color=#ff0000 size=2>Language</font><font color=#0000ff size=2>=&#8221;C#&#8221;</font><font size=2> %>  
</font><font color=#0000ff size=2><!</font><font color=#a31515 size=2>DOCTYPE</font><font size=2> </font><font color=#ff0000 size=2>html</font><font size=2> </font><font color=#ff0000 size=2>PUBLIC</font><font size=2> </font><font color=#0000ff size=2>&#8220;-//W3C//DTD XHTML 1.0 Transitional//EN&#8221;</font><font size=2> </font><font color=#0000ff size=2>&#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&#8221;>  
<</font><font color=#a31515 size=2>script</font><font size=2> </font><font color=#ff0000 size=2>runat</font><font color=#0000ff size=2>=&#8221;server&#8221;>  
</font><font size=2>

</font><font color=#0000ff size=2>protected</font><font size=2> </font><font color=#0000ff size=2>void</font><font size=2> Button1_Click(</font><font color=#0000ff size=2>object</font><font size=2> sender, </font><font color=#2b91af size=2>EventArgs</font><font size=2> e)  
{

Response.ContentType = </font><font color=#a31515 size=2>&#8220;application/pdf&#8221;</font><font size=2>;  
Response.Clear();</font>  
<font size=2>Response.TransmitFile(</font><font color=#a31515 size=2>&#8220;leopardsupport.pdf&#8221;</font><font size=2>);  
Response.End(); </font>

<font size=2>}

</font><font color=#0000ff size=2>

</</font><font color=#a31515 size=2>script</font><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>html</font><font size=2> </font><font color=#ff0000 size=2>xmlns</font><font color=#0000ff size=2>=&#8221;http://www.w3.org/1999/xhtml&#8221;>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<</font><font color=#a31515 size=2>head</font><font size=2> </font><font color=#ff0000 size=2>runat</font><font color=#0000ff size=2>=&#8221;server&#8221;>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>title</font><font color=#0000ff size=2>></font><font size=2>Untitled Page</font><font color=#0000ff size=2></</font><font color=#a31515 size=2>title</font><font color=#0000ff size=2>></font>  
<font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </</font><font color=#a31515 size=2>head</font><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>body</font><font color=#0000ff size=2>>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>form</font><font size=2> </font><font color=#ff0000 size=2>id</font><font color=#0000ff size=2>=&#8221;form1&#8243;</font><font size=2> </font><font color=#ff0000 size=2>runat</font><font color=#0000ff size=2>=&#8221;server&#8221;>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>div</font><font color=#0000ff size=2>>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </</font><font color=#a31515 size=2>div</font><font color=#0000ff size=2>>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <</font><font color=#a31515 size=2>asp</font><font color=#0000ff size=2>:</font><font color=#a31515 size=2>Button</font><font size=2> </font><font color=#ff0000 size=2>ID</font><font color=#0000ff size=2>=&#8221;Button1&#8243;</font><font size=2> </font><font color=#ff0000 size=2>runat</font><font color=#0000ff size=2>=&#8221;server&#8221;</font><font size=2> </font><font color=#ff0000 size=2>style</font><font color=#0000ff size=2>=&#8221;</font><font color=#ff0000 size=2>margin-bottom</font><font size=2>: </font><font color=#0000ff size=2>0px&#8221;</font><font size=2>  
</font><font color=#ff0000 size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Text</font><font color=#0000ff size=2>=&#8221;Button&#8221;</font><font size=2> </font><font color=#ff0000 size=2>onclick</font><font color=#0000ff size=2>=&#8221;Button1_Click&#8221;</font><font size=2> </font><font color=#0000ff size=2>/>  
</font><font size=2></font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </</font><font color=#a31515 size=2>form</font><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp; </</font><font color=#a31515 size=2>body</font><font color=#0000ff size=2>>  
</</font><font color=#a31515 size=2>html</font><font color=#0000ff size=2>>  
</font>&nbsp;

This is the solution:

The source page:

<font color=#0000ff size=2><font color=#0000ff size=2>

<</font></font><font color=#a31515 size=2><font color=#a31515 size=2>html</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; <</font></font><font color=#a31515 size=2><font color=#a31515 size=2>head</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font></font><font size=2></font><font color=#0000ff size=2><font color=#0000ff size=2><</font></font><font color=#a31515 size=2><font color=#a31515 size=2>title</font></font><font color=#0000ff size=2><font color=#0000ff size=2>></font></font><font size=2>PDF File</font><font color=#0000ff size=2><font color=#0000ff size=2></</font></font><font color=#a31515 size=2><font color=#a31515 size=2>title</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp; </</font></font><font color=#a31515 size=2><font color=#a31515 size=2>head</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>

&nbsp;&nbsp;&nbsp; <</font></font><font color=#a31515 size=2><font color=#a31515 size=2>body</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <</font></font><font color=#a31515 size=2><font color=#a31515 size=2>object</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>CLASSID</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8217;clsid:CA8A9780-280D-11CF-A24D-444553540000&#8242;</font></font><font size=2>  
</font><font color=#ff0000 size=2><font color=#ff0000 size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; TYPE</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8217;application/pdf&#8217;</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>style</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8217;</font></font><font color=#ff0000 size=2><font color=#ff0000 size=2>width</font></font><font size=2>: </font><font color=#0000ff size=2><font color=#0000ff size=2>100%</font></font><font size=2>; </font><font color=#ff0000 size=2><font color=#ff0000 size=2>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; height</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>100%</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>position</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>absolute</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>top</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>0px</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>left</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>0px</font></font><font size=2>;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font><font color=#ff0000 size=2><font color=#ff0000 size=2>margin</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>0px</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>padding</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>0px</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>border</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>0px</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>right</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>580px</font></font><font size=2>;</font><font color=#ff0000 size=2><font color=#ff0000 size=2>bottom</font></font><font size=2>:</font><font color=#0000ff size=2><font color=#0000ff size=2>500px</font></font><font size=2>;</font><font color=#0000ff size=2><font color=#0000ff size=2>&#8216;>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font></font><font size=2></font><font color=#0000ff size=2><font color=#0000ff size=2><</font></font><font color=#a31515 size=2><font color=#a31515 size=2>PARAM</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>NAME</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8217;src&#8217;</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>VALUE</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8217;https://MYSERVER/PDFDnld/DownloadWorker.aspx&#8217;>  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </</font></font><font color=#a31515 size=2><font color=#a31515 size=2>object</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
</font></font><font color=#0000ff size=2><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; </</font></font><font color=#a31515 size=2><font color=#a31515 size=2>body</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>  
</</font></font><font color=#a31515 size=2><font color=#a31515 size=2>html</font></font><font color=#0000ff size=2><font color=#0000ff size=2>></font></font>

<font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>Here is the page generating the pdf file:</font></font></font>

<font size=2>

<%</font><font color=#0000ff size=2><font color=#0000ff size=2>@</font></font><font size=2> </font><font color=#a31515 size=2><font color=#a31515 size=2>Page</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>Language</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8221;C#&#8221;</font></font><font size=2> %>  
</font><font color=#0000ff size=2><font color=#0000ff size=2><!</font></font><font color=#a31515 size=2><font color=#a31515 size=2>DOCTYPE</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>html</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>PUBLIC</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>&#8220;-//W3C//DTD XHTML 1.0 Transitional//EN&#8221;</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>&#8220;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&#8221;>  
<</font></font><font color=#a31515 size=2><font color=#a31515 size=2>script</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>runat</font></font><font color=#0000ff size=2><font color=#0000ff size=2>=&#8221;server&#8221;>

</font></font><font size=2>

</font><font color=#0000ff size=2><font color=#0000ff size=2>protected</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>void</font></font><font size=2> Page_Load(</font><font color=#0000ff size=2><font color=#0000ff size=2>object</font></font><font size=2> sender, </font><font color=#2b91af size=2><font color=#2b91af size=2>EventArgs</font></font><font size=2> e)</font>  
<font size=2>{

&nbsp;&nbsp;&nbsp; Response.ContentType = </font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;application/pdf&#8221;</font></font><font size=2>;  
&nbsp;&nbsp;&nbsp; Response.Clear();  
&nbsp;&nbsp;&nbsp; Response.TransmitFile(</font><font color=#a31515 size=2><font color=#a31515 size=2>&#8220;temp.pdf&#8221;</font></font><font size=2>);  
&nbsp;&nbsp;&nbsp; Response.End(); 

}

</font><font color=#0000ff size=2><font color=#0000ff size=2>

</</font></font><font color=#a31515 size=2><font color=#a31515 size=2>script</font></font><font color=#0000ff size=2><font color=#0000ff size=2>>

<font color=#0000ff size=2><font color=#0000ff size=2><font color=#000000>You could of course stream&nbsp;a pdf file&nbsp;generated on the fly instead of using TransmitFile.</font></font></font>

<font color=#000000>The reason this works is because the href that is used in the object tag works around the issue per this KB article: <a href="http://support.microsoft.com/kb/323308" mce_href="http://support.microsoft.com/kb/323308">http://support.microsoft.com/kb/323308</a>&nbsp;&#8220;Internet Explorer file downloads over SSL do not work with the cache control headers&#8221; (see workaround section).&nbsp; This would apply for the no-store header as well.</font>

<font color=#000000>Let me know if this BLOG entry helped you!</font>

<font color=#000000></font>&nbsp;

</font></font>