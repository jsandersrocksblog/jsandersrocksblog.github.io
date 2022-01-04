---
id: 1858
title: Accessing Azure App Services using Azure AD Bearer token
date: 2017-03-17T12:27:17-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1858
permalink: /2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta property="og:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta name="twitter:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta name="twitter:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta property="og:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta name="twitter:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta name="twitter:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta property="og:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta name="twitter:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta name="twitter:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta property="og:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta name="twitter:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta name="twitter:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta property="og:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Accessing Azure App Services using Azure AD Bearer token" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/03/17/accessing-azure-app-services-using-azure-ad-bearer-token/" />
    <meta name="twitter:description" content="Overview Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app. Review Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered..." />
    <meta name="twitter:image" content="/assets/images/2017/03/snip_20170317080739_thumb.png" />
    
categories:
  - Uncategorized
---
Here are some simplified instructions on how to setup and use Azure Active Directory authentication for Azure App Services and code that will allow an application to use a Bearer Token to access that app.

## Review

Simply put, the OAuth Bearer Token simply identifies the app that is calling an Azure Active Directory registered application.  The calling application requests a Token from AD by providing some information to include the Client Secret and Application ID of the app that will be calling the target app (the app that will use the token) as well as the Application ID of the application you wish to call.  The client secret is the key that you want to protect and keep ‘secret’.

## Walkthrough

### Register the target app you want to call in Azure AD and get the Application ID.  No client secret required.

Simply click on the application in the portal and enable Azure AD authentication (express) and save.  
Copy the Application ID.  After the app is updated go back into the Azure Active Authentication and click on the Advanced button.  This will allow you to copy the Application ID:  
[<img loading="lazy" width="701" height="292" title="snip_20170317080739" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="snip_20170317080739" src="/assets/images/2017/03/snip_20170317080739_thumb.png" border="0" />](/assets/images/2017/03/snip_20170317080739.png)  
&nbsp;

### 

### Register the client app you want to call from in Azure AD and get the Application ID, and generate a Client Secret Key

Simply click on the application in the portal and enable Azure AD authentication (express) and save.  
You now need to go to the application registered in Azure AD and get the Application ID and generate a Client Secret.  Copy the Application ID and Client Secret of this client app to use later like you did in the previous step.  
[<img loading="lazy" width="725" height="295" title="capture20170316102620455" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170316102620455" src="/assets/images/2017/03/capture20170316102620455_thumb.png" border="0" />](/assets/images/2017/03/capture20170316102620455.png)  
Generate a client Secret by going to Azure Active Directory in the portal.  Search for the Client app:  
[<img loading="lazy" width="643" height="350" title="capture20170316102812597" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170316102812597" src="/assets/images/2017/03/capture20170316102812597_thumb.png" border="0" />](/assets/images/2017/03/capture20170316102812597.png)  
In Settings choose _Keys:_  
[<img loading="lazy" width="652" height="306" title="capture20170316102831349" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170316102831349" src="/assets/images/2017/03/capture20170316102831349_thumb.png" border="0" />](/assets/images/2017/03/capture20170316102831349.png)  
In Keys create a New Key (name it whatever you want) and Save:  
[<img loading="lazy" width="483" height="285" title="capture20170316102907130" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170316102907130" src="/assets/images/2017/03/capture20170316102907130_thumb.png" border="0" />](/assets/images/2017/03/capture20170316102907130.png)  
**Important.**  When you save you need to copy the Value for later as you cannot come back and get it.  **This is the Client Secret**.  
[<img loading="lazy" width="740" height="271" title="capture20170316102930647" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170316102930647" src="/assets/images/2017/03/capture20170316102930647_thumb.png" border="0" />](/assets/images/2017/03/capture20170316102930647.png)  
Note:  You can always generate a new secret if you forget or lose it.

### Create code to get a Bearer token from Azure AD and use this token to call the Target app

Now you simply need to use the values from above to request a token and make a request using that token in the Authorization header.  
Here is some sample code.  First the ServicePrinciple class is used to build and get the token.  I am using the latest ADAL library we provide (Microsoft.IdentityModel.Clients.ActiveDirectory ver 3.13.8:  
[<img loading="lazy" width="703" height="217" title="capture20170317081758672" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border-width: 0px" alt="capture20170317081758672" src="/assets/images/2017/03/capture20170317081758672_thumb.png" border="0" />](/assets/images/2017/03/capture20170317081758672.png)

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

This is a very compact sample that can be used as a checklist.  It eliminated a lot of the information in our documentation here: <a target="_blank" href="https://docs.microsoft.com/en-us/azure/app-service-api/app-service-api-dotnet-service-principal-auth">Service principal authentication for API Apps in Azure App Service</a>  
Drop me a note if you found this useful!