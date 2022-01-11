If you want to deny HTTP methods or verbs in Azure Web Apps you can do this be changing your web.config file.

Add the following or create the following sections if they do not exist in your <configuration> section of your Azure Web App, web.config file:

<system.webServer>  
&nbsp;&nbsp;&nbsp; <validation validateIntegratedModeConfiguration=&#8221;false&#8221; />  
&nbsp;&nbsp;&nbsp; <modules runAllManagedModulesForAllRequests=&#8221;true&#8221; />  
&nbsp;&nbsp;&nbsp; <handlers>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add name=&#8221;DenyOTH&#8221; verb=&#8221;OPTIONS,TRACE,HEAD&#8221; path=&#8221;*&#8221; type=&#8221;System.Web.HttpMethodNotAllowedHandler&#8221; />  
</handlers>  
</system.webServer> 

&nbsp;

Once you add this, the response to any HTTP Verb in the verb list (in this case &#8220;OPTIONS,TRACE,HEAD&#8221;) will result in a response: 405 Method Not Allowed.

&nbsp;

Let me know if this helped you out!

Also, see this blog post for removing headers: [Remove ‘Server’ and ‘X-Powered-By’ headers from your Azure Mobile Apps](https://blogs.msdn.microsoft.com/jpsanders/2015/10/07/remove-server-and-x-powered-by-headers-from-your-azure-mobile-apps/)