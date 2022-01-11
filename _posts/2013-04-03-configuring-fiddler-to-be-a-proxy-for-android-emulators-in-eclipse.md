I struggled with getting Fiddler to work with the emulators shipped with Eclipse.&#160; Here is a quick reference for you to get Fiddler installed so you can debug HTTP and HTTPS traffic.

# Install and configure Fiddler

Install Fiddler from this link: <http://fiddler2.com>

Start Fiddler (Windows Key then type Fiddler if you cannot find it on your start screen) if Fiddler is capturing data hit F12 to stop capturing

Go to the _Tools_ menu and choose _Fiddler options…_ to get the dialog below.&#160; Configure each of the tabs in the dialog shown to match the screenshots below.&#160; For details on these settings go the Fiddler website, help or better yet buy the Book!

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7585.image_457DA3F6.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7585.image_5F00_457DA3F6.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2474.image_thumb_1D6AF4D7.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2474.image_5F00_thumb_5F00_1D6AF4D7.png" width="488" height="331" /></a>

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4846.image_358E5F32.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4846.image_5F00_358E5F32.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2364.image_thumb_09DD9536.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2364.image_5F00_thumb_5F00_09DD9536.png" width="488" height="331" /></a>

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4011.image_0D0F7D1E.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4011.image_5F00_0D0F7D1E.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4024.image_thumb_7A5A8366.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4024.image_5F00_thumb_5F00_7A5A8366.png" width="488" height="330" /></a>

Click on the _Stream_ tool bar icon to activate this (it will bypass any breakpoints etc… you may have previously defined:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4011.image_205033BD.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4011.image_5F00_205033BD.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0207.image_thumb_2B0D8B12.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0207.image_5F00_thumb_5F00_2B0D8B12.png" width="157" height="65" /></a>

&#160;

&#160;

# Pick a device for the emulator and configure it

## First choose a device and ensure it runs

Start the Android Virtual Device Manager and go to the Devices tab and select your device or create a new AVD from the Device Definitions:

&#160;

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0216.image_19D9E292.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0216.image_5F00_19D9E292.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8547.image_thumb_51AC26B5.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8547.image_5F00_thumb_5F00_51AC26B5.png" width="678" height="248" /></a>

I am going to create a new Nexus S and hit _Create AVD…_ to create a new one.&#160; Then highlight and Start the device by hitting the _Start…_ button:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3348.image_50D3C0CB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3348.image_5F00_50D3C0CB.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0118.image_thumb_2522F6CF.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0118.image_5F00_thumb_5F00_2522F6CF.png" width="689" height="281" /></a>

(Even on my hopped up system it takes _forever_ for the emulator to come all the way up).&#160; Then when I tried to load a web page it would just hang!

I took a look at the configured RAM (hit the _Edit…_ button in the AVDM above):

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8206.image_6DAC8AB0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8206.image_5F00_6DAC8AB0.png"><a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8206.image_6DAC8AB0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8206.image_5F00_6DAC8AB0.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5141.image_thumb_265734BE.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5141.image_5F00_thumb_5F00_265734BE.png" width="244" height="71" /></a></a>

and then amount of RAM used by the emulator and saw it looked like I was maxing out the memory by visiting web pages.

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00
/00/83/94/metablogapi/6646.image_15BF39D0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6646.image_5F00_15BF39D0.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0842.image_thumb_2E4ED720.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0842.image_5F00_thumb_5F00_2E4ED720.png" width="652" height="47" /></a>

I stopped the emulator and changed the RAM to 768 in the _Memory Options_ and that solved the problem!

## Configure the device to use the Fiddler Proxy&#160; 

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3755.image_3D46612A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3755.image_5F00_3D46612A.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7450.image_thumb_42B4D1CE.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7450.image_5F00_thumb_5F00_42B4D1CE.png" width="185" height="307" /></a>&#160;

Hit the OK button to dismiss the intro screen and hit the center of the circle and choose the _Settings_ app:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2350.image_41DC6BE4.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2350.image_5F00_41DC6BE4.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1273.image_thumb_683E4F2F.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1273.image_5F00_thumb_5F00_683E4F2F.png" width="225" height="238" /></a>

Then choose the _more…_ option then _Mobile networks_:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8231.image_1858915B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8231.image_5F00_1858915B.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8712.image_thumb_05A397A4.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8712.image_5F00_thumb_5F00_05A397A4.png" width="244" height="160" /></a><a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1374.image_1713F87C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1374.image_5F00_1713F87C.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0880.image_thumb_5671AC0C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0880.image_5F00_thumb_5F00_5671AC0C.png" width="244" height="205" /></a>

then _Access Point Names_ and select your APN:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4428.image_15CF5F9D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4428.image_5F00_15CF5F9D.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4118.image_thumb_031A65E6.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4118.image_5F00_thumb_5F00_031A65E6.png" width="244" height="215" /></a><a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6558.image_148AC6BE.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6558.image_5F00_148AC6BE.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4503.image_thumb_420BE681.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4503.image_5F00_thumb_5F00_420BE681.png" width="244" height="110" /></a>

You will now set the _Proxy_ and _Port_ settings for this APN:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6746.image_45AA015E.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6746.image_5F00_45AA015E.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7142.image_thumb_6C0BE4A9.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7142.image_5F00_thumb_5F00_6C0BE4A9.png" width="234" height="244" /></a>

Find the IP address of your computer by hitting the Windows Key and R key at the same time and typing cmd.&#160; Then hit enter.&#160; This will open a Command Prompt window.&#160; Type _ipconfig_ in the command window to list your network configuration:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5047.image_4EA90DBD.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5047.image_5F00_4EA90DBD.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2311.image_thumb_144D97DC.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2
311.image_5F00_thumb_5F00_144D97DC.png" width="558" height="600" /></a>

There is a lot of information in here!&#160; Ignore any addresses that start with 169. and look for IPv4 addresses.&#160; In my case the IP address of my card is 192.168.1.6 (note this and close the window).

&#160;

Enter the IP address you got above as the proxy&#160; and the port from Fiddler (8888 by default) for the _Proxy_ and _Port_ values in the APN settings on the device

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8713.image_717A554D.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8713.image_5F00_717A554D.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8371.image_thumb_50F3159B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8371.image_5F00_thumb_5F00_50F3159B.png" width="244" height="140" /></a>

Hit the Back button or Home button in the emulator controls to go back and see if you can capture traffic by starting the browser.&#160; 

You should get this error if everything is working correctly and have tried to navigate to the default google https site in the browser (**NOTE:** If you get a connection error your anti-virus or firewall is probably blocking the 8888 port so your device cannot communicate with fiddler.&#160; Configuring this is beyond the scope of this blog post):

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5732.image_53D85481.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5732.image_5F00_53D85481.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0743.image_thumb_6548B559.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0743.image_5F00_thumb_5F00_6548B559.png" width="244" height="152" /></a>

&#160;

This is because Fiddler uses a _Man in the Middle_ approach to decoding https traffic.&#160; You have to install the Fiddler certificate on this device now.&#160; This is pretty easy!&#160; Simply navigate to your Fiddler proxy and port in the browser and point to the certificate by typing in something similar to this in the browser address bar (substituting the ip address you used above for the proxy setting): <http://192.168.1.6:8888/FiddlerRoot.cer> 

You will get this dialog:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7587.image_1E328947.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7587.image_5F00_1E328947.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6521.image_thumb_0B7D8F90.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6521.image_5F00_thumb_5F00_0B7D8F90.png" width="244" height="208" /></a>

Give the certificate a name like Fiddler and hit the _OK_ button.

You will get this message:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1321.image_1CEDF068.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1321.image_5F00_1CEDF068.png"><img loading="lazy" title="image" style="margin: 0px; display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6507.image_thumb_434FD3B3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6507.image_5F00_thumb_5F00_434FD3B3.png" width="244" height="169" /></a>

So hit _OK_ and create a PIN for your device (don’t forget it).

A brief confirmation that the Certificate was installed will appear and you are now all set to debug HTTP and HTTPS traffic on your emulator!

If you go back to Fiddler you will see you are not capturing the HTTP and HTTPS traffic from the device!&#160; You do not have to capture the traffic by hitting F12 because as a proxy the traffic will appear by default in the _Web Sessions_ window.

Let me know if this was useful to you!