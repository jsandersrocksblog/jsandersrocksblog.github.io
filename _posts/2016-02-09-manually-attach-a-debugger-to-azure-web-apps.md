For various reasons you may have difficulty attaching your debugger to an Azure Web App.&nbsp; This quick blog will show you a method that may work for you if you get into this situation.&nbsp; I will NOT attempt to diagnose your issue in this blog so please don’t post a question asking why the normal methods don’t work for you (like right clicking your resource in Server Explorer of Visual Studio).

Ensure you have enabled debugging in the Azure Portal for your App and it is set to the correct version of Visual Studio (don’t forget to save):

[<img loading="lazy" title="snip_20170606155727" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170606155727" src="/assets/images/2017/06/snip_20170606155727_thumb.png" width="650" height="279" />](/assets/images/2017/06/snip_20170606155727.png)

Note:&nbsp; 

Please also make sure when deploying the app, Debug configuration is selected.&nbsp; For example: in Visual Studio Web Deploy…[<img loading="lazy" title="snip_20170322133336" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170322133336" src="/assets/images/2017/03/snip_20170322133336_thumb.png" width="569" height="272" />](/assets/images/2017/03/snip_20170322133336.png) 

&nbsp;

Step 1. From the main menu, click on the **Debug** menu item and select **Attach to Process …**

****

&nbsp;

[<img loading="lazy" title="snip_20160209113425" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20160209113425" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0576.snip_20160209113425_thumb_4EF4B455.png" width="608" height="248" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4452.snip_20160209113425_3A6F64D7.png)

Determine the remote debugging port from this article:&nbsp; <a href="https://docs.microsoft.com/en-us/visualstudio/debugger/remote-debugger-port-assignments" target="_blank">Visual Studio remote debugger port assignments</a>.&nbsp; For example, Visual Studio 2015 uses port 4020.

Type in the URL of your Azure Web App and add the port determined above then hit enter and a credential dialog will appear:

[<img loading="lazy" title="snip_20160209114253" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20160209114253" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2671.snip_20160209114253_thumb_3E7C435A.png" width="604" height="270" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3247.snip_20160209114253_755697A0.png)

For the User name and Password you can download the Publish Profile and extract it from there:

[<img loading="lazy" title="snip_20160209114840" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20160209114840" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7002.snip_20160209114840_thumb_72B06CA0.png" width="519" height="165" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6708.snip_20160209114840_04F93363.png)

Look for “userName” and “userPWD” in that file.&nbsp; Note when you enter the user name you will need to also include the domain.&nbsp; For example: if the username is ‘$constowebapp’ when you enter it in the credential dialog it should be entered like this ‘$contosowebapp\$contosowebapp’.

Now that you are authenticated choose the w3wp.exe process (Standard .NET app):

[<img loading="lazy" title="snip_20160209115800" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20160209115800" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8816.snip_20160209115800_thumb_5B84F222.png" width="554" height="137" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2021.snip_20160209115800_26E495E7.png)

For a .NET core app you will want to ensure you choose Managed(v4.6, v4.5, v4.0) code and then the name of the Core app (not w3wp.exe):

[<img loading="lazy" title="clip_image002[6]" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="clip_image002[6]" src="/assets/images/2017/03/clip_image0026_thumb.jpg" width="626" height="362" />](/assets/images/2017/03/clip_image00261.jpg)

&nbsp;

I know this was a quick and dirty blog but let me know if this helped you out.&nbsp; Again… My intent is not to troubleshoot your connection issues (firewall could be in the way, invalid or outdated publish profile could be associated with your app… The list goes on and on) but to get you unblocked so you can debug!