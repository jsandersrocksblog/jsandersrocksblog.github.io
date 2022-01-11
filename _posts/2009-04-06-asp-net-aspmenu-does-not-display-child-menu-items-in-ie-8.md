Strange.&nbsp; I found in my personal website the Child menus were not showing when I hovered over the root menu item.

There is nothing special about the menus.&nbsp; They are standard asp:menu items created when I dragged the menu tool from the navigation tools in Visual Studio 2008.

UPDATE: Fix<p style="MARGIN: 0in 0in 10pt" class=MsoNormal>

<?xml:namespace prefix = o /><o:p><font size=3 face=Calibri>

<http://support.microsoft.com/kb/962351></font></o:p></p> <p style="MARGIN: 0in 0in 10pt" class=MsoNormal><o:p><font size=3 face=Calibri>Has the hotfix to apply to your server.</font></o:p>&nbsp;</p> <p mce_keep="true">In my case my site was hosted by another company and I did not have access to update asp.net on the server, so I chose workaround #2.</p> <p mce_keep="true">I found two workarounds:</p> 

1.&nbsp; Add the IE7 compatability Meta information: IE=EmulateIE7  
<a href="http://msdn.microsoft.com/en-us/library/cc288325(VS.85).aspx#SetMode" mce_href="http://msdn.microsoft.com/en-us/library/cc288325(VS.85).aspx#SetMode">http://msdn.microsoft.com/en-us/library/cc288325(VS.85).aspx#SetMode</a>

2.&nbsp; Add this style: <p style="MARGIN: 0in 0in 0pt 0.25in" class=MsoNormal>

<span style="FONT-FAMILY: 'Courier New'; COLOR: #a31515; FONT-SIZE: 10pt">.DynamicMenuZIndex<?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt 0.25in" class=MsoNormal>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt">{<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt 0.25in" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; COLOR: red; FONT-SIZE: 10pt">z-index</span><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt">: <span style="COLOR: blue">999</span>;<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt 0.25in" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt">}<o:p></o:p></span></p> 

&nbsp;&nbsp;&nbsp; and then apply it to the menu:<p style="MARGIN: 0in 0in 0pt" class=MsoNormal>

<span style="FONT-FAMILY: 'Courier New'; COLOR: blue; FONT-SIZE: 10pt"><</span><span style="FONT-FAMILY: 'Courier New'; COLOR: #a31515; FONT-SIZE: 10pt">DynamicMenuStyle</span> <span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt"><span style="COLOR: red">CssClass</span><span style="COLOR: blue">=&#8221;DynamicMenuZIndex&#8221;/></span></span></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt"><span style="COLOR: blue"></span></span>&nbsp;</p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt"><span style="COLOR: blue"><font color=#000000 face=Arial>Let me know if this helped you!</font></span></span></p>