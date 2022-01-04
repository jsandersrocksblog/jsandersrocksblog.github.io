---
id: 5663
title: Azure Web Job not running
date: 2020-08-05T07:20:07-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5663
permalink: /2020/08/05/azure-web-job-not-running/
categories:
  - Uncategorized
---
Super simple.&nbsp; Enable “Always on” for the web site.

The SCM Web Site (also known as Kudu) can stop due to inactivity on it or the web site if Always On was not enabled for this site.

As discussed at [https://docs.microsoft.com/en-us/azure/app-service/webjobs-dotnet-deploy-vs#scheduling-a-triggered-webjob](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fapp-service%2Fwebjobs-dotnet-deploy-vs%23scheduling-a-triggered-webjob&data=02%7C01%7Cjsanders%40microsoft.com%7C6f6a969bfed1457c64f108d839393199%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637322265223030493&sdata=uCja47GLhayG%2Bltl%2B2tITEtEaGQNHq5B4l2FrDnA6Pg%3D&reserved=0)

“A web app can time out after 20 minutes of inactivity. Only requests to the actual web app reset the timer. Viewing the app&#8217;s configuration in the Azure portal or making requests to the advanced tools site ([https://<app_name>.scm.azurewebsites.net](https://%3capp_name%3e.scm.azurewebsites.net)) don&#8217;t reset the timer. If your app runs continuous or scheduled (Timer trigger) WebJobs, enable Always On to ensure that the WebJobs run reliably. This feature is available only in the Basic, Standard, and Premium pricing tiers.”