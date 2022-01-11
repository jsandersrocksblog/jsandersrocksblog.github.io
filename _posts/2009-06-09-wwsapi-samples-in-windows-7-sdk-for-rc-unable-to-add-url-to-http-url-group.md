I like to build and run&nbsp;with&nbsp;UAC on.&nbsp; When&nbsp;running the HttpCalculatorService example I got this error:&nbsp;

&nbsp;Failure: errorCode=0x80070005  
Unable to add URL to HTTP URL group.  
Access is denied.

Running from an administrator command prompt I do not get the error!

Obviously I do not have permissions to something.&nbsp; Some investigation revealed that I need to add the user I wanted to run as to the urlacl (<a href="http://msdn.microsoft.com/en-us/library/cc307223(vs.85).aspx" mce_href="http://msdn.microsoft.com/en-us/library/cc307223(vs.85).aspx">http://msdn.microsoft.com/en-us/library/cc307223(vs.85).aspx</a>)

So this is the command that allowd me to run (replace myDOMAIN\myUSERNAME with the domain and user you wish to run the Service under): netsh http add urlacl url=http://+:80/example user=myDOMAIN\myUSERNAME.

To do this in code you could use this API: <http://msdn.microsoft.com/en-us/library/aa364503(VS.85).aspx>&nbsp;but the code your are running would need to have the necessary permissions so you are in kind of a chicken and the egg situation!

Drop me&nbsp;a comment and let me know if this helped you please!&nbsp;<p mce_keep="true">&nbsp;</p>