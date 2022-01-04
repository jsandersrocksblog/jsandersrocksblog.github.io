---
id: 3915
title: Image files do not deploy when I add them to ASP.Net project
date: 2017-11-30T16:52:15-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=3915
permalink: /2017/11/30/image-files-do-not-deploy-when-i-add-them-to-asp-net-project/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Image files do not deploy when I add them to ASP.Net project" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/30/image-files-do-not-deploy-when-i-add-them-to-asp-net-project/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You might notice that when you add files like images (.png .bmp) to your project that these are not updating to your Web App (Azure Web App or on premise). Cause This is by design and because of how Visual Studio treats these resources.&nbsp; These types of resources can be bound as resources in..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Image files do not deploy when I add them to ASP.Net project" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/30/image-files-do-not-deploy-when-i-add-them-to-asp-net-project/" />
    <meta name="twitter:description" content="Overview You might notice that when you add files like images (.png .bmp) to your project that these are not updating to your Web App (Azure Web App or on premise). Cause This is by design and because of how Visual Studio treats these resources.&nbsp; These types of resources can be bound as resources in..." />
    
categories:
  - Uncategorized
---


You might notice that when you add files like images (.png .bmp) to your project that these are not updating to your Web App (Azure Web App or on premise).

## Cause

This is by design and because of how Visual Studio treats these resources.&nbsp; These types of resources can be bound as resources in code so they are not included.

## Fix

You need to simply configure the resource to be copied.&nbsp; In the ‘Solution Explorer’ click on the file and change the &#8216;Copy to Output Directory&#8217; to &#8216;Copy if newer&#8217;:

[<img loading="lazy" title="capture20171128075005125" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171128075005125" src="/assets/images/2017/11/capture20171128075005125_thumb.png" width="383" height="542" />](/assets/images/2017/11/capture20171128075005125.png)

This in turn sets the attribute in the .csproj file.&nbsp; So, you could simply edit the .csproj file directly as well!&nbsp; Below is a sample of the csproj file from above.&nbsp; You can see how CUY.jpg is configured in the csproj file as ‘Always’ and this maps to ‘Copy always’.&nbsp; You can also see that ‘Copy if newer’ maps to ‘PreserveNewest’.

[<img loading="lazy" title="capture20171130164912382" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171130164912382" src="/assets/images/2017/11/capture20171130164912382_thumb.png" width="555" height="491" />](/assets/images/2017/11/capture20171130164912382.png)

**Drop me a note if you found this useful!**