---
id: 2185
title: How to run classic ASP on Azure Web Apps
date: 2017-05-11T13:47:25-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2185
permalink: /2017/05/11/how-to-run-classic-asp-on-azure-web-apps/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to run classic ASP on Azure Web Apps" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/11/how-to-run-classic-asp-on-azure-web-apps/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview We mention you can use ASP on Azure Web Apps but documentation is a bit scarce.&nbsp; This walkthrough will show how to deploy a simple vbscript ASP page to a Azure Web App. Steps Create a Classic ASP page I will use the App Service Editor built into the Azure Portal.&nbsp; Simply go to..." />
    <meta property="og:image" content="/assets/images/2017/05/snip_20170511085109_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to run classic ASP on Azure Web Apps" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/11/how-to-run-classic-asp-on-azure-web-apps/" />
    <meta name="twitter:description" content="Overview We mention you can use ASP on Azure Web Apps but documentation is a bit scarce.&nbsp; This walkthrough will show how to deploy a simple vbscript ASP page to a Azure Web App. Steps Create a Classic ASP page I will use the App Service Editor built into the Azure Portal.&nbsp; Simply go to..." />
    <meta name="twitter:image" content="/assets/images/2017/05/snip_20170511085109_thumb.png" />
    
categories:
  - Uncategorized
---


We mention you can use ASP on Azure Web Apps but documentation is a bit scarce.&nbsp; This walkthrough will show how to deploy a simple vbscript ASP page to a Azure Web App.

## Steps

### Create a Classic ASP page

I will use the App Service Editor built into the Azure Portal.&nbsp; Simply go to your Web App (or create one if you don’t have one yet) and choose the App Service Editor:

[<img loading="lazy" title="snip_20170511085109" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170511085109" src="/assets/images/2017/05/snip_20170511085109_thumb.png" width="424" height="293" />](/assets/images/2017/05/snip_20170511085109.png)

Hint:&nbsp; You can get there quickly if you know your Web App Name by going to https://YOURWEBAPPNAME.scm.azurewebsites.net/dev 

In the Editor, hover over the WWWROOT directory, then choose the New File icon and call your page whatever you wish (using&nbsp; .asp as the extension).&nbsp; In this case I choose default.asp so it will run as the default page.&nbsp;&nbsp; Then add your VBScript asp page code (note you need to specify the Language parameter as shown:

&nbsp;

[<img loading="lazy" title="snip_20170511085403" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170511085403" src="/assets/images/2017/05/snip_20170511085403_thumb.png" width="914" height="436" />](/assets/images/2017/05/snip_20170511085403.png)

Sample code:

<pre class="code"><span style="background: yellow;color: black">&lt;%</span><span style="color: blue">@ </span><span style="color: red">Language</span><span style="color: blue">="VBScript" </span><span style="background: yellow;color: black">%&gt;
</span><span style="color: black"> </span><span style="color: blue">&lt;</span><span style="color: maroon">html</span><span style="color: blue">&gt;
        &lt;</span><span style="color: maroon">head</span><span style="color: blue">&gt; &lt;/</span><span style="color: maroon">head</span><span style="color: blue">&gt;
        &lt;</span><span style="color: maroon">body</span><span style="color: blue">&gt;
            &lt;</span><span style="color: maroon">h1</span><span style="color: blue">&gt;</span><span style="color: black">VBScript Powered ASP page on Azure Web Apps </span><span style="color: blue">&lt;/</span><span style="color: maroon">h1</span><span style="color: blue">&gt;
    </span><span style="background: yellow;color: black">&lt;%</span><span style="color: black">
  Dim dtmHour
  dtmHour = Hour(Now())
  If dtmHour &lt; 12 Then
    strGreeting = "Good Morning!"
  Else
    strGreeting = "Hello!"
  End If
</span><span style="background: yellow;color: black">%&gt;</span><span style="color: black">
</span><span style="background: yellow;color: black">&lt;%</span><span style="color: blue">= </span><span style="color: black">strGreeting </span><span style="background: yellow;color: black">%&gt;</span><span style="color: black">
        </span><span style="color: blue">&lt;/</span><span style="color: maroon">body</span><span style="color: blue">&gt;
&lt;/</span><span style="color: maroon">html</span><span style="color: blue">&gt;</span></pre>

&nbsp;

## 

## Test it

Now simply browse to your site to see the results!

[<img loading="lazy" title="snip_20170511085701" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170511085701" src="/assets/images/2017/05/snip_20170511085701_thumb.png" width="560" height="192" />](/assets/images/2017/05/snip_20170511085701.png)

## 

## Conclusion

ASP is supported and enabled by default in Azure Web Apps.&nbsp; You can easily add ASP pages to you Web App and run them!