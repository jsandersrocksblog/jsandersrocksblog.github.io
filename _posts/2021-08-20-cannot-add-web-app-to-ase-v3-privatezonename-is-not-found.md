---
id: 5740
title: 'Cannot Add Web App to ASE V3&ndash; privateZoneName is not found'
date: 2021-08-20T13:13:15-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5740
permalink: /2021/08/20/cannot-add-web-app-to-ase-v3-privatezonename-is-not-found/
categories:
  - Uncategorized
---
 

I’m a dork so… quick blog here for those of you that fall into this too.&nbsp; I created a new Azure App Service Environment (ASE) V3 and tried to add an App Service Plan and Web App to it and go the error “The template parameter ‘privateZoneName’ is not found”



## Root Cause

The ASE V3 without the dedicated host does not use the Isolated SKU like ASE V2 does so I was selecting the wrong thing.&nbsp; Instead, create your Web App as normal however with selecting the “Region” don’t use something like “East US” put use your ASE you created for the Region.



[<img loading="lazy" width="653" height="596" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/08/image_thumb.png" border="0" />](/assets/images/2021/08/image.png)