---
id: 313
title: 'Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema'
date: 2013-05-02T05:55:42-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/
permalink: /2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
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
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
orig_parent_id:
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
  - "10415615"
orig_thread_id:
  - "842786"
  - "842786"
  - "842786"
  - "842786"
  - "842786"
  - "842786"
  - "842786"
  - "842786"
  - "842786"
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
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Windows Azure Mobile Services &#8211; Accessing a Stored Procedure from a different Schema" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/05/02/windows-azure-mobile-services-accessing-a-stored-procedure-from-a-different-schema/" />
    <meta name="twitter:description" content="I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: [Microsoft][SQL Server Native Client 10.0][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" />
    
categories:
  - Uncategorized
tags:
  - SQL
  - Windows Azure Mobile Services
---
I needed to access a stored procedure in the same database but for a different schema and call it from a server side script in Windows Azure Mobile Services, however I was getting this error: Error occurred executing query:&#160; “Error: \[Microsoft\]\[SQL Server Native Client 10.0\][SQL Server]The EXECUTE permission was denied on the object &#8216;Test&#8217;, database &#8216;jsanders_db&#8217;, schema &#8216;jsandersauthdemo&#8217;.”.&#160; This made sense to me because I was calling across Schemas.&#160; The script looked like this:

<pre class="code"><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">read( query, user, request )
{
    mssql.query( </span><span style="background: white; color: rgb(163, 21, 21);">"exec GetSomeStuff ?"</span><span style="background: white; color: black;">, [</span><span style="background: white; color: rgb(163, 21, 21);">"%eff%"</span><span style="background: white; color: black;">], {
        success: </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">( results )
        {
            console.log( results );
        }
    } );
    mssql.query( </span><span style="background: white; color: rgb(163, 21, 21);">"exec jsandersauthdemo.Test"</span><span style="background: white; color: black;">, </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">, {
        success: </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">( results )
        {
            console.log( results );
        }
    } );
    request.execute();
}</span></pre>

&#160;

The first stored procedure ‘GetSomeStuff’ was in my database JeffDemo and succeeded but the second was in jsandersauthdemo and failed with the above error.

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8055.image_39F72A4B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8055.image_5F00_39F72A4B.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7558.image_thumb_44484EAB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7558.image_5F00_thumb_5F00_44484EAB.png" width="239" height="115" /></a>

The solution was to grant the appropriate permissions to allow me to call ‘jsandersauthdemo.Test’.&#160; Apparently the calling user was different depending on the scripting environment in Mobile Services.

To see what users were accessing the schemas I first clicked on my database in the Azure management dashboard and installed the tools from there (steps 1-3 following that link):

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3757.image_7C86C5C3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3757.image_5F00_7C86C5C3.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1205.image_thumb_1BC96C97.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1205.image_5F00_thumb_5F00_1BC96C97.png" width="333" height="234" /></a>&#160;

Hitting the Windows Key and start typing SQL I found the SQL tools opened it up and connected to the SQL Azure db.&#160; You can find the name of your server here:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5811.image_16E6B8DB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5811.image_5F00_16E6B8DB.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6153.image_thumb_48722670.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6153.image_5F00_thumb_5F00_48722670.png" width="484" height="152" /></a>

Connect to the server and go down to the schemas folder in the SQL Server Object Explorer.&#160; The two I am concerned with are JeffDemo (where I am calling from) and jsandersauthdemo (where the failing stored procedure is).&#160; Right clicking on ‘JeffDemo’ and choosing ‘View Permissions’ I can see what user has permissions to access that schema!&#160; I will use that user information and grant permissions to the stored procedure for that user.

GRANT CONTROL  
  
&#160;&#160;&#160; ON SCHEMA::[JeffDemo] TO [iMCrzkYNNaLoginUser]  
  
&#160;&#160;&#160; AS [dbo];

Under Programmability/Stored Procedures I found and right clicked on my procedure I was failing on and chose ‘View Permissions’ and then added the grant permissions for the User from JeffDemo:

<pre class="code"><span style="background: white; color: green;">/*
No permissions were found for [jsandersauthdemo].[Test] or all existing permissions are open in other windows
*/
</span><span style="background: white; color: blue;">GRANT CONTROL
    ON </span><span style="background: white; color: black;">[jsandersauthdemo]</span><span style="background: white; color: gray;">.</span><span style="background: white; color: black;">[Test] </span><span style="background: white; color: blue;">TO </span><span style="background: white; color: black;">[iMCrzkYNNaLoginUser]
    </span><span style="background: white; color: blue;">AS </span><span style="background: white; color: black;">[dbo]</span><span style="background: white; color: gray;">;
</span></pre>

Simply hit the ‘Update’ icon at the top of this input window and permissions were granted.

A quick test on my Script and I was rockin’ and rollin’!

&#160;

I know this is just a quicky blog post but please let me know if this helps you out!