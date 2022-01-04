---
id: 83
title: Create a Staging .NET Backend for Testing
date: 2014-04-09T12:07:06-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2014/04/09/create-a-staging-net-backend-for-testing/
permalink: /2014/04/09/create-a-staging-net-backend-for-testing/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
orig_site_id:
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
orig_post_id:
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
orig_parent_id:
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
  - "10515802"
orig_thread_id:
  - "869592"
  - "869592"
  - "869592"
  - "869592"
  - "869592"
  - "869592"
  - "869592"
  - "869592"
  - "869592"
orig_application_key:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_id:
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
orig_post_author_username:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_created:
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
orig_is_approved:
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
orig_attachment_count:
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
orig_url_title:
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/04/09/create-a-staging-net-backend-for-testing.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Create a Staging .NET Backend for Testing" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Create a Staging .NET Backend for Testing" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/04/09/create-a-staging-net-backend-for-testing/" />
    <meta name="twitter:description" content="Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" />
    
categories:
  - Uncategorized
tags:
  - Windows Azure Mobile Services
---
Debugging on your Live Service is bad!&#160; For instance if you are breaking in the debugger while one of your users is trying to get data, that call will likely timeout.&#160; Also it is difficult to isolate an issue if multiple unplanned requests are coming into your service.&#160; If you have some things you need to test or debug with your .NET backend, you can easily publish your .NET Backend code to a ‘Staging’ service to do your debugging.

### Setup

From your .NET Backend project choose publish, but click ‘Windows Azure Mobile Services’ (under ‘Select a publish target’) to publish to a new Mobile Service.

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1817.image_2E0BD60B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1817.image_5F00_2E0BD60B.png"><img loading="lazy" title="image" style="border-top: 0px; border-right: 0px; border-bottom: 0px; border-left: 0px; display: inline" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7215.image_thumb_3DAE71CD.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7215.image_5F00_thumb_5F00_3DAE71CD.png" width="487" height="382" /></a> 

Hit ‘New…’ to create a new mobile service

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3823.image_14A66382.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3823.image_5F00_14A66382.png"><img loading="lazy" title="image" style="border-top: 0px; border-right: 0px; border-bottom: 0px; border-left: 0px; display: inline" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0207.image_thumb_56ACD2C3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0207.image_5F00_thumb_5F00_56ACD2C3.png" width="501" height="298" /></a> 

Give it a name (I like Staging-<<NAME OF LIVE SERVICE HERE>>)

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8662.image_7FB771BF.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8662.image_5F00_7FB771BF.png"><img loading="lazy" title="image" style="border-top: 0px; border-right: 0px; border-bottom: 0px; border-left: 0px; display: inline" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3302.image_thumb_45C82ED3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3302.image_5F00_thumb_5F00_45C82ED3.png" width="475" height="525" /></a> 

Publish it!

And now you can debug it!

### Debug

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6567.image_2A926683.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6567.image_5F00_2A926683.png"><img loading="lazy" title="image" style="border-top: 0px; border-right: 0px; border-bottom: 0px; border-left: 0px; display: inline" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0118.image_thumb_77C&#038;E.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0118.image_5F00_thumb_5F00_77C2600E.png" width="462" height="298" /></a> 

### Notes

This is just a quick publish blog to give you some ideas.&#160; Keep the feedback coming and we can improve this post together!

By using a ‘Staging’ area you will not disrupt your service operations.

You can copy the Azure DB data to the new DB that was created, but that is beyond the scope of this quicky blog.