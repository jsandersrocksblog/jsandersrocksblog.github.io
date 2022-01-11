We document how to send push notifications using Mobile Services fairly well.&#160; You can use the wns object and push the notification.&#160; This is documented here:

<a title="http://www.windowsazure.com/en-us/develop/mobile/tutorials/get-started-with-push-dotnet/" href="http://www.windowsazure.com/en-us/develop/mobile/tutorials/get-started-with-push-dotnet/" target="_blank">Get started with push notifications in Mobile Services</a>&#160; 

<a title="http://www.windowsazure.com/en-us/develop/mobile/tutorials/push-notifications-to-users-dotnet/" href="http://www.windowsazure.com/en-us/develop/mobile/tutorials/push-notifications-to-users-dotnet/" target="_blank">Push notifications to users by using Mobile Services</a>

What is not documented until now is how to expire the notification after a certain time period.&#160; This is actually very easy (especially now that I have documented it)!

What you want to do is to pass this header: X-WNS-TTL and the number of Seconds you wish this notification to live.&#160; Here is an example of how to do this:

&#160;

push.wns.sendTileSquareBlock(  
&#160;&#160; item.channel,  
&#160;&#160; { text1: item.id, text2: item.text },  
&#160;&#160; {  
&#160;&#160;&#160;&#160;&#160;&#160; headers: { &#8216;X-WNS-TTL&#8217;: 30 },  
&#160;&#160;&#160;&#160;&#160;&#160; success: function (error, result) {  
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; console.log(error);  
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; console.log(result);  
&#160;&#160;&#160;&#160;&#160;&#160; }  
&#160;&#160; }); 

This example will expire the tile 30 seconds from now.&#160; The key here is that the second object passed now has the _headers_ option specified (<a title="https://github.com/tjanczuk/wns" href="https://github.com/tjanczuk/wns" target="_blank">https://github.com/tjanczuk/wns</a>).

Here is some further documentation on that header: 

<a title="http://msdn.microsoft.com/en-us/library/windows/apps/hh465435.aspx#pncodes_x_wns_ttl" href="http://msdn.microsoft.com/en-us/library/windows/apps/hh465435.aspx#pncodes_x_wns_ttl" target="_blank">Push notification service request and response headers &#8211; X-WNS-TTL</a>

&#160;

Let me know if this helps!