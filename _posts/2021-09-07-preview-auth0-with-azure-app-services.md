There are a couple of articles available but they are out of date.&nbsp; This is a step by step walk through of using OpenID (Auth0) with Azure App Services.

## Create App Service

The first step is to create an Azure App Service.&nbsp; Using the <a href="https://portal.azure.com" target="_blank" rel="noopener">Azure Portal</a>, I created a .NET Core 5 Web app from the portal with these parameters:

[<img loading="lazy" width="611" height="654" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb.png" border="0" />](/assets/images/2021/09/image.png)

Review and create this Web App and copy the name (in this case it is: jsandersdemo).

### Checklist

In this section you should have copied the: Web App name



## Create app Registration with Auth0

You may have to create an account if you do not have one already.&nbsp; It is free for your personal research.

Log in to <a href="https://auth0.com/" target="_blank" rel="noopener">Auth0.com</a>&nbsp;

Click on Applications

[<img loading="lazy" width="244" height="179" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-1.png" border="0" />](/assets/images/2021/09/image-1.png)

Click on + Create Application

[<img loading="lazy" width="927" height="177" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-2.png" border="0" />](/assets/images/2021/09/image-2.png)

Give you application a name, choose Regular Web Applications and click create

[<img loading="lazy" width="577" height="515" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-3.png" border="0" />](/assets/images/2021/09/image-3.png)



Once it is created click on the Settings tab and copy the Client ID and Client Secret for use later in the Web App configuration ( you can click on the blue icon to the right of the fields)

[<img loading="lazy" width="551" height="339" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-4.png" border="0" />](/assets/images/2021/09/image-4.png)

Next you will use the saved application name from the Web App you created in order to populate three fields:

Application Login URI : https://<<webappname>>.azurewebsites.net/.auth/login/auth0

Allowed Callback URLs: https://<<webappname>>.azurewebsites.net/.auth/login/auth0/callback

Allowed Logout URLs: https://<<webappname>>.azurewebsites.net/.auth/logout

Replacing <<webappname>> with the name of your app.&nbsp; In my case below, the web app name is jsandersdemo:

[<img loading="lazy" width="549" height="333" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-5.png" border="0" />](/assets/images/2021/09/image-5.png)

Scroll to the bottom and click ‘Save Changes’

[<img loading="lazy" width="244" height="128" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-6.png" border="0" />](/assets/images/2021/09/image-6.png)

Move to the right and hit the down arrow icon for ‘Advance Settings’ and copy the OpenID Configuration value for use in the Web App configuration in the next section:

[<img loading="lazy" width="628" height="402" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-7.png" border="0" />](/assets/images/2021/09/image-7.png)

### Checklist

In this section you should have copied: OpenID Configuration, Client ID and Client Secret 

## Configure the Web App Authentication Settings

Open <a href="https://resources.azure.com" target="_blank" rel="noopener">Azure Resource Explorer</a> and find your Web App from the first section (note it can take a while to populate your subscriptions and be ready)

[<img loading="lazy" width="690" height="298" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-8.png" border="0" />](/assets/images/2021/09/image-8.png)



Click on your app (Microsoft.Web/sites) and navigate to the ‘config\authsettingsV2’ node

[<img loading="lazy" width="664" height="240" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-9.png" border="0" />](/assets/images/2021/09/image-9.png)

Ensure at the top of the page you have highlighted (click on it) the ‘Read/Write’ button if it is not blue, and click on Edit.&nbsp; We will add the following inside the “properties” field:

&#8220;platform&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;enabled&#8221;: true,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;runtimeVersion&#8221;: &#8220;~1&#8221;,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;configFilePath&#8221;: &#8220;auth.json&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;globalValidation&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;requireAuthentication&#8221;: true,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;unauthenticatedClientAction&#8221;: &#8220;RedirectToLoginPage&#8221;  
} 

[<img loading="lazy" width="908" height="162" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-10.png" border="0" />](/assets/images/2021/09/image-10.png)



And click ‘PUT’

[<img loading="lazy" width="494" height="437" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-11.png" border="0" />](/assets/images/2021/09/image-11.png)

Doing this will populate some additional information.&nbsp; Just close this page now.

Go to the Kudu Site for your Web App by clicking ‘’Go” in the Advanced Tools section of you Web App portal view

[<img loading="lazy" width="380" height="266" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-12.png" border="0" />](/assets/images/2021/09/image-12.png)

Choose ‘Debug Console’ then ‘CMD’ from the dropdown and navigate to the \home\site\wwwroot directory.&nbsp; Then create a file called auth.json by using the touch command as pictured below

[<img loading="lazy" width="493" height="628" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-13.png" border="0" />](/assets/images/2021/09/image-13.png)

Click on the pencil icon of ‘auth.json’ to edit it

[<img loading="lazy" width="244" height="148" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-14.png" border="0" />](/assets/images/2021/09/image-14.png)

{  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;globalValidation&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;requireAuthentication&#8221;: true,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;unauthenticatedClientAction&#8221;: &#8220;RedirectToLoginPage&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;identityProviders&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;openIdConnectProviders&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;auth0&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;enabled&#8221;: true,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;registration&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientId&#8221;: &#8220;<<CLIENTIDFROMAUTH0>>&#8221;,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientCredential&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientSecretSettingName&#8221;: &#8220;OPEN\_ID\_SECRET&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;openIdConnectConfiguration&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;wellKnownOpenIdConfiguration&#8221;: &#8220;<<OPENIDWELLKNOWN>>&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;login&#8221;: {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;nameClaimType&#8221;: &#8220;name&#8221;,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;scopes&#8221;: [  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;openid&#8221;,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;profile&#8221;,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;email&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp; }

Use the above content for your auth.json file but replace the <font style="background-color: rgb(255, 255, 0);"><<CLIENTIDFROMAUTH0>> and&nbsp; <font style="background-color: rgb(255, 255, 0);"><<OPENIDWELLKNOWN>></font></font> placeholders with the values you copied from your Auth0 app.&nbsp; Example:

[<img loading="lazy" width="749" height="419" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-15.png" border="0" />](/assets/images/2021/09/image-15.png)

now click the ‘Save’ button

Go back to the portal and go to the ‘Configuration’ section, choose ‘+ New application setting’ give it the name ‘OPEN\_ID\_CONFIG’ (matching the value in “clientSecretSettingName” from above) and hit the ‘OK’ button

[<img loading="lazy" width="976" height="267" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-16.png" border="0" />](/assets/images/2021/09/image-16.png)

Hit the ‘Save’ icon at the top, then ‘Continue’ and you are ready to test your application

[<img loading="lazy" width="387" height="218" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-17.png" border="0" />](/assets/images/2021/09/image-17.png)

Test your app in a incognito or private windows in the event you are logged in already



[<img loading="lazy" width="296" height="465" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-18.png" border="0" />](/assets/images/2021/09/image-18.png)

## 



## References:

[https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-file-based](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-file-based "https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-file-based")

[https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-openid-connect](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-openid-connect "https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-openid-connect")