 

Kudu is the .SCM interface for Azure App Services.&nbsp; If you are running more than one instance of Azure App Services (for instance you have scaled out to 4 instances) and you need to get to the Kudu console to do something like kill a process, profile an instance or get a dump of a particular instance… you can use this technique.&nbsp; This technique does not rely on ARRAffinity being set for the Application because that setting does not affect the Kudu site.&nbsp; 

# Steps (with Instance Detective Extension)

**Note that ASE is a special case** and the Instance Detective Extension will not work.&nbsp; You can use a powershell command to get the instances:&nbsp; Get-AzureRmResource -ResourceGroupName <RG name>-ResourceType Microsoft.Web/sites/instances -ResourceName &#8220;<App Name>&#8221; -ApiVersion 2016-08-01&nbsp; 

In this example, I have a particular instance of my site (jsandersscale) that is problematic and I logged an error that point to Azure Instance ID 92294a.&nbsp; I will use Chrome to ensure I am on the correct instance (1 of 4 allocated for this site) and profile that instance.

  1. **Download Publish Profile  
** a.&nbsp; From the Azure Portal, navigate to the Overview section of your app and download the publish portal from there by selecting ‘Get publish profile’ (make a note of where it downloads to so you can find it later:  
    [<img loading="lazy" width="514" height="106" title="capture20180227101743150" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227101743150" src="/assets/images/2018/02/capture20180227101743150_thumb.png" border="0" />](/assets/images/2018/02/capture20180227101743150.png)
<!--EndFragment-->

  2. **Install Instance Explorer**&nbsp;&nbsp;&nbsp;  
    a. Open you site’s Kudu page (https://<yourappname>.scm.azurewebsites.net) and select the ‘Site extensions’ section.&nbsp; Click on the ‘Gallery’ tab then enter ‘Instance Detective’ in the search box and click on the ‘Search’ button.</p> 
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [<img loading="lazy" width="536" height="243" title="capture20180227101021493" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227101021493" src="/assets/images/2018/02/capture20180227101021493_thumb.png" border="0" />](/assets/images/2018/02/capture20180227101021493.png)  
    b. Click the ‘+’ icon to install the extension.&nbsp; When it is done installing it tells you to ‘Restart Site’ so hit the ‘Restart Site’ button so you can use this:  
    [<img loading="lazy" width="383" height="167" title="capture20180227095408213" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227095408213" src="/assets/images/2018/02/capture20180227095408213_thumb.png" border="0" />](/assets/images/2018/02/capture20180227095408213.png)  
    c.&nbsp; From this (or the Installed tab) you can hit the Run Icon to start the extension.&nbsp; The first time you run it, you need to supply the Publish Profile as pictured below.  
    [<img loading="lazy" width="294" height="380" title="capture20180227095457337" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227095457337" src="/assets/images/2018/02/capture20180227095457337_thumb.png" border="0" />](/assets/images/2018/02/capture20180227095457337.png)  
    d.&nbsp; Press the ‘Upload Publish Profile’ button and navigate to the publish profile you downloaded in step 1.

  3. **Use the Extension!  
** Now the extension is loaded and you can connect to and perform various operations on the individual instances:  
    [<img loading="lazy" width="315" height="283" title="capture20180227095533576" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227095533576" src="/assets/images/2018/02/capture20180227095533576_thumb.png" border="0" />](/assets/images/2018/02/capture20180227095533576.png)</p> 
    [<img loading="lazy" width="286" height="170" title="capture20180227095544621" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227095544621" src="/assets/images/2018/02/capture20180227095544621_thumb.png" border="0" />](/assets/images/2018/02/capture20180227095544621.png)
    
    [<img loading="lazy" width="707" height="364" title="capture20180227102322857" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227102322857" src="/assets/images/2018/02/capture20180227102322857_thumb.png" border="0" />](/assets/images/2018/02/capture20180227102322857.png) 

  4. **When finished you can uninstall the Extension  
** Simply go back to the Installed Site extensions section and click on the ‘x’ icon to remove the extension:  
    [<img loading="lazy" width="492" height="258" title="capture20180227102557607" style="border: 0px currentcolor;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180227102557607" src="/assets/images/2018/02/capture20180227102557607_thumb.png" border="0" />](/assets/images/2018/02/capture20180227102557607.png)



# Steps (without Extension)

In this example, I have a particular instance of my site (jsandersscale) that is problematic and I logged an error that point to Azure Instance ID 92294a.&nbsp; I will use Chrome to ensure I am on the correct instance (1 of 4 allocated for this site) and profile that instance.

  1. **Identify the full Instance ID**&nbsp;  
    a.&nbsp; Go to Azure Resource Explorer ([https://resources.azure.com](https://resources.azure.com "https://resources.azure.com")), log in and click on the subscription node  
    b.&nbsp; Type the name of your site in search box and click on the app to navigate to it:  
    [<img loading="lazy" width="529" height="284" title="capture20180226134710218" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226134710218" src="/assets/images/2018/02/capture20180226134710218_thumb.png" border="0" />](/assets/images/2018/02/capture20180226134710218.png)  
    c.&nbsp; Click on the ‘instances’ node of your app to get a list of the instances and search for the partial Instance ID:  
    [<img loading="lazy" width="647" height="414" title="capture20180226135025934" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226135025934" src="/assets/images/2018/02/capture20180226135025934_thumb.png" border="0" />](/assets/images/2018/02/capture20180226135025934.png)  
    d.&nbsp; Copy the full “name” that starts with the partial instance id.&nbsp; This is what we will use for the ARRAffinity Cookie.  
    [<img loading="lazy" width="643" height="182" title="capture20180226135521848" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226135521848" src="/assets/images/2018/02/capture20180226135521848_thumb.png" border="0" />](/assets/images/2018/02/capture20180226135521848.png)  
    In this case it is: 92294a4eceea77fdf386fdf56832c40e0b95a40e7628c943f2f1ba5a62eec768</p> 
      * **Set the ARRAffinity cookie in Kudu**  
        a.&nbsp; Log into Kudu using Chrome and go to the Environment tab to see what instance you are currently on (it will be one of the instances you see in Azure Resource Explorer above).  
        [<img loading="lazy" width="470" height="340" title="capture20180226135836571" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226135836571" src="/assets/images/2018/02/capture20180226135836571_thumb.png" border="0" />](/assets/images/2018/02/capture20180226135836571.png)  
        b.&nbsp; Hit the F12 key (or right click on the page and choose ‘Inspect’) and click on the ‘Application’ Tab.&nbsp; Then click on ‘Cookies’ and the page (<yourapp>.scm.azurewebsites.net) and find the ARRAffinity cookie (you will see in this example it is not the one I want… as expected):  
        [<img loading="lazy" width="466" height="206" title="capture20180226140334031" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226140334031" src="/assets/images/2018/02/capture20180226140334031_thumb.png" border="0" />](/assets/images/2018/02/capture20180226140334031.png)  
        c.&nbsp; Change the ARRAffinity cookie value to be the target by double clicking on the old value and pasting in the new.&nbsp; Then Tab out of the field&nbsp; In this case it is: 92294a4eceea77fdf386fdf56832c40e0b95a40e7628c943f2f1ba5a62eec768  
        [<img loading="lazy" width="563" height="207" title="capture20180226140408139" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226140408139" src="/assets/images/2018/02/capture20180226140408139_thumb.png" border="0" />](/assets/images/2018/02/capture20180226140408139.png)  
        d.&nbsp; Now refresh the browser and close the developer tools.&nbsp; You can confirm you are on the correct instance by looking at that value in the Environment Tab once again:  
        [<img loading="lazy" width="596" height="418" title="capture20180226140741820" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226140741820" src="/assets/images/2018/02/capture20180226140741820_thumb.png" border="0" />](/assets/images/2018/02/capture20180226140741820.png)</ol> 
    
    
    # Conclusion
    
    That’s it!&nbsp; Now you can profile or get a dump of a particular process (note the ‘SCM’ process is not your app but is the Kudu process that hosts this Kudu site).
    
    [<img loading="lazy" width="725" height="205" title="capture20180226141038680" style="border-width: 0px;padding-top: 0px;padding-right: 0px;padding-left: 0px" alt="capture20180226141038680" src="/assets/images/2018/02/capture20180226141038680_thumb.png" border="0" />](/assets/images/2018/02/capture20180226141038680.png)
    
    Please drop me a note if you found this useful!
    
    
    
    # Links
    
    **ARRAffinity  
** &nbsp;&nbsp;&nbsp; Disable: <a title="https://blogs.msdn.microsoft.com/appserviceteam/2016/05/16/disable-session-affinity-cookie-arr-cookie-for-azure-web-apps/" href="https://blogs.msdn.microsoft.com/appserviceteam/2016/05/16/disable-session-affinity-cookie-arr-cookie-for-azure-web-apps/" target="_blank">https://blogs.msdn.microsoft.com/appserviceteam/2016/05/16/disable-session-affinity-cookie-arr-cookie-for-azure-web-apps/</a>&nbsp;&nbsp;  
    &nbsp;&nbsp;&nbsp;&nbsp; General Discussion:&nbsp; <a title="https://azure.microsoft.com/en-us/blog/disabling-arrs-instance-affinity-in-windows-azure-web-sites/" href="https://azure.microsoft.com/en-us/blog/disabling-arrs-instance-affinity-in-windows-azure-web-sites/" target="_blank">https://azure.microsoft.com/en-us/blog/disabling-arrs-instance-affinity-in-windows-azure-web-sites/</a>
    
    **Kudu** <a title="https://github.com/projectkudu/kudu/wiki" href="https://github.com/projectkudu/kudu/wiki" target="_blank">https://github.com/projectkudu/kudu/wiki</a>
    
    **Azure Resource Explorer**&nbsp; <a title="https://azure.microsoft.com/en-us/blog/azure-resource-explorer-a-new-tool-to-discover-the-azure-api/" href="https://azure.microsoft.com/en-us/blog/azure-resource-explorer-a-new-tool-to-discover-the-azure-api/" target="_blank">https://azure.microsoft.com/en-us/blog/azure-resource-explorer-a-new-tool-to-discover-the-azure-api/</a>