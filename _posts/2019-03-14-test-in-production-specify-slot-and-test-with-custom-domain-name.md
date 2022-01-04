---
id: 5402
title: 'Test In Production: Specify slot and test with Custom Domain Name'
date: 2019-03-14T10:08:51-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5402
permalink: /2019/03/14/test-in-production-specify-slot-and-test-with-custom-domain-name/
categories:
  - Uncategorized
---
You can use Deployment Slots and direct a percentage of the production traffic to a particular slot.&nbsp; If you want to test only that slot say with the custom Domain on the production slot and ensure you hit that slot, you need to add a Cookie called <font style="background-color: rgb(255, 255, 0);">x-ms-routing-name</font> and specify that slot I want to route to.&nbsp; In this example I am going to route to the <font style="background-color: rgb(255, 255, 0);">test</font> slot:

Accept-Encoding: gzip, deflate, br  
&nbsp; Accept-Language: en-US,en;q=0.9  
&nbsp; <font style="background-color: rgb(255, 255, 0);">Cookie: x-ms-routing-name=test</font>

There a few tools you can use to do this but <a href="https://www.telerik.com/fiddler" target="_blank">Fiddler</a> is one of my favorite.&nbsp; To do this you can modify the rules in fiddler and look for the domain of concern, and when found… add that cookie.&nbsp; 

### To Modify the Rules

1. go to the Rules, Customize Rules section (ctrl+R).

2. In the editor find the section: function OnBeforeRequest(oSession: Session) 

3. Add a rule similar to this where the uri is your site <font style="background-color: rgb(255, 255, 0);">domain</font> name and the cookie is the <font style="background-color: rgb(255, 255, 0);">slot name</font> you are wanting to redirect to.

//Rule: add cookie for URLs containing &#8220;mytestsite.com&#8221;  
if (oSession.uriContains(&#8220;<font style="background-color: rgb(255, 255, 0);">mytestsite.com</font>&#8220;) ) {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; oSession.oRequest[&#8220;Cookie&#8221;] = (oSession.oRequest[&#8220;Cookie&#8221;] + &#8220;;x-ms-routing-name=<font style="background-color: rgb(255, 255, 0);">test</font>&#8220;);  
}

Then run Fiddler and test your slot!



### Some other important things

1.&nbsp; Ensure you are running fiddler and capturing traffic (F12).

2. If the requests include HTTPS traffic ensure you are decrypting HTTPS traffic (Tools, Options, HTTPS, check Decrypt HTTPS traffic):

[<img loading="lazy" width="454" height="308" title="DecryptHTTPS 2019-03-14 110222" style="display: inline; background-image: none;" alt="DecryptHTTPS 2019-03-14 110222" src="/assets/images/2019/03/DecryptHTTPS-2019-03-14-110222_thumb-2.jpg" border="0" />](/assets/images/2019/03/DecryptHTTPS-2019-03-14-110222-2.jpg)

3. Close all browsers and then use an in-private or incognito browser session to ensure you are not getting cached content.