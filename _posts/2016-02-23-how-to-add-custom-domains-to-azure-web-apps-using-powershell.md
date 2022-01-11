Just another quicky post:

If you need to add a custom domain to an Azure Web App you can use Powershell.&#160; Powershell does the same verification that the UI does and is just another way to accomplish setting the custom domain or domains.

Note that you don’t set, nor can you change the default azurewebsites.net domain.

Here is an example.&#160; Lets say I have an azure webapp: jsandersprod.azurewebsite.net and I want to add the [www.jsanders.com](http://www.jsanders.com) and dev.jsanders.com sub domains to it.&#160; Assuming I have set this up already with my domain provider here is how I do it in powershell:

Get-AzureWebsite -Name "jsandersprod" | Set-AzureWebsite -HostNames @("dev.jsanders.com",[www.jsanders.com](http://www.jsanders.com))

That is all there is to it!

Please drop me a note if you found this useful!