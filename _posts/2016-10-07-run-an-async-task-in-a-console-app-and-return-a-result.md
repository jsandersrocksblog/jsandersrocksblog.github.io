I had someone ask how to run an async task in Main of a console app.&nbsp; Yes there are different ways to do it and this is just one!

&nbsp;

<pre class="code"><span style="color: blue">using </span><span style="color: black">System;
</span><span style="color: blue">using </span><span style="color: black">System.Net.Http;
</span><span style="color: blue">using </span><span style="color: black">System.Threading.Tasks;
</span><span style="color: blue">namespace </span><span style="color: black">UrlAuth
{
    </span><span style="color: blue">class </span><span style="color: #2b91af">Program
    </span><span style="color: black">{
        </span><span style="color: blue">static void </span><span style="color: black">Main(</span><span style="color: blue">string</span><span style="color: black">[] args)
        {
            </span><span style="color: blue">try
            </span><span style="color: black">{
                </span><span style="color: green">// Start a task - calling an async function in this example
                </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: blue">string</span><span style="color: black">&gt; callTask = </span><span style="color: #2b91af">Task</span><span style="color: black">.Run(() =&gt; CallHttp());
                </span><span style="color: green">// Wait for it to finish
                </span><span style="color: black">callTask.Wait();
                </span><span style="color: green">// Get the result
                </span><span style="color: blue">string </span><span style="color: black">astr = callTask.Result;
                </span><span style="color: green">// Write it our
                </span><span style="color: #2b91af">Console</span><span style="color: black">.WriteLine(astr);
            }
            </span><span style="color: blue">catch </span><span style="color: black">(</span><span style="color: #2b91af">Exception </span><span style="color: black">ex)  </span><span style="color: green">//Exceptions here or in the function will be caught here
            </span><span style="color: black">{
                </span><span style="color: #2b91af">Console</span><span style="color: black">.WriteLine(</span><span style="color: #a31515">"Exception: " </span><span style="color: black">+ ex.Message);
            }
        }
        </span><span style="color: green">// Simple async function returning a string...
        </span><span style="color: blue">static public async </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: blue">string</span><span style="color: black">&gt; CallHttp()
        {
            </span><span style="color: green">// Just a demo.  Normally my HttpClient is global (see docs)
            </span><span style="color: #2b91af">HttpClient </span><span style="color: black">aClient = </span><span style="color: blue">new </span><span style="color: #2b91af">HttpClient</span><span style="color: black">();
            </span><span style="color: green">// async function call we want to wait on, so wait
            </span><span style="color: blue">string </span><span style="color: black">astr = </span><span style="color: blue">await </span><span style="color: black">aClient.GetStringAsync(</span><span style="color: #a31515">"http://microsoft.com"</span><span style="color: black">);
            </span><span style="color: green">// return the value
            </span><span style="color: blue">return </span><span style="color: black">astr;
        }
    }
}
</span></pre>

Drop me a note if this helped you out!