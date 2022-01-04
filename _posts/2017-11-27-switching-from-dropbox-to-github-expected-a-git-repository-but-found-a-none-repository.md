---
id: 3855
title: 'Switching from dropbox to github&#8211;Expected a &#039;Git&#039; repository but found a &#039;None&#039; repository'
date: 2017-11-27T15:29:20-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=3855
permalink: /2017/11/27/switching-from-dropbox-to-github-expected-a-git-repository-but-found-a-none-repository/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Switching from dropbox to github&ndash;Expected a &#8216;Git&#8217; repository but found a &#8216;None&#8217; repository" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/27/switching-from-dropbox-to-github-expected-a-git-repository-but-found-a-none-repository/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview If you have dropbox selected for a deployment option and want to switch to github you may get the error message:&nbsp; Expected a &#039;Git&#039; repository but found a &#039;None&#039; repository at path &#039;D:homesitewwwroot&#039;. Fix To switch to Github you need to remove the Application Setting (in Application Settings of the Azure portal)&nbsp; SCM_NO_REPOSITORY.&nbsp; Click..." />
    <meta property="og:image" content="/assets/images/2017/11/capture20171127152623687_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Switching from dropbox to github&ndash;Expected a &#8216;Git&#8217; repository but found a &#8216;None&#8217; repository" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/11/27/switching-from-dropbox-to-github-expected-a-git-repository-but-found-a-none-repository/" />
    <meta name="twitter:description" content="Overview If you have dropbox selected for a deployment option and want to switch to github you may get the error message:&nbsp; Expected a &#039;Git&#039; repository but found a &#039;None&#039; repository at path &#039;D:homesitewwwroot&#039;. Fix To switch to Github you need to remove the Application Setting (in Application Settings of the Azure portal)&nbsp; SCM_NO_REPOSITORY.&nbsp; Click..." />
    <meta name="twitter:image" content="/assets/images/2017/11/capture20171127152623687_thumb.png" />
    
categories:
  - Uncategorized
---


If you have dropbox selected for a deployment option and want to switch to github you may get the error message:&nbsp; Expected a &#8216;Git&#8217; repository but found a &#8216;None&#8217; repository at path &#8216;D:\\home\\site\\wwwroot&#8217;.

## 

## Fix

To switch to Github you need to remove the Application Setting (in Application Settings of the Azure portal)&nbsp; SCM\_NO\_REPOSITORY.&nbsp; Click on the ‘…’ of that setting and choose ‘Delete’

[<img loading="lazy" title="capture20171127152623687" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171127152623687" src="/assets/images/2017/11/capture20171127152623687_thumb.png" width="895" height="97" />](/assets/images/2017/11/capture20171127152623687.png)

Ref: [https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository](https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository "https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository")&nbsp; &#8211; search on Dropbox