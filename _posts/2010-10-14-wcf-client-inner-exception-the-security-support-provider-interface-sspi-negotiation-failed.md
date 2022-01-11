Creating a WCF Client in Visual Studio 2010, I struggled with this error.&nbsp; I was running as the currently logged on user and the service was as well so this made no sense to me.&nbsp; I found that this entry in the client app.config was the culprit:

<identity>  
<userPrincipalName value=&#8221;MYDOMAIN\MyUsername&#8221; />  
</identity> 

Simply deleting these 3 lines allowed me to test the client. 

Let me know if this helped you! </p>