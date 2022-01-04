---
id: 1475
title: How to deny HTTP methods (or verbs) in Azure Web Apps
date: 2016-09-20T20:05:16-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1475
permalink: /2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to deny HTTP methods (or verbs) in Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/20/how-to-deny-http-methods-or-verbs-in-azure-web-apps/" />
    <meta name="twitter:description" content="If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file. Add the following or create the following sections if they do not exist in your &lt;configuration&gt; section of your Azure Web App, web.config file: &lt;system.webServer&gt; &lt;validation validateIntegratedModeConfiguration=&#8221;false&#8221; /&gt; &lt;modules runAllManagedModulesForAllRequests=&#8221;true&#8221; /&gt; &lt;handlers&gt; &lt;add..." />
    
categories:
  - Uncategorized
---
If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file.

Add the following or create the following sections if they do not exist in your <configuration> section of your Azure Web App, web.config file:

<system.webServer>  
&nbsp;&nbsp;&nbsp; <validation validateIntegratedModeConfiguration=&#8221;false&#8221; />  
&nbsp;&nbsp;&nbsp; <modules runAllManagedModulesForAllRequests=&#8221;true&#8221; />  
&nbsp;&nbsp;&nbsp; <handlers>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add name=&#8221;DenyOTH&#8221; verb=&#8221;OPTIONS,TRACE,HEAD&#8221; path=&#8221;*&#8221; type=&#8221;System.Web.HttpMethodNotAllowedHandler&#8221; />  
</handlers>  
</system.webServer> 

&nbsp;

Once you add this, the response to any HTTP Verb in the verb list (in this case &#8220;OPTIONS,TRACE,HEAD&#8221;) will result in a response: 405 Method Not Allowed.

&nbsp;

Let me know if this helped you out!

Also, see this blog post for removing headers: [Remove ‘Server’ and ‘X-Powered-By’ headers from your Azure Mobile Apps](https://blogs.msdn.microsoft.com/jpsanders/2015/10/07/remove-server-and-x-powered-by-headers-from-your-azure-mobile-apps/)