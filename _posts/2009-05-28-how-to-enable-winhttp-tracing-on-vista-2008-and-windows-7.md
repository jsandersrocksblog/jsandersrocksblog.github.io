WinhttpTracecfg.exe for Vista does not exist, so how can you get a WinHttp trace in Vista and above?

WinHttpTraceCfg.exe has been replaced in Vista and above with the netsh winhttp command.  
see this blog:  
<http://blogs.msdn.com/wndp/archive/2007/03/21/winhttp-configuration-for-windows-vista.aspx>

**NOTE:**&nbsp; For 32 bit tracing on a 64 bit system you need to use the 32 bit netsh from the SysWOW64 directory.&nbsp; This goes for proxy settings as well!&nbsp; This netsh is located in the C:\Windows\SysWOW64 directory (if you did a default install).

A typical command to enable full tracing for WinHttp would look like this:

C:\Windows\system32>netsh winhttp set tracing trace-file-prefix=&#8221;C:\Temp\WinHttpLog&#8221; level=verbose format=hex state=enabled

For a 32 bit process on a 64 bit OS it would be from the SysWOW64 dir like this:

C:\Windows\SysWOW64>netsh winhttp set tracing trace-file-prefix=&#8221;C:\Temp\WinHttpLog&#8221; level=verbose format=hex state=enabled

You would reproduce the issue and then turn off tracing like this:

C:\Windows\system32>netsh winhttp set tracing state=disabled

&nbsp;This would leave the other parameters you set previously to remain so the next time you want to enable tracing simply type:

C:\Windows\system32>netsh winhttp set tracing state=enabled

&nbsp;

Other parameters are available:

C:\Windows\system32>netsh winhttp set tracing 

will show you the options:

Usage:&nbsp; set tracing  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [output=]file|debugger|both  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [trace-file-prefix=]<string>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [level=]default|verbose  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [format=]ansi|hex  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [max-trace-file-size=]<number>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [state=]enabled|disabled

Parameters:

&nbsp; Tag&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Value  
&nbsp; trace-file-prefix&nbsp;&nbsp; &#8211; Prefix for the log file (can include a path)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; specify &#8220;*&#8221; to delete an existing prefix  
&nbsp; output&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211; Where the trace entries are written/displayed to  
&nbsp; level&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211; How much information to log  
&nbsp; format&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211; Display format of network traffic (hex or ansi)  
&nbsp; max-trace-file-size &#8211; Maximum size of the trace file (in bytes)  
&nbsp; state&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211; Enables or disables winhttp tracing

Examples:

&nbsp; set tracing trace-file-prefix=&#8221;C:\Temp\Test3&#8243; level=verbose format=hex  
&nbsp; set tracing output=debugger max-trace-file-size=512000 state=enabled

You can display the existing settings with this command:

C:\Windows\system32>netsh winhttp show tracing

Current WinHTTP Tracing settings:

&nbsp;&nbsp;&nbsp; Tracing is not enabled.

&nbsp;&nbsp;&nbsp; Trace File Prefix: C:\Temp\Test3  
&nbsp;&nbsp;&nbsp; Trace Output: file  
&nbsp;&nbsp;&nbsp; Trace Level:&nbsp; verbose (headers, APIs, and entity body)  
&nbsp;&nbsp;&nbsp; Network Traffic Format: hex  
&nbsp;&nbsp;&nbsp; Maximum size of trace file (in bytes): 65535

Let me know if this helps!