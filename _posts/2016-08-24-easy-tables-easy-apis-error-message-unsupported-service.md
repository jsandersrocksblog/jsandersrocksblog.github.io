When you try to access or create Easy tables or Easy APIs in Azure App Services or Azure Mobile Apps you may get this error message in the portal: Unsupported service.

### Cause

Easy tables and Easy APIs are only available to an Azure Mobile App that has been created initially as an Azure Mobile App and with a Node.Js backend in the quckstart OR to an Azure Mobile App Quickstart.

### Fix

Create a new Azure Mobile App, choose quickstart and select Node.js when you are prompted for the backend OR choose Mobile Apps Quickstart and create your Easy Tables.  
[<img loading="lazy" width="1043" height="298" title="capture20160824100433414" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20160824100433414" src="/assets/images/2016/08/capture20160824100433414_thumb.png" border="0" />](/assets/images/2016/08/capture20160824100433414.png)

### FAQ:

**But I don’t want to create a new Azure Mobile App, what can I do? &#8211;** You can grab the necessary Node.js code from a quickstart you have created and then edit the code to add tables.  You can use _https://NAMEOFYOURAPP.scm.azurewebsites.net/dev_ to see and edit the table and api code (see below on how this works).  You can view you tables with your favorite database access tool.  
**How does the Easy Table/API functionality work if I don’t see them in the UI? –** The mobile app node.js packages look for certain files in the Tables and API directories (mytable.js and mytable.json for example).  It uses express middle ware and when it sees them they dynamically add then to the expressroute.  
**What if I need more help? &#8211;**  StackOverflow and MSDN forums are you first option, creating a support case is another.

## 

### More Info:

You can also not use easy tables/apis and manually define the routes and add your code:  
[https://shellmonger.com/30-days-of-azure-mobile-apps-the-table-of-contents/](https://shellmonger.com/30-days-of-azure-mobile-apps-the-table-of-contents/ "https://shellmonger.com/30-days-of-azure-mobile-apps-the-table-of-contents/")  
[https://shellmonger.com/2016/04/15/30-days-of-zumo-v2-azure-mobile-apps-day-8-table-controller-basics/](https://shellmonger.com/2016/04/15/30-days-of-zumo-v2-azure-mobile-apps-day-8-table-controller-basics/ "https://shellmonger.com/2016/04/15/30-days-of-zumo-v2-azure-mobile-apps-day-8-table-controller-basics/")  
[https://shellmonger.com/2016/05/13/30-days-of-zumo-v2-azure-mobile-apps-day-20-custom-api/](https://shellmonger.com/2016/05/13/30-days-of-zumo-v2-azure-mobile-apps-day-20-custom-api/ "https://shellmonger.com/2016/05/13/30-days-of-zumo-v2-azure-mobile-apps-day-20-custom-api/") (Version 2: The Node.js Custom API)