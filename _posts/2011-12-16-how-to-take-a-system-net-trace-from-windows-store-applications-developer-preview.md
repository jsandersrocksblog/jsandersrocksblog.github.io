In desktop applications and services we frequently take System.Net traces to diagnose issues using the HttpWebRequest class, HttpListener, sockets, smpt etc… (and now the HttpClient classes).&#160; We traditionally use the application configuration file (appname.exe.config) to enable the tracing.&#160; The config file is read and the tracing parameters are used to trace the information we find useful.&#160;&#160; Windows Store applications do not have configuration files however so you cannot use the application configuration file to take the trace. 

The good news is that you can go further up and put your tracing settings in the machine.config file!&#160; The one minor issue is that any process using system.net will be included in the trace file if it starts after you make the change.&#160; If you use my trace file it logs the process and time so you can use that to filter the trace information see: <a href="http://blogs.msdn.com/b/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx" target="_blank">My Favorite System.Net trace configuration file dumps Process ID and Date Time Information</a> .

Here are the steps:

**You will be making changes to the machine.config file.&#160; If you mess this up, you could keep .NET framework applications from running so be SURE you make a copy of the file that you can restore after you have gotten your trace!&#160; If you are using a 64 bit build you make the config changes in the Framework64 tree.**



  * Save a copy of C:\Windows\Microsoft.NET\Framework\v4.0.30319\Config\machine.config because you will be modifying this file (or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config if your image is a 64 bit build)
  * Open Notepad as an Administrator (right mouse click or press and hold with touch and choose ‘Run as Administrator’
  * From your Administrator Notepad open: C:\Windows\Microsoft.NET\Framework\v4.0.30319\Config\machine.config (or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config if your image is a 64 bit build)
  * Add the normal <a href="http://blogs.msdn.com/b/jpsanders/archive/2009/03/24/my-favorite-system-net-trace-configuration-file-dumps-process-id-and-date-time-information.aspx" target="_blank">System.Net tracing setup</a> at the bottom of the file before the </configuration> tag (see above link)
  * <font style="background-color: rgb(255, 255, 0);">Find this section</font> in the text you just added to machine.config:  
    <add  
    name="System.Net"  
    type="System.Diagnostics.TextWriterTraceListener"  
    <font style="background-color: rgb(255, 255, 0);">initializeData="System.Net.trace.log”</font>  
    traceOutputOptions = "ProcessId, DateTime"  
    />

  * Change the path and file name of initializeData to <font style="background-color: rgb(255, 255, 0);">“c:\temp\network.log”</font> (or a path of your choosing)  
    <add  
    name="System.Net"  
    type="System.Diagnostics.TextWriterTraceListener"  
    <font style="background-color: rgb(255, 255, 0);">initializeData="c:\temp\network.log”</font>  
    traceOutputOptions = "ProcessId, DateTime"  
    />

  * Save the file
  * Create the directory c:\temp\ (or if you chose a different directory go to that), and give the local user named “ALL APPLICATION PACKAGES” full control of the directory.&#160; To do this:



> a. Right click on the c:\temp folder and select properties  
> b. Click on the security tab  
> c. Hit the _Edit_ button  
> d. Hit the _Add_ button  
> e. Hit the _Locations&#8230;_ button and change the location to the very top item (the name of your computer)  
> f. In the space below _Enter the object names to select_ add _ALL APPLICATION PACKAGES_ and hit Check Names  
> g. Hit _OK_ and check _Allow, Full control_ for the _ALL APPLICATION PACKAGES_ and then hit _OK_ again to apply your changes



  1. Start your application and recreate the issue you wish to trace, and close your application
  2. Restore the machine.config file from the copy you created in step 1

You can then analyze the trace as you would in the past!

Please let me know if you have found this useful or have any questions.