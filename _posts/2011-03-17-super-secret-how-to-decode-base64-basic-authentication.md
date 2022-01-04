---
id: 563
title: 'Super secret.  How to decode Base64 Basic Authentication!'
date: 2011-03-17T11:51:38-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/
permalink: /2011/03/17/super-secret-how-to-decode-base64-basic-authentication/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
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
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
orig_parent_id:
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
  - "10142748"
orig_thread_id:
  - "757956"
  - "757956"
  - "757956"
  - "757956"
  - "757956"
  - "757956"
  - "757956"
  - "757956"
  - "757956"
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
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2011/03/17/super-secret-how-to-decode-base64-basic-authentication.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Super secret.  How to decode Base64 Basic Authentication!" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2011/03/17/super-secret-how-to-decode-base64-basic-authentication/" />
    <meta name="twitter:description" content="OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp; When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: string&nbsp;secret&nbsp;=&nbsp;Convert.ToBase64String(System.Text.Encoding.UTF8.GetBytes(&#8220;jeff:mypassword&#8221;));.&nbsp;&nbsp;To decode a username and password from..." />
    
categories:
  - Uncategorized
tags:
  - HTTP Troubleshooting
  - IE
---
OK, really not that secret.&nbsp; Basic Authentication headers are pretty simple.&nbsp;&nbsp;

When the server returns 401 and the header:&nbsp;WWW-Authenticate: Basic.&nbsp; The server wants you to send the username and password in this format:&nbsp; jeff:mypassword and then encode this as a Base64String.&nbsp; You can encode this with this code: <span style="line-height: 115%; font-family: Consolas; color: blue; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;">string</span><span style="line-height: 115%; font-family: Consolas; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;">&nbsp;secret&nbsp;=&nbsp;<span style="color: #2b91af;">Convert</span>.ToBase64String(System.Text.<span style="color: #2b91af;">Encoding</span>.UTF8.GetBytes(<span style="color: #a31515;">&#8220;jeff:mypassword&#8221;</span>));.&nbsp;&nbsp;<span style="font-family: Arial;">To decode a username and password from a header that you send (found in the Authorization: Basic&#8221; header)&nbsp;pass that string to this: <span style="line-height: 115%; font-family: Consolas; color: blue; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;">string</span><span style="line-height: 115%; font-family: Consolas; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;">&nbsp;decodedSecret&nbsp;=&nbsp;System.Text.<span style="color: #2b91af;">Encoding</span>.UTF8.GetString(<span style="color: #2b91af;">Convert</span>.FromBase64String(secret));</span></span></span>

<span style="line-height: 115%; font-family: Consolas; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;"><span style="font-family: Arial;"><span style="line-height: 115%; font-family: Consolas; font-size: 10pt; mso-fareast-font-family: 'Times New Roman'; mso-ansi-language: EN-US; mso-fareast-language: EN-US; mso-bidi-language: AR-SA;"></span></span></span>