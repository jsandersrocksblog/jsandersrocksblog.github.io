Azure App Services has a way to retrieve and analyze a memory dump of your app right from the portal.&nbsp; This is a quick reference on how to use this feature

# Steps

Go to you Web App in the Azure Portal and select the ‘Diagnose and solve problems’ pane and click on the ‘Diagnostic Tools’ section:

[<img loading="lazy" width="750" height="464" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb.png" border="0" />](/assets/images/2020/01/image.png)

In that pane select ‘Collect Memory Dump’

[<img loading="lazy" width="192" height="121" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-1.png" border="0" />](/assets/images/2020/01/image-1.png)

Ensure you read the ‘What you should know…’ section of this window.&nbsp; The wizard can walk you through creating a new storage account to store your dumps or, you can select an existing one here.&nbsp; Select the instance or instances you wish to get a dump for and ensure the mode is ‘Collect and Analyze Data’, then select the ‘Collect Memory Dump’ button and the dump collection and analysis will start:

[<img loading="lazy" width="694" height="620" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-2.png" border="0" />](/assets/images/2020/01/image-2.png)

It will collect and start analyzing the dumps:

[<img loading="lazy" width="642" height="169" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/01/image_thumb-3.png" border="0" />](/assets/images/2020/01/image-3.png)

In the case of a .NET Core application you really only care about the dump and mht file that do not have the w3wp.exe extension because in that case, the w3wp process simply is hosting .NET Core.