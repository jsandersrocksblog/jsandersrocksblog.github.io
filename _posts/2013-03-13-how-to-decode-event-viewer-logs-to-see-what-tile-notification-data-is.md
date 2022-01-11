Using Push Notifications for my Windows Store app I needed to debug what message was being received for my Tile Notifications.&#160; The payload however was just a hex blob and THAT wasn’t too useful.&#160; Here is what I did to find the payload and see what was in it.

**Using the Event Viewer you can enable (if it isn’t already) the Push Notifications logging.**

To enable and view open the event viewer 

  * Hit the Windows key and then type: event viewer (click on Event Viewer).
  * Then expand this tree: Application and Services Logs/Microsoft/Windows/PushNotifications-Platform/Operational
  * Right click on this node to enable or disable logging at this level.&#160; 
  * Once it is enabled, send the push notification (however you are doing it).

To filter on the tile notification messages

  * Click on the Operational Node and choose ‘Filter Current Log…’ from the Actions pane on the right side.
  * Click on the ‘XML’ tab and check the box ‘Edit query manually’
  * Paste the below query in (cut from here paste into notepad and copy and paste from notepad):

<QueryList>  
&#160; <Query Id="0" Path="Microsoft-Windows-PushNotification-Platform/Operational">  
&#160;&#160;&#160; <Select Path="Microsoft-Windows-PushNotification-Platform/Operational"> \*[System[Provider[@Name=&#8217;Microsoft-Windows-PushNotifications-Platform&#8217;] and (EventID=1225)]] and \*[EventData[Data[@Name=&#8217;Verb&#8217;] and (Data=&#8217;NFY&#8217;)]]</Select>  
&#160; </Query>  
< /QueryList>

&#160;

  * Hit the ‘OK’ button

**You now will have a list of the notifications sent and the payloads.**

You can browse the notifications that have been received, but the ‘Payload’ is where the encoded tile data is.

To view the payload click on an event and select the ‘Details’ tab and hit the ‘XML View’ radio button.&#160; Then scroll down to the <EventData> section and find the <Data Name="**Payload**"> section.&#160; That string is the message sent to windows!

To decode the message you can use a public hex to string decoder or this handy Power Shell script.&#160; Replace the string in ‘’ with the payload:

\# paste Hex string you want to convert here  
$hexstring=&#8217;5469…’

\# size of char array  
$hexcharcount = $hexstring.Length

\# position in hexstring  
$i = 0 

$output=$null  
\# get every two chars and convert to ascii  
while ($i -le $hexcharcount -1) {  
&#160;&#160;&#160; $output = $output + \[Char\]\[Convert\]::ToInt32($hexstring[$i] + $hexstring[$i + 1] ,16)&#160;  
&#160;&#160;&#160; $i = $i + 2  
} 

$output&#160; 

Sample output:

Time: 2013-03-13T14:12:20Z  
Channel: 1;17014027897125354927  
Type: wns/tile  
Msg-Id: 107904C1BDA0828

<tile><visual><binding template="TileWideSmallImageAndText02"><image id="1" src="images/widget2\_thin\_25.png"/><text id="1">â17 mi</text><text id="2"></text><text id="3">30% Intensity</text  
>< text id="4">2% Area</text><text id="5"></text></binding><binding template="TileSquarePeekImageAndText01"><image id="1" src="images/widget2\_thin\_25_small.png"/><text id="1">â17 mi</text><  
text id="2"></text><text id="3">30% Intensity</text><text id="4">2% Area</text></binding></visual></tile> 

**So how do you find tile notifications just for your app?**

Get your App identity from and search for it.&#160; I use this tool from <a href="http://blogs.msdn.com/b/fiddler/archive/2011/12/10/fiddler-windows-8-apps-enable-loopback-network-isolation-exemption.aspx" target="_blank">Fiddler</a>.&#160; Look for the Display name and you want to copy the ‘AC Name’ by clicking on the ‘AC Name’ and choose ‘Copy selected column…’

&#160;

Go back to the filter and replace the AppUserModelId with your app id and append ‘!App’ (cut from here paste into notepad and copy and paste from notepad):

<QueryList>  
&#160; <Query Id="0" Path="Microsoft-Windows-PushNotification-Platform/Operational">  
&#160;&#160;&#160; <Select Path="Microsoft-Windows-PushNotification-Platform/Operational"> \*[System[Provider[@Name=&#8217;Microsoft-Windows-PushNotifications-Platform&#8217;] and (EventID=1010)]] and \*[EventData[Data[@Name=&#8217;AppUserModelId&#8217;] and (Data=&#8217;44083JeffAndDeeSoftware.jsandersPushDemo_x5q5wcd24ndqc!App&#8217;)]]  
&#160;&#160;&#160; </Select>  
&#160; </Query>  
< /QueryList>

Now you will see the ‘1010’ events associated with the tile update for your app!

You can note the time of the ‘1010’ event, clear the filter and look for the next event that is a 1225 event and that will most likely be the tile notification with the Payload that you can decode using the first method I specified.

**Closing notes**

The ‘General’ tab will give you a good idea of what the various log entries are.&#160; You can use the ‘XML’ tab to drill into the message.&#160; Enable and look through this event log.&#160; You will see all sorts of notifications related to establishing a channel and receiving push notifications.&#160; If you see any errors you can drill into them here.&#160; Happy Push Notifying!

Let me know if this was helpful!