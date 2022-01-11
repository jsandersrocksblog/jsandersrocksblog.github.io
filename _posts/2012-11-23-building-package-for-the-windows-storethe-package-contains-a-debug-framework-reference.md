I was helping a customer with a problem they were encountering when trying to build a package for submission to the Windows App Store.&#160; The error was:

“The package contains a Debug framework reference”.&#160; To make a long story short the solution is simple.

The problem was that even though the project was set to Release for the solution configuration (in the Configuration Manager), the Project (here ‘CanvasSize’) configuration was set to Debug.

&#160;

&#160;

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0728.image_79E1A0C3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0728.image_5F00_79E1A0C3.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7331.image_thumb_19244797.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7331.image_5F00_thumb_5F00_19244797.png" width="581" height="285" /></a>

&#160;

The fix is simple!&#160; Just change the Configuration for the Project and any other project in the solution to Release!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8233.image_261E27A8.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8233.image_5F00_261E27A8.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3122.image_thumb_3EADC4F8.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3122.image_5F00_thumb_5F00_3EADC4F8.png" width="586" height="261" /></a>

&#160;

Let me know if this help you by adding a comment!

-Jeff