
You can add Push Notification Hubs to your Azure Web App, Azure Api App etc… (all Azure App Services).&nbsp; If you try to use the portal to add Push (a Notification Hub) to a Slot however this will fail.&nbsp; You will see the portal will just sit there with the message: “Connecting Web App to Notification Hub” forever.

[<img loading="lazy" title="capture20170330144721190" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170330144721190" src="/assets/images/2017/03/capture20170330144721190_thumb.png" width="508" height="252" />](/assets/images/2017/03/capture20170330144721190.png)

## 

## Fix

The Push Notification Hub settings from the main site are inherited by the slots.&nbsp; You cannot define a unique Push setting for the slots.&nbsp; If you need different settings for testing for example, you need to simply create a new App Service and deploy to that.

## More info

Drop me a note if you found this useful!