---
id: 5512
title: Create a fault tolerant app Using Azure App Services and Azure SQL
date: 2019-06-24T10:47:43-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5512
permalink: /2019/06/24/create-a-fault-tolerant-app-using-azure-app-services-and-azure-sql/
categories:
  - Uncategorized
---
 

Azure guarantees 99.95% uptime or better, but sometimes your application or database misbehaves due to something you have done (written bad code) or in the rare event there is a problem in a region.&nbsp; There was not a good end to end sample of setting up an Azure App Service that was deployed to multiple regions to be responsive and that utilized auto failover if a resource or data center went down so I created this one!&nbsp; This will illustrate how you can quickly and easily lay the foundation for a Geo-Distributed application in Azure built on Azure App Service, Azure Traffic Manger and Azure SQL.

# Architecture

This sample is an ASP.Net application that reads and writes to a SQL Database.&nbsp; Azure Traffic manager will allow us to serve the application from two regions and it will pick the region closest to the client for better performance.&nbsp; If one region fails, then traffic manager will route only to the region that is healthy providing failover.&nbsp; Similarly, we will have read and write operations to the SQL Database handled by a SQL Failover group.&nbsp; If a SQL Database in one region is not available due to a disaster in a certain region, the requests will go to the failover database.

# Prerequisite

You need to have an Azure Subscription.&nbsp; You can get a trial subscription here: <a href="https://azure.microsoft.com/free/" target="_blank" rel="noopener noreferrer">https://azure.microsoft.com/free/</a>

# Walkthrough

## Create a new Resource Group

All of the resources we will use will be logically grouped in a Resource Group to allow us to easily identify the Azure Resources associated with this walkthrough.&nbsp; This will also allow us to clean up all the resources easily when done.&nbsp; The resources you will create are expensive and you will want to delete these after this exercise if you do not intend to use this setup in a real environment!

To do this, navigate to the Azure Portal and login using your subscription.&nbsp; Then **click on the green + icon** in the top left of the screen and type ‘Resource Group’ in the search box:

[<img loading="lazy" width="207" height="168" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb.png" border="0" />](/assets/images/2019/06/image.png)

Press Enter on your keyboard and **click the ‘Create’ Button** in the next screen. 

[<img loading="lazy" width="412" height="271" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-1.png" border="0" />](/assets/images/2019/06/image-1.png)

If you have multiple subscriptions pick the appropriate one, Name the group ‘FailoverExample’ and create it in the (US) East US region.&nbsp; **Click the ‘Review + Create’** button:

[<img loading="lazy" width="337" height="562" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-2.png" border="0" />](/assets/images/2019/06/image-2.png)

**Click the ‘Create’ button** in the next screen and quickly the Resource group will be created!

You can open the resource group by **clicking the notification (Bell) icon** on the right and **choose ‘Go to resource group’**

[<img loading="lazy" width="202" height="244" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-3.png" border="0" />](/assets/images/2019/06/image-3.png)

At this point you will have no resources:

[<img loading="lazy" width="164" height="166" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-4.png" border="0" />](/assets/images/2019/06/image-4.png)

## Create SQL Database

Now create the Azure SQL resource we will need in the Resource group we are viewing (and just created).&nbsp; **Click on the ‘+ Add’** in this view as pictured below:

[<img loading="lazy" width="452" height="247" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-5.png" border="0" />](/assets/images/2019/06/image-5.png)

**Type ‘SQL Database’ in the search box, press you enter key and select ‘SQL Database’**

[<img loading="lazy" width="244" height="184" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-6.png" border="0" />](/assets/images/2019/06/image-6.png)

**Click the ‘Create’ button** in the next screen and start filling in the information below.&nbsp; Ensure you select the ‘FailoverExample’ Resource group we created and set the Database name to ‘eastdb’:

[<img loading="lazy" width="392" height="576" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-7.png" border="0" />](/assets/images/2019/06/image-7.png)

For the Server field **click ‘Create new’** and give the server a unique Server name, an admin login name and password, and create it in the East US location.&nbsp; <font style="background-color: rgb(255, 255, 0);">Make sure you save or remember the Server admin login and password.</font>&nbsp; Then **click the ‘Select’** button at the bottom to select your changes:

[<img loading="lazy" width="303" height="439" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-8.png" border="0" />](/assets/images/2019/06/image-8.png)

Accept the defaults for the rest of the values and **click the ‘Next : Additional settings >’ button**.&nbsp; You don’t need Advanced Data Security so **select ‘Not now’**.&nbsp; Then **click the ‘Review + create’ button and then click the ‘Create’ button in the next screen**.&nbsp; This will start the deployment of the database (which will take some time).

Once completed you can see the SQL Database and Server in your Resource group:

[<img loading="lazy" width="1000" height="402" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-9.png" border="0" />](/assets/images/2019/06/image-9.png)

## Add a Failover Group for your SQL database

**Click on the SQL server** name to navigate to that server.  **Click on Failover groups** and **click the ‘+ Add group’ icon**:

[<img loading="lazy" width="572" height="326" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-10.png" border="0" />](/assets/images/2019/06/image-10.png)

Create a new failover group and Create a new Secondary server in a different region (I am using South Central).&nbsp; <font style="background-color: rgb(255, 255, 0);">Ensure the Username and password are the same as the one you used for your first database server</font>!

[<img loading="lazy" width="1041" height="509" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-11.png" border="0" />](/assets/images/2019/06/image-11.png)

**Click the ‘Select’ button** and then **click ‘Select databases to add’** to select the database we created earlier (eastdb for me):

[<img loading="lazy" width="663" height="419" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-12.png" border="0" />](/assets/images/2019/06/image-12.png)

**Click ‘Select’** and then in the next screen **click ‘Create’** to start the failover group for your database (this will take some time).

## Create Azure App Services

You will create a web app in two different regions.&nbsp; We will use East US and South Central US regions just like our databases for performance reasons.

Open the Azure Portal and **click on the green ‘+’ icon** and **type Web App** in the search bar, then **click on the Web App text** (not the Quickstart tutorial):

[<img loading="lazy" width="404" height="301" title="NewWebApp" style="display: inline; background-image: none;" alt="NewWebApp" src="/assets/images/2019/06/NewWebApp_thumb.jpg" border="0" />](/assets/images/2019/06/NewWebApp.jpg)

**Select our Resource group called ‘FailoverExample’** and enter a unique webapp name (I suggest your alias appended with ‘eastapp’) for example:&nbsp; jsandersfailovereastapp

Choose the runtime stack and Region as shown below and create a new App Service plan with Sku and size Standard S1:

[<img loading="lazy" width="464" height="879" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-13.png" border="0" />](/assets/images/2019/06/image-13.png)

**Click on the next tab ‘Monitoring’** and **select ‘No’** for application insights (we will not be using it) and then **click on ‘Review and create’** and in the next screen **click on the ‘Create’ button** to create your web app

Now create a second web app in another region (I suggest South Central US) in the same Resource group (FailoverExample) like you did above.&nbsp; See the example below:

[<img loading="lazy" width="469" height="789" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-14.png" border="0" />](/assets/images/2019/06/image-14.png)

## 

## Configure App Settings for database connections

The code we will deploy to the Azure Web apps will need an application connection string added do the Configuration in the portal so that it can connect to the database.&nbsp; The connection string we will set is ‘WriteDbConn’

We need to get the connection string from the Database we will use and save it to an editor like notepad.&nbsp; Go to our new Resource group you created at the beginning and click on the database server you created initially.&nbsp; In my example you will see the highlighted SQL server is the one I created first (jsanderseastserver):

[<img loading="lazy" width="669" height="364" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-15.png" border="0" />](/assets/images/2019/06/image-15.png)

Click on Failover groups and then your failover group you created above to get to the configuration details page that looks like this:

[<img loading="lazy" width="437" height="863" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-16.png" border="0" />](/assets/images/2019/06/image-16.png)

**Copy the Read/write listener endpoint to your editor.**

Now you need to navigate to the database and get the connection string.&nbsp; Go back to the resource group and **click on the SQL Database you first created** (eastdb is mine).&nbsp; **Click on the Connection strings section** to see the ADO.NET connection string.

[<img loading="lazy" width="558" height="463" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-17.png" border="0" />](/assets/images/2019/06/image-17.png)

**Click on the Copy icon** on the far right side and paste this string into your text editor:

[<img loading="lazy" width="244" height="203" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-18.png" border="0" />](/assets/images/2019/06/image-18.png)

We need to edit the connection string for the application.&nbsp; You will need to **replace the database tcp: value** with the failover group information,&nbsp; **{your_username}** text with the Server admin login you saved when you created the server and the **{your_password}** text with your password (no { } characters) and you will use that for the WriteDbConn setting value.&nbsp; Here is an example:

Server=tcp:<font style="background-color: rgb(255, 255, 0);">jsandersfailover.database.windows.net</font>,1433;Initial Catalog=eastdb;Persist Security Info=False;User ID=<font style="background-color: rgb(255, 255, 0);">jsanders</font>;Password=<font style="background-color: rgb(255, 255, 0);">awesome_password</font>;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;

Go back into the resource group and navigate to the first web app in the East US region you created and go to the Configuration section and **click on the ‘+ New connection string’** section:

[<img loading="lazy" width="505" height="546" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-19.png" border="0" />](/assets/images/2019/06/image-19.png)

And add a connection using the Name ‘’WriteDbConn’, Value of the Connection string you just modified above and choose the type ‘SQLAzure’ and **click update to save**:

[<img loading="lazy" width="527" height="220" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/07/image_thumb.png" border="0" />](/assets/images/2019/07/image.png)

Do this for your second app in the Central US region since both apps need to write to the Primary Database (not the backup).

## Deploy code to Azure Web Apps

Now we will deploy a test app through the SCM site for each Web App using this zip file: <a title="https://github.com/jsandersrocks/FailoverSample/raw/master/wwwroot.zip" href="https://github.com/jsandersrocks/FailoverSample/raw/master/wwwroot.zip" target="_blank" rel="noopener noreferrer">https://github.com/jsandersrocks/FailoverSample/raw/master/wwwroot.zip</a> Download the zip file local in you downloads directory.

Go to the Resource group you just created by clicking on the resource group icon and then clicking on the new resource group you created for this walkthrough.

**Click on the first App Service** you created, scroll down to Advanced Tools and **click on the ‘Go’ link**: (Expert tip:&nbsp; The Kudu interface is simply https://yourwebappname**.scm**.azurewebsites.net)

[<img loading="lazy" width="339" height="191" title="Kudu" style="display: inline; background-image: none;" alt="Kudu" src="/assets/images/2019/06/Kudu_thumb.jpg" border="0" />](/assets/images/2019/06/Kudu.jpg)

This is the Kudu console where you can drag and drop the code for your web app.

**Click on ‘Debug Console’ and choose ‘CMD’**

[<img loading="lazy" width="244" height="71" title="KuduDebugConsole" style="display: inline; background-image: none;" alt="KuduDebugConsole" src="/assets/images/2019/06/KuduDebugConsole_thumb.jpg" border="0" />](/assets/images/2019/06/KuduDebugConsole.jpg)

**Click on the text ‘site’ then ‘wwwroot’** in the tree view to navigate to the wwwroot folder as shown:

[<img loading="lazy" width="465" height="500" title="wwwroot" style="display: inline; background-image: none;" alt="wwwroot" src="/assets/images/2019/06/wwwroot_thumb.jpg" border="0" />](/assets/images/2019/06/wwwroot.jpg)

Drag and drop the zip file from above onto the folder as shown:

[<img loading="lazy" width="744" height="322" title="Drag" style="display: inline; background-image: none;" alt="Drag" src="/assets/images/2019/06/Drag_thumb.jpg" border="0" />](/assets/images/2019/06/Drag.jpg)

<font style="background-color: rgb(255, 255, 0);">Do these same steps to deploy your code to your 2nd Web app!</font>

**Test both apps.**&nbsp; When you run the Web App it creates the appropriate table in the database (Entity Framework provides this magic for us).&nbsp; You should be able to insert records and refresh the display to see items in the listbox in both applications (east and central) and you should see the same data when you refresh the view.

## Create and configure Azure Traffic Manager

Now we will use Azure Traffic Manager to show how it can be used to route traffic to healthy instances of your applications, route to the closest region for better client performance and provide failover.

Again from your Resource group **click the ‘+’ icon** and this time **type ‘Traffic Manager profile’** and then **press enter**.&nbsp; Then select the Azure Traffic Manager profile resource and **click the Create button**:

[<img loading="lazy" width="204" height="167" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-21.png" border="0" />](/assets/images/2019/06/image-21.png)

Fill in a unique name and choose the default ‘Performance’ Routing method.&nbsp; Ensure your Subscription and Resource group are the same as the rest of your work and **click the ‘Create’ button:**

[<img loading="lazy" width="318" height="319" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-22.png" border="0" />](/assets/images/2019/06/image-22.png)

FYI:&nbsp; Performance routing is only one mode (the one we will use) <a href="https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method</a>

Once this is created, go to that resource and **click on ‘Endpoints’** to add your two Web Apps as endpoints:

[<img loading="lazy" width="282" height="472" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-23.png" border="0" />](/assets/images/2019/06/image-23.png)

Then **set the type to ‘Azure endpoint’**, give the endpoint a name, set the ‘Target resource type’ to ‘App Service’ and select the first Web App you created and **click the ‘OK’ button**:

[<img loading="lazy" width="282" height="394" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-24.png" border="0" />](/assets/images/2019/06/image-24.png)

Do the same for the 2nd app in the other region and when complete you should have two endpoints listed:

[<img loading="lazy" width="424" height="282" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-25.png" border="0" />](/assets/images/2019/06/image-25.png)

To ensure Traffic Manager is serving your requests correctly retrieve the Traffic Manager URL and use it in the browser to access your app.&nbsp; The **DNS name** you will use is available in the Overview of the Traffic Manager profile:

[<img loading="lazy" width="745" height="285" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-26.png" border="0" />](/assets/images/2019/06/image-26.png)

Since we are using ‘Performance’ routing you should be directed to the nearest healthy endpoint.&nbsp;&nbsp; The app you create will tell which server you are hitting at the bottom of the listbox:

[<img loading="lazy" width="809" height="467" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-27.png" border="0" />](/assets/images/2019/06/image-27.png)

## 

## Completed Architecture

This is what your app architecture looks like now:

[<img loading="lazy" width="651" height="427" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-32.png" border="0" />](/assets/images/2019/06/image-32.png)

Traffic manager will route Users to the closest of the two regions (as long as they are both working).&nbsp; Hidden are the details of how the Database Failover group will provide a connection to the primary database via DNS just like Traffic manager does for the web app.



## Test Traffic Manger Failover to you app

It is important to note that Traffic Manager is a DNS service.&nbsp; Traffic Manger will serve up the IP address of the closest endpoint and hand it back to the Client computer.&nbsp; Once it does that, Traffic Manger has no further involvement for that session unless the DNS TTL (Time To Live) value is exceeded. 

[<img loading="lazy" width="662" height="487" title="Traffic Manager Performance Routing" style="display: inline; background-image: none;" alt="Traffic Manager Performance Routing" src="/assets/images/2019/06/Traffic-Manager-Performance-Routing_thumb.jpg" border="0" />](/assets/images/2019/06/Traffic-Manager-Performance-Routing.jpg)

You can change the DNS TTL value in the Configuration section of Traffic Manager.&nbsp; A description of this is also available by hovering your mouse over the information icon:

[<img loading="lazy" width="539" height="285" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-28.png" border="0" />](/assets/images/2019/06/image-28.png)

The TTL determines how long a client will use the cached IP address and until the TTL expires a client will attempt to use the old IP address.&nbsp; See: <a href="https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-how-it-works" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-how-it-works</a>

The lower the TTL setting, the increased frequency a client computer needs to poll for DNS resolution again so choose this value carefully if you decrease it, as this may have performance impact trying to resolve your site.

Ref: <a href="https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-monitoring" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-monitoring</a>

“Because Traffic Manager works at the DNS level, it cannot influence existing connections to any endpoint. When it directs traffic between endpoints (either by changed profile settings, or during failover or failback), Traffic Manager directs new connections to available endpoints. However, other endpoints might continue to receive traffic via existing connections until those sessions are terminated. To enable traffic to drain from existing connections, applications should limit the session duration used with each endpoint.”

## Test

Stop the app in region you are currently hitting (the application page shows name of web app being used).&nbsp; For my example I will go to my app in the east region and **select the ‘Stop’ icon**:

[<img loading="lazy" width="550" height="200" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-29.png" border="0" />](/assets/images/2019/06/image-29.png)

You have removed the application closest to you and Traffic Manager will redirect the DNS to the working application:

[<img loading="lazy" width="758" height="482" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-33.png" border="0" />](/assets/images/2019/06/image-33.png)

After the TTL period you will see that you are redirected to the other region.&nbsp; Type in your Traffic Manager DNS name again and verify you are going to the geo-region furthest from you:

[<img loading="lazy" width="816" height="484" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-30.png" border="0" />](/assets/images/2019/06/image-30.png)

If you do not want to wait for the TTL to redirect traffic, then you can open an administrative command prompt on Windows and type ipconfig /flushdns, **Note:** if you are using Chrome, it caches DNS entries internally and does not use the client computer cache: ipconfig /displaydns will show no entries!&nbsp; Open an incognito web browser to get around this or go to <chrome://net-internals/#sockets> and **’Close idle sockets’** and **‘Flush socket pools’** then <chrome://net-internals/#dns> and **‘Clear host cache’**

Start the Web App you had stopped previously to ensure it is working again.

## Simulate Azure SQL Db failure

Go to your Azure SQL Server and go to the Failover group again.

Click on the Forced Failover icon:

[<img loading="lazy" width="783" height="348" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-31.png" border="0" />](/assets/images/2019/06/image-31.png)

Once complete you will notice the primary database has changed to be the other region and this works seamless with your application.&nbsp; That is because the failover group points to the DNS of the failover group and not the actual Database:

[<img loading="lazy" width="621" height="441" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/06/image_thumb-34.png" border="0" />](/assets/images/2019/06/image-34.png)



There are further implications to failover that are covered in the Advance Topics section links below

# 

# Delete the resource Group

Now that you have finished this exercise you will want to delete the resource group you created in the beginning.&nbsp; This will delete the resources you created in this walkthrough and prevent the costs from mounting.&nbsp; Another option would be to downgrade the sku you are using for the individual resources to reduce the cost.&nbsp; Simply go to your resource group and select the delete icon at the top!

[<img loading="lazy" width="881" height="168" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/07/image_thumb-1.png" border="0" />](/assets/images/2019/07/image-1.png)

# Summary

You were able to quickly build and demonstrate how failover mechanisms can be used in Azure.&nbsp; This is only touching the surface for this topic but I trust this has given you enough information to demonstrate and get started with using Azure App Service, Traffic Manager, SQL Db and Failover groups!

## 

## More information and Advanced Topics

DNS Resolver:&nbsp; <a href="https://www.digwebinterface.com/?hostnames=jsanders.trafficmanager.net&type=&ns=resolver&useresolver=8.8.4.4&nameservers=" target="_blank" rel="noopener noreferrer">https://www.digwebinterface.com</a>[/](https://www.digwebinterface.com/?hostnames=jsanders.trafficmanager.net&type=&ns=resolver&useresolver=8.8.4.4&nameservers=)

Standby architecture and other considerations:&nbsp; <a href="https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/app-service-web-app/multi-region" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/app-service-web-app/multi-region</a>

SQL Security (My sample code needs dbmanager, read and write): <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins>

SQL Azure failover groups: <a href="https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auto-failover-group" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auto-failover-group</a>

SQL HA: <a href="https://docs.microsoft.com/en-us/azure/sql-database/sql-database-high-availability" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/sql-database/sql-database-high-availability</a>

Traffic Manager:&nbsp; <a href="https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-monitoring" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-monitoring</a>&nbsp; <a href="https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-how-it-works" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/traffic-manager/traffic-manager-how-it-works</a>