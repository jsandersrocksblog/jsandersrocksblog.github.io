You could use the Azure CLI to create Azure Mobile Service tables for the node.js backend.&nbsp; You can no longer do this but there is a much easier solution.&nbsp; You can simply drop a .json file in the ‘Tables’ directory and when the app starts it will create the table in the database and make it accessible to the /tables/ route in your Azure Mobile App.&nbsp; This only works for the node.js backend.

## Scenario

You want to be able to add a table to your Azure Mobile App through scripting or automation.&nbsp; You are using the node SDK for Azure Mobile Apps.&nbsp; In this example I am adding a table called ‘testdrop’.

## Setup

Start with the quickstart code that gets generated for you when you go through the portal and choose the quickstart option and node.js backend.

## Details

The node SDK quickstart has the following directory structure:

[<img loading="lazy" title="capture20160930094545240" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20160930094545240" src="/assets/images/2016/09/capture20160930094545240_thumb.png" width="170" height="323" />](/assets/images/2016/09/capture20160930094545240.png)

TIP:&nbsp; You can view your app files using the App Service Editor, available in the Azure Portal or by typing https://<NAMEofYourMobileAppHere>.scm.azurewebsites.net/dev.

If you open the tables directory you will see some .json and .js files that correspond to each table you have defined so far in your mobile app:

[<img loading="lazy" title="capture20160930095254434" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20160930095254434" src="/assets/images/2016/09/capture20160930095254434_thumb.png" width="169" height="232" />](/assets/images/2016/09/capture20160930095254434.png)

The .json files define the table attributes like columns, dynamic schema and permissions.&nbsp; The .js files define the code (if any) used when accessing the table Insert, Read, Update, Undelete or Delete functions (open them and check them out).

In this example I want to add a table called ‘testdrop’ to my Azure Mobile App with the following columns:

<pre class="code"><span style="color: #2e75b6">"columns"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"userid"</span><span style="color: black">: </span><span style="color: #a31515">"string"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"text"</span><span style="color: black">: </span><span style="color: #a31515">"string"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"complete"</span><span style="color: black">: </span><span style="color: #a31515">"boolean"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"due"</span><span style="color: black">: </span><span style="color: #a31515">"datetime"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"alert"</span><span style="color: black">: </span><span style="color: #a31515">"number"
  </span><span style="color: black">},</span></pre>

I also want to turn off dynamic schema and turn on soft delete and I do not want to do any special processing on the data.

All I need to do is to create a file called ‘testdrop.json’ and put it in the ‘Tables’ directory.&nbsp; When the Mobile App runs (if you are using the quickstart the new file will trigger an app restart) the new table will be created for me and be accessible to my Azure Mobile App clients.

Sample json file contents:

<pre class="code"><span style="color: black">{
  </span><span style="color: #2e75b6">"columns"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"userid"</span><span style="color: black">: </span><span style="color: #a31515">"string"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"text"</span><span style="color: black">: </span><span style="color: #a31515">"string"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"complete"</span><span style="color: black">: </span><span style="color: #a31515">"boolean"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"due"</span><span style="color: black">: </span><span style="color: #a31515">"datetime"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"alert"</span><span style="color: black">: </span><span style="color: #a31515">"number"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"dynamicSchema"</span><span style="color: black">: </span><span style="color: blue">false</span><span style="color: black">,
  </span><span style="color: #2e75b6">"autoIncrement"</span><span style="color: black">: </span><span style="color: blue">false</span><span style="color: black">,
  </span><span style="color: #2e75b6">"softDelete"</span><span style="color: black">: </span><span style="color: blue">true</span><span style="color: black">,
  </span><span style="color: #2e75b6">"read"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"access"</span><span style="color: black">: </span><span style="color: #a31515">"anonymous"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"insert"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"access"</span><span style="color: black">: </span><span style="color: #a31515">"anonymous"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"update"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"access"</span><span style="color: black">: </span><span style="color: #a31515">"anonymous"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"delete"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"access"</span><span style="color: black">: </span><span style="color: #a31515">"anonymous"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"undelete"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"access"</span><span style="color: black">: </span><span style="color: #a31515">"anonymous"
  </span><span style="color: black">}
}</span></pre>

&nbsp;

Once you have this file then you need to get it into the Tables directory of your app.&nbsp; If you are scripting this through automation simply use FTP to transfer this file to your Azure Mobile App:&nbsp; [https://github.com/projectkudu/kudu/wiki/Accessing-files-via-ftp](https://github.com/projectkudu/kudu/wiki/Accessing-files-via-ftp "https://github.com/projectkudu/kudu/wiki/Accessing-files-via-ftp")

If you are not scripting you can create the file in the App Service Editor or at the Kudu command prompt or drag and drop the file into the directory using Kudu Console:&nbsp; [https://github.com/projectkudu/kudu/wiki/Kudu-console](https://github.com/projectkudu/kudu/wiki/Kudu-console "https://github.com/projectkudu/kudu/wiki/Kudu-console")

## More info

You can also add the testdrop.js file and add appropriate code for your solution if you want to do something to the data that is not just standard CRUD operations.&nbsp; 

You can define the table in your app.js file as well:&nbsp; mobileApp.tables.add(&#8216;TodoItem&#8217;); // Create a table for &#8216;TodoItem&#8217; with default settings&nbsp; (see: [https://azure.github.io/azure-mobile-apps-node/](https://azure.github.io/azure-mobile-apps-node/ "https://azure.github.io/azure-mobile-apps-node/") &#8211; [https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/ "https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/") )

You can define the table schema in the .js files as well with syntax like this:&nbsp; [https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/ "https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/") see: <a href="https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-node-backend-how-to-use-server-sdk/#howto-staticschema" name="howto-staticschema"></a>How to: Define tables using a static schema

&nbsp;

## 

## 

## Conclusion

There are many different ways to add tables to the Node SDK based backend.&nbsp; This super simple method may help you out in your solution.&nbsp; If so drop a comment letting me know how this worked for you!