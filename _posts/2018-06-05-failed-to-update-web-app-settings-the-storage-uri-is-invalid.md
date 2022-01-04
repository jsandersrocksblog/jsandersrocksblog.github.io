---
id: 5345
title: 'Failed to update web app settings: The storage URI is invalid'
date: 2018-06-05T14:20:38-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5345
permalink: /2018/06/05/failed-to-update-web-app-settings-the-storage-uri-is-invalid/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Failed to update web app settings: The storage URI is invalid" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/06/05/failed-to-update-web-app-settings-the-storage-uri-is-invalid/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview When updating your Azure Function App storage account keys, if you specify the wrong key… You could get an error including the text: Failed to update web app settings:&nbsp; Bad Request&nbsp; The storage URI is invalid ExtendedCode:04203 No valid combination of account information found Fix I found the older version of the key did..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Failed to update web app settings: The storage URI is invalid" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/06/05/failed-to-update-web-app-settings-the-storage-uri-is-invalid/" />
    <meta name="twitter:description" content="Overview When updating your Azure Function App storage account keys, if you specify the wrong key… You could get an error including the text: Failed to update web app settings:&nbsp; Bad Request&nbsp; The storage URI is invalid ExtendedCode:04203 No valid combination of account information found Fix I found the older version of the key did..." />
    
categories:
  - Uncategorized
---
 

When updating your Azure Function App storage account keys, if you specify the wrong key… You could get an error including the text:

Failed to update web app settings:&nbsp; Bad Request&nbsp; The storage URI is invalid ExtendedCode:04203 No valid combination of account information found

[<img loading="lazy" title="Capture" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="Capture" src="/assets/images/2018/06/Capture_thumb.png" width="478" height="292" />](/assets/images/2018/06/Capture.png)

# Fix

I found the older version of the key did not have the suffix listed.&nbsp; When I generated the new key it did… thinking that it was invalid I removed it and then got this error.&nbsp; Ensure that you copy and use the entire key as provided!

Example: DefaultEndpointsProtocol=https;AccountName=cs2d3de4593cb35x492dxa63;AccountKey=xxxxxxxxxxxxx==;<font style="background-color: #ffff00">EndpointSuffix=core.windows.net</font>

<font style="background-color: #ffff00"></font>&nbsp;

Please drop me a note if you found this useful!

<font style="background-color: #ffff00"></font>