---
id: 353
title: Server Script to Insert Table Items in Windows Azure Mobile Services
date: 2013-03-20T06:57:00-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/
permalink: /2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
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
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
orig_parent_id:
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
  - "10403874"
orig_thread_id:
  - "838386"
  - "838386"
  - "838386"
  - "838386"
  - "838386"
  - "838386"
  - "838386"
  - "838386"
  - "838386"
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
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Server Script to Insert Table Items in Windows Azure Mobile Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2013/03/20/server-script-to-insert-table-items-in-windows-azure-mobile-services/" />
    <meta name="twitter:description" content="I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" />
    
categories:
  - Uncategorized
tags:
  - Windows Azure Mobile Services
---
I needed a script to load a database with dummy items.&#160; I created a Scheduler script with a simple loop to insert 1000 items into my table.&#160; I found that when I ran this script it would kick off and seemingly never complete.&#160; What was worse, my service was returning a 500 internal server error when I tried to hit it!

The underlying problem is that a Mobile Service running in free mode (the default configuration) throttles the number of connections that can be made and in a tight loop, you can quickly exceed that and put the service in a bad state.&#160; The solution is to wait for previous inserts to complete before inserting new items.&#160; You can safely insert a batch of items (say 10) and once that is complete submit another batch of insert operations to avoid this connection limit.

Let’s create a script, step by step and discuss it so you can apply the same logic to your situation.

In my example I am using Scheduler but you may have similar logic in an Insert or Update script.

# The problem script

First the **problem script** (THIS WILL NOT WORK – DO NOT RUN THIS SCRIPT):

&#160;

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2867.image_4CDE98BA.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2867.image_5F00_4CDE98BA.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3343.image_thumb_20C19BC9.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3343.image_5F00_thumb_5F00_20C19BC9.png" width="450" height="286" /></a>

The issue is that line 11 executes asynchronously and we quickly run out of connections!

Let’s discuss a scheme to work around this async behavior and connection limit.

# Building a script to solve the issue

In this script we will insert the same 1000 records but do this in batches of 10.&#160; When we are done inserting the batch of 10, we will kick off another batch of 10 until we have completed the task.

I changed the script and started out by defining some variables and calling a yet to be defined function ‘insertItems’

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2867.image_4004429C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2867.image_5F00_4004429C.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3857.image_thumb_666625E7.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3857.image_5F00_thumb_5F00_666625E7.png" width="688" height="349" /></a>

&#160;

Note the comments and what we are using them for!

Next we will define the ‘insertItems’ function.&#160; Note that this function only inserts 10 records (the value I chose for batchSize)!&#160; We will need to do some more work to kick off the next batch of inserts!&#160; The insert method call on the table takes an Object as the second parameter.&#160; This object defines two members:&#160; success: and error:.&#160; I set each of these members to point to functions that will be called on success or error from the insert operation on the table.

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7658.image_658DBFFD.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7658.image_5F00_658DBFFD.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8637.image_thumb_5E025090.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8637.image_5F00_thumb_5F00_5E025090.png" width="785" height="307" /></a>

&#160;

Now we need to actually add the success and error callback functions.&#160; The first (insertComplete) is called if there were no errors during the insert.&#160; It will have the logic to see if we have completed the current batch.&#160; If we have completed inserting the records in the batch and have more records to process, we will call insertItems again to process the next batch.&#160; To track the number of items we have completed in the batch we also define a variable to track that!&#160; The second (errorHandler) will keep track of the error count then call insertComplete to use it’s logic for determining if we need to kick off a new batch or not.

&#160;

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8306.image_4E2B3B94.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8306.image_5F00_4E2B3B94.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2110.image_thumb_38615337.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2110.image_5F00_thumb_5F00_38615337.png" width="769" height="600" /></a>

&#160;

Note:&#160; You have to define the success and error functions before you use them in the insert function.&#160; If you do not you will get an error similar to this:

Error in script &#8216;/scheduler/testLoad.js&#8217;. Error: Invalid callback options passed to &#8216;insert&#8217;. Callback options must be an object with at least one &#8216;success&#8217; or &#8216;error&#8217; property of type &#8216;function&#8217;.

# Putting it all together

Assembling all of these pieces you can now test the script.&#160; If it is a Scheduler script you can configure it as an ‘On demand’ script and run once.&#160; Then check the log to ensure your records were processed.&#160; Any script errors will show up in the Mobile Services log as well.

Once you develop your script, you need to TEST, TEST and then of course TEST AGAIN.&#160; Check the boundary conditions (0 records, 1 record, 999 records) for whatever is inside and outside your expected conditions.&#160; Along with what I have discussed, you need to adapt this logic to your situation.&#160; For example, if you are not generating dummy data this won’t work for you!&#160; You will be able to study the logic however and apply it to your situation.&#160; The key parts are the success and error functions that allow you to detect when you have processed the current batch and how to kick off the next batch.&#160; You will also need to determine when you have reached the end of your processing to stop batching and log the results!

# Complete Code Listing

You should type all of this in yourself so you don’t become a cut and paste programmer.&#160; However… I do it too<img class="wlEmoticon wlEmoticon-winkingsmile" alt="Winking smile" src="https://msdnshared.blob.core.
windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6765.wlEmoticon-winkingsmile_0BED4373.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6765.wlEmoticon_2D00_winkingsmile_5F00_0BED4373.png" /> 

Special thanks to _Paul Batum_ who helped me with this problem!

**Code listing for sample ([Copy Code](javascript:CopyCode('WebLogID10403874');)):**

<div id="WebLogID10403874">
  &#160; </p> 
  
  <pre class="csharpcode"><span class="kwrd">function</span> testLoad(){
    <span class="rem">//Write to my service log </span>
    console.info(<span class="str">"Running 'PrePopulateTable' job."</span>);
    <span class="rem">// The table we will be inserting into </span>
    <span class="kwrd">var</span> todoTable = tables.getTable(<span class="str">'TodoItem'</span>);
    <span class="rem">// The number of records to insert at a time (to avoid blowing our connection limit) </span>
    <span class="kwrd">var</span> batchSize = 10;
    <span class="rem">// The number of records I want to generate dummy data for </span>
    <span class="kwrd">var</span> recordsToInsert = 1000;
    <span class="rem">// The number of records processed </span>
    <span class="kwrd">var</span> totalCount = 0;
    <span class="rem">// The number of insert failure </span>
    <span class="kwrd">var</span> errorCount = 0;
  </pre>
  
  <pre class="csharpcode">
    <span class="rem">// Start inserting items! </span>
    insertItems();
  </pre>
  
  <pre class="csharpcode">
    <span class="rem">// define the insertItems function </span>
    <span class="kwrd">function</span> insertItems() {
        <span class="rem">// local var shared with the insertComplete callback function. </span>
        <span class="rem">// This is scoped to this function so if the function is called again </span>
        <span class="rem">// it will be reset to 0 </span>
        <span class="kwrd">var</span> batchCompletedCount = 0;
  </pre>
  
  <pre class="csharpcode">&#160;</pre>
  
  <pre class="csharpcode">
<span class="rem">        // insertComplete is called for each record inserted into the table </span>
        <span class="rem">// called when the insert completes async. Also called by the errorHandler callback </span>
        <span class="kwrd">var</span> insertComplete = <span class="kwrd">function</span>() {
            <span class="rem">// increment the number of records we have completed the insert call for </span>
            batchCompletedCount++;
            <span class="rem">// increment the total number of records processed </span>
            totalCount++;
            <span class="rem">// if we have completed all of the records in this current batch </span>
            <span class="rem">// or don't have any more records to process we either... </span>
            <span class="kwrd">if</span>(batchCompletedCount === batchSize || totalCount === recordsToInsert) {
                <span class="kwrd">if</span>(totalCount &lt; recordsToInsert) {
                    insertItems(); <span class="rem">// kick off the next batch </span>
                } <span class="kwrd">else</span> {
                    <span class="rem">// or we are done </span>
                    <span class="rem">// report the status of the job to the log and don't do any more processing </span>
                    console.log(<span class="str">"Job 'PrePopulateTable' complete. %d Records processed. There were %d errors."</span>, totalCount, errorCount);
                }
            }
        };
        <span class="rem">// called if there was an error doing the insert </span>
        <span class="kwrd">var</span> errorHandler = <span class="kwrd">function</span>(err) {
            <span class="rem">// I want to track the number of errors for reporting, </span>
            <span class="rem">// you may want to do something different here </span>
            errorCount++;
            console.warn(<span class="str">"Ignoring insert failure as part of batch."</span>, err);
            <span class="rem">// call insertComplete simply to use the logic to track the batch count, </span>
            <span class="rem">// total count and kick off the next batch if necessary. </span>
            <span class="rem">// you may want to do something different! </span>
            insertComplete();
        };
             <span class="rem">// insert some items! </span>
        <span class="kwrd">for</span>(<span class="kwrd">var</span> i = 0; i &lt; batchSize; i++) {
            <span class="rem">// num is used to generate some unique dummy data </span>
            <span class="kwrd">var</span> num = totalCount + i;
            <span class="rem">// dummy data item to insert </span>
            <span class="kwrd">var</span> item = { text: <span class="str">"This is Item number: "</span> + num };
            <span class="rem">//This table insert completes async so we have a success and error callback set of functions </span>
            <span class="rem">// defined that will be called when the insert completes </span>
            todoTable.insert(item, {
                success: insertComplete,
                error: errorHandler
            });
        }
    }
}
  </pre>
  
  <p>
    &#160;
  </p>
</div>

End code listing

&#160;

# Helpful Links

<a href="http://www.windowsazure.com/en-us/develop/mobile/tutorials/schedule-backend-tasks/" target="_blank">Schedule recurring jobs in Mobile Services</a>

<a href="http://www.windowsazure.com/en-us/develop/mobile/tutorials/validate-modify-and-augment-data-dotnet/" target="_blank">Validate and modify data in Mobile Services by using server scripts</a>

<a href="http://thejoyofcode.com/Debugging_your_Mobile_Service_scripts.aspx" target="_blank">Debugging your Mobile Service scripts</a>

<a href="http://social.msdn.microsoft.com/Forums/en-US/azuremobile/threads" target="_blank">Forum for Windows Azure Mobile Services&#8217; projects, problems, and questions</a>

Be sure to follow me on Twitter @jsandersrocks and my team @WSDevSol

Let me know if this was useful to you!