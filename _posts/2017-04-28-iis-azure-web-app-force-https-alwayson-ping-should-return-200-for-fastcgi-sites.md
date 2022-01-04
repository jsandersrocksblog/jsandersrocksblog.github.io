---
id: 2125
title: 'IIS Azure Web App &#8211; Force HTTPS AlwaysOn ping should return 200 for FastCGI sites'
date: 2017-04-28T13:35:56-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2125
permalink: /2017/04/28/iis-azure-web-app-force-https-alwayson-ping-should-return-200-for-fastcgi-sites/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="IIS Azure Web App &#8211; Force HTTPS AlwaysOn ping should return 200 for FastCGI sites" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/04/28/iis-azure-web-app-force-https-alwayson-ping-should-return-200-for-fastcgi-sites/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview PHP, Java and other FastCGI hosted environments should respond to an Always On ping to keep the child process warmed up.&nbsp; Specifically in Azure App Services we send a request to the Root of the site with the header User-Agent: AlwaysOn.&nbsp; If you are forcing HTTPS using a Url Rewrite rule, the Always On..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="IIS Azure Web App &#8211; Force HTTPS AlwaysOn ping should return 200 for FastCGI sites" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/04/28/iis-azure-web-app-force-https-alwayson-ping-should-return-200-for-fastcgi-sites/" />
    <meta name="twitter:description" content="Overview PHP, Java and other FastCGI hosted environments should respond to an Always On ping to keep the child process warmed up.&nbsp; Specifically in Azure App Services we send a request to the Root of the site with the header User-Agent: AlwaysOn.&nbsp; If you are forcing HTTPS using a Url Rewrite rule, the Always On..." />
    
categories:
  - Uncategorized
---

PHP, Java and other FastCGI hosted environments should respond to an Always On ping to keep the child process warmed up.&nbsp; Specifically in Azure App Services we send a request to the Root of the site with the header User-Agent: AlwaysOn.&nbsp; If you are forcing HTTPS using a Url Rewrite rule, the Always On ping will get a redirect but will not follow that redirect and therefore the FastCGI module will not be hit and kept warm.

## Solution

You can simply add a rule that will look for the ping to the root of your site and the User-Agent: AlwaysOn header and not force HTTPS.&nbsp; The easiest way to do this is to add this Url Rewrite rule before the Force HTTPS rule as follows:

<system.webServer>  
&nbsp;&nbsp;&nbsp; <rewrite>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <rules>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <rule name=&#8221;No HTTPS for user agent AlwaysOn and Root of site&#8221; stopProcessing=&#8221;true&#8221;>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <match url=&#8221;^$&#8221;/>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <conditions>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add input=&#8221;{HTTP\_USER\_AGENT}&#8221; pattern=&#8221;^AlwaysOn$&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </conditions>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <action type=&#8221;None&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </rule>

The above rule will look for a match for a request to the root and with a User-Agent header of “AlwaysOn”.&nbsp; If that condition is met, no other rules are processed.

## Conclusion

If you find this blog is useful please drop me a note!&nbsp; Ref:&nbsp; [http://microsoftazurewebsitescheatsheet.info/](http://microsoftazurewebsitescheatsheet.info/ "http://microsoftazurewebsitescheatsheet.info/")&nbsp; Force HTTPS