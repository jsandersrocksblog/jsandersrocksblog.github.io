In my two previous posts I discussed how to move your table filter logic server side, and how to use Virtual tables to get different views of data.&#160; In this blog post I will show you how to pass parameters to you read script to get different views of the data.

In this example, the default view of this table will be to filter the complete items (since my services all require this as a default view) and still expose a way to get the unfiltered data back if I wish.&#160; This will also preserve the query and select parameters passed to the read in the event I wish to use those!

**Server Script**

The server script will use a jump table to execute a code path based on the parameter passed in.&#160; It also has stubbed out another operation to show how this would be done.

<pre class="code"><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">read(query, user, request) {
    </span><span style="background: white; color: green;">//console.log(request.parameters.operation);
    </span><span style="background: white; color: blue;">var </span><span style="background: white; color: black;">dispatch = {
        op1: operation1,
        nofilters: operation2,
    }
    </span><span style="background: white; color: green;">//doesn't return valid JSON but shows how you might
    // execute another function based on different parameters passed in
    </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">operation1(query, user, request) {
        request.respond(200, </span><span style="background: white; color: rgb(163, 21, 21);">"this result is from operation1"</span><span style="background: white; color: black;">);
    }
    </span><span style="background: white; color: green;">// no server side filter applied
    </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">operation2(query, user, request) {
        request.execute();
    }
    </span><span style="background: white; color: green;">// if we have parameters and a matching entry in the jump table we have defined
    // dispatch it!
    </span><span style="background: white; color: blue;">if </span><span style="background: white; color: black;">(request.parameters.operation && dispatch.hasOwnProperty(request.parameters.operation)) {
        dispatch[request.parameters.operation](query, user, request);
        </span><span style="background: white; color: blue;">return</span><span style="background: white; color: black;">;
    }
    </span><span style="background: white; color: blue;">else </span><span style="background: white; color: green;">// otherwise execute the default logic I have defined.
    </span><span style="background: white; color: black;">{
        query.where(</span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">() {
            </span><span style="background: white; color: blue;">return this</span><span style="background: white; color: black;">.complete === </span><span style="background: white; color: blue;">false </span><span style="background: white; color: black;">&& </span><span style="background: white; color: blue;">this</span><span style="background: white; color: black;">.createdAt !== </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">;
        }
        );
        request.execute({
            success: </span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">(results) {
                results.forEach(</span><span style="background: white; color: blue;">function </span><span style="background: white; color: black;">(item) {
                    </span><span style="background: white; color: blue;">delete </span><span style="background: white; color: black;">item.createdAt;
                }
                );
                request.respond();
            }
        }
        );
    }
}</span></pre>

&#160;

**Client Code:**

<pre class="code"><span style="background: white; color: black;">    </span><span style="background: white; color: blue;">private async </span><span style="background: white; color: rgb(43, 145, 175);">Task</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: blue;">string</span><span style="background: white; color: black;">&gt; RefreshTodoItems()
        {
            </span><span style="background: white; color: blue;">string </span><span style="background: white; color: black;">aStr = </span><span style="background: white; color: rgb(163, 21, 21);">"MyString"</span><span style="background: white; color: black;">;
            </span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceInvalidOperationException </span><span style="background: white; color: black;">exception = </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">;
            </span><span style="background: white; color: blue;">try
            </span><span style="background: white; color: black;">{
                </span><span style="background: white; color: green;">// This code refreshes the entries in the list view by querying the TodoItems table.
                // The query excludes completed TodoItems
                </span><span style="background: white; color: rgb(43, 145, 175);">Dictionary</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: blue;">string</span><span style="background: white; color: black;">,</span><span style="background: white; color: blue;">string</span><span style="background: white; color: black;">&gt; parameters = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">Dictionary</span><span style="background: white; color: black;">&lt;</span><span style="background: white; color: blue;">string</span><span style="background: white; color: black;">,</span><span style="background: white; color: blue;">string</span><span style="background: white; color: black;">&gt;();
                parameters.Add(</span><span style="background: white; color: rgb(163, 21, 21);">"operation"</span><span style="background: white; color: black;">,</span><span style="background: white; color: rgb(163, 21, 21);">"nofilters"</span><span style="background: white; color: black;">);
                items = </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">todoTable.WithParameters(parameters).ToCollectionAsync();
            }
            </span><span style="background: white; color: blue;">catch </span><span style="background: white; color: black;">(</span><span style="background: white; color: rgb(43, 145, 175);">MobileServiceInvalidOperationException </span><span style="background: white; color: black;">e)
            {
                exception = e;
            }
            </span><span style="background: white; color: blue;">if </span><span style="background: white; color: black;">(exception != </span><span style="background: white; color: blue;">null</span><span style="background: white; color: black;">)
            {
                </span><span style="background: white; color: blue;">await new </span><span style="background: white; color: rgb(43, 145, 175);">MessageDialog</span><span style="background: white; color: black;">(exception.Message, </span><span style="background: white; color: rgb(163, 21, 21);">"Error loading items"</span><span style="background: white; color: black;">).ShowAsync();
            }
            </span><span style="background: white; color: blue;">else
            </span><span style="background: white; color: black;">{
                ListItems.ItemsSource = items;
            }
            </span><span style="background: white; color: blue;">return </span><span style="background: white; color: black;">aStr;
        }
</span></pre>

&#160;

You should be able to see how you could extend this to do things like execute a SQL statement passed in as a parameter!

Let me know if you find this useful,

Jeff