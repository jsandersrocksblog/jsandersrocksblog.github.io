You can guarantee you will deadlock if you have a call similar to this in your code, where CallHttp is a an AsyncTask that awaits a result:

<pre class="code"><p>
  <span style="color: blue">public class </span><span style="color: #2b91af">DeadlockController </span><span style="color: black">: </span><span style="color: #2b91af">ApiController
     </span><span style="color: black">{
         </span><span style="color: blue">public string </span><span style="color: black">Get() {
             </span><span style="color: blue">string </span><span style="color: black">ret = </span><span style="color: #a31515">""</span><span style="color: black">;
             </span><span style="color: green">// deadlock
             </span><span style="color: black">ret = </span><span style="color: #2b91af">Utilities</span><span style="color: black">.CallHttp().Result;
             </span><span style="color: blue">return </span><span style="color: black">ret;
         }</span>
</p></pre>



# 

# Cause and Symptoms

The reason why is that the ASP.Net context is being used to run this call and the call inside of CallHttp().&nbsp; The inner function has an await and tries to acquire the ASP.Net context which in turn is waiting for the completion of the Result call. This same thing can happen in the UI Context of a Winforms app (See: [https://blogs.msdn.microsoft.com/pfxteam/2011/01/13/await-and-ui-and-deadlocks-oh-my/](https://blogs.msdn.microsoft.com/pfxteam/2011/01/13/await-and-ui-and-deadlocks-oh-my/ "https://blogs.msdn.microsoft.com/pfxteam/2011/01/13/await-and-ui-and-deadlocks-oh-my/") ).&nbsp; You will notice that calls do not complete and/or the process starts to leak threads and other resources.

# Confirming issue

You can have the customer look for code that is calling async methods improperly.&nbsp; If you take a dump and run the Debug Diagnostics it will show something similar to this:

The following threads in **issues.iisexpress.dmp** are waiting in **System.Threading.Monitor.Wait**  
( [**32**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread19100) [**33**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread12820) [**34**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread6184) [**38**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread7052) [**39**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread9312) [**40**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread11140) [**42**](\Users\jsanders\Documents\DebugDiag\Reports\issues.iisexpress_CrashHangAnalysis.mht#B1C1Thread17016) )  
**14.58%** of threads blocked (7 threads)

Threads waiting in [Monitor.Wait](http://msdn.microsoft.com/en-us/library/syehfawa.aspx) are actually waiting to re-acquire a lock which they released. The signal to reacquire the lock will be given by a call to **Monitor.Pulse** or **Monitor.PulseAll** or when the timeout is hit.  
Look at the callstack of the thread to see which function is making a call to Monitor.Wait and then review code to find out the function which is supposed to call **Monitor.Pulse** or **Monitor.PulseAll** and see why that function is not getting called.

&nbsp;

If you attach to a debug version of your app and break in the debugger you will see many threads waiting on the .Return function to complete.

&nbsp;

Here is a sample stack (from Debug Diagnostics) where you see the call deadlocked:

&nbsp;

**.NET Call Stack**

[[GCFrame]]

\[[HelperMethodFrame_1OBJ\] (System.Threading.Monitor.ObjWait)] System.Threading.Monitor.ObjWait(Boolean, Int32, System.Object)

mscorlib_ni!System.Threading.Monitor.Wait(System.Object, Int32, Boolean)+17

mscorlib_ni!System.Threading.Monitor.Wait(System.Object, Int32)+c

mscorlib_ni!System.Threading.ManualResetEventSlim.Wait(Int32, System.Threading.CancellationToken)+317

mscorlib_ni!System.Threading.Tasks.<font style="background-color: #ffff00">Task.SpinThenBlockingWait</font>(Int32, System.Threading.CancellationToken)+9c

mscorlib_ni!System.Threading.Tasks.Task.InternalWait(Int32, System.Threading.CancellationToken)+155

mscorlib\_ni!System.Threading.Tasks.Task\`1[[System.\__Canon, mscorlib]].<font style="background-color: #ffff00">GetResultCore</font>(Boolean)+4b

mscorlib\_ni!System.Threading.Tasks.Task\`1[[System.\_\_Canon, mscorlib]].get\_Result()+22

WaitVsResult.Controllers.DeadlockController.Get()+50

<font style="background-color: #ffff00"></font>&nbsp; 

# Fix

Do not block by using the .Result property of an asynchronous call.&nbsp; Patters such as marking the function async, or the aspx page as async and calling with _await_ will fix this issue.&nbsp; You can also use Task.Run in a lambda and call _.Wait_ to synchronize the call.

Good code:

<pre class="code"><span style="color: blue">      public async </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: blue">string</span><span style="color: black">&gt; Get() {
           </span><span style="color: blue">string </span><span style="color: black">ret = </span><span style="color: #a31515">""</span><span style="color: black">;
           </span><span style="color: green">// does NOT deadlock
           </span><span style="color: black">ret = </span><span style="color: blue">await </span><span style="color: #2b91af">Utilities</span><span style="color: black">.CallHttp();
           </span><span style="color: blue">return </span><span style="color: black">ret;
       }
       </span><span style="color: blue">public string </span><span style="color: black">Get(</span><span style="color: blue">int </span><span style="color: black">id) {
           </span><span style="color: blue">string </span><span style="color: black">ret = </span><span style="color: #a31515">""</span><span style="color: black">;
           </span><span style="color: green">// Start a task - calling an async function in this example
           </span><span style="color: #2b91af">Task</span><span style="color: black">&lt;</span><span style="color: blue">string</span><span style="color: black">&gt; callTask = </span><span style="color: #2b91af">Task</span><span style="color: black">.Run(() =&gt; </span><span style="color: #2b91af">Utilities</span><span style="color: black">.CallHttp());
           </span><span style="color: green">// Wait for it to finish
           </span><span style="color: black">callTask.Wait();
           </span><span style="color: green">// Get the result
           </span><span style="color: black">ret = callTask.Result;
           </span><span style="color: blue">return </span><span style="color: black">ret;
       }</span></pre>

&nbsp;

# Note

You will also see a great explanation here: [http://blog.stephencleary.com/2012/07/dont-block-on-async-code.html](http://blog.stephencleary.com/2012/07/dont-block-on-async-code.html "http://blog.stephencleary.com/2012/07/dont-block-on-async-code.html")