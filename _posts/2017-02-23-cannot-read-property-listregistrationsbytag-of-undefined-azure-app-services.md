Calling Register or RegisterAsync in the client code can result in a 400 status code coming back with an inner exception of: &#8216;Cannot read property &#8216;listRegistrationsByTag&#8217; of undefined&#8217; 


## Problem:
You are creating a Mobile App or Azure App Services and setting up the push notifications for the first time 

## Cause:

The Portal blade does not set the Application Setting MS_NotificationHubName 

## Workaround:

Add MS\_NotificationHubName in the Application settings.&nbsp; The name will be the name of your Notification Hub.&nbsp; It is the last item after the \ in the setting MS\_NotificationHubId or you can get in from the notification Hub blade: 

[<img loading="lazy" title="capture20170223080119644" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170223080119644" src="/assets/images/2017/02/capture20170223080119644_thumb.png" width="815" height="386" />](/assets/images/2017/02/capture20170223080119644.png) 

&nbsp; 

[<img loading="lazy" title="capture20170223080212770" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170223080212770" src="/assets/images/2017/02/capture20170223080212770_thumb.png" width="753" height="379" />](/assets/images/2017/02/capture20170223080212770.png)

## More information:

Once this is fixed the Portal Blade will set the MS_NotificationHubName for you when you walk through the Portal setup of Push notifications.&nbsp; At that time I will update this Blog!&nbsp; If you need further help, you can certainly open a support case through the Azure Portal.