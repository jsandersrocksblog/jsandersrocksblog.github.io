---
id: 2115
title: Page Loads slow and you notice certain files (js, html) seem to be extra slow downloading
date: 2017-04-14T18:28:53-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2115
permalink: /2017/04/14/page-loads-slow-and-you-notice-certain-files-js-html-see-to-be-extra-slow-downloading/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Page Loads slow and you notice certain files (js, html) see to be extra slow downloading" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/04/14/page-loads-slow-and-you-notice-certain-files-js-html-see-to-be-extra-slow-downloading/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Symptom You noticed slow performance with particular files (.js, .html and more) were downloading very slowly Cause Certain files are sent back to the client as chunked encoded.&nbsp; CDNs and Web Servers both show this behavior.&nbsp; Chunked downloads are very expensive in terms of speed because each chunk is in essence treated like a separate..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Page Loads slow and you notice certain files (js, html) see to be extra slow downloading" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/04/14/page-loads-slow-and-you-notice-certain-files-js-html-see-to-be-extra-slow-downloading/" />
    <meta name="twitter:description" content="Symptom You noticed slow performance with particular files (.js, .html and more) were downloading very slowly Cause Certain files are sent back to the client as chunked encoded.&nbsp; CDNs and Web Servers both show this behavior.&nbsp; Chunked downloads are very expensive in terms of speed because each chunk is in essence treated like a separate..." />
    
categories:
  - Uncategorized
---
## Symptom

You notice particular files (.js, .html and more) are downloading very slowly

## Cause

Certain files are sent back to the client as chunked encoded.&nbsp; CDNs and Web Servers both show this behavior.&nbsp; Chunked downloads are very expensive in terms of speed because each chunk is in essence treated like a separate download.&nbsp; Chunked encoding is based on file type and file size. 

## OK, so WHY would Web Servers and CDNs do this?

This is so that modern browsers can start rendering content before the entire file arrives at the client. This includes html and js files. Typically most websites keep individual resources under 25K and that is why for most applications the delay is negligible. If your file is big (by web standards > 25 K) the delay you see is probably due to chunked encoding.&nbsp; Also, some clients will not cache a file over 25K (another reason to keep the download small) such as some smaller devices like phones.

## Resolution

Make the files smaller is the best resolution.&nbsp; For example: Minify or break up large .js files.&nbsp; There are a TON of suggestions for increasing the speed of your web page.&nbsp; You can use Bing or Google to find them.&nbsp; Basically, put script at the bottom of your page and use individual smaller downloads.&nbsp; Visit a ‘good performing’ page and use the F12 tools of your browser or Fiddler from Telerik to see what is coming down, how big it is and if it is coming down in parallel.&nbsp; 

If you are simply looking to download these files faster as is (lets say you have an API that is downloading JS files) and you are using IIS or Azure App Services (aka Azure Web Apps) you can workaround this chunked encoded behavior by adding to your web.config in the <system.webServer> section:  
<serverRuntime enabled=&#8221;true&#8221; frequentHitThreshold=&#8221;1&#8243; frequentHitTimePeriod=&#8221;00:00:20&#8243; />

## Conclusion

Web page performance tools are available to help you speed up your pages.&nbsp; This particular post explains why some large files take a long time to download due to chunked encoding.&nbsp; I hope you find this a useful explanation of why these files take longer to download and what to do to speed things up!