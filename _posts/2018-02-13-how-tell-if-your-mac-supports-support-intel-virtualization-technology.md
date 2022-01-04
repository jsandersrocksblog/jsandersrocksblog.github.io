---
id: 4475
title: 'How tell if your Mac Supports Support Intel&#174; Virtualization Technology'
date: 2018-02-13T09:12:41-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=4475
permalink: /2018/02/13/how-tell-if-your-mac-supports-support-intel-virtualization-technology/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How tell if your Mac Supports Support Intel&reg; Virtualization Technology" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/02/13/how-tell-if-your-mac-supports-support-intel-virtualization-technology/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="I was trying to see if my MacBook Air support HAXM for Android emulation and could not find a good resource to tell me how to find out what the processor number of my Mac was. So here you go! Open a Terminal Go to Finder and press Command + Shift + U Select Terminal..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How tell if your Mac Supports Support Intel&reg; Virtualization Technology" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2018/02/13/how-tell-if-your-mac-supports-support-intel-virtualization-technology/" />
    <meta name="twitter:description" content="I was trying to see if my MacBook Air support HAXM for Android emulation and could not find a good resource to tell me how to find out what the processor number of my Mac was. So here you go! Open a Terminal Go to Finder and press Command + Shift + U Select Terminal..." />
    
categories:
  - Uncategorized
---
I was trying to see if my MacBook Air support HAXM for Android emulation and could not find a good resource to tell me how to find out what the processor number of my Mac was. So here you go! 

Open a Terminal 

  * Go to Finder and press Command + Shift + U 
      * Select Terminal 
          * Type the following:&nbsp;&nbsp; **sysctl machdep.cpu.brand_string**</ul> 
        This returns something like this: machdep.cpu.brand_string: Intel(R) Core(TM) **i7-5650U** CPU @ 2.20GHz 
        
        The **BOLD** part is the processor number so continue to follow the instructions starting at step 2 below: [Does My Processor Support Intel® Virtualization Technology?](https://www.intel.com/content/www/us/en/support/articles/000005486/processors.html) 
        
        In my case, yes this process does! 
        
        As a short cut (don’t have to look up the processor number) simply type: <font size="2"><strong>sysctl machdep.cpu.features</strong> </font> 
        
        > <font size="2">and see if it contains <strong>VMX</strong></font>