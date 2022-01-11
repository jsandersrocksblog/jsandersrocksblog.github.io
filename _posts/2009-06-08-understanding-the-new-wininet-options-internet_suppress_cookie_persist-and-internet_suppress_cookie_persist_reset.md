These options are well documented.&nbsp; Important notes: 

These&nbsp;flags affect the process that you set this option from.&nbsp;

You do not need to pass an InternetHandle (but no error if you do).

Sample code:

<font size=2>

</font><font color=#0000ff size=2><font color=#0000ff size=2>bool</font></font><font size=2> abRes = </font><font color=#0000ff size=2><font color=#0000ff size=2>false</font></font><font size=2>;  
DWORD adOption = INTERNET\_SUPPRESS\_COOKIE_PERSIST;  
abRes= InternetSetOption(hInternet, INTERNET\_OPTION\_SUPPRESS_BEHAVIOR ,&adOption,</font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(adOption));  
adOption = INTERNET\_SUPPRESS\_COOKIE\_PERSIST\_RESET;  
abRes= InternetSetOption(hInternet, INTERNET\_OPTION\_SUPPRESS_BEHAVIOR ,&adOption,</font><font color=#0000ff size=2><font color=#0000ff size=2>sizeof</font></font><font size=2>(adOption));</font>

<font size=2>&nbsp;

</font>