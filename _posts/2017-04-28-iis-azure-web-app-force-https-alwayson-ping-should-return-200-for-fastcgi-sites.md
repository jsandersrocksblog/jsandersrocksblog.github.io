
PHP, Java and other FastCGI hosted environments should respond to an Always On ping to keep the child process warmed up.&nbsp; Specifically in Azure App Services we send a request to the Root of the site with the header User-Agent: AlwaysOn.&nbsp; If you are forcing HTTPS using a Url Rewrite rule, the Always On ping will get a redirect but will not follow that redirect and therefore the FastCGI module will not be hit and kept warm.

## Solution

You can simply add a rule that will look for the ping to the root of your site and the User-Agent: AlwaysOn header and not force HTTPS.&nbsp; The easiest way to do this is to add this Url Rewrite rule before the Force HTTPS rule as follows:

<system.webServer>  
&nbsp;&nbsp;&nbsp; <rewrite>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <rules>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <rule name=&#8221;No HTTPS for user agent AlwaysOn and Root of site&#8221; stopProcessing=&#8221;true&#8221;>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <match url=&#8221;^$&#8221;/>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <conditions>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add input=&#8221;{HTTP\_USER\_AGENT}&#8221; pattern=&#8221;^AlwaysOn$&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </conditions>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <action type=&#8221;None&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </rule>

The above rule will look for a match for a request to the root and with a User-Agent header of “AlwaysOn”.&nbsp; If that condition is met, no other rules are processed.

## Conclusion

If you find this blog is useful please drop me a note!&nbsp; Ref:&nbsp; [http://microsoftazurewebsitescheatsheet.info/](http://microsoftazurewebsitescheatsheet.info/ "http://microsoftazurewebsitescheatsheet.info/")&nbsp; Force HTTPS