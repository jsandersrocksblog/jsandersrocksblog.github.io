---
id: 2027
title: Problem adding Push Notification Hub to Azure App Service Slot
date: 2017-03-30T18:53:08-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2027
permalink: /2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta property="og:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta name="twitter:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta name="twitter:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta property="og:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta name="twitter:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta name="twitter:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta property="og:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta name="twitter:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta name="twitter:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta property="og:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta name="twitter:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta name="twitter:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta property="og:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Problem adding Push Notification Hub to Azure App Service Slot" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/30/problem-adding-push-notification-hub-to-azure-app-service-slot/" />
    <meta name="twitter:description" content="Overview You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App..." />
    <meta name="twitter:image" content="/assets/images/2017/03/capture20170330144721190_thumb.png" />
    
categories:
  - Uncategorized
---

You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App to Notification Hub” forever.

[<img loading="lazy" title="capture20170330144721190" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170330144721190" src="/assets/images/2017/03/capture20170330144721190_thumb.png" width="508" height="252" />](/assets/images/2017/03/capture20170330144721190.png)

## 

## Fix

The Push Notification Hub settings from the main site are inherited by the slots.&nbsp; You cannot define a unique Push setting for the slots.&nbsp; If you need different settings for testing for example, you need to simply create a new App Service and deploy to that.

## More info

Drop me a note if you found this useful!