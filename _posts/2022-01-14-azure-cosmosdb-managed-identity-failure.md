**Quick info blog** - Customer code accessing Cosmos Db using the Azure Cosmos SDK showed failure in Application Insights: ManagedIdentityCredentials authentication failed. 

**Sample error:** _Message request to http://172.16.*.*:8081/msi/token?resource=https%3A%2F%2Fcosmos-name.documents.azure.com&api-version=2017-09-01%20application/json;%20charset=utf-8_ 

Along with the above error, we also observed execution timeouts in FunctionLogs logs table.

## Solution

Turns out the customer was using @azure/cosmos SDK earlier than v3.14.1.  This version of the SDK was creating an AAD token with every request which resulted in throttling and authentication failed.  **This was fixed with version 3.14.1.** see: 
[azure-sdk-for-js/CHANGELOG.md at main · Azure/azure-sdk-for-js](https://github.com/Azure/azure-sdk-for-js/blob/main/sdk/cosmosdb/cosmos/CHANGELOG.md#3141-2021-09-02)

Special thanks to my teammate for this content: Gilbert Appiah - Azure Rapid Response - Azure App Servivces!