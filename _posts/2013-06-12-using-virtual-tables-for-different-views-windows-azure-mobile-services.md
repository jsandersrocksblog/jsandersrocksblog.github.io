Building on my last post ([Move Your Client Logic to the Server &#8211; Windows Azure Mobile Services](http://blogs.msdn.com/b/jpsanders/archive/2013/06/12/move-your-client-logic-to-the-server-windows-azure-mobile-services.aspx)) I will show you how to create a Virtual (or dummy) table to give you a different view of your TodoItem table.&#160; This Virtual table will not contain any records however.

In this case, let’s assume you did not want to change your TodoItem table read script because you do need the full table with complete items elsewhere in your application.

Start by returning the read script back to it’s original form.

Navigate to the TodoItem read script and hit the ‘Clear’ icon at the bottom of the page to restore the script:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7356.image_22358A6B.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/7356.image_5F00_22358A6B.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/2806.image_thumb_20F0F18C.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/2806.image_5F00_thumb_5F00_20F0F18C.png" width="717" height="438" /></a>

&#160;

Your Read script should _only_ contain the request.execute(); method as it originally did.

Next define a new table called ‘todoitemcomplete’ by choosing the CREATE icon in the DATA tab:

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/5226.image_6B0BFC71.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/5226.image_5F00_6B0BFC71.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1351.image_thumb_188D1C35.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1351.image_5F00_thumb_5F00_188D1C35.png" width="283" height="317" /></a>

Be sure to set the appropriate permission levels as well

&#160;

<a href="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4503.image_1101ACC8.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/4503.image_5F00_1101ACC8.png"><img loading="lazy" title="image" style="display: inline; background-image: none;" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/1460.image_thumb_37639013.png" original-url="http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-blogs-components-weblogfiles/00-00-00-83-94-metablogapi/1460.image_5F00_thumb_5F00_37639013.png" width="369" height="278" /></a>

Next we will modify the four server scripts to use the TodoItem table and not the newly created table for their operations.

Here is the read script (actually the only one used in my example):

&#160;

<pre class="code"><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">read(query, user, request) {
    </span><span style="background: white; color: blue;">var </span><span style="background: white; color: black;">todoItemsTable = tables.getTable(</span><span style="background: white; color: rgb(163, 21, 21);">'TodoItem'</span><span style="background: white; color: black;">);
    todoItemsTable.where({ complete: </span><span style="background: white; color: blue;">false </span><span style="background: white; color: black;">}).read({ success: respondOK });
    </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">respondOK(results) {
        request.respond(statusCodes.OK, results);
    }
    </span><span style="background: white; color: green;">// no! request.execute();
</span><span style="background: white; color: black;">}</span></pre>

The next step is to setup for reading from this dummy table an mainpage.xaml.cs:

&#160;

<pre class="code"><span style="background: white; color: black;">    </span><span style="background: white; color: green;">//Strongly typed class for dummy table is same structure as old table
    </span><span style="background: white; color: blue;">public class </span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">: </span><span style="background: white; color: rgb(43, 145, 175);">TodoItem
    </span><span style="background: white; color: black;">{
    }
    </span><span style="background: white; color: blue;">public sealed partial class </span><span style="background: white; color: rgb(43, 145, 175);">MainPage </span><span style="background: white; color: black;">: </span><span style="background: white; color: rgb(43, 145, 175);">Page
    </span><span style="background: white; color: black;">{
        </span><span style="background: white; color: green;">//Changed the items collection to the new class
        </span><span style="background: white; color: blue;">private </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceCollection</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">, </span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">&gt; items;
        </span><span style="background: white; color: green;">//Added a reference to the dummy table
        </span><span style="background: white; color: blue;">private </span><span style="background: white; color: rgb(43, 145, 175);">IMobileServiceTable</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">&gt; todoTableComplete = </span><span style="background: white; color: rgb(43, 145, 175);">App</span><span style="background: white; color: black;">.MobileService.GetTable&lt;</span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">&gt;();
        </span><span style="background: white; color: green;">//For now... keep a reference to the old table for Update and Insert operations
        </span><span style="background: white; color: blue;">private </span><span style="background: white; color: rgb(43, 145, 175);">IMobileServiceTable</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: rgb(43, 145, 175);">TodoItem</span><span style="background: white; color: black;">&gt; todoTable = </span><span style="background: white; color: rgb(43, 145, 175);">App</span><span style="background: white; color: black;">.MobileService.GetTable&lt;</span><span style="background: white; color: rgb(43, 145, 175);">TodoItem</span><span style="background: white; color: black;">&gt;();
</span></pre>

&#160;

Fix up any references that used a TodoItem in this collection by casting to a TodoItemComplete such as this:

<pre class="code"><span style="background: white; color: black;">  items.Add(todoItem </span><span style="background: white; color: blue;">as </span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">);</span></pre>

<pre class="code"><span style="background: white; color: black;">  </span><span style="background: white; color: black;">items.Remove(item </span><span style="background: white; color: blue;">as </span><span style="background: white; color: rgb(43, 145, 175);">TodoItemComplete</span><span style="background: white; color: black;">);</span></pre>

<font color="#000000" face="Courier New">&#160;</font>

And change the RefreshTodoItems() to use the new todoTableComplete:

<pre class="code"><span style="background: white; color: blue;">private async void </span><span style="background: white; color: black;">RefreshTodoItems()
        {
            </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceInvalidOperationException </span><span style="background: white; color: black;">exception = </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">;
            </span><span style="background: white; color: blue;">try
            </span><span style="background: white; color: black;">{
                </span><span style="background: white; color: green;">// This code refreshes the entries in the list view by querying the TodoItems table.
                // The query excludes completed TodoItems
                </span><span style="background: white; color: black;">items =  </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">todoTableComplete.ToCollectionAsync();
                </span><span style="background: white; color: green;">//items = await todoTable.ToCollectionAsync();
            </span><span style="background: white; color: black;">}</span></pre>

&#160;

Now you have a Virtual table that will give you a view of complete items only with the logic on the server.

**Further Discussion**

I only discussed the Read script but you can extend this to the other scripts.

This has the downfall that the query parameters passed to the Read (if any) are difficult to extract and pass on to the table read.

A better option may be to use parameters in the query for the special cases (see my next post).

Let me know if this was useful to you!

&#160;

-Jeff

&#160;

&#160;

Ref: [http://www.windowsazure.com/en-us/develop/mobile/how-to-guides/work-with-server-scripts/#access-tables](http://www.windowsazure.com/en-us/develop/mobile/how-to-guides/work-with-server-scripts/#access-tables "http://www.windowsazure.com/en-us/develop/mobile/how-to-guides/work-with-server-scripts/#access-tables")