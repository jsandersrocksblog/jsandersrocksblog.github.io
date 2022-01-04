---
id: 2385
title: Azure .NET Core Application Settings
date: 2017-05-16T18:15:25-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=2385
permalink: /2017/05/16/azure-net-core-application-settings/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Azure .NET Core Application Settings" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/16/azure-net-core-application-settings/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview This article outlines how to work with Application Settings in ASP.NET Core with Azure Web Apps (Azure App Services) super simple Jeff version… How To Ref: Working with Azure App Services Application Settings and Connection Strings in ASP.NET Core The above article is wonderful but adds some complexity.&nbsp; It also does not tell you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Azure .NET Core Application Settings" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/05/16/azure-net-core-application-settings/" />
    <meta name="twitter:description" content="Overview This article outlines how to work with Application Settings in ASP.NET Core with Azure Web Apps (Azure App Services) super simple Jeff version… How To Ref: Working with Azure App Services Application Settings and Connection Strings in ASP.NET Core The above article is wonderful but adds some complexity.&nbsp; It also does not tell you..." />
    
categories:
  - Uncategorized
---


This article outlines how to work with Application Settings in ASP.NET Core with Azure Web Apps (Azure App Services) super simple Jeff version…

## How To

Ref: <a title="https://blogs.msdn.microsoft.com/cjaliaga/2016/08/10/working-with-azure-app-services-application-settings-and-connection-strings-in-asp-net-core/" href="https://blogs.msdn.microsoft.com/cjaliaga/2016/08/10/working-with-azure-app-services-application-settings-and-connection-strings-in-asp-net-core/" target="_blank">Working with Azure App Services Application Settings and Connection Strings in ASP.NET Core</a>

The above article is wonderful but adds some complexity.&nbsp; It also does not tell you how to get the Configuration in your controllers etc…&nbsp; It is super simple to do this and here is a quick sample for you to follow.

The default WebApp templates provide the wiring for the Configuration like this:

<pre class="code"><span style="color: blue">public </span><span style="color: black">Startup(</span><span style="color: #2b91af">IHostingEnvironment </span><span style="color: black">env)
        {
            </span><span style="color: blue">var </span><span style="color: black">builder = </span><span style="color: blue">new </span><span style="color: #2b91af">ConfigurationBuilder</span><span style="color: black">()
                .SetBasePath(env.ContentRootPath)
                .AddJsonFile(</span><span style="color: #a31515">"appsettings.json"</span><span style="color: black">, optional: </span><span style="color: blue">false</span><span style="color: black">, reloadOnChange: </span><span style="color: blue">true</span><span style="color: black">)
                .AddJsonFile(</span><span style="color: #a31515">$"appsettings.</span><span style="color: black">{env.EnvironmentName}</span><span style="color: #a31515">.json"</span><span style="color: black">, optional: </span><span style="color: blue">true</span><span style="color: black">)
                .AddEnvironmentVariables();
            Configuration = builder.Build();
        }
</span></pre>

If it is not there, use a template or add it yourself by copying the code and dependencies from a blank project.

Now you need to add this to the services as a singleton with the line:&nbsp; services.AddSingleton<IConfiguration>(Configuration);

<pre class="code"><span style="color: green">// This method gets called by the runtime. Use this method to add services to the container.
       </span><span style="color: blue">public void </span><span style="color: black">ConfigureServices(</span><span style="color: #2b91af">IServiceCollection </span><span style="color: black">services)
       {
           </span><span style="color: green">// Add framework services.
           </span><span style="color: black">services.AddMvc();
           </span><span style="color: green">// Add the configuration singleton here
           </span><span style="color: black">services.AddSingleton&lt;</span><span style="color: #2b91af">IConfiguration</span><span style="color: black">&gt;(Configuration);
       }</span></pre>

In the controller code, or page code, add a new constructor that takes IConfiguration.&nbsp; This will ensure that value is passed.&nbsp; Then you simply store this as a variable to use in your code:

<pre class="code"><span style="color: black">[</span><span style="color: #2b91af">Route</span><span style="color: black">(</span><span style="color: #a31515">"api/[controller]"</span><span style="color: black">)]
    </span><span style="color: blue">public class </span><span style="color: #2b91af">ValuesController </span><span style="color: black">: </span><span style="color: #2b91af">Controller
    </span><span style="color: black">{
        </span><span style="color: green">// Place to store the Config object and use in this controller
        </span><span style="color: blue">private readonly </span><span style="color: #2b91af">IConfiguration </span><span style="color: black">Config;
        </span><span style="color: green">// Constructor that that takes IConfiguration is called on instantiation thanks to Dependency injection
        </span><span style="color: blue">public </span><span style="color: black">ValuesController(</span><span style="color: #2b91af">IConfiguration </span><span style="color: black">config)
        {
            Config = config;
        }
        </span><span style="color: green">// GET api/values
        </span><span style="color: black">[</span><span style="color: #2b91af">HttpGet</span><span style="color: black">]
        </span><span style="color: blue">public </span><span style="color: #2b91af">IEnumerable</span><span style="color: black">&lt;</span><span style="color: blue">string</span><span style="color: black">&gt; Get()
        {
            </span><span style="color: green">// Use the Config object set in the constructor
            </span><span style="color: blue">var </span><span style="color: black">x = Config[</span><span style="color: #a31515">"mykey"</span><span style="color: black">];
            </span><span style="color: blue">return new string</span><span style="color: black">[] { </span><span style="color: #a31515">"value1"</span><span style="color: black">, </span><span style="color: #a31515">"value2" </span><span style="color: black">};
        }
</span></pre>

Now you can set mykey in the portal and this value will be read.&nbsp; You can also set it in the appsettings.json to set the value when testing local with IIS Express.

Note that Connection strings can be retrieved using something like: Config.GetConnectionString(“myconnstring”);

Drop me a note if you find this useful!

## References

<a title="https://blogs.msdn.microsoft.com/cjaliaga/2016/08/10/working-with-azure-app-services-application-settings-and-connection-strings-in-asp-net-core/" href="https://blogs.msdn.microsoft.com/cjaliaga/2016/08/10/working-with-azure-app-services-application-settings-and-connection-strings-in-asp-net-core/" target="_blank">Working with Azure App Services Application Settings and Connection Strings in ASP.NET Core</a>

<a title="https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection" href="https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection" target="_blank">Introduction to Dependency Injection in ASP.NET Core</a>

<a href="https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration" target="_blank">Configuration in ASP.NET Core</a>

&nbsp;

key words: “.net core azure webapp” “.net core azure appsettings” “.net core CloudConfigurationManager”