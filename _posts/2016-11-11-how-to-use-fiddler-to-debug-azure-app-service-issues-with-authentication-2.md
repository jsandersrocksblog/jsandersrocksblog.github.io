Sometimes it is difficult to isolate Azure App Service issues to determine is the problem is the client or server.&nbsp; You can remove the client easily using a tool like Fiddler or Postman however is you are using authentication there are some tricks you need to use.&nbsp; I will demonstrate this with Azure Mobile Apps, but this will work with any Azure App Service using authentication.

### Step 1 – Ensure authentication is set up correctly

This is easy to test:&nbsp; Simply try to hit the /.auth/login/<provider> endpoint of your Azure App Service and see if this succeeds.

For example:&nbsp; https://jsandersrockstest.azurewebsites.net/.auth/login/facebook to test if my facebook provider has been set up correctly.

[<img loading="lazy" title="capture20161110105813225" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20161110105813225" src="/assets/images/2016/11/capture20161110105813225_thumb.png" width="917" height="301" />](/assets/images/2016/11/capture20161110105813225.png)

If there is an issue, you cannot proceed.&nbsp; If you DO get an error, this method of using the /.auth/login/<provider> in the browser will tell you what the problem is, for examples:

URL Blocked: This redirect failed because the redirect URI is not whitelisted in the app’s Client OAuth Settings. Make sure Client and Web OAuth Login are on and add all your app domains as Valid OAuth Redirect URIs. 

Can&#8217;t Load URL: The domain of this URL isn&#8217;t included in the app&#8217;s domains. To be able to load this URL, add all domains and subdomains of your app to the App Domains field in your app settings. 

Fix these issues then proceed. 

### Step 2 – Get the x-zumo-auth token

This is the authentication token from Step 1.&nbsp; It is actually part of the return URI in the address bar (starts at #token).&nbsp; What I do is use Fiddler Text Wizard to help grab this.

Copy the entire address bar from the browser (you can use <ctrl><a> <ctrl><c>) open Fiddler, stop capturing (click on the bottom left corner of Fiddler) and go to Tools, Text Wizard.&nbsp; As you see below the wizard will automatically to a URL Decode transform and you can see the JSON of the token.&nbsp; What we want is the highlighted portion you see below which is the value of the “authenticationToken”.&nbsp; Do NOT grab the enclosing quotes.&nbsp; This will be the value we use for the x-zumo-auth token.

&nbsp;

[<img loading="lazy" title="capture20161110113903465" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20161110113903465" src="/assets/images/2016/11/capture20161110113903465_thumb.png" width="856" height="532" />](/assets/images/2016/11/capture20161110113903465.png)

Handy tip:&nbsp; To see the JWT contents use the Text Wizard to perform a ‘From Base64’ transform or you can use a tool like [https://jwt.io/](https://jwt.io/ "https://jwt.io/") to troubleshoot, verify and decode the token, see the claims, verify the iss, aud and contents of this token.

### Step 3 – Use the x-zumo-auth token to authenticate a request

&nbsp;

Fiddler and Postman have the ability to construct a request.&nbsp; I will use the Fiddler Composer tab and make an authenticated request to my Azure Mobile Apps backend.

Open the composer tab in Fiddler and create an HTTPS request to the endpoint.&nbsp; In my case I am going after the /tables/todoitem endpoint.&nbsp; I add the x-zumo-auth from the previous step to the headers section and since this is an Azure Mobile App I need to also add the zumo-api-version: 2.0.0 header.&nbsp; If you do not specify the zumo-api-version you will get a response and the body will tell you that you need to add this!

&nbsp;

[<img loading="lazy" title="capture20161110114732831" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20161110114732831" src="/assets/images/2016/11/capture20161110114732831_thumb.png" width="619" height="406" />](/assets/images/2016/11/capture20161110114732831.png)

Now the request is authenticated and you can test your backend without your client!

&nbsp;

If you found this post useful, please drop me a note and let me know!

&nbsp;

### References

<a title="https://azure.microsoft.com/en-us/documentation/articles/app-service-authentication-overview/" href="https://azure.microsoft.com/en-us/documentation/articles/app-service-authentication-overview/" target="_blank">Authentication and authorization in Azure App Service</a>

<a title="https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-client-and-server-versioning/" href="https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-client-and-server-versioning/" target="_blank">Client and server versioning in Mobile Apps and Mobile Services (zumo-api-version)</a>

[https://jwt.io/](https://jwt.io/ "https://jwt.io/") to troubleshoot, verify and decode the token