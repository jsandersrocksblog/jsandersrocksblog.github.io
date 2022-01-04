---
id: 283
title: Using an existing Azure SQL table with Windows Azure Mobile Services
date: 2013-05-24T09:06:22-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/
permalink: /2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
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
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
orig_parent_id:
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
  - "10421205"
orig_thread_id:
  - "844543"
  - "844543"
  - "844543"
  - "844543"
  - "844543"
  - "844543"
  - "844543"
  - "844543"
  - "844543"
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
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using an existing Azure SQL table with Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/24/using-an-existing-azure-sql-table-with-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this. In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" />
    
categories:
  - Uncategorized
tags:
  - SQL
  - Windows Azure Mobile Services
---
You can use an existing Azure SQL table with your Mobile Services by moving the table to the schema used by your Mobile Service.&#160; This blog post will show you one technique to accomplish this.

In this sample the table we want to use with the Mobile Service is in the dbo schema.&#160; The table is aptly named ‘TableToImport’!&#160; I want to move this to the schema for my Mobile Service and use it seamlessly from Mobile Services.

There are a couple of requirements for using an Azure SQL table seamlessly with Mobile Services (at the time of this writing):

  * The table must be in the schema of your Mobile Service (the schema is the name of your Mobile Service)
  * The table must have an identity column called ‘id’ and it must be all lower case letters
  * The column types must be correct (for example not nvarchar(50) but nvarchar(max) )

You can access your Azure SQL table in different ways.&#160; I will use the designer from the portal here:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8255.image_046AF80A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8255.image_5F00_046AF80A.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_3C3D3C2D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2311.image_5F00_thumb_5F00_3C3D3C2D.png" width="519" height="345" /></a>

This is the Table that I want to move over to my Mobile Service schema (note the schema is ‘dbo’ as seen in [dbo].[TableToImport]:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0272.image_5460A688.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0272.image_5F00_5460A688.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2744.image_thumb_7AC289D3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2744.image_5F00_thumb_5F00_7AC289D3.png" width="527" height="200" /></a>

Note that the first column ‘ID’ is the wrong case, I can change it easily here:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1602.image_0C32EAAC.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1602.image_5F00_0C32EAAC.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3264.image_thumb_39B40A6F.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3264.image_5F00_thumb_5F00_39B40A6F.png" width="525" height="173" /></a>

The next task is to find out what schema I wish to move this to.&#160; The schema for your Mobile Service is the _name_ of your mobile service.&#160; In my case it is ‘jsandersattachtodb’ as shown below:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1122.image_4B246B47.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1122.image_5F00_4B246B47.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4375.image_thumb_78A58B0A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4375.image_5F00_thumb_5F00_78A58B0A.png" width="369" height="136" /></a>

&#160;

To move the table from the ‘dbo’ schema to the ‘jsandersattachtodb’ schema you can click the ‘New Query’ icon and execute an SQL statement similar to this:

<font face="Courier New">ALTER SCHEMA JsandersAttachToDb TRANSFER dbo.TableToImport</font>

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3201.image_1F076E56.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3201.image_5F00_1F076E56.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4705.image_thumb_09A9B8EE.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4705.image_5F00_thumb_5F00_09A9B8EE.png" width="367" height="217" /></a>

Then I can simply type the name of the table that I want to add and it will pick up the definition of the table from the existing table!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0820.image_5DF8EEF1.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0820.image_5F00_5DF8EEF1.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3162.image_thumb_566D7F84.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3162.image_5F00_thumb_5F00_566D7F84.png" width="376" height="184" /></a>

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4744.image_7CCF62CF.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4744.image_5F00_7CCF62CF.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3583.image_thumb_6771AD67.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3583.image_5F00_thumb_5F00_6771AD67.png" width="380" height="236" /></a>

But something is wrong… I see that I have two records but if I click on the table to browse the data in the Mobile Service portal it in it does not display in the Portal UI!

The issue is that when I created the table, I did not set the ‘id’ column to be an _identity_ column.&#160; There is no easy way to do this (that I could find  
) so the solution is to create a table with an identical structure and ensure the ‘id’ column is set to identity.&#160; Then copy the data over!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6735.image_3BC0E36B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6735.image_5F00_3BC0E36B.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7750.image_thumb_6222C6B6.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7750.image_5F00_thumb_5F00_6222C6B6.png" width="569" height="181" /></a>

Using the Query Window in the SQL management portal I can execute a statement to copy over the data into my new table:

&#160;

<font face="Courier New">SET IDENTITY_INSERT JsandersAttachToDb.NextTableToImport ON <br /> GO <br /> INSERT INTO JsandersAttachToDb.NextTableToImport (id, Column1, Column2) SELECT id, Column1, Column2 FROM JsandersAttachToDb.TableToImport <br /></font>

Now my table is integrated into my Mobile Service and works properly!

&#160;

This is just one technique to using existing Azure SQL tables in your Mobile Service.&#160; As I come across different requirements from customers I will be sure to add new blogs to show how to accomplish these (or point you to existing walkthroughs).&#160; You can get more SQL Azure help for copying etc… from the <a href="http://social.msdn.microsoft.com/Forums/en-US/ssdsgetstarted/threads" target="_blank">Windows Azure SQL Database</a> forum as well.

Drop me a note and let me know if you liked this or it saved you some time!

**Additional Information:**

<a href="http://dineshthoughtstream.blogspot.com/2012/10/using-mobile-services-in-windows-8.html" target="_blank">Dinesh’s blog</a> describes common datatypes in Mobile Services