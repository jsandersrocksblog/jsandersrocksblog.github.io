---
id: 753
title: Using HttpWebRequest with Credential Manager
date: 2009-09-03T14:39:00-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2009/09/03/using-httpwebrequest-with-credential-manager/
permalink: /2009/09/03/using-httpwebrequest-with-credential-manager/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
orig_site_id:
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
orig_post_id:
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
orig_parent_id:
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
  - "9891052"
orig_thread_id:
  - "674541"
  - "674541"
  - "674541"
  - "674541"
  - "674541"
  - "674541"
  - "674541"
  - "674541"
  - "674541"
orig_application_key:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_id:
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
orig_post_author_username:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_created:
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
orig_is_approved:
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
orig_attachment_count:
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
orig_url_title:
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2009/09/03/using-httpwebrequest-with-credential-manager.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Using HttpWebRequest with Credential Manager" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta property="og:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Using HttpWebRequest with Credential Manager" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2009/09/03/using-httpwebrequest-with-credential-manager/" />
    <meta name="twitter:description" content="A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well). In Internet..." />
    <meta name="twitter:image" content="http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg" />
    
categories:
  - Uncategorized
tags:
  - HttpWebRequest
  - Internet Explorer
  - WinInet
---
A little know fact is that the .NET framework will use the stored credentials in the Credential Manager when accessing a network resource if the credentials exist for that particular resource (host).&nbsp; I intend to clear up how this functionality works for the HttpWebRequests (you could extend this to WebService calls as well).

In Internet Explorer, you can access a website that challenges you for credentials by filling in a username and password when the dialog is presented and asks you for authentication.&nbsp; If you check ‘Remember my password’ these credentials will be stored in protected storage (Credential Manager).&nbsp; You can see the stored credentials by running this command: Control Keymgr.dll.&nbsp; These credentials are stored in protected storage in each user’s My folder.&nbsp; You can store these credentials by using control Keymgr.dll, by using the interface available in Internet Explorer or by using C++/C and the Credentials API’s (Such as CredWrite).&nbsp; If you do not check ‘Remember my password’ then these credentials are not stored in Credential Manager and .NET will not be able to use these credentials.

The .NET framework can use the currently logged on user’s credentials to authenticate but if you have a web site that requires different credentials you can use store these credentials in Credential Manager and .NET will use these credentials instead of the currently logged on user credentials.&nbsp; To illustrate this I put together a real simple sample.

The target web server in my sample is jpsandershv2003.&nbsp; I only enabled Windows Integrated Authentication in IIS on that box.&nbsp; I then created a User ID JPSGuest on that IIS machine.&nbsp; Finally I wrote a real simple .NET console application to create an HttpWebRequest and get the response.<p style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none" class=MsoNormal>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp; </span><span style="COLOR: #2b91af">HttpWebRequest</span> aReq; <?xml:namespace prefix = o ns = "urn:schemas-microsoft-com:office:office" /><o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none" class=MsoNormal>

<span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp; </span><span style="COLOR: #2b91af">HttpWebResponse</span> aResp;<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt">&nbsp;&nbsp; aReq = <span style="COLOR: #2b91af">WebRequest</span>.Create(<span style="COLOR: #a31515">&#8220;<a href="http://jpsandershv2003/" mce_href="http://jpsandershv2003/"><font color=#0000ff>http://jpsandershv2003/</font></a>&#8220;</span>) <span style="COLOR: blue">as</span> <span style="COLOR: #2b91af">HttpWebRequest</span>;<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt">&nbsp;&nbsp; aReq.UseDefaultCredentials = <span style="COLOR: blue">true</span>;<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;</span><span style="mso-spacerun: yes">&nbsp; </span>aResp = aReq.GetResponse() <span style="COLOR: blue">as</span> <span style="COLOR: #2b91af">HttpWebResponse</span>;<o:p></o:p></span></p> <p style="MARGIN: 0in 0in 0pt; mso-layout-grid-align: none" class=MsoNormal><span style="FONT-FAMILY: 'Courier New'; FONT-SIZE: 10pt; mso-no-proof: yes"><span style="mso-spacerun: yes">&nbsp;</span><span style="mso-spacerun: yes">&nbsp; </span>aResp.Close();<o:p></o:p></span></p> 

When you run this code it will first look in the credential manager first for the credentials for attaching to jpsandershv2003 and if found use those, otherwise the Currently Logged on User credentials will be used.&nbsp; In my example since I was logged on as jpsanders to my machine I expect that the credentials used should be my domain credentials jpsanders.&nbsp; I turned on logging and ensured the IIS log was logging the username and sure enough, jpsanders was authenticated in IIS.

My next goal was to see if I could change this default behavior and make it log on using the jpsandershv2003\JPSGuest user credentials.&nbsp; Using the command control keymgr.dll I was able to add the credential as a Windows logon credential:

&nbsp;

![](http://ko3ggw.blu.livefilestore.com/y1pVpjI_RKFEB2pkzsElIsdesEuvV2lOuZK3qpILB8pQ4CQiCEO5zGlw_hD7OSQb35-UPU6E8Ry90uVwx3GpIzUVxUhk_2OhOHW/CredManAdd.jpg) <p mce_keep="true">&nbsp;</p> 

Now when I ran the console application I saw success in the IIS log!&nbsp; I was logging in now as JPSGuest.

Taking a fiddler (<a href="http://fiddlertool.com/" mce_href="http://fiddlertool.com">http://fiddlertool.com</a>) trace of Internet Explorer also confirmed I was using the stored credentials and these were NTLM credentials.&nbsp; 

Domain: jpsandershv2003  
User: JPSGuest  
Host: JPSANDERS3

Can I store credentials and have it use Kerberos?&nbsp; In theory yes, simply type domain based credentials in.&nbsp; However I could not test this because I only have one logon to my domain and you cannot save your currently logged on credentials in the Credential Manager.&nbsp; 

What about basic and digest?&nbsp; NO, this would be a huge security hole.&nbsp; Can you tell me why (it should be obvious)?

Note that the credentials used are independent of the PORT used.&nbsp; So if I change the server to bind HTTP traffic on port 8089 then change my code to access <a href="http://jpsandershv2003:8089/" mce_href="http://jpsandershv2003:8089">http://jpsandershv2003:8089</a> the code will still access the web site using the stored credentials.

To revert back to the interactive user, simply delete the credentials stored for jpsandershv2003.

**Further observations**

What is the second radio button for (A Web site or program credentials)?&nbsp; This is for programs that are writing against the credentials API directly.&nbsp; Some examples of this are Terminal Server (RDP) and Windows Live credentials.&nbsp; Here are some great links about the APIs:  
<a href="http://msdn.microsoft.com/en-us/library/aa374789(VS.85).aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa374789(VS.85).aspx">http://msdn.microsoft.com/en-us/library/aa374789(VS.85).aspx</a>  
<a href="http://msdn.microsoft.com/en-us/library/aa480470.aspx" mce_href="http://msdn.microsoft.com/en-us/library/aa480470.aspx">http://msdn.microsoft.com/en-us/library/aa480470.aspx</a>

NOTE: Because the credentials are stored in the context of the logged on user, this technique will not work for non interactive user accounts such as the service accounts and ASP.NET applications.<p mce_keep="true">&nbsp;</p> <p mce_keep="true">Please send me&nbsp;a quick note if you found this Blog helpful!</p> <p mce_keep="true">&nbsp;</p> <p mce_keep="true">&nbsp;</p>