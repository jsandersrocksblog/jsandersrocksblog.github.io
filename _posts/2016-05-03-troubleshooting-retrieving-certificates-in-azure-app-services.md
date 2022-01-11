You can upload and use Certificates securely in your Azure App Service (Azure Web App, Azure Mobile App etc… ).&nbsp; If you are having trouble, here are some basic troubleshooting steps.

Example error: ”cannot find certificate with thumbprint&#8221;

Is your certificate loaded in your Resource Group?&nbsp; You can search for the thumbprint using the <a href="https://resources.azure.com/" target="_blank">Azure Resource Explorer</a>

Is your site at least Basic SKU?&nbsp; This is required.

Did you set the Web App setting: WEBSITE\_LOAD\_CERTIFICATES?&nbsp; Try setting the WEBSITE\_LOAD\_CERTIFICATES&nbsp; value to * for testing purposes

What is your code doing?&nbsp; Here is how you can load all certificates and display the first one.&nbsp; See the <a href="https://azure.microsoft.com/en-us/blog/using-certificates-in-azure-websites-applications/" target="_blank">original article</a> for picking one by thumbprint.

<pre class="code"><span style="background: white;color: blue">static string </span><span style="background: white;color: black">testcert()
        {
            </span><span style="background: white;color: blue">string </span><span style="background: white;color: black">strRes = </span><span style="background: white;color: #a31515">"no certs found"</span><span style="background: white;color: black">;
            </span><span style="background: white;color: green">//Cert Store for CurrentUser is the only one we can get certificates for
            </span><span style="background: white;color: #2b91af">X509Store </span><span style="background: white;color: black">certStore = </span><span style="background: white;color: blue">new </span><span style="background: white;color: #2b91af">X509Store</span><span style="background: white;color: black">(</span><span style="background: white;color: #2b91af">StoreName</span><span style="background: white;color: black">.My, </span><span style="background: white;color: #2b91af">StoreLocation</span><span style="background: white;color: black">.CurrentUser);
            </span><span style="background: white;color: green">//Open it read only
            </span><span style="background: white;color: black">certStore.Open(</span><span style="background: white;color: #2b91af">OpenFlags</span><span style="background: white;color: black">.ReadOnly);
            </span><span style="background: white;color: green">// if we have any certificates...
            </span><span style="background: white;color: blue">if </span><span style="background: white;color: black">(certStore.Certificates.Count &gt; 0)
            {
                </span><span style="background: white;color: green">//Just get the first one
                </span><span style="background: white;color: #2b91af">X509Certificate2 </span><span style="background: white;color: black">cert = certStore.Certificates[0];
                </span><span style="background: white;color: green">// Use certificate
                // In this case get the subject
                </span><span style="background: white;color: black">strRes = cert.Subject;
                </span><span style="background: white;color: #2b91af">Console</span><span style="background: white;color: black">.WriteLine(strRes);
            }
            </span><span style="background: white;color: green">//Don't forget to CLOSE the store
            </span><span style="background: white;color: black">certStore.Close();
            </span><span style="background: white;color: blue">return </span><span style="background: white;color: black">strRes;
        }</span></pre>

&nbsp;

Debug the app to see what is going on in your Cert Code!&nbsp; If the cert shows up in the Portal for your web app then it must be loaded in the resource group.

Ensure the StoreName.My and StoreLocation.CurrentUser is where you are looking for the cert!

&nbsp;

I know this is simple but sometimes it helps to have a checklist!&nbsp; Let me know if this was useful to you by dropping a comment!