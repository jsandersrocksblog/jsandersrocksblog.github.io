Here are some simplified instructions on how to setup and use Azure Active Directory authentication for a client Azure App Services application and code that will allow a client application to use a Bearer Token to access a different target app.&nbsp;&nbsp; In this scenario there are two web apps.&nbsp; The _client app_ is the app that has code to call to the _target app_.&nbsp; Anyone can reach the _client app_ without authentication and the _client app_ then uses a Bearer token to access the _target app_ which requires Active Directory Authentication.&nbsp; This assumes you have already created both apps in the Azure Portal

## Review

Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered application.&nbsp; The calling application requests a Token from AD by providing some information to include the Client Secret and Application ID of the app that will be calling the target app (the app that will use the token) as well as the Application ID of the application you wish to call.&nbsp; The client secret is the key that you want to protect and keep ‘secret’.

## Walkthrough

### Register the _target app_ you are calling from the _client app_ in Azure AD and get the Application ID.&nbsp; No client secret required.

My target app is https://jsandersapicall.azurewebsites.net.&nbsp;&nbsp; Simply click on the application in the Azure Portal and enable Azure AD authentication (express) and save.

Copy the Client ID (which is also know as the Application ID).&nbsp; After the app is updated go back into the Azure Active Authentication and click on the Advanced button.&nbsp; This will allow you to copy the Application ID:

[<img loading="lazy" title="snip_20170317080739" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="snip_20170317080739" src="/assets/images/2017/03/snip_20170317080739_thumb.png" width="701" height="292" />](/assets/images/2017/03/snip_20170317080739.png)

Next Require the app to ‘Log in with Azure Active Directory’ and save.&nbsp; This will ensure only calls that are authenticated can get to this server:

[<img loading="lazy" title="capture20170317103028578" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170317103028578" src="/assets/images/2017/03/capture20170317103028578_thumb.png" width="394" height="401" />](/assets/images/2017/03/capture20170317103028578.png)

### 

### Register the _client app_ in Azure AD and get the Application ID, and generate a Client Secret Key

My client app is https://WebApplication420170316082455.azurewebsites.net (the one calling the protected target app).&nbsp; Simply click on the _client app_ in the portal and enable Azure AD authentication (express) and save.

You now need to go to the application registered in Azure AD and get the Client ID and generate a Client Secret.&nbsp; Copy the Client ID and Client Secret of this client app to use later like you did in the previous step.

[<img loading="lazy" title="capture20170316102620455" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170316102620455" src="/assets/images/2017/03/capture20170316102620455_thumb.png" width="725" height="295" />](/assets/images/2017/03/capture20170316102620455.png)

Generate a client Secret by going to Azure Active Directory in the portal.&nbsp; Search for the Client app:

[<img loading="lazy" title="capture20170316102812597" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170316102812597" src="/assets/images/2017/03/capture20170316102812597_thumb.png" width="643" height="350" />](/assets/images/2017/03/capture20170316102812597.png)

In Settings choose _Keys:_

[<img loading="lazy" title="capture20170316102831349" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170316102831349" src="/assets/images/2017/03/capture20170316102831349_thumb.png" width="652" height="306" />](/assets/images/2017/03/capture20170316102831349.png)

In Keys create a New Key (name it whatever you want) and Save:

[<img loading="lazy" title="capture20170316102907130" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170316102907130" src="/assets/images/2017/03/capture20170316102907130_thumb.png" width="483" height="285" />](/assets/images/2017/03/capture20170316102907130.png)

**Important.**&nbsp; When you save you need to copy the Value for later as you cannot come back and get it.&nbsp; **This is the Client Secret**.

[<img loading="lazy" title="capture20170316102930647" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170316102930647" src="/assets/images/2017/03/capture20170316102930647_thumb.png" width="740" height="271" />](/assets/images/2017/03/capture20170316102930647.png)

Note:&nbsp; You can always generate a new secret if you forget or lose it.

### Create code to get a Bearer token from Azure AD and use this token to call the Target app

Now you simply need to use the values from above to request a token and then make a request to the _target app_ from the _client app_ using that token in the Authorization header.

Here is some sample code.&nbsp; First the ServicePrinciple class is used to build and get the token.&nbsp; I am using the latest ADAL library we provide (Microsoft.IdentityModel.Clients.ActiveDirectory ver 3.13.8:

[<img loading="lazy" title="capture20170317081758672" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170317081758672" src="/assets/images/2017/03/capture20170317081758672_thumb.png" width="703" height="217" />](/assets/images/2017/03/capture20170317081758672.png)

<pre class="code"><span style="color: blue">public static class </span><span style="color: #2b91af">ServicePrincipal
    </span><span style="color: black">{
        </span><span style="color: gray">/// &lt;summary&gt;
        /// </span><span style="color: green">The variables below are standard Azure AD terms from our various samples
        </span><span style="color: gray">/// </span><span style="color: green">We set these in the Azure Portal for this app for security and to make it easy to change (you can reuse this code in other apps this way)
        </span><span style="color: gray">/// </span><span style="color: green">You can name each of these what you want as long as you keep all of this straight
        </span><span style="color: gray">/// &lt;/summary&gt;
        </span><span style="color: blue">static string </span><span style="color: black">authority = </span><span style="color: #2b91af">ConfigurationManager</span><span style="color: black">.AppSettings[</span><span style="color: #a31515">"ida:Authority"</span><span style="color: black">];  </span><span style="color: green">// the AD Authority used for login.  For example: https://login.microsoftonline.com/myadnamehere.onmicrosoft.com
        </span><span style="color: blue">static string </span><span style="color: black">clientId = </span><span style="color: #2b91af">ConfigurationManager</span><span style="color: black">.AppSettings[</span><span style="color: #a31515">"ida:ClientId"</span><span style="color: black">]; </span><span style="color: green">// the Application ID of this app.  This is a guid you can get from the Advanced Settings of your Auth setup in the portal
        </span><span style="color: blue">static string </span><span style="color: black">clientSecret = </span><span style="color: #2b91af">ConfigurationManager</span><span style="color: black">.AppSettings[</span><span style="color: #a31515">"ida:ClientSecret"</span><span style="color: black">]; </span><span style="color: green">// the key you generate in Azure Active Directory for this application
        </span><span style="color: blue">static string </span><span style="color: black">resource = </span><span style="color: #2b91af">ConfigurationManager</span><span style="color: black">.AppSettings[</span><span style="color: #a31515">"ida:Resource"</span><span style="color: black">]; </span><span style="color: green">// the Application ID of the app you are going to call.  This is a guid you can get from the Advanced Settings of your Auth setup for the targetapp in the portal
        </span><span style="color: gray">/// &lt;summary&gt;
        /// </span><span style="color: green">wrapper that passes the above variables
        </span><span style="color: gray">/// &lt;/summary&gt;
        /// &lt;returns&gt;&lt;/returns&gt;
        </span><span style="color: blue">static public async </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: #2b91af">AuthenticationResult</span><span style="color: black">&gt; GetS2SAccessTokenForProdMSAAsync()
        {
            </span><span style="color: blue">return await </span><span style="color: black">GetS2SAccessToken(authority, resource, clientId, clientSecret);
        }
        </span><span style="color: blue">static async </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: #2b91af">AuthenticationResult</span><span style="color: black">&gt; GetS2SAccessToken(</span><span style="color: blue">string </span><span style="color: black">authority, </span><span style="color: blue">string </span><span style="color: black">resource, </span><span style="color: blue">string </span><span style="color: black">clientId, </span><span style="color: blue">string </span><span style="color: black">clientSecret)
        {
            </span><span style="color: blue">var </span><span style="color: black">clientCredential = </span><span style="color: blue">new </span><span style="color: #2b91af">ClientCredential</span><span style="color: black">(clientId, clientSecret);
            </span><span style="color: #2b91af">AuthenticationContext </span><span style="color: black">context = </span><span style="color: blue">new </span><span style="color: #2b91af">AuthenticationContext</span><span style="color: black">(authority, </span><span style="color: blue">false</span><span style="color: black">);
            </span><span style="color: #2b91af">AuthenticationResult </span><span style="color: black">authenticationResult = </span><span style="color: blue">await </span><span style="color: black">context.AcquireTokenAsync(
                resource,  </span><span style="color: green">// the resource (app) we are going to access with the token
                </span><span style="color: black">clientCredential);  </span><span style="color: green">// the client credentials
            </span><span style="color: blue">return </span><span style="color: black">authenticationResult;
        }
    }
</span></pre>

And then using this class my code to fetch data from the Target resource:

<pre class="code"><span style="color: blue">protected async void </span><span style="color: black">Page_Load(</span><span style="color: blue">object </span><span style="color: black">sender, </span><span style="color: #2b91af">EventArgs </span><span style="color: black">e)
{
    </span><span style="color: green">// Normally you would use a single Global HttpClient per MS guidance
    // but for demo purposes... Just create one inline
    </span><span style="color: #2b91af">HttpClient </span><span style="color: black">client = </span><span style="color: blue">new </span><span style="color: #2b91af">HttpClient</span><span style="color: black">();
    </span><span style="color: green">// This is an Aspx page so clearing anything already written in the buffer
    </span><span style="color: black">Response.Clear();
    </span><span style="color: blue">try
    </span><span style="color: black">{
        </span><span style="color: green">// get the token
        </span><span style="color: blue">var </span><span style="color: black">token = </span><span style="color: blue">await </span><span style="color: #2b91af">ServicePrincipal</span><span style="color: black">.GetS2SAccessTokenForProdMSAAsync();
        </span><span style="color: green">// set the auth header with the aquired Bearer token
        </span><span style="color: black">client.DefaultRequestHeaders.Authorization =
            </span><span style="color: blue">new </span><span style="color: #2b91af">AuthenticationHeaderValue</span><span style="color: black">(</span><span style="color: #a31515">"Bearer"</span><span style="color: black">,token.AccessToken);
        </span><span style="color: green">// make the call to the resource requiring auth!
        </span><span style="color: blue">var </span><span style="color: black">resp = </span><span style="color: blue">await </span><span style="color: black">client.GetAsync(</span><span style="color: #a31515">"https://jsandersapicall.azurewebsites.net/"</span><span style="color: black">);
        </span><span style="color: green">// do something with the response
        </span><span style="color: black">Response.Write(resp.StatusCode.ToString());
    }
    </span><span style="color: blue">catch </span><span style="color: black">(</span><span style="color: #2b91af">Exception </span><span style="color: black">ex)
    {
        </span><span style="color: green">// important to log the exception if any because it will tell you what went wrong
        </span><span style="color: black">Response.Write(ex.Message);
    }
    </span><span style="color: green">// write page out
    </span><span style="color: black">Response.Flush();
}</span></pre>

&nbsp;

## Conclusion

This is a very compact sample that can be used as a checklist.&nbsp; It eliminated a lot of the information in our documentation here: <a href="https://docs.microsoft.com/en-us/azure/app-service-api/app-service-api-dotnet-service-principal-auth" target="_blank">Service principal authentication for API Apps in Azure App Service</a>&nbsp;

Drop me a note if you found this useful!