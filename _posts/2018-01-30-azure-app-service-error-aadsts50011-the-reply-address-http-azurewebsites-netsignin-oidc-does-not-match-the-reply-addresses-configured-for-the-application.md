---
id: 4215
title: 'Azure App Service error: AADSTS50011: The reply address &#039;http://.azurewebsites.net/signin-oidc&#039; does not match the reply addresses configured for the application:'
date: 2018-01-30T15:00:25-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=4215
permalink: /2018/01/30/azure-app-service-error-aadsts50011-the-reply-address-http-azurewebsites-netsignin-oidc-does-not-match-the-reply-addresses-configured-for-the-application/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure App Service error: AADSTS50011: The reply address &#8216;http://.azurewebsites.net/signin-oidc&#8217; does not match the reply addresses configured for the application:" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/01/30/azure-app-service-error-aadsts50011-the-reply-address-http-azurewebsites-netsignin-oidc-does-not-match-the-reply-addresses-configured-for-the-application/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview When you deploy an Azure Active Directory application that was working great locally you may get the following error when logging in:&nbsp; AADSTS50011: The reply address &#039;http://&lt;yourwebapp&gt;.azurewebsites.net/signin-oidc&#039; does not match the reply addresses configured for the application: &#039;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#039;. More details: not specified How to fix this This error says it all!&nbsp; When you deploy..." />
    <meta property="og:image" content="/assets/images/2018/01/appregistration_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure App Service error: AADSTS50011: The reply address &#8216;http://.azurewebsites.net/signin-oidc&#8217; does not match the reply addresses configured for the application:" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/01/30/azure-app-service-error-aadsts50011-the-reply-address-http-azurewebsites-netsignin-oidc-does-not-match-the-reply-addresses-configured-for-the-application/" />
    <meta name="twitter:description" content="Overview When you deploy an Azure Active Directory application that was working great locally you may get the following error when logging in:&nbsp; AADSTS50011: The reply address &#039;http://&lt;yourwebapp&gt;.azurewebsites.net/signin-oidc&#039; does not match the reply addresses configured for the application: &#039;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#039;. More details: not specified How to fix this This error says it all!&nbsp; When you deploy..." />
    <meta name="twitter:image" content="/assets/images/2018/01/appregistration_thumb.png" />
    
categories:
  - Uncategorized
---


When you deploy an Azure Active Directory application that was working great locally you may get the following error when logging in:&nbsp; AADSTS50011: The reply address &#8216;http://<yourwebapp>.azurewebsites.net/signin-oidc&#8217; does not match the reply addresses configured for the application: &#8216;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#8217;. More details: not specified

This error would be specific to Azure App Services authentication (Easy Auth)

AADSTS50011: The reply address &#8216;https://<yourwebapp>/.auth/login/aad/callback&#8217; does not match the reply addresses configured for the application: &#8216;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#8217;. More details: not specified&nbsp; 

## How to fix this

This error says it all!&nbsp; When you deploy your Active Directory Web app to Azure you need to ensure you add this URL to the Azure Active Directory application (or have someone with the permissions to manage you application in AD to this for you).

Go to the Azure portal: [https://portal.azure.com](https://portal.azure.com "https://portal.azure.com") sign in and click on the Azure Active Directory icon on the left. Then click on the ‘App registrations’ icon in the middle pane.&nbsp; In the search box enter the application from the error message and choose ‘All apps’ from the dropdown:

&nbsp;[<img loading="lazy" title="appregistration" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="appregistration" src="/assets/images/2018/01/appregistration_thumb.png" width="952" height="506" />](/assets/images/2018/01/appregistration.png)

Click on your application, then the Settings icon, select the ‘Reply URLs’ from the list.&nbsp; Paste in the name of the reply URL from the error message you had and ‘Save’:

[<img loading="lazy" title="capture20180130145337489" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180130145337489" src="/assets/images/2018/01/capture20180130145337489_thumb.png" width="1002" height="220" />](/assets/images/2018/01/capture20180130145337489.png)

Now you should be able to login with out that error message!

## Conclusion

Just a quick blog but I hope it saves you some time!