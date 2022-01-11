In my early testing I wanted to _**always**_ seed my Local Database.&#160; By default the db was only dropped and reseeded if you changed the models.&#160; There is a simple code change to do this.

In WebApiConfig.cs change the class implementing IDatabaseInitializer that you pass into Database.SetInitializer from DropCreateDatabaseIfModelChanges to DropCreateDatabaseAlways

## Example

Previous (only updated if DataObject schema changes):

<pre class="code"><span style="background: white; color: black">    </span><span style="background: white; color: blue">public static class </span><span style="background: white; color: #2b91af">WebApiConfig
    </span><span style="background: white; color: black">{
        </span><span style="background: white; color: blue">public static void </span><span style="background: white; color: black">Register()
        {
            </span><span style="background: white; color: green">// Use this class to set configuration options for your mobile service
            </span><span style="background: white; color: #2b91af">ConfigOptions </span><span style="background: white; color: black">options = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ConfigOptions</span><span style="background: white; color: black">();
            </span><span style="background: white; color: green">// Use this class to set WebAPI configuration options
            </span><span style="background: white; color: #2b91af">HttpConfiguration </span><span style="background: white; color: black">config = </span><span style="background: white; color: #2b91af">ServiceConfig</span><span style="background: white; color: black">.Initialize(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ConfigBuilder</span><span style="background: white; color: black">(options));
            </span><span style="background: white; color: green">// To display errors in the browser during development, uncomment the following
            // line. Comment it out again when you deploy your service for production use.
            // config.IncludeErrorDetailPolicy = IncludeErrorDetailPolicy.Always;
            </span><span style="background: white; color: #2b91af">Database</span><span style="background: white; color: black">.SetInitializer(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">MobileService3Initializer</span><span style="background: white; color: black">());
        }
    }
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">MobileService3Initializer </span><span style="background: white; color: black">: </span><span style="background: white; color: #2b91af"><font color="#ff0000"><strong>DropCreateDatabaseIfModelChanges</strong></font></span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">MobileService3Context</span><span style="background: white; color: black">&gt;
    {
        </span><span style="background: white; color: blue">protected override void </span><span style="background: white; color: black">Seed(</span><span style="background: white; color: #2b91af">MobileService3Context </span><span style="background: white; color: black">context)
        {
            </span></pre>

[](http://11011.net/software/vspaste)

Now (always recreates the Database and reseeds):

&#160;

<pre class="code"><span style="background: white; color: black">   </span><span style="background: white; color: blue">public static class </span><span style="background: white; color: #2b91af">WebApiConfig
    </span><span style="background: white; color: black">{
        </span><span style="background: white; color: blue">public static void </span><span style="background: white; color: black">Register()
        {
            </span><span style="background: white; color: green">// Use this class to set configuration options for your mobile service
            </span><span style="background: white; color: #2b91af">ConfigOptions </span><span style="background: white; color: black">options = </span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ConfigOptions</span><span style="background: white; color: black">();
            </span><span style="background: white; color: green">// Use this class to set WebAPI configuration options
            </span><span style="background: white; color: #2b91af">HttpConfiguration </span><span style="background: white; color: black">config = </span><span style="background: white; color: #2b91af">ServiceConfig</span><span style="background: white; color: black">.Initialize(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">ConfigBuilder</span><span style="background: white; color: black">(options));
            </span><span style="background: white; color: green">// To display errors in the browser during development, uncomment the following
            // line. Comment it out again when you deploy your service for production use.
            // config.IncludeErrorDetailPolicy = IncludeErrorDetailPolicy.Always;
            </span><span style="background: white; color: #2b91af">Database</span><span style="background: white; color: black">.SetInitializer(</span><span style="background: white; color: blue">new </span><span style="background: white; color: #2b91af">MobileService3Initializer</span><span style="background: white; color: black">());
        }
    }
    </span><span style="background: white; color: blue">public class </span><span style="background: white; color: #2b91af">MobileService3Initializer </span><span style="background: white; color: black">: </span><span style="background: white; color: #2b91af"><strong><font color="#ff0000">DropCreateDatabaseAlways</font></strong></span><span style="background: white; color: black">&lt;</span><span style="background: white; color: #2b91af">MobileService3Context</span><span style="background: white; color: black">&gt;
    {
        </span><span style="background: white; color: blue">protected override void </span><span style="background: white; color: black">Seed(</span><span style="background: white; color: #2b91af">MobileService3Context </span><span style="background: white; color: black">context)
        {<br /></span></pre>

[](http://11011.net/software/vspaste)