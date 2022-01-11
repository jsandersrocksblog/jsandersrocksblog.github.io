I had an interesting case that I want to share in the event anyone else experiences this problem.&#160; In this case a Symantec certificate stored on a SafeNet USB dongle was being used to sign a Windows Store app in Visual Studio.&#160; The signing was failing.&#160; Visual Studio reported: “SignTool Error:&#160; An unexpected internal error has occurred”.&#160; These guidelines were followed and everything seemed in order:

<http://msdn.microsoft.com/en-us/library/windows/apps/br230260(v=vs.110).aspx>

During packaging, Visual Studio validates the specified certificate in the following ways:

· Verifies the presence of the Basic Constraints extension and its value, which must be either Subject Type=End Entity or unspecified.

· Verifies the value of the Enhanced Key Usage property, which must contain Code Signing and may also contain Lifetime Signing. Any other EKUs are prohibited.

· Verifies the value of the KeyUsage (KU) property, which must be either Unset or DigitalSignature.

· Verifies the existence of a private key exists.

· Verifies whether the certificate is active, hasn’t expired, and hasn&#8217;t been revoked.

## Solution

I used Process Monitor (Procmon) to determine the command line that was being used and then using the command line SignTool.exe to issue the same command, saw that it was returning this:&#160; Error: SignerSign() failed." (-1073741275/0xc0000225)

SafeNet had the solution for this problem.&#160; Using the SafeNet Client Authentication tools it was found that there were ‘Orphan Objects’ on the device.&#160; Removing these resulted in being able to use this device to sign the application successfully!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2235.SafeNet_0EB846FA.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2235.SafeNet_5F00_0EB846FA.png"><img loading="lazy" title="SafeNet" style="display: inline; background-image: none;" border="0" alt="SafeNet" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3240.SafeNet_thumb_59AE487A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3240.SafeNet_5F00_thumb_5F00_59AE487A.png" width="489" height="378" /></a>

Let me know if this helps you out!