---
id: 5650
title: Azure App Service Authentication CORS error (Easy Auth)
date: 2020-04-23T14:29:56-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5650
permalink: /2020/04/23/azure-app-service-authentication-cors-error-easy-auth/
categories:
  - Uncategorized
---
 

Using Easy Auth you might see this error:

Failed to load <https://login.windows.net/>….: Response to preflight request doesn&#8217;t pass access control check: No &#8216;Access-Control-Allow-Origin&#8217; header is present on the requested resource. Origin &#8216;<https://sitename.azurewebsites.net>&#8216; is therefore not allowed access. If an opaque response serves your needs, set the request&#8217;s mode to &#8216;no-cors&#8217; to fetch the resource with CORS disabled.

## Cause

This behavior can occur if they are using fetch within their application. When using EasyAuth, a &#8220;Cookie&#8221; header is passed with the &#8220;AppServiceAuthSession&#8221; token. If the header is missing, an &#8220;authorize&#8221; request will be sent from provider. Sample below.

> Accept:  
> text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,\*/\*;q=0.8
> 
> Accept-Encoding:  
> gzip, deflate, br
> 
> Accept-Language:  
> en-US,en;q=0.9
> 
> Cache-Control:  
> no-cache
> 
> Connection:  
> keep-alive
> 
> Cookie:  
> ARRAffinity=<removed>; AppServiceAuthSession=<removed>
> 
> Host:  
> sitename.azurewebsites.net



## Solution

By default, fetch doesn&#8217;t automatically send cookies. To resolve the issue, the customer will need to add the &#8220;credentials&#8221; property with either &#8220;same-origin&#8221; or &#8220;include&#8221; provided.

Example-

> sendData() {
> 
> fetch(&#8216;/api/testapi&#8217;, {
> 
> method: &#8216;POST&#8217;,
> 
> body: JSON.stringify({
> 
> &nbsp;&nbsp;&nbsp;&nbsp; data: this.state.text
> 
> }),
> 
> credentials: &#8216;same-origin&#8217;,
> 
> headers: { &#8216;Content-Type&#8217;: &#8216;application/json&#8217; },
> 
> })

Additional information for fetch can be found at <https://github.com/github/fetch#sending-cookies>



Acknowledgement:&nbsp; Thanks to my Colleague Toan Nguyen for this information!