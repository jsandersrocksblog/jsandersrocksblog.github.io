I was using the _Windows Azure Mobile Services .NET (Preview) Backend_ and wanted to see the HTTPS traffic.&#160; I found the best way is to use Fiddler and modify the application so it will send traffic through the Fiddler proxy.&#160; By default Fiddler will not catch the localhost traffic so you need to do a little trick to get IIS Express (Cassini) to work with this setup (ref: [http://docs.telerik.com/fiddler/observe-traffic/troubleshooting/notraffictolocalhost](http://docs.telerik.com/fiddler/observe-traffic/troubleshooting/notraffictolocalhost "http://docs.telerik.com/fiddler/observe-traffic/troubleshooting/notraffictolocalhost") ).

Set up Fiddler like you normally would to capture all HTTPS traffic and modify your application code to point to localhost.fiddler instead of local host.&#160; For example, in my C# client project I changed this:

<pre class="code"><span style="background: white; color: black;">  </span><span style="background: white; color: blue;">sealed partial class </span><span style="background: white; color: rgb(43, 145, 175);">App </span><span style="background: white; color: black;">: </span><span style="background: white; color: rgb(43, 145, 175);">Application
    </span><span style="background: white; color: black;">{
        </span><span style="background: white; color: green;">// This MobileServiceClient has been configured to communicate with your local
        // test project for debugging purposes. Comment out this declaration and use the one
        // provided below when you are done developing and deploy your service to the cloud.
        </span><span style="background: white; color: blue;">public static </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceClient </span><span style="background: white; color: black;">MobileService = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceClient</span><span style="background: white; color: black;">(
            </span><span style="background: white; color: rgb(163, 21, 21);"><font style="background-color: rgb(255, 255, 0);">"http://localhost:51039"</font>
        </span><span style="background: white; color: black;">);</span></pre>

To this:

<pre class="code"><span style="background: white; color: black;">  </span><span style="background: white; color: blue;">sealed partial class </span><span style="background: white; color: rgb(43, 145, 175);">App </span><span style="background: white; color: black;">: </span><span style="background: white; color: rgb(43, 145, 175);">Application
    </span><span style="background: white; color: black;">{
        </span><span style="background: white; color: green;">// This MobileServiceClient has been configured to communicate with your local
        // test project for debugging purposes. Comment out this declaration and use the one
        // provided below when you are done developing and deploy your service to the cloud.
        </span><span style="background: white; color: blue;">public static </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceClient </span><span style="background: white; color: black;">MobileService = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceClient</span><span style="background: white; color: black;">(
            </span><span style="background: white; color: rgb(163, 21, 21);"><font style="background-color: rgb(255, 255, 0);">"http://localhost.fiddler:51039"</font>
        </span><span style="background: white; color: black;">);</span></pre>

Now I get my traffic in the local scenario!&#160; 

I hope this helps!&#160; Drop me a note if you found this useful!

Jeff