You may get an error similar to this when running your WinHttp application:

Error:&nbsp;The server name or address could not be resolved  
Code:&nbsp;80072EE7  
Source: &nbsp;WinHttp.WinHttpRequest

The familiar <a href="http://msdn.microsoft.com/en-us/library/aa384069(VS.85).aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa384069(VS.85).aspx">ProxyCfg</a> application allows you to set the proxy settings for WinHttp.&nbsp; However in this case, your&nbsp; application is not picking up the proxy settings.&nbsp; You verify this by setting the Proxy settings to the current user by typing &#8220;proxycfg -p myproxyhere&#8221; at the command line and you see from a Netmon trace that the proxy is not being utilized.&nbsp; 

Further research shows your application is loading the 32 bit version of WinHttp.&nbsp; In Windows 2003 x64, there is a directory for the 32 versions of the system components.&nbsp; You need to run this version for your 32 bit application: c:\windows\sysWow64\proxycfg -p myproxyhere.&nbsp; This fixes the issue.&nbsp; In general, on this platform when using proxycfg.exe, you should run the version in system32 and the version in sysWow64 to ensure you set the proxy setting for both versions of WinHttp on the system.

**Side note&nbsp;on WinHttp COM registration on Windows 2003 x64**

One thing interesting in the default installation of the 64 bit OS is that you will notice WinHttp.dll does not live in either the system32 or the sysWow64 directories.&nbsp; Also, if you look in the registry under HKCR\CLSID you will see no entry for WinHttp.WinHttpRequest.5.1.&nbsp; So how does a script succeed that calls CreateObject() on your progId?&nbsp; The magic here is the SideBySide (SxS) registration of WinHttp.&nbsp; You will notice there are WinHttp Dlls in the C:\WINDOWS\WinSxS\ subdirectories.&nbsp; You will also see in C:\WINDOWS\WinSxS\Manifests there are manifest files and the file names contain WINHTTP in them.&nbsp; Without going into a ton of detail, what happens is CLSIDFromProgID will take the name of the object you are creating and based on the Bitness of the application (64 or 32) there are internal system calls to find the latest version of winhttp and use that for the creation of the object.

That is why you cannot find the ProgID in the registry!

Let me know if this blog helped you out by dropping me a comment please!