There were no detailed instructions for this and I ran into some problems when following our tutorial for this so here are my super easy to follow instructions.&#160; I did this on Windows 8.1 64bit OS installed in a Hyper-V VM.&#160; These instructions are for the 64 bit environment (I did not try the 32 bit).

### Install the Android SDK

From the [Android SDK](http://developer.android.com/sdk/index.html) download choose the big button on the right (link is this [Download the SDK ADT Bundle for Windows](http://developer.android.com/sdk/index.html#win-bundle "Download the SDK ADT Bundle for Windows")):

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7268.image_01FBF5D5.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7268.image_5F00_01FBF5D5.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6131.image_thumb_6E7126E4.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6131.image_5F00_thumb_5F00_6E7126E4.png" width="542" height="304" /></a> 

Read the license agreement and if you don’t agree then STOP, otherwise grab the 64 bit SDK and download it:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6560.image_1E2ECF64.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6560.image_5F00_1E2ECF64.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7144.image_thumb_2B94E26A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7144.image_5F00_thumb_5F00_2B94E26A.png" width="551" height="243" /></a> 

Unzip the package (I put it in my documents in a folder I created called Android Development):

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2476.image_372D305A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2476.image_5F00_372D305A.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2705.image_thumb_36C0FD65.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2705.image_5F00_thumb_5F00_36C0FD65.png" width="551" height="268" /></a> 

and read this:

[http://developer.android.com/sdk/installing/bundle.html](http://developer.android.com/sdk/installing/bundle.html "http://developer.android.com/sdk/installing/bundle.html")

For convenience pin a link to Eclipse.exe on your taskbar.&#160; It is in the Eclipse sub-folder wherever you installed the android SDK and you can navigate there using Windows Explorer, right click on it and pin it:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7522.image_6AF526AB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7522.image_5F00_6AF526AB.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7041.image_thumb_341AD265.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7041.image_5F00_thumb_5F00_341AD265.png" width="244" height="241" /></a> </p> 

### Install the JDK

What is missing is now is the JDK.&#160; Go here and install it:

[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html "http://www.oracle.com/technetwork/java/javase/downloads/index.html")

Press the big Java button:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0284.image151_684EFBAB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0284.image151_5F00_684EFBAB.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1526.image151_thumb_23A2616A.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1526.image151_5F00_thumb_5F00_23A2616A.png" width="280" height="314" /></a> 

Accept the license agreement if you agree and download the Windows x64 version:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4774.image_57D68AB0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4774.image_5F00_57D68AB0.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2642.image_thumb_4353CBE3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2642.image_5F00_thumb_5F00_4353CBE3.png" width="435" height="336" /></a> 

Once you have installed the JDK there is still more to go!

### Workspace and additional components

Now we need some more components.

When you start Eclipse create a workspace in your Documents folder:</p> 

### <a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0820.image_653F2E67.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0820.image_5F00_653F2E67.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2185.image_thumb_12C04E2B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2185.image_5F00_thumb_5F00_12C04E2B.png" width="570" height="261" /></a>

If everything is OK, and Eclipse starts go to the Android SDK Manager by choosing _Window_, _Android SDK Manager._

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5241.image_74E1CA29.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-b
logs-components-weblogfiles/00-00-00-83-94-metablogapi/5241.image_5F00_74E1CA29.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5353.image_thumb_4FE409B0.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5353.image_5F00_thumb_5F00_4FE409B0.png" width="547" height="359" /></a> 

When the Android SDK Manager comes up, Close Eclipse then return to the SDK Manager and add ‘Google Play Services’ by checking it (under Extras) and install that and any updates that were detected for you:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8863.image_11EA78F2.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/8863.image_5F00_11EA78F2.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0383.image_thumb_63275100.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0383.image_5F00_thumb_5F00_63275100.png" width="533" height="405" /></a> 

When that finishes, go back and select _Google APIs_ and install that too:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7178.image_27D67BF3.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7178.image_5F00_27D67BF3.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2313.image_thumb_377917B5.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2313.image_5F00_thumb_5F00_377917B5.png" width="548" height="417" /></a> 

You can close the Android SDK Manager now.

### Configure the Emulator

In order to use Push notifications you need to configure an emulator that has the Google APIs.&#160; To do this open Eclipse and go to _Window, Android Virtual Device Manager_:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4401.image_52453DC1.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4401.image_5F00_52453DC1.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/0118.image_thumb_4238FFBB.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/0118.image_5F00_thumb_5F00_4238FFBB.png" width="553" height="324" /></a> 

Select the _Nexus S by Google_ and hit the _Create AVD…_ button:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6320.image_043F6EFD.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6320.image_5F00_043F6EFD.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5270.image_thumb_7AE63A79.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5270.image_5F00_thumb_5F00_7AE63A79.png" width="457" height="372" /></a> 

For _Target_ ensure you select _Google APIs_ as shown below (**important note**: if you don’t see that option available, then you did not follow the steps I have listed above.&#160; You must resolve this or you cannot test Push Notifications).

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3730.image_6EE44A45.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/3730.image_5F00_6EE44A45.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7888.image_thumb_5ED80C3F.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7888.image_5F00_thumb_5F00_5ED80C3F.png" width="270" height="467" /></a>

Now you can proceed with the Data and Push tutorials for Android!

### Footnotes

If you get this error when running the Push Tutorial:

E/AndroidRuntime(1701): Caused by: java.lang.NoClassDefFoundError: com.google.android.gms.gcm.GoogleCloudMessaging

You need to ensure you reference the GooglePlay Library in your project

Right Click on your project and choose properties:

Then Android, Add the google-play-services_lib as shown:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7167.image_1EF5249B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7167.image_5F00_1EF5249B.png"><img loading="lazy" title="image" style="display: inline;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6102.image_thumb_6508725F.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/6102.image_5F00_thumb_5F00_6508725F.png" width="538" height="471" /></a> 

Hit OK.

### Conclusion

There are a couple of nuances for setting up Google Play Services and the SDKs to get started, but this should help you tremendously!&#160; Drop me a note if you found this useful and be sure to follow me @jsandersrocks and my team @WSDevSol on twitter!