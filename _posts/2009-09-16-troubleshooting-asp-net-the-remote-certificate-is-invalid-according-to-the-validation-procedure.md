This error message is caused because the process is not being able to validate the Server Certificate supplied by the Server during an HTTPS (SSL) request.&nbsp; The very first troubleshooting step should be to see if the server supplied certificate and every certificate in the chain is trouble free.

**Example 1 – Root Certificate only (self signed certificate in this case)**

**Step 1 – Validate the certificate, any intermediate certificates and the root certificate**

One super handy and technical tool to help you do this first step is Internet Explorer.&nbsp; Simply try to hit the same URL that your ASP.NET web application tries to hit when it gets this error.&nbsp; For example, type in to the browser the path to the .asmx file and see what Internet Explorer says about the certificate. 

This would be a bad sign:

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_2.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_2.png"><img loading="lazy" style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb.png" width="743" height="322" /></a> 

If Internet Explorer has certificate problems, chances are you will have problems with the HttpWebRequest (or Web Service) call as well.&nbsp; The easiest fix is to install a valid certificate for the server, the root authority and all intermediate authorities.&nbsp; Then go back and verify Internet Explorer can access the https site with no errors at all.

If you continue to the site using Internet Explorer, sometimes you can diagnose the certificate problem by viewing the certificate.&nbsp; In this example the problem is spelled out for me when I typed in <https://jsanders4>.

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_4.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_4.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_1.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_1.png" width="336" height="419" /></a> 

So in my case, it appears that the I simply need to install the certificate in the ‘Trusted Root Certification Authorities’ store.&nbsp; So indeed I do this!

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_6.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_6.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_2.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_2.png" width="244" height="222" /></a>&nbsp; <a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_8.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_8.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_3.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_3.png" width="244" height="222" /></a>&nbsp; <a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_10.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_10.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_4.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_4.png" width="244" height="223" /></a> 

But I still got the certificate error…&nbsp; To avoid a long discussion about this, the problem is simple.&nbsp; I typed in <https://jsanders4> but note the certificate is for the full domain name of this machine.&nbsp; If I instead browse to <https://jsanders4.northamerica.corp.microsoft.com> then I get no certificate error.&nbsp; Now that I am sure I can browse ok to the site with no certificate errors using Internet Explorer.

You would continue to solve problems with the other Certificates in the Certificate chain by using Internet Explorer until they are all resolved.&nbsp; For example, perhaps the certificate is expired, or the Intermediate Authority is not in the Intermediate Certificate Authorities store (a very common one).&nbsp; Once you have resolved all errors with Internet Explorer your are only half way finished.&nbsp; You need to get the same information into the Local Computer store.

**Step 2 – Troubleshoot the ASP.NET problem**

I try my ASP.NET application and try to access the same site.&nbsp; I get this error: ‘The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.’

But Internet Explorer was fine… 

The next step should be to get a System.Net trace.&nbsp; To do this open the Web.Config for the troubled ASP.NET application and see if there is a <configuration> section in the file.&nbsp; If there is, add the contents inside the <configuration> </configuration> tags from this blog: [http://blogs.msdn.com/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx](http://blogs.msdn.com/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx "http://blogs.msdn.com/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx").&nbsp; If it does not exist, add the entire contents before the closing tag of the Web.Config.&nbsp; Now edit this line:&nbsp;&nbsp; initializeData=&#8221;System.Net.trace.log&#8221;&nbsp; You must ensure that the Network Service a  
ccount can write this .log so change this entry to a folder that the Network Service account can write to.&nbsp; For example, I created a folder c:\mylogs and assigned the Network Service account FULL privileges.&nbsp; Then changed this setting to initializeData=&#8221;c:\mylogs\System.Net.trace.log&#8221;

I ran the asp.net application and saw at the end of the log file (c:\mylogs\System.Net.trace.log) this information:

System.Net Information: 0 : [0880] SecureChannel#14701405 &#8211; Remote certificate has errors:  
&nbsp;&nbsp;&nbsp; ProcessId=5700  
&nbsp;&nbsp;&nbsp; DateTime=2009-09-16T12:54:06.5718699Z  
System.Net Information: 0 : [0880] SecureChannel#14701405 &#8211;&nbsp;&nbsp;&nbsp;&nbsp; A certificate chain processed, but terminated in a root certificate which is not trusted by the trust provider. 

&nbsp;&nbsp;&nbsp; ProcessId=5700  
&nbsp;&nbsp;&nbsp; DateTime=2009-09-16T12:54:06.5718699Z  
System.Net Information: 0 : [0880] SecureChannel#14701405 &#8211; Remote certificate was verified as invalid by the user.  
&nbsp;&nbsp;&nbsp; ProcessId=5700  
&nbsp;&nbsp;&nbsp; DateTime=2009-09-16T12:54:06.5718699Z  
System.Net.Sockets Verbose: 0 : [0880] Socket#26833123::Dispose()  
&nbsp;&nbsp;&nbsp; ProcessId=5700  
&nbsp;&nbsp;&nbsp; DateTime=2009-09-16T12:54:06.5718699Z  
System.Net Error: 0 : [0880] Exception in the HttpWebRequest#31364015:: &#8211; The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.  
&nbsp;&nbsp;&nbsp; ProcessId=5700  
&nbsp;&nbsp;&nbsp; DateTime=2009-09-16T12:54:06.5718699Z 

This is the key to this particular problem:&nbsp; A certificate chain processed, but terminated in a root certificate which is not trusted by the trust provider. 

However I thought I just added this certificate trough Internet Explore to my Trusted Root Authorities!&nbsp; In reality I simply added it so the store of the logged on user.&nbsp; ASP.NET is running in the local machine context.&nbsp; To resolve this, start MMC (Windows key + R and type MMC) and add the following snap-ins:

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_12.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_12.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_5.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_5.png" width="244" height="143" /></a> <a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_14.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_14.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_6.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_6.png" width="244" height="149" /></a>&nbsp;<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_18.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_18.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_8.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_8.png" width="244" height="151" /></a> 

And ensure you see the ‘Current User’ and ‘(Local Computer)’ Certificates listed (then hit OK):

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_20.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_20.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_9.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_9.png" width="244" height="185" /></a> 

In the console expand the ‘Current User’ Trusted Root store and you see I have the certificate stored there.&nbsp; However expanding the ‘(Local Computer)’ trusted root, it is NOT there:

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_22.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_22.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_10.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_10.png" width="244" height="195" /></a> <a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_24.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_24.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_11.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_11.png" width="238" height="244" /></a>

Simply Copy (do not Drag and drop) the jsanders4 certificate from the Current User\Trusted Root store to the (Local Computer)\Trusted Root store and retest.&nbsp; 

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_26.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_26.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremote
certificateisinvalidacco_D4C1/image_thumb_12.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_12.png" width="244" height="152" /></a> <a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_28.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_28.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_13.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_13.png" width="244" height="147" /></a> 

Success!

**Example 2 – Intermediate Certificate Authorities Involved**

This next example is a bit manufactured but illustrates a problem that I have had to help solve a few times.&nbsp; The trouble shooting steps remain the same, but in this case there are one or more intermediate certificates.&nbsp; This intermediate certificates should be in the ‘Intermediate Certification Authorities’ store to resolve this problem Take a look at the certificate chain for <https://www.microsoft.com> (you do this by clicking on the padlock icon in Internet Explorer and choosing the Certification Path tab:

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_30.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_30.png"><img loading="lazy" style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_14.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Tro.NETTheremotecertificateisinvalidacco_D4C1/image_thumb_14.png" width="244" height="167" /></a>&nbsp;

For the purpose of this example, assume that the three certificates that are not highlighted all have a warning icon next to them indicating a problem.

**Step 1 – Validate the certificate, any intermediate certificates and the root certificate**

Note: For Internet Explorer there actually was no problem with the certification path.&nbsp; The four certificates show no warning icons.&nbsp; For _this_ example, let’s say that the ‘GTE CyberTrust Global Root’, ‘Microsoft Internet Authority’ and ‘Microsoft Secure Server Authority’ certificates were all missing from my ‘Current User’ stores.&nbsp; The steps below are contrived from this assumption.

To fix this I add the ‘GTE CyberTrust Global Root’ cert to the ‘Trusted Root Certification Authorities’ Store and the other two certificates to the ‘Intermediate Certification Authorities’ store of the Current User.&nbsp; Test with IE again and Internet Explorer shows no problem after installing the certificates.&nbsp; Next when I tested the ASP.NET application I got an error (because I did not add these certificates to the same stores in the (Local Computer) store).

**Step 2 – Troubleshoot the ASP.NET problem**

From the first example I was smart enough to copy the ‘GTE CyberTrust Global Root’ certificate to the ‘(Local Computer)’ trusted root store but I still have an error!

The ASP.NET program now has an error: System.Net.WebException: The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel. &#8212;> System.Security.Authentication.AuthenticationException: The remote certificate is invalid according to the validation procedure.

Again taking the System.Net trace you see an error towards the end of the file in these entries:

Remote certificate has errors:  
A certificate chain could not be built to a trusted root authority.  
Remote certificate was verified as invalid by the user.  
The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel. 

_This entry is the key:_ ‘A certificate chain could not be built to a trusted root authority.’&nbsp; This means that a certificate before the Root Authority is not in the ‘(Local Computer) Intermediate Certification Authorities’ store.&nbsp; Once the two intermediate certificates are copied to the Intermediate store from the Current User intermediate store the problem is solved! 

I hope this blog helped you get to the root of your problem.&nbsp; If this was helpful please leave me a comment!