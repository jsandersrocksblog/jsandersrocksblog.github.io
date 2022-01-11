This is a step by step walkthrough of how to add AAD Authentication to Static Web Apps.&nbsp; This is based on these documents: 

[Quickstart: Building your first static web app with Azure Static Web Apps using the Azure portal | Microsoft Docs](https://docs.microsoft.com/en-us/azure/static-web-apps/get-started-portal?tabs=vanilla-javascript)



# 

# Steps

## Build the Static Web App 

## 

Using [Quickstart: Building your first static web app with Azure Static Web Apps using the Azure portal | Microsoft Docs](https://docs.microsoft.com/en-us/azure/static-web-apps/get-started-portal?tabs=vanilla-javascript) create a static web app using the ‘No Framework’ tab.

Create an account for github.com if you do not have one.&nbsp; You will need it below.

Right Click on the step in 1. – a. and open in a new tab (otherwise you navigate away from the sample page

[<img loading="lazy" width="693" height="297" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb.png" border="0" />](/assets/images/2021/07/image.png)



Per instuctions, name the repo (repository) **my-first-static-web-app** and make the repo public for simplicity**:**

[<img loading="lazy" width="541" height="360" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-1.png" border="0" />](/assets/images/2021/07/image-1.png)

Select **Create repository from template** on the github page and you repo is ready!

Leave the github repo open because we will need it later.

Create the Azure Static Web app by following the rest of the Quickstart, but ensure you do NOT choose free for the Hosting Plan.&nbsp; Instead choose Standard so we can use authentication (if you forget this step you can change it later):&nbsp; 

[<img loading="lazy" width="651" height="147" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-2.png" border="0" />](/assets/images/2021/07/image-2.png)

[Quickstart: Building your first static web app with Azure Static Web Apps using the Azure portal | Microsoft Docs](https://docs.microsoft.com/en-us/azure/static-web-apps/get-started-portal?tabs=vanilla-javascript#create-a-static-web-app)

Follow the rest of the instructions to create and attach your app to your GitHub repo you created above, and test the site!

Note in the GitHub phase you need to authorize Azure Static Web Apps to connect to your repo:

[<img loading="lazy" width="417" height="414" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-3.png" border="0" />](/assets/images/2021/07/image-3.png)

Visit the site to ensure it works by clicking on the URL of the newly created app:

Note that in this example, the site is not ready ‘We have not received any content…’&nbsp; and you need to wait for that activity to complete.

[<img loading="lazy" width="685" height="245" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-4.png" border="0" />](/assets/images/2021/07/image-4.png)

You can refresh the view and when that disappears click on the URL and you should see the site (it will just say Vanilla JavaScript App).

**Side note &#8211;**&nbsp; When you make a change to the Repo you can see the progress in the actions tab.&nbsp; This is updating your linked Static Web App.&nbsp; If you don’t see changes you have made, this ‘Actions’ tab is where to go!

[<img loading="lazy" width="854" height="231" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-5.png" border="0" />](/assets/images/2021/07/image-5.png)

<font style="background-color: rgb(255, 255, 0);">COPY the URL for use in the next step in my case it is: <a title="https://white-mushroom-02b8dcc0f.azurestaticapps.net/" href="https://white-mushroom-02b8dcc0f.azurestaticapps.net/">https://white-mushroom-02b8dcc0f.azurestaticapps.net/</a></font>



## Create an AAD Application

The next step is to create an app registration in AAD so open your Azure Active Directory in the Azure Portal [<img loading="lazy" width="63" height="63" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-6.png" border="0" />](/assets/images/2021/07/image-6.png)

Select ‘App registrations’ and ‘+ New registration’:

[<img loading="lazy" width="287" height="342" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-7.png" border="0" />](/assets/images/2021/07/image-7.png)

Give it a name and select this directory only and hit the ‘Register’ button:

[<img loading="lazy" width="293" height="358" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-8.png" border="0" />](/assets/images/2021/07/image-8.png)

Now in ‘Authentication’ choose ‘+Add a platform’ and choose ‘Web’

[<img loading="lazy" width="301" height="221" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-9.png" border="0" />](/assets/images/2021/07/image-9.png)

In this page we use the URL we copied for our web app above.&nbsp; Get that url and add /.auth/login/aad/callback to it.&nbsp; My Example: **https://white-mushroom-02b8dcc0f.azurestaticapps.net/.auth/login/aad/callback** 

Use this value as the Redirect URI.

Also ensure you check the box ‘ID tokens (used for implicit and hybrid flows)’ and hit the ‘Configure’ button:

[<img loading="lazy" width="450" height="479" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-10.png" border="0" />](/assets/images/2021/07/image-10.png)

Now we need to create a secret so click on ‘Certificates and secrets’ and ‘+New client secret’

[<img loading="lazy" width="452" height="262" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-11.png" border="0" />](/assets/images/2021/07/image-11.png)

Set the description and expiration to whatever you want (expiration is how long the secret is good for) and <font style="background-color: rgb(255, 255, 0);">copy the ‘Value’</font> once it is created.&nbsp; We will use this later in an Application Setting we will create called ‘AADSecret’

[<img loading="lazy" width="463" height="144" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-12.png" border="0" />](/assets/images/2021/07/image-12.png)

We also need to **copy the ‘Application (client) ID’ and the ‘Directory (tenant) ID’ from the ‘Overview’ tab**.&nbsp; We will use the ‘Application (client) ID’ for an Application Setting we will create called ‘AADClientID’ and we will use the Directory id in the configuration file we will create later:

[<img loading="lazy" width="468" height="161" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-13.png" border="0" />](/assets/images/2021/07/image-13.png)

At this point you should have copied three values for use in the next step so feel free to note them below:

AADSecret  
AADClientID  
Directory id 

**Side note:**&nbsp; Doing all this should have created the following in the ‘API permissions’ tab:

[<img loading="lazy" width="630" height="150" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-14.png" border="0" />](/assets/images/2021/07/image-14.png)

## 

## Configure your Static Web app

We need to add the configuration file to the Static Web App repo so the application knows to use authentication.

In your github repo add a file to the repo called ‘staticwebapp.config.json’.&nbsp; In the ‘ <> Code’ section choose ‘Add file’, ‘Create new file’:

[<img loading="lazy" width="704" height="132" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-15.png" border="0" />](/assets/images/2021/07/image-15.png)

Use the name ‘staticwebapp.config.json’.&nbsp; Then copy and modify the code below and paste it into the file.&nbsp; You need to replace <font style="background-color: rgb(255, 255, 0);">DirectoryIDHERE</font> with the value you copied above (Directory (tenant) ID’ from the ‘Overview’ tab):

<font face="Courier New">{<br />&nbsp;&nbsp;&nbsp;&nbsp; &#8220;routes&#8221;: [<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;route&#8221;: &#8220;/&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;allowedRoles&#8221;: [ &#8220;authenticated&#8221; ]<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp; ],<br />&nbsp;&nbsp;&nbsp;&nbsp; &#8220;responseOverrides&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;401&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;redirect&#8221;: &#8220;/.auth/login/aad&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;statusCode&#8221;: 302<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },<br />&nbsp;&nbsp;&nbsp;&nbsp; &#8220;auth&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;identityProviders&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;azureActiveDirectory&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;registration&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;openIdIssuer&#8221;: &#8220;https://login.microsoftonline.com/<font style="background-color: rgb(255, 255, 0);"><a><a href="https://login.microsoftonline.com/DirectoryIDHERE">DirectoryIDHERE</a>&#8220;</font>, <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientIdSettingName&#8221;: &#8220;AADClientID&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientSecretSettingName&#8221;: &#8220;AADSecret&#8221;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },&#8221;userDetailsClaim&#8221;: &#8220;http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name&#8221;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp; }<br /> </font></p> 

<p>
  <strong>Note:</strong>&nbsp; Ensure there are no spaces in these quoted values.&nbsp; If the configuration is invalid here (I had some spaces), this will result in at 403 error.
</p>

<p>
  And then ‘Commit new file’ at the bottom:
</p>

<p>
  <a href="/assets/images/2021/07/image-16.png"><img loading="lazy" width="312" height="463" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-16.png" border="0" /></a>
</p>

<p>
  This will commit the file and if you go to the ‘Actions’ tab you can see the progress of this updating your app.&nbsp;
</p>

<p>
  Before we move on, lets look at that config file you created.
</p>

<p>
  The ‘Route’ section is defining where to apply this configuration (authentication). This means that from the root of the website down, the only allowed access will be authenticated users:
</p>

<p>
  &#8220;route&#8221;: &#8220;/&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;allowedRoles&#8221;: [ &#8220;authenticated&#8221; ]
</p>

<p>
  The ‘responseOverrides’ section tells us if there is a 401 response (someone is not authorized) when accessing a page, redirect (302) to the page /.auth/login/aad.&nbsp; Remember when we set this in the App Registration?
</p>

<p>
  &nbsp;&nbsp; &#8220;responseOverrides&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;401&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;redirect&#8221;: &#8220;/.auth/login/aad&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;statusCode&#8221;: 302<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },
</p>

<p>
  The ‘auth’section tells the app what the identity provider is (azureActiveDirectory), who is Issuer (your tenant/directory), and what the client Id and secrets are.&nbsp; These last two are specified as the name of the setting we are going to add in the application configuration page in a moment (so we can change it easier like when the secret expires):
</p>

<p>
  &#8220;auth&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;identityProviders&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;azureActiveDirectory&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;registration&#8221;: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;openIdIssuer&#8221;: &#8220;https://login.microsoftonline.com/<font style="background-color: rgb(255, 255, 0);"><a><a href="https://login.microsoftonline.com/DirectoryIDHERE">DirectoryIDHERE</a>&#8220;</font>, <br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientIdSettingName&#8221;: &#8220;AADClientID&#8221;,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;clientSecretSettingName&#8221;: &#8220;AADSecret&#8221;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; },&#8221;userDetailsClaim&#8221;: &#8220;http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name&#8221;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }</p> 
  
  <p>
    If the action is complete and you try to navigate to your web app you will get the following message (404):
  </p>
  
  <p>
    <a href="/assets/images/2021/07/image-17.png"><img loading="lazy" width="360" height="229" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-17.png" border="0" /></a>
  </p>
  
  <p>
    Notice the address bar is redirecting to /.auth/login/aad.
  </p>
  
  <p>
    We need to add the AADClientID and AADSecret to the web app configuration.
  </p>
  
  <p>
  </p>
  
  <h2>
    Web App configuration
  </h2>
  
  <p>
    In your Static Web App, click on Configuration and choose ‘+ Add’:
  </p>
  
  <p>
    <a href="/assets/images/2021/07/image-18.png"><img loading="lazy" width="368" height="201" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-18.png" border="0" /></a>
  </p>
  
  <p>
    You need to add two entries, one with the name AADSecret with the value you copied in the above step and one with the name AADClientID with the client ID you copied previously.
  </p>
  
  <p>
    <a href="/assets/images/2021/07/image-19.png"><img loading="lazy" width="429" height="216" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-19.png" border="0" /></a>
  </p>
  
  <p>
    Choose the ‘Save’ icon at the top and browse to your application, you will be prompted for authentication and the first time you authenticate the app you will get a ‘Permissions requested’ dialog since we are allowing the app to sign in and read profile information:
  </p>
  
  <p>
    <a href="/assets/images/2021/07/image-20.png"><img loading="lazy" width="397" height="327" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/07/image_thumb-20.png" border="0" /></a>
  </p>
  
  <h2>
  </h2>
  
  <h2>
    Conclusion
  </h2>
  
  <p>
    This is the simplest step by step overview I could make for you.&nbsp; There are many more options to build on here.&nbsp; This is a great place to start and verify your setup!
  </p>
  
  <h2>
  </h2>
  
  <h2>
    Troubleshooting
  </h2>
  
  <p>
    Most of the time, if you have followed these steps and get an error, it is due to whitespace or an error!
  </p>
  
  <p>
    404
  </p>
  
  <p>
    If you get an error “AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: &#8216;3ae38ce7-5da2-435a-a631-c678c0894d97&#8217;.”&nbsp; this is exactly what it says.&nbsp; There is an issue with the reply URL.&nbsp; For example, I had used /add&nbsp; in the callback instead of /aad
  </p>
  
  <p>
    403
  </p>
  
  <p>
    I had an issue following a walkthrough and the <strong>userDetailsClaim</strong> value had<font style="background-color: rgb(255, 255, 0);"> a space</font> in it:&nbsp; &#8220;userDetailsClaim&#8221;:<font style="background-color: rgb(255, 255, 0);"><font style="background-color: rgb(255, 255, 0);"> &#8220;</font> http://</font>schemas.xmlsoap.org/ws/2005/05/identity/claims/name&#8221;.&nbsp; Removing the space fixed the 403
  </p>
  
  <p>
  </p>
  
  <h2>
    References
  </h2>
  
  <p>
    <a href="https://docs.microsoft.com/en-us/azure/static-web-apps/get-started-portal?tabs=vanilla-javascript">Quickstart: Building your first static web app with Azure Static Web Apps using the Azure portal | Microsoft Docs</a>
  </p>
  
  <p>
    <a href="https://docs.microsoft.com/en-us/azure/static-web-apps/authentication-custom?tabs=aad">Custom authentication in Azure Static Web Apps | Microsoft Docs</a>
  </p>
  
  <p>
    <a href="https://docs.microsoft.com/en-us/azure/static-web-apps/authentication-authorization">Authentication and authorization for Azure Static Web Apps | Microsoft Docs</a>
  </p>
  
  <p>
    <a href="https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-aad#-create-an-app-registration-in-azure-ad-for-your-app-service-app">Configure Azure AD authentication &#8211; Azure App Service | Microsoft Docs</a>
  </p>