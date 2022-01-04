---
id: 1855
title: 'Cannot read property &#039;listRegistrationsByTag&#039; of undefined&#039; (Azure App Services)'
date: 2017-02-23T16:14:37-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1855
permalink: /2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta name="twitter:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta name="twitter:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta name="twitter:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta name="twitter:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; (Azure App Services)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/23/cannot-read-property-listregistrationsbytag-of-undefined-azure-app-services/" />
    <meta name="twitter:description" content="Situation: You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time Problem: Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; Cause: The Portal blade does..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170223080119644_thumb.png" />
    
categories:
  - Uncategorized
---
Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; 


## Problem:
You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time 

## Cause:

The Portal blade does not set the Application Setting MS_NotificationHubName 

## Workaround:

Add MS\_NotificationHubName in the Application settings.&nbsp; The name will be the name of your Notification Hub.&nbsp; It is the last item after the \ in the setting MS\_NotificationHubId or you can get in from the notification Hub blade: 

[<img loading="lazy" title="capture20170223080119644" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170223080119644" src="/assets/images/2017/02/capture20170223080119644_thumb.png" width="815" height="386" />](/assets/images/2017/02/capture20170223080119644.png) 

&nbsp; 

[<img loading="lazy" title="capture20170223080212770" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170223080212770" src="/assets/images/2017/02/capture20170223080212770_thumb.png" width="753" height="379" />](/assets/images/2017/02/capture20170223080212770.png)

## More information:

Once this is fixed the Portal Blade will set the MS_NotificationHubName for you when you walk through the Portal setup of Push notifications.&nbsp; At that time I will update this Blog!&nbsp; If you need further help, you can certainly open a support case through the Azure Portal.