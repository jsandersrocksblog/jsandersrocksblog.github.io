

You have some code you have created in your subscription and a customer wants to authenticate and use your application.&nbsp; You are not connected to any other Azure Active Directory authentication.&nbsp; This is bit of a contrived example but will give you some insight in to how Azure App Services authentication works.

## 

## Setup

Create a new Azure App Service Web in your Subscription.&nbsp; Ensure it is working fine and deploy it (do not specify any authentication yet).&nbsp; In my case the app is called ‘jsandersauthtoanotherazuread’ and the full URL is [http://jsandersauthtoanotherazuread.azurewebsites.net/](http://jsandersauthtoanotherazuread.azurewebsites.net/ "http://jsandersauthtoanotherazuread.azurewebsites.net/").

The name of the Azure AD tenant I want to do the auth for my app is jsandersrocks.onmicrosoft.com

The steps will then be:

  * Give the URL to the Azure AD tenant admin of jsandersrocks so the callback URL can be assigned and the app created
  * jsandersrocks Creates an Azure App Services in there tenant and give you the issuer, and application ID information
  * You use this to configure your app for authentication

## Walkthrough

When the app authenticates it will have a generated callback url that is of the format:&nbsp; <https://jsandersauthtoanotherazuread.azurewebsites.net/.auth/login/aad/callback> .&nbsp; I need to give this callback URL to the Azure AD tenant owner.

### Tenant Directory owner tasks:

The owner of the Tenant Directory creates a dummy app (with any name) and sets the login url to the callback url above.&nbsp; The name will be the name that is shown when you login (see below).&nbsp; Choose wisely! The Sign-on URL should be the call back url above:

[<img loading="lazy" title="capture20170609141746403" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609141746403" src="/assets/images/2017/06/capture20170609141746403_thumb.png" width="844" height="218" />](/assets/images/2017/06/capture20170609141746403.png)

Then copies the generated app id to give to you from the properties of this new app:&nbsp; 512bf2b6-8a54-4c0b-9c8e-31350b16f606

[<img loading="lazy" title="capture20170609141840401" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609141840401" src="/assets/images/2017/06/capture20170609141840401_thumb.png" width="629" height="309" />](/assets/images/2017/06/capture20170609141840401.png)

and give you the issuer Directory ID from the Properties tab of the Active Directory page: 3151db49-e251-45a6-9f58-2e90469383de.&nbsp; You will use this to build the issuer ID.

[<img loading="lazy" title="capture20170609142035808" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609142035808" src="/assets/images/2017/06/capture20170609142035808_thumb.png" width="500" height="555" />](/assets/images/2017/06/capture20170609142035808.png)

### Your tasks:

Turn on App Service Authentication for your app:

[<img loading="lazy" title="capture20170609142306286" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609142306286" src="/assets/images/2017/06/capture20170609142306286_thumb.png" width="456" height="351" />](/assets/images/2017/06/capture20170609142306286.png)

Configure the Azure Active Directory Authentication by clicking on the Advanced button and use the information the Tenant Directory owner gave you.&nbsp; The app ID is used for the Client ID field and the Issuer Url is constructed from the Directory ID of the form:&nbsp; https://sts.windows.net/DIRECTORYIDHERE

[<img loading="lazy" title="capture20170609142606120" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609142606120" src="/assets/images/2017/06/capture20170609142606120_thumb.png" width="496" height="318" />](/assets/images/2017/06/capture20170609142606120.png)

Be sure to save your changes.

Test the auth to ensure it works &#8211; [https://jsandersauthtoanotherazuread.azurewebsites.net/.auth/login/aad](https://jsandersauthtoanotherazuread.azurewebsites.net/.auth/login/aad "https://jsandersauthtoanotherazuread.azurewebsites.net/.auth/login/aad")

[<img loading="lazy" title="capture20170609150131908" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609150131908" src="/assets/images/2017/06/capture20170609150131908_thumb.png" width="324" height="257" />](/assets/images/2017/06/capture20170609150131908.png)[<img loading="lazy" title="capture20170609143626284" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609143626284" src="/assets/images/2017/06/capture20170609143626284_thumb.png" width="521" height="174" />](/assets/images/2017/06/capture20170609143626284.png)

&nbsp;

## 

## Errors

If you have trouble, the sign in page will tell you what the issue is.&nbsp; For example, if the callback URL in the Tenant Directory was not correct (I initially used http instead of https) you get an error like this:

### Sign In

Sorry, but we’re having trouble signing you in. 

We received a bad request. 

  * 

Additional technical information: 

Correlation ID: cfe9995f-bae7-4fe2-a7d8-24649b92493c 

Timestamp: 2017-06-09 18:29:44Z 

AADSTS50011: The reply address &#8216;https://jsandersauthtoanotherazuread.azurewebsites.net/.auth/login/aad/callback&#8217; does not match the reply addresses configured for the application: &#8216;512bf2b6-8a54-4c0b-9c8e-31350b16f606&#8217;. More details: not specified 

## Additional Tasks

Now that I am logged in, I will add a login button (if not logged in) and display the logged in user information.&nbsp; You can do this in global.asax, page level or in an on_authenticated method.

### Login button

<pre class="code"><span style="background: yellow;color: black">&lt;%</span><span style="color: blue">@ </span><span style="color: maroon">Page </span><span style="color: red">Language</span><span style="color: blue">="C#" </span><span style="color: red">AutoEventWireup</span><span style="color: blue">="true" </span><span style="color: red">CodeBehind</span><span style="color: blue">="Default.aspx.cs" </span><span style="color: red">Inherits</span><span style="color: blue">="LoginButton.Default" </span><span style="background: yellow;color: black">%&gt;
</span><span style="color: blue">&lt;!</span><span style="color: maroon">DOCTYPE </span><span style="color: red">html</span><span style="color: blue">&gt;
&lt;</span><span style="color: maroon">html </span><span style="color: red">xmlns</span><span style="color: blue">="http://www.w3.org/1999/xhtml"&gt;
&lt;</span><span style="color: maroon">head </span><span style="color: red">runat</span><span style="color: blue">="server"&gt;
    &lt;</span><span style="color: maroon">title</span><span style="color: blue">&gt;&lt;/</span><span style="color: maroon">title</span><span style="color: blue">&gt;
&lt;/</span><span style="color: maroon">head</span><span style="color: blue">&gt;
&lt;</span><span style="color: maroon">body</span><span style="color: blue">&gt;
    &lt;</span><span style="color: maroon">form </span><span style="color: red">id</span><span style="color: blue">="form1" </span><span style="color: red">runat</span><span style="color: blue">="server"&gt;
        &lt;</span><span style="color: maroon">div</span><span style="color: blue">&gt;
            &lt;</span><span style="color: maroon">asp</span><span style="color: blue">:</span><span style="color: maroon">Button </span><span style="color: red">ID</span><span style="color: blue">="Button1" </span><span style="color: red">runat</span><span style="color: blue">="server" </span><span style="color: red">Text</span><span style="color: blue">="Button" /&gt;
            &lt;</span><span style="color: maroon">asp</span><span style="color: blue">:</span><span style="color: maroon">Label </span><span style="color: red">ID</span><span style="color: blue">="Label1" </span><span style="color: red">runat</span><span style="color: blue">="server" </span><span style="color: red">Text</span><span style="color: blue">="Not Logged In"&gt;&lt;/</span><span style="color: maroon">asp</span><span style="color: blue">:</span><span style="color: maroon">Label</span><span style="color: blue">&gt;
        &lt;/</span><span style="color: maroon">div</span><span style="color: blue">&gt;
    &lt;/</span><span style="color: maroon">form</span><span style="color: blue">&gt;
&lt;/</span><span style="color: maroon">body</span><span style="color: blue">&gt;
&lt;/</span><span style="color: maroon">html</span><span style="color: blue">&gt;
</span></pre>

## 

code:

<pre class="code"><span style="color: blue">public partial class </span><span style="color: #2b91af">Default </span><span style="color: black">: System.Web.UI.</span><span style="color: #2b91af">Page
   </span><span style="color: black">{
       </span><span style="color: blue">protected void </span><span style="color: black">Page_Load(</span><span style="color: blue">object </span><span style="color: black">sender, </span><span style="color: #2b91af">EventArgs </span><span style="color: black">e)
       {
           </span><span style="color: green">// if authenticated...
           </span><span style="color: blue">if </span><span style="color: black">(</span><span style="color: blue">this</span><span style="color: black">.User.Identity.IsAuthenticated)
           {
               Button1.Visible = </span><span style="color: blue">false</span><span style="color: black">;
               Label1.Text = </span><span style="color: blue">this</span><span style="color: black">.User.Identity.Name;
           }
           </span><span style="color: blue">else </span><span style="color: black">{
               Button1.Visible = </span><span style="color: blue">true</span><span style="color: black">;
               Label1.Text = </span><span style="color: #a31515">"Not Authenticated"</span><span style="color: black">;
           }
       }
           </span><span style="color: blue">protected void </span><span style="color: black">Button1_Click(</span><span style="color: blue">object </span><span style="color: black">sender, </span><span style="color: #2b91af">EventArgs </span><span style="color: black">e)
       {
           Response.Clear();
           Response.Redirect(</span><span style="color: #a31515">"/.auth/login/aad?post_login_redirect_url=/"</span><span style="color: black">);
           Response.Flush();
       }
   }</span></pre>

Starting an in-private or incognito browser session, when I first hit the page I am not authenticated but when I hit the button I go through the auth sequence and display the email address:

[<img loading="lazy" title="capture20170609150603934" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170609150603934" src="/assets/images/2017/06/capture20170609150603934_thumb.png" width="650" height="264" />](/assets/images/2017/06/capture20170609150603934.png)

&nbsp;

## 

## Conclusion

This just scratches the surface of what you can do.&nbsp; The point is, Azure App Services authentication can take the heavy lifting of authentication off or your plate and you can do some powerful things.&nbsp; This showed that as long as you configure the application with the correct issuer and app ID, it is able to validate and trust the token from a provider you do not have access to (with some cooperation from the sender).

If you want to do fancy things like authenticate to many different Azure AD tenants then you do need to utilize ADAL but that is beyond the scope of this post. 

Drop me a note if you found this useful!

## More references

The Bible of auth for me: <https://www.microsoftpressstore.com/store/modern-authentication-with-azure-active-directory-for-9780735696945>

Overview of auth scenarios: [https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Factive-directory%2Fdevelop%2Factive-directory-authentication-scenarios&data=02%7C01%7Cjsanders%40microsoft.com%7C375217df84aa4698da0e08d4af4f355a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636326202144438252&sdata=7vT9j8lYZHxk9AUy54k3C6QhuOvfeiVAQ4DsxFJqYoE%3D&reserved=0)

App Roles: [https://blogs.msdn.microsoft.com/waws/2017/03/09/azure-app-service-authentication-app-roles/](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.msdn.microsoft.com%2Fwaws%2F2017%2F03%2F09%2Fazure-app-service-authentication-app-roles%2F&data=02%7C01%7Cjsanders%40microsoft.com%7C375217df84aa4698da0e08d4af4f355a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636326202144438252&sdata=NGJLsvNkgVMf5MWuUn0te3Alw3sQlrvW60jDTFDQXb8%3D&reserved=0)

App Groups: [https://blogs.msdn.microsoft.com/waws/2017/03/13/azure-app-service-authentication-aad-groups/](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.msdn.microsoft.com%2Fwaws%2F2017%2F03%2F13%2Fazure-app-service-authentication-aad-groups%2F&data=02%7C01%7Cjsanders%40microsoft.com%7C375217df84aa4698da0e08d4af4f355a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636326202144438252&sdata=7cwwBJ4T9rHeNVNl4NKX6hRNCOvXvsEvZ4zyx8fOgJU%3D&reserved=0)