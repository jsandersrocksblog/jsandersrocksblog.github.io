The .NET framework version 2.0 has the ability to get the IE proxy Settings and use them when making a WebRequest.&nbsp; However it only will read the http static proxy and not use the https value when specified.&nbsp; See this example:

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/NE.0HttpWebRequestdoesnotusethehttpsPro_C8D3/clip_image002_2.jpg" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/NE.0HttpWebRequestdoesnotusethehttpsPro_C8D3/clip_image002_2.jpg"><img loading="lazy" style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="clip_image002" border="0" alt="clip_image002" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/NE.0HttpWebRequestdoesnotusethehttpsPro_C8D3/clip_image002_thumb.jpg" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/NE.0HttpWebRequestdoesnotusethehttpsPro_C8D3/clip_image002_thumb.jpg" width="391" height="417" /></a>

I would expect this code to return <http://secureproxy:8080> for the proxy when I specify&nbsp; <https://someserver> as an argument to this code:

using System;  
using System.Net;  
public class Test {  
public static void Main(string[] args)&nbsp;&nbsp;&nbsp;&nbsp; { 

IWebProxy iwp20 = WebRequest.DefaultWebProxy;  
Console.WriteLine(iwp20.GetProxy(new Uri(args[0])).ToString());  
HttpWebRequest aReq = HttpWebRequest.Create(args[0])as HttpWebRequest;  
Console.WriteLine(aReq.Proxy.GetProxy(new Uri(args[0])));  
}  
} 

It does not!&nbsp; It returns <http://proxy:8080>.

This is a problem with the 2.0 framework.&nbsp; Thankfully it HAS been fixed in the 4.0 framework!

An alternative is to code the https proxy information in the code or set in in the application .config file.

Let me know if you found this Blog entry useful!