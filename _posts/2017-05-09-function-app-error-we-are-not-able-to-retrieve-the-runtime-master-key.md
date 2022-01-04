---
id: 2135
title: 'Azure Function App Error: We are not able to retrieve the runtime master key'
date: 2017-05-09T18:59:31-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2135
permalink: /2017/05/09/function-app-error-we-are-not-able-to-retrieve-the-runtime-master-key/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure Function App Error: We are not able to retrieve the runtime master key" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/09/function-app-error-we-are-not-able-to-retrieve-the-runtime-master-key/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview When you access an Azure Function app from the portal it will attempt to retrieve the Function runtime keys.  This is documented at https://github.com/Azure/azure-webjobs-sdk-script/wiki/Http-Functions#api-keys .  There are a number of reasons why the keys cannot be retrieved and this article documents a recent change that means you may see this issue. Possible errors &#8220;We..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure Function App Error: We are not able to retrieve the runtime master key" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/09/function-app-error-we-are-not-able-to-retrieve-the-runtime-master-key/" />
    <meta name="twitter:description" content="Overview When you access an Azure Function app from the portal it will attempt to retrieve the Function runtime keys.  This is documented at https://github.com/Azure/azure-webjobs-sdk-script/wiki/Http-Functions#api-keys .  There are a number of reasons why the keys cannot be retrieved and this article documents a recent change that means you may see this issue. Possible errors &#8220;We..." />
    
categories:
  - Uncategorized
---


When you access an Azure Function app from the portal it will attempt to retrieve the Function runtime keys.&nbsp; This is documented at <https://github.com/Azure/azure-webjobs-sdk-script/wiki/Http-Functions#api-keys> .&nbsp; There are a number of reasons why the keys cannot be retrieved and this article documents a recent change that means you may see this issue.

## Possible errors

&#8220;We are not able to retrieve the runtime master key. Please try again later&#8221;

or

&#8220;We are not able to retrieve the keys for function &#8230;..This can happen if the runtime is not able to load your function app&#8221;

or

&#8220;We are not able to create or update the key default for function &#8230;&#8230;&#8221;

## Possible solutions

The Azure Function runtime has been updated to include Application Insights support. This was previously offered in the beta runtime which you accessed by setting your Functions Runtime version to “beta”.&nbsp; Some of these problems are related to the fact that beta is no longer usable.&nbsp; **Ensure you are not on beta.**

These are a few solutions.

1) You are on the beta. At this point, the beta is no longer usable, and you need to switch the app setting back to ~1.

<https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference-csharp#versioning>

2) If you&#8217;re not on the beta and are still seeing this, try Stopping and then Starting your Function App

3) if neither of those work make sure you are using the latest version of the runtime:

<https://github.com/Azure/azure-webjobs-sdk-script/wiki/Deploying-the-Functions-runtime-as-a-private-site-extension>.

This link helps run through it but make sure you are using this commit in particular:

<https://github.com/Azure/azure-webjobs-sdk-script/commit/6008a50b878e8698ad3a5d436567be78a2890e50>

NOTE: that using a private site extension is by nature unsupported. Once you move to that mode, you are responsible for keeping it updated as the product evolves. Just merge the latest bits and redeploy, and you&#8217;ll be ok.

4)&nbsp; App has a runtime error (check Failed Request Tracing for errors)

5)&nbsp; App has exhausted some resource such as threads, cpu, memory etc…&nbsp; (Typically deadlocked functions due to waiting on async tasks using .Result)

6)&nbsp; Web browser is caching an old result (clear the browser cache, log out and back in).

7)&nbsp; You regenerated the keys but did not set them in the app settings: <a href="https://social.msdn.microsoft.com/Forums/en-US/dc42cb2f-43c8-4047-b1eb-57590c61957f/azure-functions-stop-responding-saying-we-are-unable-to-access-your-function-keys?forum=AzureFunctions" target="_blank">https://social.msdn.microsoft.com/Forums/en-US/dc42cb2f-43c8-4047-b1eb-57590c61957f/azure-functions-stop-responding-saying-we-are-unable-to-access-your-function-keys?forum=AzureFunctions </a>

8) host.json is not properly formatted json or invalid

&nbsp;

## 

## Reference

<https://github.com/Azure/Azure-Functions/issues/226#issuecomment-300223858>

## 

## Conclusion

This is just a simple quick post that hopefully will set you in the right direction!&nbsp; Drop me a note if this was helpful to you.&nbsp; Thanks to Tyler Spring from my team for surfacing these issues and helping with the post.

For more assistance please jump on to the github issues, or functions forums and StackOverflow.