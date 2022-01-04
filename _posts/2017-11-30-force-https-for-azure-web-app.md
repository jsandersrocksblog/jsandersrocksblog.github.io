---
id: 3885
title: Force HTTPS for Azure Web App
date: 2017-11-30T08:12:34-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=3885
permalink: /2017/11/30/force-https-for-azure-web-app/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Force HTTPS for Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/30/force-https-for-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Sometimes you need or want to force HTTPS for Azure App Services (Azure Web App, Azure Mobile App, Azure Function App, etc…).&nbsp; In the past you could do this with a web.config change. Solution You can now simply do this as follows: Go to the Custom Domains section of you app and set HTTPS..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Force HTTPS for Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/30/force-https-for-azure-web-app/" />
    <meta name="twitter:description" content="Overview Sometimes you need or want to force HTTPS for Azure App Services (Azure Web App, Azure Mobile App, Azure Function App, etc…).&nbsp; In the past you could do this with a web.config change. Solution You can now simply do this as follows: Go to the Custom Domains section of you app and set HTTPS..." />
    
categories:
  - Uncategorized
---


Sometimes you need or want to force HTTPS for Azure App Services (Azure Web App, Azure Mobile App, Azure Function App, etc…).&nbsp; In the past you could do this with a web.config change.

## Solution

You can now simply do this as follows: Go to the Custom Domains section of you app and set HTTPS Only to On (Off is the default) and Save.

[<img loading="lazy" title="ForceHTTPS" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="ForceHTTPS" src="/assets/images/2017/11/ForceHTTPS_thumb.png" width="441" height="531" />](/assets/images/2017/11/ForceHTTPS1.png)