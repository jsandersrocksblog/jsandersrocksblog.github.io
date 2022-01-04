---
id: 1381
title: 'Azure Mobile Apps&#8211;How to remove the notification hub and get the wizard back'
date: 2016-02-19T11:54:48-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/
permalink: /2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2016/02/19/azure-mobile-apps-how-to-remove-the-notification-hub-and-get-the-wizard-back.aspx
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
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
orig_post_name:
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
  - azure mobile apps how to remove the notification hub and get the wizard back
orig_parent_id:
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
  - "10669754"
orig_thread_id:
  - "902813"
  - "902813"
  - "902813"
  - "902813"
  - "902813"
  - "902813"
  - "902813"
  - "902813"
  - "902813"
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
orig_post_author_email:
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
  - jsanders@microsoft.com
orig_post_author_created:
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
  - 2007-01-18 13:34:53.000
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
total_views:
  - "877"
  - "877"
  - "877"
  - "877"
  - "877"
  - "877"
  - "877"
  - "877"
  - "877"
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta property="og:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Mobile Apps&ndash;How to remove the notification hub and get the wizard back" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/02/19/azure-mobile-appshow-to-remove-the-notification-hub-and-get-the-wizard-back/" />
    <meta name="twitter:description" content="I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way). Here is a picture of what I mean: Run this powershell script from the Azure Powershell (or do similar using the Azure CLI): Remove-AzureRmResource -ResourceId /subscriptions/&lt;SUBCRIPTION_ID&gt;/resourcegroups/&lt;RESOURCE_GROUP&gt;/providers /Microsoft.Web/sites/&lt;APP_NAME&gt;/providers/Microsoft.Resources/links/mobile-notificationhub And I get my..." />
    <meta name="twitter:image" content="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" />
    
categories:
  - Uncategorized
---
I noticed that you cannot change the notification hub in the UI.&#160; There is a simple workaround (it will be fixed by the way).

Here is a picture of what I mean:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4062.capture20160219144141503_0F251C6C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4062.capture20160219144141503_5F00_0F251C6C.png"><img loading="lazy" title="capture20160219144141503" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="capture20160219144141503" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2402.capture20160219144141503_thumb_4A78822A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2402.capture20160219144141503_5F00_thumb_5F00_4A78822A.png" width="464" height="376" /></a>

Run this powershell script from the Azure Powershell (or do similar using the Azure CLI):

Remove-AzureRmResource -ResourceId /subscriptions/<SUBCRIPTION\_ID>/resourcegroups/<RESOURCE\_GROUP>/providers  
/Microsoft.Web/sites/<APP_NAME>/providers/Microsoft.Resources/links/mobile-notificationhub

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8875.snip_20160219145313_46020163.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8875.snip_5F00_20160219145313_5F00_46020163.png"><img loading="lazy" title="snip_20160219145313" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="snip_20160219145313" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6558.snip_20160219145313_thumb_139E2DE4.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6558.snip_5F00_20160219145313_5F00_thumb_5F00_139E2DE4.png" width="510" height="88" /></a>

And I get my wizard back!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1778.capture20160219145117858_7A362AA9.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1778.capture20160219145117858_5F00_7A362AA9.png"><img loading="lazy" title="capture20160219145117858" style="border-top: 0px; border-right: 0px; background-image: none; border-bottom: 0px; padding-top: 0px; padding-left: 0px; border-left: 0px; display: inline; padding-right: 0px" border="0" alt="capture20160219145117858" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6661.capture20160219145117858_thumb_55A49D25.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6661.capture20160219145117858_5F00_thumb_5F00_55A49D25.png" width="492" height="411" /></a>

Let me know if this is helpful by dropping me a note!