---
id: 53
title: 'Walkthrough: Attaching an Azure SQL database to your .NET Backend'
date: 2014-07-09T13:54:47-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/
permalink: /2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2014/07/17/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
orig_site_id:
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
orig_post_id:
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
orig_parent_id:
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
  - "10541061"
orig_thread_id:
  - "875233"
  - "875233"
  - "875233"
  - "875233"
  - "875233"
  - "875233"
  - "875233"
  - "875233"
orig_application_key:
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
orig_post_author_username:
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
orig_is_approved:
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
orig_url_title:
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough: Attaching an Azure SQL database to your .NET Backend" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2014/07/09/walkthrough-attaching-an-azure-sql-database-to-your-net-backend/" />
    <meta name="twitter:description" content="Overview I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way! Setup Create a new Mobile Service or download the starter..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" />
    
categories:
  - Uncategorized
---
# 

I needed to attach an existing Azure SQL database to my .NET Backend.&#160; This will allow me to expose existing data using the Azure Mobile Service I have defined.&#160; This will walk you through the steps I took and get you on your way!

## Setup

Create a new Mobile Service or download the starter project from your existing Mobile Service based on the .NET Backend.

My existing Azure SQL database has the following structure the schema is in the dbo schema (you can see this through the Management portal of your Azure SQL Databases and will be used for this example:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1050.image_133A3F1A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1050.image_5F00_133A3F1A.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_5BF3B7DE.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7457.image_5F00_thumb_5F00_5BF3B7DE.png" width="500" height="256" /></a> 

## Details

#### Get and Build base project

My existing Mobile Service only has the TodoItem table associated with it.

Download the starter project form the Mobile Services Dashboard if you don’t already have a local copy to work with or if this is a brand new project you can create your Mobile Service inside of Visual Studio.

Or you can create an new Mobile Service project and publish it later:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3678.image_700CD467.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3678.image_5F00_700CD467.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7652.image_thumb_5B1DE2A5.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7652.image_5F00_thumb_5F00_5B1DE2A5.png" width="562" height="330" /></a> 

Ensure you build your solution at least once to get the appropriate packages

#### Add Tables from Existing Database

Now we will add the existing database to the Mobile Services project.

Right click on the Models folder in your project and choose ‘Add’, ‘ADO.NET Entity Data Model’

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5141.image_1F60DAA3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5141.image_5F00_1F60DAA3.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7635.image_thumb_580E1561.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7635.image_5F00_thumb_5F00_580E1561.png" width="450" height="366" /></a> 

You can name it whatever you want but to stay organized, name it the same as your table.

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1385.image_59723833.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1385.image_5F00_59723833.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1222.image_thumb_3BFFE727.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1222.image_5F00_thumb_5F00_3BFFE727.png" width="553" height="164" /></a> 

Hit ‘OK’ then choose ‘Code First from database’:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3731.image_371D336B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3731.image_5F00_371D336B.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3264.image_thumb_5FBB9F72.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3264.image_5F00_thumb_5F00_5FBB9F72.png" width="544" height="487" /></a> 

Hit next and then choose ‘New Connection’

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6837.image_085A0B7A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6837.image_5F00_085A0B7A.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7457.image_thumb_457DC6FF.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7457.image_5F00_thumb_5F00_457DC6FF.png" width="549" height="492" /></a> 

Here you need some information from your azure management portal for your database:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6305.image_1073C880.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6305.image_5F00_1073C880.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3124.image_thumb_7FFB5784.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3124.image_5F00_thumb_5F00_7FFB5784.png" width="296" height="431" /></a> </p> 

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.m
sdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6138.image_0F9DF347.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6138.image_5F00_0F9DF347.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2352.image_thumb_55B1410B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2352.image_5F00_thumb_5F00_55B1410B.png" width="564" height="361" /></a> 

Copy the server information (in my case you can see what I entered).&#160; Ensure you are using SQL authentication and them find your database in the combo box and select it:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7585.image_412E823E.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7585.image_5F00_412E823E.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2251.image_thumb_1BC48ED0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2251.image_5F00_thumb_5F00_1BC48ED0.png" width="327" height="477" /></a> 

Hit ‘OK’

This will populate your information.&#160; Select ‘No’ on the radio button about sensitive data and hit ‘Next’:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5430.image_4E2AF300.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5430.image_5F00_4E2AF300.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1581.image_thumb_0AE27B91.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1581.image_5F00_thumb_5F00_0AE27B91.png" width="497" height="446" /></a> 

I selected 2 tables under the dbo schema and hit ‘Finish’:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8880.image_0A78D94D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8880.image_5F00_0A78D94D.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0804.image_thumb_7A006851.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0804.image_5F00_thumb_5F00_7A006851.png" width="555" height="498" /></a> 

This generates Model Files for each of the Tables I have chosen (and that is it).

Next we need to hook these models up to the Database and expose them through a Table Controller.

#### Create EntityData models

To expose these new Models to the Table Controller, we need to get these into the format the Entity Framework understands.&#160; We will call these ‘Dto’ or ‘DataTableObject’ classes.

Concentrating on one table (StuffToGet) here is the code generated by my previous steps:

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql1');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql1" class="code"><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceTest.Models
{
    </span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System;
    </span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Collections.Generic;
    </span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.ComponentModel.DataAnnotations;
    </span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.ComponentModel.DataAnnotations.Schema;
    </span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Data.Entity.Spatial;
    [</span><span style="background: white; color: #2b91af">Table</span><span style="background: white; color: black">(</span><span style="background: white; color: #a31515">"StuffToGet"</span><span style="background: white; color: black">)]
    </span><span style="background: white; color: blue">public partial class </span><span style="background: white; color: #2b91af">StuffToGet
    </span><span style="background: white; color: black">{
        [</span><span style="background: white; color: #2b91af">DatabaseGenerated</span><span style="background: white; color: black">(</span><span style="background: white; color: #2b91af">DatabaseGeneratedOption</span><span style="background: white; color: black">.None)]
        </span><span style="background: white; color: blue">public int </span><span style="background: white; color: black">ID { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        [</span><span style="background: white; color: #2b91af">Required</span><span style="background: white; color: black">]
        [</span><span style="background: white; color: #2b91af">StringLength</span><span style="background: white; color: black">(50)]
        </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Name { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        [</span><span style="background: white; color: #2b91af">StringLength</span><span style="background: white; color: black">(15)]
        </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Description { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        </span><span style="background: white; color: blue">public int</span><span style="background: white; color: black">? Purchased { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
    }
}
</span></pre>

[](http://11011.net/software/vspaste)

Right click on the ‘DataObjects’ folder and create a new class with the same name as your Model but append ‘Dto’:

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql2');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql2" class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">System;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Collections.Generic;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web;
</span><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceTest.DataObjects
{
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">StuffToGetDto
    </span><span style="background: white; color: black">{
    }
}</span></pre>

[](http://11011.net/software/vspaste)Then make the following similar modifications to your class to make it an EntiyData derived class (removing the primary ID field and normalizing the types to Mobile Service Friendly types:

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql3');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql3" class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Collections.Generic;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web;
</span><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceTest.DataObjects
{
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">:</span><span style="background: white; color: #2b91af">EntityData
    </span><span style="background: white; color: black">{
        </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Name { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Description { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        </span><span style="background: white; color: blue">public int</span><span style="background: white; color: black">? Purchased { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
    }
}</span></pre>

Now we need a controller for that Dto (DataTableObject)

#### Create Table controller

Right click on the ‘Controllers’ folder of your solution explorer and choose: ‘Add’, ‘Controller’

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7271.image_0283C79C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7271.image_5F00_0283C79C.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5148.image_thumb_2717E5D1.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5148.image_5F00_thumb_5F00_2717E5D1.png" width="486" height="129" /></a> 

Select the Mobile Services table controller as pictured:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7723.image_1B15F59D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7723.image_5F00_1B15F59D.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1715.image_thumb_5F58ED9A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1715.image_5F00_thumb_5F00_5F58ED9A.png" width="514" height="357" /></a> </p> 

Add the new DataModel you just created and hit the + button to create a new DbContext for the existing AzureSQL db:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6102.image_482D731C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6102.image_5F00_482D731C.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1323.image_thumb_239BE598.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1323.image_5F00_thumb_5F00_239BE598.png" width="461" height="267" /></a> 

Hit ‘Add’ and this will create the DbContext and Table Controller for this connection and table.&#160; And hit ‘OK’

#### Modify the created DbContext

Now remove the DbContext code and make these similar changes (see comments).&#160; In our case the generated file is ExistingAzureSqlContext.cs:

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql4');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql4" class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Data.Entity;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Data.Entity.ModelConfiguration.Conventions;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service.Tables;
</span><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceTest.Models
{
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">ExistingAzureSqlContext </span><span style="background: white; color: black">: </span><span style="background: white; color: #2b91af">DbContext
    </span><span style="background: white; color: black">{
        </span><span style="background: white; color: green">// change contructor to take the dbConnection string
        </span><span style="background: white; color: blue">public </span><span style="background: white; color: black">ExistingAzureSqlContext(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">dbConnectionString) :
            </span><span style="background: white; color: blue">base</span><span style="background: white; color: black">(dbConnectionString)
        {
        }
</span><span style="background: white; color: black">        </span><span style="background: white; color: green">//change model to the Model and not the Dto
        </span><span style="background: white; color: blue">public </span><span style="background: white; color: black">System.Data.Entity.</span><span style="background: white; color: #2b91af">DbSet</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">&gt; StuffToGet { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
    }
}
</span></pre>

[](http://11011.net/software/vspaste)

<span style="background: white; color: black">This database context will be used in the controller code to attach to the Azure SQL table.</span>

#### <span style="background: white; color: black">Create Utility Code</span>

<span style="background: white; color: black">Now we need some utility code to map between the Model and the Dto.</span>

<span style="background: white; color: black">Right click on the Models folder and create a new class called ‘SimpleMappedEntityDomainManager’ and put this in the file:</span>

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql5');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql5" class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">AutoMapper;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">AutoMapper.Impl;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service.Tables;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Collections.Generic;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Data.Entity;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq.Expressions;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Net.Http;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Reflection;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Threading.Tasks;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web.Http;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web.Http.OData;
</span><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceUtilities.Models
{
    </span><span style="background: white; color: green">//Utilities for Hooking up models
    </span><span style="background: white; color: blue">public static class </span><span style="background: white; color: #2b91af">MySqlFuncs
    </span><span style="background: white; color: black">{
        [</span><span style="background: white; color: #2b91af">DbFunction</span><span style="background: white; color: black">(</span><span style="background: white; color: #a31515">"SqlServer"</span><span style="background: white; color: black">, </span><span style="background: white; color: #a31515">"STR"</span><span style="background: white; color: black">)]
        </span><span style="background: white; color: blue">public static string </span><span style="background: white; color: black">StringConvert(</span><span style="background: white; color: blue">long </span><span style="background: white; color: black">number)
        {
            </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">number.ToString();
        }
        [</span><span style="background: white; color: #2b91af">DbFunction</span><span style="background: white; color: black">(</span><span style="background: white; color: #a31515">"SqlServer"</span><span style="background: white; color: black">, </span><span style="background: white; color: #a31515">"LTRIM"</span><span style="background: white; color: black">)]
        </span><span style="background: white; color: blue">public static string </span><span style="background: white; color: black">LTRIM(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">s)
        {
            </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">s == </span><span style="background: white; color: blue">null </span><span style="background: white; color: black">? </span><span style="background: white; color: blue">null </span><span style="background: white; color: black">: s.TrimStart();
        }
        </span><span style="background: white; color: green">// Can only be used locally.
        </span><span style="background: white; color: blue">public static long </span><span style="background: white; color: black">LongParse(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">s)
        {
            </span><span style="background: white; color: blue">long </span><span style="background: white; color: black">ret;
            </span><span style="background: white; color: blue">long</span><span style="background: white; color: black">.TryParse(s, </span><span style="background: white; color: blue">out </span><span style="background: white; color: black">ret);
            </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">ret;
        }
    }
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">SimpleMappedEntityDomainManager</span><span style="background: white; color: black">&lt;TData, TModel&gt;
        : </span><span style="background: white; color: #2b91af">MappedEntityDomainManager</span><span style="background: white; color: black">&lt;TData, TModel&gt;
        </span><span style="background: white; color: blue">where </span><span style="background: white; color: black">TData : </span><span style="background: white; color: blue">class</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">ITableData</span><span style="background: white; color: black">, </span><span style="background: white; color: blue">new</span><span style="background: white; color: black">()
        </span><span style="background: white; color: blue">where </span><span style="background: white; color: black">TModel : </span><span style="background: white; color: blue">class
    </span><span style="background: white; color: black">{
        </span><span style="background: white; color: blue">private </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">Func</span><span style="background: white; color: black">&lt;TModel, </span><span style="background: white; color: blue">object</span><span style="background: white; color: black">&gt;&gt; dbKeyProperty;
        </span><span style="background: white; color: blue">public </span><span style="background: white; color: black">SimpleMappedEntityDomainManager(</span><span style="background: white; color: #2b91af">DbContext </span><span style="background: white; color: black">context,
            </span><span style="background: white; color: #2b91af">HttpRequestMessage </span><span style="background: white; color: black">request, </span><span style="background: white; color: #2b91af">ApiServices </span><span style="background: white; color: black">services,
            </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">Func</span><span style="background: white; color: black">&lt;TModel, </span><span style="background: white; color: blue">object</span><span style="background: white; color: black">&gt;&gt; dbKeyProperty)
            : </span><span style="background: white; color: blue">base</span><span style="background: white; color: black">(context, request, services)
        {
            </span><span style="background: white; color: blue">this</span><span style="background: white; color: black">.dbKeyProperty = dbKeyProperty;
        }
        </span><span style="background: white; color: blue">public override </span><span style="background: white; color: #2b91af">SingleResult</span><span style="background: white; color: black">&lt;TData&gt; Lookup(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">id)
        {
            </span><span style="background: white; color: blue">return this</span><span style="background: white; color: black">.LookupEntity(GeneratePredicate(id));
        }
        </span><span style="background: white; color: blue">public override async </span><span style="background: white; color: #2b91af">Task</span><span style="background: white; color: black">&lt;TData&gt; UpdateAsync(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">id, </span><span style="background: white; color: #2b91af">Delta</span><span style="background: white; color: black">&lt;TData&gt; patch)
        {
            </span><span style="background: white; color: blue">return await this</span><span style="background: white; color: black">.UpdateEntityAsync(patch, ConvertId(id));
        }
        </span><span style="background: white; color: blue">public override </span><span style="background: white; color: #2b91af">Task</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: blue">bool</span><span style="background: white; color: black">&gt; DeleteAsync(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">id)
        {
            </span><span style="background: white; color: blue">return this</span><span style="background: white; color: black">.DeleteItemAsync(ConvertId(id));
        }
        </span><span style="background: white; color: blue">private static </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">Func</span><span style="background: white; color: black">&lt;TModel, </span><span style="background: white; color: blue">bool</span><span style="background: white; color: black">&gt;&gt; GeneratePredicate(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">id)
        {
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">m = </span><span style="background: white; color: #2b91af">Mapper</span><span style="background: white; color: black">.FindTypeMapFor&lt;TModel, TData&gt;();
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">pmForId = m.GetExistingPropertyMapFor(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">PropertyAccessor</span><span style="background: white; color: black">(</span><span style="background: white; color: blue">typeof</span><span style="background: white; color: black">(TData).GetProperty(</span><span style="background: white; color: #a31515">"Id"</span><span style="background: white; color: black">)));
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">keyString = pmForId.CustomExpression;
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">predicate = </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">.Lambda&lt;</span><span style="background: white; color: #2b91af">Func</span><span style="background: white; color: black">&lt;TModel, </span><span style="background: white; color: blue">bool</span><span style="background: white; color: black">&gt;&gt;(
                </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">.Equal(keyString.Body, </span><span style="background: white; color: #2b91af">Expression</span><span style="background: white; color: black">.Constant(id)),
                keyString.Parameters[0]);
            </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">predicate;
        }
        </span><span style="background: white; color: blue">private object </span><span style="background: white; color: black">ConvertId(</span><span style="background: white; color: blue">string </span><span style="background: white; color: black">id)
        {
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">m = </span><span style="background: white; color: #2b91af">Mapper</span><span style="background: white; color: black">.FindTypeMapFor&lt;TData, TModel&gt;();
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">keyPropertyAccessor = GetPropertyAccessor(</span><span style="background: white; color: blue">this</span><span style="background: white; color: black">.dbKeyProperty);
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">pmForId = m.GetExistingPropertyMapFor(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">PropertyAccessor</span><span style="background: white; color: black">(keyPropertyAccessor));
            TData tmp = </span><span style="background: white; color: blue">new </span><span style="background: white; color: black">TData() { Id = id };
            </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">convertedId = pmForId.CustomExpression.Compile().DynamicInvoke(tmp);
            </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">convertedId;
        }
        </span><span style="background: white; color: blue">private </span><span style="background: white; color: #2b91af">PropertyInfo </span><span style="background: white; color: black">GetPropertyAccessor(</span><span style="background: white; color: #2b91af">Expression </span><span style="background: white; color: black">exp)
        {
            </span><span style="background: white; color: blue">if </span><span style="background: white; color: black">(exp.NodeType == </span><span style="background: white; color: #2b91af">ExpressionType</span><span style="background: white; color: black">.Lambda)
            {
                </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">lambda = exp </span><span style="background: white; color: blue">as </span><span style="background: white; color: #2b91af">LambdaExpression</span><span style="background: white; color: black">;
                </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">GetPropertyAccessor(lambda.Body);
            }
            </span><span style="background: white; color: blue">else if </span><span style="background: white; color: black">(exp.NodeType == </span><span style="background: white; color: #2b91af">ExpressionType</span><span style="background: white; color: black">.Convert)
            {
                </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">convert = exp </span><span style="background: white; color: blue">as </span><span style="background: white; color: #2b91af">UnaryExpression</span><span style="background: white; color: black">;
                </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">GetPropertyAccessor(convert.Operand);
            }
            </span><span style="background: white; color: blue">else if </span><span style="background: white; color: black">(exp.NodeType == </span><span style="background: white; color: #2b91af">ExpressionType</span><span style="background: white; color: black">.MemberAccess)
            {
                </span><span style="background: white; color: blue">var </span><span style="background: white; color: black">propExp = exp </span><span style="background: white; color: blue">as </span><span style="background: white; color: black">System.Linq.Expressions.</span><span style="background: white; color: #2b91af">MemberExpression</span><span style="background: white; color: black">;
                </span><span style="background: white; color: blue">return </span><span style="background: white; color: black">propExp.Member </span><span style="background: white; color: blue">as </span><span style="background: white; color: #2b91af">PropertyInfo</span><span style="background: white; color: black">;
            }
            </span><span style="background: white; color: blue">else
            </span><span style="background: white; color: black">{
                </span><span style="background: white; color: blue">throw new </span><span style="background: white; color: #2b91af">InvalidOperationException</span><span style="background: white; color: black">(</span><span style="background: white; color: #a31515">"Unexpected expression node type: " </span><span style="background: white; color: black">+ exp.NodeType);
            }
        }
    }
}
</span></pre>

[](http://11011.net/software/vspaste)[](http://11011.net/software/vspaste)

#### <span style="background: white; color: black"><font color="#333333" face="Segoe UI">Modify Controller code to use new mapper</font></span>

<pre class="code"><span style="background: white; color: black"><font color="#333333" face="Segoe UI">Modify the Controller code you just generated as follows and ensure you add this reference to the top (see comments):</font></span></pre>

<pre class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">MobileServiceUtilities.Models;</span></pre>

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql6');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql6" class="code"><span style="background: white; color: black"> </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">StuffToGetDtoController </span><span style="background: white; color: black">: </span><span style="background: white; color: #2b91af">TableController</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">&gt;
    {
        </span><span style="background: white; color: blue">protected override void </span><span style="background: white; color: black">Initialize(</span><span style="background: white; color: #2b91af">HttpControllerContext </span><span style="background: white; color: black">controllerContext)
        {
            </span><span style="background: white; color: blue">base</span><span style="background: white; color: black">.Initialize(controllerContext);
            </span><span style="background: white; color: green">//modify the context to use the constructor that will take a connection string - stored in web.config
            </span><span style="background: white; color: #2b91af">ExistingAzureSqlContext </span><span style="background: white; color: black">context = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ExistingAzureSqlContext</span><span style="background: white; color: black">(Services.Settings[</span><span style="background: white; color: #a31515">"ExistingDbConnectionString"</span><span style="background: white; color: black">]);
            </span><span style="background: white; color: green">// DomainManager = new EntityDomainManager&lt;StuffToGetDto&gt;(context, Request, Services);
            // set DomainManger to a new one that we created
            </span><span style="background: white; color: black">DomainManager = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">SimpleMappedEntityDomainManager</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">&gt;(
              context,
              Request,
              Services,
              stuffToGet =&gt; stuffToGet.ID );
        }</span></pre>

#### Map the Id field in the Dto to the ID field in the Model

Finally we need to map between the Dto and Model objects.&#160; In this case the integer ‘ID’ field in the model has to map to the Mobile Service friendly ‘Id’ field which is a string.&#160; 

Open WebApiConfig.cs in the App_Start folder and add this code to the end of the Register function:

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql7');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql7" class="code"><span style="background: white; color: black">    AutoMapper.</span><span style="background: white; color: #2b91af">Mapper</span><span style="background: white; color: black">.Initialize(cfg =&gt;
            {
                </span><span style="background: white; color: green">// Mapping from database type to client type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.Id, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LTRIM(</span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.StringConvert(src.ID))));
                </span><span style="background: white; color: green">// Mapping from client type to database type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.ID, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LongParse(src.Id)));
            });
</span></pre>

[](http://11011.net/software/vspaste)

#### Add Connection String to Web.Config

The connection string specified in the DbContext needs to be added to your WebConfig.

You can get this string from your Azure SQL Management dashboard:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8712.image_484C5895.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8712.image_5F00_484C5895.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3056.image_thumb_5EA1FDDA.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3056.image_5F00_thumb_5F00_5EA1FDDA.png" width="490" height="288" /></a> 

Copy the ADO.NET one:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0247.image_0E5FA65A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0247.image_5F00_0E5FA65A.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8688.image_thumb_62AEDC5D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8688.image_5F00_thumb_5F00_62AEDC5D.png" width="451" height="270" /></a> 

Open your Web.Config and add the key ‘ExistingDbConnectionString’ and the value is this connection string, ensuring you put your password in the section that says {your\_password\_here}

**<a style="background: lightgray" href="javascript:CopyCode('CopyCodeCodeSectionASql9');">Copy Code:</a>** 

<pre id="CopyCodeCodeSectionASql9" class="code"><span style="background: white; color: blue"> &lt;</span><span style="background: white; color: #a31515">appSettings</span><span style="background: white; color: blue">&gt;
    &lt;!-- </span><span style="background: white; color: green">Service Bus specific app setings for messaging connections </span><span style="background: white; color: blue">--&gt;
    &lt;</span><span style="background: white; color: #a31515">add </span><span style="background: white; color: red">key</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">PreserveLoginUrl</span><span style="background: white; color: black">" </span><span style="background: white; color: red">value</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">true</span><span style="background: white; color: black">" </span><span style="background: white; color: blue">/&gt;
    &lt;!-- </span><span style="background: white; color: green">Use these settings for local development. After publishing to
    Mobile Services, these settings will be overridden by the values specified
    in the portal. </span><span style="background: white; color: blue">--&gt;
    &lt;</span><span style="background: white; color: #a31515">add </span><span style="background: white; color: red">key</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">ExistingDbConnectionString</span><span style="background: white; color: black">" </span><span style="background: white; color: red">value</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">Server=tcp:nagog6s9ep.database.windows.net,1433;Database=dbForJason;User <a href="mailto:ID=dbadmin@nagog6s9ep;Password=mypassword;Trusted_Connection=False;Encrypt=True;Connection">ID=dbadmin@nagog6s9ep;Password=mypassword;Trusted_Connection=False;Encrypt=True;Connection</a> Timeout=30;</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">/&gt;
    &lt;</span><span style="background: white; color: #a31515">add </span><span style="background: white; color: red">key</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">MS_MobileServiceName</span><span style="background: white; color: black">" </span><span style="background: white; color: red">value</span><span style="background: white; color: blue">=</span><span style="background: white; color: black">"</span><span style="background: white; color: blue">MobileServiceTest</span><span style="background: white; color: black">" </span><span style="background: white; color: blue">/&gt;
 </span></pre>

[](http://11011.net/software/vspaste)[](http://11011.net/software/vspaste)

#### Build

Finally, build the solution.&#160; Resolve and missing ‘using’ statements by right clicking on them and choosing ‘Resolve’

#### Test

Now you can run this solution local and test in IE.

Hit the ‘Try it’ button in IE and try to POST, GET and PATCH data into your Azure DB through the Mobile service!

Now, How about adding additional tables?

Easy!

#### Add Additional Tables from database

We included a 2nd table when we go the StuffToGet table.&#160; Let’s now add Table2 as well since we included the model when we got the first table.

Go through the same steps above:

Add the Dto class:

<pre class="code"><span style="background: white; color: blue">using </span><span style="background: white; color: black">Microsoft.WindowsAzure.Mobile.Service;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Collections.Generic;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Linq;
</span><span style="background: white; color: blue">using </span><span style="background: white; color: black">System.Web;
</span><span style="background: white; color: blue">namespace </span><span style="background: white; color: black">MobileServiceTest.DataObjects
{
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">Table2Dto</span><span style="background: white; color: black">:</span><span style="background: white; color: #2b91af">EntityData
    </span><span style="background: white; color: black">{
</span><span style="background: white; color: black">
            </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Column1 { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
            </span><span style="background: white; color: blue">public string </span><span style="background: white; color: black">Column2 { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
    }
}</span></pre>

#### Create Table controller

This is where it will get a little weird.&#160; In this step do **NOT create a new dbContext**.&#160; Instead select the existing one (note that the new one does not show up).

Add a table controller and use the existing dbContext :

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3005.image_1799F564.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3005.image_5F00_1799F564.png"><img loading="lazy" title="image" style="border-left-width: 0px; border-right-width: 0px; border-bottom-width: 0px; display: inline; border-top-width: 0px" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1780.image_thumb_730867DF.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1780.image_5F00_thumb_5F00_730867DF.png" width="486" height="229" /></a> 

Now open that db context (MobileServicesTestContext) and remove the table from that:

<pre class="code"><span style="background: white; color: black">   }
     </span><span style="background: white; color: green">//REMOVE this
        //public System.Data.Entity.DbSet&lt;MobileServiceTest.DataObjects.Table2Dto&gt; Table2Dto { get; set; }
    </span><span style="background: white; color: black">}</span></pre>

And add this into ExistingAzureSqlContext.cs under the other table definition:

<pre class="code"><span style="background: white; color: black">   </span><span style="background: white; color: green">//change model to the Model and not the Dto
        </span><span style="background: white; color: blue">public </span><span style="background: white; color: black">System.Data.Entity.</span><span style="background: white; color: #2b91af">DbSet</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">&gt; StuffToGet { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
        </span><span style="background: white; color: blue">public </span><span style="background: white; color: black">System.Data.Entity.</span><span style="background: white; color: #2b91af">DbSet</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">Table2</span><span style="background: white; color: black">&gt; Table2 { </span><span style="background: white; color: blue">get</span><span style="background: white; color: black">; </span><span style="background: white; color: blue">set</span><span style="background: white; color: black">; }
    }</span></pre>

Like before modify the Controller to use the ExistingAzureSqlContext:

<pre class="code"><span style="background: white; color: black"> </span><span style="background: white; color: blue">protected override void </span><span style="background: white; color: black">Initialize(</span><span style="background: white; color: #2b91af">HttpControllerContext </span><span style="background: white; color: black">controllerContext)
        {
            </span><span style="background: white; color: blue">base</span><span style="background: white; color: black">.Initialize(controllerContext);
            </span><span style="background: white; color: #2b91af">ExistingAzureSqlContext </span><span style="background: white; color: black">context = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ExistingAzureSqlContext</span><span style="background: white; color: black">(Services.Settings[</span><span style="background: white; color: #a31515">"ExistingDbConnectionString"</span><span style="background: white; color: black">]);
            </span><span style="background: white; color: green">// DomainManager = new EntityDomainManager&lt;StuffToGetDto&gt;(context, Request, Services);
            // set DomainManger to a new one that we will create
            </span><span style="background: white; color: black">DomainManager = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">SimpleMappedEntityDomainManager</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">Table2Dto</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">Table2</span><span style="background: white; color: black">&gt;(
              context,
              Request,
              Services,
              table2 =&gt; table2.ID);
        }
</span></pre>

#### Map the Id field in the Dto to the ID field in the Model

And add the automapper information:

<pre class="code"><span style="background: white; color: black">  AutoMapper.</span><span style="background: white; color: #2b91af">Mapper</span><span style="background: white; color: black">.Initialize(cfg =&gt;
            {
                </span><span style="background: white; color: green">// Mapping from database type to client type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.Id, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LTRIM(</span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.StringConvert(src.ID))));
                </span><span style="background: white; color: green">// Mapping from client type to database type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">StuffToGet</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.ID, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LongParse(src.Id)));
                </span><span style="background: white; color: green">// Mapping from database type to client type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">Table2</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">Table2Dto</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.Id, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LTRIM(</span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.StringConvert(src.ID))));
                </span><span style="background: white; color: green">// Mapping from client type to database type
                </span><span style="background: white; color: black">cfg.CreateMap&lt;</span><span style="background: white; color: #2b91af">Table2Dto</span><span style="background: white; color: black">, </span><span style="background: white; color: #2b91af">Table2</span><span style="background: white; color: black">&gt;()
                    .ForMember(dst =&gt; dst.ID, map =&gt; map.MapFrom(src =&gt; </span><span style="background: white; color: #2b91af">MySqlFuncs</span><span style="background: white; color: black">.LongParse(src.Id)));
            });
</span></pre>

[](http://11011.net/software/vspaste)

#### Build

Run and test!

#### Conclusion

Once you run through this you should be able to see how you can easily bring your own DB to you Mobile Service .NET Backend.&#160; You can do some cool stuff with the Mapper as well so check out the links below.

Let me know if this was useful to you!&#160; 

Follow me @jsandersrocks and my team at @WSDevSol on Twitter.

#### More information

##### Rename the table exposed by the controller:

&#160; You can rename the Controller to change the public facing name of the table.

So if you want StuffToGetDto to be exposed as StuffToGet, simply rename the class in the file it is defined:

<pre class="code"><span style="background: white; color: green">/ old name public class StuffToGetDtoController : TableController&lt;StuffToGetDto&gt;
        //new name of controller without Dto suffix
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">StuffToGetController </span><span style="background: white; color: black">: </span><span style="background: white; color: #2b91af">TableController</span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">StuffToGetDto</span><span style="background: white; color: black">&gt;
    {
    </span></pre>

[](http://11011.net/software/vspaste)

##### Build Mobile Services .NET Backend with no Azure Subscription:

If you don&#8217;t have an Azure account you can still play with this.&#160; From Visual Studio select the ‘Windows Azure Mobile Service’ template under the ‘Visual C#’, ‘Cloud’ templates when you create a new project

##### Other links:

[Bring Your Own Database with the .NET Backend](http://blogs.msdn.com/b/azuremobile/archive/2014/05/27/bring-your-own-database-with-the-net-backend.aspx)

[Mapping between Database Types and Client Types in the .NET Backend using AutoMapper](http://blogs.msdn.com/b/azuremobile/archive/2014/05/19/mapping-between-database-types-and-client-type-in-the-net-backend-using-automapper.aspx).

[Tables with Integer Keys and the .NET Backend](http://blogs.msdn.com/b/azuremobile/archive/2014/05/22/tables-with-integer-keys-and-the-net-backend.aspx).