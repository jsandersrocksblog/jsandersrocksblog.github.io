---
id: 4455
title: Using/Installing Fiddler on Mac OS
date: 2018-02-08T16:57:40-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=4455
permalink: /2018/02/08/usinginstalling-fiddler-on-mac-os/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using/Installing Fiddler on Mac OS" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/02/08/usinginstalling-fiddler-on-mac-os/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I could not find a good walkthrough so here is one for you.&nbsp; Disclaimer:&nbsp; This is on the latest OS and Latest version of Fiddler Beta Steps Install Mono – You can do this many ways but I wanted to do Xamarin development so I downloaded and installed Visual Studio for Mac and installed..." />
    <meta property="og:image" content="/assets/images/2018/02/capture20180208162842248_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using/Installing Fiddler on Mac OS" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/02/08/usinginstalling-fiddler-on-mac-os/" />
    <meta name="twitter:description" content="Overview I could not find a good walkthrough so here is one for you.&nbsp; Disclaimer:&nbsp; This is on the latest OS and Latest version of Fiddler Beta Steps Install Mono – You can do this many ways but I wanted to do Xamarin development so I downloaded and installed Visual Studio for Mac and installed..." />
    <meta name="twitter:image" content="/assets/images/2018/02/capture20180208162842248_thumb.png" />
    
categories:
  - Uncategorized
---


I could not find a good walkthrough so here is one for you.&nbsp; Disclaimer:&nbsp; This is on the latest OS and Latest version of Fiddler Beta

## Steps

Install Mono – You can do this many ways but I wanted to do Xamarin development so I downloaded and installed Visual Studio for Mac and installed Mono as part of that installation:

<a href="https://www.visualstudio.com/vs/visual-studio-mac" target="_blank">https://www.visualstudio.com/vs/visual-studio-mac</a>

Download Fiddler &#8211; <a title="https://www.telerik.com/download/fiddler" href="https://www.telerik.com/download/fiddler/fiddler-osx-beta" target="_blank">https://www.telerik.com/download/fiddler/fiddler-osx-beta</a>

You did step 1 of the instructions on this page already if you installed Visual Studio.

Move the ‘fiddler-mac’ folder somewhere you have write access to.&nbsp; I chose my Applications Folder.&nbsp; Open in Finder:

[<img loading="lazy" title="capture20180208162842248" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180208162842248" src="/assets/images/2018/02/capture20180208162842248_thumb.png" width="244" height="232" />](/assets/images/2018/02/capture20180208162842248.png)

and then just drag and drop it into Applications:

[<img loading="lazy" title="capture20180208162949169" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180208162949169" src="/assets/images/2018/02/capture20180208162949169_thumb.png" width="244" height="213" />](/assets/images/2018/02/capture20180208162949169.png)

And here it is!

&nbsp;[<img loading="lazy" title="capture20180208163026081" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180208163026081" src="/assets/images/2018/02/capture20180208163026081_thumb.png" width="490" height="281" />](/assets/images/2018/02/capture20180208163026081.png)

Next find the Terminal app in LaunchPad and run it:

[<img loading="lazy" title="capture20180208163159656" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180208163159656" src="/assets/images/2018/02/capture20180208163159656_thumb.png" width="244" height="165" />](/assets/images/2018/02/capture20180208163159656.png)

Navigate to the Applications folder: **cd /Applications/fiddler-mac/**

Pre the instructions I ran this:&nbsp; **mono fiddler.exe**

**And got this error:**

WARNING: The Carbon driver has not been ported to 64bits, and very few parts of Windows.Forms will work properly, or at all 

Stacktrace: 

&nbsp; at <unknown> <0xffffffff> 

&nbsp; at (wrapper managed-to-native) System.Windows.Forms.XplatUICarbon.CGDisplayBounds (intptr) [0x00002] in <36fbc38531724d82b10aef6ebafea6e9>:0 

**And this error because I never ran/accepted the xcodebuild license :**&nbsp; Agreeing to the Xcode/iOS license requires admin privileges, please run “sudo xcodebuild -license” and then retry this command.

To fix this I first ran: **sudo xcodebuild –license**

and then used the correct 32 bit command to run mono and fiddler: **mono &#8211;arch=32 fiddler.exe**

You next have to allow changes to your networking so you will be prompted:

[<img loading="lazy" title="capture20180208164015601" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20180208164015601" src="/assets/images/2018/02/capture20180208164015601_thumb.png" width="625" height="337" />](/assets/images/2018/02/capture20180208164015601.png)

And Fiddler will start running!

When you start capture, again you need to enter your password to reset the proxy.

## 

## Conclusion

Pretty simple but like I said, I had no luck finding a good workaround and the fiddler instructions did not have the **sudo xcodebuild –license, nor the **mono &#8211;arch=32 fiddler.exe**** commands

Drop me a note if you found this useful!