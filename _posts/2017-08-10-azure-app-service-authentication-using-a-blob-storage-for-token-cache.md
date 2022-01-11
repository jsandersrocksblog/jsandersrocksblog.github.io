Chris had this note in <a href="https://cgillum.tech/2016/03/07/app-service-token-store/" target="_blank">his blog App Service Token Store</a>

“As an alternative, you can provision an Azure Blob Storage container and configure your web app with a SaS URL (with read/write/list access) pointing to that blob container. This SaS URL can then be saved to the **WEBSITE\_AUTH\_TOKEN\_CONTAINER\_SASURL** app setting. When this app setting is present, all tokens will be stored in and fetched from the specified blob container.”

This is still in preview but very useful.&nbsp; For example, you would lose your token cache when doing a slot swap on your site from a test to production slot.

# Here is a walkthrough on how to add this to your Azure Web App

Create a Storage resource in Azure using the defaults.&nbsp; Put it in the same region as your web app for performance reasons

Create a container in the BLOB SERVICE of the storage you created using the default settings and call it _tokens_

[<img loading="lazy" title="capture20170810143155663" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170810143155663" src="/assets/images/2017/08/capture20170810143155663_thumb.png" width="592" height="494" />](/assets/images/2017/08/capture20170810143155663.png)

__&nbsp;

Create a Shared access signature (SaS) token so we can access that container.&nbsp; Note the options I chose and that I set the expiration date out 10 years in the future (You probably want a shorter date like 2 years out and renew it then):

[<img loading="lazy" title="capture20170810145712446" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170810145712446" src="/assets/images/2017/08/capture20170810145712446_thumb.png" width="578" height="715" />](/assets/images/2017/08/capture20170810145712446.png)

&nbsp;

Copy the Blob Service SAS URL, pasted in notepad and add the container name to the URL:

https://jsandersauthtokencahe.blob.core.windows.net/?sv=2017-04-17&ss=b&srt=c&sp=rwl&se=2027-08-10T22:56:09Z&st=2017-08-10T14:56:09Z&spr=https&sig=tV8wI%2F%2B4%2xxxxxx

https://jsandersauthtokencahe.blob.core.windows.net/<font style="background-color: #ffff00">token/</font>?sv=2017-04-17&ss=b&srt=c&sp=rwl&se=2027-08-10T22:56:09Z&st=2017-08-10T14:56:09Z&spr=https&sig=tV8wI%2F%2B4%2xxxxxx

Open your Azure App Service, create an Application called **WEBSITE\_AUTH\_TOKEN\_CONTAINER\_SASURL**&nbsp; and paste the modified SAS Url you just created. 

&nbsp;

That is it!

# Troubleshooting

Turn on verbose application logging in the Azure App Services and take a look at the application logs.&nbsp; They will give you any errors and reasons for those errors.

For instance:

2017-08-10T18:36:05&nbsp; PID[15432] Verbose&nbsp;&nbsp;&nbsp;&nbsp; Calling into external HTTP endpoint PUT <https://jsandersauthtokencahe.blob.core.windows.net/4ca06726d07351d870a15c6c9e8f21a9.json>.  
2017-08-10T18:36:06&nbsp; PID[15432] Warning&nbsp;&nbsp;&nbsp;&nbsp; Call to HTTP endpoint <https://jsandersauthtokencahe.blob.core.windows.net/4ca06726d07351d870a15c6c9e8f21a9.json> failed: 404 (The specified container does not exist.). Partial response: <?xml version=&#8221;1.0&#8243; encoding=&#8221;utf-8&#8243;?><Error><Code>ContainerNotFound</Code><Message>The specified container does not exist.  
RequestId:edd0e5f3-0001-0020-3707-12cfb6000000  
Time:2017-08-10T18:36:04.1903028Z</Message></Error>

The problem was that I didn’t add _tokens_ to the SAS URL

Success:

2017-08-10T18:39:19&nbsp; PID[14048] Verbose&nbsp;&nbsp;&nbsp;&nbsp; Calling into external HTTP endpoint PUT <https://jsandersauthtokencahe.blob.core.windows.net/tokens/f49bd000cd8e0ef29cf366858383b834.json>.

&nbsp;

You can see these tokens for your self by using the Microsoft Azure Storage Explorer:&nbsp; [http://storageexplorer.com/](http://storageexplorer.com/ "http://storageexplorer.com/")

[<img loading="lazy" title="capture20170810150831030" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170810150831030" src="/assets/images/2017/08/capture20170810150831030_thumb.png" width="659" height="332" />](/assets/images/2017/08/capture20170810150831030.png)