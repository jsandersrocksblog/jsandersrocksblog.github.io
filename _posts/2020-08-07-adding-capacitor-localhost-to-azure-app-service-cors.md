 

Again… just a quick post.&nbsp; The UI will not validate and allow you to add capacitor://localhost to the CORS settings in Azure App Services.&nbsp; Here are two ways to work around it.

## Use the CLI

Use the CLI/Powershell if you need to do this without a UI.&nbsp; Here is how to do it using az:

az webapp cors add &#8211;allowed-origins capacitor://localhost &#8211;name yourWebApp &#8211;resource-group webappResourceGroup &#8211;subscription yourSubscription



## Use Azure Resource Explorer

Use the Web UI for simplicity

Go to: <https://resources.azure.com/> and login.

Search for the Web App by name, find the (Microsoft.Web/Sites) link and click on it:

[<img loading="lazy" width="506" height="772" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/08/image_thumb-1.png" border="0" />](/assets/images/2020/08/image-1.png)

Ensure you select the Read/Write button on the top right and then the Edit button on the top left:

[<img loading="lazy" width="1094" height="281" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/08/image_thumb-2.png" border="0" />](/assets/images/2020/08/image-2.png)



find the cors object and add the capacitor://localhost entry.&nbsp; Ensure there is a comma after the existing entries if any and scroll back to the top and push the Patch button:

[<img loading="lazy" width="668" height="449" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/08/image_thumb-3.png" border="0" />](/assets/images/2020/08/image-3.png)

## How to test

You can use curl, Fiddler, Postman… just build the request and ensure it returns 200 and 1 in the body

Here is an example from Postman:

[<img loading="lazy" width="658" height="330" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/08/image_thumb-4.png" border="0" />](/assets/images/2020/08/image-4.png)