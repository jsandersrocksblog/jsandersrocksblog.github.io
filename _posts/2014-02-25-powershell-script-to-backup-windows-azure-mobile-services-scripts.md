Listing for a PowerShell Script to backup Windows Azure Mobile Services scripts and configuration information.&#160; I will get something more complete up on the Script Repository this next month!&#160; This also assumes you have set your subscription active using <a title="http://msdn.microsoft.com/en-us/library/windowsazure/jj156055.aspx" href="http://msdn.microsoft.com/en-us/library/windowsazure/jj156055.aspx" target="_blank">Windows Azure PowerShell</a>.&#160; See [How to install and configure Windows Azure PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=320552) for more information.

<pre class="code"><span style="color: rgb(0, 0, 139);">function </span><span style="color: rgb(138, 43, 226);">main</span>()
{
    <span style="color: rgb(255, 69, 0);">$startDir </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">Get-Location</span>;
    <span style="color: rgb(255, 69, 0);">$MobileServices </span><span style="color: rgb(169, 169, 169);">=  </span><span style="color: blue;">ListMobileServices </span>;
    <span style="color: rgb(255, 69, 0);">$MobileServices </span><span style="color: rgb(169, 169, 169);">| </span><span style="color: blue;">foreach</span>{
        <span style="color: rgb(0, 100, 0);"># for every service create a directory
        </span><span style="color: rgb(255, 69, 0);">$MobileServiceName </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>name;
        <span style="color: rgb(255, 69, 0);">$MobileServiceName</span>;
        <span style="color: rgb(255, 69, 0);">$MobileServiceDir </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">CreateMobileServiceDirectory</span>(<span style="color: rgb(255, 69, 0);">$MobileServiceName</span>);
        <span style="color: rgb(0, 100, 0);"># and move to that directory
        </span><span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$MobileServiceDir</span>;
        <span style="color: rgb(255, 69, 0);">$ScriptList </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">ListScripts </span><span style="color: rgb(255, 69, 0);">$MobileServiceName</span>;
        <span style="color: rgb(255, 69, 0);">$ScriptList</span>;
        <span style="color: rgb(0, 0, 139);">if </span>(<span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>table)
        {
            <span style="color: rgb(255, 69, 0);">$tblScriptLoc </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">CreateMobileServiceDirectory</span>(<span style="color: darkred;">"scripts"</span>);
            <span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$tblScriptLoc</span>;
            <span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>table <span style="color: rgb(169, 169, 169);">| </span><span style="color: blue;">foreach</span>{
                <span style="color: rgb(255, 69, 0);">$ScriptName </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">"table/{0}.{1}" </span><span style="color: rgb(169, 169, 169);">-f </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>table<span style="color: rgb(169, 169, 169);">, </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>operation;
                <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile script download </span><span style="color: rgb(255, 69, 0);">$MobileServiceName $ScriptName</span>;
                }
                <span style="color: rgb(0, 100, 0);">#end foreach table
            </span><span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$MobileServiceDir</span>;
        }
        <span style="color: rgb(0, 0, 139);">if</span>(<span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>scheduler)
        {
            <span style="color: rgb(255, 69, 0);">$tblScriptLoc </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">CreateMobileServiceDirectory</span>(<span style="color: darkred;">"scripts"</span>);
            <span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$tblScriptLoc</span>;
            <span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>scheduler <span style="color: rgb(169, 169, 169);">| </span><span style="color: blue;">foreach</span>{
                <span style="color: rgb(255, 69, 0);">$ScriptName </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">"scheduler/{0}" </span><span style="color: rgb(169, 169, 169);">-f </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>name;
                <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile script download </span><span style="color: rgb(255, 69, 0);">$MobileServiceName $ScriptName</span>;
                }<span style="color: rgb(0, 100, 0);">#end foreach scheduler
            </span><span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$MobileServiceDir</span>;
        }
        <span style="color: rgb(0, 0, 139);">if</span>(<span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>api)
        {
            <span style="color: rgb(255, 69, 0);">$tblScriptLoc </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">CreateMobileServiceDirectory</span>(<span style="color: darkred;">"scripts"</span>);
            <span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$tblScriptLoc</span>;
            <span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>api <span style="color: rgb(169, 169, 169);">| </span><span style="color: blue;">foreach</span>{
                <span style="color: rgb(255, 69, 0);">$ScriptName </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">"api/{0}" </span><span style="color: rgb(169, 169, 169);">-f </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>name;
                <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile script download </span><span style="color: rgb(255, 69, 0);">$MobileServiceName $ScriptName</span>;
                }
                <span style="color: rgb(0, 100, 0);">#end foreach api
            </span><span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$MobileServiceDir</span>;
        }
        <span style="color: rgb(0, 0, 139);">if</span>(<span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>shared)
        {
            <span style="color: rgb(255, 69, 0);">$tblScriptLoc </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">CreateMobileServiceDirectory</span>(<span style="color: darkred;">"scripts"</span>);
            <span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$tblScriptLoc</span>;
            <span style="color: rgb(255, 69, 0);">$ScriptList</span><span style="color: rgb(169, 169, 169);">.</span>shared <span style="color: rgb(169, 169, 169);">| </span><span style="color: blue;">foreach</span>{
                <span style="color: rgb(255, 69, 0);">$ScriptName </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">"shared/{0}" </span><span style="color: rgb(169, 169, 169);">-f </span><span style="color: rgb(255, 69, 0);">$_</span><span style="color: rgb(169, 169, 169);">.</span>name;
                <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile script download </span><span style="color: rgb(255, 69, 0);">$MobileServiceName $ScriptName</span>;
                }
                <span style="color: rgb(0, 100, 0);">#end foreach shared
            </span><span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$MobileServiceDir</span>;
        }
        <span style="color: rgb(0, 100, 0);">#dump config to a json file:
        </span><span style="color: rgb(255, 69, 0);">$tmp</span><span style="color: rgb(169, 169, 169);">=</span><span style="color: darkred;">""</span>; <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile config list --json </span><span style="color: rgb(255, 69, 0);">$MobileServiceName </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{  <span style="color: rgb(255, 69, 0);">$tmp </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_ </span>};  <span style="color: blue;">New-Item </span><span style="color: darkred;">"config.json" </span><span style="color: navy;">-ItemType </span><span style="color: rgb(138, 43, 226);">file </span><span style="color: navy;">-Value </span><span style="color: rgb(255, 69, 0);">$tmp</span>;
        <span style="color: rgb(255, 69, 0);">$tmp</span><span style="color: rgb(169, 169, 169);">=</span><span style="color: darkred;">""</span>; <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile show --json </span><span style="color: rgb(255, 69, 0);">$MobileServiceName </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{  <span style="color: rgb(255, 69, 0);">$tmp </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_ </span>};  <span style="color: blue;">New-Item </span><span style="color: darkred;">"details.json" </span><span style="color: navy;">-ItemType </span><span style="color: rgb(138, 43, 226);">file </span><span style="color: navy;">-Value </span><span style="color: rgb(255, 69, 0);">$tmp</span>;
        <span style="color: rgb(255, 69, 0);">$tmp</span><span style="color: rgb(169, 169, 169);">=</span><span style="color: darkred;">""</span>; <span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile job list --json </span><span style="color: rgb(255, 69, 0);">$MobileServiceName </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{  <span style="color: rgb(255, 69, 0);">$tmp </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_ </span>};  <span style="color: blue;">New-Item </span><span style="color: darkred;">"job.json" </span><span style="color: navy;">-ItemType </span><span style="color: rgb(138, 43, 226);">file </span><span style="color: navy;">-Value </span><span style="color: rgb(255, 69, 0);">$tmp</span>;
    <span style="color: blue;">Set-Location </span><span style="color: rgb(255, 69, 0);">$startDir</span><span style="color: rgb(169, 169, 169);">.</span>Path;
    };
    <span style="color: rgb(0, 100, 0);">#end foreach Service
</span>}
<span style="color: rgb(0, 0, 139);">function </span><span style="color: rgb(138, 43, 226);">CreateMobileServiceDirectory</span>()
{
    <span style="color: rgb(0, 0, 139);">param</span>(
        <span style="color: rgb(169, 169, 169);">[</span><span style="color: rgb(0, 191, 255);">Parameter</span>(Mandatory<span style="color: rgb(169, 169, 169);">=</span><span style="color: rgb(255, 69, 0);">$true</span>)<span style="color: rgb(169, 169, 169);">]
        </span><span style="color: rgb(255, 69, 0);">$ServiceName
        </span>)
    <span style="color: rgb(255, 69, 0);">$loc </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">Get-Location</span>;
    <span style="color: rgb(169, 169, 169);">[</span><span style="color: teal;">string</span><span style="color: rgb(169, 169, 169);">]</span><span style="color: rgb(255, 69, 0);">$fullPath </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">"{0}\{1}" </span><span style="color: rgb(169, 169, 169);">-f </span><span style="color: rgb(255, 69, 0);">$loc</span><span style="color: rgb(169, 169, 169);">.</span>Path<span style="color: rgb(169, 169, 169);">, </span><span style="color: rgb(255, 69, 0);">$ServiceName</span>;
    <span style="color: rgb(0, 0, 139);">if</span>(<span style="color: blue;">Test-Path </span><span style="color: rgb(255, 69, 0);">$fullPath</span>)
    {
        <span style="color: rgb(0, 0, 139);">if </span>( <span style="color: blue;">Test-Path </span><span style="color: rgb(255, 69, 0);">$fullPath </span><span style="color: navy;">-pathType </span><span style="color: rgb(138, 43, 226);">Container</span>)
        {
        }
        <span style="color: rgb(0, 0, 139);">else
        </span>{
            <span style="color: rgb(0, 100, 0);">#error
        </span>}
    }
    <span style="color: rgb(0, 0, 139);">else
    </span>{
        <span style="color: rgb(255, 69, 0);">$newObj</span><span style="color: rgb(169, 169, 169);">= </span><span style="color: blue;">New-Item </span><span style="color: rgb(255, 69, 0);">$fullPath </span><span style="color: navy;">-ItemType </span><span style="color: rgb(138, 43, 226);">directory</span>;
    }
    <span style="color: rgb(0, 0, 139);">return </span><span style="color: rgb(255, 69, 0);">$fullPath</span>;
}
<span style="color: rgb(0, 0, 139);">function </span><span style="color: rgb(138, 43, 226);">ListTables</span>()
{
    <span style="color: rgb(0, 0, 139);">param</span>(
        <span style="color: rgb(169, 169, 169);">[</span><span style="color: rgb(0, 191, 255);">Parameter</span>(Mandatory<span style="color: rgb(169, 169, 169);">=</span><span style="color: rgb(255, 69, 0);">$true</span>)<span style="color: rgb(169, 169, 169);">]
        </span><span style="color: rgb(255, 69, 0);">$ServiceName
        </span>)
    <span style="color: rgb(255, 69, 0);">$TableTemp </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">""</span>;
    <span style="color: rgb(255, 69, 0);">$TMPP</span><span style="color: rgb(169, 169, 169);">=</span><span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile table list --json </span><span style="color: rgb(255, 69, 0);">$ServiceName </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{
        <span style="color: rgb(255, 69, 0);">$TableTemp </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_</span>;
        };
    <span style="color: rgb(0, 0, 139);">return </span><span style="color: blue;">ConvertFrom-Json</span>(<span style="color: rgb(255, 69, 0);">$TableTemp</span>);
}
<span style="color: rgb(0, 0, 139);">function </span><span style="color: rgb(138, 43, 226);">ListScripts</span>()
{
    <span style="color: rgb(0, 0, 139);">param</span>(
        <span style="color: rgb(169, 169, 169);">[</span><span style="color: rgb(0, 191, 255);">Parameter</span>(Mandatory<span style="color: rgb(169, 169, 169);">=</span><span style="color: rgb(255, 69, 0);">$true</span>)<span style="color: rgb(169, 169, 169);">]
        </span><span style="color: rgb(255, 69, 0);">$ServiceName
    </span>)
    <span style="color: rgb(255, 69, 0);">$TableTemp </span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">""</span>;
    <span style="color: rgb(255, 69, 0);">$TMPP</span><span style="color: rgb(169, 169, 169);">=</span><span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile script list --json </span><span style="color: rgb(255, 69, 0);">$ServiceName </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{
        <span style="color: rgb(255, 69, 0);">$TableTemp </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_</span>;
        };
    <span style="color: rgb(0, 0, 139);">return </span><span style="color: blue;">ConvertFrom-Json</span>(<span style="color: rgb(255, 69, 0);">$TableTemp</span>);
}
<span style="color: rgb(0, 0, 139);">function </span><span style="color: rgb(138, 43, 226);">ListMobileServices</span>()
{
    <span style="color: rgb(255, 69, 0);">$TempJsonString</span><span style="color: rgb(169, 169, 169);">= </span><span style="color: darkred;">""</span>;
    <span style="color: rgb(0, 100, 0);"># Get a list of Services as Json objects
    # since it is a bunch of Line feeds have to concatonate the string
    </span><span style="color: blue;">azure </span><span style="color: rgb(138, 43, 226);">mobile list --json </span><span style="color: rgb(169, 169, 169);">|  </span><span style="color: blue;">foreach</span>{ <span style="color: rgb(255, 69, 0);">$TempJsonString </span><span style="color: rgb(169, 169, 169);">+= </span><span style="color: rgb(255, 69, 0);">$_  </span>};
    <span style="color: rgb(0, 0, 139);">return </span><span style="color: blue;">ConvertFrom-Json</span>(<span style="color: rgb(255, 69, 0);">$TempJsonString</span>);
}
<span style="color: rgb(0, 100, 0);">#call Main!
</span><span style="color: blue;">main</span>; </pre>

<pre class="code"></pre>