 

In this scenario, you want to provide your customer with a secured URL to download a file from Azure Storage.&nbsp; You can do this programmatically of course but another option is to use the Azure Storage Explorer to create a Shared Access Signature (SAS) for your customer.&nbsp; Then provide the URL necessary with the SAS so that they can download the resource securely over HTTPS.

It is important to note, that the SAS is the key into this file (or container) and like any key…&nbsp; You need to carefully consider how you use and/or distribute this information!

It is assumed you have an Azure Account and a basic knowledge of how to use your Azure Portal to access resources.&nbsp; You can do this walkthrough on Windows or Linux

# Walkthrough

Install Azure Storage Explorer &#8211; This page has the download link for Windows and Linux: [https://azure.microsoft.com/en-us/features/storage-explorer/](https://azure.microsoft.com/en-us/features/storage-explorer/ "https://azure.microsoft.com/en-us/features/storage-explorer/")

Open Azure Storage Explorer, and sign in using your Azure Account credentials.

Choose an existing Storage Account or create a new one and select this account (in my example I am using the existing ‘jeffs’ Storage Account).

Select the Storage Account you are using and click on the ‘Blob Containers’ node, Either choose an existing Blob Container or, create a new one by right clicking on the ‘Blob Containers’ node and choose ‘Create New’:

[<img loading="lazy" title="capture20171012085456787" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012085456787" src="/assets/images/2017/10/capture20171012085456787_thumb.png" width="454" height="402" />](/assets/images/2017/10/capture20171012085456787.png)

In the example below I selected an existing Storage Account called ‘jeffs’ and created a container called ‘filexfer’.

Ensure that the Container ‘Access policy’ is set to Private:

[<img loading="lazy" title="capture20171012130611184" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012130611184" src="/assets/images/2017/10/capture20171012130611184_thumb.png" width="879" height="350" />](/assets/images/2017/10/capture20171012130611184.png)

Now upload a file to the Blob Container.&nbsp; Simply click on the Blob container and choose ‘Upload Files…’:

[<img loading="lazy" title="capture20171012083926062" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012083926062" src="/assets/images/2017/10/capture20171012083926062_thumb.png" width="605" height="355" />](/assets/images/2017/10/capture20171012083926062.png)

Select the file from the ‘…’ button and keep the rest of the defaults and hit the upload button:

[<img loading="lazy" title="capture20171012090116252" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012090116252" src="/assets/images/2017/10/capture20171012090116252_thumb.png" width="387" height="263" />](/assets/images/2017/10/capture20171012090116252.png)

## Generate Shared Access Signature for the file

You now can generate a SAS.&nbsp; Right click on the file and select ‘Get Shared Access Signature…’ :

[<img loading="lazy" title="capture20171012090313213" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012090313213" src="/assets/images/2017/10/capture20171012090313213_thumb.png" width="346" height="377" />](/assets/images/2017/10/capture20171012090313213.png)

Set the Expiry time for the SAS for whatever you determine best suits your needs and set the permissions.&nbsp; In this case, I am setting it for two years and only giving Read permissions and hit the Create button:

[<img loading="lazy" title="capture20171012090756261" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012090756261" src="/assets/images/2017/10/capture20171012090756261_thumb.png" width="417" height="417" />](/assets/images/2017/10/capture20171012090756261.png)

(NOTE:&nbsp; If you app is writing multiple files to the container and you want to generate a SAS for then entire container (instead of one specific to this particular file) you can check the ‘Generate container-level… ‘ option here)

In the next screen simply copy and save the URL that was generated:

[<img loading="lazy" title="capture20171012091158436" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171012091158436" src="/assets/images/2017/10/capture20171012091158436_thumb.png" width="440" height="440" />](/assets/images/2017/10/capture20171012091158436.png)

Now you can provide the URL to your customer and they can use this to securely download the file you have provided in Azure Storage!

# Learn More

Let me know if this was useful to you!&nbsp; This only scratches the surface and I provided this since there was not a simple walkthrough to get you started.&nbsp; Make sure you understand the security implications of a long lifetime SAS like I showed here!&nbsp; Here is some more information for you to research:

Blob Storage: <a href="https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction" target="_blank">https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction</a> 

You can create storage, SAS tokens and upload files programmatically as well:

**Upload the file to storage using the key**. <a href="https://docs.microsoft.com/en-us/azure/storage/blobs/storage-dotnet-how-to-use-blobs" target="_blank">https://docs.microsoft.com/en-us/azure/storage/blobs/storage-dotnet-how-to-use-blobs</a> &#8211; relevant section for you is the ‘Upload a blob into a container’ 

**Using shared access signatures (SAS) &** 

**Retrieve the file from storage in an app (You do NOT want to give the customer your storage key)** 

<a href="https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1" target="_blank">https://docs.microsoft.com/en-us/azure/storage/common/storage-dotnet-shared-access-signature-part-1</a> 

**Getting Started with Shared Access Signatures (SAS)** 

<https://azure.microsoft.com/en-us/resources/samples/storage-dotnet-sas-getting-started/> 

**Get started with Storage Explorer (Preview)** 

[https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-manage-with-storage-explorer](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-manage-with-storage-explorer "https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-manage-with-storage-explorer")