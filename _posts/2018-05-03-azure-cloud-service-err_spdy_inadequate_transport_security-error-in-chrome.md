I ran into an interesting error that I had to debunk where a customer thought with HTTP/2 on Windows Server 2016 which has IIS 10 installed, that this caused the error above.&nbsp; That was not true!

## Analysis

Looking at a network trace I could see that the client (Chrome) was advertising higher level encryption as accepted Cipher Suites but the server was coming back with Cipher Suite: TLS\_RSA\_WITH\_AES\_256\_CBC\_SHA (0x0035) in the server hello reply

I spun up an Azure Cloud Service, ensured I could use HTTP/2 with no error and indeed, in my case I could see in the trace indeed, no error from Chrome and the Cipher Suite returned was: Cipher Suite: TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM_SHA384 (0xc030)

Knowing that SChannel will return the Cipher Suites in the order that they are prioritized, compared the unadulterated machine Cipher Suite order with the broken one and sure enough, the broken one had the wrong (non-default) order.&nbsp; The way to check this is to run the following in a powershell command window:&nbsp;&nbsp; get-tlsciphersuite&nbsp; | foreach {$_.Name}.&nbsp; For the broken case I saw the offending Cipher Suite listed as the 2nd item in the list.&nbsp; Further queries revealed on startup them were manually setting the cipher suites due to some old requirements!

[<img loading="lazy" width="832" height="618" title="cipher suites" alt="cipher suites" src="/assets/images/2018/05/cipher-suites_thumb.png" border="0" />](/assets/images/2018/05/cipher-suites.png)

## Solution

Don’t mess with the default cipher suite order as this is set correctly out of the box for the latest OS updates!&nbsp; The default should serve you needs and is in the correct order.&nbsp; ref: <https://msdn.microsoft.com/en-us/library/windows/desktop/mt490158(v=vs.85).aspx> is the listing for 2016

If this helped you, drop me a note!