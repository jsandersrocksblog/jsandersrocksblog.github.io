There are two settings for WinHttp Proxy settings for a 64 Bit OS.&nbsp; One applies to the 64 bit environment and one for the 32 bit environment.&nbsp; You can use netsh for Windows 2008, Windows 7 and later OSes and proxycfg.exe for earlier OSes.&nbsp; If you are confused and not sure where your WinHttp application is reading proxy settings from, the easiest way to determine where WinHttp is reading proxy settings from is to use procmon (process monitor).

To set the x64 WinHttp settings using netsh.exe, simply open a command prompt and type ‘netsh winhttp set proxy’ and set your proxy there (if you do not supply arguments it gives you some examples).&nbsp; This will run the 64 bit version of netsh from the System32 directory.

To set the 32 bit (x86) WinHttp settings, open a command prompt and navigate to the Windows\SysWOW64 directory and run netsh there. 

For proxycfg.exe you need to run proxycfg from the command line (system32 dir by default so x64 code) or the proxycfg from the c:\windows\sysWow64\ directory (x86 – 32bit).

&nbsp;

For another issue with the WinHttp COM object you can refer to my earlier post here: [http://blogs.msdn.com/b/jpsanders/archive/2009/07/21/winhttp-proxy-configuration-on-windows-2003-x64.aspx](http://blogs.msdn.com/b/jpsanders/archive/2009/07/21/winhttp-proxy-configuration-on-windows-2003-x64.aspx "http://blogs.msdn.com/b/jpsanders/archive/2009/07/21/winhttp-proxy-configuration-on-windows-2003-x64.aspx")

Let me know if this helps you!