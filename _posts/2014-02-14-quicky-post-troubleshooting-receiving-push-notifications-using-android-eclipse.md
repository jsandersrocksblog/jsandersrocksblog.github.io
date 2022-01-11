## Issue

I confirmed Windows Azure Mobile Services was able to communicate with GCM (Google Cloud Messaging) and had no errors sending the notification to GCM.&#160; But how could I see how this got or didn’t get to my Android Emulator?

## Server side

I was able to confirm that there were no errors by dumping out the result of doing a push.gcm.send using this script (from our tutorial):

<pre class="code"><span style="background: white; color: black;">push.gcm.send(item.handle, item.text, {
    success: </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">(response) {
        console.log(</span><span style="background: white; color: rgb(163, 21, 21);">'Push notification sent: '</span><span style="background: white; color: black;">, response);
    }, error: </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">(error) {
        console.log(</span><span style="background: white; color: rgb(163, 21, 21);">'Error sending push notification: '</span><span style="background: white; color: black;">, error);
    }
});</span></pre>

And opening the LOGS tab saw this result:

Push notification sent: {  
  
multicast_id: 4877295250689814000,  
  
success: 1,  
  
failure: 0,  
  
canonical_ids: 0,  
  
results: [  
  
{ <font style="background-color: rgb(255, 255, 0);">message_id</font><font style="background-color: rgb(255, 255, 0);">: &#8216;0:1392395679428889%0d284a0ef9fd7ecd&#8217;</font> } ], invalidIds: [], updatedIds: {} }

So how to see what if anything is happening on the client?&#160; The _message_id_ looks promising!

## Client side

<p align="left">
  Running the program from Eclipse and ensuring <em>Log Cat</em> is running I was able to confirm that I am getting the message from the GCM service!
</p>

02-14 11:34:39.769: I/GCM(624): GCM message com.example.jsanderspushgcm <font style="background-color: rgb(255, 255, 0);">0:1392395679428889%0d284a0ef9fd7ecd</font>

I clicked on the message to set up a verbose filter for GCM:



And now I can easily filter and see what GCM logs are showing me!

## Conclusion

I could also use fiddler as a proxy to see network traffic but with a little logging and knowledge of the available server and client side tools, was able to correlate the GCM messages quickly!

Let me know if this was useful to you!