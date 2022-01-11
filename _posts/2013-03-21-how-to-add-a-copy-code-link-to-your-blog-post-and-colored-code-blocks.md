A nice touch to your blog is to have a link to copy the code you have entered.&nbsp; Another great feature is to have your code colored as it would be in Visual Studio.&nbsp; There a couple of ways you can do this.&nbsp; Here is how I prefer to do it!

# LiveWriter Plug-in for code formatting

I use LiveWriter so I love to use Plug-Ins when appropriate.&nbsp; There are some plugins to make code pretty but some require <style> definitions.&nbsp; The MSDN blogs parse out these styles so you end up having to manually adding these styles to your blog’s theme (yuck).

## Install plug-in

In LiveWriter, go to the ‘Insert’ tab and choose ‘Add plug-in’

[<img loading="lazy" title="image" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/7167.image_thumb_2D9CF77E.png" width="752" height="172" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/8231.image_15798D23.png)

&nbsp;

Once there filter by ‘Formatting / clipboard’ and choose ‘Paste from Visual Studio’

[<img loading="lazy" title="image" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6177.image_thumb_59D97E62.png" width="738" height="374" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/3056.image_0CA984D7.png)

Hit the download button, then run the installer.

Now close and restart LiveWriter (don’t forget to save your work).

## Use the Plug-in

To use this plugin:

  * Copy the code you want from Visual Studio 
      * From the ‘Insert’ tab choose the ‘VSPaste’ plug-in (highlighted for you here: </ul> 
    &nbsp;
    
    [<img loading="lazy" title="image" border="0" alt="image" src="/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/6175.image_thumb_380DA5D1.png" width="771" height="180" />](/assets/images/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/83/94/metablogapi/4431.image_31C6CF43.png)
    
    Result:
    
    &nbsp;
    
    <pre class="code"><span style="background: white;color: black">    app.addEventListener(</span><span>"activated"</span><span style="background: white;color: black">, </span><span style="background: white;color: blue">function </span><span style="background: white;color: black">(args) {
        </span><span style="background: white;color: blue">if </span><span style="background: white;color: black">(args.detail.kind === activation.ActivationKind.launch) {
            </span><span style="background: white;color: blue">if </span><span style="background: white;color: black">(args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {
                </span><span style="background: white;color: green">// TODO: This application has been newly launched. Initialize
                // your application here.
            </span><span style="background: white;color: black">} </span><span style="background: white;color: blue">else </span><span style="background: white;color: black">{
                </span><span style="background: white;color: green">// TODO: This application has been reactivated from suspension.
                // Restore application state here.
            </span><span style="background: white;color: black">}
            </span><span style="background: white;color: blue">if </span><span style="background: white;color: black">(app.sessionState.history) {
                nav.history = app.sessionState.history;
            }
            args.setPromise(WinJS.UI.processAll().then(</span><span style="background: white;color: blue">function </span><span style="background: white;color: black">() {
                </span><span style="background: white;color: blue">if </span><span style="background: white;color: black">(nav.location) {
                    nav.history.current.initialPlaceholder = </span><span style="background: white;color: blue">true</span><span style="background: white;color: black">;
                    </span><span style="background: white;color: blue">return </span><span style="background: white;color: black">nav.navigate(nav.location, nav.state);
                } </span><span style="background: white;color: blue">else </span><span style="background: white;color: black">{
                    </span><span style="background: white;color: blue">return </span><span style="background: white;color: black">nav.navigate(Application.navigator.home);
                }
            }));
        }
    });
</span></pre>
    
    &nbsp;
    
    > Note:&nbsp; If you disable any plug-in, installing it will not make it show up in the plug-in list.&nbsp; Simply re-enable it.
    
    # Add a Copy Code link
    
    You can of course sweep out code and copy it from the page.&nbsp; I like to provide a ‘Copy Code’ link so I can ensure the blog reader gets all of the code correctly from me (and it is cool).
    
    To do this you simply need to add a little JavaScript and a give a unique name to the block around the code you just pasted into the document.
    
    ## How to add the Copy Code JavaScript to your page </p> 
    
      * Click on the ‘Source’ tab at the bottom LiveWriter and then scroll all the way to the top of the page. 
          * Insert this script at the top </ul> 
        > **<a style="background: lightgray">Copy Code:</a>**
        > 
        > <pre id="CopyCodeCodeSection1" class="code"><span style="background: white;color: blue">&lt;</span><span style="background: white;color: maroon">SCRIPT </span><span style="background: white;color: red">language</span><span style="background: white;color: blue">=jscript&gt;
    function </span><span style="background: white;color: black">CopyCode(elemName) {
        </span><span style="background: white;color: blue">var </span><span style="background: white;color: black">obj = document.getElementById(elemName);
        window.clipboardData.setData(</span><span>"Text"</span><span style="background: white;color: black">, obj.innerText);
    }
</span><span style="background: white;color: blue">&lt;/</span><span style="background: white;color: maroon">SCRIPT</span><span style="background: white;color: blue">&gt;
</span></pre>
        
        ## How to use the JavaScript and add Copy Code links
        
        &nbsp;
        
          * Still in the Source view, find the code you want to add the Copy Code link to (hint, if you used the _VSInsert_ plug-in it will start with <pre class=&#8221;code&#8221;> and end with </pre> 
              * Give this block of text a unique id.&nbsp; This id has to unique to your entire blog as well as this page because on your blog home page there may be more than just your current blog with a copy code section (and you would get the wrong one potentially).&nbsp; </ul> 
            &nbsp;
            
            **<button style="background: lightgray">Copy Code:</button>** </p> 
            
            <pre id="CopyCodeCodeSection2" class="code"><span style="background: white;color: blue">&lt;</span><span style="background: white;color: maroon">pre </span><span style="background: white;color: red">id</span><span style="background: white;color: blue">="CopyCodeCodeSection1" </span></pre>
            
            > 
              * Insert the Copy Code link and use the same id with the link handler like this 
            
            &nbsp;
            
            **<a style="background: lightgray" href="copyToClipboard('CopyCodeCodeSection3');">Copy Code:</a>** </p> 
            
            <pre id="CopyCodeCodeSection3" class="code"><span style="background: white;color: blue">&lt;</span><span style="background: white;color: maroon">strong</span><span style="background: white;color: blue">&gt;&lt;</span><span style="background: white;color: maroon">a </span><span style="background: white;color: red">href</span><span style="background: white;color: blue">="javascript:CopyCode('CopyCodeCodeSection1');"&gt;</span><span style="background: white;color: black">Copy Code:</span><span style="background: white;color: blue">&lt;/</span><span style="background: white;color: maroon">a</span><span style="background: white;color: blue">&gt;</span><span style="background: white;color: blue">&lt;/</span><span style="background: white;color: maroon">strong</span><span style="background: white;color: blue">&gt;
</span></pre>
            
              * Add more Copy Code buttons to your code and ensure you increment the name each time for the code id and the text for the javascript (CopyCodeCodeSection2, CopyCodeCodeSection3, CopyCodeCodeSection4, etc…) 
              * Save your blog as a draft and see how it works! 
                  * Note: You will see my ‘Copy Code:’ text has a lightgray background.&nbsp; I did this by styling the <a> tag like this: <pre class="code"><span style="background: white;color: blue">&lt;</span><span style="background: white;color: maroon">strong</span><span style="background: white;color: blue">&gt;<br />&lt;</span><span style="background: white;color: maroon">a </span><span style="background: white;color: red">style</span><span style="background: white;color: blue">="</span><span style="background: white;color: red">background</span><span style="background: white;color: black">: </span><span style="background: white;color: blue">lightgray</span><span style="background: white;color: black">;</span><span style="background: white;color: blue">" </span><span style="background: white;color: red">href</span><span style="background: white;color: blue">="javascript:CopyCode('CopyCodeCodeSection1');"&gt;</span><span style="background: white;color: black">Copy Code:</span><span style="background: white;color: blue">&lt;/</span><span style="background: white;color: maroon">a</span><span style="background: white;color: blue">&gt;<br />&lt;/</span><span style="background: white;color: maroon">strong</span><span style="background: white;color: blue">&gt; </span></pre></ul> 
                
                > &nbsp;
                
                # Summary
                
                You can feel free to change the formatting or style of you Copy Code: link!&nbsp; I hope you find this useful so drop me a note if you like it!
                
                @JsandersRocks, @WSDevSol
                
                # Helpful links
                
                <a title="http://windows.microsoft.com/en-US/windows-live/essentials-other-programs?T1=t4" href="http://windows.microsoft.com/en-US/windows-live/essentials-other-programs?T1=t4" target="_blank">Windows Live Writer</a>
                
                <a href="http://plugins.live.com/writer/detail/paste-from-visual-studio" target="_blank">Install point for &#8216;Paste from Visual Studio&#8217;</a>