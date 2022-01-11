PowerShell can and does use System.Net classes to communicate over the wire.&nbsp; This example will cover capturing a System.Net trace of the Azure PowerShell _Publish-AzureWebsiteProject_ command-let.

## 

## 

## Setup

**Close any running PowerShell instances**.&nbsp; PowerShell reads the .config file when you first start the executable.&nbsp; 

**Locate the PowerShell (or PowerShell_ise) executable** so you can alter the application .config file (or create it).

&nbsp;

On my Windows 10 machine the location of the PowerShell executable is here:&nbsp; C:\Windows\System32\WindowsPowerShell\v1.0

[<img loading="lazy" title="capture20180215110755159" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180215110755159" src="/assets/images/2018/02/capture20180215110755159_thumb.png" width="1080" height="161" />](/assets/images/2018/02/capture20180215110755159.png)

Note the ‘CONFIG File’ for PowerShell.exe.&nbsp; If you have file extensions turned on in Windows Explorer it they look like this:

&nbsp;

[<img loading="lazy" title="capture20180215111016568" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180215111016568" src="/assets/images/2018/02/capture20180215111016568_thumb.png" width="1079" height="174" />](/assets/images/2018/02/capture20180215111016568.png)

&nbsp;

If there are no .config files, don’t panic!&nbsp; You simply will create one.

**Open (or create) the appropriate .config file**.&nbsp; In my case I will not be using the integrated editor so I need to edit _powershell.exe.config_.&nbsp; This directory is protected however so if you simply open it with notepad and try and save it, you will get this error: _You do not have permission to open this file.&nbsp; See the owner of the file or an administrator to obtain permission.&nbsp; (_Note: depending on how your machine is configured, you may have to take ownership of this file – do this in the security tab of the properties).

Open notepad (or your favorite editor), right click on the icon and find Notepad.exe,&nbsp; and choose: _Run as administrator_:

[<img loading="lazy" title="capture20180215111340287" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180215111340287" src="/assets/images/2018/02/capture20180215111340287_thumb.png" width="244" height="170" />](/assets/images/2018/02/capture20180215111340287.png)&nbsp;

&nbsp;

**Copy the .config file** for a backup and name it something like PowerShell.exe.backupconfig.&nbsp; You can use this to restore the .config file later.

**Alter the .config file** to enable System.Net tracing. Copy the trace configuration from my blog: [https://blogs.msdn.microsoft.com/jpsanders/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information/](https://blogs.msdn.microsoft.com/jpsanders/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information/ "https://blogs.msdn.microsoft.com/jpsanders/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information/") and add it to the existing config file or create a new one if it does not exist.

In my case the <configuration> section already exists so I simply need the section and everything inside the **<system.diagnostics> </system.diagnostics>** section from the above blog:

[<img loading="lazy" title="capture20180215111735958" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180215111735958" src="/assets/images/2018/02/capture20180215111735958_thumb.png" width="549" height="354" />](/assets/images/2018/02/capture20180215111735958.png)

&nbsp;

**Find the section: initializeData=&#8221;System.Net.trace.log&#8221;** .&nbsp; This section tells where to write the log and the name of the file.&nbsp; We cannot write to this directory so, **change that entry** to initializeData=&#8221;c:\temp\System.Net.trace.log&#8221;

**Save the .config file.**

**Create the directory c:\temp** on your machine and you are all set to trace!

**Start powershell and run the command you wish to trace.** &nbsp; In my example I navigated to the directory where my WebDeploy package was and typed: _Publish-AzureWebsiteProject -Name jspowershellpublish -Package .\PowershellPublish.zip_

**Exit PowerShell and restore the .config file.&nbsp;** If you didn’t have a config file previously simply delete the file you created.&nbsp; If you did have one, copy your backup .config file over top of the one you altered.

**Read your trace and enjoy!**

## Conclusion

This blog is not intended to help you solve you issue but simply give you a tool to collect the System.Net trace.&nbsp; Using System.Net tracing to analyze the network traffic in PowerShell is a powerful tool.&nbsp; I hope this blog helps you grab that trace easily.&nbsp; If you found this blog useful, drop me a note!