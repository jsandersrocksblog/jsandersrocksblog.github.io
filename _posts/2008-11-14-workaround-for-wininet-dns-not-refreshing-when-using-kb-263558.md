If you are making Synchronous calls in WinInet, the DNS timeouts don&#8217;t appear to work when set (see: <a href="http://support.microsoft.com/kb/263558" mce_href="http://support.microsoft.com/kb/263558">http://support.microsoft.com/kb/263558</a>&nbsp;).

Async calls do however work correctly.

One workaround is to simply restart the&nbsp;application&nbsp;using WinInet.&nbsp;

I found a code workaround for the issue as well.&nbsp; Simply open and close the handle you get with the InternetOpen call then open it again:

hOpen= ::InternetOpen(&#8230;..);

InternetCloseHandle(hOpen);

hOpen= ::InternetOpen(&#8230;..);

// now use handle&#8230;

&nbsp;The performance impact will be very low.

&nbsp;-Jeff