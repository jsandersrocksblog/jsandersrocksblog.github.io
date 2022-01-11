I was able to cause this error in Internet Explorer 6 and Internet Explore 7.&nbsp; I found that editing my registry entry so that the user agent was greater than 260 I could cause this error in jscript dialogs.&nbsp; By removing entries to get below the size I could avoid the error.&nbsp; This is the registry location for the user agent strings (see <a href="http://support.microsoft.com/kb/218933" mce_href="http://support.microsoft.com/kb/218933">http://support.microsoft.com/kb/218933</a>&nbsp;for setting this using IEAK):

<font face=Courier color=#000080>HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\User Agent\Post Platform</font>

Calls to the navigator object method userAgent was the source of the error.&nbsp; I found that the size of the string to hold this value (internal to the Navigator object) is hard coded to a length of 260.&nbsp;&nbsp;<p mce_keep="true">update:&nbsp; This affects three methods on the object:</p> <p mce_keep="true">appCodeName

  
appVersion  
userAgent</p> <p mce_keep="true">&nbsp;</p>