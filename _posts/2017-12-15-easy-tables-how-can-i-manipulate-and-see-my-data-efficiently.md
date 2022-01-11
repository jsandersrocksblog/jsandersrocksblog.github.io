The Easy tables feature of Node.js backend Azure Mobile Apps is a great way to do your initial development.&nbsp; Once you get a few hundred rows of data however the browser based interface simply does not work well.&nbsp; This is when you should move to an alternative.&nbsp; This also allows you to run SQL queries and filters to narrow down the data you want to see or manipulate.&nbsp; This guide is for the option when you are using Azure SQL for your backend database.

# 

# Gather data

You need to know the database server and database name for your Azure Mobile App.&nbsp; You can get this from your connection string in your application:

[<img loading="lazy" title="capture20171215093917838" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171215093917838" src="/assets/images/2017/12/capture20171215093917838_thumb.png" width="225" height="152" />](/assets/images/2017/12/capture20171215093917838.png)&nbsp;[<img loading="lazy" title="capture20171215093931641" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171215093931641" src="/assets/images/2017/12/capture20171215093931641_thumb.png" width="201" height="188" />](/assets/images/2017/12/capture20171215093931641.png)

[<img loading="lazy" title="dataconnectiondetails" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="dataconnectiondetails" src="/assets/images/2017/12/dataconnectiondetails_thumb.png" width="421" height="200" />](/assets/images/2017/12/dataconnectiondetails.png)

Data Source (after tcp) is the database server and Initial Catalog is the database on the database server.&nbsp; ID and Password are self explanatory:

    Data Source=tcp:xxxxxxxx.database.windows.net,1433;Initial Catalog=xxxxx;User ID=xxxxxx;Password=xxxxxx
    

# Options

## 

## Azure Portal

This is the easiest by far and quite powerful.&nbsp; Simply find your Azure SQL Database in the Azure Portal and select it:

[<img loading="lazy" title="capture20171215100425320" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215100425320" src="/assets/images/2017/12/capture20171215100425320_thumb.png" width="254" height="504" />](/assets/images/2017/12/capture20171215100425320.png)

Click on Data explorer, and Login, then click on Edit Data:

[<img loading="lazy" title="EditDataOption" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="EditDataOption" src="/assets/images/2017/12/EditDataOption_thumb.png" width="740" height="268" />](/assets/images/2017/12/EditDataOption.png)

To narrow you returned data you can execute T-SQL commands by creating a New Query:

[<img loading="lazy" title="capture20171215101524858" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215101524858" src="/assets/images/2017/12/capture20171215101524858_thumb.png" width="843" height="367" />](/assets/images/2017/12/capture20171215101524858.png)

## Visual Studio

This is my next favorite option.&nbsp; All you need is Visual Studio installed, and the community edition is free!&nbsp; If you don’t already have it installed, install the full community edition of Visual Studio (at the time of this blog it is Visual Studio 2017 community edition: [https://www.visualstudio.com/vs/community/](https://www.visualstudio.com/vs/community/ "https://www.visualstudio.com/vs/community/")&nbsp;

Simply find your Azure SQL Database in the Azure Portal as before and in the Overview select the Connect with… dropdown and select Visual Studio:

[<img loading="lazy" title="capture20171215101919098" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215101919098" src="/assets/images/2017/12/capture20171215101919098_thumb.png" width="774" height="165" />](/assets/images/2017/12/capture20171215101919098.png)

**<font style="background-color: #ffff00">Make sure you ‘Configure your firewall’ and ‘Add client IP’ and ‘Save’ or you will not be able to connect to Azure SQL:</font>**

[<img loading="lazy" title="VisualStudioconnect2" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="VisualStudioconnect2" src="/assets/images/2017/12/VisualStudioconnect2_thumb.png" width="789" height="471" />](/assets/images/2017/12/VisualStudioconnect2.png)

And then just click ‘Open in Visual Studio’ and login (Username and Password you already found in you connection string if you don’t remember it):

[<img loading="lazy" title="login" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="login" src="/assets/images/2017/12/login_thumb.png" width="384" height="467" />](/assets/images/2017/12/login.png)

Then you can go to the View Data menu or apply filters:

[<img loading="lazy" title="capture20171215103351905" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215103351905" src="/assets/images/2017/12/capture20171215103351905_thumb.png" width="416" height="363" />](/assets/images/2017/12/capture20171215103351905.png)

[<img loading="lazy" title="capture20171215103330382" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215103330382" src="/assets/images/2017/12/capture20171215103330382_thumb.png" width="544" height="162" />](/assets/images/2017/12/capture20171215103330382.png)

[<img loading="lazy" title="capture20171215103708122" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215103708122" src="/assets/images/2017/12/capture20171215103708122_thumb.png" width="702" height="451" />](/assets/images/2017/12/capture20171215103708122.png)

## Microsoft SQL Server Management Studio

This option is the best if you are used to doing powerful things in this robust interface.&nbsp; Ensure you set the firewall option for your client IP as above, and simply connect using that tool using the database server name, database, username and password:

## 

[<img loading="lazy" title="capture20171215104056770" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171215104056770" src="/assets/images/2017/12/capture20171215104056770_thumb.png" width="457" height="327" />](/assets/images/2017/12/capture20171215104056770.png)

&nbsp;

# 

# Conclusion

I gave you my favorite options (in order) of how to see your database information for your Mobile App (stored in Azure SQL).

Drop me a note if you found this useful!