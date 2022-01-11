When you deploy an Azure Active Directory application that was working great locally you may get the following error when logging in:&nbsp; AADSTS50011: The reply address &#8216;http://<yourwebapp>.azurewebsites.net/signin-oidc&#8217; does not match the reply addresses configured for the application: &#8216;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#8217;. More details: not specified

This error would be specific to Azure App Services authentication (Easy Auth)

AADSTS50011: The reply address &#8216;https://<yourwebapp>/.auth/login/aad/callback&#8217; does not match the reply addresses configured for the application: &#8216;c8a23e63-b4e3-4d10-9cf8-0fca55207424&#8217;. More details: not specified&nbsp; 

## How to fix this

This error says it all!&nbsp; When you deploy your Active Directory Web app to Azure you need to ensure you add this URL to the Azure Active Directory application (or have someone with the permissions to manage you application in AD to this for you).

Go to the Azure portal: [https://portal.azure.com](https://portal.azure.com "https://portal.azure.com") sign in and click on the Azure Active Directory icon on the left. Then click on the ‘App registrations’ icon in the middle pane.&nbsp; In the search box enter the application from the error message and choose ‘All apps’ from the dropdown:

&nbsp;[<img loading="lazy" title="appregistration" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="appregistration" src="/assets/images/2018/01/appregistration_thumb.png" width="952" height="506" />](/assets/images/2018/01/appregistration.png)

Click on your application, then the Settings icon, select the ‘Reply URLs’ from the list.&nbsp; Paste in the name of the reply URL from the error message you had and ‘Save’:

[<img loading="lazy" title="capture20180130145337489" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180130145337489" src="/assets/images/2018/01/capture20180130145337489_thumb.png" width="1002" height="220" />](/assets/images/2018/01/capture20180130145337489.png)

Now you should be able to login with out that error message!

## Conclusion

Just a quick blog but I hope it saves you some time!