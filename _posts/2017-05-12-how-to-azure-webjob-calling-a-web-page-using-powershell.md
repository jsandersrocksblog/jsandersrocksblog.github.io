---
id: 2376
title: 'How To: Azure WebJob calling a Web Page using Powershell'
date: 2017-05-12T16:03:47-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2376
permalink: /2017/05/12/how-to-azure-webjob-calling-a-web-page-using-powershell/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How To: Azure WebJob calling a Web Page using Powershell" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/12/how-to-azure-webjob-calling-a-web-page-using-powershell/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Just a quicky post to get you started on how to use CRON expressions and Powershell to call a web page from a WebJob.&nbsp; There are many different ways to use Azure WebJobs and this is using a Powershell script to call an endpoint and scheduling this using CRON. Steps Create a Powershell script..." />
    <meta property="og:image" content="/assets/images/2017/05/snip_20170512102547_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How To: Azure WebJob calling a Web Page using Powershell" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/12/how-to-azure-webjob-calling-a-web-page-using-powershell/" />
    <meta name="twitter:description" content="Overview Just a quicky post to get you started on how to use CRON expressions and Powershell to call a web page from a WebJob.&nbsp; There are many different ways to use Azure WebJobs and this is using a Powershell script to call an endpoint and scheduling this using CRON. Steps Create a Powershell script..." />
    <meta name="twitter:image" content="/assets/images/2017/05/snip_20170512102547_thumb.png" />
    
categories:
  - Uncategorized
---


Just a quicky post to get you started on how to use CRON expressions and Powershell to call a web page from a WebJob.&nbsp; There are many different ways to use Azure WebJobs and this is using a Powershell script to call an endpoint and scheduling this using CRON.

## Steps

### 

### Create a Powershell script file that does what you want and test it locally

Start by using the Powershell ISE to develop your script.&nbsp; It is easier to debug and you can be assured of the results of running your script.&nbsp; Ref: <a title="https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/ise/introducing-the-windows-powershell-ise" href="https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/ise/introducing-the-windows-powershell-ise" target="_blank">Introducing the Windows PowerShell ISE</a>

Here is a super simple script that simply calls an HTTP endpoint.&nbsp; This endpoint in turn will do some processing for me.&nbsp; I don’t care about the return value, just if it is successfully called or not (which the WebJob logs will show) but you could extend this to get a return value and do something else with that return value.&nbsp; In general, WebJobs are designed to just execute and either succeed or fail so this works well.&nbsp; In this case you can see the call returned the HTTP Status 200 indicating success:

[<img loading="lazy" title="snip_20170512102547" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512102547" src="/assets/images/2017/05/snip_20170512102547_thumb.png" width="926" height="749" />](/assets/images/2017/05/snip_20170512102547.png)

You can see that I tested it here in the ISE.&nbsp; I saved the file in my Documents directory with the name: CallWebPage.ps1

More info:&nbsp; You can do more powerful things with Invoke-WebRequest and this documentation will help you out: <a title="https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest" href="https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest" target="_blank">Invoke-WebRequest</a> .&nbsp; Here is a more complete sample:

$ProgressPreference=&#8221;SilentlyContinue&#8221;  
try {  
&nbsp;&nbsp;&nbsp; $Res = Invoke-WebRequest <http://classicASPvbscript.azurewebsites.net>&nbsp; -UseBasicParsing  
&nbsp;&nbsp;&nbsp; $Res.StatusCode  
&nbsp;&nbsp;&nbsp;  
&nbsp;&nbsp;&nbsp; }  
catch {  
&nbsp;&nbsp;&nbsp; $ErrorMessage = $_.Exception.Message  
&nbsp;&nbsp;&nbsp; $ErrorMessage  
&nbsp;&nbsp;&nbsp; Exit 1  
&nbsp;&nbsp;&nbsp; }

&nbsp;

### Upload the working file as a WebJob using the Azure Portal

Now that I verified this file does what I want, I can create a WebJob to host it!&nbsp; You do not want to call the target site in a WebJob hosted on that same site (for various reasons) unless this is not called frequently and no other calls are coming to the target site.&nbsp; This is not efficient (just put the code in the WebJob by golly) and could create more traffic to the target site.&nbsp; I am creating an Azure Web App just to call the WebJob and putting it in a basic plan so I can enable Always On.&nbsp; I enable Always On (Set in App Settings) because I want to use a CRON expression and this is a requirement (see <a title="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/#.WRWzNsLruUl" href="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/" target="_blank">http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/</a> ).

Next, go to the app in the portal and create a WebJob by choosing Add: 

[<img loading="lazy" title="snip_20170512113118" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512113118" src="/assets/images/2017/05/snip_20170512113118_thumb.png" width="399" height="274" />](/assets/images/2017/05/snip_20170512113118.png)

Give it a name, upload you powershell script file, change the type to Triggered and set the Triggers to Scheduled:

[<img loading="lazy" title="snip_20170512113255" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512113255" src="/assets/images/2017/05/snip_20170512113255_thumb.png" width="334" height="508" />](/assets/images/2017/05/snip_20170512113255.png)

Finally, define the CRON expression to kick off this job when ever you want this to execute.&nbsp; CRON expressions trip everyone up.&nbsp; First CRON is based on the Server Time Zone which is UTC and so if you want to run at 10:50 AM My time zone, you may get confused.&nbsp; Second, although standard, many of us mere mortals don’t know how to translate them.

**First:&nbsp; UTC issue.**&nbsp; I find it easiest to go to the Kudo console of the app and see what time it is now (which by default is UTC).&nbsp; To go to Kudu you can find this in the portal it is in Advanced Tools and hit the go link (I just type Kudu in search):

[<img loading="lazy" title="snip_20170512113906" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512113906" src="/assets/images/2017/05/snip_20170512113906_thumb.png" width="353" height="231" />](/assets/images/2017/05/snip_20170512113906.png)

Then go to the&nbsp; Debug console, CMD menu and select it:

[<img loading="lazy" title="snip_20170512114001" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114001" src="/assets/images/2017/05/snip_20170512114001_thumb.png" width="429" height="218" />](/assets/images/2017/05/snip_20170512114001.png)

Then type:&nbsp; _time_&nbsp; in the command window.&nbsp; Since I am testing this I will set my CRON expression to 15:00 just a few minutes from now.

[<img loading="lazy" title="snip_20170512113820" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512113820" src="/assets/images/2017/05/snip_20170512113820_thumb.png" width="508" height="248" />](/assets/images/2017/05/snip_20170512113820.png)

**Second: The Expression issue.&nbsp;** The simplest CRON expression is based on a 6 position pattern of _sec min hour \* \* *_ which will kick off the job at the specified time each day.&nbsp; Here are a couple of references to help you with:&nbsp; <a title="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/#.WRWzNsLruUl" href="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/" target="_blank">http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/</a>&nbsp; (See CRON Expressions).&nbsp; You can find some more cron expression samples <a href="https://code.google.com/p/ncrontab/wiki/CrontabExamples" target="_blank">here</a> but note that they have 5 fields, to use them you should add a `` as the first field (for the seconds).

Looking back at the reference the syntax will be: 0 0 15 \* \* *

[<img loading="lazy" title="snip_20170512114
128" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114128" src="/assets/images/2017/05/snip_20170512114128_thumb.png" width="309" height="445" />](/assets/images/2017/05/snip_20170512114128.png)

Once I hit OK it takes some time for the Job to show up in the Portal.&nbsp; Give it about 30 seconds and hit the Refresh Icon to see the Job:

[<img loading="lazy" title="snip_20170512114200" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114200" src="/assets/images/2017/05/snip_20170512114200_thumb.png" width="728" height="200" />](/assets/images/2017/05/snip_20170512114200.png)

Finally hit the Logs icon and wait for the Job to succeed:

[<img loading="lazy" title="snip_20170512114305" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114305" src="/assets/images/2017/05/snip_20170512114305_thumb.png" width="645" height="314" />](/assets/images/2017/05/snip_20170512114305.png)

### 

### Modify the CRON expression (optional)

If you wish to change the CRON expression you can delete and recreate the WebJob.&nbsp; I found a better way to do this is to edit the Settings File using the App Service Editor however.

Bring up the App Service Editor from the portal (hit the Go link):

[<img loading="lazy" title="snip_20170512114504" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114504" src="/assets/images/2017/05/snip_20170512114504_thumb.png" width="664" height="328" />](/assets/images/2017/05/snip_20170512114504.png)

Navigate to your triggered web job (will be WWWROOT\App_Data\jobs\triggered\<Name of your WebJob here> ) and clicking on the settings.job file:

[<img loading="lazy" title="snip_20170512114510" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114510" src="/assets/images/2017/05/snip_20170512114510_thumb.png" width="653" height="331" />](/assets/images/2017/05/snip_20170512114510.png)

Edit the CRON expression in the _schedule_ item of the json text.&nbsp; In this case I am changing it to quarter past 3PM UTC):

[<img loading="lazy" title="snip_20170512114517" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114517" src="/assets/images/2017/05/snip_20170512114517_thumb.png" width="663" height="312" />](/assets/images/2017/05/snip_20170512114517.png)

The change will be automatically saved and will run at that time:

[<img loading="lazy" title="snip_20170512114523" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170512114523" src="/assets/images/2017/05/snip_20170512114523_thumb.png" width="608" height="366" />](/assets/images/2017/05/snip_20170512114523.png)

&nbsp;

## 

## Conclusion

This is just a quick start for you to follow.&nbsp; Obviously you can do much more with Scheduled jobs and other options are Triggered WebJobs and Function Apps.

If you did find this helpful, please drop me a note!

## 

## References

<a title="http://blog.amitapple.com/post/74215124623/deploy-azure-webjobs/" href="http://blog.amitapple.com/post/74215124623/deploy-azure-webjobs/" target="_blank">http://blog.amitapple.com/post/74215124623/deploy-azure-webjobs/</a>

<a title="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/" href="http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/" target="_blank">http://blog.amitapple.com/post/2015/06/scheduling-azure-webjobs/</a>

<a title="https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/ise/introducing-the-windows-powershell-ise" href="https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/ise/introducing-the-windows-powershell-ise" target="_blank">https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/ise/introducing-the-windows-powershell-ise</a>

<a title="https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest" href="https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest" target="_blank">https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest</a>

<a title="https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-create-web-jobs" href="https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-create-web-jobs" target="_blank">https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-create-web-jobs</a>

<a title="https://azure.microsoft.com/en-us/services/functions/" href="https://azure.microsoft.com/en-us/services/functions/" target="_blank">https://azure.microsoft.com/en-us/services/functions/</a>