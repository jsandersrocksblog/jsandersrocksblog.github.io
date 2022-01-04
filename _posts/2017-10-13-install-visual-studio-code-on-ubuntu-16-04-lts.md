---
id: 3825
title: Install Visual Studio Code on Ubuntu 16.04 LTS
date: 2017-10-13T14:01:36-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=3825
permalink: /2017/10/13/install-visual-studio-code-on-ubuntu-16-04-lts/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Install Visual Studio Code on Ubuntu 16.04 LTS" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/10/13/install-visual-studio-code-on-ubuntu-16-04-lts/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview I had trouble getting Visual Studio Code to install by simple clicking on the package from https://code.visualstudio.com.&nbsp; Whether I tried do download or use Ubuntu Software to install this I got an error: status code 400: Bad Request. Solution Download the file, then right click on the desktop and open a terminal: Type cd..." />
    <meta property="og:image" content="/assets/images/2017/10/capture20171013144839126_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Install Visual Studio Code on Ubuntu 16.04 LTS" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/10/13/install-visual-studio-code-on-ubuntu-16-04-lts/" />
    <meta name="twitter:description" content="Overview I had trouble getting Visual Studio Code to install by simple clicking on the package from https://code.visualstudio.com.&nbsp; Whether I tried do download or use Ubuntu Software to install this I got an error: status code 400: Bad Request. Solution Download the file, then right click on the desktop and open a terminal: Type cd..." />
    <meta name="twitter:image" content="/assets/images/2017/10/capture20171013144839126_thumb.png" />
    
categories:
  - Uncategorized
---
 

I had trouble getting Visual Studio Code to install by simple clicking on the package from <https://code.visualstudio.com>.&nbsp; Whether I tried do download or use Ubuntu Software to install this I got an error: status code 400: Bad Request.

# Solution

Download the .deb package from the Visual Studio Code site, then right click on the desktop and open a terminal:

[<img loading="lazy" title="capture20171013144839126" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013144839126" src="/assets/images/2017/10/capture20171013144839126_thumb.png" width="146" height="85" />](/assets/images/2017/10/capture20171013144839126.png)

Go to the Download directory.&nbsp; Type _cd Dow_ and hit the tab key to complete the directory name:

[<img loading="lazy" title="capture20171013144931211" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013144931211" src="/assets/images/2017/10/capture20171013144931211_thumb.png" width="394" height="188" />](/assets/images/2017/10/capture20171013144931211.png)

Type _ls_ to list the files in the Download directory and find the code_ package:

[<img loading="lazy" title="capture20171013145032064" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013145032064" src="/assets/images/2017/10/capture20171013145032064_thumb.png" width="507" height="182" />](/assets/images/2017/10/capture20171013145032064.png)

Install the package with this command _sudo dpkg –i code_ (and hit tab to complete the name):

[<img loading="lazy" title="capture20171013145404656" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013145404656" src="/assets/images/2017/10/capture20171013145404656_thumb.png" width="710" height="160" />](/assets/images/2017/10/capture20171013145404656.png)

Provide your password and Visual Studio Code will install.

**NOTE:** if you get dependency errors when using dpkg with a package, simply type _sudo apt-get install –f_&nbsp; which will download and install missing dependencies and configure them.

Now, find it and run it:

[<img loading="lazy" title="capture20171013145544701" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013145544701" src="/assets/images/2017/10/capture20171013145544701_thumb.png" width="244" height="228" />](/assets/images/2017/10/capture20171013145544701.png)

And you can right click on the icon in the side bar (Launcher) and choose _Lock to Launcher_ so you don’t need to hunt for it again!

[<img loading="lazy" title="capture20171013145638693" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20171013145638693" src="/assets/images/2017/10/capture20171013145638693_thumb.png" width="244" height="101" />](/assets/images/2017/10/capture20171013145638693.png)

&nbsp;

# 

# Conclusion

Just a quick blog to help you out.&nbsp; If you find it helpful, please let me know!

Note:&nbsp; You can kick of Visual Studio Code in a terminal window if you are command line guy like me by simply typing _code_ in the terminal.

## References

[https://help.ubuntu.com/lts/serverguide/dpkg.html](https://help.ubuntu.com/lts/serverguide/dpkg.html "https://help.ubuntu.com/lts/serverguide/dpkg.html")

[https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache](https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache "https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache")