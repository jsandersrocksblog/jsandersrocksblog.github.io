EasyAuth (<a href="https://cgillum.tech/category/easy-auth/" target="_blank" rel="noopener noreferrer">https://cgillum.tech/category/easy-auth/</a>)&nbsp; generates an internal access token ‘x-ms-token-aad-access-token‘.&nbsp; By default this token is an internal only format that you can’t use as a bearer token (it does not even look like one).&nbsp; You can utilize an unpublished (until now) feature to authenticate against another resource and this will result in a bearer token being generated that you can use to access that resource.&nbsp; The concept is that you can add additional login parameters that authenticate you against the object you wish to get an access token for.&nbsp; So you log into that resource and an access token is generated for you by Easy Auth.&nbsp; Special thanks to Connor McMahon who helped me get this all figured out!



# Walkthrough

In this example, An app called “jsandersadauthtestweb” and will be the app that will be used to authenticate and will in turn use a bearer token to authenticate to the api app called “jsandersadtestapi”

Create an App Service and use the Authentication Active Directory express mode to generate the necessary entries in your Active Directory. 



[<img loading="lazy" width="484" height="354" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-4.png" border="0" />](/assets/images/2020/01/image-4.png)

Create another resource similarly “jsandersadtestapi”

[<img loading="lazy" width="483" height="347" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-5.png" border="0" />](/assets/images/2020/01/image-5.png)

Add permissions for the first app to use user_impersonation to the api app by opening the app in Azure Active Directory,

Then go to API permissions and select ‘+ Add a permission’:



[<img loading="lazy" width="473" height="352" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-14.png" border="0" />](/assets/images/2020/01/image-23.png)



Find the API app you are going to call from the Web App under ‘APIs my organization uses’ and click on it

[<img loading="lazy" width="351" height="660" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-15.png" border="0" />](/assets/images/2020/01/image-24.png)

and grant user_impersonation by selecting and hitting the ‘Add permissions’ button:

[<img loading="lazy" width="488" height="472" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-16.png" border="0" />](/assets/images/2020/01/image-25.png)

This results in Configured Permissions similar to this:

[<img loading="lazy" width="441" height="252" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-17.png" border="0" />](/assets/images/2020/01/image-28.png)



Get the Client ID of the resource you want the x-ms-token-aad-access-token to be used for (the target)

You can do this several ways but in this case I simply look it up in the Active Directory:

[<img loading="lazy" width="587" height="368" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-6.png" border="0" />](/assets/images/2020/01/image-6.png)

You will use this ID in the next step…

Go back to the source app “jsandersadauthtestweb” and invoke resource explorer, select ‘Go’

[<img loading="lazy" width="516" height="277" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-7.png" border="0" />](/assets/images/2020/01/image-7.png)

Click on Read/Write at the top so we can make changes:

[<img loading="lazy" width="221" height="92" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-8.png" border="0" />](/assets/images/2020/01/image-8.png)

Expand the ‘config’, ‘authsettings’ section 

Click on Edit:

[<img loading="lazy" width="244" height="133" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-9.png" border="0" />](/assets/images/2020/01/image-9.png)

and change the “additionalLoginParams” section from null to point to the clientid of the object you want to get a access toke for “jsandersadtestapi”

&#8220;additionalLoginParams&#8221;: [  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;resource=9cffc72e-9a8c-44d1-9604-638028ad823d&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp; ],

[<img loading="lazy" width="834" height="246" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-10.png" border="0" />](/assets/images/2020/01/image-10.png)

Click on ‘Put’ to save your changes.

I insert the following code in the web app to retrieve the auth token and display it in a Literal control I dropped on the form:

protected void Page_Load(object sender, EventArgs e)  
{  
&nbsp;&nbsp;&nbsp;&nbsp; try  
&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // this token is a propriatary token, not a bearer token, however you can auth to another resource  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // and get this as a bearer token  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; string accessToken = Request.Headers[&#8220;x-ms-token-aad-access-token&#8221;];  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Literal1.Text = accessToken;  
&nbsp;&nbsp;&nbsp;&nbsp; }  
&nbsp;&nbsp;&nbsp;&nbsp; catch (Exception ex) {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Literal1.Text = &#8220;Problem with access token: &#8221; + ex.Message;  
&nbsp;&nbsp;&nbsp;&nbsp; }  
}



Authenticating into the app I displayed a good bearer token that I can use to authenticate to the api app (using postman below):

[  
](/assets/images/2020/01/image-31.png) 

[<img loading="lazy" width="844" height="514" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-11.png" border="0" />](/assets/images/2020/01/image-32.png)

# 

# Extending to your Slots

If you want to apply this to your slots, you need to apply the same settings to the slot.&nbsp; Enable AD Authentication like you did for the site but ensure you choose and existing Active Directory App this time and use the one that was created for the main site.

You will need to add the slot url as a valid reply url.&nbsp; Open the application in Active Directory and put the slot form of the reply url in and save:

[<img loading="lazy" width="1003" height="258" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-12.png" border="0" />](/assets/images/2020/01/image-17.png)

After that, use resource explorer and for the new slot fill in the clientSecret and additionalLoginParams in the slots, <yourslotname> config, authsettings section and save!

[<img loading="lazy" width="708" height="482" title="clip_image002" style="display: inline; background-image: none;" alt="clip_image002" src="/assets/images/2020/01/clip_image002_thumb.jpg" border="0" />](/assets/images/2020/01/clip_image002.jpg)

# Troubleshooting

You can use the /.auth/me endpoint of your application to see these tokens and play with them:

[<img loading="lazy" width="570" height="559" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-13.png" border="0" />](/assets/images/2020/01/image-20.png)

If the token is not formed like a bearer token ‘ey…..&nbsp; then you forget to add the correct ‘additionalLoginParams’

If the token is blank, you don’t have the client secret set (or set correctly).

Use <a href="https://jwt.io/" target="_blank" rel="noopener noreferrer">https://jwt.io/</a> to decode your token and see what it contains&nbsp; (note the ‘aud’) for example

Use fiddler or postman to see the auth flow!

User verbose application logging in the web app to see what Easy Auth is doing.

# 

# Summary

This just scratches the surface of what you can do but there was nothing ‘Easy’ out there to get you started until now.

Here is a similar post you may found enlightening as well! <a href="https://techcommunity.microsoft.com/t5/azure-app-service/azure-app-service-easyauth-and-azure-active-directory-flows/ba-p/1099890" target="_blank" rel="noopener noreferrer">Azure App Service EasyAuth and Azure Active Directory Flows</a>

Drop me a note if you find this useful!