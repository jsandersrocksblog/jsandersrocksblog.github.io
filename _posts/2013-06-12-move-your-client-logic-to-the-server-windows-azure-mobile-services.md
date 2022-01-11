The Client Libraries for Windows Azure Mobile Services are powerful and allow you to embed logic within your client application.&#160; The quickstart and sample applications give you a great overview on how to implement logic on the client to get the view of data you would like in the client application.&#160; A different architecture for you would be to move this view logic to the server using the Server Scripting capability of Windows Azure Mobile Services so that you do not have to duplicate the client side logic for each platform that you target as a client!&#160; 

**NOTE:** There is nothing wrong with having your query logic client side but sometimes it makes sense to have it all on the server.&#160; For example if it is a complicated query and every platform needs to implement it, consider moving it server side.

For this example I will to take the C# Windows Store app Todo sample project that is generated for you from the Azure Management Dashboard and move the client side logic into the server.&#160; In this case we never want any view besides the one that excludes the complete items so I will modify the client code to remove the filtering logic and add it to the server read script.&#160; Then I will show you how to modify the C# Windows Phone sample to take advantage of these views.

**Follow along with me to get started!**

Create a new Mobile Service and follow the steps to create your TodoItem table and download and run a new Windows Store app (C#).

Ensure you can add items and mark several of them complete.

Create a new Windows Phone app and ensure you can see the data you see in the store app and it is the same (completed items should be hidden).

&#160;

**Modify your code in the Windows Store app to remove the client logic**

Open Mainpage.xaml.cs and remove the filtering logic when you read the table in RefreshTodoItems:

<pre class="code"><span style="background: white; color: black;">  </span><span style="background: white; color: blue;">private async void </span><span style="background: white; color: black;">RefreshTodoItems()
        {
            </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceInvalidOperationException </span><span style="background: white; color: black;">exception = </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">;
            </span><span style="background: white; color: blue;">try
            </span><span style="background: white; color: black;">{
                </span><span style="background: white; color: green;">// This code refreshes the entries in the list view by querying the TodoItems table.
                // The query excludes completed TodoItems
                </span><span style="background: white; color: black;">items = </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">todoTable.ToCollectionAsync();
            }
         </span></pre>

Run your app to verify that even the items in your list appear briefly but then go away!&#160; Put a breakpoint on CheckBoxComplete_checked to see why they appear briefly.&#160;&#160; Leave this breakpoint in place to verify after you modify the server read script, you are not retrieving completed items (you will not hit this breakpoint after the server side change).

Now, go to your DATA tab in your mobile service, click on your TodoItem table and choose the SCRIPT tab.&#160; Choose the Read script from the dropdown and we will move the login to only return completed items (since that is the only thing we need to read in our app anyhow).

<pre class="code"><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">read(query, user, request) {
    query.where({ complete: </span><span style="background: white; color: blue;">false </span><span style="background: white; color: black;">});
    request.execute();
}</span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

<pre class="code"><span style="background: white; color: black;"></span></pre>

Test you Windows Store app with the breakpoint still set on CheckBoxComplete_checked to verify you are not longer retrieving complete items.

Now go to your Phone application and remove the filter from RefreshTodoItems() like you did in your Windows Store app and test this code!

<pre class="code"><span style="background: white; color: black;">        </span><span style="background: white; color: blue;">private async void </span><span style="background: white; color: black;">RefreshTodoItems()
        {
            </span><span style="background: white; color: green;">// This code refreshes the entries in the list view be querying the TodoItems table.
            // The query excludes completed TodoItems
            </span><span style="background: white; color: blue;">try
            </span><span style="background: white; color: black;">{
                items = </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">todoTable.ToCollectionAsync();
            }
</span></pre>

&#160;

You have now successfully moved your client logic server side!

Obviously this is a super simple example of moving Client Logic server side.&#160; You would want to do this whenever you have a complex query as well so that you do not burden each of the client platforms (I only showed you two) with implementing the same logic.&#160; In my next post I will show you how to implement the same Server side logic to access complete items only in the read form TodoItem but in a dummy table so that you do not modify the TodoItem table.

&#160;

Let me know if this was useful to you!

&#160;

-Jeff