Knowing the server type and what it is running can be information that an attacker may leverage.  This article explains how you can remove the subject headers.  
Azure Mobile Apps are really Azure Web Apps.  You can configure the headers by altering the Web.Config just like you would with a standard ASP.Net application!

## Problem

Here is an example of the headers returned from a simple Azure Mobile App (replace _contosomobileapp_ with the name of your Mobile app):  
<span style="font-family: Calibri">HTTP/1.1 200 OK<br /> Cache-Control: no-cache<br /> Pragma: no-cache<br /> Content-Length: 422<br /> Content-Type: application/json; charset=utf-8<br /> Expires: 0<br /> </span><span style="font-family: Calibri"><span style="background-color: #ffff00">Server: Microsoft-IIS/8.0<br /> X-Powered-By: ASP.NET<br /> </span>Set-Cookie: ARRAffinity=df41f72d5dafaca237feeeb4df546bb62b24197ead56d3e53c2496c1f90fe094;Path=/;Domain=contosomobileapp.azurewebsites.net<br /> Date: Wed, 07 Oct 2015 13:13:57 GMT<br /> </span>

## Solution

Open the site **Web.Config** in your Visual Studio project and find the **<system.webServer_>_** section  
[<img loading="lazy" width="782" height="273" title="snip_20151007093103" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="snip_20151007093103" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4377.snip_20151007093103_thumb_6EA63E29.png" border="0" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0638.snip_20151007093103_17AE4C75.png)  
Add these two sections inside this section:  
**<a>Copy Code:</a>** 

<pre class="code" id="CopyCodeCodeSectionRemoveHeaders1"><span style="background: white;color: blue">    &lt;</span><span style="background: white;color: #a31515">security</span><span style="background: white;color: blue">&gt;
      &lt;</span><span style="background: white;color: #a31515">requestFiltering </span><span style="background: white;color: red">removeServerHeader </span><span style="background: white;color: blue">=</span><span style="background: white;color: black">"</span><span style="background: white;color: blue">true</span><span style="background: white;color: black">"</span><span style="background: white;color: blue">&gt;&lt;/</span><span style="background: white;color: #a31515">requestFiltering</span><span style="background: white;color: blue">&gt;
    &lt;/</span><span style="background: white;color: #a31515">security</span><span style="background: white;color: blue">&gt;
    &lt;</span><span style="background: white;color: #a31515">httpProtocol</span><span style="background: white;color: blue">&gt;
      &lt;</span><span style="background: white;color: #a31515">customHeaders</span><span style="background: white;color: blue">&gt;
        &lt;</span><span style="background: white;color: #a31515">remove </span><span style="background: white;color: red">name</span><span style="background: white;color: blue">=</span><span style="background: white;color: black">"</span><span style="background: white;color: blue">X-Powered-By</span><span style="background: white;color: black">"</span><span style="background: white;color: blue">/&gt;
      &lt;/</span><span style="background: white;color: #a31515">customHeaders</span><span style="background: white;color: blue">&gt;
    &lt;/</span><span style="background: white;color: #a31515">httpProtocol</span><span style="background: white;color: blue">&gt;
</span></pre>

So the final Web.Config section will look something like this:  
[<img loading="lazy" width="702" height="370" title="snip_20151007095619" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="snip_20151007095619" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4152.snip_20151007095619_thumb_07386C2B.png" border="0" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8688.snip_20151007095619_2BC9F9AF.png)  
(you can ignore the squiggle under _removeServerHeader_)  
Now right mouse click on the Web.Config in your _Solution Explorer_ view and choose publish:  
[<img loading="lazy" width="518" height="355" title="Untitled" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="Untitled" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5165.Untitled_thumb_4F85B1FA.png" border="0" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4857.Untitled_;627C.png)

## Result

The headers are removed:  
<span style="font-family: Calibri">HTTP/1.1 200 OK<br /> Cache-Control: no-cache </span>  
Pragma: no-cache  
Content-Length: 422  
Content-Type: application/json; charset=utf-8  
Expires: 0  
Set-Cookie: ARRAffinity=df41f72d5dafaca237feeeb4df546bb62b24197ead56d3e53c2496c1f90fe094;Path=/;Domain=contosomobileapp.azurewebsites.net  
Date: Wed, 07 Oct 2015 13:19:07 GMT  
&nbsp;

## Conclusion

<span style="font-family: Calibri">As you can see Azure Mobile Apps are really Azure Web Sites with some additional code to access and present data.  You can easily configure your Azure Mobile App using the Web.Config like you would for an ASP.Net app deployed on Azure Web Sites.</span>  
<span style="font-family: Calibri">Let me know if this was a help to you!  Also see this post:</span>

<blockquote class="wp-embedded-content" data-secret="wtIyT64SgM">
  <p>
    <a href="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/">How to deny HTTP methods (or verbs) in Azure Web Apps</a>
  </p>
</blockquote>

  
&nbsp;  
<span style="font-family: Calibri">Ref: <a href="https://azure.microsoft.com/en-us/blog/removing-standard-server-headers-on-windows-azure-web-sites/" title="https://azure.microsoft.com/en-us/blog/removing-standard-server-headers-on-windows-azure-web-sites/">https://azure.microsoft.com/en-us/blog/removing-standard-server-headers-on-windows-azure-web-sites/</a></span>