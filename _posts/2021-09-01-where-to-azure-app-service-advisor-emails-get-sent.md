---
id: 5746
title: Where to Azure App Service Advisor Emails get sent?
date: 2021-09-01T08:04:13-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5746
permalink: /2021/09/01/where-to-azure-app-service-advisor-emails-get-sent/
categories:
  - Uncategorized
---
 

Azure App Service Advisor will send notification emails and add notifications to the portal when your app is not healthy.&nbsp; Where does the email notification system retrieve a list of recipients?

## Answer

The system will send email to the RBAC Owner of the resource, Service Admin and Account Admin of the Subscription.

You can find the RBAC Owners in the Access control section of your application:

[<img loading="lazy" width="543" height="265" title="serviceadmin" style="display: inline; background-image: none;" alt="serviceadmin" src="http://jsandersblog.azurewebsites.net/wp-content/uploads/2021/09/serviceadmin_thumb.jpg" border="0" />](http://jsandersblog.azurewebsites.net/wp-content/uploads/2021/09/serviceadmin.jpg)



You can find the Subscription Service Admin and Account Admin in the Subscription/Properties in the portal:

[<img loading="lazy" width="824" height="417" title="serviceadmin" style="display: inline; background-image: none;" alt="serviceadmin" src="http://jsandersblog.azurewebsites.net/wp-content/uploads/2021/09/serviceadmin_thumb-1.jpg" border="0" />](http://jsandersblog.azurewebsites.net/wp-content/uploads/2021/09/serviceadmin-1.jpg)



## Additional information

The source of these emails is not configurable other than these locations.&nbsp; You can change the Service Admin of the subscriptions and you can adjust the RBAC owner of your resource (it may make sense to do it at the resource group level for you) however.&nbsp; You are not able to disable this functionality.

Overview of this feature: [https://azure.microsoft.com/en-us/resources/videos/azure-app-service-advisor/](https://azure.microsoft.com/en-us/resources/videos/azure-app-service-advisor/ "https://azure.microsoft.com/en-us/resources/videos/azure-app-service-advisor/")