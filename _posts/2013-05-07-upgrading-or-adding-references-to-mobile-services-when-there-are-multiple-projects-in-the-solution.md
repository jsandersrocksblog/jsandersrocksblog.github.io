When you have multiple projects in a solution (for example a Phone and Windows Store app) and you need to add a reference using nuget for each of them there are two methods you can choose from.&#160; You can use the command line using the <a href="http://docs.nuget.org/docs/start-here/using-the-package-manager-console" target="_blank">Package Manager Console</a> or you can <a href="http://docs.nuget.org/docs/start-here/Managing-NuGet-Packages-Using-The-Dialog" target="_blank">Use the Dialog</a>.&#160; Note: The latest version of Windows Azure Mobile Services is here: <a title="http://nuget.org/packages/WindowsAzure.MobileServices" href="http://nuget.org/packages/WindowsAzure.MobileServices" target="_blank">http://nuget.org/packages/WindowsAzure.MobileServices</a>.

The important thing to remember is that you need to do this for each project in the solution.&#160; In the Package Manager Console you need to select each project that needs to be updated and execute the command.&#160; You do this by choosing each project from the ‘Default Project’ pull down shown below:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5040.image_49BE6F47.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5040.image_5F00_49BE6F47.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4456.image_thumb_13D97A2D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4456.image_5F00_thumb_5F00_13D97A2D.png" width="643" height="169" /></a>

And executing the command: Install-Package WindowsAzure.MobileServices –Pre

For the dialog you right click on the ‘References’ node for each project (see Use the Dialog link in the opening paragraph) and use the dialog!

If this saved you some time let me know!

-Jeff