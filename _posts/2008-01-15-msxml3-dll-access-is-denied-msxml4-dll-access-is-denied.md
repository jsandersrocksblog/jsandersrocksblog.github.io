The following vb Script can fail with an &#8220;Access is denied&#8221; error message:

Dim aRequest  
Set aRequest = CreateObject (&#8220;Microsoft.XMLHTTP&#8221;)  
aRequest.Open &#8220;POST&#8221;,&#8221;<a href="http://www.contoso.com/PostAccepter.aspx%22,False" mce_href="http://www.contoso.com/PostAccepter.aspx%22,False">http://www.contoso.com/PostAccepter.aspx&#8221;,False</a>  
aRequest.setRequestHeader &#8220;Content-Type&#8221;, &#8220;application/x-www-form-urlencoded&#8221;  
aRequest.Send &#8220;this is data&#8221;  
Wscript.Echo aRequest.responseText

If you use Fiddler (<a href="http://fiddler2.com/" mce_href="http://fiddler2.com/">http://fiddler2.com</a>) you will see a comple of redirects to Microsoft.com.&nbsp; That is the reason for this failure in my case.&nbsp; By clearing the flag in Internet Explorer for that internet zone that prevents this POST (Access data sources across domains), I am able to run again.

<table class="list ol" class="list ol">
  <tr>
    <td class=number class="number">1.</td> <td class=text class="text">In Internet Explorer, click <b>Internet Options</b> on the <b>Tools</b> menu.</td>
  </tr>
  
  <tr>
    <td class=number class="number">2.</td> <td class=text class="text">On the <b>Security</b> tab, click <b>Trusted</b> sites, and then click <b>Sites</b>.</td>
  </tr>
  
  <tr>
    <td class=number class="number">3.</td> <td class=text class="text">Add your site to the zone.</td>
  </tr>
  
  <tr>
    <td class=number class="number">4.</td> <td class=text class="text">Click <b>Custom Level</b>.</td>
  </tr>
  
  <tr>
    <td class=number class="number">5.</td> <td class=text class="text">Under <strong class=uiterm>Miscellaneous/Access data sources across domains</strong>, click <b>Enable</b>.</td>
  </tr>
</table><p mce_keep="true">&nbsp;</p> <p mce_keep="true">see 

<http://msdn.microsoft.com/en-us/library/cc507438(VS.85).aspx>&nbsp;(security model)</p> <p mce_keep="true">also see <font size=2><http://support.microsoft.com/?id=820882></font></p> <p mce_keep="true"><font size=2>&nbsp;</p> 

</font>