---
id: 1805
title: Azure Traffic Manager probe degraded due to 401 from Azure Web App
date: 2017-02-06T15:50:11-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1805
permalink: /2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta property="og:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Traffic Manager probe degraded due to 401 from Azure Web App" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/06/azure-traffic-manager-probe-degraded-due-to-401-from-azure-web-app/" />
    <meta name="twitter:description" content="Symptom Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded. Cause Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down..." />
    <meta name="twitter:image" content="/assets/images/2017/02/snip_20170206104636_thumb.png" />
    
categories:
  - Uncategorized
---
Your Azure Web App (or any Azure App Service) has authentication enabled but you want to use Traffic Manager.&nbsp; Since the probe returns the HTTP status code 401, the endpoint is considered degraded.&nbsp; This blog only applies to <a href="https://docs.microsoft.com/en-us/azure/app-service/app-service-authentication-overview" target="_blank" rel="noopener noreferrer">Azure App Service Authentication</a>.&nbsp; If you are using a third Party like Auth0 you need to provide a non-authenticated URL using a different method.

## Cause

Whatever you use for an endpoint in Azure Traffic Manager, it must return a 200.&nbsp; Your site is locked down so any request returns 401

## Solution

<font style="background-color: rgb(255, 255, 0);">UPDATE 6/3/2020 – You can now use WEBSITE_WARMUP_PATH per: </font><a href="https://github.com/cgillum/easyauth/wiki/Advanced-Application-Settings" target="_blank" rel="noopener noreferrer"><font style="background-color: rgb(255, 255, 0);">https://github.com/cgillum/easyauth/wiki/Advanced-Application-Settings</font></a><font style="background-color: rgb(255, 255, 0);">&nbsp; and ignore the below instructions:</font>

Use URL Authorization rules with a special Route to allow the ping to succeed.&nbsp; Note:&nbsp; <font style="background-color: rgb(255, 255, 0);">This is in preview</font>, so there may be updates as this matures.

  1. Create a directory in your application and call it whatever you wish (for this sample I am using TMStatus). 
      * Put an html file in it and call it something like status.html. 
          * Next add URL Authorization Rule to disable authentication for that directory and ensure you place this json file it in the wwwroot directory.&nbsp; See: <a href="https://blogs.msdn.microsoft.com/appserviceteam/2016/11/17/url-authorization-rules/" target="_blank" rel="noopener noreferrer">URL Authorization Rules</a>&nbsp; In this case All routes will be RedirectedToLogin, however the /TMStatus route will allow anonymous requests.</ol> 
        Your json would look something like this:
        
        {  
        &nbsp;&nbsp; &#8220;routes&#8221;: [{  
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;path_prefix&#8221;: &#8220;/&#8221;,  
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;policies&#8221;: { &#8220;unauthenticated_action&#8221;: &#8220;RedirectToLoginPage&#8221; }  
        &nbsp;&nbsp;&nbsp;&nbsp; },{  
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;path_prefix&#8221;: &#8220;/TMStatus&#8221;,  
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;policies&#8221;: { &#8220;unauthenticated_action&#8221;: &#8220;AllowAnonymous&#8221; }  
        &nbsp;&nbsp;&nbsp;&nbsp; }]  
        }
        
        &nbsp;&nbsp; 4. Configure Authorization to Allow Anonymous requests in your Azure Portal:
        
        [<img loading="lazy" width="486" height="289" title="snip_20170206104636" style="border-width: 0px; padding-top: 0px; padding-right: 0px; padding-left: 0px;" alt="snip_20170206104636" src="/assets/images/2017/02/snip_20170206104636_thumb.png" border="0" />](/assets/images/2017/02/snip_20170206104636.png)
        
        This should restart your web app and pickup the changes, then point traffic manager to your app/TMStatus/status.html&nbsp; (or whatever you choose to call these from above).
        
        Now when the ping from traffic manager hits this endpoint, it will return a 200 instead of a 401.
        
        ## Troubleshooting problems
        
        <a href="https://blogs.msdn.microsoft.com/appserviceteam/2016/11/17/url-authorization-rules/" target="_blank" rel="noopener noreferrer">URL Authorization Rules</a> has a section that talks about using verbose application logging for troubleshooting [enabling Application Logging](https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-enable-diagnostic-log#a-nameenablediagahow-to-enable-diagnostics).&nbsp; If you do not see the logs common causes are that you did not restart the app or you did not select ‘Allow Anonymous requests (no action) as pictured above.