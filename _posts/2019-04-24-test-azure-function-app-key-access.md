You can test the key that Azure Functions uses when communicating to it’s associated storage account.&nbsp; This is a great troubleshooting step if you get errors that the function is not accessible.



## 

# 

# Steps

Install Storage Explorer on your machine: <a href="https://azure.microsoft.com/en-us/features/storage-explorer/" target="_blank">https://azure.microsoft.com/en-us/features/storage-explorer/</a>

Open Azure Storage Explorer and choose the Plug Icon to create a new Connection.&nbsp;&nbsp; The option you want is: Use a storage account name and key



[<img loading="lazy" width="454" height="284" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/04/image_thumb.png" border="0" />](/assets/images/2019/04/image.png)

Copy the Key from your Function App application settings (note it will/can be in a couple of places…. Ensure it is identical in all).&nbsp; Ref: <a href="https://docs.microsoft.com/en-us/azure/azure-functions/functions-app-settings" target="_blank">https://docs.microsoft.com/en-us/azure/azure-functions/functions-app-settings</a>

[<img loading="lazy" width="656" height="384" title="clip_image001" style="margin: 0px; display: inline; background-image: none;" alt="clip_image001" src="/assets/images/2019/04/clip_image001_thumb.png" border="0" />](/assets/images/2019/04/clip_image001.png)

Use the AccountName and AccountKey values from the application settings you copied.

[<img loading="lazy" width="244" height="217" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/04/image_thumb-1.png" border="0" />](/assets/images/2019/04/image-1.png)

Hit the Next, then the Connect button.&nbsp;&nbsp; Then try and use that connection to browse down to the blob for that new connection:

[<img loading="lazy" width="352" height="227" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/04/image_thumb-2.png" border="0" />](/assets/images/2019/04/image-2.png)

Please drop me a note if you found this useful!