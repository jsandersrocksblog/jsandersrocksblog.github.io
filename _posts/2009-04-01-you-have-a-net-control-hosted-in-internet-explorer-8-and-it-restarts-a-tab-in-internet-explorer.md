<?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p><font size=3 face=Calibri><p style="MARGIN: 0in 0in 10pt" class=MsoNormal></font></o:p><o:p><font size=3 face=Calibri>Message: This Tab Has&nbsp;Been Recovered&nbsp;</font></o:p></p> <p style="MARGIN: 0in 0in 10pt" class=MsoNormal><font size=3 face=Calibri>Previous versions of IE are fine.</font></p> <p style="MARGIN: 0in 0in 10pt" class=MsoNormal><font size=3 face=Calibri>If the control implements IObjectSafety or other interfaces improperly, this could&nbsp;cause this message.

<span style="mso-spacerun: yes">&nbsp; </span>The reasons for this include that you did not implement the IObjectSafety Interface properly.<span style="mso-spacerun: yes">&nbsp; </span>You must use the PreserveSig attribute in this interface definition:</font></p> 

`<span style="FONT-SIZE: 10pt; mso-ansi-language: EN" lang=EN>[ComImport]</span>`<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-ansi-language: EN" lang=EN>  
`[Guid("CB5BDC81-93C1-11CF-8F20-00805F2CD064")]`  
`[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]`  
`interface IObjectSafety`  
`{`  
`&nbsp;&nbsp; [PreserveSig]`  
`&nbsp;&nbsp; int GetInterfaceSafetyOptions(ref Guid riid, out int pdwSupportedOptions, out int pdwEnabledOptions);`  
`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`  
`&nbsp;&nbsp; [PreserveSig]`  
`&nbsp;&nbsp; int SetInterfaceSafetyOptions(ref Guid riid, int dwOptionSetMask, int dwEnabledOptions);`  
`}`</span>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-ansi-language: EN" lang=EN>`<font size=3 face=Calibri>The reason your control may work in IE7 fine and stop working in IE8 without the PreserveSig attribute is because the older code is compiled different.&nbsp; IE8 is using Stack objects and indexed on ESP.&nbsp; The incorrect method definition for the interface unbalances the stack and ESP is off and this causes the underlying AV that results in this message.</font>`</span>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-ansi-language: EN" lang=EN>`<font size=3 face=Calibri>Fix your code to implement the Interface correctly and this will fix the problem.</font>`</span>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-ansi-language: EN" lang=EN>`<font size=3 face=Calibri></p>
<p style="MARGIN: 0in 0in 10pt" class=MsoNormal><o:p><font size=3 face=Calibri>Let me know if you find this useful!</font></o:p></p>
<p></font>`</span>