Starting with Windows XP SP2, the Crypto API CRL check uses WinHttp (see: [http://support.microsoft.com/kb/887196](http://support.microsoft.com/kb/887196 "http://support.microsoft.com/kb/887196")).&nbsp; This can cause some confusion with network administrators and developers since they might have set proxy information for WinInet or applications using CryptoAPIs but the certificate validation fails for the https calls inside certain networks.

To allow the CRL check out to the cloud, the CLR code using WinHttp needs to be able to make it through your proxy!&nbsp; WinHttp can ONLY perform Automatic Proxy Detection using WPAD or use a static proxy.&nbsp; If you network supports WPAD (which is recommended) then you should not have a problem.&nbsp; If machines are using a static proxy, then you must set the same static proxy for WinHttp on that machine or the CRL check will fail.&nbsp; If you have a static pac file configured, then this will fail since WinHttp cannot use a static Pac file (use WPAD to provide the PAC file instead).

Another option is to allow direct connection through your proxy or firewall by configuring a rule to allow the User-Agent header that the CRL check uses to pass through.&nbsp; That header is currently: User-Agent: Microsoft-CryptoAPI/6.0 

If you refuse to use WPAD then you can set a static proxy for WinHttp settings that will in turn be used by the Crypto API CRL check.&nbsp; Depending on the version of the OS you are running you will use netsh or winhttpcfg.exe to set the static proxy.&nbsp; You cannot set this value programmatically inside of your program for just that particular instance or process however.&nbsp; The setting for the proxy in this case is a system wide setting and not per process. 

More information: 

How Certificate Revocation Works &#8211; [http://technet.microsoft.com/en-us/library/ee619754(WS.10).aspx](http://technet.microsoft.com/en-us/library/ee619754(WS.10).aspx "http://technet.microsoft.com/en-us/library/ee619754(WS.10).aspx") 

Summary of CryptoAPI changes: [http://support.microsoft.com/kb/887195](http://support.microsoft.com/kb/887195 "http://support.microsoft.com/kb/887195") and <http://support.microsoft.com/kb/887196> 

&nbsp; 

Please Drop me a note if you found this helpful!