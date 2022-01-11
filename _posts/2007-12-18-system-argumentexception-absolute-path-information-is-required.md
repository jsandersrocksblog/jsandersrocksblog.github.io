You have a .NET 2.0 control hosted in a browser.&nbsp; The control uses the System.Uri class.&nbsp; When upgrading to .NET 2.0 SP1 you can get an error: System.ArgumentException: Absolute path information is required.

Four conditions must exist for this to happen:

> 1.&nbsp;Using the 2.0 Framework SP1  
> 2.&nbsp;Control uses the System.Uri class  
> 3.&nbsp;Uri class passed a URI that has escaped characters (% escaped or puny code)  
> 4.&nbsp;Control has a .config file on the http server

The same error can occur in an application that Creates an AppDomain and points to a web location for the application configuration file.

The problem occurs because of a new test in the System.Uri class that checks for a config file when it encounters an escaped URI as an input.&nbsp; It demands that the configuration file reside on a local disk.&nbsp; If the class is a WebApplication (ASP.NET) then it will not have the problem.&nbsp; Due to the nature of this test, you have to fool the code to make it think it is a web application.&nbsp; The control will have to have the necessary permissions to modify the appdomain however.

For a Browser hosted control you could do this:<p class=MsoNormal style="MARGIN: 0in 0in 0pt">

<span style="FONT-SIZE: 10pt; COLOR: #2b91af; FONT-FAMILY: 'Courier New'">AppDomain</span><span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">.CurrentDomain.SetData(<span style="COLOR: #a31515">&#8220;.appVPath&#8221;</span>, <span style="COLOR: #a31515">&#8220;/&#8221;</span>);</span><span style="FONT-SIZE: 11pt; COLOR: #1f497d; FONT-FAMILY: 'Calibri','sans-serif'"><?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span></p> 

or if you have created your own domain (in a desktop app for example) set that domain property: 

<span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'; mso-fareast-font-family: Calibri; mso-fareast-theme-font: minor-latin; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA">myNewDomain.SetData(<span style="COLOR: #a31515">&#8220;.appVPath&#8221;</span>, <span style="COLOR: #a31515">&#8220;/&#8221;</span>);</span>

Hope this helps!&nbsp; Let me know if you are able to use this information.