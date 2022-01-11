Code that was working on a machine with the 2.0 (3.5) version of the .NET framework all of a sudden failed when this was flipped to the 4.0 version of the framework.&nbsp; The end error was “The request was aborted, cannot create SSL/TLS secure channel” and “AcquireCredentialsHandle() failed with error 0X8009030D”.&nbsp; This code imported a client certificate and key and was not using a client certificate stored on the machine.&nbsp; I enabled CAPI logging and took traces of the failed and successful cases to compare.&nbsp; Enabling CAPI logging: 

<http://www.microsoft.com/downloads/en/details.aspx?FamilyID=FE8EB7EA-68DA-4331-9D38-BDBF9FA2C266&displaylang=en>

You could see in the trace the only real difference with the client certificate was that it did not have a KeyContainerName: containerName=&#8221;&#8221; vs the successful which did: containerName=&#8221;CLR{6FB09BC6-3199-49E0-83F4-8941879D4300}&#8221;

Debugging this you could clearly see the 4.0 code did not have this set when you inspected the RSACryptoServiceProvider object that was being created.&nbsp; You could see this member was null: CspKeyContainerInfo.KeyContainerName.&nbsp; Also this member was not set in the 4.0 version but was set in the 2.0 version: CspKeyContainerInfo.UniqueKeyContainerName.

To fix this, simply create the container name and pass it into the constructor of the RSACryptoServiceProvider:

> var cspPrms = new CspParameters();  
> cspPrms.KeyContainerName = &#8220;TempContainerName&#8221;;  
> var rsa = new RSACryptoServiceProvider(cspPrms);

Please drop me a note if you found this useful!