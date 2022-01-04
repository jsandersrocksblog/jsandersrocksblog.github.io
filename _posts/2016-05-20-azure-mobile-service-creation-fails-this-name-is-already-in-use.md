---
id: 1435
title: 'Azure Mobile Service Creation fails &#034;this name is already in use&#034;'
date: 2016-05-20T19:40:12-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1435
permalink: /2016/05/20/azure-mobile-service-creation-fails-this-name-is-already-in-use/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="" />
    <meta property="og:url" content="" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:url" content="" />
    <meta name="twitter:description" content="" />
    
categories:
  - Uncategorized
---
Just a quick blog on this…

## Problem

You cannot create an Azure Mobile Service.&nbsp; You enter a unique name when creating the Mobile Service but get an error:&nbsp; &#8220;this name is already in use&#8221; and a red exclamation mark.

&nbsp;

## Reason

Mobile Services are deprecated, that is why you cannot create one. Please see this article: <https://azure.microsoft.com/en-us/blog/transition-of-azure-mobile-services/> 

&nbsp; 

## Solution

You must create a Mobile App instead in <https://portal.azure.com>. Here is a quick start for you to follow: <https://azure.microsoft.com/en-us/documentation/learning-paths/appservice-mobileapps/> 

and 

<https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-windows-store-dotnet-get-started/> 

&nbsp;

No the error is not intuitive and we are getting that fixed!