<font size=2>

Here is a VB Version of the JScript DebugDiag script for analyzing WebRequest hangs using DebugDiag <a href="http://blogs.msdn.com/jpsanders/archive/2008/10/24/analyzing-httpwebrequest-connection-saturation-in-net.aspx" mce_href="http://blogs.msdn.com/jpsanders/archive/2008/10/24/analyzing-httpwebrequest-connection-saturation-in-net.aspx">http://blogs.msdn.com/jpsanders/archive/2008/10/24/analyzing-httpwebrequest-connection-saturation-in-net.aspx</a>.&nbsp; It has several improvements over the previous version.&nbsp; First you will notice many similarities to the previous script.&nbsp; Some minor changes were added to translate from Jscript to VBscript.&nbsp; One big change is the .loadby command.&nbsp; This will load the sos.dll from the same path the mscorwks is loaded.&nbsp; You would normally run this script on the machine that you took the dump from.&nbsp; This would ensure that the sos version matches the mscorwks version in the dump.&nbsp; Another change is to seach not only for GetRequest but for SubmitRequest as well.&nbsp; Finally I am dumping out more information like when there request is fine and the ConnectionGroupName.<p mce_keep="true"><font color=#ff0000>

**Problem! All available connections used up.  
** HttpRequest URI:http://10.10.10.10/Service/Service.asmx  
ServicePoint &#8211; ConnectionLimit:12 CurrentConnections:14  
ConnectionGroupName: MyConnectionPool </font></p> <p mce_keep="true">I thought it would be equally important to dump when there were no issues:</p> <p mce_keep="true">&nbsp;<font color=#008000>**No Hang Problems found  
** HttpRequest URI:http://Mydev/output.asmx/test?&Name=test2  
ServicePoint &#8211; ConnectionLimit:10 CurrentConnections:1  
ConnectionGroupName: </font></p> 

Finally, fomatting the URI in a more readable format was fairly simple.&nbsp; I used the -nofields switch when dumping the string and parsed out the String: text.

<font size=2>

function getUriString(aObjAddr)  
Dim aRetStr  
Dim aCmdOutput  
Dim aFoundIdx  
aCmdOutput = g\_Debugger.Execute(&#8220;!do -nofields poi(poi(&#8221; & aObjAddr & &#8220;+&#8221; & g\_HttpObjectOffsets.Item(&#8220;\_Uri&#8221;) & &#8220;)+&#8221; & g\_UriObjectOffsets.Item(&#8220;m_String&#8221;) & &#8220;)&#8221; )

aFoundIdx = InStr(1,aCmdOutput,&#8221;String:&#8221;,1)<p mce_keep="true">&nbsp;</p> 

if (aFoundIdx <> 0) then  
&nbsp; aRetStr=trim( Mid(aCmdOutput, aFoundIdx + Len(&#8220;String:&#8221;)))  
end if  
getUriString = aRetStr

end function

</font><p mce_keep="true">&nbsp;</p> 

As with ANY sample code, I leave it to you&nbsp;to debug and&nbsp;test!&nbsp; I also left some &#8220;TODO&#8221; sections for you to fill in yourself.&nbsp; I hope you find it useful.&nbsp; An industrious person could embed this into the existing&nbsp;DebugDiag scripts to included it in the&nbsp;HangAnalysis portion of the scripts and really have a powerful tool for troubleshooting WebRequest issue.<p mce_keep="true">&nbsp;</p> 

**&nbsp;Full script below ([Copy Code](javascript:CopyCode('VBDDcodesection1');)):**<div style="BACKGROUND-COLOR: #e0e0e0" id=VBDDcodesection1><font color=#008000 size=2></p> 

<%</font><font color=#0000ff size=2><font color=#0000ff size=2>@</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>Language</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>=</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>vbscript</font></font><font size=2> %><%</font><font color=#0000ff size=2><font color=#0000ff size=2>@</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>Category</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>=</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>Crash/Hang</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>Analyzers</font></font><font size=2> %><%</font><font color=#0000ff size=2><font color=#0000ff size=2>@</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>Description</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>=</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>Template</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>System.Net</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>analysis</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>script</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>to</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>build</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>from&#8230;</font></font><font size=2>%><%</font><font color=#0000ff size=2><font color=#0000ff size=2>@</font></font><font size=2> </font><font color=#ff0000 size=2><font color=#ff0000 size=2>TopLevelScript</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>=</font></font><font size=2> </font><font color=#0000ff size=2><font color=#0000ff size=2>True</font></font><font size=2> %><%

Option Explicit  
Dim g_Progress  
Dim g_Debugger

Dim g_HttpObjectOffsets  
Dim g_SvcPointObjectOffsets  
Dim g_UriObjectOffsets  
Dim g_StringObjectOffsets

Dim g_MaxConnectionErrorThreads &#8216; array of thread id&#8217;s that have exceed max connection.  
Dim g_MaxConnectionWarningThreads &#8216; array of thread id&#8217;s that have 50% max connection.

main()

&#8216; this kicks off everything  
sub main()

Dim a_DataFile  
Dim i  
Dim a_NumberOfDumps

Manager.Write &#8220;<b>System.Net sample analysis script</b><BR>&#8221;

Manager.Progress.SetOverallRange 0,100  
Manager.Progress.OverallPosition = 10  
Manager.Progress.OverallStatus=&#8221;Initializing&#8221;  
a_NumberOfDumps = Manager.DataFiles.Count

&#8216; for each data file specified&#8230;

for i=0 to a_NumberOfDumps-1

&#8216; get the dump  
a_DataFile = Manager.DataFiles(i)  
Manager.Progress.OverallStatus=&#8221;Starting analysis of: &#8221; & a_DataFile

&#8216; get an instance of a debugger  
set g\_Debugger = Manager.GetDebugger(a\_DataFile)<p mce\_keep="true">Manager.Write &#8220;<h2>Analysis of: &#8221; & a\_DataFile & &#8220;</h2>&#8221;</p> 

if g_Debugger.IsCrashDump then  
&nbsp; Manager.ReportInformation &#8220;DebugDiag determined that this dump file (&#8221; & a\_DataFile & &#8220;) is a <font color=&#8217;Red&#8217;><b> crash </b></font>&#8221; &\_  
&#8220;dump and this script does not analyze crashes (only hangs). Please run analysis using a crash Script.&#8221;

end if

&#8216; try to load the managed debugging extension  
if(LoadSOS)then

&#8216; initialize some object information for performance  
initGlobals

&#8216; walk all threads but report only specific managed ones  
walkManagedThreads  
reportErrors

else  
&#8216; todo  
end if

&#8216; done with the debugger, so close it  
Manager.CloseDebugger a_DataFile  
Manager.Progress.OverallPosition = 100/a_NumberOfDumps * (i+1)

next  
end sub

sub initGlobals()

set g_HttpObjectOffsets = CreateObject(&#8220;Scripting.Dictionary&#8221;)  
ManagedFieldOffsets g\_HttpObjectOffsets, Array(&#8220;\_ServicePoint&#8221;, &#8220;\_Uri&#8221;, &#8220;\_HttpRequestHeaders&#8221;, &#8220;\_Proxy&#8221;,&#8221;\_ConnectionGroupName&#8221;),&#8221;system.dll!System.Net.HttpWebRequest&#8221;

set g_SvcPointObjectOffsets = CreateObject(&#8220;Scripting.Dictionary&#8221;)  
ManagedFieldOffsets g\_SvcPointObjectOffsets, Array(&#8220;m\_ConnectionLimit&#8221;, &#8220;m_CurrentConnections&#8221;),&#8221;system.dll!System.Net.ServicePoint&#8221;

set g_UriObjectOffsets = CreateObject(&#8220;Scripting.Dictionary&#8221;)  
ManagedFieldOffsets g\_UriObjectOffsets, Array(&#8220;m\_String&#8221;), &#8220;system.dll!System.Uri&#8221;

set g_StringObjectOffsets = CreateObject(&#8220;Scripting.Dictionary&#8221;)  
ManagedFieldOffsets g\_StringObjectOffsets, Array( &#8220;m\_firstChar&#8221;), &#8220;mscorlib.dll!System.String&#8221;

g_MaxConnectionErrorThreads = &#8220;&#8221;  
g_MaxConnectionWarningThreads = &#8220;&#8221;

end sub<p mce_keep="true">&nbsp;</p> 

&#8216; this starts the analysis&#8230;

sub walkManagedThreads()

Dim aCmdOutput  
Dim aStackOutput  
Dim aThreadInfo  
Dim aDebugThread  
Dim aNumThreads  
Dim aAddr

Dim i  
Dim aFoundIdx  
Dim bFoundFirstThread  
bFoundFirstThread =false

set aThreadInfo = g_Debugger.ThreadInfo  
aNumThreads = aThreadInfo.Count

Manager.Progress.SetCurrentRange 0,aNumThreads  
Manager.Progress.CurrentStatus=&#8221;Finding threads waiting on &#8216;System.Net.HttpWebRequest.GetResponse()&#8217; or &#8216;System.Net.HttpWebRequest.SubmitRequest()'&#8221;

for i=0 to aNumThreads-1

Manager.Progress.CurrentPosition = i

set aDebugThread = aThreadInfo(i)

if Not( aDebugThread is nothing ) then

aStackOutput = g_Debugger.Execute(&#8220;~&#8221; & aDebugThread.ThreadID & &#8220;e!CLRStack&#8221;)  
aFoundIdx = InStr(aStackOutput,&#8221;System.Net.HttpWebRequest.GetResponse&#8221;)

if (aFoundIdx = 0)then  
&nbsp; aFoundIdx = InStr(aStackOutput,&#8221;System.Net.HttpWebRequest.SubmitRequest&#8221;)  
end if 

&#8216; highlight the call???  
&#8216;is the tread processing GetResponse?

if (aFoundIdx <> 0) then  
&nbsp; if Not(bFoundFirstThread) then

&nbsp;&nbsp;&nbsp; bFoundFirstThread=true  
Manager.Write &#8220;<br><h2>Managed Threads Waiting on &#8216;System.Net.HttpWebRequest.GetResponse()'</h2><br>&#8221;

&nbsp; end if

Manager.Write &#8220;<A NAME=&#8217;ThreadAnchor&#8221; & aDebugThread.ThreadID & &#8220;&#8216;>&#8221; 

&#8216; dump managed objects on the stack  
aCmdOutput = g_Debugger.Execute(&#8220;~&#8221; & aDebugThread.ThreadID & &#8220;e!dso&#8221;)

&#8216; Collect the HttpWebRequest objects on the stack.  
aFoundIdx = InStr(aCmdOutput,&#8221;System.Net.HttpWebRequest&#8221;)

while aFoundIdx <> 0

&#8216; if we found an object of interest on the stack,  
&#8216; sav the address fo the object and the thread ID.

aAddr = Mid(aCmdOutput,aFoundIdx-9, 8)

checkObj aAddr,aDebugThread.ThreadID

&#8216;build error/warning strings here instead.  
&#8216;display total number of managed threads? 

&#8216; look for another one&#8230;  
aFoundIdx = 0 &#8216;aCmdOutput.indexOf(&#8220;System.Net.HttpWebRequest&#8221;, aFoundIdx + 25)

wend

Manager.Write regexReplace(aStackOutput, &#8220;\n&#8221;, &#8220;<br>&#8221; )  
end if  
end if

next

end sub<p mce_keep="true">&nbsp;</p> 

function regexReplace(aSrcStr, aPattern, aReplacement )

dim aRetStr  
dim aRegEx  
set aRegEx = New RegExp  
aRegEx.Pattern=aPattern  
aRegEx.Global=True

aRetStr = aRegEx.Replace( aSrcStr,aReplacement)  
regexReplace = aRetStr

end function<p mce_keep="true">&nbsp;</p> 

sub reportErrors()

Dim i  
Dim threadList  
if Len(g_MaxConnectionErrorThreads) then

Manager.ReportError &#8220;The number connections exceeds the number of available connections for these threads:&#8221; & g\_MaxConnectionErrorThreads,&#8221;Increase the number of connections available per this article: <a TARGET=\_blank href=&#8217;http:&#8217;msdn.microsoft.com/en-us/library/7af54za5.aspx&#8217;>Managing Connections</a>&#8221;

end if

end sub

&#8221;&#8221;&#8221;&#8221;&#8221;&#8217;/ Managed code helpers &#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8217;/

&#8216; use .loadby to find where mscorwks is loaded and then load SOS from the same place  
function LoadSOS()

Dim abSuccess  
Dim begPos  
Dim endPos  
Dim CmdOutput  
Dim Module

abSuccess = false  
CmdOutput = g_Debugger.Execute(&#8220;.loadby sos mscorwks&#8221;)  
&#8216;todo, check CmdOutput to ensure SOS loaded!

LoadSOS = true

end function<p mce_keep="true">&nbsp;</p> 

&#8216; given an Array, populate a dictionary object with offets for these array items to be used later.  
sub ManagedFieldOffsets( dictObj ,aArray, aObject)

Dim aStr  
Dim i  
Dim aCmdOutput  
&#8216; get the Class information  
aCmdOutput = g_Debugger.Execute(&#8220;!DumpClass &#8221; + getEEClass(aObject))

for each aStr in aArray  
&nbsp; dictObj.Add aStr, findOffset(aCmdOutput,aStr)  
next

End Sub

&#8216; simple helper functions

function getManagedLongVal( aObjAddr, aOffset )  
&nbsp; getManagedLongVal = g_Debugger.Execute(&#8220;dt long &#8221; & aObjAddr & &#8220;+&#8221; & aOffset)  
end function<p mce_keep="true">&nbsp;</p> 

function getManagedStringVal( aObjAddr, aOffset )

Dim retStr  
Dim aCmdOutput  
Dim aFoundIdx  
aCmdOutput = g_Debugger.Execute(&#8220;!do -nofields poi(&#8221; & aObjAddr & &#8220;+&#8221; & aOffset & &#8220;)&#8221;)

aFoundIdx = InStr(aCmdOutput,&#8221;String:&#8221;)

if (aFoundIdx <> 0) then  
retStr=trim( Mid(aCmdOutput, aFoundIdx + Len(&#8220;String:&#8221;)))  
end if 

getManagedStringVal = retStr

end function

&#8221;&#8221;&#8221;&#8221;&#8217; Helper Function &#8211; findOffset  
&#8216; given a string, extract the field offset specified  
&#8216; this is really an excercise it string parsing  
function findOffset(aCmdOutput, aField)

Dim retStr  
retStr=&#8221;&#8221;

Dim aFoundIdx  
Dim aBOL  
Dim sArray

&#8216; find the field  
aFoundIdx = InStr(1,aCmdOutput,aField,1)

if aFoundIdx <> 0 then

&#8216; look backwards from there for the offset.  
&#8216; find the previous line  
aBOL = InStrRev(aCmdOutput,Chr(10),aFoundIdx,1)+1

&#8216;need to strip all but one space from the string and make an array of the column values  
retStr=normalizeWhitespace(Mid(aCmdOutput,aBOL, aFoundIdx-aBOL))  
sArray = Split(retStr)  
retStr=&#8221;&#8221;  
&#8216; 7 columns total, offset is third column (0 based array)  
retStr = sArray(2)

else  
&nbsp; &#8216;TODO Manager.Write &#8220;Did not find Field: &#8221; & aField & &#8220;<<<<<<<<<<<<<<&#8221;  
end if

findOffset= retStr

end function

&#8221;&#8221;&#8221;&#8221;&#8217; Helper Function &#8211; getEEClass  
&#8216; given a string, extract the EEClass address  
&#8216; theClass name is direct input to !Name2EE must be MODULENAME!CLASSNAM  
function getEEClass( theClassName )

Dim retStr  
retStr=&#8221;&#8221;  
Dim aCmdOutput  
Dim aFoundIdx  
Dim aEOL

aCmdOutput = g_Debugger.Execute(&#8220;!Name2EE &#8221; & theClassName) 

aFoundIdx = InStr(1,aCmdOutput,&#8221;EEClass:&#8221;,1)

if (aFoundIdx <> 0) then  
&nbsp; aEOL = InStr(aFoundIdx,aCmdOutput,&#8221;Name:&#8221;,1)  
&nbsp; retStr = Mid(aCmdOutput, aFoundIdx + Len(&#8220;EEClass:&#8221;) , aEOL &#8211; (aFoundIdx + Len(&#8220;EEClass:&#8221;)))  
end if

getEEClass= retStr

end function<p mce_keep="true">&#8216; utility functions</p> 

&#8216; utility function removing extra whitespace and replacing it with a single space  
&#8216; for example &#8221; some text here&#8221; will be converted to &#8221; some text here&#8221;

function normalizeWhitespace(stringToTrim) 

dim aRegEx  
set aRegEx = New RegExp  
aRegEx.Pattern=&#8221;\s+&#8221;  
aRegEx.Global=True  
normalizeWhitespace = aRegEx.Replace( stringToTrim,&#8221; &#8220;)

end function<p mce_keep="true">&nbsp;</p> 

&#8216; calculate and save offsets for the Object fields we need  
&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221;&#8221; Non-generic managed object helpers&#8230;.<p mce_keep="true">&#8216; Given an address of an object get the service point object address

  
function getSvcPointFromReq(aHttpObjAddr)</p> 

Dim aRetStr  
aRetStr=&#8221;&#8221;  
Dim aCmdOutput

aCmdOutput = g\_Debugger.Execute(&#8220;dd &#8221; & aHttpObjAddr & &#8220;+&#8221; & g\_HttpObjectOffsets.Item(&#8220;_ServicePoint&#8221;) & &#8221; L1&#8243;)

aRetStr = Mid(aCmdOutput, Len(aCmdOutput) &#8211; 8,8)  
getSvcPointFromReq = Trim(aRetStr)

end function<p mce_keep="true">function getUriString(aObjAddr)

  
Dim aRetStr  
Dim aCmdOutput  
Dim aFoundIdx  
aCmdOutput = g\_Debugger.Execute(&#8220;!do -nofields poi(poi(&#8221; & aObjAddr & &#8220;+&#8221; & g\_HttpObjectOffsets.Item(&#8220;\_Uri&#8221;) & &#8220;)+&#8221; & g\_UriObjectOffsets.Item(&#8220;m_String&#8221;) & &#8220;)&#8221; )</p> 

aFoundIdx = InStr(1,aCmdOutput,&#8221;String:&#8221;,1)  
if (aFoundIdx <> 0) then  
&nbsp; aRetStr=trim( Mid(aCmdOutput, aFoundIdx + Len(&#8220;String:&#8221;)))  
end if<p mce_keep="true">getUriString = aRetStr</p> 

end function<p mce_keep="true">&nbsp;</p> 

function getConnectionGroupName(aObjAddr)

getConnectionGroupName=g\_Debugger.Execute(&#8220;du poi(poi(&#8221; & aObjAddr & &#8220;+&#8221; & g\_HttpObjectOffsets.Item(&#8220;\_ConnectionGroupName&#8221;) & &#8220;)+&#8221; & g\_UriObjectOffsets.Item(&#8220;m\_String&#8221;) & &#8220;)+&#8221; & g\_StringObjectOffsets.Item(&#8220;m_firstChar&#8221;)).substr(9)

end function<p mce_keep="true">&nbsp;</p> 

&#8216; obj is an address we can do !do on to get information from  
sub checkObj(aObjAddr, threadID)

&#8216;get service point and see if it is OK.  
Dim bSvcPointErrorOrWarning  
bSvcPointErrorOrWarning = false

Dim maxConn  
Dim currConn  
Dim connGroup  
Dim aCmdOutput  
Dim i  
Dim aFoundIdx

aCmdOutput = getSvcPointFromReq(aObjAddr)

if( (aCmdOutput<>&#8221;00000000&#8243;) And (aCmdOutput<>&#8221;????????&#8221;)) then

maxConn = getManagedLongVal( aCmdOutput, g\_SvcPointObjectOffsets.Item(&#8220;m\_ConnectionLimit&#8221;))  
currConn = getManagedLongVal( aCmdOutput, g\_SvcPointObjectOffsets.Item(&#8220;m\_CurrentConnections&#8221;))  
connGroup = getManagedStringVal( aObjAddr, g\_HttpObjectOffsets.Item(&#8220;\_ConnectionGroupName&#8221;))

if(currConn>=maxConn) then

&#8216; report out info and error  
g\_MaxConnectionErrorThreads = g\_MaxConnectionErrorThreads & &#8220;<a href=&#8217;#ThreadAnchor&#8221; & threadID & &#8220;&#8216;>&#8221; & threadID & &#8220;</a>, &#8220;

Manager.Write &#8220;<br> <font color=&#8217;red&#8217;><b>Problem! All available connections used up.</b><br> HttpRequest URI:&#8221; & getUriString(aObjAddr) & &#8220;<br>ServicePoint &#8211; ConnectionLimit:&#8221; & maxConn & &#8221; CurrentConnections:&#8221; & currConn &&#8221;<br>ConnectionGroupName: &#8221; & connGroup & &#8220;</font><br><br>&#8221;

else

if(((currConn)*2)>=maxConn) then

&#8216; report out info and error  
g\_MaxConnectionWarningThreads = g\_MaxConnectionWarningThreads & &#8220;<a href=&#8217;#ThreadAnchor&#8221; & threadID + &#8220;&#8216;>&#8221; & threadID & &#8220;</a>, &#8220;

Manager.Write &#8220;<br> <font color=&#8217;orange&#8217;><b>Warning, half of the availabe connections are being used</b><br> HttpRequest URI:&#8221; & getUriString(aObjAddr) & &#8220;<br>ServicePoint &#8211; ConnectionLimit:&#8221; & maxConn & &#8221; CurrentConnections:&#8221; & currConn &&#8221;<br>ConnectionGroupName: &#8221; & connGroup & &#8220;</font><br><br>&#8221;

else

&#8216; no problems found  
Manager.Write &#8220;<br> <font color=&#8217;green&#8217;> <b>No Hang Problems found</b><br>HttpRequest URI:&#8221; & getUriString(aObjAddr) & &#8220;<br>ServicePoint &#8211; ConnectionLimit:&#8221; & maxConn & &#8221; CurrentConnections:&#8221; & currConn &&#8221;<br>ConnectionGroupName: &#8221; & connGroup & &#8220;</font><br><br>&#8221;

end if  
end if  
end if

End Sub  
%>

</font></div> 

</font>