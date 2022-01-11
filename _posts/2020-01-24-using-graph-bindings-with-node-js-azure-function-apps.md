Using Graph Bindings with Node.JS Azure

# Draft
  1. Create a function app and enable AppServices Authentication for AAD but don’t require login.&nbsp; Use the express settings.&nbsp; Since we are using the app identity ensure you Allow Anonymous requests.




[<img loading="lazy" width="513" height="371" title="clip_image002" style="display: inline; background-image: none;" alt="clip_image002" src="/assets/images/2020/01/clip_image002_thumb.gif" border="0" />](/assets/images/2020/01/clip_image002.gif)

<ol start="2">
  <li>
    Navigate to the root of the site and Admin Consent access, make sure you can log in. <li>
      Only if you want to develop local Next retrieve the following variables from the KUDU console from the Environment section of the Kudu interface:
    </li></ol> 
    <p>
      <a href="/assets/images/2020/01/clip_image004.gif"><img loading="lazy" width="539" height="443" title="clip_image004" style="display: inline; background-image: none;" alt="clip_image004" src="/assets/images/2020/01/clip_image004_thumb.gif" border="0" /></a>
    </p>
    
    <p>
      And set this in the local.settings.json
    </p>
    
    <p>
      &#8220;WEBSITE_AUTH_CLIENT_ID&#8221;:&nbsp; &#8220;fbd9bb9c-xxxxxx-245221e766cc&#8221;,
    </p>
    
    <p>
      &#8220;WEBSITE_AUTH_CLIENT_SECRET&#8221;:&#8221;ctboPyySE/JD2oGlAlXxxxx7ylVNQRhXU=&#8221;,
    </p>
    
    <p>
      &#8220;WEBSITE_AUTH_OPENID_ISSUER&#8221;: &#8220;<a href="https://sts.windows.net/fb840fe1-3b88xxxx-18fbf56fae21/">https://sts.windows.net/fb840fe1-3b88xxxx-18fbf56fae21/</a>&#8220;,
    </p>
    
    <p>
      &#8220;BYOB_TokenMap&#8221;:&#8221;C:\temp&#8221;
    </p>
    
    <ol start="4">
      <li>
        Create the extensions.csproj file in the wwwroot folder with these values.&nbsp; You can use the app service editor to do this (<a href="https://yourfuncsite.scm.azurewebsites.net/dev">https://yourfuncsite.scm.azurewebsites.net/dev</a>
      </li>
    </ol>
    
    <p>
      <code>&lt;/p>
&lt;p>&lt;Project Sdk="Microsoft.NET.Sdk"&gt;&lt;/p>
&lt;p>&nbsp; &lt;PropertyGroup&gt;&lt;/p>
&lt;p>&nbsp;&nbsp;&nbsp; &lt;TargetFramework&gt;netcoreapp2.2&lt;/TargetFramework&gt;&lt;/p>
&lt;p>&nbsp;&nbsp;&nbsp; &lt;WarningsAsErrors /&gt;&lt;/p>
&lt;p>&nbsp; &lt;/PropertyGroup&gt;&lt;/p>
&lt;p>&nbsp; &lt;ItemGroup&gt;&lt;/p>
&lt;p>&nbsp;&nbsp;&nbsp; &lt;PackageReference Include="Microsoft.Azure.WebJobs.Extensions.AuthTokens" Version="1.0.0-beta6" /&gt;&lt;/p>
&lt;p>&nbsp;&nbsp;&nbsp; &lt;PackageReference Include="Microsoft.Azure.WebJobs.Extensions.Storage" Version="3.0.10" /&gt;&lt;/p>
&lt;p>&nbsp;&nbsp;&nbsp; &lt;PackageReference Include="Microsoft.Azure.WebJobs.Script.ExtensionsMetadataGenerator" Version="1.1.2" /&gt;&lt;/p>
&lt;p>&nbsp; &lt;/ItemGroup&gt;&lt;/p>
&lt;p></code>
    </p>
    
    <p>
      <code>&lt;/Project&gt;</code>
    </p>
    
    <ol start="5">
      <li>
        Stop the website <li>
          Clean your Host.json so it ONLY has this:
        </li></ol> 
        <blockquote>
          <p>
            {
          </p>
          
          <p>
            &nbsp; &#8220;version&#8221;: &#8220;2.0&#8221;
          </p>
          
          <p>
            }
          </p>
        </blockquote>
        
        <ol start="5">
          <li>
            Go to WWWROOT folder in the kudu console and run this command:
          </li>
        </ol>
        
        <p>
          D:\home\site\wwwroot> <code> </code>
        </p>
        
        <p>
          <code>dotnet build extensions.csproj -o bin --no-incremental --packages D:\home\.nuget</code>
        </p>
        
        <p>
        </p>
        
        <p>
          Wait until the command prompt comes back and restart the site.
        </p>
        
        <ol start="7">
          <li>
            Create an httptrigger function an use this function.json
          </li>
        </ol>
        
        <p>
          {
        </p>
        
        <p>
          &nbsp; &#8220;bindings&#8221;: [
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; {
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;name&#8221;: &#8220;req&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;type&#8221;: &#8220;httpTrigger&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;direction&#8221;: &#8220;in&#8221;
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; },
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; {
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;type&#8221;: &#8220;token&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;direction&#8221;: &#8220;in&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;name&#8221;: &#8220;graphToken&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;resource&#8221;: &#8220;<a href="https://graph.microsoft.com">https://graph.microsoft.com</a>&#8220;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;identity&#8221;: &#8220;clientCredentials&#8221;
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; },
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; {
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;name&#8221;: &#8220;$return&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;type&#8221;: &#8220;http&#8221;,
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8220;direction&#8221;: &#8220;out&#8221;
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; }
        </p>
        
        <p>
          &nbsp; ],
        </p>
        
        <p>
          &nbsp; &#8220;disabled&#8221;: false
        </p>
        
        <p>
          }
        </p>
        
        <p>
          And index js for the code to prove you get the token!
        </p>
        
        <p>
          module.exports = async function (context, req) {
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; context.log(&#8216;JavaScript HTTP trigger function processed a request.&#8217;);
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp; let token = &#8220;Bearer &#8221; + context.bindings.graphToken;
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp; context.log(token);
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; context.res = {
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // status: 200, /* Defaults to 200 */
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; body: &#8220;Hello &#8221; + token
        </p>
        
        <p>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; };
        </p>
        
        <p>
          };
        </p>
        
        <p>
          You will see it dumps the current bearer token based on the ID of the function app.
        </p>
        
        <p>
        </p>
        
        <p>
        </p>
        
        <p>
          References:&nbsp; <a href="https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-microsoft-graph">https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-microsoft-graph</a>
        </p>
        
        <p>
          <a href="https://github.com/Azure/azure-functions-microsoftgraph-extension/blob/master/samples/GraphExtensionSamples/WebhookTriggerExamples.cs">https://github.com/Azure/azure-functions-microsoftgraph-extension/blob/master/samples/GraphExtensionSamples/WebhookTriggerExamples.cs</a>
        </p>
        
        <p>
          <a href="https://github.com/Azure/azure-functions-microsoftgraph-extension">https://github.com/Azure/azure-functions-microsoftgraph-extension</a>
        </p>