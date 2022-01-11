An embedded WMP or Flash&nbsp;movie would not start when Internet Explorer loaded this page:

<html>  
<BODY>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
<table width=&#8221;100%&#8221;>  
&nbsp; <tr>  
&nbsp;&nbsp;&nbsp; <td>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <div style=&#8217;width:100%; height:100%; margin:0px;&#8217;>

<OBJECT ID=&#8221;MediaPlayer&#8221; WIDTH=100% HEIGHT=100%  
&nbsp; CLASSID=&#8221;CLSID:22D6f312-B0F6-11D0-94AB-0080C74C7E95&#8243;  
&nbsp; STANDBY=&#8221;Loading Windows Media Player components&#8230;&#8221;  
&nbsp; TYPE=&#8221;application/x-oleobject&#8221;  
CODEBASE=&#8221;<http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=6,4,7>,

1112&#8243;>

&nbsp; <PARAM name=&#8221;autoStart&#8221; value=&#8221;True&#8221;>  
&nbsp; <PARAM name=&#8221;filename&#8221; value=&#8221;C:\Users\Public\Videos\Sample Videos\bear.wmv&#8221;>

<EMBED TYPE=&#8221;application/x-mplayer2&#8243;  
&nbsp;&nbsp;&nbsp; SRC=&#8221;[http://WebServer/MyFile.wvx](http://webserver/MyFile.wvx)&#8220;  
&nbsp;&nbsp;&nbsp; NAME=&#8221;MediaPlayer&#8221;  
&nbsp;&nbsp;&nbsp; WIDTH=100%  
&nbsp;&nbsp;&nbsp; HEIGHT=100%>  
&nbsp; </EMBED>  
</OBJECT>  
&nbsp;&nbsp;&nbsp; </div>  
&nbsp;&nbsp;&nbsp; </td>  
&nbsp; </tr>  
/table>

</BODY>  
</html>

<span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Arial','sans-serif'">Looking through the code&nbsp;I found that&nbsp;the control was not sent the&nbsp;OleControlSite Activate command that would start the display and the movie playing.<?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span>

<span style="FONT-SIZE: 10pt; FONT-FAMILY: 'Arial','sans-serif'">Fix:&nbsp; Change one of the size parameters&nbsp;to be Pixels instead of % and the movie will activate and run (true for Flash as well).<span style="mso-spacerun: yes">&nbsp; </span>Alternatively you could have the jscript put focus on the control when the page loads which would have the same effect.<o:p></o:p></span><p mce_keep="true">&nbsp;</p>