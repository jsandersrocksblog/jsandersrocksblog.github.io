---
id: 1775
title: How to get a full memory dump in Azure App Services
date: 2017-02-02T17:10:24-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1775
permalink: /2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to get a full memory dump in Azure App Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta property="og:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to get a full memory dump in Azure App Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/02/02/how-to-get-a-full-memory-dump-in-azure-app-services/" />
    <meta name="twitter:description" content="There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!&nbsp; Here is my simple version Go to the Kudu site for your Azure Web App (or App..." />
    <meta name="twitter:image" content="/assets/images/2017/02/capture20170202114609022_thumb.png" />
    
categories:
  - Uncategorized
---
There are a ton of blogs on getting full memory dumps but some get complicated.&nbsp; **Note then when you create a full memory dump it will have the effect of pausing your web app so use this judiciously!**&nbsp; Here is my simple version

## Go to the Kudu site for your Azure Web App (or App Service)

You can do this from the portal for your app or simply use the azurewebsites.net url for your app and insert <font style="background-color: #ffff00">.scm</font> after the name.&nbsp; For example:

https://problemwebapp<font style="background-color: #ffff00">.scm</font>.azurewebsites.net

## Find the Process ID (pid) of the process you wish to get a dump for

Navigate to the Process Explorer by clicking on the **Process explorer** tab at the top of the page.

You will want the pid for the w3wp.exe process (in this case 5484) that is running your code.&nbsp; This is NOT the SCM process.&nbsp; That is the process running the Kudu site.&nbsp; Save this PID for use below.

Note: .Net Core apps will be a sub process listed under the w3wp.exe process.&nbsp; Java process would be a different process as well

[<img loading="lazy" title="capture20170202114609022" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170202114609022" src="/assets/images/2017/02/capture20170202114609022_thumb.png" width="804" height="227" />](/assets/images/2017/02/capture20170202114609022.png)

## Go do the Debug console and capture the dump

Navigate by choosing the Debug console, then CMD pull down to get to the command line interface:

[<img loading="lazy" title="capture20170202115040673" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170202115040673" src="/assets/images/2017/02/capture20170202115040673_thumb.png" width="220" height="143" />](/assets/images/2017/02/capture20170202115040673.png)

Create a directory for the dumps and navigate there as pictured below using the commands: cd logfiles, md dumps, cd dumps

[<img loading="lazy" title="capture20170202115311981" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170202115311981" src="/assets/images/2017/02/capture20170202115311981_thumb.png" width="454" height="603" />](/assets/images/2017/02/capture20170202115311981.png)

Now you can create the full memory dump with this command.  **The Number after the –ma is the <font style="background-color: #ffff00">PID</font> you determined from above.**

d:\devtools\sysinternals\procdump -accepteula -ma **<font style="background-color: #ffff00">5484</font>** 

And this will write a dump to the current directory:

[<img loading="lazy" title="capture20170202115903578" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170202115903578" src="/assets/images/2017/02/capture20170202115903578_thumb.png" width="652" height="519" />](/assets/images/2017/02/capture20170202115903578.png)

Note:&nbsp; You can use several different procdump commands.&nbsp; See this site for more options: <a href="https://technet.microsoft.com/en-us/sysinternals/dd996900.aspx" target="_blank">ProcDump &#8211; technet.microsoft.com</a>****

## Download Dumps for analysis

The easiest way is to navigate back to the log files directory and click on the download icon for the entire directory.&nbsp; This will zip that folder and download it.

You can navigate through the directory structure by clicking on the icons at the top.&nbsp; For instance click on the picture of the house, then the text LogFiles next to the folder icon.&nbsp; Click on the down load icon for the dumps directory you created the dump in.

[<img loading="lazy" title="snip_20170202120509" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170202120509" src="/assets/images/2017/02/snip_20170202120509_thumb.png" width="244" height="116" />](/assets/images/2017/02/snip_20170202120509.png)

&nbsp;

[<img loading="lazy" title="capture20170202120545552" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170202120545552" src="/assets/images/2017/02/capture20170202120545552_thumb.png" width="1150" height="80" />](/assets/images/2017/02/capture20170202120545552.png)

&nbsp;

Alternatively you can zip files using the built in tools:

d:\7zip\7za a dumps.zip w3wp.exe\_170202\_165808.dmp 

And download the zip by navigating to it in the Debug console and using the download console, or not zip the dump at all and download it! 

## 

## 

## 

## Analyzing the dump

By far DebugDiag is the fasted way to analyze your dump.&nbsp; You could also use Visual Studio.

<a title="Download Debug Diagnostic Tool v2 Update 2 from Official" href="http://www.microsoft.com/en-us/download/details.aspx?id=49924" target="_blank">Download Debug Diagnostic Tool v2 Update 2 from Official</a>

&nbsp;

Drop me a note if you thought this was useful!